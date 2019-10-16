---
title: Modernizowanie aplikacji za pomocą monitorowania i telemetrii
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Modernizacja aplikacji dzięki monitorowaniu i telemetrii
ms.date: 04/30/2018
ms.openlocfilehash: 3d629e89a73c870d4b6396c6b1d0ecbe95b79ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393855"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizowanie aplikacji za pomocą monitorowania i telemetrii

Gdy uruchamiasz aplikację w środowisku produkcyjnym, niezwykle ważne jest, aby uzyskać szczegółowe informacje na temat sposobu działania aplikacji. Czy jest ono wykonywane na wysokim poziomie? Czy użytkownicy uzyskują błędy czy aplikacje są stabilne i niezawodne? Potrzebujesz rozbudowanego monitorowania wydajności, zaawansowanego alertu i pulpitów nawigacyjnych, aby zapewnić, że aplikacja jest dostępna i działa zgodnie z oczekiwaniami. Należy również szybko sprawdzić, czy wystąpił problem, określić liczbę klientów, których to dotyczy, i przeprowadzić analizę głównych przyczyn, aby znaleźć i rozwiązać problem.

## <a name="monitor-your-application-with-application-insights"></a>Monitoruj swoją aplikację za pomocą Application Insights

Application Insights to rozszerzalna usługa zarządzania wydajnością aplikacji (APM) dla deweloperów sieci Web, którzy pracują na wielu platformach. Służy do monitorowania działającej aplikacji sieci Web. Application Insights automatycznie wykrywa anomalie wydajności. Zawiera ona zaawansowane narzędzia analityczne ułatwiające diagnozowanie problemów oraz ułatwiające zrozumienie, które użytkownicy faktycznie robią z Twoją aplikacją. Application Insights zaprojektowano, aby pomóc w ciągłym ulepszaniu wydajności i użyteczności. Działa w przypadku aplikacji na wielu różnych platformach, w tym .NET, Node. js i J2EE, niezależnie od tego, czy są hostowane lokalnie, czy w chmurze. Application Insights integruje się z procesami DevOps i ma punkty połączenia z różnymi narzędziami programistycznymi.

Na rysunku 4-10 przedstawiono przykład sposobu, w jaki Application Insights monitoruje aplikację i jak pokazuje te informacje na pulpicie nawigacyjnym.

![Zrzut ekranu przedstawiający pulpit nawigacyjny monitorowania Application Insights.](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Rysunek 4-10.** Pulpit nawigacyjny monitorowania Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorowanie infrastruktury platformy Docker przy użyciu Log Analytics i rozwiązania do monitorowania kontenerów

[Usługa Azure log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) jest częścią [Microsoft Azure ogólnego rozwiązania do monitorowania](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Jest to również usługa [pakietu Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Log Analytics monitoruje środowiska chmurowe i lokalne (OMS dla lokalnego) w celu zapewnienia dostępności i wydajności. Zbiera ona dane wygenerowane przez zasoby w środowiskach w chmurze i lokalnych oraz z innych narzędzi do monitorowania w celu zapewnienia analiz w wielu źródłach.

W odniesieniu do dzienników infrastruktury platformy Azure, Log Analytics, jako usługi platformy Azure, pozyskuje dane dzienników i metryk z innych usług platformy Azure (za pośrednictwem [Azure monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), maszyn wirtualnych platformy Azure, kontenerów Docker i lokalnych lub innych infrastruktury chmurowych. Log Analytics oferuje elastyczne wyszukiwanie w dzienniku i wbudowaną analizę na podstawie tych danych. Udostępnia ona zaawansowane narzędzia, których można użyć do analizowania danych między źródłami, umożliwia złożone zapytania dla wszystkich dzienników i może aktywnie otrzymywać alerty na podstawie określonych warunków. Możesz nawet zbierać dane niestandardowe w centralnym repozytorium Log Analytics, w którym można wykonywać zapytania i wizualizować je. Możesz również skorzystać z wbudowanych rozwiązań Log Analytics, aby natychmiast uzyskać wgląd w zabezpieczenia i funkcjonalność infrastruktury.

Dostęp do Log Analytics można uzyskać za pomocą portalu pakietu OMS lub Azure Portal, który działa w dowolnej przeglądarce i zapewnia dostęp do ustawień konfiguracji oraz wielu narzędzi umożliwiających analizowanie zebranych danych i wykonywanie na nich działań.

[Rozwiązanie do monitorowania kontenerów](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) w log Analytics ułatwia wyświetlanie hostów platformy Docker i kontenerów systemu Windows oraz zarządzanie nimi w jednej lokalizacji. Rozwiązanie pokazuje, które kontenery są uruchomione, jaki obraz kontenera jest uruchomiony, oraz miejsce, w którym są uruchomione kontenery. Można wyświetlić szczegółowe informacje o inspekcji, w tym polecenia, które są używane z kontenerami. Możesz również rozwiązywać problemy z kontenerami, wyświetlając i przeszukując scentralizowane dzienniki, bez konieczności zdalnego wyświetlania hostów platformy Docker lub Windows. Możesz znaleźć kontenery, które mogą być zakłóceniami i zużywać nadmierne zasoby na hoście. Ponadto można wyświetlić scentralizowane użycie procesora CPU, pamięci, magazynu i sieci oraz informacje o wydajności dla kontenerów. Na komputerach z systemem Windows można scentralizować i porównać dzienniki z systemu Windows Server, funkcji Hyper-V i kontenerów platformy Docker. Rozwiązanie obsługuje następujące Koordynatory kontenerów:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

Rysunek 4-11 pokazuje relacje między różnymi hostami kontenerów i agentami oraz pakietem OMS.

![Zrzut ekranu przedstawiający rozwiązanie do monitorowania kontenerów Log Analytics.](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Rysunek 4-11.** Log Analytics rozwiązanie do monitorowania kontenerów

Rozwiązania do monitorowania kontenerów Log Analytics można użyć do:

- Informacje o wszystkich hostach kontenerów można znaleźć w jednej lokalizacji.

- Dowiedz się, które kontenery są uruchomione, jaki obraz działa i gdzie są uruchomione.

- Zobacz dziennik inspekcji dla akcji w kontenerach.

- Rozwiązywanie problemów przez wyświetlanie i wyszukiwanie scentralizowanych dzienników bez konieczności zdalnego logowania do hostów platformy Docker.

- Znajdź kontenery, które mogą być "zakłóceniami", i zużywać nadmierne zasoby na hoście.

- Wyświetl scentralizowany procesor, pamięć, magazyn i użycie sieci oraz informacje o wydajności dla kontenerów.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Przegląd monitorowania w Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co to jest Application Insights?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co to jest Log Analytics?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Rozwiązanie do monitorowania kontenerów w Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Omówienie Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co to jest pakiet Operations Management Suite (OMS)?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Poprzedni](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[Następny](life-cycle-ci-cd-pipelines-devops-tools.md)
