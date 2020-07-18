---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441556"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="684b2-101">Autoryzacja: zasób w routingu punktu końcowego jest obiektem HttpContext</span><span class="sxs-lookup"><span data-stu-id="684b2-101">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="684b2-102">W przypadku korzystania z routingu punktów końcowych w ASP.NET Core 3,1, zasób używany do autoryzacji jest punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="684b2-102">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="684b2-103">Takie podejście było niewystarczające do uzyskania dostępu do danych trasy ( <xref:Microsoft.AspNetCore.Routing.RouteData> ).</span><span class="sxs-lookup"><span data-stu-id="684b2-103">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="684b2-104">Wcześniej w MVC <xref:Microsoft.AspNetCore.Http.HttpContext> zasób został przekazano, co umożliwia dostęp do punktu końcowego ( <xref:Microsoft.AspNetCore.Http.Endpoint> ) i danych trasy.</span><span class="sxs-lookup"><span data-stu-id="684b2-104">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="684b2-105">Ta zmiana gwarantuje, że zasób przeszedł do autoryzacji jest zawsze `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="684b2-105">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="684b2-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="684b2-106">Version introduced</span></span>

<span data-ttu-id="684b2-107">5,0 wersja zapoznawcza 7</span><span class="sxs-lookup"><span data-stu-id="684b2-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="684b2-108">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="684b2-108">Old behavior</span></span>

<span data-ttu-id="684b2-109">W przypadku używania routingu punktów końcowych i atrybutów autoryzacji oprogramowania pośredniczącego ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) lub [[autoryzuje]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) zasób przeszedł do autoryzacji jest zgodnym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="684b2-109">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="684b2-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="684b2-110">New behavior</span></span>

<span data-ttu-id="684b2-111">Routing punktów końcowych przekazuje `HttpContext` do autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="684b2-111">Endpoint routing passes the `HttpContext` to authorization.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="684b2-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="684b2-112">Reason for change</span></span>

<span data-ttu-id="684b2-113">Możesz przejść do punktu końcowego z `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="684b2-113">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="684b2-114">Nie ma jednak możliwości uzyskania od punktu końcowego do elementów, takich jak dane trasy.</span><span class="sxs-lookup"><span data-stu-id="684b2-114">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="684b2-115">Nastąpiła utrata funkcjonalności z poziomu routingu spoza punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="684b2-115">There was a loss in functionality from non-endpoint routing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="684b2-116">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="684b2-116">Recommended action</span></span>

<span data-ttu-id="684b2-117">Jeśli aplikacja korzysta z zasobu punktu końcowego, wywołaj polecenie, <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> `HttpContext` Aby kontynuować dostęp do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="684b2-117">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="684b2-118">W ASP.NET Core 5,0 wersji zapoznawczej 8 i nowszych można przywrócić stare zachowanie przy użyciu programu <xref:System.AppContext.SetSwitch%2A> .</span><span class="sxs-lookup"><span data-stu-id="684b2-118">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="684b2-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="684b2-119">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a><span data-ttu-id="684b2-120">Kategoria</span><span class="sxs-lookup"><span data-stu-id="684b2-120">Category</span></span>

<span data-ttu-id="684b2-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="684b2-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="684b2-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="684b2-122">Affected APIs</span></span>

<span data-ttu-id="684b2-123">Brak</span><span class="sxs-lookup"><span data-stu-id="684b2-123">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
