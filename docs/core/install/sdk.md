---
title: Instalowanie zestaw .NET Core SDK w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do tworzenia aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 6e9af6c84c81b1244e10fa7d5955ab67d34b1f0a
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552205"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="0ca53-104">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="0ca53-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="0ca53-105">W tym artykule dowiesz się, jak zainstalować zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0ca53-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="0ca53-106">Zestaw .NET Core SDK jest używany do tworzenia aplikacji i bibliotek platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ca53-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="0ca53-107">Środowisko uruchomieniowe platformy .NET Core jest zawsze instalowane z zestawem SDK.</span><span class="sxs-lookup"><span data-stu-id="0ca53-107">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="0ca53-108">Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="0ca53-108">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="0ca53-109">Pliki do pobrania dla programu .NET Core 3,1 Preview 3</span><span class="sxs-lookup"><span data-stu-id="0ca53-109">.NET Core 3.1 Preview 3 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="0ca53-110">Pliki do pobrania w programie .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="0ca53-110">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="0ca53-111">Pliki do pobrania w programie .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="0ca53-111">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="0ca53-112">Pliki do pobrania w programie .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0ca53-112">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

<span data-ttu-id="0ca53-113">Program .NET Core można również zainstalować w ramach zintegrowanego środowiska programistycznego (IDE), szczegółowo w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="0ca53-113">You can also install .NET Core as part of an integrated development environment (IDE), detailed in the sections below.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="0ca53-114">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="0ca53-114">Install with an installer</span></span>

<span data-ttu-id="0ca53-115">Zarówno system Windows, jak i macOS mają autonomiczne Instalatory, których można użyć do zainstalowania zestawu SDK platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0ca53-115">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="0ca53-116">[Procesory CPU Windows x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPU](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span><span class="sxs-lookup"><span data-stu-id="0ca53-116">Windows [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span></span>
- <span data-ttu-id="0ca53-117">[procesory macOS x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="0ca53-117">macOS [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="0ca53-118">Instalowanie przy użyciu Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="0ca53-118">Install with a package manager</span></span>

<span data-ttu-id="0ca53-119">Zestaw .NET Core SDK można zainstalować przy użyciu wielu popularnych menedżerów pakietów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="0ca53-119">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="0ca53-120">Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — Instalowanie programu .NET Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-120">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="0ca53-121">Instalowanie za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ca53-121">Install with Visual Studio</span></span>

<span data-ttu-id="0ca53-122">Jeśli używasz programu Visual Studio do tworzenia aplikacji platformy .NET Core, w poniższej tabeli opisano minimalną wymaganą wersję programu Visual Studio opartą na docelowej wersji zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0ca53-122">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="0ca53-123">Wersja zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="0ca53-123">.NET Core SDK version</span></span> | <span data-ttu-id="0ca53-124">Wersja programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ca53-124">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="0ca53-125">3.0</span><span class="sxs-lookup"><span data-stu-id="0ca53-125">3.0</span></span>                   | <span data-ttu-id="0ca53-126">Program Visual Studio 2019 w wersji 16,3 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="0ca53-126">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="0ca53-127">2,2</span><span class="sxs-lookup"><span data-stu-id="0ca53-127">2.2</span></span>                   | <span data-ttu-id="0ca53-128">Program Visual Studio 2017 w wersji 15,9 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="0ca53-128">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="0ca53-129">2,1</span><span class="sxs-lookup"><span data-stu-id="0ca53-129">2.1</span></span>                   | <span data-ttu-id="0ca53-130">Program Visual Studio 2017 w wersji 15,7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="0ca53-130">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="0ca53-131">Jeśli masz już zainstalowany program Visual Studio, możesz sprawdzić swoją wersję, wykonując poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="0ca53-131">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="0ca53-132">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ca53-132">Open Visual Studio.</span></span>
01. <span data-ttu-id="0ca53-133">Wybierz **pomoc** > **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0ca53-133">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="0ca53-134">Odczytaj numer wersji z okna dialogowego **informacje** .</span><span class="sxs-lookup"><span data-stu-id="0ca53-134">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="0ca53-135">Program Visual Studio może zainstalować najnowsze zestaw .NET Core SDK i środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="0ca53-135">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="0ca53-136">[Pobierz program Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="0ca53-136">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="0ca53-137">Wybierz obciążenie</span><span class="sxs-lookup"><span data-stu-id="0ca53-137">Select a workload</span></span>

<span data-ttu-id="0ca53-138">Podczas instalowania lub modyfikowania programu Visual Studio wybierz jedno z następujących obciążeń, w zależności od rodzaju kompilowanej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="0ca53-138">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="0ca53-139">Obciążenie **Międzyplatformowe dla platformy .NET Core** w sekcji **inne zestawy narzędzi** .</span><span class="sxs-lookup"><span data-stu-id="0ca53-139">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="0ca53-140">**ASP.NET i programowanie w sieci Web** w sekcji **chmury & sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="0ca53-140">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="0ca53-141">Obciążenie **Programowanie na platformie Azure** w sekcji **chmury & sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="0ca53-141">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="0ca53-142">Obciążenie **Programowanie aplikacji klasycznych na platformie .NET** znajduje się w sekcji **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="0ca53-142">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="0ca53-143">[![Windows Visual Studio 2019 z obciążeniem platformy .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="0ca53-143">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="0ca53-144">Zainstaluj przy użyciu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="0ca53-144">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="0ca53-145">Visual Studio dla komputerów Mac instaluje zestaw .NET Core SDK w przypadku wybrania obciążenia **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="0ca53-145">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="0ca53-146">Aby rozpocząć pracę z programowaniem programu .NET Core w systemie macOS, zobacz [Instalowanie programu Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="0ca53-146">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="0ca53-147">[![macOS programu Visual Studio 2019 for Mac z funkcją obciążenia .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="0ca53-147">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-from-visual-studio-code"></a><span data-ttu-id="0ca53-148">Zainstaluj z Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0ca53-148">Install from Visual Studio Code</span></span>

<span data-ttu-id="0ca53-149">Visual Studio Code to zaawansowany i lekki Edytor kodu źródłowego, który jest uruchamiany na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="0ca53-149">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="0ca53-150">Visual Studio Code jest dostępny dla systemów Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="0ca53-150">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="0ca53-151">Mimo że Visual Studio Code nie jest obsługiwana przez platformę .NET Core, Dodawanie obsługi .NET Core jest proste.</span><span class="sxs-lookup"><span data-stu-id="0ca53-151">While Visual Studio Code doesn't come with .NET Core support, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="0ca53-152">[Pobierz i zainstaluj Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="0ca53-152">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="0ca53-153">[Pobierz i zainstaluj zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="0ca53-153">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>
01. <span data-ttu-id="0ca53-154">[Zainstaluj C# rozszerzenie z witryny Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="0ca53-154">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="0ca53-155">Instalowanie przy użyciu programu PowerShell Automation</span><span class="sxs-lookup"><span data-stu-id="0ca53-155">Install with PowerShell automation</span></span>

<span data-ttu-id="0ca53-156">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="0ca53-156">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="0ca53-157">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-157">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="0ca53-158">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="0ca53-158">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="0ca53-159">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="0ca53-159">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="0ca53-160">Instalowanie przy użyciu usługi Bash Automation</span><span class="sxs-lookup"><span data-stu-id="0ca53-160">Install with bash automation</span></span>

<span data-ttu-id="0ca53-161">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="0ca53-161">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="0ca53-162">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-162">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="0ca53-163">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="0ca53-163">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="0ca53-164">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="0ca53-164">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a><span data-ttu-id="0ca53-165">Docker</span><span class="sxs-lookup"><span data-stu-id="0ca53-165">Docker</span></span>

<span data-ttu-id="0ca53-166">Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="0ca53-166">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="0ca53-167">Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ca53-167">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="0ca53-168">Środowisko .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="0ca53-168">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="0ca53-169">Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="0ca53-169">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="0ca53-170">Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="0ca53-170">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="0ca53-171">Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="0ca53-171">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="0ca53-172">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="0ca53-172">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="0ca53-173">Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-173">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0ca53-174">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0ca53-174">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="0ca53-175">[Samouczek: C# samouczek Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-175">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="0ca53-176">[Samouczek: Visual Basic Hello World samouczka](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-176">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="0ca53-177">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="0ca53-177">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="0ca53-178">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-178">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="0ca53-179">[Samouczek: Rozpoczynanie pracy w witrynie macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-179">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="0ca53-180">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="0ca53-180">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="0ca53-181">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-181">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
