# 如何使用VSCode创建自定义模块

## 创建项目

```powershell
dotnet new classlib -o Xizhang.Modules.Hello.Actions -f netstandard2.0
```

项目名称中需要带有一个Modules


## 添加对SDK的应用

```powershell
dotnet add package pad.action.sdk
```

## 修改csproj文件

```diff
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
+    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>

```

## 增加AssemblyInfo.cs

```csharp
using System.Reflection;

[assembly: AssemblyTitle("程序集标题")]
```


## 修改默认的Class1

```csharp
using System;
using Microsoft.Flow.RPA.Desktop.Modules.SDK;
using Microsoft.Flow.RPA.Desktop.Modules.SDK.Extended.Attributes;
using Microsoft.Flow.RPA.Desktop.Modules.SDK.Attributes;

namespace Xizhang.Modules.Hello.Actions
{
    [Action(Id = "Hello")]
    [Icon(Code = "EEE7")]
    public class HelloAction : ActionBase
    {
        [InputArgument]
        public string Name { get; set; }

        [OutputArgument]
        public string Result { get; set; }
        public override void Execute(ActionContext context)
        {
            Result = String.Format("Hello, {0}", Name);
        }
    }
}
```


## 编译得到dll

```powershell
dotnet build
```

## 创建要签名的证书

在管理员模式下打开PowerShell

```powershell

# 创建证书，并且导出私钥，另外启动安装，请注意要安装到 Trusted Root Certifications Authorities 里面

New-SelfSignedCertificate -Subject Xizhang.PAD.Actions.Cert -Type CodeSigningCert `
  | Export-PfxCertificate -Password (ConvertTo-SecureString -AsPlainText -Force "123456") `
    -FilePath c:\temp\Xizhang.Test.pfx

start c:\temp\Xizhang.Test.pfx

```

导出这个证书的私钥，pfx文件，例如 xizhang.pfx, 这个证书要安装到 个人 =》可信根中。

- [x] 如何在创建证书时一步到位，放在可信根下面，并且导出pfx文件（含密码）
  > 不能直接安装到可信根下面。这个必须手工操作。

## 使用证书签名

```
signtool sign /f xizhang.pfx /p 123456 .\Xizhang.Modules.Hello.Actions.dll
signtool timestamp /t http://time.certum.pl .\Xizhang.Modules.Hello.Actions.dll
```

## 放在对应的目录中去

把 dll 复制到下面的目录

C:\Program Files (x86)\Power Automate Desktop\custom-Modules

**这里的关键是路径名必须是 custom-modules**

请注意，把 Microsoft.Flow.RPA.Desktop.Modules.SDK.Extended.dll 也复制这个目录


现在可以工作了。


## 添加资源文件支持（例如对中文的支持）

创建资源文件，例如 Xizhang.Modules.Hello.Actions.txt

这个文件中的内容是一个键值对，例如对中文的支持

```text
title = value
```

- [ ] 这里要搞清楚有哪些键是必须的，如何映射AssemblyTitle, 到action，以及内部的参数

## 编译资源文件

```powershell
resgen Xizhang.Modules.Hello.Actions.txt
```

这个会生成一个 Xizhang.Modules.Hello.Actions.resources的文件

接下来利用这个文件生成一个dll

```powershell
al /embed:Xizhang.Modules.Hello.Actions.resources /out:Xizhang.Modules.Hello.Actions.resources.dll
```

把这个文件复制到下面目录

C:\Program Files (x86)\Power Automate Desktop\custom-Modules\zh-Hans

