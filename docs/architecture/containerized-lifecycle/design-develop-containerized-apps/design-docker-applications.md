---
title: Projektowanie aplikacji platformy Docker
description: Zapoznaj się z tym artykułem, aby uzyskać szczegółowy przewodnik dotyczący architektury mikrousług, ponieważ jest to temat, którego nie opisano w tym przewodniku.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295864"
---
# <a name="design-docker-applications"></a>Projektowanie aplikacji platformy Docker

Rozdział 1 wprowadził podstawowe koncepcje dotyczące kontenerów i platformy Docker. Te informacje to podstawowy poziom informacji, które należy wykonać, aby rozpocząć pracę. Jednak aplikacje dla przedsiębiorstw mogą być złożone i składać się z wielu usług zamiast jednej usługi lub kontenera. W przypadku tych opcjonalnych przypadków użycia należy poznać dodatkowe podejścia do projektowania, takie jak architektura zorientowana na usługę (SOA) i bardziej zaawansowane koncepcje mikrousług i koncepcje aranżacji kontenerów. Zakres tego dokumentu nie jest ograniczony do mikrousług, ale do dowolnego cyklu życia aplikacji platformy Docker, dlatego nie sprawdza architektury mikrousług, ponieważ można również używać kontenerów i platformy Docker z regularnym elementem SOA, zadaniami w tle lub zadaniami, a nawet ze podejściami do wdrożenia aplikacji monolitycznych.

**Więcej informacji** Aby dowiedzieć się więcej na temat architektury aplikacji i mikrousług dla przedsiębiorstw, przeczytaj przewodniki [dotyczące mikrousług w sieci: Architektura kontenerów aplikacji](../../microservices/index.md) platformy .NET, z <https://aka.ms/MicroservicesEbook>których można pobrać program.

Jednak zanim przejdziemy do cyklu życia aplikacji i DevOps, ważne jest, aby wiedzieć, w jaki sposób planujesz projektowanie i konstruowanie aplikacji oraz jakie są opcje projektowania.

>[!div class="step-by-step"]
>[Poprzedni](index.md)Następny
>[](common-container-design-principles.md)
