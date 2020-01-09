---
title: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows (wersja 2)
description: Dowiedz się, jak Podnieś i przenieść istniejące aplikacje do chmury platformy Azure i kontenerów z tą książką elektroniczną.
ms.date: 04/28/2018
ms.openlocfilehash: fa20e606c9a1364fbdf8c9a58c8703420d9e65a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714569"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows (wersja 2)

![Obraz okładki przewodnika dotyczącego modernizacji aplikacji .NET.](./media/index/web-application-guide-cover-image.png)

OPUBLIKOWANA PRZEZ  
Microsoft Press i Microsoft DevDiv  
Działy firmy Microsoft Corporation  
One Microsoft Way  
Redmond, Waszyngton 98052-6399  

Prawa autorskie © 2018 przez firmę Microsoft Corporation  

Wszelkie prawa zastrzeżone. Żadna część zawartości tej księgi nie może zostać odgotowana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.

Książka ta jest dostępna bezpłatnie w formie książki elektronicznej (książka elektroniczna), która jest dostępna za pośrednictwem wielu kanałów w firmie Microsoft, takich jak <https://dot.net/architecture>.

Jeśli masz pytania związane z tą książką, Wyślij wiadomość e-mail na adres [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora. Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre przedstawione przykłady są fikcyjne i pełnią wyłącznie rolę ilustracyjną. Skojarzenie lub powiązanie z rzeczywistością nie jest zamierzone ani nie powinno być wnioskowane.

Firma Microsoft i znaki towarowe wymienione w <https://www.microsoft.com> na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft. Wszystkie inne znaczniki są własnością odpowiednich właścicieli.

Autor:
> **Cesar de La Torre**, SR. PM, zespół produktu .NET, Microsoft Corp.

Uczestnicy i recenzenci:
> **Scott myśliwy**, dyrektor ds. partnerów, .NET Team, Microsoft  
> **Paul Yuknewicz**, dyrektor ds. firmy PM, zespół Visual Studio Tools, Microsoft  
> **Lisa Guthrie**, SR. PM, Visual Studio Tools zespół, Microsoft  
> **Autor Ankit Asthana**, kierownik ds. platformy PM, zespół .NET, Microsoft  
> **Unai Zorrilla**, lider deweloperów, zwykłe pojęcia  
> **Javier Valero**, dyrektor ds. operacyjnych w Grupo Solutio  

## <a name="introduction"></a>Wprowadzenie

W przypadku podjęcia decyzji o modernizacji aplikacji lub usług sieci Web i przeniesieniu ich do chmury nie trzeba będzie w pełni zmieniać architektury aplikacji. Przetworzenie architektury aplikacji przy użyciu zaawansowanego podejścia, takiego jak mikrousługi, nie zawsze jest opcją z powodu ograniczeń kosztu i czasu. W zależności od typu aplikacji może być również konieczne przeprowadzenie ponownej architektury aplikacji. Aby zoptymalizować efektywność strategii migracji do chmury w organizacji, należy wziąć pod uwagę potrzeby biznesowe i wymagania aplikacji. Należy określić:

- Aplikacje wymagające przekształcenia lub przetworzenia architektury.

- Które aplikacje muszą być tylko częściowo zmodernizowane.

- Aplikacje, które można "Unieś" i przenieść bezpośrednio do chmury.

## <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik koncentruje się głównie na początkowej modernizacji istniejących aplikacji sieci Web lub zorientowanych na usługi Microsoft .NET Framework, co oznacza działania związane z przeniesieniem obciążenia do nowszego lub bardziej nowoczesnego środowiska bez znaczącego zmiany kodu aplikacji i podstawowa architektura.

W tym przewodniku przedstawiono również zalety przechodzenia aplikacji do chmury i częściowej modernizacji aplikacji przy użyciu określonego zestawu nowych technologii i metod, takich jak kontenery systemu Windows i powiązane platformy obliczeniowe na platformie Azure.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Ścieżka do chmury dla istniejących aplikacji .NET

Organizacje zwykle przechodzą na chmurę, aby uzyskać elastyczność i szybkość, którą mogą uzyskać w swoich aplikacjach. Można skonfigurować tysiące serwerów (maszyn wirtualnych) w chmurze w ciągu kilku minut w porównaniu do tygodni, które zwykle są potrzebne do skonfigurowania serwerów lokalnych.

W przypadku migrowania aplikacji do chmury nie ma żadnej jednolitej strategii. Odpowiednia strategia migracji zależy od potrzeb i priorytetów organizacji oraz rodzaju aplikacji, które są migrowane. Nie wszystkie aplikacje uzasadniają inwestycję w model platformy jako usługi ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) lub opracowywanie modelu aplikacji [natywnych dla chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) . W wielu przypadkach można podjąć etapowe lub przyrostowe podejście do inwestowania w przeniesienie zasobów do chmury w zależności od potrzeb firmy.

W przypadku nowoczesnych aplikacji z najlepszą długoterminową elastyczność i korzyścią dla organizacji możesz skorzystać z inwestycji w architekturę aplikacji *natywnych dla chmury* . Jednak w przypadku aplikacji, które są istniejącymi lub starszymi zasobami, klucz ma poświęcać za minimalny czas i pieniądze (bez konieczności zmiany architektury lub zmian w kodzie) podczas przechodzenia do chmury w celu osiągnięcia znaczących korzyści.

Na rysunku 1-1 przedstawiono możliwe ścieżki, które można wykonać po przeniesieniu istniejących aplikacji .NET do chmury w fazach przyrostowych.

 ![Ścieżki modernizacji istniejących aplikacji i usług platformy .NET](./media/image1-1.png)

**Rysunek 1-1**. Ścieżki modernizacji istniejących aplikacji i usług platformy .NET

Każde podejście migracji ma różne zalety i przyczyny jego użycia. Podczas migrowania aplikacji do chmury można wybrać jedno podejście lub wybrać pewne składniki z wielu metod. Pojedyncze aplikacje nie są ograniczone do pojedynczego podejścia lub stanu ważności. Na przykład wspólne podejście hybrydowe będzie obejmować pewne składniki lokalne oraz inne składniki w chmurze.

Definicja i krótkie wyjaśnienie poszczególnych poziomów dojrzałości aplikacji są następujące:

**Poziom 1: aplikacje gotowe do infrastruktury chmurowej** : w ramach tego podejścia migracji można po prostu migrować lub przehostować bieżące aplikacje lokalne do platformy infrastruktury jako usługi ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)). Aplikacje mają prawie tę samą kompozycję co poprzednio, ale teraz wdrażamy je na maszynach wirtualnych w chmurze.
Ten prosty typ migracji jest zwykle znany w branży jako "dźwig & Shift".

**Poziom 2: aplikacje zoptymalizowane pod kątem chmury** : na tym poziomie i nadal bez konieczności ponownego tworzenia architektury lub zmiany istotnego kodu możesz uzyskać dodatkowe korzyści z używania aplikacji w chmurze przy użyciu nowoczesnych technologii, takich jak kontenery i dodatkowe usługi zarządzane przez chmurę. Zwiększasz elastyczność aplikacji, aby szybciej dostarczać je przez udoskonalenie procesów operacji tworzenia przedsiębiorstw (DevOps). Można to osiągnąć za pomocą technologii, takich jak kontenery systemu Windows, opartych na aparacie platformy Docker. Kontenery usuwają tarcie spowodowane przez zależności aplikacji podczas wdrażania w wielu etapach. W tym modelu zapadalności można wdrożyć kontenery na IaaS lub PaaS przy użyciu dodatkowych usług zarządzanych w chmurze związanych z bazami danych, pamięci podręcznej jako usługi, monitorowania i ciągłej integracji/ciągłego wdrażania (CI/CD).

Trzeci poziom dojrzałości jest ostatecznym celem w chmurze, ale jest on opcjonalny w przypadku wielu aplikacji, a nie głównego punktu skupienia tego przewodnika:

**Poziom 3: aplikacje natywne w chmurze** : takie podejście migracji zwykle jest zależne od potrzeb firmy i celów modernizacji aplikacji o znaczeniu krytycznym. Na tym poziomie używasz usług PaaS Services do przenoszenia aplikacji na platformę obliczeniową PaaS. Wdrażaj aplikacje [natywne w chmurze](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) i architekturę mikrousług, aby rozwijać aplikacje z długoterminową elastyczność i skalować je do nowych limitów. Ten typ modernizacji zwykle wymaga projektowania zaprojektowanego dla chmury. Często należy napisać nowy kod, szczególnie podczas przenoszenia do modeli aplikacji i mikrousług opartych na chmurze. Takie podejście może pomóc w uzyskaniu korzyści, które są trudne do osiągnięcia w lokalnym i lokalnym środowisku aplikacji.

W tabeli 1-1 opisano główne zalety i przyczyny wyboru każdej metody migracji lub modernizacji.

| **Infrastruktura chmury — gotowe** <br /> *Unieś i Przenieś* | **Zoptymalizowane pod kątem chmury** <br /> *Modernizowanie* | **Cloud-Native** <br /> *Modernizacja, ponowne tworzenie architektury i ponowne zapisywanie* |
|---|---|---|
| **Obiekt docelowy obliczeń aplikacji** |
| Aplikacje wdrożone na maszynach wirtualnych na platformie Azure | Aplikacje monolityczne lub N-warstwowe wdrożone w celu Azure App Service, Azure Container Instance (ACI), maszyn wirtualnych z kontenerami lub AKS (usługa Azure Kubernetes Service) | Mikrousługi z kontenerami w usłudze Azure Kubernetes Service (AKS) i/lub mikrousługi bezserwerowe oparte na Azure Functions. |
| **Obiekt docelowy danych** |
| SQL lub dowolna relacyjna baza danych na maszynie wirtualnej | Azure SQL Database wystąpienie zarządzane lub inną zarządzaną bazę danych w chmurze. | Drobnoziarniste bazy danych na mikrousługi w oparciu o Azure SQL Database, Azure Cosmos DB lub inną zarządzaną bazę danych w chmurze |
| **Zalety**|
| <li>Bez ponownej architektury, brak nowego kodu <li> Najmniej wysiłku do szybkiej migracji <li> Najmniejszy typowy mianownik obsługiwany na platformie Azure <li> Podstawowe gwarancje dostępności <li> Po przejściu do chmury można łatwiej przeprowadzić modernizację jeszcze więcej | <li> Bez ponownej architektury <li> Minimalne zmiany kodu/konfiguracji <li> Udoskonalone wdrożenie i elastyczność DevOps do wydania ze względu na kontenery <li> Zwiększona gęstość i niższe koszty wdrożenia <li> Przenośność aplikacji i zależności <li> Elastyczność obiektów docelowych hosta: podejścia PaaS lub IaaS | <li> Architekt chmury pozwala uzyskać najlepsze korzyści z chmury, ale jest wymagany nowy kod <li> Obsługa mikrousług w chmurze — podejścia natywne <li> Nowoczesne aplikacje o znaczeniu strategicznym, odporne na błędy w chmurze — skalowalne <li> W pełni zarządzane usługi <li> Zoptymalizowane pod kątem skalowania <li> Optymalizacja pod kątem elastyczności w podsystemie <li> Kompilacja oparta na wdrożeniu i DevOps |
| **Wyzwania** |
| <li> Mniejsza wartość w chmurze, inna niż przesunięcia w ramach kosztów operacyjnych lub zamykania centrów danych <li> Niewielki jest zarządzany: brak stosowania poprawek systemu operacyjnego lub oprogramowania pośredniczącego; może korzystać z rozwiązań infrastruktury, takich jak Terraform, Spinnaker lub Puppet | <li> Konteneryzowania to dodatkowy krok krzywej uczenia dla deweloperów i operacji IT <li> Potoki DevOps i ciągłej integracji/ciągłego wdrażania są zwykle "a". Jeśli obecnie nie ma w kulturze organizacji, może to być dodatkowe wyzwanie| <li> Wymaga ponownej architektury dla natywnych aplikacji w chmurze i architektury mikrousług, a zazwyczaj wymaga znacznego refaktoryzacji kodu lub ponownego zapisu podczas modernizacji (zwiększony czas i budżet)|
> **Tabela 1-1.** Zalety i wyzwania związane z modernizacją ścieżek dla istniejących aplikacji i usług .NET

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Najważniejsze technologie i architektury według poziomu dojrzałości

.NET Framework aplikacje początkowo uruchamiane z .NET Framework wersji 1,0, która została wydana w późnej 2001. Następnie firmy przeniesiono do nowszej wersji (np. 2,0, 3,5 i .NET 4. x). Większość z tych aplikacji działa w systemach Windows Server i Internet Information Server (IIS) oraz korzysta z relacyjnej bazy danych, takiej jak SQL Server, Oracle, MySQL lub inne RDBMS.

Większość istniejących aplikacji .NET może obecnie być oparta na .NET Framework 4. x, a nawet na .NET Framework 3,5 i używać platform sieci Web, takich jak ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, Windows Communication Foundation (WCF), ASP.NET sygnalizujący i ASP.NET Web Pages . Te ustanowione .NET Framework technologie zależą od systemu Windows. Ta zależność jest ważna, jeśli po prostu migrujesz starsze aplikacje i chcesz wprowadzić minimalne zmiany infrastruktury aplikacji.

Na rysunku 1-2 przedstawiono podstawowe technologie i style architektury używane na każdym z trzech poziomów dojrzałości w chmurze:

![Podstawowe technologie dla każdego poziomu zapadalności dla modernizacji istniejących aplikacji sieci Web platformy .NET](./media/image1-2.png)

**Rysunek 1-2.** Podstawowe technologie dla każdego poziomu zapadalności dla modernizacji istniejących aplikacji sieci Web platformy .NET

Rysunek 1-2 wyróżnia najpopularniejsze scenariusze, ale wiele hybrydowych i mieszanych odmian jest możliwe, gdy chodzi o architekturę. Na przykład modele zapadalności dotyczą nie tylko wbudowanych architektur w istniejących aplikacjach sieci Web, ale również do orientacji usługi, warstwy N-warstwowej i innych odmian stylu architektury. Wyższy fokus lub wartość procentowa dla jednego lub innego typu architektury i powiązanych technologii określają ogólny poziom ważności aplikacji.

Każdy poziom dojrzałości w procesie modernizacji jest skojarzony z następującymi najważniejszymi technologiami i podejść:

- **Infrastruktura chmury — gotowe** (rehostowanie lub podstawowe dźwigi & Shift): w pierwszym kroku wiele organizacji chce tylko szybko wykonać strategię migracji w chmurze. W takim przypadku aplikacje są przeszukane. Większość operacji hostowania można zautomatyzować za pomocą [Azure Migrate](https://aka.ms/azuremigrate), usługi, która zapewnia wskazówki, szczegółowe informacje i mechanizmy potrzebne do przeprowadzenia migracji do platformy Azure w oparciu o narzędzia chmurowe, takie jak [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) i [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/). Możesz również skonfigurować Ręczne Hostowanie, aby poznać szczegóły infrastruktury dotyczące zasobów w przypadku przenoszenia starszych aplikacji do chmury. Na przykład możesz przenieść aplikacje do maszyn wirtualnych na platformie Azure z małą modyfikacją — prawdopodobnie z uwzględnieniem tylko drobnych zmian konfiguracji. Sieć w tym przypadku jest podobna do środowiska lokalnego, szczególnie jeśli tworzysz sieci wirtualne na platformie Azure.

- **Zoptymalizowane pod kątem chmury** (usługi zarządzane i kontenery systemu Windows): ten model polega na zapewnieniu kilku ważnych optymalizacji wdrożenia w celu uzyskania znaczących korzyści z chmury bez konieczności zmiany podstawowej architektury aplikacji. Podstawowym krokiem jest dodanie obsługi [kontenerów systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do istniejących aplikacji .NET Framework. Ten ważny krok (kontenerach) nie wymaga dotknięcia kodu, więc jest jasne, że zostanie wysunięty ogólny skok i przesunięcia. Za pomocą narzędzi [platformy Docker](https://www.docker.com/)można używać narzędzi takich jak [Image2Docker](https://github.com/docker/communitytools-image2docker-win) lub Visual Studio. Program Visual Studio automatycznie wybiera inteligentne wartości domyślne dla aplikacji ASP.NET i obrazów kontenerów systemu Windows. Narzędzia te oferują zarówno szybką pętlę wewnętrzną, jak i szybką ścieżkę do uzyskiwania kontenerów na platformę Azure. Zwiększona elastyczność w przypadku wdrażania w wielu środowiskach.
Następnie przejście do środowiska produkcyjnego pozwala wdrożyć kontenery systemu Windows na [platformie azure Web App for Containers](https://azure.microsoft.com/services/app-service/containers/), [Azure Container Instances (ACI)](https://azure.microsoft.com/services/container-instances/)i maszyn wirtualnych platformy Azure z systemem Windows Server 2016 i kontenerami, jeśli wolisz podejście IaaS. W przypadku bardziej złożonych aplikacji z wieloma kontenerami Rozważ użycie programu Orchestrator, takiego jak [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/).

Podczas tej początkowej modernizacji można także dodawać zasoby z chmury, takie jak monitorowanie za pomocą narzędzi takich jak [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); Potoki ciągłej integracji/ciągłego wdrażania dla cyklu życia aplikacji z [Azure DevOps Services](https://azure.microsoft.com/services/devops/); i wiele dodatkowych usług zasobów danych, które są dostępne na platformie Azure. Na przykład można zmodyfikować monolityczną aplikację sieci Web, która została pierwotnie opracowana przy użyciu tradycyjnych [ASP.NET Web Forms](https://www.asp.net/web-forms) lub [ASP.NET MVC](https://www.asp.net/mvc), ale teraz można ją wdrożyć za pomocą kontenerów systemu Windows. W przypadku korzystania z kontenerów systemu Windows należy również migrować dane do bazy danych w [Azure SQL Database wystąpieniu zarządzanym](https://docs.microsoft.com/azure/sql-database/), bez konieczności zmiany podstawowej architektury aplikacji.

- **Natywne w chmurze**: jak zostało to wprowadzone, należy wziąć pod uwagę projektowanie aplikacji [natywnych w chmurze](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) , jeśli są przeznaczone dla dużych i złożonych aplikacji z wieloma niezależnymi zespołami programistycznymi pracującymi nad różnymi mikrousługami, które można opracować i wdrożyć autonomicznie. Ponadto ze względu na granulowaną i niezależną skalowalność na mikrousługach. Takie podejście podejścia do tych rozwiązań ma bardzo ważne wyzwania i złożoność, ale można je znacznie uprościć, korzystając z usług Cloud PaaS i Orchestrator, takich jak [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (zarządzane Kubernetes) i [Azure Functions](https://azure.microsoft.com/services/functions/) w przypadku podejścia bezserwerowego. Wszystkie te podejścia (takie jak mikrousługi i bezserwerowe) wymagają zazwyczaj architektów w chmurze i zapisują nowy kod — kod dostosowany do określonych platform PaaS lub kod, który jest wyrównany do określonych architektur, takich jak mikrousługi.

Rysunek 1-3 pokazuje wewnętrzne technologie, których można użyć dla każdego poziomu dojrzałości:

![Wewnętrzne technologie dla każdego poziomu dojrzałości modernizacji](./media/image1-3.png)

**Rysunek 1-3.** Wewnętrzne technologie dla każdego poziomu dojrzałości modernizacji

## <a name="lift-and-shift-scenario"></a>Scenariusz podnoszenia i przesunięcia

W celu przeprowadzenia migracji i przesunięcia należy pamiętać, że można użyć wielu różnych kombinacji klawiszy podnoszenia i przesunięcia w scenariuszach aplikacji. W przypadku przeszukania tylko aplikacji możesz użyć scenariusza, takiego jak przedstawiony na rysunku 1-4, gdzie są używane maszyny wirtualne w chmurze tylko dla aplikacji i serwera bazy danych.

![Przykład czystego scenariusza IaaS w chmurze](./media/image1-4.png)

**Rysunek 1-4**. Przykład czystego scenariusza IaaS w chmurze

## <a name="modernization-scenarios"></a>Scenariusze modernizacji

W przypadku scenariuszy modernizacji może istnieć czysta Aplikacja zoptymalizowana pod kątem chmury, która używa elementów tylko z tego poziomu. Możesz też mieć aplikację o stanie pośrednią z niektórymi elementami z infrastruktury chmurowej — gotowe i inne elementy z poziomu chmury ("Wybieranie i wybieranie" lub model mieszany), jak na rysunku 1-5.

![Przykład scenariusza "Wybieranie i wybieranie" z bazą danych w zasobach IaaS, DevOps i kontenerach](./media/image1-5.png)

**Rysunek 1-5.** Przykład scenariusza "Wybieranie i wybieranie" z bazą danych w zasobach IaaS, DevOps i kontenerach

Następnie, jako idealny scenariusz dla wielu istniejących aplikacji .NET Framework do migracji, można przeprowadzić migrację do aplikacji zoptymalizowanej pod kątem chmury, aby uzyskać znaczne korzyści z małego nakładu pracy. Takie podejście umożliwia również skonfigurowanie natywnej chmury jako możliwej do przyszłej ewolucji. Na rysunku 1-6 przedstawiono przykład.

![Przykładowy scenariusz aplikacji zoptymalizowanych pod kątem chmury, z kontenerami systemu Windows i usługami zarządzanymi](./media/image1-6.png)

**Rysunek 1-6.** Przykładowy scenariusz aplikacji zoptymalizowanych pod kątem chmury, z kontenerami systemu Windows i usługami zarządzanymi

Jeszcze więcej, możesz rozszerzyć istniejącą aplikację zoptymalizowaną pod kątem chmury, dodając kilka mikrousług dla konkretnych scenariuszy. Spowoduje to przełączenie go częściowo do poziomu modelu natywnego w chmurze, który nie jest głównym fokusem niniejszych wskazówek.

## <a name="what-this-guide-does-not-cover"></a>Czym nie obejmuje ten przewodnik

Ten przewodnik obejmuje określony podzestaw przykładowych scenariuszy, jak pokazano na rysunku 1-7. Ten przewodnik koncentruje się tylko na scenariuszach podnoszenia i przesunięcia, a ostatecznie w modelu zoptymalizowanym pod kątem chmury. W modelu zoptymalizowanym pod kątem chmury aplikacja .NET Framework jest nowoczesny przy użyciu kontenerów systemu Windows oraz dodatkowych składników, takich jak monitorowanie i potoki ciągłej integracji/ciągłego wdrażania. Każdy składnik ma podstawowe znaczenie dla wdrażania aplikacji w chmurze, szybszej i elastyczności.

![Chmura w chmurze nie została omówiona w tym przewodniku](./media/image1-7.png)

**Rysunek 1-7.** Chmura w chmurze nie została omówiona w tym przewodniku

Fokus tego przewodnika jest określony. Pokazuje ścieżkę, którą można wykonać w celu osiągnięcia przełączenia i przesunięcia istniejących aplikacji .NET, bez konieczności ich tworzenia i wprowadzania zmian w kodzie. W końcu przedstawiono sposób, w jaki aplikacja jest zoptymalizowana pod kątem chmury.

Ten przewodnik nie pokazuje, jak tworzyć aplikacje natywne w chmurze, takie jak sposób ewolucji do architektury mikrousług. Aby przetworzyć platformę aplikacji lub utworzyć nowe aplikacje, które są oparte na mikrousługach, zapoznaj się z tematem obsługa mikrousług w sieci e-Book [: architektura dla kontenerów aplikacji .NET](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Cykl życia aplikacji platformy Docker w kontenerze z platformą i narzędziami firmy Microsoft (do** pobrania książek elektronicznych) \
  <https://aka.ms/dockerlifecycleebook>

- **Mikrousługi platformy .NET: architektura dla kontenerów aplikacji .NET (do** pobrania — książka elektroniczna) \
  <https://aka.ms/microservicesebook>

- Tworzenie **architektury nowoczesnych aplikacji sieci Web przy użyciu ASP.NET Core i platformy Azure** (do pobrania książki elektronicznej) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Ten przewodnik został utworzony dla deweloperów i architektów rozwiązań, którzy chcą przeprowadzić modernizację istniejących aplikacji sieci Web ASP.NET lub usług WCF, które są oparte na .NET Framework, aby zwiększyć elastyczność dostarczania i zwalniania aplikacji.

Ten przewodnik może być również przydatny, jeśli jesteś specjalistą ds. decyzji technicznej, na przykład z architektem przedsiębiorstwa lub liderem deweloperskim/dyrektorem, który tylko chce zapoznać się z korzyściami, które można uzyskać przy użyciu kontenerów systemu Windows, i wdrażać je w chmurze przy użyciu Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak korzystać z tego przewodnika

Ten przewodnik dotyczy "przyczyny" — Dlaczego warto przeprowadzić modernizację istniejących aplikacji oraz konkretne korzyści wynikające z korzystania z kontenerów systemu Windows podczas przenoszenia aplikacji do chmury. Zawartość z kilku pierwszych rozdziałów przewodnika jest przeznaczona dla architektów i osób podejmujących decyzje techniczne, którzy chcą zapoznać się z omówieniem, ale którzy nie muszą skupić się na implementacji i technicznych krokach krok po kroku.

W ostatnim rozdziale tego przewodnika wprowadzono wiele przewodników, które koncentrują się na konkretnych scenariuszach wdrażania. Ten przewodnik oferuje krótsze wersje przewodników, aby podsumować scenariusze i wyróżnić ich korzyści. Pełne instruktaże przechodzenia do szczegółów konfiguracji i implementacji oraz są publikowane jako zbiór [wpisów typu wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) w tym samym publicznym [repozytorium GitHub](https://github.com/dotnet-architecture/eShopModernizing) , w którym znajdują się powiązane przykładowe aplikacje (omówione w następnej sekcji). Ostatni rozdział i instrukcje krok po kroku w witrynie GitHub będą bardziej interesujące dla deweloperów i architektów, którzy chcą skupić się na szczegółach wdrożenia.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Przykładowe aplikacje do modernizacji starszych aplikacji: eShopModernizing

Repozytorium [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) w usłudze GitHub oferuje dwie przykładowe aplikacje, które symulują starsze aplikacje monolityczne sieci Web. Jedna aplikacja sieci Web jest opracowywana przy użyciu ASP.NET MVC; Druga aplikacja internetowa jest opracowywana przy użyciu formularzy sieci Web ASP.NET, a trzecia — aplikacji N-warstwowej, która korzysta z aplikacji klasycznej usługi WCF. Wszystkie te aplikacje są oparte na tradycyjnych .NET Frameworkach. Te przykładowe aplikacje nie korzystają z platformy .NET Core ani ASP.NET Core, ponieważ mają być nowoczesne/starsze aplikacje .NET Framework do zmodernizowania.

Te przykładowe aplikacje mają drugą wersję, z nowoczesnym kodem i które są dość proste. Najważniejszymi różnicami między wersjami aplikacji jest użycie kontenerów systemu Windows jako wyboru wdrożenia. Istnieje również kilka dodatków do drugiej wersji, takich jak obiekty blob usługi Azure Storage do zarządzania obrazami, Azure Active Directory zarządzania zabezpieczeniami i Application Insights platformy Azure do monitorowania i przeprowadzania inspekcji aplikacji.

## <a name="send-your-feedback"></a>Wyślij opinię

Ten przewodnik został zapisany, aby ułatwić zrozumienie opcji ulepszania i modernizacji istniejących aplikacji sieci Web platformy .NET. Przewodnik i powiązane przykładowe aplikacje są rozwijane. Chętnie poznamy Twoją opinię! Jeśli masz komentarze dotyczące tego, jak ten przewodnik może być bardziej przydatny, wyślij je do [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
>[Next](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
