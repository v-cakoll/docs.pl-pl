---
title: Projektowanie aplikacji platformy Docker
description: Znajdź tutaj odwołanie do szczegółowego przewodnika po architekturze mikrousług, ponieważ jest to temat, który nie jest szczegółowo opisany w tym przewodniku.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295864"
---
# <a name="design-docker-applications"></a>Projektowanie aplikacji platformy Docker

Rozdział 1 wprowadził podstawowe pojęcia dotyczące kontenerów i platformy Docker. Te informacje są podstawowym poziomem informacji potrzebnych do rozpoczęcia pracy. Ale aplikacje dla przedsiębiorstw mogą być złożone i składają się z wielu usług zamiast pojedynczej usługi lub kontenera. W przypadku tych opcjonalnych przypadków użycia należy znać dodatkowe podejścia do projektowania, takie jak architektura zorientowana na usługi (SOA) i bardziej zaawansowane pojęcia dotyczące mikrousług i koncepcje aranżacji kontenerów. Zakres tego dokumentu nie jest ograniczona do mikrousług, ale do dowolnego cyklu życia aplikacji platformy Docker, w związku z tym nie eksploruje architektury mikrousług w głębi, ponieważ można również używać kontenerów i platformy Docker z regularnych SOA, zadania w tle lub zadania, a nawet nawet z monolitycznymi podejściami do wdrażania aplikacji.

**Więcej informacji** Aby dowiedzieć się więcej o aplikacjach dla przedsiębiorstw i architekturze mikrousług, przeczytaj przewodnik [NET Microservices: Architecture for Containerized .NET Applications,](../../microservices/index.md) które można również pobrać z <https://aka.ms/MicroservicesEbook>programu .

Jednak zanim przejdziemy do cyklu życia aplikacji i DevOps, ważne jest, aby wiedzieć, jak zamierzasz projektować i konstruować aplikację i jakie są twoje wybory projektowe.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](common-container-design-principles.md)
