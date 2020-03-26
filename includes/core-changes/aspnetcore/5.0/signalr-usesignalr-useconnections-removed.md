---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291637"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="cdb7c-101">SignalR: UseSignalR i UseConnections metody usunięte</span><span class="sxs-lookup"><span data-stu-id="cdb7c-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="cdb7c-102">W ASP.NET Core 3.0 SignalR przyjął routing punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="cdb7c-103">W ramach tej <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>zmiany, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, i niektóre powiązane metody zostały oznaczone jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="cdb7c-104">W ASP.NET Core 5.0 te przestarzałe metody zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="cdb7c-105">Aby uzyskać pełną listę metod, zobacz [interfejsy API, których dotyczy problem](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="cdb7c-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="cdb7c-106">Aby do dyskusji na ten temat, zobacz [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="cdb7c-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cdb7c-107">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="cdb7c-107">Version introduced</span></span>

<span data-ttu-id="cdb7c-108">5.0 Wersja zapoznawcza 3</span><span class="sxs-lookup"><span data-stu-id="cdb7c-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cdb7c-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="cdb7c-109">Old behavior</span></span>

<span data-ttu-id="cdb7c-110">Koncentratory signalr i programy obsługi połączeń mogą być `UseSignalR` rejestrowane `UseConnections` w potoku oprogramowania pośredniczącego przy użyciu lub metod.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cdb7c-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="cdb7c-111">New behavior</span></span>

<span data-ttu-id="cdb7c-112">Koncentratory SignalR i programy obsługi <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> połączeń <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> powinny <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> być <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>rejestrowane przy użyciu i metody rozszerzenia na .</span><span class="sxs-lookup"><span data-stu-id="cdb7c-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cdb7c-113">Powód zmiany</span><span class="sxs-lookup"><span data-stu-id="cdb7c-113">Reason for change</span></span>

<span data-ttu-id="cdb7c-114">Stare metody miały niestandardową logikę routingu, która nie wchodziła w interakcje z innymi składnikami routingu w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="cdb7c-115">W ASP.NET Core 3.0 wprowadzono nowy system routingu ogólnego przeznaczenia, zwany routingiem punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="cdb7c-116">Routing punktu końcowego umożliwił SignalR interakcję z innymi składnikami routingu.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="cdb7c-117">Przełączenie do tego modelu umożliwia użytkownikom realizację pełnych zalet routingu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="cdb7c-118">W związku z tym stare metody zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cdb7c-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="cdb7c-119">Recommended action</span></span>

<span data-ttu-id="cdb7c-120">Usuń kod, `UseSignalR` `UseConnections` który wywołuje lub `Startup.Configure` z metody projektu.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="cdb7c-121">Wymień go `MapHub` `MapConnectionHandler`na połączenia lub, odpowiednio, w `UseEndpoints`treści połączenia do .</span><span class="sxs-lookup"><span data-stu-id="cdb7c-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="cdb7c-122">Przykład:</span><span class="sxs-lookup"><span data-stu-id="cdb7c-122">For example:</span></span>

<span data-ttu-id="cdb7c-123">**Stary kod:**</span><span class="sxs-lookup"><span data-stu-id="cdb7c-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="cdb7c-124">**Nowy kod:**</span><span class="sxs-lookup"><span data-stu-id="cdb7c-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="cdb7c-125">Ogólnie `MapHub` rzecz biorąc, poprzednie i `MapConnectionHandler` połączenia mogą być `UseSignalR` przesyłane bezpośrednio z ciała i `UseConnections` do `UseEndpoints` niej z małą lub żadną zmianą.</span><span class="sxs-lookup"><span data-stu-id="cdb7c-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="cdb7c-126">Kategoria</span><span class="sxs-lookup"><span data-stu-id="cdb7c-126">Category</span></span>

<span data-ttu-id="cdb7c-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cdb7c-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cdb7c-128">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cdb7c-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
