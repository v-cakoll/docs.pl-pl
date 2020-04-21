---
title: Modernizowanie aplikacji za pomocą monitorowania i telemetrii
description: Modernizacja istniejących aplikacji platformy .NET za pomocą kontenerów usługi Azure Cloud i Windows | Zmodernizuj aplikacje za pomocą monitorowania i telemetrii
ms.date: 04/30/2018
ms.openlocfilehash: a5101f150d6548406db8638904fb4ab6375edf9c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739181"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizowanie aplikacji za pomocą monitorowania i telemetrii

Po uruchomieniu aplikacji w produkcji, ważne jest, aby uzyskać szczegółowe informacje na temat działania aplikacji. Czy występuje na wysokim poziomie? Czy użytkownicy otrzymują błędy, czy aplikacja jest stabilna i niezawodna? Potrzebujesz zaawansowanego monitorowania wydajności, zaawansowanego alertów i pulpitów nawigacyjnych, aby zapewnić, że aplikacja jest dostępna i działa zgodnie z oczekiwaniami. Należy również szybko sprawdzić, czy występuje problem, określić, ilu klientów dotyczy problem, i przeprowadzić analizę przyczyn źródłowych, aby znaleźć i rozwiązać problem.

## <a name="monitor-your-application-with-application-insights"></a>Monitorowanie aplikacji za pomocą usługi Application Insights

Usługa Application Insights to usługa zarządzania wydajnością aplikacji rozszerzalna (APM) dla deweloperów sieci web, którzy pracują na wielu platformach. Użyj tej usługi do monitorowania aplikacji internetowej na żywo. Usługa Application Insights automatycznie wykrywa anomalie wydajności. Zawiera zaawansowane narzędzia analityczne ułatwiające diagnozowanie problemów i pomoc w zrozumieniu, co użytkownicy faktycznie robią z twoją aplikacją. Usługa Application Insights została zaprojektowana, aby pomóc Ci stale zwiększać wydajność i użyteczność. Działa dla aplikacji na różnych platformach, w tym .NET, Node.js i J2EE, niezależnie od tego, czy są hostowane lokalnie, czy w chmurze. Usługa Application Insights integruje się z procesami DevOps i ma punkty połączenia z różnymi narzędziami programistycznymi.

Rysunek 4-10 przedstawia przykład monitorowania aplikacji w usłudze Application Insights i sposobu, w jaki przedstawia te szczegółowe informacje na pulpicie nawigacyjnym.

![Zrzut ekranu przedstawiający pulpit nawigacyjny monitorowania usługi Application Insights.](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Rysunek 4-10.** Pulpit nawigacyjny monitorowania usługi Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitoruj infrastrukturę platformy Docker za pomocą usługi Log Analytics i jej rozwiązania do monitorowania kontenerów

[Usługa Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) jest częścią [ogólnego rozwiązania do monitorowania platformy Microsoft Azure.](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview) Jest to również usługa w [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Usługa Log Analytics monitoruje środowisko chmury i środowiska lokalne (OMS dla środowiska lokalnego), aby pomóc w utrzymaniu dostępności i wydajności. Zbiera ona dane generowane przez zasoby w środowiskach chmurowych i lokalnych oraz inne narzędzia do monitorowania, aby przeprowadzać analizę na podstawie wielu źródeł.

W odniesieniu do dzienników infrastruktury platformy Azure, usługi Log Analytics, jako usługa platformy Azure, pozyskiwania danych dziennika i metryki z innych usług platformy Azure (za pośrednictwem [usługi Azure Monitor),](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)maszyn wirtualnych platformy Azure, kontenerów platformy Docker i infrastruktury lokalnej lub innej infrastruktury chmury. Usługa Log Analytics oferuje elastyczne wyszukiwanie dzienników i gotowe analizy na podstawie tych danych. Zapewnia zaawansowane narzędzia, których można używać do analizowania danych między źródłami, umożliwia złożone zapytania we wszystkich dziennikach i może proaktywnie alertować na podstawie określonych warunków. Można nawet zbierać dane niestandardowe w centralnym repozytorium usługi Log Analytics, gdzie można je wyszukiwać i wizualizować. Można również skorzystać z wbudowanych rozwiązań usługi Log Analytics, aby natychmiast uzyskać wgląd w zabezpieczenia i funkcje infrastruktury.

Usługa Log Analytics można uzyskać za pośrednictwem portalu OMS lub witryny Azure portal, które są uruchamiane w dowolnej przeglądarce, a także zapewnia dostęp do ustawień konfiguracji i wielu narzędzi do analizowania zebranych danych i działania na ich podstawie.

[Rozwiązanie do monitorowania kontenerów](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) w usłudze Log Analytics ułatwia wyświetlanie hostów platformy Docker i Kontener systemu Windows w jednej lokalizacji i zarządzanie nimi. Rozwiązanie pokazuje, które kontenery są uruchomione, jaki obraz kontenera są uruchomione i gdzie kontenery są uruchomione. Można wyświetlić szczegółowe informacje inspekcji, w tym polecenia, które są używane z kontenerami. Można również rozwiązywać problemy z kontenerami, wyświetlając i wyszukując scentralizowane dzienniki, bez konieczności zdalnego wyświetlania hostów platformy Docker lub Windows. Można znaleźć kontenery, które mogą być hałaśliwe i zużywa nadmiar zasobów na hoście. Ponadto można wyświetlić scentralizowane procesora CPU, pamięci, pamięci masowej i użycia sieciowego oraz informacje o wydajności kontenerów. Na komputerach z systemem Windows można scentralizować i porównywać dzienniki z kontenerów systemu Windows Server, Funkcji Hyper-V i Platformy Docker. Rozwiązanie obsługuje następujące orchestrators kontenera:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

Rysunek 4-11 przedstawia relacje między różnymi hostami kontenerów i agentami i usługą OMS.

![Zrzut ekranu przedstawiający rozwiązanie do monitorowania kontenerów usługi Log Analytics.](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Rysunek 4-11.** Rozwiązanie do monitorowania kontenerów analizy dzienników

Można użyć rozwiązania monitorowania kontenerów analizy dzienników, aby:

- Zobacz informacje o wszystkich hostach kontenerów w jednej lokalizacji.

- Dowiedz się, które kontenery są uruchomione, jaki obraz są uruchomione i gdzie są uruchomione.

- Zobacz dziennik inspekcji dla akcji na kontenerach.

- Rozwiązywanie problemów, wyświetlając i wyszukując scentralizowane dzienniki bez zdalnego logowania do hostów platformy Docker.

- Znajdź kontenery, które mogą być "hałaśliwymi sąsiadami" i zużywają nadmiar zasobów na hoście.

- Wyświetlanie scentralizowanych procesorów, pamięci, pamięci masowej i użycia sieci oraz informacji o wydajności kontenerów.

### <a name="additional-resources"></a>Dodatkowe zasoby

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
