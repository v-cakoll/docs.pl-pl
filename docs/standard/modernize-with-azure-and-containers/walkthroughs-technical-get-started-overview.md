---
title: Przewodniki i technicznych wprowadzająca
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów Windows | Przewodniki i technicznych wprowadzająca
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 41fbeb3abc201ef03cf0c237a069e7687c98dd18
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519785"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="ac4cb-103">Przewodniki i technicznych wprowadzająca</span><span class="sxs-lookup"><span data-stu-id="ac4cb-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="ac4cb-104">Aby ograniczyć rozmiar tę książkę elektroniczną, dodatkową dokumentację techniczną i pełne przewodniki zostały udostępnione w repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="ac4cb-105">Online instruktaży, które jest opisane w tym rozdziale omówiono krok po kroku instalacji wielu środowisk, które są oparte na Windows kontenerów i wdrażanie na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="ac4cb-106">W poniższych sekcjach opisano, co poszczególnych przewodników o jego celów i wysokiego poziomu wizji i zawiera diagram zadania, które są zaangażowane.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="ac4cb-107">Możesz uzyskać wskazówki, samodzielnie w *eShopModernizing* aplikacje typu wiki repozytorium GitHub na [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="ac4cb-108">Lista technicznym</span><span class="sxs-lookup"><span data-stu-id="ac4cb-108">Technical walkthrough list</span></span>

<span data-ttu-id="ac4cb-109">Poniższe przewodniki get-started zapewniają spójne i wyczerpujące wskazówki techniczne dotyczące przykładowe aplikacje, które można podnieść i shift przy użyciu kontenerów, a następnie przesuń przy użyciu wielu opcji wdrażania na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="ac4cb-110">Każda z poniższych instruktażach używa nowych przykładowych eShopLegacy i eShopModernizing aplikacji, które są dostępne w usłudze GitHub w [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="ac4cb-111">**Przewodnik po przykładzie eShop starsze aplikacje (aplikacje linii bazowej w celu zmodernizowania)**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="ac4cb-112">**Konteneryzowanie istniejących aplikacji sieci web platformy ASP.NET (WebForms i MVC) przy użyciu kontenerów Windows**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="ac4cb-113">**Konteneryzowanie istniejącej usług WCF (aplikacje N-warstwowej) za pomocą kontenerów Windows**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="ac4cb-114">**Wdrażanie aplikacji opartych na kontenerach Windows na maszynach wirtualnych platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="ac4cb-115">**Wdrażanie aplikacji opartych na kontenerach Windows do rozwiązania Kubernetes w usłudze Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="ac4cb-116">**Wdrażanie aplikacji opartych na kontenerach Windows w usłudze Azure Service Fabric**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="ac4cb-117">Przewodnik 1: Przewodnik po przykładzie eShop starszych aplikacji</span><span class="sxs-lookup"><span data-stu-id="ac4cb-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ac4cb-118">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="ac4cb-118">Technical walkthrough availability</span></span>

<span data-ttu-id="ac4cb-119">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="ac4cb-120">wskazówki dotyczące witryny typu wiki eShopModernizing</span><span class="sxs-lookup"><span data-stu-id="ac4cb-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="ac4cb-121">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ac4cb-121">Overview</span></span>

<span data-ttu-id="ac4cb-122">W tym przewodniku możesz eksplorować wstępnej implementacji trzy próbki starszych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="ac4cb-123">Pierwsze dwie przykładowe aplikacje sieci web mają monolityczne architektury i zostały utworzone za pomocą klasycznego programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="ac4cb-124">Jedna aplikacja opiera się na platformie ASP.NET 4.x MVC; druga aplikacja opiera się na formularzach sieci Web programu ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="ac4cb-125">Trzeci aplikacja jest aplikacją 3-warstwowej aplikacji formularzy WinForms klienta i po stronie serwera [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) usługi.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="ac4cb-126">Te aplikacje są dostępne pod adresem [repozytorium GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="ac4cb-127">Cele</span><span class="sxs-lookup"><span data-stu-id="ac4cb-127">Goals</span></span>

<span data-ttu-id="ac4cb-128">Głównym celem tego przewodnika jest po prostu zapoznać się z tych aplikacji i ich kodu i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="ac4cb-129">Aplikacje można skonfigurować tak, aby wygenerować i użyć danych testowych, bez korzystania z bazy danych SQL do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="ac4cb-130">Ta opcjonalna konfiguracja opiera się na iniekcji zależności w sposób odłączony.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="ac4cb-131">Scenariusz 1: Aplikacje ASP.NET sieci Web</span><span class="sxs-lookup"><span data-stu-id="ac4cb-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="ac4cb-132">Na poniższym rysunku przedstawiono prosty scenariusz oryginalnego starsze aplikacje sieci web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![Architektura Prosty scenariusz oryginalnego starsze aplikacje sieci web platformy ASP.NET](./media/image5-1.png)
>

<span data-ttu-id="ac4cb-134">Z punktu widzenia domeny biznesowej obie aplikacje oferują tego samego katalogu funkcje zarządzania.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="ac4cb-135">Członkowie zespołu enterprise eShop użyć jej do wyświetlania i edytowania katalogu produktów.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="ac4cb-136">Na kolejnej ilustracji przedstawiono zrzuty ekranu aplikacji początkowej.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-136">The next figure shows the initial app screenshots.</span></span>

![Aplikacje platformy ASP.NET MVC i formularzy sieci Web platformy ASP.NET (istniejącej starszych technologiach)](./media/image5-2.png)

<span data-ttu-id="ac4cb-138">Zależności w programie ASP.NET 4.x i jego wcześniejsze wersje, (zarówno dla platformy MVC i formularzy sieci Web) oznacza, że te aplikacje nie będą uruchamiane na platformie .NET Core, chyba że kod jest w pełni przepisany przy użyciu platformy ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="ac4cb-139">Scenariusz 2: Usługi WCF i aplikację kliencką WinForms (3-warstwowej aplikacji)</span><span class="sxs-lookup"><span data-stu-id="ac4cb-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="ac4cb-140">Na poniższym rysunku przedstawiono prosty scenariusz oryginalnego starszych aplikacji 3-warstwowej.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![Architektura Prosty scenariusz oryginalnego starszych aplikacji 3-warstwowej przy użyciu usługi WCF i aplikację kliencką WinForms](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="ac4cb-142">Zalety</span><span class="sxs-lookup"><span data-stu-id="ac4cb-142">Benefits</span></span>

<span data-ttu-id="ac4cb-143">Korzyści wynikające z tego przewodnika są proste: po prostu zapoznać się z kodem i początkowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ac4cb-144">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ac4cb-144">Next steps</span></span>

<span data-ttu-id="ac4cb-145">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="ac4cb-146">Samouczek linii bazowej platformy ASP.NET MVC i formularzy sieci Web "starszych" aplikacji</span><span class="sxs-lookup"><span data-stu-id="ac4cb-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="ac4cb-147">Samouczek na temat usługi WCF linii bazowej i aplikacja "starszych" (3-warstwowej) WinForms</span><span class="sxs-lookup"><span data-stu-id="ac4cb-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="ac4cb-148">Przewodnik 2: Konteneryzowanie istniejącej aplikacji .NET za pomocą kontenerów Windows</span><span class="sxs-lookup"><span data-stu-id="ac4cb-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="ac4cb-149">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ac4cb-149">Overview</span></span>

<span data-ttu-id="ac4cb-150">Korzystaj z kontenerów Windows, w celu wdrożenia istniejących aplikacji .NET, takich jak te oparte na WCF, MVC i formularzy sieci Web w środowisku produkcyjnym, programowania i środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ac4cb-151">Cele</span><span class="sxs-lookup"><span data-stu-id="ac4cb-151">Goals</span></span>

<span data-ttu-id="ac4cb-152">Celem tego przewodnika jest, aby pokazać Ci kilka opcji konteneryzowania istniejącej aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="ac4cb-153">Można:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-153">You can:</span></span>

- <span data-ttu-id="ac4cb-154">Konteneryzowanie aplikacji przy użyciu [Visual Studio 2017 r Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowsze wersje).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="ac4cb-155">Konteneryzowanie aplikacji, ręcznie dodając [pliku Dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie używając [interfejsu wiersza polecenia Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="ac4cb-156">Konteneryzowanie aplikacji przy użyciu [Img2Docker](https://github.com/docker/communitytools-image2docker-win) narzędzia (narzędzie typu open-source docker).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="ac4cb-157">Ten przewodnik koncentruje się na Visual Studio Tools 2017 podejścia platformy Docker, ale pozostałe dwie metody są podobne rozumieniu przy użyciu plików Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="ac4cb-158">Scenariusz 1: Aplikacje sieci web ASP.NET konteneryzowanych</span><span class="sxs-lookup"><span data-stu-id="ac4cb-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="ac4cb-159">Na poniższym rysunku przedstawiono scenariusz konteneryzowanych eShop starszych internetowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![Diagram architektury uproszczone kontenerowych nimi aplikacji ASP.NET w środowisku programistycznym](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="ac4cb-161">Scenariusz 2: Przekazywanie Usługa WCF konteneryzowanych</span><span class="sxs-lookup"><span data-stu-id="ac4cb-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="ac4cb-162">Na poniższym rysunku przedstawiono scenariusz, w przypadku aplikacji 3-warstwowej przy użyciu konteneryzowana Usługa WCF.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![Uproszczony diagram architektury konteneryzowane usługi WCF w środowisku programistycznym](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="ac4cb-164">Zalety</span><span class="sxs-lookup"><span data-stu-id="ac4cb-164">Benefits</span></span>

<span data-ttu-id="ac4cb-165">Istnieją zalety łączenia uruchamiania aplikacji monolitycznych w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="ac4cb-166">Najpierw należy utworzyć obraz dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-166">First, you create an image for the application.</span></span> <span data-ttu-id="ac4cb-167">Od tego momentu każde wdrożenie jest uruchamiane w tym samym środowisku.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="ac4cb-168">Każdy kontener korzysta z tej samej wersji systemu operacyjnego, ma tę samą wersję zależności zainstalowane, korzysta z tej samej wersji programu .NET framework i powstała przy użyciu tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="ac4cb-169">Zasadniczo możesz kontrolować zależności aplikacji przy użyciu obrazu platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="ac4cb-170">Zależności są przesyłane przy użyciu aplikacji podczas wdrażania kontenerów.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="ac4cb-171">Dodatkową korzyścią jest to, że deweloperzy mogą uruchomić aplikację w spójne środowisko, które są dostarczane przez kontenery Windows.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="ac4cb-172">Problemy, które są wyświetlane tylko w przypadku niektórych wersji mogą wykrył od razu, zamiast, dzięki czemu są ujawniane w środowisku tymczasowym czy produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="ac4cb-173">Różnice w środowiskach programistycznych, które posługują się członkowie zespołu rozwoju znaczenia mniejsza, gdy aplikacje są uruchamiane w kontenerach.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="ac4cb-174">Konteneryzowane aplikacje mają również płaski krzywej skalowalnego w poziomie.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="ac4cb-175">Konteneryzowanych aplikacji pozwalają na więcej aplikacji i wystąpień usługi (oparte na kontenerach) w maszynie Wirtualnej lub komputera fizycznego w porównaniu do regularnego acji dla poszczególnych komputerów.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="ac4cb-176">Przekłada się to wyższych gęstości, a mniej wymaganych zasobów, szczególnie w przypadku, gdy używasz koordynatorów, takich jak Kubernetes lub usługi Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="ac4cb-177">Konteneryzacji w sytuacjach, idealnym rozwiązaniem, nie wymaga wprowadzania żadnych zmian w kodzie aplikacji (C\#).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="ac4cb-178">W większości przypadków wystarczy Docker wdrożenia metadanych plików (pliki Dockerfile i narzędzia Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="ac4cb-179">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ac4cb-179">Next steps</span></span>

<span data-ttu-id="ac4cb-180">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="ac4cb-181">Jak konteneryzowanie aplikacji sieci web .NET Framework za pomocą Windows kontenery i Docker</span><span class="sxs-lookup"><span data-stu-id="ac4cb-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="ac4cb-182">Dodawanie obsługi platformy Docker do usługi WCF</span><span class="sxs-lookup"><span data-stu-id="ac4cb-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="ac4cb-183">Przewodnik 3: Wdrażanie aplikacji opartych na kontenerach Windows na maszynach wirtualnych platformy Azure</span><span class="sxs-lookup"><span data-stu-id="ac4cb-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ac4cb-184">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="ac4cb-184">Technical walkthrough availability</span></span>

<span data-ttu-id="ac4cb-185">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="ac4cb-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="ac4cb-186">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ac4cb-186">Overview</span></span>

<span data-ttu-id="ac4cb-187">Wdrażanie hosta platformy Docker na system Windows Server 2016 maszyny wirtualnej (VM) na platformie Azure umożliwia szybkie konfigurowanie środowisk projektowania/testów/wdrażanie przejściowe.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="ac4cb-188">Oferuje on również typowe miejscu dla testerów lub użytkownicy biznesowi sprawdzić poprawność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="ac4cb-189">Maszyny wirtualne również mogą być prawidłowe infrastruktury jako środowisk produkcyjnych usługi (IaaS).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ac4cb-190">Cele</span><span class="sxs-lookup"><span data-stu-id="ac4cb-190">Goals</span></span>

<span data-ttu-id="ac4cb-191">Celem tego przewodnika jest aby pokazać Ci kilka rozwiązań alternatywnych, do których masz podczas wdrażania kontenerów Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ac4cb-192">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="ac4cb-192">Scenarios</span></span>

<span data-ttu-id="ac4cb-193">W tym przewodniku znajdują się kilku scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="ac4cb-194">Scenariusz A: Wdrażanie na Maszynie wirtualnej platformy Azure, od deweloperów komputera za pośrednictwem połączenia aparat platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ac4cb-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Wdrażanie na Maszynie wirtualnej platformy Azure od deweloperów komputera za pośrednictwem połączenia aparat platformy Docker](./media/image5-4.png)

> <span data-ttu-id="ac4cb-196">**Rysunek 5-4.**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-196">**Figure 5-4.**</span></span> <span data-ttu-id="ac4cb-197">Wdrażanie na Maszynie wirtualnej platformy Azure od deweloperów komputera za pośrednictwem połączenia aparat platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ac4cb-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="ac4cb-198">Scenariusz B: Wdrażanie na maszynie Wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ac4cb-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker](./media/image5-5.png)

> <span data-ttu-id="ac4cb-200">**Rysunek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-200">**Figure 5-5.**</span></span> <span data-ttu-id="ac4cb-201">Wdrażanie na maszynie Wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ac4cb-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ac4cb-202">Scenariusz C: wdrożyć na Maszynie wirtualnej platformy Azure z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="ac4cb-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Wdrożyć Maszynę wirtualną platformy Azure z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure](./media/image5-6.png)

> <span data-ttu-id="ac4cb-204">**Rysunek 5 – 6.**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-204">**Figure 5-6.**</span></span> <span data-ttu-id="ac4cb-205">Wdrożyć Maszynę wirtualną platformy Azure z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="ac4cb-205">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="ac4cb-206">Maszyny wirtualne platformy Azure dla kontenerów Windows</span><span class="sxs-lookup"><span data-stu-id="ac4cb-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="ac4cb-207">Maszyny wirtualne dla Windows kontenery usługi Azure maszyn wirtualnych opartych na systemie Windows Server 2016, Windows 10 lub nowszy, konfigurowanie zarówno z aparatem Docker.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="ac4cb-208">W większości przypadków systemu Windows Server 2016 jest używana w maszynach wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="ac4cb-209">System Azure oferuje obecnie Maszynę wirtualną o nazwie **systemu Windows Server 2016 z kontenerami**.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="ac4cb-210">Korzystanie z tej maszyny Wirtualnej, do wypróbowania nowej funkcji kontenera z systemem Windows Server z systemu Windows Server Core lub Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="ac4cb-211">Kontener obrazów systemu operacyjnego są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z platformą Docker.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="ac4cb-212">Zalety</span><span class="sxs-lookup"><span data-stu-id="ac4cb-212">Benefits</span></span>

<span data-ttu-id="ac4cb-213">Mimo, że kontenery Windows można wdrożyć do lokalnego systemu Windows Server 2016 maszyn wirtualnych, w przypadku wdrażania na platformie Azure, możesz uzyskać łatwiejszy sposób, aby rozpocząć pracę, przy użyciu gotowych do użycia kontener maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="ac4cb-214">Możesz także uzyskać wspólnej lokalizacji online, który jest dostępny dla testerów i automatyczne skalowalności za pomocą zestawów skalowania maszyn wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ac4cb-215">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ac4cb-215">Next steps</span></span>

<span data-ttu-id="ac4cb-216">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="ac4cb-217">Przewodnik po 4: Wdrażanie aplikacji opartych na kontenerach Windows Azure Container instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="ac4cb-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ac4cb-218">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="ac4cb-218">Technical walkthrough availability</span></span>

<span data-ttu-id="ac4cb-219">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="ac4cb-220">[Wdrażanie aplikacji w usłudze aci Uzyskaj (wystąpienia kontenera platformy Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="ac4cb-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="ac4cb-221">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ac4cb-221">Overview</span></span>

<span data-ttu-id="ac4cb-222">[Usługa Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) jest najszybszym sposobem kontenerów środowiska dev/test/wdrażanie przejściowe, którym można wdrożyć z pojedynczego wystąpienia kontenerów.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="ac4cb-223">Cele</span><span class="sxs-lookup"><span data-stu-id="ac4cb-223">Goals</span></span>

<span data-ttu-id="ac4cb-224">W tym przewodniku przedstawiono główne scenariusze wdrażania kontenerów Windows do usługi Azure Container Instances (ACI) i jak można wdrażać aplikacje eShopModernizing w usłudze ACI.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ac4cb-225">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="ac4cb-225">Scenarios</span></span>

<span data-ttu-id="ac4cb-226">Może to być różnice dotyczące wdrażania aplikacji eShopModernizing w usłudze ACI, takie jak wdrożenie tylko jednej lub wszystkich aplikacji (aplikacji MVC, aplikacja formularzy sieci Web lub usługi WCF).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="ac4cb-227">W poniższym scenariuszu przedstawionym poniżej widać aplikacji ASP.NET MVC oraz kontener programu SQL Server, oba jest wdrażane jako kontenery w usłudze ACI (usługi Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Wdrażanie usługi ACI z środowiska deweloperskiego](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="ac4cb-229">Zalety</span><span class="sxs-lookup"><span data-stu-id="ac4cb-229">Benefits</span></span>

<span data-ttu-id="ac4cb-230">Usługa Azure Container Instances ułatwia tworzenie i zarządzanie nimi kontenerów platformy Docker na platformie Azure, bez konieczności aprowizowania maszyn wirtualnych lub stosowania usługi wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="ac4cb-231">Za pomocą usługi ACI można bezpośrednio wdrożyć kontener Windows na platformie Azure i ujawnisz go w Internecie przy użyciu w pełni kwalifikowaną nazwę domeny (FQDN) w ciągu kilku sekund (pod warunkiem, że masz gotowy obraz Windows kontenera w rejestrze Docker, takich jak usługi Docker Hub lub Azure Container Rejestr).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="ac4cb-232">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac4cb-232">Considerations</span></span>

<span data-ttu-id="ac4cb-233">Wdrażanie kontenerów Windows przy użyciu albo pełny program .NET Framework / platformy ASP.NET lub program SQL Server do usługi Azure Container Instances (ACI) nie jest dość tak szybko, jak wdrażanie regularne hosta platformy Docker (np. Windows Server 2016 z kontenerami Windows), ponieważ obraz platformy Docker musi być pobrany (ściągnięty z rejestru platformy Docker), każdym razem, gdy i obraz kontenera SQL (15.1 GB) i obrazu kontenera platformy ASP.NET (13.9 GB) są znacznie dużych, jednak jest znacznie tańsze niż utrzymywania własnego hosta platformy docker (trwale online Windows Server 2016 z maszyną Wirtualną z kontenerów Windows na platformie Azure) nie, aby wspomnieć o całego programu orchestrator, takich jak Kubernetes na platformie Azure (usługi AKS/ACS) lub Azure Service Fabric, które są z drugiej strony, doskonały wybór w przypadku wdrożeń produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="ac4cb-234">Jako podstawowy wniosek za pomocą usługi Azure Container Instances jest to opcja niezwykle atrakcyjne rozwiązanie dla scenariuszy deweloperskich lub testowych oraz dla potoków ciągłej integracji/ciągłego Dostarczania.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ac4cb-235">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ac4cb-235">Next steps</span></span>

<span data-ttu-id="ac4cb-236">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="ac4cb-237">Przewodnik po 5: Wdrażanie aplikacji opartych na kontenerach Windows do rozwiązania Kubernetes w usłudze Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="ac4cb-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ac4cb-238">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="ac4cb-238">Technical walkthrough availability</span></span>

<span data-ttu-id="ac4cb-239">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="ac4cb-240">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ac4cb-240">Overview</span></span>

<span data-ttu-id="ac4cb-241">Aplikacja, która opiera się na kontenery Windows szybko będą musieli używać platform, jeszcze bardziej odpływowi z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="ac4cb-242">To jest potrzebna do łatwo osiągnąć wysoką skalowalność lepiej automatycznego skalowania i znaczne ulepszenia w zautomatyzowane wdrożenia oraz zarządzanie ich wersjami.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="ac4cb-243">Można osiągnąć te cele przy użyciu koordynatora [Kubernetes](https://kubernetes.io/), która jest dostępna w [usług Azure Container Service](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="ac4cb-244">Cele</span><span class="sxs-lookup"><span data-stu-id="ac4cb-244">Goals</span></span>

<span data-ttu-id="ac4cb-245">Celem tego przewodnika jest Dowiedz się, jak wdrażanie aplikacji dla komputerów z systemem Windows kontenera w usłudze Kubernetes (nazywane również *K8s*) w usłudze Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="ac4cb-246">Wdrażanie od zera rozwiązania Kubernetes jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="ac4cb-247">Wdrażanie klastra Kubernetes w usłudze Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="ac4cb-248">Wdrażanie aplikacji i powiązanych zasobów do klastra Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ac4cb-249">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="ac4cb-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="ac4cb-250">Scenariusz A: Wdróż bezpośrednio w klastrze Kubernetes w środowisku deweloperskim</span><span class="sxs-lookup"><span data-stu-id="ac4cb-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Wdróż bezpośrednio w klastrze Kubernetes z poziomu środowiska projektowego](./media/image5-7.png)

> <span data-ttu-id="ac4cb-252">**Rysunek 5 – 7.**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-252">**Figure 5-7.**</span></span> <span data-ttu-id="ac4cb-253">Wdróż bezpośrednio w klastrze Kubernetes z poziomu środowiska projektowego</span><span class="sxs-lookup"><span data-stu-id="ac4cb-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ac4cb-254">Scenariusz B: wdrażanie klastra Kubernetes z ciągłej integracji/ciągłego wdrażania potoków w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="ac4cb-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Wdrażanie klastra Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure](./media/image5-8.png)

> <span data-ttu-id="ac4cb-256">**Rysunek 5 – 8.**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-256">**Figure 5-8.**</span></span> <span data-ttu-id="ac4cb-257">Wdrażanie klastra Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="ac4cb-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="ac4cb-258">Zalety</span><span class="sxs-lookup"><span data-stu-id="ac4cb-258">Benefits</span></span>

<span data-ttu-id="ac4cb-259">Istnieje wiele korzyści dla wdrażania w klastrze na platformie Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="ac4cb-260">Największa zaleta jest znaczny środowisko gotowe do produkcji, w którym można skalować w poziomie aplikacji, w oparciu o liczbę wystąpień kontenera, mają być używane (wewnętrzny skalowalności istniejących węzłów), a na podstawie liczby węzłów lub maszyn wirtualnych w (klastra globalną skalowalność klastra).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="ac4cb-261">Usługa Azure Container Service optymalizuje popularnych narzędzi typu open source i technologii, pod kątem platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="ac4cb-262">Uzyskujesz otwarte rozwiązanie, przenośność, kontenerów i konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="ac4cb-263">Wybierasz rozmiar, liczbę hostów i orchestrator narzędzia Container Service zajmuje się całą resztą.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="ac4cb-264">Przy użyciu rozwiązania Kubernetes deweloperzy mogą postępu z myśleć o fizycznych i maszyn wirtualnych do planowania infrastruktury skoncentrowane na kontener, który ułatwia następujące funkcje, między innymi:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="ac4cb-265">Aplikacje oparte na wielu kontenerów</span><span class="sxs-lookup"><span data-stu-id="ac4cb-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="ac4cb-266">Replikowanie wystąpień kontenera oraz skalowanie automatyczne w poziomie</span><span class="sxs-lookup"><span data-stu-id="ac4cb-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="ac4cb-267">Nazewnictwo i odnajdywania (na przykład wewnętrznego serwera DNS)</span><span class="sxs-lookup"><span data-stu-id="ac4cb-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="ac4cb-268">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="ac4cb-268">Balancing loads</span></span>

- <span data-ttu-id="ac4cb-269">Aktualizacje stopniowe</span><span class="sxs-lookup"><span data-stu-id="ac4cb-269">Rolling updates</span></span>

- <span data-ttu-id="ac4cb-270">Dystrybucja wpisów tajnych</span><span class="sxs-lookup"><span data-stu-id="ac4cb-270">Distributing secrets</span></span>

- <span data-ttu-id="ac4cb-271">Kontrole kondycji aplikacji</span><span class="sxs-lookup"><span data-stu-id="ac4cb-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="ac4cb-272">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ac4cb-272">Next steps</span></span>

<span data-ttu-id="ac4cb-273">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="ac4cb-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="ac4cb-274">Przewodnik 6: Wdrażanie aplikacji opartych na kontenerach Windows do usługi Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="ac4cb-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ac4cb-275">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="ac4cb-275">Technical walkthrough availability</span></span>

<span data-ttu-id="ac4cb-276">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="ac4cb-277">Omówienie</span><span class="sxs-lookup"><span data-stu-id="ac4cb-277">Overview</span></span>

<span data-ttu-id="ac4cb-278">Aplikacji opartej na Windows kontenery szybko musi korzystać z platform, jeszcze bardziej odpływowi z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="ac4cb-279">To jest potrzebna do łatwo osiągnąć wysoką skalowalność lepiej automatycznego skalowania i znaczne ulepszenia w zautomatyzowane wdrożenia oraz zarządzanie ich wersjami.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="ac4cb-280">Można osiągnąć te cele przy użyciu koordynatora usługi Azure Service Fabric, która jest dostępna w chmurze platformy Azure, ale także dostępne do użycia w środowisku lokalnym, lub nawet w innej chmurze publicznej.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="ac4cb-281">Cele</span><span class="sxs-lookup"><span data-stu-id="ac4cb-281">Goals</span></span>

<span data-ttu-id="ac4cb-282">Celem tego przewodnika jest informacje o sposobie wdrażania aplikacji dla komputerów z systemem Windows kontenera w klastrze usługi Service Fabric na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="ac4cb-283">Wdrażanie usługi Service Fabric od podstaw jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="ac4cb-284">Wdrażanie klastra usługi Service Fabric na platformie Azure (lub do innego środowiska).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="ac4cb-285">Wdrażanie aplikacji i powiązanych zasobów do klastra usługi Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ac4cb-286">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="ac4cb-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="ac4cb-287">Scenariusz A: Wdróż bezpośrednio do klastra usługi Service Fabric w środowisku deweloperskim</span><span class="sxs-lookup"><span data-stu-id="ac4cb-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Wdróż bezpośrednio do klastra usługi Service Fabric z poziomu środowiska projektowego](./media/image5-9.png)

> <span data-ttu-id="ac4cb-289">**Rysunek 5-9.**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-289">**Figure 5-9.**</span></span> <span data-ttu-id="ac4cb-290">Wdróż bezpośrednio do klastra usługi Service Fabric z poziomu środowiska projektowego</span><span class="sxs-lookup"><span data-stu-id="ac4cb-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ac4cb-291">Scenariusz B: wdrażanie klastra usługi Service Fabric z ciągłej integracji/ciągłego wdrażania potoków w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="ac4cb-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Wdrożyć klaster usługi Service Fabric z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure](./media/image5-10.png)

> <span data-ttu-id="ac4cb-293">**Rysunek 5 – 10.**</span><span class="sxs-lookup"><span data-stu-id="ac4cb-293">**Figure 5-10.**</span></span> <span data-ttu-id="ac4cb-294">Wdrożyć klaster usługi Service Fabric z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="ac4cb-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

## <a name="benefits"></a><span data-ttu-id="ac4cb-295">Zalety</span><span class="sxs-lookup"><span data-stu-id="ac4cb-295">Benefits</span></span>

<span data-ttu-id="ac4cb-296">Korzyści z wdrożenia w klastrze w usłudze Service Fabric są podobne do korzyści z używania platformy Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="ac4cb-297">Jedną różnicą jest jednak to, że Usługa Service Fabric to bardziej dojrzałych środowiska produkcyjnego dla aplikacji Windows, w porównaniu do rozwiązania Kubernetes, który jest w fazie beta dla kontenerów Windows w usłudze Kubernetes wersji 1.9 (grudnia 2017 r.).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="ac4cb-298">Kubernetes to bardziej dojrzałych środowisko dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="ac4cb-299">Główną zaletą przy użyciu usługi Azure Service Fabric jest znaczny środowisko gotowe do produkcji, w którym można skalować w poziomie aplikacji, w oparciu o liczbę wystąpień kontenera, mają być używane (wewnętrzny skalowalności istniejących węzłów), a na podstawie liczby węzły lub maszyny wirtualne w klastrze (globalną skalowalność klastra).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="ac4cb-300">Usługa Azure Service Fabric zapewnia przenośność kontenerów i konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="ac4cb-301">Masz usługi Service Fabric klaster na platformie Azure lub ją zainstalować lokalnie we własnym centrum danych.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="ac4cb-302">Można nawet zainstalować klaster usługi Service Fabric w innej chmurze, takie jak [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="ac4cb-303">Dzięki usłudze Service Fabric deweloperzy mogą postępu z myśleć o fizycznych i maszyn wirtualnych do planowania infrastruktury skoncentrowane na kontener, który ułatwia następujące funkcje, między innymi:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="ac4cb-304">Aplikacje oparte na wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="ac4cb-305">Replikowanie wystąpień kontenera oraz skalowanie automatyczne w poziomie.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="ac4cb-306">Nazewnictwo i odnajdywania (na przykład wewnętrznego serwera DNS).</span><span class="sxs-lookup"><span data-stu-id="ac4cb-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="ac4cb-307">Równoważenie obciążenia.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-307">Balancing loads.</span></span>

- <span data-ttu-id="ac4cb-308">Stopniowe aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-308">Rolling updates.</span></span>

- <span data-ttu-id="ac4cb-309">Dystrybucja wpisów tajnych.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-309">Distributing secrets.</span></span>

- <span data-ttu-id="ac4cb-310">Kontrole kondycji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-310">Application health checks.</span></span>

<span data-ttu-id="ac4cb-311">Wyłączne w usłudze Service Fabric (w porównaniu do innych orkiestratorów) są następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="ac4cb-312">Możliwości usług stanowych przy użyciu usług Reliable Services w modelu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="ac4cb-313">Aktorzy wzorca za pomocą modelu aplikacji Reliable Actors.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="ac4cb-314">Wdrażaj bez kości procesów, oprócz kontenery Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="ac4cb-315">Zaawansowane aktualizacje stopniowe i kontroli kondycji.</span><span class="sxs-lookup"><span data-stu-id="ac4cb-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ac4cb-316">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ac4cb-316">Next steps</span></span>

<span data-ttu-id="ac4cb-317">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="ac4cb-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="ac4cb-318">[Poprzednie](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[dalej](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="ac4cb-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
