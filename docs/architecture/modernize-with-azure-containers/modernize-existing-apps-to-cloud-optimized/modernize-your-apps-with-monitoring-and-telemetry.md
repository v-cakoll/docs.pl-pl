---
title: Modernizowanie aplikacji za pomocą monitorowania i telemetrii
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Modernizacja aplikacji za pomocą monitorowania i telemetrii
ms.date: 04/30/2018
ms.openlocfilehash: 3d629e89a73c870d4b6396c6b1d0ecbe95b79ead
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393855"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizowanie aplikacji za pomocą monitorowania i telemetrii

Po uruchomieniu aplikacji w środowisku produkcyjnym, ważne jest, aby uzyskać szczegółowe informacje o tym, jak aplikacja jest wykonywanie. Czy działa na wysokim poziomie? Czy użytkownicy otrzymują błędy, czy aplikacja jest stabilna i niezawodna? Aby zapewnić, że aplikacja jest dostępna i działa zgodnie z oczekiwaniami, potrzebujesz zaawansowanego monitorowania wydajności, zaawansowanych alertów i pulpitów nawigacyjnych. Musisz również być w stanie szybko zobaczyć, czy występuje problem, określić, ilu klientów dotyczy i przeprowadzić analizę głównej przyczyny, aby znaleźć i rozwiązać problem.

## <a name="monitor-your-application-with-application-insights"></a>Monitorowanie aplikacji za pomocą usługi Application Insights

Usługa Application Insights to rozszerzalna usługa zarządzania wydajnością aplikacji (APM) dla deweloperów sieci Web, którzy pracują na wielu platformach. Użyj tej usługi do monitorowania aplikacji internetowej na żywo. Usługa Application Insights automatycznie wykrywa anomalie wydajności. Zawiera zaawansowane narzędzia analityczne ułatwiające diagnozowanie problemów i ułatwiające zrozumienie, co użytkownicy faktycznie robią z aplikacją. Usługa Application Insights została zaprojektowana, aby pomóc Ci stale poprawiać wydajność i użyteczność. Działa dla aplikacji na wielu różnych platformach, w tym .NET, Node.js i J2EE, czy hostowane lokalnie lub w chmurze. Usługa Application Insights integruje się z procesami DevOps i ma punkty połączenia z różnymi narzędziami programistycznymi.

Rysunek 4-10 przedstawia przykład monitorowania aplikacji w aplikacji w usłudze Application Insights i przedstawia te szczegółowe informacje na pulpicie nawigacyjnym.

![Zrzut ekranu przedstawiający pulpit nawigacyjny monitorowania usługi Application Insights.](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Rysunek 4-10.** Pulpit nawigacyjny monitorowania usługi Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorowanie infrastruktury platformy Docker za pomocą usługi Log Analytics i rozwiązania do monitorowania kontenerów

[Usługa Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) jest częścią [ogólnego rozwiązania do monitorowania platformy Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Jest to również usługa w [pakiecie Operations Management Suite (OMS).](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview) Usługa Log Analytics monitoruje środowiska chmurowe i lokalne (OMS dla środowiska lokalnego), aby zapewnić dostępność i wydajność. Zbiera ona dane generowane przez zasoby w środowiskach chmurowych i lokalnych oraz inne narzędzia do monitorowania, aby przeprowadzać analizę na podstawie wielu źródeł.

W odniesieniu do dzienników infrastruktury platformy Azure, usługi Log Analytics jako usługa platformy Azure, pozyskiwanie danych dziennika i metryki z innych usług platformy Azure (za pośrednictwem [usługi Azure Monitor),](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)maszyn wirtualnych platformy Azure, kontenerów platformy Docker oraz infrastruktury lokalnej lub innej infrastruktury chmury. Usługa Log Analytics oferuje elastyczne wyszukiwanie dzienników i gotowe analizy na tych danych. Zapewnia bogate narzędzia, których można użyć do analizowania danych między źródłami, umożliwia złożone zapytania we wszystkich dziennikach i może proaktywnie alert na podstawie określonych warunków. Możesz nawet zbierać dane niestandardowe w centralnym repozytorium usługi Log Analytics, w którym można wysyłać zapytania i wizualizować dane. Możesz również skorzystać z wbudowanych rozwiązań usługi Log Analytics, aby natychmiast uzyskać wgląd w zabezpieczenia i funkcjonalność infrastruktury.

Dostęp do usługi Log Analytics można uzyskać za pośrednictwem portalu programu OMS lub portalu Azure, które są uruchamiane w dowolnej przeglądarce, i zapewnia dostęp do ustawień konfiguracji i wielu narzędzi do analizowania i działania na podstawie zebranych danych.

[Rozwiązanie do monitorowania kontenerów](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) w usłudze Log Analytics ułatwia wyświetlanie hostów platformy Docker i kontenerów systemu Windows oraz zarządzanie nimi w jednej lokalizacji. Rozwiązanie pokazuje, które kontenery są uruchomione, jaki obraz kontenera są uruchomione i gdzie kontenery są uruchomione. Można wyświetlić szczegółowe informacje inspekcji, w tym polecenia, które są używane z kontenerami. Można również rozwiązywać problemy z kontenerami, wyświetlając i przeszukując scentralizowane dzienniki bez konieczności zdalnego wyświetlania hostów platformy Docker lub Windows. Można znaleźć kontenery, które mogą być hałaśliwe i zużywa nadmiar zasobów na hoście. Ponadto można wyświetlić scentralizowane procesora CPU, pamięci, pamięci masowej i użycia sieci oraz informacje o wydajności dla kontenerów. Na komputerach z systemem Windows można scentralizować i porównywać dzienniki z kontenerów windows server, hyper-V i docker. Rozwiązanie obsługuje następujące koordynatory kontenerów:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

Rysunek 4-11 przedstawia relacje między różnymi hostami kontenerów i agentami i oms.

![Zrzut ekranu przedstawiający rozwiązanie do monitorowania kontenerów usługi Log Analytics Container.](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Rysunek 4-11.** Rozwiązanie do monitorowania kontenerów usługi Log Analytics

Za pomocą rozwiązania do monitorowania kontenerów usługi Log Analytics Container można:

- Zobacz informacje o wszystkich hostach kontenerów w jednej lokalizacji.

- Dowiedz się, które kontenery są uruchomione, jaki obraz są uruchomione i gdzie są uruchomione.

- Zobacz dziennik inspekcji dla akcji na kontenerach.

- Rozwiązywanie problemów przez wyświetlanie i wyszukiwanie scentralizowanych dzienników bez zdalnego logowania do hostów platformy Docker.

- Znajdź kontenery, które mogą być "hałaśliwymi sąsiadami" i zużywa nadmiar zasobów na hoście.

- Wyświetlanie scentralizowanych procesorów CPU, pamięci, pamięci masowej i użycia sieci oraz informacji o wydajności kontenerów.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Omówienie monitorowania na platformie Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co to jest usługa Application Insights?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co to jest usługa Log Analytics?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Rozwiązanie do monitorowania kontenerów w usłudze Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Omówienie usługi Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co to jest pakiet Operations Management Suite (OMS)?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Poprzedni](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[następny](life-cycle-ci-cd-pipelines-devops-tools.md)
