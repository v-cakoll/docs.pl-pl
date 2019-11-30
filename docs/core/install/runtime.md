---
title: Instalowanie środowiska uruchomieniowego platformy .NET Core w systemach Windows, Linux i macOS — .NET Core
description: Dowiedz się, jak zainstalować platformę .NET Core w systemach Windows, Linux i macOS. Odkryj zależności wymagane do uruchamiania aplikacji platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: fbe9b9e12dc53d9ab6570299e03f2b0a8868fb53
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567271"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="f406b-104">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="f406b-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="f406b-105">W tym artykule dowiesz się, jak pobrać i zainstalować środowisko uruchomieniowe programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f406b-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="f406b-106">Środowisko uruchomieniowe platformy .NET Core służy do uruchamiania aplikacji utworzonych za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f406b-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="f406b-107">Instalowanie za pomocą Instalatora</span><span class="sxs-lookup"><span data-stu-id="f406b-107">Install with an installer</span></span>

<span data-ttu-id="f406b-108">Zarówno system Windows, jak i macOS mają autonomiczne Instalatory, których można użyć do zainstalowania środowiska uruchomieniowego programu .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="f406b-108">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 runtime.</span></span>

- <span data-ttu-id="f406b-109">Procesory Windows [x64 (64-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [procesora x86 (32-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="f406b-109">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="f406b-110">[procesory macOS x64 (64-bitowe)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="f406b-110">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="f406b-111">Instalowanie przy użyciu Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="f406b-111">Install with a package manager</span></span>

<span data-ttu-id="f406b-112">Środowisko uruchomieniowe platformy .NET Core można zainstalować przy użyciu wielu popularnych menedżerów pakietów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="f406b-112">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="f406b-113">Aby uzyskać więcej informacji, zobacz [Menedżer pakietów systemu Linux — Instalowanie programu .NET Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="f406b-113">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="f406b-114">Instalowanie przy użyciu programu PowerShell Automation</span><span class="sxs-lookup"><span data-stu-id="f406b-114">Install with PowerShell automation</span></span>

<span data-ttu-id="f406b-115">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f406b-115">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="f406b-116">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f406b-116">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f406b-117">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="f406b-117">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="f406b-118">Aby zainstalować bieżącą wersję programu .NET Core (3,0), uruchom skrypt z następującym przełącznikiem:</span><span class="sxs-lookup"><span data-stu-id="f406b-118">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="f406b-119">Instalowanie przy użyciu usługi Bash Automation</span><span class="sxs-lookup"><span data-stu-id="f406b-119">Install with bash automation</span></span>

<span data-ttu-id="f406b-120">[Skrypty programu dotnet-Install](../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji niebędących administratorami środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f406b-120">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="f406b-121">Skrypt można pobrać ze [strony odniesienia do skryptu dotnet-Install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f406b-121">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f406b-122">Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="f406b-122">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="f406b-123">Aby zainstalować bieżącą wersję programu .NET Core (3,0), uruchom skrypt z następującym przełącznikiem:</span><span class="sxs-lookup"><span data-stu-id="f406b-123">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="f406b-124">Wszystkie pliki do pobrania z platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="f406b-124">All .NET Core downloads</span></span>

<span data-ttu-id="f406b-125">Program .NET Core można pobrać i zainstalować bezpośrednio przy użyciu jednego z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="f406b-125">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="f406b-126">Pobieranie z wersji zapoznawczej programu .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="f406b-126">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f406b-127">Pliki do pobrania w programie .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="f406b-127">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="f406b-128">Pliki do pobrania w programie .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="f406b-128">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="f406b-129">Pliki do pobrania w programie .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="f406b-129">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="f406b-130">Docker</span><span class="sxs-lookup"><span data-stu-id="f406b-130">Docker</span></span>

<span data-ttu-id="f406b-131">Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta.</span><span class="sxs-lookup"><span data-stu-id="f406b-131">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="f406b-132">Kontenery na tym samym komputerze udostępniają tylko jądro i używają zasobów przyznanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f406b-132">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="f406b-133">Środowisko .NET Core można uruchomić w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="f406b-133">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="f406b-134">Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="f406b-134">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="f406b-135">Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="f406b-135">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="f406b-136">Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f406b-136">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="f406b-137">Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="f406b-137">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="f406b-138">Aby uzyskać więcej informacji na temat korzystania z platformy .NET Core w kontenerze platformy Docker, zobacz [wprowadzenie do oprogramowania .NET i platformy Docker](../docker/introduction.md) i [przykładów](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="f406b-138">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f406b-139">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f406b-139">Next steps</span></span>

- <span data-ttu-id="f406b-140">[Jak sprawdzić, czy program .NET Core jest już zainstalowany](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="f406b-140">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
