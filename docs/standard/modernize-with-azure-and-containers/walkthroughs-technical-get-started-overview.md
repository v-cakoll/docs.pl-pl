---
title: Wskazówki i technical uzyskać uruchomiono — omówienie
description: Modernizacji istniejących aplikacji .NET z chmury Azure i kontenery systemu Windows | Wskazówki i technical uzyskać uruchomiono — omówienie
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 27de9d1c5475855a22f2d8a3518982605277f6d9
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="f9db3-103">Wskazówki i technical uzyskać uruchomiono — omówienie</span><span class="sxs-lookup"><span data-stu-id="f9db3-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="f9db3-104">Aby ograniczyć rozmiar Książka elektroniczna, dodatkową dokumentację techniczną i pełne wskazówki zostały udostępnione w repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="f9db3-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="f9db3-105">Serie online wskazówki, które jest opisane w tym rozdziale opisano krok po kroku instalacji wielu środowiskach, które są oparte na kontenery systemu Windows i wdrażanie na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="f9db3-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="f9db3-106">W poniższych sekcjach opisano, co każdy wskazówki jest o jego cele i wizji wysokiego poziomu i zapewnia diagram zadań, które są związane z.</span><span class="sxs-lookup"><span data-stu-id="f9db3-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="f9db3-107">Możesz uzyskać wskazówki, same w *eShopModernizing* wiki repozytorium GitHub aplikacje na [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="f9db3-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="f9db3-108">Lista wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="f9db3-108">Technical walkthrough list</span></span>

<span data-ttu-id="f9db3-109">Poniższe wskazówki get-started zapewnić spójne i wyczerpujące wskazówki techniczne przykładowych aplikacji, które można przyrostu i przesunięte za pomocą kontenerów, a następnie przesuń za pomocą wielu opcji wdrażania na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="f9db3-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="f9db3-110">Każda z następujących wskazówki używa nowe próbki eShopLegacy i eShopModernizing aplikacji, które są dostępne w witrynie GitHub pod [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="f9db3-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="f9db3-111">**Samouczek eShop starsze aplikacje (aplikacje linii bazowej do modernizacji)**</span><span class="sxs-lookup"><span data-stu-id="f9db3-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="f9db3-112">**Containerize istniejące aplikacje sieci web platformy ASP.NET (WebForms & MVC) z kontenerami systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="f9db3-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="f9db3-113">**Containerize istniejących usług WCF (warstwowe aplikacje) z kontenerami systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="f9db3-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="f9db3-114">**Wdrażanie aplikacji opartych na kontenery systemu Windows na maszynach wirtualnych platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="f9db3-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="f9db3-115">**Wdrażanie aplikacji opartych na kontenery systemu Windows na Kubernetes w usłudze kontenera platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="f9db3-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="f9db3-116">**Wdrażanie aplikacji Windows kontenery sieci szkieletowej usług Azure**</span><span class="sxs-lookup"><span data-stu-id="f9db3-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="f9db3-117">Wskazówki 1: Samouczek eShop starszej wersji aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9db3-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f9db3-118">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="f9db3-118">Technical walkthrough availability</span></span>

<span data-ttu-id="f9db3-119">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="f9db3-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="f9db3-120">wskazówki dotyczące wiki eShopModernizing</span><span class="sxs-lookup"><span data-stu-id="f9db3-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="f9db3-121">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f9db3-121">Overview</span></span>

<span data-ttu-id="f9db3-122">W tym przewodniku można eksplorować początkowego stosowania trzy przykładowe starsze aplikacje.</span><span class="sxs-lookup"><span data-stu-id="f9db3-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="f9db3-123">Pierwsze dwie przykładowe aplikacje sieci web mają wbudowanymi architekturę i zostały utworzone przy użyciu klasycznego ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f9db3-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="f9db3-124">Co aplikacja jest oparta na platformie ASP.NET 4.x MVC; drugi aplikacja jest oparta na formularzach sieci Web ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="f9db3-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="f9db3-125">Trzeci jest to aplikacja WinForms klienta i po stronie serwera aplikacja 3-warstwowej [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) usługi.</span><span class="sxs-lookup"><span data-stu-id="f9db3-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="f9db3-126">Te aplikacje są dostępne pod adresem [repozytorium GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="f9db3-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="f9db3-127">Cele</span><span class="sxs-lookup"><span data-stu-id="f9db3-127">Goals</span></span>

<span data-ttu-id="f9db3-128">Głównym celem tego przewodnika jest po prostu zapoznać się z tych aplikacji i ich kodu i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="f9db3-129">Aplikacje można skonfigurować tak, aby wygenerować i użycia danych testowych, bez korzystania z bazy danych SQL do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="f9db3-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="f9db3-130">Ten opcjonalny config opiera się na iniekcji zależności w sposób rozdzielonymi.</span><span class="sxs-lookup"><span data-stu-id="f9db3-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="f9db3-131">Scenariusz 1: Aplikacje sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f9db3-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="f9db3-132">Na poniższym rysunku przedstawiono prosty scenariusz oryginalnego starsze aplikacje sieci web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f9db3-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![Architektura Prosty scenariusz oryginalnego starsze aplikacje sieci web ASP.NET](./media/image5-1.png)
>

<span data-ttu-id="f9db3-134">Z punktu widzenia domeny business obie aplikacje oferują tego samego katalogu funkcje zarządzania.</span><span class="sxs-lookup"><span data-stu-id="f9db3-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="f9db3-135">Członkowie zespołu enterprise eShop użyje aplikacji, aby wyświetlić i edytować katalogu produktów.</span><span class="sxs-lookup"><span data-stu-id="f9db3-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="f9db3-136">Następny rysunek przedstawia zrzuty ekranu aplikacji początkowej.</span><span class="sxs-lookup"><span data-stu-id="f9db3-136">The next figure shows the initial app screenshots.</span></span>

![Aplikacje ASP.NET MVC i formularzy sieci Web platformy ASP.NET (technologii istniejące starsze)](./media/image5-2.png)

<span data-ttu-id="f9db3-138">Zależności w programie ASP.NET 4.x i jego wcześniejsze wersje, (zarówno dla platformy MVC i formularzy sieci Web) oznacza, że te aplikacje nie będą uruchamiane .NET Core, chyba że kod jest w pełni ulegną przy użyciu platformy ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="f9db3-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="f9db3-139">Scenariusz 2: Usługi WCF i aplikacji klienckich WinForms (3-warstwowych aplikacji)</span><span class="sxs-lookup"><span data-stu-id="f9db3-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="f9db3-140">Na poniższym rysunku przedstawiono prosty scenariusz oryginalnego starszych aplikacji 3-warstwowych.</span><span class="sxs-lookup"><span data-stu-id="f9db3-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![Architektura Prosty scenariusz oryginalnego starszych aplikacji 3-warstwowej z usługą WCF i aplikacji klienckich WinForms](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="f9db3-142">Zalety</span><span class="sxs-lookup"><span data-stu-id="f9db3-142">Benefits</span></span>

<span data-ttu-id="f9db3-143">Korzyści wynikające z tego przewodnika są proste: po prostu zapoznać się z kodu i początkowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="f9db3-144">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f9db3-144">Next steps</span></span>

<span data-ttu-id="f9db3-145">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="f9db3-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="f9db3-146">Samouczek na linii bazowej ASP.NET MVC i formularzy sieci Web aplikacji "starszych"</span><span class="sxs-lookup"><span data-stu-id="f9db3-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="f9db3-147">Samouczek na temat usługi WCF linii bazowej i aplikacji "starszych" (3-warstwowej) WinForms</span><span class="sxs-lookup"><span data-stu-id="f9db3-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="f9db3-148">Wskazówki 2: Containerize istniejących aplikacji .NET z kontenerami systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9db3-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="f9db3-149">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f9db3-149">Overview</span></span>

<span data-ttu-id="f9db3-150">Używanie kontenerów Windows zwiększające wdrożenia istniejących aplikacji .NET, podobnie jak na podstawie MVC, formularzy sieci Web lub usługi WCF, do produkcji, projektowanie i środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="f9db3-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="f9db3-151">Cele</span><span class="sxs-lookup"><span data-stu-id="f9db3-151">Goals</span></span>

<span data-ttu-id="f9db3-152">Celem tego przewodnika jest pokazanie kilka opcji containerizing istniejącej aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9db3-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="f9db3-153">Można:</span><span class="sxs-lookup"><span data-stu-id="f9db3-153">You can:</span></span>

- <span data-ttu-id="f9db3-154">Containerize aplikacji przy użyciu [2017 Visual Studio Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="f9db3-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="f9db3-155">Containerize aplikacji przez ręczne dodanie [plik Dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie użyć [interfejsu wiersza polecenia Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="f9db3-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="f9db3-156">Containerize aplikacji przy użyciu [Img2Docker](https://github.com/docker/communitytools-image2docker-win) narzędzia (narzędzie open source z Docker).</span><span class="sxs-lookup"><span data-stu-id="f9db3-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="f9db3-157">Ten przewodnik koncentruje się na Visual Studio Tools 2017 Docker podejścia, ale inne podejścia są dość podobne pod względem przy użyciu Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="f9db3-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="f9db3-158">Scenariusz 1: Aplikacje sieci web ASP.NET konteneryzowanych</span><span class="sxs-lookup"><span data-stu-id="f9db3-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="f9db3-159">Na poniższym rysunku przedstawiono scenariusz konteneryzowanych eShop starszych sieci web apps aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![Diagram architektury uproszczony konteneryzowanych aplikacji ASP.NET w środowisku deweloperskim](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="f9db3-161">Scenariusz 2: Usługi WCF konteneryzowanych</span><span class="sxs-lookup"><span data-stu-id="f9db3-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="f9db3-162">Na poniższym rysunku przedstawiono scenariusz aplikacji 3-warstwowej konteneryzowanych usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f9db3-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![Diagram architektury konteneryzowanych usługi WCF w środowisku projektowym uproszczony](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="f9db3-164">Zalety</span><span class="sxs-lookup"><span data-stu-id="f9db3-164">Benefits</span></span>

<span data-ttu-id="f9db3-165">Istnieją pewne zalety uruchamiania aplikacji z wbudowanymi w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="f9db3-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="f9db3-166">Najpierw należy utworzyć obraz dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-166">First, you create an image for the application.</span></span> <span data-ttu-id="f9db3-167">Od tego momentu każde wdrożenie jest uruchamiany w tym samym środowisku.</span><span class="sxs-lookup"><span data-stu-id="f9db3-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="f9db3-168">Każdy kontener korzysta z tej samej wersji systemu operacyjnego, ma tę samą wersję zainstalowane zależności używa tej samej wersji programu .NET framework i zbudowany przy użyciu tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="f9db3-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="f9db3-169">Zasadniczo kontrolować zależności aplikacji przy użyciu obrazu Docker.</span><span class="sxs-lookup"><span data-stu-id="f9db3-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="f9db3-170">Zależności są przesyłane z aplikacji podczas wdrażania kontenerów.</span><span class="sxs-lookup"><span data-stu-id="f9db3-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="f9db3-171">Dodatkową korzyścią jest to deweloperzy mogą uruchomić aplikację w spójne środowisko, które są dostarczane przez Windows kontenerów.</span><span class="sxs-lookup"><span data-stu-id="f9db3-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="f9db3-172">Problemy, które są wyświetlane tylko w niektórych wersjach można wykrył natychmiast, zamiast udostępniając w środowisku tymczasowym czy produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="f9db3-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="f9db3-173">Różnice w środowiskach programistycznych używanych przez członków zespołu deweloperów znaczenia mniej aplikacji uruchamianych w kontenerach.</span><span class="sxs-lookup"><span data-stu-id="f9db3-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="f9db3-174">Konteneryzowanych aplikacje mają również płaska krzywej skalowalnego w poziomie.</span><span class="sxs-lookup"><span data-stu-id="f9db3-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="f9db3-175">Aplikacje konteneryzowanych umożliwiają mają więcej aplikacji i wystąpień usługi (w oparciu kontenery) w maszynie Wirtualnej lub komputera fizycznego w porównaniu do wdrożenia aplikacji regularnych dla poszczególnych komputerów.</span><span class="sxs-lookup"><span data-stu-id="f9db3-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="f9db3-176">Przekłada się wyżej gęstości i mniej wymagane zasoby, szczególnie w przypadku, gdy używasz orchestrators Kubernetes lub sieci szkieletowej usług.</span><span class="sxs-lookup"><span data-stu-id="f9db3-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="f9db3-177">Przechowywanie w kontenerach, w sytuacjach idealne rozwiązanie nie wymaga wprowadzania jakichkolwiek zmian w kodzie aplikacji (C\#).</span><span class="sxs-lookup"><span data-stu-id="f9db3-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="f9db3-178">W większości przypadków wystarczy Docker wdrożenia metadanych plików (Dockerfiles i rozwiązania Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="f9db3-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="f9db3-179">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f9db3-179">Next steps</span></span>

<span data-ttu-id="f9db3-180">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="f9db3-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="f9db3-181">Jak containerize aplikacji sieci web .NET Framework za pomocą kontenery systemu Windows i Docker</span><span class="sxs-lookup"><span data-stu-id="f9db3-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="f9db3-182">Dodawanie obsługi Docker z usługą WCF</span><span class="sxs-lookup"><span data-stu-id="f9db3-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="f9db3-183">Wskazówki 3: Wdrażanie aplikacji opartych na kontenery systemu Windows na maszynach wirtualnych platformy Azure</span><span class="sxs-lookup"><span data-stu-id="f9db3-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f9db3-184">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="f9db3-184">Technical walkthrough availability</span></span>

<span data-ttu-id="f9db3-185">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="f9db3-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="f9db3-186">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f9db3-186">Overview</span></span>

<span data-ttu-id="f9db3-187">Wdrożeniu na hoście Docker na systemu Windows Server 2016 maszyn wirtualnych (VM) na platformie Azure pozwala szybko skonfigurować środowiska przejściowe development/testu.</span><span class="sxs-lookup"><span data-stu-id="f9db3-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="f9db3-188">Również udostępnia typowe miejsce dla testerów i użytkowników biznesowych zatwierdzania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="f9db3-189">Maszyny wirtualne również może być nieprawidłowa że jako środowisk produkcyjnych usługę (IaaS).</span><span class="sxs-lookup"><span data-stu-id="f9db3-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="f9db3-190">Cele</span><span class="sxs-lookup"><span data-stu-id="f9db3-190">Goals</span></span>

<span data-ttu-id="f9db3-191">Celem tego przewodnika jest pokazanie wielu rozwiązań alternatywnych, których masz wdrażając kontenery systemu Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="f9db3-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="f9db3-192">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="f9db3-192">Scenarios</span></span>

<span data-ttu-id="f9db3-193">W tym przewodniku opisano kilka scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f9db3-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="f9db3-194">Scenariusz A: Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów komputera za pośrednictwem połączenia z aparatem platformy Docker</span><span class="sxs-lookup"><span data-stu-id="f9db3-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów PC przez połączenie z aparatem platformy Docker](./media/image5-4.png)

> <span data-ttu-id="f9db3-196">**Rysunek 5-4.**</span><span class="sxs-lookup"><span data-stu-id="f9db3-196">**Figure 5-4.**</span></span> <span data-ttu-id="f9db3-197">Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów PC przez połączenie z aparatem platformy Docker</span><span class="sxs-lookup"><span data-stu-id="f9db3-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="f9db3-198">Scenariusz B: wdrażania na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker</span><span class="sxs-lookup"><span data-stu-id="f9db3-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker](./media/image5-5.png)

> <span data-ttu-id="f9db3-200">**Rysunek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="f9db3-200">**Figure 5-5.**</span></span> <span data-ttu-id="f9db3-201">Wdrażanie na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker</span><span class="sxs-lookup"><span data-stu-id="f9db3-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="f9db3-202">Scenariusz C: wdrożyć na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="f9db3-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services](./media/image5-6.png)

> <span data-ttu-id="f9db3-204">**Rysunek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="f9db3-204">**Figure 5-6.**</span></span> <span data-ttu-id="f9db3-205">Wdrażanie na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="f9db3-205">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="f9db3-206">Maszyny wirtualne platformy Azure dla systemu Windows kontenerów</span><span class="sxs-lookup"><span data-stu-id="f9db3-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="f9db3-207">Azure maszyn wirtualnych systemu Windows dla kontenerów maszyn wirtualnych na podstawie systemu Windows Server 2016, Windows 10 lub nowszy, konfigurowanie zarówno z aparatem platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="f9db3-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="f9db3-208">W większości przypadków systemu Windows Server 2016 jest używany w maszynach wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="f9db3-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="f9db3-209">Platforma Azure obecnie udostępnia maszyny Wirtualnej o nazwie **systemu Windows Server 2016 z kontenerami**.</span><span class="sxs-lookup"><span data-stu-id="f9db3-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="f9db3-210">Próby nowa funkcja systemu Windows Server kontenera systemu Windows Server Core lub serwerze Nano systemu Windows, można użyć tej maszyny Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="f9db3-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="f9db3-211">Kontener obrazów systemu operacyjnego są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z Docker.</span><span class="sxs-lookup"><span data-stu-id="f9db3-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="f9db3-212">Zalety</span><span class="sxs-lookup"><span data-stu-id="f9db3-212">Benefits</span></span>

<span data-ttu-id="f9db3-213">Mimo że kontenery systemu Windows można wdrożyć do lokalnego systemu Windows Server 2016 maszyn wirtualnych, gdy wdrażanie na platformie Azure, możesz uzyskać łatwiejszy sposób, aby rozpocząć pracę z maszynami wirtualnymi o kontenera gotowe do użycia systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="f9db3-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="f9db3-214">Możesz również uzyskać wspólnej lokalizacji online, który jest dostępny dla testerów i automatyczne skalowalności za pomocą zestawów skali maszyny wirtualnej platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="f9db3-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="f9db3-215">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f9db3-215">Next steps</span></span>

<span data-ttu-id="f9db3-216">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="f9db3-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="f9db3-217">Wskazówki 4: Wdrażanie aplikacji opartych na kontenery systemu Windows do wystąpień kontenera platformy Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="f9db3-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f9db3-218">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="f9db3-218">Technical walkthrough availability</span></span>

<span data-ttu-id="f9db3-219">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="f9db3-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="f9db3-220">[Wdrażanie aplikacji na ACI (wystąpień kontenera platformy Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="f9db3-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="f9db3-221">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f9db3-221">Overview</span></span>

<span data-ttu-id="f9db3-222">[Wystąpień kontenera platformy Azure (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) jest najszybszym sposobem na którym można wdrożyć pojedynczych wystąpień kontenery środowiska przemieszczania dev/testu kontenery.</span><span class="sxs-lookup"><span data-stu-id="f9db3-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="f9db3-223">Cele</span><span class="sxs-lookup"><span data-stu-id="f9db3-223">Goals</span></span>

<span data-ttu-id="f9db3-224">W tym przewodniku przedstawiono główne scenariusze wdrażania kontenery systemu Windows Azure wystąpień kontenera (ACI) i jak można wdrażać aplikacje eShopModernizing do ACI.</span><span class="sxs-lookup"><span data-stu-id="f9db3-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="f9db3-225">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="f9db3-225">Scenarios</span></span>

<span data-ttu-id="f9db3-226">Może to być zmian dotyczących wdrażania aplikacji eShopModernizing do ACI, takie jak wdrażanie jedno lub wszystkie aplikacje (aplikacji MVC, formularzy sieci Web aplikacji lub usługi WCF).</span><span class="sxs-lookup"><span data-stu-id="f9db3-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="f9db3-227">W poniższym scenariuszu pokazano poniżej widać aplikacji ASP.NET MVC plus kontenera programu SQL Server, oba wdrożony jako kontenery do ACI (wystąpień kontenera Azure).</span><span class="sxs-lookup"><span data-stu-id="f9db3-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Wdrażanie na ACI środowiska programowania](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="f9db3-229">Zalety</span><span class="sxs-lookup"><span data-stu-id="f9db3-229">Benefits</span></span>

<span data-ttu-id="f9db3-230">Wystąpień kontenera Azure ułatwia tworzenie i zarządzanie nimi kontenery Docker na platformie Azure, bez konieczności umieszczanie maszyn wirtualnych lub wdrożyć usługę wyższego poziomu usługi.</span><span class="sxs-lookup"><span data-stu-id="f9db3-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="f9db3-231">Dzięki ACI można bezpośrednio wdrożenia kontenera systemu Windows na platformie Azure i uwidacznia go do Internetu z w pełni kwalifikowaną nazwą domeny (FQDN) w ciągu kilku sekund (pod warunkiem, że masz gotowy obraz kontenera systemu Windows w rejestrze Docker, takich jak Centrum Docker lub kontenera Azure Rejestr).</span><span class="sxs-lookup"><span data-stu-id="f9db3-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="f9db3-232">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9db3-232">Considerations</span></span>

<span data-ttu-id="f9db3-233">Wdrażanie kontenerów systemu Windows albo pełną .NET Framework / ASP.NET lub SQL Server do wystąpień kontenera platformy Azure (ACI) nie jest dość tak szybko, jak wdrożeniem regularne hosta Docker (np. Windows Server 2016 z kontenerami systemu Windows), ponieważ obraz Docker musi być pobrana (pobrany z rejestru Docker) zawsze i obrazu kontenera SQL (15,1 GB) i obraz kontenera platformy ASP.NET (13.9 GB) są znacznie duży, jednak jest znacznie tańszy niż utrzymywania własnego hostów docker (trwale online Windows Server 2016 z maszyny Wirtualnej kontenery systemu Windows na platformie Azure) nie można wymienić całego programu orchestrator, takich jak Kubernetes Azure (AKS/ACS) lub sieć szkieletowa usług Azure, które są z drugiej strony opcji doskonałe wdrożeń produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="f9db3-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="f9db3-234">Jako podstawowy wniosek za pomocą wystąpień kontenera Azure jest bardzo istotne opcja scenariusze tworzenia/testowania i dla elementu konfiguracji/CD potoków.</span><span class="sxs-lookup"><span data-stu-id="f9db3-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f9db3-235">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f9db3-235">Next steps</span></span>

<span data-ttu-id="f9db3-236">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="f9db3-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="f9db3-237">Wskazówki 5: Wdrażanie aplikacji opartych na kontenery systemu Windows na Kubernetes w usłudze kontenera platformy Azure</span><span class="sxs-lookup"><span data-stu-id="f9db3-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f9db3-238">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="f9db3-238">Technical walkthrough availability</span></span>

<span data-ttu-id="f9db3-239">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="f9db3-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="f9db3-240">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f9db3-240">Overview</span></span>

<span data-ttu-id="f9db3-241">Aplikacja, która jest oparta na kontenery Windows szybko będą musieli używać platformy optymalizacji jeszcze bardziej przenoszenie z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="f9db3-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="f9db3-242">To pozwala łatwo osiągnąć wysoką skalowalność na potrzeby lepiej automatycznego skalowalność i uzyskać znaczne ulepszenia w automatycznego wdrożenia i przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="f9db3-243">Te cele można osiągnąć za pomocą orchestrator [Kubernetes](https://kubernetes.io/), dostępną w [usługi kontenera platformy Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="f9db3-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="f9db3-244">Cele</span><span class="sxs-lookup"><span data-stu-id="f9db3-244">Goals</span></span>

<span data-ttu-id="f9db3-245">Celem tego przewodnika jest Dowiedz się, jak wdrożyć aplikację na podstawie kontenera systemu Windows do Kubernetes (nazywane również *K8s*) w usłudze kontenera platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="f9db3-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="f9db3-246">Wdrażanie na Kubernetes od podstaw jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="f9db3-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="f9db3-247">Wdrażanie klastra Kubernetes do usługi kontenera platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="f9db3-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="f9db3-248">Wdrażanie aplikacji i powiązanych zasobów do klastra Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="f9db3-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="f9db3-249">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="f9db3-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="f9db3-250">Scenariusz A: Wdróż bezpośrednio do klastra Kubernetes z tego środowiska deweloperskiego</span><span class="sxs-lookup"><span data-stu-id="f9db3-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Wdrażanie bezpośrednio do klastra Kubernetes środowiska programowania](./media/image5-7.png)

> <span data-ttu-id="f9db3-252">**Rysunek 5-7.**</span><span class="sxs-lookup"><span data-stu-id="f9db3-252">**Figure 5-7.**</span></span> <span data-ttu-id="f9db3-253">Wdrażanie bezpośrednio do klastra Kubernetes środowiska programowania</span><span class="sxs-lookup"><span data-stu-id="f9db3-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="f9db3-254">Scenariusz B: wdrożyć klaster Kubernetes z elementu konfiguracji/CD potoków w Team Services</span><span class="sxs-lookup"><span data-stu-id="f9db3-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![Wdrażanie klastra Kubernetes z potoków CI/CD w Team Services](./media/image5-8.png)

> <span data-ttu-id="f9db3-256">**Rysunek 5 – 8.**</span><span class="sxs-lookup"><span data-stu-id="f9db3-256">**Figure 5-8.**</span></span> <span data-ttu-id="f9db3-257">Wdrażanie klastra Kubernetes z potoków CI/CD w Team Services</span><span class="sxs-lookup"><span data-stu-id="f9db3-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="f9db3-258">Zalety</span><span class="sxs-lookup"><span data-stu-id="f9db3-258">Benefits</span></span>

<span data-ttu-id="f9db3-259">Istnieje wiele korzyści z wdrażaniem do klastra w Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="f9db3-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="f9db3-260">Największych korzyści jest uzyskanie środowisku gotowe do produkcji, w którym można skalować w poziomie na podstawie liczby wystąpień kontenera, aby użyć (wewnętrzny skalowalności w istniejących węzłów), a na podstawie liczby węzłów lub maszyn wirtualnych w klastrze (aplikacji globalne skalowanie klastra).</span><span class="sxs-lookup"><span data-stu-id="f9db3-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="f9db3-261">Usługa kontenera platformy Azure optymalizuje popularnych open source narzędzia i technologie specjalnie dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="f9db3-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="f9db3-262">Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność, zarówno w przypadku kontenerów, jak i konfigurację aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="f9db3-263">Wybierz rozmiar, liczby hostów, a narzędzia orchestrator-kontenera usługi obsługuje wszystkie inne.</span><span class="sxs-lookup"><span data-stu-id="f9db3-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="f9db3-264">Z Kubernetes deweloperzy mogą postępu od planowania fizycznych i maszyn wirtualnych do planowania skoncentrowane kontenera infrastruktury, która ułatwia obsługę następujących funkcji, między innymi:</span><span class="sxs-lookup"><span data-stu-id="f9db3-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="f9db3-265">Aplikacje oparte na wielu kontenerów</span><span class="sxs-lookup"><span data-stu-id="f9db3-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="f9db3-266">Replikowanie wystąpień kontenera i skalowanie automatyczne pozioma</span><span class="sxs-lookup"><span data-stu-id="f9db3-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="f9db3-267">Nazewnictwo i odkrywania (na przykład wewnętrzny serwer DNS)</span><span class="sxs-lookup"><span data-stu-id="f9db3-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="f9db3-268">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="f9db3-268">Balancing loads</span></span>

- <span data-ttu-id="f9db3-269">Wprowadzanie aktualizacji</span><span class="sxs-lookup"><span data-stu-id="f9db3-269">Rolling updates</span></span>

- <span data-ttu-id="f9db3-270">Dystrybuowanie kluczy tajnych</span><span class="sxs-lookup"><span data-stu-id="f9db3-270">Distributing secrets</span></span>

- <span data-ttu-id="f9db3-271">Sprawdzanie kondycji aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9db3-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="f9db3-272">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f9db3-272">Next steps</span></span>

<span data-ttu-id="f9db3-273">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="f9db3-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="f9db3-274">Wskazówki 6: Wdrażanie aplikacji opartych na kontenery systemu Windows do usługi Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="f9db3-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f9db3-275">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="f9db3-275">Technical walkthrough availability</span></span>

<span data-ttu-id="f9db3-276">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="f9db3-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="f9db3-277">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f9db3-277">Overview</span></span>

<span data-ttu-id="f9db3-278">Aplikacji opartej na kontenery Windows szybko powinna być używana platform optymalizacji jeszcze bardziej przenoszenie z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="f9db3-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="f9db3-279">To pozwala łatwo osiągnąć wysoką skalowalność na potrzeby lepiej automatycznego skalowalność i uzyskać znaczne ulepszenia w automatycznego wdrożenia i przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="f9db3-280">Można osiągnięcie tych celów, za pomocą usługi orchestrator sieci szkieletowej usług Azure, która jest dostępna w chmurze Azure, ale również dostępne do użycia lokalnego, a nawet w innej chmurze publicznej.</span><span class="sxs-lookup"><span data-stu-id="f9db3-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="f9db3-281">Cele</span><span class="sxs-lookup"><span data-stu-id="f9db3-281">Goals</span></span>

<span data-ttu-id="f9db3-282">Celem tego przewodnika jest informacje na temat wdrażania aplikacji na podstawie kontenera systemu Windows do klastra usługi sieć szkieletowa na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="f9db3-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="f9db3-283">Wdrażanie sieci szkieletowej usług od podstaw jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="f9db3-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="f9db3-284">Wdrażanie klastra usługi sieć szkieletowa usług Azure (lub innego środowiska).</span><span class="sxs-lookup"><span data-stu-id="f9db3-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="f9db3-285">Wdrażanie aplikacji i powiązanych zasobów do klastra usługi sieć szkieletowa usług.</span><span class="sxs-lookup"><span data-stu-id="f9db3-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="f9db3-286">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="f9db3-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="f9db3-287">Scenariusz A: Wdróż bezpośrednio do klastra usługi sieć szkieletowa z tego środowiska deweloperskiego</span><span class="sxs-lookup"><span data-stu-id="f9db3-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Wdrażanie bezpośrednio do klastra usługi sieć szkieletowa środowiska programowania](./media/image5-9.png)

> <span data-ttu-id="f9db3-289">**Rysunek 5 – 9.**</span><span class="sxs-lookup"><span data-stu-id="f9db3-289">**Figure 5-9.**</span></span> <span data-ttu-id="f9db3-290">Wdrażanie bezpośrednio do klastra usługi sieć szkieletowa środowiska programowania</span><span class="sxs-lookup"><span data-stu-id="f9db3-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="f9db3-291">Scenariusz B: wdrażanie klastra usługi sieć szkieletowa z elementu konfiguracji/CD potoków w Team Services</span><span class="sxs-lookup"><span data-stu-id="f9db3-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Wdrażanie klastra usługi sieć szkieletowa z potoków CI/CD w Visual Studio Team Services](./media/image5-10.png)

> <span data-ttu-id="f9db3-293">**Rysunek 5-10.**</span><span class="sxs-lookup"><span data-stu-id="f9db3-293">**Figure 5-10.**</span></span> <span data-ttu-id="f9db3-294">Wdrażanie klastra usługi sieć szkieletowa z potoków CI/CD w Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="f9db3-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="f9db3-295">Zalety</span><span class="sxs-lookup"><span data-stu-id="f9db3-295">Benefits</span></span>

<span data-ttu-id="f9db3-296">Korzyści z wdrożenia do klastra w sieci szkieletowej usług są podobne do korzyści wynikające ze stosowania Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="f9db3-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="f9db3-297">Jedną różnicą, jednak jest sieci szkieletowej usług dla aplikacji systemu Windows w porównaniu do Kubernetes, który jest w fazie beta kontenerów systemu Windows w wersji 1.9 Kubernetes więcej dojrzałe środowiska produkcyjnego (2017 grudnia).</span><span class="sxs-lookup"><span data-stu-id="f9db3-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="f9db3-298">Kubernetes jest bardziej dojrzałe środowisko dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="f9db3-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="f9db3-299">Główne zaletą używania sieci szkieletowej usług Azure jest uzyskanie środowisku gotowe do produkcji, w którym można skalować w poziomie na podstawie liczby wystąpień kontenera, aby użyć (wewnętrzny skalowalności w istniejących węzłów), a na podstawie liczby aplikacji węzły lub maszyny wirtualne w klastrze (globalne skalowanie klastra).</span><span class="sxs-lookup"><span data-stu-id="f9db3-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="f9db3-300">Sieć szkieletowa usług Azure oferuje przenośność zarówno w przypadku kontenerów, jak i konfigurację aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="f9db3-301">Masz usługi sieć szkieletowa klastra na platformie Azure, lub jego zainstalowanie lokalnego we własnym centrum danych.</span><span class="sxs-lookup"><span data-stu-id="f9db3-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="f9db3-302">Można nawet zainstalować klaster sieci szkieletowej usług w innej chmurze tak samo, jak [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="f9db3-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="f9db3-303">Z sieci szkieletowej usług deweloperzy mogą postępu od planowania fizycznych i maszyn wirtualnych do planowania skoncentrowane kontenera infrastruktury, która ułatwia obsługę następujących funkcji, między innymi:</span><span class="sxs-lookup"><span data-stu-id="f9db3-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="f9db3-304">Aplikacje oparte na wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="f9db3-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="f9db3-305">Replikowanie wystąpień kontenera i poziomy Skalowanie automatyczne.</span><span class="sxs-lookup"><span data-stu-id="f9db3-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="f9db3-306">Nazewnictwo i odkrywania (na przykład wewnętrzny serwer DNS).</span><span class="sxs-lookup"><span data-stu-id="f9db3-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="f9db3-307">Równoważenie obciążenia.</span><span class="sxs-lookup"><span data-stu-id="f9db3-307">Balancing loads.</span></span>

- <span data-ttu-id="f9db3-308">Wprowadzanie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-308">Rolling updates.</span></span>

- <span data-ttu-id="f9db3-309">Dystrybuowanie kluczy tajnych.</span><span class="sxs-lookup"><span data-stu-id="f9db3-309">Distributing secrets.</span></span>

- <span data-ttu-id="f9db3-310">Umożliwia sprawdzenie kondycji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-310">Application health checks.</span></span>

<span data-ttu-id="f9db3-311">Następujące funkcje są wyłączne w sieci szkieletowej usług (w porównaniu do innych orchestrators):</span><span class="sxs-lookup"><span data-stu-id="f9db3-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="f9db3-312">Możliwości usługi stanowej, za pomocą niezawodnych usług modelu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="f9db3-313">Wzorzec złośliwych użytkowników za pomocą modelu aplikacji Reliable Actors.</span><span class="sxs-lookup"><span data-stu-id="f9db3-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="f9db3-314">Wdróż procesów kości bez systemu operacyjnego, oprócz kontenery systemu Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="f9db3-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="f9db3-315">Zaawansowane aktualizacji stopniowych i kontroli kondycji.</span><span class="sxs-lookup"><span data-stu-id="f9db3-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="f9db3-316">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f9db3-316">Next steps</span></span>

<span data-ttu-id="f9db3-317">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="f9db3-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="f9db3-318">[Poprzednie](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[dalej](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="f9db3-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
