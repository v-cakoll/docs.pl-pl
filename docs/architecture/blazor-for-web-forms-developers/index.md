---
title: Platforma Blazor dla deweloperów technologii ASP.NET Web Forms
description: Dowiedz się, jak tworzyć aplikacje sieci Web z pełnym stosem za pomocą platformy .NET przy użyciu funkcji Blazor i .NET Core w prosty i znajomy sposób.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 394d11038b59f4cbe9e9955df43b6198eb5daaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73088130"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>Platforma Blazor dla deweloperów technologii ASP.NET Web Forms

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![Zrzut ekranu przedstawiający okładkę e-booków aplikacji bez serwerów.](./media/index/blazor-for-web-forms-developers-cover.png)

> POBIERZ dostępny pod adresem:<https://aka.ms/blazor-ebook>

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział Firmy Microsoft Corporation

One Microsoft Way

Redmond (Waszyngton) 98052-6399

Prawa autorskie © 2019 przez Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część treści tej książki nie może być powielana lub przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ta książka jest "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Microsoft i znaki towarowe <https://www.microsoft.com> wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Mac i macOS są znakami towarowymi firmy Apple Inc.

Wszystkie inne znaki i logo są własnością ich właścicieli.

Autorów:

> **[Daniel Roth](https://github.com/danroth27)**, Główny Menedżer Programu, Microsoft Corp.

> **[Jeff Fritz](https://github.com/csharpfritz)**, Starszy Menedżer Programu, Microsoft Corp.

> **[Taylor Southwick](https://github.com/twsouthwick)**, Starszy Inżynier Oprogramowania, Microsoft Corp.

> **[Scott Addie](https://github.com/scottaddie)**, Starszy programista treści, Microsoft Corp.

## <a name="introduction"></a>Wprowadzenie

.NET od dawna obsługuje tworzenie aplikacji sieci web za pośrednictwem ASP.NET, kompleksowy zestaw struktur i narzędzi do tworzenia wszelkiego rodzaju aplikacji sieci web. ASP.NET ma swój własny potomek struktur internetowych i technologii, począwszy od klasycznych stron Active Server Pages (ASP). Struktury, takie jak ASP.NET formularzy sieci Web, ASP.NET MVC, ASP.NET stron sieci Web, a ostatnio ASP.NET Core, zapewniają produktywny i wydajny sposób tworzenia aplikacji sieci Web *renderowanych przez serwer,* w których zawartość interfejsu użytkownika jest dynamicznie generowana na serwerze w odpowiedzi na żądania HTTP. Każda struktura ASP.NET zaspokaja inną grupę odbiorców i filozofię budowania aplikacji. ASP.NET formularze sieci Web dostarczane z oryginalnej wersji .NET Framework i włączone tworzenie sieci web przy użyciu wielu wzorców znanych deweloperom pulpitu, takich jak formanty interfejsu użytkownika wielokrotnego użytku z prostą obsługą zdarzeń. Jednak żadna z ofert ASP.NET nie umożliwiają uruchamiania kodu wykonywanego w przeglądarce użytkownika. Aby to zrobić, wymaga pisania JavaScript i korzystania z wielu platform JavaScript i narzędzi, które stopniowo i obecnie popularność na przestrzeni lat: jQuery, Knockout, Angular, React, i tak dalej.

[Blazor](https://blazor.net) to nowa struktura sieci web, która zmienia to, co jest możliwe podczas tworzenia aplikacji sieci web za pomocą .NET. Blazor jest platformą interfejsu użytkownika sieci web po stronie klienta na podstawie języka C# zamiast języka JavaScript. Za pomocą blazora można napisać logikę po stronie klienta i składniki interfejsu użytkownika w języku C#, skompilować je do normalnych zestawów .NET, a następnie uruchomić je bezpośrednio w przeglądarce przy użyciu nowego otwartego standardu sieci web o nazwie WebAssembly. Lub alternatywnie Blazor może uruchamiać składniki interfejsu użytkownika .NET na serwerze i obsługiwać wszystkie interakcje interfejsu użytkownika płynnie za pomocą połączenia w czasie rzeczywistym z przeglądarką. Po sparowaniu z platformą .NET działającą na serwerze blazor umożliwia tworzenie sieci web w trybie pełnego stosu za pomocą platformy .NET. Podczas gdy Blazor współużytkuje wiele podobieństw z ASP.NET web forms, takich jak model składników wielokrotnego użytku i prosty sposób obsługi zdarzeń użytkownika, opiera się również na podstawach .NET Core, aby zapewnić nowoczesne i wysokiej wydajności środowiska tworzenia sieci web.

Ta książka wprowadza ASP.NET twórców formularzy internetowych do Blazorw sposób, który jest znany i wygodny. Wprowadza koncepcje Blazora równolegle z analogicznymi pojęciami w ASP.NET Web Forms, a jednocześnie wyjaśnia nowe koncepcje, które mogą być mniej znane. Obejmuje szeroki zakres tematów i problemów, w tym tworzenie składników, routing, układ, konfigurację i zabezpieczenia. I chociaż zawartość tej książki jest przede wszystkim do umożliwienia nowego rozwoju, obejmuje również wytyczne i strategie migracji istniejących ASP.NET formularzy internetowych do Blazor, gdy chcesz zmodernizować istniejącą aplikację.

## <a name="who-should-use-the-book"></a>Kto powinien korzystać z książki

Ta książka jest dla ASP.NET web forms deweloperzy szukają wprowadzenia do Blazor, który odnosi się do ich istniejącej wiedzy i umiejętności. Ta książka może pomóc w szybkim rozpoczęciu nowego projektu opartego na Blazorze lub pomóc w nakreśleniu planu modernizacji istniejącej aplikacji ASP.NET Web Forms.

## <a name="how-to-use-the-book"></a>Jak korzystać z książki

Pierwsza część tej książki obejmuje to, czym jest Blazor i porównuje go do tworzenia aplikacji internetowych z ASP.NET formularzami internetowymi. Książka następnie obejmuje różne tematy Blazor, rozdział po rozdziale, i odnosi się do każdej koncepcji Blazor do odpowiedniej koncepcji w ASP.NET Web Forms, lub wyjaśnia w pełni wszelkie zupełnie nowe pojęcia. Książka odnosi się również regularnie do pełnej przykładowej aplikacji zaimplementowanej zarówno w ASP.NET Web Forms, jak i Blazor, aby zademonstrować funkcje Blazora i zapewnić studium przypadku migracji z ASP.NET formularzy internetowych do Blazora. Obie implementacje przykładowej aplikacji (ASP.NET formularzy sieci Web i wersji Blazor) można znaleźć w [usteercie GitHub.](https://github.com/dotnet-architecture/eshoponblazor)

## <a name="what-this-book-doesnt-cover"></a>Czego ta książka nie obejmuje

Ta książka jest wprowadzeniem do Blazora, a nie kompleksowym przewodnikiem po migracji. Chociaż zawiera wskazówki dotyczące podejścia do migracji projektu z ASP.NET Web Forms do Blazor, nie próbuje objąć wszystkich niuansów i szczegółów. Bardziej ogólne wskazówki dotyczące migracji z ASP.NET do ASP.NET Core można znaleźć [w wskazówki dotyczące migracji](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) w dokumentacji ASP.NET Core.

### <a name="additional-resources"></a>Zasoby dodatkowe

Oficjalną stronę główną blazora i <https://blazor.net>dokumentację można znaleźć na stronie głównej.

## <a name="send-your-feedback"></a>Wyślij swoją opinię

Ta książka i powiązane próbki stale ewoluują, więc Twoja opinia jest mile widziana! Jeśli masz komentarze dotyczące sposobu ulepszenia tej książki, skorzystaj z sekcji opinii u dołu dowolnej strony zbudowanej na [problemach z githubem](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Dalej](introduction.md)
