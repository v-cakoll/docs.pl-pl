---
title: Omówienie przewodników i wprowadzającej dokumentacji technicznej
description: Modernizacja istniejących aplikacji .NET za pomocą usługi Azure Cloud i kontenerów systemu Windows | Instruktaży i przegląd początku technicznego
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69660885"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Omówienie przewodników i wprowadzającej dokumentacji technicznej

Aby ograniczyć rozmiar tej e-booka, w repozytorium Usługi GitHub udostępniono dodatkową dokumentację techniczną i pełne rozwiązania. Seria instruktażu online opisana w tym rozdziale obejmuje konfigurację krok po kroku wielu środowisk opartych na kontenerach systemu Windows i wdrażanie na platformie Azure.

W poniższych sekcjach wyjaśniono, o co chodzi w każdym instruktażu, jego celach i wizji wysokiego poziomu, a także przedstawiono diagram zadań, które są zaangażowane. Możesz uzyskać same instruktaże w *eShopModernizing* aplikacji GitHub repo wiki w . <https://github.com/dotnet-architecture/eShopModernizing/wiki>

## <a name="technical-walkthrough-list"></a>Lista instruktażów technicznych

Poniższe wskazówki dotyczące początku zawierają spójne i kompleksowe wskazówki techniczne dotyczące przykładowych aplikacji, które można podnieść i zmienić przy użyciu kontenerów, a następnie przenieść przy użyciu wielu opcji wdrażania na platformie Azure.

Każdy z poniższych instruktaże używa nowego przykładowego eShopLegacy i eShopModernizing aplikacji, które są dostępne w GitHub w . <https://github.com/dotnet-architecture/eShopModernizing>

- **Przewodnik po starszych aplikacjach sklepu eShop (aplikacje bazowe do modernizacji)**

- **Konteneryzuj istniejące ASP.NET aplikacje sieci Web (WebForms & MVC) za pomocą kontenerów systemu Windows**

- **Konteneryzuj istniejące usługi WCF (aplikacje n-warstwowe) za pomocą kontenerów systemu Windows**

- **Wdrażanie aplikacji opartej na kontenerach systemu Windows na maszynach wirtualnych platformy Azure**

- **Wdrażanie aplikacji opartych na kontenerach systemu Windows w programie Kubernetes w usłudze Azure Container Service**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Przewodnik 1: Zwiedzanie starszych aplikacji sklepu eShop

### <a name="technical-walkthrough-availability"></a>Dostępność instruktażetechnicznym

Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:

[eShopModernizing wiki instruktaże](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Omówienie

W tym instruktażem można eksplorować wstępną implementację trzech przykładowych starszych aplikacji. Pierwsze dwie przykładowe aplikacje internetowe mają monolityczną architekturę i zostały utworzone przy użyciu klasycznych ASP.NET. Jedna aplikacja jest oparta na ASP.NET 4.x MVC; druga aplikacja jest oparta na ASP.NET 4.x Web Forms.
Trzecia aplikacja to aplikacja 3-warstwowa skomponowana przez aplikację WinForms klienta i usługę [WCF (Windows Communication Foundation)](../../framework/wcf/whats-wcf.md) po stronie serwera.

Wszystkie te aplikacje są dostępne w [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Cele

Głównym celem tego instruktażu jest po prostu zapoznanie się z tymi aplikacjami oraz z ich kodem i konfiguracją. Aplikacje można skonfigurować tak, aby generowały i używały makiet danych bez używania bazy danych SQL do celów testowych. Ta opcjonalna konfiguracja jest oparta na iniekcji zależności, w sposób niesparzony.

### <a name="scenario-1-aspnet-web-apps"></a>Scenariusz 1: ASP.NET aplikacje sieci Web

Poniższy rysunek przedstawia prosty scenariusz oryginalnego starszego ASP.NET aplikacji sieci Web.

![Prosty scenariusz architektury oryginalnej starszej ASP.NET aplikacji sieci Web](./media/image5-1.png)

Z punktu widzenia domeny biznesowej obie aplikacje oferują te same funkcje zarządzania katalogami. Członkowie zespołu przedsiębiorstwa sklepu internetowego będą używać aplikacji do wyświetlania i edytowania katalogu produktów.

Na następnej ilustracji przedstawiono początkowe zrzuty ekranu aplikacji.

![ASP.NET mvc i ASP.NET web forms (istniejące/starsze technologie)](./media/image5-2.png)

Zależności w ASP.NET wersji 4.x lub wcześniejszych (dla MVC lub dla formularzy sieci Web) oznacza, że te aplikacje nie będą działać na .NET Core, chyba że kod jest w pełni przepisany przy użyciu ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scenariusz 2: Usługa WCF i aplikacja kliencz WinForms (aplikacja 3-warstwowa)

Poniższy rysunek przedstawia prosty scenariusz oryginalnej 3-warstwowej starszej aplikacji.

![Prosty scenariusz architektury oryginalnej starszej aplikacji 3-warstwowej z usługą WCF i aplikacją kliencką WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Korzyści

Zalety tego instruktażu są proste: Wystarczy zapoznać się z kodem i początkowymi aplikacjami.

### <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:

- [Przewodnik po podstawowych ASP.NET MVC i starszych aplikacji formularzy sieci Web](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Przewodnik po podstawowej usłudze WCF i aplikacji "legacy" WinForms (3-warstwowej)](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Instruktaż 2: Konteneryzuj istniejące aplikacje .NET za pomocą kontenerów systemu Windows

### <a name="overview"></a>Omówienie

Użyj kontenerów systemu Windows, aby usprawnić wdrażanie istniejących aplikacji .NET, takich jak te oparte na MVC, Web Forms lub WCF, w środowiskach produkcyjnych, deweloperskich i testowych.

### <a name="goals"></a>Cele

Celem tego instruktażejest pokazać kilka opcji konteneryzacji istniejącej aplikacji .NET Framework. Możesz:

- Konteneryzuj aplikację przy użyciu [programu Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowsze wersje).

- Konteneryzuj aplikację ręcznie dodając [plik Dockerfile,](https://docs.docker.com/engine/reference/builder/)a następnie używając [interfejsu cli](https://docs.docker.com/engine/reference/commandline/cli/)platformy Docker .

- Konteneryzuj aplikację za pomocą narzędzia [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (narzędzia typu open source z platformy Docker).

Ten instruktaż koncentruje się na visual studio 2017 Narzędzia dla platformy Docker podejście, ale pozostałe dwa podejścia są dość podobne w odniesieniu do korzystania z plików dockerfiles.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scenariusz 1: konteneryzowane ASP.NET aplikacje sieci Web

Poniższy rysunek przedstawia scenariusz konteneryzowanych starszych aplikacji sieci web sklepu eShop.

![Diagram architektury uproszczonej konteneryzowanych aplikacji ASP.NET w środowisku programistycznym](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scenariusz 2: Konteneryzowana usługa WCF

Poniższy rysunek przedstawia scenariusz dla aplikacji 3-warstwowej z konteneryzowaną usługą WCF.

![Diagram architektury uproszczonej konteneryzowanej usługi WCF w środowisku programistycznym](./media/image5-3.5.png)

### <a name="benefits"></a>Korzyści

Istnieją zalety uruchamiania aplikacji monolityczne w kontenerze. Najpierw należy utworzyć obraz dla aplikacji. Od tego momentu każde wdrożenie jest uruchamiane w tym samym środowisku. Każdy kontener używa tej samej wersji systemu operacyjnego, ma tę samą wersję zależności zainstalowane, używa tej samej wersji platformy .NET i jest zbudowany przy użyciu tego samego procesu. Zasadniczo można kontrolować zależności aplikacji przy użyciu obrazu platformy Docker. Zależności podróży z aplikacją podczas wdrażania kontenerów.

Dodatkową korzyścią jest to, że deweloperzy mogą uruchamiać aplikację w spójnym środowisku, które jest dostarczane przez kontenery systemu Windows. Problemy, które pojawiają się tylko w niektórych wersjach można wykryć natychmiast, zamiast pojawiać się w środowisku przejściowym lub produkcyjnym. Różnice w środowiskach programistycznych używanych przez członków zespołu programistycznego mają mniejsze znaczenie, gdy aplikacje są uruchamiane w kontenerach.

Konteneryzowane aplikacje mają również bardziej płaską krzywą skalowania w skali. Konteneryzowane aplikacje umożliwiają więcej wystąpień aplikacji i usługi (na podstawie kontenerów) na maszynie wirtualnej lub komputerze fizycznym w porównaniu z regularnymi wdrożeniami aplikacji na komputerze. Przekłada się to na większą gęstość i mniej wymaganych zasobów, zwłaszcza w przypadku korzystania z koordynatorów, takich jak Kubernetes.

Konteneryzacja, w idealnych sytuacjach, nie wymaga wprowadzania\#żadnych zmian w kodzie aplikacji (C). W większości scenariuszy wystarczy pliki metadanych wdrażania platformy Docker (pliki dockerfiles i pliki docker Compose).

### <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:

- [Jak konteneryzować aplikacje sieci web .NET Framework za pomocą kontenerów systemu Windows i platformy Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Dodawanie obsługi platformy Docker do usługi WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Instruktaż 3: Wdrażanie aplikacji opartej na kontenerach systemu Windows na maszynach wirtualnych platformy Azure

### <a name="technical-walkthrough-availability"></a>Dostępność instruktażetechnicznym

Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Omówienie

Wdrażanie na hoście platformy Docker na maszynie wirtualnej (VM) systemu Windows Server 2016 na platformie Azure umożliwia szybkie konfigurowanie środowisk deweloperskich/testowych/przemieszczania. Zapewnia również wspólne miejsce dla testerów lub użytkowników biznesowych do sprawdzania poprawności aplikacji. Maszyny wirtualne mogą być również prawidłową infrastrukturą jako środowiskami produkcyjnymi usługi (IaaS).

### <a name="goals"></a>Cele

Celem tego instruktażenia jest pokazanie wielu alternatyw, które masz podczas wdrażania kontenerów systemu Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszych wersjach.

### <a name="scenarios"></a>Scenariusze

W tym instruktacie uwzględniono kilka scenariuszy.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scenariusz A: Wdrażanie na maszynie wirtualnej platformy Azure z komputera dewelopera za pośrednictwem połączenia aparatu platformy Docker

![Wdrażanie na maszynie wirtualnej platformy Azure z komputera dewelopera za pośrednictwem połączenia aparatu platformy Docker](./media/image5-4.png)

**Rysunek 5-4.** Wdrażanie na maszynie wirtualnej platformy Azure z komputera dewelopera za pośrednictwem połączenia aparatu platformy Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scenariusz B: Wdrażanie na maszynie wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker

![Wdrażanie na maszynie wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker](./media/image5-5.png)

**Rysunek 5-5.** Wdrażanie na maszynie wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scenariusz C: Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services

![Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services](./media/image5-6.png)

**Rysunek 5-6.** Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services

### <a name="azure-vms-for-windows-containers"></a>Maszyny wirtualne platformy Azure dla kontenerów systemu Windows

Maszyny wirtualne platformy Azure dla kontenerów systemu Windows to maszyny wirtualne oparte na wersjach systemu Windows Server 2016, Windows 10 lub nowszych, zarówno z skonfigurowaną przez aparat platformy Docker. W większości przypadków system Windows Server 2016 jest używany w maszynach wirtualnych platformy Azure.

Platforma Azure udostępnia obecnie maszynę wirtualną o nazwie **Windows Server 2016 z kontenerami**. Za pomocą tej maszyny Wirtualnej można wypróbować nową funkcję kontenera systemu Windows Server za pomocą systemu Windows Server Core lub systemu Windows Nano Server. Obrazy systemu operacyjnego kontenera są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z platformą Docker.

### <a name="benefits"></a>Korzyści

Mimo że kontenery systemu Windows można wdrożyć na lokalnych maszynach wirtualnych systemu Windows Server 2016, podczas wdrażania na platformie Azure można uzyskać łatwiejszy sposób, aby rozpocząć pracę, z gotowymi do użycia maszynami wirtualnymi kontenera systemu Windows Server. Możesz również uzyskać wspólną lokalizację online, która jest dostępna dla testerów i automatyczną skalowalność za pomocą zestawów skalowania maszyn wirtualnych platformy Azure.

### <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Instruktaż 4: Wdrażanie aplikacji opartych na kontenerach systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)

### <a name="technical-walkthrough-availability"></a>Dostępność instruktażetechnicznym

Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:

[Wdrażanie aplikacji do usługi ACI (wystąpienia kontenera azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Omówienie

[Wystąpienia kontenera platformy Azure (ACI)](https://docs.microsoft.com/azure/container-instances/) jest najszybszym sposobem posiadania środowiska deweloperów/testów/przemieszczania kontenerów, w którym można wdrażać pojedyncze wystąpienia kontenerów.

### <a name="goals"></a>Cele

W tym instruktażu przedstawiono główne scenariusze podczas wdrażania kontenerów systemu Windows w wystąpieniach kontenerów platformy Azure (ACI) i sposób wdrażania aplikacji eShopModernizing w usłudze ACI.

### <a name="scenarios"></a>Scenariusze

Mogą istnieć różnice dotyczące wdrażania aplikacji eShopModernizing w aci, takich jak wdrażanie tylko jednej lub wszystkich aplikacji (aplikacja MVC, aplikacja WebForms lub usługa WCF). W poniższym scenariuszu przedstawiono ASP.NET aplikacji MVC oraz kontenera programu SQL Server, oba zostały wdrożone jako kontenery w usłudze ACI (wystąpienia kontenera Azure).

![Wdrażanie w aci ze środowiska programistycznego](./media/image5-3.5.6.png)

### <a name="benefits"></a>Korzyści

Usługa Azure Container Instances ułatwia tworzenie kontenerów Docker na platformie Azure oraz zarządzanie nimi bez konieczności inicjowania obsługi maszyn wirtualnych czy adoptowania usługi wyższego poziomu. Za pomocą usługi ACI można bezpośrednio wdrożyć kontener systemu Windows na platformie Azure i udostępnić go w Internecie za pomocą w pełni kwalifikowanej nazwy domeny (FQDN) w ciągu kilku sekund (pod warunkiem, że obraz kontenera systemu Windows jest gotowy w rejestrze platformy Docker, takim jak Docker Hub lub Azure Container rejestru).

### <a name="considerations"></a>Zagadnienia do rozważenia

Wdrażanie kontenerów systemu Windows z pełną platformą .NET Framework / ASP.NET lub SQL Server w wystąpieniach kontenerów platformy Azure (ACI) nie jest tak szybkie, jak wdrażanie na zwykłym hoście platformy Docker (takim jak Windows Server 2016 z kontenerami systemu Windows), ponieważ obraz platformy Docker musi zostać pobrany (pobrany z rejestru platformy Docker) za każdym razem, a rozmiary obrazu kontenera SQL (15,1 GB) i obrazu kontenera ASP.NET (13,9 GB) są znacznie duże, a rozmiary obrazu kontenera SQL (15,1 GB) i obrazu kontenera ASP.NET (13,9 GB) są znacznie duże, jednak jest to znacznie tańsze niż utrzymanie własnego hosta docker (na stałe on-line Windows Serwer 2016 z maszyną wirtualną kontenerów systemu Windows na platformie Azure) nie wspominając o całym koordynatorze, takim jak Kubernetes na platformie Azure (AKS), który z drugiej strony jest doskonałym wyborem dla wdrożeń produkcyjnych.

Jako główny wniosek przy użyciu wystąpienia kontenera Azure jest bardzo atrakcyjną opcją dla scenariuszy deweloperskich/testowych i potoków ciągłej integracji/ciągłego dysku CD.

## <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Instruktaż 5: Wdrażanie aplikacji opartych na kontenerach systemu Windows w programie Kubernetes w usłudze Azure Container Service

### <a name="technical-walkthrough-availability"></a>Dostępność instruktażetechnicznym

Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Omówienie

Aplikacja oparta na kontenerach systemu Windows będzie szybko musiała korzystać z platform, oddalając się jeszcze bardziej od maszyn wirtualnych IaaS. Jest to konieczne, aby łatwo osiągnąć wysoką skalowalność i lepszą skalowalność automatyczną oraz znacznie poprawić zautomatyzowane wdrożenia i przechowywanie wersji. Cele te można osiągnąć przy użyciu koordynatora [Kubernetes](https://kubernetes.io/), dostępne w [usłudze Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Cele

Celem tego instruktażejest dowiedzieć się, jak wdrożyć aplikację opartą na kontenerze systemu Windows do kubernetes (nazywany także *K8s)* w usłudze Azure Container Service. Wdrażanie w kubernetes od podstaw jest procesem dwuetapowym:

1. Wdrażanie klastra Kubernetes w usłudze Azure Container Service.

2. Wdrażanie aplikacji i powiązanych zasobów w klastrze Kubernetes.

### <a name="scenarios"></a>Scenariusze

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scenariusz A: Wdrażanie bezpośrednio w klastrze Kubernetes ze środowiska deweloperów

![Wdrażanie bezpośrednio w klastrze Kubernetes ze środowiska programistycznego](./media/image5-7.png)

**Rysunek 5-7.** Wdrażanie bezpośrednio w klastrze Kubernetes ze środowiska programistycznego

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scenariusz B: Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services

![Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services](./media/image5-8.png)

**Rysunek 5-8.** Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services

### <a name="benefits"></a>Korzyści

Wdrażanie w klastrze w kubernetes ma wiele korzyści. Największą zaletą jest to, że można uzyskać środowisko gotowe do produkcji, w którym można skalować w sposób skalowalny aplikacji na podstawie liczby wystąpień kontenera, których chcesz użyć (skalowalność wewnętrzna w istniejących węzłach) i na podstawie liczby węzłów lub maszyn wirtualnych w klastrze ( globalnej skalowalności klastra).

Usługa Azure Container Service optymalizuje popularne narzędzia i technologie typu open source specjalnie dla platformy Azure. Otrzymujesz otwarte rozwiązanie, które oferuje przenośność, zarówno dla kontenerów, jak i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzi koordynatora Container Service obsługuje wszystko inne.

Dzięki programom Kubernetes deweloperzy mogą przejść od myślenia o maszynach fizycznych i wirtualnych do planowania infrastruktury zorientowanej na kontenery, która ułatwia między innymi następujące możliwości:

- Aplikacje oparte na wielu kontenerach

- Replikowanie wystąpień kontenera i skalowanie poziome

- Nazewnictwo i odnajdywanie (na przykład wewnętrzny dns)

- Obciążenia wyważające

- Aktualizacje stopniowe

- Rozpowszechnianie tajemnic

- Kontrole kondycji aplikacji

## <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Instruktaż 6: Wdrażanie aplikacji opartych na kontenerach systemu Windows w usłudze Azure App Service for Containers

### <a name="technical-walkthrough-availability"></a>Dostępność instruktażetechnicznym

Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Omówienie

Prostą aplikację konteneryzowaną przy użyciu kontenerów systemu Windows można łatwo wdrożyć w usłudze Azure App Service for Containers. Jest to zalecane podejście dla większości aplikacji opartych na kontenerze systemu Windows.

### <a name="goals"></a>Cele

Celem tego instruktażejest dowiedzieć się, jak wdrożyć aplikację opartą na kontenerze systemu Windows do usługi Azure App Service for Containers z rejestru (Docker Hub lub Azure Container Registry).

### <a name="scenario"></a>Scenariusz

![Wdrażanie aplikacji opartej na kontenerze systemu Windows w usłudze Azure App Service for Containers](./media/image5-11.png)

### <a name="benefits"></a>Korzyści

Wdrażanie w usłudze Azure App Service for Containers oferuje zalety kontenerów sparowanych z zaletami usługi Azure App Service platformy Azure. Usługę aplikacji można łatwo skalować zarówno w pionie, jak i w poziomie, i można ją skonfigurować do automatycznego skalowania w celu spełnienia zmieniających się wymagań. Aktualizacje można wykonywać przy zerowym przestoju, a konfiguracja ciągłego wdrażania z rejestru jest również łatwa w konfiguracji.

## <a name="next-steps"></a>Następne kroki

Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Poprzedni](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [następny](conclusions.md) <!-- Next Chapter -->
