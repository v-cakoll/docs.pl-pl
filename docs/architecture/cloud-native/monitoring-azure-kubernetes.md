---
title: Monitorowanie w usługach Azure Kubernetes Services
description: Monitorowanie w usługach Azure Kubernetes Services
ms.date: 09/23/2019
ms.openlocfilehash: fc9d84fd738ff1c40d25860680e14313c9323517
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711652"
---
# <a name="monitoring-in-azure-kubernetes-services"></a><span data-ttu-id="11e06-103">Monitorowanie w usługach Azure Kubernetes Services</span><span class="sxs-lookup"><span data-stu-id="11e06-103">Monitoring in Azure Kubernetes Services</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="11e06-104">Wbudowane rejestrowanie w Kubernetes jest pierwotne.</span><span class="sxs-lookup"><span data-stu-id="11e06-104">The built-in logging in Kubernetes is primitive.</span></span> <span data-ttu-id="11e06-105">Dostępne są jednak pewne doskonałe opcje pobierania dzienników z usługi Kubernetes oraz do miejsca, w którym można je prawidłowo analizować.</span><span class="sxs-lookup"><span data-stu-id="11e06-105">However, there are some great options for getting the logs out of Kubernetes and into a place where they can be properly analyzed.</span></span> <span data-ttu-id="11e06-106">Jeśli musisz monitorować klastry AKS, skonfigurowanie elastycznego stosu dla Kubernetes jest doskonałym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="11e06-106">If you need to monitor your AKS clusters, configuring Elastic Stack for Kubernetes is a great solution.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="11e06-107">Elastyczny stos</span><span class="sxs-lookup"><span data-stu-id="11e06-107">Elastic Stack</span></span>

<span data-ttu-id="11e06-108">Elastyczny stos to zaawansowana opcja zbierania informacji z klastra Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="11e06-108">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="11e06-109">Kubernetes obsługuje wysyłanie dzienników do punktu końcowego Elasticsearch, a w [większości](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), wszystko, co musisz zrobić, to ustawienie zmiennych środowiskowych, jak pokazano na rysunku 7-5:</span><span class="sxs-lookup"><span data-stu-id="11e06-109">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="11e06-110">**Rysunek 7-5** — Zmienne konfiguracyjne dla Kubernetes</span><span class="sxs-lookup"><span data-stu-id="11e06-110">**Figure 7-5** - Configuration variables for Kubernetes</span></span>

<span data-ttu-id="11e06-111">Spowoduje to zainstalowanie Elasticsearch w klastrze i skierowanie do niego wszystkich dzienników klastra.</span><span class="sxs-lookup"><span data-stu-id="11e06-111">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="11e06-112">![przykładu pulpitu nawigacyjnego Kibana, pokazującego wyniki zapytania względem dzienników pozyskanych z Kubernetes](./media/kibana-dashboard.png)
**rysunek 7-6**.</span><span class="sxs-lookup"><span data-stu-id="11e06-112">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="11e06-113">Przykład pulpitu nawigacyjnego Kibana, pokazujący wyniki zapytania względem dzienników, które są pozyskiwane z Kubernetes</span><span class="sxs-lookup"><span data-stu-id="11e06-113">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="azure-container-monitoring"></a><span data-ttu-id="11e06-114">Monitorowanie kontenerów platformy Azure</span><span class="sxs-lookup"><span data-stu-id="11e06-114">Azure Container Monitoring</span></span>

<span data-ttu-id="11e06-115">Usługa Azure Container monitoring obsługuje używanie dzienników nie tylko Kubernetes, ale również z innych aparatów aranżacji, takich jak DC/OS, Docker Swarm i Red Hat OpenShift.</span><span class="sxs-lookup"><span data-stu-id="11e06-115">Azure Container Monitoring supports consuming logs from not just Kubernetes but also from other orchestration engines such as DC/OS, Docker Swarm, and Red Hat OpenShift.</span></span>

<span data-ttu-id="11e06-116">![zużywanie dzienników z różnych kontenerów](./media/containers-diagram.png)
**rysunku 7-7**.</span><span class="sxs-lookup"><span data-stu-id="11e06-116">![Consuming logs from various containers](./media/containers-diagram.png)
**Figure 7-7**.</span></span>  <span data-ttu-id="11e06-117">Zużywanie dzienników z różnych kontenerów</span><span class="sxs-lookup"><span data-stu-id="11e06-117">Consuming logs from various containers</span></span>

<span data-ttu-id="11e06-118">Informacje o dziennikach i metrykach są zbierane nie tylko z kontenerów uruchomionych w klastrze, ale również z hostów klastra.</span><span class="sxs-lookup"><span data-stu-id="11e06-118">Log and metric information is gathered not just from the containers running in the cluster but also from the cluster hosts themselves.</span></span> <span data-ttu-id="11e06-119">Umożliwia on skorelowanie informacji dzienników z dwóch, ułatwiając śledzenie błędów.</span><span class="sxs-lookup"><span data-stu-id="11e06-119">It allows correlating log information from the two making it much easier to track down an error.</span></span>

<span data-ttu-id="11e06-120">Instalowanie modułów zbierających dzienniki różni się w zależności od klastrów [systemów Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) i [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) .</span><span class="sxs-lookup"><span data-stu-id="11e06-120">Installing the log collectors differs on [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) and [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) clusters.</span></span> <span data-ttu-id="11e06-121">Jednak w obu przypadkach kolekcja dzienników jest zaimplementowana jako Kubernetes [elementu daemonset](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), co oznacza, że moduł zbierający dzienniki jest uruchamiany jako kontener na każdym z węzłów.</span><span class="sxs-lookup"><span data-stu-id="11e06-121">But in both cases the log collection is implemented as a Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), meaning that the log collector is run as a container on each of the nodes.</span></span>

<span data-ttu-id="11e06-122">Niezależnie od tego, który koordynator lub system operacyjny działa demon Azure Monitor, informacje dziennika są przekazywane do tych samych Azure Monitor narzędzi, z którymi użytkownicy znają.</span><span class="sxs-lookup"><span data-stu-id="11e06-122">No matter which orchestrator or operating system is running the Azure Monitor daemon, the log information is forwarded to the same Azure Monitor tools with which users are familiar.</span></span> <span data-ttu-id="11e06-123">Zapewnia to równoległe środowisko w środowiskach, które mieszają różne źródła dzienników, takie jak hybrydowe środowisko Kubernetes/Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="11e06-123">This ensures a parallel experience in environments that mix different log sources such as a hybrid Kubernetes/Azure Functions environment.</span></span>

<span data-ttu-id="11e06-124">![przykładowego pulpitu nawigacyjnego wyświetlającego informacje o rejestrowaniu i metrykach z wielu uruchomionych kontenerów.](./media/containers-dashboard.png)
**rysunek 7-8**.</span><span class="sxs-lookup"><span data-stu-id="11e06-124">![A sample dashboard showing logging and metric information from a number of running containers.](./media/containers-dashboard.png)
**Figure 7-8**.</span></span> <span data-ttu-id="11e06-125">Przykładowy pulpit nawigacyjny przedstawiający rejestrowanie i informacje o metrykach z wielu uruchomionych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="11e06-125">A sample dashboard showing logging and metric information from a number of running containers.</span></span>

## <a name="logfinalize"></a><span data-ttu-id="11e06-126">Log. Finalize ()</span><span class="sxs-lookup"><span data-stu-id="11e06-126">Log.Finalize()</span></span>

<span data-ttu-id="11e06-127">Rejestrowanie jest jednym z najbardziej zagłębień, a nie najważniejszych części wdrażania dowolnej aplikacji na dużą skalę.</span><span class="sxs-lookup"><span data-stu-id="11e06-127">Logging is one of the most overlooked and yet most important parts of deploying any application at scale.</span></span> <span data-ttu-id="11e06-128">W miarę zwiększania rozmiaru i złożoności aplikacji jest to trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="11e06-128">As the size and complexity of applications increase, then so does the difficulty of debugging them.</span></span> <span data-ttu-id="11e06-129">Posiadanie dostępnych dzienników najwyższej jakości ułatwia debugowanie i przenosi je z obszaru "niemal niemożliwe" do "przyjemnego środowiska".</span><span class="sxs-lookup"><span data-stu-id="11e06-129">Having top quality logs available makes debugging much easier and moves it from the realm of "nearly impossible" to "a pleasant experience".</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="11e06-130">[Poprzedni](logging-with-elastic-stack.md)
>[Następny](azure-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="11e06-130">[Previous](logging-with-elastic-stack.md)
[Next](azure-monitor.md)</span></span>
