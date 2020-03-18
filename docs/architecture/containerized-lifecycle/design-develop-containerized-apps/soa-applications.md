---
title: Aplikacje SOA
description: Należy pamiętać, że kontenery mogą być również użyteczną opcją wdrażania dla aplikacji SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295274"
---
# <a name="service-oriented-applications"></a>Aplikacje zorientowane na usługi

Service-Oriented Architecture (SOA) był nadużywany termin, który oznaczał wiele różnych rzeczy dla różnych ludzi. Ale jako wspólny mianownik SOA oznacza, że struktura architektury aplikacji przez rozkładanie go na kilka usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typach, takich jak podsystemy lub, w innych przypadkach, jako warstwy.

Obecnie można wdrożyć te usługi jako kontenery platformy Docker, które rozwiązują problemy związane z wdrażaniem, ponieważ wszystkie zależności są uwzględnione w obrazie kontenera. Jednak gdy trzeba skalować w sposób skalowania w sposób skalowania w czasie, mogą wystąpić problemy, jeśli wdrażasz na podstawie pojedynczych wystąpień. To wyzwanie można obsługiwać za pomocą oprogramowania klastrowania platformy Docker lub koordynatora. Przyjrzymy się koordynatorów bardziej szczegółowo w następnej sekcji, gdy eksplorujemy podejścia mikrousług.

Kontenery platformy Docker są przydatne (ale nie są wymagane) zarówno dla tradycyjnych architektur zorientowanych na usługi, jak i bardziej zaawansowanych architektur mikrousług.

Na koniec dnia rozwiązania klastrowania kontenerów są przydatne zarówno dla tradycyjnej architektury SOA, jak i dla bardziej zaawansowanej architektury mikrousług, w której każda mikrousługa jest właścicielem modelu danych. Dzięki wielu bazom danych można również skalować w poziomie warstwy danych zamiast pracować z monolitycznymi bazami danych współużytkowane przez usługi SOA. Jednak dyskusja na temat dzielenia danych dotyczy wyłącznie architektury i projektowania.

>[!div class="step-by-step"]
>[Poprzedni](state-and-data-in-docker-applications.md)
>[następny](orchestrate-high-scalability-availability.md)
