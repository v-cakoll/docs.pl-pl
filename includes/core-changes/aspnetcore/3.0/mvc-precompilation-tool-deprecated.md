---
ms.openlocfilehash: 8395428e1729a00fc1af72cf53fe689ee95b5fdf
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721199"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC: Narzędzie wstępnej kompilacji zostało zaniechane

W ASP.NET Core 1,1 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` został wprowadzony pakiet (Narzędzie prekompilacji MVC) w celu dodania obsługi kompilacji plików Razor (plików *. cshtml* ) w czasie publikowania. W ASP.NET Core 2,1 został wprowadzony [zestaw SDK Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) do rozwinięcia przy użyciu funkcji narzędzia prekompilacji. Zestaw SDK Razor dodaliśmy obsługę kompilacji i kompilowania plików Razor w czasie kompilowania i publikowania. Zestaw SDK sprawdza poprawność plików *. cshtml* w czasie kompilacji podczas poprawiania czasu uruchamiania aplikacji. Zestaw SDK Razor jest domyślnie włączony i żaden gest nie jest wymagany do rozpoczęcia korzystania z niego.

W ASP.NET Core 3,0 zostało usunięte narzędzie wstępnej kompilacji MVC ASP.NET Core 1,1. Wcześniejsze wersje pakietu będą nadal otrzymywać ważne poprawki błędów i zabezpieczeń w wersji poprawki.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`Pakiet został użyty do wstępnego skompilowania widoków Razor MVC.

#### <a name="new-behavior"></a>Nowe zachowanie

Zestaw Razor SDK natywnie obsługuje tę funkcję. `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`Pakiet nie jest już aktualizowany.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zestaw SDK Razor oferuje większą funkcjonalność i sprawdza poprawność plików *. cshtml* w czasie kompilacji. Zestaw SDK poprawia również czas uruchamiania aplikacji.

#### <a name="recommended-action"></a>Zalecana akcja

W przypadku użytkowników ASP.NET Core 2,1 lub nowszych należy zaktualizować do korzystania z natywnej obsługi wstępnej kompilacji w [zestawie Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0). Jeśli błędy lub brakujące funkcje uniemożliwiają migrację do zestawu Razor SDK, Otwórz problem w programie [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
