---
ms.openlocfilehash: 8cc2e1436059f92564d4c3ec534632674081ae75
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394004"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a>Sygnalizacja: zmieniono konstruktory HubConnectionContext

Konstruktory `HubConnectionContext` zostały zmienione w celu zaakceptowania typu opcji, a nie wielu parametrów, do dalszej próby dodania opcji. Ta zmiana zastępuje dwa konstruktory z pojedynczym konstruktorem akceptującym typ opcji.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`HubConnectionContext` ma dwa konstruktory:

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a>Nowe zachowanie

Dwa konstruktory zostały usunięte i zastąpione jednym konstruktorem:

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a>Przyczyna zmiany

Nowy Konstruktor używa nowego obiektu options. W związku z tym funkcje `HubConnectionContext` mogą być rozwinięte w przyszłości bez tworzenia większej liczby konstruktorów i istotnej zmiany.

#### <a name="recommended-action"></a>Zalecana akcja

Zamiast korzystać z następującego konstruktora:

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext, 
    keepAliveInterval: TimeSpan.FromSeconds(15), 
    loggerFactory, 
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

Użyj następującego konstruktora:

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
