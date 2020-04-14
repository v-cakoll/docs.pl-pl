---
ms.openlocfilehash: 6be98e7ced6608ba0793c635adfe61c8b1a7e9d9
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274776"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="c63ac-101">SignalR: HubConnectionContext konstruktory zmienione</span><span class="sxs-lookup"><span data-stu-id="c63ac-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="c63ac-102">`HubConnectionContext` Konstruktory SignalR zmienił się zaakceptować typ opcji, a nie wiele parametrów, do przyszłości opcje dodawania.</span><span class="sxs-lookup"><span data-stu-id="c63ac-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="c63ac-103">Ta zmiana zastępuje dwa konstruktory z jednego konstruktora, który akceptuje typ opcji.</span><span class="sxs-lookup"><span data-stu-id="c63ac-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c63ac-104">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="c63ac-104">Version introduced</span></span>

<span data-ttu-id="c63ac-105">3.0</span><span class="sxs-lookup"><span data-stu-id="c63ac-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c63ac-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="c63ac-106">Old behavior</span></span>

<span data-ttu-id="c63ac-107">`HubConnectionContext`posiada dwa konstruktory:</span><span class="sxs-lookup"><span data-stu-id="c63ac-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="c63ac-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="c63ac-108">New behavior</span></span>

<span data-ttu-id="c63ac-109">Dwa konstruktory zostały usunięte i zastąpione jednym konstruktorem:</span><span class="sxs-lookup"><span data-stu-id="c63ac-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="c63ac-110">Powód zmiany</span><span class="sxs-lookup"><span data-stu-id="c63ac-110">Reason for change</span></span>

<span data-ttu-id="c63ac-111">Nowy konstruktor używa nowego obiektu opcji.</span><span class="sxs-lookup"><span data-stu-id="c63ac-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="c63ac-112">W związku z `HubConnectionContext` tym funkcje mogą być rozszerzane w przyszłości bez wprowadzania większej liczby konstruktorów i wprowadzania zmian.</span><span class="sxs-lookup"><span data-stu-id="c63ac-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c63ac-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="c63ac-113">Recommended action</span></span>

<span data-ttu-id="c63ac-114">Zamiast używać następującego konstruktora:</span><span class="sxs-lookup"><span data-stu-id="c63ac-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="c63ac-115">Użyj następującego konstruktora:</span><span class="sxs-lookup"><span data-stu-id="c63ac-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="c63ac-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="c63ac-116">Category</span></span>

<span data-ttu-id="c63ac-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c63ac-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c63ac-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c63ac-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
