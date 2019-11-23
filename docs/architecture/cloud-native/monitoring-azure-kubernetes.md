---
title: Monitorowanie w usługach Azure Kubernetes Services
description: Monitorowanie w usługach Azure Kubernetes Services
ms.date: 09/23/2019
ms.openlocfilehash: 71192601eac2169db188b25da3dc91b71b860903
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184989"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Monitorowanie w usługach Azure Kubernetes Services

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Wbudowane rejestrowanie w Kubernetes jest pierwotne. Dostępne są jednak pewne doskonałe opcje pobierania dzienników z usługi Kubernetes oraz do miejsca, w którym można je prawidłowo analizować. Jeśli musisz monitorować klastry AKS, skonfigurowanie elastycznego stosu dla Kubernetes jest doskonałym rozwiązaniem.

## <a name="elastic-stack"></a>Elastyczny stos

Elastyczny stos to zaawansowana opcja zbierania informacji z klastra Kubernetes. Kubernetes obsługuje wysyłanie dzienników do punktu końcowego Elasticsearch, a w [większości](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), wszystko, co musisz zrobić, to ustawienie zmiennych środowiskowych, jak pokazano na rysunku 7-5:

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**Rysunek 7-5** — Zmienne konfiguracyjne dla Kubernetes

Spowoduje to zainstalowanie Elasticsearch w klastrze i skierowanie do niego wszystkich dzienników klastra.

![przykładu pulpitu nawigacyjnego Kibana, pokazującego wyniki zapytania względem dzienników pozyskanych z Kubernetes](./media/kibana-dashboard.png)
**rysunek 7-6**. Przykład pulpitu nawigacyjnego Kibana, pokazujący wyniki zapytania względem dzienników, które są pozyskiwane z Kubernetes

## <a name="azure-container-monitoring"></a>Monitorowanie kontenerów platformy Azure

Usługa Azure Container monitoring obsługuje używanie dzienników nie tylko Kubernetes, ale również z innych aparatów aranżacji, takich jak DC/OS, Docker Swarm i Red Hat OpenShift.

![zużywanie dzienników z różnych kontenerów](./media/containers-diagram.png)
**rysunku 7-7**.  Zużywanie dzienników z różnych kontenerów

Informacje o dziennikach i metrykach są zbierane nie tylko z kontenerów uruchomionych w klastrze, ale również z hostów klastra. Umożliwia on skorelowanie informacji dzienników z dwóch, ułatwiając śledzenie błędów.

Instalowanie modułów zbierających dzienniki różni się w zależności od klastrów [systemów Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) i [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) . Jednak w obu przypadkach kolekcja dzienników jest zaimplementowana jako Kubernetes [elementu daemonset](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), co oznacza, że moduł zbierający dzienniki jest uruchamiany jako kontener na każdym z węzłów.

Niezależnie od tego, który koordynator lub system operacyjny działa demon Azure Monitor, informacje dziennika są przekazywane do tych samych Azure Monitor narzędzi, z którymi użytkownicy znają. Zapewnia to równoległe środowisko w środowiskach, które mieszają różne źródła dzienników, takie jak hybrydowe środowisko Kubernetes/Azure Functions.

![przykładowego pulpitu nawigacyjnego wyświetlającego informacje o rejestrowaniu i metrykach z wielu uruchomionych kontenerów.](./media/containers-dashboard.png)
**rysunek 7-8**. Przykładowy pulpit nawigacyjny przedstawiający rejestrowanie i informacje o metrykach z wielu uruchomionych kontenerów.

## <a name="logfinalize"></a>Log. Finalize ()

Rejestrowanie jest jednym z najbardziej zagłębień, a nie najważniejszych części wdrażania dowolnej aplikacji na dużą skalę. W miarę zwiększania rozmiaru i złożoności aplikacji jest to trudne do debugowania. Posiadanie dostępnych dzienników najwyższej jakości ułatwia debugowanie i przenosi je z obszaru "niemal niemożliwe" do "przyjemnego środowiska".

>[!div class="step-by-step"]
>[Poprzedni](logging-with-elastic-stack.md)
>[Następny](azure-monitor.md)
