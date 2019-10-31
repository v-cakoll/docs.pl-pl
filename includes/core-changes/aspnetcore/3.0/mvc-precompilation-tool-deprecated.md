---
ms.openlocfilehash: 3f702febc78488b9413ec9303ded211493650f02
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198532"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC: Narzędzie wstępnej kompilacji zostało zaniechane

W ASP.NET Core 1,1 został wprowadzony pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (Narzędzie wstępnej kompilacji MVC) w celu dodania obsługi kompilacji plików Razor ( *. cshtml* ) w czasie publikowania. W ASP.NET Core 2,1 został wprowadzony [zestaw SDK Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) do rozwinięcia przy użyciu funkcji narzędzia prekompilacji. Zestaw SDK Razor dodaliśmy obsługę kompilacji i kompilowania plików Razor w czasie kompilowania i publikowania. Zestaw SDK sprawdza poprawność plików *. cshtml* w czasie kompilacji podczas poprawiania czasu uruchamiania aplikacji. Zestaw SDK Razor jest domyślnie włączony i żaden gest nie jest wymagany do rozpoczęcia korzystania z niego.

W ASP.NET Core 3,0 zostało usunięte narzędzie wstępnej kompilacji MVC ASP.NET Core 1,1. Wcześniejsze wersje pakietu będą nadal otrzymywać ważne poprawki błędów i zabezpieczeń w wersji poprawki.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` został użyty do wstępnego skompilowania widoków Razor MVC.

#### <a name="new-behavior"></a>Nowe zachowanie

Zestaw Razor SDK natywnie obsługuje tę funkcję. Pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` nie jest już aktualizowany.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zestaw SDK Razor oferuje większą funkcjonalność i sprawdza poprawność plików *. cshtml* w czasie kompilacji. Zestaw SDK poprawia również czas uruchamiania aplikacji.

#### <a name="recommended-action"></a>Zalecana akcja

W przypadku użytkowników ASP.NET Core 2,1 lub nowszych należy zaktualizować do korzystania z natywnej obsługi wstępnej kompilacji w [zestawie Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0). Jeśli błędy lub brakujące funkcje uniemożliwiają migrację do zestawu Razor SDK, Otwórz problem na [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

### Affected APIs

Not detectable via API analysis

-->
