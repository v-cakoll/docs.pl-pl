---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344319"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: Kompilacja środowiska uruchomieniowego została przeniesiona do pakietu

Obsługa kompilacji w czasie wykonywania widoków Razor i Razor Pages została przeniesiona do oddzielnego pakietu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Kompilacja środowiska uruchomieniowego jest dostępna bez dodatkowych pakietów.

#### <a name="new-behavior"></a>Nowe zachowanie

Funkcja została przeniesiona do pakietu [Microsoft. AspNetCore. MVC. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) .

Poniższe interfejsy API były wcześniej dostępne w `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` programie w celu obsługi kompilacji w czasie wykonywania. Interfejsy API są teraz dostępne za `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`pośrednictwem programu.

- `RazorViewEngineOptions.FileProviders`jest teraz`MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences`jest teraz`MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Ponadto program `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` został usunięty. Ponowna kompilacja zmian w pliku jest domyślnie włączona przez odwołanie do `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` pakietu.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana była niezbędna do usunięcia ASP.NET Core zależności współdzielona struktura w programie Roslyn.

#### <a name="recommended-action"></a>Zalecana akcja

Aplikacje wymagające kompilacji lub ponownej kompilacji plików Razor powinny wykonać następujące czynności:

1. Dodaj odwołanie do `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` pakietu.
1. Zaktualizuj `Startup.ConfigureServices` metodę projektu w celu dołączenia wywołania do `AddRazorRuntimeCompilation`. Przykład:

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
