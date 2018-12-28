---
title: Wymagania wstępne dla platformy .NET Core w systemie Linux
description: Obsługiwane wersje systemu Linux i zależności platformy .NET Core, opracowywanie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 7a2b0b3af97500ab0988e5de7a44713a8c05ccb9
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656053"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="8d76a-103">Wymagania wstępne dla platformy .NET Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="8d76a-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="8d76a-104">W tym artykule przedstawiono zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="8d76a-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="8d76a-105">Obsługiwane dystrybucje systemu Linux/wersje i zależności, które należy wykonać są stosowane na dwa sposoby tworzenia aplikacji platformy .NET Core w systemie Linux:</span><span class="sxs-lookup"><span data-stu-id="8d76a-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="8d76a-106">Wiersza polecenia za pomocą ulubionego edytora</span><span class="sxs-lookup"><span data-stu-id="8d76a-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="8d76a-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8d76a-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="8d76a-108">Pakiet .NET Core SDK nie jest wymagana dla środowisk serwerów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="8d76a-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="8d76a-109">Pakiet środowiska uruchomieniowego .NET Core jest potrzebna w przypadku aplikacji wdrożonych na środowisko produkcyjne.</span><span class="sxs-lookup"><span data-stu-id="8d76a-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="8d76a-110">Środowisko uruchomieniowe platformy .NET Core jest wdrażana przy użyciu aplikacji jako część wdrożenia niezależna, jednak musi zostać wdrożony jako zależny od struktury aplikacji wdrożona oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="8d76a-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="8d76a-111">Aby uzyskać więcej informacji na temat typów wdrożeń zależny od struktury, niezależna zobacz [wdrażanie aplikacji .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d76a-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="8d76a-112">Zobacz też [aplikacje dla systemu Linux Self-contained](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) dla szczególnych wytycznych.</span><span class="sxs-lookup"><span data-stu-id="8d76a-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="8d76a-113">Obsługiwane wersje systemu Linux</span><span class="sxs-lookup"><span data-stu-id="8d76a-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8d76a-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8d76a-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="8d76a-115">.NET core 2.x traktuje Linux jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="8d76a-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="8d76a-116">Brak pojedynczej kompilacji systemu Linux (na architektura mikroukładu) obsługiwane dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="8d76a-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="8d76a-117">Łącza pobierania oraz więcej informacji, zobacz [platformy .NET Core 2.2 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/2.2) lub [platformy .NET Core 2.1 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="8d76a-117">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="8d76a-118">.NET core 2.x obsługuje poniższe dystrybucje systemu Linux/wersji:</span><span class="sxs-lookup"><span data-stu-id="8d76a-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="8d76a-119">Red Hat Enterprise Linux 7, 6 - 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8d76a-120">CentOS 7 - 64-bitowy (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="8d76a-121">Oracle Linux 7 - 64-bitowy (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="8d76a-122">Fedora 28, 27 — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="8d76a-123">Debian 9 (64-bitowy, `arm32`), 8.7 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8d76a-124">Ubuntu 18.04 (64-bitowy, `arm32`), 16.04, 14.04 - 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8d76a-125">Linux mennic 18, 17 — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8d76a-126">openSUSE 42.3 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8d76a-127">SUSE Linux Enterprise (SLES) 12 z dodatkiem Service Pack 2 lub nowszego - 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8d76a-128">Firma Alpine Linux 3.7 lub nowsze wersje — 64-bitowych (`x86_64` lub `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8d76a-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="8d76a-129">Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) i [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pełną listę platformy .NET Core 2.1 i .NET Core 2.2 obsługiwane systemy operacyjne, dystrybucji i wersji, z obsługuje wersje systemów operacyjnych i łącza zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="8d76a-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8d76a-130">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8d76a-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8d76a-131">Łącza pobierania oraz więcej informacji, zobacz [pobiera .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) lub [platformy .NET Core 1.0 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="8d76a-131">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="8d76a-132">.NET core 1.x jest obsługiwane na następujących Linux 64-bitowych (`x86_64` lub `amd64`) dystrybucje/wersji:</span><span class="sxs-lookup"><span data-stu-id="8d76a-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="8d76a-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="8d76a-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="8d76a-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="8d76a-134">CentOS 7</span></span>
* <span data-ttu-id="8d76a-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="8d76a-135">Oracle Linux 7</span></span>
* <span data-ttu-id="8d76a-136">Fedora 28 (.NET Core 1.1) 27</span><span class="sxs-lookup"><span data-stu-id="8d76a-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="8d76a-137">Debian 8.2 lub nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="8d76a-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="8d76a-138">18.04 (.NET Core 1.1), Ubuntu 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="8d76a-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="8d76a-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="8d76a-139">Linux Mint 17</span></span>
* <span data-ttu-id="8d76a-140">openSUSE 42.3 lub nowszej wersji (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="8d76a-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="8d76a-141">Zobacz [obsługiwanych wersjach systemu operacyjnego programu .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) kompletną listę platformy .NET Core 1.x obsługiwane systemy operacyjne, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="8d76a-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="8d76a-142">.NET core 3.0 w wersji zapoznawczej 1</span><span class="sxs-lookup"><span data-stu-id="8d76a-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="8d76a-143">.NET core 3.0 w wersji zapoznawczej 1 traktuje systemu Linux jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="8d76a-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="8d76a-144">Brak pojedynczej kompilacji systemu Linux (na architektura mikroukładu) obsługiwane dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="8d76a-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="8d76a-145">Łącza pobierania oraz więcej informacji, zobacz [.NET Core 3.0 to pliki do pobrania](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="8d76a-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="8d76a-146">.NET core 3.0 w wersji zapoznawczej 1 jest obsługiwane na poniższe dystrybucje systemu Linux/wersje.</span><span class="sxs-lookup"><span data-stu-id="8d76a-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="8d76a-147">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="8d76a-147">OS</span></span>                            | <span data-ttu-id="8d76a-148">Wersja</span><span class="sxs-lookup"><span data-stu-id="8d76a-148">Version</span></span>               | <span data-ttu-id="8d76a-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="8d76a-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="8d76a-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="8d76a-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="8d76a-151">6</span><span class="sxs-lookup"><span data-stu-id="8d76a-151">6</span></span>                     | <span data-ttu-id="8d76a-152">X64</span><span class="sxs-lookup"><span data-stu-id="8d76a-152">x64</span></span>
<span data-ttu-id="8d76a-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="8d76a-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="8d76a-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="8d76a-154">CentOS</span></span><br><span data-ttu-id="8d76a-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="8d76a-155">Oracle Linux</span></span>  | <span data-ttu-id="8d76a-156">7</span><span class="sxs-lookup"><span data-stu-id="8d76a-156">7</span></span>                     | <span data-ttu-id="8d76a-157">X64</span><span class="sxs-lookup"><span data-stu-id="8d76a-157">x64</span></span>
<span data-ttu-id="8d76a-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="8d76a-158">Fedora</span></span>                        | <span data-ttu-id="8d76a-159">28</span><span class="sxs-lookup"><span data-stu-id="8d76a-159">28</span></span>                    | <span data-ttu-id="8d76a-160">X64</span><span class="sxs-lookup"><span data-stu-id="8d76a-160">x64</span></span>
<span data-ttu-id="8d76a-161">Debian</span><span class="sxs-lookup"><span data-stu-id="8d76a-161">Debian</span></span>                        | <span data-ttu-id="8d76a-162">9</span><span class="sxs-lookup"><span data-stu-id="8d76a-162">9</span></span>                     | <span data-ttu-id="8d76a-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="8d76a-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="8d76a-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8d76a-164">Ubuntu</span></span>                        | <span data-ttu-id="8d76a-165">16.04 +, 18.04 +</span><span class="sxs-lookup"><span data-stu-id="8d76a-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="8d76a-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="8d76a-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="8d76a-167">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="8d76a-167">Linux Mint</span></span>                    | <span data-ttu-id="8d76a-168">18</span><span class="sxs-lookup"><span data-stu-id="8d76a-168">18</span></span>                    | <span data-ttu-id="8d76a-169">X64</span><span class="sxs-lookup"><span data-stu-id="8d76a-169">x64</span></span>
<span data-ttu-id="8d76a-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="8d76a-170">openSUSE</span></span>                      | <span data-ttu-id="8d76a-171">42.3 +</span><span class="sxs-lookup"><span data-stu-id="8d76a-171">42.3+</span></span>                 | <span data-ttu-id="8d76a-172">X64</span><span class="sxs-lookup"><span data-stu-id="8d76a-172">x64</span></span>
<span data-ttu-id="8d76a-173">SUSE Linux Enterprise (SLES)</span><span class="sxs-lookup"><span data-stu-id="8d76a-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="8d76a-174">12 Z DODATKIEM SP2 +</span><span class="sxs-lookup"><span data-stu-id="8d76a-174">12 SP2+</span></span>               | <span data-ttu-id="8d76a-175">X64</span><span class="sxs-lookup"><span data-stu-id="8d76a-175">x64</span></span>
<span data-ttu-id="8d76a-176">Firma Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="8d76a-176">Alpine Linux</span></span>                  | <span data-ttu-id="8d76a-177">3.8 +</span><span class="sxs-lookup"><span data-stu-id="8d76a-177">3.8+</span></span>                  | <span data-ttu-id="8d76a-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="8d76a-178">x64, ARM64</span></span>

<span data-ttu-id="8d76a-179">\* Obsługa ARM32 i ARM64 rozpoczyna się od Debian 9 i Ubuntu 16.04.</span><span class="sxs-lookup"><span data-stu-id="8d76a-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="8d76a-180">Wcześniejszych wersjach te dystrybucje nie są obsługiwane na mikroukładami ARM.</span><span class="sxs-lookup"><span data-stu-id="8d76a-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="8d76a-181">Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .NET Core 3.0 to pełna lista obsługiwanych systemów operacyjnych, dystrybucji i wersji poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="8d76a-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="8d76a-182">Aby uzyskać więcej informacji o sposobie instalowania programu .NET Core 3.0 dla procesorów ARM64, zobacz [instalowanie platformy .NET Core 3.0 dla procesorów Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="8d76a-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>



---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="8d76a-183">Zależności do dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="8d76a-183">Linux distribution dependencies</span></span>

<span data-ttu-id="8d76a-184">Poniżej mają być przykłady.</span><span class="sxs-lookup"><span data-stu-id="8d76a-184">The following are intended to be examples.</span></span> <span data-ttu-id="8d76a-185">Na wybranej dystrybucji systemu Linux, nazwy i wersje dokładny mogą się nieco różnić.</span><span class="sxs-lookup"><span data-stu-id="8d76a-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="8d76a-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8d76a-186">Ubuntu</span></span>

<span data-ttu-id="8d76a-187">Dystrybucje systemu Ubuntu wymagają następujących bibliotek zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="8d76a-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="8d76a-188">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="8d76a-188">liblttng-ust0</span></span>
* <span data-ttu-id="8d76a-189">libcurl3</span><span class="sxs-lookup"><span data-stu-id="8d76a-189">libcurl3</span></span>
* <span data-ttu-id="8d76a-190">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="8d76a-190">libssl1.0.0</span></span>
* <span data-ttu-id="8d76a-191">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="8d76a-191">libkrb5-3</span></span>
* <span data-ttu-id="8d76a-192">zlib1g</span><span class="sxs-lookup"><span data-stu-id="8d76a-192">zlib1g</span></span>
* <span data-ttu-id="8d76a-193">libicu52 (w przypadku 14.x)</span><span class="sxs-lookup"><span data-stu-id="8d76a-193">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="8d76a-194">libicu55 (w przypadku 16.x)</span><span class="sxs-lookup"><span data-stu-id="8d76a-194">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="8d76a-195">libicu57 (w przypadku 17.x)</span><span class="sxs-lookup"><span data-stu-id="8d76a-195">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="8d76a-196">libicu60 (w przypadku 18.x)</span><span class="sxs-lookup"><span data-stu-id="8d76a-196">libicu60 (for 18.x)</span></span>

<span data-ttu-id="8d76a-197">W wersjach wcześniejszych niż .NET Core 2.1, następujące zależności wymagane są również:</span><span class="sxs-lookup"><span data-stu-id="8d76a-197">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="8d76a-198">libunwind8</span><span class="sxs-lookup"><span data-stu-id="8d76a-198">libunwind8</span></span>
* <span data-ttu-id="8d76a-199">libuuid1</span><span class="sxs-lookup"><span data-stu-id="8d76a-199">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="8d76a-200">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="8d76a-200">CentOS and Fedora</span></span>

<span data-ttu-id="8d76a-201">Dystrybucje centOS wymagają następujących bibliotek zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="8d76a-201">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="8d76a-202">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="8d76a-202">lttng-ust</span></span>
* <span data-ttu-id="8d76a-203">libcurl</span><span class="sxs-lookup"><span data-stu-id="8d76a-203">libcurl</span></span>
* <span data-ttu-id="8d76a-204">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="8d76a-204">openssl-libs</span></span>
* <span data-ttu-id="8d76a-205">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="8d76a-205">krb5-libs</span></span>
* <span data-ttu-id="8d76a-206">libicu</span><span class="sxs-lookup"><span data-stu-id="8d76a-206">libicu</span></span>
* <span data-ttu-id="8d76a-207">zlib</span><span class="sxs-lookup"><span data-stu-id="8d76a-207">zlib</span></span>

<span data-ttu-id="8d76a-208">Użytkownicy fedora: Jeśli Twoje openssl wersji > = 1.1, musisz zainstalować openssl10 zgodności.</span><span class="sxs-lookup"><span data-stu-id="8d76a-208">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="8d76a-209">W wersjach wcześniejszych niż .NET Core 2.1, następujące zależności wymagane są również:</span><span class="sxs-lookup"><span data-stu-id="8d76a-209">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="8d76a-210">libunwind</span><span class="sxs-lookup"><span data-stu-id="8d76a-210">libunwind</span></span>
* <span data-ttu-id="8d76a-211">libuuid</span><span class="sxs-lookup"><span data-stu-id="8d76a-211">libuuid</span></span>

<span data-ttu-id="8d76a-212">Aby uzyskać więcej informacji o zależnościach, zobacz [aplikacje dla systemu Linux Self-contained](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="8d76a-212">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="8d76a-213">Instalacja zależności platformy .NET Core z natywnych instalatorów</span><span class="sxs-lookup"><span data-stu-id="8d76a-213">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="8d76a-214">.NET core, który natywnych instalatorów są dostępne dla obsługiwane wersje dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="8d76a-214">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="8d76a-215">Natywnych instalatorów wymaga dostępu administratora ("sudo") do serwera.</span><span class="sxs-lookup"><span data-stu-id="8d76a-215">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="8d76a-216">Zalet za pomocą natywnego Instalatora jest, że są zainstalowane wszystkie zależności natywnego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d76a-216">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="8d76a-217">Natywnych instalatorów także zainstalować całego systemu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8d76a-217">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="8d76a-218">W systemie Linux istnieją dwie opcje pakiet Instalatora:</span><span class="sxs-lookup"><span data-stu-id="8d76a-218">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="8d76a-219">Przy użyciu Menedżera pakietów na podstawie źródła danych, takich jak polecenia apt-get dla systemu Ubuntu lub yum na CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="8d76a-219">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="8d76a-220">Za pomocą pakietów, Mistrzostwo DEB lub obr. / min.</span><span class="sxs-lookup"><span data-stu-id="8d76a-220">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="8d76a-221">Skrypty instalacji przy użyciu skryptu Instalatora platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="8d76a-221">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="8d76a-222">[Skryptów instalacji dotnet](./tools/dotnet-install-script.md) są używane do wykonywania instalacji bez uprawnień administratora, łańcuch narzędzi interfejsu wiersza polecenia i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8d76a-222">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="8d76a-223">Możesz pobrać skrypt z [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).</span><span class="sxs-lookup"><span data-stu-id="8d76a-223">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="8d76a-224">Domyślnie skrypt zainstalowanie najnowszej wersji "LTS", która jest obecnie .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="8d76a-224">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="8d76a-225">Aby zainstalować program .NET Core 2.1, uruchom skrypt przy użyciu następującego przełącznika:</span><span class="sxs-lookup"><span data-stu-id="8d76a-225">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="8d76a-226">Skrypt powłoki bash Instalatora jest używany w scenariuszach automatyzacji oraz przed instalacjami bez uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="8d76a-226">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="8d76a-227">Ten skrypt odczytuje również przełączników programu PowerShell, dzięki czemu może być używany ze skryptem w systemach Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="8d76a-227">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="8d76a-228">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="8d76a-228">Troubleshoot</span></span>

<span data-ttu-id="8d76a-229">Jeśli masz problemy z instalacją .NET Core w obsługiwanych dystrybucji systemu Linux/wersji dla Twojej dystrybucji zainstalowanych/wersji należy zapoznać się następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="8d76a-229">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="8d76a-230">.NET core 3.0 to znane problemy</span><span class="sxs-lookup"><span data-stu-id="8d76a-230">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="8d76a-231">.NET core 2.2 znane problemy</span><span class="sxs-lookup"><span data-stu-id="8d76a-231">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="8d76a-232">Znane problemy dotyczące programu .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="8d76a-232">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="8d76a-233">Znane problemy dotyczące programu .NET core 1.1</span><span class="sxs-lookup"><span data-stu-id="8d76a-233">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="8d76a-234">Znane problemy dotyczące programu .NET core 1.0</span><span class="sxs-lookup"><span data-stu-id="8d76a-234">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
