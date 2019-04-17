---
title: Modernizacja istniejących .NET aplikacje z chmury platformy Azure i kontenerów Windows (wersja 2)
description: Dowiedz się, przenoszenie i shift i modernizacji istniejących aplikacji do chmury platformy Azure i kontenerów za pomocą tej książce elektronicznej.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 7e56238e129cadd128240d51f03a5926e6de3e6b
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613099"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów Windows (wersja 2)

![Obejmuje obraz modernizowanie .NET — Przewodnik aplikacji.](./media/index/web-application-guide-cover-image.png)

OPUBLIKOWANE PRZEZ  
Microsoft Press i DevDiv firmy Microsoft  
Działy firmy Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2018 Microsoft Corporation  

Wszelkie prawa zastrzeżone. Nie części zawartości tej książki może odtworzyć w jakiejkolwiek formie lub za pomocą jakichkolwiek środków bez pisemnej zgody wydawcy.

Ten podręcznik jest dostępna bezpłatnie w formie elektronicznej book (książka) dostępnych za pośrednictwem wielu kanałów w firmie Microsoft takie jak <https://dot.net/architecture>.

Jeśli masz pytania dotyczące tej książki, adresem e-mail [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Ten podręcznik jest dostarczany "jako — jest" i wyraża, widoki i opinie od autora. Widoki, opinie i informacje wyrażone w tym podręczniku, w tym adresy URL i inne odnośniki do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre przedstawione przykłady znajdują się wyłącznie do celów informacyjnych i są fikcyjne. Nie rzeczywiste skojarzenia ani powiązania nie są zamierzone ani powinny być zakładane.

Firma Microsoft i znaków towarowych, opisane w temacie <https://www.microsoft.com> na stronie sieci Web "Znakami" są znakami towarowymi grupy firm Microsoft. Wszelkie inne znaki są własnością ich prawnych właścicieli.

Autor:
> **Torre'a de la Cesarowi**, starszy PM, .NET produktu zespołu, Microsoft Corp.

Uczestnicy i osób dokonujących przeglądu:
> **Scott Hunter**, Dyrektor ds. partnerów PM, zespołem platformy .NET, Microsoft  
> **Paulem Yuknewiczem**, główny menedżer PM, Visual Studio Tools zespołu firmy Microsoft  
> **Lisa Guthrie**, starszy PM, Visual Studio Tools zespołu firmy Microsoft  
> **Ankit Asthana**, główny menedżer PM, zespołem platformy .NET, Microsoft  
> **Unai Zorrilla**, potencjalnych klientów dla deweloperów, Plain Concepts  
> **Javier Valero**, Dyrektor operacyjny ds. na rozwiązanie Grupo  

## <a name="introduction"></a>Wprowadzenie

Jeśli zdecydujesz się modernizowanie aplikacji sieci web oraz usług i przenieść je do chmury, niekoniecznie nie trzeba pełni Przekształcanie aplikacji. Transformować aplikacji przy użyciu metody zaawansowanych, takich jak mikrousługi nie zawsze jest opcjonalnym ze względu na ograniczenia kosztów i czasu. W zależności od typu aplikacji transformować aplikacji również może nie być konieczne. W celu zoptymalizowania efektywność kosztową strategia migracji do chmury w organizacji, należy wziąć pod uwagę wymagania firmy i wymagań aplikacji. Należy określić:

- Aplikacje, które wymagają transformacji lub transformować.

- Aplikacje, które muszą zostać tylko częściowo zmodernizowane.

- Aplikacje, które użytkownik może metodą "lift and shift" bezpośrednio do chmury.

## <a name="about-this-guide"></a>Przewodnik — informacje

Ten przewodnik koncentruje się głównie na początkowej modernizacji istniejących Microsoft .NET Framework w sieci web lub aplikacji usługowych, co oznacza akcję przenoszenie obciążenia do nowszego lub nowocześniejszego środowiska bez znacznie modyfikacji kodu aplikacji ani podstawowej architektury. 

Ten przewodnik prezentuje również korzyści z przeniesieniem aplikacji do chmury i częściowo modernizowanie aplikacji za pomocą określonego zestawu nowych technologii i metod, takich jak Windows kontenery i powiązane platform obliczeniowych na platformie Azure, obsługę kontenerów Windows.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Drogą do chmury istniejących aplikacji .NET

Organizacje zazwyczaj możliwość przeniesienia do chmury, elastyczność i szybkość, z którego będą oni mogli uzyskać dla poszczególnych aplikacji. Możesz skonfigurować tysięcy serwerów (VM) w chmurze w ciągu kilku minut, w porównaniu do tygodni, jaki zajmuje zwykle do konfigurowania serwerów lokalnych.

Nie ma jednego, opracowanie strategii migracji do chmury. Strategię migracji odpowiednie będzie zależeć od potrzeb organizacji i priorytety i rodzaju aplikacji, które są migrowane. Nie wszystkie aplikacje oświadcza inwestycji przechodzenia do platformy jako usługi ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) modelu lub tworzenia [natywnych dla chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) modelu aplikacji. W wielu przypadkach możesz korzystać z podejścia etapowego, czy przyrostowe inwestować podczas przenoszenia zasobów w chmurze, w zależności od potrzeb biznesowych.

Dla nowoczesnych aplikacji za pomocą najlepsze długoterminowe elastyczność i wartość dla organizacji, mogą skorzystać z inwestowanie w *natywnych dla chmury* architektury aplikacji. Jednak dla aplikacji, które są istniejące lub starsze zasoby klucz jest poświęcić minimalny czas i pieniądze (Brak transformować lub kod zmian) podczas przenoszenia ich do chmury w celu osiągnięcia znaczne korzyści.

Rysunek 1-1 przedstawiono możliwe ścieżki, które można wykonać po przeniesieniu istniejące aplikacje .NET do chmury w fazach przyrostowe.

 ![Ścieżki modernizacji istniejących aplikacji .NET i usługi](./media/image1-1.png)

> **Rysunek 1-1**. Ścieżki modernizacji istniejących aplikacji .NET i usługi

Każde podejście migracji ma różne korzyści i przyczyny, dotyczące korzystania z niego. Można wybrać pojedynczy podejścia, gdy migracja aplikacji do chmury, lub wybierz niektóre składniki z wielu metod. Poszczególne aplikacje nie są ograniczone do pojedynczego stanu podejście lub dojrzałości. Na przykład wspólne podejście hybrydowe musiałby pewne składniki w środowisku lokalnym, a także inne składniki w chmurze.

Definicja i krótki opis dla każdego poziomu dojrzałości aplikacji są następujące:

**Poziom 1: Gotowa do użycia w infrastrukturze w chmurze** aplikacji: To podejście do migracji, należy po prostu migracji lub ponowne hostowanie istniejących aplikacji lokalnych do infrastruktury jako usługi ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) platformy. Twoje aplikacje mają prawie skład taki sam jak przed, ale teraz wdrożyć do maszyn wirtualnych w chmurze.
Ten prosty typ migracji zwykle jest znany w branży "Lift & Shift".

**Poziom 2: Optymalizacja pod kątem chmury** aplikacji: Na tym poziomie i nadal bez transformować lub zmienianie kodu znaczące możesz uzyskać dodatkowe korzyści z uruchamiania aplikacji w chmurze przy użyciu nowoczesnych technologii, takich jak kontenery i dodatkowe usługi zarządzane w chmurze. Możesz zwiększyć elastyczność aplikacjom szybsze dostarczanie przez doprecyzowanie procesy operacji (DevOps) rozwoju przedsiębiorstwa. Można to osiągnąć przy użyciu technologii, takich jak kontenery Windows, która jest oparta na aparacie Docker. Kontenery Usuń zajmowania się powodowane przez zależności aplikacji, w przypadku wdrażania w wielu etapach. W tym modelu dojrzałości można wdrażać kontenery w usłudze IaaS lub PaaS podczas korzystania z dodatkowych usług zarządzanych w chmurze związane z bazy danych w pamięci podręcznej jako usługi, monitorowania i ciągłej integracji/ciągłego wdrażania potoków (CI/CD).

Trzeci poziom dojrzałości jest ostatecznym celem w chmurze, ale jest opcjonalny w przypadku wielu aplikacji i nie głównym celem tego przewodnika:

**Poziom 3: Natywnych dla chmury** aplikacji: To podejście do migracji jest zazwyczaj prowadzona przez potrzeb biznesowych i elementy docelowe modernizujesz swoje aplikacje o znaczeniu krytycznym. Na tym poziomie umożliwia usług PaaS przenieść swoje aplikacje do platformy PaaS. Możesz wdrożyć [natywnych dla chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) architektury mikrousług i aplikacji, rozwój aplikacji z elastycznością długoterminowego i skalowanie do nowych limitów. Tego rodzaju modernizacji wymaga zazwyczaj projektowanie specjalnie dla chmury. Nowy kod często muszą być napisane, szczególnie w przypadku, gdy zostanie przeniesione do aplikacji natywnych dla chmury i modeli opartych na mikrousługach. Takie podejście może pomóc w także umożliwia czerpanie korzyści, które są trudne do osiągnięcia w środowisku aplikacji monolitycznych i lokalnych.

Tabela 1-1 w tym artykule opisano najważniejsze zalety i wybór każde podejście migracji lub modernizacji.

| **Obsługa infrastruktury chmury** <br /> *Lift- and -shift* | **Cloud-Optimized** <br /> *Modernizuj* | **Cloud-Native** <br /> *Modernizacja, przekształcanie i ponowne zapisywanie adresów* |
|---|---|---|
| **Aplikacji obliczeniowych elementów docelowych** |
| Aplikacje wdrożone maszyny wirtualne na platformie Azure | Monolityczne lub aplikacji N-warstwowych wdrożone maszyny wirtualne i wystąpienia kontenera platformy Azure (ACI) oraz usługi Azure App Service za pomocą kontenerów, usługi Azure Service Fabric lub AKS (usługi Azure Kubernetes Service) | Konteneryzowane mikrousługi w usłudze Azure Kubernetes Service (AKS), Usługa Service Fabric i/lub mikrousług bezserwerowe, oparte na usłudze Azure Functions. |
| **Obiekt docelowy danych** |
| SQL lub dowolnym relacyjnej bazy danych na maszynie Wirtualnej | Wystąpienie usługi Azure SQL Database Managed lub innej bazy danych zarządzanej w chmurze. | Ziarna karę baz danych, na mikrousługach, na podstawie usługi Azure SQL Database, Azure Cosmos DB lub innej bazy danych zarządzanej w chmurze |
| **Zalety**|
| <li>Nie transformować żadnego nowego kodu <li> Co najmniej nakładu pracy dla szybkiej migracji <li> Najmniej uniwersalność w obsługiwane na platformie Azure <li> Gwarancje dostępności podstawowe <li> Po przeniesieniu do chmury, łatwiej jest je modernizowanie nawet więcej | <li> Nie transformować <li> Zmiany w minimalnym kodu/konfiguracji <li> Ulepszone wdrażanie i elastyczność DevOps do zwolnienia z powodu kontenerów <li> Zwiększona gęstość i niższe koszty wdrożenia <li> Przenośność aplikacji i zależności <li> Elastyczność cele hosta: Metody PaaS lub IaaS | <li> Architekt chmury, otrzymasz najlepszych korzyści z chmury, ale nowy kod jest wymagany <li> Metod natywnych dla chmury Mikrousług <li> Nowoczesne aplikacje o znaczeniu krytycznym, odporne na błędy dla chmury doskonale skalowalnej <li> W pełni zarządzane usługi <li> Zoptymalizowane pod kątem skalowania <li> Zoptymalizowane pod kątem elastyczności autonomicznego przez podsystem <li> Oparta na wdrożenia i metodyki DevOps |
| **Challenges** |
| <li> Mniejszą wartość chmury, innego niż przesunięcie kosztów operacyjnych lub zamyka centrów danych <li> Odbywa się trochę: Bez systemu operacyjnego i stosowanie poprawek oprogramowania pośredniczącego; może używać rozwiązań infrastruktury, takich jak narzędzia Terraform, Spinnaker lub Puppet | <li> Konteneryzowania jest dodatkowy krok w krzywą uczenia się dla deweloperów i operacji IT <li> Potoki metodyki DevOps i ciągłej integracji/ciągłego Dostarczania jest zazwyczaj "musisz" dla tej metody. Jeśli nie jest aktualnie obecna w kulturze organizacji, może być dodatkowym wyzwaniem| <li> Wymaga rearchitecture dla natywnych aplikacji w chmurze i architektur mikrousług i zazwyczaj wymaga znaczących kodu zdebugować podczas modernizacji lub refaktoryzacji (dłuższego czasu i budżetu) <li> Potoki metodyki DevOps i ciągłej integracji/ciągłego Dostarczania jest zazwyczaj "musisz" dla tej metody. Jeśli nie jest aktualnie obecna w kulturze organizacji, może być dodatkowym wyzwaniem|
> **Tabela 1-1.** Korzyści i problemy ścieżki modernizacji istniejących aplikacji .NET i usługi

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Kluczowe technologie i architektur według poziomu dojrzałości

Aplikacje programu .NET framework jest początkowo pracę z usługą .NET Framework w wersji 1.0, która została wydana w 2001 r. opóźnione. Następnie firm przeniesione do nowszych wersji (np. w wersji 2.0, 3.5 i .NET 4.x). Większość z tych aplikacji został uruchomiony w systemie Windows Server i usług Internet Information Server (IIS), a używane relacyjnej bazy danych, takich jak SQL Server, Oracle, MySQL lub innych RDBMS.

Większość istniejących aplikacji .NET dzisiaj utworzona na podstawie .NET Framework 4.x, a nawet w .NET Framework 3.5 i Użyj struktury sieci web, takich jak ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, usług Windows Communication Foundation (WCF), biblioteki SignalR platformy ASP.NET i stron ASP.NET Web Pages . Ustalona tych technologii .NET Framework są zależne od Windows. Tej zależności ważne jest, aby wziąć pod uwagę, jeśli są po prostu Migrowanie starszych aplikacji, a użytkownik chce wprowadzenia minimalnych zmianach w infrastrukturze aplikacji.

Rysunek 1 – 2 przedstawiono podstawowe technologie i style architektury używane na każdym poziomie dojrzałości trzy chmury:

![Podstawowe technologie dla każdego poziomu dojrzałości w przypadku przeprowadzania modernizacji istniejących .NET aplikacji sieci web](./media/image1-2.png)

> **Rysunek 1-2.** Podstawowe technologie dla każdego poziomu dojrzałości w przypadku przeprowadzania modernizacji istniejących .NET aplikacji sieci web

Rysunek 1 – 2 wyróżnia najbardziej typowych scenariuszy, ale wielu hybrydowych i odmiany mieszane są możliwe, jeśli chodzi o architekturze. Na przykład modele dojrzałości zastosowanie nie tylko do architekturami monolitycznymi w istniejących aplikacji sieci web, ale orientacji usługi, N-warstwowa i innych zmian stylów architektury. Wyższe fokus lub wartość procentowa na typ jednej lub drugiej architektury i technologii pokrewnych określa ogólny poziom dojrzałości w aplikacji.

Każdy poziom dojrzałości w procesie modernizacji jest skojarzona z następujących technologii klucza i metod:

- **Gotowa do użycia w infrastrukturze w chmurze** (rehost lub basic przekształcenia): Pierwszym krokiem w wielu organizacjach chcesz tylko szybko wykonywać strategii migracji do chmury. W takim przypadku aplikacje są rehostowanym. Większość rehosting można zautomatyzować za pomocą [usługi Azure Migrate](https://aka.ms/azuremigrate), to usługa, która zawiera wskazówki, szczegółowe informacje i mechanizmy potrzebne, aby pomóc w migracji do platformy Azure oparte na chmurze narzędzi, takich jak [usługi Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)i [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/). Możesz również skonfigurować rehosting ręcznie, dzięki czemu można zapoznać się szczegóły infrastruktury zasobów podczas przenoszenia starsze aplikacje w chmurze. Na przykład można przenieść swoje aplikacje na maszynach wirtualnych na platformie Azure z małym modyfikacji prawdopodobnie za pomocą tylko zmiany w konfiguracji pomocniczych. W tym przypadku sieci jest podobne do środowiska lokalnego, zwłaszcza, jeśli tworzenie sieci wirtualnych na platformie Azure.

- **Zoptymalizowane pod kątem chmury** (zarządzane usługi i kontenery Windows): Ten model jest o wprowadzaniu kilka optymalizacji wdrożenia ważne uzyskanie niektórych znaczące korzyści związane z chmury, bez konieczności zmieniania podstawowa Architektura aplikacji. W tym miejscu podstawowych krokiem jest dodanie [kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) obsługuje do istniejącej aplikacji .NET Framework. To ważny krok (konteneryzacji) nie wymaga zmiany kodu, więc ogólnego nakładu lift- and -shift światła. Możesz użyć narzędzi, takich jak [Image2Docker](https://github.com/docker/communitytools-image2docker-win) lub Visual Studio przy użyciu jego narzędzi [Docker](https://www.docker.com/). Visual Studio automatycznie wybiera inteligentne wartości domyślne dla aplikacji ASP.NET i obrazy kontenerów Windows. Narzędzia te oferują szybkie wewnętrzną pętlę i szybkiej ścieżki, aby uzyskać kontenery na platformie Azure. Zwiększona elastyczności podczas wdrażania w wielu środowiskach. Następnie skierowaniem ich do produkcji, można wdrożyć kontenerów Windows [Azure Web App for Containers](https://azure.microsoft.com/services/app-service/containers/), [Azure Container Instances (ACI), a maszyny wirtualne platformy Azure z systemem Windows Server 2016 i kontenerów, jeśli wolisz podejście IaaS. W przypadku nieco bardziej złożonych aplikacji obsługującej wiele kontenerów do koordynatorów, takich jak [usługi Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) lub [usługi Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/). W trakcie tego początkowego modernizacji można dodać zasoby w chmurze, takich jak monitorowanie za pomocą narzędzi, takich jak [usługi Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); Potoków ciągłej integracji/ciągłego Dostarczania cykle Twojej aplikacji za pomocą [usługom DevOps platformy Azure](https://azure.microsoft.com/services/devops/); i wiele więcej zasobów usługi danych, które są dostępne na platformie Azure. Na przykład można zmodyfikować aplikacji monolitycznych sieci web, który pierwotnie został opracowany przy użyciu tradycyjnych [wzorca ASP.NET Web Forms](https://www.asp.net/web-forms) lub [platformy ASP.NET MVC](https://www.asp.net/mvc), ale teraz wdrożyć ją za pomocą kontenerów Windows. Gdy używasz kontenery Windows, należy również Migruj dane do bazy danych w [wystąpienia zarządzanego Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), wszystko to bez konieczności zmieniania podstawowa Architektura aplikacji.

- **Cloud-Native**: Systemie, możesz pomyśleć o projektowanie [natywnych dla chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikacji, gdy są one ukierunkowane przy wielu zespołach niezależne opracowywanie nad różnych mikrousług, które mogą być duże i złożone aplikacje rozwinięte i wdrażane niezależnie. Ponadto ze względu na skalowalność granularized i jest niezależny od poszczególnych mikrousług. Te podejściach architektonicznych stoją w obliczu wyzwań bardzo ważne i złożoności, ale może być znacznie upraszczane przez użycie usłudze PaaS w chmurze i koordynatorów, takich jak [usługi Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (zarządzane rozwiązanie Kubernetes), [usługa platformy Azure Service Fabric i [usługi Azure Functions](https://azure.microsoft.com/services/functions/) podejście bez użycia serwera. Te metody (takie jak mikrousługi i aplikacje niewymagające użycia serwera) zwykle wymagają architektury w chmurze i pisanie nowego kodu — kod, który jest dostosowany do konkretnych platform PaaS lub kod, który jest wyrównywany z konkretnej architektury, takich jak mikrousługi.

Rysunek 1 – 3 przedstawiono technologie wewnętrznego użyć na każdym poziomie dojrzałości:

![Wewnętrzny technologii dla każdego poziomu dojrzałości modernizacji](./media/image1-3.png)

> **Rysunek 1-3.** Wewnętrzny technologii dla każdego poziomu dojrzałości modernizacji

## <a name="lift-and-shift-scenario"></a>Scenariusz Lift- and -shift

Lift- and -shift migracji należy pamiętać o tym, że w swoich scenariuszy aplikacji, można użyć wielu różnych odmian lift- and -shift. Jeśli możesz rehost tylko aplikacji, może być scenariusz, tak jak pokazano na rysunku 1-: 4, gdzie używanie maszyn wirtualnych w chmurze tylko dla aplikacji i serwera bazy danych.

![Przykładowy scenariusz czystego IaaS w chmurze](./media/image1-4.png)

> **Rysunek 1 – 4**. Przykładowy scenariusz czystego IaaS w chmurze

## <a name="modernization-scenarios"></a>Modernizacja scenariuszy

W przypadku scenariuszy modernizacja może mieć czystego aplikacji zoptymalizowane pod kątem chmury, która używa elementów tylko z tego poziomu dojrzałości. Mogą też stan pośredni aplikacji za pomocą niektóre elementy z obsługa infrastruktury chmury i innych elementów z zoptymalizowane pod kątem chmury (a "wybrać" lub mieszanego modelu), takich jak rysunek 1-5.

![Przykładowy "wybrać" scenariusz, używając bazy danych IaaS, metodyki DevOps i zasoby konteneryzacji](./media/image1-5.png)

> **Rysunek 1 – 5.** Przykładowy "wybrać" scenariusz, używając bazy danych IaaS, metodyki DevOps i zasoby konteneryzacji

Następnie idealnym scenariuszu wielu istniejących aplikacji .NET Framework przeprowadzić migrację można przeprowadzić migracji aplikacji zoptymalizowane pod kątem chmury, aby uzyskać znaczące korzyści związane z małego wysiłku. Ta metoda ustawia również możesz dla natywnych dla chmury jako możliwego do przyszłego rozwoju. Rysunek 1 – 6 przedstawia przykład.

![Przykładowy scenariusz aplikacje zoptymalizowane pod kątem chmury za pomocą kontenerów Windows i usługi zarządzane](./media/image1-6.png)

> **Rysunek 1 – 6.** Przykładowy scenariusz aplikacje zoptymalizowane pod kątem chmury za pomocą kontenerów Windows i usługi zarządzane

Kontynuowanie nawet, można rozszerzyć swoją istniejącą aplikację zoptymalizowane pod kątem chmury, dodając kilka mikrousług w określonych scenariuszach. To spowoduje przeniesienie można częściowo na poziomie modelu natywnych dla chmury, który nie jest główny zespół obecne wskazówki.

## <a name="what-this-guide-does-not-cover"></a>Co ten przewodnik nie obejmuje

Ten przewodnik obejmuje określony podzbiór przykładowe scenariusze, jak pokazano w rysunku 1-7. Ten przewodnik koncentruje się tylko w scenariuszach lift- and -shift, a ostatecznie, na podstawie modelu zoptymalizowane pod kątem chmury. Zoptymalizowane pod kątem chmury w modelu w aplikacji .NET Framework jest zmodernizowane przy użyciu kontenerów Windows, a także dodatkowe składniki, takie jak monitorowanie i potoków ciągłej integracji/ciągłego wdrażania. Każdy składnik jest szybsze wdrażanie aplikacji w chmurze, a także z elastycznością.

![W tym przewodniku nie pasuje do natywnych dla chmury](./media/image1-7.png)

> **Rysunek 1-7.** W tym przewodniku nie pasuje do natywnych dla chmury

Ten przewodnik koncentruje się określone. Przedstawia on ścieżki, które można podjąć w celu osiągnięcia lift- and -shift istniejących aplikacji platformy .NET, bez transformować i wprowadzania zmian w kodzie. Ostatecznie go dowiesz się, jak utworzyć aplikację zoptymalizowane pod kątem chmury.

Ten przewodnik nie pokazuje sposób tworzenia aplikacji natywnych dla chmury, takich jak rozwój do architektury mikrousług. Przekształcanie aplikacji lub utworzyć zupełnie nowym aplikacje, które są oparte na mikrousługach, zobacz książki elektronicznej [Mikrousługi .NET: Architektura konteneryzowanych aplikacji .NET](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Kontenerowych nimi cykl życia aplikacji platformy Docker przy użyciu platformy firmy Microsoft i narzędzi** (do pobrania Książka elektroniczna) \
  <https://aka.ms/dockerlifecycleebook>

- **Mikrousługi .NET: Architektura konteneryzowanych aplikacji .NET** (do pobrania Książka elektroniczna) \
  <https://aka.ms/microservicesebook>

- **Tworzenie architektury nowoczesnych aplikacji sieci web platformy ASP.NET Core oraz platforma Azure** (do pobrania Książka elektroniczna) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Kto powinien używać tego przewodnika

Ten przewodnik został napisany dla deweloperów i architektów rozwiązań, chcą modernizacji istniejących aplikacji sieci web ASP.NET lub usługi WCF, które są oparte na .NET Framework dla zwiększonej elastyczności w wysyłki i zwalniania aplikacji.

Również może być przydatne w przewodniku Jeśli jesteś osobą podejmującą decyzje techniczne, np. architektury przedsiębiorstwa lub rozwoju potencjalnych klientów/Dyrektor metodykę tylko z omówieniem korzyści, które można uzyskać przy użyciu kontenerów Windows i wdrażania w chmurze, korzystając z Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak używać tego przewodnika

Ten przewodnik dotyczy "Dlaczego" — Dlaczego warto modernizacji istniejących aplikacji, a określone korzyści z używania kontenerów Windows, gdy przeniesiesz swoje aplikacje w chmurze. Zawartość w pierwszym kilka rozdziałach przewodnika jest przeznaczony dla architektów i osób podejmujących decyzje techniczne, potrzebują Przegląd, ale który nie ma potrzeby skupić się na implementacji i szczegółowe informacje techniczne, krok po kroku.

Ostatnie rozdział przewodnika wprowadza wiele wskazówki koncentrujących się na konkretnych scenariuszach wdrażania. Ten przewodnik oferuje krótszych wersji wskazówki, aby podsumować scenariusze i wyróżnić swoje korzyści. Pełne przewodniki Przechodzenie do szczegółów instalacji i wdrożenia i są publikowane jako zbiór [wpisów w witrynie typu wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) w tej samej publicznego [repozytorium GitHub](https://github.com/dotnet-architecture/eShopModernizing) w przypadku, gdy powiązane przykładowych aplikacji znajdują się (zostało to omówione w ciągu następnych sekcja). Ostatni rozdział i przewodniki krok po kroku w witrynie typu wiki w witrynie GitHub są większe znaczenie dla deweloperów i architektów, którzy chcesz skupić się na szczegółów implementacji.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Przykładowe aplikacje w przypadku przeprowadzania modernizacji starsze aplikacje: eShopModernizing

[EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) repozytorium w serwisie GitHub oferuje dwie przykładowe aplikacje, które symulują aplikacji monolitycznych starszej wersji w sieci web. Jedna aplikacja sieci web jest opracowany przy użyciu platformy ASP.NET MVC; opracowano drugiej aplikacji sieci web przy użyciu wzorca ASP.NET Web Forms i trzeci aplikacja to aplikacja N-warstwowa przy użyciu formularzy WinForm klienta aplikacji pulpitu, korzystanie z zapleczem usługi WCF. Te aplikacje są oparte na tradycyjnych .NET Framework. Te przykładowe aplikacje nie używaj platformy .NET Core lub ASP.NET Core, ponieważ są one powinien być istniejącej starszych aplikacji .NET Framework, aby być zmodernizowane.

Te przykładowe aplikacje druga wersja, przy użyciu zmodernizowane kodu, które są dość prosta. Najważniejsza różnica między wersjami aplikacji jest drugi wersji kontenerów Windows jako wyboru wdrożenia. Istnieje również kilka dodatki do drugiej wersji, takich jak magazyn obiektów blob platformy Azure do zarządzania obrazami, usługi Azure Active Directory do zarządzania zabezpieczeniami i usługi Azure Application Insights do monitorowania i przeprowadzania inspekcji aplikacji.

## <a name="send-your-feedback"></a>Wyślij opinię

Ten przewodnik został napisany, aby lepiej zrozumieć opcje poprawianie i modernizacji istniejących aplikacji sieci web platformy .NET. Przewodnik i powiązane przykładowe aplikacje są obecnie przekształcane. Chętnie poznamy Twoją opinię! Jeśli masz komentarze na temat sposobu ten przewodnik może być bardziej użyteczne, wyślij je do [ dotnet-architecture-ebooks-feedback@service.microsoft.com ](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
>[Next](lift-and-shift-existing-apps-azure-iaas.md)
