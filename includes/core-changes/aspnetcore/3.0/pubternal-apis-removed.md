---
ms.openlocfilehash: 52b9caf2d5b3d44c0c6349501dafc371541fdd70
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396349"
---
### <a name="pubternal-apis-removed"></a>Usunięte interfejsy API "Pubternal"

Aby lepiej zachować publiczną powierzchnię interfejsu API ASP.NET Core, większość typów w `*.Internal` przestrzeniach nazw (nazywanych :::no-loc text="\"pubternal\""::: interfejsami API) staje się naprawdę wewnętrzna. Elementy członkowskie w tych przestrzeniach nazw nigdy nie były obsługiwane jako interfejsy API dostępne publicznie. Interfejsy API można przerwać w mniejszych wersjach i często zostały wykonane. Kod, który zależy od tych interfejsów API, jest dzielony podczas aktualizacji do ASP.NET Core 3,0.

Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) i [dotnet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Narażone interfejsy API są oznaczone `public` modyfikatorem dostępu i istnieją w `*.Internal` przestrzeni nazw.

#### <a name="new-behavior"></a>Nowe zachowanie

Odpowiednie interfejsy API są oznaczone za pomocą modyfikatora dostępu Internal (~/docs/CSharp/Language-Reference/Keywords/Internal.MD) i nie mogą być już używane przez kod poza tym zestawem.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Wskazówki dotyczące tych :::no-loc text="\"pubternal\""::: interfejsów API to:

* Może ulec zmianie bez powiadomienia.
* Nie podlegają zasadom platformy .NET, aby zapobiec wprowadzeniu zmian.

Pozostawienie interfejsów API `public` (nawet w `*.Internal` przestrzeniach nazw) zostało mylące dla klientów.

#### <a name="recommended-action"></a>Zalecana akcja

Zatrzymaj korzystanie z tych :::no-loc text="\"pubternal\""::: interfejsów API. Jeśli masz pytania dotyczące alternatywnych interfejsów API, Otwórz problem w repozytorium [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) .

Rozważmy na przykład następujący kod buforowania żądania HTTP w projekcie ASP.NET Core 2,2. `EnableRewind`Metoda rozszerzenia istnieje w `Microsoft.AspNetCore.Http.Internal` przestrzeni nazw.

```csharp
HttpContext.Request.EnableRewind();
```

W projekcie ASP.NET Core 3,0 Zastąp wywołanie wywołaniu `EnableRewind` `EnableBuffering` metody rozszerzenia. Funkcja buforowania żądań działa tak, jak w przeszłości. `EnableBuffering`wywołuje `internal` interfejs API teraz.

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Wszystkie interfejsy API w `Microsoft.AspNetCore.*` `Microsoft.Extensions.*` przestrzeni nazw i, które mają `Internal` segment w nazwie przestrzeni nazw. Przykład:

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
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
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
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
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->
