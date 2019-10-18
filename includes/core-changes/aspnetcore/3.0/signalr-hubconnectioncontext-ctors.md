---
ms.openlocfilehash: 8979b7ffc09726c6588fe3ba60b916202697648f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522686"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="99752-101">Sygnalizacja: zmieniono konstruktory HubConnectionContext</span><span class="sxs-lookup"><span data-stu-id="99752-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="99752-102">Konstruktory `HubConnectionContext` zostały zmienione w celu zaakceptowania typu opcji, a nie wielu parametrów, do dalszej próby dodania opcji.</span><span class="sxs-lookup"><span data-stu-id="99752-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="99752-103">Ta zmiana zastępuje dwa konstruktory z pojedynczym konstruktorem akceptującym typ opcji.</span><span class="sxs-lookup"><span data-stu-id="99752-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="99752-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="99752-104">Version introduced</span></span>

<span data-ttu-id="99752-105">3.0</span><span class="sxs-lookup"><span data-stu-id="99752-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="99752-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="99752-106">Old behavior</span></span>

<span data-ttu-id="99752-107">`HubConnectionContext` ma dwa konstruktory:</span><span class="sxs-lookup"><span data-stu-id="99752-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="99752-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="99752-108">New behavior</span></span>

<span data-ttu-id="99752-109">Dwa konstruktory zostały usunięte i zastąpione jednym konstruktorem:</span><span class="sxs-lookup"><span data-stu-id="99752-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="99752-110">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="99752-110">Reason for change</span></span>

<span data-ttu-id="99752-111">Nowy Konstruktor używa nowego obiektu options.</span><span class="sxs-lookup"><span data-stu-id="99752-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="99752-112">W związku z tym funkcje `HubConnectionContext` mogą być rozwinięte w przyszłości bez tworzenia większej liczby konstruktorów i istotnej zmiany.</span><span class="sxs-lookup"><span data-stu-id="99752-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="99752-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="99752-113">Recommended action</span></span>

<span data-ttu-id="99752-114">Zamiast korzystać z następującego konstruktora:</span><span class="sxs-lookup"><span data-stu-id="99752-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="99752-115">Użyj następującego konstruktora:</span><span class="sxs-lookup"><span data-stu-id="99752-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="99752-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="99752-116">Category</span></span>

<span data-ttu-id="99752-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="99752-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="99752-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="99752-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
