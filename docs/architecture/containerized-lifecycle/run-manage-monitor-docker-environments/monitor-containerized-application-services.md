---
title: Monitorowanie usług konteneryzowanych aplikacji
description: Poznaj niektóre kluczowe aspekty monitorowania architektur kontenerów
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295620"
---
# <a name="monitor-containerized-application-services"></a>Monitorowanie usług konteneryzowanych aplikacji

Ma kluczowe znaczenie dla aplikacji podzielonych na wiele kontenerów i mikrousług, aby mieć sposób monitorowania i analizowania zachowania całej aplikacji.

## <a name="azure-monitor"></a>Azure Monitor

[Usługa Azure Monitor](https://azure.microsoft.com/services/monitor/) to rozszerzalna usługa analityczna, która monitoruje aplikację na żywo. Pomaga wykrywać i diagnozować problemy z wydajnością oraz zrozumieć, co użytkownicy faktycznie robią z aplikacją. Jest on przeznaczony dla deweloperów, z zamiarem pomaga stale poprawić wydajność i użyteczność usług lub aplikacji. Usługa Azure Monitor współpracuje zarówno z usługami sieci web/services, jak i aplikacjami autonomicznymi na wielu różnych platformach, takich jak .NET, Java, Node.js i wiele innych platform, hostowanych lokalnie lub w chmurze.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Omówienie usługi Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co to jest usługa Application Insights?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co to są metryki usługi Azure Monitor?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Rozwiązanie do monitorowania kontenerów w usłudze Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Usługi zabezpieczeń i tworzenia kopii zapasowych

Istnieje wiele obowiązków pomocy technicznej z dużą ilością szczegółów, które trzeba obsługiwać, aby upewnić się, że aplikacje i infrastruktura są w najwyższej kondycji do obsługi potrzeb biznesowych, a sytuacja staje się bardziej skomplikowana w dziedzinie mikrousług, więc potrzebujesz sposobu, aby mają zarówno widoki wysokiego, jak i szczegółowe, gdy trzeba podjąć działania.

Platforma Azure oferuje narzędzia do zarządzania i zapewnienia ujednoliconego widoku czterech krytycznych aspektów zarówno zasobów chmurowych, jak i lokalnych:

- **Zabezpieczenia**. Z [centrum zabezpieczeń platformy Azure](https://azure.microsoft.com/services/security-center/).
  - Uzyskaj pełną widoczność i kontrolę nad bezpieczeństwem maszyn wirtualnych, aplikacji i obciążeń.
  - Scentralizuj zarządzanie zasadami zabezpieczeń i zintegruj istniejące procesy i narzędzia.
  - Wykrywaj realne zagrożenia za pomocą zaawansowanych analiz.

- **Kopia zapasowa**. Z [kopią zapasową platformy Azure](https://azure.microsoft.com/services/backup/).
  - Unikaj kosztownych przerw w działalności, osiągaj cele w zakresie zgodności i chroń swoje dane przed oprogramowaniem wymuszającym okup i błędami ludzkimi.
  - Dane kopii zapasowej zaszyfruj podczas przesyłania i spoczynku.
  - Zapewnij dostęp na podstawie uwierzytelniania wieloskładnikowego, aby zapobiec nieautoryzowanemu użyciu.

- **Zasoby lokalne**. Z [prawdziwie spójną chmurą hybrydową.](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)

>[!div class="step-by-step"]
>[Poprzedni](manage-production-docker-environments.md)
>[następny](../key-takeaways/index.md)
