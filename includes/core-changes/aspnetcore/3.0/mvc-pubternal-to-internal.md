---
ms.openlocfilehash: 09fd95ba5f3aee59f2abdfbb4e64eb6202e2b873
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394035"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: typy "Pubternal" zostały zmienione na wewnętrzne

W ASP.NET Core 3,0 wszystkie typy "pubternal" w MVC zostały zaktualizowane do `public` w obsługiwanej przestrzeni nazw lub `internal`, zgodnie z potrzebami.

#### <a name="change-description"></a>Zmień opis

W ASP.NET Core typy "pubternal" są deklarowane jako `public`, ale znajdują się w @no__t przestrzeni nazw z sufiksem -1. Chociaż te typy są `public`, nie mają żadnych zasad pomocy technicznej i podlegają nieprzerwanym zmianom. Niestety, przypadkowe użycie tych typów było wspólne, co spowodowało istotne zmiany w tych projektach i ograniczenie możliwości utrzymania struktury.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Niektóre typy w MVC zostały `public`, ale w przestrzeni nazw `.Internal`. Te typy nie miały zasad pomocy technicznej i podlegają istotnym zmianom.

#### <a name="new-behavior"></a>Nowe zachowanie

Wszystkie takie typy są aktualizowane do `public` w obsługiwanej przestrzeni nazw lub oznaczone jako `internal`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Przypadkowe użycie typów "pubternal" jest wspólne, co skutkuje istotnymi zmianami w tych projektach i ograniczeniem możliwości utrzymania struktury.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli używasz typów, które staną się naprawdę `public` i zostały przeniesione do nowej, obsługiwanej przestrzeni nazw, zaktualizuj odwołania, aby odpowiadały nowym przestrzeniom nazw.

Jeśli używasz typów, które zostały oznaczone jako `internal`, musisz znaleźć alternatywę. Wcześniej typy "pubternal" nigdy nie były obsługiwane do użytku publicznego. Jeśli istnieją określone typy w tych obszarach nazw, które mają krytyczne znaczenie dla aplikacji, należy rozwiązać problem na [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues). W przypadku tworzenia żądanych typów `public`.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Ta zmiana obejmuje typy w następujących przestrzeniach nazw:

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
