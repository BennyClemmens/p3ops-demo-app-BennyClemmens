# SportStore

This project is a very simple e-commerce website for sports products.

## Requirements

- [.NET 6.0 SDK](https://dotnet.microsoft.com/en-us/download)

   ```bash
   PS C:\Windows\system32> winget search Microsoft.DotNet.SDK
   Name                           Id                           Version               Source
   -----------------------------------------------------------------------------------------
   Microsoft .NET SDK 3.1         Microsoft.DotNet.SDK.3_1     3.1.426               winget
   Microsoft .NET SDK 5.0         Microsoft.DotNet.SDK.5       5.0.408               winget
   Microsoft .NET SDK 6.0         Microsoft.DotNet.SDK.6       6.0.427               winget
   Microsoft .NET SDK 7.0         Microsoft.DotNet.SDK.7       7.0.410               winget
   Microsoft .NET SDK 8.0         Microsoft.DotNet.SDK.8       8.0.403               winget
   Microsoft .NET SDK 9.0 Preview Microsoft.DotNet.SDK.Preview 9.0.100-rc.2.24474.11 winget
   PS C:\Windows\system32> winget install --id Microsoft.DotNet.SDK --source winget
   No package found matching input criteria.
   PS C:\Windows\system32> winget install --id Microsoft.DotNet.SDK.6 --source winget
   Found Microsoft .NET SDK 6.0 [Microsoft.DotNet.SDK.6] Version 6.0.427
   This application is licensed to you by its owner.
   Microsoft is not responsible for, nor does it grant any licenses to, third-party packages.
   Downloading https://dotnetcli.azureedge.net/dotnet/Sdk/6.0.427/dotnet-sdk-6.0.427-win-x64.exe
   ██████████████████████████████   195 MB /  195 MB
   Successfully verified installer hash
   Starting package install...
   Successfully installed
   ```

   ![001_installing_dotnet6](img/001_installing_dotnet6.PNG)

- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

   ```bash
   PS C:\Windows\system32> winget search Microsoft.SQLServer
   Name                                    Id                                    Version        Source
   ----------------------------------------------------------------------------------------------------
   Microsoft SQL Server 2012 Native Client Microsoft.SQLServer.2012.NativeClient 11.4.7001.0    winget
   Microsoft SQL Server 2017 Developer     Microsoft.SQLServer.2017.Developer    14.0.1000.169  winget
   Microsoft SQL Server 2017 Express       Microsoft.SQLServer.2017.Express      14.0.1000.169  winget
   Microsoft SQL Server 2019 Developer     Microsoft.SQLServer.2019.Developer    15.2204.5490.2 winget
   Microsoft SQL Server 2019 Express       Microsoft.SQLServer.2019.Express      15.2204.5490.2 winget
   Microsoft SQL Server 2022 Developer     Microsoft.SQLServer.2022.Developer    16.0.1000.6    winget
   Microsoft SQL Server 2022 Express       Microsoft.SQLServer.2022.Express      16.0.1000.6    winget
   Microsoft SQL Server Management Studio  Microsoft.SQLServerManagementStudio   20.2           winget
   PS C:\Windows\system32> winget install --id Microsoft.SQLServer.2022.Express --source winget
   Found Microsoft SQL Server 2022 Express [Microsoft.SQLServer.2022.Express] Version 16.0.1000.6
   This application is licensed to you by its owner.
   Microsoft is not responsible for, nor does it grant any licenses to, third-party packages.
   Downloading https://download.microsoft.com/download/5/1/4/5145fe04-4d30-4b85-b0d1-39533663a2f1/SQL2022-SSEI-Expr.exe
   ██████████████████████████████  4.09 MB / 4.09 MB
   Successfully verified installer hash
   Starting package install...
   ```

   ```bash
   Microsoft (R) SQL Server Installer
   Copyright (c) 2022 Microsoft.  All rights reserved.


   Your language Nederlands (België) (nl-BE) is not supported. Continue in English?

   See this for more information: https://docs.microsoft.com/sql/sql-server/install/local-language-versions-in-sql-server


   For more information use /? or /Help.
   Installer failed with exit code: 1009
   ```

   ```Installing the correct language pack ...```
   ![002_english_language_pack](img/002_english_language_pack.PNG)

   ```bash
   Microsoft (R) SQL Server Installer
   Copyright (c) 2022 Microsoft.  All rights reserved.

   Operation finished with result: Success

   Installation has completed successfully!
   INSTANCE NAME
         SQLEXPRESS01

   SQL ADMINISTRATORS
         FUJITSUWIN\benny

   FEATURES INSTALLED
         SQLENGINE

   VERSION
         16.0.1000.6, RTM

   CONNECTION STRING
         Server=localhost\SQLEXPRESS01;Database=master;Trusted_Connection=True;

   SQL SERVER INSTALL LOG FOLDER
         C:\Program Files\Microsoft SQL Server\160\Setup Bootstrap\Log\20241015_104420

   INSTALLATION MEDIA FOLDER
         C:\SQL2022\Express_ENU

   INSTALLATION RESOURCES FOLDER
         C:\Program Files\Microsoft SQL Server\160\SSEI\Resources

   Successfully installed
   ```

- SSMS

   ```bash
   PS C:\Windows\system32> winget install --id Microsoft.SQLServerManagementStudio --source winget
   Found Microsoft SQL Server Management Studio [Microsoft.SQLServerManagementStudio] Version 20.2
   This application is licensed to you by its owner.
   Microsoft is not responsible for, nor does it grant any licenses to, third-party packages.
   Downloading https://download.microsoft.com/download/9/b/e/9bee9f00-2ee2-429a-9462-c9bc1ce14c28/SSMS-Setup-ENU.exe
   ██████████████████████████████   473 MB /  473 MB
   Successfully verified installer hash
   Starting package install...
   Successfully installed
   ```

   ![004_ssms](img/004_ssms.PNG)

   `Connecting with SSMS to verify running SQL Server`

   ![005_connect](img/005_connect.PNG)

   `Note: trust the certificate or else ...`

   ![007_certificate](img/007_certificate.PNG)

   ![006_connected](img/006_connected.PNG)

## How to run in development

> These steps assume that you have a SQL Server instance running on your machine. If not, you can use the [SQL Server Docker image](https://hub.docker.com/_/microsoft-mssql-server) to run one. Make sure to set the correct connection string of the SQL Server instance in `src/Server/appsettings.Development.json`.

1. Clone the repository

```bash
benny@fujitsuwin MINGW64 /c/DATA/GIT/DEVOPS
$ git clone https://github.com/HoGentTIN/p3ops-demo-app.git
Cloning into 'p3ops-demo-app'...
remote: Enumerating objects: 184, done.
remote: Counting objects: 100% (37/37), done.
remote: Compressing objects: 100% (31/31), done.
remote: Total 184 (delta 13), reused 6 (delta 6), pack-reused 147 (from 1)
Receiving objects: 100% (184/184), 55.83 KiB | 985.00 KiB/s, done.
Resolving deltas: 100% (38/38), done.

benny@fujitsuwin MINGW64 /c/DATA/GIT/DEVOPS
$ mv p3ops-demo-app/ p3ops-demo-app-BennyClemmens/

benny@fujitsuwin MINGW64 /c/DATA/GIT/DEVOPS/p3ops-demo-app-BennyClemmens (main)
$ git remote remove origin

benny@fujitsuwin MINGW64 /c/DATA/GIT/DEVOPS/p3ops-demo-app-BennyClemmens (main)
$ git remote add origin https://github.com/BennyClemmens/p3ops-demo-app-BennyClemmens.git

benny@fujitsuwin MINGW64 /c/DATA/GIT/DEVOPS/p3ops-demo-app-BennyClemmens (main)
$ git push -u origin
fatal: The current branch main has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin main

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.


benny@fujitsuwin MINGW64 /c/DATA/GIT/DEVOPS/p3ops-demo-app-BennyClemmens (main)
$ git push --set-upstream origin main
Enumerating objects: 184, done.
Counting objects: 100% (184/184), done.
Delta compression using up to 4 threads
Compressing objects: 100% (141/141), done.
Writing objects: 100% (184/184), 55.84 KiB | 55.84 MiB/s, done.
Total 184 (delta 38), reused 184 (delta 38), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (38/38), done.
To https://github.com/BennyClemmens/p3ops-demo-app-BennyClemmens.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

```bash
benny@fujitsuwin MINGW64 /c/DATA/GIT/DEVOPS/p3ops-demo-app-BennyClemmens (main)
$ cat src/Server/appsettings.Development.json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "ConnectionStrings": {
    "SqlDatabase": "Server=(localdb)\\mssqllocaldb;Database=SportStore;Trusted_Connection=True;"
  }
}
```

```bash
benny@fujitsuwin MINGW64 /c/DATA/GIT/DEVOPS/p3ops-demo-app-BennyClemmens (main)
$ cat src/Server/appsettings.Development.json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "ConnectionStrings": {
    "SqlDatabase": "Server=localhost\\SQLEXPRESS01;Database=master;Trusted_Connection=True;"
  }
}
```

2. Restore the packages: `dotnet restore src/Server/Server.csproj`
3. Start the server: `dotnet run watch --project src/Server/Server.csproj`

## How to run in production

1. Clone the repository
2. Restore the packages: `dotnet restore src/Server/Server.csproj`
3. Build the server: `dotnet build src/Server/Server.csproj`
4. Publish the server: `dotnet publish src/Server/Server.csproj -c Release -o publish`
5. Make sure the following environment variables are set:
   - `DOTNET_ENVIRONMENT`: environment name, e.g. `Production`
   - `DOTNET_ConnectionStrings__SqlDatabase`: connection string to the SQL Server database
6. Start the server: `dotnet publish/Server.dll`

## How to test

> No database is required to run the unit tests.

1. Clone the repository
2. Restore the packages: `dotnet restore src/Server/Server.csproj` and `dotnet restore tests/Domain.Tests/Domain.Tests.csproj`
3. Run the unit tests for the domain: `dotnet test tests/Domain.Tests/Domain.Tests.csproj`
