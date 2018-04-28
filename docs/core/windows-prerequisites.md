---
title: Wymagania wstępne dotyczące platformy .NET Core w systemie Windows
description: Dowiedz się, w zależności, należy na okien komputera do opracowywania i uruchamiania aplikacji .NET Core.
author: JRAlexander
ms.author: johalex
ms.date: 04/24/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 6f2ba8540a38f8e30d3d968f5e2c891c850053aa
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="ea317-103">Wymagania wstępne dotyczące platformy .NET Core w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="ea317-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="ea317-104">W tym artykule opisano zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="ea317-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="ea317-105">Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core w systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="ea317-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="ea317-106">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="ea317-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="ea317-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ea317-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="ea317-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ea317-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="ea317-109">Oprogramowanie .NET core obsługiwane wersje systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ea317-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="ea317-110">Oprogramowanie .NET core jest obsługiwana w następujących wersjach:</span><span class="sxs-lookup"><span data-stu-id="ea317-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="ea317-111">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="ea317-111">Windows 7 SP1</span></span>
* <span data-ttu-id="ea317-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ea317-112">Windows 8.1</span></span>
* <span data-ttu-id="ea317-113">Windows 10 Anniversary Update (w wersji 1607) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="ea317-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="ea317-114">Windows Server 2008 R2 z dodatkiem SP1 (całego serwera lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="ea317-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="ea317-115">Windows Server 2012 z dodatkiem SP1 (całego serwera lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="ea317-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="ea317-116">Windows Server 2012 R2 (całego serwera lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="ea317-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="ea317-117">Windows Server 2016 (całego serwera, Server Core lub serwerze Nano)</span><span class="sxs-lookup"><span data-stu-id="ea317-117">Windows Server 2016 (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="ea317-118">Zobacz [.NET Core 2.x - obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pełną listę .NET Core 2.x obsługiwanych systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="ea317-118">See [.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems.</span></span>

<span data-ttu-id="ea317-119">Zobacz [1.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pełną listę .NET Core 1.x obsługiwanych systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="ea317-119">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="ea317-120">Zależności .NET core</span><span class="sxs-lookup"><span data-stu-id="ea317-120">.NET Core dependencies</span></span>

<span data-ttu-id="ea317-121">Podczas pracy z wersjami systemu Windows starszych niż Windows 10 i Windows Server 2016 .NET core 1.1 i wcześniejszych wersjach wymaga pakietu redystrybucyjnego Visual C++</span><span class="sxs-lookup"><span data-stu-id="ea317-121">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="ea317-122">Ta zależność jest automatycznie instalowany przez Instalatora platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea317-122">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="ea317-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musi zostać zainstalowany ręcznie po:</span><span class="sxs-lookup"><span data-stu-id="ea317-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="ea317-124">Instalowanie platformy .NET Core z [skryptu Instalatora](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="ea317-124">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="ea317-125">Wdrażanie aplikacji .NET Core niezależne.</span><span class="sxs-lookup"><span data-stu-id="ea317-125">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="ea317-126">Kompilowanie produktu ze źródła.</span><span class="sxs-lookup"><span data-stu-id="ea317-126">Building the product from source.</span></span>
* <span data-ttu-id="ea317-127">Instalowanie platformy .NET Core za pomocą *.zip* pliku.</span><span class="sxs-lookup"><span data-stu-id="ea317-127">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="ea317-128">Może to obejmować serwery kompilacji/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="ea317-128">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="ea317-129">*Dla Windows 8.1 i starszych wersjach, lub Windows Server 2012 R2 i wcześniejszych wersjach:* upewnij się, że instalacji systemu Windows jest aktualny i uwzględnia [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) którego można zainstalować za pomocą usługi Windows Update.</span><span class="sxs-lookup"><span data-stu-id="ea317-129">*For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:* Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) which can be installed through Windows Update.</span></span> <span data-ttu-id="ea317-130">Jeśli nie zainstalowano tę aktualizację, zostanie wyświetlone wystąpił błąd podczas uruchamiania aplikacji .NET Core, podobnie do następującej: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`.</span><span class="sxs-lookup"><span data-stu-id="ea317-130">If you don't have this update installed, you'll see an error when you launch a .NET Core application like the following: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="ea317-131">Wstępnie wymaganych składników w programie Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="ea317-131">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="ea317-132">Do tworzenia aplikacji platformy .NET Core przy użyciu zestawu SDK .NET Core, można użyć dowolnego edytora.</span><span class="sxs-lookup"><span data-stu-id="ea317-132">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="ea317-133">[Visual Studio 2017](#visual-studio-2017) zapewnia zintegrowane środowisko deweloperskie dla aplikacji .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="ea317-133">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="ea317-134">Więcej informacji na temat zmian w programie Visual Studio 2017 w [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="ea317-134">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ea317-135">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ea317-135">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ea317-136">Aby tworzyć aplikacje 2.x .NET Core w Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="ea317-136">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="ea317-137">[Pobierz i zainstaluj program Visual Studio 2017 wersji 15.3.0 lub nowszej](/visualstudio/install/install-visual-studio) z **aplikacji dla wielu platform .NET Core** obciążenie (w **inne procesami** sekcji) wybrane.</span><span class="sxs-lookup"><span data-stu-id="ea317-137">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z obciążeniem "Programowanie wieloplatformowych .NET Core" wybrane](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="ea317-139">Po **aplikacji dla wielu platform .NET Core** zestawu narzędzi jest zainstalowany, program Visual Studio 2017 używa .NET Core 1.x domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ea317-139">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="ea317-140">Zainstaluj oprogramowanie .NET Core 2.x zestaw SDK, aby uzyskać pomoc techniczną 2.x .NET Core w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="ea317-140">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="ea317-141">Zainstaluj [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="ea317-141">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="ea317-142">Przekieruj istniejące lub nowe projekty 1.x .NET Core do platformy .NET Core 2.x z poniższymi instrukcjami:</span><span class="sxs-lookup"><span data-stu-id="ea317-142">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="ea317-143">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ea317-143">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="ea317-144">W **platformy docelowej** zaznaczenia menu, ustaw wartość na **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="ea317-144">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.0" docelowego framework wybranego elementu](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="ea317-146">Raz .NET Core 2.x zainstalowano zestaw SDK dla programu Visual Studio 2017 używa .NET Core SDK 2.x domyślnie i obsługuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="ea317-146">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

* <span data-ttu-id="ea317-147">Otwórz kompilacji i uruchamianie istniejących projektów 1.x .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea317-147">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="ea317-148">Przekierować projekty 1.x .NET Core 2.x, kompilacji i uruchom .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea317-148">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
* <span data-ttu-id="ea317-149">Utwórz nowe projekty 2.x .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea317-149">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ea317-150">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ea317-150">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ea317-151">Do opracowywania aplikacji 1.x .NET Core w programie Visual Studio, [pobrać i zainstalować program Visual Studio 2017 RTM (wersja 15.0.26228.4) lub wyższej](/visualstudio/install/install-visual-studio) z **"Programowanie wieloplatformowych .NET Core"** obciążenie (w  **Inne procesami** sekcji) wybrane.</span><span class="sxs-lookup"><span data-stu-id="ea317-151">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z obciążeniem "Programowanie wieloplatformowych .NET Core" wybrane](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="ea317-153">Można użyć programu Visual Studio 2015 dla platformy .NET Core 1.x wdrożenia, ale nie jest zalecane z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="ea317-153">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="ea317-154">Narzędzia .NET Core jest w wersji preview, która nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="ea317-154">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="ea317-155">Projekty są oparte na project.json, które jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="ea317-155">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="ea317-156">Aby uzyskać więcej informacji o zmianach format projektu, zobacz [ogólne omówienie zmiany](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="ea317-156">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

> [!TIP]
> <span data-ttu-id="ea317-157">Aby sprawdzić swoją wersję programu Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="ea317-157">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="ea317-158">Na **pomocy** menu, wybierz **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ea317-158">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="ea317-159">W **Microsoft Visual Studio** okna dialogowego, sprawdź numer wersji.</span><span class="sxs-lookup"><span data-stu-id="ea317-159">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="ea317-160">W przypadku aplikacji .NET Core 2.1 Preview 1 programu Visual Studio 2017 wersji 15,6 6 lub nowszy w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="ea317-160">For .NET Core 2.1 Preview 1 apps, Visual Studio 2017 version 15.6 Preview 6 or higher.</span></span>
>   * <span data-ttu-id="ea317-161">W przypadku aplikacji .NET Core 2.0, Visual Studio 2017 wersji 15.3 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ea317-161">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="ea317-162">W przypadku aplikacji .NET Core 1.x Visual Studio 2017 wersji 15,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ea317-162">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
