---
title: Zależności zestaw .NET Core SDK i środowiska uruchomieniowego — .NET Core
description: Szczegółowe informacje na temat wymagań wstępnych dotyczących architektury procesora i systemu operacyjnego w celu zainstalowania zestaw .NET Core SDK i środowiska uruchomieniowego w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 11/06/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: b79ec6a9723cbd44717d5f187213278556c0b6ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451102"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="71274-103">Zależności i wymagania dotyczące platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="71274-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="71274-104">W tym artykule szczegółowo przedstawiono systemy operacyjne i architekturę procesora CPU obsługiwane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="71274-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="71274-105">Supported operating systems</span><span class="sxs-lookup"><span data-stu-id="71274-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="71274-106">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="71274-106">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="71274-107">W przypadku programu .NET Core 3,0 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="71274-107">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="71274-108">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="71274-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="71274-109">OS</span><span class="sxs-lookup"><span data-stu-id="71274-109">OS</span></span>                            | <span data-ttu-id="71274-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="71274-110">Version</span></span>                        | <span data-ttu-id="71274-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="71274-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="71274-112">Klient z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="71274-112">Windows Client</span></span>                | <span data-ttu-id="71274-113">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="71274-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="71274-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="71274-114">x64, x86</span></span>        |
| <span data-ttu-id="71274-115">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="71274-115">Windows 10 Client</span></span>             | <span data-ttu-id="71274-116">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="71274-116">Version 1607+</span></span>                  | <span data-ttu-id="71274-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="71274-117">x64, x86</span></span>        |
| <span data-ttu-id="71274-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="71274-118">Windows Server</span></span>                | <span data-ttu-id="71274-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="71274-119">2012 R2+</span></span>                       | <span data-ttu-id="71274-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="71274-120">x64, x86</span></span>        |
| <span data-ttu-id="71274-121">Serwer nano</span><span class="sxs-lookup"><span data-stu-id="71274-121">Nano Server</span></span>                   | <span data-ttu-id="71274-122">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="71274-122">Version 1803+</span></span>                  | <span data-ttu-id="71274-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="71274-123">x64, ARM32</span></span>      |

<span data-ttu-id="71274-124">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="71274-124">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="71274-125">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="71274-125">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="71274-126">W przypadku programu .NET Core 2,2 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="71274-126">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="71274-127">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="71274-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="71274-128">OS</span><span class="sxs-lookup"><span data-stu-id="71274-128">OS</span></span>                            | <span data-ttu-id="71274-129">Wersja</span><span class="sxs-lookup"><span data-stu-id="71274-129">Version</span></span>                        | <span data-ttu-id="71274-130">Architektury</span><span class="sxs-lookup"><span data-stu-id="71274-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="71274-131">Klient z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="71274-131">Windows Client</span></span>                | <span data-ttu-id="71274-132">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="71274-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="71274-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="71274-133">x64, x86</span></span>        |
| <span data-ttu-id="71274-134">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="71274-134">Windows 10 Client</span></span>             | <span data-ttu-id="71274-135">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="71274-135">Version 1607+</span></span>                  | <span data-ttu-id="71274-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="71274-136">x64, x86</span></span>        |
| <span data-ttu-id="71274-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="71274-137">Windows Server</span></span>                | <span data-ttu-id="71274-138">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="71274-138">2008 R2 SP1+</span></span>                   | <span data-ttu-id="71274-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="71274-139">x64, x86</span></span>        |
| <span data-ttu-id="71274-140">Serwer nano</span><span class="sxs-lookup"><span data-stu-id="71274-140">Nano Server</span></span>                   | <span data-ttu-id="71274-141">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="71274-141">Version 1803+</span></span>                   | <span data-ttu-id="71274-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="71274-142">x64, ARM32</span></span>      |

<span data-ttu-id="71274-143">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="71274-143">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="71274-144">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="71274-144">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="71274-145">W przypadku programu .NET Core 2,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="71274-145">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="71274-146">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="71274-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="71274-147">OS</span><span class="sxs-lookup"><span data-stu-id="71274-147">OS</span></span>                            | <span data-ttu-id="71274-148">Wersja</span><span class="sxs-lookup"><span data-stu-id="71274-148">Version</span></span>                        | <span data-ttu-id="71274-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="71274-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="71274-150">Klient z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="71274-150">Windows Client</span></span>                | <span data-ttu-id="71274-151">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="71274-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="71274-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="71274-152">x64, x86</span></span>        |
| <span data-ttu-id="71274-153">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="71274-153">Windows 10 Client</span></span>             | <span data-ttu-id="71274-154">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="71274-154">Version 1607+</span></span>                  | <span data-ttu-id="71274-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="71274-155">x64, x86</span></span>        |
| <span data-ttu-id="71274-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="71274-156">Windows Server</span></span>                | <span data-ttu-id="71274-157">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="71274-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="71274-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="71274-158">x64, x86</span></span>        |
| <span data-ttu-id="71274-159">Serwer nano</span><span class="sxs-lookup"><span data-stu-id="71274-159">Nano Server</span></span>                   | <span data-ttu-id="71274-160">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="71274-160">Version 1803+</span></span>                  | <span data-ttu-id="71274-161">procesorów</span><span class="sxs-lookup"><span data-stu-id="71274-161">x64,</span></span>            |

<span data-ttu-id="71274-162">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="71274-162">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="71274-163">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="71274-163">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="71274-164">Jeśli instalujesz zestaw .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows, wymagane są dodatkowe zależności:</span><span class="sxs-lookup"><span data-stu-id="71274-164">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="71274-165">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="71274-165">Windows 7 SP1</span></span>
- <span data-ttu-id="71274-166">Windows Vista z dodatkiem SP 2</span><span class="sxs-lookup"><span data-stu-id="71274-166">Windows Vista SP 2</span></span>
- <span data-ttu-id="71274-167">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="71274-167">Windows 8.1</span></span>
- <span data-ttu-id="71274-168">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="71274-168">Windows Server 2008 R2</span></span>
- <span data-ttu-id="71274-169">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="71274-169">Windows Server 2012 R2</span></span>

<span data-ttu-id="71274-170">Zainstaluj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="71274-170">Install the following:</span></span>

- <span data-ttu-id="71274-171">Pakiet [redystrybucyjny Microsoft Visual C++ 2015 z aktualizacją Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="71274-171">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="71274-172">POPRAWKI KB2533623</span><span class="sxs-lookup"><span data-stu-id="71274-172">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="71274-173">Powyższe wymagania są również wymagane w przypadku wystąpienia jednego z następujących błędów:</span><span class="sxs-lookup"><span data-stu-id="71274-173">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="71274-174">Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-CRT-Runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="71274-174">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="71274-175">Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="71274-175">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="71274-176">\- lub-</span><span class="sxs-lookup"><span data-stu-id="71274-176">\- or -</span></span>
>
> <span data-ttu-id="71274-177">Znaleziono bibliotekę *hostfxr. dll* , ale ładowanie jej z *dysku C:\\\<path_to_app >\\hostfxr. dll* nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="71274-177">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="71274-178">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="71274-178">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="71274-179">Program .NET Core 3,0 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="71274-179">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="71274-180">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="71274-180">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="71274-181">Platforma .NET Core 3,0 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="71274-181">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="71274-182">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="71274-182">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="71274-183">OS</span><span class="sxs-lookup"><span data-stu-id="71274-183">OS</span></span>                             | <span data-ttu-id="71274-184">Wersja</span><span class="sxs-lookup"><span data-stu-id="71274-184">Version</span></span>               | <span data-ttu-id="71274-185">Architektury</span><span class="sxs-lookup"><span data-stu-id="71274-185">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="71274-186">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="71274-186">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="71274-187">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="71274-187">6, 7, 8</span></span>               | <span data-ttu-id="71274-188">x64</span><span class="sxs-lookup"><span data-stu-id="71274-188">x64</span></span> |
| <span data-ttu-id="71274-189">CentOS</span><span class="sxs-lookup"><span data-stu-id="71274-189">CentOS</span></span>                         | <span data-ttu-id="71274-190">7+</span><span class="sxs-lookup"><span data-stu-id="71274-190">7+</span></span>                    | <span data-ttu-id="71274-191">x64</span><span class="sxs-lookup"><span data-stu-id="71274-191">x64</span></span> |
| <span data-ttu-id="71274-192">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="71274-192">Oracle Linux</span></span>                   | <span data-ttu-id="71274-193">7+</span><span class="sxs-lookup"><span data-stu-id="71274-193">7+</span></span>                    | <span data-ttu-id="71274-194">x64</span><span class="sxs-lookup"><span data-stu-id="71274-194">x64</span></span> |
| <span data-ttu-id="71274-195">Fedora</span><span class="sxs-lookup"><span data-stu-id="71274-195">Fedora</span></span>                         | <span data-ttu-id="71274-196">29 +</span><span class="sxs-lookup"><span data-stu-id="71274-196">29+</span></span>                   | <span data-ttu-id="71274-197">x64</span><span class="sxs-lookup"><span data-stu-id="71274-197">x64</span></span> |
| <span data-ttu-id="71274-198">Debian</span><span class="sxs-lookup"><span data-stu-id="71274-198">Debian</span></span>                         | <span data-ttu-id="71274-199">9+</span><span class="sxs-lookup"><span data-stu-id="71274-199">9+</span></span>                    | <span data-ttu-id="71274-200">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="71274-200">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="71274-201">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="71274-201">Ubuntu</span></span>                         | <span data-ttu-id="71274-202">16.04 +</span><span class="sxs-lookup"><span data-stu-id="71274-202">16.04+</span></span>                | <span data-ttu-id="71274-203">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="71274-203">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="71274-204">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="71274-204">Linux Mint</span></span>                     | <span data-ttu-id="71274-205">18 +</span><span class="sxs-lookup"><span data-stu-id="71274-205">18+</span></span>                   | <span data-ttu-id="71274-206">x64</span><span class="sxs-lookup"><span data-stu-id="71274-206">x64</span></span> |
| <span data-ttu-id="71274-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="71274-207">openSUSE</span></span>                       | <span data-ttu-id="71274-208">15 +</span><span class="sxs-lookup"><span data-stu-id="71274-208">15+</span></span>                   | <span data-ttu-id="71274-209">x64</span><span class="sxs-lookup"><span data-stu-id="71274-209">x64</span></span> |
| <span data-ttu-id="71274-210">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="71274-210">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="71274-211">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="71274-211">12 SP2+</span></span>               | <span data-ttu-id="71274-212">x64</span><span class="sxs-lookup"><span data-stu-id="71274-212">x64</span></span> |
| <span data-ttu-id="71274-213">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="71274-213">Alpine Linux</span></span>                   | <span data-ttu-id="71274-214">3.8 +</span><span class="sxs-lookup"><span data-stu-id="71274-214">3.8+</span></span>                  | <span data-ttu-id="71274-215">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="71274-215">x64, ARM64</span></span> |

<span data-ttu-id="71274-216">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="71274-216">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="71274-217">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="71274-217">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="71274-218">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="71274-218">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="71274-219">Program .NET Core 2,2 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="71274-219">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="71274-220">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="71274-220">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="71274-221">Platforma .NET Core 2,2 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="71274-221">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="71274-222">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="71274-222">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="71274-223">OS</span><span class="sxs-lookup"><span data-stu-id="71274-223">OS</span></span>                             |  <span data-ttu-id="71274-224">Wersja</span><span class="sxs-lookup"><span data-stu-id="71274-224">Version</span></span>                |  <span data-ttu-id="71274-225">Architektury</span><span class="sxs-lookup"><span data-stu-id="71274-225">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="71274-226">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="71274-226">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="71274-227">6, 7</span><span class="sxs-lookup"><span data-stu-id="71274-227">6, 7</span></span>                   | <span data-ttu-id="71274-228">x64</span><span class="sxs-lookup"><span data-stu-id="71274-228">x64</span></span> |
| <span data-ttu-id="71274-229">CentOS</span><span class="sxs-lookup"><span data-stu-id="71274-229">CentOS</span></span>                         |  <span data-ttu-id="71274-230">7</span><span class="sxs-lookup"><span data-stu-id="71274-230">7</span></span>                      | <span data-ttu-id="71274-231">x64</span><span class="sxs-lookup"><span data-stu-id="71274-231">x64</span></span> |
| <span data-ttu-id="71274-232">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="71274-232">Oracle Linux</span></span>                   |  <span data-ttu-id="71274-233">7</span><span class="sxs-lookup"><span data-stu-id="71274-233">7</span></span>                      | <span data-ttu-id="71274-234">x64</span><span class="sxs-lookup"><span data-stu-id="71274-234">x64</span></span> |
| <span data-ttu-id="71274-235">Fedora</span><span class="sxs-lookup"><span data-stu-id="71274-235">Fedora</span></span>                         |  <span data-ttu-id="71274-236">29, 30</span><span class="sxs-lookup"><span data-stu-id="71274-236">29, 30</span></span>                 | <span data-ttu-id="71274-237">x64</span><span class="sxs-lookup"><span data-stu-id="71274-237">x64</span></span> |
| <span data-ttu-id="71274-238">Debian</span><span class="sxs-lookup"><span data-stu-id="71274-238">Debian</span></span>                         |  <span data-ttu-id="71274-239">9</span><span class="sxs-lookup"><span data-stu-id="71274-239">9</span></span>                      | <span data-ttu-id="71274-240">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="71274-240">x64, ARM32</span></span> |
| <span data-ttu-id="71274-241">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="71274-241">Ubuntu</span></span>                         |  <span data-ttu-id="71274-242">16,04, 18,04, 18,10, 19,04</span><span class="sxs-lookup"><span data-stu-id="71274-242">16.04, 18.04, 18.10, 19.04</span></span>    | <span data-ttu-id="71274-243">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="71274-243">x64, ARM32</span></span> |
| <span data-ttu-id="71274-244">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="71274-244">Linux Mint</span></span>                     |  <span data-ttu-id="71274-245">17, 18</span><span class="sxs-lookup"><span data-stu-id="71274-245">17, 18</span></span>                 | <span data-ttu-id="71274-246">x64</span><span class="sxs-lookup"><span data-stu-id="71274-246">x64</span></span> |
| <span data-ttu-id="71274-247">openSUSE</span><span class="sxs-lookup"><span data-stu-id="71274-247">openSUSE</span></span>                       |  <span data-ttu-id="71274-248">15 +</span><span class="sxs-lookup"><span data-stu-id="71274-248">15+</span></span>                    | <span data-ttu-id="71274-249">x64</span><span class="sxs-lookup"><span data-stu-id="71274-249">x64</span></span> |
| <span data-ttu-id="71274-250">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="71274-250">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="71274-251">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="71274-251">12 SP2+</span></span>                | <span data-ttu-id="71274-252">x64</span><span class="sxs-lookup"><span data-stu-id="71274-252">x64</span></span> |
| <span data-ttu-id="71274-253">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="71274-253">Alpine Linux</span></span>                   |  <span data-ttu-id="71274-254">3.8 +</span><span class="sxs-lookup"><span data-stu-id="71274-254">3.8+</span></span>                   | <span data-ttu-id="71274-255">x64</span><span class="sxs-lookup"><span data-stu-id="71274-255">x64</span></span> |

<span data-ttu-id="71274-256">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="71274-256">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="71274-257">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="71274-257">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="71274-258">Program .NET Core 2,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="71274-258">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="71274-259">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="71274-259">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="71274-260">Platforma .NET Core 2,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="71274-260">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="71274-261">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="71274-261">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="71274-262">OS</span><span class="sxs-lookup"><span data-stu-id="71274-262">OS</span></span>                             |  <span data-ttu-id="71274-263">Wersja</span><span class="sxs-lookup"><span data-stu-id="71274-263">Version</span></span>                |  <span data-ttu-id="71274-264">Architektury</span><span class="sxs-lookup"><span data-stu-id="71274-264">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="71274-265">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="71274-265">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="71274-266">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="71274-266">6, 7, 8</span></span>                | <span data-ttu-id="71274-267">x64</span><span class="sxs-lookup"><span data-stu-id="71274-267">x64</span></span> |
| <span data-ttu-id="71274-268">CentOS</span><span class="sxs-lookup"><span data-stu-id="71274-268">CentOS</span></span>                         |  <span data-ttu-id="71274-269">7+</span><span class="sxs-lookup"><span data-stu-id="71274-269">7+</span></span>                     | <span data-ttu-id="71274-270">x64</span><span class="sxs-lookup"><span data-stu-id="71274-270">x64</span></span> |
| <span data-ttu-id="71274-271">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="71274-271">Oracle Linux</span></span>                   |  <span data-ttu-id="71274-272">7+</span><span class="sxs-lookup"><span data-stu-id="71274-272">7+</span></span>                     | <span data-ttu-id="71274-273">x64</span><span class="sxs-lookup"><span data-stu-id="71274-273">x64</span></span> |
| <span data-ttu-id="71274-274">Fedora</span><span class="sxs-lookup"><span data-stu-id="71274-274">Fedora</span></span>                         |  <span data-ttu-id="71274-275">29 +</span><span class="sxs-lookup"><span data-stu-id="71274-275">29+</span></span>                    | <span data-ttu-id="71274-276">x64</span><span class="sxs-lookup"><span data-stu-id="71274-276">x64</span></span> |
| <span data-ttu-id="71274-277">Debian</span><span class="sxs-lookup"><span data-stu-id="71274-277">Debian</span></span>                         |  <span data-ttu-id="71274-278">9</span><span class="sxs-lookup"><span data-stu-id="71274-278">9</span></span>                      | <span data-ttu-id="71274-279">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="71274-279">x64, ARM32</span></span> |
| <span data-ttu-id="71274-280">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="71274-280">Ubuntu</span></span>                         |  <span data-ttu-id="71274-281">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="71274-281">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="71274-282">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="71274-282">x64, ARM32</span></span> |
| <span data-ttu-id="71274-283">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="71274-283">Linux Mint</span></span>                     |  <span data-ttu-id="71274-284">17 +</span><span class="sxs-lookup"><span data-stu-id="71274-284">17+</span></span>                    | <span data-ttu-id="71274-285">x64</span><span class="sxs-lookup"><span data-stu-id="71274-285">x64</span></span> |
| <span data-ttu-id="71274-286">openSUSE</span><span class="sxs-lookup"><span data-stu-id="71274-286">openSUSE</span></span>                       |  <span data-ttu-id="71274-287">15 +</span><span class="sxs-lookup"><span data-stu-id="71274-287">15+</span></span>                    | <span data-ttu-id="71274-288">x64</span><span class="sxs-lookup"><span data-stu-id="71274-288">x64</span></span> |
| <span data-ttu-id="71274-289">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="71274-289">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="71274-290">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="71274-290">12 SP2+</span></span>                | <span data-ttu-id="71274-291">x64</span><span class="sxs-lookup"><span data-stu-id="71274-291">x64</span></span> |
| <span data-ttu-id="71274-292">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="71274-292">Alpine Linux</span></span>                   |  <span data-ttu-id="71274-293">3.8 +</span><span class="sxs-lookup"><span data-stu-id="71274-293">3.8+</span></span>                   | <span data-ttu-id="71274-294">x64</span><span class="sxs-lookup"><span data-stu-id="71274-294">x64</span></span> |

<span data-ttu-id="71274-295">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="71274-295">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="71274-296">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="71274-296">Linux distribution dependencies</span></span>

<span data-ttu-id="71274-297">W zależności od dystrybucji systemu Linux może być konieczne zainstalowanie dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="71274-297">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71274-298">Dokładne wersje i nazwy mogą się nieco różnić w zależności od wybranej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="71274-298">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="71274-299">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="71274-299">Ubuntu</span></span>

<span data-ttu-id="71274-300">W przypadku dystrybucji Ubuntu wymagane jest zainstalowanie następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="71274-300">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="71274-301">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="71274-301">liblttng-ust0</span></span>
- <span data-ttu-id="71274-302">libcurl3 (dla 14. x i 16. x)</span><span class="sxs-lookup"><span data-stu-id="71274-302">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="71274-303">libcurl4 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="71274-303">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="71274-304">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="71274-304">libssl1.0.0</span></span>
- <span data-ttu-id="71274-305">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="71274-305">libkrb5-3</span></span>
- <span data-ttu-id="71274-306">zlib1g</span><span class="sxs-lookup"><span data-stu-id="71274-306">zlib1g</span></span>
- <span data-ttu-id="71274-307">libicu52 (dla 14. x)</span><span class="sxs-lookup"><span data-stu-id="71274-307">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="71274-308">libicu55 (dla 16. x)</span><span class="sxs-lookup"><span data-stu-id="71274-308">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="71274-309">libicu57 (dla 17. x)</span><span class="sxs-lookup"><span data-stu-id="71274-309">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="71274-310">libicu60 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="71274-310">libicu60 (for 18.x)</span></span>

<span data-ttu-id="71274-311">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:</span><span class="sxs-lookup"><span data-stu-id="71274-311">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="71274-312">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="71274-312">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="71274-313">Większość wersji programu Ubuntu obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="71274-313">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="71274-314">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="71274-314">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="71274-315">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="71274-315">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="71274-316">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="71274-316">CentOS and Fedora</span></span>

<span data-ttu-id="71274-317">Dystrybucje CentOS wymagają zainstalowanych następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="71274-317">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="71274-318">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="71274-318">lttng-ust</span></span>
- <span data-ttu-id="71274-319">libcurl</span><span class="sxs-lookup"><span data-stu-id="71274-319">libcurl</span></span>
- <span data-ttu-id="71274-320">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="71274-320">openssl-libs</span></span>
- <span data-ttu-id="71274-321">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="71274-321">krb5-libs</span></span>
- <span data-ttu-id="71274-322">libicu</span><span class="sxs-lookup"><span data-stu-id="71274-322">libicu</span></span>
- <span data-ttu-id="71274-323">zlib</span><span class="sxs-lookup"><span data-stu-id="71274-323">zlib</span></span>

<span data-ttu-id="71274-324">Fedora użytkownicy: Jeśli OpenSSL wersja > = 1,1, należy zainstalować polecenie **COMPAT-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="71274-324">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="71274-325">W przypadku platformy .NET Core 2,0 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="71274-325">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="71274-326">libunwind</span><span class="sxs-lookup"><span data-stu-id="71274-326">libunwind</span></span>
- <span data-ttu-id="71274-327">libuuid</span><span class="sxs-lookup"><span data-stu-id="71274-327">libuuid</span></span>

<span data-ttu-id="71274-328">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="71274-328">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="71274-329">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="71274-329">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="71274-330">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="71274-330">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="71274-331">Większość wersji CentOS i Fedora obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="71274-331">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="71274-332">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="71274-332">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="71274-333">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="71274-333">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="71274-334">Platforma .NET Core jest obsługiwana w następujących wersjach macOS:</span><span class="sxs-lookup"><span data-stu-id="71274-334">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="71274-335">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="71274-335">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="71274-336">Wersja platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="71274-336">.NET Core Version</span></span> | <span data-ttu-id="71274-337">macOS</span><span class="sxs-lookup"><span data-stu-id="71274-337">macOS</span></span>                 | <span data-ttu-id="71274-338">Architektury</span><span class="sxs-lookup"><span data-stu-id="71274-338">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="71274-339">3.0</span><span class="sxs-lookup"><span data-stu-id="71274-339">3.0</span></span>               | <span data-ttu-id="71274-340">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="71274-340">High Sierra (10.13+)</span></span>  | <span data-ttu-id="71274-341">x64</span><span class="sxs-lookup"><span data-stu-id="71274-341">x64</span></span> | [<span data-ttu-id="71274-342">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="71274-342">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="71274-343">2.2</span><span class="sxs-lookup"><span data-stu-id="71274-343">2.2</span></span>               | <span data-ttu-id="71274-344">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="71274-344">Sierra (10.12+)</span></span>       | <span data-ttu-id="71274-345">x64</span><span class="sxs-lookup"><span data-stu-id="71274-345">x64</span></span> | [<span data-ttu-id="71274-346">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="71274-346">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="71274-347">2.1</span><span class="sxs-lookup"><span data-stu-id="71274-347">2.1</span></span>               | <span data-ttu-id="71274-348">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="71274-348">Sierra (10.12+)</span></span>       | <span data-ttu-id="71274-349">x64</span><span class="sxs-lookup"><span data-stu-id="71274-349">x64</span></span> | [<span data-ttu-id="71274-350">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="71274-350">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="71274-351">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="71274-351">libgdiplus</span></span>

<span data-ttu-id="71274-352">Aplikacje .NET Core używające zestawu *System. Drawing. Common* wymagają zainstalowania libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="71274-352">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="71274-353">Łatwym sposobem uzyskania libgdiplus jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS.</span><span class="sxs-lookup"><span data-stu-id="71274-353">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="71274-354">Po zainstalowaniu *rozwiązania brew*Zainstaluj libgdiplus, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="71274-354">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="71274-355">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="71274-355">Next steps</span></span>

- <span data-ttu-id="71274-356">Aby opracowywać i uruchamiać aplikacje, zainstaluj [zestaw .NET Core SDK](sdk.md) (w tym środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="71274-356">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="71274-357">Aby uruchamiać aplikacje utworzone przez inne osoby, zainstaluj [środowisko uruchomieniowe programu .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="71274-357">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
