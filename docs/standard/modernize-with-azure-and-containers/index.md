---
title: Modernizacji istniejących .NET aplikacji z chmury Azure i kontenery systemu Windows (wydanie 2)
description: Dowiedz się przyrostu i przesunięcia oraz modernizacji istniejących aplikacji do chmury Azure i kontenerów Książka elektroniczna.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 4/28/2018
ms.openlocfilehash: 3fcfdca68e05494785148cbbe149cdc2f812c577
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956386"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizacji istniejących aplikacji .NET z chmury Azure i kontenery systemu Windows (wydanie 2)

![Obraz tytułowych](./media/cover.png)

OPUBLIKOWANY PRZEZ  
Microsoft, naciśnij i DevDiv firmy Microsoft  
Działy firmy Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399, USA  

Copyright © 2018 przez firmę Microsoft Corporation  

Wszelkie prawa zastrzeżone. Nie części zawartości tej książki może odtworzyć w jakimkolwiek formularzu, lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ten podręcznik jest dostępny bezpłatnie w formie elektronicznej książki (Książka elektroniczna) dostępnych za pośrednictwem wielu kanałów w firmie Microsoft takich jak http://dot.net/architecture.

Jeśli masz pytania dotyczące tej książki, poczty e-mail w [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Ten podręcznik podano "jako — jest" i odzwierciedla widoków i opinie autora. Widoki, opinie i informacje wyrażone w tej książki, w tym adresy URL i innymi odwołaniami do witryn internetowych, mogą ulec zmianie bez uprzedzenia.

Niektóre przedstawione przykłady są udostępniane tylko do celów ilustracyjnych i są fikcyjne. Żadne rzeczywiste skojarzenia ani połączenia jest przeznaczony lub powinny być zakładane.

Firma Microsoft i znakami, znajduje się na http://www.microsoft.com na stronie sieci Web "Znaki towarowe" są znakami towarowymi grupy firm Microsoft. Wszystkie inne znaki są własnością ich prawnych właścicieli.

Autor:
> **Cesarowi de la Torre**, Sr. PM, .NET Product Team, Microsoft Corp.

Uczestnicy i osoby dokonujące przeglądu:
> **Scott myśliwego**, PM Dyrektor partnera, .NET zespół firmy Microsoft  
> **Yuknewicz Pawła**, główny menedżer PM, Microsoft Visual Studio Tools zespołu  
> **Ewa Guthrie**, Sr. Microsoft Visual Studio Tools zespół PM  
> **Ankit Asthana**, główny menedżer PM, .NET zespół firmy Microsoft  
> **Unai Zorrilla**, realizacji Developer, zwykły pojęcia  
> **Javier Valero**, dyrektora operacyjnego urzędnika na rozwiązanie Grupo  

## <a name="introduction"></a>Wprowadzenie

W przypadku podjęcia decyzji modernizacji sieci web aplikacji lub usług i przenieś je do chmury, niekoniecznie nie trzeba pełni rearchitect aplikacji. Oszczędzasz aplikacji przy użyciu metody zaawansowanych, takich jak mikrousług nie zawsze jest opcja ze względu na ograniczenia kosztów i czasu. W zależności od typu aplikacji oszczędzasz aplikacji również może nie być konieczne. W celu zoptymalizowania efektywności kosztowej strategii migracji chmurze organizacji, ważne jest wziąć pod uwagę wymagania dotyczące aplikacji i wymagania firmy. Musisz określić:

- Aplikacje, które wymagają transformację lub oszczędzasz.

- Aplikacje, które muszą zostać tylko częściowo modernizowana.

- Aplikacje, które można "przyrostu i przesunięcia" bezpośrednio do chmury.

## <a name="about-this-guide"></a>O tym przewodniku

W tym przewodniku skupiono się głównie na początkowej modernizacji istniejącą witrynę sieci web platformy Microsoft .NET Framework lub zorientowane na usługę aplikacji, co oznacza akcji przenoszenia obciążeń w środowisku nowszej lub bardziej nowoczesnych bez znacznie modyfikacji kodu aplikacji Podstawowa architektura i. 

W tym przewodniku omówiono również zalet przenoszenie aplikacji w chmurze i częściowo modernizacji aplikacji przy użyciu określonego zestawu nowych technologii i metod, takich jak kontenery systemu Windows i powiązane platform obliczeń w obsługi kontenery systemu Windows Azure.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Ścieżka do chmury dla istniejących aplikacji .NET

Organizacje zazwyczaj wybrać przenosić do chmury, elastyczność i szybkość, jaką może uzyskać ich aplikacji. Skonfigurowaniem tysiącami serwerów (VM) w chmurze (w minutach) w porównaniu do tygodni, zwykle wymagany do konfigurowania serwerów lokalnych.

Nie ma jednej, pasującego strategii migracji aplikacji w chmurze. Strategię migracji prawo zależy od potrzeb organizacji i priorytety i rodzaju aplikacji, które są migrowane. Nie wszystkie aplikacje gwarantuje inwestycji przechodzenia do platforma jako usługa ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) modelu lub tworzenie [native chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) modelu aplikacji. W wielu przypadkach można wykonać podejście etapowe lub przyrostowej inwestycji podczas przenoszenia zasobów w chmurze, na podstawie Twoich potrzeb biznesowych.

Dla nowoczesnych aplikacji z najlepiej długoterminowej elastyczność i wartość dla organizacji, mogą korzystać z zainwestować w *native chmury* architekturach aplikacji. Jednak dla aplikacji, które są istniejące lub starsze zasoby klucz jest poświęcić minimalny czas i pieniądze (niezmienioną oszczędzasz lub kodu) podczas przenoszenia ich do chmury, do osiągnięcia znaczących korzyści.

Rysunek 1-1 przedstawiono możliwe ścieżki, które można wykonać w przypadku przenoszenia istniejących aplikacji .NET do chmury w fazach przyrostowe.

 ![Ścieżki modernizacji istniejących aplikacji .NET i usługi](./media/image1-1.png)

> **Rysunek 1-1**. Ścieżki modernizacji istniejących aplikacji .NET i usługi

Każde podejście migracji jest różne korzyści i przyczyn dotyczących korzystania z niego. Można wybrać jeden podejście, gdy migrację aplikacji do chmury, lub opcję niektóre składniki z wielu metod. Poszczególne aplikacje nie są ograniczone do pojedynczego stanu podejście lub płatności. Na przykład typowym podejściem hybrydowego musi niektórych składników lokalnych oraz inne składniki w chmurze.

Definicja i krótki opis dla każdego poziomu dojrzałości aplikacji są następujące:

**Poziom 1: Gotowe infrastruktury chmury** aplikacji: takie podejście migracji, należy po prostu migracji lub rehost bieżącej aplikacji lokalnej infrastruktury jako usługi ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) platformy. Aplikacje mają prawie skład taki sam jak przed, ale teraz wdrażać maszyny wirtualne w chmurze.
Zazwyczaj nosi tego prostego typu migracji w branży "Podnieś & przesunięcia".

**Poziom 2: Chmury zoptymalizowany pod kątem** aplikacji: na tym poziomie i nadal bez oszczędzasz lub zmienianie kodu znaczących można uzyskać dodatkowe korzyści uruchamianie aplikacji w chmurze przy użyciu nowoczesnych technologii, takich jak kontenery i dodatkowe zarządzanymi w chmurze usługi. Można zwiększyć elastyczność aplikacji na potrzeby wysłania szybciej dopracowanie procesów operations (DevOps) rozwoju przedsiębiorstwa. Można to osiągnąć przy użyciu technologii, takich jak kontenery systemu Windows, który jest oparty na aparatem platformy Docker. Kontenery Usuń tarcie powodowany przez zależności aplikacji, podczas wdrażania w kilku etapach. W tym modelu dojrzałości wdrożeniem kontenerów na IaaS, lub PaaS podczas korzystania z dodatkowych zarządzanymi w chmurze usługi związane z bazami danych, buforować jako usługa, monitorowania i ciągłej integracji/ciągłe wdrażanie potoki (CI/CD).

Trzeci poziom dojrzałości jest ostatecznym celem w chmurze, ale jest opcjonalny w przypadku wielu aplikacji i nie głównym celem niniejszego przewodnika:

**Poziom 3: Natywne chmury** aplikacji: takie podejście migracji jest zwykle regulowane przez potrzeb biznesowych i celów modernizacji kluczowych aplikacji. Na tym poziomie PaaS usługi są używane do przenoszenia aplikacji na platformach obliczeniowych PaaS. Można zaimplementować [native chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) architektury aplikacji i mikrousług podlegać ewolucji aplikacji z długoterminowej elastyczność i można skalować do nowych limitów. Ten typ modernizacji wymaga zwykle zaprojektowanie specjalnie z myślą o chmurze. Nowy kod często muszą być napisane, szczególnie w przypadku, gdy zostanie przeniesione do chmury natywnych aplikacji i modele oparte na mikrousługi. Takie podejście ułatwia udogodnień, które są trudne do osiągnięcia w danym środowisku wbudowanymi i lokalnych aplikacji.

Tabela 1-1 opisano podstawowe zalety i wybór każde podejście migracji lub modernizacji.

| **Gotowe do infrastruktury w chmurze** <br /> *Podnieś i przesunięcia* | **Zoptymalizowane pod kątem chmury** <br /> *Modernizacji* | **Natywne chmury** <br /> *Modernizacji, rearchitect i Zapisz ponownie* |
|---|---|---|
| **Docelowy obliczeń aplikacji** |
| Aplikacje wdrożone na maszynach wirtualnych na platformie Azure | Wbudowanymi lub warstwowe aplikacje wdrożone usługi Azure App Service, wystąpienie kontenera platformy Azure (ACI), maszynach wirtualnych z kontenerów, sieć szkieletowa usług Azure lub AKS (usługa Azure Kubernetes) | Konteneryzowanych mikrousług usługi Kubernetes Azure (AKS), usługi Service Fabric i niekorzystającą mikrousług oparta na funkcjach Azure. |
| **Miejsce docelowe danych** |
| SQL lub dowolnego relacyjnej bazy danych na maszynie Wirtualnej | Azure wystąpienia bazy danych SQL zarządzane lub innej zarządzanej bazy danych w chmurze. | Ziarno grzywną baz danych, na mikrousługi, na podstawie bazy danych SQL Azure, Azure DB rozwiązania Cosmos lub innej zarządzanej bazy danych w chmurze |
| **Zalety**|
| <li>Brak oszczędzasz nie nowego kodu <li> Co najmniej wysiłku dla szybkiej migracji. <li> Najmniej-najprostszy obsługiwany na platformie Azure <li> Gwarantuje dostępność podstawowych <li> Po przeniesieniu do chmury, łatwiej modernizacji jeszcze więcej | <li> Nie oszczędzasz <li> Zmiany minimalnego kodu/konfiguracji <li> Ulepszone wdrażanie oraz elastyczność DevOps do zwolnienia z powodu kontenerów <li> Zwiększona gęstość i obniżyć koszty wdrożenia <li> Mobilność aplikacji i zależności <li> Elastyczność host docelowy: PaaS podejścia lub IaaS | <li> Architektów chmury, możesz pobrać najważniejsze korzyści z chmury, ale jest wymagany nowy kod <li> Mikrousług metod natywnych w chmurze <li> Nowoczesne aplikacje krytycznym, elastyczne chmury hyper skalowalności <li> Usługi w pełni zarządzane <li> Zoptymalizowana pod kątem skalowania <li> Zoptymalizowana pod kątem elastyczność autonomicznego przez podsystem <li> Oparty na wdrożenia i opracowywania oprogramowania |
| **Wyzwania** |
| <li> Mniejsze wartości chmury, innej niż shift kosztów operacyjnych lub zamknięcia centrów danych <li> Odbywa się tylko: Brak systemu operacyjnego lub stosowanie poprawek do oprogramowania pośredniczącego; mogą korzystać z rozwiązań infrastruktury, takich jak Terraform, Spinnaker lub Puppet | <li> Containerizing jest dodatkowy krok w naukę dla deweloperów i operacji IT <li> DevOps i CI/CD potoki jest zwykle "koniecznością" dla tej metody. Jeśli nie jest aktualnie w kultury organizacji, można ją żądanie dodatkowe| <li> Wymaga rearchitecture natywnych aplikacji w chmurze i architektury mikrousługi i zwykle wymaga znaczących kodu refaktoryzacji lub ponowne zapisywanie podczas modernizacji (zwiększona czas i pieniądze) <li> DevOps i CI/CD potoki jest zwykle "koniecznością" dla tej metody. Jeśli nie jest aktualnie w kultury organizacji, można ją żądanie dodatkowe|
> **Tabela 1-1.** Korzyści i wyzwania modernizacji ścieżki dla usług i aplikacji .NET

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Kluczowe technologie i architektur według poziomu dojrzałości

Aplikacji programu .NET framework początkowo korzystać z programu .NET Framework w wersji 1.0, wydanej w późne 2001. Następnie przenieść firmy do nowszej wersji (np. 2.0 i 3.5, .NET 4.x). Większość tych aplikacji został uruchomiony w systemie Windows Server i usługi Internet Information Server (IIS), a używane relacyjnej bazy danych, takich jak SQL Server, Oracle, MySQL lub innych RDBMS.

Większość istniejących aplikacji .NET dzisiaj może być oparta na programie .NET Framework 4.x, lub nawet w przypadku programu .NET Framework 3.5 i użyj struktur sieci web, takich jak ASP.NET MVC, formularzy sieci Web ASP.NET Web API platformy ASP.NET, Windows Communication Foundation (WCF), ASP.NET SignalR i stron sieci Web ASP.NET . Te ustalona technologii .NET Framework są zależne od systemu Windows. Zależność ta jest istotnym elementem do rozważenia, jeśli są po prostu Migrowanie starszych aplikacji i chcesz dokonać zmian minimalnej infrastruktury aplikacji.

Rysunek 1 i 2 przedstawiono podstawowe technologie i style architektura używane na każdym z poziomów trzy chmury:

![Podstawowe technologie dla każdego poziomu dojrzałości dla .NET istniejących modernizacji aplikacji sieci web](./media/image1-2.png)

> **Rysunek 1 i 2.** Podstawowe technologie dla każdego poziomu dojrzałości dla .NET istniejących modernizacji aplikacji sieci web

Rysunek 1 i 2 prezentuje najbardziej typowych scenariuszy, ale wiele hybrydowego i mieszanych zmiany są możliwe po przejściu do architektury. Na przykład modele dojrzałości mają zastosowanie nie tylko do architektury wbudowanymi w istniejących aplikacji sieci web, ale orientacji usługi, N-warstwowa i innych zmian styl architektury. Wyższy fokus lub wartość procentowa w jednej lub drugiej Architektura typu i technologii pokrewnych określa ogólnego poziomu dojrzałości aplikacji.

Każdego poziomu dojrzałości w procesie modernizacji jest skojarzona z następujące kluczowe technologie i metod:

- **Gotowe do infrastruktury w chmurze** (rehost lub basic Podnieś & przesunięcia): jako pierwszy krok w wielu organizacjach będzie tylko szybko wykonywany strategii migracji chmury. W tym przypadku są rehosted aplikacji. Większość rehosting można zautomatyzować za pomocą [migracji Azure](https://aka.ms/azuremigrate), usługa, która zawiera wskazówki, szczegółowych informacji i mechanizmów konieczne jest pomocne podczas migracji do usługi Azure oparte na chmurze takich narzędzi jak [usługi Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)i [usługi migracji bazy danych platformy Azure](https://azure.microsoft.com/campaigns/database-migration/). Można również skonfigurowaniu rehosting ręcznie, dzięki czemu można zapoznać się szczegóły infrastruktury zasobów podczas przenoszenia starsze aplikacje w chmurze. Na przykład przenieść aplikacji do maszyn wirtualnych na platformie Azure przy małej modyfikacji prawdopodobnie z tylko konfiguracji drobne zmiany. W takim przypadku sieci jest podobne do środowiska lokalnego, zwłaszcza, jeśli tworzenie sieci wirtualnych na platformie Azure.

- **Zoptymalizowane pod kątem chmury** (zarządzanych usług i kontenery systemu Windows): ten model jest o wprowadzaniu kilka optymalizacji wdrożenia ważne uzyskanie niektóre istotne korzyści z chmury, bez konieczności zmieniania podstawowa Architektura aplikacji. W tym miejscu podstawowych krokiem jest dodanie [kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) obsługuje do istniejących aplikacji .NET Framework. To ważny krok (przechowywanie w kontenerach) nie wymaga modyfikowania kodu, więc ogólnego nakładu przyrostu i shift jest lekki. Można użyć narzędzia, takie jak [Image2Docker](https://github.com/docker/communitytools-image2docker-win) lub Visual Studio z jej narzędzi dla [Docker](https://www.docker.com/). Visual Studio automatycznie wybiera inteligentne wartości domyślne dla aplikacji ASP.NET i obrazy kontenery systemu Windows. Te narzędzia zapewniają szybkie pętli wewnętrznej i szybka ścieżka uzyskanie kontenerów na platformie Azure. Zwiększona aktywności podczas wdrażania w wielu środowiskach. Następnie przenoszenia do produkcji, można wdrożyć do kontenerów Windows [aplikacji sieci Web platformy Azure dla kontenerów](https://azure.microsoft.com/en-us/services/app-service/containers/), [wystąpień kontenera platformy Azure (ACI) i maszyn wirtualnych platformy Azure z systemem Windows Server 2016 i kontenerów, jeśli wolisz podejście IaaS. Nieco bardziej złożonych aplikacji kontenera usługi, do orchestrators, takich jak [sieć szkieletowa usług Azure](https://azure.microsoft.com/services/service-fabric/) lub [usługę Azure Kubernetes (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/). Podczas tej początkowej modernizacji można dodać zasoby z chmury, takich jak monitorowanie za pomocą takich narzędzi jak [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); Potoki CI/CD dla Twojego cyklami życia aplikacji z [Visual Studio Team Services](https://www.visualstudio.com/team-services/); i wiele więcej danych zasobów usług, które są dostępne w systemie Azure. Na przykład można zmodyfikować aplikacji sieci web wbudowanymi, który pierwotnie został opracowany przy użyciu tradycyjnych [formularzy sieci Web ASP.NET](https://www.asp.net/web-forms) lub [ASP.NET MVC](https://www.asp.net/mvc), ale teraz wdrożyć ją przy użyciu kontenery systemu Windows. Gdy używasz kontenery systemu Windows, należy również migrację danych do bazy danych w [wystąpienia zarządzane bazy danych SQL Azure](https://docs.microsoft.com/azure/sql-database/), wszystko to bez zmieniania podstawowa Architektura aplikacji.

- **Natywne chmury**: wprowadzonymi, możesz pomyśleć o zaprojektowanie [native chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikacji przeznaczonych dużych i złożonych aplikacji z wielu niezależnych zespoły programistyczne mogły pracować nad różne mikrousług, które mogą być opracowane i wdrożone autonomicznie. Ponadto z powodu granularized i niezależne skalowanie na mikrousługi. Te podejścia do architektury wyzwania bardzo ważna i złożoności, ale może być znacznie uproszczone przy użyciu chmury PaaS i orchestrators, takich jak [usługę Azure Kubernetes (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/) (zarządzane Kubernetes), [usługę Azure Sieć szkieletowa, i [usługi Azure Functions](https://azure.microsoft.com/services/functions/) niekorzystającą podejścia. Te metody (takich jak mikrousług i Serverless) zwykle wymaga projektowania dla chmury i pisanie nowego kodu — kod, który jest dostosowane do określonych platform PaaS lub kod, aby była zgodna z określonych architektur, takich jak mikrousług.

Rysunek 1 – 3 przedstawiono technologie wewnętrzny można dla każdego poziomu dojrzałości:

![Wewnętrzny technologii dla każdego poziomu dojrzałości modernizacji](./media/image1-3.png)

> **Rysunek 1-3.** Wewnętrzny technologii dla każdego poziomu dojrzałości modernizacji

## <a name="lift-and-shift-scenario"></a>Scenariusz przyrostu i shift

Migracji przyrostu i shift należy pamiętać, że można użyć wielu różnych wariantów przyrostu i shift w scenariuszach Twojej aplikacji. Jeśli aplikację można tylko rehost, może być scenariusza, tak jak pokazano na rysunku 1-: 4, którym używać maszyn wirtualnych w chmurze tylko dla aplikacji i serwer bazy danych.

![Przykładowy scenariusz IaaS czysty w chmurze](./media/image1-4.png)

> **Rysunek 1-4**. Przykładowy scenariusz IaaS czysty w chmurze

## <a name="modernization-scenarios"></a>Scenariusze modernizacji

W przypadku scenariuszy modernizacji może mieć czystego aplikacji zoptymalizowanych pod kątem chmury, która używa elementów tylko z tego poziomu dojrzałości. Mogą też stan pośredni aplikacja o niektóre elementy z gotowości infrastruktury chmury i inne elementy z zoptymalizowanych pod kątem chmury (a "wybrać" lub mieszane modelu), takich jak rysunek 1-5.

![Przykład "wybrać" scenariuszu z bazą danych IaaS, metodyki DevOps i zasoby przechowywanie w kontenerach](./media/image1-5.png)

> **Rysunek 1-5.** Przykład "wybrać" scenariuszu z bazą danych IaaS, metodyki DevOps i zasoby przechowywanie w kontenerach

Obok idealnym scenariuszu wielu istniejących aplikacji .NET Framework przeprowadzić migrację można migrować do aplikacji zoptymalizowanych pod kątem chmury, aby uzyskać istotne korzyści z małego wysiłku. Takie podejście ustawi należy do chmury Native możliwego do przyszłego rozwoju. Rysunek 1 – 6 przedstawiono przykład.

![Przykładowy scenariusz aplikacji zoptymalizowanych pod kątem chmury kontenery systemu Windows i zarządzane usługi](./media/image1-6.png)

> **Rysunek 1 – 6.** Przykładowy scenariusz aplikacji zoptymalizowanych pod kątem chmury kontenery systemu Windows i zarządzane usługi

Kontynuowanie nawet, można rozszerzyć istniejącą aplikację zoptymalizowanych pod kątem chmury, dodając kilka mikrousług w określonych scenariuszach. To przeniosłaby można częściowo na poziomie modelu chmury macierzystego, który nie jest głównym celem niniejszego wskazówki.


## <a name="what-this-guide-does-not-cover"></a>Czego ten przewodnik nie obejmuje

W tym przewodniku dotyczą konkretnego podzestawu przykładowe scenariusze, jak pokazano w rysunek 1-7. Ten przewodnik koncentruje się tylko w scenariuszach przyrostu i shift, a ostatecznie w modelu zoptymalizowanych pod kątem chmury. W modelu zoptymalizowanych pod kątem chmury aplikacji .NET Framework jest modernizowana przy użyciu kontenery systemu Windows, a także dodatkowe składniki, takie jak monitorowanie, i potoków CI/CD. Każdy składnik jest szybsze wdrażanie aplikacji w chmurze i elastyczność.

![W tym przewodniku nie pasuje do chmury natywne](./media/image1-7.png)

> **Rysunek 1-7.** W tym przewodniku nie pasuje do chmury natywne

Celem niniejszego przewodnika jest określone. Przedstawia on ścieżkę, którą można wykonać w celu osiągnięcia przyrostu i shift istniejących aplikacji .NET, bez oszczędzasz i bez zmian kodu. Ostatecznie, jego pokazuje, jak utworzyć aplikację zoptymalizowanych pod kątem chmury.

Ten przewodnik nie pokazuje, jak tworzyć aplikacje natywne w chmurze, np. sposób rozwijać do architektury mikrousług. Aby rearchitect aplikacji lub tworzenie zupełnie nowym aplikacji, które są oparte na mikrousług, zobacz Książka elektroniczna [Mikrousług .NET: Architektura konteneryzowanych aplikacji .NET](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami** (do pobrania Książka elektroniczna): [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **.NET Mikrousług: Architektura konteneryzowanych aplikacji .NET** (do pobrania Książka elektroniczna): [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **Zaprojektowanie nowoczesnych aplikacji sieci web platformy ASP.NET Core i Azure** (do pobrania Książka elektroniczna): [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>Kto powinien używać ten przewodnik

Ten przewodnik został napisany dla deweloperów i architekci rozwiązań, którzy chcą modernizacji istniejących aplikacji sieci web ASP.NET lub usługi WCF, które są oparte na programie .NET Framework dla ulepszone elastycznie wysyłki i wydanie aplikacji.

Możesz również może być przydatne w tym przewodniku Jeśli jesteś osobą podejmującą decyzje technicznych, takich jak architekta enterprise lub programowanie realizacji/dyrektora, który właśnie chce omówienie korzyści, które można uzyskać za pomocą kontenery systemu Windows i wdrażając do chmury przy użyciu Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak używać tego przewodnika

Ten przewodnik dotyczy "Dlaczego" — Dlaczego warto modernizacji istniejących aplikacji i korzyści, Pobierz z aplikacji w przypadku przenoszenia do chmury, za pomocą kontenery systemu Windows. Zawartość w pierwszej kilka rozdziałach przewodnika jest przeznaczony dla architektów i technicznych inne osoby podejmujące decyzje, którzy potrzebują Przegląd, ale który nie ma potrzeby skupić się na implementacji i szczegółowe informacje techniczne, krok po kroku.

Poprzedni rozdział przewodnika wprowadzono wiele wskazówki koncentrujących się na scenariuszach wdrażania. W tym przewodniku oferuje krótszych wersji wskazówki, podsumować scenariusze i zaznacz ich zalety. Pełny przegląd Przechodzenie do szczegółów, Konfiguracja i implementacja i są publikowane jako zestaw [wpisów wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) w tej samej publicznego [repozytorium GitHub](https://github.com/dotnet-architecture/eShopModernizing) w przypadku, gdy pokrewne przykładowych aplikacji znajdują się (omówiona w następnej sekcja). Poprzedni rozdział i wskazówki krok po kroku typu wiki w witrynie GitHub mogą być większe znaczenie dla programistów i architektów, którzy chcą się skupić na szczegóły implementacji.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Przykładowe aplikacje dla modernizacji starsze aplikacje: eShopModernizing

[EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) repozytorium w usłudze GitHub oferuje dwie przykładowe aplikacje symulujących aplikacji starszych wbudowanymi sieci web. Jednej aplikacji sieci web został utworzony przy użyciu platformy ASP.NET MVC; drugi aplikacji sieci web został utworzony przy użyciu składnika ASP.NET Web Forms, a trzeci jest N-warstwowa aplikacja WinForms klienta aplikacji pulpitu, korzystanie z zapleczem usługi WCF. Te aplikacje są oparte na tradycyjnych .NET Framework. Te przykładowe aplikacje nie używaj .NET Core i ASP.NET Core, jak mają być istniejących starszych aplikacji .NET Framework do modernizowana można.

Te przykładowe aplikacje druga wersja zmodernizowanej kodu, które są bardzo prosta. Najważniejsze różnicę między wersjami aplikacji jest czy drugi wersji używanie kontenerów systemu Windows jako wybór wdrożenia. Istnieją również kilka dodatki do drugiej wersji, takich jak obiektach blob magazynu Azure do zarządzania obrazami, Azure Active Directory do zarządzania zabezpieczeniami i Azure Application Insights do monitorowania i przeprowadzania inspekcji aplikacji.

## <a name="send-your-feedback"></a>Wyślij swoją opinię

Ten przewodnik został napisany ułatwią zrozumienie opcji dotyczących poprawy i modernizacji istniejących aplikacji sieci web platformy .NET. Przewodnik i powiązane przykładowe aplikacje zmieniających się. Twoja opinia jest Zapraszamy! Jeśli masz komentarze na temat sposobu w tym przewodniku pomocne może być więcej Wyślij je do [ dotnet-architecture-ebooks-feedback@service.microsoft.com ](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
[Next](lift-and-shift-existing-apps-azure-iaas.md)
