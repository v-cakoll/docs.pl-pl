---
title: Aplikacje SOA
description: Należy pamiętać, że kontenery mogą być również użyteczną opcją wdrażania dla aplikacji SOA.
ms.date: 02/15/2019
ms.openlocfilehash: f8619cb50a7d90b911db9ff2c8ef37c3c5fde210
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738383"
---
# <a name="service-oriented-applications"></a>Aplikacje zorientowane na usługi

Architektura zorientowana na usługi (SOA) była nadużywanym terminem, który oznaczał wiele różnych rzeczy dla różnych ludzi. Ale jako wspólny mianownik SOA oznacza, że struktura architektury aplikacji przez rozkładanie go na kilka usług (najczęściej jako usługi HTTP), które mogą być klasyfikowane w różnych typach, takich jak podsystemy lub, w innych przypadkach, jako warstwy.

Obecnie można wdrożyć te usługi jako kontenery platformy Docker, które rozwiązują problemy związane z wdrażaniem, ponieważ wszystkie zależności są zawarte w obrazie kontenera. Jednak gdy trzeba skalować w poziomie SOA, mogą wystąpić problemy, jeśli wdrażasz na podstawie pojedynczych wystąpień. To wyzwanie można obsługiwać za pomocą oprogramowania klastrowego platformy Docker lub koordynatora. Przyjrzymy się koordynatorów bardziej szczegółowo w następnej sekcji, podczas eksplorowania mikrousług podejścia.

Kontenery platformy Docker są przydatne (ale nie są wymagane) zarówno dla tradycyjnych architektur zorientowanych na usługi, jak i bardziej zaawansowanych architektur mikrousług.

Na koniec dnia rozwiązania klastrowania kontenerów są przydatne zarówno dla tradycyjnej architektury SOA, jak i dla bardziej zaawansowanej architektury mikrousług, w której każda mikrousługa jest właścicielem swojego modelu danych. Dzięki wielu bazom danych można również skalować warstwę danych w poziomie zamiast pracować z monolitycznymi bazami danych współużytku udostępnianymi przez usługi SOA. Jednak dyskusja na temat podziału danych dotyczy wyłącznie architektury i projektowania.

>[!div class="step-by-step"]
>[Poprzedni](state-and-data-in-docker-applications.md)
>[następny](orchestrate-high-scalability-availability.md)
