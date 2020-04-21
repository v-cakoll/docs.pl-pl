---
title: Projektowanie aplikacji platformy Docker
description: Znajdź tutaj odwołanie do szczegółowego przewodnika po architekturze mikrousług, ponieważ jest to temat, który nie jest szczegółowo opisany w tym przewodniku.
ms.date: 02/15/2019
ms.openlocfilehash: b8a08658ec6c3df3e1aed596a0240223768dd647
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738463"
---
# <a name="design-docker-applications"></a>Projektowanie aplikacji platformy Docker

W rozdziale 1 wprowadzono podstawowe pojęcia dotyczące kontenerów i platformy Docker. Te informacje są podstawowym poziomem informacji potrzebnych do rozpoczęcia pracy. Jednak aplikacje dla przedsiębiorstw mogą być złożone i składają się z wielu usług zamiast jednej usługi lub kontenera. W przypadku tych przypadków opcjonalnych użycia należy znać dodatkowe podejścia do projektowania, takie jak architektura zorientowana na usługę (SOA) i bardziej zaawansowane koncepcje mikrousług i koncepcje aranżacji kontenera. Zakres tego dokumentu nie ogranicza się do mikrousług, ale do dowolnego cyklu życia aplikacji platformy Docker, w związku z tym nie eksploruje architektury mikrousług w głębi, ponieważ można również używać kontenerów i platformy Docker z regularnych SOA, zadania w tle lub zadania, a nawet z monolitycznych metod wdrażania aplikacji.

**Więcej informacji** Aby dowiedzieć się więcej na temat aplikacji dla przedsiębiorstw i architektury mikrousług w głębi, przeczytaj przewodnik <https://aka.ms/MicroservicesEbook> [NET Microservices: Architektura dla konteneryzowanych aplikacji .NET,](../../microservices/index.md) które można również pobrać z .

Jednak zanim przejdziemy do cyklu życia aplikacji i DevOps, ważne jest, aby wiedzieć, jak masz zamiar zaprojektować i skonstruować aplikację i jakie są twoje wybory projektowe.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](common-container-design-principles.md)
