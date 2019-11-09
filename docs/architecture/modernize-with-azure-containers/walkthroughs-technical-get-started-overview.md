---
title: Omówienie przewodników i wprowadzającej dokumentacji technicznej
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Przewodniki i przegląd wprowadzenie techniczne
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "69660885"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="13fab-103">Omówienie przewodników i wprowadzającej dokumentacji technicznej</span><span class="sxs-lookup"><span data-stu-id="13fab-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="13fab-104">Aby ograniczyć rozmiar tej książki elektronicznej, w repozytorium GitHub udostępniono dodatkową dokumentację techniczną i pełne instruktaże.</span><span class="sxs-lookup"><span data-stu-id="13fab-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="13fab-105">Serie online przewodników, które opisano w tym rozdziale, obejmują konfigurację krok po kroku dla wielu środowisk opartych na kontenerach systemu Windows oraz wdrażanie na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="13fab-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="13fab-106">W poniższych sekcjach wyjaśniono, czym są poszczególne instruktaże, ich cele i wizja wysokiego poziomu, a także przedstawiono diagram zadań, które są związane.</span><span class="sxs-lookup"><span data-stu-id="13fab-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="13fab-107">Instruktaże można uzyskać w witrynie typu wiki repozytorium *eShopModernizing* aplikacje w witrynie GitHub na <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span><span class="sxs-lookup"><span data-stu-id="13fab-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="13fab-108">Lista przewodników technicznych</span><span class="sxs-lookup"><span data-stu-id="13fab-108">Technical walkthrough list</span></span>

<span data-ttu-id="13fab-109">Poniższe przewodniki Get-Started zapewniają spójne i kompleksowe wskazówki techniczne dotyczące przykładowych aplikacji, które można dołączać i przenosić przy użyciu kontenerów, a następnie przełączać się za pomocą wielu opcji wdrożenia na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="13fab-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="13fab-110">W każdym z poniższych instruktażów są wykorzystywane nowe przykładowe aplikacje eShopLegacy i eShopModernizing, które są dostępne w witrynie GitHub w <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="13fab-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="13fab-111">**Przewodnik po eShop starszych aplikacji (aplikacje podstawowe do modernizacji)**</span><span class="sxs-lookup"><span data-stu-id="13fab-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="13fab-112">**Konteneryzowanie istniejące aplikacje sieci Web ASP.NET (WebForms & MVC) z kontenerami systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="13fab-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="13fab-113">**Konteneryzowanie istniejące usługi WCF (aplikacje N-warstwowe) za pomocą kontenerów systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="13fab-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="13fab-114">**Wdrażanie aplikacji opartych na kontenerach systemu Windows na maszynach wirtualnych platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="13fab-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="13fab-115">**Wdróż aplikacje oparte na kontenerach systemu Windows w usłudze Kubernetes w Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="13fab-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="13fab-116">Przewodnik 1: Przewodnik po starszych aplikacjach eShop</span><span class="sxs-lookup"><span data-stu-id="13fab-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="13fab-117">Dostępność przewodnika technicznego</span><span class="sxs-lookup"><span data-stu-id="13fab-117">Technical walkthrough availability</span></span>

<span data-ttu-id="13fab-118">Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub:</span><span class="sxs-lookup"><span data-stu-id="13fab-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="13fab-119">Wskazówki dotyczące eShopModernizing wiki</span><span class="sxs-lookup"><span data-stu-id="13fab-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="13fab-120">Omówienie</span><span class="sxs-lookup"><span data-stu-id="13fab-120">Overview</span></span>

<span data-ttu-id="13fab-121">W tym instruktażu można poznać początkową implementację trzech przykładowych starszych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13fab-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="13fab-122">Pierwsze dwie przykładowe aplikacje internetowe mają niemonolityczną architekturę i zostały utworzone przy użyciu klasycznego ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="13fab-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="13fab-123">Jedna aplikacja jest oparta na ASP.NET 4. x MVC; Druga aplikacja jest oparta na formularzach sieci Web ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="13fab-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="13fab-124">Trzecia aplikacja to 3-warstwowa aplikacja, która składa się z aplikacji WinForms klienta i usługi Windows Communication Foundation po stronie serwera [(WCF)](../../framework/wcf/whats-wcf.md) .</span><span class="sxs-lookup"><span data-stu-id="13fab-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="13fab-125">Wszystkie te aplikacje są dostępne w [repozytorium GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="13fab-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="13fab-126">Wyniki</span><span class="sxs-lookup"><span data-stu-id="13fab-126">Goals</span></span>

<span data-ttu-id="13fab-127">Głównym celem tego przewodnika jest po prostu zaznajomienie się z tymi aplikacjami oraz ich kodem i konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="13fab-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="13fab-128">Aplikacje można skonfigurować w taki sposób, aby generowały i używały danych makiety bez używania bazy danych SQL do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="13fab-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="13fab-129">Ta opcjonalna konfiguracja jest oparta na iniekcji zależności w oddzielnym sposobie.</span><span class="sxs-lookup"><span data-stu-id="13fab-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="13fab-130">Scenariusz 1: ASP.NET Web Apps</span><span class="sxs-lookup"><span data-stu-id="13fab-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="13fab-131">Na poniższym rysunku przedstawiono prosty scenariusz oryginalnych starszych aplikacji sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="13fab-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Prosty scenariusz architektury dla oryginalnych starszych aplikacji sieci Web ASP.NET](./media/image5-1.png)

<span data-ttu-id="13fab-133">W perspektywie domeny biznesowej obie aplikacje oferują te same funkcje zarządzania katalogami.</span><span class="sxs-lookup"><span data-stu-id="13fab-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="13fab-134">Członkowie zespołu eShop Enterprise używają aplikacji do wyświetlania i edytowania wykazu produktów.</span><span class="sxs-lookup"><span data-stu-id="13fab-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="13fab-135">Następny rysunek przedstawia początkowe zrzuty ekranu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13fab-135">The next figure shows the initial app screenshots.</span></span>

![Aplikacje ASP.NET MVC i ASP.NET Web Forms (istniejące/starsze technologie)](./media/image5-2.png)

<span data-ttu-id="13fab-137">Zależności w ASP.NET 4. x lub starszych wersjach (w przypadku wersji MVC lub for Web Forms) oznacza, że te aplikacje nie będą działać w programie .NET Core, chyba że kod jest w pełni zapisany przy użyciu ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="13fab-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="13fab-138">Scenariusz 2. aplikacja kliencka usługi WCF i WinForms (aplikacja 3-warstwowa)</span><span class="sxs-lookup"><span data-stu-id="13fab-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="13fab-139">Na poniższej ilustracji przedstawiono prosty scenariusz oryginalnej starszej aplikacji 3-warstwowej.</span><span class="sxs-lookup"><span data-stu-id="13fab-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Prosty scenariusz architektury oryginalnej starszej aplikacji 3-warstwowej z usługą WCF i aplikacją kliencką WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="13fab-141">Zalety</span><span class="sxs-lookup"><span data-stu-id="13fab-141">Benefits</span></span>

<span data-ttu-id="13fab-142">Zalety tego instruktażu są proste: po prostu zapoznaj się z kodem i początkowymi aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="13fab-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="13fab-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="13fab-143">Next steps</span></span>

<span data-ttu-id="13fab-144">Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="13fab-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="13fab-145">Przewodnik po aplikacjach podstawowych ASP.NET MVC i Web Forms "starsze"</span><span class="sxs-lookup"><span data-stu-id="13fab-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="13fab-146">Samouczek dotyczący podstawowej usługi WCF i WinForms (3-warstwowej) "starszej" aplikacji</span><span class="sxs-lookup"><span data-stu-id="13fab-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="13fab-147">Przewodnik 2: Konteneryzowanie istniejących aplikacji .NET za pomocą kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="13fab-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="13fab-148">Omówienie</span><span class="sxs-lookup"><span data-stu-id="13fab-148">Overview</span></span>

<span data-ttu-id="13fab-149">Użyj kontenerów systemu Windows, aby usprawnić wdrażanie istniejących aplikacji platformy .NET, takich jak te oparte na technologii MVC, Web Forms lub WCF, w środowiskach produkcyjnych, programistycznych i testowych.</span><span class="sxs-lookup"><span data-stu-id="13fab-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="13fab-150">Wyniki</span><span class="sxs-lookup"><span data-stu-id="13fab-150">Goals</span></span>

<span data-ttu-id="13fab-151">Celem tego instruktażu jest wyświetlenie kilku opcji konteneryzowania istniejącej aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13fab-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="13fab-152">Można:</span><span class="sxs-lookup"><span data-stu-id="13fab-152">You can:</span></span>

- <span data-ttu-id="13fab-153">Konteneryzowanie aplikację przy użyciu [narzędzi programu Visual studio 2017 dla platformy Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowsze wersje).</span><span class="sxs-lookup"><span data-stu-id="13fab-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="13fab-154">Konteneryzowanie aplikację przez ręczne dodanie [pliku dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie za pomocą [interfejsu wiersza polecenia platformy Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="13fab-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="13fab-155">Konteneryzowanie aplikację przy użyciu narzędzia [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (narzędzia Open Source z platformy Docker).</span><span class="sxs-lookup"><span data-stu-id="13fab-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="13fab-156">Ten przewodnik koncentruje się na rozdziałach Visual Studio 2017 Tools for Docker, ale inne dwa podejścia są dość podobne w odniesieniu do używania wieloetapowe dockerfile.</span><span class="sxs-lookup"><span data-stu-id="13fab-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="13fab-157">Scenariusz 1: kontenery ASP.NET Web Apps</span><span class="sxs-lookup"><span data-stu-id="13fab-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="13fab-158">Na poniższej ilustracji przedstawiono scenariusz dla aplikacji kontenerów eShop starsze aplikacje sieci Web.</span><span class="sxs-lookup"><span data-stu-id="13fab-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Uproszczony diagram architektury aplikacji ASP.NET dla kontenerów w środowisku programistycznym](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="13fab-160">Scenariusz 2. kontener usługi WCF</span><span class="sxs-lookup"><span data-stu-id="13fab-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="13fab-161">Na poniższej ilustracji przedstawiono scenariusz dla aplikacji 3-warstwowej z użyciem kontenera usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="13fab-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Uproszczony diagram architektury usługi WCF w kontenerze w środowisku programistycznym](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="13fab-163">Zalety</span><span class="sxs-lookup"><span data-stu-id="13fab-163">Benefits</span></span>

<span data-ttu-id="13fab-164">Istnieją zalety uruchamiania aplikacji monolitycznej w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="13fab-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="13fab-165">Najpierw utworzysz obraz dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13fab-165">First, you create an image for the application.</span></span> <span data-ttu-id="13fab-166">Od tego momentu każde wdrożenie jest uruchamiane w tym samym środowisku.</span><span class="sxs-lookup"><span data-stu-id="13fab-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="13fab-167">Każdy kontener używa tej samej wersji systemu operacyjnego, ma taką samą wersję zależności, korzysta z tej samej wersji programu .NET Framework i został skompilowany przy użyciu tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="13fab-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="13fab-168">W zasadzie można kontrolować zależności aplikacji przy użyciu obrazu platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="13fab-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="13fab-169">Zależności są przesyłane wraz z aplikacją podczas wdrażania kontenerów.</span><span class="sxs-lookup"><span data-stu-id="13fab-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="13fab-170">Dodatkową korzyścią jest to, że deweloperzy mogą uruchamiać aplikację w spójnym środowisku dostarczanym przez kontenery systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="13fab-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="13fab-171">Problemy, które pojawiają się tylko w niektórych wersjach, można natychmiast wycofać, zamiast obsłużyć w środowisku przejściowym lub produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="13fab-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="13fab-172">Różnice w środowiskach deweloperskich używanych przez członków zespołu deweloperskiego są mniejsze, gdy aplikacje działają w kontenerach.</span><span class="sxs-lookup"><span data-stu-id="13fab-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="13fab-173">Aplikacje kontenerowe mają również krzywą skalowania w poziomie Flatter.</span><span class="sxs-lookup"><span data-stu-id="13fab-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="13fab-174">Aplikacje kontenerowe umożliwiają korzystanie z większej liczby wystąpień aplikacji i usług (opartych na kontenerach) w maszynie wirtualnej lub na komputerze fizycznym w porównaniu do zwykłych wdrożeń aplikacji na maszynę.</span><span class="sxs-lookup"><span data-stu-id="13fab-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="13fab-175">Powoduje to przetłumaczenie na wyższą gęstość i mniejszą ilość wymaganych zasobów, zwłaszcza w przypadku korzystania z programu Orchestrator, takiego jak Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="13fab-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="13fab-176">Kontenerach w idealnych sytuacjach nie wymaga wprowadzania żadnych zmian w kodzie aplikacji (C\#).</span><span class="sxs-lookup"><span data-stu-id="13fab-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="13fab-177">W większości scenariuszy wymagane są tylko pliki metadanych wdrożenia platformy Docker (pliki wieloetapowe dockerfile i Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="13fab-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="13fab-178">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="13fab-178">Next steps</span></span>

<span data-ttu-id="13fab-179">Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="13fab-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="13fab-180">Jak konteneryzowanie aplikacje sieci Web .NET Framework przy użyciu kontenerów systemu Windows i platformy Docker</span><span class="sxs-lookup"><span data-stu-id="13fab-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="13fab-181">Dodawanie obsługi platformy Docker do usługi WCF</span><span class="sxs-lookup"><span data-stu-id="13fab-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="13fab-182">Przewodnik 3: wdrażanie aplikacji opartych na kontenerach systemu Windows na maszynach wirtualnych platformy Azure</span><span class="sxs-lookup"><span data-stu-id="13fab-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="13fab-183">Dostępność przewodnika technicznego</span><span class="sxs-lookup"><span data-stu-id="13fab-183">Technical walkthrough availability</span></span>

<span data-ttu-id="13fab-184">Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="13fab-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="13fab-185">Omówienie</span><span class="sxs-lookup"><span data-stu-id="13fab-185">Overview</span></span>

<span data-ttu-id="13fab-186">Wdrożenie na hoście Docker na maszynie wirtualnej z systemem Windows Server 2016 (VM) na platformie Azure pozwala szybko skonfigurować środowisko deweloperskie/testowe/przejściowe.</span><span class="sxs-lookup"><span data-stu-id="13fab-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="13fab-187">Zapewnia również typowe miejsce dla testerów lub użytkowników firmowych w celu zweryfikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13fab-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="13fab-188">Maszyny wirtualne mogą również być prawidłowymi środowiskami produkcyjnymi infrastruktury jako usługi (IaaS).</span><span class="sxs-lookup"><span data-stu-id="13fab-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="13fab-189">Wyniki</span><span class="sxs-lookup"><span data-stu-id="13fab-189">Goals</span></span>

<span data-ttu-id="13fab-190">Celem tego przewodnika jest przedstawienie wielu alternatyw, które są używane podczas wdrażania kontenerów systemu Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="13fab-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="13fab-191">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="13fab-191">Scenarios</span></span>

<span data-ttu-id="13fab-192">W tym instruktażu omówiono kilka scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="13fab-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="13fab-193">Scenariusz A: wdrażanie na maszynie wirtualnej platformy Azure z komputera deweloperskiego za pośrednictwem połączenia aparatu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="13fab-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Wdrażanie na maszynie wirtualnej platformy Azure z komputera deweloperskiego za pośrednictwem połączenia aparatu platformy Docker](./media/image5-4.png)

<span data-ttu-id="13fab-195">**Rysunek 5-4.**</span><span class="sxs-lookup"><span data-stu-id="13fab-195">**Figure 5-4.**</span></span> <span data-ttu-id="13fab-196">Wdrażanie na maszynie wirtualnej platformy Azure z komputera deweloperskiego za pośrednictwem połączenia aparatu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="13fab-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="13fab-197">Scenariusz B. wdrażanie na maszynie wirtualnej platformy Azure za pomocą rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="13fab-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Wdrażanie na maszynie wirtualnej platformy Azure przy użyciu rejestru platformy Docker](./media/image5-5.png)

<span data-ttu-id="13fab-199">**Rysunek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="13fab-199">**Figure 5-5.**</span></span> <span data-ttu-id="13fab-200">Wdrażanie na maszynie wirtualnej platformy Azure przy użyciu rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="13fab-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="13fab-201">Scenariusz C: wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="13fab-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services](./media/image5-6.png)

<span data-ttu-id="13fab-203">**Rysunek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="13fab-203">**Figure 5-6.**</span></span> <span data-ttu-id="13fab-204">Wdrażanie na maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="13fab-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="13fab-205">Maszyny wirtualne platformy Azure dla kontenerów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="13fab-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="13fab-206">Maszyny wirtualne platformy Azure dla kontenerów systemu Windows są maszynami wirtualnymi opartymi na systemie Windows Server 2016, Windows 10 lub nowszym, zarówno z skonfigurowanym aparatem platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="13fab-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="13fab-207">W większości przypadków system Windows Server 2016 jest używany na maszynach wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="13fab-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="13fab-208">Platforma Azure udostępnia teraz maszynę wirtualną o nazwie **Windows Server 2016 z kontenerami**.</span><span class="sxs-lookup"><span data-stu-id="13fab-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="13fab-209">Za pomocą tej maszyny wirtualnej można wypróbować nową funkcję kontenera systemu Windows Server z systemem Windows Server Core lub Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="13fab-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="13fab-210">Obrazy systemu operacyjnego kontenera są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z platformą Docker.</span><span class="sxs-lookup"><span data-stu-id="13fab-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="13fab-211">Zalety</span><span class="sxs-lookup"><span data-stu-id="13fab-211">Benefits</span></span>

<span data-ttu-id="13fab-212">Chociaż kontenery systemu Windows można wdrażać na lokalnych maszynach wirtualnych z systemem Windows Server 2016, podczas wdrażania na platformie Azure można łatwiej rozpocząć pracę z gotowymi do użycia maszyn wirtualnych kontenerów systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="13fab-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="13fab-213">Możesz również uzyskać wspólną lokalizację online dostępną dla testerów oraz automatyczną skalowalność za pomocą zestawów skalowania maszyn wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="13fab-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="13fab-214">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="13fab-214">Next steps</span></span>

<span data-ttu-id="13fab-215">Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="13fab-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="13fab-216">Przewodnik 4. wdrażanie aplikacji opartych na kontenerach systemu Windows w celu Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="13fab-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="13fab-217">Dostępność przewodnika technicznego</span><span class="sxs-lookup"><span data-stu-id="13fab-217">Technical walkthrough availability</span></span>

<span data-ttu-id="13fab-218">Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub:</span><span class="sxs-lookup"><span data-stu-id="13fab-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="13fab-219">[Wdrażanie aplikacji w usłudze ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="13fab-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="13fab-220">Omówienie</span><span class="sxs-lookup"><span data-stu-id="13fab-220">Overview</span></span>

<span data-ttu-id="13fab-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) to najszybszy sposób tworzenia kontenerów w środowisku deweloperskim/testowym/przejściowym, w którym można wdrożyć pojedyncze wystąpienia kontenerów.</span><span class="sxs-lookup"><span data-stu-id="13fab-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="13fab-222">Wyniki</span><span class="sxs-lookup"><span data-stu-id="13fab-222">Goals</span></span>

<span data-ttu-id="13fab-223">W tym instruktażu przedstawiono główne scenariusze wdrażania kontenerów systemu Windows w programie Azure Container Instances (ACI) oraz sposobu wdrażania aplikacji eShopModernizing w programie ACI.</span><span class="sxs-lookup"><span data-stu-id="13fab-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="13fab-224">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="13fab-224">Scenarios</span></span>

<span data-ttu-id="13fab-225">Mogą istnieć różne odmiany dotyczące wdrażania aplikacji eShopModernizing w programie ACI, takie jak wdrażanie tylko jednej lub wszystkich aplikacji (aplikacja MVC, WebForms lub usługa WCF).</span><span class="sxs-lookup"><span data-stu-id="13fab-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="13fab-226">W poniższym scenariuszu widocznym poniżej można zobaczyć aplikację ASP.NET MVC i kontener SQL Server obu wdrożonych jako kontenery w ACI (Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="13fab-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Wdrażanie w programie ACI z poziomu środowiska programistycznego](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="13fab-228">Zalety</span><span class="sxs-lookup"><span data-stu-id="13fab-228">Benefits</span></span>

<span data-ttu-id="13fab-229">Azure Container Instances ułatwia tworzenie kontenerów platformy Docker na platformie Azure i zarządzanie nimi bez konieczności aprowizacji maszyn wirtualnych ani wdrażania usług wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="13fab-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="13fab-230">Za pomocą ACI można bezpośrednio wdrożyć kontener systemu Windows na platformie Azure i uwidocznić go w Internecie za pomocą w pełni kwalifikowanej nazwy domeny (FQDN) w ciągu kilku sekund (pod warunkiem, że obraz kontenera systemu Windows jest gotowy do użycia w rejestrze Docker, np. w usłudze Docker Hub lub kontenera platformy Azure) Rejestr).</span><span class="sxs-lookup"><span data-stu-id="13fab-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="13fab-231">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13fab-231">Considerations</span></span>

<span data-ttu-id="13fab-232">Wdrażanie kontenerów systemu Windows z pełnymi .NET Framework/ASP.NET lub SQL Server do Azure Container Instances (ACI) nie jest równie szybkie, jak wdrażanie na zwykłych hostach platformy Docker (na przykład w systemie Windows Server 2016 z kontenerami systemu Windows), ponieważ Docker obraz musi zostać pobrany (ściągany z rejestru Docker) za każdym razem, a rozmiary obrazu kontenera SQL (15,1 GB) i obraz kontenera ASP.NET (13,9 GB) są znacznie duże. jest to jednak znacznie tańsze niż utrzymywanie własnego hosta platformy Docker (trwałe online systemu Windows) Serwer 2016 z maszyną wirtualną kontenerów systemu Windows na platformie Azure) nie powinien wymieniać całego programu Orchestrator, takiego jak Kubernetes na platformie Azure (AKS), który z drugiej strony stanowi doskonały wybór dla wdrożeń produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="13fab-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="13fab-233">Jako główne rozwiązanie przy użyciu Azure Container Instances jest bardzo atrakcyjną opcją dla scenariuszy tworzenia i testowania oraz dla potoków ciągłej integracji/ciągłego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="13fab-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="13fab-234">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="13fab-234">Next steps</span></span>

<span data-ttu-id="13fab-235">Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki:</span><span class="sxs-lookup"><span data-stu-id="13fab-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="13fab-236">Przewodnik 5: wdrażanie aplikacji opartych na kontenerach systemu Windows w programie Kubernetes w Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="13fab-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="13fab-237">Dostępność przewodnika technicznego</span><span class="sxs-lookup"><span data-stu-id="13fab-237">Technical walkthrough availability</span></span>

<span data-ttu-id="13fab-238">Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub:</span><span class="sxs-lookup"><span data-stu-id="13fab-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="13fab-239">Omówienie</span><span class="sxs-lookup"><span data-stu-id="13fab-239">Overview</span></span>

<span data-ttu-id="13fab-240">Aplikacja, która jest oparta na kontenerach systemu Windows, będzie szybko potrzebować do użycia Platform, a nawet dalej z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="13fab-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="13fab-241">Jest to konieczne w celu łatwego osiągnięcia wysokiej skalowalności i lepszej automatycznej skalowalności oraz znaczących ulepszeń zautomatyzowanych wdrożeń i przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="13fab-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="13fab-242">Cele te można osiągnąć przy użyciu [Kubernetes](https://kubernetes.io/)programu Orchestrator, dostępnego w usłudze [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="13fab-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="13fab-243">Wyniki</span><span class="sxs-lookup"><span data-stu-id="13fab-243">Goals</span></span>

<span data-ttu-id="13fab-244">Celem tego instruktażu jest nauczenie się, jak wdrożyć aplikację opartą na kontenerach systemu Windows w usłudze Kubernetes (nazywanej również *K8s*) w Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="13fab-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="13fab-245">Wdrażanie do Kubernetes od podstaw jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="13fab-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="13fab-246">Wdróż klaster Kubernetes do Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="13fab-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="13fab-247">Wdróż aplikację i powiązane zasoby w klastrze Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="13fab-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="13fab-248">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="13fab-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="13fab-249">Scenariusz A: wdrażanie bezpośrednio w klastrze Kubernetes z poziomu środowiska deweloperskiego</span><span class="sxs-lookup"><span data-stu-id="13fab-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Wdrażanie bezpośrednio w klastrze Kubernetes z poziomu środowiska deweloperskiego](./media/image5-7.png)

<span data-ttu-id="13fab-251">**Rysunek 5-7.**</span><span class="sxs-lookup"><span data-stu-id="13fab-251">**Figure 5-7.**</span></span> <span data-ttu-id="13fab-252">Wdrażanie bezpośrednio w klastrze Kubernetes z poziomu środowiska deweloperskiego</span><span class="sxs-lookup"><span data-stu-id="13fab-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="13fab-253">Scenariusz B: wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="13fab-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services](./media/image5-8.png)

<span data-ttu-id="13fab-255">**Rysunek 5-8.**</span><span class="sxs-lookup"><span data-stu-id="13fab-255">**Figure 5-8.**</span></span> <span data-ttu-id="13fab-256">Wdrażanie w klastrze Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="13fab-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="13fab-257">Zalety</span><span class="sxs-lookup"><span data-stu-id="13fab-257">Benefits</span></span>

<span data-ttu-id="13fab-258">Wdrożenie w klastrze w programie Kubernetes ma wiele zalet.</span><span class="sxs-lookup"><span data-stu-id="13fab-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="13fab-259">Największą korzyścią jest to, że możesz uzyskać gotowe do użycia środowisko produkcyjne, w którym można skalować aplikację na podstawie liczby wystąpień kontenerów, które mają być używane (skalowalność wewnętrzna w istniejących węzłach) i na podstawie liczby węzłów lub maszyn wirtualnych w klastrze ( globalna skalowalność klastra).</span><span class="sxs-lookup"><span data-stu-id="13fab-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="13fab-260">Azure Container Service optymalizuje popularne narzędzia i technologie "open source" przeznaczone dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="13fab-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="13fab-261">Uzyskasz otwarte rozwiązanie, które oferuje przenośność dla kontenerów i konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13fab-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="13fab-262">Wybierasz rozmiar, liczbę hostów i narzędzie Orchestrator Tools-Container Service obsługuje wszystko inne.</span><span class="sxs-lookup"><span data-stu-id="13fab-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="13fab-263">Dzięki Kubernetes deweloperzy mogą postępować nad maszynami fizycznymi i wirtualnymi, aby zaplanować infrastrukturę skoncentrowaną na kontenerach, która ułatwia między innymi następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="13fab-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="13fab-264">Aplikacje oparte na wielu kontenerach</span><span class="sxs-lookup"><span data-stu-id="13fab-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="13fab-265">Replikowanie wystąpień kontenera i skalowanie w poziomie</span><span class="sxs-lookup"><span data-stu-id="13fab-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="13fab-266">Nazewnictwo i odnajdywanie (na przykład wewnętrzny serwer DNS)</span><span class="sxs-lookup"><span data-stu-id="13fab-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="13fab-267">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="13fab-267">Balancing loads</span></span>

- <span data-ttu-id="13fab-268">Aktualizacje stopniowe</span><span class="sxs-lookup"><span data-stu-id="13fab-268">Rolling updates</span></span>

- <span data-ttu-id="13fab-269">Dystrybuowanie wpisów tajnych</span><span class="sxs-lookup"><span data-stu-id="13fab-269">Distributing secrets</span></span>

- <span data-ttu-id="13fab-270">Kontrole kondycji aplikacji</span><span class="sxs-lookup"><span data-stu-id="13fab-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="13fab-271">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="13fab-271">Next steps</span></span>

<span data-ttu-id="13fab-272">Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="13fab-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="13fab-273">Przewodnik 6. wdrażanie aplikacji opartych na kontenerach systemu Windows w celu Azure App Service dla kontenerów</span><span class="sxs-lookup"><span data-stu-id="13fab-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="13fab-274">Dostępność przewodnika technicznego</span><span class="sxs-lookup"><span data-stu-id="13fab-274">Technical walkthrough availability</span></span>

<span data-ttu-id="13fab-275">Pełny przewodnik techniczny jest dostępny na stronie wiki repozytorium eShopModernizing GitHub:</span><span class="sxs-lookup"><span data-stu-id="13fab-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="13fab-276">Omówienie</span><span class="sxs-lookup"><span data-stu-id="13fab-276">Overview</span></span>

<span data-ttu-id="13fab-277">Prostą aplikację kontenerową korzystającą z kontenerów systemu Windows można łatwo wdrożyć do Azure App Service dla kontenerów.</span><span class="sxs-lookup"><span data-stu-id="13fab-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="13fab-278">Jest to zalecane podejście dla większości aplikacji opartych na kontenerach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="13fab-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="13fab-279">Wyniki</span><span class="sxs-lookup"><span data-stu-id="13fab-279">Goals</span></span>

<span data-ttu-id="13fab-280">Celem tego instruktażu jest nauczenie się, jak wdrożyć aplikację opartą na kontenerach systemu Windows w celu Azure App Service kontenerów z rejestru (centrum Docker lub Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="13fab-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="13fab-281">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="13fab-281">Scenario</span></span>

![Wdrażanie aplikacji opartej na kontenerze systemu Windows w celu Azure App Service dla kontenerów](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="13fab-283">Zalety</span><span class="sxs-lookup"><span data-stu-id="13fab-283">Benefits</span></span>

<span data-ttu-id="13fab-284">Wdrożenie do Azure App Service for Containers oferuje zalety kontenerów sparowanych z zaletami Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="13fab-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="13fab-285">Usługa App Service może być łatwo skalowana w pionie i w poziomie i można ją skonfigurować do automatycznego skalowania w celu spełnienia zmienionych wymagań.</span><span class="sxs-lookup"><span data-stu-id="13fab-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="13fab-286">Aktualizacje mogą być przeprowadzane z zerowym przestojem, a Konfiguracja ciągłego wdrażania z rejestru jest również łatwa do skonfigurowania.</span><span class="sxs-lookup"><span data-stu-id="13fab-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="13fab-287">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="13fab-287">Next steps</span></span>

<span data-ttu-id="13fab-288">Więcej szczegółowych informacji na ten temat znajduje się w witrynie GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="13fab-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="13fab-289">[Poprzedni](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [dalej](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="13fab-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
