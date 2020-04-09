---
title: Zmodernizuj istniejące aplikacje platformy .NET za pomocą kontenerów w chmurze azure i windows (wydanie drugiej)
description: Dowiedz się, jak przenosić i modernizować istniejące aplikacje do chmury i kontenerów platformy Azure za pomocą tego e-booka.
ms.date: 04/28/2018
ms.openlocfilehash: 95a5870254481a4c6c9eed82b5be5e1eb10be346
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987949"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Zmodernizuj istniejące aplikacje platformy .NET za pomocą chmury Azure i kontenerów systemu Windows (wydanie drugiej)

![Okładka przewodnika modernizuj aplikacje .NET.](./media/index/web-application-guide-cover-image.png)

OPUBLIKOWANA PRZEZ  
Microsoft Press i Microsoft DevDiv  
Oddziały firmy Microsoft Corporation  
One Microsoft Way  
Redmond, Waszyngton 98052-6399  

Prawa autorskie © 2020 roku przez Microsoft Corporation  

Wszelkie prawa zastrzeżone. Żadna część zawartości tej książki nie może być powielana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ta książka jest dostępna za darmo w formie książki elektronicznej (e-book) <https://dot.net/architecture>dostępnej za pośrednictwem wielu kanałów w firmie Microsoft, takich jak.

Jeśli masz pytania związane z tą [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)książką, wyślij wiadomość e-mail na adres .

Książka ta jest dostarczana "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Firma Microsoft i znaki <https://www.microsoft.com> towarowe wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft. Wszystkie pozostałe znaki są własnością ich odpowiednich właścicieli.

Autor:
> **Cesar de la Torre**, Sr. PM, .NET Product Team, Microsoft Corp.

Uczestnicy i recenzenci:
> **Scott Hunter**, Dyrektor Handlowy PM, zespół .NET, Microsoft  
> **Paul Yuknewicz**, Główny Menedżer PM, zespół Visual Studio Tools, Microsoft  
> **Lisa Guthrie**, Sr. PM, zespół Visual Studio Tools, Microsoft  
> **Ankit Asthana**, Główny Menedżer PM, zespół .NET, Microsoft  
> **Unai Zorrilla**, Główny Deweloper, Plain Concepts  
> **Javier Valero**, Chief Operating Officer w Grupo Solutio  

## <a name="introduction"></a>Wprowadzenie

Gdy zdecydujesz się zmodernizować aplikacje lub usługi sieci web i przenieść je do chmury, nie musisz w pełni rearchitect aplikacji. Rearchitecting aplikacji przy użyciu zaawansowanego podejścia, takich jak mikrousług nie zawsze jest opcją ze względu na ograniczenia kosztów i czasu. W zależności od typu aplikacji rearchitecting aplikacji również może nie być konieczne. Aby zoptymalizować opłacalność strategii migracji do chmury w organizacji, należy wziąć pod uwagę potrzeby firmy i wymagania aplikacji. Musisz określić:

- Aplikacje, które wymagają transformacji lub rearchitecting.

- Które aplikacje muszą być tylko częściowo zmodernizowane.

- Które aplikacje można "podnieść i przesunąć" bezpośrednio do chmury.

## <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik koncentruje się przede wszystkim na początkowej modernizacji istniejących aplikacji sieci web lub aplikacji zorientowanych na usługi Microsoft .NET Framework, co oznacza akcję przenoszenia obciążenia do nowszego lub bardziej nowoczesnego środowiska bez znaczącej zmiany kodu aplikacji i architektury podstawowej.

W tym przewodniku przedstawiono również korzyści wynikające z przenoszenia aplikacji do chmury i częściowego unowocześniania aplikacji przy użyciu określonego zestawu nowych technologii i podejść, takich jak kontenery systemu Windows i powiązane platformy obliczeniowe na platformie Azure obsługujące kontenery systemu Windows.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Ścieżka do chmury dla istniejących aplikacji .NET

Organizacje zazwyczaj decydują się przenieść do chmury dla elastyczności i szybkości, które mogą uzyskać dla swoich aplikacji. Można skonfigurować tysiące serwerów (VM) w chmurze w ciągu kilku minut, w porównaniu do tygodni, które zwykle trwa do skonfigurowania serwerów lokalnych.

Nie ma jednej, uniwersalnej strategii migracji aplikacji do chmury. Odpowiednia strategia migracji będzie zależeć od potrzeb i priorytetów organizacji oraz rodzaju migrujących aplikacji. Nie wszystkie aplikacje wymagają inwestycji w przejście na platformę jako modelu usługi[(PaaS)](https://azure.microsoft.com/overview/what-is-paas/)lub opracowanie modelu aplikacji [natywnego dla chmury.](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) W wielu przypadkach można podjąć stopniowe lub stopniowe podejście do inwestowania w przenoszenie zasobów do chmury, w zależności od potrzeb biznesowych.

W przypadku nowoczesnych aplikacji o najlepszej długoterminowej elastyczności i wartości dla organizacji możesz skorzystać z inwestowania w *natywne* architektury aplikacji w chmurze. Jednak dla aplikacji, które są istniejące lub starszych zasobów, kluczem jest poświęcić minimalny czas i pieniądze (bez rearchitecting lub zmiany kodu) podczas przenoszenia ich do chmury, aby osiągnąć znaczące korzyści.

Rysunek 1-1 przedstawia możliwe ścieżki, które można podjąć podczas przenoszenia istniejących aplikacji platformy .NET do chmury w fazach przyrostowych.

 ![Ścieżki modernizacji istniejących aplikacji i usług platformy .NET](./media/image1-1.png)

**Rysunek 1-1**. Ścieżki modernizacji istniejących aplikacji i usług platformy .NET

Każde podejście migracji ma różne korzyści i powody, dla których można go używać. Można wybrać pojedyncze podejście podczas migracji aplikacji do chmury lub wybrać niektóre składniki z wielu podejść. Poszczególne aplikacje nie są ograniczone do pojedynczego podejścia lub stanu dojrzałości. Na przykład wspólne podejście hybrydowe będzie miało pewne składniki lokalne oraz inne składniki w chmurze.

Definicja i krótkie wyjaśnienie dla każdego poziomu dojrzałości aplikacji są następujące:

**Poziom 1:** Aplikacje gotowe do obsługi infrastruktury w chmurze: w tym podejściu do migracji po prostu przeprowadzasz migrację lub ponownie hostujesz bieżące aplikacje lokalne do infrastruktury jako platformy usługi[(IaaS).](https://azure.microsoft.com/overview/what-is-iaas/) Aplikacje mają prawie taką samą kompozycję jak poprzednio, ale teraz można wdrożyć je do maszyn wirtualnych w chmurze.
Ten prosty typ migracji jest zazwyczaj znany w branży jako "Lift & Shift".

**Poziom 2: Aplikacje zoptymalizowane pod kątem chmury:** na tym poziomie i nadal bez ponownego wycięcie lub zmiany kodu znaczące, można uzyskać dodatkowe korzyści z uruchamiania aplikacji w chmurze z nowoczesnych technologii, takich jak kontenery i dodatkowe usługi zarządzane w chmurze. Zwiększasz elastyczność aplikacji, aby szybciej wysyłać, udoskonalając procesy rozwoju przedsiębiorstwa (DevOps). Można to osiągnąć przy użyciu technologii, takich jak kontenery systemu Windows, który jest oparty na aparatu platformy Docker. Kontenery usuwają tarcie spowodowane zależnościami aplikacji podczas wdrażania w wielu etapach. W tym modelu dojrzałości można wdrażać kontenery w usługach IaaS lub PaaS przy użyciu dodatkowych usług zarządzanych w chmurze związanych z bazami danych, pamięci podręcznej jako usługi, monitorowania i ciągłej integracji/ciągłego wdrażania (CI/CD).

Trzeci poziom dojrzałości jest ostatecznym celem w chmurze, ale jest opcjonalny dla wielu aplikacji, a nie głównym celem tego przewodnika:

**Poziom 3: Aplikacje natywne dla chmury:** to podejście do migracji jest zazwyczaj oparte na potrzebach biznesowych i celach modernizujących aplikacje o znaczeniu krytycznym. Na tym poziomie usługi PaaS umożliwiają przenoszenie aplikacji na platformy obliczeniowe PaaS. Implementujesz aplikacje [natywne w chmurze](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) i architekturę mikrousług, aby rozwijać aplikacje z długoterminową elastycznością i skalować do nowych limitów. Ten typ modernizacji zwykle wymaga egoistycznych ekwiomów specjalnie dla chmury. Nowy kod często musi być napisany, zwłaszcza podczas przenoszenia do aplikacji natywnych dla chmury i modeli opartych na mikrousługach. Takie podejście może pomóc uzyskać korzyści, które są trudne do osiągnięcia w środowisku aplikacji monolitycznych i lokalnych.

W tabeli 1-1 opisano główne zalety i powody wyboru każdego podejścia migracji lub modernizacji.

| **Gotowość do infrastruktury chmury** <br /> *Migrowanie metodą „lift-and-shift”* | **Zoptymalizowane pod kątem chmury** <br /> *Modernizacji* | **Natywne chmury** <br /> *Modernizuj, przebudowuj i przepisuj* |
|---|---|---|
| **Docelowy obiekt obliczeniowy aplikacji** |
| Aplikacje wdrożone na maszynach wirtualnych na platformie Azure | Aplikacje monolityczne lub n-warstwowe wdrożone w usłudze Azure App Service, wystąpieniu kontenera platformy Azure (ACI), maszynach wirtualnych z kontenerami lub aks (usługa Azure Kubernetes) | Konteneryzowane mikrousługi w usłudze Azure Kubernetes Service (AKS) i/lub mikrousług bezserwerowych oparte na usłudze Azure Functions. |
| **Miejsce docelowe danych** |
| SQL lub dowolnej relacyjnej bazy danych na maszynie Wirtualnej | Wystąpienie zarządzanej usługi Azure SQL Database lub inna zarządzana baza danych w chmurze. | Bazy danych na podstawie bazy danych na podstawie bazy danych SQL Azure, usługi Azure Cosmos DB lub innej zarządzanej bazy danych w chmurze |
| **Zalety**|
| <li>Bez rearchitectingu, bez nowego kodu <li> Najmniejszy wysiłek w zakresie szybkiej migracji <li> Najmniej wspólny mianownik obsługiwany na platformie Azure <li> Podstawowe gwarancje dostępności <li> Po przejściu do chmury łatwiej jest zmodernizować jeszcze więcej | <li> Brak ponownego wycięcie <li> Minimalne zmiany kodu/konfiguracji <li> Ulepszone wdrażanie i elastyczność DevOps do wydania z powodu kontenerów <li> Zwiększona gęstość i niższe koszty wdrożenia <li> Przenoszenie aplikacji i zależności <li> Elastyczność celów gospodarza: podejścia PaaS lub IaaS | <li> Architekt chmury, można uzyskać najlepsze korzyści z chmury, ale nowy kod jest potrzebny <li> Podejścia natywne dla chmury mikrousług <li> Nowoczesne aplikacje o znaczeniu krytycznym, odporne na chmurę, hiperskalowalne <li> W pełni zarządzane usługi <li> Zoptymalizowane pod kątem skali <li> Zoptymalizowany pod kątem autonomicznej elastyczności przez podsystem <li> Zbudowany na wdrażaniu i DevOps |
| **Wyzwania** |
| <li> Mniejsza wartość chmury, inna niż przesunięcie kosztów operacyjnych lub zamknięcie centrów danych <li> Niewiele jest zarządzane: brak systemu operacyjnego lub oprogramowania pośredniczącego poprawek; mogą korzystać z rozwiązań infrastrukturalnych, takich jak Terraform, Spinnaker lub Puppet | <li> Konteneryzowanie jest dodatkowym krokiem w krzywej uczenia się dla programistów i operacji IT <li> DevOps i CI/CD potoki są zwykle "koniecznością" dla tego podejścia. Jeśli nie są obecnie obecni w kulturze organizacji, może to być dodatkowe wyzwanie| <li> Wymaga rearchitecture dla aplikacji natywnych w chmurze i architektury mikrousług i zwykle wymaga znacznego refaktoryzacji kodu lub przepisywania podczas modernizacji (zwiększony czas i budżet)|
> **Tabela 1-1.** Korzyści i wyzwania związane z modernizacją ścieżek dla istniejących aplikacji i usług .NET

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Kluczowe technologie i architektury według poziomu dojrzałości

Aplikacje .NET Framework początkowo zostały uruchomione z programem .NET Framework w wersji 1.0, który został wydany pod koniec 2001 r. Następnie firmy przeniosły się do nowszych wersji (takich jak 2.0, 3.5 i .NET 4.x). Większość z tych aplikacji działała w systemie Windows Server i Internet Information Server (IIS) i używała relacyjnej bazy danych, takiej jak SQL Server, Oracle, MySQL lub innego RDBMS.

Większość istniejących aplikacji platformy .NET może obecnie opierać się na programie .NET Framework 4.x, a nawet na platformie .NET Framework 3.5 i używać struktur sieci web, takich jak ASP.NET MVC, ASP.NET formularzy sieci Web, ASP.NET interfejsu API sieci Web, programu Windows Communication Foundation (WCF), ASP.NET SignalR i ASP.NET stron sieci Web. Te ustanowione technologie platformy .NET Framework zależą od systemu Windows. Ta zależność jest ważne, aby wziąć pod uwagę, jeśli są po prostu migracji starszych aplikacji i chcesz wprowadzić minimalne zmiany w infrastrukturze aplikacji.

Rysunek 1-2 przedstawia podstawowe technologie i style architektury używane na każdym z trzech poziomów dojrzałości chmury:

![Podstawowe technologie dla każdego poziomu dojrzałości do modernizacji istniejących aplikacji sieci web .NET](./media/image1-2.png)

**Rysunek 1-2.** Podstawowe technologie dla każdego poziomu dojrzałości do modernizacji istniejących aplikacji sieci web .NET

Rysunek 1-2 przedstawia najbardziej typowe scenariusze, ale wiele odmian hybrydowych i mieszanych jest możliwe, jeśli chodzi o architekturę. Na przykład modele dojrzałości dotyczą nie tylko architektury monolityczne w istniejących aplikacjach sieci web, ale także orientacji usługi, N-warstwy i innych odmian stylu architektury. Wyższy nacisk lub procent na jeden lub inny typ architektury i powiązanych technologii określa ogólny poziom dojrzałości aplikacji.

Każdy poziom dojrzałości w procesie modernizacji jest skojarzony z następującymi kluczowymi technologiami i podejściami:

- **Cloud Infrastructure-Ready** (rehost lub podstawowy & zmiany windy): W pierwszym kroku wiele organizacji chce tylko szybko wykonać strategię migracji do chmury. W takim przypadku aplikacje są ponownie hostowane. Większość ponownego hostowania można zautomatyzować przy użyciu [usługi Azure Migrate](https://aka.ms/azuremigrate), usługi, która zapewnia wskazówki, szczegółowe informacje i mechanizmy niezbędne do pomocy w migracji na platformę Azure na podstawie narzędzi w chmurze, takich jak [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) i Usługa migracji bazy danych [Azure.](https://azure.microsoft.com/campaigns/database-migration/) Ponowne hostowanie można również skonfigurować ręcznie, aby podczas przenoszenia starszych aplikacji do chmury dowiedzieć się więcej o infrastrukturze dotyczących zasobów. Na przykład można przenieść aplikacje do maszyn wirtualnych na platformie Azure z niewielkimi modyfikacjami prawdopodobnie tylko niewielkie zmiany konfiguracji. Sieci w tym przypadku jest podobny do środowiska lokalnego, zwłaszcza w przypadku tworzenia sieci wirtualnych na platformie Azure.

- **Zoptymalizowane pod kątem chmury** (usługi zarządzane i kontenery systemu Windows): Ten model polega na tworzeniu kilku ważnych optymalizacji wdrażania w celu uzyskania znaczących korzyści z chmury, bez zmiany podstawowej architektury aplikacji. Podstawowym krokiem w tym miejscu jest dodanie [obsługi kontenerów systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do istniejących aplikacji .NET Framework. Ten ważny krok (konteneryzacja) nie wymaga dotykania kodu, więc ogólny wysiłek podnoszenia i zmiany jest lekki. Za pomocą narzędzi, takich jak [Image2Docker](https://github.com/docker/communitytools-image2docker-win) lub Visual Studio, można używać z jego narzędziami [dok.](https://www.docker.com/) Program Visual Studio automatycznie wybiera inteligentne ustawienia domyślne dla ASP.NET aplikacji i obrazów kontenerów systemu Windows. Te narzędzia oferują zarówno szybką pętlę wewnętrzną, jak i szybką ścieżkę, aby uzyskać kontenery na platformę Azure. Elastyczność jest lepsza podczas wdrażania w wielu środowiskach.
Następnie, przechodząc do środowiska produkcyjnego, można wdrożyć kontenery systemu Windows w [aplikacji Azure Web App dla kontenerów,](https://azure.microsoft.com/services/app-service/containers/)wystąpienia [kontenerów platformy Azure (ACI)](https://azure.microsoft.com/services/container-instances/)i maszyn wirtualnych platformy Azure z systemem Windows Server 2016 i kontenerów, jeśli wolisz podejście IaaS. W przypadku bardziej złożonych aplikacji z wieloma kontenerami należy rozważyć użycie koordynatorów, takich jak [usługa Azure Kubernetes Service (AKS/ACS).](https://azure.microsoft.com/services/container-service/)

Podczas tej wstępnej modernizacji można również dodawać zasoby z chmury, takie jak monitorowanie za pomocą narzędzi, takich jak [usługa Azure Application Insights;](https://docs.microsoft.com/azure/application-insights/app-insights-overview) Potoki ciągłej integracji/ciągłego wdrażania dla cyklu życia aplikacji za pomocą [usług Azure DevOps;](https://azure.microsoft.com/services/devops/) i wiele innych usług zasobów danych, które są dostępne na platformie Azure. Na przykład można zmodyfikować monolityczną aplikację sieci web, która została pierwotnie opracowana przy użyciu tradycyjnych [ASP.NET formularzy sieci Web](https://www.asp.net/web-forms) lub ASP.NET [MVC](https://www.asp.net/mvc), ale teraz można wdrożyć za pomocą kontenerów systemu Windows. Korzystając z kontenerów systemu Windows, należy również migrować dane do bazy danych w [wystąpieniu zarządzanym usługi Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), a wszystko to bez zmiany podstawowej architektury aplikacji.

- **Natywne dla chmury:** Zgodnie z wprowadzeniem należy pomyśleć o projektowaniu aplikacji [natywnych dla chmury,](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) gdy kierujesz reklamy na duże i złożone aplikacje z wieloma niezależnymi zespołami programisty działającymi nad różnymi mikrousługami, które można opracować i wdrożyć autonomicznie. Ponadto ze względu na granulowane i niezależne skalowalności na mikrousługi. Te podejścia architektoniczne stoją przed bardzo ważnymi wyzwaniami i złożoności, ale można znacznie uprościć przy użyciu paaS chmury i orchestrators jak [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (zarządzane Kubernetes) i [usługi Azure Functions](https://azure.microsoft.com/services/functions/) dla podejścia bezserwerowego. Wszystkie te podejścia (takie jak mikrousługi i bezserwerowe) zazwyczaj wymagają architekta dla chmury i napisać nowy kod — kod, który jest dostosowany do określonych platform PaaS lub kodu, który dostosowuje się do określonych architektur, takich jak mikrousługi.

Rysunek 1-3 przedstawia wewnętrzne technologie, których można użyć dla każdego poziomu dojrzałości:

![Technologie wewnętrzne dla każdego poziomu dojrzałości modernizacji](./media/image1-3.png)

**Rysunek 1-3.** Technologie wewnętrzne dla każdego poziomu dojrzałości modernizacji

## <a name="lift-and-shift-scenario"></a>Scenariusz podnoszenia i zmiany

W przypadku migracji windy i zmiany należy pamiętać, że można użyć wielu różnych odmian podnoszenia i zmiany w scenariuszach aplikacji. Jeśli tylko ponownie hostować aplikację, może mieć scenariusz, taki jak pokazano na rysunku 1-4, w którym używane są maszyny wirtualne w chmurze tylko dla aplikacji i serwera bazy danych.

![Przykład czystego scenariusza IaaS w chmurze](./media/image1-4.png)

**Rysunek 1-4**. Przykład czystego scenariusza IaaS w chmurze

## <a name="modernization-scenarios"></a>Scenariusze modernizacji

W przypadku scenariuszy modernizacji może mieć czystą aplikację zoptymalizowaną pod kątem chmury, która używa elementów tylko z tego poziomu dojrzałości. Lub może mieć aplikacji stanu pośredniego z niektórych elementów z cloud infrastructure-ready i innych elementów z cloud-optimized ("wybierz i wybierz" lub model mieszany), jak na rysunku 1-5.

![Przykładowy scenariusz "wybierz i wybierz" z bazą danych w zasobach IaaS, DevOps i konteneryzacji](./media/image1-5.png)

**Rysunek 1-5.** Przykładowy scenariusz "wybierz i wybierz" z bazą danych w zasobach IaaS, DevOps i konteneryzacji

Następnie jako idealny scenariusz dla wielu istniejących aplikacji .NET Framework do migracji, można przeprowadzić migrację do aplikacji zoptymalizowane pod kątem chmury, aby uzyskać znaczne korzyści z niewielkiej pracy. Takie podejście również ustawia dla Cloud-Native jako możliwe przyszłej ewolucji. Rysunek 1-6 przedstawia przykład.

![Przykład scenariusz aplikacji zoptymalizowanych pod kątem chmury z kontenerami systemu Windows i usługami zarządzanymi](./media/image1-6.png)

**Rysunek 1-6.** Przykład scenariusz aplikacji zoptymalizowanych pod kątem chmury z kontenerami systemu Windows i usługami zarządzanymi

Idąc jeszcze dalej, można rozszerzyć istniejącą aplikację zoptymalizowaną pod kątem chmury, dodając kilka mikrousług dla określonych scenariuszy. Spowoduje to przeniesienie częściowo do poziomu modelu cloud-native, który nie jest głównym celem niniejszych wskazówek.

## <a name="what-this-guide-does-not-cover"></a>Co ten przewodnik nie obejmuje

Ten przewodnik obejmuje określony podzbiór przykładowych scenariuszy, jak pokazano na rysunku 1-7. Ten przewodnik koncentruje się tylko na scenariuszach windy i zmiany, a ostatecznie na modelu zoptymalizowanym pod kątem chmury. W modelu zoptymalizowanym pod kątem chmury aplikacja .NET Framework jest modernizowana przy użyciu kontenerów systemu Windows oraz dodatkowych składników, takich jak monitorowanie i potoki ciągłej integracji/ciągłego wdrażania. Każdy składnik ma podstawowe znaczenie dla wdrażania aplikacji w chmurze, szybciej i ze zwinnością.

![Natywne dla chmury nie są opisane w tym przewodniku](./media/image1-7.png)

**Rysunek 1-7.** Natywne dla chmury nie są opisane w tym przewodniku

Ten przewodnik koncentruje się na konkretnym. Pokazuje ścieżkę, którą można podjąć, aby osiągnąć windę i przesunięcie istniejących aplikacji .NET, bez ponownego wycinania i bez zmian kodu. Ostatecznie pokazuje, jak sprawić, by aplikacja zoptymalizowana pod kątem chmury.

W tym przewodniku nie pokazano, jak utworzyć aplikacje natywne dla chmury, takie jak jak rozwijać się do architektury mikrousług. Aby ponownie zmienić aplikacje lub utworzyć zupełnie nowe aplikacje oparte na mikrousługach, zobacz e-book [.NET Microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Konteneryzowany cykl życia aplikacji platformy Docker z platformą i narzędziami firmy Microsoft** (e-book do pobrania) \
  <https://aka.ms/dockerlifecycleebook>

- **.NET Mikrousługi: Architektura konteneryzowanych aplikacji .NET** (e-book do pobrania) \
  <https://aka.ms/microservicesebook>

- **Projektowanie nowoczesnych aplikacji internetowych za pomocą ASP.NET Core i Azure** (e-book do pobrania) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Ten przewodnik został napisany dla deweloperów i architektów rozwiązań, którzy chcą zmodernizować istniejące ASP.NET aplikacji sieci web lub usług WCF, które są oparte na programie .NET Framework, aby zwiększyć elastyczność w zakresie wysyłki i zwalniania aplikacji.

Ten przewodnik może również okazać się przydatny, jeśli jesteś technicznym decydentem, takim jak architekt przedsiębiorstwa lub kierownik/dyrektor dewelopera, który po prostu chce uzyskać przegląd korzyści, które można uzyskać za pomocą kontenerów systemu Windows i wdrażając w chmurze podczas korzystania z platformy Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak korzystać z tego przewodnika

W tym przewodniku opowiedzieć o powodach, dla których warto zmodernizować istniejące aplikacje, oraz o konkretnych korzyściach płynących z używania kontenerów systemu Windows podczas przenoszenia aplikacji do chmury. Zawartość kilku pierwszych rozdziałów przewodnika jest przeznaczona dla architektów i decydentów technicznych, którzy chcą przeglądu, ale którzy nie muszą koncentrować się na implementacji i szczegółach technicznych krok po kroku.

Ostatni rozdział tego przewodnika przedstawia wiele instruktajnie, które koncentrują się na określonych scenariuszach wdrażania. Ten przewodnik oferuje krótsze wersje instruktaży, aby podsumować scenariusze i wyróżnić ich korzyści. Pełne wskazówki przechodzenie do szczegółów konfiguracji i implementacji są publikowane jako zestaw [wpisów wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) w tym samym publicznym [repozytorium GitHub,](https://github.com/dotnet-architecture/eShopModernizing) w którym znajdują się powiązane przykładowe aplikacje (omówione w następnej sekcji). Ostatni rozdział i instruktaże wiki krok po kroku na GitHub będą bardziej interesujące dla deweloperów i architektów, którzy chcą skupić się na szczegółach implementacji.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Przykładowe aplikacje do modernizacji starszych aplikacji: eShopModernizing

[Repozytorium eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) w usłudze GitHub oferuje dwie przykładowe aplikacje, które symulują starsze monolityczne aplikacje sieci web. Jedna aplikacja internetowa jest rozwijana przy użyciu ASP.NET MVC; druga aplikacja internetowa jest rozwijany przy użyciu ASP.NET formularzy sieci Web, a trzecia aplikacja jest N-Warstwa aplikacji z winforms klienckiej aplikacji klasycznej korzystających z wewnętrznej bazy danych usługi WCF. Wszystkie te aplikacje są oparte na tradycyjnych .NET Framework. Te przykładowe aplikacje nie używają .NET Core lub ASP.NET Core, ponieważ mają być istniejące/starsze aplikacje .NET Framework do modernizacji.

Te przykładowe aplikacje mają drugą wersję, z modernizowanym kodem i które są dość proste. Najważniejszą różnicą między wersjami aplikacji jest to, że w drugiej wersji używane są kontenery systemu Windows jako wybór wdrożenia. Istnieje również kilka dodatków do drugiej wersji, takich jak obiekty blob usługi Azure Storage do zarządzania obrazami, usługa Azure Active Directory do zarządzania zabezpieczeniami i usługa Azure Application Insights do monitorowania i inspekcji aplikacji.

## <a name="send-your-feedback"></a>Wyślij swoją opinię

Ten przewodnik został napisany, aby ułatwić zrozumienie opcji ulepszania i modernizacji istniejących aplikacji sieci web .NET. Przewodnik i powiązane przykładowe aplikacje ewoluują. Chętnie poznamy Twoją opinię! Jeśli masz uwagi na temat tego, jak ten [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)przewodnik może być bardziej pomocne, wyślij je do .

>[!div class="step-by-step"]
>[Dalej](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
