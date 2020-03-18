---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901832"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC: Przestarzałe narzędzie kompilacji wstępnej

W ASP.NET Core 1.1 wprowadzono pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (narzędzie do wstępnej kompilacji MVC), aby dodać obsługę kompilacji plików Razor w czasie publikacji (plików*cshtml).* W ASP.NET Core 2.1, [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) został wprowadzony w celu rozszerzenia na funkcje narzędzia wstępnej kompilacji. Zestaw Razor SDK dodał obsługę kompilacji i publikowania w czasie kompilacji plików Razor. Zestaw SDK sprawdza poprawność plików *cshtml w* czasie kompilacji, jednocześnie poprawiając czas uruchamiania aplikacji. Zestaw SDK razor jest domyślnie włączony i nie jest wymagany gest, aby zacząć go używać.

W ASP.NET Core 3.0 usunięto narzędzie ASP.NET Core 1.1-era MVC prekompilacji. Wcześniejsze wersje pakietów będą nadal otrzymywać ważne poprawki błędów i zabezpieczeń w wydaniu poprawki.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` został użyty do wstępnej kompilacji widoków MVC Razor.

#### <a name="new-behavior"></a>Nowe zachowanie

Zestaw SDK Razor natywnie obsługuje tę funkcję. Pakiet `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` nie jest już aktualizowany.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zestaw SDK Razor zapewnia więcej funkcjonalności i weryfikuje poprawność plików *cshtml* w czasie kompilacji. Zestaw SDK poprawia również czas uruchamiania aplikacji.

#### <a name="recommended-action"></a>Zalecana akcja

Dla użytkowników ASP.NET Core 2.1 lub nowszej, zaktualizuj, aby użyć natywnej obsługi wstępnej kompilacji w [zestawie Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0). Jeśli błędy lub brakujące funkcje uniemożliwiają migrację do zestaw SDK Razor, otwórz problem w [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

### Affected APIs

Not detectable via API analysis

-->
