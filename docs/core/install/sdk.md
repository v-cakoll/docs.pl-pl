---
title: Instalowanie zestaw .NET Core SDK w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do tworzenia aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 54819b409422e8bda9efe25478aa3424683a380b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567470"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="d993d-104">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="d993d-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="d993d-105">W tym artykule dowiesz się, jak zainstalować zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d993d-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="d993d-106">Zestaw .NET Core SDK jest używany do tworzenia aplikacji i bibliotek platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d993d-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="d993d-107">Środowisko uruchomieniowe platformy .NET Core jest zawsze instalowane z zestawem SDK.</span><span class="sxs-lookup"><span data-stu-id="d993d-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="d993d-108">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="d993d-108">Install with an installer</span></span>

<span data-ttu-id="d993d-109">Zarówno system Windows, jak i macOS mają autonomiczne Instalatory, których można użyć do zainstalowania zestawu SDK platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d993d-109">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="d993d-110">Procesory Windows [x64 (64-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [procesora x86 (32-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="d993d-110">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="d993d-111">[procesory macOS x64 (64-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="d993d-111">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="d993d-112">Instalowanie przy użyciu Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="d993d-112">Install with a package manager</span></span>

<span data-ttu-id="d993d-113">Zestaw .NET Core SDK można zainstalować przy użyciu wielu popularnych menedżerów pakietów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d993d-113">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="d993d-114">Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — Instalowanie programu .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="d993d-114">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="d993d-115">Pobierz i ręcznie zainstaluj</span><span class="sxs-lookup"><span data-stu-id="d993d-115">Download and manually install</span></span>

<span data-ttu-id="d993d-116">Aby wyodrębnić zestaw SDK i udostępnić polecenia w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d993d-116">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="d993d-117">Następnie otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="d993d-117">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.0.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="d993d-118">Powyższe polecenia spowodują udostępnienie poleceń zestawu .NET SDK dla sesji terminalu, w której został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="d993d-118">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="d993d-119">Możesz edytować profil powłoki, aby trwale dodać polecenia.</span><span class="sxs-lookup"><span data-stu-id="d993d-119">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="d993d-120">Istnieje wiele różnych powłok dostępnych dla systemu Linux, a każdy z nich ma inny profil.</span><span class="sxs-lookup"><span data-stu-id="d993d-120">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="d993d-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d993d-121">For example:</span></span>
>
> - <span data-ttu-id="d993d-122">**Bash Shell**: *~/. bash_profile*, *~/.bashrc.*</span><span class="sxs-lookup"><span data-stu-id="d993d-122">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="d993d-123">**Powłoka Korn**: *~/.KSHRC* lub *. profile*</span><span class="sxs-lookup"><span data-stu-id="d993d-123">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="d993d-124">**Powłoka Z**: *~/.zshrc* lub *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="d993d-124">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="d993d-125">Edytuj odpowiedni plik źródłowy dla powłoki i Dodaj `:$HOME/dotnet` na końcu istniejącej instrukcji `PATH`.</span><span class="sxs-lookup"><span data-stu-id="d993d-125">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="d993d-126">Jeśli nie dołączono żadnej instrukcji `PATH`, Dodaj nowy wiersz z `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="d993d-126">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="d993d-127">Ponadto Dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="d993d-127">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="d993d-128">Instalowanie za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d993d-128">Install with Visual Studio</span></span>

<span data-ttu-id="d993d-129">Jeśli używasz programu Visual Studio do tworzenia aplikacji platformy .NET Core, w poniższej tabeli opisano minimalną wymaganą wersję programu Visual Studio opartą na docelowej wersji zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d993d-129">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="d993d-130">Wersja zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="d993d-130">.NET Core SDK version</span></span> | <span data-ttu-id="d993d-131">Wersja programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d993d-131">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="d993d-132">wersja zapoznawcza 3,1</span><span class="sxs-lookup"><span data-stu-id="d993d-132">3.1 Preview</span></span>           | <span data-ttu-id="d993d-133">Visual Studio 2019 w wersji 16,4 Preview lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="d993d-133">Visual Studio 2019 version 16.4 preview or higher.</span></span> |
| <span data-ttu-id="d993d-134">3.0</span><span class="sxs-lookup"><span data-stu-id="d993d-134">3.0</span></span>                   | <span data-ttu-id="d993d-135">Program Visual Studio 2019 w wersji 16,3 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="d993d-135">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="d993d-136">2,2</span><span class="sxs-lookup"><span data-stu-id="d993d-136">2.2</span></span>                   | <span data-ttu-id="d993d-137">Program Visual Studio 2017 w wersji 15,9 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="d993d-137">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="d993d-138">2,1</span><span class="sxs-lookup"><span data-stu-id="d993d-138">2.1</span></span>                   | <span data-ttu-id="d993d-139">Program Visual Studio 2017 w wersji 15,7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="d993d-139">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="d993d-140">Jeśli masz już zainstalowany program Visual Studio, możesz sprawdzić swoją wersję, wykonując poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="d993d-140">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="d993d-141">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d993d-141">Open Visual Studio.</span></span>
01. <span data-ttu-id="d993d-142">Wybierz **pomoc** > **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d993d-142">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="d993d-143">Odczytaj numer wersji z okna dialogowego **informacje** .</span><span class="sxs-lookup"><span data-stu-id="d993d-143">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="d993d-144">Program Visual Studio może zainstalować najnowsze zestaw .NET Core SDK i środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="d993d-144">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="d993d-145">[Pobierz program Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="d993d-145">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="d993d-146">Wybierz obciążenie</span><span class="sxs-lookup"><span data-stu-id="d993d-146">Select a workload</span></span>

<span data-ttu-id="d993d-147">Podczas instalowania lub modyfikowania programu Visual Studio wybierz jedno z następujących obciążeń, w zależności od rodzaju kompilowanej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d993d-147">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="d993d-148">Obciążenie **Międzyplatformowe dla platformy .NET Core** w sekcji **inne zestawy narzędzi** .</span><span class="sxs-lookup"><span data-stu-id="d993d-148">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="d993d-149">**ASP.NET i programowanie w sieci Web** w sekcji **chmury & sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="d993d-149">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="d993d-150">Obciążenie **Programowanie na platformie Azure** w sekcji **chmury & sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="d993d-150">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="d993d-151">Obciążenie **Programowanie aplikacji klasycznych na platformie .NET** znajduje się w sekcji **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="d993d-151">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="d993d-152">[![Windows Visual Studio 2019 z obciążeniem platformy .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d993d-152">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="d993d-153">Zainstaluj przy użyciu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="d993d-153">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="d993d-154">Visual Studio dla komputerów Mac instaluje zestaw .NET Core SDK w przypadku wybrania obciążenia **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="d993d-154">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="d993d-155">Aby rozpocząć pracę z programowaniem programu .NET Core w systemie macOS, zobacz [Instalowanie programu Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="d993d-155">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="d993d-156">[![macOS programu Visual Studio 2019 for Mac z funkcją obciążenia .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d993d-156">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="d993d-157">Zainstaluj obok Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d993d-157">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="d993d-158">Visual Studio Code to zaawansowany i lekki Edytor kodu źródłowego, który jest uruchamiany na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="d993d-158">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="d993d-159">Visual Studio Code jest dostępny dla systemów Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="d993d-159">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="d993d-160">Mimo że Visual Studio Code nie jest dołączony do zautomatyzowanego Instalatora .NET Core, takiego jak Visual Studio, Dodawanie obsługi .NET Core jest proste.</span><span class="sxs-lookup"><span data-stu-id="d993d-160">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="d993d-161">[Pobierz i zainstaluj Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="d993d-161">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="d993d-162">[Pobierz i zainstaluj zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="d993d-162">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="d993d-163">[Zainstaluj C# rozszerzenie z witryny Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="d993d-163">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="d993d-164">Instalowanie przy użyciu programu PowerShell Automation</span><span class="sxs-lookup"><span data-stu-id="d993d-164">Install with PowerShell automation</span></span>

<span data-ttu-id="d993d-165">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="d993d-165">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="d993d-166">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="d993d-166">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="d993d-167">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="d993d-167">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="d993d-168">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="d993d-168">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="d993d-169">Instalowanie przy użyciu usługi Bash Automation</span><span class="sxs-lookup"><span data-stu-id="d993d-169">Install with bash automation</span></span>

<span data-ttu-id="d993d-170">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="d993d-170">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="d993d-171">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="d993d-171">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="d993d-172">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="d993d-172">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="d993d-173">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="d993d-173">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="d993d-174">Wszystkie pliki do pobrania z platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="d993d-174">All .NET Core downloads</span></span>

<span data-ttu-id="d993d-175">Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="d993d-175">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="d993d-176">Pobieranie z wersji zapoznawczej programu .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="d993d-176">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="d993d-177">Pliki do pobrania w programie .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="d993d-177">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="d993d-178">Pliki do pobrania w programie .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="d993d-178">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="d993d-179">Pliki do pobrania w programie .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d993d-179">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="d993d-180">Docker</span><span class="sxs-lookup"><span data-stu-id="d993d-180">Docker</span></span>

<span data-ttu-id="d993d-181">Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="d993d-181">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="d993d-182">Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d993d-182">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="d993d-183">Środowisko .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="d993d-183">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="d993d-184">Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="d993d-184">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="d993d-185">Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="d993d-185">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="d993d-186">Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="d993d-186">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="d993d-187">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="d993d-187">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="d993d-188">Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="d993d-188">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d993d-189">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d993d-189">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="d993d-190">[Samouczek: C# samouczek Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d993d-190">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="d993d-191">[Samouczek: Visual Basic Hello World samouczka](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d993d-191">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="d993d-192">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="d993d-192">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="d993d-193">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="d993d-193">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="d993d-194">[Samouczek: Rozpoczynanie pracy w witrynie macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d993d-194">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="d993d-195">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="d993d-195">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="d993d-196">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="d993d-196">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
