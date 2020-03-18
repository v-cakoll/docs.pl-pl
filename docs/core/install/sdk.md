---
title: Instalowanie .NET Core SDK w systemach Windows, Linux i macOS - .NET Core
description: Dowiedz się, jak zainstalować program .NET Core w systemach Windows, Linux i macOS. Odnajdowanie zależności wymaganych do tworzenia aplikacji .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399008"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="40c8e-104">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="40c8e-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="40c8e-105">W tym artykule dowiesz się, jak zainstalować zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40c8e-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="40c8e-106">Zestaw SDK .NET Core służy do tworzenia aplikacji i bibliotek .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40c8e-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="40c8e-107">Czas uruchomieniowy .NET Core jest zawsze instalowany przy ks.</span><span class="sxs-lookup"><span data-stu-id="40c8e-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="40c8e-108">Instalacja z instalatorem</span><span class="sxs-lookup"><span data-stu-id="40c8e-108">Install with an installer</span></span>

<span data-ttu-id="40c8e-109">System Windows ma autonomiczne instalatory, za których można zainstalować zestaw SDK .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="40c8e-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="40c8e-110">x64 (64-bitowe) procesory</span><span class="sxs-lookup"><span data-stu-id="40c8e-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="40c8e-111">x86 (32-bitowe) procesory</span><span class="sxs-lookup"><span data-stu-id="40c8e-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="40c8e-112">Instalacja z instalatorem</span><span class="sxs-lookup"><span data-stu-id="40c8e-112">Install with an installer</span></span>

<span data-ttu-id="40c8e-113">System macOS ma autonomiczne instalatory, za których można zainstalować zestaw SDK .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="40c8e-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="40c8e-114">x64 (64-bitowe) procesory</span><span class="sxs-lookup"><span data-stu-id="40c8e-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="40c8e-115">Pobieranie i ręczne instalowanie</span><span class="sxs-lookup"><span data-stu-id="40c8e-115">Download and manually install</span></span>

<span data-ttu-id="40c8e-116">Jako alternatywę dla instalatorów systemu macOS dla platformy .NET Core można pobrać i ręcznie zainstalować zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="40c8e-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="40c8e-117">Aby wyodrębnić zestaw SDK i udostępnić polecenia wiersza polecenia .NET Core na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40c8e-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="40c8e-118">Następnie otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="40c8e-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="40c8e-119">Zakłada się, że czas wykonywania `~/Downloads/dotnet-sdk.pkg` jest pobierany do pliku.</span><span class="sxs-lookup"><span data-stu-id="40c8e-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="40c8e-120">Instalowanie za pomocą menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="40c8e-120">Install with a package manager</span></span>

<span data-ttu-id="40c8e-121">Zestaw SDK .NET Core można zainstalować z wieloma typowymi menedżerami pakietów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="40c8e-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="40c8e-122">Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — instalowanie programu .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="40c8e-123">Instalacja z menedżerem pakietów jest obsługiwana tylko w architekturze x64.</span><span class="sxs-lookup"><span data-stu-id="40c8e-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="40c8e-124">Jeśli instalujesz zestaw SDK .NET Core o innej architekturze, takiej jak ARM, postępuj zgodnie z poniższą [instrukcją pobierania i ręcznie zainstaluj.](#download-and-manually-install)</span><span class="sxs-lookup"><span data-stu-id="40c8e-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="40c8e-125">Aby uzyskać więcej informacji na temat obsługiwanych architektur, zobacz [zależności i wymagania programu .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="40c8e-126">Pobieranie i ręczne instalowanie</span><span class="sxs-lookup"><span data-stu-id="40c8e-126">Download and manually install</span></span>

<span data-ttu-id="40c8e-127">Aby wyodrębnić zestaw SDK i udostępnić polecenia wiersza polecenia .NET Core na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40c8e-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="40c8e-128">Następnie otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="40c8e-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="40c8e-129">Poprzednie `export` polecenia udostępniają tylko polecenia cli .NET Core dla sesji terminala, w której została ona uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="40c8e-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="40c8e-130">Profil powłoki można edytować, aby trwale dodawać polecenia.</span><span class="sxs-lookup"><span data-stu-id="40c8e-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="40c8e-131">Istnieje wiele różnych powłok dostępnych dla Linuksa i każdy ma inny profil.</span><span class="sxs-lookup"><span data-stu-id="40c8e-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="40c8e-132">Przykład:</span><span class="sxs-lookup"><span data-stu-id="40c8e-132">For example:</span></span>
>
> - <span data-ttu-id="40c8e-133">**Powłoka Bash**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="40c8e-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="40c8e-134">**Korn Shell**: *~/.kshrc* lub *.profile*</span><span class="sxs-lookup"><span data-stu-id="40c8e-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="40c8e-135">**Z Powłoka**: *~/.zshrc* lub *.zprofil*</span><span class="sxs-lookup"><span data-stu-id="40c8e-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="40c8e-136">Edytowanie odpowiedniego pliku źródłowego dla `:$HOME/dotnet` powłoki i `PATH` dodanie na końcu istniejącej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="40c8e-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="40c8e-137">Jeśli `PATH` instrukcja nie jest dołączona, dodaj nowy wiersz z . `export PATH=$PATH:$HOME/dotnet`</span><span class="sxs-lookup"><span data-stu-id="40c8e-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="40c8e-138">Ponadto dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="40c8e-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="40c8e-139">Instalowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="40c8e-139">Install with Visual Studio</span></span>

<span data-ttu-id="40c8e-140">Jeśli używasz programu Visual Studio do tworzenia aplikacji .NET Core, w poniższej tabeli opisano minimalną wymaganą wersję programu Visual Studio na podstawie docelowej wersji sdk .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40c8e-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="40c8e-141">Wersja SDK programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="40c8e-141">.NET Core SDK version</span></span> | <span data-ttu-id="40c8e-142">Wersja programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="40c8e-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="40c8e-143">3.1</span><span class="sxs-lookup"><span data-stu-id="40c8e-143">3.1</span></span>                   | <span data-ttu-id="40c8e-144">Program Visual Studio 2019 w wersji 16.4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="40c8e-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="40c8e-145">3.0</span><span class="sxs-lookup"><span data-stu-id="40c8e-145">3.0</span></span>                   | <span data-ttu-id="40c8e-146">Program Visual Studio 2019 w wersji 16.3 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="40c8e-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="40c8e-147">2.2</span><span class="sxs-lookup"><span data-stu-id="40c8e-147">2.2</span></span>                   | <span data-ttu-id="40c8e-148">Program Visual Studio 2017 w wersji 15.9 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="40c8e-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="40c8e-149">2.1</span><span class="sxs-lookup"><span data-stu-id="40c8e-149">2.1</span></span>                   | <span data-ttu-id="40c8e-150">Program Visual Studio 2017 w wersji 15.7 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="40c8e-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="40c8e-151">Jeśli masz już zainstalowany program Visual Studio, możesz sprawdzić wersję, wykonując następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="40c8e-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="40c8e-152">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40c8e-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="40c8e-153">Wybierz **pozycję Pomoc dotyczącą** > **programu Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="40c8e-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="40c8e-154">Przeczytaj numer wersji z okna dialogowego **Informacje.**</span><span class="sxs-lookup"><span data-stu-id="40c8e-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="40c8e-155">Program Visual Studio może zainstalować najnowszy zestaw SDK i program .NET Core SDK i program runtime.</span><span class="sxs-lookup"><span data-stu-id="40c8e-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="40c8e-156">[Pobierz program Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="40c8e-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="40c8e-157">Wybieranie obciążenia</span><span class="sxs-lookup"><span data-stu-id="40c8e-157">Select a workload</span></span>

<span data-ttu-id="40c8e-158">Podczas instalowania lub modyfikowania programu Visual Studio wybierz co najmniej jeden z następujących obciążeń, w zależności od rodzaju aplikacji, którą budujesz:</span><span class="sxs-lookup"><span data-stu-id="40c8e-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="40c8e-159">**Obciążenie programistyczne programu .NET Core na wielu platformach** w sekcji **Inne zestawy narzędzi.**</span><span class="sxs-lookup"><span data-stu-id="40c8e-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="40c8e-160">Obciążenie **ASP.NET i tworzeniem stron internetowych** w sekcji Web & **Cloud.**</span><span class="sxs-lookup"><span data-stu-id="40c8e-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="40c8e-161">Obciążenie **programistyczne platformy Azure** w sekcji **& chmura w sieci Web.**</span><span class="sxs-lookup"><span data-stu-id="40c8e-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="40c8e-162">Obciążenie **programistyczne dla komputerów stacjonarnych .NET** w sekcji **Desktop & Mobile.**</span><span class="sxs-lookup"><span data-stu-id="40c8e-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="40c8e-163">[![Program Windows Visual Studio 2019 z obciążeniem programu .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="40c8e-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="40c8e-164">Pobieranie i ręczne instalowanie</span><span class="sxs-lookup"><span data-stu-id="40c8e-164">Download and manually install</span></span>

<span data-ttu-id="40c8e-165">Aby wyodrębnić czas wykonywania i udostępnić polecenia wiersza polecenia .NET Core na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40c8e-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="40c8e-166">Następnie utwórz katalog do zainstalowania `%USERPROFILE%\dotnet`na przykład .</span><span class="sxs-lookup"><span data-stu-id="40c8e-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="40c8e-167">Na koniec wyodrębnij pobrany plik zip do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="40c8e-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="40c8e-168">Domyślnie polecenia i aplikacje cli programu .NET Core nie będą używać zainstalowanego w ten sposób programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40c8e-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="40c8e-169">Musisz jawnie zdecydować się na jego użycie.</span><span class="sxs-lookup"><span data-stu-id="40c8e-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="40c8e-170">W tym celu należy zmienić zmienne środowiskowe, z którymi aplikacja jest uruchamiana:</span><span class="sxs-lookup"><span data-stu-id="40c8e-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="40c8e-171">Takie podejście umożliwia zainstalowanie wielu wersji w oddzielnych lokalizacjach, a następnie jawnie wybrać lokalizację instalacji, której aplikacja powinna używać, uruchamiając aplikację ze zmiennymi środowiskowymi wskazującymi w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="40c8e-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="40c8e-172">Nawet wtedy, gdy te zmienne środowiskowe są ustawione, .NET Core nadal bierze pod uwagę domyślną globalną lokalizację instalacji podczas wybierania najlepszej struktury do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40c8e-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="40c8e-173">Wartością domyślną `C:\Program Files\dotnet`jest zazwyczaj , z której korzystają instalatorzy.</span><span class="sxs-lookup"><span data-stu-id="40c8e-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="40c8e-174">Środowisko uruchomieniowe można poinstruować, aby używały tylko niestandardowej lokalizacji instalacji, ustawiając również tę zmienną środowiskową:</span><span class="sxs-lookup"><span data-stu-id="40c8e-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="40c8e-175">Instalowanie w programie Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="40c8e-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="40c8e-176">Program Visual Studio dla komputerów Mac instaluje zestaw SDK .NET Core po wybraniu obciążenia **.NET Core.**</span><span class="sxs-lookup"><span data-stu-id="40c8e-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="40c8e-177">Aby rozpocząć pracę z programami .NET Core w systemie macOS, zobacz [Instalowanie programu Visual Studio 2019 dla komputerów Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="40c8e-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="40c8e-178">Aby uzyskać najnowszą wersję .NET Core 3.1, należy użyć programu Visual Studio preview dla komputerów Mac 8.4.</span><span class="sxs-lookup"><span data-stu-id="40c8e-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="40c8e-179">[![MacOS Visual Studio 2019 dla komputerów Mac z funkcją obciążenia .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="40c8e-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="40c8e-180">Instalowanie obok kodu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="40c8e-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="40c8e-181">Visual Studio Code to zaawansowany i lekki edytor kodu źródłowego, który jest uruchamiany na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="40c8e-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="40c8e-182">Kod programu Visual Studio jest dostępny dla systemów Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="40c8e-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="40c8e-183">Chociaż kod programu Visual Studio nie pochodzi z automatycznego instalatora .NET Core, jak Visual Studio nie, dodawanie .NET Core obsługuje jest prosta.</span><span class="sxs-lookup"><span data-stu-id="40c8e-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="40c8e-184">[Pobierz i zainstaluj kod programu Visual Studio](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="40c8e-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="40c8e-185">[Pobierz i zainstaluj zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="40c8e-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="40c8e-186">[Zainstaluj rozszerzenie C# z portalu Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="40c8e-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="40c8e-187">Instalacja za pomocą automatyzacji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="40c8e-187">Install with PowerShell automation</span></span>

<span data-ttu-id="40c8e-188">[Skrypty dotnet-install](../tools/dotnet-install-script.md) są używane do automatyzacji i instalacji bez administratora sdk.</span><span class="sxs-lookup"><span data-stu-id="40c8e-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="40c8e-189">Skrypt można pobrać ze [strony referencyjnej skryptu dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="40c8e-190">Skrypt domyślnie instaluje najnowszą wersję [obsługi długoterminowej (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) która jest .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="40c8e-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="40c8e-191">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt za pomocą następującego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="40c8e-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="40c8e-192">Instalacja z automatyzacją bash</span><span class="sxs-lookup"><span data-stu-id="40c8e-192">Install with bash automation</span></span>

<span data-ttu-id="40c8e-193">[Skrypty dotnet-install](../tools/dotnet-install-script.md) są używane do automatyzacji i instalacji bez administratora sdk.</span><span class="sxs-lookup"><span data-stu-id="40c8e-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="40c8e-194">Skrypt można pobrać ze [strony referencyjnej skryptu dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="40c8e-195">Skrypt domyślnie instaluje najnowszą wersję [obsługi długoterminowej (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) która jest .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="40c8e-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="40c8e-196">Aby zainstalować bieżącą wersję programu .NET Core, uruchom skrypt za pomocą następującego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="40c8e-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="40c8e-197">Wszystkie pliki do pobrania programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="40c8e-197">All .NET Core downloads</span></span>

<span data-ttu-id="40c8e-198">Program .NET Core można pobrać i zainstalować bezpośrednio za pomocą jednego z następujących łączy:</span><span class="sxs-lookup"><span data-stu-id="40c8e-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="40c8e-199">Pliki do pobrania programu .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="40c8e-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="40c8e-200">Pliki do pobrania programu .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="40c8e-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="40c8e-201">Pliki do pobrania programu .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="40c8e-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="40c8e-202">Pliki do pobrania programu .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="40c8e-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="40c8e-203">Docker</span><span class="sxs-lookup"><span data-stu-id="40c8e-203">Docker</span></span>

<span data-ttu-id="40c8e-204">Kontenery zapewniają lekki sposób izolowania aplikacji od reszty systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="40c8e-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="40c8e-205">Kontenery na tym samym komputerze współużytkują tylko jądro i używają zasobów podanych do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40c8e-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="40c8e-206">Program .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="40c8e-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="40c8e-207">Oficjalne obrazy platformy Docker platformy .NET Core są publikowane w rejestrze kontenerów firmy Microsoft (MCR) i można je wykryć w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="40c8e-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="40c8e-208">Każde repozytorium zawiera obrazy dla różnych kombinacji .NET (SDK lub Runtime) i OS, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="40c8e-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="40c8e-209">Firma Microsoft udostępnia obrazy dostosowane do określonych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="40c8e-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="40c8e-210">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy, które są tworzone do uruchamiania ASP.NET aplikacji Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="40c8e-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="40c8e-211">Aby uzyskać więcej informacji na temat używania programu .NET Core w kontenerze platformy Docker, zobacz [Wprowadzenie do platformy .NET i platformy Docker](../docker/introduction.md) oraz [samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="40c8e-212">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="40c8e-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="40c8e-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="40c8e-214">[Samouczek: Tworzenie nowej aplikacji z kodem programu Visual Studio](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="40c8e-215">[Samouczek: Konteneryzuj aplikację .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="40c8e-216">[Praca z notarialną macOS Catalina](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="40c8e-217">[Samouczek: Wprowadzenie do systemu macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="40c8e-218">[Samouczek: Tworzenie nowej aplikacji z kodem programu Visual Studio](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="40c8e-219">[Samouczek: Konteneryzuj aplikację .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="40c8e-220">[Samouczek: Tworzenie nowej aplikacji z kodem programu Visual Studio](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="40c8e-221">[Samouczek: Konteneryzuj aplikację .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="40c8e-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
