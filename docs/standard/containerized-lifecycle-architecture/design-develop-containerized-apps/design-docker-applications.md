---
title: Projektowanie aplikacji platformy Docker
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: d02cec0595024eb7bd7c0ac46df093359680da74
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155382"
---
# <a name="design-docker-applications"></a>Projektowanie aplikacji platformy Docker

Rozdział 1 wprowadzono podstawowe pojęcia dotyczące kontenerów i platformy Docker. Te informacje są podstawowy poziom informacje wymagane do rozpoczęcia pracy. Jednak aplikacje dla przedsiębiorstw mogą być złożone i składa się z wielu usług, zamiast jednej usługi lub kontenera. Dla tych przypadków Opcjonalnie użyj musisz wiedzieć dodatkowe podejścia do projektowania, takich jak architektura Service-Oriented (SOA) i bardziej zaawansowane pojęcia mikrousług i kontenerów koncepcjami dotyczącymi organizowania. Zakres tego dokumentu nie jest ograniczona do mikrousług, ale aby wszelkie cyklu życia aplikacji platformy Docker, w związku z tym, go nie zapoznaj się z architektury mikrousług szczegółowo ponieważ również można użyć kontenerów i platformy Docker za pomocą regularnego SAO, zadania w tle lub zadania, lub nawet za pomocą metod wdrażania aplikacji monolitycznej.

Jednak przed przejściem do cyklu życia aplikacji i metodyki DevOps, jest ważne, aby dowiedzieć się, jak zamierzasz projektowania i tworzenia aplikacji i jakie uzasadnienie wyboru tych elementów.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](common-container-design-principles.md)