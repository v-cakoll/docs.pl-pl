---
title: Instalowanie środowiska uruchomieniowego .NET Core w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować program .NET Core w systemach Windows, Linux i macOS. Odnajdowanie zależności wymaganych do uruchamiania aplikacji .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399015"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="628f3-104">Instalowanie programu runowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="628f3-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="628f3-105">W tym artykule dowiesz się, jak pobrać i zainstalować program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="628f3-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="628f3-106">Czas uruchomieniowy .NET Core służy do uruchamiania aplikacji utworzonych za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="628f3-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="628f3-107">Instalacja z instalatorem</span><span class="sxs-lookup"><span data-stu-id="628f3-107">Install with an installer</span></span>

<span data-ttu-id="628f3-108">System Windows ma autonomiczne instalatory, za których można zainstalować środowisko uruchomieniowe .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="628f3-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="628f3-109">x64 (64-bitowe) procesory</span><span class="sxs-lookup"><span data-stu-id="628f3-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="628f3-110">x86 (32-bitowe) procesory</span><span class="sxs-lookup"><span data-stu-id="628f3-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="628f3-111">Instalacja z instalatorem</span><span class="sxs-lookup"><span data-stu-id="628f3-111">Install with an installer</span></span>

<span data-ttu-id="628f3-112">System macOS ma autonomiczne instalatory, za których można zainstalować program .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="628f3-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="628f3-113">x64 (64-bitowe) procesory</span><span class="sxs-lookup"><span data-stu-id="628f3-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="628f3-114">Pobieranie i ręczne instalowanie</span><span class="sxs-lookup"><span data-stu-id="628f3-114">Download and manually install</span></span>

<span data-ttu-id="628f3-115">Jako alternatywę dla instalatorów systemu macOS dla platformy .NET Core można pobrać i ręcznie zainstalować program runtime.</span><span class="sxs-lookup"><span data-stu-id="628f3-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="628f3-116">Aby zainstalować program runtime i włączyć polecenia cli .NET Core dostępne na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core.</span><span class="sxs-lookup"><span data-stu-id="628f3-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="628f3-117">Następnie otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="628f3-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="628f3-118">Zakłada się, że czas wykonywania `~/Downloads/dotnet-runtime.pkg` jest pobierany do pliku.</span><span class="sxs-lookup"><span data-stu-id="628f3-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="628f3-119">Instalowanie za pomocą menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="628f3-119">Install with a package manager</span></span>

<span data-ttu-id="628f3-120">Program .NET Core Runtime można zainstalować z wieloma typowymi menedżerami pakietów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="628f3-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="628f3-121">Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — instalowanie programu .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="628f3-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="628f3-122">Instalowanie go za pomocą menedżera pakietów jest obsługiwane tylko w architekturze x64.</span><span class="sxs-lookup"><span data-stu-id="628f3-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="628f3-123">Jeśli instalujesz program .NET Core Runtime o innej architekturze, takiej jak ARM, postępuj zgodnie z instrukcjami w sekcji [Pobieranie i instaluj ręcznie.](#download-and-manually-install)</span><span class="sxs-lookup"><span data-stu-id="628f3-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="628f3-124">Aby uzyskać więcej informacji na temat obsługiwanych architektur, zobacz [zależności i wymagania programu .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="628f3-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="628f3-125">Pobieranie i ręczne instalowanie</span><span class="sxs-lookup"><span data-stu-id="628f3-125">Download and manually install</span></span>

<span data-ttu-id="628f3-126">Aby wyodrębnić czas wykonywania i udostępnić polecenia wiersza polecenia .NET Core na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core.</span><span class="sxs-lookup"><span data-stu-id="628f3-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="628f3-127">Następnie otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="628f3-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="628f3-128">Poprzednie `export` polecenia udostępniają tylko polecenia cli .NET Core dla sesji terminala, w której została ona uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="628f3-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="628f3-129">Profil powłoki można edytować, aby trwale dodawać polecenia.</span><span class="sxs-lookup"><span data-stu-id="628f3-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="628f3-130">Istnieje wiele różnych powłok dostępnych dla Linuksa i każdy ma inny profil.</span><span class="sxs-lookup"><span data-stu-id="628f3-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="628f3-131">Przykład:</span><span class="sxs-lookup"><span data-stu-id="628f3-131">For example:</span></span>
>
> - <span data-ttu-id="628f3-132">**Powłoka Bash**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="628f3-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="628f3-133">**Korn Shell**: *~/.kshrc* lub *.profile*</span><span class="sxs-lookup"><span data-stu-id="628f3-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="628f3-134">**Z Powłoka**: *~/.zshrc* lub *.zprofil*</span><span class="sxs-lookup"><span data-stu-id="628f3-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="628f3-135">Edytowanie odpowiedniego pliku źródłowego dla `:$HOME/dotnet` powłoki i `PATH` dodanie na końcu istniejącej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="628f3-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="628f3-136">Jeśli `PATH` instrukcja nie jest dołączona, dodaj nowy wiersz z . `export PATH=$PATH:$HOME/dotnet`</span><span class="sxs-lookup"><span data-stu-id="628f3-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="628f3-137">Ponadto dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="628f3-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="628f3-138">Takie podejście umożliwia instalowanie różnych wersji w oddzielnych lokalizacjach i jawnie wybrać, który z nich do użycia przez którą aplikację.</span><span class="sxs-lookup"><span data-stu-id="628f3-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="628f3-139">Instalacja za pomocą automatyzacji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="628f3-139">Install with PowerShell automation</span></span>

<span data-ttu-id="628f3-140">[Skrypty dotnet-install](../tools/dotnet-install-script.md) są używane do automatyzacji i instalacji innych niż administrator w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="628f3-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="628f3-141">Skrypt można pobrać ze [strony referencyjnej skryptu dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="628f3-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="628f3-142">Skrypt domyślnie instaluje najnowszą wersję [obsługi długoterminowej (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) która jest .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="628f3-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="628f3-143">Można wybrać określoną wersję, określając `Channel` przełącznik.</span><span class="sxs-lookup"><span data-stu-id="628f3-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="628f3-144">Dołącz `Runtime` przełącznik, aby zainstalować czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="628f3-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="628f3-145">W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="628f3-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="628f3-146">Powyższe polecenie instaluje ASP.NET core'u w celu zapewnienia maksymalnej zgodności.</span><span class="sxs-lookup"><span data-stu-id="628f3-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="628f3-147">ASP.NET Core runtime zawiera również standardowy program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="628f3-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="628f3-148">Pobieranie i ręczne instalowanie</span><span class="sxs-lookup"><span data-stu-id="628f3-148">Download and manually install</span></span>

<span data-ttu-id="628f3-149">Aby wyodrębnić czas wykonywania i udostępnić polecenia wiersza polecenia .NET Core na terminalu, najpierw [pobierz](#all-net-core-downloads) wersję binarną .NET Core.</span><span class="sxs-lookup"><span data-stu-id="628f3-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="628f3-150">Następnie utwórz katalog do zainstalowania `%USERPROFILE%\dotnet`na przykład .</span><span class="sxs-lookup"><span data-stu-id="628f3-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="628f3-151">Na koniec wyodrębnij pobrany plik zip do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="628f3-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="628f3-152">Domyślnie polecenia i aplikacje cli programu .NET Core nie będą używać zainstalowanego w ten sposób programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="628f3-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="628f3-153">Musisz jawnie zdecydować się na jego użycie.</span><span class="sxs-lookup"><span data-stu-id="628f3-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="628f3-154">W tym celu należy zmienić zmienne środowiskowe, z którymi aplikacja jest uruchamiana:</span><span class="sxs-lookup"><span data-stu-id="628f3-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="628f3-155">Takie podejście umożliwia zainstalowanie wielu wersji w oddzielnych lokalizacjach, a następnie jawnie wybrać lokalizację instalacji, której aplikacja powinna używać, uruchamiając aplikację ze zmiennymi środowiskowymi wskazującymi w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="628f3-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="628f3-156">Nawet wtedy, gdy te zmienne środowiskowe są ustawione, .NET Core nadal bierze pod uwagę domyślną globalną lokalizację instalacji podczas wybierania najlepszej struktury do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="628f3-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="628f3-157">Wartością domyślną `C:\Program Files\dotnet`jest zazwyczaj , z której korzystają instalatorzy.</span><span class="sxs-lookup"><span data-stu-id="628f3-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="628f3-158">Środowisko uruchomieniowe można poinstruować, aby używały tylko niestandardowej lokalizacji instalacji, ustawiając również tę zmienną środowiskową:</span><span class="sxs-lookup"><span data-stu-id="628f3-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="628f3-159">Instalacja z automatyzacją bash</span><span class="sxs-lookup"><span data-stu-id="628f3-159">Install with bash automation</span></span>

<span data-ttu-id="628f3-160">[Skrypty dotnet-install](../tools/dotnet-install-script.md) są używane do automatyzacji i instalacji innych niż administrator w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="628f3-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="628f3-161">Skrypt można pobrać ze [strony referencyjnej skryptu dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="628f3-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="628f3-162">Skrypt domyślnie instaluje najnowszą wersję [obsługi długoterminowej (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) która jest .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="628f3-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="628f3-163">Można wybrać określoną wersję, określając `current` przełącznik.</span><span class="sxs-lookup"><span data-stu-id="628f3-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="628f3-164">Dołącz `runtime` przełącznik, aby zainstalować czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="628f3-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="628f3-165">W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="628f3-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="628f3-166">Powyższe polecenie instaluje ASP.NET core'u w celu zapewnienia maksymalnej zgodności.</span><span class="sxs-lookup"><span data-stu-id="628f3-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="628f3-167">ASP.NET Core runtime zawiera również standardowy program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="628f3-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="628f3-168">Wszystkie pliki do pobrania programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="628f3-168">All .NET Core downloads</span></span>

<span data-ttu-id="628f3-169">Program .NET Core można pobrać i zainstalować bezpośrednio za pomocą jednego z następujących łączy:</span><span class="sxs-lookup"><span data-stu-id="628f3-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="628f3-170">Pliki do pobrania programu .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="628f3-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="628f3-171">Pliki do pobrania programu .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="628f3-171">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="628f3-172">Docker</span><span class="sxs-lookup"><span data-stu-id="628f3-172">Docker</span></span>

<span data-ttu-id="628f3-173">Kontenery zapewniają lekki sposób izolowania aplikacji od reszty systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="628f3-173">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="628f3-174">Kontenery na tym samym komputerze współużytkują tylko jądro i używają zasobów podanych do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="628f3-174">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="628f3-175">Program .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="628f3-175">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="628f3-176">Oficjalne obrazy platformy Docker platformy .NET Core są publikowane w rejestrze kontenerów firmy Microsoft (MCR) i można je wykryć w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="628f3-176">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="628f3-177">Każde repozytorium zawiera obrazy dla różnych kombinacji .NET (SDK lub Runtime) i OS, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="628f3-177">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="628f3-178">Firma Microsoft udostępnia obrazy dostosowane do określonych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="628f3-178">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="628f3-179">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy, które są tworzone do uruchamiania ASP.NET aplikacji Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="628f3-179">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="628f3-180">Aby uzyskać więcej informacji na temat używania programu .NET Core w kontenerze platformy Docker, zobacz [Wprowadzenie do platformy .NET i platformy Docker](../docker/introduction.md) oraz [samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="628f3-180">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="628f3-181">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="628f3-181">Next steps</span></span>

- <span data-ttu-id="628f3-182">[Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="628f3-182">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
