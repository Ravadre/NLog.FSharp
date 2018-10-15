NLog.FSharp
===========

Simple F# helper for NLog

## Installation

 - [NuGet](https://www.nuget.org/packages/NLog.FSharp/)
   - Using the Package Manager Console:

     ```
      PM> Install-Package NLog.FSharp
     ```

   - Using [paket](https://fsprojects.github.io/Paket/):

     ```
      >./.paket/paket.exe add NLog.FSharp --project MyProject
     ```

## Examples

```
>open NLog.FSharp

>let log = new Logger()        // logger name is determined using the caller type
>let log = new Logger("mylog") // or use an explicit logger name
>let log = new Logger(logger)  // or any NLog.Logger

>let text = "Welcome"
>log.Info "Text:%s" text       // <- use formatted text

// use formatted input with any of these:
>log.{Trace, Debug, Info, Warn, Error, Fatal} "More than one number %M or %i" 3.0m 7

// or with exceptions
>let e, i = new System.Exception(), 3
>log.InfoException e "An exception has occurred %d times" i
```

More examples of formatted text in F# are available [here](https://fsharpforfunandprofit.com/posts/printf/).

## Configuration

For information on NLog configuration files, visit the [NLog wiki](https://github.com/nlog/NLog/wiki/Configuration-file).  Use this resource to determine what to log and where to log it when you need to capture output at runtime.

## Open Source

### Compile NLog.FSharp

Using the [`.NET Core`](https://www.microsoft.com/net/download) SDK (e.g. version 2.1.402):
```
.\.paket\paket.bootstrapper.exe
.\.paket\paket.exe restore
dotnet restore
dotnet build -c Release
```

### Publish NLog.FSharp to NuGet

Using the publishing `$key` provided by nuget:
```
dotnet nuget push **/*.nupkg -k $key -s https://api.nuget.org/v3/index.json
```