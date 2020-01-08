---
title: Instalowanie środowiska uruchomieniowego platformy .NET Core w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do uruchamiania aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a45cb570ccf572a699359598319fd3867fb5e5dd
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340957"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="690ca-104">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="690ca-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="690ca-105">W tym artykule dowiesz się, jak pobrać i zainstalować środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="690ca-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="690ca-106">Środowisko uruchomieniowe platformy .NET Core służy do uruchamiania aplikacji utworzonych za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="690ca-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="690ca-107">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="690ca-107">Install with an installer</span></span>

<span data-ttu-id="690ca-108">System Windows ma autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="690ca-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="690ca-109">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="690ca-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="690ca-110">Procesory x86 (32-bitowe)</span><span class="sxs-lookup"><span data-stu-id="690ca-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="690ca-111">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="690ca-111">Install with an installer</span></span>

<span data-ttu-id="690ca-112">macOS ma autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="690ca-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="690ca-113">Procesory x64 (64-bitowe)</span><span class="sxs-lookup"><span data-stu-id="690ca-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="690ca-114">Instalowanie przy użyciu Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="690ca-114">Install with a package manager</span></span>

<span data-ttu-id="690ca-115">Środowisko uruchomieniowe platformy .NET Core można zainstalować przy użyciu wielu popularnych menedżerów pakietów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="690ca-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="690ca-116">Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — Instalowanie programu .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="690ca-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="690ca-117">Instalacja za pomocą Menedżera pakietów jest obsługiwana tylko w architekturze x64.</span><span class="sxs-lookup"><span data-stu-id="690ca-117">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="690ca-118">Jeśli instalujesz środowisko uruchomieniowe platformy .NET Core z inną architekturą, taką jak ARM, postępuj zgodnie z instrukcjami w sekcji [pobieranie i ręczne instalowanie](#download-and-manually-install) .</span><span class="sxs-lookup"><span data-stu-id="690ca-118">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="690ca-119">Aby uzyskać więcej informacji o obsługiwanych architekturach, zobacz temat [zależności i wymagania dotyczące platformy .NET Core](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="690ca-119">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="690ca-120">Pobierz i ręcznie zainstaluj</span><span class="sxs-lookup"><span data-stu-id="690ca-120">Download and manually install</span></span>

<span data-ttu-id="690ca-121">Aby wyodrębnić środowisko uruchomieniowe i udostępnić interfejs wiersza polecenia platformy .NET Core polecenia w terminalu, należy najpierw [pobrać](#all-net-core-downloads) wydanie binarne platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="690ca-121">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="690ca-122">Następnie otwórz Terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="690ca-122">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="690ca-123">Poprzednie polecenia `export` powodują, że interfejs wiersza polecenia platformy .NET Core polecenia dostępne dla sesji terminalu, w której został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="690ca-123">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="690ca-124">Możesz edytować profil powłoki, aby trwale dodać polecenia.</span><span class="sxs-lookup"><span data-stu-id="690ca-124">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="690ca-125">Istnieje wiele różnych powłok dostępnych dla systemu Linux, a każdy z nich ma inny profil.</span><span class="sxs-lookup"><span data-stu-id="690ca-125">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="690ca-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="690ca-126">For example:</span></span>
>
> - <span data-ttu-id="690ca-127">**Bash Shell**: *~/. bash_profile*, *~/.bashrc.*</span><span class="sxs-lookup"><span data-stu-id="690ca-127">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="690ca-128">**Powłoka Korn**: *~/.KSHRC* lub *. profile*</span><span class="sxs-lookup"><span data-stu-id="690ca-128">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="690ca-129">**Powłoka Z**: *~/.zshrc* lub *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="690ca-129">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="690ca-130">Edytuj odpowiedni plik źródłowy dla powłoki i Dodaj `:$HOME/dotnet` na końcu istniejącej instrukcji `PATH`.</span><span class="sxs-lookup"><span data-stu-id="690ca-130">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="690ca-131">Jeśli nie dołączono żadnej instrukcji `PATH`, Dodaj nowy wiersz z `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="690ca-131">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="690ca-132">Ponadto Dodaj `export DOTNET_ROOT=$HOME/dotnet` na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="690ca-132">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="690ca-133">Instalowanie przy użyciu programu PowerShell Automation</span><span class="sxs-lookup"><span data-stu-id="690ca-133">Install with PowerShell automation</span></span>

<span data-ttu-id="690ca-134">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="690ca-134">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="690ca-135">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="690ca-135">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="690ca-136">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="690ca-136">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="690ca-137">Możesz wybrać określoną wersję, określając przełącznik `Channel`.</span><span class="sxs-lookup"><span data-stu-id="690ca-137">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="690ca-138">Dołącz przełącznik `Runtime`, aby zainstalować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="690ca-138">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="690ca-139">W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="690ca-139">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="690ca-140">Powyższe polecenie instaluje środowisko uruchomieniowe ASP.NET Core, aby uzyskać maksymalną zgodność.</span><span class="sxs-lookup"><span data-stu-id="690ca-140">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="690ca-141">Środowisko uruchomieniowe ASP.NET Core obejmuje również standardowe środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="690ca-141">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="690ca-142">Instalowanie przy użyciu usługi Bash Automation</span><span class="sxs-lookup"><span data-stu-id="690ca-142">Install with bash automation</span></span>

<span data-ttu-id="690ca-143">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="690ca-143">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="690ca-144">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="690ca-144">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="690ca-145">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="690ca-145">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="690ca-146">Możesz wybrać określoną wersję, określając przełącznik `current`.</span><span class="sxs-lookup"><span data-stu-id="690ca-146">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="690ca-147">Dołącz przełącznik `runtime`, aby zainstalować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="690ca-147">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="690ca-148">W przeciwnym razie skrypt instaluje [zestaw SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="690ca-148">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="690ca-149">Powyższe polecenie instaluje środowisko uruchomieniowe ASP.NET Core, aby uzyskać maksymalną zgodność.</span><span class="sxs-lookup"><span data-stu-id="690ca-149">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="690ca-150">Środowisko uruchomieniowe ASP.NET Core obejmuje również standardowe środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="690ca-150">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="690ca-151">Wszystkie pliki do pobrania z platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="690ca-151">All .NET Core downloads</span></span>

<span data-ttu-id="690ca-152">Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="690ca-152">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="690ca-153">Pliki do pobrania w programie .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="690ca-153">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="690ca-154">Pliki do pobrania w programie .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="690ca-154">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="690ca-155">Pliki do pobrania w programie .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="690ca-155">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="690ca-156">Pliki do pobrania w programie .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="690ca-156">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="690ca-157">Docker</span><span class="sxs-lookup"><span data-stu-id="690ca-157">Docker</span></span>

<span data-ttu-id="690ca-158">Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="690ca-158">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="690ca-159">Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="690ca-159">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="690ca-160">Środowisko .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="690ca-160">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="690ca-161">Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="690ca-161">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="690ca-162">Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="690ca-162">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="690ca-163">Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="690ca-163">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="690ca-164">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="690ca-164">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="690ca-165">Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="690ca-165">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="690ca-166">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="690ca-166">Next steps</span></span>

- <span data-ttu-id="690ca-167">[Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="690ca-167">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
