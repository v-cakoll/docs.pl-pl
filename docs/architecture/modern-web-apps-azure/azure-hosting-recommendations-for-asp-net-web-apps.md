---
title: Zalecenia dotyczące hostingu platformy Azure dla aplikacji sieci Web ASP.NET Core
description: Architekt nowoczesne aplikacje internetowe z ASP.NET Core i Azure | Zalecenia dotyczące hostingu platformy Azure dla ASP.NET aplikacji sieci web
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: 5587b8b20da8a6801d77b722e9c3326f6e695574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416713"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Zalecenia dotyczące hostingu platformy Azure dla aplikacji sieci Web ASP.NET Core

> "Liderzy biznesu na całym świecie omijają działy IT, aby otrzymywać aplikacje z chmury (znanej również jako SaaS) i płacą za nie tak, jak w przypadku subskrypcji czasopism. A gdy usługa nie jest już wymagana, mogą anulować subskrypcję bez sprzętu pozostawionego nieużywanego w rogu."  
> _\-Daryl Plummer, analityk firmy Gartner_

Niezależnie od potrzeb i architektury aplikacji, platforma Microsoft Azure może ją obsługiwać. Twoje potrzeby hostingowe mogą być tak proste, jak statyczna strona internetowa lub wyrafinowana aplikacja składająca się z kilkudziesięciu usług. W przypadku ASP.NET Core monolitycznych aplikacji internetowych i usług pomocniczych istnieje kilka dobrze znanych konfiguracji, które są zalecane. Zalecenia dotyczące tego artykułu są pogrupowane na podstawie rodzaju zasobu, który ma być hostowany, czy pełne aplikacje, poszczególne procesy lub dane.

## <a name="web-applications"></a>Aplikacje internetowe

Aplikacje internetowe mogą być hostowane za pomocą:

- Aplikacje sieci Web usługi aplikacji

- Kontenery (kilka opcji)

- Maszyny wirtualne (maszyny wirtualne)

Z tych aplikacji sieci Web usługi app service jest zalecane podejście dla większości scenariuszy, w tym prostych aplikacji opartych na kontenerach. W przypadku architektur mikrousług należy wziąć pod uwagę podejście oparte na kontenerze. Jeśli potrzebujesz większej kontroli nad maszynami z uruchomioną aplikacją, należy wziąć pod uwagę maszyny wirtualne platformy Azure.

### <a name="app-service-web-apps"></a>Aplikacje sieci Web usługi aplikacji

App Service Web Apps oferuje w pełni zarządzaną platformę zoptymalizowaną pod kątem hostowania aplikacji sieci Web. Jest to platforma jako usługa (PaaS) oferuje, który pozwala skupić się na logice biznesowej, podczas gdy platforma Azure dba o infrastrukturę potrzebną do uruchamiania i skalowania aplikacji. Niektóre kluczowe funkcje aplikacji App Service Web Apps:

- Optymalizacja DevOps (ciągła integracja i dostarczanie, wiele środowisk, testowanie A/B, obsługa skryptów).

- Globalna skala i wysoka dostępność.

- Połączenia z platformami SaaS i danymi lokalnymi.

- Bezpieczeństwo i zgodność z przepisami.

- Integracja z programem Visual Studio.

Usługa Azure App Service to najlepszy wybór w przypadku większości aplikacji internetowych. Wdrażanie i zarządzanie są zintegrowane z platformą, witryny można szybko skalować na potrzeby obsługi dużych obciążeń generowanych przez ruch sieciowy, a wbudowane równoważenie obciążenia i usługa Traffic Manager zapewniają wysoką dostępność. Istniejące witryny możesz łatwo przenieść do usługi Azure App Service za pomocą narzędzia do migracji online, używając aplikacji open source z galerii aplikacji internetowych lub tworząc nową witrynę za pomocą wybranej platformy i narzędzi. Zadania WebJob upraszczają dodawanie przetwarzania zadań w tle do aplikacji internetowej usługi App Service. Jeśli masz istniejącą aplikację ASP.NET hostowane lokalnie przy użyciu lokalnej bazy danych, istnieje wyczyść ścieżkę do migracji aplikacji do aplikacji app service web app z bazą danych SQL platformy Azure (lub bezpieczny dostęp do lokalnego serwera bazy danych, jeśli jest to preferowane).

![Zalecana strategia migracji lokalnych aplikacji .NET do usługi Azure App Service](./media/image1-6.png)

W większości przypadków przejście z lokalnie hostowane ASP.NET aplikacji do aplikacji sieci Web usługi app service jest prosty proces. Niewielkie lub żadne modyfikacje powinny być wymagane od samej aplikacji i można szybko rozpocząć korzystanie z wielu funkcji, które oferują aplikacje sieci Web usługi Azure App Service.

Oprócz aplikacji, które nie są zoptymalizowane pod kątem chmury, aplikacje Azure App Service Web Apps są doskonałym rozwiązaniem dla wielu prostych aplikacji monolitycznych (nierozproszonych), takich jak wiele ASP.NET aplikacje Core. W tym podejściu architektura jest podstawowa i prosta do zrozumienia i zarządzania:

![Podstawowa architektura platformy Azure](./media/image1-5.png)

Niewielka liczba zasobów w jednej grupie zasobów jest zazwyczaj wystarczająca do zarządzania taką aplikacją. Aplikacje, które są zazwyczaj wdrażane jako pojedyncza jednostka, a nie te aplikacje, które są wykonane z wielu oddzielnych procesów, są dobrymi kandydatami do tego [podstawowego podejścia architektonicznego.](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app) Chociaż architektonicznie proste, takie podejście nadal umożliwia hostowanej aplikacji skalowanie zarówno w górę (więcej zasobów na węzeł) i obecnie (więcej węzłów hostowanych), aby sprostać wzrostowi popytu. Dzięki skalowaniu automatycznemu aplikację można skonfigurować tak, aby automatycznie dostosowywała liczbę węzłów hostujących aplikację na podstawie popytu i średniego obciążenia w węzłach.

### <a name="app-service-web-apps-for-containers"></a>Aplikacje sieci Web usługi App Service dla kontenerów

Oprócz obsługi bezpośredniego hostowania aplikacji sieci Web [aplikacje app service dla kontenerów](https://azure.microsoft.com/services/app-service/containers/) mogą służyć do uruchamiania aplikacji kontenerowych w systemach Windows i Linux. Za pomocą tej usługi można łatwo wdrażać i uruchamiać konteneryzowane aplikacje, które można skalować w firmie. Aplikacje mają wszystkie funkcje aplikacji App Service Web Apps wymienione powyżej. Ponadto aplikacje sieci Web dla kontenerów obsługują usprawnioną usługę CI/CD za pomocą usługi Docker Hub, azure container registry i github. Za pomocą usługi Azure DevOps można zdefiniować potoki kompilacji i wdrażania, które publikują zmiany w rejestrze. Zmiany te można następnie przetestować w środowisku przejściowym i automatycznie wdrożyć w środowisku produkcyjnym przy użyciu gniazd wdrożeniowych, co pozwala na uaktualnianie zerowego przestoju. Cofanie się do poprzednich wersji można zrobić równie łatwo.

Istnieje kilka scenariuszy, w których aplikacje sieci Web dla kontenerów mają największy sens. Jeśli masz istniejące aplikacje, które można konteneryzować, czy w kontenerach systemu Windows lub Linux, można je łatwo hostować za pomocą tego zestawu narzędzi. Po prostu opublikuj kontener, a następnie skonfiguruj aplikacje sieci Web dla kontenerów, aby pobierać najnowszą wersję tego obrazu z wybranego rejestru. Jest to podejście "lift and shift" do migracji z klasycznych modeli hostingu aplikacji do modelu zoptymalizowanego pod kątem chmury.

![Migrowanie konteneryzowanej aplikacji lokalnej .NET do aplikacji Azure Web Apps dla kontenerów](./media/image1-8.png)

Takie podejście działa również dobrze, jeśli zespół deweloperski jest w stanie przejść do procesu tworzenia opartego na kontenerach. "Wewnętrzna pętla" tworzenia aplikacji z kontenerami obejmuje tworzenie aplikacji za pomocą kontenerów. Zmiany wprowadzone w kodzie, a także konfiguracji kontenera są wypychane do kontroli źródła, a kompilacja automatyczna jest odpowiedzialna za publikowanie nowych obrazów kontenerów w rejestrze, takim jak Docker Hub lub Azure Container Registry. Te obrazy są następnie używane jako podstawa do dodatkowego rozwoju, a także dla wdrożeń do produkcji, jak pokazano na poniższym diagramie:

![Praca nad cyklem życia cyklu życia dokowania do końca](./media/image1-7.png)

Rozwój z kontenerów oferuje wiele zalet, zwłaszcza gdy pojemniki są używane w produkcji. Ta sama konfiguracja kontenera służy do hostowania aplikacji w każdym środowisku, w którym działa, od lokalnej maszyny deweloperskiej do tworzenia i testowania systemów do produkcji. Znacznie zmniejsza to prawdopodobieństwo wystąpienia usterek wynikających z różnic w konfiguracji maszyny lub wersjach oprogramowania. Deweloperzy mogą również używać dowolnych narzędzi, z których są najbardziej produktywni, w tym systemu operacyjnego, ponieważ kontenery mogą działać na dowolnym systemie operacyjnym. W niektórych przypadkach rozproszone aplikacje obejmujące wiele kontenerów mogą być bardzo intensywnie korzystające z zasobów do uruchamiania na jednym komputerze deweloperskim. W tym scenariuszu może być sens, aby uaktualnić do przy użyciu Kubernetes i Azure Dev Spaces, omówione w następnej sekcji.

Ponieważ części większych aplikacji są podzielone na własne mniejsze, niezależne *mikrousługi,* dodatkowe wzorce projektu mogą służyć do poprawy zachowania aplikacji. Zamiast pracować bezpośrednio z poszczególnymi usługami, *brama interfejsu API* może uprościć dostęp i oddzielić klienta od zaplecza. Posiadanie oddzielnych zapleczy usługowych dla różnych frontów pozwala również na rozwój usług w porozumieniu z konsumentami. Typowe usługi są dostępne za pośrednictwem oddzielnego kontenera *samochodu bocznego,* który może obejmować biblioteki łączności wspólnej klienta przy użyciu wzorca *ambasadora.*

![Mikrousług przykładowej architektury z kilku typowych wzorców projektowania zauważyć.](./media/image1-10.png)

[Dowiedz się więcej o wzorcach projektowania, które należy wziąć pod uwagę podczas tworzenia systemów opartych na mikrousługach.](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Usługa Azure Kubernetes Service (AKS) zarządza hostowanym środowiskiem Kubernetes, dzięki czemu można szybko i łatwo wdrażać konteneryzowane aplikacje i zarządzać nimi bez specjalistycznej wiedzy z zakresu aranżacji kontenerów. Eliminuje to również uciążliwości związane z bieżącą obsługą i konserwacją dzięki aprowizowaniu, aktualizowaniu i skalowaniu zasobów na żądanie bez przełączania aplikacji do trybu offline.

Usługa AKS zmniejsza złożoność i nakłady operacyjne związane z zarządzaniem klastrem Kubernetes, przenosząc znaczną część tej odpowiedzialności na platformę Azure. Jako hostowana usługa Kubernetes, platforma Azure obsługuje krytyczne zadania, takie jak monitorowanie kondycji i konserwacja. Ponadto płacisz tylko za węzły agenta w klastrach, a nie za wzorce. Jako zarządzana usługa Kubernetes, usługa AKS zapewnia:

- Automatyczne uaktualnianie wersji Kubernetes i łatanie.
- Łatwe skalowanie klastra.
- Samonaprawiający się hostowany samolot kontrolny (masters).
- Oszczędności kosztów — zapłać tylko za uruchamianie węzłów puli agentów.

Dzięki temu, że platforma Azure obsługuje zarządzanie węzłami w klastrze AKS, nie musisz już ręcznie wykonywać wielu zadań, takich jak uaktualnianie klastra. Ponieważ platforma Azure obsługuje te krytyczne zadania konserwacji dla Ciebie, AKS nie zapewnia bezpośredniego dostępu (na przykład z SSH) do klastra.

Zespoły korzystające z usługi AKS mogą również korzystać z platformy Azure Dev Spaces. Usługa Azure Dev Spaces pomaga zespołom skupić się na tworzeniu i szybkiej iteracji aplikacji mikrousług, umożliwiając zespołom bezpośrednią pracę z całą architekturą mikrousług lub aplikacją działającą w usłudze AKS. Usługa Azure Dev Spaces zapewnia również sposób niezależnie aktualizować części architektury mikrousług w izolacji bez wpływu na resztę klastra AKS lub innych deweloperów.

![Przykład przepływu pracy usługi Azure Dev Spaces](./media/image1-9.gif)

Przestrzenie deweloperów platformy Azure:

- Minimalizowanie czasu konfiguracji maszyny lokalnej i wymagań dotyczących zasobów
- Zezwalaj zespołom na szybsze itetencje
- Zmniejsz liczbę środowisk integracji wymaganych przez zespół
- Usuń potrzebę makiety niektórych usług w systemie rozproszonym podczas opracowywania / testowania

[Dowiedz się więcej o przestrzeniach deweloperskich platformy Azure](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

Jeśli masz istniejącą aplikację, która wymaga znacznych modyfikacji do uruchomienia w usłudze App Service, można wybrać maszyny wirtualne w celu uproszczenia migracji do chmury. Jednak prawidłowe konfigurowanie, zabezpieczanie i obsługa maszyn wirtualnych wymaga znacznie więcej czasu i wiedzy in-it w porównaniu z usługą Azure App Service. Jeśli rozważasz maszyny wirtualne platformy Azure, upewnij się, że bierzesz pod uwagę bieżące działania konserwacyjne wymagane do stosowania poprawek, aktualizacji i zarządzania środowiskiem maszyn wirtualnych. Maszyny wirtualne platformy Azure to infrastruktura jako usługa (IaaS), podczas gdy usługa App Service to PaaS. Należy również rozważyć, czy wdrażanie aplikacji jako kontenera systemu Windows do aplikacji sieci Web dla kontenerów może być realną opcją dla scenariusza.

## <a name="logical-processes"></a>Procesy logiczne

Poszczególne procesy logiczne, które można oddzielić od reszty aplikacji, mogą być wdrażane niezależnie w usłudze Azure Functions w sposób "bezserwerowy". Usługa Azure Functions umożliwia po prostu napisać kod potrzebny do danego problemu, nie martwiąc się o aplikacji lub infrastruktury, aby go uruchomić. Możesz wybierać spośród wielu języków programowania,\#w\#tym C, F, Node.js, Python i PHP, co pozwala wybrać najbardziej produktywny język dla wykonywanego zadania. Podobnie jak większość rozwiązań opartych na chmurze, płacisz tylko za czas użycia i możesz zaufać usłudze Azure Functions skalować w razie potrzeby.

## <a name="data"></a>Dane

Platforma Azure oferuje szeroką gamę opcji magazynu danych, dzięki czemu aplikacja może używać odpowiedniego dostawcy danych dla danych, o których mowa.

W przypadku danych transakcyjnych, relacyjnych najlepszym rozwiązaniem są bazy danych SQL platformy Azure. Dla wysokiej wydajności odczytu głównie danych, redis pamięci podręcznej wspierane przez bazę danych SQL platformy Azure jest dobrym rozwiązaniem.

Nieustrukturyzowane dane JSON mogą być przechowywane na różne sposoby, od kolumn bazy danych SQL po obiekty blob lub tabele w usłudze Azure Storage po usługę Azure Cosmos DB. Z tych usługi Azure Cosmos DB oferuje najlepszą funkcję wykonywania zapytań i jest zalecana opcja dla dużej liczby dokumentów opartych na JSON, które muszą obsługiwać wykonywanie zapytań.

Dane przejściowe oparte na poleceniach lub zdarzeniach używane do organizowania zachowania aplikacji mogą używać usługi Azure Service Bus lub kolejek usługi Azure Storage. Usługa Azure Storage Bus oferuje większą elastyczność i jest zalecaną usługą dla nietrywialnych wiadomości w aplikacjach i między nimi.

## <a name="architecture-recommendations"></a>Zalecenia dotyczące architektury

Wymagania aplikacji powinny dyktować jego architektury. Dostępnych jest wiele różnych usług platformy Azure. Wybór właściwego jest ważną decyzją. Firma Microsoft oferuje galerię architektur referencyjnych ułatwiających identyfikowanie typowych architektur zoptymalizowanych pod kątem typowych scenariuszy. Może się okazać, architektury odwołania, który mapuje ściśle do wymagań aplikacji lub przynajmniej oferuje punkt wyjścia.

Rysunek 11-1 przedstawia przykładową architekturę odwołania. Na tym diagramie opisano zalecane podejście architektury dla witryny sieci Web systemu zarządzania treścią sitecore zoptymalizowanej pod kątem marketingu.

![Rysunek 11-1](./media/image11-2.png)

**Rysunek 11-1.** Architektura referencyjna witryny marketingu Sitecore.

**Odwołania — zalecenia dotyczące hostingu platformy Azure**

- Architektury rozwiązań platformy Azure\
  <https://azure.microsoft.com/solutions/architecture/>

- Podstawowa architektura aplikacji sieci Web platformy Azure\
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Wzorce projektowania mikrousług\
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Przewodnik dla deweloperów platformy Azure\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Omówienie aplikacji Sieci Web\
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Aplikacja internetowa dla kontenerów\
  <https://azure.microsoft.com/services/app-service/containers/>

- Wprowadzenie do usługi Azure Kubernetes Service (AKS)\
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Wstecz](development-process-for-azure.md)
