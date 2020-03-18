---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344319"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Brzytwa: Kompilacja runtime przeniesiona do pakietu

Obsługa kompilacji w czasie wykonywania widoków Razor i Stron Razor została przeniesiona do oddzielnego pakietu.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Kompilacja w czasie wykonywania jest dostępna bez konieczności dodatkowych pakietów.

#### <a name="new-behavior"></a>Nowe zachowanie

Funkcja została przeniesiona do pakietu [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)

Następujące interfejsy API `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` były wcześniej dostępne w celu obsługi kompilacji w czasie wykonywania. Interfejsy API są `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`teraz dostępne za pośrednictwem .

- `RazorViewEngineOptions.FileProviders`jest teraz`MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences`jest teraz`MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Ponadto `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` został usunięty. Ponowna kompilacja zmian plików jest domyślnie `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` włączona, odwołując się do pakietu.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana była konieczna, aby usunąć zależność ASP.NET core współużytkowane struktury na Roslyn.

#### <a name="recommended-action"></a>Zalecana akcja

Aplikacje, które wymagają kompilacji w czasie wykonywania lub ponownej kompilacji plików Razor powinny wykonać następujące kroki:

1. Dodaj odwołanie do `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` pakietu.
1. Zaktualizuj `Startup.ConfigureServices` metodę projektu, aby uwzględnić `AddRazorRuntimeCompilation`wywołanie . Przykład:

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
