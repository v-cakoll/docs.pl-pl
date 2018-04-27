---
title: Zalecenia dotyczące aplikacji sieci web platformy ASP.NET Core hostingu Azure
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | Zalecenia dotyczące aplikacji sieci web ASP.NET hostingu Azure
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eccb57e5ccf9162a6e6ce11434e644682881debc
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Zalecenia dotyczące aplikacji sieci Web platformy ASP.NET Core hostingu Azure

> "Biznesowych z liderów wszędzie są pomijanie działy IT, aby uzyskać aplikacje w chmurze (alias SaaS) i płatności dla nich jak Subskrypcja magazynu. I gdy usługa nie jest już wymagane, będzie można zrezygnować z subskrypcji z nie urządzeń pozostałych nieużywanych w prawym górnym rogu. "  
> _\- Daryl Plummer, Gartner analityka_

## <a name="summary"></a>Podsumowanie

Niezależnie od aplikacji potrzeb i architektura systemu Windows Azure można jego obsługi. Potrzeb hostingu może być prosty jak witryny sieci web statyczny do aplikacji bardzo zaawansowane składa się z wielu usług. Dla obsługi usług i aplikacji sieci web wbudowanymi platformy ASP.NET Core istnieje kilka dobrze znanych konfiguracji, które są zalecane. Poniższe zalecenia są pogrupowane według rodzaju zasobu do możliwości hostowania, czy pełnego aplikacji, poszczególnych procesów i danych.

## <a name="web-applications"></a>Aplikacje sieci Web

Aplikacje sieci Web mogą być przechowywane z:

-   Aplikacje sieci Web usługi aplikacji

-   Kontenery

-   Azure Service Fabric

-   Maszynach wirtualnych (VM)

Z nich aplikacje sieci Web usługi aplikacji są zalecane podejście do większości scenariuszy. Dla architektury mikrousługi należy wziąć pod uwagę opartego na kontener lub usługi sieci szkieletowej. Aby uzyskać większą kontrolę nad maszynami aplikacji, należy wziąć pod uwagę maszynach wirtualnych platformy Azure.

### <a name="app-service-web-apps"></a>Aplikacje sieci Web usługi aplikacji

Usługi aplikacji Web Apps oferuje pełni zarządzana platforma zoptymalizowane pod kątem obsługi aplikacji sieci web. Jest platform-as-a-service(PaaS), oferty, że pozwala skupić się na logice biznesowej, podczas gdy platforma Azure jest odpowiedzialna infrastruktury potrzebne do uruchamiania i skalowania aplikacji. Niektóre główne funkcje aplikacji usługi sieci Web aplikacji:

-   Optymalizacja metodyki DevOps (ciągłej integracji i dostarczania, wiele środowisk, A / B, testowanie, obsługi skryptów)

-   Globalne skalowanie i wysoka dostępność

-   Połączenia z platformami SaaS i danych lokalnych

-   Zabezpieczeń i zgodności

-   integracja z programem Visual Studio

Usługa aplikacji Azure jest najlepszym rozwiązaniem w przypadku większości aplikacji sieci web. Wdrażania i zarządzania są zintegrowane z platformy witryny można szybko skalować do obsługi obciążeń dużego natężenia ruchu sieciowego i zapewnia wysoką dostępność, Menedżera ruchu i równoważenie obciążenia wbudowanych. Można przenieść istniejących witryn w usłudze Azure App Service, łatwo za pomocą narzędzia migracji w trybie online użyć aplikacji open source z galerii aplikacji sieci Web lub Utwórz nową witrynę za pomocą framework i narzędzia wybranych przez użytkownika. Funkcja zadań Webjob ułatwia Dodaj zadanie w tle przetwarzania do aplikacji sieci web usługi aplikacji.

### <a name="containers-and-azure-container-service"></a>Kontenery i usługi kontenera platformy Azure

Usługa kontenera platformy Azure uproszczono do tworzenia, konfigurowania i zarządzania klastrem maszyn wirtualnych, które są wstępnie skonfigurowane do uruchamiania aplikacji konteneryzowanych. Używa zoptymalizowane konfiguracji popularnych narzędzi planowania i aranżacji open source. Dzięki temu można korzystać z istniejących umiejętności lub sięgać duży i rosnącym treści doświadczenia społeczności, wdrażanie i zarządzanie nimi na podstawie kontenera aplikacji w systemie Microsoft Azure.

Usługa kontenera platformy Azure uproszczono do tworzenia, konfigurowania i zarządzania klastrem maszyn wirtualnych, które są wstępnie skonfigurowane do uruchamiania aplikacji konteneryzowanych. Używa zoptymalizowane konfiguracji popularnych narzędzi planowania i aranżacji open source. Dzięki temu można korzystać z istniejących umiejętności lub sięgać duży i rosnącym treści doświadczenia społeczności, wdrażanie i zarządzanie nimi na podstawie kontenera aplikacji w systemie Microsoft Azure.

Jeden cel usługi kontenera platformy Azure jest zapewnienie środowiska macierzystego kontenera za pomocą open source, narzędzia i technologie, które są obecnie popularnością wśród klientów firmy Microsoft. W tym celu usługi kontenera platformy Azure udostępnia standardowe punkty końcowe interfejsu API dla programu orchestrator wybrany (DC/OS, Docker Swarm lub Kubernetes). Korzystając z tych punktów końcowych, można wykorzystać dowolne oprogramowanie, które jest w stanie rozmowie z tych punktów końcowych. Na przykład w przypadku punktu końcowego Docker Swarm można użyć Docker interfejsu wiersza polecenia (CLI). Dla platformy DC/OS możesz wybrać DCOS interfejsu wiersza polecenia. Dla Kubernetes możesz wybrać kubectl. Rysunek 11-1 pokazuje, jak te punkty końcowe umożliwiają zarządzanie klastrów kontenera.

![](./media/image11-1.png)

**Rysunek 11-1.** Zarządzanie usługi kontenera platformy Azure z punktami końcowymi Docker, Kubernetes lub DC/OS.

### <a name="azure-service-fabric"></a>Azure Service Fabric

Sieć szkieletowa usług jest dobrym rozwiązaniem, jeśli tworzysz nową aplikację lub ponownego zapisywania istniejących aplikacji przy użyciu architektury mikrousługi. Aplikacje, które działają w udostępnionej puli maszyn, można rozpoczęcie od czegoś małego i powiększania na ogromną skalę z setkami lub tysiącami maszyn zgodnie z potrzebami. Usługi stanowej ułatwiają spójnie i niezawodne przechowywanie stanu aplikacji i sieci szkieletowej usług automatycznie zarządza partycjonowania usługi, skalowanie i dostępność dla Ciebie. Sieć szkieletowa usług obsługuje również WebAPI z interfejsu Open Web dla platformy .NET (OWIN) i ASP.NET Core. W porównaniu do usługi App Service, usługi sieć szkieletowa dostępne są także więcej kontroli nad lub bezpośredni dostęp do podstawowej infrastruktury. Możesz zdalnym do serwerów lub skonfigurować zadania uruchamiania serwera.

### <a name="azure-virtual-machines"></a>Maszyny wirtualne platformy Azure

Jeśli masz istniejącą aplikację wymagające istotne zmiany do uruchamiania w usługi aplikacji lub usługi sieci szkieletowej, można wybrać w celu uproszczenia migracji do chmury maszyn wirtualnych. Jednak poprawnie konfigurowania, zabezpieczania i obsługa maszyn wirtualnych wymaga znacznie więcej czasu i doświadczenia IT w porównaniu do usługi Azure App Service i sieci szkieletowej usług. Planując maszynach wirtualnych platformy Azure, upewnij się, że należy wziąć pod uwagę nakładu rutynowej konserwacji wymagane do stosowania poprawek, aktualizacji i zarządzania środowiskiem maszyny Wirtualnej. Maszyny wirtualne platformy Azure jest infrastruktury jako — usługa (IaaS), a usługi aplikacji i sieci szkieletowej usług platformy jako — usługa (Paas).

#### <a name="feature-comparison"></a>Porównanie funkcji

| Usługi aplikacji — funkcja | Sieci szkieletowej usług | Maszyny wirtualne |
|---------|----------|----------|
| Niemal natychmiastowe wdrożenia | X | X | |
| Skalowanie w górę do większych maszyn bez ponownego wdrażania | X | X | |
| Wystąpienia udostępniania zawartości i konfiguracji. konieczność ponownego wdrażania lub ponownej konfiguracji podczas skalowania | X | X | |
| Wiele środowisk wdrażania (produkcji, przemieszczania) | X | X | |
| Automatyczne zarządzanie aktualizacjami systemu operacyjnego | X | | |
| Bezproblemowe przełączenie między platformami 32/x 64 | X | | |
| Wdrażanie kodu za pomocą narzędzia Git, FTP | X | | X |
| Wdrażanie kodu przy WebDeploy | X | | X |
| Wdrażanie kodu z programem TFS | X | X | X |
| Witryna sieci web hosta lub warstwy usług sieci web w wielowarstwowych architektury | X | X | X |
| Dostęp do usług Azure, takich jak usługi Service Bus, magazynu, baza danych SQL | X | X | X |
| Zainstaluj wszelkie niestandardowe MSI | | X | X |

## <a name="logical-processes"></a>Procesy logiczne

Poszczególnych logicznej procesów, które mogą być całkowicie niezależna od pozostałej części aplikacji może niezależnie wdrożyć do usługi Azure Functions w sposób "pliki". Środowisko Azure Functions umożliwia tylko napisać kod, potrzebnych dla danego problemu, nie martwiąc się o aplikacji lub infrastruktury, aby go uruchomić. Można wybierać spośród różnych języków programowania, w tym C\#, F\#, Node.js, Python i PHP, co umożliwia pobranie najbardziej produktywności języka zadania wykonywanego. Podobnie jak większość rozwiązań w chmurze płacisz tylko przez czas użytkowania i ufasz usługi Azure Functions można skalować zgodnie z potrzebami.

## <a name="data"></a>Dane

System Azure oferuje szeroką gamę opcji przechowywania danych, dzięki czemu aplikacja może używać dostawcy danych odpowiednie dla danego danych.

W przypadku danych transakcyjnych, relacyjnych baz danych SQL Azure są najlepszym rozwiązaniem. W przypadku wysokiej wydajności odczytu głównie danych pamięci podręcznej Redis obsługiwana przez bazę danych SQL Azure jest dobrym rozwiązaniem.

Dane JSON bez struktury mogą być przechowywane w różnych sposobów, z kolumny bazy danych SQL do obiektów blob lub tabel w magazynie Azure DocumentDB. Z nich usługa DocumentDB oferuje najlepsze funkcjach zapytań i jest to zalecana opcja, w przypadku dużej liczby dokumentów opartych na formacie JSON, które muszą obsługiwać zapytań.

Przejściowa polecenia - lub opartego na zdarzeniach danych używane do organizowania zachowanie aplikacji można użyć usługi Azure Service Bus lub kolejek magazynu Azure. Azure Storage Bus zapewnia większą elastyczność i jest zalecany usługi nieuproszczony obsługi wiadomości w obrębie i między aplikacjami.

## <a name="architecture-recommendations"></a>Zalecenia dotyczące architektury

Wymagania dotyczące aplikacji powinny definiować jego architektury. Brak dostępnych wielu różnych usług Azure, wybierając właściwą jest bardzo ważne. Firma Microsoft oferuje galerii architektury odwołania do identyfikowania typowe architektury zoptymalizowane pod kątem typowych scenariuszy. Architektura referencyjna, że mapy do wymagań aplikacji lub na najmniej zapewnia punkt początkowy może powiązać.

Rysunek 11-2 przedstawiono przykład architekturę odwołania. Ten schemat przedstawia podejście zalecane architektura Sitecore witrynie system zarządzania zawartością zoptymalizowane pod kątem obrotu.

![](./media/image11-2.png)

**Rysunek 11-2.** Sitecore marketing architektura referencyjna witryny sieci Web.

**Odwołania — zalecenia dotyczące hostingu Azure**

-   Architectures\ rozwiązania Azure
    <https://azure.microsoft.com/solutions/architecture/>

-   Guide\ deweloperów platformy Azure
    <https://azure.microsoft.com/campaigns/developer-guide/>

-   Co to jest usługa aplikacji Azure? \
    <https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is>

-   Usługa aplikacji Azure, maszyny wirtualne i usługi sieć szkieletowa Comparison\ usługi w chmurze
    <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

>[!div class="step-by-step"]
[Previous] (development-process-for-azure.md)
