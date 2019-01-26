---
layout: page
title: Logging w/log4net
excerpt: This article will detail how to setup log4net within your Visual Studio's project.
cover: /assets/covers/pexels-photo-1112048.jpeg
categories: [tutorials]
tags: [logging, visual-studios, pragmatic, programming]
difficulty: easy
---

# Introduction

This article will detail how to setup log4net within your Visual Studio - C# .Net project. The [log4net manual](https://logging.apache.org/log4net/release/manual/introduction.html)  can be a bit wordy, so I'll try to break it down into three steps: Installation, Configuration, and Usage.

## Setup

#### Installation

* Create or open an existing project.
* Right-click the project root from within the **Solution Explorer** tab.
* Select *Manage NuGet Packages...* from the drop-down menu.
* Search for *"log4net"* in the **Browse** tab.
* Select log4net from the list and *Install*.

NuGet will now download and install the library files so that you project can access them at runtime.

#### Configuration

Add the following to the bottom of your `Properties/AssemblyInfo.cs` file. This will tell log4net to parse the `App.config` (or `Web.config`) file.

```csharp
[assembly: log4net.Config.XmlConfigurator(Watch = true)]
```

Next, open the `App.config` file.

> Note: You may need to create the `App.config` file if it doesn't already exist.

You must first register the `<log4net>` otherwise  config file parser won't know how to process it.

```xml
<configSections>
    <section name="log4net" type="log4net.Config.Log4NetConfigurationSectionHandler, log4net" />
  </configSections>
```

Now, start another root `<log4net>` (now that it's been registered from above). In order for log4net to know where to log to (i.e. output destination) we'll first need to set up at least one `<appender>`. Appenders can be thought of as output destinations.

```xml
<log4net>
    <appender name="TraceAppender" type="log4net.Appender.TraceAppender">
      <layout type="log4net.Layout.PatternLayout">
        <conversionPattern value="[%date] %level (%logger:%line) - %message%newline" />
      </layout>
    </appender>
    ...
    <root>
      <level value="INFO" />
      <appender-ref ref="TraceAppender" />
    </root>
</log4net>
```

The `<root>` element is optional. You can use it to set sets configurations for the default logging level.

For more information regarding configurations see [More On Configurations](#More On Configurations).

#### Usage

Use the code snippet below as reference for using logging in your own project.

* It's recommended that every class gets it's own logger.
* `_logger` has several methods to call varying log levels (i.e. `info`, `debug`).

```csharp
using System;
using log4net;

namespace Project
{
    public static class Program
    {
    	private static readonly ILog _logger = LogManager.GetLogger(typeof(Screen));

        static void Main()
        {
        	_logger.Info("Testing!!");
        }
    }
}
```

## More On Configurations

#### Logging Levels

| Level | Description                                          |
| ----- | ---------------------------------------------------- |
| OFF   | Log nothing; essentially used to disable an Appender |
| FATAL | Issue caused the program to crashed.                 |
| ERROR | Problem occurred, but didn't yet crash the program.  |
| WARN  | Potential problem.                                   |
| INFO  | Informational message.                               |
| DEBUG | Used strictly for debugging purposes.                |
| ALL   | Log everything regardless of level.                  |
{: .table .table-striped }

#### Layout - ConversionPattern

These patterns are used to format the log output.

| Pattern    | Details                                                |
| ---------- | ------------------------------------------------------ |
| `%date`    | Logs date of logging event in the local time zone.     |
| `%file`    | Logs the file name of where the logging event occured. |
| `%line`    | Logs the line number where the logging event occurred. |
| `%method`  | Logs the method  where the logging event occurred.     |
| `%level`   | Level specified for event.                             |
| `%message` | Message passed through the log event.                  |
| `%newline` | Newline character.                                     |
{: .table .table-striped }

> You can reference the list below or see a full listing [here](https://logging.apache.org/log4net/release/sdk/html/T_log4net_Layout_PatternLayout.htm).

#### Appenders

| Type                | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| AdoNetAppender      | Writes log events to a database.                             |
| FileAppender        | Writes log events to a file you specify.                     |
| RollingFileAppender | Writes log events to a file you specify, while performing archived file cleanup. |
| TraceAppender       | Writes log events to **Visual Studio**'s Output interface.   |
{: .table .table-striped }

> For a full list of Appenders [check here](https://logging.apache.org/log4net/release/manual/introduction.html#appenders).

## Conclusion

You should now have log4net setup and working. Check out the further reading below for more in-depth reading on the topic.

## Further Reading

* [log4net Online Manual](https://logging.apache.org/log4net/release/manual/introduction.html)
* [log4net - PatternLayout Class](https://logging.apache.org/log4net/release/sdk/html/T_log4net_Layout_PatternLayout.htm)
* [log4net - List of Appenders](https://logging.apache.org/log4net/release/manual/introduction.html#appenders)
* [log4net Tutorial - by Tim Corey](https://www.codeproject.com/Articles/140911/log-net-Tutorial)
* [The Art of Logging by Colin Eberhardt](https://www.codeproject.com/Articles/42354/The-Art-of-Logging)
