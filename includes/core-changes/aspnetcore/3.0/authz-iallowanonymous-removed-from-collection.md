---
ms.openlocfilehash: 89af89d3580fd1396335a0cd8964b46c13d7637e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344286"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Autoryzacja: Usunięto IAllowAnonymous z AuthorizationFilterContext. filters

Począwszy od ASP.NET Core 3,0, MVC nie dodaje [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) dla atrybutów [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) , które zostały odnalezione na kontrolerach i metodach akcji. Ta zmiana jest rozwiązywana lokalnie w przypadku pochodnych <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, ale jest to istotna zmiana dla implementacji <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> i <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter>. Takie implementacje opakowane w atrybucie [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) są [popularnym](https://stackoverflow.com/a/41348219/608220) i obsługiwanym sposobem na osiągnięcie silnie wpisanej autoryzacji opartej na atrybutach, gdy wymagane jest wymaganie zarówno konfiguracji, jak i iniekcji zależności.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> pojawił się w kolekcji [AuthorizationFilterContext. filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) . Testowanie obecności interfejsu było prawidłowym podejściem do przesłonięcia lub wyłączenia filtru na poszczególnych metodach kontrolera.

#### <a name="new-behavior"></a>Nowe zachowanie

`IAllowAnonymous` nie pojawia się już w kolekcji `AuthorizationFilterContext.Filters`. implementacje `IAsyncAuthorizationFilter`, które są zależne od starych zachowań, zwykle powodują sporadyczne nieautoryzowane żądania HTTP 401 lub żądania HTTP 403.

#### <a name="reason-for-change"></a>Przyczyna zmiany

W ASP.NET Core 3,0 wprowadzono nową strategię routingu punktów końcowych.

#### <a name="recommended-action"></a>Zalecane działanie

Wyszukaj w metadanych punktu końcowego `IAllowAnonymous`. Na przykład:

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Przykład tej techniki jest widoczny w [tej metodzie HasAllowAnonymous](https://github.com/aspnet/AspNetCore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
