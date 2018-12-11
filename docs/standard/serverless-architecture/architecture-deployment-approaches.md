---
title: Architektura wdrożenia podejścia — aplikacje niekorzystające z serwera
description: Przewodnik dotyczący architektury przedsiębiorstwa różne sposoby są wdrożone w chmurze, z funkcją porównania między IaaS, PaaS, kontenery i bez użycia serwera.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5477b8c4531780fdebf194e4f798564e59cd2953
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152672"
---
# <a name="architecture-deployment-approaches"></a>Metody wdrażania dotyczące architektury

Niezależnie od architektury podejście do projektowania aplikacji biznesowej, wykonania lub wdrożenia tych aplikacji może się różnić. Firmom udostępnić aplikacjom bezserwerowym na wszystko — od sprzętu fizycznego.

## <a name="n-tier-applications"></a>N-warstwowych

[Wzorzec architektury N-warstwowa](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) to dojrzała architektura i odwołujący się do aplikacji, które rozdzielają różne warstwy logiczne w oddzielne warstwy fizyczne. Architektura N-warstwowa jest fizyczna implementacja architektury N-warstwy. Najbardziej typowe wdrożenia tej architektury obejmują:

* Warstwa prezentacji, na przykład aplikacja sieci web.
* Interfejs API lub danych warstwy dostępu, takich jak interfejs API REST.
* Warstwa danych, takich jak bazy danych SQL.

![Architektury N-warstwowej](./media/n-tier-architecture.png)

N-warstwowa rozwiązania mają następującą charakterystykę:

* Projekty zazwyczaj są wyrównane z warstwami.
* Testowanie może być w stanie inaczej przez warstwę.
* Warstwy zapewniają warstwy abstrakcji, na przykład Warstwa prezentacji zwykle zakresu o szczegóły implementacji warstwy danych.
* Zazwyczaj warstwy komunikować się tylko z sąsiednie warstwy.
* Zwalnia często są zarządzane w projekcie, a w związku z tym warstwy, poziom. Proste zmiany interfejsu API mogą wymagać nowej wersji całej warstwy środkowej.

To podejście zapewnia kilka korzyści, w tym:

* Izolacja bazy danych (często frontonu nie mają bezpośredniego dostępu do wewnętrznej bazy danych).
* Ponowne używanie interfejsu API (na przykład, mobilnych, klasycznych i klientów w aplikacji sieci web mogą wszystkie ponowne użycie tych samych interfejsów API).
* Możliwość skalowania w poziomie warstwy od siebie niezależne.
* Refaktoryzacja izolacji: jedna warstwa może być refaktoryzowany bez wywierania wpływu na pozostałe warstwy.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>W środowisku lokalnym i infrastruktura jako usługa (IaaS)

Tradycyjne podejście do hostowania aplikacji wymaga zakupu sprzętu i zarządzania nimi, wszystkie instalacje oprogramowania, łącznie z systemem operacyjnym. Pierwotnie to zaangażowane centrów danych kosztowne i sprzęcie fizycznym. Problemy, które wynikają z pracą sprzęcie fizycznym jest duża, w tym:

* Musisz kupić nadmiar na "tylko w przypadku" lub szczytowego zapotrzebowania scenariuszy.
* Zabezpieczanie fizyczny dostęp do sprzętu.
* Odpowiedzialność za awaria sprzętu (na przykład awaria dysku).
* Chłodzenie.
* Konfigurowanie routery i moduły równoważenia obciążenia.
* Nadmiarowość zasilania.
* Zabezpieczanie dostępu do oprogramowania.

![Podejście IaaS](./media/iaas-approach.png)

Wirtualizacja sprzętu za pomocą "maszyny wirtualne" umożliwia infrastruktura jako usługa (IaaS). Komputery-hosty skutecznie są podzielone na partycje zapewnienie zasobów do wystąpień alokacji własnych pamięci, procesora CPU i pamięci masowej. Zespół przepisy prawa niezbędne maszyn wirtualnych i konfiguruje skojarzonych sieci i dostęp do magazynu.

Aby uzyskać więcej informacji, zobacz [maszynę wirtualną N-warstwowej architekturze referencyjnej](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Chociaż wirtualizacja i infrastruktura jako usługa (IaaS) rozwiązać wiele problemów, nadal pozostawia dużo odpowiedzialność w ręce infrastruktury. Zespół zachowuje wersje systemu operacyjnego, zastosowanie poprawek zabezpieczeń i zainstalowanie zależności innych firm na komputerach docelowych. Aplikacje często zachowywać się inaczej na komputerach produkcyjnych w porównaniu do środowiska testowego. Problemów ze względu na zależność różnych wersji i/lub poziomach jednostka SKU systemu operacyjnego. Chociaż w wielu organizacjach wdrażania aplikacji N-warstwowa te obiekty docelowe, wiele firm korzystają z wdrażania do modelu natywnych w chmurze więcej takich jak [platforma jako usługa](#platform-as-a-service-paas). Architektury przy użyciu mikrousług jest trudniejsze ze względu na wymagania skalowania w poziomie w celu zapewnienia elastyczności i odporności.

Aby uzyskać więcej informacji, zobacz [maszyn wirtualnych](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>Platforma jako usługa (PaaS)

Platforma jako usługa (PaaS) oferuje skonfigurowane rozwiązania, które deweloperzy mogą podłączyć bezpośrednio do. PaaS jest inny termin do zarządzanego hostingu. Eliminuje to konieczność zarządzania podstawowego systemu operacyjnego, poprawki zabezpieczeń i w wielu przypadkach wszelkie zależności innych firm. Platform przykłady aplikacji sieci web, baz danych i zaplecza aplikacji mobilnych.

PaaS sprostać wyzwaniom, które są wspólne dla IaaS. PaaS umożliwia deweloperom skoncentrowanie się na schemat kodu lub bazy danych, a nie jak zostanie wdrożona. Zalety rozwiązania paas, obejmują:

* Płać modeli użycia, które wyeliminować inwestowania w przypadku bezczynności maszyn.
* Bezpośrednie wdrożenie i ulepszone metodyki DevOps, ciągłej integracji (CI) i potoków ciągłego dostarczania (polecenie CD).
* Automatyczne uaktualnienia, aktualizacji i poprawek zabezpieczeń.
* Z przyciskiem skalowania w poziomie i skalowanie w górę (elastyczne skalowanie).

Główną wadą PaaS tradycyjnie była blokady w dostawcy. Na przykład niektórzy dostawcy PaaS obsługują tylko, ASP.NET, Node.js lub innych określonych języków i platform. Produktów, takich jak usługa Azure App Service rozwinęły się w kierunku rozwiązać wiele platform i obsługi różnych języków i platform do hostowania aplikacji sieci web.

![Platforma jako architektura usługi](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Oprogramowanie jako usługa (SaaS)

Oprogramowanie jako usługa lub infrastrukturą SaaS jest centralnie hostowanych i dostępne bez konieczności instalacji lokalnej lub inicjowania obsługi administracyjnej. SaaS często znajduje się na górze PaaS jako platforma do wdrażania oprogramowania. SaaS oferują usługi do uruchamiania i połącz się z istniejącego oprogramowania. SaaS jest często w branży i specyficznych dla pionowy. SaaS często jest licencjonowana i zwykle zapewnia modelu klient/serwer. Większość nowoczesnych ofertami SaaS na użytek aplikacji opartych na sieci web klienta. Firmy zwykle należy wziąć pod uwagę SaaS jako rozwiązanie firmy do ofert licencji. Nie jest ona często zaimplementowane jako architektura brany pod uwagę skalowalność i łatwość konserwacji aplikacji. W rzeczywistości większość rozwiązań SaaS są tworzone w modelu IaaS, PaaS i/lub bez użycia serwera zaplecza.

Dowiedz się więcej o rozwiązaniu SaaS za pośrednictwem [Przykładowa aplikacja](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Kontenery i funkcjonuje jako usługi (FaaS)

Kontenery są interesujące rozwiązanie, które umożliwia korzyści podobnych PaaS bez konieczności IaaS. Kontener jest zasadniczo środowiska uruchomieniowego, które zawiera podstawy systemu od zera, potrzebnych do uruchomienia aplikacji unikatowy. Jądra lub core część systemu operacyjnego hosta i usług, takich jak magazyn są współdzielone przez hosta. Udostępnione jądra umożliwia kontenerów (niektóre są zwykłe MB, w porównaniu do rozmiaru gigabajtów Typowa maszyn wirtualnych). Z hostami już uruchomione kontenery można uruchomić szybkie, ułatwienia wysokiej dostępności. Możliwość szybkiego uruchamiaj kontenery są także dodatkowe warstwy odporności. Docker jest jednym z najpopularniejszych wdrożeń kontenerów.

Kontenery korzyści:

* Lekkie i przenośna
* Niezależna więc nie trzeba instalować zależności
* Zapewnić spójne środowisko niezależnie od hosta (działa dokładnie tych samych na laptopie na serwerze chmury)
* Można szybko aprowizować dla skalowalnego w poziomie
* Można ponownie uruchomić szybkiego odzyskiwania po awarii

Kontener działa na hoście kontenera, (które z kolei mogą być uruchomione na maszynie bez systemu operacyjnego lub maszynie wirtualnej). Wiele kontenerów lub wystąpień tych samych kontenerów może działać na jednym hoście. Wartość true, pracy awaryjnej i zwiększa odporność kontenerów musi być zwiększana na hostach.

Aby uzyskać więcej informacji na temat kontenerów platformy Docker, zobacz [co to jest Docker](../microservices-architecture/container-docker-introduction/docker-defined.md)?

Zarządzanie kontenerami na hostach zwykle wymaga narzędzia aranżacji, takich jak Kubernetes. Konfigurowanie i zarządzanie nimi aranżacji rozwiązań może dodać dodatkowe obciążenie i złożoność projektów. Na szczęście wielu dostawców rozwiązań w chmurze świadczenia usług aranżacji za pośrednictwem rozwiązania PaaS, aby uprościć zarządzanie kontenerów.

Na poniższym obrazie przedstawiono przykład instalacji usługi Kubernetes. Węzły w instalacji adresów skalowania w poziomie i trybu failover. Działają one Docker wystąpień kontenera, które są zarządzane przez serwer główny. *Agenta kubelet* to klient, który przekazuje poleceń usługi Kubernetes do platformy Docker.

![Kubernetes](./media/kubernetes-example.png)

Aby uzyskać więcej informacji na temat organizowania zobacz [Kubernetes na platformie Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Funkcje jako usługa (FaaS) to usługa wyspecjalizowane kontenera, która jest podobna do bez użycia serwera. Określonej implementacji FaaS, o nazwie [usługi OpenFaaS](https://github.com/openfaas/faas), znajduje się na górze kontenerów w celu zapewnienia możliwości bez użycia serwera. Usługi OpenFaaS zapewnia szablony, które wszystkie niezbędne do uruchomienia fragment kodu zależności kontenera pakietu. Za pomocą szablonów upraszcza proces wdrażania kodu jednostkę funkcjonalną. Usługi OpenFaaS jest przeznaczony dla architektur, które już zawierają kontenerów i koordynatorów, ponieważ można użyć istniejącej infrastruktury. Chociaż dostarcza funkcję, bez użycia serwera, w szczególności wymaga przy użyciu platform Docker i orkiestrator.

## <a name="serverless"></a>Bez użycia serwera

Architektura bezserwerowa zapewnia separacji między kodem i jego środowisko hostingu. Możesz wdrożyć kod w *funkcja* , wywoływany przez *wyzwalacza*. Po zakończeniu tej funkcji, wszystkie wymagane zasoby mogą zostać uwolniona. Wyzwalacz może być ręczne "," Przekroczono limit czasu procesu "," żądanie HTTP "lub" przekazywanie pliku. Wynikiem wyzwalacza jest wykonywanie kodu. Chociaż różnią się platform bezserwerowych, najbardziej zapewniają dostęp do wstępnie zdefiniowanych interfejsów API i powiązania, aby usprawnić zadania, takie jak zapisywanie do bazy danych lub Kolejkowanie wyników.

Bez użycia serwera to architektura, która intensywnie korzysta z troszczyć środowisko hosta, aby skoncentrować się na kodzie. Jego można traktować jako *mniej serwera*.

Rozwiązań do obsługi kontenerów zapewnia deweloperom istniejące tworzenia skryptów do publikowania kodu bez użycia serwera gotowych do użycia obrazy. Inne implementacje Użyj istniejących rozwiązań PaaS, aby dostarczyć Skalowalna architektura.

Abstrakcja oznacza, że zespół DevOps nie ma obsługi administracyjnej ani zarządzać nimi serwerów ani określonych kontenerów. Kod hosty platformą bez użycia serwera, skrypt i spakowane pliki wykonywalne utworzonych za pomocą powiązanych zestawu SDK i przydziela zasoby wymagane dla kodu do skalowania.

Na poniższej ilustracji diagramy cztery składniki bez użycia serwera. Żądanie HTTP powoduje uruchomienie kodu realizacji transakcji interfejsu API. Interfejs API wyewidencjonowania wstawia kodu do bazy danych i Wstaw wyzwala kilka innych funkcji, aby uruchomić, aby wykonywać zadania takie jak przetwarzanie zadań i realizując.

![Implementacja bez użycia serwera](./media/serverless-implementation.png)

Zalety bez użycia serwera obejmują:

* **O wysokiej gęstości.** Wiele wystąpień tego samego kodu bez użycia serwera mogą działać na tym samym hoście, w porównaniu do kontenerów i maszyn wirtualnych. Skaluj wystąpienia w wielu hostów skalowanie i zwiększa odporność.
* **Rozliczenia Micro**. Najbardziej bezserwerowe rachunek dostawców oparte na wykonań bez użycia serwera, włączanie ogromne oszczędności w niektórych scenariuszach.
* **Natychmiastowe skalowanie**. Aplikacje niewymagające użycia serwera można skalować w celu dopasowania obciążenia, automatyczne i szybko.
* **Krótszy czas wprowadzenia na rynek** deweloperom skupić się na kodzie i wdróż bezpośrednio z platformą bez użycia serwera. Składniki może być zwolnione niezależnie od siebie nawzajem.

Aplikacje niewymagające użycia serwera w większości przypadków jest omówione w mocy obliczeniowej, ale można także zastosować do danych. Na przykład [Azure SQL](https://docs.microsoft.com/azure/sql-database) i [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) udostępniają baz danych w chmurze, które nie wymagają skonfigurowania komputerów-hostów lub klastrów. Ten podręcznik koncentruje się na bezserwerowe środowisko obliczeniowe.

## <a name="summary"></a>Podsumowanie

Istnieje szerokie spektrum dostępne opcje architektury, w tym podejście hybrydowe. Aplikacje niewymagające użycia serwera upraszcza podejście, zarządzanie i koszt funkcje aplikacji kosztem kontroli i przenośność. Jednak wiele platform bezserwerowych ujawniaj konfigurację, aby pomóc dostosować rozwiązanie. Dobre praktyki programowania również może prowadzić do bardziej przenośny kod i mniej blokady w platformą bez użycia serwera. W poniższej tabeli przedstawiono metody dotyczące architektury obok siebie. Wybierz bez użycia serwera, na podstawie skalowania potrzeby, czy mają być zarządzane w środowisku uruchomieniowym i jak można podzielić obciążeń małych składników. Poznasz potencjalne wyzwania związane z rozwiązaniami bezserwerowymi i inne punkty decyzyjne, w następnym rozdziale.

|         |IaaS     |PaaS     |Kontener|Bez użycia serwera|
|---------|---------|---------|---------|----------|
|**Skala**|VM       |Wystąpienie |Aplikacja      |Funkcja  |
|**Abstract**|Sprzęt|Platforma|System operacyjny hosta|Środowisko uruchomieniowe   |
|**Unit** |VM       |Projekt  |Obraz    |Kod      |
|**Okres istnienia**|Miesiące|Liczba dni, miesięcy|Minut do dni|Milisekund minut|
|**Odpowiedzialność**|Aplikacje, zależności, środowisko uruchomieniowe i systemu operacyjnego|Aplikacje i zależności|Aplikacje, zależności i środowiska uruchomieniowego|Funkcja

* **Skala** odwołuje się do jednostki, która umożliwia skalowanie aplikacji
* **Przenosi** odwołuje się do warstwy, która jest wyodrębniony przez implementację
* **Jednostka** odwołuje się do zakresu co to jest wdrożony
* **Okres istnienia** odwołuje się do typowy czas wykonywania określonego wystąpienia
* **Odpowiedzialność za** odwołuje się do obciążenia tworzenie, wdrażanie i obsługa aplikacji

Następny rozdział skupić się na architekturze bezserwerowej, przypadki użycia i wzorce projektowe.

## <a name="recommended-resources"></a>Zalecane zasoby

* [Przewodnik dotyczący architektury aplikacji platformy Azure](https://docs.microsoft.com/azure/architecture/guide/)
* [Usługi Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
* [Usługi Azure SQL](https://docs.microsoft.com/azure/sql-database)
* [Wzorzec architektury N-warstwowej](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
* [Kubernetes na platformie Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)
* [Mikrousługi](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
* [Architektura referencyjna N-warstwowa maszyny wirtualnej](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
* [Maszyny wirtualne](https://docs.microsoft.com/azure/virtual-machines/)
* [Co to jest Docker?](../microservices-architecture/container-docker-introduction/docker-defined.md)
* [Aplikacja SaaS biletów o nazwie Wingtip](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Poprzednie](architecture-approaches.md)
>[dalej](serverless-architecture.md)