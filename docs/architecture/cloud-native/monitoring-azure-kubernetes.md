---
title: Monitorowanie w usługach Azure Kubernetes Services
description: Monitorowanie w usługach Azure Kubernetes Services
ms.date: 02/05/2020
ms.openlocfilehash: 5c46b9e8599f70d430ad26cf1364343454d30a16
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450066"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Monitorowanie w usługach Azure Kubernetes Services

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Wbudowane rejestrowanie w Kubernetes jest pierwotne. Dostępne są jednak pewne doskonałe opcje pobierania dzienników z usługi Kubernetes oraz do miejsca, w którym można je prawidłowo analizować. Jeśli musisz monitorować klastry AKS, skonfigurowanie elastycznego stosu dla Kubernetes jest doskonałym rozwiązaniem.

## <a name="azure-monitor-for-containers"></a>Usługa Azure Monitor dla kontenerów

[Azure monitor kontenerów](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview) obsługuje używanie dzienników nie tylko Kubernetes, ale również z innych aparatów aranżacji, takich jak DC/OS, Docker Swarm i Red Hat OpenShift.

![zużywanie dzienników z różnych kontenerów](./media/containers-diagram.png)
**rysunku 7-10**. Zużywanie dzienników z różnych kontenerów

[Prometheus](https://prometheus.io/) to popularne rozwiązanie do monitorowania metryk typu open source. Jest to część natywnej platformy obliczeniowej w chmurze. Zazwyczaj użycie Prometheus wymaga zarządzania serwerem Prometheus z własnym magazynem. Jednak [Azure monitor dla kontenerów zapewnia bezpośrednią integrację z punktami końcowymi metryk Prometheus](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-prometheus-integration), więc nie jest wymagany oddzielny serwer.

Informacje o dziennikach i metrykach są zbierane nie tylko z kontenerów uruchomionych w klastrze, ale również z hostów klastra. Umożliwia on skorelowanie informacji dzienników z dwóch, ułatwiając śledzenie błędów.

Instalowanie modułów zbierających dzienniki różni się w zależności od klastrów [systemów Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) i [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) . Jednak w obu przypadkach kolekcja dzienników jest zaimplementowana jako Kubernetes [elementu daemonset](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), co oznacza, że moduł zbierający dzienniki jest uruchamiany jako kontener na każdym z węzłów.

Niezależnie od tego, który koordynator lub system operacyjny działa demon Azure Monitor, informacje dziennika są przekazywane do tych samych Azure Monitor narzędzi, z którymi użytkownicy znają. Zapewnia to równoległe środowisko w środowiskach, które mieszają różne źródła dzienników, takie jak hybrydowe środowisko Kubernetes/Azure Functions.

![przykładowego pulpitu nawigacyjnego wyświetlającego informacje o rejestrowaniu i metrykach z wielu uruchomionych kontenerów.](./media/containers-dashboard.png)
**rysunek 7-11**. Przykładowy pulpit nawigacyjny przedstawiający rejestrowanie i informacje o metrykach z wielu uruchomionych kontenerów.

## <a name="logfinalize"></a>Log. Finalize ()

Rejestrowanie jest jednym z najbardziej zagłębień, a nie najważniejszych części wdrażania dowolnej aplikacji na dużą skalę. W miarę zwiększania rozmiaru i złożoności aplikacji jest to trudne do debugowania. Posiadanie dostępnych dzienników najwyższej jakości ułatwia debugowanie i przenosi je z obszaru "niemal niemożliwe" do "przyjemnego środowiska".

>[!div class="step-by-step"]
>[Poprzednie](logging-with-elastic-stack.md)
>[dalej](azure-monitor.md)
