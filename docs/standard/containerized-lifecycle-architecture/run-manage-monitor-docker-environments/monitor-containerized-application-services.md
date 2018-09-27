---
title: Monitorowanie usług konteneryzowanych aplikacji
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 4bdc4470624ce6e905ab858a2bd8b607c8d3d646
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232927"
---
# <a name="monitor-containerized-application-services"></a>Monitorowanie usług konteneryzowanych aplikacji

Koniecznie dla aplikacji, podzielić na wiele kontenerów oraz mikrousług ma możliwości monitorowania i analizy zachowania aplikacji.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Usługa Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) jest rozszerzalną usługą analizy, który monitoruje działającą aplikację. Pomaga wykrywać i diagnozować problemy z wydajnością i zrozumienie, jak użytkownicy w rzeczywistości korzystają z aplikacją. Jest ona przeznaczona dla deweloperów z zamiarem pomaga usprawnić wydajność i użyteczność swoje aplikacje lub usługi. Usługa Application Insights w programach zarówno autonomiczne, jak i usług sieci web/aplikacji na różnych platformach, takich jak .NET, Java, Node.js i wielu innych platform hostowanych lokalnie lub w chmurze.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Analizowanie aplikacji platformy Docker w środowisku kontroli jakości za pomocą usługi Application Insights

W odniesieniu do platformy Docker, możesz wykresu zdarzenia cyklu życia i liczniki wydajności z kontenerów platformy Docker w usłudze Application Insights. Wystarczy uruchomić [obrazu platformy Docker programu Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) jako kontenerów w hoście, a zostaną wyświetlone liczniki wydajności dla hosta, jak również jak w przypadku obrazów platformy Docker. Ten obraz platformy Docker Insights aplikacji (rysunek 6 - 1) ułatwia monitorowanie aplikacji konteneryzowanych za zbieranie danych telemetrycznych dotyczących wydajności i działania (Twoje maszyny wirtualne systemu Linux) hosta platformy Docker, kontenery platformy Docker i aplikacje uruchomione w ramach ich.

![przykład](./media/image1.png)

Rysunek 6-1: Usługa Application Insights, monitorowanie hostów platformy Docker i kontenerów

Po uruchomieniu [obrazu platformy Docker programu Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) na hoście platformy Docker, korzystają z następujących wartości:

-   Cykl życia telemetrii dotyczącej wszystkie kontenery działające na hoście — uruchamianie, zatrzymywanie i tak dalej.

-   Liczniki wydajności dla wszystkich kontenerów: procesor CPU, pamięci, użycie sieci i.

-   Jeśli zainstalowano także [zestawu SDK usługi Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) w aplikacji działających w kontenerach, wszystkie dane telemetryczne aplikacji, które będą miały dodatkowych właściwości identyfikowanie kontenera i hostów maszyn. Tak na przykład w przypadku wystąpienia aplikacji działających w więcej niż jednego hosta, możesz łatwo będzie filtrującą dane telemetrii aplikacji przez hosta.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Konfigurowanie usługi Application Insights do monitorowania aplikacji platformy Docker i hostów platformy Docker

Aby utworzyć zasób usługi Application Insights, postępuj zgodnie z instrukcjami artykuły znajdujące się w opisane poniżej. Witryna Azure Portal utworzy skrypt niezbędne dla Ciebie.

-   **Monitorowanie aplikacji Docker w usłudze Application Insights:**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Obraz platformy Docker Insights aplikacji w usłudze Docker Hub i Github:**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) i <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **Konfigurowanie usługi Application Insights dla platformy ASP.NET**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Usługa Application Insights dla stron sieci web:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Pakiet Operations Management Suite](https://microsoft.com/oms) jest uproszczone rozwiązanie zarządzania IT, która zapewnia usługi log analytics, automation, backup i site recovery. Na podstawie [zapytania](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) w pakiecie Operations Management Suite można podnieść [alerty](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) i ustaw korygowania za pośrednictwem [usługi Azure Automation](https://docs.microsoft.com/azure/automation/). Integruje się także bezproblemowo z istniejącymi rozwiązaniami zarządzania, aby zapewnić pojedynczy widok okienka z szkła. Pakiet Operations Management Suite pomaga i zarządzanie nimi oraz ochrona lokalnej infrastruktury chmury.

### <a name="operations-management-suitehttpsmicrosoftcomoms-container-solution-for-docker"></a>[Pakiet Operations Management Suite](https://microsoft.com/oms) rozwiązania kontenerów dla platformy Docker

Oprócz dostarcza wartościowych usług swój własny, rozwiązanie kontenera pakiet zarządzania Operations mogą zarządzać i monitorować hostów platformy Docker i kontenerów, pokazując informacji na temat której kontenerów i hostach kontenerów, które są uruchomione kontenery albo nie powiodło się i dzienniki demona i kontener platformy Docker wysyłane do *stdout* i *stderr*. Pokazuje także metryki wydajności, takie jak procesor CPU, pamięci, sieci i magazynu dla kontenera i hosty, które ułatwiają rozwiązywanie problemów i Znajdź zasobożernymi kontenerów.

![](./media/image2.png)

Rysunek 6-2: informacje o kontenerach Docker, wyświetlane przez pakiet Operations Management Suite

Usługa Application Insights i pakietu Operations Management Suite skupić się na monitorowaniu działań związanych z; Jednak usługi Application Insights skupia się więcej na temat monitorowania same aplikacje dzięki gotowej do tego zestawu SDK w ramach aplikacji. Jednak pakietu Operations Management Suite znacznie bardziej koncentruje się na infrastrukturze na hostach, a także oferuje dokładnej analizy dzienników w dużej skali przy jednoczesnym zapewnieniu systemu bardzo elastyczny opartych na danych/zapytania wyszukiwania.

Ponieważ pakietu Operations Management Suite jest zaimplementowany jako usługa w chmurze, możesz mieć ona działa szybko przy minimalnych inwestycjach w usługi infrastruktury. Nowe funkcje są dostarczane automatycznie, eliminuje konieczność konserwacji i uaktualniania kosztów.

Za pomocą rozwiązania kontenera programu Operations Management Suite, możesz wykonać następujące czynności:

-   Scentralizuj i korelowanie milionów dzienniki z kontenerów platformy Docker na dużą skalę

-   Zobacz informacje o wszystkich hostach kontenerów w jednej lokalizacji

-   Kontenery, które są uruchomione, obrazu są one uruchamiane i gdzie są one uruchamiane

-   Szybkie diagnozowanie kontenerów "hałaśliwego sąsiada", które mogą powodować problemy na hostach kontenerów

-   Zobacz dziennik inspekcji dla działań w kontenerach

-   Rozwiązywanie problemów, wyświetlania i przeszukiwania scentralizowanych dzienników bez komunikacji zdalnej do hostów platformy Docker

-   Znajdź kontenerów, które mogą być "hałaśliwym sąsiadów" i konsumencki nadmiar zasobów na hoście

-   Wyświetl scentralizowane procesora CPU, pamięci, magazynu i informacje użycia i wydajności sieci dla kontenerów

-   Generowanie testu kontenery platformy Docker za pomocą usługi Azure Automation

Informacje o wydajności można wyświetlić za pomocą uruchamiania zapytań, takich jak typ = Perf, jak pokazano w rysunek 6-3.

![DockerPerfMetricsView](./media/image3.png){width="5.78625in" height="3.25in"}

Rysunek 6-3: metryki wydajności hostów platformy Docker, wyświetlane przez pakiet Operations Management Suite

Zapisywanie zapytań jest również standardowych funkcji w pakiecie Operations Management Suite i mogą pomóc zachować zapytań Ci się znaleźć przydatne i odkrywanie trendów w Twoim systemie.

**Więcej informacji o** można znaleźć informacje dotyczące instalowania i konfigurowania platformy Docker z rozwiązania containers w [pakietu Operations Management Suite](https://microsoft.com/oms), przejdź do <https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>.

>[!div class="step-by-step"]
[Poprzednie](manage-production-docker-environments.md)
[dalej](../key-takeaways/index.md)
