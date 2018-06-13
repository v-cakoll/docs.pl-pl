---
title: Wymagania wstępne dotyczące platformy .NET Core w systemie Windows
description: Dowiedz się, w zależności, należy na okien komputera do opracowywania i uruchamiania aplikacji .NET Core.
author: JRAlexander
ms.author: johalex
ms.date: 05/18/2018
ms.openlocfilehash: 3d172c83f0a79744afbaeeff52d7fea62d9b98b6
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34311991"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="8ae68-103">Wymagania wstępne dotyczące platformy .NET Core w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="8ae68-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="8ae68-104">W tym artykule opisano zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="8ae68-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="8ae68-105">Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core w systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="8ae68-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="8ae68-106">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="8ae68-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="8ae68-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8ae68-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="8ae68-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8ae68-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="8ae68-109">Oprogramowanie .NET core obsługiwane wersje systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8ae68-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="8ae68-110">Oprogramowanie .NET core jest obsługiwana w następujących wersjach:</span><span class="sxs-lookup"><span data-stu-id="8ae68-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="8ae68-111">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="8ae68-111">Windows 7 SP1</span></span>
* <span data-ttu-id="8ae68-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="8ae68-112">Windows 8.1</span></span>
* <span data-ttu-id="8ae68-113">Windows 10 Anniversary Update (w wersji 1607) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="8ae68-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="8ae68-114">Windows Server 2008 R2 z dodatkiem SP1 (całego serwera lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="8ae68-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="8ae68-115">Windows Server 2012 z dodatkiem SP1 (całego serwera lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="8ae68-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="8ae68-116">Windows Server 2012 R2 (całego serwera lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="8ae68-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="8ae68-117">Windows Server 2016 lub nowszy (całego serwera, Server Core lub Nano Server)</span><span class="sxs-lookup"><span data-stu-id="8ae68-117">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="8ae68-118">Następujące artykuły zawierają pełną listę .NET Core, obsługiwane systemy operacyjne dla poszczególnych wersji:</span><span class="sxs-lookup"><span data-stu-id="8ae68-118">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="8ae68-119">Oprogramowanie .NET core 2.1 — obsługiwane wersje systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="8ae68-119">.NET Core 2.1 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="8ae68-120">Oprogramowanie .NET core 2.0 — obsługiwane wersje systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="8ae68-120">.NET Core 2.0 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [<span data-ttu-id="8ae68-121">.NET core 1.x — wersje obsługiwany system operacyjny</span><span class="sxs-lookup"><span data-stu-id="8ae68-121">.NET Core 1.x - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a><span data-ttu-id="8ae68-122">Zależności .NET core</span><span class="sxs-lookup"><span data-stu-id="8ae68-122">.NET Core dependencies</span></span>

<span data-ttu-id="8ae68-123">Podczas pracy z wersjami systemu Windows starszych niż Windows 10 i Windows Server 2016 .NET core 1.1 i wcześniejszych wersjach wymaga pakietu redystrybucyjnego Visual C++</span><span class="sxs-lookup"><span data-stu-id="8ae68-123">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="8ae68-124">Ta zależność jest automatycznie instalowany przez Instalatora platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ae68-124">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="8ae68-125">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musi zostać zainstalowany ręcznie po:</span><span class="sxs-lookup"><span data-stu-id="8ae68-125">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="8ae68-126">Instalowanie platformy .NET Core z [skryptu Instalatora](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="8ae68-126">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="8ae68-127">Wdrażanie aplikacji .NET Core niezależne.</span><span class="sxs-lookup"><span data-stu-id="8ae68-127">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="8ae68-128">Kompilowanie produktu ze źródła.</span><span class="sxs-lookup"><span data-stu-id="8ae68-128">Building the product from source.</span></span>
* <span data-ttu-id="8ae68-129">Instalowanie platformy .NET Core za pomocą *.zip* pliku.</span><span class="sxs-lookup"><span data-stu-id="8ae68-129">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="8ae68-130">Może to obejmować serwery kompilacji/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="8ae68-130">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="8ae68-131">**Windows 8.1 i starszych wersjach, lub Windows Server 2012 R2 i wcześniejszych wersji:**</span><span class="sxs-lookup"><span data-stu-id="8ae68-131">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="8ae68-132">Upewnij się, że instalacji systemu Windows jest aktualny i uwzględnia [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), które można zainstalować za pomocą usługi Windows Update.</span><span class="sxs-lookup"><span data-stu-id="8ae68-132">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="8ae68-133">Jeśli nie zainstalowano tę aktualizację, podczas uruchamiania aplikacji .NET Core zostanie wyświetlony błąd podobnie do następującej: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="8ae68-133">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="8ae68-134">**W przypadku systemu Windows 7 lub Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="8ae68-134">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="8ae68-135">Oprócz KB2999226, upewnij się, masz również [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="8ae68-135">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="8ae68-136">Jeśli nie zainstalowano tę aktualizację, zostanie wyświetlone błąd podobny do następującego podczas uruchamiania aplikacji .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="8ae68-136">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="8ae68-137">Wstępnie wymaganych składników w programie Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="8ae68-137">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="8ae68-138">Do tworzenia aplikacji platformy .NET Core przy użyciu zestawu SDK .NET Core, można użyć dowolnego edytora.</span><span class="sxs-lookup"><span data-stu-id="8ae68-138">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="8ae68-139">[Visual Studio 2017](#visual-studio-2017) zapewnia zintegrowane środowisko deweloperskie dla aplikacji .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="8ae68-139">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="8ae68-140">Więcej informacji na temat zmian w programie Visual Studio 2017 w [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="8ae68-140">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8ae68-141">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8ae68-141">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="8ae68-142">Aby tworzyć aplikacje 2.x .NET Core w Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="8ae68-142">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="8ae68-143">[Pobierz i zainstaluj program Visual Studio 2017 wersji 15.3.0 lub nowszej](/visualstudio/install/install-visual-studio) z **aplikacji dla wielu platform .NET Core** obciążenie (w **inne procesami** sekcji) wybrane.</span><span class="sxs-lookup"><span data-stu-id="8ae68-143">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z obciążeniem "Programowanie wieloplatformowych .NET Core" wybrane](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="8ae68-145">Po **aplikacji dla wielu platform .NET Core** zestawu narzędzi jest zainstalowany, program Visual Studio 2017 używa .NET Core 1.x domyślnie.</span><span class="sxs-lookup"><span data-stu-id="8ae68-145">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="8ae68-146">Zainstaluj oprogramowanie .NET Core 2.x zestaw SDK, aby uzyskać pomoc techniczną 2.x .NET Core w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="8ae68-146">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="8ae68-147">Zainstaluj [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="8ae68-147">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="8ae68-148">Przekieruj istniejące lub nowe projekty 1.x .NET Core do platformy .NET Core 2.x z poniższymi instrukcjami:</span><span class="sxs-lookup"><span data-stu-id="8ae68-148">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="8ae68-149">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="8ae68-149">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="8ae68-150">W **platformy docelowej** zaznaczenia menu, ustaw wartość na **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="8ae68-150">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.0" docelowego framework wybranego elementu](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="8ae68-152">Raz .NET Core 2.x zainstalowano zestaw SDK dla programu Visual Studio 2017 używa .NET Core SDK 2.x domyślnie i obsługuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="8ae68-152">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

* <span data-ttu-id="8ae68-153">Otwórz kompilacji i uruchamianie istniejących projektów 1.x .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ae68-153">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="8ae68-154">Przekierować projekty 1.x .NET Core 2.x, kompilacji i uruchom .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ae68-154">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
* <span data-ttu-id="8ae68-155">Utwórz nowe projekty 2.x .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8ae68-155">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8ae68-156">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8ae68-156">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8ae68-157">Do opracowywania aplikacji 1.x .NET Core w programie Visual Studio, [pobrać i zainstalować program Visual Studio 2017 RTM (wersja 15.0.26228.4) lub wyższej](/visualstudio/install/install-visual-studio) z **"Programowanie wieloplatformowych .NET Core"** obciążenie (w  **Inne procesami** sekcji) wybrane.</span><span class="sxs-lookup"><span data-stu-id="8ae68-157">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z obciążeniem "Programowanie wieloplatformowych .NET Core" wybrane](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="8ae68-159">Można użyć programu Visual Studio 2015 dla platformy .NET Core 1.x wdrożenia, ale nie jest zalecane z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="8ae68-159">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="8ae68-160">Narzędzia .NET Core jest w wersji preview, która nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="8ae68-160">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="8ae68-161">Projekty są oparte na project.json, które jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="8ae68-161">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="8ae68-162">Aby uzyskać więcej informacji o zmianach format projektu, zobacz [ogólne omówienie zmiany](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="8ae68-162">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

> [!TIP]
> <span data-ttu-id="8ae68-163">Aby sprawdzić swoją wersję programu Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="8ae68-163">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="8ae68-164">Na **pomocy** menu, wybierz **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8ae68-164">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="8ae68-165">W **Microsoft Visual Studio** okna dialogowego, sprawdź numer wersji.</span><span class="sxs-lookup"><span data-stu-id="8ae68-165">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="8ae68-166">W przypadku aplikacji .NET Core 2.1 RC programu Visual Studio 2017 wersji 15.7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="8ae68-166">For .NET Core 2.1 RC apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="8ae68-167">W przypadku aplikacji .NET Core 2.0, Visual Studio 2017 wersji 15.3 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="8ae68-167">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="8ae68-168">W przypadku aplikacji .NET Core 1.x Visual Studio 2017 wersji 15,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="8ae68-168">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
