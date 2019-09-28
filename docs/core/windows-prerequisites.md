---
title: Wymagania wstępne dotyczące platformy .NET Core w systemie Windows
description: Dowiedz się, jakie zależności są potrzebne na komputerze z systemem Windows, aby opracowywać i uruchamiać aplikacje platformy .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: b1557e6910cb6d0b6d7e2b3ce2aec97d3715fec7
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591672"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="232c5-103">Wymagania wstępne dotyczące platformy .NET Core w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="232c5-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="232c5-104">W tym artykule przedstawiono obsługiwane wersje systemu operacyjnego w celu uruchamiania aplikacji platformy .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="232c5-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="232c5-105">Obsługiwane wersje systemu operacyjnego i zależności stosują się do trzech sposobów tworzenia aplikacji platformy .NET Core w systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="232c5-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="232c5-106">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="232c5-106">Command line</span></span>](./tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="232c5-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="232c5-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [<span data-ttu-id="232c5-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="232c5-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="232c5-109">Ponadto, Jeśli opracowujesz system Windows przy użyciu programu Visual Studio, [wymagania wstępne dotyczące tworzenia aplikacji .NET Core za pomocą programu Visual Studio zawierają](#prerequisites-to-develop-net-core-apps-with-visual-studio) więcej szczegółów na temat minimalnych wersji obsługiwanych w przypadku programowania na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="232c5-109">Also, if you're developing on Windows using Visual Studio, the [Prerequisites to develop .NET Core apps with Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="232c5-110">Obsługiwane systemy operacyjne .NET Core</span><span class="sxs-lookup"><span data-stu-id="232c5-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="232c5-111">Następujące artykuły zawierają pełną listę obsługiwanych systemów operacyjnych .NET Core na wersję:</span><span class="sxs-lookup"><span data-stu-id="232c5-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="232c5-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="232c5-112">.NET Core 3.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="232c5-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="232c5-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="232c5-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="232c5-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

<span data-ttu-id="232c5-115">Aby uzyskać linki do pobrania i więcej informacji, zobacz artykuł [pobieranie z platformy .NET](https://dotnet.microsoft.com/download) , aby pobrać najnowszą wersję lub [archiwum pobierania programu .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) dla starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="232c5-115">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="232c5-116">Zależności .NET Core</span><span class="sxs-lookup"><span data-stu-id="232c5-116">.NET Core dependencies</span></span>

<span data-ttu-id="232c5-117">[Pakiet redystrybucyjny Microsoft Visual C++ 2015 z aktualizacją Update 3](https://www.microsoft.com/download/details.aspx?id=52685) należy zainstalować ręcznie, gdy:</span><span class="sxs-lookup"><span data-stu-id="232c5-117">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="232c5-118">Instalowanie programu .NET Core za pomocą [skryptu Instalatora](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="232c5-118">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="232c5-119">Wdrażanie samodzielnej aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="232c5-119">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="232c5-120">Kompilowanie produktu ze źródła.</span><span class="sxs-lookup"><span data-stu-id="232c5-120">Building the product from source.</span></span>
* <span data-ttu-id="232c5-121">Instalowanie platformy .NET Core za pośrednictwem pliku *. zip* .</span><span class="sxs-lookup"><span data-stu-id="232c5-121">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="232c5-122">Może to obejmować serwery kompilacji/ciągłej integracji/ciągłego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="232c5-122">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="232c5-123">**W przypadku Windows 8.1 i starszych wersji lub systemu Windows Server 2012 R2 i starszych wersji:**</span><span class="sxs-lookup"><span data-stu-id="232c5-123">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="232c5-124">Upewnij się, że instalacja systemu Windows jest aktualna i zawiera [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), które można zainstalować za Windows Update.</span><span class="sxs-lookup"><span data-stu-id="232c5-124">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="232c5-125">Jeśli ta aktualizacja nie została zainstalowana, podczas uruchamiania aplikacji .NET Core zobaczysz błąd podobny do poniższego:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="232c5-125">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="232c5-126">**Dla systemu Windows 7 lub Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="232c5-126">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="232c5-127">Oprócz KB2999226 upewnij się, że zainstalowano również [poprawki KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) .</span><span class="sxs-lookup"><span data-stu-id="232c5-127">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="232c5-128">Jeśli ta aktualizacja nie została zainstalowana, podczas uruchamiania aplikacji platformy .NET Core zobaczysz błąd podobny do poniższego: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="232c5-128">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a><span data-ttu-id="232c5-129">Wymagania wstępne dotyczące opracowywania aplikacji platformy .NET Core za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="232c5-129">Prerequisites to develop .NET Core apps with Visual Studio</span></span>
    
<span data-ttu-id="232c5-130">Mimo że można użyć dowolnego edytora do tworzenia aplikacji platformy .NET Core przy użyciu zestaw .NET Core SDK, program Visual Studio 2017 i jego nowsze wersje zapewniają zintegrowane środowisko programistyczne dla aplikacji platformy .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="232c5-130">Even though you can use any editor to develop .NET Core applications using the .NET Core SDK, Visual Studio 2017 and later versions provide an integrated development environment for .NET Core apps on Windows.</span></span>

<a name="vs-mapping"></a>

<span data-ttu-id="232c5-131">Każda wersja programu .NET Core ma wymaganą minimalną wersję programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="232c5-131">Each .NET Core version has a minimum version of Visual Studio required.</span></span> <span data-ttu-id="232c5-132">Aby sprawdzić wersję programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="232c5-132">To verify your Visual Studio version:</span></span>

* <span data-ttu-id="232c5-133">W menu **Pomoc** wybierz pozycję **informacje Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="232c5-133">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
* <span data-ttu-id="232c5-134">W oknie dialogowym **Informacje o Microsoft Visual Studio** Sprawdź numer wersji.</span><span class="sxs-lookup"><span data-stu-id="232c5-134">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>

<span data-ttu-id="232c5-135">W poniższej tabeli wymieniono minimalną wersję każdego zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="232c5-135">The following table lists the minimum version for each SDK:</span></span>

| <span data-ttu-id="232c5-136">Wersja zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="232c5-136">.NET Core SDK version</span></span> | <span data-ttu-id="232c5-137">Visual Studio w wersji</span><span class="sxs-lookup"><span data-stu-id="232c5-137">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="232c5-138">3.0</span><span class="sxs-lookup"><span data-stu-id="232c5-138">3.0</span></span>                   | <span data-ttu-id="232c5-139">Program Visual Studio 2019 w wersji 16,3 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="232c5-139">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="232c5-140">2.2</span><span class="sxs-lookup"><span data-stu-id="232c5-140">2.2</span></span>                   | <span data-ttu-id="232c5-141">Program Visual Studio 2017 w wersji 15,9 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="232c5-141">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="232c5-142">2.1</span><span class="sxs-lookup"><span data-stu-id="232c5-142">2.1</span></span>                   | <span data-ttu-id="232c5-143">Program Visual Studio 2017 w wersji 15,7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="232c5-143">Visual Studio 2017 version 15.7 or higher.</span></span> |
| <span data-ttu-id="232c5-144">1.x</span><span class="sxs-lookup"><span data-stu-id="232c5-144">1.x</span></span>                   | <span data-ttu-id="232c5-145">Program Visual Studio 2017 w wersji 15,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="232c5-145">Visual Studio 2017 version 15.0 or higher.</span></span> |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="232c5-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="232c5-146">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="232c5-147">Aby tworzyć aplikacje platformy .NET Core w programie Visual Studio 2019 przy użyciu zestawu SDK programu .NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="232c5-147">To develop .NET Core apps in Visual Studio 2019 using the .NET Core 3.0 SDK:</span></span>

* <span data-ttu-id="232c5-148">[Pobierz i zainstaluj program Visual Studio 2019 w wersji 16,3 lub nowszej](/visualstudio/install/install-visual-studio) i wybierz jedno z następujących obciążeń, które zawierają zestaw .NET Core SDK, w zależności od rodzaju kompilowanej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="232c5-148">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) and select one of the following workloads that includes the .NET Core SDK, depending on the kind of application you're building:</span></span>

  * <span data-ttu-id="232c5-149">Obciążenie **Międzyplatformowe dla platformy .NET Core** w sekcji **inne zestawy narzędzi** .</span><span class="sxs-lookup"><span data-stu-id="232c5-149">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
  * <span data-ttu-id="232c5-150">**ASP.NET i programowanie w sieci Web** w sekcji **chmury & sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="232c5-150">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
  * <span data-ttu-id="232c5-151">Obciążenie **programowaniem pulpitu sieciowego** w sekcji **systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="232c5-151">The **NET desktop development** workload in the **Windows** section.</span></span>

<span data-ttu-id="232c5-152">Na poniższej ilustracji przedstawiono obciążenie **Międzyplatformowe platformy .NET Core** wybrane w interfejsie użytkownika programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="232c5-152">The following image shows the **.NET Core cross-platform development** workload selected in the Visual Studio UI:</span></span>

![Zrzut ekranu instalacji programu Visual Studio 2019 z wybranym obciążeniem "Programowanie dla wielu platform" platformy .NET Core](./media/windows-prerequisites/vs-2019-workloads.jpg)

<span data-ttu-id="232c5-154">Program Visual Studio 2019 16,3 domyślnie używa programu .NET Core 3,0 SDK po zainstalowaniu dowolnego z tych obciążeń.</span><span class="sxs-lookup"><span data-stu-id="232c5-154">Visual Studio 2019 16.3 uses .NET Core 3.0 SDK by default after any of these workloads are installed.</span></span>

<span data-ttu-id="232c5-155">Jeśli chcesz, aby istniejące projekty korzystały z najnowszego środowiska uruchomieniowego platformy .NET Core, Przekieruj każdy istniejący projekt .NET Core do programu .NET Core 3,0, korzystając z następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="232c5-155">If you want your existing projects to use the latest .NET Core runtime, retarget each existing .NET Core project to .NET Core 3.0 using the following instructions:</span></span>

* <span data-ttu-id="232c5-156">W menu **projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="232c5-156">On the **Project** menu, choose **Properties**.</span></span>
* <span data-ttu-id="232c5-157">W menu wyboru **platformy docelowej** ustaw wartość na **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="232c5-157">In the **Target framework** selection menu, set the value to **.NET Core 3.0**.</span></span>

![Zrzut ekranu przedstawiający właściwość projektu aplikacji programu Visual Studio 2019 z wybranym elementem menu platformy docelowej ".NET Core 3,0"](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

<span data-ttu-id="232c5-159">Po skonfigurowaniu programu Visual Studio przy użyciu zestawu SDK platformy .NET Core 3,0 można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="232c5-159">Once you have Visual Studio configured with .NET Core 3.0 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="232c5-160">Otwórz, skompiluj i uruchom istniejące projekty platformy .NET Core 1. x i 2. x.</span><span class="sxs-lookup"><span data-stu-id="232c5-160">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="232c5-161">Przekieruj projekty platformy .NET Core 1. x i 2. x do platformy .NET Core 3,0, kompilacji i uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="232c5-161">Retarget .NET Core 1.x and 2.x projects to .NET Core 3.0, build, and run.</span></span>
* <span data-ttu-id="232c5-162">Utwórz nowe projekty platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="232c5-162">Create new .NET Core 3.0 projects.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="232c5-163">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="232c5-163">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="232c5-164">Aby tworzyć aplikacje platformy .NET Core w programie Visual Studio 2017 przy użyciu zestawu SDK programu .NET Core 2,2:</span><span class="sxs-lookup"><span data-stu-id="232c5-164">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

* <span data-ttu-id="232c5-165">[Pobierz i zainstaluj program Visual Studio 2019 w wersji 16,3 lub nowszej](/visualstudio/install/install-visual-studio) przy użyciu obciążenia **międzyplatformowego platformy .NET Core** (w sekcji **inne zestawy narzędzi** ).</span><span class="sxs-lookup"><span data-stu-id="232c5-165">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>
* <span data-ttu-id="232c5-166">[Pobierz i zainstaluj program Visual Studio 2017 w wersji 15.9.0 lub nowszej](/visualstudio/install/install-visual-studio) z wybranym obciążeniem międzyplatformowym **platformy .NET Core** (w sekcji **inne zestawy narzędzi** ).</span><span class="sxs-lookup"><span data-stu-id="232c5-166">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Zrzut ekranu instalacji programu Visual Studio 2017 z wybranym obciążeniem "Programowanie dla wielu platform" platformy .NET Core](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="232c5-168">Po zainstalowaniu zestawu narzędzi do **tworzenia aplikacji dla wielu platform platformy .NET Core** program Visual Studio zwykle instaluje poprzednią wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="232c5-168">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="232c5-169">Na przykład program Visual Studio 2017 15,9 domyślnie używa programu .NET Core 2,1 SDK po zainstalowaniu obciążenia.</span><span class="sxs-lookup"><span data-stu-id="232c5-169">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="232c5-170">Aby zaktualizować program Visual Studio do korzystania z zestawu SDK programu .NET Core 2,2:</span><span class="sxs-lookup"><span data-stu-id="232c5-170">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="232c5-171">Zainstaluj [zestaw SDK platformy .NET Core 2,2](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="232c5-171">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="232c5-172">Jeśli chcesz, aby projekt używał najnowszej wersji środowiska uruchomieniowego platformy .NET Core, Przekieruj każdy istniejący lub nowy projekt .NET Core do programu .NET Core 2,2, korzystając z następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="232c5-172">If you want your project to use the latest .NET Core runtime, retarget each existing or new .NET Core project to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="232c5-173">W menu **projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="232c5-173">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="232c5-174">W menu wyboru **platformy docelowej** ustaw wartość na **.NET Core 2,2**.</span><span class="sxs-lookup"><span data-stu-id="232c5-174">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Zrzut ekranu przedstawiający właściwość projektu aplikacji programu Visual Studio 2017 z wybranym elementem menu platformy docelowej ".NET Core 2,2"](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="232c5-176">Po skonfigurowaniu programu Visual Studio przy użyciu zestawu SDK platformy .NET Core 2,2 można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="232c5-176">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="232c5-177">Otwórz, skompiluj i uruchom istniejące projekty platformy .NET Core 1. x i 2. x.</span><span class="sxs-lookup"><span data-stu-id="232c5-177">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="232c5-178">Przekieruj projekty platformy .NET Core 1. x i 2. x do platformy .NET Core 2,2, kompilacji i uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="232c5-178">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="232c5-179">Utwórz nowe projekty platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="232c5-179">Create new .NET Core 2.2 projects.</span></span>

---
