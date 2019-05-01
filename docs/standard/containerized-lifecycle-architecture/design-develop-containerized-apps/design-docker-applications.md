---
title: Projektowanie aplikacji platformy Docker
description: Tu znaleźć odwołania do szczegółowy przewodnik dotyczący architektury mikrousług, ponieważ jest to tematu, który nie jest szczegółowo w tym przewodniku.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1d49f7509c0a12edfe375486429147e8fd240b2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799349"
---
# <a name="design-docker-applications"></a>Projektowanie aplikacji platformy Docker

Rozdział 1 wprowadzono podstawowe pojęcia dotyczące kontenerów i platformy Docker. Te informacje są podstawowy poziom informacje wymagane do rozpoczęcia pracy. Jednak aplikacje dla przedsiębiorstw mogą być złożone i składa się z wielu usług, zamiast jednej usługi lub kontenera. Dla tych przypadków Opcjonalnie użyj musisz wiedzieć dodatkowe podejścia do projektowania, takich jak architektura Service-Oriented (SOA) i bardziej zaawansowane pojęcia mikrousług i kontenerów koncepcjami dotyczącymi organizowania. Zakres tego dokumentu nie jest ograniczona do mikrousług, ale aby wszelkie cyklu życia aplikacji platformy Docker, w związku z tym, go nie zapoznaj się z architektury mikrousług, bardziej ponieważ możesz również używać kontenerów i platformy Docker za pomocą regularnego SOA, zadania w tle lub zadania lub nawet za pomocą metod wdrażania aplikacji monolitycznej.

**Więcej informacji o** Aby dowiedzieć się więcej na temat aplikacji dla przedsiębiorstw i architektury mikrousług szczegółowo, zapoznaj się z przewodnikiem [Mikrousług .NET: Architektura aplikacji kontenerowych nimi .NET](../../microservices-architecture/index.md) , którą można również pobrać z <https://aka.ms/MicroservicesEbook>.

Jednak przed przejściem do cyklu życia aplikacji i metodyki DevOps, jest ważne, aby dowiedzieć się, jak możesz zacząć projektowanie i tworzenie aplikacji i jakie są uzasadnienie wyboru tych elementów.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](common-container-design-principles.md)