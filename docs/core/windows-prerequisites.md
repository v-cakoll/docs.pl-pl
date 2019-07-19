---
title: Wymagania wstępne dotyczące platformy .NET Core w systemie Windows
description: Dowiedz się, jakie zależności są potrzebne na komputerze z systemem Windows, aby opracowywać i uruchamiać aplikacje platformy .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 1921ef565c2d04624009f7684e439ddba1cdf57e
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331075"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="f3e0a-103">Wymagania wstępne dotyczące platformy .NET Core w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="f3e0a-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="f3e0a-104">W tym artykule przedstawiono obsługiwane wersje systemu operacyjnego w celu uruchamiania aplikacji platformy .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="f3e0a-105">Obsługiwane wersje systemu operacyjnego i zależności stosują się do trzech sposobów tworzenia aplikacji platformy .NET Core w systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="f3e0a-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="f3e0a-106">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="f3e0a-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="f3e0a-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3e0a-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [<span data-ttu-id="f3e0a-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f3e0a-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="f3e0a-109">Ponadto, Jeśli opracowujesz system Windows przy użyciu programu Visual Studio 2017, [wymagania wstępne dotyczące programu Visual studio 2017 zawierają](#prerequisites-with-visual-studio-2017) więcej szczegółów na temat minimalnej wersji, które są obsługiwane w przypadku programowania na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-109">Also, if you're developing on Windows using Visual Studio 2017, the [Prerequisites with Visual Studio 2017](#prerequisites-with-visual-studio-2017) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="f3e0a-110">Obsługiwane systemy operacyjne .NET Core</span><span class="sxs-lookup"><span data-stu-id="f3e0a-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="f3e0a-111">Następujące artykuły zawierają pełną listę obsługiwanych systemów operacyjnych .NET Core na wersję:</span><span class="sxs-lookup"><span data-stu-id="f3e0a-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="f3e0a-112">.NET Core 3,0 (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="f3e0a-112">.NET Core 3.0 (Preview)</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="f3e0a-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="f3e0a-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="f3e0a-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f3e0a-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="f3e0a-115">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f3e0a-115">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="f3e0a-116">Aby uzyskać linki do pobrania i więcej informacji, zobacz artykuł [pobieranie z platformy .NET](https://dotnet.microsoft.com/download) , aby pobrać najnowszą wersję lub [archiwum pobierania programu .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) dla starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-116">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="f3e0a-117">Zależności .NET Core</span><span class="sxs-lookup"><span data-stu-id="f3e0a-117">.NET Core dependencies</span></span>

<span data-ttu-id="f3e0a-118">Program .NET Core 1,1 i jego wcześniejsze wersje wymagają C++ , aby pakiet redystrybucyjny wizualizacji był uruchamiany w wersjach systemu Windows starszych niż Windows 10 i windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-118">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="f3e0a-119">Ta zależność jest automatycznie instalowana przez Instalatora .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-119">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="f3e0a-120">[Pakiet redystrybucyjny Microsoft Visual C++ 2015 z aktualizacją Update 3](https://www.microsoft.com/download/details.aspx?id=52685) należy zainstalować ręcznie, gdy:</span><span class="sxs-lookup"><span data-stu-id="f3e0a-120">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="f3e0a-121">Instalowanie programu .NET Core za pomocą [skryptu Instalatora](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f3e0a-121">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="f3e0a-122">Wdrażanie samodzielnej aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-122">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="f3e0a-123">Kompilowanie produktu ze źródła.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-123">Building the product from source.</span></span>
* <span data-ttu-id="f3e0a-124">Instalowanie platformy .NET Core za pośrednictwem pliku *. zip* .</span><span class="sxs-lookup"><span data-stu-id="f3e0a-124">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="f3e0a-125">Może to obejmować serwery kompilacji/ciągłej integracji/ciągłego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-125">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="f3e0a-126">**W przypadku Windows 8.1 i starszych wersji lub systemu Windows Server 2012 R2 i starszych wersji:**</span><span class="sxs-lookup"><span data-stu-id="f3e0a-126">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="f3e0a-127">Upewnij się, że instalacja systemu Windows jest aktualna i zawiera [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), które można zainstalować za Windows Update.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-127">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="f3e0a-128">Jeśli ta aktualizacja nie została zainstalowana, podczas uruchamiania aplikacji .NET Core zobaczysz błąd podobny do poniższego:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="f3e0a-128">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="f3e0a-129">**Dla systemu Windows 7 lub Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="f3e0a-129">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="f3e0a-130">Oprócz KB2999226 upewnij się, że zainstalowano również [poprawki KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) .</span><span class="sxs-lookup"><span data-stu-id="f3e0a-130">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="f3e0a-131">Jeśli ta aktualizacja nie została zainstalowana, podczas uruchamiania aplikacji platformy .NET Core zobaczysz błąd podobny do poniższego: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-131">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-for-net-core-30-preview-3"></a><span data-ttu-id="f3e0a-132">Wymagania wstępne dotyczące programu .NET Core 3,0 (wersja zapoznawcza 3)</span><span class="sxs-lookup"><span data-stu-id="f3e0a-132">Prerequisites for .NET Core 3.0 Preview 3</span></span>

<span data-ttu-id="f3e0a-133">Program .NET Core 3,0 w wersji zapoznawczej 3 ma takie same wymagania wstępne jak w przypadku innych wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-133">.NET Core 3.0 Preview 3 has the same prerequisites as other versions of .NET Core.</span></span> <span data-ttu-id="f3e0a-134">Jeśli jednak chcesz użyć programu Visual Studio do tworzenia projektów platformy .NET Core 3,0, musisz użyć programu [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="f3e0a-134">However, if you want to use Visual Studio to create .NET Core 3.0 projects, you must use the [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="f3e0a-135">Program Visual Studio 2019 można zainstalować równolegle z innymi wersjami programu Visual Studio bez konfliktu.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-135">Visual Studio 2019 can be installed side-by-side with other versions of Visual Studio without conflict.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="f3e0a-136">Wymagania wstępne dotyczące programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f3e0a-136">Prerequisites with Visual Studio 2017</span></span>
    
<span data-ttu-id="f3e0a-137">Za pomocą dowolnego edytora można opracowywać aplikacje platformy .NET Core przy użyciu zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-137">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="f3e0a-138">Program Visual Studio 2017 zapewnia zintegrowane środowisko programistyczne dla aplikacji platformy .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-138">Visual Studio 2017 provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="f3e0a-139">Więcej informacji o zmianach w programie Visual Studio 2017 można znaleźć w [informacjach o wersji](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="f3e0a-139">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f3e0a-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f3e0a-140">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="f3e0a-141">Aby tworzyć aplikacje platformy .NET Core w programie Visual Studio 2017 przy użyciu zestawu SDK programu .NET Core 2,2:</span><span class="sxs-lookup"><span data-stu-id="f3e0a-141">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="f3e0a-142">[Pobierz i zainstaluj program Visual Studio 2017 w wersji 15.9.0 lub nowszej](/visualstudio/install/install-visual-studio) z wybranym obciążeniem międzyplatformowym **platformy .NET Core** (w sekcji **inne zestawy narzędzi** ).</span><span class="sxs-lookup"><span data-stu-id="f3e0a-142">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu instalacji programu Visual Studio 2017 z wybranym obciążeniem "Programowanie dla wielu platform" platformy .NET Core](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="f3e0a-144">Po zainstalowaniu zestawu narzędzi do **tworzenia aplikacji dla wielu platform platformy .NET Core** program Visual Studio zwykle instaluje poprzednią wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-144">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="f3e0a-145">Na przykład program Visual Studio 2017 15,9 domyślnie używa programu .NET Core 2,1 SDK po zainstalowaniu obciążenia.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-145">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="f3e0a-146">Aby zaktualizować program Visual Studio do korzystania z zestawu SDK programu .NET Core 2,2:</span><span class="sxs-lookup"><span data-stu-id="f3e0a-146">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="f3e0a-147">Zainstaluj [zestaw SDK platformy .NET Core 2,2](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="f3e0a-147">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="f3e0a-148">Jeśli chcesz, aby projekt używał najnowszej wersji środowiska uruchomieniowego platformy .NET Core, Przekieruj istniejące lub nowe projekty platformy .NET Core do programu .NET Core 2,2, korzystając z następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="f3e0a-148">If you want your project to use the latest .NET Core runtime, retarget existing or new .NET Core projects to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="f3e0a-149">W menu **projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-149">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="f3e0a-150">W menu wyboru **platformy docelowej** ustaw wartość na **.NET Core 2,2**.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-150">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Zrzut ekranu przedstawiający właściwość projektu aplikacji programu Visual Studio 2017 z wybranym elementem menu platformy docelowej ".NET Core 2,2"](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="f3e0a-152">Po skonfigurowaniu programu Visual Studio przy użyciu zestawu SDK platformy .NET Core 2,2 można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f3e0a-152">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="f3e0a-153">Otwórz, skompiluj i uruchom istniejące projekty platformy .NET Core 1. x i 2. x.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-153">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="f3e0a-154">Przekieruj projekty platformy .NET Core 1. x i 2. x do platformy .NET Core 2,2, kompilacji i uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-154">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="f3e0a-155">Utwórz nowe projekty platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-155">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f3e0a-156">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f3e0a-156">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f3e0a-157">Aby opracowywać aplikacje platformy .NET Core 1. x w programie Visual Studio, [Pobierz i zainstaluj program Visual Studio 2017](/visualstudio/install/install-visual-studio) z użyciem obciążenia międzyplatformowego dla **platformy .NET Core** (w sekcji **inne zestawy narzędzi** ).</span><span class="sxs-lookup"><span data-stu-id="f3e0a-157">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu instalacji programu Visual Studio 2017 z wybranym obciążeniem "Programowanie dla wielu platform" platformy .NET Core](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="f3e0a-159">Możliwe jest korzystanie z programu Visual Studio 2015 do programowania w środowisku .NET Core 1. x, ale nie jest to zalecane z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="f3e0a-159">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="f3e0a-160">Narzędzia .NET Core są w wersji zapoznawczej, która nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-160">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="f3e0a-161">Projekty to oparte na pliku Project. JSON, które jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-161">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="f3e0a-162">Aby uzyskać więcej informacji na temat zmian w formacie projektu, zobacz [Ogólne omówienie zmian](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="f3e0a-162">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="f3e0a-163">Aby sprawdzić wersję programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="f3e0a-163">To verify your Visual Studio version:</span></span>
>
> * <span data-ttu-id="f3e0a-164">W menu **Pomoc** wybierz pozycję **informacje Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-164">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="f3e0a-165">W oknie dialogowym **Informacje o Microsoft Visual Studio** Sprawdź numer wersji.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-165">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="f3e0a-166">W przypadku aplikacji .NET Core 3,0 Preview 3, Visual Studio 2019 w wersji 16,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-166">For .NET Core 3.0 Preview 3 apps, Visual Studio 2019 version 16.0 or higher.</span></span>
>   * <span data-ttu-id="f3e0a-167">W przypadku aplikacji platformy .NET Core 2,2 program Visual Studio 2017 w wersji 15,9 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-167">For .NET Core 2.2 apps, Visual Studio 2017 version 15.9 or higher.</span></span>
>   * <span data-ttu-id="f3e0a-168">W przypadku aplikacji platformy .NET Core 2,1 program Visual Studio 2017 w wersji 15,7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-168">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="f3e0a-169">W przypadku aplikacji platformy .NET Core 1. x program Visual Studio 2017 w wersji 15,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-169">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
