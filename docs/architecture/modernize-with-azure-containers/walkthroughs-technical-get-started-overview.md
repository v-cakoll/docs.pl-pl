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
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="cfb57-103">Omówienie przewodników i wprowadzającej dokumentacji technicznej</span><span class="sxs-lookup"><span data-stu-id="cfb57-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="cfb57-104">Aby ograniczyć rozmiar tej e-booka, w repozytorium Usługi GitHub udostępniono dodatkową dokumentację techniczną i pełne rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cfb57-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="cfb57-105">Seria instruktażu online opisana w tym rozdziale obejmuje konfigurację krok po kroku wielu środowisk opartych na kontenerach systemu Windows i wdrażanie na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="cfb57-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="cfb57-106">W poniższych sekcjach wyjaśniono, o co chodzi w każdym instruktażu, jego celach i wizji wysokiego poziomu, a także przedstawiono diagram zadań, które są zaangażowane.</span><span class="sxs-lookup"><span data-stu-id="cfb57-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="cfb57-107">Możesz uzyskać same instruktaże w *eShopModernizing* aplikacji GitHub repo wiki w . <https://github.com/dotnet-architecture/eShopModernizing/wiki></span><span class="sxs-lookup"><span data-stu-id="cfb57-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="cfb57-108">Lista instruktażów technicznych</span><span class="sxs-lookup"><span data-stu-id="cfb57-108">Technical walkthrough list</span></span>

<span data-ttu-id="cfb57-109">Poniższe wskazówki dotyczące początku zawierają spójne i kompleksowe wskazówki techniczne dotyczące przykładowych aplikacji, które można podnieść i zmienić przy użyciu kontenerów, a następnie przenieść przy użyciu wielu opcji wdrażania na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="cfb57-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="cfb57-110">Każdy z poniższych instruktaże używa nowego przykładowego eShopLegacy i eShopModernizing aplikacji, które są dostępne w GitHub w . <https://github.com/dotnet-architecture/eShopModernizing></span><span class="sxs-lookup"><span data-stu-id="cfb57-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="cfb57-111">**Przewodnik po starszych aplikacjach sklepu eShop (aplikacje bazowe do modernizacji)**</span><span class="sxs-lookup"><span data-stu-id="cfb57-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="cfb57-112">**Konteneryzuj istniejące ASP.NET aplikacje sieci Web (WebForms & MVC) za pomocą kontenerów systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="cfb57-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="cfb57-113">**Konteneryzuj istniejące usługi WCF (aplikacje n-warstwowe) za pomocą kontenerów systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="cfb57-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="cfb57-114">**Wdrażanie aplikacji opartej na kontenerach systemu Windows na maszynach wirtualnych platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="cfb57-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="cfb57-115">**Wdrażanie aplikacji opartych na kontenerach systemu Windows w programie Kubernetes w usłudze Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="cfb57-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="cfb57-116">Przewodnik 1: Zwiedzanie starszych aplikacji sklepu eShop</span><span class="sxs-lookup"><span data-stu-id="cfb57-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="cfb57-117">Dostępność instruktażetechnicznym</span><span class="sxs-lookup"><span data-stu-id="cfb57-117">Technical walkthrough availability</span></span>

<span data-ttu-id="cfb57-118">Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="cfb57-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="cfb57-119">eShopModernizing wiki instruktaże</span><span class="sxs-lookup"><span data-stu-id="cfb57-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="cfb57-120">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cfb57-120">Overview</span></span>

<span data-ttu-id="cfb57-121">W tym instruktażem można eksplorować wstępną implementację trzech przykładowych starszych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfb57-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="cfb57-122">Pierwsze dwie przykładowe aplikacje internetowe mają monolityczną architekturę i zostały utworzone przy użyciu klasycznych ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cfb57-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="cfb57-123">Jedna aplikacja jest oparta na ASP.NET 4.x MVC; druga aplikacja jest oparta na ASP.NET 4.x Web Forms.</span><span class="sxs-lookup"><span data-stu-id="cfb57-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="cfb57-124">Trzecia aplikacja to aplikacja 3-warstwowa skomponowana przez aplikację WinForms klienta i usługę [WCF (Windows Communication Foundation)](../../framework/wcf/whats-wcf.md) po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="cfb57-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="cfb57-125">Wszystkie te aplikacje są dostępne w [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="cfb57-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="cfb57-126">Cele</span><span class="sxs-lookup"><span data-stu-id="cfb57-126">Goals</span></span>

<span data-ttu-id="cfb57-127">Głównym celem tego instruktażu jest po prostu zapoznanie się z tymi aplikacjami oraz z ich kodem i konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="cfb57-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="cfb57-128">Aplikacje można skonfigurować tak, aby generowały i używały makiet danych bez używania bazy danych SQL do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="cfb57-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="cfb57-129">Ta opcjonalna konfiguracja jest oparta na iniekcji zależności, w sposób niesparzony.</span><span class="sxs-lookup"><span data-stu-id="cfb57-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="cfb57-130">Scenariusz 1: ASP.NET aplikacje sieci Web</span><span class="sxs-lookup"><span data-stu-id="cfb57-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="cfb57-131">Poniższy rysunek przedstawia prosty scenariusz oryginalnego starszego ASP.NET aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cfb57-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Prosty scenariusz architektury oryginalnej starszej ASP.NET aplikacji sieci Web](./media/image5-1.png)

<span data-ttu-id="cfb57-133">Z punktu widzenia domeny biznesowej obie aplikacje oferują te same funkcje zarządzania katalogami.</span><span class="sxs-lookup"><span data-stu-id="cfb57-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="cfb57-134">Członkowie zespołu przedsiębiorstwa sklepu internetowego będą używać aplikacji do wyświetlania i edytowania katalogu produktów.</span><span class="sxs-lookup"><span data-stu-id="cfb57-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="cfb57-135">Na następnej ilustracji przedstawiono początkowe zrzuty ekranu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfb57-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET mvc i ASP.NET web forms (istniejące/starsze technologie)](./media/image5-2.png)

<span data-ttu-id="cfb57-137">Zależności w ASP.NET wersji 4.x lub wcześniejszych (dla MVC lub dla formularzy sieci Web) oznacza, że te aplikacje nie będą działać na .NET Core, chyba że kod jest w pełni przepisany przy użyciu ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="cfb57-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="cfb57-138">Scenariusz 2: Usługa WCF i aplikacja kliencz WinForms (aplikacja 3-warstwowa)</span><span class="sxs-lookup"><span data-stu-id="cfb57-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="cfb57-139">Poniższy rysunek przedstawia prosty scenariusz oryginalnej 3-warstwowej starszej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfb57-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Prosty scenariusz architektury oryginalnej starszej aplikacji 3-warstwowej z usługą WCF i aplikacją kliencką WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="cfb57-141">Korzyści</span><span class="sxs-lookup"><span data-stu-id="cfb57-141">Benefits</span></span>

<span data-ttu-id="cfb57-142">Zalety tego instruktażu są proste: Wystarczy zapoznać się z kodem i początkowymi aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="cfb57-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="cfb57-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="cfb57-143">Next steps</span></span>

<span data-ttu-id="cfb57-144">Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="cfb57-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="cfb57-145">Przewodnik po podstawowych ASP.NET MVC i starszych aplikacji formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="cfb57-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="cfb57-146">Przewodnik po podstawowej usłudze WCF i aplikacji "legacy" WinForms (3-warstwowej)</span><span class="sxs-lookup"><span data-stu-id="cfb57-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="cfb57-147">Instruktaż 2: Konteneryzuj istniejące aplikacje .NET za pomocą kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cfb57-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="cfb57-148">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cfb57-148">Overview</span></span>

<span data-ttu-id="cfb57-149">Użyj kontenerów systemu Windows, aby usprawnić wdrażanie istniejących aplikacji .NET, takich jak te oparte na MVC, Web Forms lub WCF, w środowiskach produkcyjnych, deweloperskich i testowych.</span><span class="sxs-lookup"><span data-stu-id="cfb57-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="cfb57-150">Cele</span><span class="sxs-lookup"><span data-stu-id="cfb57-150">Goals</span></span>

<span data-ttu-id="cfb57-151">Celem tego instruktażejest pokazać kilka opcji konteneryzacji istniejącej aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cfb57-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="cfb57-152">Możesz:</span><span class="sxs-lookup"><span data-stu-id="cfb57-152">You can:</span></span>

- <span data-ttu-id="cfb57-153">Konteneryzuj aplikację przy użyciu [programu Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowsze wersje).</span><span class="sxs-lookup"><span data-stu-id="cfb57-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="cfb57-154">Konteneryzuj aplikację ręcznie dodając [plik Dockerfile,](https://docs.docker.com/engine/reference/builder/)a następnie używając [interfejsu cli](https://docs.docker.com/engine/reference/commandline/cli/)platformy Docker .</span><span class="sxs-lookup"><span data-stu-id="cfb57-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="cfb57-155">Konteneryzuj aplikację za pomocą narzędzia [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (narzędzia typu open source z platformy Docker).</span><span class="sxs-lookup"><span data-stu-id="cfb57-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="cfb57-156">Ten instruktaż koncentruje się na visual studio 2017 Narzędzia dla platformy Docker podejście, ale pozostałe dwa podejścia są dość podobne w odniesieniu do korzystania z plików dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="cfb57-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="cfb57-157">Scenariusz 1: konteneryzowane ASP.NET aplikacje sieci Web</span><span class="sxs-lookup"><span data-stu-id="cfb57-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="cfb57-158">Poniższy rysunek przedstawia scenariusz konteneryzowanych starszych aplikacji sieci web sklepu eShop.</span><span class="sxs-lookup"><span data-stu-id="cfb57-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Diagram architektury uproszczonej konteneryzowanych aplikacji ASP.NET w środowisku programistycznym](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="cfb57-160">Scenariusz 2: Konteneryzowana usługa WCF</span><span class="sxs-lookup"><span data-stu-id="cfb57-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="cfb57-161">Poniższy rysunek przedstawia scenariusz dla aplikacji 3-warstwowej z konteneryzowaną usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="cfb57-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Diagram architektury uproszczonej konteneryzowanej usługi WCF w środowisku programistycznym](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="cfb57-163">Korzyści</span><span class="sxs-lookup"><span data-stu-id="cfb57-163">Benefits</span></span>

<span data-ttu-id="cfb57-164">Istnieją zalety uruchamiania aplikacji monolityczne w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="cfb57-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="cfb57-165">Najpierw należy utworzyć obraz dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfb57-165">First, you create an image for the application.</span></span> <span data-ttu-id="cfb57-166">Od tego momentu każde wdrożenie jest uruchamiane w tym samym środowisku.</span><span class="sxs-lookup"><span data-stu-id="cfb57-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="cfb57-167">Każdy kontener używa tej samej wersji systemu operacyjnego, ma tę samą wersję zależności zainstalowane, używa tej samej wersji platformy .NET i jest zbudowany przy użyciu tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="cfb57-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="cfb57-168">Zasadniczo można kontrolować zależności aplikacji przy użyciu obrazu platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="cfb57-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="cfb57-169">Zależności podróży z aplikacją podczas wdrażania kontenerów.</span><span class="sxs-lookup"><span data-stu-id="cfb57-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="cfb57-170">Dodatkową korzyścią jest to, że deweloperzy mogą uruchamiać aplikację w spójnym środowisku, które jest dostarczane przez kontenery systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cfb57-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="cfb57-171">Problemy, które pojawiają się tylko w niektórych wersjach można wykryć natychmiast, zamiast pojawiać się w środowisku przejściowym lub produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="cfb57-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="cfb57-172">Różnice w środowiskach programistycznych używanych przez członków zespołu programistycznego mają mniejsze znaczenie, gdy aplikacje są uruchamiane w kontenerach.</span><span class="sxs-lookup"><span data-stu-id="cfb57-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="cfb57-173">Konteneryzowane aplikacje mają również bardziej płaską krzywą skalowania w skali.</span><span class="sxs-lookup"><span data-stu-id="cfb57-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="cfb57-174">Konteneryzowane aplikacje umożliwiają więcej wystąpień aplikacji i usługi (na podstawie kontenerów) na maszynie wirtualnej lub komputerze fizycznym w porównaniu z regularnymi wdrożeniami aplikacji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cfb57-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="cfb57-175">Przekłada się to na większą gęstość i mniej wymaganych zasobów, zwłaszcza w przypadku korzystania z koordynatorów, takich jak Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="cfb57-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="cfb57-176">Konteneryzacja, w idealnych sytuacjach, nie wymaga wprowadzania\#żadnych zmian w kodzie aplikacji (C).</span><span class="sxs-lookup"><span data-stu-id="cfb57-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="cfb57-177">W większości scenariuszy wystarczy pliki metadanych wdrażania platformy Docker (pliki dockerfiles i pliki docker Compose).</span><span class="sxs-lookup"><span data-stu-id="cfb57-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="cfb57-178">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="cfb57-178">Next steps</span></span>

<span data-ttu-id="cfb57-179">Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="cfb57-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="cfb57-180">Jak konteneryzować aplikacje sieci web .NET Framework za pomocą kontenerów systemu Windows i platformy Docker</span><span class="sxs-lookup"><span data-stu-id="cfb57-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="cfb57-181">Dodawanie obsługi platformy Docker do usługi WCF</span><span class="sxs-lookup"><span data-stu-id="cfb57-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="cfb57-182">Instruktaż 3: Wdrażanie aplikacji opartej na kontenerach systemu Windows na maszynach wirtualnych platformy Azure</span><span class="sxs-lookup"><span data-stu-id="cfb57-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="cfb57-183">Dostępność instruktażetechnicznym</span><span class="sxs-lookup"><span data-stu-id="cfb57-183">Technical walkthrough availability</span></span>

<span data-ttu-id="cfb57-184">Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="cfb57-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="cfb57-185">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cfb57-185">Overview</span></span>

<span data-ttu-id="cfb57-186">Wdrażanie na hoście platformy Docker na maszynie wirtualnej (VM) systemu Windows Server 2016 na platformie Azure umożliwia szybkie konfigurowanie środowisk deweloperskich/testowych/przemieszczania.</span><span class="sxs-lookup"><span data-stu-id="cfb57-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="cfb57-187">Zapewnia również wspólne miejsce dla testerów lub użytkowników biznesowych do sprawdzania poprawności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfb57-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="cfb57-188">Maszyny wirtualne mogą być również prawidłową infrastrukturą jako środowiskami produkcyjnymi usługi (IaaS).</span><span class="sxs-lookup"><span data-stu-id="cfb57-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="cfb57-189">Cele</span><span class="sxs-lookup"><span data-stu-id="cfb57-189">Goals</span></span>

<span data-ttu-id="cfb57-190">Celem tego instruktażenia jest pokazanie wielu alternatyw, które masz podczas wdrażania kontenerów systemu Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="cfb57-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="cfb57-191">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="cfb57-191">Scenarios</span></span>

<span data-ttu-id="cfb57-192">W tym instruktacie uwzględniono kilka scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="cfb57-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="cfb57-193">Scenariusz A: Wdrażanie na maszynie wirtualnej platformy Azure z komputera dewelopera za pośrednictwem połączenia aparatu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="cfb57-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Wdrażanie na maszynie wirtualnej platformy Azure z komputera dewelopera za pośrednictwem połączenia aparatu platformy Docker](./media/image5-4.png)

<span data-ttu-id="cfb57-195">**Rysunek 5-4.**</span><span class="sxs-lookup"><span data-stu-id="cfb57-195">**Figure 5-4.**</span></span> <span data-ttu-id="cfb57-196">Wdrażanie na maszynie wirtualnej platformy Azure z komputera dewelopera za pośrednictwem połączenia aparatu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="cfb57-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="cfb57-197">Scenariusz B: Wdrażanie na maszynie wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="cfb57-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Wdrażanie na maszynie wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker](./media/image5-5.png)

<span data-ttu-id="cfb57-199">**Rysunek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="cfb57-199">**Figure 5-5.**</span></span> <span data-ttu-id="cfb57-200">Wdrażanie na maszynie wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="cfb57-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="cfb57-201">Scenariusz C: Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="cfb57-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services](./media/image5-6.png)

<span data-ttu-id="cfb57-203">**Rysunek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="cfb57-203">**Figure 5-6.**</span></span> <span data-ttu-id="cfb57-204">Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="cfb57-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="cfb57-205">Maszyny wirtualne platformy Azure dla kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cfb57-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="cfb57-206">Maszyny wirtualne platformy Azure dla kontenerów systemu Windows to maszyny wirtualne oparte na wersjach systemu Windows Server 2016, Windows 10 lub nowszych, zarówno z skonfigurowaną przez aparat platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="cfb57-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="cfb57-207">W większości przypadków system Windows Server 2016 jest używany w maszynach wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="cfb57-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="cfb57-208">Platforma Azure udostępnia obecnie maszynę wirtualną o nazwie **Windows Server 2016 z kontenerami**.</span><span class="sxs-lookup"><span data-stu-id="cfb57-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="cfb57-209">Za pomocą tej maszyny Wirtualnej można wypróbować nową funkcję kontenera systemu Windows Server za pomocą systemu Windows Server Core lub systemu Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="cfb57-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="cfb57-210">Obrazy systemu operacyjnego kontenera są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z platformą Docker.</span><span class="sxs-lookup"><span data-stu-id="cfb57-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="cfb57-211">Korzyści</span><span class="sxs-lookup"><span data-stu-id="cfb57-211">Benefits</span></span>

<span data-ttu-id="cfb57-212">Mimo że kontenery systemu Windows można wdrożyć na lokalnych maszynach wirtualnych systemu Windows Server 2016, podczas wdrażania na platformie Azure można uzyskać łatwiejszy sposób, aby rozpocząć pracę, z gotowymi do użycia maszynami wirtualnymi kontenera systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="cfb57-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="cfb57-213">Możesz również uzyskać wspólną lokalizację online, która jest dostępna dla testerów i automatyczną skalowalność za pomocą zestawów skalowania maszyn wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="cfb57-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="cfb57-214">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="cfb57-214">Next steps</span></span>

<span data-ttu-id="cfb57-215">Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="cfb57-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="cfb57-216">Instruktaż 4: Wdrażanie aplikacji opartych na kontenerach systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="cfb57-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="cfb57-217">Dostępność instruktażetechnicznym</span><span class="sxs-lookup"><span data-stu-id="cfb57-217">Technical walkthrough availability</span></span>

<span data-ttu-id="cfb57-218">Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="cfb57-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="cfb57-219">[Wdrażanie aplikacji do usługi ACI (wystąpienia kontenera azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="cfb57-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="cfb57-220">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cfb57-220">Overview</span></span>

<span data-ttu-id="cfb57-221">[Wystąpienia kontenera platformy Azure (ACI)](https://docs.microsoft.com/azure/container-instances/) jest najszybszym sposobem posiadania środowiska deweloperów/testów/przemieszczania kontenerów, w którym można wdrażać pojedyncze wystąpienia kontenerów.</span><span class="sxs-lookup"><span data-stu-id="cfb57-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="cfb57-222">Cele</span><span class="sxs-lookup"><span data-stu-id="cfb57-222">Goals</span></span>

<span data-ttu-id="cfb57-223">W tym instruktażu przedstawiono główne scenariusze podczas wdrażania kontenerów systemu Windows w wystąpieniach kontenerów platformy Azure (ACI) i sposób wdrażania aplikacji eShopModernizing w usłudze ACI.</span><span class="sxs-lookup"><span data-stu-id="cfb57-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="cfb57-224">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="cfb57-224">Scenarios</span></span>

<span data-ttu-id="cfb57-225">Mogą istnieć różnice dotyczące wdrażania aplikacji eShopModernizing w aci, takich jak wdrażanie tylko jednej lub wszystkich aplikacji (aplikacja MVC, aplikacja WebForms lub usługa WCF).</span><span class="sxs-lookup"><span data-stu-id="cfb57-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="cfb57-226">W poniższym scenariuszu przedstawiono ASP.NET aplikacji MVC oraz kontenera programu SQL Server, oba zostały wdrożone jako kontenery w usłudze ACI (wystąpienia kontenera Azure).</span><span class="sxs-lookup"><span data-stu-id="cfb57-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Wdrażanie w aci ze środowiska programistycznego](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="cfb57-228">Korzyści</span><span class="sxs-lookup"><span data-stu-id="cfb57-228">Benefits</span></span>

<span data-ttu-id="cfb57-229">Usługa Azure Container Instances ułatwia tworzenie kontenerów Docker na platformie Azure oraz zarządzanie nimi bez konieczności inicjowania obsługi maszyn wirtualnych czy adoptowania usługi wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="cfb57-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="cfb57-230">Za pomocą usługi ACI można bezpośrednio wdrożyć kontener systemu Windows na platformie Azure i udostępnić go w Internecie za pomocą w pełni kwalifikowanej nazwy domeny (FQDN) w ciągu kilku sekund (pod warunkiem, że obraz kontenera systemu Windows jest gotowy w rejestrze platformy Docker, takim jak Docker Hub lub Azure Container rejestru).</span><span class="sxs-lookup"><span data-stu-id="cfb57-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="cfb57-231">Zagadnienia do rozważenia</span><span class="sxs-lookup"><span data-stu-id="cfb57-231">Considerations</span></span>

<span data-ttu-id="cfb57-232">Wdrażanie kontenerów systemu Windows z pełną platformą .NET Framework / ASP.NET lub SQL Server w wystąpieniach kontenerów platformy Azure (ACI) nie jest tak szybkie, jak wdrażanie na zwykłym hoście platformy Docker (takim jak Windows Server 2016 z kontenerami systemu Windows), ponieważ obraz platformy Docker musi zostać pobrany (pobrany z rejestru platformy Docker) za każdym razem, a rozmiary obrazu kontenera SQL (15,1 GB) i obrazu kontenera ASP.NET (13,9 GB) są znacznie duże, a rozmiary obrazu kontenera SQL (15,1 GB) i obrazu kontenera ASP.NET (13,9 GB) są znacznie duże, jednak jest to znacznie tańsze niż utrzymanie własnego hosta docker (na stałe on-line Windows Serwer 2016 z maszyną wirtualną kontenerów systemu Windows na platformie Azure) nie wspominając o całym koordynatorze, takim jak Kubernetes na platformie Azure (AKS), który z drugiej strony jest doskonałym wyborem dla wdrożeń produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="cfb57-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="cfb57-233">Jako główny wniosek przy użyciu wystąpienia kontenera Azure jest bardzo atrakcyjną opcją dla scenariuszy deweloperskich/testowych i potoków ciągłej integracji/ciągłego dysku CD.</span><span class="sxs-lookup"><span data-stu-id="cfb57-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cfb57-234">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="cfb57-234">Next steps</span></span>

<span data-ttu-id="cfb57-235">Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="cfb57-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="cfb57-236">Instruktaż 5: Wdrażanie aplikacji opartych na kontenerach systemu Windows w programie Kubernetes w usłudze Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="cfb57-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="cfb57-237">Dostępność instruktażetechnicznym</span><span class="sxs-lookup"><span data-stu-id="cfb57-237">Technical walkthrough availability</span></span>

<span data-ttu-id="cfb57-238">Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="cfb57-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="cfb57-239">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cfb57-239">Overview</span></span>

<span data-ttu-id="cfb57-240">Aplikacja oparta na kontenerach systemu Windows będzie szybko musiała korzystać z platform, oddalając się jeszcze bardziej od maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="cfb57-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="cfb57-241">Jest to konieczne, aby łatwo osiągnąć wysoką skalowalność i lepszą skalowalność automatyczną oraz znacznie poprawić zautomatyzowane wdrożenia i przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="cfb57-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="cfb57-242">Cele te można osiągnąć przy użyciu koordynatora [Kubernetes](https://kubernetes.io/), dostępne w [usłudze Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="cfb57-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="cfb57-243">Cele</span><span class="sxs-lookup"><span data-stu-id="cfb57-243">Goals</span></span>

<span data-ttu-id="cfb57-244">Celem tego instruktażejest dowiedzieć się, jak wdrożyć aplikację opartą na kontenerze systemu Windows do kubernetes (nazywany także *K8s)* w usłudze Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="cfb57-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="cfb57-245">Wdrażanie w kubernetes od podstaw jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="cfb57-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="cfb57-246">Wdrażanie klastra Kubernetes w usłudze Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="cfb57-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="cfb57-247">Wdrażanie aplikacji i powiązanych zasobów w klastrze Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="cfb57-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="cfb57-248">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="cfb57-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="cfb57-249">Scenariusz A: Wdrażanie bezpośrednio w klastrze Kubernetes ze środowiska deweloperów</span><span class="sxs-lookup"><span data-stu-id="cfb57-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Wdrażanie bezpośrednio w klastrze Kubernetes ze środowiska programistycznego](./media/image5-7.png)

<span data-ttu-id="cfb57-251">**Rysunek 5-7.**</span><span class="sxs-lookup"><span data-stu-id="cfb57-251">**Figure 5-7.**</span></span> <span data-ttu-id="cfb57-252">Wdrażanie bezpośrednio w klastrze Kubernetes ze środowiska programistycznego</span><span class="sxs-lookup"><span data-stu-id="cfb57-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="cfb57-253">Scenariusz B: Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="cfb57-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services](./media/image5-8.png)

<span data-ttu-id="cfb57-255">**Rysunek 5-8.**</span><span class="sxs-lookup"><span data-stu-id="cfb57-255">**Figure 5-8.**</span></span> <span data-ttu-id="cfb57-256">Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługach Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="cfb57-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="cfb57-257">Korzyści</span><span class="sxs-lookup"><span data-stu-id="cfb57-257">Benefits</span></span>

<span data-ttu-id="cfb57-258">Wdrażanie w klastrze w kubernetes ma wiele korzyści.</span><span class="sxs-lookup"><span data-stu-id="cfb57-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="cfb57-259">Największą zaletą jest to, że można uzyskać środowisko gotowe do produkcji, w którym można skalować w sposób skalowalny aplikacji na podstawie liczby wystąpień kontenera, których chcesz użyć (skalowalność wewnętrzna w istniejących węzłach) i na podstawie liczby węzłów lub maszyn wirtualnych w klastrze ( globalnej skalowalności klastra).</span><span class="sxs-lookup"><span data-stu-id="cfb57-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="cfb57-260">Usługa Azure Container Service optymalizuje popularne narzędzia i technologie typu open source specjalnie dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="cfb57-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="cfb57-261">Otrzymujesz otwarte rozwiązanie, które oferuje przenośność, zarówno dla kontenerów, jak i konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfb57-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="cfb57-262">Wybierz rozmiar, liczbę hostów i narzędzi koordynatora Container Service obsługuje wszystko inne.</span><span class="sxs-lookup"><span data-stu-id="cfb57-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="cfb57-263">Dzięki programom Kubernetes deweloperzy mogą przejść od myślenia o maszynach fizycznych i wirtualnych do planowania infrastruktury zorientowanej na kontenery, która ułatwia między innymi następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="cfb57-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="cfb57-264">Aplikacje oparte na wielu kontenerach</span><span class="sxs-lookup"><span data-stu-id="cfb57-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="cfb57-265">Replikowanie wystąpień kontenera i skalowanie poziome</span><span class="sxs-lookup"><span data-stu-id="cfb57-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="cfb57-266">Nazewnictwo i odnajdywanie (na przykład wewnętrzny dns)</span><span class="sxs-lookup"><span data-stu-id="cfb57-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="cfb57-267">Obciążenia wyważające</span><span class="sxs-lookup"><span data-stu-id="cfb57-267">Balancing loads</span></span>

- <span data-ttu-id="cfb57-268">Aktualizacje stopniowe</span><span class="sxs-lookup"><span data-stu-id="cfb57-268">Rolling updates</span></span>

- <span data-ttu-id="cfb57-269">Rozpowszechnianie tajemnic</span><span class="sxs-lookup"><span data-stu-id="cfb57-269">Distributing secrets</span></span>

- <span data-ttu-id="cfb57-270">Kontrole kondycji aplikacji</span><span class="sxs-lookup"><span data-stu-id="cfb57-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="cfb57-271">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="cfb57-271">Next steps</span></span>

<span data-ttu-id="cfb57-272">Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="cfb57-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="cfb57-273">Instruktaż 6: Wdrażanie aplikacji opartych na kontenerach systemu Windows w usłudze Azure App Service for Containers</span><span class="sxs-lookup"><span data-stu-id="cfb57-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="cfb57-274">Dostępność instruktażetechnicznym</span><span class="sxs-lookup"><span data-stu-id="cfb57-274">Technical walkthrough availability</span></span>

<span data-ttu-id="cfb57-275">Pełny instruktaż techniczny jest dostępny w eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="cfb57-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="cfb57-276">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cfb57-276">Overview</span></span>

<span data-ttu-id="cfb57-277">Prostą aplikację konteneryzowaną przy użyciu kontenerów systemu Windows można łatwo wdrożyć w usłudze Azure App Service for Containers.</span><span class="sxs-lookup"><span data-stu-id="cfb57-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="cfb57-278">Jest to zalecane podejście dla większości aplikacji opartych na kontenerze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cfb57-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="cfb57-279">Cele</span><span class="sxs-lookup"><span data-stu-id="cfb57-279">Goals</span></span>

<span data-ttu-id="cfb57-280">Celem tego instruktażejest dowiedzieć się, jak wdrożyć aplikację opartą na kontenerze systemu Windows do usługi Azure App Service for Containers z rejestru (Docker Hub lub Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="cfb57-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="cfb57-281">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="cfb57-281">Scenario</span></span>

![Wdrażanie aplikacji opartej na kontenerze systemu Windows w usłudze Azure App Service for Containers](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="cfb57-283">Korzyści</span><span class="sxs-lookup"><span data-stu-id="cfb57-283">Benefits</span></span>

<span data-ttu-id="cfb57-284">Wdrażanie w usłudze Azure App Service for Containers oferuje zalety kontenerów sparowanych z zaletami usługi Azure App Service platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="cfb57-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="cfb57-285">Usługę aplikacji można łatwo skalować zarówno w pionie, jak i w poziomie, i można ją skonfigurować do automatycznego skalowania w celu spełnienia zmieniających się wymagań.</span><span class="sxs-lookup"><span data-stu-id="cfb57-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="cfb57-286">Aktualizacje można wykonywać przy zerowym przestoju, a konfiguracja ciągłego wdrażania z rejestru jest również łatwa w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cfb57-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cfb57-287">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="cfb57-287">Next steps</span></span>

<span data-ttu-id="cfb57-288">Poznaj tę zawartość bardziej szczegółowo na wiki GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="cfb57-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="cfb57-289">[Poprzedni](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [następny](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="cfb57-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
