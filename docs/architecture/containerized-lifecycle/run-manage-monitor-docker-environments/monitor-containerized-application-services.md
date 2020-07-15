---
title: Monitorowanie usług konteneryzowanych aplikacji
description: Poznaj kluczowe aspekty architektury kontenerów monitorowania
ms.date: 02/15/2019
ms.openlocfilehash: e41df53ad94784436442c3cf7defed3fab510455
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374445"
---
# <a name="monitor-containerized-application-services"></a>Monitorowanie usług konteneryzowanych aplikacji

Najważniejsze dla aplikacji, które dzielą się na wiele kontenerów i mikrousług, aby można było monitorować i analizować zachowanie całej aplikacji.

## <a name="azure-monitor"></a>Azure Monitor

[Azure monitor](https://azure.microsoft.com/services/monitor/) to rozszerzalna Usługa analityczna, która monitoruje działającą aplikację. Pomaga wykrywać i diagnozować problemy z wydajnością oraz dowiedzieć się, co użytkownicy faktycznie robią z Twoją aplikacją. Jest on przeznaczony dla deweloperów, z zamiarem ułatwienia ciągłego ulepszania wydajności i użyteczności usług lub aplikacji. Azure Monitor współpracuje z aplikacjami sieci Web/usług i aplikacji autonomicznymi na różnych platformach, takich jak .NET, Java, Node.js i wiele innych platform hostowanych lokalnie lub w chmurze.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Omówienie Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co to jest usługa Application Insights?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co to są metryki Azure Monitor?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Rozwiązanie do monitorowania kontenerów w Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Usługi zabezpieczeń i tworzenia kopii zapasowych

Istnieje wiele zadań związanych z pomocą techniczną z dużą ilością szczegółowych informacji, które należy obsłużyć w celu zapewnienia, że Twoje aplikacje i infrastruktura są w stanie najwyższego poziomu, aby zapewnić obsługę potrzeb firmy, a sytuacja stanie się bardziej skomplikowana w obszarze mikrousług, dzięki czemu musisz mieć dostęp do szerokiego i szczegółowego widoku, gdy trzeba podjąć odpowiednie działania.

Platforma Azure oferuje narzędzia do zarządzania i zapewnienia ujednoliconego widoku czterech krytycznych aspektów zasobów w chmurze i lokalnych:

- **Bezpieczeństwo**. Z [Azure Security Center](https://azure.microsoft.com/services/security-center/).
  - Uzyskaj pełny wgląd i kontrolę nad zabezpieczeniami maszyn wirtualnych, aplikacji i obciążeń.
  - Scentralizowanie zarządzania zasadami zabezpieczeń oraz integrowanie istniejących procesów i narzędzi.
  - Wykrywaj prawdziwe zagrożenia dzięki zaawansowanej analizie.

- **Kopia zapasowa**. Z [Azure Backup](https://azure.microsoft.com/services/backup/).
  - Unikaj kosztownych przerw w działalności biznesowej, Poznaj cele zgodności i Chroń dane przed wirusami i błędami ludzkimi.
  - Przechowuj dane kopii zapasowej w trakcie przesyłania i przechowywania.
  - Upewnij się, że dostęp oparty na uwierzytelnianiu wieloskładnikowym uniemożliwia nieautoryzowane użycie.

- **Zasoby lokalne**. Z [rozwiązaniami w chmurze hybrydowej](https://azure.microsoft.com/solutions/hybrid-cloud-app/).

>[!div class="step-by-step"]
>[Poprzedni](manage-production-docker-environments.md) 
> [Dalej](../key-takeaways/index.md)
