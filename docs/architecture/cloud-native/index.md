---
title: Projektowanie aplikacji platformy .NET natywnych dla chmury dla platformy Azure
description: Przewodnik do tworzenia aplikacji natywnych dla chmury, wykorzystując kontenery, mikrousług i bezserwerowych funkcji platformy Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: cf3be07f0d37aacf4f0252ef2f4d922b7be93eee
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989067"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>Projektowanie aplikacji platformy .NET natywnych dla chmury dla platformy Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![obraz okładki](./media/cover.png)

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Prawa &copy; autorskie 2019 firmy Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej książki nie może być powielana ani przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Książka ta jest dostarczana "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Firma Microsoft i znaki https://www.microsoft.com towarowe wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Mac i macOS są znakami towarowymi firmy Apple Inc.

Logo docker wielorybów jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany za zgodą.

Wszystkie inne znaki i logo są własnością ich odpowiednich właścicieli.

Autorów:

> **Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)
>
> **Rob Vettor** - Microsoft - Główny architekt systemu chmury/architekt IP - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/)

Uczestnicy i recenzenci:

> **Cesar De la Torre**, Główny Menedżer Programu, zespół .NET, Microsoft
>
> **Nish Anil**, Sr. Program Manager, zespół .NET, Microsoft

Edytory:

> **Maira Wenzel**, Sr. Content Developer, zespół .NET, Microsoft

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Odbiorcami tego przewodnika są głównie deweloperzy, potencjalni klienci programiści i architekci, którzy są zainteresowani nauką tworzenia aplikacji zaprojektowanych dla chmury.

Dodatkową grupą odbiorców są decydenci techniczni, którzy planują wybrać, czy mają tworzyć swoje aplikacje przy użyciu podejścia natywnego dla chmury.

## <a name="how-you-can-use-this-guide"></a>Jak można korzystać z tego przewodnika

Ten przewodnik rozpoczyna się od zdefiniowania natywnego chmury i wprowadzenia aplikacji referencyjnej utworzonej przy użyciu natywnych dla chmury zasad i technologii. Poza tymi dwoma pierwszymi rozdziałami, reszta książki jest podzielona na konkretne rozdziały, koncentrujące się na tematach wspólnych dla większości aplikacji natywnych dla chmury. Możesz przejść do dowolnego z tych rozdziałów, aby dowiedzieć się więcej o podejściach natywnych dla chmury:

- Dostęp do danych i danych
- Wzorce komunikacji
- Skalowanie i skalowalność
- Odporność aplikacji
- Monitorowanie i kondycja
- Tożsamość i bezpieczeństwo
- DevOps

Ten przewodnik jest dostępny zarówno w formacie PDF, jak i online. Możesz przesłać ten dokument lub łącza do jego wersji online do swojego zespołu, aby zapewnić wspólne zrozumienie tych tematów. Większość z tych tematów korzysta ze spójnego zrozumienia podstawowych zasad i wzorców, a także kompromisów związanych z decyzjami związanymi z tymi tematami. Naszym celem w tym dokumencie jest wyposażenie zespołów i ich liderów w informacje potrzebne do podejmowania świadomych decyzji dotyczących architektury, rozwoju i hostingu ich aplikacji.

>[!div class="step-by-step"]
>[Dalej](introduction.md)
