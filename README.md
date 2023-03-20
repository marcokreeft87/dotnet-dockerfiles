# dotnet-dockerfiles
Windows based DockerFiles that generate Docker images to use for testing your application


# RobotFramework
Generates an image based on Windows that can run [Robotframework](https://robotframework.org) test files.

# .NET Framework
Generates an image based on Windows Server that has MSSQL Server installed with IIS to run your .NET Framework applicatien in Docker

Can be build with the following command:

```
docker build -f Dockerfile.baseImage --build-arg BASE=ltsc2019 --build-arg DEV_ISO=https://download.microsoft.com/download/7/c/1/7c14e92e-bdcb-4f89-b7cf-93543e7112d1/SQLServer2019-x64-ENU-Dev.iso --build-arg CU=https://download.microsoft.com/download/6/e/7/6e72dddf-dfa4-4889-bc3d-e5d3a0fd11ce/SQLServer2019-KB5023049-x64.exe --build-arg VERSION=15.0.4298.1 --build-arg TYPE=dev -t aspnetmssql_dev .
```

Where the BASE arg is the version of the base Windows Server image. The DEV_ISO argument is the iso file to install SQL Server, CU arg (optional) is the url to the patch you want to be installed on SQL Server. 
The version build arg is the version of SQL Server and the TYPE build arg defines if you want to install an named instance of the default instance.
