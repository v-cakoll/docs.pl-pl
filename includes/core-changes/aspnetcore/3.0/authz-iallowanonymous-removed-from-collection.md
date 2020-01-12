---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901662"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="6bacf-101">Autoryzacja: Usunięto IAllowAnonymous z AuthorizationFilterContext. filters</span><span class="sxs-lookup"><span data-stu-id="6bacf-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="6bacf-102">Począwszy od ASP.NET Core 3,0, MVC nie dodaje [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) dla atrybutów [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) , które zostały odnalezione na kontrolerach i metodach akcji.</span><span class="sxs-lookup"><span data-stu-id="6bacf-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="6bacf-103">Ta zmiana jest rozwiązywana lokalnie w przypadku pochodnych <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, ale jest to istotna zmiana dla implementacji <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> i <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter>.</span><span class="sxs-lookup"><span data-stu-id="6bacf-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="6bacf-104">Takie implementacje opakowane w atrybucie [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) są [popularnym](https://stackoverflow.com/a/41348219/608220) i obsługiwanym sposobem na osiągnięcie silnie wpisanej autoryzacji opartej na atrybutach, gdy wymagane jest wymaganie zarówno konfiguracji, jak i iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="6bacf-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6bacf-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6bacf-105">Version introduced</span></span>

<span data-ttu-id="6bacf-106">3.0</span><span class="sxs-lookup"><span data-stu-id="6bacf-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6bacf-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="6bacf-107">Old behavior</span></span>

<span data-ttu-id="6bacf-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> pojawił się w kolekcji [AuthorizationFilterContext. filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) .</span><span class="sxs-lookup"><span data-stu-id="6bacf-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="6bacf-109">Testowanie obecności interfejsu było prawidłowym podejściem do przesłonięcia lub wyłączenia filtru na poszczególnych metodach kontrolera.</span><span class="sxs-lookup"><span data-stu-id="6bacf-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6bacf-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="6bacf-110">New behavior</span></span>

<span data-ttu-id="6bacf-111">`IAllowAnonymous` nie pojawia się już w kolekcji `AuthorizationFilterContext.Filters`.</span><span class="sxs-lookup"><span data-stu-id="6bacf-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="6bacf-112">implementacje `IAsyncAuthorizationFilter`, które są zależne od starych zachowań, zwykle powodują sporadyczne nieautoryzowane żądania HTTP 401 lub żądania HTTP 403.</span><span class="sxs-lookup"><span data-stu-id="6bacf-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6bacf-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="6bacf-113">Reason for change</span></span>

<span data-ttu-id="6bacf-114">W ASP.NET Core 3,0 wprowadzono nową strategię routingu punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="6bacf-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6bacf-115">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="6bacf-115">Recommended action</span></span>

<span data-ttu-id="6bacf-116">Wyszukaj w metadanych punktu końcowego `IAllowAnonymous`.</span><span class="sxs-lookup"><span data-stu-id="6bacf-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="6bacf-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6bacf-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="6bacf-118">Przykład tej techniki jest widoczny w [tej metodzie HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span><span class="sxs-lookup"><span data-stu-id="6bacf-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="6bacf-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6bacf-119">Category</span></span>

<span data-ttu-id="6bacf-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6bacf-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6bacf-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6bacf-121">Affected APIs</span></span>

<span data-ttu-id="6bacf-122">Brak</span><span class="sxs-lookup"><span data-stu-id="6bacf-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
