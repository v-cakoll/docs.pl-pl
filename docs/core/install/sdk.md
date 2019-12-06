---
title: Instalowanie zestaw .NET Core SDK w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do tworzenia aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 5ac2d7897ee4c6707669e4f9104317aeb2e1f473
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835683"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="6367d-104">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6367d-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="6367d-105">W tym artykule dowiesz się, jak zainstalować zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6367d-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="6367d-106">Zestaw .NET Core SDK jest używany do tworzenia aplikacji i bibliotek platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6367d-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="6367d-107">Środowisko uruchomieniowe platformy .NET Core jest zawsze instalowane z zestawem SDK.</span><span class="sxs-lookup"><span data-stu-id="6367d-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="6367d-108">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="6367d-108">Install with an installer</span></span>

<span data-ttu-id="6367d-109">System Windows ma autonomiczne Instalatory, których można użyć do zainstalowania zestawu SDK programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="6367d-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="6367d-110">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="6367d-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="6367d-111">Procesory x86 (32-bitowe)</span><span class="sxs-lookup"><span data-stu-id="6367d-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="6367d-112">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="6367d-112">Install with an installer</span></span>

<span data-ttu-id="6367d-113">macOS ma autonomiczne Instalatory, których można użyć do zainstalowania zestawu SDK programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="6367d-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="6367d-114">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="6367d-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="6367d-115">Instalowanie przy użyciu Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="6367d-115">Install with a package manager</span></span>

<span data-ttu-id="6367d-116">Zestaw .NET Core SDK można zainstalować przy użyciu wielu popularnych menedżerów pakietów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="6367d-116">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="6367d-117">Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — Instalowanie programu .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-117">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="6367d-118">Pobierz i ręcznie zainstaluj</span><span class="sxs-lookup"><span data-stu-id="6367d-118">Download and manually install</span></span>

<span data-ttu-id="6367d-119">Aby wyodrębnić zestaw SDK i udostępnić polecenia w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6367d-119">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="6367d-120">Następnie otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="6367d-120">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="6367d-121">Powyższe polecenia spowodują udostępnienie poleceń zestawu .NET SDK dla sesji terminalu, w której został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="6367d-121">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="6367d-122">Możesz edytować profil powłoki, aby trwale dodać polecenia.</span><span class="sxs-lookup"><span data-stu-id="6367d-122">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="6367d-123">Istnieje wiele różnych powłok dostępnych dla systemu Linux, a każdy z nich ma inny profil.</span><span class="sxs-lookup"><span data-stu-id="6367d-123">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="6367d-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6367d-124">For example:</span></span>
>
> - <span data-ttu-id="6367d-125">**Bash Shell**: *~/. bash_profile*, *~/.bashrc.*</span><span class="sxs-lookup"><span data-stu-id="6367d-125">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="6367d-126">**Powłoka Korn**: *~/.KSHRC* lub *. profile*</span><span class="sxs-lookup"><span data-stu-id="6367d-126">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="6367d-127">**Powłoka Z**: *~/.zshrc* lub *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="6367d-127">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="6367d-128">Edytuj odpowiedni plik źródłowy dla powłoki i Dodaj `:$HOME/dotnet` na końcu istniejącej instrukcji `PATH`.</span><span class="sxs-lookup"><span data-stu-id="6367d-128">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="6367d-129">Jeśli nie dołączono żadnej instrukcji `PATH`, Dodaj nowy wiersz z `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="6367d-129">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="6367d-130">Ponadto Dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="6367d-130">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="6367d-131">Instalowanie za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6367d-131">Install with Visual Studio</span></span>

<span data-ttu-id="6367d-132">Jeśli używasz programu Visual Studio do tworzenia aplikacji platformy .NET Core, w poniższej tabeli opisano minimalną wymaganą wersję programu Visual Studio opartą na docelowej wersji zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6367d-132">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="6367d-133">Wersja zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6367d-133">.NET Core SDK version</span></span> | <span data-ttu-id="6367d-134">Wersja programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6367d-134">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="6367d-135">3.1</span><span class="sxs-lookup"><span data-stu-id="6367d-135">3.1</span></span>                   | <span data-ttu-id="6367d-136">Program Visual Studio 2019 w wersji 16,4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="6367d-136">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="6367d-137">3.0</span><span class="sxs-lookup"><span data-stu-id="6367d-137">3.0</span></span>                   | <span data-ttu-id="6367d-138">Program Visual Studio 2019 w wersji 16,3 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="6367d-138">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="6367d-139">2.2</span><span class="sxs-lookup"><span data-stu-id="6367d-139">2.2</span></span>                   | <span data-ttu-id="6367d-140">Program Visual Studio 2017 w wersji 15,9 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="6367d-140">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="6367d-141">2.1</span><span class="sxs-lookup"><span data-stu-id="6367d-141">2.1</span></span>                   | <span data-ttu-id="6367d-142">Program Visual Studio 2017 w wersji 15,7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="6367d-142">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="6367d-143">Jeśli masz już zainstalowany program Visual Studio, możesz sprawdzić swoją wersję, wykonując poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="6367d-143">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="6367d-144">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6367d-144">Open Visual Studio.</span></span>
01. <span data-ttu-id="6367d-145">Wybierz **pomoc** > **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6367d-145">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="6367d-146">Odczytaj numer wersji z okna dialogowego **informacje** .</span><span class="sxs-lookup"><span data-stu-id="6367d-146">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="6367d-147">Program Visual Studio może zainstalować najnowsze zestaw .NET Core SDK i środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="6367d-147">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="6367d-148">[Pobierz program Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="6367d-148">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="6367d-149">Wybierz obciążenie</span><span class="sxs-lookup"><span data-stu-id="6367d-149">Select a workload</span></span>

<span data-ttu-id="6367d-150">Podczas instalowania lub modyfikowania programu Visual Studio wybierz jedno z następujących obciążeń, w zależności od rodzaju kompilowanej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="6367d-150">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="6367d-151">Obciążenie **Międzyplatformowe dla platformy .NET Core** w sekcji **inne zestawy narzędzi** .</span><span class="sxs-lookup"><span data-stu-id="6367d-151">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="6367d-152">**ASP.NET i programowanie w sieci Web** w sekcji **chmury & sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="6367d-152">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="6367d-153">Obciążenie **Programowanie na platformie Azure** w sekcji **chmury & sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="6367d-153">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="6367d-154">Obciążenie **Programowanie aplikacji klasycznych na platformie .NET** znajduje się w sekcji **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="6367d-154">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="6367d-155">[![Windows Visual Studio 2019 z obciążeniem platformy .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="6367d-155">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="6367d-156">Zainstaluj przy użyciu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="6367d-156">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="6367d-157">Visual Studio dla komputerów Mac instaluje zestaw .NET Core SDK w przypadku wybrania obciążenia **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="6367d-157">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="6367d-158">Aby rozpocząć pracę z programowaniem programu .NET Core w systemie macOS, zobacz [Instalowanie programu Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="6367d-158">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="6367d-159">W przypadku najnowszej wersji programu .NET Core 3,1 należy użyć wersji zapoznawczej Visual Studio dla komputerów Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="6367d-159">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="6367d-160">[![macOS programu Visual Studio 2019 for Mac z funkcją obciążenia .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="6367d-160">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="6367d-161">Zainstaluj obok Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6367d-161">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="6367d-162">Visual Studio Code to zaawansowany i lekki Edytor kodu źródłowego, który jest uruchamiany na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="6367d-162">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="6367d-163">Visual Studio Code jest dostępny dla systemów Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="6367d-163">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="6367d-164">Mimo że Visual Studio Code nie jest dołączony do zautomatyzowanego Instalatora .NET Core, takiego jak Visual Studio, Dodawanie obsługi .NET Core jest proste.</span><span class="sxs-lookup"><span data-stu-id="6367d-164">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="6367d-165">[Pobierz i zainstaluj Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="6367d-165">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="6367d-166">[Pobierz i zainstaluj zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6367d-166">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="6367d-167">[Zainstaluj C# rozszerzenie z witryny Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="6367d-167">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="6367d-168">Instalowanie przy użyciu programu PowerShell Automation</span><span class="sxs-lookup"><span data-stu-id="6367d-168">Install with PowerShell automation</span></span>

<span data-ttu-id="6367d-169">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="6367d-169">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="6367d-170">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-170">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="6367d-171">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="6367d-171">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="6367d-172">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="6367d-172">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="6367d-173">Instalowanie przy użyciu usługi Bash Automation</span><span class="sxs-lookup"><span data-stu-id="6367d-173">Install with bash automation</span></span>

<span data-ttu-id="6367d-174">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="6367d-174">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="6367d-175">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-175">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="6367d-176">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="6367d-176">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="6367d-177">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="6367d-177">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="6367d-178">Wszystkie pliki do pobrania z platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="6367d-178">All .NET Core downloads</span></span>

<span data-ttu-id="6367d-179">Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="6367d-179">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="6367d-180">Pobieranie z wersji zapoznawczej programu .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="6367d-180">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="6367d-181">Pliki do pobrania w programie .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="6367d-181">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="6367d-182">Pliki do pobrania w programie .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="6367d-182">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="6367d-183">Pliki do pobrania w programie .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="6367d-183">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="6367d-184">Docker</span><span class="sxs-lookup"><span data-stu-id="6367d-184">Docker</span></span>

<span data-ttu-id="6367d-185">Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="6367d-185">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="6367d-186">Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6367d-186">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="6367d-187">Środowisko .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="6367d-187">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="6367d-188">Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="6367d-188">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="6367d-189">Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="6367d-189">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="6367d-190">Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="6367d-190">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="6367d-191">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="6367d-191">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="6367d-192">Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-192">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6367d-193">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="6367d-193">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="6367d-194">[Samouczek: C# samouczek Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-194">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="6367d-195">[Samouczek: Visual Basic Hello World samouczka](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-195">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="6367d-196">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-196">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="6367d-197">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-197">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="6367d-198">[Samouczek: Rozpoczynanie pracy w witrynie macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-198">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="6367d-199">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-199">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="6367d-200">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-200">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="6367d-201">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="6367d-202">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="6367d-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
