---
title: Instalowanie zestaw .NET Core SDK w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do tworzenia aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 004ef2a768f4a5415942d405e4a8292928c89f94
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340656"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="fbe15-104">Zainstaluj zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="fbe15-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="fbe15-105">W tym artykule dowiesz się, jak zainstalować zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="fbe15-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="fbe15-106">Zestaw .NET Core SDK jest używany do tworzenia aplikacji i bibliotek platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fbe15-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="fbe15-107">Środowisko uruchomieniowe platformy .NET Core jest zawsze instalowane z zestawem SDK.</span><span class="sxs-lookup"><span data-stu-id="fbe15-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="fbe15-108">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="fbe15-108">Install with an installer</span></span>

<span data-ttu-id="fbe15-109">System Windows ma autonomiczne Instalatory, których można użyć do zainstalowania zestawu SDK programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="fbe15-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="fbe15-110">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="fbe15-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="fbe15-111">Procesory x86 (32-bitowe)</span><span class="sxs-lookup"><span data-stu-id="fbe15-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="fbe15-112">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="fbe15-112">Install with an installer</span></span>

<span data-ttu-id="fbe15-113">macOS ma autonomiczne Instalatory, których można użyć do zainstalowania zestawu SDK programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="fbe15-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="fbe15-114">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="fbe15-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="fbe15-115">Instalowanie przy użyciu Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="fbe15-115">Install with a package manager</span></span>

<span data-ttu-id="fbe15-116">Zestaw .NET Core SDK można zainstalować przy użyciu wielu popularnych menedżerów pakietów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="fbe15-116">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="fbe15-117">Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — Instalowanie programu .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-117">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="fbe15-118">Instalowanie za pomocą Menedżera pakietów jest obsługiwane tylko w architekturze x64.</span><span class="sxs-lookup"><span data-stu-id="fbe15-118">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="fbe15-119">Jeśli instalujesz zestaw .NET Core SDK z inną architekturą, taką jak ARM, postępuj zgodnie z poniższymi instrukcjami [pobierania i ręcznej instalacji](#download-and-manually-install) .</span><span class="sxs-lookup"><span data-stu-id="fbe15-119">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="fbe15-120">Aby uzyskać więcej informacji o obsługiwanych architekturach, zobacz temat [zależności i wymagania dotyczące platformy .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-120">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="fbe15-121">Pobierz i ręcznie zainstaluj</span><span class="sxs-lookup"><span data-stu-id="fbe15-121">Download and manually install</span></span>

<span data-ttu-id="fbe15-122">Aby wyodrębnić zestaw SDK i udostępnić interfejs wiersza polecenia platformy .NET Core polecenia w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fbe15-122">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="fbe15-123">Następnie otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="fbe15-123">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="fbe15-124">Poprzednie polecenia `export` powodują, że interfejs wiersza polecenia platformy .NET Core polecenia dostępne dla sesji terminalu, w której został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="fbe15-124">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="fbe15-125">Możesz edytować profil powłoki, aby trwale dodać polecenia.</span><span class="sxs-lookup"><span data-stu-id="fbe15-125">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="fbe15-126">Istnieje wiele różnych powłok dostępnych dla systemu Linux, a każdy z nich ma inny profil.</span><span class="sxs-lookup"><span data-stu-id="fbe15-126">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="fbe15-127">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fbe15-127">For example:</span></span>
>
> - <span data-ttu-id="fbe15-128">**Bash Shell**: *~/. bash_profile*, *~/.bashrc.*</span><span class="sxs-lookup"><span data-stu-id="fbe15-128">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="fbe15-129">**Powłoka Korn**: *~/.KSHRC* lub *. profile*</span><span class="sxs-lookup"><span data-stu-id="fbe15-129">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="fbe15-130">**Powłoka Z**: *~/.zshrc* lub *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="fbe15-130">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="fbe15-131">Edytuj odpowiedni plik źródłowy dla powłoki i Dodaj `:$HOME/dotnet` na końcu istniejącej instrukcji `PATH`.</span><span class="sxs-lookup"><span data-stu-id="fbe15-131">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="fbe15-132">Jeśli nie dołączono żadnej instrukcji `PATH`, Dodaj nowy wiersz z `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="fbe15-132">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="fbe15-133">Ponadto Dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="fbe15-133">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="fbe15-134">Instalowanie za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fbe15-134">Install with Visual Studio</span></span>

<span data-ttu-id="fbe15-135">Jeśli używasz programu Visual Studio do tworzenia aplikacji platformy .NET Core, w poniższej tabeli opisano minimalną wymaganą wersję programu Visual Studio opartą na docelowej wersji zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="fbe15-135">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="fbe15-136">Wersja zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="fbe15-136">.NET Core SDK version</span></span> | <span data-ttu-id="fbe15-137">Wersja programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fbe15-137">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="fbe15-138">3.1</span><span class="sxs-lookup"><span data-stu-id="fbe15-138">3.1</span></span>                   | <span data-ttu-id="fbe15-139">Program Visual Studio 2019 w wersji 16,4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="fbe15-139">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="fbe15-140">3.0</span><span class="sxs-lookup"><span data-stu-id="fbe15-140">3.0</span></span>                   | <span data-ttu-id="fbe15-141">Program Visual Studio 2019 w wersji 16,3 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="fbe15-141">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="fbe15-142">2.2</span><span class="sxs-lookup"><span data-stu-id="fbe15-142">2.2</span></span>                   | <span data-ttu-id="fbe15-143">Program Visual Studio 2017 w wersji 15,9 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="fbe15-143">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="fbe15-144">2.1</span><span class="sxs-lookup"><span data-stu-id="fbe15-144">2.1</span></span>                   | <span data-ttu-id="fbe15-145">Program Visual Studio 2017 w wersji 15,7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="fbe15-145">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="fbe15-146">Jeśli masz już zainstalowany program Visual Studio, możesz sprawdzić swoją wersję, wykonując poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="fbe15-146">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="fbe15-147">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fbe15-147">Open Visual Studio.</span></span>
01. <span data-ttu-id="fbe15-148">Wybierz **pomoc** > **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="fbe15-148">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="fbe15-149">Odczytaj numer wersji z okna dialogowego **informacje** .</span><span class="sxs-lookup"><span data-stu-id="fbe15-149">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="fbe15-150">Program Visual Studio może zainstalować najnowsze zestaw .NET Core SDK i środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="fbe15-150">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="fbe15-151">[Pobierz program Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="fbe15-151">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="fbe15-152">Wybierz obciążenie</span><span class="sxs-lookup"><span data-stu-id="fbe15-152">Select a workload</span></span>

<span data-ttu-id="fbe15-153">Podczas instalowania lub modyfikowania programu Visual Studio wybierz jedno z następujących obciążeń, w zależności od rodzaju kompilowanej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="fbe15-153">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="fbe15-154">Obciążenie **Międzyplatformowe dla platformy .NET Core** w sekcji **inne zestawy narzędzi** .</span><span class="sxs-lookup"><span data-stu-id="fbe15-154">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="fbe15-155">**ASP.NET i programowanie w sieci Web** w sekcji **chmury & sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="fbe15-155">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="fbe15-156">Obciążenie **Programowanie na platformie Azure** w sekcji **chmury & sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="fbe15-156">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="fbe15-157">Obciążenie **Programowanie aplikacji klasycznych na platformie .NET** znajduje się w sekcji **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="fbe15-157">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="fbe15-158">[![Windows Visual Studio 2019 z obciążeniem platformy .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="fbe15-158">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="fbe15-159">Zainstaluj przy użyciu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="fbe15-159">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="fbe15-160">Visual Studio dla komputerów Mac instaluje zestaw .NET Core SDK w przypadku wybrania obciążenia **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="fbe15-160">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="fbe15-161">Aby rozpocząć pracę z programowaniem programu .NET Core w systemie macOS, zobacz [Instalowanie programu Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="fbe15-161">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="fbe15-162">W przypadku najnowszej wersji programu .NET Core 3,1 należy użyć wersji zapoznawczej Visual Studio dla komputerów Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="fbe15-162">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="fbe15-163">[![macOS programu Visual Studio 2019 for Mac z funkcją obciążenia .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="fbe15-163">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="fbe15-164">Zainstaluj obok Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fbe15-164">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="fbe15-165">Visual Studio Code to zaawansowany i lekki Edytor kodu źródłowego, który jest uruchamiany na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="fbe15-165">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="fbe15-166">Visual Studio Code jest dostępny dla systemów Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="fbe15-166">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="fbe15-167">Mimo że Visual Studio Code nie jest dołączony do zautomatyzowanego Instalatora .NET Core, takiego jak Visual Studio, Dodawanie obsługi .NET Core jest proste.</span><span class="sxs-lookup"><span data-stu-id="fbe15-167">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="fbe15-168">[Pobierz i zainstaluj Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="fbe15-168">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="fbe15-169">[Pobierz i zainstaluj zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="fbe15-169">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="fbe15-170">[Zainstaluj C# rozszerzenie z witryny Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="fbe15-170">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="fbe15-171">Instalowanie przy użyciu programu PowerShell Automation</span><span class="sxs-lookup"><span data-stu-id="fbe15-171">Install with PowerShell automation</span></span>

<span data-ttu-id="fbe15-172">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="fbe15-172">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="fbe15-173">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-173">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="fbe15-174">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="fbe15-174">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="fbe15-175">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="fbe15-175">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="fbe15-176">Instalowanie przy użyciu usługi Bash Automation</span><span class="sxs-lookup"><span data-stu-id="fbe15-176">Install with bash automation</span></span>

<span data-ttu-id="fbe15-177">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="fbe15-177">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="fbe15-178">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-178">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="fbe15-179">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="fbe15-179">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="fbe15-180">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt z następującym przełącznikiem.</span><span class="sxs-lookup"><span data-stu-id="fbe15-180">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="fbe15-181">Wszystkie pliki do pobrania z platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="fbe15-181">All .NET Core downloads</span></span>

<span data-ttu-id="fbe15-182">Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="fbe15-182">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="fbe15-183">Pliki do pobrania w programie .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="fbe15-183">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="fbe15-184">Pliki do pobrania w programie .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="fbe15-184">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="fbe15-185">Pliki do pobrania w programie .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="fbe15-185">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="fbe15-186">Pliki do pobrania w programie .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="fbe15-186">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="fbe15-187">Docker</span><span class="sxs-lookup"><span data-stu-id="fbe15-187">Docker</span></span>

<span data-ttu-id="fbe15-188">Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="fbe15-188">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="fbe15-189">Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fbe15-189">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="fbe15-190">Środowisko .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="fbe15-190">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="fbe15-191">Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="fbe15-191">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="fbe15-192">Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="fbe15-192">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="fbe15-193">Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="fbe15-193">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="fbe15-194">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="fbe15-194">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="fbe15-195">Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-195">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fbe15-196">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fbe15-196">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="fbe15-197">[Samouczek: samouczek Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-197">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="fbe15-198">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-198">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="fbe15-199">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-199">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="fbe15-200">[Samouczek: Rozpoczynanie pracy w witrynie macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-200">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="fbe15-201">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="fbe15-202">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="fbe15-203">[Samouczek: Tworzenie nowej aplikacji przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-203">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="fbe15-204">[Samouczek: konteneryzowanie aplikacji .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="fbe15-204">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
