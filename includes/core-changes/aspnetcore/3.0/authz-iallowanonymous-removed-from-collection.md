---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901662"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="efb3e-101">Autoryzacja: IAllowAnonymous usunięte z AuthorizationFilterContext.Filters</span><span class="sxs-lookup"><span data-stu-id="efb3e-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="efb3e-102">Od ASP.NET Core 3.0, MVC nie dodaje [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) dla [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) atrybuty, które zostały wykryte na kontrolerach i metody akcji.</span><span class="sxs-lookup"><span data-stu-id="efb3e-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="efb3e-103">Ta zmiana jest skierowana lokalnie na instrumenty <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>pochodne <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> , ale jest to przełomowa zmiana dla i implementacji.</span><span class="sxs-lookup"><span data-stu-id="efb3e-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="efb3e-104">Takie implementacje opakowane w [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) atrybut są [popularnym](https://stackoverflow.com/a/41348219/608220) i obsługiwany sposób osiągnięcia silnie typizowana autoryzacja oparta na atrybutach, gdy wymagane są zarówno konfiguracji i zależności iniekcji.</span><span class="sxs-lookup"><span data-stu-id="efb3e-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="efb3e-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="efb3e-105">Version introduced</span></span>

<span data-ttu-id="efb3e-106">3.0</span><span class="sxs-lookup"><span data-stu-id="efb3e-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="efb3e-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="efb3e-107">Old behavior</span></span>

<span data-ttu-id="efb3e-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>w [kolekcji AuthorizationFilterContext.Filters.](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A)</span><span class="sxs-lookup"><span data-stu-id="efb3e-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="efb3e-109">Testowanie obecności interfejsu było prawidłowym podejściem do zastępowania lub wyłączania filtru na poszczególnych metodach kontrolera.</span><span class="sxs-lookup"><span data-stu-id="efb3e-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="efb3e-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="efb3e-110">New behavior</span></span>

<span data-ttu-id="efb3e-111">`IAllowAnonymous`nie są już `AuthorizationFilterContext.Filters` wyświetlane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="efb3e-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="efb3e-112">`IAsyncAuthorizationFilter`implementacje, które są zależne od starego zachowania zazwyczaj powodują sporadyczne HTTP 401 Nieautoryzowane lub HTTP 403 Zabronione odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="efb3e-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="efb3e-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="efb3e-113">Reason for change</span></span>

<span data-ttu-id="efb3e-114">W ASP.NET Core 3.0 wprowadzono nową strategię routingu punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="efb3e-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="efb3e-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="efb3e-115">Recommended action</span></span>

<span data-ttu-id="efb3e-116">Wyszukaj metadane punktu `IAllowAnonymous`końcowego w poszukiwaniu .</span><span class="sxs-lookup"><span data-stu-id="efb3e-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="efb3e-117">Przykład:</span><span class="sxs-lookup"><span data-stu-id="efb3e-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="efb3e-118">Przykład tej techniki jest widoczny w [tej HasAllowAnonymous metody](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span><span class="sxs-lookup"><span data-stu-id="efb3e-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="efb3e-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="efb3e-119">Category</span></span>

<span data-ttu-id="efb3e-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="efb3e-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="efb3e-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="efb3e-121">Affected APIs</span></span>

<span data-ttu-id="efb3e-122">Brak</span><span class="sxs-lookup"><span data-stu-id="efb3e-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
