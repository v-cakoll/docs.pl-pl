---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901690"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: Typy "Pubternal" zmienione na wewnętrzne

W ASP.NET Core 3.0 wszystkie typy "pubternal" w MVC zostały zaktualizowane, aby być `public` w obsługiwanej przestrzeni nazw lub `internal` w stosownych przypadkach.

#### <a name="change-description"></a>Zmień opis

W ASP.NET Core typy "pubternal" `public` są deklarowane `.Internal`jako, ale znajdują się w przestrzeni nazw -sufiks. Chociaż te `public`typy są , nie mają żadnych zasad wsparcia i podlegają przełomowym zmianom. Niestety, przypadkowe użycie tych typów było powszechne, co spowodowało przełomowe zmiany w tych projektach i ograniczyło możliwość utrzymania struktury.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Niektóre typy w `public` MVC `.Internal` były, ale w przestrzeni nazw. Tego typu nie miały żadnych zasad wsparcia i podlegały przełomowym zmianom.

#### <a name="new-behavior"></a>Nowe zachowanie

Wszystkie takie typy są aktualizowane w `public` obsługiwanej przestrzeni `internal`nazw lub oznaczone jako .

#### <a name="reason-for-change"></a>Przyczyna zmiany

Przypadkowe użycie typów "pubternal" było powszechne, co spowodowało zerwanie zmian w tych projektach i ograniczenie możliwości utrzymania struktury.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli używasz typów, które stały `public` się naprawdę i zostały przeniesione do nowego, obsługiwanego obszaru nazw, zaktualizuj odwołania, aby dopasować je do nowych obszarów nazw.

Jeśli używasz typów, które zostały `internal`oznaczone jako , musisz znaleźć alternatywę. Wcześniej typy "pubternal" nigdy nie były obsługiwane do użytku publicznego. Jeśli istnieją określone typy w tych przestrzeniach nazw, które mają kluczowe znaczenie dla aplikacji, należy zgłosić problem w [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues). Można zastanowić się nad dokonaniem `public`żądanych typów .

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Ta zmiana obejmuje typy w następujących obszarach nazw:

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
