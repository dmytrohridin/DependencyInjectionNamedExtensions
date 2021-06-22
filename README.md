# .NET Core Dependency Injection Named Extensions
Extensions for [.NET Core](https://github.com/dotnet/extensions/) Dependency Injection container, that allow to resolve dependencies by key. 

![.NET Core](https://github.com/dmytrohridin/DependencyInjectionNamedExtensions/workflows/.NET%20Core/badge.svg?branch=master)
[![NuGet package](https://badge.fury.io/nu/DependencyInjection.Extensions.NamedDependencies.svg)](https://www.nuget.org/packages/DependencyInjection.Extensions.NamedDependencies/)

## Why?

Current implementation of .NET Core Dependency Injection container does not support registration and resolving dependencies by name or key.

## Installation

Can be installed via Nuget

```Install-Package DependencyInjection.Extensions.NamedDependencies```

or .NET CLI

```dotnet add package DependencyInjection.Extensions.NamedDependencies```

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
This extensions are built with .NET Standart 2.0 and depends on [Microsoft.Extensions.DependencyInjection](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection)

## Versioning
``` DependencyInjection.Extensions.NamedDependencies``` follows the versioning of the [Microsoft.Extensions.DependencyInjection](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection), since it's main dependency.

## Q&A
If you have any questions or proposals - please create issue or PR. 
