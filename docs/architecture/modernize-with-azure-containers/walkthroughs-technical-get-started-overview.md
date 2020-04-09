---
title: Omówienie przewodników i wprowadzającej dokumentacji technicznej
description: Zmodernizuj istniejące aplikacje platformy .NET za pomocą kontenerów w chmurze azure i windows | Omówienie przewodników i pomocy technicznej
ms.date: 04/28/2018
ms.openlocfilehash: cff418d9b6e931a3082d8a2f8b818e7275139578
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987872"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Omówienie przewodników i wprowadzającej dokumentacji technicznej

Aby ograniczyć rozmiar tego e-booka, w repozytorium GitHub udostępniono dodatkową dokumentację techniczną i pełne wskazówki. Seria przewodników online opisana w tym rozdziale obejmuje konfigurację krok po kroku wielu środowisk opartych na kontenerach systemu Windows i wdrażanie na platformie Azure.

W poniższych sekcjach wyjaśniono, o czym jest każdy przewodnik, jego cele i wizję wysokiego poziomu i zawiera diagram zadań, które są zaangażowane. Możesz uzyskać same instruktaże w *eShopModernizing* aplikacje GitHub repo wiki w <https://github.com/dotnet-architecture/eShopModernizing/wiki>.

## <a name="technical-walkthrough-list"></a>Lista przewodników technicznych

Poniższe wskazówki dotyczące wprowadzenie zapewniają spójne i kompleksowe wskazówki techniczne dotyczące przykładowych aplikacji, które można podnosić i przesuwać za pomocą kontenerów, a następnie przenosić przy użyciu wielu opcji wdrażania na platformie Azure.

Każdy z poniższych instruktaży używa nowych przykładowych aplikacji eShopLegacy i eShopModernizing, które są dostępne na GitHub pod adresem <https://github.com/dotnet-architecture/eShopModernizing>.

- **Zwiedzanie starszych aplikacji eShop (podstawowe aplikacje do modernizacji)**

- **Kontenerowanie istniejących ASP.NET aplikacji internetowych (WebForms & MVC) za pomocą kontenerów systemu Windows**

- **Kontenerowanie istniejących usług WCF (aplikacje warstwy N) za pomocą kontenerów systemu Windows**

- **Wdrażanie aplikacji opartej na kontenerach systemu Windows na maszynach wirtualnych platformy Azure**

- **Wdrażanie aplikacji opartych na kontenerach systemu Windows w usłudze Kubernetes w usłudze kontenerów platformy Azure**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Przewodnik 1: Zwiedzanie starszych aplikacji eShop

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki technicznej

Pełny przewodnik techniczny jest dostępny w eShopModernizing GitHub repozytorium wiki:

[eShopModernizacja przewodników wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Omówienie

W tym instruktażu można eksplorować początkową implementację trzech przykładowych starszych aplikacji. Pierwsze dwie przykładowe aplikacje sieci web mają architekturę monolityczną i zostały utworzone przy użyciu klasycznego ASP.NET. Jedna aplikacja jest oparta na ASP.NET 4.x MVC; druga aplikacja jest oparta na ASP.NET 4.x Formularze internetowe.
Trzecia aplikacja to aplikacja 3-warstwowa składająca się z aplikacji WinForms klienta i usługi [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) po stronie serwera.

Wszystkie te aplikacje są dostępne w [eShopModernizing GitHub repozytorium](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Cele

Głównym celem tego przewodnika jest po prostu zapoznać się z tych aplikacji i ich kodu i konfiguracji. Aplikacje można skonfigurować tak, aby generować i używać makiety danych, bez użycia bazy danych SQL, do celów testowych. Ten opcjonalny config opiera się na iniekcji zależności, w sposób oddzielony.

### <a name="scenario-1-aspnet-web-apps"></a>Scenariusz 1: ASP.NET aplikacje sieci Web

Poniższy rysunek przedstawia prosty scenariusz oryginalnego ASP.NET aplikacji sieci web.

![Prosty scenariusz architektury oryginalnego ASP.NET aplikacji sieci Web](./media/image5-1.png)

Z punktu widzenia domeny biznesowej obie aplikacje oferują te same funkcje zarządzania katalogiem. Członkowie zespołu przedsiębiorstwa eShop będą używać aplikacji do wyświetlania i edytowania katalogu produktów.

Na następnej ilustracji przedstawiono początkowe zrzuty ekranu aplikacji.

![ASP.NET aplikacje MVC i ASP.NET Web Forms (istniejące/starsze technologie)](./media/image5-2.png)

Zależności w ASP.NET wersji 4.x lub wcześniejszych (dla MVC lub formularzy sieci Web) oznacza, że te aplikacje nie będą uruchamiane w programie .NET Core, chyba że kod jest w pełni przepisany przy użyciu ASP.NET Core MVC.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Scenariusz 2: Usługa WCF i aplikacja kliencka WinForms (aplikacja 3-warstwowa)

Poniższy rysunek przedstawia prosty scenariusz oryginalnej aplikacji starszej 3-warstwowej.

![Prosty scenariusz architektury oryginalnej starszej aplikacji 3-warstwowej z usługą WCF i aplikacją kliencką WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Zalety

Korzyści z tego przewodnika są proste: wystarczy zapoznać się z kodem i początkowymi aplikacjami.

### <a name="next-steps"></a>Następne kroki

Zapoznaj się z tą zawartością bardziej szczegółowo na wiki GitHub:

- [Przewodnik po linii bazowej ASP.NET "starszych" aplikacji MVC i web forms](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Przewodnik po podstawowej usłudze WCF i aplikacji WinForms (3-warstwowa) "legacy"](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Przewodnik 2: Konteneryzuj istniejące aplikacje platformy .NET za pomocą kontenerów systemu Windows

### <a name="overview"></a>Omówienie

Użyj kontenerów systemu Windows, aby usprawnić wdrażanie istniejących aplikacji platformy .NET, takich jak te oparte na MVC, formularzy sieci Web lub WCF, do środowisk produkcyjnych, deweloperskich i testowych.

### <a name="goals"></a>Cele

Celem tego przewodnika jest pokazanie kilku opcji konteneryzacji istniejącej aplikacji .NET Framework. Możesz:

- Konteneryzuj aplikację przy użyciu [programu Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowsze wersje).

- Konteneryzuj aplikację, ręcznie dodając [plik dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie używając [interfejsu wiersza polecenia platformy Docker](https://docs.docker.com/engine/reference/commandline/cli/).

- Konteneryzuj aplikację za pomocą narzędzia [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (narzędzia typu open source z platformy Docker).

Ten przewodnik koncentruje się na visual studio 2017 Narzędzia do platformy Docker podejście, ale pozostałe dwa podejścia są dość podobne w odniesieniu do korzystania z dockerfiles.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Scenariusz 1: Konteneryzowane ASP.NET aplikacje internetowe

Rysunek poniżej przedstawia scenariusz konteneryzowanych aplikacji sieci web starszych sklepów eShop.

![Uproszczony diagram architektury konteneryzowanych aplikacji ASP.NET w środowisku deweloperskim](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Scenariusz 2: Konteneryzowana usługa WCF

Rysunek poniżej przedstawia scenariusz dla aplikacji 3-warstwowej z konteneryzowaną usługą WCF.

![Uproszczony diagram architektury konteneryzowanej usługi WCF w środowisku deweloperskim](./media/image5-3.5.png)

### <a name="benefits"></a>Zalety

Istnieją zalety uruchamiania aplikacji monolityczne w kontenerze. Najpierw należy utworzyć obraz dla aplikacji. Od tego momentu każde wdrożenie jest uruchamiane w tym samym środowisku. Każdy kontener używa tej samej wersji systemu operacyjnego, ma zainstalowaną tę samą wersję zależności, używa tej samej wersji .NET framework i jest zbudowany przy użyciu tego samego procesu. Zasadniczo można kontrolować zależności aplikacji przy użyciu obrazu platformy Docker. Zależności są przesyłane z aplikacją podczas wdrażania kontenerów.

Dodatkową zaletą jest to, że deweloperzy mogą uruchamiać aplikację w spójnym środowisku, które jest dostarczane przez kontenery systemu Windows. Problemy, które pojawiają się tylko w niektórych wersjach można dostrzec natychmiast, zamiast napawania się w środowisku przejściowym lub produkcyjnym. Różnice w środowiskach programistów używanych przez członków zespołu deweloperów mają mniejsze znaczenie, gdy aplikacje są uruchamiane w kontenerach.

Aplikacje konteneryzowane mają również bardziej płaski krzywej skalowalnej w poziomie. Konteneryzowane aplikacje umożliwiają więcej wystąpień aplikacji i usług (na podstawie kontenerów) na maszynie wirtualnej lub komputerze fizycznym w porównaniu do regularnych wdrożeń aplikacji na komputerze. Przekłada się to na większą gęstość i mniej wymaganych zasobów, zwłaszcza gdy używasz koordynatorów, takich jak Kubernetes.

Konteneryzacja, w idealnych sytuacjach, nie wymaga wprowadzania żadnych zmian w kodzie aplikacji (C).\# W większości scenariuszy wystarczy pliki metadanych wdrażania platformy Docker (pliki dockerfiles i docker compose).

### <a name="next-steps"></a>Następne kroki

Zapoznaj się z tą zawartością bardziej szczegółowo na wiki GitHub:

- [Jak konteneryzować aplikacje sieci Web programu .NET Framework za pomocą kontenerów systemu Windows i platformy Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Dodawanie pomocy technicznej platformy Docker do usługi WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Przewodnik 3: Wdrażanie aplikacji opartej na kontenerach systemu Windows na maszynach wirtualnych platformy Azure

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki technicznej

Pełny przewodnik techniczny jest dostępny w eShopModernizing GitHub repozytorium wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Omówienie

Wdrażanie na hoście platformy Docker na maszynie wirtualnej systemu Windows Server 2016 (VM) na platformie Azure umożliwia szybkie konfigurowanie środowisk deweloperskich/testowych/przejściowych. Zapewnia również wspólne miejsce dla testerów lub użytkowników biznesowych, aby sprawdzić poprawność aplikacji. Maszyny wirtualne mogą być również prawidłowe środowiska produkcyjne Infrastruktury jako usługi (IaaS).

### <a name="goals"></a>Cele

Celem tego przewodnika jest pokazanie wielu alternatyw, które masz podczas wdrażania kontenerów systemu Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszych wersjach.

### <a name="scenarios"></a>Scenariusze

W tym instruktażu przedstawiono kilka scenariuszy.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scenariusz A: Wdrażanie na maszynie wirtualnej platformy Azure z komputera dewelopera za pośrednictwem połączenia z aparatem platformy Docker

![Wdrażanie na maszynie wirtualnej platformy Azure z komputera dewelopera za pośrednictwem połączenia z aparatem platformy Docker](./media/image5-4.png)

**Rysunek 5-4.** Wdrażanie na maszynie wirtualnej platformy Azure z komputera dewelopera za pośrednictwem połączenia z aparatem platformy Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scenariusz B: Wdrażanie na maszynie wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker

![Wdrażanie na maszynie wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker](./media/image5-5.png)

**Rysunek 5-5.** Wdrażanie na maszynie wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Scenariusz C: Wdrażanie na maszynie Wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps

![Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługach DevOps platformy Azure](./media/image5-6.png)

**Rysunek 5-6.** Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługach DevOps platformy Azure

### <a name="azure-vms-for-windows-containers"></a>Maszyny wirtualne platformy Azure dla kontenerów systemu Windows

Maszyny wirtualne platformy Azure dla kontenerów systemu Windows są maszynami wirtualnymi opartymi na systemach Windows Server 2016, Windows 10 lub nowszych wersjach, obie z konfiguracją aparatu platformy Docker. W większości przypadków system Windows Server 2016 jest używany na maszynach wirtualnych platformy Azure.

Platforma Azure zapewnia obecnie maszynę wirtualną o nazwie **Windows Server 2016 z kontenerami.** Za pomocą tej maszyny Wirtualnej można wypróbować nową funkcję kontenera systemu Windows Server z systemem Windows Server Core lub Windows Nano Server. Obrazy systemu operacyjnego kontenera są instalowane, a następnie maszyna wirtualna jest gotowa do użycia z platformyą Docker.

### <a name="benefits"></a>Zalety

Chociaż kontenery systemu Windows można wdrożyć na lokalnych maszynach wirtualnych systemu Windows Server 2016, podczas wdrażania na platformie Azure można łatwiej rozpocząć pracę dzięki gotowym do użycia maszynom wirtualnym kontenerów systemu Windows Server. Można również uzyskać wspólną lokalizację online, która jest dostępna dla testerów i automatyczną skalowalność za pośrednictwem zestawów skalowania maszyny wirtualnej platformy Azure.

### <a name="next-steps"></a>Następne kroki

Zapoznaj się z tą zawartością bardziej szczegółowo na wiki GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Przewodnik 4: Wdrażanie aplikacji opartych na kontenerach systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki technicznej

Pełny przewodnik techniczny jest dostępny w eShopModernizing GitHub repozytorium wiki:

[Wdrażanie aplikacji w usłudze ACI (wystąpienia kontenerów platformy Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Omówienie

[Wystąpienia kontenera platformy Azure (ACI)](https://docs.microsoft.com/azure/container-instances/) jest najszybszym sposobem, aby kontenery dev/test/staging środowiska, w którym można wdrożyć pojedyncze wystąpienia kontenerów.

### <a name="goals"></a>Cele

W tym przewodniku przedstawiono główne scenariusze podczas wdrażania kontenerów systemu Windows w wystąpieniach kontenerów platformy Azure (ACI) i jak można wdrożyć aplikacje eShopModernizing w usłudze ACI.

### <a name="scenarios"></a>Scenariusze

Mogą istnieć różnice dotyczące wdrażania aplikacji eShopModernizing w ACI, takie jak wdrażanie tylko jednej lub wszystkich aplikacji (aplikacja MVC, aplikacja WebForms lub usługa WCF). W poniższym scenariuszu można zobaczyć ASP.NET aplikacji MVC oraz kontenera programu SQL Server, który został wdrożony jako kontenery w usłudze ACI (wystąpienia kontenerów platformy Azure).

![Wdrażanie w ujm w środowisku programistycznym](./media/image5-3.5.6.png)

### <a name="benefits"></a>Zalety

Usługa Azure Container Instances ułatwia tworzenie kontenerów Docker na platformie Azure oraz zarządzanie nimi bez konieczności inicjowania obsługi maszyn wirtualnych czy adoptowania usługi wyższego poziomu. Za pomocą usługi ACI można bezpośrednio wdrożyć kontener systemu Windows na platformie Azure i udostępnić go w Internecie z w pełni kwalifikowaną nazwą domeny (FQDN) w ciągu kilku sekund (pod warunkiem, że masz gotowy obraz kontenera systemu Windows w rejestrze platformy Docker, takim jak Centrum platformy Docker lub Azure Container Registry).

### <a name="considerations"></a>Zagadnienia do rozważenia

Wdrażanie kontenerów systemu Windows z pełnym programem .NET Framework / ASP.NET lub SQL Server w instancjach kontenerów platformy Azure (ACI) nie jest tak szybkie, jak wdrażanie na zwykłym hoście platformy Docker (np. 15,1 GB) i obraz kontenera ASP.NET (13,9 GB) są znacznie duże, jednak jest znacznie tańszy niż utrzymywanie własnego hosta platformy docker (na stałe on-line Windows Server 2016 z windows containers VM na platformie Azure), nie wspominając o całym koordynatorze, takim jak Kubernetes na platformie Azure (AKS), który jest, z drugiej strony, doskonały wybór dla wdrożeń produkcyjnych.

Jako główny wniosek przy użyciu wystąpienia kontenera platformy Azure jest bardzo atrakcyjną opcją dla scenariuszy deweloperów/testów i potoków ciągłej integracji/ciągłego wdrażania.

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z tą zawartością bardziej szczegółowo na wiki GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Przewodnik 5: Wdrażanie aplikacji opartych na kontenerach systemu Windows w usłudze Kubernetes w usłudze kontenerów platformy Azure

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki technicznej

Pełny przewodnik techniczny jest dostępny w eShopModernizing GitHub repozytorium wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Omówienie

Aplikacja oparta na kontenerach systemu Windows będzie szybko musiała korzystać z platform, oddając się jeszcze dalej od maszyn wirtualnych IaaS. Jest to potrzebne do łatwego osiągnięcia wysokiej skalowalności i lepszej zautomatyzowanej skalowalności oraz do znacznej poprawy w zakresie zautomatyzowanych wdrożeń i przechowywania wersji. Można osiągnąć te cele za pomocą programu [Kubernetes](https://kubernetes.io/)programu orchestrator , dostępne w [usłudze Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Cele

Celem tego przewodnika jest, aby dowiedzieć się, jak wdrożyć aplikację opartą na kontenerze systemu Windows do kubernetes (zwany także *K8s)* w usłudze Azure Container Service. Wdrażanie w udusznikach kubernetes od podstaw jest procesem dwuetapowym:

1. Wdrażanie klastra usługi Kubernetes w usłudze Azure Container Service.

2. Wdrażanie aplikacji i powiązanych zasobów w klastrze Kubernetes.

### <a name="scenarios"></a>Scenariusze

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scenariusz A: Wdrażanie bezpośrednio w klastrze Kubernetes ze środowiska deweloperskiego

![Wdrażanie bezpośrednio w klastrze kubernetes ze środowiska deweloperskiego](./media/image5-7.png)

**Rysunek 5-7.** Wdrażanie bezpośrednio w klastrze kubernetes ze środowiska deweloperskiego

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Scenariusz B: Wdrażanie w klastrze kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps

![Wdrażanie w klastrze usługi Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługach DevOps platformy Azure](./media/image5-8.png)

**Rysunek 5-8.** Wdrażanie w klastrze usługi Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługach DevOps platformy Azure

### <a name="benefits"></a>Zalety

Istnieje wiele korzyści do wdrożenia w klastrze w uduchowionych w ud. Największą zaletą jest uzyskanie środowiska gotowego do produkcji, w którym można skalować w poziomie aplikacji na podstawie liczby wystąpień kontenera, których chcesz użyć (skalowalność wewnętrzna w istniejących węzłach) i na podstawie liczby węzłów lub maszyn wirtualnych w klastrze (globalna skalowalność klastra).

Usługa Azure Container Service optymalizuje popularne narzędzia i technologie typu open source specjalnie dla platformy Azure. Otrzymujesz otwarte rozwiązanie, które oferuje przenośność, zarówno dla kontenerów, jak i dla konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia aranżatora-Usługa kontenera obsługuje wszystko inne.

Dzięki usłudze Kubernetes deweloperzy mogą przejść od myślenia o maszynach fizycznych i wirtualnych do planowania infrastruktury zorientowanej na kontenery, która ułatwia następujące możliwości, między innymi:

- Aplikacje oparte na wielu kontenerach

- Replikowanie wystąpień kontenerów i skalowanie w poziomie

- Nazywanie i odkrywanie (na przykład wewnętrzny DNS)

- Obciążenia równoważące

- Aktualizacje stopniowe

- Rozpowszechnianie wpisów tajnych

- Kontrole kondycji aplikacji

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z tą zawartością bardziej szczegółowo na wiki GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Przewodnik 6: Wdrażanie aplikacji opartych na kontenerach systemu Windows w usłudze Azure App Service for Containers

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki technicznej

Pełny przewodnik techniczny jest dostępny w eShopModernizing GitHub repozytorium wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Omówienie

Prostą konteneryzowaną aplikację przy użyciu kontenerów systemu Windows można łatwo wdrożyć w usłudze Azure App Service for Containers. Jest to zalecane podejście dla większości aplikacji opartych na kontenerze systemu Windows.

### <a name="goals"></a>Cele

Celem tego przewodnika jest, aby dowiedzieć się, jak wdrożyć aplikację opartą na kontenerze systemu Windows do usługi Azure App Service for Containers z rejestru (Docker Hub lub Azure Container Registry).

### <a name="scenario"></a>Scenariusz

![Wdrażanie aplikacji opartej na kontenerze systemu Windows w usłudze Azure App Service for Containers](./media/image5-11.png)

### <a name="benefits"></a>Zalety

Wdrażanie w usłudze Azure App Service for Containers oferuje korzyści związane z kontenerami w połączeniu z zaletami usługi PaaS usługi Azure App Service. Usługę aplikacji można łatwo skalować zarówno w pionie, jak i poziomo i można ją skonfigurować do skalowania automatycznego w celu spełnienia zmieniających się wymagań. Aktualizacje mogą być wykonywane przy zerowym przestoju i konfiguracji ciągłego wdrażania z rejestru jest łatwo skonfigurowany, jak również.

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z tą zawartością bardziej szczegółowo na wiki GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Poprzedni](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [następny](conclusions.md) <!-- Next Chapter -->
