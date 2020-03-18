---
title: Modernizacja istniejących aplikacji .NET za pomocą usługi Azure Cloud i kontenerów systemu Windows (wydanie 2.
description: Dowiedz się, jak podnosić i zmieniać i modernizować istniejące aplikacje do chmury platformy Azure i kontenerów za pomocą tego e-booka.
ms.date: 04/28/2018
ms.openlocfilehash: 9439de84dd46ac3153d951378764d10184c33a52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628455"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows (wydanie 2.

![Obraz okładki przewodnika aplikacji Modernizuj .NET.](./media/index/web-application-guide-cover-image.png)

OPUBLIKOWANA PRZEZ  
Prasa Microsoft i Microsoft DevDiv  
Oddziały Microsoft Corporation  
One Microsoft Way  
Redmond (Waszyngton) 98052-6399  

Prawa autorskie © 2020 r. przez Firmę Microsoft Corporation  

Wszelkie prawa zastrzeżone. Żadna część treści tej książki nie może być powielana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ta książka jest dostępna bezpłatnie w formie książki elektronicznej (e-book) dostępnej za pośrednictwem wielu kanałów w firmie Microsoft, takich jak <https://dot.net/architecture>.

Jeśli masz pytania związane z tą [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)książką, wyślij e-mail na adres .

Ta książka jest "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Microsoft i znaki towarowe <https://www.microsoft.com> wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft. Wszystkie pozostałe znaki towarowe są własnością ich właścicieli.

Autor:
> **Cesar de la Torre**, Sr. PM, .NET Product Team, Microsoft Corp.

Uczestnicy i recenzenci:
> **Scott Hunter**, Dyrektor Partnera PM, zespół .NET, Microsoft  
> **Paweł Yuknewicz**, Główny Kierownik PM, Zespół Narzędzi Wizualnych, Microsoft  
> **Lisa Guthrie**, Sr. PM, Zespół Narzędzi Programu Visual Studio, Microsoft  
> **Ankit Asthana**, Główny menedżer PM, zespół .NET, Microsoft  
> **Unai Zorrilla**, Developer Lead, Proste koncepcje  
> **Javier Valero**, Chief Operating Officer w Grupo Solutio  

## <a name="introduction"></a>Wprowadzenie

Gdy zdecydujesz się zmodernizować aplikacje lub usługi internetowe i przenieść je do chmury, nie musisz w pełni przeprojektować swoich aplikacji. Rearchitecting aplikacji przy użyciu zaawansowanego podejścia, takich jak mikrousług nie zawsze jest opcją ze względu na ograniczenia kosztów i czasu. W zależności od typu aplikacji ponowne gozaprojektowanie aplikacji również może nie być konieczne. Aby zoptymalizować opłacalność strategii migracji w chmurze organizacji, należy wziąć pod uwagę potrzeby firmy i wymagania aplikacji. Musisz określić:

- Które aplikacje wymagają transformacji lub przeprojektowania.

- Które aplikacje muszą być tylko częściowo zmodernizowane.

- Jakie aplikacje można "podnieść i przenieść" bezpośrednio do chmury.

## <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik koncentruje się przede wszystkim na początkowej modernizacji istniejących aplikacji internetowych lub zorientowanych na usługi microsoft .NET Framework, co oznacza akcję przenoszenia obciążenia do nowszego lub bardziej nowoczesnego środowiska bez znaczącej zmiany kodu aplikacji i podstawową architekturę.

W tym przewodniku przedstawiono również zalety przenoszenia aplikacji do chmury i częściowej modernizacji aplikacji przy użyciu określonego zestawu nowych technologii i metod, takich jak kontenery systemu Windows i powiązane platformy obliczeniowe na platformie Azure obsługujące kontenery systemu Windows.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Ścieżka do chmury dla istniejących aplikacji .NET

Organizacje zazwyczaj decydują się na przejście do chmury ze względu na elastyczność i szybkość, jaką mogą uzyskać dla swoich aplikacji. W ciągu kilku minut można skonfigurować tysiące serwerów (VM) w chmurze w porównaniu z tygodniami, które zwykle są potrzebne do skonfigurowania serwerów lokalnych.

Nie ma jednej, uniwersalnej strategii migracji aplikacji do chmury. Właściwa strategia migracji zależy od potrzeb i priorytetów organizacji oraz rodzaju migracji aplikacji. Nie wszystkie aplikacje uzasadniają inwestycję w przejście na model platformy jako usługi[(PaaS)](https://azure.microsoft.com/overview/what-is-paas/)lub opracowanie modelu aplikacji [natywnej dla chmury.](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) W wielu przypadkach można przyjąć stopniowe lub stopniowe podejście do inwestowania w przenoszenie zasobów do chmury, w zależności od potrzeb biznesowych.

W przypadku nowoczesnych aplikacji o najlepszej długoterminowej elastyczności i wartości dla organizacji możesz skorzystać z inwestowania w architektury aplikacji *natywnych dla chmury.* Jednak w przypadku aplikacji, które są istniejącymi lub starszymi zasobami, kluczem jest spędzanie minimalnego czasu i pieniędzy (bez zmiany architekta lub zmiany kodu) podczas przenoszenia ich do chmury, aby uzyskać znaczące korzyści.

Rysunek 1-1 przedstawia możliwe ścieżki, które można podjąć podczas przenoszenia istniejących aplikacji .NET do chmury w fazach przyrostowych.

 ![Ścieżki modernizacji dla istniejących aplikacji i usług .NET](./media/image1-1.png)

**Rysunek 1-1**. Ścieżki modernizacji dla istniejących aplikacji i usług .NET

Każde podejście do migracji ma różne zalety i powody korzystania z niego. Podczas migracji aplikacji do chmury można wybrać jedną opcję lub wybrać niektóre składniki z wielu metod. Poszczególne aplikacje nie są ograniczone do jednego podejścia lub stanu dojrzałości. Na przykład wspólne podejście hybrydowe będzie miał niektórych składników lokalnych oraz innych składników w chmurze.

Definicja i krótkie wyjaśnienie dla każdego poziomu dojrzałości aplikacji są następujące:

Poziom 1: Aplikacje **gotowe do obsługi infrastruktury w chmurze:** W tym podejściu migracji po prostu migrować lub ponownie hostować bieżące aplikacje lokalne do platformy infrastruktury jako usługi[(IaaS).](https://azure.microsoft.com/overview/what-is-iaas/) Aplikacje mają prawie taką samą kompozycję jak poprzednio, ale teraz wdrażasz je na maszynach wirtualnych w chmurze.
Ten prosty typ migracji jest zazwyczaj znany w branży jako "Lift & Shift".

Poziom 2: Aplikacje **zoptymalizowane pod kątem chmury:** Na tym poziomie i nadal bez ponownego projektowania lub zmiany znaczącego kodu, można uzyskać dodatkowe korzyści z uruchamiania aplikacji w chmurze z nowoczesnych technologii, takich jak kontenery i dodatkowe usługi zarządzane w chmurze. Zwiększasz elastyczność aplikacji, aby szybciej wysyłać, udoskonalając procesy rozwoju przedsiębiorstwa (DevOps). Można to osiągnąć przy użyciu technologii, takich jak kontenery systemu Windows, który jest oparty na docker engine. Kontenery usunąć tarcie, które jest spowodowane przez zależności aplikacji podczas wdrażania w wielu etapach. W tym modelu dojrzałości można wdrożyć kontenery na IaaS lub PaaS przy użyciu dodatkowych usług zarządzanych w chmurze związanych z bazami danych, pamięci podręcznej jako usługi, monitorowania i ciągłej integracji/ciągłego wdrażania (CI/CD) potoków.

Trzeci poziom dojrzałości jest ostatecznym celem w chmurze, ale jest opcjonalny dla wielu aplikacji, a nie głównym celem tego przewodnika:

Poziom 3: Aplikacje **natywne dla chmury:** To podejście do migracji jest zazwyczaj napędzane potrzebami biznesowymi i jest przeznaczona na modernizację aplikacji o znaczeniu krytycznym. Na tym poziomie używasz usług PaaS, aby przenieść swoje aplikacje na platformy obliczeniowe PaaS. Implementujesz aplikacje [natywne dla chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) i architekturę mikrousług, aby rozwijać aplikacje z długoterminową elastycznością i skalować do nowych limitów. Ten rodzaj modernizacji zwykle wymaga projektowania specjalnie dla chmury. Nowy kod często musi być napisany, zwłaszcza po przejściu do aplikacji natywnych dla chmury i modeli opartych na mikrousługach. Takie podejście może pomóc w uzyskaniu korzyści, które są trudne do osiągnięcia w środowisku aplikacji monolitycznych i lokalnych.

W tabeli 1-1 opisano główne zalety i powody wyboru każdego podejścia do migracji lub modernizacji.

| **Infrastruktura w chmurze gotowa** <br /> *Migrowanie metodą „lift-and-shift”* | **Zoptymalizowane pod kątem chmury** <br /> *Modernizacji* | **Natywna w chmurze** <br /> *Modernizacja, rearchitect i przepisać* |
|---|---|---|
| **Docelowy obliczeniowy aplikacji** |
| Aplikacje wdrożone na maszynach wirtualnych na platformie Azure | Aplikacje monolityczne lub n-warstwowe wdrożone w usłudze Azure App Service, wystąpieniu usługi Azure Container Instance (ACI), maszynach wirtualnych z kontenerami lub usłudze AKS (usługa Azure Kubernetes) | Konteneryzowane mikrousługi w usłudze Azure Kubernetes Service (AKS) i/lub mikrousługi bezserwerowe oparte na funkcjach platformy Azure. |
| **Cel danych** |
| SQL lub dowolna relacyjna baza danych na maszynie wirtualnej | Wystąpienie zarządzane bazy danych SQL platformy Azure lub inna zarządzana baza danych w chmurze. | Bazy danych ziarnem ukarane na mikrousługę, oparte na bazie danych SQL Azure, usłudze Azure Cosmos DB lub innej zarządzanej bazie danych w chmurze |
| **Zalety**|
| <li>Bez przebudowy, bez nowego kodu <li> Najmniej wysiłku w szybkiej migracji <li> Najmniej typowy mianownik obsługiwany na platformie Azure <li> Podstawowe gwarancje dostępności <li> Po przejściu do chmury łatwiej jest jeszcze bardziej zmodernizować | <li> Brak przebudowy <li> Minimalne zmiany kodu/konfiguracji <li> Ulepszone wdrożenie i elastyczność devops do wydania z powodu kontenerów <li> Większa gęstość i niższe koszty wdrożenia <li> Przenośność aplikacji i zależności <li> Elastyczność celów gospodarza: podejścia PaaS lub IaaS | <li> Architekt dla chmury, otrzymujesz najlepsze korzyści z chmury, ale potrzebny jest nowy kod <li> Podejścia natywne dla mikrousług w chmurze <li> Nowoczesne aplikacje o znaczeniu krytycznym, odporne na chmury hiperskalowalne <li> W pełni zarządzane usługi <li> Zoptymalizowany pod kątem skali <li> Zoptymalizowany pod kątem autonomii sprawności przez podsystem <li> Zbudowany na wdrożeniu i devops |
| **Wyzwania** |
| <li> Mniejsza wartość chmury, inna niż zmiana kosztów operacyjnych lub zamykanie centrów danych <li> Niewiele się udało: Brak poprawki systemu operacyjnego lub pośredniczenia; mogą korzystać z rozwiązań infrastrukturalnych, takich jak Terraform, Spinnaker lub Puppet | <li> Konteneryzacja to dodatkowy krok w krzywej uczenia się dla deweloperów i operacji IT <li> DevOps i potoków ciągłej integracji/cd są zwykle "koniecznością" dla tego podejścia. Jeśli nie jest obecnie obecny w kulturze organizacji, może to być dodatkowe wyzwanie| <li> Wymaga ponownej architektury dla aplikacji natywnych w chmurze i architektur mikrousług i zwykle wymaga znacznego refaktoryzacji kodu lub przepisywania podczas modernizacji (zwiększony czas i budżet)|
> **Tabela 1-1.** Korzyści i wyzwania związane ze ścieżkami modernizacji dla istniejących aplikacji i usług .NET

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Kluczowe technologie i architektury według poziomu dojrzałości

Aplikacje .NET Framework początkowo uruchamiane z .NET Framework w wersji 1.0, która została wydana pod koniec 2001 roku. Następnie firmy przeniosły się do nowszych wersji (takich jak 2.0, 3.5 i .NET 4.x). Większość z tych aplikacji działała na windows server i Internet Information Server (IIS) i używała relacyjnej bazy danych, takiej jak SQL Server, Oracle, MySQL lub jakikolwiek inny rdbms.

Większość istniejących aplikacji .NET może obecnie opierać się na programie .NET Framework 4.x, a nawet na platformie .NET Framework 3.5 i używać struktur sieci Web, takich jak ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, Windows Communication Foundation (WCF), ASP.NET SignalR i ASP.NET stron sieci Web . Te ustanowione technologie .NET Framework zależą od systemu Windows. Ta zależność jest ważne, aby wziąć pod uwagę, jeśli po prostu migracji starszych aplikacji i chcesz wprowadzić minimalne zmiany w infrastrukturze aplikacji.

Rysunek 1-2 przedstawia podstawowe technologie i style architektury używane na każdym z trzech poziomów dojrzałości chmury:

![Podstawowe technologie dla każdego poziomu dojrzałości do modernizacji istniejących aplikacji sieci Web .NET](./media/image1-2.png)

**Rysunek 1-2.** Podstawowe technologie dla każdego poziomu dojrzałości do modernizacji istniejących aplikacji sieci Web .NET

Rysunek 1-2 podkreśla najczęstsze scenariusze, ale wiele odmian hybrydowych i mieszanych jest możliwych, jeśli chodzi o architekturę. Na przykład modele dojrzałości dotyczą nie tylko monolitycznych architektur w istniejących aplikacjach sieci web, ale także orientacji usługi, n-warstwy i innych odmian stylu architektury. Większy nacisk lub procent na jeden lub inny typ architektury i powiązanych technologii określa ogólny poziom dojrzałości aplikacji.

Każdy poziom dojrzałości w procesie modernizacji jest skojarzony z następującymi kluczowymi technologiami i podejściami:

- **Infrastruktura w chmurze (rehost** lub podstawowy winda & shift): W pierwszym kroku wiele organizacji chce tylko szybko wykonać strategię migracji do chmury. W takim przypadku aplikacje są hostowane ponownie. Większość ponownego hostingu można zautomatyzować przy użyciu [usługi Azure Migrate](https://aka.ms/azuremigrate), usługi, która zapewnia wskazówki, szczegółowe informacje i mechanizmy potrzebne do pomocy w migracji do platformy Azure na podstawie narzędzi w chmurze, takich jak [usługa Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) i usługa Azure Database Migration [Service](https://azure.microsoft.com/campaigns/database-migration/). Możesz również ręcznie skonfigurować rehosting, aby uzyskać szczegółowe informacje o zasobach po przeniesieniu starszych aplikacji do chmury. Na przykład można przenieść aplikacje do maszyn wirtualnych na platformie Azure z niewielkim modyfikacji, prawdopodobnie tylko z niewielkimi zmianami konfiguracji. Sieć w tym przypadku jest podobna do środowiska lokalnego, zwłaszcza w przypadku tworzenia sieci wirtualnych na platformie Azure.

- **Zoptymalizowane pod kątem chmury** (usługi zarządzane i kontenery systemu Windows): Ten model polega na tworzeniu kilku ważnych optymalizacji wdrażania w celu uzyskania znaczących korzyści z chmury bez zmiany podstawowej architektury aplikacji. Podstawowym krokiem w tym miejscu jest dodanie obsługi [kontenerów systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do istniejących aplikacji .NET Framework. Ten ważny krok (konteneryzacja) nie wymaga dotykania kodu, więc ogólny wysiłek podnoszenia i zmiany jest lekki. Za pomocą narzędzi, takich jak [Image2Docker](https://github.com/docker/communitytools-image2docker-win) lub Visual Studio, można używać za pomocą narzędzi do [platformy Docker](https://www.docker.com/). Program Visual Studio automatycznie wybiera inteligentne ustawienia domyślne dla ASP.NET aplikacji i obrazów kontenerów systemu Windows. Te narzędzia oferują zarówno szybką pętlę wewnętrzną, jak i szybką ścieżkę umożliwiającą uzyskanie kontenerów na platformę Azure. Elastyczność jest ulepszona podczas wdrażania w wielu środowiskach.
Następnie, przechodząc do środowiska produkcyjnego, można wdrożyć kontenery systemu Windows w [usłudze Azure Web App for Containers,](https://azure.microsoft.com/services/app-service/containers/) [wystąpienia kontenerów platformy Azure (ACI)](https://azure.microsoft.com/services/container-instances/)i maszyny wirtualne platformy Azure z systemem Windows Server 2016 i kontenerów, jeśli wolisz podejście IaaS. W przypadku bardziej złożonych aplikacji wielokontenerowych należy rozważyć użycie koordynatorów, takich jak [usługa Azure Kubernetes Service (AKS/ACS).](https://azure.microsoft.com/services/container-service/)

Podczas tej początkowej modernizacji można również dodać zasoby z chmury, takie jak monitorowanie za pomocą narzędzi, takich jak [usługa Azure Application Insights;](https://docs.microsoft.com/azure/application-insights/app-insights-overview) Potoki ciągłej integracji/ciągłego rozwoju dla cyklu życia aplikacji z [usługami Azure DevOps;](https://azure.microsoft.com/services/devops/) i wiele innych usług zasobów danych, które są dostępne na platformie Azure. Na przykład można zmodyfikować monolityczną aplikację internetową, która została pierwotnie opracowana przy użyciu tradycyjnych [ASP.NET formularzy sieci Web](https://www.asp.net/web-forms) lub ASP.NET [MVC](https://www.asp.net/mvc), ale teraz można ją wdrożyć przy użyciu kontenerów systemu Windows. Korzystając z kontenerów systemu Windows, należy również migrować dane do bazy danych w [wystąpieniu zarządzanym bazy danych azure SQL](https://docs.microsoft.com/azure/sql-database/), wszystko bez zmiany architektury podstawowej aplikacji.

- **Natywna w chmurze**: Zgodnie z wprowadzeniem należy pomyśleć o projektowaniu aplikacji [natywnych dla chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) podczas kierowania na duże i złożone aplikacje z wieloma niezależnymi zespołami programistycznymi pracującymi nad różnymi mikrousługami, które można rozwijać i wdrażać autonomicznie. Ponadto ze względu na ziarnistą i niezależną skalowalność na mikrousługę. Te podejścia architektoniczne stoją w obliczu bardzo ważnych wyzwań i złożoności, ale można znacznie uprościć za pomocą usługi PaaS w chmurze i koordynatorów, takich jak [usługa Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (zarządzane Kubernetes) i [usługi Azure Functions](https://azure.microsoft.com/services/functions/) dla podejścia bezużycia serwera. Wszystkie te metody (takie jak mikrousługi i bezserwerowe) zazwyczaj wymagają architekta dla chmury i napisać nowy kod — kod, który jest dostosowany do określonych platform PaaS lub kod, który jest zgodny z określonymi architekturami, takimi jak mikrousługi.

Rysunek 1-3 przedstawia wewnętrzne technologie, których można użyć dla każdego poziomu dojrzałości:

![Technologie wewnętrzne dla każdego poziomu dojrzałości modernizacji](./media/image1-3.png)

**Rysunek 1-3.** Technologie wewnętrzne dla każdego poziomu dojrzałości modernizacji

## <a name="lift-and-shift-scenario"></a>Scenariusz podnoszenia i zmiany

W przypadku migracji podnoszenia i zmiany należy pamiętać, że można użyć wielu różnych odmian podnoszenia i zmiany w scenariuszach aplikacji. Jeśli tylko rehost aplikacji, może mieć scenariusz podobny do tego pokazanego na rysunku 1-4, gdzie używasz maszyn wirtualnych w chmurze tylko dla aplikacji i serwera bazy danych.

![Przykład czystego scenariusza IaaS w chmurze](./media/image1-4.png)

**Rysunek 1-4**. Przykład czystego scenariusza IaaS w chmurze

## <a name="modernization-scenarios"></a>Scenariusze modernizacji

W przypadku scenariuszy modernizacji może mieć czystą aplikację zoptymalizowaną pod kątem chmury, która używa elementów tylko z tego poziomu dojrzałości. Lub może mieć aplikację pośredniego stanu z niektórych elementów z cloud Infrastructure-Ready i innych elementów z cloud-Optimized ("wybierz i wybierz" lub model mieszany), jak na rysunku 1-5.

![Przykładowy scenariusz "wybierz i wybierz" z bazą danych na iaaS, DevOps i zasobami konteneryzacji](./media/image1-5.png)

**Rysunek 1-5.** Przykładowy scenariusz "wybierz i wybierz" z bazą danych na iaaS, DevOps i zasobami konteneryzacji

Następnie, jako idealny scenariusz dla wielu istniejących aplikacji .NET Framework do migracji, można przeprowadzić migrację do aplikacji zoptymalizowanej pod kątem chmury, aby uzyskać znaczące korzyści z niewielkiej pracy. Takie podejście ustawia również dla cloud-native jako możliweprzyszłej ewolucji. Rysunek 1-6 przedstawia przykład.

![Przykładowy scenariusz aplikacji zoptymalizowany pod kątem chmury z kontenerami systemu Windows i usługami zarządzanymi](./media/image1-6.png)

**Rysunek 1-6.** Przykładowy scenariusz aplikacji zoptymalizowany pod kątem chmury z kontenerami systemu Windows i usługami zarządzanymi

Idąc jeszcze dalej, można rozszerzyć istniejącej aplikacji zoptymalizowanej pod kątem chmury, dodając kilka mikrousług dla określonych scenariuszy. Spowoduje to przeniesienie się częściowo do poziomu modelu cloud-native, który nie jest głównym celem niniejszych wskazówek.

## <a name="what-this-guide-does-not-cover"></a>Co ten przewodnik nie obejmuje

Ten przewodnik obejmuje określony podzbiór przykładowych scenariuszy, jak pokazano na rysunku 1-7. Ten przewodnik koncentruje się tylko na scenariuszach podnoszenia i zmiany, a ostatecznie na modelu zoptymalizowanym pod kątem chmury. W modelu zoptymalizowanym pod kątem chmury aplikacja .NET Framework jest modernizowana przy użyciu kontenerów systemu Windows, a także dodatkowych składników, takich jak monitorowanie i potoki ciągłej integracji/ciągłego przetwarzania danych. Każdy składnik ma podstawowe znaczenie dla wdrażania aplikacji w chmurze, szybciej i z elastycznością.

![Cloud-Native nie jest objęty tym przewodnikiem](./media/image1-7.png)

**Rysunek 1-7.** Cloud-Native nie jest objęty tym przewodnikiem

Temat ten przewodnik jest specyficzny. Pokazuje ścieżkę, którą można podjąć, aby osiągnąć windę i przesunięcie istniejących aplikacji .NET, bez ponownego projektowania i bez zmian kodu. Ostatecznie pokazuje, jak dokonać aplikacji zoptymalizowane pod kątem chmury.

W tym przewodniku nie przedstawiono sposobu tworzenia aplikacji natywnych dla chmury, takich jak ewoluować do architektury mikrousług. Aby zmienić architekta aplikacji lub utworzyć zupełnie nowe aplikacje oparte na mikrousługach, zobacz e-book [.NET Microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Cykl życia aplikacji doplatformowania kontenerowego z platformą i narzędziami firmy Microsoft** (e-book do pobrania) \
  <https://aka.ms/dockerlifecycleebook>

- **.NET Microservices: Architektura konteneryzowanych aplikacji .NET** (e-book do pobrania) \
  <https://aka.ms/microservicesebook>

- **Projektowanie nowoczesnych aplikacji internetowych z ASP.NET Core i Azure** (e-book do pobrania) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Kto powinien skorzystać z tego przewodnika

Ten przewodnik został napisany dla deweloperów i architektów rozwiązań, którzy chcą zmodernizować istniejące ASP.NET aplikacji sieci web lub usług WCF, które są oparte na .NET Framework, dla zwiększenia elastyczności w wysyłaniu i zwalnianiu aplikacji.

Ten przewodnik może również okazać się przydatny, jeśli jesteś twórcą decyzji technicznych, takim jak architekt przedsiębiorstwa lub kierownik/dyrektor rozwoju, który chce tylko omówienie korzyści, które można uzyskać przy użyciu kontenerów systemu Windows i wdrażając w chmurze podczas korzystania z platformy Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak korzystać z tego przewodnika

Ten przewodnik dotyczy "dlaczego", dlaczego warto zmodernizować istniejące aplikacje, oraz konkretne korzyści wynikające z używania kontenerów systemu Windows podczas przenoszenia aplikacji do chmury. Treść w pierwszych kilku rozdziałach przewodnika jest przeznaczona dla architektów i decydentów technicznych, którzy chcą przeglądu, ale którzy nie muszą koncentrować się na implementacji i technicznych, szczegółowych szczegółach krok po kroku.

Ostatni rozdział tego przewodnika wprowadza wiele instruktaże, które koncentrują się na określonych scenariuszy wdrażania. Ten przewodnik zawiera krótsze wersje instruktaże, aby podsumować scenariusze i wyróżnić ich korzyści. Pełne instruktaże przechodzenia do szczegółów konfiguracji i implementacji i są publikowane jako zestaw [wpisów wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) w tym samym publicznym [repozytowie GitHub,](https://github.com/dotnet-architecture/eShopModernizing) w którym znajdują się powiązane przykładowe aplikacje (omówione w następnej sekcji). Ostatni rozdział i instruktaże wiki krok po kroku w GitHubie będą bardziej interesujące dla deweloperów i architektów, którzy chcą skupić się na szczegółach implementacji.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Przykładowe aplikacje do modernizacji starszych aplikacji: eShopModernizing

Repo [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) w serwisie GitHub oferuje dwie przykładowe aplikacje, które symulują starsze monolityczne aplikacje internetowe. Jedna aplikacja internetowa jest rozwijany przy użyciu ASP.NET MVC; druga aplikacja sieci web jest rozwijany przy użyciu ASP.NET formularzy sieci Web, a trzecia aplikacja jest aplikacja N-Tier z aplikacją pulpitu klienta WinForms zużywa zaplecza usługi WCF. Wszystkie te aplikacje są oparte na tradycyjnej platformie .NET Framework. Te przykładowe aplikacje nie używają .NET Core lub ASP.NET Core, ponieważ mają być istniejące/starsze aplikacje .NET Framework do modernizacji.

Te przykładowe aplikacje mają drugą wersję, z modernizowanym kodem i które są dość proste. Najważniejszą różnicą między wersjami aplikacji jest to, że druga wersja używa kontenerów systemu Windows jako wyboru wdrożenia. Istnieje również kilka dodatków do drugiej wersji, takich jak obiekty Blob usługi Azure Storage do zarządzania obrazami, usługa Azure Active Directory do zarządzania zabezpieczeniami i usługi Azure Application Insights do monitorowania i inspekcji aplikacji.

## <a name="send-your-feedback"></a>Wyślij swoją opinię

Ten przewodnik został napisany, aby ułatwić zrozumienie opcji ulepszania i modernizacji istniejących aplikacji sieci Web .NET. Przewodnik i powiązane przykładowe aplikacje ewoluują. Chętnie poznamy Twoją opinię! Jeśli masz uwagi na temat tego, jak ten [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)przewodnik może być bardziej pomocne, wyślij je do .

>[!div class="step-by-step"]
>[Dalej](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
