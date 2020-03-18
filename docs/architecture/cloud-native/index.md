---
title: Projektowanie aplikacji cloud native .NET dla platformy Azure
description: Przewodnik do tworzenia aplikacji natywnych dla chmury z wykorzystaniem kontenerów, mikrousług i funkcji bezserwerowych platformy Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 7f14a690d0153edc43f0ce7f4e91c9e9cd2c6858
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71696773"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Projektowanie aplikacji cloud native .NET dla platformy Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![obraz okładki](./media/cover.png)

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział Firmy Microsoft Corporation

One Microsoft Way

Redmond (Waszyngton) 98052-6399

Prawa autorskie © 2019 przez Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część treści tej książki nie może być powielana lub przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ta książka jest "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Microsoft i znaki towarowe https://www.microsoft.com wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Mac i macOS są znakami towarowymi firmy Apple Inc.

Logo wieloryba Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używanym za zgodą.

Wszystkie inne znaki i logo są własnością ich właścicieli.

Autorów:

> **Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)
>
> **Rob Vettor** - Microsoft - Główny Architekt Systemu Chmury / Architekt IP - [RobVettor.com](https://robvettor.com)

Uczestnicy i recenzenci:

> **Cesar De la Torre**, Główny Menedżer Programu, zespół .NET, Microsoft
>
> **Nish Anil**, Sr. Program Manager, zespół .NET, Microsoft

Edytory:

> **Maira Wenzel**, Sr. Content Developer, zespół .NET, Microsoft

## <a name="who-should-use-this-guide"></a>Kto powinien skorzystać z tego przewodnika

Odbiorcami tego przewodnika są głównie deweloperzy, potencjalni klienci i architekci, którzy są zainteresowani nauką tworzenia aplikacji przeznaczonych dla chmury.

Dodatkowa grupa odbiorców to decydenci techniczni, którzy planują zdecydować, czy tworzyć swoje aplikacje przy użyciu podejścia natywnego dla chmury.

## <a name="how-you-can-use-this-guide"></a>Jak korzystać z tego przewodnika

Ten przewodnik rozpoczyna się od zdefiniowania natywnej chmury i wprowadzenia aplikacji referencyjnej utworzonej przy użyciu natywnych zasad i technologii dla chmury. Poza tymi dwoma pierwszymi rozdziałami reszta książki jest podzielona na konkretne rozdziały poświęcone tematom typowym dla większości aplikacji natywnych dla chmury. Możesz przejść do dowolnego z tych rozdziałów, aby dowiedzieć się więcej o podejściach natywnych dla chmury:

- Dostęp do danych i danych
- Wzorce komunikacji
- Skalowanie i skalowalność
- Odporność aplikacji
- Monitorowanie i kondycja
- Tożsamość i bezpieczeństwo
- DevOps

Ten przewodnik jest dostępny zarówno w formacie PDF, jak i online. Możesz przekazać ten dokument lub linki do jego wersji online do swojego zespołu, aby zapewnić wspólne zrozumienie tych tematów. Większość z tych tematów korzysta ze spójnego zrozumienia podstawowych zasad i wzorców, a także kompromisów związanych z decyzjami związanymi z tymi tematami. Naszym celem w tym dokumencie jest wyposażenie zespołów i ich liderów w informacje potrzebne do podejmowania świadomych decyzji dotyczących architektury, rozwoju i hostingu aplikacji.

>[!div class="step-by-step"]
>[Dalej](introduction.md)
