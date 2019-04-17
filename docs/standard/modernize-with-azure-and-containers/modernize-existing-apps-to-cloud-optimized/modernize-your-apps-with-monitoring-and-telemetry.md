---
title: Modernizowanie aplikacji za pomocą monitorowania i telemetrii
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Modernizowanie aplikacji za pomocą monitorowania i telemetrii
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: cd54861600127191b852e0a966baae6e0fe7914e
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613879"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizowanie aplikacji za pomocą monitorowania i telemetrii

Po uruchomieniu aplikacji w środowisku produkcyjnym, jest krytyczny, że masz szczegółowe dane na temat jaka jest wydajność aplikacji. Czy wykonuje na wysokim poziomie? Użytkownicy pojawiają się błędy, lub jest aplikacją stabilne i niezawodne? Należy zaawansowanego monitorowania wydajności, zaawansowanym alerty i pulpity nawigacyjne, aby mieć pewność, że aplikacja jest dostępne i działają zgodnie z oczekiwaniami. Należy również można szybko sprawdzić, czy jest problem, należy określić, ilu klientów dotyczy problem, a następnie przeprowadzić analizę głównej przyczyny problemu i rozwiąż problem.

## <a name="monitor-your-application-with-application-insights"></a>Monitorowanie aplikacji za pomocą usługi Application Insights

Usługa Application Insights jest rozszerzalną usługę zarządzania wydajnością aplikacji (APM) dla deweloperów sieci web, którzy pracują na wielu platformach. Umożliwia monitorowanie aplikacji sieci web na żywo. Usługa Application Insights automatycznie wykrywa anomalie wydajność. Obejmuje ona zaawansowane funkcje analityczne narzędzia ułatwiające diagnozowanie problemów i aby lepiej zrozumieć, jak użytkownicy w rzeczywistości korzystają z aplikacją. Usługa Application Insights jest przeznaczony do pomagają w ciągłym udoskonalaniu wydajności i użyteczności. Działa to w przypadku aplikacji na różnych platformach, w tym .NET, Node.js i J2EE, czy hostowanych lokalnie lub w chmurze. Application Insights integruje się z procesy metodyki DevOps i ma punkty połączenia z szeroką gamą narzędzi programistycznych.

Rysunek 4 – 10 przedstawia przykład sposobu usługi Application Insights monitoruje aplikację, i jak udostępnia te informacje do pulpitu nawigacyjnego.

![Pulpit nawigacyjny monitorowania usługi Application Insights](./media/image10.png)

> **Rysunek 4 – 10.** Pulpit nawigacyjny monitorowania usługi Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorowanie infrastruktury za pomocą usługi Log Analytics i rozwiązania do monitorowania kontenerów platformy Docker

[Usługa Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) jest częścią [Microsoft Azure ogólnego rozwiązania do monitorowania](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Warto również usługi [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Usługa log Analytics monitoruje chmury i środowiskach lokalnych (OMS i lokalnych), aby pomóc w zachowaniu dostępności i wydajności. Zbiera ona dane generowane przez zasoby w środowiskach chmurowych i lokalnych oraz inne narzędzia do monitorowania, aby przeprowadzać analizę na podstawie wielu źródeł.

W odniesieniu do dzienników infrastruktury platformy Azure, usługi Log Analytics jako usługi platformy Azure pozyskuje dane dzienników i metryk z innymi usługami platformy Azure (za pośrednictwem [usługi Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), maszyn wirtualnych platformy Azure, kontenery platformy Docker i w środowisku lokalnym lub inne elementy infrastruktury chmury. Usługa log Analytics oferuje elastyczne wyszukiwania i dzienników out-gotową do analiz na podstawie tych danych. Zapewnia ona zaawansowanych narzędzi służących do analizowania danych w źródłach, umożliwia złożonych zapytań we wszystkich dzienników i aktywnie może on informować na podstawie określonych warunków. Można nawet zbierania niestandardowych danych w centralnym repozytorium usługi Log Analytics, gdzie można wykonywać zapytania i wizualizacji. Możesz również korzystać z zalet rozwiązania wbudowanej usługi Log Analytics, aby natychmiast uzyskać wgląd w zabezpieczenia i funkcje infrastruktury.

Można dostęp do usługi Log Analytics za pośrednictwem portalu pakietu OMS lub witryny Azure portal, które działają w dowolnej przeglądarce, i zapewnia dostęp do ustawień konfiguracji oraz wielu narzędzi służących do analizowania i korzystania z zebranych danych.

[Rozwiązanie do monitorowania kontenerów](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) w usłudze Log Analytics ułatwia wyświetlanie i zarządzanie hostów platformy Docker i kontenerów Windows w obrębie jednej lokalizacji. To rozwiązanie przedstawia, kontenery, które są uruchomione, jakie obraz kontenera są one uruchamiane i gdzie są uruchomione kontenery. Można wyświetlić szczegółowe informacje inspekcji, włącznie z poleceniami, które są używane z kontenerami. Możesz również rozwiązać kontenerów, wyświetlania i przeszukiwania scentralizowanych dzienników, bez konieczności zdalnie wyświetlić hostów platformy Docker lub Windows. Możesz znaleźć kontenerów, które mogą być hałas i korzystanie z nich nadmiar zasobów na hoście. Ponadto można wyświetlić, scentralizowane procesora CPU, pamięci, magazynu i użycia sieci i informacje o wydajności dla kontenerów. Na komputerach z systemem Windows, można scentralizować i porównać dzienników z systemu Windows Server, Hyper-V i kontenery platformy Docker. Rozwiązanie obsługuje następujące koordynatorów kontenerów:

-   Docker Swarm

-   DC/OS

-   Kubernetes

-   Service Fabric

-   Red Hat OpenShift

Rysunek 4 – 11 przedstawiono relacje między różnymi hostach kontenerów i agentów i OMS.

![Rozwiązanie do monitorowania kontenerów analizy dzienników](./media/image11.png)

> **Rysunek 4 – 11.** Rozwiązanie do monitorowania kontenerów analizy dzienników

Można użyć do rozwiązania monitorowanie kontenerów usługi Log Analytics:

-   Wyświetlone informacje o wszystkich hostach kontenerów w jednej lokalizacji.

-   Kontenery, które są uruchomione, obrazu są one uruchamiane i gdzie są one uruchamiane.

-   Zobacz dziennik inspekcji dla działań w kontenerach.

-   Rozwiązywanie problemów, wyświetlania i przeszukiwania scentralizowanych dzienników bez zdalne logowanie do hostów platformy Docker.

-   Znajdź kontenerów, które mogą być "hałaśliwym sąsiadów" i zużywałoby nadmiar zasobów na hoście.

-   Wyświetl scentralizowane procesora CPU, pamięci, magazynu i użycia sieci i informacje o wydajności dla kontenerów.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Omówienie monitorowania na platformie Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

-   **Co to jest usługa Application Insights?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

-   **Co to jest usługa Log Analytics?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

-   **Rozwiązanie do monitorowania kontenerów w usłudze Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

-   **Omówienie usługi Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

-   **Co to jest Operations Management Suite (OMS)?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

-   **Monitorowanie kontenerów systemu Windows Server w usłudze Service Fabric za pomocą pakietu OMS**

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
>[Poprzednie](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[dalej](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
