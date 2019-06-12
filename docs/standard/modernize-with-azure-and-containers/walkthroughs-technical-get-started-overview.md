---
title: Omówienie przewodników i wprowadzającej dokumentacji technicznej
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów Windows | Przewodniki i technicznych wprowadzająca
ms.date: 04/28/2018
ms.openlocfilehash: 1ae6f3c1e739184356b97fa96e74bab402bf1d2a
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832951"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Omówienie przewodników i wprowadzającej dokumentacji technicznej

Aby ograniczyć rozmiar tę książkę elektroniczną, dodatkową dokumentację techniczną i pełne przewodniki zostały udostępnione w repozytorium GitHub. Online instruktaży, które jest opisane w tym rozdziale omówiono krok po kroku instalacji wielu środowisk, które są oparte na Windows kontenerów i wdrażanie na platformie Azure.

W poniższych sekcjach opisano, co poszczególnych przewodników o jego celów i wysokiego poziomu wizji i zawiera diagram zadania, które są zaangażowane. Możesz uzyskać wskazówki, samodzielnie w *eShopModernizing* aplikacje typu wiki repozytorium GitHub na <https://github.com/dotnet-architecture/eShopModernizing/wiki>.

## <a name="technical-walkthrough-list"></a>Lista technicznym

Poniższe przewodniki get-started zapewniają spójne i wyczerpujące wskazówki techniczne dotyczące przykładowe aplikacje, które można podnieść i shift przy użyciu kontenerów, a następnie przesuń przy użyciu wielu opcji wdrażania na platformie Azure.

Każda z poniższych instruktażach używa nowych przykładowych eShopLegacy i eShopModernizing aplikacji, które są dostępne w usłudze GitHub w <https://github.com/dotnet-architecture/eShopModernizing>.

- **Przewodnik po przykładzie eShop starsze aplikacje (aplikacje linii bazowej w celu zmodernizowania)**

- **Konteneryzowanie istniejących aplikacji sieci web platformy ASP.NET (WebForms i MVC) przy użyciu kontenerów Windows**

- **Konteneryzowanie istniejącej usług WCF (aplikacje N-warstwowej) za pomocą kontenerów Windows**

- **Wdrażanie aplikacji opartych na kontenerach Windows na maszynach wirtualnych platformy Azure**

- **Wdrażanie aplikacji opartych na kontenerach Windows do rozwiązania Kubernetes w usłudze Azure Container Service**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Przewodnik 1: Przewodnik po przykładzie eShop starszych aplikacji

### <a name="technical-walkthrough-availability"></a>Dostępność technicznym

Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:

[wskazówki dotyczące witryny typu wiki eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Omówienie

W tym przewodniku możesz eksplorować wstępnej implementacji trzy próbki starszych aplikacji. Pierwsze dwie przykładowe aplikacje sieci web mają monolityczne architektury i zostały utworzone za pomocą klasycznego programu ASP.NET. Jedna aplikacja opiera się na platformie ASP.NET 4.x MVC; druga aplikacja opiera się na formularzach sieci Web programu ASP.NET 4.x.
Trzeci aplikacja jest aplikacją 3-warstwowej aplikacji formularzy WinForms klienta i po stronie serwera [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) usługi.

Te aplikacje są dostępne pod adresem [repozytorium GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Cele

Głównym celem tego przewodnika jest po prostu zapoznać się z tych aplikacji i ich kodu i konfiguracji. Aplikacje można skonfigurować tak, aby wygenerować i użyć danych testowych, bez korzystania z bazy danych SQL do celów testowych. Ta opcjonalna konfiguracja opiera się na iniekcji zależności w sposób odłączony.

### <a name="scenario-1-aspnet-web-apps"></a>Scenariusz 1: Aplikacje sieci Web platformy ASP.NET

Na poniższym rysunku przedstawiono prosty scenariusz oryginalnego starsze aplikacje sieci web platformy ASP.NET.

![Architektura Prosty scenariusz oryginalnego starsze aplikacje sieci web platformy ASP.NET](./media/image5-1.png)

Z punktu widzenia domeny biznesowej obie aplikacje oferują tego samego katalogu funkcje zarządzania. Członkowie zespołu enterprise eShop użyć jej do wyświetlania i edytowania katalogu produktów.

Na kolejnej ilustracji przedstawiono zrzuty ekranu aplikacji początkowej.

![Aplikacje platformy ASP.NET MVC i formularzy sieci Web platformy ASP.NET (istniejącej starszych technologiach)](./media/image5-2.png)

Zależności w programie ASP.NET 4.x i jego wcześniejsze wersje, (zarówno dla platformy MVC i formularzy sieci Web) oznacza, że te aplikacje nie będą uruchamiane na platformie .NET Core, chyba że kod jest w pełni przepisany przy użyciu platformy ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scenariusz 2: Usługi WCF i aplikację kliencką WinForms (3-warstwowej aplikacji)

Na poniższym rysunku przedstawiono prosty scenariusz oryginalnego starszych aplikacji 3-warstwowej.

![Architektura Prosty scenariusz oryginalnego starszych aplikacji 3-warstwowej przy użyciu usługi WCF i aplikację kliencką WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Zalety

Korzyści wynikające z tego przewodnika są proste: Po prostu zapoznać się z kodem i początkowy aplikacji.

### <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:

- [Samouczek linii bazowej platformy ASP.NET MVC i formularzy sieci Web "starszych" aplikacji](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Samouczek na temat usługi WCF linii bazowej i aplikacja "starszych" (3-warstwowej) WinForms](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Przewodnik 2: Konteneryzowanie istniejącej aplikacji .NET za pomocą kontenerów Windows

### <a name="overview"></a>Omówienie

Korzystaj z kontenerów Windows, w celu wdrożenia istniejących aplikacji .NET, takich jak te oparte na WCF, MVC i formularzy sieci Web w środowisku produkcyjnym, programowania i środowisk testowych.

### <a name="goals"></a>Cele

Celem tego przewodnika jest, aby pokazać Ci kilka opcji konteneryzowania istniejącej aplikacji .NET Framework. Można:

- Konteneryzowanie aplikacji przy użyciu [Visual Studio 2017 r Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowsze wersje).

- Konteneryzowanie aplikacji, ręcznie dodając [pliku Dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie używając [interfejsu wiersza polecenia Docker](https://docs.docker.com/engine/reference/commandline/cli/).

- Konteneryzowanie aplikacji przy użyciu [Img2Docker](https://github.com/docker/communitytools-image2docker-win) narzędzia (narzędzie typu open-source docker).

Ten przewodnik koncentruje się na Visual Studio Tools 2017 podejścia platformy Docker, ale pozostałe dwie metody są podobne rozumieniu przy użyciu plików Dockerfile.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scenariusz 1: Konteneryzowanych aplikacji sieci web platformy ASP.NET

Na poniższym rysunku przedstawiono scenariusz konteneryzowanych eShop starszych internetowych aplikacji.

![Diagram architektury uproszczone kontenerowych nimi aplikacji ASP.NET w środowisku programistycznym](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scenariusz 2: Konteneryzowana Usługa WCF

Na poniższym rysunku przedstawiono scenariusz, w przypadku aplikacji 3-warstwowej przy użyciu konteneryzowana Usługa WCF.

![Uproszczony diagram architektury konteneryzowane usługi WCF w środowisku programistycznym](./media/image5-3.5.png)

### <a name="benefits"></a>Zalety

Istnieją zalety łączenia uruchamiania aplikacji monolitycznych w kontenerze. Najpierw należy utworzyć obraz dla aplikacji. Od tego momentu każde wdrożenie jest uruchamiane w tym samym środowisku. Każdy kontener korzysta z tej samej wersji systemu operacyjnego, ma tę samą wersję zależności zainstalowane, korzysta z tej samej wersji programu .NET framework i powstała przy użyciu tego samego procesu. Zasadniczo możesz kontrolować zależności aplikacji przy użyciu obrazu platformy Docker. Zależności są przesyłane przy użyciu aplikacji podczas wdrażania kontenerów.

Dodatkową korzyścią jest to, że deweloperzy mogą uruchomić aplikację w spójne środowisko, które są dostarczane przez kontenery Windows. Problemy, które są wyświetlane tylko w przypadku niektórych wersji mogą wykrył od razu, zamiast, dzięki czemu są ujawniane w środowisku tymczasowym czy produkcyjnym. Różnice w środowiskach programistycznych, które posługują się członkowie zespołu rozwoju znaczenia mniejsza, gdy aplikacje są uruchamiane w kontenerach.

Konteneryzowane aplikacje mają również płaski krzywej skalowalnego w poziomie. Konteneryzowanych aplikacji pozwalają na więcej aplikacji i wystąpień usługi (oparte na kontenerach) w maszynie Wirtualnej lub komputera fizycznego w porównaniu do regularnego acji dla poszczególnych komputerów. Przekłada się to wyższych gęstości, a mniej wymaganych zasobów, szczególnie w przypadku, gdy używasz koordynatorów, takich jak Kubernetes.

Konteneryzacji w sytuacjach, idealnym rozwiązaniem, nie wymaga wprowadzania żadnych zmian w kodzie aplikacji (C\#). W większości przypadków wystarczy Docker wdrożenia metadanych plików (pliki Dockerfile i narzędzia Docker Compose).

### <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:

- [Jak konteneryzowanie aplikacji sieci web .NET Framework za pomocą Windows kontenery i Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Dodawanie obsługi platformy Docker do usługi WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Przewodnik 3: Wdrażanie aplikacji opartych na kontenerach Windows na maszynach wirtualnych platformy Azure

### <a name="technical-walkthrough-availability"></a>Dostępność technicznym

Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Omówienie

Wdrażanie hosta platformy Docker na system Windows Server 2016 maszyny wirtualnej (VM) na platformie Azure umożliwia szybkie konfigurowanie środowisk projektowania/testów/wdrażanie przejściowe. Oferuje on również typowe miejscu dla testerów lub użytkownicy biznesowi sprawdzić poprawność aplikacji. Maszyny wirtualne również mogą być prawidłowe infrastruktury jako środowisk produkcyjnych usługi (IaaS).

### <a name="goals"></a>Cele

Celem tego przewodnika jest aby pokazać Ci kilka rozwiązań alternatywnych, do których masz podczas wdrażania kontenerów Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszy.

### <a name="scenarios"></a>Scenariusze

W tym przewodniku znajdują się kilku scenariuszy.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scenariusz A: Wdrażanie na Maszynie wirtualnej platformy Azure od deweloperów komputera za pośrednictwem połączenia aparat platformy Docker

![Wdrażanie na Maszynie wirtualnej platformy Azure od deweloperów komputera za pośrednictwem połączenia aparat platformy Docker](./media/image5-4.png)

**Rysunek 5-4.** Wdrażanie na Maszynie wirtualnej platformy Azure od deweloperów komputera za pośrednictwem połączenia aparat platformy Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scenariusz B: Wdrażanie na maszynie Wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker

![Wdrażanie na maszynie Wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker](./media/image5-5.png)

**Rysunek 5-5.** Wdrażanie na maszynie Wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scenariusz C: Wdrożyć Maszynę wirtualną platformy Azure z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure

![Wdrożyć Maszynę wirtualną platformy Azure z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure](./media/image5-6.png)

**Rysunek 5 – 6.** Wdrożyć Maszynę wirtualną platformy Azure z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure

### <a name="azure-vms-for-windows-containers"></a>Maszyny wirtualne platformy Azure dla kontenerów Windows

Maszyny wirtualne dla Windows kontenery usługi Azure maszyn wirtualnych opartych na systemie Windows Server 2016, Windows 10 lub nowszy, konfigurowanie zarówno z aparatem Docker. W większości przypadków systemu Windows Server 2016 jest używana w maszynach wirtualnych platformy Azure.

System Azure oferuje obecnie Maszynę wirtualną o nazwie **systemu Windows Server 2016 z kontenerami**. Korzystanie z tej maszyny Wirtualnej, do wypróbowania nowej funkcji kontenera z systemem Windows Server z systemu Windows Server Core lub Windows Nano Server. Kontener obrazów systemu operacyjnego są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z platformą Docker.

### <a name="benefits"></a>Zalety

Mimo, że kontenery Windows można wdrożyć do lokalnego systemu Windows Server 2016 maszyn wirtualnych, w przypadku wdrażania na platformie Azure, możesz uzyskać łatwiejszy sposób, aby rozpocząć pracę, przy użyciu gotowych do użycia kontener maszyn wirtualnych. Możesz także uzyskać wspólnej lokalizacji online, który jest dostępny dla testerów i automatyczne skalowalności za pomocą zestawów skalowania maszyn wirtualnych platformy Azure.

### <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Przewodnik po 4: Wdrażanie aplikacji opartych na kontenerach Windows Azure Container instances (ACI)

### <a name="technical-walkthrough-availability"></a>Dostępność technicznym

Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:

[Wdrażanie aplikacji w usłudze aci Uzyskaj (wystąpienia kontenera platformy Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Omówienie

[Usługa Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) jest najszybszym sposobem kontenerów środowiska dev/test/wdrażanie przejściowe, którym można wdrożyć z pojedynczego wystąpienia kontenerów.

### <a name="goals"></a>Cele

W tym przewodniku przedstawiono główne scenariusze wdrażania kontenerów Windows do usługi Azure Container Instances (ACI) i jak można wdrażać aplikacje eShopModernizing w usłudze ACI.

### <a name="scenarios"></a>Scenariusze

Może to być różnice dotyczące wdrażania aplikacji eShopModernizing w usłudze ACI, takie jak wdrożenie tylko jednej lub wszystkich aplikacji (aplikacji MVC, aplikacja formularzy sieci Web lub usługi WCF). W poniższym scenariuszu przedstawionym poniżej widać aplikacji ASP.NET MVC oraz kontener programu SQL Server, oba jest wdrażane jako kontenery w usłudze ACI (usługi Azure Container Instances).

![Wdrażanie usługi ACI z środowiska deweloperskiego](./media/image5-3.5.6.png)

### <a name="benefits"></a>Zalety

Usługa Azure Container Instances ułatwia tworzenie i zarządzanie nimi kontenerów platformy Docker na platformie Azure, bez konieczności aprowizowania maszyn wirtualnych lub stosowania usługi wyższego poziomu. Za pomocą usługi ACI można bezpośrednio wdrożyć kontener Windows na platformie Azure i ujawnisz go w Internecie przy użyciu w pełni kwalifikowaną nazwę domeny (FQDN) w ciągu kilku sekund (pod warunkiem, że masz gotowy obraz Windows kontenera w rejestrze Docker, takich jak usługi Docker Hub lub Azure Container Rejestr).

### <a name="considerations"></a>Uwagi

Wdrażanie kontenerów Windows przy użyciu albo pełny program .NET Framework / platformy ASP.NET lub program SQL Server do usługi Azure Container Instances (ACI) nie jest dość tak szybko, jak wdrażanie regularne hosta platformy Docker (np. Windows Server 2016 z kontenerami Windows), ponieważ obraz platformy Docker musi być pobrany (ściągnięty z rejestru platformy Docker), każdym razem, gdy i obraz kontenera SQL (15.1 GB) i obrazu kontenera platformy ASP.NET (13.9 GB) są znacznie dużych, jednak jest znacznie tańsze niż utrzymywania własnego hosta platformy docker (trwale online Windows Server 2016 z maszyną Wirtualną z kontenerów Windows na platformie Azure) nie, aby wspomnieć o całego programu orchestrator, takich jak Kubernetes w usłudze Azure (AKS) czyli, z drugiej strony, to dobry wybór dla wdrożeń produkcyjnych.

Jako podstawowy wniosek za pomocą usługi Azure Container Instances jest to opcja niezwykle atrakcyjne rozwiązanie dla scenariuszy deweloperskich lub testowych oraz dla potoków ciągłej integracji/ciągłego Dostarczania.

## <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Przewodnik po 5: Wdrażanie aplikacji opartych na kontenerach Windows do rozwiązania Kubernetes w usłudze Azure Container Service

### <a name="technical-walkthrough-availability"></a>Dostępność technicznym

Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Omówienie

Aplikacja, która opiera się na kontenery Windows szybko będą musieli używać platform, jeszcze bardziej odpływowi z maszyn wirtualnych IaaS. To jest potrzebna do łatwo osiągnąć wysoką skalowalność lepiej automatycznego skalowania i znaczne ulepszenia w zautomatyzowane wdrożenia oraz zarządzanie ich wersjami. Można osiągnąć te cele przy użyciu koordynatora [Kubernetes](https://kubernetes.io/), która jest dostępna w [usług Azure Container Service](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Cele

Celem tego przewodnika jest Dowiedz się, jak wdrażanie aplikacji dla komputerów z systemem Windows kontenera w usłudze Kubernetes (nazywane również *K8s*) w usłudze Azure Container Service. Wdrażanie od zera rozwiązania Kubernetes jest procesem dwuetapowym:

1. Wdrażanie klastra Kubernetes w usłudze Azure Container Service.

2. Wdrażanie aplikacji i powiązanych zasobów do klastra Kubernetes.

### <a name="scenarios"></a>Scenariusze

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scenariusz A: Wdróż bezpośrednio w klastrze Kubernetes w środowisku deweloperskim

![Wdróż bezpośrednio w klastrze Kubernetes z poziomu środowiska projektowego](./media/image5-7.png)

**Rysunek 5 – 7.** Wdróż bezpośrednio w klastrze Kubernetes z poziomu środowiska projektowego

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scenariusz B: Wdrażanie klastra Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure

![Wdrażanie klastra Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure](./media/image5-8.png)

**Rysunek 5 – 8.** Wdrażanie klastra Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure

### <a name="benefits"></a>Zalety

Istnieje wiele korzyści dla wdrażania w klastrze na platformie Kubernetes. Największa zaleta jest znaczny środowisko gotowe do produkcji, w którym można skalować w poziomie aplikacji, w oparciu o liczbę wystąpień kontenera, mają być używane (wewnętrzny skalowalności istniejących węzłów), a na podstawie liczby węzłów lub maszyn wirtualnych w (klastra globalną skalowalność klastra).

Usługa Azure Container Service optymalizuje popularnych narzędzi typu open source i technologii, pod kątem platformy Azure. Uzyskujesz otwarte rozwiązanie, przenośność, kontenerów i konfiguracji aplikacji. Wybierasz rozmiar, liczbę hostów i orchestrator narzędzia Container Service zajmuje się całą resztą.

Przy użyciu rozwiązania Kubernetes deweloperzy mogą postępu z myśleć o fizycznych i maszyn wirtualnych do planowania infrastruktury skoncentrowane na kontener, który ułatwia następujące funkcje, między innymi:

- Aplikacje oparte na wielu kontenerów

- Replikowanie wystąpień kontenera oraz skalowanie automatyczne w poziomie

- Nazewnictwo i odnajdywania (na przykład wewnętrznego serwera DNS)

- Równoważenie obciążenia

- Aktualizacje stopniowe

- Dystrybucja wpisów tajnych

- Kontrole kondycji aplikacji

## <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Przewodnik 6: Wdrażanie aplikacji opartych na kontenerach Windows w usłudze Azure App Service dla kontenerów

### <a name="technical-walkthrough-availability"></a>Dostępność technicznym

Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Omówienie

Prostej aplikacji konteneryzowanych za pomocą kontenerów Windows można łatwo wdrożyć w usłudze Azure App Service dla kontenerów. Jest to zalecane podejście do większości aplikacji opartych na kontenerach Windows.

### <a name="goals"></a>Cele

Celem tego przewodnika jest, aby dowiedzieć się, jak wdrożyć aplikację kontenera Windows oparte na usłudze Azure App Service dla kontenerów z rejestru (usługi Docker Hub lub Azure Container Registry).

### <a name="scenario"></a>Scenariusz

![Wdrażanie aplikacji opartych na kontenerach Windows w usłudze Azure App Service dla kontenerów](./media/image5-11.png)

### <a name="benefits"></a>Zalety

Wdrażanie w usłudze Azure App Service dla kontenerów oferuje zalety kontenery skojarzone z korzyściami PaaS w usłudze Azure App Service. Usługa app service można łatwo skalować w pionie i w poziomie, a następnie można skonfigurować do automatycznego skalowania, aby spełnić zgłaszanych. Aktualizacje mogą być wykonywane bez przestojów i łatwo konfigurować również konfiguracja ciągłego wdrażania z rejestru.

## <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Poprzednie](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
> [dalej](conclusions.md)
