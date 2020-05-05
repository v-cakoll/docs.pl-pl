---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901662"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Autoryzacja: Usunięto IAllowAnonymous z AuthorizationFilterContext. filters

Począwszy od ASP.NET Core 3,0, MVC nie dodaje [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) dla atrybutów [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) , które zostały odnalezione na kontrolerach i metodach akcji. Ta zmiana dotyczy lokalnie dla pochodnych <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, ale jest to istotna zmiana dla <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> i <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementacji. Takie implementacje opakowane w atrybucie [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) są [popularnym](https://stackoverflow.com/a/41348219/608220) i obsługiwanym sposobem na osiągnięcie silnie wpisanej autoryzacji opartej na atrybutach, gdy wymagane jest wymaganie zarówno konfiguracji, jak i iniekcji zależności.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>pojawił się w kolekcji [AuthorizationFilterContext. filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) . Testowanie obecności interfejsu było prawidłowym podejściem do przesłonięcia lub wyłączenia filtru na poszczególnych metodach kontrolera.

#### <a name="new-behavior"></a>Nowe zachowanie

`IAllowAnonymous`nie pojawia się już w `AuthorizationFilterContext.Filters` kolekcji. `IAsyncAuthorizationFilter`implementacje zależne od starych zachowań zwykle powodują sporadyczne nieautoryzowane żądania HTTP 401 lub żądania HTTP 403.

#### <a name="reason-for-change"></a>Przyczyna zmiany

W ASP.NET Core 3,0 wprowadzono nową strategię routingu punktów końcowych.

#### <a name="recommended-action"></a>Zalecana akcja

Przeszukaj metadane punktu końcowego `IAllowAnonymous`dla programu. Przykład:

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Przykład tej techniki jest widoczny w [tej metodzie HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
