---
title: Odporność na platformę Azure
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Odporność infrastruktury chmurowej na platformę Azure
ms.date: 06/30/2019
ms.openlocfilehash: 8b33c1cec1633c9fb25ae2b02e51f8be01c22941
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337387"
---
# <a name="azure-platform-resiliency"></a>Odporność na platformę Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Tworzenie niezawodnej aplikacji w chmurze różni się od tradycyjnego tworzenia aplikacji lokalnych. Chociaż historycznie zakupiono sprzęt do skalowania w górę, w środowisku chmury można skalować w poziomie. Zamiast próbować uniknąć błędów, celem jest Minimalizacja ich efektów i utrzymywanie stabilności systemu.

Takie jak niezawodne aplikacje w chmurze wyświetlają różne charakterystyki:

- Są one odporne, odzyskiwane bezpiecznie z problemów i nadal działają.
- Są one wysoce dostępne i działają zgodnie z oczekiwaniami w dobrej kondycji bez znaczącego przestoju.

Zrozumienie, jak te charakterystyki współpracują ze sobą i jak mają wpływ na koszt — są niezbędne do tworzenia niezawodnej aplikacji natywnej dla chmury. Będziemy następnym zajrzeć się na sposoby tworzenia odporności i dostępności w aplikacjach natywnych w chmurze, korzystając z funkcji z chmury platformy Azure.

## <a name="design-with-redundancy"></a>Projektowanie z nadmiarowością

Awarie różnią się w zakresie wpływu. Awaria sprzętowa, taka jak uszkodzony dysk, może mieć wpływ na pojedynczy węzeł w klastrze. Uszkodzony przełącznik sieciowy może mieć wpływ na cały stojak serwera. Mniej typowe błędy, takie jak utrata mocy, mogą zakłócać całe centrum danych. Rzadko, cały region jest niedostępny.

[Nadmiarowość](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy) jest jednym ze sposobów zapewnienia odporności aplikacji. Dokładny poziom nadmiarowości zależy od wymagań firmy i wpłynie na koszty i złożoność systemu. Na przykład wdrożenie w wielu regionach jest droższe i bardziej skomplikowane niż w przypadku wdrożenia w jednym regionie. Aby zarządzać trybem failover i powrotu po awarii, musisz wykonać procedury operacyjne. Dodatkowy koszt i złożoność mogą być uzasadnione w pewnych scenariuszach biznesowych, a w innych — już nie.

Aby zapewnić nadmiarowość, należy zidentyfikować ścieżki krytyczne w aplikacji, a następnie określić, czy istnieje nadmiarowość w każdym punkcie ścieżki? Jeśli podsystem nie powinien działać, aplikacja przejdzie w tryb failover na coś innego? Na koniec należy jasno zrozumieć te funkcje, które są wbudowane w platformę chmury platformy Azure, z których można korzystać w celu spełnienia wymagań dotyczących nadmiarowości. Poniżej przedstawiono zalecenia dotyczące tworzenia nadmiarowości:

- *Wdróż wiele wystąpień usług.* Jeśli aplikacja zależy od pojedynczego wystąpienia usługi, tworzy single point of failure. Obsługa wielu wystąpień pozwala zwiększyć odporność i skalowalność. W przypadku hostowania w usłudze Azure Kubernetes można deklaratywnie skonfigurować nadmiarowe wystąpienia (zestawy replik) w pliku manifestu Kubernetes. Wartością liczby replik można zarządzać programowo w portalu lub za pomocą funkcji skalowania automatycznego, które zostaną omówione w dalszej części tego artykułu.

- *Korzystanie z modułu równoważenia obciążenia.* Równoważenie obciążenia dystrybuuje żądania aplikacji do wystąpień usługi w dobrej kondycji i automatycznie usuwa wystąpienia w złej kondycji z obrotu. W przypadku wdrażania w usłudze Kubernetes Równoważenie obciążenia można określić w pliku manifestu Kubernetes w sekcji usługi.

- *Planowanie wdrożenia wieloregionowego.* Jeśli aplikacja jest wdrożona w jednym regionie, a region staje się niedostępny, aplikacja również stanie się niedostępna. Może to być nieakceptowalne w warunkach umowy dotyczącej poziomu usług aplikacji. Zamiast tego warto rozważyć wdrożenie aplikacji i jej usług w wielu regionach. Na przykład klaster usługi Azure Kubernetes Service (AKS) jest wdrażany w jednym regionie. Aby chronić system przed awarią regionalną, można wdrożyć aplikację w wielu klastrach AKS w różnych regionach i użyć funkcji [par regionów](https://buildazure.com/2017/01/06/azure-region-pairs-explained/) do koordynowania aktualizacji platformy i określania priorytetów działań związanych z odzyskiwaniem.

- *Włącz [replikację geograficzną](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication).* Replikacja geograficzna dla usług, takich jak Azure SQL Database i Cosmos DB, spowoduje utworzenie replik pomocniczych danych w wielu regionach. Podczas gdy obie usługi będą automatycznie replikować dane w tym samym regionie, replikacja geograficzna chroni przed awarią regionalną, umożliwiając przechodzenie w tryb failover do regionu pomocniczego. Innym najlepszym rozwiązaniem dla centrów replikacji geograficznej wokół przechowywania obrazów kontenerów. Aby wdrożyć usługę w programie AKS, należy przechowywać i ściągać obraz z repozytorium. Azure Container Registry integruje się z usługą AKS i umożliwia bezpieczne przechowywanie obrazów kontenerów. Aby zwiększyć wydajność i dostępność, należy rozważyć replikację geograficzną obrazów do rejestru w każdym regionie, w którym znajduje się klaster AKS. Każdy klaster AKS następnie ściąga obrazy kontenerów z rejestru kontenerów lokalnych w jego regionie, jak pokazano na rysunku 6-6:

![Zreplikowane zasoby w różnych regionach](./media/replicated-resources.png)

**Rysunek 6-6**. Zreplikowane zasoby w różnych regionach

- *Zaimplementuj moduł równoważenia obciążenia ruchem DNS.* Usługa [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview) zapewnia wysoką dostępność aplikacji o krytycznym znaczeniu przez równoważenie obciążenia na poziomie systemu DNS. Może kierować ruch do różnych regionów na podstawie lokalizacji geograficznej, czasu odpowiedzi klastra, a nawet kondycji punktu końcowego aplikacji. Na przykład usługa Azure Traffic Manager może kierować klientów do najbliższego klastra AKS i wystąpienia aplikacji. Jeśli masz wiele klastrów AKS w różnych regionach, użyj Traffic Manager, aby kontrolować sposób przepływu ruchu do aplikacji uruchamianych w każdym klastrze. Na rysunku 6-7 przedstawiono ten scenariusz.

![AKS i Traffic Manager platformy Azure](./media/aks-traffic-manager.png)

**Rysunek 6-7**. AKS i Traffic Manager platformy Azure

## <a name="design-for-scalability"></a>Projektowanie pod kątem skalowalności

Chmura jest w trakcie skalowania. Możliwość zwiększenia/zmniejszenia zasobów systemowych w celu zwiększenia/zmniejszenia obciążenia systemu jest kluczem cechą w chmurze platformy Azure. Aby efektywnie skalować aplikację, musisz zrozumieć funkcje skalowania każdej usługi platformy Azure, która jest dołączana do aplikacji.  Poniżej przedstawiono zalecenia dotyczące efektywnego implementowania skalowania w systemie.

- *Projektuj do skalowania.* Aplikacja musi być przeznaczona do skalowania. Aby rozpocząć, usługi powinny być bezstanowe, aby żądania mogły być kierowane do dowolnego wystąpienia. Usługa bezstanowa oznacza również, że dodanie lub usunięcie wystąpienia nie ma negatywnego wpływu na bieżących użytkowników.

- *Dzielenie obciążeń*. Tworzenie domen w niezależnych, samodzielnych mikrousługach umożliwia skalowanie niezależnie od innych usług. Zazwyczaj usługi będą mieć różne potrzeby i wymagania dotyczące skalowalności. Partycjonowanie umożliwia skalowanie tylko tego, co musi być skalowane bez niepotrzebnego kosztu skalowania całej aplikacji.

- *Preferuj skalowanie w poziomie.* Aplikacje oparte na chmurze preferują skalowanie zasobów w przeciwieństwie do skalowania w górę. Skalowanie w poziomie (nazywane również skalowaniem poziomym) obejmuje dodanie więcej zasobów usługi do istniejącego systemu w celu spełnienia i udostępnienia żądanego poziomu wydajności. Skalowanie w górę (znane także jako skalowanie w pionie) obejmuje zastępowanie istniejących zasobów bardziej wydajnym sprzętem (więcej rdzeni dysku, pamięci i przetwarzania). Skalowanie w górę może być wywoływane automatycznie przy użyciu funkcji skalowania automatycznego dostępnych w niektórych zasobach w chmurze platformy Azure. Skalowanie w poziomie wielu zasobów powoduje również dodanie nadmiarowości do całego systemu. Na koniec skalowanie pojedynczego zasobu jest zwykle droższe niż skalowanie w poziomie wielu mniejszych zasobów. Rysunek 6-8 przedstawia dwa podejścia:

![Skalowanie w górę i skalowanie w poziomie](./media/scale-up-scale-out.png)

**Rysunek 6-8.** Skalowanie w górę i skalowanie w poziomie

- *Skaluj proporcjonalnie.* W przypadku skalowania usługi należy wziąć pod uwagę *zestawy zasobów*. Jeśli chcesz znacząco skalować określoną usługę, jaki ma wpływ na magazyny danych zaplecza, pamięci podręczne i usługi zależne? Niektóre zasoby, takie jak Cosmos DB mogą być skalowane proporcjonalnie, a wiele innych nie. Chcesz się upewnić, że nie skalujesz zasobu do punktu, w którym będzie on wyczerpać inne skojarzone zasoby.

- *Należy unikać koligacji.* Najlepszym rozwiązaniem jest upewnienie się, że węzeł nie wymaga lokalnej koligacji, często nazywanej *sesją programu Sticky Notes*. Żądanie powinno być możliwe do skierowania do dowolnego wystąpienia. Jeśli zachodzi potrzeba utrwalenia stanu, powinien on zostać zapisany w rozproszonej pamięci podręcznej, na przykład w [pamięci podręcznej usługi Azure Redis](https://azure.microsoft.com/services/cache/).

- *Skorzystaj z funkcji skalowania automatycznego platformy.* Korzystaj z wbudowanych funkcji skalowania automatycznego, jeśli jest to możliwe, a nie mechanizmów niestandardowych lub innych firm. Jeśli to możliwe, Użyj reguł skalowania zaplanowanego, aby upewnić się, że zasoby są dostępne bez opóźnień uruchamiania, ale Dodaj aktywne Skalowanie automatyczne do odpowiednich reguł, aby sprostać nieoczekiwanym zmianom popytu. Aby uzyskać więcej informacji, zobacz [wskazówki dotyczące skalowania](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)automatycznego.

- *Agresywne skalowanie w poziomie.* Ostatecznym celem jest agresywne skalowanie w poziomie, dzięki czemu można szybko zaspokoić natychmiastowe wzrosty ruchu bez utraty firmy. A następnie Skaluj w dół (czyli usunąć niepotrzebne wystąpienia), aby zachować stabilność systemu. Prostym sposobem wdrożenia tego ustawienia jest ustawienie okresu dla chłodzenia, czyli czasu oczekiwania między operacjami skalowania, do pięciu minut w przypadku dodawania zasobów oraz do 15 minut na usuwanie wystąpień.

## <a name="built-in-retry-in-services"></a>Wbudowane ponawianie próby w usługach

Zachęcamy do stosowania najlepszych rozwiązań dotyczących implementowania operacji ponownych prób w poprzedniej sekcji. Należy pamiętać, że wiele usług platformy Azure i odpowiadających im zestawów SDK klienta obejmuje również mechanizm ponawiania prób. Poniższa lista zawiera podsumowanie funkcji ponawiania prób w wielu usługach platformy Azure omówionych w tej książce:

- *Azure Cosmos DB.* Klasa <xref:Microsoft.Azure.Documents.Client.DocumentClient> z interfejsu API klienta automatycznie ponawia nieudane próby. Liczba ponownych prób i maksymalny czas oczekiwania można skonfigurować. Wyjątki zgłoszone przez interfejs API klienta to żądania, które przekraczają zasady ponawiania lub błędy nieprzejściowe.

- *Azure Redis Cache.* Klient programu Redis StackExchange używa klasy Menedżera połączeń, która obejmuje ponawianie prób przy nieudanych próbach. Można skonfigurować liczbę ponownych prób, konkretne zasady ponawiania i czas oczekiwania.

- *Azure Service Bus.* Klient Service Bus uwidacznia [klasę RetryPolicy](xref:Microsoft.ServiceBus.RetryPolicy) , która może być skonfigurowana z interwałem wycofywania, liczbą ponownych prób i <xref:Microsoft.ServiceBus.RetryExponential.TerminationTimeBuffer%2A>, która określa maksymalny czas trwania operacji. Domyślną zasadą jest dziewięć Maksymalna liczba ponownych prób z 30-sekundowym okresem wycofywania między kolejnymi próbami.

- *Azure SQL Database.* W przypadku korzystania z biblioteki [Entity Framework Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency) podano ponowną pomoc techniczną.

- *Usługa Azure Storage.* Biblioteka klienta magazynu obsługuje operacje ponawiania. Strategie różnią się w zależności od tabel, obiektów blob i kolejek usługi Azure Storage. Ponadto alternatywna ponowna próba jest przełączana między lokacjami podstawowej i pomocniczej usługi magazynu po włączeniu funkcji nadmiarowości geograficznej.

- *Event Hubs platformy Azure.* Biblioteka klienta centrum zdarzeń oferuje Właściwość RetryPolicy, która obejmuje konfigurowalną funkcję wykładniczą wycofywania.

>[!div class="step-by-step"]
>[Poprzedni](application-resiliency-patterns.md)
>[Następny](resilient-communications.md)
