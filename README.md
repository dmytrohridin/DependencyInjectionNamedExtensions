# .NET Core Dependency Injection Named Extensions
Extensions for [.NET Core](https://github.com/dotnet/extensions/) Dependency Injection container, that allow to resolve dependencies by key. 

![.NET Core](https://github.com/dmytrohridin/DependencyInjectionNamedExtensions/workflows/.NET%20Core/badge.svg?branch=master)

## Why?

Current implementation of .NET Core Dependency Injection container does not support registration and resolving dependencies by name or key.

## Installation

TODO: Add description after final nuget package will be ready

## Usage

Register named services with ```IServiceCollection```
```csharp
services.AddScoped<IEventBus, AzureServiceBusPersistance, string>("azureServiceBus");
services.AddScoped<IEventBus, RabbitMQServicePersistance, string>("rabbitMQ");
```

Inject ```IServiceProvider``` interface where you need to resolve dependency and call ```GetService``` method with key provided
```csharp
var eventBus = serviceProvider.GetService<IEventBus, string>(eventBusKey);
```

### Note
Not only ```string``` can be used as type for key parameter. All extensions is parameterized, so ```Enum```, ```Guid``` or another types can be used as key.  

## Dependencies
This extensions is build with .NET Standart 2.0 and depends on [Microsoft.Extensions.DependencyInjection](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection) starting from version 3.1.2.

## Q&A
If you have any questions or proposals - please create issue or PR. 
