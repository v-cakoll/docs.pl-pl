---
title: Wymagania wstępne dla platformy .NET Core w systemie Linux
description: Obsługiwane wersje systemu Linux i zależności platformy .NET Core, opracowywanie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 0bd3287535ba2c398f6577890d1d39f42a806364
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612228"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="369ca-103">Wymagania wstępne dla platformy .NET Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="369ca-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="369ca-104">W tym artykule przedstawiono zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="369ca-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="369ca-105">Obsługiwane dystrybucje systemu Linux/wersje i zależności, które należy wykonać są stosowane na dwa sposoby tworzenia aplikacji platformy .NET Core w systemie Linux:</span><span class="sxs-lookup"><span data-stu-id="369ca-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="369ca-106">Wiersza polecenia za pomocą ulubionego edytora</span><span class="sxs-lookup"><span data-stu-id="369ca-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="369ca-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="369ca-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="369ca-108">Pakiet .NET Core SDK nie jest wymagana dla środowisk serwerów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="369ca-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="369ca-109">Pakiet środowiska uruchomieniowego .NET Core jest potrzebna w przypadku aplikacji wdrożonych na środowisko produkcyjne.</span><span class="sxs-lookup"><span data-stu-id="369ca-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="369ca-110">Środowisko uruchomieniowe platformy .NET Core jest wdrażana przy użyciu aplikacji jako część wdrożenia niezależna, jednak musi zostać wdrożony jako zależny od struktury aplikacji wdrożona oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="369ca-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="369ca-111">Aby uzyskać więcej informacji na temat typów wdrożeń zależny od struktury, niezależna zobacz [wdrażanie aplikacji .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="369ca-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="369ca-112">Zobacz też [aplikacje dla systemu Linux Self-contained](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) dla szczególnych wytycznych.</span><span class="sxs-lookup"><span data-stu-id="369ca-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="369ca-113">Obsługiwane wersje systemu Linux</span><span class="sxs-lookup"><span data-stu-id="369ca-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="369ca-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="369ca-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="369ca-115">.NET core 2.x traktuje Linux jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="369ca-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="369ca-116">Brak pojedynczej kompilacji systemu Linux (na architektura mikroukładu) obsługiwane dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="369ca-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="369ca-117">Łącza pobierania oraz więcej informacji, zobacz [platformy .NET Core 2.2 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/2.2) lub [platformy .NET Core 2.1 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="369ca-117">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="369ca-118">.NET core 2.x obsługuje poniższe dystrybucje systemu Linux/wersji:</span><span class="sxs-lookup"><span data-stu-id="369ca-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="369ca-119">Red Hat Enterprise Linux 7, 6 - 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="369ca-120">CentOS 7 - 64-bitowy (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="369ca-121">Oracle Linux 7 - 64-bitowy (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="369ca-122">Fedora 28, 27 — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="369ca-123">Debian 9 (64-bitowy, `arm32`), 8.7 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="369ca-124">Ubuntu 18.04 (64-bitowy, `arm32`), 16.04, 14.04 - 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="369ca-125">Linux mennic 18, 17 — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="369ca-126">openSUSE 42.3 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="369ca-127">SUSE Linux Enterprise (SLES) 12 z dodatkiem Service Pack 2 lub nowszego - 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="369ca-128">Firma Alpine Linux 3.7 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="369ca-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="369ca-129">Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) i [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pełną listę platformy .NET Core 2.1 i .NET Core 2.2 obsługiwane systemy operacyjne, dystrybucji i wersji, z obsługuje wersje systemów operacyjnych i łącza zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="369ca-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="369ca-130">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="369ca-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="369ca-131">Łącza pobierania oraz więcej informacji, zobacz [pobiera .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) lub [platformy .NET Core 1.0 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="369ca-131">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="369ca-132">.NET core 1.x jest obsługiwane na następujących Linux 64-bitowych (`x86_64` lub `amd64`) dystrybucje/wersji:</span><span class="sxs-lookup"><span data-stu-id="369ca-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="369ca-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="369ca-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="369ca-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="369ca-134">CentOS 7</span></span>
* <span data-ttu-id="369ca-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="369ca-135">Oracle Linux 7</span></span>
* <span data-ttu-id="369ca-136">Fedora 28 (.NET Core 1.1), 27</span><span class="sxs-lookup"><span data-stu-id="369ca-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="369ca-137">Debian 8.2 lub nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="369ca-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="369ca-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="369ca-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="369ca-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="369ca-139">Linux Mint 17</span></span>
* <span data-ttu-id="369ca-140">openSUSE 42.3 lub nowszej wersji (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="369ca-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="369ca-141">Zobacz [obsługiwanych wersjach systemu operacyjnego programu .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) kompletną listę platformy .NET Core 1.x obsługiwane systemy operacyjne, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="369ca-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="369ca-142">.NET core 3.0 w wersji zapoznawczej 1</span><span class="sxs-lookup"><span data-stu-id="369ca-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="369ca-143">.NET core 3.0 w wersji zapoznawczej 1 traktuje systemu Linux jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="369ca-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="369ca-144">Brak pojedynczej kompilacji systemu Linux (na architektura mikroukładu) obsługiwane dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="369ca-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="369ca-145">Łącza pobierania oraz więcej informacji, zobacz [.NET Core 3.0 to pliki do pobrania](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="369ca-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="369ca-146">.NET core 3.0 w wersji zapoznawczej 1 jest obsługiwane na poniższe dystrybucje systemu Linux/wersje.</span><span class="sxs-lookup"><span data-stu-id="369ca-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="369ca-147">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="369ca-147">OS</span></span>                            | <span data-ttu-id="369ca-148">Wersja</span><span class="sxs-lookup"><span data-stu-id="369ca-148">Version</span></span>               | <span data-ttu-id="369ca-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="369ca-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="369ca-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="369ca-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="369ca-151">6</span><span class="sxs-lookup"><span data-stu-id="369ca-151">6</span></span>                     | <span data-ttu-id="369ca-152">X64</span><span class="sxs-lookup"><span data-stu-id="369ca-152">x64</span></span>
<span data-ttu-id="369ca-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="369ca-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="369ca-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="369ca-154">CentOS</span></span><br><span data-ttu-id="369ca-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="369ca-155">Oracle Linux</span></span>  | <span data-ttu-id="369ca-156">7</span><span class="sxs-lookup"><span data-stu-id="369ca-156">7</span></span>                     | <span data-ttu-id="369ca-157">X64</span><span class="sxs-lookup"><span data-stu-id="369ca-157">x64</span></span>
<span data-ttu-id="369ca-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="369ca-158">Fedora</span></span>                        | <span data-ttu-id="369ca-159">28</span><span class="sxs-lookup"><span data-stu-id="369ca-159">28</span></span>                    | <span data-ttu-id="369ca-160">X64</span><span class="sxs-lookup"><span data-stu-id="369ca-160">x64</span></span>
<span data-ttu-id="369ca-161">Debian</span><span class="sxs-lookup"><span data-stu-id="369ca-161">Debian</span></span>                        | <span data-ttu-id="369ca-162">9</span><span class="sxs-lookup"><span data-stu-id="369ca-162">9</span></span>                     | <span data-ttu-id="369ca-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="369ca-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="369ca-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="369ca-164">Ubuntu</span></span>                        | <span data-ttu-id="369ca-165">16.04+, 18.04+</span><span class="sxs-lookup"><span data-stu-id="369ca-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="369ca-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="369ca-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="369ca-167">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="369ca-167">Linux Mint</span></span>                    | <span data-ttu-id="369ca-168">18</span><span class="sxs-lookup"><span data-stu-id="369ca-168">18</span></span>                    | <span data-ttu-id="369ca-169">X64</span><span class="sxs-lookup"><span data-stu-id="369ca-169">x64</span></span>
<span data-ttu-id="369ca-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="369ca-170">openSUSE</span></span>                      | <span data-ttu-id="369ca-171">42.3+</span><span class="sxs-lookup"><span data-stu-id="369ca-171">42.3+</span></span>                 | <span data-ttu-id="369ca-172">X64</span><span class="sxs-lookup"><span data-stu-id="369ca-172">x64</span></span>
<span data-ttu-id="369ca-173">SUSE Linux Enterprise (SLES)</span><span class="sxs-lookup"><span data-stu-id="369ca-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="369ca-174">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="369ca-174">12 SP2+</span></span>               | <span data-ttu-id="369ca-175">X64</span><span class="sxs-lookup"><span data-stu-id="369ca-175">x64</span></span>
<span data-ttu-id="369ca-176">Firma Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="369ca-176">Alpine Linux</span></span>                  | <span data-ttu-id="369ca-177">3.8+</span><span class="sxs-lookup"><span data-stu-id="369ca-177">3.8+</span></span>                  | <span data-ttu-id="369ca-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="369ca-178">x64, ARM64</span></span>

<span data-ttu-id="369ca-179">\* Obsługa ARM32 i ARM64 rozpoczyna się od Debian 9 i Ubuntu 16.04.</span><span class="sxs-lookup"><span data-stu-id="369ca-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="369ca-180">Wcześniejszych wersjach te dystrybucje nie są obsługiwane na mikroukładami ARM.</span><span class="sxs-lookup"><span data-stu-id="369ca-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="369ca-181">Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .NET Core 3.0 to pełna lista obsługiwanych systemów operacyjnych, dystrybucji i wersji poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="369ca-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="369ca-182">Aby uzyskać więcej informacji o sposobie instalowania programu .NET Core 3.0 dla procesorów ARM64, zobacz [instalowanie platformy .NET Core 3.0 dla procesorów Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="369ca-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="369ca-183">Zależności do dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="369ca-183">Linux distribution dependencies</span></span>

<span data-ttu-id="369ca-184">Poniżej mają być przykłady.</span><span class="sxs-lookup"><span data-stu-id="369ca-184">The following are intended to be examples.</span></span> <span data-ttu-id="369ca-185">Na wybranej dystrybucji systemu Linux, nazwy i wersje dokładny mogą się nieco różnić.</span><span class="sxs-lookup"><span data-stu-id="369ca-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="369ca-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="369ca-186">Ubuntu</span></span>

<span data-ttu-id="369ca-187">Dystrybucje systemu Ubuntu wymagają następujących bibliotek zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="369ca-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="369ca-188">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="369ca-188">liblttng-ust0</span></span>
* <span data-ttu-id="369ca-189">libcurl3 (dla 14.x i 16.x)</span><span class="sxs-lookup"><span data-stu-id="369ca-189">libcurl3 (for 14.x and 16.x)</span></span>
* <span data-ttu-id="369ca-190">libcurl4 (w przypadku 18.x)</span><span class="sxs-lookup"><span data-stu-id="369ca-190">libcurl4 (for 18.x)</span></span>
* <span data-ttu-id="369ca-191">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="369ca-191">libssl1.0.0</span></span>
* <span data-ttu-id="369ca-192">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="369ca-192">libkrb5-3</span></span>
* <span data-ttu-id="369ca-193">zlib1g</span><span class="sxs-lookup"><span data-stu-id="369ca-193">zlib1g</span></span>
* <span data-ttu-id="369ca-194">libicu52 (w przypadku 14.x)</span><span class="sxs-lookup"><span data-stu-id="369ca-194">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="369ca-195">libicu55 (w przypadku 16.x)</span><span class="sxs-lookup"><span data-stu-id="369ca-195">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="369ca-196">libicu57 (w przypadku 17.x)</span><span class="sxs-lookup"><span data-stu-id="369ca-196">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="369ca-197">libicu60 (w przypadku 18.x)</span><span class="sxs-lookup"><span data-stu-id="369ca-197">libicu60 (for 18.x)</span></span>

<span data-ttu-id="369ca-198">W wersjach wcześniejszych niż .NET Core 2.1, następujące zależności wymagane są również:</span><span class="sxs-lookup"><span data-stu-id="369ca-198">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="369ca-199">libunwind8</span><span class="sxs-lookup"><span data-stu-id="369ca-199">libunwind8</span></span>
* <span data-ttu-id="369ca-200">libuuid1</span><span class="sxs-lookup"><span data-stu-id="369ca-200">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="369ca-201">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="369ca-201">CentOS and Fedora</span></span>

<span data-ttu-id="369ca-202">Dystrybucje centOS wymagają następujących bibliotek zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="369ca-202">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="369ca-203">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="369ca-203">lttng-ust</span></span>
* <span data-ttu-id="369ca-204">libcurl</span><span class="sxs-lookup"><span data-stu-id="369ca-204">libcurl</span></span>
* <span data-ttu-id="369ca-205">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="369ca-205">openssl-libs</span></span>
* <span data-ttu-id="369ca-206">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="369ca-206">krb5-libs</span></span>
* <span data-ttu-id="369ca-207">libicu</span><span class="sxs-lookup"><span data-stu-id="369ca-207">libicu</span></span>
* <span data-ttu-id="369ca-208">zlib</span><span class="sxs-lookup"><span data-stu-id="369ca-208">zlib</span></span>

<span data-ttu-id="369ca-209">Użytkownicy fedora: Jeśli Twoje openssl wersji > = 1.1, musisz zainstalować openssl10 zgodności.</span><span class="sxs-lookup"><span data-stu-id="369ca-209">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="369ca-210">W wersjach wcześniejszych niż .NET Core 2.1, następujące zależności wymagane są również:</span><span class="sxs-lookup"><span data-stu-id="369ca-210">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="369ca-211">libunwind</span><span class="sxs-lookup"><span data-stu-id="369ca-211">libunwind</span></span>
* <span data-ttu-id="369ca-212">libuuid</span><span class="sxs-lookup"><span data-stu-id="369ca-212">libuuid</span></span>

<span data-ttu-id="369ca-213">Aby uzyskać więcej informacji o zależnościach, zobacz [aplikacje dla systemu Linux Self-contained](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="369ca-213">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="369ca-214">Instalacja zależności platformy .NET Core z natywnych instalatorów</span><span class="sxs-lookup"><span data-stu-id="369ca-214">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="369ca-215">.NET core, który natywnych instalatorów są dostępne dla obsługiwane wersje dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="369ca-215">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="369ca-216">Natywnych instalatorów wymaga dostępu administratora ("sudo") do serwera.</span><span class="sxs-lookup"><span data-stu-id="369ca-216">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="369ca-217">Zalet za pomocą natywnego Instalatora jest, że są zainstalowane wszystkie zależności natywnego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="369ca-217">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="369ca-218">Natywnych instalatorów także zainstalować całego systemu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="369ca-218">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="369ca-219">W systemie Linux istnieją dwie opcje pakiet Instalatora:</span><span class="sxs-lookup"><span data-stu-id="369ca-219">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="369ca-220">Przy użyciu Menedżera pakietów na podstawie źródła danych, takich jak polecenia apt-get dla systemu Ubuntu lub yum na CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="369ca-220">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="369ca-221">Za pomocą pakietów, Mistrzostwo DEB lub obr. / min.</span><span class="sxs-lookup"><span data-stu-id="369ca-221">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="369ca-222">Skrypty instalacji przy użyciu skryptu Instalatora platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="369ca-222">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="369ca-223">[Skryptów instalacji dotnet](./tools/dotnet-install-script.md) są używane do wykonywania instalacji bez uprawnień administratora, łańcuch narzędzi interfejsu wiersza polecenia i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="369ca-223">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="369ca-224">Możesz pobrać skrypt z <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="369ca-224">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="369ca-225">Domyślnie skrypt zainstalowanie najnowszej wersji "LTS", która jest obecnie .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="369ca-225">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="369ca-226">Aby zainstalować program .NET Core 2.1, uruchom skrypt przy użyciu następującego przełącznika:</span><span class="sxs-lookup"><span data-stu-id="369ca-226">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="369ca-227">Skrypt powłoki bash Instalatora jest używany w scenariuszach automatyzacji oraz przed instalacjami bez uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="369ca-227">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="369ca-228">Ten skrypt odczytuje również przełączników programu PowerShell, dzięki czemu może być używany ze skryptem w systemach Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="369ca-228">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="369ca-229">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="369ca-229">Troubleshoot</span></span>

<span data-ttu-id="369ca-230">Jeśli masz problemy z instalacją .NET Core w obsługiwanych dystrybucji systemu Linux/wersji dla Twojej dystrybucji zainstalowanych/wersji należy zapoznać się następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="369ca-230">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="369ca-231">.NET core 3.0 to znane problemy</span><span class="sxs-lookup"><span data-stu-id="369ca-231">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="369ca-232">.NET core 2.2 znane problemy</span><span class="sxs-lookup"><span data-stu-id="369ca-232">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="369ca-233">Znane problemy dotyczące programu .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="369ca-233">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="369ca-234">Znane problemy dotyczące programu .NET core 1.1</span><span class="sxs-lookup"><span data-stu-id="369ca-234">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="369ca-235">Znane problemy dotyczące programu .NET core 1.0</span><span class="sxs-lookup"><span data-stu-id="369ca-235">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
