---
title: Podejścia do wdrażania architektury — aplikacje bezserwerowe
description: Przewodnik po różnych sposobach wdrażania architektur przedsiębiorstwa w chmurze, z porównaniem iaaS, PaaS, kontenerów i bezserwerowych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c745a4eb1c6f4a00bf139100b02f31cf3327d01e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522730"
---
# <a name="architecture-deployment-approaches"></a>Podejścia do wdrażania architektury

Niezależnie od podejścia architektury używanego do projektowania aplikacji biznesowej implementacja lub wdrażanie tych aplikacji mogą się różnić. Firmy hostują aplikacje na wszystkich urządzeniach, od sprzętu fizycznego po funkcje bezserwerowe.

## <a name="n-tier-applications"></a>Aplikacje N-warstwowe

[Wzorzec architektury N-Warstwa](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) jest dojrzałą architekturą i po prostu odwołuje się do aplikacji, które oddzielają różne warstwy logiczne w oddzielnych warstwach fizycznych. Architektura n-warstwowa jest fizyczną implementacją architektury N-Layer. Najbardziej typowe implementacji tej architektury obejmuje:

- Warstwa prezentacji, na przykład aplikacja sieci web.
- Interfejs API lub warstwy dostępu do danych, takich jak interfejs API REST.
- Warstwa danych, takich jak baza danych SQL.

![Architektura n-warstwowa](./media/n-tier-architecture.png)

Rozwiązania n-warstwowe mają następujące właściwości:

- Projekty są zazwyczaj wyrównane z warstwami.
- Testowanie może być podchodzić inaczej przez warstwę.
- Warstwy zapewniają warstwy abstrakcji, na przykład warstwa prezentacji jest zazwyczaj nieświadomy szczegółów implementacji warstwy danych.
- Zazwyczaj warstwy oddziałują tylko z sąsiednimi warstwami.
- Wersje są często zarządzane na poziomie projektu, a zatem warstwy. Prosta zmiana interfejsu API może wymagać nowej wersji całej warstwy środkowej.

Takie podejście zapewnia kilka korzyści, w tym:

- Izolacja bazy danych (często fronton nie ma bezpośredniego dostępu do zaplecza bazy danych).
- Ponowne użycie interfejsu API (na przykład klienci aplikacji mobilnych, stacjonarnych i internetowych mogą ponownie używać tych samych interfejsów API).
- Możliwość skalowania w poziomie poziomów niezależnych od siebie.
- Izolacja refaktoryzacji: jeden warstwa może być refaktoryzacji bez wpływu na inne warstwy.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Lokalnie i infrastruktura jako usługa (IaaS)

Tradycyjne podejście do hostingu aplikacji wymaga zakupu sprzętu i zarządzania wszystkimi instalacjami oprogramowania, w tym systemem operacyjnym. Początkowo wiązało się to z drogimi centrami danych i sprzętem fizycznym. Wyzwania związane z obsługą sprzętu fizycznego są liczne, w tym:

- Konieczność zakupu nadwyżki dla "na wszelki wypadek" lub szczytowych scenariuszy popytu.
- Zapewnienie fizycznego dostępu do sprzętu.
- Odpowiedzialność za awarię sprzętu (na przykład awarię dysku).
- Chłodzenia.
- Konfigurowanie routerów i modułów równoważenia obciążenia.
- Nadmiarowość zasilania.
- Zabezpieczanie dostępu do oprogramowania.

![Podejście IaaS](./media/iaas-approach.png)

Wirtualizacja sprzętu za pośrednictwem "maszyn wirtualnych" umożliwia infrastrukturę jako usługę (IaaS). Maszyny hosta są skutecznie podzielony na partycje, aby zapewnić zasoby do wystąpień z alokacji dla własnej pamięci, procesora CPU i magazynu. Zespół aprowizacje niezbędnych maszyn wirtualnych i konfiguruje skojarzone sieci i dostęp do magazynu.

Aby uzyskać więcej informacji, zobacz [architektura odwołań dla maszyn n-warstwowych maszyny wirtualnej](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Chociaż wirtualizacja i infrastruktura jako usługa (IaaS) rozwiązają wiele problemów, nadal pozostawia wiele odpowiedzialności w rękach zespołu infrastruktury. Zespół przechowuje wersje systemu operacyjnego, stosuje poprawki zabezpieczeń i instaluje zależności innych firm na komputerach docelowych. Aplikacje często zachowują się inaczej na maszynach produkcyjnych w porównaniu ze środowiskiem testowym. Problemy powstają z powodu różnych wersji zależności i/lub poziomów sku SKU systemu operacyjnego. Chociaż wiele organizacji wdraża aplikacje n-warstwowe do tych obiektów docelowych, wiele firm korzysta z wdrażania w modelu natywnym w chmurze, takim jak [Platformas as a Service.](#platform-as-a-service-paas) Architektury z mikrousług są trudniejsze ze względu na wymagania, aby skalować w sposób skalowany w sposób skalowany w sposób elastyczny i odporności.

Aby uzyskać więcej informacji, zobacz [maszyny wirtualne](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>Platforma jako usługa (PaaS)

Platformas as a Service (PaaS) oferuje skonfigurowane rozwiązania, które deweloperzy mogą podłączyć bezpośrednio. PaaS to kolejny termin dla zarządzanego hostingu. Eliminuje konieczność zarządzania podstawowym systemem operacyjnym, poprawek zabezpieczeń i w wielu przypadkach wszelkich zależności innych firm. Przykłady platform obejmują aplikacje internetowe, bazy danych i zaplecze mobilne.

PaaS zajmuje się wyzwaniami wspólnymi dla IaaS. PaaS umożliwia deweloperowi skupić się na schemacie kodu lub bazy danych, a nie jak zostanie wdrożony. Korzyści z PaaS obejmują:

- Zapłać za modele użytkowe, które eliminują obciążenie inwestowaniem w maszyny bezczynne.
- Bezpośrednie wdrażanie i ulepszone polecenia DevOps, ciągła integracja (CI) i ciągłe dostarczanie (CD).
- Automatyczne uaktualnienia, aktualizacje i poprawki zabezpieczeń.
- Za pomocą przycisku można skalować w górę i skalować w górę (skala elastyczna).

Główną wadą PaaS tradycyjnie był blokada dostawcy. Na przykład niektórzy dostawcy PaaS obsługują tylko ASP.NET, Node.js lub inne określone języki i platformy. Produkty, takie jak usługa Azure App Service, ewoluowały, aby rozwiązać wiele platform i obsługiwać różne języki i struktury do hostowania aplikacji sieci web.

![Platforma jako architektura usług](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Oprogramowanie jako usługa (SaaS)

Oprogramowanie jako usługa lub SaaS jest centralnie hostowane i dostępne bez lokalnej instalacji lub obsługi administracyjnej. SaaS często jest hostowany na górze PaaS jako platforma do wdrażania oprogramowania. SaaS świadczy usługi uruchamiania i łączenia się z istniejącym oprogramowaniem. SaaS jest często specyficzne dla przemysłu i pionu. SaaS jest często licencjonowany i zazwyczaj zapewnia model klient/serwer. Większość nowoczesnych ofert SaaS korzysta z aplikacji internetowych dla klienta. Firmy zazwyczaj uważają SaaS za rozwiązanie biznesowe do licencjonowania ofert. Nie jest często implementowane jako zagadnienia architektury dla skalowalności i łatwość konserwacji aplikacji. W rzeczywistości większość rozwiązań SaaS jest zbudowana na iaaS, PaaS i/lub bezserwerowych tylnych końcach.

Dowiedz się więcej o SaaS za pośrednictwem [przykładowej aplikacji](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Kontenery i funkcje jako usługa (FaaS)

Kontenery są ciekawym rozwiązaniem, które umożliwia korzyści podobne do PaaS bez narzutów IaaS. Kontener jest zasadniczo w czasie wykonywania, który zawiera niegdysione podstawowe potrzebne do uruchomienia aplikacji unikatowy. Jądro lub podstawowa część systemu operacyjnego hosta i usług, takich jak magazyn, są współużytkowane przez hosta. Udostępnione jądro umożliwia kontenery być lekkie (niektóre są tylko megabajty w rozmiarze, w porównaniu do wielkości gigabajtów typowych maszyn wirtualnych). Dzięki już uruchomionym hostom kontenery można szybko uruchomić, co ułatwia wysoką dostępność. Możliwość szybkiego rozkręcenia pojemników zapewnia również dodatkowe warstwy odporności. Docker jest jednym z bardziej popularnych implementacji kontenerów.

Zalety kontenerów obejmują:

- Lekki i przenośny
- Niezależne, więc nie ma potrzeby instalowania zależności
- Zapewnij spójne środowisko niezależnie od hosta (działa dokładnie tak samo na laptopie, jak na serwerze w chmurze)
- Może być szybko aprowizowany w celu skalowania w czasie
- Można szybko uruchomić ponownie, aby odzyskać po awarii

Kontener jest uruchamiany na hoście kontenera (który z kolei może działać na bezlitosnej maszynie metalowej lub maszynie wirtualnej). Wiele kontenerów lub wystąpień tych samych kontenerów może działać na jednym hoście. W przypadku true pracy awaryjnej i odporności kontenery muszą być skalowane między hostami.

Aby uzyskać więcej informacji na temat kontenerów platformy Docker, zobacz [Co to jest platforma Docker](../microservices/container-docker-introduction/docker-defined.md).

Zarządzanie kontenerami między hostami zazwyczaj wymaga narzędzia aranżacji, takiego jak Kubernetes. Konfigurowanie rozwiązań aranżacji i zarządzanie nimi może zwiększyć obciążenie i złożoność projektów. Na szczęście wielu dostawców chmury świadczy usługi aranżacji za pośrednictwem rozwiązań PaaS, aby uprościć zarządzanie kontenerami.

Na poniższej ilustracji przedstawiono przykładinstalacji Kubernetes. Węzły w adresie instalacji skalowania w sposób skalowany i pracy awaryjnej. Uruchamiają wystąpienia kontenerów platformy Docker, które są zarządzane przez serwer główny. *Kubelet* jest klientem, który przekazuje polecenia z Kubernetes do Platformy Docker.

![Kubernetes](./media/kubernetes-example.png)

Aby uzyskać więcej informacji na temat aranżacji, zobacz [Kubernetes na platformie Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Funkcje jako usługa (FaaS) jest wyspecjalizowaną usługą kontenera, która jest podobna do bezserwerowej. Specyficzna implementacja FaaS, o nazwie [OpenFaaS,](https://github.com/openfaas/faas)znajduje się na kontenerach, aby zapewnić możliwości bezserwerowe. OpenFaaS udostępnia szablony, które pakują wszystkie zależności kontenera niezbędne do uruchomienia fragmentu kodu. Korzystanie z szablonów upraszcza proces wdrażania kodu jako jednostki funkcjonalnej. OpenFaaS dotyczy architektury, które już zawierają kontenery i koordynatorów, ponieważ można użyć istniejącej infrastruktury. Mimo że zapewnia funkcjonalność bezserwerową, w szczególności wymaga użycia platformy Docker i koordynatora.

## <a name="serverless"></a>Praca bezserwerowa

Architektura bezserwerowa zapewnia wyraźne oddzielenie kodu od jego środowiska hostingowego. Kod można zaimplementować w *funkcji,* która jest wywoływana przez *wyzwalacz*. Po zamknięciu tej funkcji wszystkie potrzebne zasoby mogą zostać zwolnione. Wyzwalacz może być ręczny, proces czasowy, żądanie HTTP lub przekazywanie pliku. Wynikiem wyzwalacza jest wykonanie kodu. Mimo że platformy bezserwerowe różnią się, większość zapewnia dostęp do wstępnie zdefiniowanych interfejsów API i powiązań w celu usprawnienia zadań, takich jak zapisywanie w bazie danych lub kolejkowanie wyników.

Serverless to architektura, która w dużej mierze opiera się na abstrakcji od środowiska hosta, aby skupić się na kodzie. Można go traktować jako *mniej serwera.*

Rozwiązania kontenerowe zapewniają deweloperom istniejące skrypty kompilacji do publikowania kodu na obrazach gotowych do użycia bez użycia serwera. Inne implementacje używają istniejących rozwiązań PaaS, aby zapewnić skalowalną architekturę.

Abstrakcja oznacza, że zespół DevOps nie musi aprowizować ani zarządzać serwerami ani określonymi kontenerami. Platforma bezserwerowa obsługuje kod jako skrypt lub spakowane pliki wykonywalne utworzone przy uwidaczniającej zestaw SDK i przydziela niezbędne zasoby do skalowania kodu.

Na poniższych ilustracjach przedstawiono cztery składniki bezserwerowe. Żądanie HTTP powoduje uruchomienie kodu interfejsu API realizacji. Interfejs API wyewidencjonowania wstawia kod do bazy danych, a wstawianie wyzwala kilka innych funkcji do uruchomienia w celu wykonywania zadań, takich jak zadania obliczeniowe i realizacja zamówienia.

![Implementacja bezserwerowa](./media/serverless-implementation.png)

Zalety bezserwerowe obejmują:

- **Wysoka gęstość.** Wiele wystąpień tego samego kodu bezserwerowego można uruchomić na tym samym hoście w porównaniu do kontenerów lub maszyn wirtualnych. Wystąpienia są skalowane w wielu hostach w sposób skalowany w sposób skalowany w sposób skalowany w czasie i odporność.
- **Mikrorozliczanie.** Większość dostawców bezserwerowych rozlicza się na podstawie wykonań bezserwerowych, co pozwala na ogromne oszczędności w niektórych scenariuszach.
- **Natychmiastowa skala.** Bezserwerowy można skalować, aby automatycznie i szybko dopasować obciążenia.
- **Krótszy czas na rynku.** Deweloperzy koncentrują się na kodzie i wdrażają bezpośrednio na platformie bezserwerowej. Komponenty mogą być uwalniane niezależnie od siebie.

Bezserwerowe jest najczęściej omawiane w kontekście obliczeń, ale można również zastosować do danych. Na przykład [azure SQL](https://docs.microsoft.com/azure/sql-database) i [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) zapewniają bazy danych w chmurze, które nie wymagają konfigurowania maszyn hosta lub klastrów. Ta książka koncentruje się na obliczeniach bezserwerowych.

## <a name="summary"></a>Podsumowanie

Istnieje szerokie spektrum dostępnych opcji dla architektury, w tym podejście hybrydowe. Bezserwerowe upraszcza podejście, zarządzanie i koszt funkcji aplikacji kosztem kontroli i przenośności. Jednak wiele platform bezserwerowych uwidacznia konfigurację, aby pomóc dostosować rozwiązanie. Dobre praktyki programowania może również prowadzić do bardziej przenośny kod i mniej bezserwerowe platformy lock-in. W poniższej tabeli przedstawiono architektury podejścia obok siebie. Wybierz bezserwerowe na podstawie potrzeb skali, czy chcesz zarządzać czasem wykonywania i jak dobrze można podzielić obciążeń na małe składniki. Dowiesz się o potencjalnych wyzwaniach związanych z bezserwerowymi i innymi punktami decyzyjną w następnym rozdziale.

|         |IaaS     |PaaS     |Kontener|Praca bezserwerowa|
|---------|---------|---------|---------|----------|
|**Skali**|VM       |Wystąpienie |Aplikacja      |Funkcja  |
|**Abstrakty**|Sprzęt|Platforma|OS Host|Środowisko uruchomieniowe   |
|**Jednostki** |VM       |Project  |Image (Obraz)    |Code      |
|**Okres istnienia**|Miesiące|Dni do miesięcy|Minuty do dni|Milisekundy do minut|
|**Odpowiedzialność**|Aplikacje, zależności, czas wykonywania i system operacyjny|Aplikacje i zależności|Aplikacje, zależności i czas wykonywania|Funkcja

- **Skala** odnosi się do urządzenia, które służy do skalowania aplikacji
- **Abstrakty** odnosi się do warstwy, która jest abstrakcja przez implementację
- **Jednostka** odnosi się do zakresu tego, co jest wdrażane
- **Okres istnienia** odnosi się do typowego czasu wykonywania określonego wystąpienia
- **Odpowiedzialność** odnosi się do obciążenie do tworzenia, wdrażania i obsługi aplikacji

Następny rozdział skupi się na architekturze bezserwerowej, przypadkach użycia i wzorcach projektowania.

## <a name="recommended-resources"></a>Zalecane zasoby

- [Przewodnik po architekturze aplikacji platformy Azure](https://docs.microsoft.com/azure/architecture/guide/)
- [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
- [Azure SQL](https://docs.microsoft.com/azure/sql-database)
- [Wzorzec architektury N-Warstwowej](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
- [Usługa Kubernetes na platformie Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)
- [Mikrousług](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
- [Architektura referencyjna dla maszyn wielowarstwowych maszyny wirtualnej](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
- [Maszyny wirtualne](https://docs.microsoft.com/azure/virtual-machines/)
- [Co to jest Docker?](../microservices/container-docker-introduction/docker-defined.md)
- [Aplikacja Wingtip Tickets SaaS](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Poprzedni](architecture-approaches.md)
>[następny](serverless-architecture.md)
