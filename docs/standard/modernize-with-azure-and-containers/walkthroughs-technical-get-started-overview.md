---
title: Wskazówki i technical uzyskać uruchomiono — omówienie
description: Modernizacji istniejących aplikacji .NET z chmury Azure i kontenery systemu Windows | wskazówki i technical uzyskać uruchomiono — omówienie
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: b41fe9e8b492b1348cc5615f6254d5fd3ddebf25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Wskazówki i technical uzyskać uruchomiono — omówienie

Aby ograniczyć rozmiar Książka elektroniczna, dodatkową dokumentację techniczną i pełne wskazówki zostały udostępnione w repozytorium GitHub. Serie online wskazówki, które jest opisane w tym rozdziale opisano krok po kroku instalacji wielu środowiskach, które są oparte na kontenery systemu Windows i wdrażanie na platformie Azure.

W poniższych sekcjach opisano, co każdy wskazówki jest o jego cele i wizji wysokiego poziomu i zapewnia diagram zadań, które są związane z. Możesz uzyskać wskazówki, same w *eShopModernizing* wiki repozytorium GitHub aplikacje na [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).

## <a name="technical-walkthrough-list"></a>Lista wskazówki techniczne

Poniższe wskazówki get-started zapewnić spójne i wyczerpujące wskazówki techniczne przykładowych aplikacji, które można przyrostu i przesunięte za pomocą kontenerów, a następnie przesuń za pomocą wielu opcji wdrażania na platformie Azure.

Każda z następujących wskazówki używa nowe próbki eShopLegacy i eShopModernizing aplikacji, które są dostępne w witrynie GitHub pod [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).

- **Samouczek eShop starszej wersji aplikacji**

- **Containerize istniejących aplikacji .NET z kontenerami systemu Windows**

- **Wdrażanie aplikacji opartych na kontenery systemu Windows na maszynach wirtualnych platformy Azure**

- **Wdrażanie aplikacji opartych na kontenery systemu Windows na Kubernetes w usłudze kontenera platformy Azure**

- **Wdrażanie aplikacji Windows kontenery sieci szkieletowej usług Azure**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Wskazówki 1: Samouczek eShop starszej wersji aplikacji

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki techniczne

Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a>Omówienie

W tym przewodniku można eksplorować początkowego stosowania dwie przykładowe aplikacje starszej wersji. Zarówno przykładowe aplikacje mają wbudowanymi architekturę i zostały utworzone przy użyciu klasycznego ASP.NET. Co aplikacja jest oparta na platformie ASP.NET 4.x MVC; drugi aplikacja jest oparta na formularzach sieci Web ASP.NET 4.x. Obie aplikacje są w [repozytorium GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

Można containerize zarówno przykładowych aplikacji, w podobny sposób można containerize na klasyczny [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) aplikacji (WCF) do użycia jako aplikacja na komputerze. Na przykład zobacz [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).

### <a name="goals"></a>Cele

Głównym celem tego przewodnika jest po prostu zapoznać się z tych aplikacji i ich kodu i konfiguracji. Aplikacje można skonfigurować tak, aby wygenerować i użycia danych testowych, bez korzystania z bazy danych SQL do celów testowych. Ten opcjonalny config opiera się na iniekcji zależności w sposób rozdzielonymi.

### <a name="scenario"></a>Scenariusz

Rysunek 5-1 przedstawiono prosty scenariusz oryginalnego starsze aplikacje.

> ![Architektura Prosty scenariusz oryginalnego starszych aplikacji](./media/image5-1.png)
>
> **Rysunek 5-1.** Architektura Prosty scenariusz oryginalnego starszych aplikacji

Z punktu widzenia domeny business obie aplikacje oferują tego samego katalogu funkcje zarządzania. Członkowie zespołu enterprise eShop użyje aplikacji, aby wyświetlić i edytować katalogu produktów. Rysunek 5-2 zawiera zrzuty ekranu aplikacji początkowej.

![Aplikacje ASP.NET MVC i formularzy sieci Web platformy ASP.NET (technologii istniejące starsze)](./media/image5-2.png)

> **Rysunek 5-2.** Aplikacje ASP.NET MVC i formularzy sieci Web platformy ASP.NET (technologii istniejące starsze)

Są to aplikacje sieci web, które są używane do przeglądania i modyfikowania wpisy w katalogu. Fakt, że obie aplikacje dostarczyć te same funkcje firm/funkcjonalności jest po prostu do porównania. Podobnej procedurze modernizacji aplikacje, które zostały utworzone przy użyciu platformy ASP.NET MVC i formularzy sieci Web ASP.NET jest widoczny.

Zależności w programie ASP.NET 4.x i jego wcześniejsze wersje, (zarówno dla platformy MVC i formularzy sieci Web) oznacza, że te aplikacje nie będą uruchamiane .NET Core, chyba że kod jest w pełni ulegną przy użyciu platformy ASP.NET Core MVC. Oznacza to punkt, że jeśli nie chcesz ponownego projektowania lub ponownego pisania kodu, można containerize istniejących aplikacji i nadal używać tej samej technologii .NET i tego samego kodu. Widać, jak można uruchomić aplikacji, takich jak te w kontenerach, bez wprowadzania żadnych zmian do starszej wersji kodu.

### <a name="benefits"></a>Zalety

Korzyści wynikające z tego przewodnika są proste: po prostu zapoznać się z konfiguracji kod i aplikacji, oparty na iniekcji zależności. Następnie możesz eksperymentować z tej metody podczas containerize i wdrażania w wielu środowiskach, w przyszłości.

### <a name="next-steps"></a>Następne kroki

Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Wskazówki 2: Containerize istniejących aplikacji .NET z kontenerami systemu Windows

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki techniczne

Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a>Omówienie

Używanie kontenerów Windows zwiększające wdrożenia istniejących aplikacji .NET, podobnie jak na podstawie MVC, formularzy sieci Web lub usługi WCF, do produkcji, projektowanie i środowisk testowych.

### <a name="goals"></a>Cele

Celem tego przewodnika jest pokazanie kilka opcji containerizing istniejącej aplikacji .NET Framework. Można:

- Containerize aplikacji przy użyciu [2017 Visual Studio Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowszy).

- Containerize aplikacji przez ręczne dodanie [plik Dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie użyć [interfejsu wiersza polecenia Docker](https://docs.docker.com/engine/reference/commandline/cli/).

- Containerize aplikacji przy użyciu [Img2Docker](https://github.com/docker/communitytools-image2docker-win) narzędzia (narzędzie open source z Docker).

Ten przewodnik koncentruje się na Visual Studio Tools 2017 Docker podejścia, ale inne podejścia są dość podobne pod względem przy użyciu Dockerfiles.

### <a name="scenario"></a>Scenariusz

Rysunek 5-3 przedstawiono scenariusz konteneryzowanych eShop starsze aplikacje.

> ![Diagram architektury uproszczony konteneryzowanych aplikacji w środowisku deweloperskim](./media/image5-3.png)
>
> **Rysunek 5-3.** Diagram architektury uproszczony konteneryzowanych aplikacji w środowisku deweloperskim

### <a name="benefits"></a>Zalety

Istnieją pewne zalety uruchamiania aplikacji z wbudowanymi w kontenerze. Najpierw należy utworzyć obraz dla aplikacji. Od tego momentu każde wdrożenie jest uruchamiany w tym samym środowisku. Każdy kontener korzysta z tej samej wersji systemu operacyjnego, ma tę samą wersję zainstalowane zależności używa tej samej wersji programu .NET framework i zbudowany przy użyciu tego samego procesu. Zasadniczo kontrolować zależności aplikacji przy użyciu obrazu Docker. Zależności są przesyłane z aplikacji podczas wdrażania kontenerów.

Dodatkową korzyścią jest to deweloperzy mogą uruchomić aplikację w spójne środowisko, które są dostarczane przez Windows kontenerów. Problemy, które są wyświetlane tylko w niektórych wersjach można wykrył natychmiast, zamiast udostępniając w środowisku tymczasowym czy produkcyjnym. Różnice w środowiskach programistycznych używanych przez członków zespołu deweloperów znaczenia mniej aplikacji uruchamianych w kontenerach.

Konteneryzowanych aplikacje mają również płaska krzywej skalowalnego w poziomie. Aplikacje konteneryzowanych umożliwiają mają więcej aplikacji i wystąpień usługi (w oparciu kontenery) w maszynie Wirtualnej lub komputera fizycznego w porównaniu do wdrożenia aplikacji regularnych dla poszczególnych komputerów. Przekłada się wyżej gęstości i mniej wymagane zasoby, szczególnie w przypadku, gdy używasz orchestrators Kubernetes lub sieci szkieletowej usług.

Przechowywanie w kontenerach, w sytuacjach idealne rozwiązanie nie wymaga wprowadzania jakichkolwiek zmian w kodzie aplikacji (C\#). W większości przypadków wystarczy Docker wdrożenia metadanych plików (Dockerfiles i rozwiązania Docker Compose).

### <a name="next-steps"></a>Następne kroki

Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Wskazówki 3: Wdrażanie aplikacji opartych na kontenery systemu Windows na maszynach wirtualnych platformy Azure

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki techniczne

Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>Omówienie

Wdrożeniu na hoście Docker na systemu Windows Server 2016 maszyn wirtualnych (VM) na platformie Azure pozwala szybko skonfigurować środowiska przejściowe development/testu. Również udostępnia typowe miejsce dla testerów i użytkowników biznesowych zatwierdzania aplikacji. Maszyny wirtualne również może być nieprawidłowa że jako środowisk produkcyjnych usługę (IaaS).

### <a name="goals"></a>Cele

Celem tego przewodnika jest pokazanie wielu rozwiązań alternatywnych, których masz wdrażając kontenery systemu Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszy.

### <a name="scenarios"></a>Scenariusze

W tym przewodniku opisano kilka scenariuszy.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Scenariusz A: Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów komputera za pośrednictwem połączenia z aparatem platformy Docker

![Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów PC przez połączenie z aparatem platformy Docker](./media/image5-4.png)

> **Rysunek 5-4.** Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów PC przez połączenie z aparatem platformy Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Scenariusz B: wdrażania na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker

![Wdrażanie na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker](./media/image5-5.png)

> **Rysunek 5-5.** Wdrażanie na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a>Scenariusz C: wdrożyć na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services

![Wdrażanie na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services](./media/image5-6.png)

> **Rysunek 5-6.** Wdrażanie na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services

### <a name="azure-vms-for-windows-containers"></a>Maszyny wirtualne platformy Azure dla systemu Windows kontenerów

Azure maszyn wirtualnych systemu Windows dla kontenerów maszyn wirtualnych na podstawie systemu Windows Server 2016, Windows 10 lub nowszy, konfigurowanie zarówno z aparatem platformy Docker. W większości przypadków systemu Windows Server 2016 jest używany w maszynach wirtualnych platformy Azure.

Platforma Azure obecnie udostępnia maszyny Wirtualnej o nazwie **systemu Windows Server 2016 z kontenerami**. Próby nowa funkcja systemu Windows Server kontenera systemu Windows Server Core lub serwerze Nano systemu Windows, można użyć tej maszyny Wirtualnej. Kontener obrazów systemu operacyjnego są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z Docker.

### <a name="benefits"></a>Zalety

Mimo że kontenery systemu Windows można wdrożyć do lokalnego systemu Windows Server 2016 maszyn wirtualnych, gdy wdrażanie na platformie Azure, możesz uzyskać łatwiejszy sposób, aby rozpocząć pracę z maszynami wirtualnymi o kontenera gotowe do użycia systemu Windows Server. Możesz również uzyskać wspólnej lokalizacji online, który jest dostępny dla testerów i automatyczne skalowalności za pomocą zestawów skali maszyny wirtualnej platformy Azure.

### <a name="next-steps"></a>Następne kroki

Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Wskazówki 4: Wdrażanie aplikacji opartych na kontenery systemu Windows na Kubernetes w usłudze kontenera platformy Azure

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki techniczne

Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>Omówienie

Aplikacja, która jest oparta na kontenery Windows szybko będą musieli używać platformy optymalizacji jeszcze bardziej przenoszenie z maszyn wirtualnych IaaS. To pozwala łatwo osiągnąć wysoką skalowalność na potrzeby lepiej automatycznego skalowalność i uzyskać znaczne ulepszenia w automatycznego wdrożenia i przechowywanie wersji. Te cele można osiągnąć za pomocą orchestrator [Kubernetes](https://kubernetes.io/), dostępną w [usługi kontenera platformy Azure](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Cele

Celem tego przewodnika jest Dowiedz się, jak wdrożyć aplikację na podstawie kontenera systemu Windows do Kubernetes (nazywane również *K8s*) w usłudze kontenera platformy Azure. Wdrażanie na Kubernetes od podstaw jest procesem dwuetapowym:

1.  Wdrażanie klastra Kubernetes do usługi kontenera platformy Azure.

2.  Wdrażanie aplikacji i powiązanych zasobów do klastra Kubernetes.

### <a name="scenarios"></a>Scenariusze

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Scenariusz A: Wdróż bezpośrednio do klastra Kubernetes z tego środowiska deweloperskiego

![Wdrażanie bezpośrednio do klastra Kubernetes środowiska programowania](./media/image5-7.png)

> **Rysunek 5-7.** Wdrażanie bezpośrednio do klastra Kubernetes środowiska programowania

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a>Scenariusz B: wdrożyć klaster Kubernetes z elementu konfiguracji/CD potoków w Team Services

![Wdrażanie klastra Kubernetes z potoków CI/CD w Team Services](./media/image5-8.png)

> **Rysunek 5 – 8.** Wdrażanie klastra Kubernetes z potoków CI/CD w Team Services

### <a name="benefits"></a>Zalety

Istnieje wiele korzyści z wdrażaniem do klastra w Kubernetes. Największych korzyści jest uzyskanie środowisku gotowe do produkcji, w którym można skalować w poziomie na podstawie liczby wystąpień kontenera, aby użyć (wewnętrzny skalowalności w istniejących węzłów), a na podstawie liczby węzłów lub maszyn wirtualnych w klastrze (aplikacji globalne skalowanie klastra).

Usługa kontenera platformy Azure optymalizuje popularnych open source narzędzia i technologie specjalnie dla platformy Azure. Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność, zarówno w przypadku kontenerów, jak i konfigurację aplikacji. Wybierz rozmiar, liczby hostów, a narzędzia orchestrator-kontenera usługi obsługuje wszystkie inne.

Z Kubernetes deweloperzy mogą postępu od planowania fizycznych i maszyn wirtualnych do planowania skoncentrowane kontenera infrastruktury, która ułatwia obsługę następujących funkcji, między innymi:

- Aplikacje oparte na wielu kontenerów

- Replikowanie wystąpień kontenera i skalowanie automatyczne pozioma

- Nazewnictwo i odkrywania (na przykład wewnętrzny serwer DNS)

- Równoważenie obciążenia

- Wprowadzanie aktualizacji

- Dystrybuowanie kluczy tajnych

- Sprawdzanie kondycji aplikacji

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>Wskazówki 5: Wdrażanie aplikacji opartych na kontenery systemu Windows do usługi Azure Service Fabric

### <a name="technical-walkthrough-availability"></a>Dostępność wskazówki techniczne

Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>Omówienie

Aplikacji opartej na kontenery Windows szybko powinna być używana platform optymalizacji jeszcze bardziej przenoszenie z maszyn wirtualnych IaaS. To pozwala łatwo osiągnąć wysoką skalowalność na potrzeby lepiej automatycznego skalowalność i uzyskać znaczne ulepszenia w automatycznego wdrożenia i przechowywanie wersji. Można osiągnięcie tych celów, za pomocą usługi orchestrator sieci szkieletowej usług Azure, która jest dostępna w chmurze Azure, ale również dostępne do użycia lokalnego, a nawet w innej chmurze publicznej.

### <a name="goals"></a>Cele

Celem tego przewodnika jest informacje na temat wdrażania aplikacji na podstawie kontenera systemu Windows do klastra usługi sieć szkieletowa na platformie Azure. Wdrażanie sieci szkieletowej usług od podstaw jest procesem dwuetapowym:

1.  Wdrażanie klastra usługi sieć szkieletowa usług Azure (lub innego środowiska).

2.  Wdrażanie aplikacji i powiązanych zasobów do klastra usługi sieć szkieletowa usług.

### <a name="scenarios"></a>Scenariusze

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>Scenariusz A: Wdróż bezpośrednio do klastra usługi sieć szkieletowa z tego środowiska deweloperskiego

![Wdrażanie bezpośrednio do klastra usługi sieć szkieletowa środowiska programowania](./media/image5-9.png)

> **Rysunek 5 – 9.** Wdrażanie bezpośrednio do klastra usługi sieć szkieletowa środowiska programowania

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a>Scenariusz B: wdrażanie klastra usługi sieć szkieletowa z elementu konfiguracji/CD potoków w Team Services

![Wdrażanie klastra usługi sieć szkieletowa z potoków CI/CD w Visual Studio Team Services](./media/image5-10.png)

> **Rysunek 5-10.** Wdrażanie klastra usługi sieć szkieletowa z potoków CI/CD w Visual Studio Team Services

## <a name="benefits"></a>Zalety

Korzyści z wdrożenia do klastra w sieci szkieletowej usług są podobne do korzyści wynikające ze stosowania Kubernetes. Jedną różnicą, jednak jest sieci szkieletowej usług dla aplikacji systemu Windows w porównaniu do Kubernetes, który jest w fazie beta kontenerów systemu Windows w wersji 1.9 Kubernetes więcej dojrzałe środowiska produkcyjnego (2017 grudnia). Kubernetes jest bardziej dojrzałe środowisko dla systemu Linux.

Główne zaletą używania sieci szkieletowej usług Azure jest uzyskanie środowisku gotowe do produkcji, w którym można skalować w poziomie na podstawie liczby wystąpień kontenera, aby użyć (wewnętrzny skalowalności w istniejących węzłów), a na podstawie liczby aplikacji węzły lub maszyny wirtualne w klastrze (globalne skalowanie klastra).

Sieć szkieletowa usług Azure oferuje przenośność zarówno w przypadku kontenerów, jak i konfigurację aplikacji. Masz usługi sieć szkieletowa klastra na platformie Azure, lub jego zainstalowanie lokalnego we własnym centrum danych. Można nawet zainstalować klaster sieci szkieletowej usług w innej chmurze tak samo, jak [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).

Z sieci szkieletowej usług deweloperzy mogą postępu od planowania fizycznych i maszyn wirtualnych do planowania skoncentrowane kontenera infrastruktury, która ułatwia obsługę następujących funkcji, między innymi:

- Aplikacje oparte na wiele kontenerów.

- Replikowanie wystąpień kontenera i poziomy Skalowanie automatyczne.

- Nazewnictwo i odkrywania (na przykład wewnętrzny serwer DNS).

- Równoważenie obciążenia.

- Wprowadzanie aktualizacji.

- Dystrybuowanie kluczy tajnych.

- Umożliwia sprawdzenie kondycji aplikacji.

Następujące funkcje są wyłączne w sieci szkieletowej usług (w porównaniu do innych orchestrators):

- Możliwości usługi stanowej, za pomocą niezawodnych usług modelu aplikacji.

- Wzorzec złośliwych użytkowników za pomocą modelu aplikacji Reliable Actors.

- Wdróż procesów kości bez systemu operacyjnego, oprócz kontenery systemu Windows lub Linux.

- Zaawansowane aktualizacji stopniowych i kontroli kondycji.

### <a name="next-steps"></a>Następne kroki

Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
[Poprzednie](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[dalej](conclusions.md)
