---
title: Instalowanie środowiska uruchomieniowego platformy .NET Core w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do uruchamiania aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: c079e1856cdd370a278efc6fdfb4953059b6f2ba
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596296"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="f2d17-104">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="f2d17-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="f2d17-105">W tym artykule dowiesz się, jak pobrać i zainstalować środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2d17-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="f2d17-106">Środowisko uruchomieniowe platformy .NET Core służy do uruchamiania aplikacji utworzonych za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2d17-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="f2d17-107">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="f2d17-107">Install with an installer</span></span>

<span data-ttu-id="f2d17-108">System Windows ma autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="f2d17-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="f2d17-109">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="f2d17-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f2d17-110">Procesory x86 (32-bitowe)</span><span class="sxs-lookup"><span data-stu-id="f2d17-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="f2d17-111">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="f2d17-111">Install with an installer</span></span>

<span data-ttu-id="f2d17-112">macOS ma autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="f2d17-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="f2d17-113">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="f2d17-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="f2d17-114">Pobierz i ręcznie zainstaluj</span><span class="sxs-lookup"><span data-stu-id="f2d17-114">Download and manually install</span></span>

<span data-ttu-id="f2d17-115">Jako alternatywę dla instalatorów macOS dla platformy .NET Core można pobrać i ręcznie zainstalować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="f2d17-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="f2d17-116">Aby zainstalować środowisko uruchomieniowe i włączyć interfejs wiersza polecenia platformy .NET Core polecenia dostępne w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2d17-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="f2d17-117">Następnie otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="f2d17-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="f2d17-118">Przyjęto założenie, że środowisko uruchomieniowe jest pobierane do `~/Downloads/dotnet-runtime.pkg` pliku.</span><span class="sxs-lookup"><span data-stu-id="f2d17-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="f2d17-119">Instalowanie w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="f2d17-119">Install on Linux</span></span>

<span data-ttu-id="f2d17-120">Ten artykuł zostanie wkrótce usunięty.</span><span class="sxs-lookup"><span data-stu-id="f2d17-120">This article will be removed soon.</span></span> <span data-ttu-id="f2d17-121">Jest ona zastępowana przez [zainstalowanie platformy .NET Core w systemie Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="f2d17-121">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="f2d17-122">Instalowanie przy użyciu programu PowerShell Automation</span><span class="sxs-lookup"><span data-stu-id="f2d17-122">Install with PowerShell automation</span></span>

<span data-ttu-id="f2d17-123">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f2d17-123">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="f2d17-124">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f2d17-124">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f2d17-125">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="f2d17-125">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="f2d17-126">Możesz wybrać określoną wersję, określając `Channel` przełącznik.</span><span class="sxs-lookup"><span data-stu-id="f2d17-126">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="f2d17-127">Dołącz `Runtime` przełącznik, aby zainstalować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="f2d17-127">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="f2d17-128">W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="f2d17-128">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="f2d17-129">Powyższe polecenie instaluje środowisko uruchomieniowe ASP.NET Core, aby uzyskać maksymalną zgodność.</span><span class="sxs-lookup"><span data-stu-id="f2d17-129">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="f2d17-130">Środowisko uruchomieniowe ASP.NET Core obejmuje również standardowe środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2d17-130">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="f2d17-131">Pobierz i ręcznie zainstaluj</span><span class="sxs-lookup"><span data-stu-id="f2d17-131">Download and manually install</span></span>

<span data-ttu-id="f2d17-132">Aby wyodrębnić środowisko uruchomieniowe i udostępnić interfejs wiersza polecenia platformy .NET Core polecenia w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2d17-132">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="f2d17-133">Następnie Utwórz katalog do zainstalowania na przykład `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="f2d17-133">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="f2d17-134">Na koniec Wyodrębnij pobrany plik zip do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f2d17-134">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="f2d17-135">Domyślnie interfejs wiersza polecenia platformy .NET Core polecenia i aplikacje nie będą używać platformy .NET Core w ten sposób i musisz jawnie wybrać jej użycie.</span><span class="sxs-lookup"><span data-stu-id="f2d17-135">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="f2d17-136">W tym celu Zmień zmienne środowiskowe, z którymi aplikacja jest uruchomiona:</span><span class="sxs-lookup"><span data-stu-id="f2d17-136">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="f2d17-137">Takie podejście umożliwia zainstalowanie wielu wersji w oddzielnych lokalizacjach, a następnie jawne wybranie lokalizacji instalacji, która ma być używana przez aplikację, uruchamiając aplikację ze zmiennymi środowiskowymi wskazującymi w tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="f2d17-137">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="f2d17-138">Nawet jeśli są ustawione te zmienne środowiskowe, program .NET Core nadal uznaje domyślną lokalizację instalacji globalnej podczas wybierania najlepszej platformy do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2d17-138">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="f2d17-139">Wartość domyślna to zwykle `C:\Program Files\dotnet` , których instalatorzy używają.</span><span class="sxs-lookup"><span data-stu-id="f2d17-139">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="f2d17-140">Można wydać instrukcje środowiska uruchomieniowego, aby używać niestandardowej lokalizacji instalacji przez ustawienie tej zmiennej środowiskowej również:</span><span class="sxs-lookup"><span data-stu-id="f2d17-140">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="f2d17-141">Instalowanie przy użyciu usługi Bash Automation</span><span class="sxs-lookup"><span data-stu-id="f2d17-141">Install with bash automation</span></span>

<span data-ttu-id="f2d17-142">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f2d17-142">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="f2d17-143">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f2d17-143">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f2d17-144">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="f2d17-144">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="f2d17-145">Możesz wybrać określoną wersję, określając `current` przełącznik.</span><span class="sxs-lookup"><span data-stu-id="f2d17-145">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="f2d17-146">Dołącz `runtime` przełącznik, aby zainstalować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="f2d17-146">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="f2d17-147">W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="f2d17-147">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="f2d17-148">Powyższe polecenie instaluje środowisko uruchomieniowe ASP.NET Core, aby uzyskać maksymalną zgodność.</span><span class="sxs-lookup"><span data-stu-id="f2d17-148">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="f2d17-149">Środowisko uruchomieniowe ASP.NET Core obejmuje również standardowe środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2d17-149">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="f2d17-150">Wszystkie pliki do pobrania z platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="f2d17-150">All .NET Core downloads</span></span>

<span data-ttu-id="f2d17-151">Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="f2d17-151">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="f2d17-152">Pliki do pobrania w programie .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="f2d17-152">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f2d17-153">Pliki do pobrania w programie .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="f2d17-153">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="f2d17-154">Docker</span><span class="sxs-lookup"><span data-stu-id="f2d17-154">Docker</span></span>

<span data-ttu-id="f2d17-155">Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="f2d17-155">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="f2d17-156">Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2d17-156">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="f2d17-157">Środowisko .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="f2d17-157">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="f2d17-158">Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="f2d17-158">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="f2d17-159">Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="f2d17-159">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="f2d17-160">Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f2d17-160">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="f2d17-161">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="f2d17-161">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="f2d17-162">Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="f2d17-162">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2d17-163">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f2d17-163">Next steps</span></span>

- <span data-ttu-id="f2d17-164">[Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="f2d17-164">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
