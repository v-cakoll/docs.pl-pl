---
title: Wymagania wstępne dotyczące programu .NET Core w systemie Linux
description: Obsługiwane wersje systemów Linux i .NET Core umożliwiają tworzenie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 31c53b2cc0fe576e56685f4a5561258136fd2541
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116586"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="634a7-103">Wymagania wstępne dotyczące programu .NET Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="634a7-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="634a7-104">W tym artykule przedstawiono zależności, które są konieczne do tworzenia aplikacji .NET Core w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="634a7-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="634a7-105">Obsługiwane dystrybucje i wersje systemu Linux oraz następujące zależności dotyczą dwóch sposobów tworzenia aplikacji platformy .NET Core w systemie Linux:</span><span class="sxs-lookup"><span data-stu-id="634a7-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="634a7-106">Wiersz polecenia z ulubionym edytorem</span><span class="sxs-lookup"><span data-stu-id="634a7-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="634a7-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="634a7-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="634a7-108">Pakiet zestaw .NET Core SDK nie jest wymagany w przypadku serwerów produkcyjnych/środowisk.</span><span class="sxs-lookup"><span data-stu-id="634a7-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="634a7-109">W przypadku aplikacji wdrożonych w środowiskach produkcyjnych wymagany jest tylko pakiet środowiska uruchomieniowego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="634a7-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="634a7-110">Środowisko uruchomieniowe platformy .NET Core jest wdrażane z użyciem aplikacji w ramach wdrożenia samodzielnego, jednak należy je wdrożyć osobno dla wdrożonych aplikacji zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="634a7-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="634a7-111">Aby uzyskać więcej informacji na temat typów wdrożeń zależnych od platformy i samodzielnych, zobacz [wdrażanie aplikacji .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="634a7-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="634a7-112">Zobacz również [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) dla określonych wytycznych.</span><span class="sxs-lookup"><span data-stu-id="634a7-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="634a7-113">Obsługiwane wersje systemu Linux</span><span class="sxs-lookup"><span data-stu-id="634a7-113">Supported Linux versions</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="634a7-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="634a7-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="634a7-115">Program .NET Core 2. x traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="634a7-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="634a7-116">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="634a7-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="634a7-117">Aby uzyskać linki do pobrania i więcej informacji, zobacz pliki do pobrania w [programie .net core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) lub w [programie .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="634a7-117">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="634a7-118">Platforma .NET Core 2. x jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="634a7-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="634a7-119">Red Hat Enterprise Linux 7, 6-64-bitowy (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="634a7-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="634a7-120">CentOS 7-64-bit (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="634a7-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="634a7-121">Oracle Linux 7-64-bitowy (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="634a7-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="634a7-122">Fedora 28, 27-64-bitowy (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="634a7-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="634a7-123">Debian 9 (64-bitowy, `arm32`), 8,7 i nowsze wersje — 64-bit (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="634a7-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="634a7-124">Ubuntu 18,04 (64-bit, `arm32`), 16,04, 14,04-64-bit (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="634a7-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="634a7-125">Linux mennic 18, 17-64-bitowy (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="634a7-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="634a7-126">openSUSE 42,3 lub nowszy — 64-bitowy (`x86_64` lub) `amd64`</span><span class="sxs-lookup"><span data-stu-id="634a7-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="634a7-127">SUSE Enterprise Linux (SLES) 12 z dodatkiem Service Pack 2 lub nowszym — 64`x86_64` - `amd64`bitowy (lub)</span><span class="sxs-lookup"><span data-stu-id="634a7-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="634a7-128">System Alpine Linux 3,7 lub nowszy — 64-bitowy (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="634a7-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="634a7-129">Zobacz obsługiwane wersje systemu operacyjnego .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) i [obsługiwane wersje systemu operacyjnego .NET Core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) , aby zapoznać się z pełną listą systemów operacyjnych .NET Core 2,1 i .NET Core 2,2 Obsługiwane systemy operacyjne, dystrybucje i wersje, nieobsługiwane wersje systemu operacyjnego i zasady cyklu życia linki.</span><span class="sxs-lookup"><span data-stu-id="634a7-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="634a7-130">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="634a7-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="634a7-131">Aby uzyskać linki do pobrania i więcej informacji, zobacz pliki do pobrania w [programie .net core 1,1](https://dotnet.microsoft.com/download/dotnet-core/1.1) lub w [programie .NET Core 1,0](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="634a7-131">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="634a7-132">Platforma .NET Core 1. x jest obsługiwana w następujących dystrybucjach/wersjach systemu`x86_64` Linux `amd64`64-bit (lub):</span><span class="sxs-lookup"><span data-stu-id="634a7-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="634a7-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="634a7-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="634a7-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="634a7-134">CentOS 7</span></span>
* <span data-ttu-id="634a7-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="634a7-135">Oracle Linux 7</span></span>
* <span data-ttu-id="634a7-136">Fedora 28 (.NET Core 1.1), 27</span><span class="sxs-lookup"><span data-stu-id="634a7-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="634a7-137">Debian 8,2 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="634a7-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="634a7-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="634a7-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="634a7-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="634a7-139">Linux Mint 17</span></span>
* <span data-ttu-id="634a7-140">openSUSE 42,3 lub nowsza (.NET Core 1,1)</span><span class="sxs-lookup"><span data-stu-id="634a7-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="634a7-141">Zobacz [obsługiwane wersje systemu operacyjnego na platformie .NET Core 1. x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych .NET Core 1. x, wersje systemu operacyjnego i linki do zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="634a7-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="634a7-142">.NET Core 3,0 — wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="634a7-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="634a7-143">Program .NET Core 3,0 w wersji zapoznawczej 1 traktuje system Linux jako pojedynczą wersję systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="634a7-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="634a7-144">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="634a7-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="634a7-145">Aby uzyskać linki do pobrania i więcej informacji, zobacz temat [pobieranie z programu .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="634a7-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="634a7-146">Program .NET Core 3,0 wersja zapoznawcza 1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="634a7-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="634a7-147">OS</span><span class="sxs-lookup"><span data-stu-id="634a7-147">OS</span></span>                            | <span data-ttu-id="634a7-148">Wersja</span><span class="sxs-lookup"><span data-stu-id="634a7-148">Version</span></span>               | <span data-ttu-id="634a7-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="634a7-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="634a7-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="634a7-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="634a7-151">6</span><span class="sxs-lookup"><span data-stu-id="634a7-151">6</span></span>                     | <span data-ttu-id="634a7-152">X64</span><span class="sxs-lookup"><span data-stu-id="634a7-152">x64</span></span>
<span data-ttu-id="634a7-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="634a7-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="634a7-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="634a7-154">CentOS</span></span><br><span data-ttu-id="634a7-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="634a7-155">Oracle Linux</span></span>  | <span data-ttu-id="634a7-156">7</span><span class="sxs-lookup"><span data-stu-id="634a7-156">7</span></span>                     | <span data-ttu-id="634a7-157">X64</span><span class="sxs-lookup"><span data-stu-id="634a7-157">x64</span></span>
<span data-ttu-id="634a7-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="634a7-158">Fedora</span></span>                        | <span data-ttu-id="634a7-159">28</span><span class="sxs-lookup"><span data-stu-id="634a7-159">28</span></span>                    | <span data-ttu-id="634a7-160">X64</span><span class="sxs-lookup"><span data-stu-id="634a7-160">x64</span></span>
<span data-ttu-id="634a7-161">Debian</span><span class="sxs-lookup"><span data-stu-id="634a7-161">Debian</span></span>                        | <span data-ttu-id="634a7-162">9</span><span class="sxs-lookup"><span data-stu-id="634a7-162">9</span></span>                     | <span data-ttu-id="634a7-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="634a7-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="634a7-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="634a7-164">Ubuntu</span></span>                        | <span data-ttu-id="634a7-165">16.04 +, 18.04 +</span><span class="sxs-lookup"><span data-stu-id="634a7-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="634a7-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="634a7-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="634a7-167">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="634a7-167">Linux Mint</span></span>                    | <span data-ttu-id="634a7-168">18</span><span class="sxs-lookup"><span data-stu-id="634a7-168">18</span></span>                    | <span data-ttu-id="634a7-169">X64</span><span class="sxs-lookup"><span data-stu-id="634a7-169">x64</span></span>
<span data-ttu-id="634a7-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="634a7-170">openSUSE</span></span>                      | <span data-ttu-id="634a7-171">42.3 +</span><span class="sxs-lookup"><span data-stu-id="634a7-171">42.3+</span></span>                 | <span data-ttu-id="634a7-172">X64</span><span class="sxs-lookup"><span data-stu-id="634a7-172">x64</span></span>
<span data-ttu-id="634a7-173">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="634a7-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="634a7-174">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="634a7-174">12 SP2+</span></span>               | <span data-ttu-id="634a7-175">X64</span><span class="sxs-lookup"><span data-stu-id="634a7-175">x64</span></span>
<span data-ttu-id="634a7-176">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="634a7-176">Alpine Linux</span></span>                  | <span data-ttu-id="634a7-177">3.8 +</span><span class="sxs-lookup"><span data-stu-id="634a7-177">3.8+</span></span>                  | <span data-ttu-id="634a7-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="634a7-178">x64, ARM64</span></span>

<span data-ttu-id="634a7-179">\*Obsługa ARM32 i ARM64 rozpoczyna się od Debian 9 i Ubuntu 16,04.</span><span class="sxs-lookup"><span data-stu-id="634a7-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="634a7-180">Wcześniejsze wersje tych dystrybucje nie są obsługiwane w mikroukładach ARM.</span><span class="sxs-lookup"><span data-stu-id="634a7-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="634a7-181">Zobacz [obsługiwane wersje systemu operacyjnego .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucje i wersje programu .net Core 3,0, wersje systemu operacyjnego i linki do zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="634a7-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="634a7-182">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="634a7-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="634a7-183">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="634a7-183">Linux distribution dependencies</span></span>

<span data-ttu-id="634a7-184">Poniżej przedstawiono przykłady.</span><span class="sxs-lookup"><span data-stu-id="634a7-184">The following are intended to be examples.</span></span> <span data-ttu-id="634a7-185">Dokładne wersje i nazwy mogą się nieco różnić w zależności od wybranej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="634a7-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="634a7-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="634a7-186">Ubuntu</span></span>

<span data-ttu-id="634a7-187">Dystrybucje Ubuntu wymagają zainstalowanych następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="634a7-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="634a7-188">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="634a7-188">liblttng-ust0</span></span>
* <span data-ttu-id="634a7-189">libcurl3 (dla 14. x i 16. x)</span><span class="sxs-lookup"><span data-stu-id="634a7-189">libcurl3 (for 14.x and 16.x)</span></span>
* <span data-ttu-id="634a7-190">libcurl4 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="634a7-190">libcurl4 (for 18.x)</span></span>
* <span data-ttu-id="634a7-191">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="634a7-191">libssl1.0.0</span></span>
* <span data-ttu-id="634a7-192">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="634a7-192">libkrb5-3</span></span>
* <span data-ttu-id="634a7-193">zlib1g</span><span class="sxs-lookup"><span data-stu-id="634a7-193">zlib1g</span></span>
* <span data-ttu-id="634a7-194">libicu52 (dla 14. x)</span><span class="sxs-lookup"><span data-stu-id="634a7-194">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="634a7-195">libicu55 (dla 16. x)</span><span class="sxs-lookup"><span data-stu-id="634a7-195">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="634a7-196">libicu57 (dla 17. x)</span><span class="sxs-lookup"><span data-stu-id="634a7-196">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="634a7-197">libicu60 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="634a7-197">libicu60 (for 18.x)</span></span>

<span data-ttu-id="634a7-198">W przypadku wersji wcześniejszej niż .NET Core 2,1 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="634a7-198">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="634a7-199">libunwind8</span><span class="sxs-lookup"><span data-stu-id="634a7-199">libunwind8</span></span>
* <span data-ttu-id="634a7-200">libuuid1</span><span class="sxs-lookup"><span data-stu-id="634a7-200">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="634a7-201">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="634a7-201">CentOS and Fedora</span></span>

<span data-ttu-id="634a7-202">Dystrybucje CentOS wymagają zainstalowanych następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="634a7-202">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="634a7-203">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="634a7-203">lttng-ust</span></span>
* <span data-ttu-id="634a7-204">libcurl</span><span class="sxs-lookup"><span data-stu-id="634a7-204">libcurl</span></span>
* <span data-ttu-id="634a7-205">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="634a7-205">openssl-libs</span></span>
* <span data-ttu-id="634a7-206">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="634a7-206">krb5-libs</span></span>
* <span data-ttu-id="634a7-207">libicu</span><span class="sxs-lookup"><span data-stu-id="634a7-207">libicu</span></span>
* <span data-ttu-id="634a7-208">zlib</span><span class="sxs-lookup"><span data-stu-id="634a7-208">zlib</span></span>

<span data-ttu-id="634a7-209">Fedora użytkownicy: Jeśli wersja OpenSSL > = 1,1, należy zainstalować polecenie COMPAT-openssl10.</span><span class="sxs-lookup"><span data-stu-id="634a7-209">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="634a7-210">W przypadku wersji wcześniejszej niż .NET Core 2,1 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="634a7-210">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="634a7-211">libunwind</span><span class="sxs-lookup"><span data-stu-id="634a7-211">libunwind</span></span>
* <span data-ttu-id="634a7-212">libuuid</span><span class="sxs-lookup"><span data-stu-id="634a7-212">libuuid</span></span>

<span data-ttu-id="634a7-213">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="634a7-213">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="634a7-214">Instalowanie zależności programu .NET Core z natywnymi instalatorami</span><span class="sxs-lookup"><span data-stu-id="634a7-214">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="634a7-215">Natywne Instalatory platformy .NET Core są dostępne dla obsługiwanych dystrybucji lub wersji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="634a7-215">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="634a7-216">Natywne Instalatory wymagają dostępu administratora (sudo) do serwera programu.</span><span class="sxs-lookup"><span data-stu-id="634a7-216">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="634a7-217">Zaletą korzystania z instalatora natywnego jest to, że wszystkie zależności natywne platformy .NET Core są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="634a7-217">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="634a7-218">Natywne Instalatory również instalują zestaw .NET Core SDK całego systemu.</span><span class="sxs-lookup"><span data-stu-id="634a7-218">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="634a7-219">W systemie Linux dostępne są dwa opcje pakietu Instalatora:</span><span class="sxs-lookup"><span data-stu-id="634a7-219">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="634a7-220">Za pomocą Menedżera pakietów opartych na źródle danych, takiego jak apt-get for Ubuntu lub yum for CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="634a7-220">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="634a7-221">Korzystanie z samych pakietów, DEB lub RPM.</span><span class="sxs-lookup"><span data-stu-id="634a7-221">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="634a7-222">Skrypty są instalowane za pomocą skryptu Instalatora .NET Core</span><span class="sxs-lookup"><span data-stu-id="634a7-222">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="634a7-223">[Skrypty programu dotnet-Install](./tools/dotnet-install-script.md) są używane do przeprowadzania instalacji niebędącej administratorem interfejsu wiersza polecenia łańcucha narzędzi i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="634a7-223">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="634a7-224">Skrypt można pobrać z programu <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="634a7-224">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="634a7-225">Skrypt domyślnie instaluje najnowszą wersję "LTS", która jest obecnie platformą .NET Core 1,1.</span><span class="sxs-lookup"><span data-stu-id="634a7-225">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="634a7-226">Aby zainstalować program .NET Core 2,1, uruchom skrypt z następującym przełącznikiem:</span><span class="sxs-lookup"><span data-stu-id="634a7-226">To install .NET Core 2.1, run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="634a7-227">Skrypt bash Instalatora jest używany w scenariuszach automatyzacji i instalacjach niebędących administratorami.</span><span class="sxs-lookup"><span data-stu-id="634a7-227">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="634a7-228">Ten skrypt odczytuje również przełączniki programu PowerShell, dzięki czemu mogą być używane z skryptem w systemach Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="634a7-228">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="634a7-229">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="634a7-229">Troubleshoot</span></span>

<span data-ttu-id="634a7-230">Jeśli masz problemy z instalacją programu .NET Core w obsługiwanej dystrybucji/wersji systemu Linux, zapoznaj się z następującymi tematami dotyczącymi zainstalowanych dystrybucji/wersji:</span><span class="sxs-lookup"><span data-stu-id="634a7-230">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="634a7-231">Znane problemy dotyczące programu .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="634a7-231">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="634a7-232">Znane problemy dotyczące programu .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="634a7-232">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="634a7-233">Znane problemy dotyczące programu .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="634a7-233">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="634a7-234">Znane problemy dotyczące programu .NET Core 1,1</span><span class="sxs-lookup"><span data-stu-id="634a7-234">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="634a7-235">Znane problemy dotyczące programu .NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="634a7-235">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
