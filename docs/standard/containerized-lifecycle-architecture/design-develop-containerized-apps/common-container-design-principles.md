---
title: Wspólne zasady projektowania kontenera
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 8aa388c7c19f532829d64208a48b6e556e43d802
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152880"
---
# <a name="common-container-design-principles"></a>Wspólne zasady projektowania kontenera

Dalej pobierania z procesem tworzenia aplikacji istnieje kilka podstawowych pojęć, warto zauważyć, jak używać kontenerów w odniesieniu do.

## <a name="container-equals-a-process"></a>Kontener jest równe procesu

W modelu kontenera kontener reprezentuje pojedynczego procesu. Definiując kontener jako granica procesu, rozpoczęciem tworzenia podstawowych używaną do skalowania, lub wyłączyć usługi batch, procesów. Po uruchomieniu kontenera platformy Docker, zobaczysz [punktu wejścia](https://docs.docker.com/engine/reference/builder/#/entrypoint) definicji. Definiuje proces i okresu istnienia kontenera. Po zakończeniu procesu, kończy się cyklu życia kontenera. Istnieją długotrwałe procesy takie jak serwery sieci web i krótkotrwałe procesy, takie jak zadania usługi batch, które może być implementowana jako Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/). Jeśli proces zakończy się niepowodzeniem, kończy się kontenera i koordynatora przejmuje. Jeśli koordynatora poinstruowano zapewnienie pięć wystąpień i zawiedzie, koordynatora spowoduje utworzenie innego kontenera w celu zastąpienia procesu nie powiodło się. W ramach zadania usługi batch proces zostanie uruchomiony przy użyciu parametrów. Po zakończeniu tego procesu roboczego zostało ukończone.

Może się okazać scenariusz, w którym ma wiele procesów w jeden kontener. W każdym dokumencie architektury nigdy nie jest nigdy nie "," nie ma zawsze wiadomość "zawsze". W przypadku scenariuszy wymagających wielu procesów typowym wzorcem jest użycie [nadzorcy](http://supervisord.org/).

>[!div class="step-by-step"]
>[Poprzednie](design-docker-applications.md)
>[dalej](monolithic-applications.md)