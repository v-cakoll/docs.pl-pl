---
title: Wymagania wstępne dla platformy .NET Core w Windows
description: Dowiedz się, jakie zależności dotyczące usługi Windows komputera na opracowywanie i uruchamianie aplikacji .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 08/31/2018
ms.openlocfilehash: bbf54c8d215783656830f0fa035708be82a7c39c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482613"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="ed723-103">Wymagania wstępne dla platformy .NET Core w Windows</span><span class="sxs-lookup"><span data-stu-id="ed723-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="ed723-104">W tym artykule przedstawiono zależności niezbędne do tworzenia aplikacji platformy .NET Core w Windows.</span><span class="sxs-lookup"><span data-stu-id="ed723-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="ed723-105">Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core na Windows:</span><span class="sxs-lookup"><span data-stu-id="ed723-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="ed723-106">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="ed723-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="ed723-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ed723-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="ed723-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ed723-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="ed723-109">.NET core, obsługiwane wersje serwera Windows</span><span class="sxs-lookup"><span data-stu-id="ed723-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="ed723-110">.NET core jest obsługiwana w następujących wersjach:</span><span class="sxs-lookup"><span data-stu-id="ed723-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="ed723-111">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="ed723-111">Windows 7 SP1</span></span>
* <span data-ttu-id="ed723-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ed723-112">Windows 8.1</span></span>
* <span data-ttu-id="ed723-113">Rocznicowa aktualizacja (wersja 1607) dla systemu Windows 10 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="ed723-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="ed723-114">Windows Server 2008 R2 z dodatkiem SP1 (pełny serwer lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="ed723-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="ed723-115">Windows Server 2012 z dodatkiem SP1 (pełny serwer lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="ed723-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="ed723-116">Windows Server 2012 R2 (pełny serwer lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="ed723-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="ed723-117">Windows Server 2016 lub nowszy (pełny serwer, Server Core lub Nano Server)</span><span class="sxs-lookup"><span data-stu-id="ed723-117">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="ed723-118">Następujące artykuły mają pełną listę systemów operacyjnych .NET Core, obsługiwane poszczególnych wersji:</span><span class="sxs-lookup"><span data-stu-id="ed723-118">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="ed723-119">.NET core 2.1 — obsługiwane wersje systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="ed723-119">.NET Core 2.1 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="ed723-120">.NET core 2.0 — obsługiwane wersje systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="ed723-120">.NET Core 2.0 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [<span data-ttu-id="ed723-121">.NET core 1.x — wersje obsługiwanych systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="ed723-121">.NET Core 1.x - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a><span data-ttu-id="ed723-122">Zależności platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="ed723-122">.NET Core dependencies</span></span>

<span data-ttu-id="ed723-123">.NET core 1.1 i wcześniejszych wersji wymagają pakietu redystrybucyjnego Visual C++, podczas uruchamiania na wersje Windows wcześniejsze niż Windows 10 i Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="ed723-123">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="ed723-124">Ta zależność jest automatycznie instalowany przez Instalatora programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ed723-124">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="ed723-125">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musi zostać zainstalowany ręcznie po:</span><span class="sxs-lookup"><span data-stu-id="ed723-125">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="ed723-126">Instalowanie platformy .NET Core za pomocą [skryptu Instalatora](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="ed723-126">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="ed723-127">Wdrażanie aplikacji .NET Core w niezależna.</span><span class="sxs-lookup"><span data-stu-id="ed723-127">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="ed723-128">Kompilowanie produktu ze źródła.</span><span class="sxs-lookup"><span data-stu-id="ed723-128">Building the product from source.</span></span>
* <span data-ttu-id="ed723-129">Instalowanie platformy .NET Core za pomocą *zip* pliku.</span><span class="sxs-lookup"><span data-stu-id="ed723-129">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="ed723-130">Może to obejmować serwery kompilacji/ciągłej integracji/ciągłego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="ed723-130">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="ed723-131">**Dla Windows 8.1 i starszych wersjach, lub Windows Server 2012 R2 i wcześniejszych wersji:**</span><span class="sxs-lookup"><span data-stu-id="ed723-131">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="ed723-132">Upewnij się, że instalacja Windows jest aktualny i zawiera [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), którą można zainstalować za pośrednictwem usługi Windows Update.</span><span class="sxs-lookup"><span data-stu-id="ed723-132">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="ed723-133">Jeśli nie masz zainstalowano tę aktualizację, zobaczysz następujący błąd podczas uruchamiania aplikacji .NET Core: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="ed723-133">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="ed723-134">**Windows 7 lub Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="ed723-134">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="ed723-135">Oprócz KB2999226, upewnij się, masz także [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ed723-135">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="ed723-136">Jeśli nie zainstalowano tę aktualizację, zobaczysz błąd podobny do poniższego, podczas uruchamiania aplikacji .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="ed723-136">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="ed723-137">Wymagania wstępne dotyczące programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ed723-137">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="ed723-138">Tworzenie aplikacji .NET Core przy użyciu zestawu .NET Core SDK, można użyć dowolnego edytora.</span><span class="sxs-lookup"><span data-stu-id="ed723-138">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="ed723-139">[Program Visual Studio 2017](#visual-studio-2017) zapewnia zintegrowane środowisko programistyczne dla aplikacji .NET Core w Windows.</span><span class="sxs-lookup"><span data-stu-id="ed723-139">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="ed723-140">Możesz dowiedzieć się więcej o zmianach wprowadzonych w programie Visual Studio 2017 w [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="ed723-140">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ed723-141">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ed723-141">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ed723-142">Do tworzenia aplikacji platformy .NET Core 2.1 w programie Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="ed723-142">To develop .NET Core 2.1 apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="ed723-143">[Pobierz i zainstaluj program Visual Studio 2017, wersja 15.7.0 lub nowszej](/visualstudio/install/install-visual-studio) z **programowanie dla wielu platform .NET Core** obciążenie (w **inne zestawy narzędzi** sekcji) wybranego.</span><span class="sxs-lookup"><span data-stu-id="ed723-143">[Download and install Visual Studio 2017 version 15.7.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs-15-8-workloads.jpg)

<span data-ttu-id="ed723-145">Po **programowanie dla wielu platform .NET Core** zestawu narzędzi jest zainstalowany, domyślnie i .NET Core 2.0 SDK korzysta z programu Visual Studio 2017 w wersji 15.7 programu Visual Studio 2017 15.8 użyto zestawu SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="ed723-145">After the **.NET Core cross-platform development** toolset is installed, by default, Visual Studio 2017 15.7 uses .NET Core 2.0 SDK and Visual Studio 2017 15.8 uses 2.1 SDK.</span></span>

 2. <span data-ttu-id="ed723-146">Jeśli używasz programu Visual Studio 2017 w wersji 15.7, zainstaluj [zestawu SDK programu .NET Core 2.1](https://www.microsoft.com/net/download/core) lub uaktualnienia do programu Visual Studio 2017 15.8.</span><span class="sxs-lookup"><span data-stu-id="ed723-146">If you're using Visual Studio 2017 15.7, install the [.NET Core 2.1 SDK](https://www.microsoft.com/net/download/core) or upgrade to Visual Studio 2017 15.8.</span></span>

 3. <span data-ttu-id="ed723-147">Przekieruj istniejących lub nowych projektów .NET Core do platformy .NET Core 2.1 przy użyciu następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="ed723-147">Retarget existing or new .NET Core projects to .NET Core 2.1 using the following instructions:</span></span>
    * <span data-ttu-id="ed723-148">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ed723-148">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="ed723-149">W **platformę docelową** menu wyboru, ustaw wartość **platformy .NET Core 2.1**.</span><span class="sxs-lookup"><span data-stu-id="ed723-149">In the **Target framework** selection menu, set the value to **.NET Core 2.1**.</span></span>

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.0" Target framework wybranego elementu](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="ed723-151">Gdy program Visual Studio skonfigurowane przy użyciu zestawu SDK programu .NET Core 2.1, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ed723-151">Once you have Visual Studio configured with .NET Core 2.1 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="ed723-152">Otwórz, tworzenia i uruchamiania istniejących projektów .NET Core 1.x i 2.x.</span><span class="sxs-lookup"><span data-stu-id="ed723-152">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="ed723-153">Przekieruj platformy .NET Core 1.x i 2.0 projektów .NET Core 2.1, skompilować i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="ed723-153">Retarget .NET Core 1.x and 2.0 projects to .NET Core 2.1, build, and run.</span></span>
* <span data-ttu-id="ed723-154">Utwórz nowe projekty platformy .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="ed723-154">Create new .NET Core 2.1 projects.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ed723-155">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ed723-155">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="ed723-156">Tworzenie aplikacji .NET Core 2.0, w programie Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="ed723-156">To develop .NET Core 2.0 apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="ed723-157">[Pobierz i zainstaluj program Visual Studio 2017 w wersji 15.3.0 lub nowszej](/visualstudio/install/install-visual-studio) z **programowanie dla wielu platform .NET Core** obciążenie (w **inne zestawy narzędzi** sekcji) wybranego.</span><span class="sxs-lookup"><span data-stu-id="ed723-157">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="ed723-159">Po **programowanie dla wielu platform .NET Core** zestawu narzędzi jest zainstalowana, program Visual Studio 2017 korzysta z platformy .NET Core 1.x domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ed723-159">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="ed723-160">Zainstaluj zestaw .NET Core 2.0 SDK można pobrać zestaw .NET Core 2.0 pomocy technicznej w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ed723-160">Install the .NET Core 2.0 SDK to get .NET Core 2.0 support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="ed723-161">Zainstaluj [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/dotnet-core/2.0).</span><span class="sxs-lookup"><span data-stu-id="ed723-161">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/dotnet-core/2.0).</span></span>
 3. <span data-ttu-id="ed723-162">Przekieruj istniejącej lub nowej platformy .NET Core 1.x projektów .NET Core 2.0 przy użyciu następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="ed723-162">Retarget existing or new .NET Core 1.x projects to .NET Core 2.0 using the following instructions:</span></span>
    * <span data-ttu-id="ed723-163">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ed723-163">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="ed723-164">W **platformę docelową** menu wyboru, ustaw wartość **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="ed723-164">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.0" Target framework wybranego elementu](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="ed723-166">Po zainstalowaniu zestawu .NET Core 2.0 SDK programu Visual Studio 2017 domyślnie używa .NET Core SDK 2.0 i obsługuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="ed723-166">Once the .NET Core 2.0 SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.0 by default, and supports the following actions:</span></span>

* <span data-ttu-id="ed723-167">Otwórz, tworzenie i uruchamianie istniejących projektów programu .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="ed723-167">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="ed723-168">Przekieruj projektów programu .NET Core 1.x do platformy .NET Core 2.0, kompilacja i uruchom.</span><span class="sxs-lookup"><span data-stu-id="ed723-168">Retarget .NET Core 1.x projects to .NET Core 2.0, build, and run.</span></span>
* <span data-ttu-id="ed723-169">Utwórz nowe projekty .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="ed723-169">Create new .NET Core 2.0 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ed723-170">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ed723-170">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ed723-171">Tworzenie aplikacji .NET Core 1.x, w programie Visual Studio, [Pobierz i zainstaluj program Visual Studio 2017](/visualstudio/install/install-visual-studio) z **"Programowanie dla wielu platform .NET Core"** obciążenia (w **inne zestawy narzędzi**sekcji) wybranego.</span><span class="sxs-lookup"><span data-stu-id="ed723-171">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="ed723-173">Można użyć programu Visual Studio 2015 dla platformy .NET Core 1.x rozwoju, ale nie jest zalecane w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="ed723-173">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="ed723-174">Zestaw narzędzi .NET Core jest w wersji preview, która nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="ed723-174">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="ed723-175">Projekty są oparte na pliku project.json, które jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="ed723-175">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="ed723-176">Aby uzyskać więcej informacji na temat zmiany formatu projektu, zobacz [ogólny przegląd zmian](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="ed723-176">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="ed723-177">Aby sprawdzić używanej wersji programu Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="ed723-177">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="ed723-178">Na **pomocy** menu, wybierz **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ed723-178">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="ed723-179">W **Microsoft Visual Studio** okno dialogowe, sprawdź numer wersji.</span><span class="sxs-lookup"><span data-stu-id="ed723-179">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="ed723-180">W przypadku aplikacji .NET Core 2.2 w wersji zapoznawczej 1, Visual Studio 2017 w wersji 15.9 (obecnie w wersji zapoznawczej) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ed723-180">For .NET Core 2.2 Preview 1 apps, Visual Studio 2017 version 15.9 (currently in Preview) or higher.</span></span>
>   * <span data-ttu-id="ed723-181">W przypadku aplikacji platformy .NET Core 2.1 programu Visual Studio 2017 w wersji 15.7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ed723-181">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="ed723-182">W przypadku aplikacji .NET Core 2.0, programu Visual Studio 2017 w wersji 15.3 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ed723-182">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="ed723-183">W przypadku aplikacji .NET Core 1.x programu Visual Studio 2017 w wersji 15,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ed723-183">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
