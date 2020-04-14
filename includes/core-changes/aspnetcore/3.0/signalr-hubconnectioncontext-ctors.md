---
ms.openlocfilehash: 6be98e7ced6608ba0793c635adfe61c8b1a7e9d9
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274776"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a>SignalR: HubConnectionContext konstruktory zmienione

`HubConnectionContext` Konstruktory SignalR zmienił się zaakceptować typ opcji, a nie wiele parametrów, do przyszłości opcje dodawania. Ta zmiana zastępuje dwa konstruktory z jednego konstruktora, który akceptuje typ opcji.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`HubConnectionContext`posiada dwa konstruktory:

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a>Nowe zachowanie

Dwa konstruktory zostały usunięte i zastąpione jednym konstruktorem:

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a>Powód zmiany

Nowy konstruktor używa nowego obiektu opcji. W związku z `HubConnectionContext` tym funkcje mogą być rozszerzane w przyszłości bez wprowadzania większej liczby konstruktorów i wprowadzania zmian.

#### <a name="recommended-action"></a>Zalecana akcja

Zamiast używać następującego konstruktora:

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

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
