---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901662"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Autoryzacja: IAllowAnonymous usunięte z AuthorizationFilterContext.Filters

Od ASP.NET Core 3.0, MVC nie dodaje [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) dla [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) atrybuty, które zostały wykryte na kontrolerach i metody akcji. Ta zmiana jest skierowana lokalnie na instrumenty <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>pochodne <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> , ale jest to przełomowa zmiana dla i implementacji. Takie implementacje opakowane w [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) atrybut są [popularnym](https://stackoverflow.com/a/41348219/608220) i obsługiwany sposób osiągnięcia silnie typizowana autoryzacja oparta na atrybutach, gdy wymagane są zarówno konfiguracji i zależności iniekcji.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>w [kolekcji AuthorizationFilterContext.Filters.](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) Testowanie obecności interfejsu było prawidłowym podejściem do zastępowania lub wyłączania filtru na poszczególnych metodach kontrolera.

#### <a name="new-behavior"></a>Nowe zachowanie

`IAllowAnonymous`nie są już `AuthorizationFilterContext.Filters` wyświetlane w kolekcji. `IAsyncAuthorizationFilter`implementacje, które są zależne od starego zachowania zazwyczaj powodują sporadyczne HTTP 401 Nieautoryzowane lub HTTP 403 Zabronione odpowiedzi.

#### <a name="reason-for-change"></a>Przyczyna zmiany

W ASP.NET Core 3.0 wprowadzono nową strategię routingu punktów końcowych.

#### <a name="recommended-action"></a>Zalecana akcja

Wyszukaj metadane punktu `IAllowAnonymous`końcowego w poszukiwaniu . Przykład:

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Przykład tej techniki jest widoczny w [tej HasAllowAnonymous metody](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
