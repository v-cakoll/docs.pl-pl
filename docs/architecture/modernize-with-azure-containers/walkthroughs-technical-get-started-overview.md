---
title: Omówienie przewodników i wprowadzającej dokumentacji technicznej
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Przewodniki i przegląd wprowadzenie techniczne
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660885"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Omówienie przewodników i wprowadzającej dokumentacji technicznej

Aby ograniczyć rozmiar tej książki elektronicznej, w repozytorium GitHub udostępniono dodatkową dokumentację techniczną i pełne instruktaże. Serie online przewodników, które opisano w tym rozdziale, obejmują konfigurację krok po kroku dla wielu środowisk opartych na kontenerach systemu Windows oraz wdrażanie na platformie Azure.

W poniższych sekcjach wyjaśniono, czym są poszczególne instruktaże, ich cele i wizja wysokiego poziomu, a także przedstawiono diagram zadań, które są związane. Instruktaże można uzyskać w witrynie typu wiki repozytorium GitHub *eShopModernizing* Apps w witrynie <https://github.com/dotnet-architecture/eShopModernizing/wiki>.

## <a name="technical-walkthrough-list"></a>Lista przewodników technicznych

Poniższe przewodniki Get-Started zapewniają spójne i kompleksowe wskazówki techniczne dotyczące przykładowych aplikacji, które można dołączać i przenosić przy użyciu kontenerów, a następnie przełączać się za pomocą wielu opcji wdrożenia na platformie Azure.

W każdym z poniższych instruktażów są wykorzystywane nowe przykładowe aplikacje eShopLegacy i eShopModernizing, które są dostępne w witrynie GitHub <https://github.com/dotnet-architecture/eShopModernizing>w witrynie.

- **Przewodnik po eShop starszych aplikacji (aplikacje podstawowe do modernizacji)**

- **Konteneryzowanie istniejące aplikacje sieci Web ASP.NET (WebForms & MVC) z kontenerami systemu Windows**

- **Konteneryzowanie istniejące usługi WCF (aplikacje N-warstwowe) za pomocą kontenerów systemu Windows**

- **Wdrażanie aplikacji opartych na kontenerach systemu Windows na maszynach wirtualnych platformy Azure**

- **Wdróż aplikacje oparte na kontenerach systemu Windows w usłudze Kubernetes w Azure Container Service**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Przewodnik 1: Przewodnik po starszych aplikacjach eShop

### <a name="technical-walkthrough-availability"></a>Dostępność przewodnika technicznego

Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub:

[Wskazówki dotyczące eShopModernizing wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Omówienie

W tym instruktażu można poznać początkową implementację trzech przykładowych starszych aplikacji. Pierwsze dwie przykładowe aplikacje internetowe mają niemonolityczną architekturę i zostały utworzone przy użyciu klasycznego ASP.NET. Jedna aplikacja jest oparta na ASP.NET 4. x MVC; Druga aplikacja jest oparta na formularzach sieci Web ASP.NET 4. x.
Trzecia aplikacja to 3-warstwowa aplikacja, która składa się z aplikacji WinForms klienta i usługi Windows Communication Foundation po stronie serwera [(WCF)](../../framework/wcf/whats-wcf.md) .

Wszystkie te aplikacje są dostępne w [repozytorium GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Cele

Głównym celem tego przewodnika jest po prostu zaznajomienie się z tymi aplikacjami oraz ich kodem i konfiguracją. Aplikacje można skonfigurować w taki sposób, aby generowały i używały danych makiety bez używania bazy danych SQL do celów testowych. Ta opcjonalna konfiguracja jest oparta na iniekcji zależności w oddzielnym sposobie.

### <a name="scenario-1-aspnet-web-apps"></a>Scenariusz 1: ASP.NET aplikacje sieci Web

Na poniższym rysunku przedstawiono prosty scenariusz oryginalnych starszych aplikacji sieci Web ASP.NET.

![Prosty scenariusz architektury dla oryginalnych starszych aplikacji sieci Web ASP.NET](./media/image5-1.png)

W perspektywie domeny biznesowej obie aplikacje oferują te same funkcje zarządzania katalogami. Członkowie zespołu eShop Enterprise używają aplikacji do wyświetlania i edytowania wykazu produktów.

Następny rysunek przedstawia początkowe zrzuty ekranu aplikacji.

![Aplikacje ASP.NET MVC i ASP.NET Web Forms (istniejące/starsze technologie)](./media/image5-2.png)

Zależności w ASP.NET 4. x lub starszych wersjach (w przypadku wersji MVC lub for Web Forms) oznacza, że te aplikacje nie będą działać w programie .NET Core, chyba że kod jest w pełni zapisany przy użyciu ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scenariusz 2: Usługa WCF i aplikacja kliencka WinForms (aplikacja 3-warstwowa)

Na poniższej ilustracji przedstawiono prosty scenariusz oryginalnej starszej aplikacji 3-warstwowej.

![Prosty scenariusz architektury oryginalnej starszej aplikacji 3-warstwowej z usługą WCF i aplikacją kliencką WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Zalety

Zalety tego instruktażu są proste: Zapoznaj się z kodem i początkowymi aplikacjami.

### <a name="next-steps"></a>Następne kroki

Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:

- [Przewodnik po aplikacjach podstawowych ASP.NET MVC i Web Forms "starsze"](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Samouczek dotyczący podstawowej usługi WCF i WinForms (3-warstwowej) "starszej" aplikacji](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Przewodnik 2: Konteneryzowanie istniejące aplikacje .NET przy użyciu kontenerów systemu Windows

### <a name="overview"></a>Omówienie

Użyj kontenerów systemu Windows, aby usprawnić wdrażanie istniejących aplikacji platformy .NET, takich jak te oparte na technologii MVC, Web Forms lub WCF, w środowiskach produkcyjnych, programistycznych i testowych.

### <a name="goals"></a>Cele

Celem tego instruktażu jest wyświetlenie kilku opcji konteneryzowania istniejącej aplikacji .NET Framework. Można:

- Konteneryzowanie aplikację przy użyciu [narzędzi programu Visual studio 2017 dla platformy Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowsze wersje).

- Konteneryzowanie aplikację przez ręczne dodanie [pliku dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie za pomocą [interfejsu wiersza polecenia platformy Docker](https://docs.docker.com/engine/reference/commandline/cli/).

- Konteneryzowanie aplikację przy użyciu narzędzia [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (narzędzia Open Source z platformy Docker).

Ten przewodnik koncentruje się na rozdziałach Visual Studio 2017 Tools for Docker, ale inne dwa podejścia są dość podobne w odniesieniu do używania wieloetapowe dockerfile.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scenariusz 1: Kontenery ASP.NET Web Apps

Na poniższej ilustracji przedstawiono scenariusz dla aplikacji kontenerów eShop starsze aplikacje sieci Web.

![Uproszczony diagram architektury aplikacji ASP.NET dla kontenerów w środowisku programistycznym](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scenariusz 2: Kontener usługi WCF

Na poniższej ilustracji przedstawiono scenariusz dla aplikacji 3-warstwowej z użyciem kontenera usługi WCF.

![Uproszczony diagram architektury usługi WCF w kontenerze w środowisku programistycznym](./media/image5-3.5.png)

### <a name="benefits"></a>Zalety

Istnieją zalety uruchamiania aplikacji monolitycznej w kontenerze. Najpierw utworzysz obraz dla aplikacji. Od tego momentu każde wdrożenie jest uruchamiane w tym samym środowisku. Każdy kontener używa tej samej wersji systemu operacyjnego, ma taką samą wersję zależności, korzysta z tej samej wersji programu .NET Framework i został skompilowany przy użyciu tego samego procesu. W zasadzie można kontrolować zależności aplikacji przy użyciu obrazu platformy Docker. Zależności są przesyłane wraz z aplikacją podczas wdrażania kontenerów.

Dodatkową korzyścią jest to, że deweloperzy mogą uruchamiać aplikację w spójnym środowisku dostarczanym przez kontenery systemu Windows. Problemy, które pojawiają się tylko w niektórych wersjach, można natychmiast wycofać, zamiast obsłużyć w środowisku przejściowym lub produkcyjnym. Różnice w środowiskach deweloperskich używanych przez członków zespołu deweloperskiego są mniejsze, gdy aplikacje działają w kontenerach.

Aplikacje kontenerowe mają również krzywą skalowania w poziomie Flatter. Aplikacje kontenerowe umożliwiają korzystanie z większej liczby wystąpień aplikacji i usług (opartych na kontenerach) w maszynie wirtualnej lub na komputerze fizycznym w porównaniu do zwykłych wdrożeń aplikacji na maszynę. Powoduje to przetłumaczenie na wyższą gęstość i mniejszą ilość wymaganych zasobów, zwłaszcza w przypadku korzystania z programu Orchestrator, takiego jak Kubernetes.

Kontenerach w idealnych sytuacjach nie wymaga wprowadzania żadnych zmian w kodzie aplikacji (C\#). W większości scenariuszy wymagane są tylko pliki metadanych wdrożenia platformy Docker (pliki wieloetapowe dockerfile i Docker Compose).

### <a name="next-steps"></a>Następne kroki

Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:

- [Jak konteneryzowanie aplikacje sieci Web .NET Framework przy użyciu kontenerów systemu Windows i platformy Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Dodawanie obsługi platformy Docker do usługi WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Przewodnik 3: Wdrażanie aplikacji opartych na kontenerach systemu Windows na maszynach wirtualnych platformy Azure

### <a name="technical-walkthrough-availability"></a>Dostępność przewodnika technicznego

Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Omówienie

Wdrożenie na hoście Docker na maszynie wirtualnej z systemem Windows Server 2016 (VM) na platformie Azure pozwala szybko skonfigurować środowisko deweloperskie/testowe/przejściowe. Zapewnia również typowe miejsce dla testerów lub użytkowników firmowych w celu zweryfikowania aplikacji. Maszyny wirtualne mogą również być prawidłowymi środowiskami produkcyjnymi infrastruktury jako usługi (IaaS).

### <a name="goals"></a>Cele

Celem tego przewodnika jest przedstawienie wielu alternatyw, które są używane podczas wdrażania kontenerów systemu Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszym.

### <a name="scenarios"></a>Scenariusze

W tym instruktażu omówiono kilka scenariuszy.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scenariusz A: Wdrażanie na maszynie wirtualnej platformy Azure z komputera deweloperskiego za pośrednictwem połączenia aparatu platformy Docker

![Wdrażanie na maszynie wirtualnej platformy Azure z komputera deweloperskiego za pośrednictwem połączenia aparatu platformy Docker](./media/image5-4.png)

**Rysunek 5-4.** Wdrażanie na maszynie wirtualnej platformy Azure z komputera deweloperskiego za pośrednictwem połączenia aparatu platformy Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scenariusz B: Wdrażanie na maszynie wirtualnej platformy Azure przy użyciu rejestru platformy Docker

![Wdrażanie na maszynie wirtualnej platformy Azure przy użyciu rejestru platformy Docker](./media/image5-5.png)

**Rysunek 5-5.** Wdrażanie na maszynie wirtualnej platformy Azure przy użyciu rejestru platformy Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scenariusz C: Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services

![Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services](./media/image5-6.png)

**Rysunek 5-6.** Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services

### <a name="azure-vms-for-windows-containers"></a>Maszyny wirtualne platformy Azure dla kontenerów systemu Windows

Maszyny wirtualne platformy Azure dla kontenerów systemu Windows są maszynami wirtualnymi opartymi na systemie Windows Server 2016, Windows 10 lub nowszym, zarówno z skonfigurowanym aparatem platformy Docker. W większości przypadków system Windows Server 2016 jest używany na maszynach wirtualnych platformy Azure.

Platforma Azure udostępnia teraz maszynę wirtualną o nazwie **Windows Server 2016 z kontenerami**. Za pomocą tej maszyny wirtualnej można wypróbować nową funkcję kontenera systemu Windows Server z systemem Windows Server Core lub Windows nano Server. Obrazy systemu operacyjnego kontenera są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z platformą Docker.

### <a name="benefits"></a>Zalety

Chociaż kontenery systemu Windows można wdrażać na lokalnych maszynach wirtualnych z systemem Windows Server 2016, podczas wdrażania na platformie Azure można łatwiej rozpocząć pracę z gotowymi do użycia maszyn wirtualnych kontenerów systemu Windows Server. Możesz również uzyskać wspólną lokalizację online dostępną dla testerów oraz automatyczną skalowalność za pomocą zestawów skalowania maszyn wirtualnych platformy Azure.

### <a name="next-steps"></a>Następne kroki

Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Przewodnik 4: Wdrażanie aplikacji opartych na kontenerach systemu Windows w celu Azure Container Instances (ACI)

### <a name="technical-walkthrough-availability"></a>Dostępność przewodnika technicznego

Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub:

[Wdrażanie aplikacji w usłudze ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Omówienie

[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) to najszybszy sposób tworzenia kontenerów w środowisku deweloperskim/testowym/przejściowym, w którym można wdrożyć pojedyncze wystąpienia kontenerów.

### <a name="goals"></a>Cele

W tym instruktażu przedstawiono główne scenariusze wdrażania kontenerów systemu Windows w programie Azure Container Instances (ACI) oraz sposobu wdrażania aplikacji eShopModernizing w programie ACI.

### <a name="scenarios"></a>Scenariusze

Mogą istnieć różne odmiany dotyczące wdrażania aplikacji eShopModernizing w programie ACI, takie jak wdrażanie tylko jednej lub wszystkich aplikacji (aplikacja MVC, WebForms lub usługa WCF). W poniższym scenariuszu widocznym poniżej można zobaczyć aplikację ASP.NET MVC i kontener SQL Server obu wdrożonych jako kontenery w ACI (Azure Container Instances).

![Wdrażanie w programie ACI z poziomu środowiska programistycznego](./media/image5-3.5.6.png)

### <a name="benefits"></a>Zalety

Azure Container Instances ułatwia tworzenie kontenerów platformy Docker na platformie Azure i zarządzanie nimi bez konieczności aprowizacji maszyn wirtualnych ani wdrażania usług wyższego poziomu. Za pomocą ACI można bezpośrednio wdrożyć kontener systemu Windows na platformie Azure i uwidocznić go w Internecie za pomocą w pełni kwalifikowanej nazwy domeny (FQDN) w ciągu kilku sekund (pod warunkiem, że obraz kontenera systemu Windows jest gotowy do użycia w rejestrze Docker, np. w usłudze Docker Hub lub kontenera platformy Azure) Rejestr).

### <a name="considerations"></a>Uwagi

Wdrażanie kontenerów systemu Windows z pełnymi .NET Framework/ASP.NET lub SQL Server do Azure Container Instances (ACI) nie jest równie szybkie, jak wdrażanie na zwykłych hostach platformy Docker (na przykład w przypadku systemu Windows Server 2016 z kontenerami systemu Windows), ponieważ obraz platformy Docker musi być pobrane (pobierane z rejestru platformy Docker) za każdym razem, gdy rozmiar obrazu kontenera SQL (15,1 GB) i obraz kontenera ASP.NET (13,9 GB) są znacznie duże, ale jest znacznie tańszy niż utrzymywanie własnego hosta platformy Docker (na stałe w wierszu) System Windows Server 2016 z maszyną wirtualną z kontenerami systemu Windows na platformie Azure nie oznacza całego programu Orchestrator, takiego jak Kubernetes na platformie Azure (AKS), czyli z drugiej strony, doskonały wybór dla wdrożeń produkcyjnych.

Jako główne rozwiązanie przy użyciu Azure Container Instances jest bardzo atrakcyjną opcją dla scenariuszy tworzenia i testowania oraz dla potoków ciągłej integracji/ciągłego wdrażania.

## <a name="next-steps"></a>Następne kroki

Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Przewodnik 5: Wdróż aplikacje oparte na kontenerach systemu Windows w usłudze Kubernetes w Azure Container Service

### <a name="technical-walkthrough-availability"></a>Dostępność przewodnika technicznego

Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Omówienie

Aplikacja, która jest oparta na kontenerach systemu Windows, będzie szybko potrzebować do użycia Platform, a nawet dalej z maszyn wirtualnych IaaS. Jest to konieczne w celu łatwego osiągnięcia wysokiej skalowalności i lepszej automatycznej skalowalności oraz znaczących ulepszeń zautomatyzowanych wdrożeń i przechowywania wersji. Cele te można osiągnąć przy użyciu [Kubernetes](https://kubernetes.io/)programu Orchestrator, dostępnego w usłudze [Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Cele

Celem tego instruktażu jest nauczenie się, jak wdrożyć aplikację opartą na kontenerach systemu Windows w usłudze Kubernetes (nazywanej również *K8s*) w Azure Container Service. Wdrażanie do Kubernetes od podstaw jest procesem dwuetapowym:

1. Wdróż klaster Kubernetes do Azure Container Service.

2. Wdróż aplikację i powiązane zasoby w klastrze Kubernetes.

### <a name="scenarios"></a>Scenariusze

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scenariusz A: Wdróż bezpośrednio w klastrze Kubernetes z poziomu środowiska deweloperskiego

![Wdrażanie bezpośrednio w klastrze Kubernetes z poziomu środowiska deweloperskiego](./media/image5-7.png)

**Rysunek 5-7.** Wdrażanie bezpośrednio w klastrze Kubernetes z poziomu środowiska deweloperskiego

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scenariusz B: Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services

![Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services](./media/image5-8.png)

**Rysunek 5-8.** Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services

### <a name="benefits"></a>Zalety

Wdrożenie w klastrze w programie Kubernetes ma wiele zalet. Największą korzyścią jest to, że możesz uzyskać gotowe do użycia środowisko produkcyjne, w którym można skalować aplikację na podstawie liczby wystąpień kontenerów, które mają być używane (skalowalność wewnętrzna w istniejących węzłach) i na podstawie liczby węzłów lub maszyn wirtualnych w klastrze ( globalna skalowalność klastra).

Azure Container Service optymalizuje popularne narzędzia i technologie "open source" przeznaczone dla platformy Azure. Uzyskasz otwarte rozwiązanie, które oferuje przenośność dla kontenerów i konfiguracji aplikacji. Wybierasz rozmiar, liczbę hostów i narzędzie Orchestrator Tools-Container Service obsługuje wszystko inne.

Dzięki Kubernetes deweloperzy mogą postępować nad maszynami fizycznymi i wirtualnymi, aby zaplanować infrastrukturę skoncentrowaną na kontenerach, która ułatwia między innymi następujące możliwości:

- Aplikacje oparte na wielu kontenerach

- Replikowanie wystąpień kontenera i skalowanie w poziomie

- Nazewnictwo i odnajdywanie (na przykład wewnętrzny serwer DNS)

- Równoważenie obciążenia

- Aktualizacje stopniowe

- Dystrybuowanie wpisów tajnych

- Kontrole kondycji aplikacji

## <a name="next-steps"></a>Następne kroki

Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Przewodnik 6: Wdrażanie aplikacji opartych na kontenerach systemu Windows w celu Azure App Service dla kontenerów

### <a name="technical-walkthrough-availability"></a>Dostępność przewodnika technicznego

Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Omówienie

Prostą aplikację kontenerową korzystającą z kontenerów systemu Windows można łatwo wdrożyć do Azure App Service dla kontenerów. Jest to zalecane podejście dla większości aplikacji opartych na kontenerach systemu Windows.

### <a name="goals"></a>Cele

Celem tego instruktażu jest nauczenie się, jak wdrożyć aplikację opartą na kontenerach systemu Windows w celu Azure App Service kontenerów z rejestru (centrum Docker lub Azure Container Registry).

### <a name="scenario"></a>Scenariusz

![Wdrażanie aplikacji opartej na kontenerze systemu Windows w celu Azure App Service dla kontenerów](./media/image5-11.png)

### <a name="benefits"></a>Zalety

Wdrożenie do Azure App Service for Containers oferuje zalety kontenerów sparowanych z zaletami Azure App Service. Usługa App Service może być łatwo skalowana w pionie i w poziomie i można ją skonfigurować do automatycznego skalowania w celu spełnienia zmienionych wymagań. Aktualizacje mogą być przeprowadzane z zerowym przestojem, a Konfiguracja ciągłego wdrażania z rejestru jest również łatwa do skonfigurowania.

## <a name="next-steps"></a>Następne kroki

Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Poprzedni](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)Następny
> [](conclusions.md) <!-- Next Chapter -->
