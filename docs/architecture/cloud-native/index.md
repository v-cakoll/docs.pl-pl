---
title: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure
description: Przewodnik tworzenia aplikacji natywnych w chmurze wykorzystujących kontenery, mikrousługi i funkcje bezserwerowe platformy Azure.
author: ardalis
ms.date: 05/13/2020
ms.openlocfilehash: 172097b4915deb2d6f0b06441d7c4ca389bbca25
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051509"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure

![obraz okładki](./media/cover.png)

**Wersja 1.0**

OPUBLIKOWANA PRZEZ

Zespoły deweloperów firmy Microsoft, .NET i Visual Studio

Dział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Copyright &copy; 2020 od firmy Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.

Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora. Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Firma Microsoft i znaki towarowe wymienione na <https://www.microsoft.com> stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.

Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. używanym przez uprawnienie.

Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.

Autorów

> **Rob Vettor**, główny architekt systemu w chmurze/IP architekt- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft
>
> **Steve "ardalis" Smith**, architekt oprogramowania i Trainer- [Ardalis.com](https://ardalis.com)

Uczestnicy i recenzenci:

> **Cesar de La Torre**, główny Menedżer programu, zespół .NET, Microsoft
>
> **Nish Anil**, starszy kierownik ds. programów, .NET Team, Microsoft
>
> **Jeremy Likness**, starszy kierownik ds. programów, .NET Team, Microsoft
>
> **Cecil Phillip**, starszy ambasador w chmurze, Microsoft

Edytory

> **Maira Wenzel**, Menedżer programów, .NET Team, Microsoft

## <a name="version"></a>Wersja

Ten przewodnik został zapisany w celu uwzględnienia wersji **programu .NET Core 3,1** wraz z wieloma dodatkowymi aktualizacjami związanymi z tym samym "" Wave "technologiami (czyli platformą Azure i dodatkowymi technologiami innych firm), które są zgodne z wersją platformy .net Core 3,1.

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Odbiorcy tego przewodnika są głównie deweloperzy, potencjalni klienci programistyczni i architektzy, którzy interesują się tworzeniem aplikacji przeznaczonych dla chmury.

Dodatkowymi odbiorcami są, którzy decydują o wyborze, czy kompilować aplikacje przy użyciu podejścia natywnego w chmurze.

## <a name="how-you-can-use-this-guide"></a>Jak można użyć tego przewodnika

Ten przewodnik rozpoczyna się od zdefiniowania natywnej chmury i wprowadzenia aplikacji referencyjnej skompilowanej przy użyciu zasad i technologii natywnych w chmurze. Oprócz tych pierwszych dwóch rozdziałów pozostała część książki jest dzielona do określonych rozdziałów ukierunkowanych na tematy wspólne dla większości aplikacji natywnych w chmurze. Możesz przejść do dowolnego z tych rozdziałów, aby dowiedzieć się więcej na temat podejścia natywnego w chmurze:

- Dostęp do danych i danych
- Wzorce komunikacji
- Skalowanie i skalowalność
- Odporność aplikacji
- Monitorowanie i kondycja
- Obsługa tożsamości i zabezpieczeń
- DevOps

Ten przewodnik jest dostępny zarówno w formacie [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) , jak i w trybie online. Możesz przesłać dalej ten dokument lub linki do swojej wersji online swojego zespołu, aby pomóc w zapewnieniu powszechnego poznania się z tymi tematami. Większość z tych tematów korzysta ze spójnych zasad i wzorców, a także tych, których dotyczą decyzje związane z tymi tematami. Naszym celem tego dokumentu jest wyposażenie zespołów i ich liderów z informacjami potrzebnymi do podejmowania świadomych decyzji o architekturze, programowaniu i hostingu aplikacji.

## <a name="send-your-feedback"></a>Wyślij opinię

Ta książka i powiązane przykłady są ciągle zmieniane, dzięki czemu Twoje opinie są gotowe! Jeśli masz komentarze dotyczące sposobu, w jaki można ulepszyć tę książkę, Skorzystaj z sekcji opinia w dolnej części strony utworzonej w witrynie [GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Dalej](introduction.md)
