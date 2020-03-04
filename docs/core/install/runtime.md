---
title: Instalowanie środowiska uruchomieniowego platformy .NET Core w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do uruchamiania aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a41bbdf5419585f06773583dbe82ab0d84ebaa4c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157639"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="b3a50-104">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="b3a50-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="b3a50-105">W tym artykule dowiesz się, jak pobrać i zainstalować środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3a50-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="b3a50-106">Środowisko uruchomieniowe platformy .NET Core służy do uruchamiania aplikacji utworzonych za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3a50-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="b3a50-107">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="b3a50-107">Install with an installer</span></span>

<span data-ttu-id="b3a50-108">System Windows ma autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="b3a50-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="b3a50-109">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="b3a50-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="b3a50-110">Procesory x86 (32-bitowe)</span><span class="sxs-lookup"><span data-stu-id="b3a50-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="b3a50-111">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="b3a50-111">Install with an installer</span></span>

<span data-ttu-id="b3a50-112">macOS ma autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="b3a50-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="b3a50-113">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="b3a50-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="b3a50-114">Pobierz i ręcznie zainstaluj</span><span class="sxs-lookup"><span data-stu-id="b3a50-114">Download and manually install</span></span>

<span data-ttu-id="b3a50-115">Jako alternatywę dla instalatorów macOS dla platformy .NET Core można pobrać i ręcznie zainstalować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="b3a50-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="b3a50-116">Aby zainstalować środowisko uruchomieniowe i włączyć interfejs wiersza polecenia platformy .NET Core polecenia dostępne w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3a50-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="b3a50-117">Następnie otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="b3a50-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="b3a50-118">Przyjęto założenie, że środowisko uruchomieniowe jest pobierane do pliku `~/Downloads/dotnet-runtime.pkg`.</span><span class="sxs-lookup"><span data-stu-id="b3a50-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="b3a50-119">Instalowanie przy użyciu Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="b3a50-119">Install with a package manager</span></span>

<span data-ttu-id="b3a50-120">Środowisko uruchomieniowe platformy .NET Core można zainstalować przy użyciu wielu popularnych menedżerów pakietów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b3a50-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="b3a50-121">Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — Instalowanie programu .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="b3a50-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="b3a50-122">Instalacja za pomocą Menedżera pakietów jest obsługiwana tylko w architekturze x64.</span><span class="sxs-lookup"><span data-stu-id="b3a50-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="b3a50-123">Jeśli instalujesz środowisko uruchomieniowe platformy .NET Core z inną architekturą, taką jak ARM, postępuj zgodnie z instrukcjami w sekcji [pobieranie i ręczne instalowanie](#download-and-manually-install) .</span><span class="sxs-lookup"><span data-stu-id="b3a50-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="b3a50-124">Aby uzyskać więcej informacji o obsługiwanych architekturach, zobacz temat [zależności i wymagania dotyczące platformy .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="b3a50-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="b3a50-125">Pobierz i ręcznie zainstaluj</span><span class="sxs-lookup"><span data-stu-id="b3a50-125">Download and manually install</span></span>

<span data-ttu-id="b3a50-126">Aby wyodrębnić środowisko uruchomieniowe i udostępnić interfejs wiersza polecenia platformy .NET Core polecenia w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3a50-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="b3a50-127">Następnie otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="b3a50-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="b3a50-128">Poprzednie polecenia `export` powodują, że interfejs wiersza polecenia platformy .NET Core polecenia dostępne dla sesji terminalu, w której został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="b3a50-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="b3a50-129">Możesz edytować profil powłoki, aby trwale dodać polecenia.</span><span class="sxs-lookup"><span data-stu-id="b3a50-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="b3a50-130">Istnieje wiele różnych powłok dostępnych dla systemu Linux, a każdy z nich ma inny profil.</span><span class="sxs-lookup"><span data-stu-id="b3a50-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="b3a50-131">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b3a50-131">For example:</span></span>
>
> - <span data-ttu-id="b3a50-132">**Bash Shell**: *~/. bash_profile*, *~/.bashrc.*</span><span class="sxs-lookup"><span data-stu-id="b3a50-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="b3a50-133">**Powłoka Korn**: *~/.KSHRC* lub *. profile*</span><span class="sxs-lookup"><span data-stu-id="b3a50-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="b3a50-134">**Powłoka Z**: *~/.zshrc* lub *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="b3a50-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="b3a50-135">Edytuj odpowiedni plik źródłowy dla powłoki i Dodaj `:$HOME/dotnet` na końcu istniejącej instrukcji `PATH`.</span><span class="sxs-lookup"><span data-stu-id="b3a50-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="b3a50-136">Jeśli nie dołączono żadnej instrukcji `PATH`, Dodaj nowy wiersz z `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="b3a50-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="b3a50-137">Ponadto Dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="b3a50-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="b3a50-138">Takie podejście umożliwia zainstalowanie różnych wersji w oddzielnych lokalizacjach i wybór jawny, który ma być używany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="b3a50-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="b3a50-139">Instalowanie przy użyciu programu PowerShell Automation</span><span class="sxs-lookup"><span data-stu-id="b3a50-139">Install with PowerShell automation</span></span>

<span data-ttu-id="b3a50-140">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b3a50-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="b3a50-141">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="b3a50-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="b3a50-142">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="b3a50-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="b3a50-143">Możesz wybrać określoną wersję, określając przełącznik `Channel`.</span><span class="sxs-lookup"><span data-stu-id="b3a50-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="b3a50-144">Dołącz przełącznik `Runtime`, aby zainstalować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="b3a50-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="b3a50-145">W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b3a50-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="b3a50-146">Powyższe polecenie instaluje środowisko uruchomieniowe ASP.NET Core, aby uzyskać maksymalną zgodność.</span><span class="sxs-lookup"><span data-stu-id="b3a50-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="b3a50-147">Środowisko uruchomieniowe ASP.NET Core obejmuje również standardowe środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3a50-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="b3a50-148">Pobierz i ręcznie zainstaluj</span><span class="sxs-lookup"><span data-stu-id="b3a50-148">Download and manually install</span></span>

<span data-ttu-id="b3a50-149">Aby wyodrębnić środowisko uruchomieniowe i udostępnić interfejs wiersza polecenia platformy .NET Core polecenia w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3a50-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="b3a50-150">Następnie Utwórz katalog, na którym chcesz zainstalować program, na przykład `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="b3a50-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="b3a50-151">Na koniec Wyodrębnij pobrany plik zip do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="b3a50-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="b3a50-152">Domyślnie interfejs wiersza polecenia platformy .NET Core polecenia i aplikacje nie będą używać platformy .NET Core w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="b3a50-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="b3a50-153">Musisz jawnie wybrać tę opcję, aby jej używać.</span><span class="sxs-lookup"><span data-stu-id="b3a50-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="b3a50-154">W tym celu Zmień zmienne środowiskowe, z którymi aplikacja jest uruchomiona:</span><span class="sxs-lookup"><span data-stu-id="b3a50-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="b3a50-155">Takie podejście umożliwia zainstalowanie wielu wersji w oddzielnych lokalizacjach, a następnie jawne wybranie lokalizacji instalacji, która ma być używana przez aplikację, uruchamiając aplikację ze zmiennymi środowiskowymi wskazującymi w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="b3a50-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="b3a50-156">Nawet jeśli są ustawione te zmienne środowiskowe, program .NET Core nadal uznaje domyślną lokalizację instalacji globalnej podczas wybierania najlepszej platformy do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3a50-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="b3a50-157">Wartość domyślna to zwykle `C:\Program Files\dotnet`, których instalatorzy używają.</span><span class="sxs-lookup"><span data-stu-id="b3a50-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="b3a50-158">Można wydać instrukcje środowiska uruchomieniowego, aby używać niestandardowej lokalizacji instalacji przez ustawienie tej zmiennej środowiskowej również:</span><span class="sxs-lookup"><span data-stu-id="b3a50-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="b3a50-159">Instalowanie przy użyciu usługi Bash Automation</span><span class="sxs-lookup"><span data-stu-id="b3a50-159">Install with bash automation</span></span>

<span data-ttu-id="b3a50-160">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b3a50-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="b3a50-161">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="b3a50-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="b3a50-162">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="b3a50-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="b3a50-163">Możesz wybrać określoną wersję, określając przełącznik `current`.</span><span class="sxs-lookup"><span data-stu-id="b3a50-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="b3a50-164">Dołącz przełącznik `runtime`, aby zainstalować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="b3a50-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="b3a50-165">W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b3a50-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="b3a50-166">Powyższe polecenie instaluje środowisko uruchomieniowe ASP.NET Core, aby uzyskać maksymalną zgodność.</span><span class="sxs-lookup"><span data-stu-id="b3a50-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="b3a50-167">Środowisko uruchomieniowe ASP.NET Core obejmuje również standardowe środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3a50-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="b3a50-168">Wszystkie pliki do pobrania z platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="b3a50-168">All .NET Core downloads</span></span>

<span data-ttu-id="b3a50-169">Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="b3a50-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="b3a50-170">Pliki do pobrania w programie .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b3a50-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="b3a50-171">Pliki do pobrania w programie .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="b3a50-171">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="b3a50-172">Pliki do pobrania w programie .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="b3a50-172">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="b3a50-173">Pliki do pobrania w programie .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="b3a50-173">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="b3a50-174">Docker</span><span class="sxs-lookup"><span data-stu-id="b3a50-174">Docker</span></span>

<span data-ttu-id="b3a50-175">Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="b3a50-175">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="b3a50-176">Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3a50-176">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="b3a50-177">Środowisko .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b3a50-177">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="b3a50-178">Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="b3a50-178">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="b3a50-179">Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="b3a50-179">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="b3a50-180">Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="b3a50-180">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="b3a50-181">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="b3a50-181">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="b3a50-182">Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="b3a50-182">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b3a50-183">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b3a50-183">Next steps</span></span>

- <span data-ttu-id="b3a50-184">[Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b3a50-184">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
