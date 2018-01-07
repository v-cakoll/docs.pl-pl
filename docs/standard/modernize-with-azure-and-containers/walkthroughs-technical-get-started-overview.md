---
title: "Wskazówki i technical uzyskać uruchomiono — omówienie"
description: "Modernizacji istniejących aplikacji .NET z chmury Azure i kontenery systemu Windows | wskazówki i technical uzyskać uruchomiono — omówienie"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ead28fe1ffe1e002af73642a1c3b2e72479520f4
ms.sourcegitcommit: bf8a3ba647252010bdce86dd914ac6c61b5ba89d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/06/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="b5996-103">Wskazówki i technical uzyskać uruchomiono — omówienie</span><span class="sxs-lookup"><span data-stu-id="b5996-103">Walkthroughs and technical get started overview</span></span> 

<span data-ttu-id="b5996-104">Aby ograniczyć rozmiar Książka elektroniczna, wprowadziliśmy dodatkową dokumentację techniczną i pełne wskazówki dostępne w repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="b5996-104">To limit the size of this e-book, we've made additional technical documentation and the full walkthroughs available in a GitHub repo.</span></span> <span data-ttu-id="b5996-105">Serie online wskazówki, które jest opisane w tym rozdziale opisano krok po kroku instalacji wielu środowiskach, które są oparte na kontenery systemu Windows i wdrażanie na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="b5996-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="b5996-106">W poniższych sekcjach opisano każdy wskazówki nowości dotyczących jej cele, jego wysokiego poziomu wizji- i zapewnia diagram zadań, które są związane z.</span><span class="sxs-lookup"><span data-stu-id="b5996-106">The following sections explain what each walkthrough is about-its objectives, its high-level vision-and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="b5996-107">Możesz uzyskać wskazówki, same w *eShopModernizing* wiki repozytorium GitHub aplikacje na [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="b5996-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

# <a name="technical-walkthrough-list"></a><span data-ttu-id="b5996-108">Lista wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="b5996-108">Technical walkthrough list</span></span>

<span data-ttu-id="b5996-109">Poniższe wskazówki get-started zapewnić spójne i wyczerpujące wskazówki techniczne przykładowych aplikacji, które można przyrostu i przesunięte za pomocą kontenerów, a następnie przesuń za pomocą wielu opcji wdrażania na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="b5996-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="b5996-110">Każda z następujących wskazówki używa nowe próbki eShopLegacy i eShopModernizing aplikacji, które są dostępne w witrynie GitHub pod [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="b5996-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

-   <span data-ttu-id="b5996-111">**Samouczek eShop starszej wersji aplikacji**</span><span class="sxs-lookup"><span data-stu-id="b5996-111">**Tour of eShop legacy apps**</span></span>

-   <span data-ttu-id="b5996-112">**Containerize istniejących aplikacji .NET z kontenerami systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="b5996-112">**Containerize your existing .NET applications with Windows Containers**</span></span>

-   <span data-ttu-id="b5996-113">**Wdrażanie aplikacji opartych na kontenery systemu Windows na maszynach wirtualnych platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="b5996-113">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

-   <span data-ttu-id="b5996-114">**Wdrażanie aplikacji opartych na kontenery systemu Windows na Kubernetes w usłudze kontenera platformy Azure**</span><span class="sxs-lookup"><span data-stu-id="b5996-114">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

-   <span data-ttu-id="b5996-115">**Wdrażanie aplikacji Windows kontenery sieci szkieletowej usług Azure**</span><span class="sxs-lookup"><span data-stu-id="b5996-115">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="b5996-116">Wskazówki 1: Samouczek eShop starszej wersji aplikacji</span><span class="sxs-lookup"><span data-stu-id="b5996-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b5996-117">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="b5996-117">Technical walkthrough availability</span></span>

<span data-ttu-id="b5996-118">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="b5996-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="b5996-119">https://github.com/DotNet-Architecture/eShopModernizing/Wiki/01.-Tour-on-eShopModernizing-Apps-Implementation-Code</span><span class="sxs-lookup"><span data-stu-id="b5996-119">https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a><span data-ttu-id="b5996-120">Omówienie</span><span class="sxs-lookup"><span data-stu-id="b5996-120">Overview</span></span>

<span data-ttu-id="b5996-121">W tym przewodniku można eksplorować początkowego stosowania dwie przykładowe aplikacje starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="b5996-121">In this walkthrough, you can explore the initial implementation of two sample legacy applications.</span></span> <span data-ttu-id="b5996-122">Zarówno przykładowe aplikacje mają wbudowanymi architekturę i zostały utworzone przy użyciu klasycznego ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b5996-122">Both sample apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="b5996-123">Co aplikacja jest oparta na platformie ASP.NET 4.x MVC; drugi aplikacja jest oparta na formularzach sieci Web ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="b5996-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="b5996-124">Obie aplikacje są w [repozytorium GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="b5996-124">Both applications are in the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

<span data-ttu-id="b5996-125">Można containerize zarówno przykładowych aplikacji, w podobny sposób można containerize na klasyczny [Windows Communication Foundation](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) aplikacji (WCF) do użycia jako aplikacja na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b5996-125">You can containerize both sample apps, similar to the way you can containerize a classic [Windows Communication Foundation](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) (WCF) application to be consumed as a desktop application.</span></span> <span data-ttu-id="b5996-126">Na przykład zobacz [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span><span class="sxs-lookup"><span data-stu-id="b5996-126">For an example, see [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span></span>

### <a name="goals"></a><span data-ttu-id="b5996-127">Cele</span><span class="sxs-lookup"><span data-stu-id="b5996-127">Goals</span></span>

<span data-ttu-id="b5996-128">Głównym celem tego przewodnika jest po prostu zapoznać się z tych aplikacji i ich kodu i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b5996-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="b5996-129">Aplikacje można skonfigurować tak, aby wygenerować i użycia danych testowych, bez korzystania z bazy danych SQL do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="b5996-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="b5996-130">Ten opcjonalny config opiera się na iniekcji zależności w sposób rozdzielonymi.</span><span class="sxs-lookup"><span data-stu-id="b5996-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario"></a><span data-ttu-id="b5996-131">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="b5996-131">Scenario</span></span>

<span data-ttu-id="b5996-132">Rysunek 5-1 przedstawiono prosty scenariusz oryginalnego starsze aplikacje.</span><span class="sxs-lookup"><span data-stu-id="b5996-132">Figure 5-1 shows the simple scenario of the original legacy applications.</span></span>

> ![Architektura Prosty scenariusz oryginalnego starszych aplikacji](./media/image5-1.png)
>
> <span data-ttu-id="b5996-134">**Rysunek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="b5996-134">**Figure 5-1.**</span></span> <span data-ttu-id="b5996-135">Architektura Prosty scenariusz oryginalnego starszych aplikacji</span><span class="sxs-lookup"><span data-stu-id="b5996-135">Simple architecture scenario of the original legacy applications</span></span>

<span data-ttu-id="b5996-136">Z punktu widzenia domeny business obie aplikacje oferują tego samego katalogu funkcje zarządzania.</span><span class="sxs-lookup"><span data-stu-id="b5996-136">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="b5996-137">Członkowie zespołu enterprise eShop użyje aplikacji, aby wyświetlić i edytować katalogu produktów.</span><span class="sxs-lookup"><span data-stu-id="b5996-137">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> <span data-ttu-id="b5996-138">Rysunek 5-2 zawiera zrzuty ekranu aplikacji początkowej.</span><span class="sxs-lookup"><span data-stu-id="b5996-138">Figure 5-2 shows the initial app screenshots.</span></span>

![Aplikacje ASP.NET MVC i formularzy sieci Web platformy ASP.NET (technologii istniejące starsze)](./media/image5-2.png)

> <span data-ttu-id="b5996-140">**Rysunek 5-2.**</span><span class="sxs-lookup"><span data-stu-id="b5996-140">**Figure 5-2.**</span></span> <span data-ttu-id="b5996-141">Aplikacje ASP.NET MVC i formularzy sieci Web platformy ASP.NET (technologii istniejące starsze)</span><span class="sxs-lookup"><span data-stu-id="b5996-141">ASP.NET MVC and ASP.NET Web Forms applications (existing/legacy technologies)</span></span>

<span data-ttu-id="b5996-142">Są to aplikacje sieci web, które są używane do przeglądania i modyfikowania wpisy w katalogu.</span><span class="sxs-lookup"><span data-stu-id="b5996-142">These are web applications that are used to browse and modify catalog entries.</span></span> <span data-ttu-id="b5996-143">Fakt, że obie aplikacje dostarczyć te same funkcje firm/funkcjonalności jest po prostu do porównania.</span><span class="sxs-lookup"><span data-stu-id="b5996-143">The fact that both apps deliver the same business/functional features is simply for comparison purposes.</span></span> <span data-ttu-id="b5996-144">Podobnej procedurze modernizacji aplikacje, które zostały utworzone przy użyciu platformy ASP.NET MVC i formularzy sieci Web ASP.NET jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="b5996-144">You can see a similar modernization process for apps that were created by using the ASP.NET MVC and ASP.NET Web Forms frameworks.</span></span>

<span data-ttu-id="b5996-145">Zależności w programie ASP.NET 4.x i jego wcześniejsze wersje, (zarówno dla platformy MVC i formularzy sieci Web) oznacza, że te aplikacje nie będą uruchamiane .NET Core, chyba że kod jest w pełni ulegną przy użyciu platformy ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="b5996-145">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> <span data-ttu-id="b5996-146">Oznacza to punkt, że jeśli nie chcesz ponownego projektowania lub ponownego pisania kodu, można containerize istniejących aplikacji i nadal używać tej samej technologii .NET i tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="b5996-146">This demonstrates the point that if you don't want to re-architect or rewrite code, you can containerize existing applications, and still use the same .NET technologies and the same code.</span></span> <span data-ttu-id="b5996-147">Widać, jak można uruchomić aplikacji, takich jak te w kontenerach, bez wprowadzania żadnych zmian do starszej wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="b5996-147">You can see how you can run applications like these in containers, without any changes to legacy code.</span></span>

### <a name="benefits"></a><span data-ttu-id="b5996-148">Zalety</span><span class="sxs-lookup"><span data-stu-id="b5996-148">Benefits</span></span>

<span data-ttu-id="b5996-149">Korzyści wynikające z tego przewodnika są proste: po prostu zapoznać się z konfiguracji kod i aplikacji, oparty na iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="b5996-149">The benefits of this walkthrough are simple: Just get familiar with the code and application configuration, based on dependency injection.</span></span> <span data-ttu-id="b5996-150">Następnie możesz eksperymentować z tej metody podczas containerize i wdrażania w wielu środowiskach, w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="b5996-150">Then, you can experiment with this approach when you containerize and deploy to multiple environments in the future.</span></span>

### <a name="next-steps"></a><span data-ttu-id="b5996-151">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b5996-151">Next steps</span></span>

<span data-ttu-id="b5996-152">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="b5996-152">Explore this content more in-depth on the GitHub wiki:</span></span>

[<span data-ttu-id="b5996-153">https://github.com/DotNet-Architecture/eShopModernizing/Wiki/01.-Tour-on-eShopModernizing-Apps-Implementation-Code</span><span class="sxs-lookup"><span data-stu-id="b5996-153">https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="b5996-154">Wskazówki 2: Containerize istniejących aplikacji .NET z kontenerami systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b5996-154">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b5996-155">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="b5996-155">Technical walkthrough availability</span></span>

<span data-ttu-id="b5996-156">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="b5996-156">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="b5996-157">https://github.com/DotNet-Architecture/eShopModernizing/Wiki/02.-How-to-containerize-the-.NET-Framework-Web-Apps-with-Windows-containers-and-Docker</span><span class="sxs-lookup"><span data-stu-id="b5996-157">https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a><span data-ttu-id="b5996-158">Omówienie</span><span class="sxs-lookup"><span data-stu-id="b5996-158">Overview</span></span>

<span data-ttu-id="b5996-159">Używanie kontenerów Windows zwiększające wdrożenia istniejących aplikacji .NET, podobnie jak na podstawie MVC, formularzy sieci Web lub usługi WCF, do produkcji, projektowanie i środowisk testowych.</span><span class="sxs-lookup"><span data-stu-id="b5996-159">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="b5996-160">Cele</span><span class="sxs-lookup"><span data-stu-id="b5996-160">Goals</span></span>

<span data-ttu-id="b5996-161">Celem tego przewodnika jest pokazanie kilka opcji containerizing istniejącej aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5996-161">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="b5996-162">Można:</span><span class="sxs-lookup"><span data-stu-id="b5996-162">You can:</span></span>

-   <span data-ttu-id="b5996-163">Containerize aplikacji przy użyciu [2017 Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/core/docker/visual-studio-tools-for-docker) (Visual Studio 2017 lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="b5996-163">Containerize your application by using [Visual Studio 2017 Tools for Docker](https://docs.microsoft.com/dotnet/core/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

-   <span data-ttu-id="b5996-164">Containerize aplikacji przez ręczne dodanie [plik Dockerfile](https://docs.docker.com/engine/reference/builder/), a następnie użyć [interfejsu wiersza polecenia Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="b5996-164">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

-   <span data-ttu-id="b5996-165">Containerize aplikacji przy użyciu [Img2Docker](https://github.com/docker/communitytools-image2docker-win) narzędzia (narzędzie open source z Docker).</span><span class="sxs-lookup"><span data-stu-id="b5996-165">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="b5996-166">Ten przewodnik koncentruje się na Visual Studio Tools 2017 Docker podejścia, ale dwa podejścia są dość podobne w odniesieniu do przy użyciu Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="b5996-166">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regards to using Dockerfiles.</span></span>

### <a name="scenario"></a><span data-ttu-id="b5996-167">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="b5996-167">Scenario</span></span>

<span data-ttu-id="b5996-168">Rysunek 5-3 przedstawiono scenariusz konteneryzowanych eShop starsze aplikacje.</span><span class="sxs-lookup"><span data-stu-id="b5996-168">Figure 5-3 shows the scenario for containerized eShop legacy applications.</span></span>

> ![Diagram architektury uproszczony konteneryzowanych aplikacji w środowisku deweloperskim](./media/image5-3.png)
>
> <span data-ttu-id="b5996-170">**Rysunek 5-3.**</span><span class="sxs-lookup"><span data-stu-id="b5996-170">**Figure 5-3.**</span></span> <span data-ttu-id="b5996-171">Diagram architektury uproszczony konteneryzowanych aplikacji w środowisku deweloperskim</span><span class="sxs-lookup"><span data-stu-id="b5996-171">Simplified architecture diagram of containerized applications in a development environment</span></span>

### <a name="benefits"></a><span data-ttu-id="b5996-172">Zalety</span><span class="sxs-lookup"><span data-stu-id="b5996-172">Benefits</span></span>

<span data-ttu-id="b5996-173">Istnieją pewne zalety uruchamiania aplikacji z wbudowanymi w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="b5996-173">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="b5996-174">Najpierw należy utworzyć obraz dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5996-174">First, you create an image for the application.</span></span> <span data-ttu-id="b5996-175">Od tego momentu każde wdrożenie jest uruchamiany w tym samym środowisku.</span><span class="sxs-lookup"><span data-stu-id="b5996-175">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="b5996-176">Każdy kontener korzysta z tej samej wersji systemu operacyjnego, ma tę samą wersję zainstalowane zależności używa tej samej wersji programu .NET framework i zbudowany przy użyciu tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="b5996-176">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="b5996-177">Zasadniczo kontrolować zależności aplikacji przy użyciu obrazu Docker.</span><span class="sxs-lookup"><span data-stu-id="b5996-177">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="b5996-178">Zależności są przesyłane z aplikacji podczas wdrażania kontenerów.</span><span class="sxs-lookup"><span data-stu-id="b5996-178">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="b5996-179">Dodatkową korzyścią jest to deweloperzy mogą uruchomić aplikację w spójne środowisko, które są dostarczane przez Windows kontenerów.</span><span class="sxs-lookup"><span data-stu-id="b5996-179">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="b5996-180">Problemy, które są wyświetlane tylko w niektórych wersjach można wykrył natychmiast, zamiast udostępniając w środowisku tymczasowym czy produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="b5996-180">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="b5996-181">Różnice w środowiskach programistycznych używanych przez członków zespołu deweloperów znaczenia mniej aplikacji uruchamianych w kontenerach.</span><span class="sxs-lookup"><span data-stu-id="b5996-181">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="b5996-182">Konteneryzowanych aplikacje mają również płaska krzywej skalowalnego w poziomie.</span><span class="sxs-lookup"><span data-stu-id="b5996-182">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="b5996-183">Aplikacje konteneryzowanych umożliwiają mają więcej aplikacji i wystąpień usługi (w oparciu kontenery) w maszynie Wirtualnej lub komputera fizycznego w porównaniu do wdrożenia aplikacji regularnych dla poszczególnych komputerów.</span><span class="sxs-lookup"><span data-stu-id="b5996-183">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="b5996-184">Przekłada się wyżej gęstości i mniej wymagane zasoby, szczególnie w przypadku, gdy używasz orchestrators Kubernetes lub sieci szkieletowej usług.</span><span class="sxs-lookup"><span data-stu-id="b5996-184">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="b5996-185">Przechowywanie w kontenerach, w sytuacjach idealne rozwiązanie nie wymaga wprowadzania jakichkolwiek zmian w kodzie aplikacji (C\#).</span><span class="sxs-lookup"><span data-stu-id="b5996-185">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="b5996-186">W większości przypadków wystarczy Docker wdrożenia metadanych plików (Dockerfiles i rozwiązania Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="b5996-186">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="b5996-187">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b5996-187">Next steps</span></span>

<span data-ttu-id="b5996-188">Poznaj więcej informacji na temat zawartości w witrynie typu wiki GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span><span class="sxs-lookup"><span data-stu-id="b5996-188">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span></span>

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="b5996-189">Wskazówki 3: Wdrażanie aplikacji opartych na kontenery systemu Windows na maszynach wirtualnych platformy Azure</span><span class="sxs-lookup"><span data-stu-id="b5996-189">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b5996-190">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="b5996-190">Technical walkthrough availability</span></span>

<span data-ttu-id="b5996-191">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="b5996-191">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="b5996-192">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/03.-How-to-deploy-your-Windows-containers-based-App-INTO-Azure-VMs-(including-Ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="b5996-192">[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="b5996-193">Omówienie</span><span class="sxs-lookup"><span data-stu-id="b5996-193">Overview</span></span>

<span data-ttu-id="b5996-194">Wdrażanie hosta Docker na maszynie Wirtualnej 2016 serwera systemu Windows na platformie Azure pozwala szybko skonfigurować środowiska przejściowe dev/testu.</span><span class="sxs-lookup"><span data-stu-id="b5996-194">Deploying to a Docker host on a Windows Server 2016 VM in Azure lets you quickly set up dev/test/staging environments.</span></span> <span data-ttu-id="b5996-195">Również udostępnia typowe miejsce dla testerów i użytkowników biznesowych zatwierdzania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5996-195">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="b5996-196">Maszyny wirtualne można również prawidłowe środowisk produkcyjnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="b5996-196">VMs also can be valid IaaS production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="b5996-197">Cele</span><span class="sxs-lookup"><span data-stu-id="b5996-197">Goals</span></span>

<span data-ttu-id="b5996-198">Celem tego przewodnika jest pokazanie wielu rozwiązań alternatywnych, których masz wdrażając kontenery systemu Windows na maszynach wirtualnych platformy Azure, które są oparte na systemie Windows Server 2016 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="b5996-198">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="b5996-199">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="b5996-199">Scenarios</span></span>

<span data-ttu-id="b5996-200">W tym przewodniku opisano kilka scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="b5996-200">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="b5996-201">Scenariusz A: Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów komputera za pośrednictwem połączenia z aparatem platformy Docker</span><span class="sxs-lookup"><span data-stu-id="b5996-201">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów PC przez połączenie z aparatem platformy Docker](./media/image5-4.png)

> <span data-ttu-id="b5996-203">**Rysunek 5-4.**</span><span class="sxs-lookup"><span data-stu-id="b5996-203">**Figure 5-4.**</span></span> <span data-ttu-id="b5996-204">Wdrażanie na maszynie Wirtualnej platformy Azure z deweloperów PC przez połączenie z aparatem platformy Docker</span><span class="sxs-lookup"><span data-stu-id="b5996-204">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="b5996-205">Scenariusz B: wdrażania na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker</span><span class="sxs-lookup"><span data-stu-id="b5996-205">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker](./media/image5-5.png)

> <span data-ttu-id="b5996-207">**Rysunek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="b5996-207">**Figure 5-5.**</span></span> <span data-ttu-id="b5996-208">Wdrażanie na maszynie Wirtualnej platformy Azure za pomocą rejestru Docker</span><span class="sxs-lookup"><span data-stu-id="b5996-208">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="b5996-209">Scenariusz C: wdrożyć na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="b5996-209">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Wdrażanie na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services](./media/image5-6.png)

> <span data-ttu-id="b5996-211">**Rysunek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="b5996-211">**Figure 5-6.**</span></span> <span data-ttu-id="b5996-212">Wdrażanie na maszynie Wirtualnej platformy Azure z potoków CI/CD w Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="b5996-212">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="b5996-213">Maszyny wirtualne platformy Azure dla systemu Windows kontenerów</span><span class="sxs-lookup"><span data-stu-id="b5996-213">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="b5996-214">Azure maszyn wirtualnych systemu Windows dla kontenerów są po prostu maszyn wirtualnych, które są oparte na systemie Windows Server 2016, Windows 10 lub nowszy, zarówno z aparatem platformy Docker ustawienie.</span><span class="sxs-lookup"><span data-stu-id="b5996-214">Azure VMs for Windows Containers are simply VMs that are based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="b5996-215">W większości przypadków użyjesz systemu Windows Server 2016 w maszynach wirtualnych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b5996-215">In most cases, you will use Windows Server 2016 in the Azure VMs.</span></span>

<span data-ttu-id="b5996-216">Platforma Azure obecnie udostępnia maszyny Wirtualnej o nazwie **systemu Windows Server 2016 z kontenerami**.</span><span class="sxs-lookup"><span data-stu-id="b5996-216">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="b5996-217">Próby nowa funkcja systemu Windows Server kontenera systemu Windows Server Core lub serwerze Nano systemu Windows, można użyć tej maszyny Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="b5996-217">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="b5996-218">Kontener obrazów systemu operacyjnego są zainstalowane, a następnie maszyna wirtualna jest gotowa do użycia z Docker.</span><span class="sxs-lookup"><span data-stu-id="b5996-218">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="b5996-219">Zalety</span><span class="sxs-lookup"><span data-stu-id="b5996-219">Benefits</span></span>

<span data-ttu-id="b5996-220">Mimo że kontenery systemu Windows można wdrożyć do lokalnego systemu Windows Server 2016 maszyn wirtualnych, gdy wdrażanie na platformie Azure, możesz uzyskać łatwiejszy sposób, aby rozpocząć pracę z maszynami wirtualnymi o kontenera gotowe do użycia systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="b5996-220">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="b5996-221">Możesz również uzyskać wspólnej lokalizacji online, który jest dostępny dla testerów i automatyczne skalowalności za pomocą zestawów skali maszyny Wirtualnej platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b5996-221">You also get a common online location that’s accessible to testers, and automatic scalability through Azure VM scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="b5996-222">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b5996-222">Next steps</span></span>

<span data-ttu-id="b5996-223">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="b5996-223">Explore this content more in-depth on the GitHub wiki:</span></span>

<span data-ttu-id="b5996-224">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/03.-How-to-deploy-your-Windows-containers-based-App-INTO-Azure-VMs-(including-Ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="b5996-224">[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="b5996-225">Wskazówki 4: Wdrażanie aplikacji opartych na kontenery systemu Windows na Kubernetes w usłudze kontenera platformy Azure</span><span class="sxs-lookup"><span data-stu-id="b5996-225">Walkthrough 4: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b5996-226">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="b5996-226">Technical walkthrough availability</span></span>

<span data-ttu-id="b5996-227">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="b5996-227">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="b5996-228">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/04.-How-to-deploy-your-Windows-containers-based-Apps-INTO-Kubernetes-in-Azure-container-Service-(including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="b5996-228">[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="b5996-229">Omówienie</span><span class="sxs-lookup"><span data-stu-id="b5996-229">Overview</span></span>

<span data-ttu-id="b5996-230">Aplikacja, która jest oparta na kontenery Windows szybko będą musieli używać platformy optymalizacji jeszcze bardziej przenoszenie z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="b5996-230">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="b5996-231">To pozwala łatwo osiągnąć wysoką skalowalność na potrzeby lepiej automatycznego skalowalność i uzyskać znaczne ulepszenia w automatycznego wdrożenia i przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="b5996-231">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="b5996-232">Te cele można osiągnąć za pomocą orchestrator [Kubernetes](https://kubernetes.io/), dostępną w [usługi kontenera platformy Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="b5996-232">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="b5996-233">Cele</span><span class="sxs-lookup"><span data-stu-id="b5996-233">Goals</span></span>

<span data-ttu-id="b5996-234">Celem tego przewodnika jest Dowiedz się, jak wdrożyć aplikację na podstawie kontenera systemu Windows do Kubernetes (nazywane również *K8s*) w usłudze kontenera platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b5996-234">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="b5996-235">Wdrażanie na Kubernetes od podstaw jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="b5996-235">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="b5996-236">Wdrażanie klastra Kubernetes do usługi kontenera platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b5996-236">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="b5996-237">Wdrażanie aplikacji i powiązanych zasobów do klastra Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b5996-237">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="b5996-238">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="b5996-238">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="b5996-239">Scenariusz A: Wdróż bezpośrednio do klastra Kubernetes z tego środowiska deweloperskiego</span><span class="sxs-lookup"><span data-stu-id="b5996-239">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Wdrażanie bezpośrednio do klastra Kubernetes środowiska programowania](./media/image5-7.png)

> <span data-ttu-id="b5996-241">**Rysunek 5-7.**</span><span class="sxs-lookup"><span data-stu-id="b5996-241">**Figure 5-7.**</span></span> <span data-ttu-id="b5996-242">Wdrażanie bezpośrednio do klastra Kubernetes środowiska programowania</span><span class="sxs-lookup"><span data-stu-id="b5996-242">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="b5996-243">Scenariusz B: wdrożyć klaster Kubernetes z elementu konfiguracji/CD potoków w Team Services</span><span class="sxs-lookup"><span data-stu-id="b5996-243">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![Wdrażanie klastra Kubernetes z potoków CI/CD w Team Services](./media/image5-8.png)

> <span data-ttu-id="b5996-245">**Rysunek 5 – 8.**</span><span class="sxs-lookup"><span data-stu-id="b5996-245">**Figure 5-8.**</span></span> <span data-ttu-id="b5996-246">Wdrażanie klastra Kubernetes z potoków CI/CD w Team Services</span><span class="sxs-lookup"><span data-stu-id="b5996-246">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="b5996-247">Zalety</span><span class="sxs-lookup"><span data-stu-id="b5996-247">Benefits</span></span>

<span data-ttu-id="b5996-248">Istnieje wiele korzyści z wdrażaniem do klastra w Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b5996-248">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="b5996-249">Największych korzyści jest uzyskanie środowisku gotowe do produkcji, w którym użytkownik może skalowalnego w poziomie aplikacji na podstawie liczby wystąpień kontenera, aby użyć (wewnętrzny skalowalności w istniejących węzłów), a na podstawie liczby węzłów lub maszyn wirtualnych w klastrze ( globalne skalowanie klastra).</span><span class="sxs-lookup"><span data-stu-id="b5996-249">The biggest benefit is that you get a production-ready environment in which you can scale-out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="b5996-250">Usługa kontenera platformy Azure optymalizuje popularnych open source narzędzia i technologie specjalnie dla platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b5996-250">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="b5996-251">Możesz uzyskać Otwórz rozwiązanie, które oferuje przenośność, zarówno w przypadku kontenerów, jak i konfigurację aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5996-251">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="b5996-252">Wybierz rozmiar, liczby hostów, a narzędzia orchestrator-kontenera usługi obsługuje wszystkie inne.</span><span class="sxs-lookup"><span data-stu-id="b5996-252">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="b5996-253">Z Kubernetes deweloperzy mogą postępu od planowania fizycznych i maszyn wirtualnych do planowania skoncentrowane kontenera infrastruktury, która ułatwia obsługę następujących funkcji, między innymi:</span><span class="sxs-lookup"><span data-stu-id="b5996-253">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

-   <span data-ttu-id="b5996-254">Aplikacje oparte na wielu kontenerów</span><span class="sxs-lookup"><span data-stu-id="b5996-254">Applications based on multiple containers</span></span>

-   <span data-ttu-id="b5996-255">Replikowanie wystąpień kontenera i skalowanie automatyczne pozioma</span><span class="sxs-lookup"><span data-stu-id="b5996-255">Replicating container instances and horizontal autoscaling</span></span>

-   <span data-ttu-id="b5996-256">Nazewnictwo i odkrywania (na przykład wewnętrzny serwer DNS)</span><span class="sxs-lookup"><span data-stu-id="b5996-256">Naming and discovering (for example, internal DNS)</span></span>

-   <span data-ttu-id="b5996-257">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="b5996-257">Balancing loads</span></span>

-   <span data-ttu-id="b5996-258">Wprowadzanie aktualizacji</span><span class="sxs-lookup"><span data-stu-id="b5996-258">Rolling updates</span></span>

-   <span data-ttu-id="b5996-259">Dystrybuowanie kluczy tajnych</span><span class="sxs-lookup"><span data-stu-id="b5996-259">Distributing secrets</span></span>

-   <span data-ttu-id="b5996-260">Sprawdzanie kondycji aplikacji</span><span class="sxs-lookup"><span data-stu-id="b5996-260">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="b5996-261">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b5996-261">Next steps</span></span>

<span data-ttu-id="b5996-262">Poznaj więcej informacji na temat zawartości w witrynie typu wiki GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-() Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="b5996-262">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="b5996-263">Wskazówki 5: Wdrażanie aplikacji opartych na kontenery systemu Windows do usługi Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="b5996-263">Walkthrough 5: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="b5996-264">Dostępność wskazówki techniczne</span><span class="sxs-lookup"><span data-stu-id="b5996-264">Technical walkthrough availability</span></span>

<span data-ttu-id="b5996-265">Pełny techniczny przewodnik jest dostępna w wiki eShopModernizing repozytorium GitHub:</span><span class="sxs-lookup"><span data-stu-id="b5996-265">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="b5996-266">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/05.-How-to-deploy-your-Windows-containers-based-Apps-INTO-Azure-Service-Fabric-(including-Ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="b5996-266">[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="b5996-267">Omówienie</span><span class="sxs-lookup"><span data-stu-id="b5996-267">Overview</span></span>

<span data-ttu-id="b5996-268">Aplikacja, która jest oparta na kontenery Windows szybko będą musieli używać platformy optymalizacji jeszcze bardziej przenoszenie z maszyn wirtualnych IaaS.</span><span class="sxs-lookup"><span data-stu-id="b5996-268">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="b5996-269">To pozwala łatwo osiągnąć wysoką skalowalność na potrzeby lepiej automatycznego skalowalność i uzyskać znaczne ulepszenia w automatycznego wdrożenia i przechowywanie wersji.</span><span class="sxs-lookup"><span data-stu-id="b5996-269">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="b5996-270">Można osiągnięcie tych celów, za pomocą usługi orchestrator sieci szkieletowej usług Azure, która jest dostępna w chmurze Azure, ale również dostępne do użycia lokalnego, a nawet w innej chmurze publicznej.</span><span class="sxs-lookup"><span data-stu-id="b5996-270">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="b5996-271">Cele</span><span class="sxs-lookup"><span data-stu-id="b5996-271">Goals</span></span>

<span data-ttu-id="b5996-272">Celem tego przewodnika jest informacje na temat wdrażania aplikacji na podstawie kontenera systemu Windows do klastra usługi sieć szkieletowa na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="b5996-272">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="b5996-273">Wdrażanie sieci szkieletowej usług od podstaw jest procesem dwuetapowym:</span><span class="sxs-lookup"><span data-stu-id="b5996-273">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="b5996-274">Wdrażanie klastra usługi sieć szkieletowa usług Azure (lub innego środowiska).</span><span class="sxs-lookup"><span data-stu-id="b5996-274">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="b5996-275">Wdrażanie aplikacji i powiązanych zasobów do klastra usługi sieć szkieletowa usług.</span><span class="sxs-lookup"><span data-stu-id="b5996-275">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="b5996-276">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="b5996-276">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="b5996-277">Scenariusz A: Wdróż bezpośrednio do klastra usługi sieć szkieletowa z tego środowiska deweloperskiego</span><span class="sxs-lookup"><span data-stu-id="b5996-277">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Wdrażanie bezpośrednio do klastra usługi sieć szkieletowa środowiska programowania](./media/image5-9.png)

> <span data-ttu-id="b5996-279">**Rysunek 5 – 9.**</span><span class="sxs-lookup"><span data-stu-id="b5996-279">**Figure 5-9.**</span></span> <span data-ttu-id="b5996-280">Wdrażanie bezpośrednio do klastra usługi sieć szkieletowa środowiska programowania</span><span class="sxs-lookup"><span data-stu-id="b5996-280">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="b5996-281">Scenariusz B: wdrażanie klastra usługi sieć szkieletowa z elementu konfiguracji/CD potoków w Team Services</span><span class="sxs-lookup"><span data-stu-id="b5996-281">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Wdrażanie klastra usługi sieć szkieletowa z potoków CI/CD w Visual Studio Team Services](./media/image5-10.png)

> <span data-ttu-id="b5996-283">**Rysunek 5-10.**</span><span class="sxs-lookup"><span data-stu-id="b5996-283">**Figure 5-10.**</span></span> <span data-ttu-id="b5996-284">Wdrażanie klastra usługi sieć szkieletowa z potoków CI/CD w Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="b5996-284">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="b5996-285">Zalety</span><span class="sxs-lookup"><span data-stu-id="b5996-285">Benefits</span></span>

<span data-ttu-id="b5996-286">Korzyści z wdrożenia do klastra w sieci szkieletowej usług są podobne do korzyści wynikające ze stosowania Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b5996-286">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="b5996-287">Jedną różnicą, jednak jest to sieci szkieletowej usług środowiska produkcyjnego bardzo dojrzałe dla aplikacji systemu Windows w porównaniu do Kubernetes, objęte był w wersji zapoznawczej kontenerów systemu Windows do wcześniej z 2017 r.</span><span class="sxs-lookup"><span data-stu-id="b5996-287">One difference, though, is that Service Fabric is a very mature production environment for Windows applications compared to Kubernetes, which was in preview for Windows Containers until early fall of 2017.</span></span> <span data-ttu-id="b5996-288">(Kubernetes jest bardziej dojrzałe środowisko dla systemu Linux).</span><span class="sxs-lookup"><span data-stu-id="b5996-288">(Kubernetes is a more mature environment for Linux).</span></span> 

<span data-ttu-id="b5996-289">Główne zaletą używania sieci szkieletowej usług Azure jest uzyskanie środowisku gotowe do produkcji, w którym użytkownik może skalowalnego w poziomie aplikacji na podstawie liczby wystąpień kontenera, aby użyć (wewnętrzny skalowalności w istniejących węzłów), a na podstawie liczby węzły lub maszyny wirtualne w klastrze (globalne skalowanie klastra).</span><span class="sxs-lookup"><span data-stu-id="b5996-289">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale-out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="b5996-290">Sieć szkieletowa usług Azure oferuje przenośność zarówno w przypadku kontenerów, jak i konfigurację aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5996-290">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="b5996-291">Masz usługi sieć szkieletowa klastra na platformie Azure, lub jego zainstalowanie lokalnego we własnym centrum danych.</span><span class="sxs-lookup"><span data-stu-id="b5996-291">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="b5996-292">Można nawet zainstalować klaster sieci szkieletowej usług w innej chmurze tak samo, jak [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="b5996-292">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="b5996-293">Z sieci szkieletowej usług deweloperzy mogą postępu od planowania fizycznych i maszyn wirtualnych do planowania skoncentrowane kontenera infrastruktury, która ułatwia obsługę następujących funkcji, między innymi:</span><span class="sxs-lookup"><span data-stu-id="b5996-293">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

-   <span data-ttu-id="b5996-294">Aplikacje oparte na wiele kontenerów.</span><span class="sxs-lookup"><span data-stu-id="b5996-294">Applications based on multiple containers.</span></span>

-   <span data-ttu-id="b5996-295">Replikowanie wystąpień kontenera i poziomy Skalowanie automatyczne.</span><span class="sxs-lookup"><span data-stu-id="b5996-295">Replicating container instances and horizontal autoscaling.</span></span>

-   <span data-ttu-id="b5996-296">Nazewnictwo i odkrywania (na przykład wewnętrzny serwer DNS).</span><span class="sxs-lookup"><span data-stu-id="b5996-296">Naming and discovering (for example, internal DNS).</span></span>

-   <span data-ttu-id="b5996-297">Równoważenie obciążenia.</span><span class="sxs-lookup"><span data-stu-id="b5996-297">Balancing loads.</span></span>

-   <span data-ttu-id="b5996-298">Wprowadzanie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="b5996-298">Rolling updates.</span></span>

-   <span data-ttu-id="b5996-299">Dystrybuowanie kluczy tajnych.</span><span class="sxs-lookup"><span data-stu-id="b5996-299">Distributing secrets.</span></span>

-   <span data-ttu-id="b5996-300">Umożliwia sprawdzenie kondycji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5996-300">Application health checks.</span></span>

<span data-ttu-id="b5996-301">Następujące funkcje są wyłączne w sieci szkieletowej usług (w porównaniu do innych orchestrators):</span><span class="sxs-lookup"><span data-stu-id="b5996-301">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

-   <span data-ttu-id="b5996-302">Możliwości usługi stanowej, za pomocą niezawodnych usług modelu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5996-302">Stateful services capability, through the Reliable Services application model.</span></span>

-   <span data-ttu-id="b5996-303">Wzorzec złośliwych użytkowników za pomocą modelu aplikacji Reliable Actors.</span><span class="sxs-lookup"><span data-stu-id="b5996-303">Actors pattern, through the Reliable Actors application model.</span></span>

-   <span data-ttu-id="b5996-304">Wdróż procesów kości bez systemu operacyjnego, oprócz kontenery systemu Windows lub Linux.</span><span class="sxs-lookup"><span data-stu-id="b5996-304">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

-   <span data-ttu-id="b5996-305">Zaawansowane aktualizacji stopniowych i kontroli kondycji.</span><span class="sxs-lookup"><span data-stu-id="b5996-305">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="b5996-306">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b5996-306">Next steps</span></span>

<span data-ttu-id="b5996-307">Zapoznaj się z bardziej szczegółowym zawartość w witrynie typu wiki GitHub:</span><span class="sxs-lookup"><span data-stu-id="b5996-307">Explore this content more in-depth on the GitHub wiki:</span></span>

<span data-ttu-id="b5996-308">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/05.-How-to-deploy-your-Windows-containers-based-Apps-INTO-Azure-Service-Fabric-(including-Ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="b5996-308">[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b5996-309">[Poprzednie](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[dalej](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="b5996-309">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
