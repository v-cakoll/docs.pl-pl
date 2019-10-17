---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394206"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: Kompilacja środowiska uruchomieniowego została przeniesiona do pakietu

Obsługa kompilacji w czasie wykonywania widoków Razor i Razor Pages została przeniesiona do oddzielnego pakietu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Kompilacja środowiska uruchomieniowego jest dostępna bez dodatkowych pakietów.

#### <a name="new-behavior"></a>Nowe zachowanie

Funkcja została przeniesiona do pakietu `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.

Poniższe interfejsy API były wcześniej dostępne w `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` w celu obsługi kompilacji w czasie wykonywania. Interfejsy API są teraz dostępne za pośrednictwem `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Ponadto `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` został usunięty. Ponowna kompilacja zmian w pliku jest domyślnie włączona, odwołując się do pakietu `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana była niezbędna do usunięcia ASP.NET Core zależności współdzielona struktura w programie Roslyn.

#### <a name="recommended-action"></a>Zalecana akcja

Aplikacje wymagające kompilacji lub ponownej kompilacji plików Razor powinny wykonać następujące czynności:

1. Dodaj odwołanie do pakietu `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.
1. Zaktualizuj metodę `Startup.ConfigureServices` projektu w celu uwzględnienia wywołania `AddMvcRazorRuntimeCompilation`. Na przykład w `Startup.ConfigureServices`:

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
