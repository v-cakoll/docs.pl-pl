---
title: Monitorowanie usług konteneryzowanych aplikacji
description: Dowiedz się, niektóre kluczowe aspekty monitorowania kontenera architektury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 925db543617deb28590cf6631ebbda3ee96836c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975748"
---
# <a name="monitor-containerized-application-services"></a>Monitorowanie usług konteneryzowanych aplikacji

Koniecznie dla aplikacji, podzielić na wiele kontenerów oraz mikrousług sposób monitorowanie i analizowanie zachowanie całej aplikacji.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Usługa Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) jest rozszerzalną usługą analizy, który monitoruje działającą aplikację. Pomaga wykrywać i diagnozować problemy z wydajnością i zrozumienie, jak użytkownicy w rzeczywistości korzystają z aplikacją. Jest ona przeznaczona dla deweloperów z zamiarem pomaga usprawnić wydajność i użyteczność swoje aplikacje lub usługi. Usługa Application Insights w programach zarówno autonomiczne, jak i usług sieci web/aplikacji na różnych platformach, takich jak .NET, Java, Node.js i wielu innych platform hostowanych lokalnie lub w chmurze.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Analizowanie aplikacji platformy Docker w środowisku kontroli jakości za pomocą usługi Application Insights

W odniesieniu do platformy Docker, możesz wykresu zdarzenia cyklu życia i liczniki wydajności z kontenerów platformy Docker w usłudze Application Insights. Wystarczy uruchomić [obrazu platformy Docker programu Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) jako kontenerów w hoście, a zostaną wyświetlone liczniki wydajności dla hosta, jak również jak w przypadku obrazów platformy Docker. Ten obraz platformy Docker Insights aplikacji (rysunek 6 - 1) ułatwia monitorowanie aplikacji konteneryzowanych za zbieranie danych telemetrycznych dotyczących wydajności i działania (Twoje maszyny wirtualne systemu Linux) hosta platformy Docker, kontenery platformy Docker i aplikacje uruchomione w ramach ich.

![przykład](./media/image1.png)

**Rysunek 6-1**. Monitorowanie hostów platformy Docker i kontenerów w usłudze Application Insights

Po uruchomieniu [obrazu platformy Docker programu Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) na hoście platformy Docker, korzystają z następujących wartości:

- Cykl życia telemetrii dotyczącej wszystkie kontenery działające na hoście — uruchamianie, zatrzymywanie i tak dalej.

- Liczniki wydajności dla wszystkich kontenerów: Procesor CPU, pamięci, użycie sieci i więcej.

- Jeśli zainstalowano także [zestawu SDK usługi Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) w aplikacji działających w kontenerach, wszystkie dane telemetryczne aplikacji, które będą miały dodatkowych właściwości identyfikowanie kontenera i hostów maszyn. Tak na przykład w przypadku wystąpienia aplikacji działających w więcej niż jednego hosta, możesz łatwo będzie filtrującą dane telemetrii aplikacji przez hosta.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Konfigurowanie usługi Application Insights do monitorowania aplikacji platformy Docker i hostów platformy Docker

Aby utworzyć zasób usługi Application Insights, postępuj zgodnie z instrukcjami artykuły znajdujące się w opisane poniżej. Witryna Azure portal utworzy skrypt niezbędne dla Ciebie.

- **Monitorowanie aplikacji Docker w usłudze Application Insights:** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-docker>

- **Obraz platformy Docker Insights aplikacji w usłudze Docker Hub i GitHub:** \
  <https://hub.docker.com/r/microsoft/applicationinsights/> i \
  <https://github.com/Microsoft/ApplicationInsights-Docker>

- **Konfigurowanie usługi Application Insights dla aplikacji sieci web platformy ASP.NET i ASP.NET Core** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-asp-net>

- **Usługa Application Insights dla stron sieci web:**  
  <https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="security-backup-and-monitoring-services"></a>Zabezpieczenia, kopia zapasowa i monitorowania usług

Istnieje wiele zadań pomocy technicznej z dużą liczbą szczegółowe informacje, które trzeba obsługiwać, aby upewnić się, że infrastruktura i aplikacje znajdują się w górnym więcej warunek do obsługi wymagań biznesowych i sytuacji staje się bardziej skomplikowane, w obszarze mikrousług, więc należy sposób ma wysokiego poziomu i szczegółowe widoki, gdy trzeba podjąć działania.

Platforma Azure oferuje narzędzia do zarządzania i zapewnić spójny widok cztery krytyczne aspekty w chmurze i lokalnych zasobów:

- **Zabezpieczenia**. Za pomocą [usługi Azure Security Center](https://azure.microsoft.com/services/security-center/).
  - Uzyskaj pełną widoczność i kontrolę nad ich zabezpieczeniami maszyn wirtualnych, aplikacji i obciążeń.
  - Scentralizuj Zarządzanie swoimi zasadami zabezpieczeń oraz Zintegruj istniejące procesy i narzędzia.
  - Wykrywaj rzeczywiste zagrożenia za pomocą zaawansowanych analiz.

- **Kopia zapasowa**. Za pomocą [usługa Azure Backup](https://azure.microsoft.com/services/backup/).
  - Unikaj firm kosztownych przerw w działaniu, cele zapewniania zgodności i chronić dane przed oprogramowaniem wymuszającym okup i błędami ludzkimi.
  - Zachowaj dane kopii zapasowej szyfrowane podczas przesyłania i magazynowanych.
  - Zapewnia dostęp na podstawie uwierzytelniania wieloskładnikowego, aby zapobiec nieautoryzowanemu użyciu.

- **Monitorowanie**. Za pomocą [monitorowania platformy Azure](https://azure.microsoft.com/solutions/monitoring/), [usługi Log Analytics](https://azure.microsoft.com/services/log-analytics/), i [usługi Application Insights](https://azure.microsoft.com/services/application-insights/).
  - Zyskaj pełny wgląd w kondycję i wydajność obciążeń platformy Azure, aplikacji i infrastruktury.
  - Zbieranie danych z dowolnego źródła i uzyskuj szczegółowe informacje na maszyny wirtualne, kontenery i aplikacje.
  - Zawiera informacje potrzebne przy użyciu zapytania interakcyjne oraz wyszukiwanie pełnotekstowe. 
  - Analiza głównej przyczyny za pomocą zaawansowanej Analityki, w tym algorytmów uczenia maszynowego.

- **Zasobów lokalnych**. Za pomocą [prawdziwie spójna chmura hybrydowa](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Poprzednie](manage-production-docker-environments.md)
>[dalej](../key-takeaways/index.md)
