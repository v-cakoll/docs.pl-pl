---
title: Podejście do wdrożenia architektury — aplikacje bezserwerowe
description: Przewodnik dotyczący różnych rozwiązań dla przedsiębiorstw jest wdrażany w chmurze z porównaniem między IaaS, PaaS, kontenerami i bezserwerowym.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c745a4eb1c6f4a00bf139100b02f31cf3327d01e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522730"
---
# <a name="architecture-deployment-approaches"></a>Podejścia do wdrażania architektury

Niezależnie od metody architektury używanej do projektowania aplikacji biznesowej, implementacja lub wdrożenie tych aplikacji może się różnić. Firmy obsługują aplikacje na wszystkich urządzeniach fizycznych niż w przypadku funkcji bezserwerowych.

## <a name="n-tier-applications"></a>Aplikacje N-warstwowe

[Wzorzec architektury N-warstwowej](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) to dojrzała architektura i po prostu odwołuje się do aplikacji, które oddzielają różne warstwy logiczne do oddzielnych warstw fizycznych. Architektura n-warstwowa jest fizyczną implementacją architektury N-warstwowej. Najbardziej typowa implementacja tej architektury obejmuje:

- Warstwa prezentacji, na przykład aplikacja internetowa.
- Warstwa dostępu do interfejsu API lub danych, taka jak interfejs API REST.
- Warstwa danych, na przykład baza danych SQL.

![Architektura N-warstwowa](./media/n-tier-architecture.png)

Rozwiązania N-warstwowe mają następujące cechy:

- Projekty są zwykle wyrównane z warstwami.
- Testowanie może się różnić w zależności od warstwy.
- Warstwy zapewniają warstwy abstrakcji, na przykład warstwa prezentacji zazwyczaj ignorujących szczegóły implementacji warstwy danych.
- Zazwyczaj warstwy współpracują tylko z sąsiednimi warstwami.
- Wersje są często zarządzane w projekcie, dlatego poziom. Prosta zmiana interfejsu API może wymagać nowej wersji całej warstwy środkowej.

Takie podejście zapewnia kilka korzyści, w tym:

- Izolacja bazy danych (często fronton nie ma bezpośredniego dostępu do zaplecza bazy danych).
- Ponowne użycie interfejsu API (na przykład klientów aplikacji mobilnych, klasycznych i internetowych może ponownie używać tych samych interfejsów API).
- Możliwość skalowania w poziomie warstw niezależnie od siebie.
- Izolacja refaktoryzacji: jedna warstwa może być Refaktoryzacja bez wpływu na inne warstwy.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Lokalna i infrastruktura jako usługa (IaaS)

Tradycyjne podejście do hostingu aplikacji wymaga zakupu sprzętu i zarządzania wszystkimi instalacjami oprogramowania, w tym systemem operacyjnym. Pierwotnie to dotyczyło kosztownych centrów danych i sprzętu fizycznego. Problemy związane z sprzętem fizycznym to wiele, w tym:

- Konieczność kupowania nadmiarowych scenariuszy "just in case" lub szczytowego zapotrzebowania na żądania.
- Zabezpieczanie fizycznego dostępu do sprzętu.
- Odpowiedzialność za awarie sprzętu (na przykład awaria dysku).
- Stosować.
- Konfigurowanie routerów i modułów równoważenia obciążenia.
- Nadmiarowość.
- Zabezpieczanie dostępu do oprogramowania.

![Podejście IaaS](./media/iaas-approach.png)

Wirtualizacja sprzętu za pośrednictwem "maszyn wirtualnych" umożliwia korzystanie z infrastruktury jako usługi (IaaS). Maszyny hosta są efektywnie partycjonowane w celu zapewnienia zasobów do wystąpień z alokacjami dla własnej pamięci, procesora i magazynu. Zespół inicjuje odpowiednie maszyny wirtualne i konfiguruje skojarzone sieci i dostęp do magazynu.

Aby uzyskać więcej informacji, zobacz [architekturę referencyjną N-warstwowej maszyny wirtualnej](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Chociaż rozwiązanie "Wirtualizacja i infrastruktura jako usługa" (IaaS) ma wiele obaw, nadal pozostaje wiele odpowiedzialności w zespole infrastruktury. Zespół zachowuje wersje systemu operacyjnego, stosuje poprawki zabezpieczeń i instaluje zależności innych firm na komputerach docelowych. Aplikacje często działają inaczej na maszynach produkcyjnych w porównaniu do środowiska testowego. Problemy powstają z powodu różnych wersji zależności i/lub poziomów jednostki SKU systemu operacyjnego. Chociaż w wielu organizacjach aplikacje N-warstwowe są wdrażane dla tych celów, wiele firm skorzystało z wdrażania do bardziej natywnego modelu chmury, takiego jak [platforma jako usługa](#platform-as-a-service-paas). Architektury z mikrousługami są trudniejsze ze względu na wymagania dotyczące elastyczności i odporności.

Aby uzyskać więcej informacji, zobacz [maszyny wirtualne](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>Platforma jako usługa (PaaS)

Platforma jako usługa (PaaS) oferuje skonfigurowane rozwiązania, które deweloperzy mogą podłączyć bezpośrednio. PaaS jest kolejnym terminem hostingu zarządzanego. Eliminuje to konieczność zarządzania podstawowymi systemami operacyjnymi, poprawkami zabezpieczeń oraz w wielu przypadkach, w których wszystkie zależności innych firm. Przykłady platform obejmują aplikacje sieci Web, bazy danych i zaplecza mobilne.

PaaS zaspokaja wyzwania typowe dla IaaS. PaaS umożliwia deweloperom skoncentrowanie się na kodzie lub schemacie bazy danych, a nie w porównaniu z ich wdrożeniem. Zalety PaaS obejmują:

- Płatność za korzystanie z modeli, które eliminują nakłady inwestycyjne w odniesieniu do bezczynnych maszyn.
- Bezpośrednie wdrożenie i udoskonalone DevOps, ciągłej integracji (CI) i ciągłe dostarczanie (CD).
- Automatyczne uaktualnienia, aktualizacje i poprawki zabezpieczeń.
- Wypchnij przycisk w poziomie i Skaluj w górę (elastyczne skalowanie).

Główną wadą PaaS tradycyjnie jest blokada dostawcy. Na przykład niektórzy dostawcy PaaS obsługują tylko ASP.NET, Node. js i inne określone Języki i platformy. Produkty takie jak Azure App Service uległy rozwojem wielu platform i obsługują różne języki i struktury do hostowania aplikacji sieci Web.

![Platforma jako Architektura usługi](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Oprogramowanie jako usługa (SaaS)

Oprogramowanie jako usługa lub SaaS jest centralnie hostowane i dostępne bez konieczności instalacji lokalnej ani aprowizacji. SaaS często jest hostowany na PaaS jako platforma do wdrażania oprogramowania. SaaS zapewnia usługi do uruchamiania i łączenia z istniejącym oprogramowaniem. SaaS jest często charakterystyczne dla branż i w pionie. SaaS jest często licencjonowane i zazwyczaj udostępnia model klient/serwer. Większość nowoczesnych ofert SaaS korzysta z aplikacji sieci Web dla klienta. Firmy zwykle rozważają SaaS jako rozwiązanie biznesowe do ofert licencji. Nie jest to często implementowane jako zagadnienia dotyczące skalowalności i utrzymania aplikacji. W rzeczywistości większość rozwiązań SaaS jest oparta na zapleczu IaaS, PaaS i/lub bezserwerowym.

Dowiedz się więcej na temat SaaS za pomocą [przykładowej aplikacji](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Kontenery i funkcje jako usługa (FaaS)

Kontenery to interesujące rozwiązanie, które zapewnia korzyści podobne do PaaS bez narzutu IaaS. Kontener to zasadniczo środowisko uruchomieniowe, które zawiera system operacyjnego, który jest wymagany do uruchomienia unikatowej aplikacji. Jądro lub rdzeń systemu operacyjnego hosta, takich jak magazyn, jest współużytkowany przez hosta. Udostępnione jądro umożliwia lekkie korzystanie z kontenerów (niektóre są zwykle w megabajtach w porównaniu z rozmiarem gigabajtów typowych maszyn wirtualnych). Dzięki już uruchomionym hostom można szybko uruchamiać kontenery, co ułatwia wysoką dostępność. Możliwość szybkiego rozłożonego kontenerów zapewnia również dodatkowe warstwy odporności. Platforma Docker jest jednym z bardziej popularnych implementacji kontenerów.

Zalety kontenerów obejmują:

- Lekki i przenośny
- Samodzielny, więc nie trzeba instalować zależności
- Zapewnianie spójnego środowiska bez względu na to, że host (działa tak samo na laptopie jak na serwerze w chmurze)
- Możliwość szybkiego aprowizacji w celu skalowania w poziomie
- Można szybko uruchomić ponownie, aby odzyskać sprawność po awarii

Kontener jest uruchamiany na hoście kontenera (który z kolei może działać na komputerze bez systemu operacyjnego lub maszynie wirtualnej). Wiele kontenerów lub wystąpień tych samych kontenerów może działać na jednym hoście. W przypadku prawdziwej pracy awaryjnej i odporności kontenery muszą być skalowane między hostami.

Aby uzyskać więcej informacji na temat kontenerów platformy Docker, zobacz [co to jest platforma Docker](../microservices/container-docker-introduction/docker-defined.md).

Zarządzanie kontenerami między hostami wymaga zwykle narzędzia Orchestration, takiego jak Kubernetes. Konfigurowanie rozwiązań aranżacji i zarządzanie nimi może zwiększyć obciążenie i złożoność projektów. Na szczęście wielu dostawców chmury zapewnia usługi aranżacji za pomocą rozwiązań PaaS, co upraszcza zarządzanie kontenerami.

Na poniższej ilustracji przedstawiono przykładową instalację Kubernetes. Węzły w adresie instalacji skalowanie w poziomie i w trybie failover. Uruchamiają one wystąpienia kontenerów platformy Docker, które są zarządzane przez serwer główny. *Kubelet* to klient, który przekazuje polecenia z Kubernetes do platformy Docker.

![Kubernetes](./media/kubernetes-example.png)

Aby uzyskać więcej informacji o aranżacji, zobacz [Kubernetes na platformie Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Funkcja jako usługa (FaaS) to wyspecjalizowana Usługa kontenera, która jest podobna do bezserwerowej. Określona implementacja FaaS o nazwie [OpenFaaS](https://github.com/openfaas/faas)znajduje się na szczycie kontenerów w celu zapewnienia bezserwerowych funkcji. OpenFaaS udostępnia szablony, które pakują wszystkie zależności kontenera niezbędne do uruchomienia fragmentu kodu. Używanie szablonów upraszcza proces wdrażania kodu jako jednostki funkcjonalnej. OpenFaaS docelowe architektury, które zawierają już kontenery i Koordynatory, ponieważ mogą korzystać z istniejącej infrastruktury programu. Chociaż oferuje ona funkcje bezserwerowe, w tym celu należy użyć platformy Docker i programu Orchestrator.

## <a name="serverless"></a>Bezserwerowej

Architektura bezserwerowa zapewnia wyraźne rozdzielenie kodu i jego środowiska hostingu. Zaimplementuj kod w *funkcji* , która jest wywoływana przez *wyzwalacz*. Po zakończeniu tej funkcji wszystkie jej zasoby muszą być zwolnione. Wyzwalacz może być ręczny, proces przekroczenia limitu czasu, żądanie HTTP lub przekazywanie pliku. Wynikiem wyzwalacza jest wykonanie kodu. Chociaż platformy bezserwerowe różnią się, większość zapewniają dostęp do wstępnie zdefiniowanych interfejsów API i powiązań, aby usprawnić zadania, takie jak zapisywanie w bazie danych lub kolejkowanie wyników.

Bezserwerowy jest architekturą, która opiera się głównie na abstrakcji środowiska hosta, aby skoncentrować się na kodzie. Może być uważany za *mniej niż serwer*.

Rozwiązania kontenerów udostępniają deweloperom istniejące skrypty kompilacji do publikowania kodu w obrazach gotowych do używania z serwerem. Inne implementacje używają istniejących rozwiązań PaaS, aby zapewnić skalowalną architekturę.

Streszczenie oznacza, że zespół DevOps nie musi inicjować obsługi administracyjnej serwerów ani nie zarządzać nimi ani określonych kontenerów. Platforma bezserwerowa obsługuje kod, jako skrypt lub spakowane pliki wykonywalne utworzone przy użyciu powiązanego zestawu SDK, i przydziela zasoby niezbędne do skalowania kodu.

Na poniższej ilustracji przedstawiono wykresy czterech składników bezserwerowych. Żądanie HTTP powoduje uruchomienie kodu interfejsu API wyewidencjonowania. Interfejs API wyewidencjonowywania wstawia kod do bazy danych, a INSERT wyzwala kilka innych funkcji do uruchomienia w celu wykonywania zadań, takich jak przetwarzanie zadań i zrealizowanie zamówienia.

![Implementacja bezserwerowa](./media/serverless-implementation.png)

Zalety serwera obejmują:

- **Wysoka gęstość.** Wiele wystąpień tego samego kodu bezserwerowego można uruchomić na tym samym hoście w porównaniu z kontenerami lub maszynami wirtualnymi. Wystąpienia są skalowane na wielu hostach w poziomie i w odporności.
- **Rozliczanie.** Większość dostawców bezserwerowych jest rozliczana na podstawie wykonań bezserwerowych, co zapewnia duże oszczędności kosztów w niektórych scenariuszach.
- **Natychmiastowa Skala.** Bezserwerowe skalowanie może być skalowane w celu automatycznego i szybkiego dopasowania obciążeń.
- **Krótszy czas wprowadzenia na rynek.** Deweloperzy koncentrują się na kodzie i wdrażają bezpośrednio na platformie bezserwerowej. Składniki mogą być wydzierżawione niezależnie od siebie.

Bezserwerowe jest najczęściej omawiane w kontekście obliczeń, ale mogą również dotyczyć danych. Na przykład baza danych [SQL platformy Azure i usługa](https://docs.microsoft.com/azure/sql-database) [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) są w chmurze, które nie wymagają konfigurowania maszyn lub klastrów hostów. Ta książka koncentruje się na obliczeniach bezserwerowych.

## <a name="summary"></a>Podsumowanie

Istnieje szeroki zakres dostępnych opcji architektury, w tym podejście hybrydowe. Bezserwerowy upraszcza podejście, zarządzanie i koszt funkcji aplikacji przy kosztach kontroli i przenośności. Jednak wiele platform bezserwerowych uwidacznia konfigurację, aby ułatwić dostosowanie rozwiązania. Dobre praktyki programistyczne mogą również prowadzić do bardziej przenośnego kodu i mniejszej blokady platformy bezserwerowej. W poniższej tabeli przedstawiono podejścia do architektury obok siebie. Wybierz opcję bezserwerowa zależna od potrzeb skalowania, niezależnie od tego, czy chcesz zarządzać środowiskiem uruchomieniowym, a także jak można przerwać obciążenia w małych składnikach. Zapoznaj się z potencjalnymi wyzwaniami dotyczącymi bezserwerowych i innych decyzji w następnym rozdziale.

|         |IaaS     |PaaS     |wbudowane|Bezserwerowej|
|---------|---------|---------|---------|----------|
|**Zasięgu**|MASZYN       |Wystąpienie |Aplikacje      |Funkcja  |
|**Streszczenia**|Sprzęt|Platforma|Host systemu operacyjnego|Środowisko uruchomieniowe   |
|**Jednostka** |MASZYN       |Projekt  |Obraz    |Kod      |
|**Cykl życia**|Od|Dni do miesięcy|Minuty na dni|Milisekundy na minuty|
|**Odpowiedzialność za**|Aplikacje, zależności, środowisko uruchomieniowe i system operacyjny|Aplikacje i zależności|Aplikacje, zależności i środowisko uruchomieniowe|Funkcja

- **Skala** odnosi się do jednostki, która jest używana do skalowania aplikacji.
- **Streszczenia** odnosi się do warstwy, która jest abstrakcyjna przez implementację
- **Jednostka** odnosi się do zakresu wdrożenia
- **Okres istnienia** dotyczy typowego środowiska uruchomieniowego określonego wystąpienia
- **Odpowiedzialność** dotyczy narzutów związanych z kompilowaniem, wdrażaniem i konserwacją aplikacji

Następny rozdział koncentruje się na architekturze bezserwerowej, przypadków użycia i wzorcach projektowych.

## <a name="recommended-resources"></a>Zalecane zasoby

- [Przewodnik po architekturze aplikacji platformy Azure](https://docs.microsoft.com/azure/architecture/guide/)
- [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
- [Azure SQL](https://docs.microsoft.com/azure/sql-database)
- [Wzorzec architektury N-warstwowej](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
- [Kubernetes na platformie Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)
- [Mikrousług](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
- [Architektura referencyjna N-warstwowej maszyny wirtualnej](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
- [Maszyny wirtualne](https://docs.microsoft.com/azure/virtual-machines/)
- [Co to jest Docker?](../microservices/container-docker-introduction/docker-defined.md)
- [Wingtip bilety SaaS aplikacji](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Poprzedni](architecture-approaches.md)
>[dalej](serverless-architecture.md)
