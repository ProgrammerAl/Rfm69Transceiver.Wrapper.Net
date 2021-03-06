# Rfm69Transceiver.Wrapper.Net 

[![Build status](https://dev.azure.com/ProgrammerAl/OSS/_apis/build/status/Rfm69Transceiver.Wrapper.Net)](https://dev.azure.com/ProgrammerAl/OSS/_build/latest?definitionId=30)

![](https://sonarcloud.io/api/project_badges/measure?project=Rfm69Transceiver.Wrapper.Net&metric=alert_status)

This repo is a .NET Wrapper for working with an RFM69 Transceiver on a Raspberry Pi. This is a wrapper around the code in https://github.com/ProgrammerAl/RaspberryPiRfm69.RaspberryPi repository. The compiled native library from that repo is already included in this one. Ys, it's not reccomended. But there won't be a lot of changes to this repo, so it's fine. 

The NuGet package is hosted [here](https://www.nuget.org/packages/ProgrammerAl.HardwareSpecific.RF.Rfm69Transceiver).

## How to Compile and Run
The Demo project has an example on getting started with sending and receiving messages. If you would like to compile that project, use the following instructions. The instructions publish a self-contained .NET Core application, but you will still need to have the .NET Core runtime installed on your Raspberry Pi. If you have not already done so, download and install the runtime for the Linux ARM32 verion from https://www.microsoft.com/net/download. I've only run the below instructions from a Windows 10 machine, but they should work on any machine that supports .NET Core.

1. Open command line to root directory of Rfm69Transceiver.sln solution file
1. To compile a debug version run: dotnet publish ./Demo -c Debug -r linux-arm --self-contained
1. Or, to compile a release version run: dotnet publish ./Demo -c Release -r linux-arm --self-contained
1. Navigate to the output directory from your chosen publish command: `~/Demo/bin/<debug or release>/netcoreapp2.1/linux-arm/publish`
1. Copy all files in the publish folder and paste them to your desired location on a raspberry Pi (ex: /home/pi/Desktop/Practice)
1. On the Raspberry Pi, open a terminal command line window and navigate to the folder you copy/pasted the above files to
1. Run the demo project with the command: dotnet ProgrammerAl.HardwareSpecific.RF.Demo.dll

Important Notes:
1. This is hardware specific and will only work on a Raspberry Pi with an RFM69 Transceiver properly wired up.
1. If you are using the NuGet package, you need to manually force the RaspberryPiRfm69Wrapper.o file to be output as part of a build. If you're using Visual Studio, right-click the file and click properties. Then make sure the Copy to Output Directory option is set to Copy Always or Copy If Newer. If you are not using Visual Studio, you will need to manually edit your csproj file to copy the file to the output directory.
