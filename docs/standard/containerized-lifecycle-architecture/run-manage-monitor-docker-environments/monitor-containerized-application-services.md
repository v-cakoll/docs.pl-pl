---
title: "Monitor konteneryzowanych usługi aplikacji"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 58bf96dfa06a78892563698200e6f4df5f371346
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="monitor-containerized-application-services"></a>Monitor konteneryzowanych usługi aplikacji

Jest krytyczne znaczenie w aplikacjach podzielony na wiele kontenerów i mikrousług sposób monitorowania i analizy zachowania aplikacji.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Usługa Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) jest usługą extensible analytics, która monitoruje działającej aplikacji. Pomaga wykrywać i diagnozować problemy z wydajnością i zrozumieć, co faktycznie zrobić użytkownicy z aplikacją. Jest on przeznaczony dla deweloperów z celem pomaga stale zwiększyć wydajność i użyteczność, usług lub aplikacji. Usługa Application Insights działa zarówno z usług sieci web/i autonomicznych aplikacji na różnych platformach, takich jak .NET, Java, Node.js i wiele innych platform obsługiwanego lokalnie lub w chmurze.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Analiza aplikacji Docker w środowiskach pytań i odpowiedzi przy użyciu usługi Application Insights

W odniesieniu do Docker, można wykresu cyklu zdarzenia i liczniki wydajności z kontenerów Docker na usługi Application Insights. Wystarczy uruchomić [obrazu Application Insights Docker](https://hub.docker.com/r/microsoft/applicationinsights/) jako kontener na hoście, a zostaną wyświetlone liczniki wydajności dla hosta oraz inne obrazy Docker. Ten obraz Application Insights Docker (rysunek 6 - 1) ułatwia monitorowanie aplikacji konteneryzowanych zbierać dane telemetryczne dotyczące wydajności i aktywności Docker hosta (sieci maszyn wirtualnych systemu Linux), kontenery Docker i aplikacje uruchomione w nich.

![przykład](./media/image1.png)

Rysunek 6-1: Usługa Application Insights monitorowanie hostów Docker i kontenerów

Po uruchomieniu [obrazu Application Insights Docker](https://hub.docker.com/r/microsoft/applicationinsights/) na hoście Docker, korzystać z następujących czynności:

-   Cykl życia dane telemetryczne dotyczące wszystkich kontenerów, które są uruchomione na hoście — uruchamianie, zatrzymywanie i tak dalej.

-   Liczniki wydajności dla wszystkich kontenerów: procesora CPU, pamięci, użycie sieci i.

-   Jeśli zainstalowano także [zestaw SDK usługi Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) w aplikacje uruchomione w kontenerach, wszystkie dane telemetryczne tych aplikacji będą miały dodatkowe właściwości identyfikacji komputera hosta i kontenera. Tak na przykład jeśli masz wystąpienie aplikacji uruchomionej w więcej niż jednego hosta, można łatwo będzie można filtrować telemetrii aplikacji przez hosta.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Konfigurowanie usługi Application Insights do monitorowania Docker aplikacji i Docker hostów

Aby utworzyć zasobu usługi Application Insights, postępuj zgodnie z instrukcjami w artykułach przedstawionych na liście poniżej. Azure Portal będzie tworzy niezbędne skryptu.

-   **Monitorowanie aplikacji Docker w usłudze Application Insights:**[https://docs.microsoft.com/azure/application-insights/app-insights-docker  ](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Obraz Insights Docker aplikacji w Centrum Docker i Github:**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) and <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **Skonfiguruj usługę Application Insights dla platformy ASP.NET:**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Usługa Application Insights dla stron sieci web:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Operations Management Suite](http://microsoft.com/oms) uproszczone rozwiązanie zarządzania IT, zapewniająca analizy dzienników, automatyzacji tworzenia kopii zapasowej i odzyskiwania lokacji. Na podstawie [zapytania](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) w Operations Management Suite może zgłaszać [alerty](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) i ustaw korygowania za pośrednictwem [usługi Automatyzacja Azure](https://docs.microsoft.com/azure/automation/). Również bezproblemowo zintegrować z istniejących rozwiązań zarządzania zapewnienie pojedynczego widoku okienka z awaryjne. Operations Management Suite pomaga zarządzać i chronić lokalnej i w chmurze infrastruktury.

### <a name="operations-management-suitehttpmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite](http://microsoft.com/oms) rozwiązanie kontenera Docker

Oprócz zapewnienia usług cenne samodzielnie, rozwiązania kontenera Operations Management Suite można zarządzać i monitorować hostów Docker i kontenery poprzez wyświetlenie informacji o Twojej kontenery i hosty kontenera skutkującej, które są uruchomione kontenerów czy nie, dzienniki demona i kontener Docker wysyłane do i *stdout* i *stderr*. Przedstawia on także metryki wydajności, np. Procesora, pamięci, sieci i magazynu dla kontenera i hostów ułatwiające rozwiązywanie problemów i znaleźć zakłócenia sąsiada kontenerów.

![](./media/image2.png)

Rysunek 6-2: informacje o kontenery Docker wyświetlane przez usługi Operations Management Suite

Usługa Application Insights i Operations Management Suite skupić się na monitorowanie działań; Jednak usługi Application Insights skupiono się więcej na monitorowania aplikacji się dzięki użyciu jego SDK działających w aplikacji. Jednak Operations Management Suite bardziej koncentruje się na infrastrukturze wokół hostów, a także oferuje szczegółowa analiza dzienników na dużą skalę, zapewniając systemu bardzo elastyczne danymi/zapytania wyszukiwania.

Ponieważ Operations Management Suite jest zaimplementowany jako usługa w chmurze, można mieć on działa szybko z minimalnym inwestycji w infrastrukturę usług. Nowe funkcje są przeprowadzane automatycznie, eliminuje konieczność rutynowej konserwacji i uaktualnić kosztów.

Za pomocą Operations Management Suite kontenera rozwiązania, można wykonać następujące czynności:

-   Scentralizowanie i skorelowania miliony dzienniki z kontenerów Docker na dużą skalę

-   Zobacz informacje o wszystkich hostów kontenera w jednym miejscu

-   Znać kontenery, które są uruchomione, obrazów są na nich uruchomione i którym jest uruchomiona

-   Szybkie diagnozowanie kontenerów "zakłócenia sąsiada", które mogą powodować problemy na hostach kontenera

-   Zobacz dziennik inspekcji dla akcji do kontenerów

-   Rozwiązywanie problemów z wyświetlanie i wyszukując scentralizowane dzienniki bez usług zdalnych na hostach Docker

-   Znajdź kontenerów, które mogą być "zakłócenia sąsiadów" i zużywające zasoby nadmiarowe na hoście

-   Wyświetl scentralizowane procesora CPU, pamięci, magazynu i użycia i wydajności informacje o sieci dla kontenerów

-   Generowanie testu Docker kontenerów w usłudze Automatyzacja Azure

Informacje o wydajności wyświetlane przez uruchomienie zapytania, takie jak typ = wydajności, jak pokazano na rysunku 6-3.

![DockerPerfMetricsView](./media/image3.png){width="5.78625in" height="3.25in"}

Rysunek 6-3 metryki wydajności hostów Docker wyświetlane przez usługi Operations Management Suite

Zapisywanie kwerend również jest standardowa funkcja Operations Management Suite i pomaga zachować zapytań znaleźliśmy przydatne i odnajdywanie trendów w systemie.

**Więcej informacji o** można znaleźć informacje o instalowaniu i konfigurowaniu Docker rozwiązania kontenera w [Operations Management Suite](http://microsoft.com/oms), przejdź do <https://docs.microsoft.com/azure/log-analytics /log-Analytics-containers>.

>[!div class="step-by-step"]
[Poprzednie] (Zarządzanie produkcji — docker-environments.md) [dalej] (.. /Key-takeaways/index.MD)
