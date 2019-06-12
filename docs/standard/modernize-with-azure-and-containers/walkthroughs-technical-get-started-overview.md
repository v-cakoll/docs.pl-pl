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
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="31aa7-103">Omówienie przewodników i wprowadzającej dokumentacji technicznej</span><span class="sxs-lookup"><span data-stu-id="31aa7-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="31aa7-104">Aby ograniczyć rozmiar tę książkę elektroniczną, dodatkową dokumentację techniczną i pełne przewodniki zostały udostępnione w repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="31aa7-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="31aa7-105">Online instruktaży, które jest opisane w tym rozdziale omówiono krok po kroku instalacji wielu środowisk, które są oparte na Windows kontenerów i wdrażanie na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="31aa7-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="31aa7-106">W poniższych sekcjach opisano, co poszczególnych przewodników o jego celów i wysokiego poziomu wizji i zawiera diagram zadania, które są zaangażowane.</span><span class="sxs-lookup"><span data-stu-id="31aa7-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="31aa7-107">Możesz uzyskać wskazówki, samodzielnie w *eShopModernizing* aplikacje typu wiki repozytorium GitHub na <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span><span class="sxs-lookup"><span data-stu-id="31aa7-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="31aa7-108">Lista technicznym</span><span class="sxs-lookup"><span data-stu-id="31aa7-108">Technical walkthrough list</span></span>

<span data-ttu-id="31aa7-109">Poniższe przewodniki get-started zapewniają spójne i wyczerpujące wskazówki techniczne dotyczące przykładowe aplikacje, które można podnieść i shift przy użyciu kontenerów, a następnie przesuń przy użyciu wielu opcji wdrażania na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="31aa7-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="31aa7-110">Każda z poniższych instruktażach używa nowych przykładowych eShopLegacy i eShopModernizing aplikacji, które są dostępne w usłudze GitHub w <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="31aa7-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="31aa7-111">**Przewodnik po przykładzie eShop starsze aplikacje (aplikacje linii bazowej w celu zmodernizowania)**</span><span class="sxs-lookup"><span data-stu-id="31aa7-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="31aa7-112">**Konteneryzowanie istniejących aplikacji sieci web platformy ASP.NET (WebForms i MVC) przy użyciu kontenerów Windows**</span><span class="sxs-lookup"><span data-stu-id="31aa7-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="31aa7-113">**Konteneryzowanie istniejącej usług WCF (aplikacje N-warstwowej) za pomocą kontenerów Windows**</span><span class="sxs-lookup"><span data-stu-id="31aa7-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="31aa7-114">**Wdrażanie aplikacji opartych na kontenerach Windows na maszynach wirtualnych platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="31aa7-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="31aa7-115">**Wdrażanie aplikacji opartych na kontenerach Windows do rozwiązania Kubernetes w usłudze Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="31aa7-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="31aa7-116">Przewodnik 1: Przewodnik po przykładzie eShop starszych aplikacji</span><span class="sxs-lookup"><span data-stu-id="31aa7-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="31aa7-117">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="31aa7-117">Technical walkthrough availability</span></span>

<span data-ttu-id="31aa7-118">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="31aa7-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="31aa7-119">wskazówki dotyczące witryny typu wiki eShopModernizing</span><span class="sxs-lookup"><span data-stu-id="31aa7-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="31aa7-120">Omówienie</span><span class="sxs-lookup"><span data-stu-id="31aa7-120">Overview</span></span>

<span data-ttu-id="31aa7-121">W tym przewodniku możesz eksplorować wstępnej implementacji trzy próbki starszych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31aa7-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="31aa7-122">Pierwsze dwie przykładowe aplikacje sieci web mają monolityczne architektury i zostały utworzone za pomocą klasycznego programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="31aa7-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="31aa7-123">Jedna aplikacja opiera się na platformie ASP.NET 4.x MVC; druga aplikacja opiera się na formularzach sieci Web programu ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="31aa7-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="31aa7-124">Trzeci aplikacja jest aplikacją 3-warstwowej aplikacji formularzy WinForms klienta i po stronie serwera [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) usługi.</span><span class="sxs-lookup"><span data-stu-id="31aa7-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="31aa7-125">Te aplikacje są dostępne pod adresem [repozytorium GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="31aa7-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="31aa7-126">Cele</span><span class="sxs-lookup"><span data-stu-id="31aa7-126">Goals</span></span>

<span data-ttu-id="31aa7-127">Głównym celem tego przewodnika jest po prostu zapoznać się z tych aplikacji i ich kodu i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="31aa7-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="31aa7-128">Aplikacje można skonfigurować tak, aby wygenerować i użyć danych testowych, bez korzystania z bazy danych SQL do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="31aa7-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="31aa7-129">Ta opcjonalna konfiguracja opiera się na iniekcji zależności w sposób odłączony.</span><span class="sxs-lookup"><span data-stu-id="31aa7-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="31aa7-130">Scenariusz 1: Aplikacje sieci Web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="31aa7-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="31aa7-131">Na poniższym rysunku przedstawiono prosty scenariusz oryginalnego starsze aplikacje sieci web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="31aa7-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Architektura Prosty scenariusz oryginalnego starsze aplikacje sieci web platformy ASP.NET](./media/image5-1.png)

<span data-ttu-id="31aa7-133">Z punktu widzenia domeny biznesowej obie aplikacje oferują tego samego katalogu funkcje zarządzania.</span><span class="sxs-lookup"><span data-stu-id="31aa7-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="31aa7-134">Członkowie zespołu enterprise eShop użyć jej do wyświetlania i edytowania katalogu produktów.</span><span class="sxs-lookup"><span data-stu-id="31aa7-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="31aa7-135">Na kolejnej ilustracji przedstawiono zrzuty ekranu aplikacji początkowej.</span><span class="sxs-lookup"><span data-stu-id="31aa7-135">The next figure shows the initial app screenshots.</span></span>

![Aplikacje platformy ASP.NET MVC i formularzy sieci Web platformy ASP.NET (istniejącej starszych technologiach)](./media/image5-2.png)

<span data-ttu-id="31aa7-137">Zależności w programie ASP.NET 4.x i jego wcześniejsze wersje, (zarówno dla platformy MVC i formularzy sieci Web) oznacza, że te aplikacje nie będą uruchamiane na platformie .NET Core, chyba że kod jest w pełni przepisany przy użyciu platformy ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="31aa7-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="31aa7-138">Scenariusz 2: Usługi WCF i aplikację kliencką WinForms (3-warstwowej aplikacji)</span><span class="sxs-lookup"><span data-stu-id="31aa7-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="31aa7-139">Na poniższym rysunku przedstawiono prosty scenariusz oryginalnego starszych aplikacji 3-warstwowej.</span><span class="sxs-lookup"><span data-stu-id="31aa7-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Architektura Prosty scenariusz oryginalnego starszych aplikacji 3-warstwowej przy użyciu usługi WCF i aplikację kliencką WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="31aa7-141">Zalety</span><span class="sxs-lookup"><span data-stu-id="31aa7-141">Benefits</span></span>

<span data-ttu-id="31aa7-142">Korzyści wynikające z tego przewodnika są proste: Po prostu zapoznać się z kodem i początkowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31aa7-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="31aa7-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="31aa7-143">Next steps</span></span>

<span data-ttu-id="31aa7-144">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="31aa7-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="31aa7-145">Samouczek linii bazowej platformy ASP.NET MVC i formularzy sieci Web "starszych" aplikacji</span><span class="sxs-lookup"><span data-stu-id="31aa7-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="31aa7-146">Samouczek na temat usługi WCF linii bazowej i aplikacja "starszych" (3-warstwowej) WinForms</span><span class="sxs-lookup"><span data-stu-id="31aa7-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="31aa7-147">Przewodnik 2: Konteneryzowanie istniejącej aplikacji .NET za pomocą kontenerów Windows</span><span class="sxs-lookup"><span data-stu-id="31aa7-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="31aa7-148">Omówienie</span><span class="sxs-lookup"><span data-stu-id="31aa7-148">Overview</span></span>

<span data-ttu-id="31aa7-149">Korzystaj z kontenerów Windows, w celu wdrożenia istniejących aplikacji .NET, takich jak te oparte na WCF, MVC i formularzy sieci Web w środowisku produkcyjnym, programowania i środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="31aa7-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="31aa7-150">Cele</span><span class="sxs-lookup"><span data-stu-id="31aa7-150">Goals</span></span>

<span data-ttu-id="31aa7-151">Celem tego przewodnika jest, aby pokazać Ci kilka opcji konteneryzowania istniejącej aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31aa7-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="31aa7-152">Można:</span><span class="sxs-lookup"><span data-stu-id="31aa7-152">You can:</span></span>

- <span data-ttu-id="31aa7-153">Konteneryzowanie aplikacji przy użyciu [Visual Studio 2017 r Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowsze wersje).</span><span class="sxs-lookup"><span data-stu-id="31aa7-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="31aa7-154">Konteneryzowanie aplikacji, ręcznie dodając [pliku Dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie używając [interfejsu wiersza polecenia Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="31aa7-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="31aa7-155">Konteneryzowanie aplikacji przy użyciu [Img2Docker](https://github.com/docker/communitytools-image2docker-win) narzędzia (narzędzie typu open-source docker).</span><span class="sxs-lookup"><span data-stu-id="31aa7-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="31aa7-156">Ten przewodnik koncentruje się na Visual Studio Tools 2017 podejścia platformy Docker, ale pozostałe dwie metody są podobne rozumieniu przy użyciu plików Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="31aa7-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="31aa7-157">Scenariusz 1: Konteneryzowanych aplikacji sieci web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="31aa7-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="31aa7-158">Na poniższym rysunku przedstawiono scenariusz konteneryzowanych eShop starszych internetowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31aa7-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Diagram architektury uproszczone kontenerowych nimi aplikacji ASP.NET w środowisku programistycznym](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="31aa7-160">Scenariusz 2: Konteneryzowana Usługa WCF</span><span class="sxs-lookup"><span data-stu-id="31aa7-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="31aa7-161">Na poniższym rysunku przedstawiono scenariusz, w przypadku aplikacji 3-warstwowej przy użyciu konteneryzowana Usługa WCF.</span><span class="sxs-lookup"><span data-stu-id="31aa7-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Uproszczony diagram architektury konteneryzowane usługi WCF w środowisku programistycznym](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="31aa7-163">Zalety</span><span class="sxs-lookup"><span data-stu-id="31aa7-163">Benefits</span></span>

<span data-ttu-id="31aa7-164">Istnieją zalety łączenia uruchamiania aplikacji monolitycznych w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="31aa7-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="31aa7-165">Najpierw należy utworzyć obraz dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31aa7-165">First, you create an image for the application.</span></span> <span data-ttu-id="31aa7-166">Od tego momentu każde wdrożenie jest uruchamiane w tym samym środowisku.</span><span class="sxs-lookup"><span data-stu-id="31aa7-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="31aa7-167">Każdy kontener korzysta z tej samej wersji systemu operacyjnego, ma tę samą wersję zależności zainstalowane, korzysta z tej samej wersji programu .NET framework i powstała przy użyciu tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="31aa7-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="31aa7-168">Zasadniczo możesz kontrolować zależności aplikacji przy użyciu obrazu platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="31aa7-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="31aa7-169">Zależności są przesyłane przy użyciu aplikacji podczas wdrażania kontenerów.</span><span class="sxs-lookup"><span data-stu-id="31aa7-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="31aa7-170">Dodatkową korzyścią jest to, że deweloperzy mogą uruchomić aplikację w spójne środowisko, które są dostarczane przez kontenery Windows.</span><span class="sxs-lookup"><span data-stu-id="31aa7-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="31aa7-171">Problemy, które są wyświetlane tylko w przypadku niektórych wersji mogą wykrył od razu, zamiast, dzięki czemu są ujawniane w środowisku tymczasowym czy produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="31aa7-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="31aa7-172">Różnice w środowiskach programistycznych, które posługują się członkowie zespołu rozwoju znaczenia mniejsza, gdy aplikacje są uruchamiane w kontenerach.</span><span class="sxs-lookup"><span data-stu-id="31aa7-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="31aa7-173">Konteneryzowane aplikacje mają również płaski krzywej skalowalnego w poziomie.</span><span class="sxs-lookup"><span data-stu-id="31aa7-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="31aa7-174">Konteneryzowanych aplikacji pozwalają na więcej aplikacji i wystąpień usługi (oparte na kontenerach) w maszynie Wirtualnej lub komputera fizycznego w porównaniu do regularnego acji dla poszczególnych komputerów.</span><span class="sxs-lookup"><span data-stu-id="31aa7-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="31aa7-175">Przekłada się to wyższych gęstości, a mniej wymaganych zasobów, szczególnie w przypadku, gdy używasz koordynatorów, takich jak Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="31aa7-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="31aa7-176">Konteneryzacji w sytuacjach, idealnym rozwiązaniem, nie wymaga wprowadzania żadnych zmian w kodzie aplikacji (C\#).</span><span class="sxs-lookup"><span data-stu-id="31aa7-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="31aa7-177">W większości przypadków wystarczy Docker wdrożenia metadanych plików (pliki Dockerfile i narzędzia Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="31aa7-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="31aa7-178">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="31aa7-178">Next steps</span></span>

<span data-ttu-id="31aa7-179">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="31aa7-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="31aa7-180">Jak konteneryzowanie aplikacji sieci web .NET Framework za pomocą Windows kontenery i Docker</span><span class="sxs-lookup"><span data-stu-id="31aa7-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="31aa7-181">Dodawanie obsługi platformy Docker do usługi WCF</span><span class="sxs-lookup"><span data-stu-id="31aa7-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="31aa7-182">Przewodnik 3: Wdrażanie aplikacji opartych na kontenerach Windows na maszynach wirtualnych platformy Azure</span><span class="sxs-lookup"><span data-stu-id="31aa7-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="31aa7-183">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="31aa7-183">Technical walkthrough availability</span></span>

<span data-ttu-id="31aa7-184">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="31aa7-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="31aa7-185">Omówienie</span><span class="sxs-lookup"><span data-stu-id="31aa7-185">Overview</span></span>

<span data-ttu-id="31aa7-186">Wdrażanie hosta platformy Docker na system Windows Server 2016 maszyny wirtualnej (VM) na platformie Azure umożliwia szybkie konfigurowanie środowisk projektowania/testów/wdrażanie przejściowe.</span><span class="sxs-lookup"><span data-stu-id="31aa7-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="31aa7-187">Oferuje on również typowe miejscu dla testerów lub użytkownicy biznesowi sprawdzić poprawność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31aa7-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="31aa7-188">Maszyny wirtualne również mogą być prawidłowe infrastruktury jako środowisk produkcyjnych usługi (IaaS).</span><span class="sxs-lookup"><span data-stu-id="31aa7-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="31aa7-189">Cele</span><span class="sxs-lookup"><span data-stu-id="31aa7-189">Goals</span></span>

<span data-ttu-id="31aa7-190">Celem tego przewodnika jest aby pokazać Ci kilka rozwiązań alternatywnych, do których masz podczas wdrażania kontenerów Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="31aa7-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="31aa7-191">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="31aa7-191">Scenarios</span></span>

<span data-ttu-id="31aa7-192">W tym przewodniku znajdują się kilku scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="31aa7-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="31aa7-193">Scenariusz A: Wdrażanie na Maszynie wirtualnej platformy Azure od deweloperów komputera za pośrednictwem połączenia aparat platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31aa7-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Wdrażanie na Maszynie wirtualnej platformy Azure od deweloperów komputera za pośrednictwem połączenia aparat platformy Docker](./media/image5-4.png)

<span data-ttu-id="31aa7-195">**Rysunek 5-4.**</span><span class="sxs-lookup"><span data-stu-id="31aa7-195">**Figure 5-4.**</span></span> <span data-ttu-id="31aa7-196">Wdrażanie na Maszynie wirtualnej platformy Azure od deweloperów komputera za pośrednictwem połączenia aparat platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31aa7-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="31aa7-197">Scenariusz B: Wdrażanie na maszynie Wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31aa7-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker](./media/image5-5.png)

<span data-ttu-id="31aa7-199">**Rysunek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="31aa7-199">**Figure 5-5.**</span></span> <span data-ttu-id="31aa7-200">Wdrażanie na maszynie Wirtualnej platformy Azure za pośrednictwem rejestru platformy Docker</span><span class="sxs-lookup"><span data-stu-id="31aa7-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="31aa7-201">Scenariusz C: Wdrożyć Maszynę wirtualną platformy Azure z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="31aa7-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Wdrożyć Maszynę wirtualną platformy Azure z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure](./media/image5-6.png)

<span data-ttu-id="31aa7-203">**Rysunek 5 – 6.**</span><span class="sxs-lookup"><span data-stu-id="31aa7-203">**Figure 5-6.**</span></span> <span data-ttu-id="31aa7-204">Wdrożyć Maszynę wirtualną platformy Azure z poziomu potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="31aa7-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="31aa7-205">Maszyny wirtualne platformy Azure dla kontenerów Windows</span><span class="sxs-lookup"><span data-stu-id="31aa7-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="31aa7-206">Maszyny wirtualne dla Windows kontenery usługi Azure maszyn wirtualnych opartych na systemie Windows Server 2016, Windows 10 lub nowszy, konfigurowanie zarówno z aparatem Docker.</span><span class="sxs-lookup"><span data-stu-id="31aa7-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="31aa7-207">W większości przypadków systemu Windows Server 2016 jest używana w maszynach wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="31aa7-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="31aa7-208">System Azure oferuje obecnie Maszynę wirtualną o nazwie **systemu Windows Server 2016 z kontenerami**.</span><span class="sxs-lookup"><span data-stu-id="31aa7-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="31aa7-209">Korzystanie z tej maszyny Wirtualnej, do wypróbowania nowej funkcji kontenera z systemem Windows Server z systemu Windows Server Core lub Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="31aa7-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="31aa7-210">Kontener obrazów systemu operacyjnego są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z platformą Docker.</span><span class="sxs-lookup"><span data-stu-id="31aa7-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="31aa7-211">Zalety</span><span class="sxs-lookup"><span data-stu-id="31aa7-211">Benefits</span></span>

<span data-ttu-id="31aa7-212">Mimo, że kontenery Windows można wdrożyć do lokalnego systemu Windows Server 2016 maszyn wirtualnych, w przypadku wdrażania na platformie Azure, możesz uzyskać łatwiejszy sposób, aby rozpocząć pracę, przy użyciu gotowych do użycia kontener maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="31aa7-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="31aa7-213">Możesz także uzyskać wspólnej lokalizacji online, który jest dostępny dla testerów i automatyczne skalowalności za pomocą zestawów skalowania maszyn wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="31aa7-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="31aa7-214">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="31aa7-214">Next steps</span></span>

<span data-ttu-id="31aa7-215">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="31aa7-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="31aa7-216">Przewodnik po 4: Wdrażanie aplikacji opartych na kontenerach Windows Azure Container instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="31aa7-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="31aa7-217">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="31aa7-217">Technical walkthrough availability</span></span>

<span data-ttu-id="31aa7-218">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="31aa7-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="31aa7-219">[Wdrażanie aplikacji w usłudze aci Uzyskaj (wystąpienia kontenera platformy Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="31aa7-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="31aa7-220">Omówienie</span><span class="sxs-lookup"><span data-stu-id="31aa7-220">Overview</span></span>

<span data-ttu-id="31aa7-221">[Usługa Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) jest najszybszym sposobem kontenerów środowiska dev/test/wdrażanie przejściowe, którym można wdrożyć z pojedynczego wystąpienia kontenerów.</span><span class="sxs-lookup"><span data-stu-id="31aa7-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="31aa7-222">Cele</span><span class="sxs-lookup"><span data-stu-id="31aa7-222">Goals</span></span>

<span data-ttu-id="31aa7-223">W tym przewodniku przedstawiono główne scenariusze wdrażania kontenerów Windows do usługi Azure Container Instances (ACI) i jak można wdrażać aplikacje eShopModernizing w usłudze ACI.</span><span class="sxs-lookup"><span data-stu-id="31aa7-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="31aa7-224">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="31aa7-224">Scenarios</span></span>

<span data-ttu-id="31aa7-225">Może to być różnice dotyczące wdrażania aplikacji eShopModernizing w usłudze ACI, takie jak wdrożenie tylko jednej lub wszystkich aplikacji (aplikacji MVC, aplikacja formularzy sieci Web lub usługi WCF).</span><span class="sxs-lookup"><span data-stu-id="31aa7-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="31aa7-226">W poniższym scenariuszu przedstawionym poniżej widać aplikacji ASP.NET MVC oraz kontener programu SQL Server, oba jest wdrażane jako kontenery w usłudze ACI (usługi Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="31aa7-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Wdrażanie usługi ACI z środowiska deweloperskiego](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="31aa7-228">Zalety</span><span class="sxs-lookup"><span data-stu-id="31aa7-228">Benefits</span></span>

<span data-ttu-id="31aa7-229">Usługa Azure Container Instances ułatwia tworzenie i zarządzanie nimi kontenerów platformy Docker na platformie Azure, bez konieczności aprowizowania maszyn wirtualnych lub stosowania usługi wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="31aa7-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="31aa7-230">Za pomocą usługi ACI można bezpośrednio wdrożyć kontener Windows na platformie Azure i ujawnisz go w Internecie przy użyciu w pełni kwalifikowaną nazwę domeny (FQDN) w ciągu kilku sekund (pod warunkiem, że masz gotowy obraz Windows kontenera w rejestrze Docker, takich jak usługi Docker Hub lub Azure Container Rejestr).</span><span class="sxs-lookup"><span data-stu-id="31aa7-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="31aa7-231">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31aa7-231">Considerations</span></span>

<span data-ttu-id="31aa7-232">Wdrażanie kontenerów Windows przy użyciu albo pełny program .NET Framework / platformy ASP.NET lub program SQL Server do usługi Azure Container Instances (ACI) nie jest dość tak szybko, jak wdrażanie regularne hosta platformy Docker (np. Windows Server 2016 z kontenerami Windows), ponieważ obraz platformy Docker musi być pobrany (ściągnięty z rejestru platformy Docker), każdym razem, gdy i obraz kontenera SQL (15.1 GB) i obrazu kontenera platformy ASP.NET (13.9 GB) są znacznie dużych, jednak jest znacznie tańsze niż utrzymywania własnego hosta platformy docker (trwale online Windows Server 2016 z maszyną Wirtualną z kontenerów Windows na platformie Azure) nie, aby wspomnieć o całego programu orchestrator, takich jak Kubernetes w usłudze Azure (AKS) czyli, z drugiej strony, to dobry wybór dla wdrożeń produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="31aa7-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="31aa7-233">Jako podstawowy wniosek za pomocą usługi Azure Container Instances jest to opcja niezwykle atrakcyjne rozwiązanie dla scenariuszy deweloperskich lub testowych oraz dla potoków ciągłej integracji/ciągłego Dostarczania.</span><span class="sxs-lookup"><span data-stu-id="31aa7-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="31aa7-234">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="31aa7-234">Next steps</span></span>

<span data-ttu-id="31aa7-235">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub:</span><span class="sxs-lookup"><span data-stu-id="31aa7-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="31aa7-236">Przewodnik po 5: Wdrażanie aplikacji opartych na kontenerach Windows do rozwiązania Kubernetes w usłudze Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="31aa7-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="31aa7-237">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="31aa7-237">Technical walkthrough availability</span></span>

<span data-ttu-id="31aa7-238">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="31aa7-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="31aa7-239">Omówienie</span><span class="sxs-lookup"><span data-stu-id="31aa7-239">Overview</span></span>

<span data-ttu-id="31aa7-240">Aplikacja, która opiera się na kontenery Windows szybko będą musieli używać platform, jeszcze bardziej odpływowi z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="31aa7-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="31aa7-241">To jest potrzebna do łatwo osiągnąć wysoką skalowalność lepiej automatycznego skalowania i znaczne ulepszenia w zautomatyzowane wdrożenia oraz zarządzanie ich wersjami.</span><span class="sxs-lookup"><span data-stu-id="31aa7-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="31aa7-242">Można osiągnąć te cele przy użyciu koordynatora [Kubernetes](https://kubernetes.io/), która jest dostępna w [usług Azure Container Service](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="31aa7-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="31aa7-243">Cele</span><span class="sxs-lookup"><span data-stu-id="31aa7-243">Goals</span></span>

<span data-ttu-id="31aa7-244">Celem tego przewodnika jest Dowiedz się, jak wdrażanie aplikacji dla komputerów z systemem Windows kontenera w usłudze Kubernetes (nazywane również *K8s*) w usłudze Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="31aa7-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="31aa7-245">Wdrażanie od zera rozwiązania Kubernetes jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="31aa7-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="31aa7-246">Wdrażanie klastra Kubernetes w usłudze Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="31aa7-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="31aa7-247">Wdrażanie aplikacji i powiązanych zasobów do klastra Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="31aa7-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="31aa7-248">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="31aa7-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="31aa7-249">Scenariusz A: Wdróż bezpośrednio w klastrze Kubernetes w środowisku deweloperskim</span><span class="sxs-lookup"><span data-stu-id="31aa7-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Wdróż bezpośrednio w klastrze Kubernetes z poziomu środowiska projektowego](./media/image5-7.png)

<span data-ttu-id="31aa7-251">**Rysunek 5 – 7.**</span><span class="sxs-lookup"><span data-stu-id="31aa7-251">**Figure 5-7.**</span></span> <span data-ttu-id="31aa7-252">Wdróż bezpośrednio w klastrze Kubernetes z poziomu środowiska projektowego</span><span class="sxs-lookup"><span data-stu-id="31aa7-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="31aa7-253">Scenariusz B: Wdrażanie klastra Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="31aa7-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Wdrażanie klastra Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure](./media/image5-8.png)

<span data-ttu-id="31aa7-255">**Rysunek 5 – 8.**</span><span class="sxs-lookup"><span data-stu-id="31aa7-255">**Figure 5-8.**</span></span> <span data-ttu-id="31aa7-256">Wdrażanie klastra Kubernetes z potoków ciągłej integracji/ciągłego wdrażania w usługom DevOps platformy Azure</span><span class="sxs-lookup"><span data-stu-id="31aa7-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="31aa7-257">Zalety</span><span class="sxs-lookup"><span data-stu-id="31aa7-257">Benefits</span></span>

<span data-ttu-id="31aa7-258">Istnieje wiele korzyści dla wdrażania w klastrze na platformie Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="31aa7-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="31aa7-259">Największa zaleta jest znaczny środowisko gotowe do produkcji, w którym można skalować w poziomie aplikacji, w oparciu o liczbę wystąpień kontenera, mają być używane (wewnętrzny skalowalności istniejących węzłów), a na podstawie liczby węzłów lub maszyn wirtualnych w (klastra globalną skalowalność klastra).</span><span class="sxs-lookup"><span data-stu-id="31aa7-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="31aa7-260">Usługa Azure Container Service optymalizuje popularnych narzędzi typu open source i technologii, pod kątem platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="31aa7-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="31aa7-261">Uzyskujesz otwarte rozwiązanie, przenośność, kontenerów i konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31aa7-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="31aa7-262">Wybierasz rozmiar, liczbę hostów i orchestrator narzędzia Container Service zajmuje się całą resztą.</span><span class="sxs-lookup"><span data-stu-id="31aa7-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="31aa7-263">Przy użyciu rozwiązania Kubernetes deweloperzy mogą postępu z myśleć o fizycznych i maszyn wirtualnych do planowania infrastruktury skoncentrowane na kontener, który ułatwia następujące funkcje, między innymi:</span><span class="sxs-lookup"><span data-stu-id="31aa7-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="31aa7-264">Aplikacje oparte na wielu kontenerów</span><span class="sxs-lookup"><span data-stu-id="31aa7-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="31aa7-265">Replikowanie wystąpień kontenera oraz skalowanie automatyczne w poziomie</span><span class="sxs-lookup"><span data-stu-id="31aa7-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="31aa7-266">Nazewnictwo i odnajdywania (na przykład wewnętrznego serwera DNS)</span><span class="sxs-lookup"><span data-stu-id="31aa7-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="31aa7-267">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="31aa7-267">Balancing loads</span></span>

- <span data-ttu-id="31aa7-268">Aktualizacje stopniowe</span><span class="sxs-lookup"><span data-stu-id="31aa7-268">Rolling updates</span></span>

- <span data-ttu-id="31aa7-269">Dystrybucja wpisów tajnych</span><span class="sxs-lookup"><span data-stu-id="31aa7-269">Distributing secrets</span></span>

- <span data-ttu-id="31aa7-270">Kontrole kondycji aplikacji</span><span class="sxs-lookup"><span data-stu-id="31aa7-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="31aa7-271">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="31aa7-271">Next steps</span></span>

<span data-ttu-id="31aa7-272">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="31aa7-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="31aa7-273">Przewodnik 6: Wdrażanie aplikacji opartych na kontenerach Windows w usłudze Azure App Service dla kontenerów</span><span class="sxs-lookup"><span data-stu-id="31aa7-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="31aa7-274">Dostępność technicznym</span><span class="sxs-lookup"><span data-stu-id="31aa7-274">Technical walkthrough availability</span></span>

<span data-ttu-id="31aa7-275">Pełna pomoc przewodnik jest dostępna w wiki repozytorium GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="31aa7-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="31aa7-276">Omówienie</span><span class="sxs-lookup"><span data-stu-id="31aa7-276">Overview</span></span>

<span data-ttu-id="31aa7-277">Prostej aplikacji konteneryzowanych za pomocą kontenerów Windows można łatwo wdrożyć w usłudze Azure App Service dla kontenerów.</span><span class="sxs-lookup"><span data-stu-id="31aa7-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="31aa7-278">Jest to zalecane podejście do większości aplikacji opartych na kontenerach Windows.</span><span class="sxs-lookup"><span data-stu-id="31aa7-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="31aa7-279">Cele</span><span class="sxs-lookup"><span data-stu-id="31aa7-279">Goals</span></span>

<span data-ttu-id="31aa7-280">Celem tego przewodnika jest, aby dowiedzieć się, jak wdrożyć aplikację kontenera Windows oparte na usłudze Azure App Service dla kontenerów z rejestru (usługi Docker Hub lub Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="31aa7-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="31aa7-281">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="31aa7-281">Scenario</span></span>

![Wdrażanie aplikacji opartych na kontenerach Windows w usłudze Azure App Service dla kontenerów](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="31aa7-283">Zalety</span><span class="sxs-lookup"><span data-stu-id="31aa7-283">Benefits</span></span>

<span data-ttu-id="31aa7-284">Wdrażanie w usłudze Azure App Service dla kontenerów oferuje zalety kontenery skojarzone z korzyściami PaaS w usłudze Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="31aa7-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="31aa7-285">Usługa app service można łatwo skalować w pionie i w poziomie, a następnie można skonfigurować do automatycznego skalowania, aby spełnić zgłaszanych.</span><span class="sxs-lookup"><span data-stu-id="31aa7-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="31aa7-286">Aktualizacje mogą być wykonywane bez przestojów i łatwo konfigurować również konfiguracja ciągłego wdrażania z rejestru.</span><span class="sxs-lookup"><span data-stu-id="31aa7-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="31aa7-287">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="31aa7-287">Next steps</span></span>

<span data-ttu-id="31aa7-288">Poznaj tę zawartość, więcej informacji na temat w witrynie typu wiki usługi GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="31aa7-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="31aa7-289">[Poprzednie](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
> [dalej](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="31aa7-289">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
