---
title: Monitorowanie usług konteneryzowanych aplikacji
description: Dowiedz się, niektóre kluczowe aspekty monitorowania kontenera architektury
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641221"
---
# <a name="monitor-containerized-application-services"></a>Monitorowanie usług konteneryzowanych aplikacji

Koniecznie dla aplikacji, podzielić na wiele kontenerów oraz mikrousług sposób monitorowanie i analizowanie zachowanie całej aplikacji.

## <a name="azure-monitor"></a>Azure Monitor

[Usługa Azure Monitor](https://azure.microsoft.com/services/monitor/) jest rozszerzalną usługą analizy, który monitoruje działającą aplikację. Pomaga wykrywać i diagnozować problemy z wydajnością i zrozumienie, jak użytkownicy w rzeczywistości korzystają z aplikacją. Jest ona przeznaczona dla deweloperów z zamiarem pomaga usprawnić wydajność i użyteczność swoje aplikacje lub usługi. Usługa Azure Monitor współpracuje z zarówno autonomiczne, jak i usług sieci web/aplikacji na różnych platformach, takich jak .NET, Java, Node.js i wielu innych platform hostowanych lokalnie lub w chmurze.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Omówienie usługi Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co to jest usługa Application Insights?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co to jest Azure monitorowanie metryk?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Rozwiązanie do monitorowania kontenerów w usłudze Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Usługi zabezpieczeń i kopii zapasowej

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

- **Zasobów lokalnych**. Za pomocą [prawdziwie spójna chmura hybrydowa](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Poprzednie](manage-production-docker-environments.md)
>[dalej](../key-takeaways/index.md)
