---
title: "Wymagania wstępne dotyczące platformy .NET Core w systemie Windows"
description: "Dowiedz się, w zależności, należy na okien komputera do opracowywania i uruchamiania aplikacji .NET Core."
author: JRAlexander
ms.author: johalex
ms.date: 02/28/2018
ms.topic: article
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: e64ecb807fd377458a9998ebbdfe2f6f15b115bb
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="7af75-103">Wymagania wstępne dotyczące platformy .NET Core w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="7af75-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="7af75-104">W tym artykule opisano zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="7af75-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="7af75-105">Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core w systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="7af75-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="7af75-106">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="7af75-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="7af75-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7af75-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="7af75-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7af75-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="7af75-109">Oprogramowanie .NET core obsługiwane wersje systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7af75-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="7af75-110">Oprogramowanie .NET core jest obsługiwana w następujących wersjach:</span><span class="sxs-lookup"><span data-stu-id="7af75-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="7af75-111">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="7af75-111">Windows 7 SP1</span></span>
* <span data-ttu-id="7af75-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="7af75-112">Windows 8.1</span></span>
* <span data-ttu-id="7af75-113">Windows 10 Anniversary Update (w wersji 1607) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="7af75-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="7af75-114">Windows Server 2008 R2 z dodatkiem SP1 (całego serwera lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="7af75-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="7af75-115">Windows Server 2012 z dodatkiem SP1 (całego serwera lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="7af75-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="7af75-116">Windows Server 2012 R2 (całego serwera lub Server Core)</span><span class="sxs-lookup"><span data-stu-id="7af75-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="7af75-117">Windows Server 2016 (całego serwera, Server Core lub serwerze Nano)</span><span class="sxs-lookup"><span data-stu-id="7af75-117">Windows Server 2016 (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="7af75-118">Zobacz [.NET Core 2.x - obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pełną listę .NET Core 2.x obsługiwanych systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="7af75-118">See [.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems.</span></span>

<span data-ttu-id="7af75-119">Zobacz [1.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pełną listę .NET Core 1.x obsługiwanych systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="7af75-119">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="7af75-120">Zależności .NET core</span><span class="sxs-lookup"><span data-stu-id="7af75-120">.NET Core dependencies</span></span>

<span data-ttu-id="7af75-121">Podczas pracy z wersjami systemu Windows starszych niż Windows 10 i Windows Server 2016 .NET core 1.1 i wcześniejszych wersjach wymaga pakietu redystrybucyjnego Visual C++</span><span class="sxs-lookup"><span data-stu-id="7af75-121">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="7af75-122">Ta zależność jest automatycznie instalowany przez Instalatora platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7af75-122">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="7af75-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musi zostać zainstalowany ręcznie po:</span><span class="sxs-lookup"><span data-stu-id="7af75-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="7af75-124">Instalowanie platformy .NET Core z [skryptu Instalatora](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="7af75-124">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="7af75-125">Wdrażanie aplikacji .NET Core niezależne.</span><span class="sxs-lookup"><span data-stu-id="7af75-125">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="7af75-126">Kompilowanie produktu ze źródła.</span><span class="sxs-lookup"><span data-stu-id="7af75-126">Building the product from source.</span></span>
* <span data-ttu-id="7af75-127">Instalowanie platformy .NET Core za pomocą *.zip* pliku.</span><span class="sxs-lookup"><span data-stu-id="7af75-127">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="7af75-128">Może to obejmować serwery kompilacji/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="7af75-128">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="7af75-129">*Windows 7 i Windows Server 2008 tylko dla maszyn:* upewnij się, że instalacji systemu Windows jest aktualny i uwzględnia poprawkę [KB2533623](https://support.microsoft.com/help/2533623) zainstalowane za pomocą usługi Windows Update.</span><span class="sxs-lookup"><span data-stu-id="7af75-129">*For Windows 7 and Windows Server 2008 machines only:* Make sure that your Windows installation is up-to-date and includes hotfix [KB2533623](https://support.microsoft.com/help/2533623) installed through Windows Update.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="7af75-130">Wstępnie wymaganych składników w programie Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="7af75-130">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="7af75-131">Do tworzenia aplikacji platformy .NET Core przy użyciu zestawu SDK .NET Core, można użyć dowolnego edytora.</span><span class="sxs-lookup"><span data-stu-id="7af75-131">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="7af75-132">[Visual Studio 2017](#visual-studio-2017) zapewnia zintegrowane środowisko deweloperskie dla aplikacji .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="7af75-132">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="7af75-133">Więcej informacji na temat zmian w programie Visual Studio 2017 w [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="7af75-133">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7af75-134">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7af75-134">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="7af75-135">Aby tworzyć aplikacje 2.x .NET Core w Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="7af75-135">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="7af75-136">[Pobierz i zainstaluj program Visual Studio 2017 wersji 15.3.0 lub nowszej](/visualstudio/install/install-visual-studio) z **aplikacji dla wielu platform .NET Core** obciążenie (w **inne procesami** sekcji) wybrane.</span><span class="sxs-lookup"><span data-stu-id="7af75-136">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z obciążeniem "Programowanie wieloplatformowych .NET Core" wybrane](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="7af75-138">Po **aplikacji dla wielu platform .NET Core** zestawu narzędzi jest zainstalowany, program Visual Studio 2017 używa .NET Core 1.x domyślnie.</span><span class="sxs-lookup"><span data-stu-id="7af75-138">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="7af75-139">Zainstaluj oprogramowanie .NET Core 2.x zestaw SDK, aby uzyskać pomoc techniczną 2.x .NET Core w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="7af75-139">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="7af75-140">Zainstaluj [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="7af75-140">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="7af75-141">Przekieruj istniejące lub nowe projekty 1.x .NET Core do platformy .NET Core 2.x z poniższymi instrukcjami:</span><span class="sxs-lookup"><span data-stu-id="7af75-141">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="7af75-142">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7af75-142">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="7af75-143">W **platformy docelowej** zaznaczenia menu, ustaw wartość na **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="7af75-143">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.0" docelowego framework wybranego elementu](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="7af75-145">Raz .NET Core 2.x zainstalowano zestaw SDK dla programu Visual Studio 2017 używa .NET Core SDK 2.x domyślnie i obsługuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="7af75-145">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

* <span data-ttu-id="7af75-146">Otwórz kompilacji i uruchamianie istniejących projektów 1.x .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7af75-146">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="7af75-147">Przekierować projekty 1.x .NET Core 2.x, kompilacji i uruchom .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7af75-147">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
* <span data-ttu-id="7af75-148">Utwórz nowe projekty 2.x .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7af75-148">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7af75-149">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7af75-149">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="7af75-150">Do opracowywania aplikacji 1.x .NET Core w programie Visual Studio, [pobrać i zainstalować program Visual Studio 2017 RTM (wersja 15.0.26228.4) lub wyższej](/visualstudio/install/install-visual-studio) z **"Programowanie wieloplatformowych .NET Core"** obciążenie (w  **Inne procesami** sekcji) wybrane.</span><span class="sxs-lookup"><span data-stu-id="7af75-150">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu programu Visual Studio 2017 instalacji z obciążeniem "Programowanie wieloplatformowych .NET Core" wybrane](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="7af75-152">Można użyć programu Visual Studio 2015 dla platformy .NET Core 1.x wdrożenia, ale nie jest zalecane z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="7af75-152">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="7af75-153">Narzędzia .NET Core jest w wersji preview, która nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="7af75-153">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="7af75-154">Projekty są oparte na project.json, które jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="7af75-154">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="7af75-155">Aby uzyskać więcej informacji o zmianach format projektu, zobacz [ogólne omówienie zmiany](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="7af75-155">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

> [!TIP]
> <span data-ttu-id="7af75-156">Aby sprawdzić swoją wersję programu Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="7af75-156">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="7af75-157">Na **pomocy** menu, wybierz **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7af75-157">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="7af75-158">W **Microsoft Visual Studio** okna dialogowego, sprawdź numer wersji.</span><span class="sxs-lookup"><span data-stu-id="7af75-158">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="7af75-159">W przypadku aplikacji 2.x .NET Core, programu Visual Studio 2017 wersji 15 ustęp 3 (26730.01) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="7af75-159">For .NET Core 2.x apps, Visual Studio 2017 version 15.3 (26730.01) or higher.</span></span>
>   * <span data-ttu-id="7af75-160">W przypadku aplikacji 1.x .NET Core, programu Visual Studio 2017 wersji 15.0 (26228.04) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="7af75-160">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 (26228.04) or higher.</span></span>
