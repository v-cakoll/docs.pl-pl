---
title: Wymagania wstępne dla platformy .NET Core w Windows
description: Dowiedz się, jakie zależności dotyczące usługi Windows komputera na opracowywanie i uruchamianie aplikacji .NET Core.
ms.date: 12/05/2018
ms.openlocfilehash: 8f9a823ab3eea15d7e33da6ff00992057c8c4e38
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130924"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="1d7e1-103">Wymagania wstępne dla platformy .NET Core w Windows</span><span class="sxs-lookup"><span data-stu-id="1d7e1-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="1d7e1-104">W tym artykule przedstawiono obsługiwane wersje systemu operacyjnego w celu uruchamiania aplikacji .NET Core na Windows.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="1d7e1-105">Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core na Windows:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="1d7e1-106">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="1d7e1-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="1d7e1-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1d7e1-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [<span data-ttu-id="1d7e1-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1d7e1-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="1d7e1-109">Ponadto, jeśli tworzysz Windows przy użyciu programu Visual Studio 2017, [wstępnie wymaganych składników w programie Visual Studio 2017](#prerequisites-with-visual-studio-2017) sekcji znajduje się w bardziej szczegółowo wersje minimalną obsługę programowania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-109">Also, if you're developing on Windows using Visual Studio 2017, the [Prerequisites with Visual Studio 2017](#prerequisites-with-visual-studio-2017) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="1d7e1-110">.NET core, obsługiwane wersje serwera Windows</span><span class="sxs-lookup"><span data-stu-id="1d7e1-110">.NET Core supported Windows versions</span></span>

<span data-ttu-id="1d7e1-111">.NET core jest obsługiwana w następujących wersjach:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-111">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="1d7e1-112">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="1d7e1-112">Windows 7 SP1</span></span>
* <span data-ttu-id="1d7e1-113">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="1d7e1-113">Windows 8.1</span></span>
* <span data-ttu-id="1d7e1-114">Rocznicowa aktualizacja (wersja 1607) dla systemu Windows 10 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="1d7e1-114">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="1d7e1-115">Windows Server 2008 R2 z dodatkiem SP1 (pełny serwer lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="1d7e1-115">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="1d7e1-116">Windows Server 2012 z dodatkiem SP1 (pełny serwer lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="1d7e1-116">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="1d7e1-117">Windows Server 2012 R2 (pełny serwer lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="1d7e1-117">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="1d7e1-118">Windows Server 2016 lub nowszy (pełny serwer, Server Core lub Nano Server)</span><span class="sxs-lookup"><span data-stu-id="1d7e1-118">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="1d7e1-119">.NET core, obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="1d7e1-119">.NET Core supported operating systems</span></span>

<span data-ttu-id="1d7e1-120">Następujące artykuły mają pełną listę systemów operacyjnych .NET Core, obsługiwane poszczególnych wersji:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-120">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="1d7e1-121">.NET core 2.2</span><span class="sxs-lookup"><span data-stu-id="1d7e1-121">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="1d7e1-122">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="1d7e1-122">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="1d7e1-123">.NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="1d7e1-123">.NET Core 1.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1-supported-os.md)
* [<span data-ttu-id="1d7e1-124">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1d7e1-124">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="1d7e1-125">Łącza pobierania oraz więcej informacji, zobacz [pobiera .NET](https://www.microsoft.com/net/download) Aby pobrać najnowszą wersję lub [.NET pobiera archiwum](https://dotnet.microsoft.com/download/archives#dotnet-core) dla starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-125">For download links and more information, see [.NET downloads](https://www.microsoft.com/net/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="1d7e1-126">Zależności platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="1d7e1-126">.NET Core dependencies</span></span>

<span data-ttu-id="1d7e1-127">.NET core 1.1 i wcześniejszych wersji wymagają pakietu redystrybucyjnego Visual C++, podczas uruchamiania na wersje Windows wcześniejsze niż Windows 10 i Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-127">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="1d7e1-128">Ta zależność jest automatycznie instalowany przez Instalatora programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-128">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="1d7e1-129">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musi zostać zainstalowany ręcznie po:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-129">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="1d7e1-130">Instalowanie platformy .NET Core za pomocą [skryptu Instalatora](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="1d7e1-130">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="1d7e1-131">Wdrażanie aplikacji .NET Core w niezależna.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-131">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="1d7e1-132">Kompilowanie produktu ze źródła.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-132">Building the product from source.</span></span>
* <span data-ttu-id="1d7e1-133">Instalowanie platformy .NET Core za pomocą *zip* pliku.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-133">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="1d7e1-134">Może to obejmować serwery kompilacji/ciągłej integracji/ciągłego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-134">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="1d7e1-135">**Dla Windows 8.1 i starszych wersjach, lub Windows Server 2012 R2 i wcześniejszych wersji:**</span><span class="sxs-lookup"><span data-stu-id="1d7e1-135">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="1d7e1-136">Upewnij się, że instalacja Windows jest aktualny i zawiera [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), którą można zainstalować za pośrednictwem usługi Windows Update.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-136">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="1d7e1-137">Jeśli nie masz zainstalowano tę aktualizację, zobaczysz następujący błąd podczas uruchamiania aplikacji .NET Core: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="1d7e1-137">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="1d7e1-138">**Windows 7 lub Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="1d7e1-138">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="1d7e1-139">Oprócz KB2999226, upewnij się, masz także [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-139">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="1d7e1-140">Jeśli nie zainstalowano tę aktualizację, zobaczysz błąd podobny do poniższego, podczas uruchamiania aplikacji .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-140">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="1d7e1-141">Wymagania wstępne dotyczące programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1d7e1-141">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="1d7e1-142">Tworzenie aplikacji .NET Core przy użyciu zestawu .NET Core SDK, można użyć dowolnego edytora.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-142">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="1d7e1-143">Program Visual Studio 2017 udostępnia zintegrowane środowisko programistyczne dla aplikacji .NET Core w Windows.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-143">Visual Studio 2017 provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="1d7e1-144">Możesz dowiedzieć się więcej o zmianach wprowadzonych w programie Visual Studio 2017 w [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="1d7e1-144">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1d7e1-145">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1d7e1-145">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="1d7e1-146">Aby opracować aplikacje platformy .NET Core w programie Visual Studio 2017 przy użyciu zestawu .NET Core 2.2 SDK:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-146">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="1d7e1-147">[Pobierz i zainstaluj program Visual Studio 2017 w wersji 15.9.0 lub nowszej](/visualstudio/install/install-visual-studio) z **programowanie dla wielu platform .NET Core** obciążenie (w **inne zestawy narzędzi** sekcji) wybranego.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-147">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="1d7e1-149">Po **programowanie dla wielu platform .NET Core** zestawu narzędzi jest zainstalowana, program Visual Studio instaluje zwykle poprzedniej wersji programu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-149">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="1d7e1-150">Na przykład program Visual Studio 2017 15.9 używa zestawu SDK programu .NET Core 2.1 domyślnie po zainstalowaniu obciążenia.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-150">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="1d7e1-151">Aby zaktualizować program Visual Studio, aby użyć zestawu .NET Core 2.2 SDK:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-151">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="1d7e1-152">Zainstaluj [.NET Core SDK 2,2](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="1d7e1-152">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="1d7e1-153">Jeśli chcesz, aby projekt do najnowsze środowisko uruchomieniowe platformy .NET Core, należy przekierować istniejących lub nowych projektów .NET Core do wersji 2.2 podstawowych platformy .NET przy użyciu następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-153">If you want your project to use the latest .NET Core runtime, retarget existing or new .NET Core projects to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="1d7e1-154">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-154">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="1d7e1-155">W **platformę docelową** menu wyboru, ustaw wartość **platformy .NET Core 2.2**.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-155">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.2" target framework wybranego elementu](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="1d7e1-157">Gdy program Visual Studio skonfigurowane przy użyciu zestawu .NET Core 2.2 SDK, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-157">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="1d7e1-158">Otwórz, tworzenia i uruchamiania istniejących projektów .NET Core 1.x i 2.x.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-158">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="1d7e1-159">Przekierowanie wersji 1.x i 2.x projektów .NET Core do platformy .NET Core 2.2, kompilacja i uruchom.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-159">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="1d7e1-160">Utwórz nowe projekty platformy .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-160">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1d7e1-161">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1d7e1-161">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="1d7e1-162">Tworzenie aplikacji .NET Core 1.x, w programie Visual Studio, [Pobierz i zainstaluj program Visual Studio 2017](/visualstudio/install/install-visual-studio) z **"Programowanie dla wielu platform .NET Core"** obciążenia (w **inne zestawy narzędzi**sekcji) wybranego.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-162">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="1d7e1-164">Można użyć programu Visual Studio 2015 dla platformy .NET Core 1.x rozwoju, ale nie jest zalecane w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-164">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="1d7e1-165">Zestaw narzędzi .NET Core jest w wersji preview, która nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-165">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="1d7e1-166">Projekty są oparte na pliku project.json, które jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-166">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="1d7e1-167">Aby uzyskać więcej informacji na temat zmiany formatu projektu, zobacz [ogólny przegląd zmian](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="1d7e1-167">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="1d7e1-168">Aby sprawdzić używanej wersji programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="1d7e1-168">To verify your Visual Studio version:</span></span>
>
> * <span data-ttu-id="1d7e1-169">Na **pomocy** menu, wybierz **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-169">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="1d7e1-170">W **Microsoft Visual Studio** okno dialogowe, sprawdź numer wersji.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-170">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="1d7e1-171">W przypadku aplikacji .NET Core 3.0 w wersji zapoznawczej 1, Visual Studio 2019 r w wersji zapoznawczej 1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-171">For .NET Core 3.0 Preview 1 apps, Visual Studio 2019 Preview 1 or higher.</span></span>
>   * <span data-ttu-id="1d7e1-172">W przypadku aplikacji platformy .NET Core 2.2 programu Visual Studio 2017 w wersji 15.9 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-172">For .NET Core 2.2 apps, Visual Studio 2017 version 15.9 or higher.</span></span>
>   * <span data-ttu-id="1d7e1-173">W przypadku aplikacji platformy .NET Core 2.1 programu Visual Studio 2017 w wersji 15.7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-173">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="1d7e1-174">W przypadku aplikacji .NET Core 1.x programu Visual Studio 2017 w wersji 15,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-174">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
