---
title: Platforma Blazor dla deweloperów technologii ASP.NET Web Forms
description: Dowiedz się, jak tworzyć aplikacje sieci Web w pełnym stosie przy użyciu platformy .NET, Blazor i .NET Core w prosty i znany sposób.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 394d11038b59f4cbe9e9955df43b6198eb5daaf8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088130"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>Platforma Blazor dla deweloperów technologii ASP.NET Web Forms

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![Zrzut ekranu przedstawiający centrum poczty elektronicznej aplikacji bezserwerowych.](./media/index/blazor-for-web-forms-developers-cover.png)

> Pobieranie dostępne o: <https://aka.ms/blazor-ebook>

OPUBLIKOWANO PRZEZ

Zespoły deweloperów firmy Microsoft, .NET i Visual Studio

Dział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Prawa autorskie © 2019 przez firmę Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.

Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora. Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre przykłady opisane w niniejszym dokumencie są dostępne tylko dla ilustracji i są fikcyjne. Żadne prawdziwe skojarzenie lub połączenie nie jest zamierzone ani nie powinno zostać wywnioskowane.

Firma Microsoft i znaki towarowe wymienione w <https://www.microsoft.com> na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.

Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.

Autorów

> **[Daniel Roth](https://github.com/danroth27)** , główny Menedżer programu, Microsoft Corp.

> **[Jan Fritz](https://github.com/csharpfritz)** , starszy kierownik ds. programów, Microsoft Corp.

> **[Southwick Taylor](https://github.com/twsouthwick)** , starszy inżynier ds. oprogramowania, Microsoft Corp.

> **[Scott Addie](https://github.com/scottaddie)** , Starszy programista ds. zawartości, Microsoft Corp.

## <a name="introduction"></a>Wprowadzenie

Platforma .NET ma długotrwałe Programowanie aplikacji sieci Web za pomocą ASP.NET, kompleksowego zestawu Platform i narzędzi do tworzenia dowolnego rodzaju aplikacji sieci Web. ASP.NET ma własne elementy platformy sieci Web i technologii, które zaczynają cały sposób z klasycznymi Active Server stronami (ASP). Platformy, takie jak ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web Pages i ostatnio ASP.NET Core, zapewniają wydajny i wydajny sposób kompilowania aplikacji sieci Web *renderowanych na serwerze* , w przypadku których zawartość interfejsu użytkownika jest generowana dynamicznie na serwerze w odpowiedzi na http żądań. Każdy ASP.NET Framework jest przeznaczony dla różnych grup odbiorców i tworzenia aplikacji. ASP.NET formularze sieci Web dostarczane z oryginalną wersją .NET Framework i obsługują programowanie w sieci Web przy użyciu wielu wzorców, które są znane dla deweloperów komputerów, takich jak kontrolki interfejsu użytkownika wielokrotnego użytku z prostą obsługą zdarzeń. Żadna z ofert ASP.NET nie umożliwia jednak uruchamiania kodu, który jest wykonywany w przeglądarce użytkownika. Aby to zrobić, należy napisać kod JavaScript i korzystać z dowolnej z wielu platform i narzędzi języka JavaScript, które są stopniowane i niepopularne w latach: jQuery, odcinania, kątowy, reagowanie i tak dalej.

[Blazor](https://blazor.net) to nowa platforma sieci Web, która zmienia możliwości podczas kompilowania aplikacji sieci Web przy użyciu platformy .NET. Blazor to struktura interfejsu użytkownika sieci Web po stronie klienta oparta C# na zamiast języka JavaScript. Za pomocą Blazor można napisać składniki logiki i interfejsu użytkownika po stronie klienta w C#programie, skompilować je do normalnych zestawów .NET, a następnie uruchomić je bezpośrednio w przeglądarce przy użyciu nowego otwartego standardu sieci Web o nazwie webassembly. Alternatywnie, Blazor może uruchamiać składniki interfejsu użytkownika platformy .NET na serwerze i obsługiwać wszystkie interakcje interfejsu użytkownika w sposób płynny przez połączenie w czasie rzeczywistym z przeglądarką. W przypadku sparowania z platformą .NET działającą na serwerze Blazor umożliwia tworzenie aplikacji sieci Web na całym stosie przy użyciu platformy .NET. Chociaż Blazor udostępnia wiele commonalities z formularzy sieci Web ASP.NET, takich jak posiadanie modelu składników wielokrotnego użytku i prosty sposób obsługi zdarzeń użytkowników, to również kompiluje podstawy platformy .NET Core, aby zapewnić nowoczesne i wysoce wydajne środowisko programistyczne dla sieci Web.

W tej książce wprowadzono ASP.NET deweloperów formularzy sieci Web do Blazor w sposób znany i wygodny. Wprowadza Blazor koncepcje równolegle ze analogicznymi koncepcjami w formularzach sieci Web ASP.NET, a także objaśnia nowe koncepcje, które mogą być mniej znane. Obejmuje szeroki zakres tematów i problemów, w tym Tworzenie składników, kierowanie, układ, konfigurację i zabezpieczenia. Natomiast zawartość tej książki jest przede wszystkim przeznaczona do włączenia nowego opracowywania. obejmuje ona również wytyczne i strategie dotyczące migrowania istniejących formularzy sieci Web ASP.NET do Blazor w przypadku, gdy chcesz przeprowadzić modernizację istniejącej aplikacji.

## <a name="who-should-use-the-book"></a>Kto powinien korzystać z książki

Ta książka jest przeznaczony dla deweloperów ASP.NET Web Forms poszukujących wprowadzenia do Blazor, który odnosi się do istniejącej wiedzy i umiejętności. Ta książka może pomóc szybko rozpocząć pracę nad nowym projektem opartym na Blazor lub ułatwić tworzenie planu modernizacji istniejącej aplikacji ASP.NET Web Forms.

## <a name="how-to-use-the-book"></a>Jak korzystać z książki

W pierwszej części tej książki zawarto informacje o tym, co jest Blazor i porównuje je z programowaniem aplikacji sieci Web za pomocą formularzy sieci Web ASP.NET. Książka obejmuje wiele tematów Blazor, rozdział według rozdziałów i wiąże się z każdą koncepcją Blazor z odpowiednim koncepcją w postaci ASP.NET Web Forms lub objaśnia wszystkie zupełnie nowe koncepcje. Książka często odwołuje się również do kompletnej przykładowej aplikacji zaimplementowanej zarówno w ASP.NET Web Forms, jak i w Blazor w celu przedstawienia funkcji Blazor i zapewnienia analizy przypadku migracji z formularzy sieci Web ASP.NET do Blazor. Obie implementacje przykładowej aplikacji (ASP.NET Web Forms i wersje Blazor) można znaleźć w witrynie [GitHub](https://github.com/dotnet-architecture/eshoponblazor).

## <a name="what-this-book-doesnt-cover"></a>Czym nie obejmuje ta książka

Ta książka stanowi wprowadzenie do Blazor, a nie przewodnika po migracji. Chociaż zawiera wskazówki dotyczące sposobu podejścia do migracji projektu z formularzy sieci Web ASP.NET do Blazor, nie jest podejmowana próba pozyskania wszystkich Nuance i szczegółów. Aby uzyskać bardziej ogólne wskazówki dotyczące migracji z programu ASP.NET do ASP.NET Core, zapoznaj się ze [wskazówkami](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) dotyczącymi migracji w dokumentacji ASP.NET Core.

### <a name="additional-resources"></a>Dodatkowe zasoby

Oficjalną stronę główną Blazor i dokumentację można znaleźć na stronie <https://blazor.net>.

## <a name="send-your-feedback"></a>Wyślij opinię

Ta książka i powiązane przykłady są ciągle zmieniane, dzięki czemu Twoje opinie są gotowe! Jeśli masz komentarze dotyczące sposobu, w jaki można ulepszyć tę książkę, Skorzystaj z sekcji opinia w dolnej części strony utworzonej w witrynie [GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Next](introduction.md)
