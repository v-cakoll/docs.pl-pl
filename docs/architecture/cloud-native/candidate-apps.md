---
title: Aplikacje kandydujące dla natywnych dla chmury
description: Dowiedz się, które typy aplikacji korzystają z podejścia natywnego dla chmury
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805610"
---
# <a name="candidate-apps-for-cloud-native"></a>Aplikacje kandydujące dla natywnych dla chmury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Spójrz na aplikacje w swoim portfolio. Ile z nich kwalifikuje się do architektury natywnej dla chmury? Wszystkie? Być może niektóre?

Stosując analizę kosztów i korzyści, istnieje duża szansa, że większość nie będzie obsługiwać mocny tag cena wymagane do chmury rodzimych. Koszt natywnego chmury znacznie przekroczy wartość biznesową aplikacji.

Jaki typ aplikacji może być kandydatem do chmury natywnej?

- Duży, strategiczny system dla przedsiębiorstw, który musi stale rozwijać możliwości/funkcje biznesowe

- Aplikacja, która wymaga dużej prędkości uwalniania - z dużą pewnością

- System, w którym poszczególne funkcje muszą zostać uwolnione *bez* pełnego przemieszczenia całego systemu

- Aplikacja opracowana przez zespoły z doświadczeniem w różnych stosach technologicznych

- Aplikacja ze składnikami, które muszą być skalowane niezależnie

Następnie są starsze systemy. Chociaż wszyscy chcielibyśmy tworzyć nowe aplikacje, często jesteśmy odpowiedzialni za modernizację starszych obciążeń, które mają kluczowe znaczenie dla firmy. Z biegiem czasu starsza aplikacja może być rozłożona na mikrousługi, konteneryzowane i ostatecznie "replatformed" do architektury natywnej chmury.

### <a name="modernizing-legacy-apps"></a>Modernizacja starszych aplikacji

Bezpłatna e-book firmy Microsoft [Modernizuj istniejące aplikacje platformy .NET za pomocą chmury Azure i kontenerów systemu Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) zawiera wskazówki dotyczące migracji obciążeń lokalnych do chmury. Rysunek 1-10 pokazuje, że nie ma jednej, uniwersalnej strategii modernizacji starszych aplikacji.

![Strategie migracji starszych obciążeń](./media/strategies-for-migrating-legacy-workloads.png)

**Rysunek 1-10**. Strategie migracji starszych obciążeń

Aplikacje monolityczne, które nie są krytyczne, w dużej mierze korzystają z szybkiej migracji[(Cloud Infrastructure-Ready).](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md) W tym miejscu obciążenie lokalne jest ponownie hostowane na maszynie Wirtualnej opartej na chmurze, bez zmian. Takie podejście używa [modelu IaaS (Infrastruktura jako usługa).](https://azure.microsoft.com/overview/what-is-iaas/) Platforma Azure zawiera kilka narzędzi, takich jak [Azure Migrate,](https://azure.microsoft.com/services/azure-migrate/) [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)i Usługa migracji bazy danych platformy [Azure,](https://azure.microsoft.com/campaigns/database-migration/) aby ułatwić taki ruch. Chociaż ta strategia może przynieść pewne oszczędności, takie aplikacje zazwyczaj nie zostały zaprojektowany, aby odblokować i wykorzystać zalety chmury obliczeniowej.

Monolityczne aplikacje, które są często krytyczne dla firmy, korzystają z ulepszonej migracji lift-and-shift *(Cloud Optimized).* Takie podejście obejmuje optymalizacje wdrażania, które umożliwiają kluczowe usługi w chmurze — bez zmiany podstawowej architektury aplikacji. Na przykład można [konteneryzować](https://docs.microsoft.com/virtualization/windowscontainers/about/) aplikację i wdrożyć ją w koordynatorze kontenerów, takich jak [usługi Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/)Services, omówione w dalszej części tej książki. Raz w chmurze, aplikacja może korzystać z innych usług w chmurze, takich jak bazy danych, kolejki komunikatów, monitorowania i rozproszonego buforowania.

Wreszcie monolityczne aplikacje, które wykonują strategiczne funkcje przedsiębiorstwa, mogą najlepiej skorzystać z podejścia *natywnego w chmurze,* przedmiotu tej książki. Takie podejście zapewnia zwinność i prędkość. Ale, to jest kosztem replatforming, rearchitecting i przepisywania kodu.

Jeśli ty i Twój zespół uważacie, że podejście natywne dla chmury jest właściwe, należy zracjonalizować decyzję w organizacji. Jaki dokładnie jest problem biznesowy, który rozwiąże podejście natywne dla chmury? W jaki sposób będzie to zgodne z potrzebami biznesowymi?

- Szybkie wydania funkcji ze zwiększoną pewnością siebie?

- Skalowalność drobnoziarnista - bardziej efektywne wykorzystanie zasobów?

- Zwiększona odporność systemu?

- Poprawiono wydajność systemu?

- Większy wgląd w operacje?

- Łączenie platform programistów i magazynów danych, aby uzyskać najlepsze narzędzie do pracy?

- Przyszłościowa inwestycja w aplikację?

Właściwa strategia migracji zależy od priorytetów organizacyjnych i systemów, na które kierujesz reklamy. Dla wielu osób optymalizacja monolitycznej aplikacji w chmurze lub dodawanie usług gruboziarnistych do aplikacji n-warstwowej może być bardziej opłacalna. W takich przypadkach nadal można w pełni korzystać z funkcji paaS w chmurze, takich jak te oferowane przez usługę Azure App Service.

## <a name="summary"></a>Podsumowanie

W tym rozdziale wprowadziliśmy przetwarzanie natywne dla chmury. Udostępniliśmy definicję wraz z kluczowymi funkcjami, które napędzają aplikację natywną dla chmury. Przyjrzeliśmy się rodzajom wniosków, które mogą uzasadniać tę inwestycję i wysiłek.

Wraz z wprowadzeniem za, teraz zanurzyć się w znacznie bardziej szczegółowe spojrzenie na natywnych chmury.

### <a name="references"></a>Dokumentacja

- [Cloud Native Computing Foundation](https://www.cncf.io/)

- [Mikrousług .NET: Architektura konteneryzowanych aplikacji .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Modernizuj istniejące aplikacje platformy .NET za pomocą chmury Azure i kontenerów systemu Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Cloud Native Patterns przez Cornelia Davis](https://www.manning.com/books/cloud-native-patterns)

- [Poza zastosowaniem dwunastoceli factor](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [Co to jest infrastruktura jako kod](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Mikro wdrożenie Uber Engineering: codzienne wdrażanie z ufnością](https://eng.uber.com/micro-deploy/)

- [Jak netflix wdraża kod](https://www.infoq.com/news/2013/06/netflix/)

- [Kontrola przeciążenia do skalowania mikrousług WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[Poprzedni](definition.md)
>[następny](introduce-eshoponcontainers-reference-app.md)
