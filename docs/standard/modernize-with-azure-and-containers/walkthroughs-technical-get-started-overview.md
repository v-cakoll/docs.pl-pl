---
title: Wskazówki i technical uzyskać uruchomiono — omówienie
description: Modernizacji istniejących aplikacji .NET z chmury Azure i kontenery systemu Windows | wskazówki i technical uzyskać uruchomiono — omówienie
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0bad7e3afbdf3e55c447319b3756f2235b9e0a19
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="8ddd6-103">Wskazówki i technical uzyskać uruchomiono — omówienie</span><span class="sxs-lookup"><span data-stu-id="8ddd6-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="8ddd6-104">Aby ograniczyć rozmiar Książka elektroniczna, dodatkową dokumentację techniczną i pełne wskazówki zostały udostępnione w repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="8ddd6-105">Serie online wskazówki, które jest opisane w tym rozdziale opisano krok po kroku instalacji wielu środowiskach, które są oparte na kontenery systemu Windows i wdrażanie na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="8ddd6-106">W poniższych sekcjach opisano, co każdy wskazówki jest o jego cele i wizji wysokiego poziomu i zapewnia diagram zadań, które są związane z.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="8ddd6-107">Możesz uzyskać wskazówki, same w *eShopModernizing* wiki repozytorium GitHub aplikacje na [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="8ddd6-108">Lista wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="8ddd6-108">Technical walkthrough list</span></span>

<span data-ttu-id="8ddd6-109">Poniższe wskazówki get-started zapewnić spójne i wyczerpujące wskazówki techniczne przykładowych aplikacji, które można przyrostu i przesunięte za pomocą kontenerów, a następnie przesuń za pomocą wielu opcji wdrażania na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="8ddd6-110">Każda z następujących wskazówki używa nowe próbki eShopLegacy i eShopModernizing aplikacji, które są dostępne w witrynie GitHub pod [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="8ddd6-111">**Samouczek eShop starszej wersji aplikacji**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-111">**Tour of eShop legacy apps**</span></span>

- <span data-ttu-id="8ddd6-112">**Containerize istniejących aplikacji .NET z kontenerami systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-112">**Containerize your existing .NET applications with Windows Containers**</span></span>

- <span data-ttu-id="8ddd6-113">**Wdrażanie aplikacji opartych na kontenery systemu Windows na maszynach wirtualnych platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-113">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="8ddd6-114">**Wdrażanie aplikacji opartych na kontenery systemu Windows na Kubernetes w usłudze kontenera platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-114">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="8ddd6-115">**Wdrażanie aplikacji Windows kontenery sieci szkieletowej usług Azure**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-115">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="8ddd6-116">Wskazówki 1: Samouczek eShop starszej wersji aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ddd6-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="8ddd6-117">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="8ddd6-117">Technical walkthrough availability</span></span>

<span data-ttu-id="8ddd6-118">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a><span data-ttu-id="8ddd6-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8ddd6-119">Overview</span></span>

<span data-ttu-id="8ddd6-120">W tym przewodniku można eksplorować początkowego stosowania dwie przykładowe aplikacje starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-120">In this walkthrough, you can explore the initial implementation of two sample legacy applications.</span></span> <span data-ttu-id="8ddd6-121">Zarówno przykładowe aplikacje mają wbudowanymi architekturę i zostały utworzone przy użyciu klasycznego ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-121">Both sample apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="8ddd6-122">Co aplikacja jest oparta na platformie ASP.NET 4.x MVC; drugi aplikacja jest oparta na formularzach sieci Web ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-122">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="8ddd6-123">Obie aplikacje są w [repozytorium GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-123">Both applications are in the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

<span data-ttu-id="8ddd6-124">Można containerize zarówno przykładowych aplikacji, w podobny sposób można containerize na klasyczny [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) aplikacji (WCF) do użycia jako aplikacja na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-124">You can containerize both sample apps, similar to the way you can containerize a classic [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) (WCF) application to be consumed as a desktop application.</span></span> <span data-ttu-id="8ddd6-125">Na przykład zobacz [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-125">For an example, see [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span></span>

### <a name="goals"></a><span data-ttu-id="8ddd6-126">Cele</span><span class="sxs-lookup"><span data-stu-id="8ddd6-126">Goals</span></span>

<span data-ttu-id="8ddd6-127">Głównym celem tego przewodnika jest po prostu zapoznać się z tych aplikacji i ich kodu i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="8ddd6-128">Aplikacje można skonfigurować tak, aby wygenerować i użycia danych testowych, bez korzystania z bazy danych SQL do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="8ddd6-129">Ten opcjonalny config opiera się na iniekcji zależności w sposób rozdzielonymi.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario"></a><span data-ttu-id="8ddd6-130">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="8ddd6-130">Scenario</span></span>

<span data-ttu-id="8ddd6-131">Rysunek 5-1 przedstawiono prosty scenariusz oryginalnego starsze aplikacje.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-131">Figure 5-1 shows the simple scenario of the original legacy applications.</span></span>

> ![Architektura Prosty scenariusz oryginalnego starszych aplikacji](./media/image5-1.png)
>
> <span data-ttu-id="8ddd6-133">**Rysunek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-133">**Figure 5-1.**</span></span> <span data-ttu-id="8ddd6-134">Architektura Prosty scenariusz oryginalnego starszych aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ddd6-134">Simple architecture scenario of the original legacy applications</span></span>

<span data-ttu-id="8ddd6-135">Z punktu widzenia domeny business obie aplikacje oferują tego samego katalogu funkcje zarządzania.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-135">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="8ddd6-136">Członkowie zespołu enterprise eShop użyje aplikacji, aby wyświetlić i edytować katalogu produktów.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-136">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> <span data-ttu-id="8ddd6-137">Rysunek 5-2 zawiera zrzuty ekranu aplikacji początkowej.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-137">Figure 5-2 shows the initial app screenshots.</span></span>

![Aplikacje ASP.NET MVC i formularzy sieci Web platformy ASP.NET (technologii istniejące starsze)](./media/image5-2.png)

> <span data-ttu-id="8ddd6-139">**Rysunek 5-2.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-139">**Figure 5-2.**</span></span> <span data-ttu-id="8ddd6-140">Aplikacje ASP.NET MVC i formularzy sieci Web platformy ASP.NET (technologii istniejące starsze)</span><span class="sxs-lookup"><span data-stu-id="8ddd6-140">ASP.NET MVC and ASP.NET Web Forms applications (existing/legacy technologies)</span></span>

<span data-ttu-id="8ddd6-141">Są to aplikacje sieci web, które są używane do przeglądania i modyfikowania wpisy w katalogu.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-141">These are web applications that are used to browse and modify catalog entries.</span></span> <span data-ttu-id="8ddd6-142">Fakt, że obie aplikacje dostarczyć te same funkcje firm/funkcjonalności jest po prostu do porównania.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-142">The fact that both apps deliver the same business/functional features is simply for comparison purposes.</span></span> <span data-ttu-id="8ddd6-143">Podobnej procedurze modernizacji aplikacje, które zostały utworzone przy użyciu platformy ASP.NET MVC i formularzy sieci Web ASP.NET jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-143">You can see a similar modernization process for apps that were created by using the ASP.NET MVC and ASP.NET Web Forms frameworks.</span></span>

<span data-ttu-id="8ddd6-144">Zależności w programie ASP.NET 4.x i jego wcześniejsze wersje, (zarówno dla platformy MVC i formularzy sieci Web) oznacza, że te aplikacje nie będą uruchamiane .NET Core, chyba że kod jest w pełni ulegną przy użyciu platformy ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-144">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> <span data-ttu-id="8ddd6-145">Oznacza to punkt, że jeśli nie chcesz ponownego projektowania lub ponownego pisania kodu, można containerize istniejących aplikacji i nadal używać tej samej technologii .NET i tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-145">This demonstrates the point that if you don't want to re-architect or rewrite code, you can containerize existing applications, and still use the same .NET technologies and the same code.</span></span> <span data-ttu-id="8ddd6-146">Widać, jak można uruchomić aplikacji, takich jak te w kontenerach, bez wprowadzania żadnych zmian do starszej wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-146">You can see how you can run applications like these in containers, without any changes to legacy code.</span></span>

### <a name="benefits"></a><span data-ttu-id="8ddd6-147">Zalety</span><span class="sxs-lookup"><span data-stu-id="8ddd6-147">Benefits</span></span>

<span data-ttu-id="8ddd6-148">Korzyści wynikające z tego przewodnika są proste: po prostu zapoznać się z konfiguracji kod i aplikacji, oparty na iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-148">The benefits of this walkthrough are simple: Just get familiar with the code and application configuration, based on dependency injection.</span></span> <span data-ttu-id="8ddd6-149">Następnie możesz eksperymentować z tej metody podczas containerize i wdrażania w wielu środowiskach, w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-149">Then, you can experiment with this approach when you containerize and deploy to multiple environments in the future.</span></span>

### <a name="next-steps"></a><span data-ttu-id="8ddd6-150">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8ddd6-150">Next steps</span></span>

<span data-ttu-id="8ddd6-151">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-151">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="8ddd6-152">Wskazówki 2: Containerize istniejących aplikacji .NET z kontenerami systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8ddd6-152">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="8ddd6-153">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="8ddd6-153">Technical walkthrough availability</span></span>

<span data-ttu-id="8ddd6-154">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-154">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a><span data-ttu-id="8ddd6-155">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8ddd6-155">Overview</span></span>

<span data-ttu-id="8ddd6-156">Używanie kontenerów Windows zwiększające wdrożenia istniejących aplikacji .NET, podobnie jak na podstawie MVC, formularzy sieci Web lub usługi WCF, do produkcji, projektowanie i środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-156">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="8ddd6-157">Cele</span><span class="sxs-lookup"><span data-stu-id="8ddd6-157">Goals</span></span>

<span data-ttu-id="8ddd6-158">Celem tego przewodnika jest pokazanie kilka opcji containerizing istniejącej aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-158">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="8ddd6-159">Można:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-159">You can:</span></span>

- <span data-ttu-id="8ddd6-160">Containerize aplikacji przy użyciu [2017 Visual Studio Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-160">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="8ddd6-161">Containerize aplikacji przez ręczne dodanie [plik Dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie użyć [interfejsu wiersza polecenia Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-161">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="8ddd6-162">Containerize aplikacji przy użyciu [Img2Docker](https://github.com/docker/communitytools-image2docker-win) narzędzia (narzędzie open source z Docker).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-162">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="8ddd6-163">Ten przewodnik koncentruje się na Visual Studio Tools 2017 Docker podejścia, ale inne podejścia są dość podobne pod względem przy użyciu Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-163">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario"></a><span data-ttu-id="8ddd6-164">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="8ddd6-164">Scenario</span></span>

<span data-ttu-id="8ddd6-165">Rysunek 5-3 przedstawiono scenariusz konteneryzowanych eShop starsze aplikacje.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-165">Figure 5-3 shows the scenario for containerized eShop legacy applications.</span></span>

> ![Diagram architektury uproszczony konteneryzowanych aplikacji w środowisku deweloperskim](./media/image5-3.png)
>
> <span data-ttu-id="8ddd6-167">**Rysunek 5-3.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-167">**Figure 5-3.**</span></span> <span data-ttu-id="8ddd6-168">Diagram architektury uproszczony konteneryzowanych aplikacji w środowisku deweloperskim</span><span class="sxs-lookup"><span data-stu-id="8ddd6-168">Simplified architecture diagram of containerized applications in a development environment</span></span>

### <a name="benefits"></a><span data-ttu-id="8ddd6-169">Zalety</span><span class="sxs-lookup"><span data-stu-id="8ddd6-169">Benefits</span></span>

<span data-ttu-id="8ddd6-170">Istnieją pewne zalety uruchamiania aplikacji z wbudowanymi w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-170">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="8ddd6-171">Najpierw należy utworzyć obraz dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-171">First, you create an image for the application.</span></span> <span data-ttu-id="8ddd6-172">Od tego momentu każde wdrożenie jest uruchamiany w tym samym środowisku.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-172">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="8ddd6-173">Każdy kontener korzysta z tej samej wersji systemu operacyjnego, ma tę samą wersję zainstalowane zależności używa tej samej wersji programu .NET framework i zbudowany przy użyciu tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-173">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="8ddd6-174">Zasadniczo kontrolować zależności aplikacji przy użyciu obrazu Docker.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-174">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="8ddd6-175">Zależności są przesyłane z aplikacji podczas wdrażania kontenerów.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-175">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="8ddd6-176">Dodatkową korzyścią jest to deweloperzy mogą uruchomić aplikację w spójne środowisko, które są dostarczane przez Windows kontenerów.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-176">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="8ddd6-177">Problemy, które są wyświetlane tylko w niektórych wersjach można wykrył natychmiast, zamiast udostępniając w środowisku tymczasowym czy produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-177">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="8ddd6-178">Różnice w środowiskach programistycznych używanych przez członków zespołu deweloperów znaczenia mniej aplikacji uruchamianych w kontenerach.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-178">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="8ddd6-179">Konteneryzowanych aplikacje mają również płaska krzywej skalowalnego w poziomie.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-179">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="8ddd6-180">Aplikacje konteneryzowanych umożliwiają mają więcej aplikacji i wystąpień usługi (w oparciu kontenery) w maszynie Wirtualnej lub komputera fizycznego w porównaniu do wdrożenia aplikacji regularnych dla poszczególnych komputerów.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-180">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="8ddd6-181">Przekłada się wyżej gęstości i mniej wymagane zasoby, szczególnie w przypadku, gdy używasz orchestrators Kubernetes lub sieci szkieletowej usług.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-181">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="8ddd6-182">Przechowywanie w kontenerach, w sytuacjach idealne rozwiązanie nie wymaga wprowadzania jakichkolwiek zmian w kodzie aplikacji (C\#).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-182">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="8ddd6-183">W większości przypadków wystarczy Docker wdrożenia metadanych plików (Dockerfiles i rozwiązania Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-183">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="8ddd6-184">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8ddd6-184">Next steps</span></span>

<span data-ttu-id="8ddd6-185">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span><span class="sxs-lookup"><span data-stu-id="8ddd6-185">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span></span>

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="8ddd6-186">Wskazówki 3: Wdrażanie aplikacji opartych na kontenery systemu Windows na maszynach wirtualnych platformy Azure</span><span class="sxs-lookup"><span data-stu-id="8ddd6-186">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="8ddd6-187">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="8ddd6-187">Technical walkthrough availability</span></span>

<span data-ttu-id="8ddd6-188">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-188">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="8ddd6-189">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8ddd6-189">Overview</span></span>

<span data-ttu-id="8ddd6-190">Wdrożeniu na hoście Docker na systemu Windows Server 2016 maszyn wirtualnych (VM) na platformie Azure pozwala szybko skonfigurować środowiska przejściowe development/testu.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-190">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="8ddd6-191">Również udostępnia typowe miejsce dla testerów i użytkowników biznesowych zatwierdzania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-191">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="8ddd6-192">Maszyny wirtualne również może być nieprawidłowa że jako środowisk produkcyjnych usługę (IaaS).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-192">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="8ddd6-193">Cele</span><span class="sxs-lookup"><span data-stu-id="8ddd6-193">Goals</span></span>

<span data-ttu-id="8ddd6-194">Celem tego przewodnika jest pokazanie wielu rozwiązań alternatywnych, których masz wdrażając kontenery systemu Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-194">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="8ddd6-195">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="8ddd6-195">Scenarios</span></span>

<span data-ttu-id="8ddd6-196">W tym przewodniku opisano kilka scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-196">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="8ddd6-197">Scenariusz A: Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów komputera za pośrednictwem połączenia z aparatem platformy Docker</span><span class="sxs-lookup"><span data-stu-id="8ddd6-197">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów PC przez połączenie z aparatem platformy Docker](./media/image5-4.png)

> <span data-ttu-id="8ddd6-199">**Rysunek 5-4.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-199">**Figure 5-4.**</span></span> <span data-ttu-id="8ddd6-200">Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów PC przez połączenie z aparatem platformy Docker</span><span class="sxs-lookup"><span data-stu-id="8ddd6-200">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="8ddd6-201">Scenariusz B: wdrażania na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker</span><span class="sxs-lookup"><span data-stu-id="8ddd6-201">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker](./media/image5-5.png)

> <span data-ttu-id="8ddd6-203">**Rysunek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-203">**Figure 5-5.**</span></span> <span data-ttu-id="8ddd6-204">Wdrażanie na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker</span><span class="sxs-lookup"><span data-stu-id="8ddd6-204">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="8ddd6-205">Scenariusz C: wdrożyć na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="8ddd6-205">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services](./media/image5-6.png)

> <span data-ttu-id="8ddd6-207">**Rysunek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-207">**Figure 5-6.**</span></span> <span data-ttu-id="8ddd6-208">Wdrażanie na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="8ddd6-208">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="8ddd6-209">Maszyny wirtualne platformy Azure dla systemu Windows kontenerów</span><span class="sxs-lookup"><span data-stu-id="8ddd6-209">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="8ddd6-210">Azure maszyn wirtualnych systemu Windows dla kontenerów maszyn wirtualnych na podstawie systemu Windows Server 2016, Windows 10 lub nowszy, konfigurowanie zarówno z aparatem platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-210">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="8ddd6-211">W większości przypadków systemu Windows Server 2016 jest używany w maszynach wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-211">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="8ddd6-212">Platforma Azure obecnie udostępnia maszyny Wirtualnej o nazwie **systemu Windows Server 2016 z kontenerami**.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-212">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="8ddd6-213">Próby nowa funkcja systemu Windows Server kontenera systemu Windows Server Core lub serwerze Nano systemu Windows, można użyć tej maszyny Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-213">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="8ddd6-214">Kontener obrazów systemu operacyjnego są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z Docker.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-214">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="8ddd6-215">Zalety</span><span class="sxs-lookup"><span data-stu-id="8ddd6-215">Benefits</span></span>

<span data-ttu-id="8ddd6-216">Mimo że kontenery systemu Windows można wdrożyć do lokalnego systemu Windows Server 2016 maszyn wirtualnych, gdy wdrażanie na platformie Azure, możesz uzyskać łatwiejszy sposób, aby rozpocząć pracę z maszynami wirtualnymi o kontenera gotowe do użycia systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-216">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="8ddd6-217">Możesz również uzyskać wspólnej lokalizacji online, który jest dostępny dla testerów i automatyczne skalowalności za pomocą zestawów skali maszyny wirtualnej platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-217">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="8ddd6-218">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8ddd6-218">Next steps</span></span>

<span data-ttu-id="8ddd6-219">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-219">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="8ddd6-220">Wskazówki 4: Wdrażanie aplikacji opartych na kontenery systemu Windows na Kubernetes w usłudze kontenera platformy Azure</span><span class="sxs-lookup"><span data-stu-id="8ddd6-220">Walkthrough 4: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="8ddd6-221">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="8ddd6-221">Technical walkthrough availability</span></span>

<span data-ttu-id="8ddd6-222">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-222">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="8ddd6-223">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8ddd6-223">Overview</span></span>

<span data-ttu-id="8ddd6-224">Aplikacja, która jest oparta na kontenery Windows szybko będą musieli używać platformy optymalizacji jeszcze bardziej przenoszenie z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-224">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="8ddd6-225">To pozwala łatwo osiągnąć wysoką skalowalność na potrzeby lepiej automatycznego skalowalność i uzyskać znaczne ulepszenia w automatycznego wdrożenia i przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-225">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="8ddd6-226">Te cele można osiągnąć za pomocą orchestrator [Kubernetes](https://kubernetes.io/), dostępną w [usługi kontenera platformy Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-226">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="8ddd6-227">Cele</span><span class="sxs-lookup"><span data-stu-id="8ddd6-227">Goals</span></span>

<span data-ttu-id="8ddd6-228">Celem tego przewodnika jest Dowiedz się, jak wdrożyć aplikację na podstawie kontenera systemu Windows do Kubernetes (nazywane również *K8s*) w usłudze kontenera platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-228">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="8ddd6-229">Wdrażanie na Kubernetes od podstaw jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-229">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="8ddd6-230">Wdrażanie klastra Kubernetes do usługi kontenera platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-230">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="8ddd6-231">Wdrażanie aplikacji i powiązanych zasobów do klastra Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-231">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="8ddd6-232">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="8ddd6-232">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="8ddd6-233">Scenariusz A: Wdróż bezpośrednio do klastra Kubernetes z tego środowiska deweloperskiego</span><span class="sxs-lookup"><span data-stu-id="8ddd6-233">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Wdrażanie bezpośrednio do klastra Kubernetes środowiska programowania](./media/image5-7.png)

> <span data-ttu-id="8ddd6-235">**Rysunek 5-7.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-235">**Figure 5-7.**</span></span> <span data-ttu-id="8ddd6-236">Wdrażanie bezpośrednio do klastra Kubernetes środowiska programowania</span><span class="sxs-lookup"><span data-stu-id="8ddd6-236">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="8ddd6-237">Scenariusz B: wdrożyć klaster Kubernetes z elementu konfiguracji/CD potoków w Team Services</span><span class="sxs-lookup"><span data-stu-id="8ddd6-237">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![Wdrażanie klastra Kubernetes z potoków CI/CD w Team Services](./media/image5-8.png)

> <span data-ttu-id="8ddd6-239">**Rysunek 5 – 8.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-239">**Figure 5-8.**</span></span> <span data-ttu-id="8ddd6-240">Wdrażanie klastra Kubernetes z potoków CI/CD w Team Services</span><span class="sxs-lookup"><span data-stu-id="8ddd6-240">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="8ddd6-241">Zalety</span><span class="sxs-lookup"><span data-stu-id="8ddd6-241">Benefits</span></span>

<span data-ttu-id="8ddd6-242">Istnieje wiele korzyści z wdrażaniem do klastra w Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-242">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="8ddd6-243">Największych korzyści jest uzyskanie środowisku gotowe do produkcji, w którym można skalować w poziomie na podstawie liczby wystąpień kontenera, aby użyć (wewnętrzny skalowalności w istniejących węzłów), a na podstawie liczby węzłów lub maszyn wirtualnych w klastrze (aplikacji globalne skalowanie klastra).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-243">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="8ddd6-244">Usługa kontenera platformy Azure optymalizuje popularnych open source narzędzia i technologie specjalnie dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-244">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="8ddd6-245">Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność, zarówno w przypadku kontenerów, jak i konfigurację aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-245">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="8ddd6-246">Wybierz rozmiar, liczby hostów, a narzędzia orchestrator-kontenera usługi obsługuje wszystkie inne.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-246">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="8ddd6-247">Z Kubernetes deweloperzy mogą postępu od planowania fizycznych i maszyn wirtualnych do planowania skoncentrowane kontenera infrastruktury, która ułatwia obsługę następujących funkcji, między innymi:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-247">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="8ddd6-248">Aplikacje oparte na wielu kontenerów</span><span class="sxs-lookup"><span data-stu-id="8ddd6-248">Applications based on multiple containers</span></span>

- <span data-ttu-id="8ddd6-249">Replikowanie wystąpień kontenera i skalowanie automatyczne pozioma</span><span class="sxs-lookup"><span data-stu-id="8ddd6-249">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="8ddd6-250">Nazewnictwo i odkrywania (na przykład wewnętrzny serwer DNS)</span><span class="sxs-lookup"><span data-stu-id="8ddd6-250">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="8ddd6-251">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="8ddd6-251">Balancing loads</span></span>

- <span data-ttu-id="8ddd6-252">Wprowadzanie aktualizacji</span><span class="sxs-lookup"><span data-stu-id="8ddd6-252">Rolling updates</span></span>

- <span data-ttu-id="8ddd6-253">Dystrybuowanie kluczy tajnych</span><span class="sxs-lookup"><span data-stu-id="8ddd6-253">Distributing secrets</span></span>

- <span data-ttu-id="8ddd6-254">Sprawdzanie kondycji aplikacji</span><span class="sxs-lookup"><span data-stu-id="8ddd6-254">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="8ddd6-255">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8ddd6-255">Next steps</span></span>

<span data-ttu-id="8ddd6-256">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="8ddd6-256">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="8ddd6-257">Wskazówki 5: Wdrażanie aplikacji opartych na kontenery systemu Windows do usługi Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="8ddd6-257">Walkthrough 5: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="8ddd6-258">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="8ddd6-258">Technical walkthrough availability</span></span>

<span data-ttu-id="8ddd6-259">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-259">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="8ddd6-260">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8ddd6-260">Overview</span></span>

<span data-ttu-id="8ddd6-261">Aplikacji opartej na kontenery Windows szybko powinna być używana platform optymalizacji jeszcze bardziej przenoszenie z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-261">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="8ddd6-262">To pozwala łatwo osiągnąć wysoką skalowalność na potrzeby lepiej automatycznego skalowalność i uzyskać znaczne ulepszenia w automatycznego wdrożenia i przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-262">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="8ddd6-263">Można osiągnięcie tych celów, za pomocą usługi orchestrator sieci szkieletowej usług Azure, która jest dostępna w chmurze Azure, ale również dostępne do użycia lokalnego, a nawet w innej chmurze publicznej.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-263">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="8ddd6-264">Cele</span><span class="sxs-lookup"><span data-stu-id="8ddd6-264">Goals</span></span>

<span data-ttu-id="8ddd6-265">Celem tego przewodnika jest informacje na temat wdrażania aplikacji na podstawie kontenera systemu Windows do klastra usługi sieć szkieletowa na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-265">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="8ddd6-266">Wdrażanie sieci szkieletowej usług od podstaw jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-266">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="8ddd6-267">Wdrażanie klastra usługi sieć szkieletowa usług Azure (lub innego środowiska).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-267">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="8ddd6-268">Wdrażanie aplikacji i powiązanych zasobów do klastra usługi sieć szkieletowa usług.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-268">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="8ddd6-269">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="8ddd6-269">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="8ddd6-270">Scenariusz A: Wdróż bezpośrednio do klastra usługi sieć szkieletowa z tego środowiska deweloperskiego</span><span class="sxs-lookup"><span data-stu-id="8ddd6-270">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Wdrażanie bezpośrednio do klastra usługi sieć szkieletowa środowiska programowania](./media/image5-9.png)

> <span data-ttu-id="8ddd6-272">**Rysunek 5 – 9.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-272">**Figure 5-9.**</span></span> <span data-ttu-id="8ddd6-273">Wdrażanie bezpośrednio do klastra usługi sieć szkieletowa środowiska programowania</span><span class="sxs-lookup"><span data-stu-id="8ddd6-273">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="8ddd6-274">Scenariusz B: wdrażanie klastra usługi sieć szkieletowa z elementu konfiguracji/CD potoków w Team Services</span><span class="sxs-lookup"><span data-stu-id="8ddd6-274">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Wdrażanie klastra usługi sieć szkieletowa z potoków CI/CD w Visual Studio Team Services](./media/image5-10.png)

> <span data-ttu-id="8ddd6-276">**Rysunek 5-10.**</span><span class="sxs-lookup"><span data-stu-id="8ddd6-276">**Figure 5-10.**</span></span> <span data-ttu-id="8ddd6-277">Wdrażanie klastra usługi sieć szkieletowa z potoków CI/CD w Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="8ddd6-277">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="8ddd6-278">Zalety</span><span class="sxs-lookup"><span data-stu-id="8ddd6-278">Benefits</span></span>

<span data-ttu-id="8ddd6-279">Korzyści z wdrożenia do klastra w sieci szkieletowej usług są podobne do korzyści wynikające ze stosowania Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-279">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="8ddd6-280">Jedną różnicą, jednak jest sieci szkieletowej usług dla aplikacji systemu Windows w porównaniu do Kubernetes, który jest w fazie beta kontenerów systemu Windows w wersji 1.9 Kubernetes więcej dojrzałe środowiska produkcyjnego (2017 grudnia).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-280">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="8ddd6-281">Kubernetes jest bardziej dojrzałe środowisko dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-281">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="8ddd6-282">Główne zaletą używania sieci szkieletowej usług Azure jest uzyskanie środowisku gotowe do produkcji, w którym można skalować w poziomie na podstawie liczby wystąpień kontenera, aby użyć (wewnętrzny skalowalności w istniejących węzłów), a na podstawie liczby aplikacji węzły lub maszyny wirtualne w klastrze (globalne skalowanie klastra).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-282">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="8ddd6-283">Sieć szkieletowa usług Azure oferuje przenośność zarówno w przypadku kontenerów, jak i konfigurację aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-283">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="8ddd6-284">Masz usługi sieć szkieletowa klastra na platformie Azure, lub jego zainstalowanie lokalnego we własnym centrum danych.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-284">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="8ddd6-285">Można nawet zainstalować klaster sieci szkieletowej usług w innej chmurze tak samo, jak [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-285">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="8ddd6-286">Z sieci szkieletowej usług deweloperzy mogą postępu od planowania fizycznych i maszyn wirtualnych do planowania skoncentrowane kontenera infrastruktury, która ułatwia obsługę następujących funkcji, między innymi:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-286">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="8ddd6-287">Aplikacje oparte na wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-287">Applications based on multiple containers.</span></span>

- <span data-ttu-id="8ddd6-288">Replikowanie wystąpień kontenera i poziomy Skalowanie automatyczne.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-288">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="8ddd6-289">Nazewnictwo i odkrywania (na przykład wewnętrzny serwer DNS).</span><span class="sxs-lookup"><span data-stu-id="8ddd6-289">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="8ddd6-290">Równoważenie obciążenia.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-290">Balancing loads.</span></span>

- <span data-ttu-id="8ddd6-291">Wprowadzanie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-291">Rolling updates.</span></span>

- <span data-ttu-id="8ddd6-292">Dystrybuowanie kluczy tajnych.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-292">Distributing secrets.</span></span>

- <span data-ttu-id="8ddd6-293">Umożliwia sprawdzenie kondycji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-293">Application health checks.</span></span>

<span data-ttu-id="8ddd6-294">Następujące funkcje są wyłączne w sieci szkieletowej usług (w porównaniu do innych orchestrators):</span><span class="sxs-lookup"><span data-stu-id="8ddd6-294">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="8ddd6-295">Możliwości usługi stanowej, za pomocą niezawodnych usług modelu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-295">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="8ddd6-296">Wzorzec złośliwych użytkowników za pomocą modelu aplikacji Reliable Actors.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-296">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="8ddd6-297">Wdróż procesów kości bez systemu operacyjnego, oprócz kontenery systemu Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-297">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="8ddd6-298">Zaawansowane aktualizacji stopniowych i kontroli kondycji.</span><span class="sxs-lookup"><span data-stu-id="8ddd6-298">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="8ddd6-299">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8ddd6-299">Next steps</span></span>

<span data-ttu-id="8ddd6-300">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="8ddd6-300">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="8ddd6-301">[Poprzednie](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[dalej](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="8ddd6-301">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
