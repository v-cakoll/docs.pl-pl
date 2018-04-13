---
title: "Modernizacji aplikacjami za pomocą monitorowania i telemetrii"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Modernizacji aplikacjami za pomocą monitorowania i telemetrii"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3caeb60cf0107aaf5413d935f3bde11863561c7d
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizacji aplikacjami za pomocą monitorowania i telemetrii

Po uruchomieniu aplikacji w środowisku produkcyjnym, jest krytyczny, że masz wgląd w sposób wykonuje aplikacji. Czy wykonuje na wysokim poziomie? Użytkownicy występują błędy lub jest aplikacją stabilną i niezawodną? Konieczne jest monitorowanie wydajności sformatowanego zaawansowanych alertów i pulpitów nawigacyjnych w celu zapewnienia, że aplikacja jest dostępna i zostanie wykonana zgodnie z oczekiwaniami. Należy również można szybko sprawdzić, czy jest problem, można określić, ilu użytkowników dotyczy i wykonywać analizy głównej przyczyny problemu, aby znaleźć i rozwiązać problem.

## <a name="monitor-your-application-with-application-insights"></a>Monitorowanie aplikacji z usługą Application Insights

Usługa Application Insights jest rozszerzalną usługę zarządzania wydajności aplikacji (APM) dla deweloperów sieci web, którzy pracują na wielu platformach. Używana do monitorowania aplikacji sieci web na żywo. Usługa Application Insights automatycznie wykrywa anomalii wydajności. Obejmuje on analytics zaawansowane narzędzia ułatwiające diagnozowanie problemów, a także pomagające zrozumieć, co faktycznie zrobić użytkownicy z aplikacją. Usługa Application Insights zaprojektowano w celu stale poprawić wydajność i użyteczność. Działa na różnych platform, w tym .NET, Node.js i J2EE, czy dla aplikacji hostowanych lokalnie lub w chmurze. Usługa Application Insights integruje się z procesów opracowywania oprogramowania i ma punkty połączenia do różnych narzędzi do tworzenia.

Rysunek 4-10 przedstawiono przykład sposobu usługi Application Insights monitoruje aplikację i jak udostępnia informacje na temat tych technologii do pulpitu nawigacyjnego.

![Pulpit nawigacyjny monitorowania usługi Application Insights](./media/image10.png)

> **Rysunek 4-10.** Pulpit nawigacyjny monitorowania usługi Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorowanie infrastruktury Docker z analizy dzienników i jego rozwiązanie monitorowanie kontenera

[Analiza dzienników Azure](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) jest częścią [Microsoft Azure ogólną rozwiązanie monitorujące](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Usługa ta jest również [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Analiza dzienników monitoruje chmury i lokalnych środowiskach (OMS dla lokalnego) ułatwiają utrzymanie wydajności i dostępności. Zbiera dane generowane przez zasobów w swoich środowiskach w chmurze i lokalnie i z innych narzędzi do monitorowania w celu zapewnienia analizy całej wielu źródeł.

W odniesieniu do dzienników infrastruktury platformy Azure Log Analytics jako usługi Azure wysyła strumień danych dziennika i metryki z innymi usługami Azure (za pośrednictwem [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), maszynach wirtualnych platformy Azure, kontenery Docker i lokalnymi lub innymi infrastruktury chmury. Analizy dzienników oferuje elastyczne dziennik wyszukiwania i analiza poza z pole na podstawie tych danych. Zapewnia ona zaawansowanych narzędzi można użyć do analizowania danych między źródłami, umożliwia złożonych zapytań przez wszystkie dzienniki i może aktywnie alertów na podstawie określonych warunków. Można nawet zbierania danych niestandardowych w centralnym repozytorium analizy dzienników, gdzie zapytanie i wizualizacji go. Możesz również można przyrostowo korzystać wbudowanych rozwiązań analizy dzienników można natychmiast uzyskać wgląd w zabezpieczenia infrastruktury.

Można dostęp za pośrednictwem portalu OMS lub w portalu Azure, które są uruchamiane w dowolnej przeglądarce, analizy dzienników i zapewnić dostęp do ustawień konfiguracji i wiele narzędzi do analizowania i korzystania z zebranych danych.

[Rozwiązanie monitorowanie kontenera](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) w pomaga analizy dzienników i zarządzanie hostach Docker i kontenera systemu Windows w jednym miejscu. Rozwiązanie zawiera kontenery, które są, obrazów kontenera nich uruchomiony uruchomiona, i gdy kontenery są. Można wyświetlić szczegółowe informacje inspekcji, włącznie z poleceniami, które są używane z kontenerów. Można również rozwiązywać kontenery wyświetlanie i wyszukując scentralizowane dzienniki, bez konieczności zdalnie wyświetlić hostach Docker lub systemu Windows. Można znaleźć kontenerów, które mogą być zakłócenia i spójniejsze nadmiarowe zasobów na hoście. Ponadto można wyświetlić scentralizowane Procesora, pamięci, magazynu i użycie sieci oraz informacje o wydajności dla kontenerów. Na komputerach z systemem Windows, można scentralizować i porównaj dzienniki systemu Windows Server, Hyper-V i kontenery Docker. Rozwiązanie obsługuje następujące orchestrators kontenera:

-   Rozwiązanie docker Swarm

-   DC/OS

-   Kubernetes

-   Service Fabric

-   Red Hat OpenShift

Rysunek 4-11 przedstawia relacje między różnych hostów kontenera i agentów oraz OMS.

![Rozwiązanie monitorowanie kontenera analizy dzienników](./media/image11.png)

> **Rysunek 4-11.** Rozwiązanie monitorowanie kontenera analizy dzienników

Za pomocą rozwiązania monitorowania kontenera analizy dziennika na:

-   Zawiera informacje o wszystkich hostów kontenera w jednym miejscu.

-   Znać kontenery, które są uruchomione, obrazów są na nich uruchomione i którym jest uruchomiona.

-   Do kontenerów, zobacz dziennik inspekcji dla akcji.

-   Rozwiązywanie problemów z wyświetlanie i wyszukując scentralizowane dzienniki bez zdalne logowanie do hostów Docker.

-   Znajdź kontenerów, które może być "zakłócenia sąsiadów" i korzystać z nadmiarowych zasobów na hoście.

-   Wyświetl scentralizowane Procesora, pamięci, magazynu i użycie sieci oraz informacje o wydajności dla kontenerów.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Omówienie monitorowania na platformie Microsoft Azure**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   **Co to jest usługa Application Insights?**

[https://docs.microsoft.com/azure/application-insights/app-insights-overview](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   **Co to jest analiza dziennika?**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-overview](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   **Kontener rozwiązania monitorowanie analizy dzienników**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-containers](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   **Omówienie usługi Azure monitora**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   **Co to jest Operations Management Suite (OMS)?**

[https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   **Monitorowanie kontenery systemu Windows Server w sieci szkieletowej usług z pakietu OMS**

[https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
[Poprzednie](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[dalej](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
