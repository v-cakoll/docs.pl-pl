---
title: Zalecenia dotyczące aplikacji sieci web platformy ASP.NET Core hostingu platformy Azure
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Zalecenia dotyczące aplikacji sieci web platformy ASP.NET hostingu platformy Azure
author: ardalis
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: 221ea2a9fc154468f16ce09195a0415883ada9df
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125935"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Zalecenia dotyczące aplikacji sieci web platformy ASP.NET Core hostingu platformy Azure

> "Line-of-business liderów wszędzie, gdzie są pomijanie działom IT Pobierz aplikacje z chmury (zwane również SaaS) i płacić je jak Subskrypcja magazynu. A gdy usługa nie jest już wymagane, ich może anulować subskrypcję, nie sprzęt, pozostanie nieużywana w prawym górnym rogu."  
> _\- Daryl Plummer, analityk firmy Gartner_

Niezależnie od aplikacji potrzebom i architektura platformy Windows Azure może obsługiwać go. Twoje potrzeby hostingu mogą być proste i polega na statyczna witryna internetowa, do wyrafinowanych aplikacji składa się z wielu usług. Dla aplikacji monolitycznych sieci web platformy ASP.NET Core i usługi pomocnicze istnieje kilka znanych konfiguracje, które są zalecane. Zalecenia w tym artykule są grupowane w zależności od rodzaju zasobów, aby znajdować, czy pełna aplikacji, poszczególnych procesów i danych.

## <a name="web-applications"></a>Aplikacje internetowe

Aplikacje sieci Web mogą być przechowywane za pomocą:

- Aplikacje sieci Web usługi App Service

- Kontenery

- Azure Service Fabric

- Maszyny wirtualne (VM)

Z tych opcji App Service Web Apps to zalecane podejście do większości scenariuszy. Architektury mikrousługi należy wziąć pod uwagę podejście oparte na kontenerach lub usługi Service Fabric. Jeśli potrzebujesz większej kontroli nad maszynami działania aplikacji, należy wziąć pod uwagę maszyn wirtualnych platformy Azure.

### <a name="app-service-web-apps"></a>Aplikacje sieci Web usługi App Service

Usługa App Service Web Apps oferuje w pełni zarządzana platforma, zoptymalizowana pod kątem hostowania aplikacji sieci web. Jest to platforma jako usługa (PaaS), oferty, że umożliwia użytkownikom skoncentrowanie się na logice biznesowej, podczas gdy platforma Azure zajmie się infrastrukturą potrzebne do uruchamiania i skalowania aplikacji. Niektóre kluczowe funkcje usługi App Service Web Apps:

- Optymalizacja metodyki DevOps (ciągła integracja i dostarczanie, wielu środowisk, A / B, testowanie, obsługi skryptów).

- Skala globalna i o wysokiej dostępności.

- Połączenia z platformami SaaS i danych w środowisku lokalnym.

- Zabezpieczenia i zgodność.

- Integracja z programem Visual Studio.

Usługa Azure App Service jest najlepszym wyborem dla większości aplikacji sieci web. Wdrażanie i zarządzanie są zintegrowane z platformą, witryny można szybko skalować w celu obsługi obciążeń z dużym ruchem i wbudowanego obciążenia równoważenia i usługa traffic manager zapewniają wysoką dostępność. Można przenieść istniejące witryny w usłudze Azure App Service za pomocą narzędzia do migracji online, korzystanie z aplikacji typu open source z galerii aplikacji sieci Web lub Utwórz nową witrynę przy użyciu framework i wybranych przez siebie narzędzi. Funkcja zadań Webjob ułatwia dodawanie zadania w tle przetwarzania do aplikacji sieci web usługi App Service.

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Usługa Azure Kubernetes Service (AKS) zarządza hostowanym środowiskiem Kubernetes, pozwalając szybko i łatwo wdrażać konteneryzowane aplikacje i Zarządzaj bez doświadczenia z organizowaniem kontenerów. Eliminuje to również obciążenia i konserwacją dzięki inicjowania obsługi administracyjnej, aktualizowaniu i skalowaniu zasobów na żądanie bez przełączania aplikacji w trybie offline.

Usługa AKS zmniejsza złożoność i nakłady operacyjne związane z zarządzaniem klastrem Kubernetes, przenosząc znaczną część tej odpowiedzialności na platformę Azure. Jako hostowana usługa Kubernetes, platforma Azure obsługuje krytyczne zadania, takie jak monitorowanie kondycji i konserwacja. Ponadto płacisz tylko za węzły agenta w ramach Twoich klastrów, nie za wzorce. Jako zarządzana usługa Kubernetes AKS zapewnia:

- Automatyczne uaktualnienia wersji platformy Kubernetes i stosowanie poprawek.
- Łatwe skalowanie klastra.
- Samonaprawialną hostowaną warstwę kontroli (wzorce).
- Oszczędności — płacisz tylko za uruchomione węzły puli agentów.

Platforma Azure obsługuje zarządzanie węzłami w klastrze AKS nie trzeba ręcznie wykonywać wielu zadań, takich jak Uaktualnianie klastra. Ponieważ platforma Azure wykonuje te krytyczne zadania konserwacji za Ciebie, AKS nie zapewnia bezpośredni dostęp (takich jak przy użyciu protokołu SSH) do klastra.

### <a name="azure-service-fabric"></a>Azure Service Fabric

Service Fabric to dobry wybór, jeśli tworzysz nową aplikację lub ponownego tworzenia istniejącej aplikacji opartych na architekturze mikrousług. Wdrożenie aplikacji działających w ramach współużytkowanej puli maszyn, można zacząć od małej i do ogromnej skali z setkami lub tysiącami maszyn, zgodnie z potrzebami. Usługi stanowe ułatwiają spójne i niezawodne przechowywanie stanu aplikacji, a Usługa Service Fabric automatycznie zarządza partycjonowaniem usługi, skalowaniem i dostępnością za Ciebie. Usługa Service Fabric obsługuje także interfejs WebAPI z Open Web Interface for .NET (OWIN) i ASP.NET Core. W porównaniu do usługi App Service, Service Fabric udostępnia więcej kontroli nad lub bezpośredni dostęp do podstawowej infrastruktury. Możesz zdalnym do serwerów lub skonfigurowania zadań uruchamiania serwera.

### <a name="azure-virtual-machines"></a>Usługa Azure Virtual Machines

Jeśli masz istniejącą aplikację, która wymagałaby istotnych zmian do uruchamiania w usłudze App Service lub Service Fabric, możesz wybrać maszyny wirtualne w celu uproszczenia migracji do chmury. Jednak poprawne skonfigurowanie, zabezpieczenie i konserwowanie maszyn wirtualnych wymaga znacznie więcej czasu i doświadczenia w zakresie IT w porównaniu do usługi Azure App Service i Service Fabric. Jeśli rozważasz usługę Azure Virtual Machines, upewnij się, że należy wziąć pod uwagę rutynowej konserwacji pracę wymaganą do dostarczenia poprawek, aktualizacji, a także zarządzać środowiskiem maszyny Wirtualnej. Usługa Azure Virtual Machines to infrastruktura jako usługa (IaaS), usługi App Service i Service Fabric są PaaS.

#### <a name="feature-comparison"></a>Porównanie funkcji

| Funkcja                                                                                    | App Service | Kontenery (AKS) | Service Fabric | Maszyna wirtualna |
| ------------------------------------------------------------------------------------------ | ----------- | ---------------- | -------------- | --------------- |
| Niemal natychmiastowe wdrażanie                                                                    | X           | X                | X              |                 |
| Skalowanie na większe maszyny bez ponownego wdrażania                                               | X           | X                | X              |                 |
| Wystąpienia współużytkują zawartość i konfigurację; nie ma potrzeby ponownego wdrażania lub ponownie podczas skalowania | X           | X                | X              |                 |
| Wiele środowisk wdrażania (produkcyjne, przejściowe)                                     | X           | X                | X              |                 |
| Automatyczne zarządzanie aktualizacjami systemu operacyjnego                                                             | X           | X                |                |                 |
| Bezproblemowe przełączanie między platformami 64-32-bitowe                                             | X           | X                |                |                 |
| Wdrażanie kodu za pomocą narzędzia Git, FTP                                                                  | X           | X                |                | X               |
| Wdrażanie kodu za pomocą WebDeploy                                                                 | X           | X                |                | X               |
| Wdrażanie kodu za pomocą serwera TFS                                                                       | X           | X                | X              | X               |
| Sieć web hosta lub warstwy usługi sieci web architektury wielowarstwowej                                    | X           | X                | X              | X               |
| Uzyskiwanie dostępu do usług platformy Azure, takich jak Service Bus, Storage, SQL Database                              | X           | X                | X              | X               |
| Instalowanie dowolnego niestandardowego pakietu MSI                                                                     |             | X                | X              | X               |

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

- Guide\ dla deweloperów platformy Azure
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Overview\ aplikacji sieci Web
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Usługa Azure App Service, maszyny wirtualne, usługi Service Fabric i Cloud Services comparison\
  <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

- Wprowadzenie do usługi Azure Kubernetes Service (AKS) \
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Poprzednie](development-process-for-azure.md)