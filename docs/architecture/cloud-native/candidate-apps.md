---
title: Aplikacje kandydujące dla chmury natywnej
description: Dowiedz się, które typy aplikacji korzystają z podejścia natywnego w chmurze
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 2087ef0c327a82419be95552293d1b56742b73c7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337438"
---
# <a name="candidate-apps-for-cloud-native"></a>Aplikacje kandydujące dla chmury natywnej

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Zobacz aplikacje w portfolio. Ile z nich kwalifikuje się do architektury natywnej w chmurze? Wszystkie? Być może niektóre?

W przypadku analizy kosztów/korzyści istnieje dobry szansa, że najprawdopodobniej Obsługa znacznika ceny Hefty musi być natywna w chmurze. Koszt chmury w chmurze znacznie przekracza wartość biznesową aplikacji.

Jakiego typu aplikacja może być kandydatem dla natywnej chmury?

- Duży, strategiczny system przedsiębiorstwa, który musi stale rozwijać możliwości i funkcje biznesowe

- Aplikacja, która wymaga dużej szybkości wydania — z wysokim poziomem pewności

- System, w którym poszczególne funkcje muszą zostać wydane *bez* pełnego ponownego wdrożenia całego systemu

- Aplikacja opracowana przez zespoły z doświadczeniem w różnych stosach technologicznych

- Aplikacja ze składnikami, które muszą być skalowane niezależnie

Następnie istnieją starsze systemy. Mimo że chcielibyśmy utworzyć nowe aplikacje, często są odpowiedzialni za modernizację starszych obciążeń, które mają kluczowe znaczenie dla działalności firmy. W czasie Starsza aplikacja może zostać rozłączona do mikrousług, kontenerów i ostatecznie "replatformowo" do architektury natywnej w chmurze.

### <a name="modernizing-legacy-apps"></a>Modernizacja starszych aplikacji

Bezpłatna książka elektroniczna firmy Microsoft umożliwia [modernizację istniejących aplikacji .NET w chmurze platformy Azure i kontenery systemu Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) zapewniają wskazówki dotyczące migrowania obciążeń lokalnych do chmury. Rysunek 1-10 pokazuje, że dla modernizacji starszych aplikacji nie istnieje jedna, jednokrotna strategia dopasowania.

![Strategie migracji starszych obciążeń](./media/strategies-for-migrating-legacy-workloads.png)

**Rysunek 1-10**. Strategie migracji starszych obciążeń

Wbudowane aplikacje, które nie mają krytycznego znaczenia, korzystają z szybkiej migracji podnoszenia i przesunięć ([gotowej do infrastruktury w chmurze](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)). W tym miejscu obciążenie lokalne jest hostowane na maszynie wirtualnej opartej na chmurze bez zmian. To podejście używa [modelu IaaS (infrastruktura jako usługa)](https://azure.microsoft.com/overview/what-is-iaas/). Platforma Azure oferuje kilka narzędzi, takich jak ([Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)i [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/)), aby ułatwić takie przenoszenie. Chociaż ta strategia może przynieść pewne oszczędności, takie aplikacje zwykle nie zostały zaprojektowane w celu odblokowania i wykorzystania zalet chmury obliczeniowej.

Monolityczne aplikacje mające kluczowe znaczenie dla korzyści z często biznesowej z rozszerzonej migracji podniesienia i przesunięcia (*zoptymalizowane pod kątem chmury*). Takie podejście obejmuje optymalizacje wdrożenia, które umożliwiają korzystanie z kluczowych usług Cloud Services — bez konieczności zmiany podstawowej architektury aplikacji. Na przykład możesz [konteneryzowanie](https://docs.microsoft.com/virtualization/windowscontainers/about/) aplikację i wdrożyć ją w usłudze Orchestrator Containers, takiej jak [usługi Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), omówionej w dalszej części tej książki. W chmurze aplikacja może korzystać z innych usług w chmurze, takich jak bazy danych, kolejki komunikatów, monitorowanie i rozproszone buforowanie.

Na koniec aplikacje monolityczne, które wykonują strategiczne funkcje korporacyjne, mogą najlepiej korzystać z *natywnych rozwiązań chmurowych* . Takie podejście zapewnia elastyczność i szybkość pracy. Jest to jednak koszt przetworzenia platformy, ponownej architektury i ponownego pisania kodu.

Jeśli ty i Twój zespół uzna, że podejście natywne w chmurze jest odpowiednie, behooves Ci, aby usprawnić podejmowanie decyzji w organizacji. Jaki jest dokładnie problem biznesowy, który zostanie rozwiązany przez natywne rozwiązanie w chmurze? Jak będzie ono wyrównane z potrzebami biznesowymi?

- Szybkie wydania funkcji ze zwiększonym zaufaniem?

- Szczegółowa skalowalność — bardziej wydajne użycie zasobów?

- Zwiększona odporność systemu?

- Lepsza wydajność systemu?

- Widzisz więcej operacji?

- Czy program Blend platform deweloperskich i magazynów danych ma dotrzeć do najlepszego narzędzia dla tego zadania?

- W przyszłości poświadczanie aplikacji?

Właściwa Strategia migracji zależy od priorytetów organizacyjnych i systemów, do których są ukierunkowane. Dla wielu z nich może być bardziej opłacalne, aby zoptymalizować aplikację w chmurze lub dodać duże usługi do aplikacji N-warstwowej. W takich przypadkach można nadal korzystać z funkcji PaaS w chmurze, takich jak te oferowane przez Azure App Service.

## <a name="summary"></a>Podsumowanie

W tym rozdziale wprowadziliśmy przetwarzanie natywne w chmurze. Firma Microsoft udostępniła definicje wraz z kluczowymi funkcjami, które zapewniają aplikację natywną w chmurze. Przeszukamy typy aplikacji, które mogą uzasadniać te inwestycje i nakłady pracy.

Po wprowadzeniu tych informacji szczegółowemy bardziej szczegółowy wgląd w chmurę w chmurze.

### <a name="references"></a>Odwołania

- [Natywna platforma obliczeniowa w chmurze](https://www.cncf.io/)

- [Mikrousługi platformy .NET: architektura dla kontenerów aplikacji .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Natywne wzorce chmury według Cornelia Davis](https://www.manning.com/books/cloud-native-patterns)

- [Poza aplikacją 12-Składnikową](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [Co to jest infrastruktura jako kod](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Micro Deploying inżyniera Uber: wdrażanie codziennie z pewnością](https://eng.uber.com/micro-deploy/)

- [Jak Netflix wdraża kod](https://www.infoq.com/news/2013/06/netflix/)

- [Kontrola przeciążenia na potrzeby skalowania mikrousług WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[Poprzedni](definition.md)
>[Następny](introduce-eshoponcontainers-reference-app.md)
