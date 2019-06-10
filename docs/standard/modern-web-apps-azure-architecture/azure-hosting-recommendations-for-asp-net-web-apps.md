---
title: Zalecenia dotyczące aplikacji sieci web platformy ASP.NET Core hostingu platformy Azure
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Zalecenia dotyczące aplikacji sieci web platformy ASP.NET hostingu platformy Azure
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: 7cfb9ada4f963aa392a41cfb9f1b2df22f542d41
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758658"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Zalecenia dotyczące aplikacji sieci web platformy ASP.NET Core hostingu platformy Azure

> "Line-of-business liderów wszędzie, gdzie są pomijanie działom IT Pobierz aplikacje z chmury (znany także jako SaaS) i płacić je jak Subskrypcja magazynu. A gdy usługa nie jest już wymagane, ich może anulować subskrypcję, nie sprzęt, pozostanie nieużywana w prawym górnym rogu."  
> _\- Daryl Plummer, analityk firmy Gartner_

Niezależnie od aplikacji potrzebom i architektury, Microsoft Azure może obsługiwać go. Twoje potrzeby hostingu mogą być proste i polega na statycznej witryny internetowej lub aplikacji złożone składają się z wielu usług. Dla aplikacji monolitycznych sieci web platformy ASP.NET Core i usługi pomocnicze istnieje kilka znanych konfiguracje, które są zalecane. Zalecenia w tym artykule są grupowane w zależności od rodzaju zasobów, aby znajdować, czy pełna aplikacji, poszczególnych procesów i danych.

## <a name="web-applications"></a>Aplikacje internetowe

Aplikacje sieci Web mogą być przechowywane za pomocą:

- Aplikacje sieci Web usługi App Service

- Kontenery (kilka opcji)

- Maszyny wirtualne (VM)

Z tych opcji App Service Web Apps to zalecane podejście do większości scenariuszy, w tym prostych aplikacji opartych na kontenerach. W przypadku architektur mikrousług należy rozważyć podejście oparte na kontenerach. Jeśli potrzebujesz większej kontroli nad maszynami działania aplikacji, należy wziąć pod uwagę maszyn wirtualnych platformy Azure.

### <a name="app-service-web-apps"></a>Aplikacje sieci Web usługi App Service

Usługa App Service Web Apps oferuje w pełni zarządzana platforma, zoptymalizowana pod kątem hostowania aplikacji sieci web. Jest to platforma jako usługa (PaaS), oferty, że umożliwia użytkownikom skoncentrowanie się na logice biznesowej, podczas gdy platforma Azure zajmie się infrastrukturą potrzebne do uruchamiania i skalowania aplikacji. Niektóre kluczowe funkcje usługi App Service Web Apps:

- Optymalizacja metodyki DevOps (ciągła integracja i dostarczanie, wielu środowisk, A / B, testowanie, obsługi skryptów).

- Skala globalna i o wysokiej dostępności.

- Połączenia z platformami SaaS i danych w środowisku lokalnym.

- Zabezpieczenia i zgodność.

- Integracja z programem Visual Studio.

Usługa Azure App Service jest najlepszym wyborem dla większości aplikacji sieci web. Wdrażanie i zarządzanie są zintegrowane z platformą, witryny można szybko skalować w celu obsługi obciążeń z dużym ruchem i wbudowanego obciążenia równoważenia i usługa traffic manager zapewniają wysoką dostępność. Można przenieść istniejące witryny w usłudze Azure App Service za pomocą narzędzia do migracji online, korzystanie z aplikacji typu open source z galerii aplikacji sieci Web lub Utwórz nową witrynę przy użyciu framework i wybranych przez siebie narzędzi. Funkcja zadań Webjob ułatwia dodawanie zadania w tle przetwarzania do aplikacji sieci web usługi App Service. Jeśli masz istniejącą aplikację ASP.NET hostowanej lokalnie przy użyciu lokalnej bazy danych, jest przejrzystą ścieżkę, aby przeprowadzić migrację aplikacji do aplikacji sieci Web usługi App Service za pomocą usługi Azure SQL Database (lub bezpiecznego dostępu do serwera bazy danych w środowisku lokalnym, jeśli preferowane).

![Strategię migracji zalecana dla środowiska lokalnego aplikacji .NET w usłudze Azure App Service](./media/image1-6.png)

W większości przypadków przenoszenie z hostowanych lokalnie aplikacji ASP.NET do aplikacji sieci Web usługi App Service jest dość proste. Niewielkie modyfikacje należy wymagać samej aplikacji, a następnie go szybko rozpocząć korzystanie z zalet wiele funkcji, które oferują usługi Azure App Service Web Apps.

Oprócz aplikacji, które nie są zoptymalizowane dla chmury Azure App Service Web Apps to idealne rozwiązanie dla wielu proste monolityczne (nierozpowszechniony) aplikacji, takich jak wiele aplikacji platformy ASP.NET Core. W tym podejściu architektura jest podstawowych i proste do zrozumienia i zarządzanie nimi:

![Podstawowa architektura platformy Azure](./media/image1-5.png)

Mała liczba zasobów w pojedynczej grupy zasobów jest zwykle wystarczające, aby zarządzać takiej aplikacji. Aplikacje, które zazwyczaj są wdrażane jako pojedynczą jednostkę, a nie te aplikacje, które składają się z wielu osobnych procesach i dobrze nadają się do tego [podstawowe podejście architektoniczne](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app). Chociaż pod względem architektury proste tego podejścia nadal umożliwia hostowanej aplikacji skalowany w górę (więcej zasobów na węzeł) i out (bardziej hostowanej węzły) do spełnienia wzrost zapotrzebowania. Z funkcją automatycznego skalowania można skonfigurować aplikację do automatycznie dostosowywać liczbę węzłów hostujących aplikację na podstawie zapotrzebowania i średnie obciążenie między węzłami.

### <a name="app-service-web-apps-for-containers"></a>Usługa App Service Web Apps for Containers

Oprócz obsługę hostowania aplikacji sieci web bezpośrednio [App Service Web Apps for Containers](https://azure.microsoft.com/services/app-service/containers/) może służyć do uruchamiania konteneryzowanych aplikacji w systemach Windows i Linux. W ramach tej usługi można łatwe wdrażanie i uruchamianie konteneryzowanych aplikacji, które można skalować z Twoją firmą. Aplikacje są wszystkie funkcje usługi App Service Web Apps wymienionych powyżej. Ponadto aplikacje sieci Web do obsługi kontenerów uproszczenie ciągłej integracji/ciągłego wdrażania z usługi Docker Hub, Azure Container Registry i GitHub. DevOps platformy Azure służy do definiowania potoki kompilacji i wdrażania, które Opublikuj zmiany do rejestru. Te zmiany, a następnie można przetestować w środowisku przejściowym i automatycznie wdrożoną w środowisku produkcyjnym za pomocą miejsc wdrożenia, dzięki czemu uaktualnienia bez jakichkolwiek przestojów. Wycofywanie z poprzednimi wersjami można zrobić równie łatwo.

Istnieje kilka scenariuszy, w którym Web App for Containers mają najwięcej sensu. Jeśli masz istniejące aplikacje, które można konteneryzowanie, czy w kontenerach Windows lub Linux możesz hostować je łatwo za pomocą tego zestawu narzędzi. Po prostu opublikowany kontener, a następnie skonfiguruj Web App for Containers ściągnąć najnowszą wersję tego obrazu z rejestru wybranego. To podejścia "lift- and -shift", jak w przypadku migracji z klasycznej aplikacji hostowania modeli do modelu zoptymalizowane pod kątem chmury.

![Migrowanie lokalnego konteneryzowanych aplikacji .NET w celu usługi Azure Web Apps for Containers](./media/image1-8.png)

Ta metoda działa również dobrze, jeśli Twój zespół deweloperów jest możliwe przeniesienie do procesu tworzenia opartych na kontenerach. "Wewnętrzną pętlę" związanych z tworzeniem aplikacji za pomocą kontenerów obejmuje tworzenie aplikacji za pomocą kontenerów. Zmiany wprowadzone do kodu, a także konfigurację kontenera są przekazywane do kontroli źródła, a następnie automatycznej kompilacji jest odpowiedzialny za publikowanie nowych obrazów kontenera do rejestru, takich jak usługi Docker Hub lub Azure Container Registry. Obrazy te są następnie używane jako podstawa dla dodatkowego programowania, a także w przypadku wdrożeń do środowiska produkcyjnego, jak pokazano na poniższym diagramie:

![Przepływ pracy cykl życia metodyki DevOps platformy Docker typu end to End](./media/image1-7.png)

Opracowywanie zawartości przy użyciu kontenerów oferuje wiele korzyści, szczególnie w przypadku, gdy kontenery są używane w środowisku produkcyjnym. Taką samą konfigurację kontenera służy do hostowania tej aplikacji w każdym środowisku, w której jest uruchamiany, z lokalnej maszynie do programowania do tworzenia i testowania systemów do środowiska produkcyjnego. Znacznie zmniejsza to prawdopodobieństwo wady wynikające z różnic w konfiguracji komputera lub wersji oprogramowania. Deweloperzy mogą również używać dowolnych narzędzi są one najbardziej produktywny, łącznie z systemu operacyjnego, ponieważ kontenerów można uruchomić w dowolnym systemie operacyjnym. W niektórych przypadkach aplikacje rozproszone, obejmujących wiele kontenerów może być bardzo obciąża do uruchamiania na maszynie deweloperskiej jednego. W tym scenariuszu rozsądne może okazać się uaktualnienia do przy użyciu platformy Kubernetes i usługi Azure Dev miejsca do magazynowania, opisane w następnej sekcji.

Jako części większych aplikacji są dzielone na ich własnych mniejsze, niezależnie od *mikrousług*, wzorce projektowe dodatkowe może służyć do poprawy zachowanie aplikacji. Nie pracować bezpośrednio z poszczególnych usług *bramy interfejsu API* można uprościć dostęp i rozdzielenie klienta ze swojej wewnętrznej. Również posiadanie oddzielnej usługi zaplecza dla różnych Frontony umożliwia usługom podlegać ewolucji w połączeniu z niego korzystają. Wspólne usługi jest możliwy za pośrednictwem oddzielnego *przyczepki* kontenera, które mogą obejmować wspólnych bibliotek łączności klienta przy użyciu *Ambasador* wzorca.

![Mikrousługi przykładowe architektury za pomocą zauważyć kilka często używane wzorce projektowe.](./media/image1-10.png)

[Dowiedz się więcej na temat wzorców projektowych, które należy uwzględnić podczas tworzenia systemów opartych na mikrousługach.](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Usługa Azure Kubernetes Service (AKS) zarządza hostowanym środowiskiem Kubernetes, pozwalając szybko i łatwo wdrażać konteneryzowane aplikacje i Zarządzaj bez doświadczenia z organizowaniem kontenerów. Eliminuje to również obciążenia i konserwacją dzięki inicjowania obsługi administracyjnej, aktualizowaniu i skalowaniu zasobów na żądanie bez przełączania aplikacji w trybie offline.

Usługa AKS zmniejsza złożoność i nakłady operacyjne związane z zarządzaniem klastrem Kubernetes, przenosząc znaczną część tej odpowiedzialności na platformę Azure. Jako hostowana usługa Kubernetes, platforma Azure obsługuje krytyczne zadania, takie jak monitorowanie kondycji i konserwacja. Ponadto płacisz tylko za węzły agenta w ramach Twoich klastrów, nie za wzorce. Jako zarządzana usługa Kubernetes AKS zapewnia:

- Automatyczne uaktualnienia wersji platformy Kubernetes i stosowanie poprawek.
- Łatwe skalowanie klastra.
- Samonaprawialną hostowaną warstwę kontroli (wzorce).
- Oszczędności — płacisz tylko za uruchomione węzły puli agentów.

Platforma Azure obsługuje zarządzanie węzłami w klastrze AKS nie trzeba ręcznie wykonywać wielu zadań, takich jak Uaktualnianie klastra. Ponieważ platforma Azure wykonuje te krytyczne zadania konserwacji za Ciebie, AKS nie zapewnia bezpośredni dostęp (takich jak przy użyciu protokołu SSH) do klastra.

Zespoły, które korzysta z usługi AKS również korzystać z zalet usługi Azure Dev miejsca do magazynowania. Usługa Azure Dev do magazynowania ułatwia zespołom skoncentrowanie się na rozwoju i szybkie iteracji w swojej aplikacji mikrousług, umożliwiając zespołom pracować bezpośrednio z ich architektury mikrousług całego lub aplikacja działająca w usłudze AKS. Usługa Azure Dev spacje umożliwia również niezależnie aktualizować części architektury mikrousług w izolacji bez wpływu na pozostałe klastra AKS lub innym deweloperom.

![Przykład przepływu pracy w usłudze Azure Dev miejsca do magazynowania](./media/image1-9.gif)

Usługa Azure Dev miejsca do magazynowania:

- Należy zminimalizować komputera lokalnego ustawienia czasu i zasobów
- Umożliwić zespołom sprawne Kończenie iteracji szybciej
- Zmniejsz liczbę środowisk integration wymagana przez zespół
- Usuń konieczne testowanie pewnych usług w systemie rozproszonym, podczas opracowywania i testowania

[Dowiedz się więcej na temat usługi Azure Dev miejsca do magazynowania](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Usługa Azure Virtual Machines

Jeśli masz istniejącą aplikację, która wymagałaby istotnych zmian do uruchamiania w usłudze App Service, możesz wybrać maszyny wirtualne w celu uproszczenia migracji do chmury. Jednak prawidłowo Konfigurowanie, zabezpieczanie i obsługa maszyn wirtualnych wymaga znacznie więcej czasu i doświadczenia w zakresie IT w porównaniu do usługi Azure App Service. Jeśli rozważasz usługę Azure Virtual Machines, upewnij się, że należy wziąć pod uwagę rutynowej konserwacji pracę wymaganą do dostarczenia poprawek, aktualizacji, a także zarządzać środowiskiem maszyny Wirtualnej. Maszyny wirtualne platformy Azure to infrastruktura jako usługa (IaaS), podczas gdy usługi App Service jest PaaS. Należy również rozważyć, czy wdrażania aplikacji jako kontener Windows w usłudze Web App for Containers może być wygodną opcją dla danego scenariusza.

## <a name="logical-processes"></a>Logiczne procesów

Poszczególne logiczne procesów, które mogą być odłączone od reszty aplikacji można wdrażać niezależnie do usługi Azure Functions w sposób "bezserwerowych". Usługa Azure Functions umożliwia wystarczy napisać kod, potrzebne dla danego problemu, nie martwiąc się o aplikację lub infrastrukturę, aby go uruchomić. Możesz korzystać z różnych języków programowania, w tym C\#, F\#, Node.js, Python czy PHP, dzięki czemu możesz wybrać najbardziej wydajny język dla zadania pod ręką. Jak większość rozwiązań opartych na chmurze możesz płacić tylko za używane czasu używania i ufasz usługi Azure Functions, aby skalować w górę odpowiednio do potrzeb.

## <a name="data"></a>Dane

Platforma Azure oferuje szeroką gamę opcji przechowywania danych, dzięki czemu aplikacja może używać dostawcy danych odpowiednie dla danego danych.

W przypadku danych transakcyjnych, relacyjnej bazy danych SQL Azure są najlepszym rozwiązaniem. Dla o wysokiej wydajności odczytu głównie danych usługi Redis cache wspierana przez usługi Azure SQL Database jest doskonałym rozwiązaniem.

Dane JSON bez określonej struktury mogą być przechowywane w na różne sposoby: z kolumny bazy danych SQL do obiektów blob lub tabel w usłudze Azure Storage do bazy danych DocumentDB. Z tych opcji baza danych DocumentDB oferuje najlepsze funkcje zapytań i jest to zalecana opcja, w przypadku dużej liczby opartych na formacie JSON dokumentów, które muszą obsługiwać zapytań.

Przejściowy polecenia lub zdarzenie oparte na danych, używane do organizowania zachowanie aplikacji, można użyć usługi Azure Service Bus lub kolejek usługi Azure Storage. Usługa Azure Storage Bus oferuje bardziej elastyczne i jest zalecana dla nietrywialnymi obsługi komunikatów w ramach i między aplikacjami.

## <a name="architecture-recommendations"></a>Zalecenia dotyczące architektury

Twoja aplikacja powinna uwarunkowania jej architektury. Dostępne są różne usługi platformy Azure. Właściwy wybór jest ważnym krokiem. Firma Microsoft oferuje galerii architektury referencyjne, aby ułatwić identyfikację typowej architektury zoptymalizowane pod kątem typowych scenariuszy. Może się okazać, architektury referencyjnej, mapy do wymagań aplikacji lub na co najmniej oferuje początkowy punkt.

Rysunek 11-2 przedstawiono przykład architektury referencyjnej. Ten diagram w tym artykule opisano podejście zalecaną architekturę Sitecore strony internetowej systemu zarządzania zawartością zoptymalizowane pod kątem marketing.

![](./media/image11-2.png)

**Rysunek 11-1.** Oprogramowanie Sitecore marketingu architektury referencyjnej witryny sieci Web.

**Odwołania — zalecenia dotyczące hostingu platformy Azure**

- Architectures\ rozwiązanie na platformie Azure
  <https://azure.microsoft.com/solutions/architecture/>

- Architecture\ aplikacji sieci Web platformy Azure podstawowe
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Wzorce projektowe zapewniające Microservices\
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Guide\ dla deweloperów platformy Azure
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Overview\ aplikacji sieci Web
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Aplikacja sieci Web dla Containers\
  <https://azure.microsoft.com/services/app-service/containers/>

- Wprowadzenie do usługi Azure Kubernetes Service (AKS) \
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Poprzednie](development-process-for-azure.md)
