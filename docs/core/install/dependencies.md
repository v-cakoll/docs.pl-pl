---
title: Zależności zestaw .NET Core SDK i środowiska uruchomieniowego — .NET Core
description: Szczegółowe informacje na temat wymagań wstępnych dotyczących architektury procesora i systemu operacyjnego w celu zainstalowania zestaw .NET Core SDK i środowiska uruchomieniowego w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157816"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="56b18-103">Zależności i wymagania dotyczące platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="56b18-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="56b18-104">W tym artykule szczegółowo przedstawiono systemy operacyjne i architekturę procesora CPU obsługiwane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="56b18-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="56b18-105">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="56b18-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="56b18-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="56b18-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="56b18-107">W przypadku programu .NET Core 3,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="56b18-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="56b18-108">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="56b18-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="56b18-109">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="56b18-109">OS</span></span>                            | <span data-ttu-id="56b18-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="56b18-110">Version</span></span>                        | <span data-ttu-id="56b18-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="56b18-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="56b18-112">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="56b18-112">Windows Client</span></span>                | <span data-ttu-id="56b18-113">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="56b18-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="56b18-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-114">x64, x86</span></span>        |
| <span data-ttu-id="56b18-115">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="56b18-115">Windows 10 Client</span></span>             | <span data-ttu-id="56b18-116">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="56b18-116">Version 1607+</span></span>                  | <span data-ttu-id="56b18-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-117">x64, x86</span></span>        |
| <span data-ttu-id="56b18-118">Oprogramowanie Windows Server</span><span class="sxs-lookup"><span data-stu-id="56b18-118">Windows Server</span></span>                | <span data-ttu-id="56b18-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="56b18-119">2012 R2+</span></span>                       | <span data-ttu-id="56b18-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-120">x64, x86</span></span>        |
| <span data-ttu-id="56b18-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="56b18-121">Nano Server</span></span>                   | <span data-ttu-id="56b18-122">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="56b18-122">Version 1803+</span></span>                  | <span data-ttu-id="56b18-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="56b18-123">x64, ARM32</span></span>      |

<span data-ttu-id="56b18-124">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="56b18-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="56b18-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="56b18-126">W przypadku programu .NET Core 3,0 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="56b18-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="56b18-127">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="56b18-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="56b18-128">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="56b18-128">OS</span></span>                            | <span data-ttu-id="56b18-129">Wersja</span><span class="sxs-lookup"><span data-stu-id="56b18-129">Version</span></span>                        | <span data-ttu-id="56b18-130">Architektury</span><span class="sxs-lookup"><span data-stu-id="56b18-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="56b18-131">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="56b18-131">Windows Client</span></span>                | <span data-ttu-id="56b18-132">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="56b18-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="56b18-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-133">x64, x86</span></span>        |
| <span data-ttu-id="56b18-134">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="56b18-134">Windows 10 Client</span></span>             | <span data-ttu-id="56b18-135">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="56b18-135">Version 1607+</span></span>                  | <span data-ttu-id="56b18-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-136">x64, x86</span></span>        |
| <span data-ttu-id="56b18-137">Oprogramowanie Windows Server</span><span class="sxs-lookup"><span data-stu-id="56b18-137">Windows Server</span></span>                | <span data-ttu-id="56b18-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="56b18-138">2012 R2+</span></span>                       | <span data-ttu-id="56b18-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-139">x64, x86</span></span>        |
| <span data-ttu-id="56b18-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="56b18-140">Nano Server</span></span>                   | <span data-ttu-id="56b18-141">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="56b18-141">Version 1803+</span></span>                  | <span data-ttu-id="56b18-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="56b18-142">x64, ARM32</span></span>      |

<span data-ttu-id="56b18-143">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="56b18-144">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="56b18-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="56b18-145">W przypadku programu .NET Core 2,2 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="56b18-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="56b18-146">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="56b18-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="56b18-147">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="56b18-147">OS</span></span>                            | <span data-ttu-id="56b18-148">Wersja</span><span class="sxs-lookup"><span data-stu-id="56b18-148">Version</span></span>                        | <span data-ttu-id="56b18-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="56b18-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="56b18-150">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="56b18-150">Windows Client</span></span>                | <span data-ttu-id="56b18-151">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="56b18-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="56b18-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-152">x64, x86</span></span>        |
| <span data-ttu-id="56b18-153">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="56b18-153">Windows 10 Client</span></span>             | <span data-ttu-id="56b18-154">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="56b18-154">Version 1607+</span></span>                  | <span data-ttu-id="56b18-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-155">x64, x86</span></span>        |
| <span data-ttu-id="56b18-156">Oprogramowanie Windows Server</span><span class="sxs-lookup"><span data-stu-id="56b18-156">Windows Server</span></span>                | <span data-ttu-id="56b18-157">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="56b18-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="56b18-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-158">x64, x86</span></span>        |
| <span data-ttu-id="56b18-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="56b18-159">Nano Server</span></span>                   | <span data-ttu-id="56b18-160">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="56b18-160">Version 1803+</span></span>                   | <span data-ttu-id="56b18-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="56b18-161">x64, ARM32</span></span>      |

<span data-ttu-id="56b18-162">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="56b18-163">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="56b18-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="56b18-164">W przypadku programu .NET Core 2,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="56b18-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="56b18-165">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="56b18-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="56b18-166">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="56b18-166">OS</span></span>                            | <span data-ttu-id="56b18-167">Wersja</span><span class="sxs-lookup"><span data-stu-id="56b18-167">Version</span></span>                        | <span data-ttu-id="56b18-168">Architektury</span><span class="sxs-lookup"><span data-stu-id="56b18-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="56b18-169">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="56b18-169">Windows Client</span></span>                | <span data-ttu-id="56b18-170">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="56b18-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="56b18-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-171">x64, x86</span></span>        |
| <span data-ttu-id="56b18-172">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="56b18-172">Windows 10 Client</span></span>             | <span data-ttu-id="56b18-173">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="56b18-173">Version 1607+</span></span>                  | <span data-ttu-id="56b18-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-174">x64, x86</span></span>        |
| <span data-ttu-id="56b18-175">Oprogramowanie Windows Server</span><span class="sxs-lookup"><span data-stu-id="56b18-175">Windows Server</span></span>                | <span data-ttu-id="56b18-176">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="56b18-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="56b18-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="56b18-177">x64, x86</span></span>        |
| <span data-ttu-id="56b18-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="56b18-178">Nano Server</span></span>                   | <span data-ttu-id="56b18-179">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="56b18-179">Version 1803+</span></span>                  | <span data-ttu-id="56b18-180">procesorów</span><span class="sxs-lookup"><span data-stu-id="56b18-180">x64,</span></span>            |

<span data-ttu-id="56b18-181">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="56b18-182">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="56b18-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="56b18-183">Jeśli instalujesz zestaw .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows, wymagane są dodatkowe zależności:</span><span class="sxs-lookup"><span data-stu-id="56b18-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="56b18-184">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="56b18-184">Windows 7 SP1</span></span>
- <span data-ttu-id="56b18-185">Windows Vista z dodatkiem SP 2</span><span class="sxs-lookup"><span data-stu-id="56b18-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="56b18-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="56b18-186">Windows 8.1</span></span>
- <span data-ttu-id="56b18-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="56b18-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="56b18-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="56b18-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="56b18-189">Zainstaluj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="56b18-189">Install the following:</span></span>

- <span data-ttu-id="56b18-190">Pakiet [redystrybucyjny Microsoft Visual C++ 2015 z aktualizacją Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="56b18-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="56b18-191">POPRAWKI KB2533623</span><span class="sxs-lookup"><span data-stu-id="56b18-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="56b18-192">Powyższe wymagania są również wymagane w przypadku wystąpienia jednego z następujących błędów:</span><span class="sxs-lookup"><span data-stu-id="56b18-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="56b18-193">Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-CRT-Runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="56b18-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="56b18-194">Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="56b18-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="56b18-195">\- lub-</span><span class="sxs-lookup"><span data-stu-id="56b18-195">\- or -</span></span>
>
> <span data-ttu-id="56b18-196">Znaleziono bibliotekę *hostfxr. dll* , ale ładowanie jej z *dysku C:\\\<path_to_app >\\hostfxr. dll* nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="56b18-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="56b18-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="56b18-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="56b18-198">Program .NET Core 3,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="56b18-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="56b18-199">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="56b18-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="56b18-200">Platforma .NET Core 3,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="56b18-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="56b18-201">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="56b18-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="56b18-202">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="56b18-202">OS</span></span>                             | <span data-ttu-id="56b18-203">Wersja</span><span class="sxs-lookup"><span data-stu-id="56b18-203">Version</span></span>               | <span data-ttu-id="56b18-204">Architektury</span><span class="sxs-lookup"><span data-stu-id="56b18-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="56b18-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="56b18-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="56b18-206">6, 7, 8</span></span>               | <span data-ttu-id="56b18-207">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-207">x64</span></span> |
| <span data-ttu-id="56b18-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="56b18-208">CentOS</span></span>                         | <span data-ttu-id="56b18-209">7+</span><span class="sxs-lookup"><span data-stu-id="56b18-209">7+</span></span>                    | <span data-ttu-id="56b18-210">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-210">x64</span></span> |
| <span data-ttu-id="56b18-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-211">Oracle Linux</span></span>                   | <span data-ttu-id="56b18-212">7+</span><span class="sxs-lookup"><span data-stu-id="56b18-212">7+</span></span>                    | <span data-ttu-id="56b18-213">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-213">x64</span></span> |
| <span data-ttu-id="56b18-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="56b18-214">Fedora</span></span>                         | <span data-ttu-id="56b18-215">29 +</span><span class="sxs-lookup"><span data-stu-id="56b18-215">29+</span></span>                   | <span data-ttu-id="56b18-216">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-216">x64</span></span> |
| <span data-ttu-id="56b18-217">Debian</span><span class="sxs-lookup"><span data-stu-id="56b18-217">Debian</span></span>                         | <span data-ttu-id="56b18-218">9+</span><span class="sxs-lookup"><span data-stu-id="56b18-218">9+</span></span>                    | <span data-ttu-id="56b18-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="56b18-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="56b18-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="56b18-220">Ubuntu</span></span>                         | <span data-ttu-id="56b18-221">16.04 +</span><span class="sxs-lookup"><span data-stu-id="56b18-221">16.04+</span></span>                | <span data-ttu-id="56b18-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="56b18-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="56b18-223">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-223">Linux Mint</span></span>                     | <span data-ttu-id="56b18-224">18 +</span><span class="sxs-lookup"><span data-stu-id="56b18-224">18+</span></span>                   | <span data-ttu-id="56b18-225">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-225">x64</span></span> |
| <span data-ttu-id="56b18-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="56b18-226">openSUSE</span></span>                       | <span data-ttu-id="56b18-227">15 +</span><span class="sxs-lookup"><span data-stu-id="56b18-227">15+</span></span>                   | <span data-ttu-id="56b18-228">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-228">x64</span></span> |
| <span data-ttu-id="56b18-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="56b18-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="56b18-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="56b18-230">12 SP2+</span></span>               | <span data-ttu-id="56b18-231">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-231">x64</span></span> |
| <span data-ttu-id="56b18-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-232">Alpine Linux</span></span>                   | <span data-ttu-id="56b18-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="56b18-233">3.10+</span></span>                 | <span data-ttu-id="56b18-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="56b18-234">x64, ARM64</span></span> |

<span data-ttu-id="56b18-235">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="56b18-236">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,1 w systemie ARM64 (jądro 4.14 +), zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="56b18-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56b18-237">Obsługa ARM64 wymaga jądra systemu Linux 4,14 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="56b18-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="56b18-238">Niektóre dystrybucje systemu Linux spełniają to wymaganie, a inne nie.</span><span class="sxs-lookup"><span data-stu-id="56b18-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="56b18-239">Na przykład Ubuntu 18,04 jest obsługiwany, ale Ubuntu 16,04 nie jest.</span><span class="sxs-lookup"><span data-stu-id="56b18-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="56b18-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="56b18-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="56b18-241">Program .NET Core 3,0 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="56b18-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="56b18-242">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="56b18-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="56b18-243">Platforma .NET Core 3,0 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="56b18-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="56b18-244">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="56b18-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="56b18-245">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="56b18-245">OS</span></span>                             | <span data-ttu-id="56b18-246">Wersja</span><span class="sxs-lookup"><span data-stu-id="56b18-246">Version</span></span>               | <span data-ttu-id="56b18-247">Architektury</span><span class="sxs-lookup"><span data-stu-id="56b18-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="56b18-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="56b18-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="56b18-249">6, 7, 8</span></span>               | <span data-ttu-id="56b18-250">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-250">x64</span></span> |
| <span data-ttu-id="56b18-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="56b18-251">CentOS</span></span>                         | <span data-ttu-id="56b18-252">7+</span><span class="sxs-lookup"><span data-stu-id="56b18-252">7+</span></span>                    | <span data-ttu-id="56b18-253">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-253">x64</span></span> |
| <span data-ttu-id="56b18-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-254">Oracle Linux</span></span>                   | <span data-ttu-id="56b18-255">7+</span><span class="sxs-lookup"><span data-stu-id="56b18-255">7+</span></span>                    | <span data-ttu-id="56b18-256">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-256">x64</span></span> |
| <span data-ttu-id="56b18-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="56b18-257">Fedora</span></span>                         | <span data-ttu-id="56b18-258">29 +</span><span class="sxs-lookup"><span data-stu-id="56b18-258">29+</span></span>                   | <span data-ttu-id="56b18-259">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-259">x64</span></span> |
| <span data-ttu-id="56b18-260">Debian</span><span class="sxs-lookup"><span data-stu-id="56b18-260">Debian</span></span>                         | <span data-ttu-id="56b18-261">9+</span><span class="sxs-lookup"><span data-stu-id="56b18-261">9+</span></span>                    | <span data-ttu-id="56b18-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="56b18-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="56b18-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="56b18-263">Ubuntu</span></span>                         | <span data-ttu-id="56b18-264">16.04 +</span><span class="sxs-lookup"><span data-stu-id="56b18-264">16.04+</span></span>                | <span data-ttu-id="56b18-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="56b18-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="56b18-266">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-266">Linux Mint</span></span>                     | <span data-ttu-id="56b18-267">18 +</span><span class="sxs-lookup"><span data-stu-id="56b18-267">18+</span></span>                   | <span data-ttu-id="56b18-268">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-268">x64</span></span> |
| <span data-ttu-id="56b18-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="56b18-269">openSUSE</span></span>                       | <span data-ttu-id="56b18-270">15 +</span><span class="sxs-lookup"><span data-stu-id="56b18-270">15+</span></span>                   | <span data-ttu-id="56b18-271">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-271">x64</span></span> |
| <span data-ttu-id="56b18-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="56b18-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="56b18-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="56b18-273">12 SP2+</span></span>               | <span data-ttu-id="56b18-274">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-274">x64</span></span> |
| <span data-ttu-id="56b18-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-275">Alpine Linux</span></span>                   | <span data-ttu-id="56b18-276">3.8 +</span><span class="sxs-lookup"><span data-stu-id="56b18-276">3.8+</span></span>                  | <span data-ttu-id="56b18-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="56b18-277">x64, ARM64</span></span> |

<span data-ttu-id="56b18-278">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="56b18-279">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="56b18-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="56b18-280">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="56b18-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="56b18-281">Program .NET Core 2,2 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="56b18-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="56b18-282">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="56b18-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="56b18-283">Platforma .NET Core 2,2 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="56b18-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="56b18-284">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="56b18-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="56b18-285">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="56b18-285">OS</span></span>                             |  <span data-ttu-id="56b18-286">Wersja</span><span class="sxs-lookup"><span data-stu-id="56b18-286">Version</span></span>                |  <span data-ttu-id="56b18-287">Architektury</span><span class="sxs-lookup"><span data-stu-id="56b18-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="56b18-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="56b18-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="56b18-289">6, 7</span></span>                   | <span data-ttu-id="56b18-290">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-290">x64</span></span> |
| <span data-ttu-id="56b18-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="56b18-291">CentOS</span></span>                         |  <span data-ttu-id="56b18-292">7</span><span class="sxs-lookup"><span data-stu-id="56b18-292">7</span></span>                      | <span data-ttu-id="56b18-293">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-293">x64</span></span> |
| <span data-ttu-id="56b18-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-294">Oracle Linux</span></span>                   |  <span data-ttu-id="56b18-295">7</span><span class="sxs-lookup"><span data-stu-id="56b18-295">7</span></span>                      | <span data-ttu-id="56b18-296">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-296">x64</span></span> |
| <span data-ttu-id="56b18-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="56b18-297">Fedora</span></span>                         |  <span data-ttu-id="56b18-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="56b18-298">29, 30</span></span>                 | <span data-ttu-id="56b18-299">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-299">x64</span></span> |
| <span data-ttu-id="56b18-300">Debian</span><span class="sxs-lookup"><span data-stu-id="56b18-300">Debian</span></span>                         |  <span data-ttu-id="56b18-301">9</span><span class="sxs-lookup"><span data-stu-id="56b18-301">9</span></span>                      | <span data-ttu-id="56b18-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="56b18-302">x64, ARM32</span></span> |
| <span data-ttu-id="56b18-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="56b18-303">Ubuntu</span></span>                         |  <span data-ttu-id="56b18-304">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="56b18-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="56b18-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="56b18-305">x64, ARM32</span></span> |
| <span data-ttu-id="56b18-306">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-306">Linux Mint</span></span>                     |  <span data-ttu-id="56b18-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="56b18-307">17, 18</span></span>                 | <span data-ttu-id="56b18-308">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-308">x64</span></span> |
| <span data-ttu-id="56b18-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="56b18-309">openSUSE</span></span>                       |  <span data-ttu-id="56b18-310">15 +</span><span class="sxs-lookup"><span data-stu-id="56b18-310">15+</span></span>                    | <span data-ttu-id="56b18-311">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-311">x64</span></span> |
| <span data-ttu-id="56b18-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="56b18-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="56b18-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="56b18-313">12 SP2+</span></span>                | <span data-ttu-id="56b18-314">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-314">x64</span></span> |
| <span data-ttu-id="56b18-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-315">Alpine Linux</span></span>                   |  <span data-ttu-id="56b18-316">3.8 +</span><span class="sxs-lookup"><span data-stu-id="56b18-316">3.8+</span></span>                   | <span data-ttu-id="56b18-317">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-317">x64</span></span> |

<span data-ttu-id="56b18-318">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="56b18-319">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="56b18-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="56b18-320">Program .NET Core 2,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="56b18-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="56b18-321">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="56b18-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="56b18-322">Platforma .NET Core 2,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="56b18-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="56b18-323">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="56b18-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="56b18-324">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="56b18-324">OS</span></span>                             |  <span data-ttu-id="56b18-325">Wersja</span><span class="sxs-lookup"><span data-stu-id="56b18-325">Version</span></span>                |  <span data-ttu-id="56b18-326">Architektury</span><span class="sxs-lookup"><span data-stu-id="56b18-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="56b18-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="56b18-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="56b18-328">6, 7, 8</span></span>                | <span data-ttu-id="56b18-329">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-329">x64</span></span> |
| <span data-ttu-id="56b18-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="56b18-330">CentOS</span></span>                         |  <span data-ttu-id="56b18-331">7+</span><span class="sxs-lookup"><span data-stu-id="56b18-331">7+</span></span>                     | <span data-ttu-id="56b18-332">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-332">x64</span></span> |
| <span data-ttu-id="56b18-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-333">Oracle Linux</span></span>                   |  <span data-ttu-id="56b18-334">7+</span><span class="sxs-lookup"><span data-stu-id="56b18-334">7+</span></span>                     | <span data-ttu-id="56b18-335">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-335">x64</span></span> |
| <span data-ttu-id="56b18-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="56b18-336">Fedora</span></span>                         |  <span data-ttu-id="56b18-337">29 +</span><span class="sxs-lookup"><span data-stu-id="56b18-337">29+</span></span>                    | <span data-ttu-id="56b18-338">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-338">x64</span></span> |
| <span data-ttu-id="56b18-339">Debian</span><span class="sxs-lookup"><span data-stu-id="56b18-339">Debian</span></span>                         |  <span data-ttu-id="56b18-340">9</span><span class="sxs-lookup"><span data-stu-id="56b18-340">9</span></span>                      | <span data-ttu-id="56b18-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="56b18-341">x64, ARM32</span></span> |
| <span data-ttu-id="56b18-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="56b18-342">Ubuntu</span></span>                         |  <span data-ttu-id="56b18-343">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="56b18-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="56b18-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="56b18-344">x64, ARM32</span></span> |
| <span data-ttu-id="56b18-345">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-345">Linux Mint</span></span>                     |  <span data-ttu-id="56b18-346">17 +</span><span class="sxs-lookup"><span data-stu-id="56b18-346">17+</span></span>                    | <span data-ttu-id="56b18-347">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-347">x64</span></span> |
| <span data-ttu-id="56b18-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="56b18-348">openSUSE</span></span>                       |  <span data-ttu-id="56b18-349">15 +</span><span class="sxs-lookup"><span data-stu-id="56b18-349">15+</span></span>                    | <span data-ttu-id="56b18-350">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-350">x64</span></span> |
| <span data-ttu-id="56b18-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="56b18-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="56b18-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="56b18-352">12 SP2+</span></span>                | <span data-ttu-id="56b18-353">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-353">x64</span></span> |
| <span data-ttu-id="56b18-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-354">Alpine Linux</span></span>                   |  <span data-ttu-id="56b18-355">3.8 +</span><span class="sxs-lookup"><span data-stu-id="56b18-355">3.8+</span></span>                   | <span data-ttu-id="56b18-356">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-356">x64</span></span> |

<span data-ttu-id="56b18-357">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="56b18-358">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="56b18-358">Linux distribution dependencies</span></span>

<span data-ttu-id="56b18-359">W zależności od dystrybucji systemu Linux może być konieczne zainstalowanie dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="56b18-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56b18-360">Dokładne wersje i nazwy mogą się nieco różnić w zależności od wybranej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="56b18-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="56b18-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="56b18-361">Ubuntu</span></span>

<span data-ttu-id="56b18-362">W przypadku dystrybucji Ubuntu wymagane jest zainstalowanie następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="56b18-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="56b18-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="56b18-363">liblttng-ust0</span></span>
- <span data-ttu-id="56b18-364">libcurl3 (dla 14. x i 16. x)</span><span class="sxs-lookup"><span data-stu-id="56b18-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="56b18-365">libcurl4 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="56b18-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="56b18-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="56b18-366">libssl1.0.0</span></span>
- <span data-ttu-id="56b18-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="56b18-367">libkrb5-3</span></span>
- <span data-ttu-id="56b18-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="56b18-368">zlib1g</span></span>
- <span data-ttu-id="56b18-369">libicu52 (dla 14. x)</span><span class="sxs-lookup"><span data-stu-id="56b18-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="56b18-370">libicu55 (dla 16. x)</span><span class="sxs-lookup"><span data-stu-id="56b18-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="56b18-371">libicu57 (dla 17. x)</span><span class="sxs-lookup"><span data-stu-id="56b18-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="56b18-372">libicu60 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="56b18-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="56b18-373">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:</span><span class="sxs-lookup"><span data-stu-id="56b18-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="56b18-374">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="56b18-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="56b18-375">Większość wersji programu Ubuntu obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="56b18-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="56b18-376">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="56b18-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="56b18-377">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="56b18-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="56b18-378">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="56b18-378">CentOS and Fedora</span></span>

<span data-ttu-id="56b18-379">Dystrybucje CentOS wymagają zainstalowanych następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="56b18-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="56b18-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="56b18-380">lttng-ust</span></span>
- <span data-ttu-id="56b18-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="56b18-381">libcurl</span></span>
- <span data-ttu-id="56b18-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="56b18-382">openssl-libs</span></span>
- <span data-ttu-id="56b18-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="56b18-383">krb5-libs</span></span>
- <span data-ttu-id="56b18-384">libicu</span><span class="sxs-lookup"><span data-stu-id="56b18-384">libicu</span></span>
- <span data-ttu-id="56b18-385">zlib</span><span class="sxs-lookup"><span data-stu-id="56b18-385">zlib</span></span>

<span data-ttu-id="56b18-386">Fedora użytkownicy: Jeśli OpenSSL wersja > = 1,1, należy zainstalować polecenie **COMPAT-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="56b18-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="56b18-387">W przypadku platformy .NET Core 2,0 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="56b18-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="56b18-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="56b18-388">libunwind</span></span>
- <span data-ttu-id="56b18-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="56b18-389">libuuid</span></span>

<span data-ttu-id="56b18-390">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="56b18-391">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="56b18-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="56b18-392">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="56b18-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="56b18-393">Większość wersji CentOS i Fedora obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="56b18-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="56b18-394">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="56b18-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="56b18-395">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="56b18-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="56b18-396">Platforma .NET Core jest obsługiwana w następujących wersjach macOS:</span><span class="sxs-lookup"><span data-stu-id="56b18-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="56b18-397">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="56b18-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="56b18-398">Wersja platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="56b18-398">.NET Core Version</span></span> | <span data-ttu-id="56b18-399">macOS</span><span class="sxs-lookup"><span data-stu-id="56b18-399">macOS</span></span>                 | <span data-ttu-id="56b18-400">Architektury</span><span class="sxs-lookup"><span data-stu-id="56b18-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="56b18-401">3.1</span><span class="sxs-lookup"><span data-stu-id="56b18-401">3.1</span></span>               | <span data-ttu-id="56b18-402">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="56b18-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="56b18-403">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-403">x64</span></span> | [<span data-ttu-id="56b18-404">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="56b18-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="56b18-405">3.0</span><span class="sxs-lookup"><span data-stu-id="56b18-405">3.0</span></span>               | <span data-ttu-id="56b18-406">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="56b18-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="56b18-407">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-407">x64</span></span> | [<span data-ttu-id="56b18-408">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="56b18-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="56b18-409">2.2</span><span class="sxs-lookup"><span data-stu-id="56b18-409">2.2</span></span>               | <span data-ttu-id="56b18-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="56b18-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="56b18-411">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-411">x64</span></span> | [<span data-ttu-id="56b18-412">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="56b18-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="56b18-413">2.1</span><span class="sxs-lookup"><span data-stu-id="56b18-413">2.1</span></span>               | <span data-ttu-id="56b18-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="56b18-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="56b18-415">x64</span><span class="sxs-lookup"><span data-stu-id="56b18-415">x64</span></span> | [<span data-ttu-id="56b18-416">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="56b18-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="56b18-417">Począwszy od programu macOS Catalina (wersja 10,15), całe oprogramowanie skompilowane po 1 czerwca 2019, które jest dystrybuowane z IDENTYFIKATORem dewelopera, musi być notarialne.</span><span class="sxs-lookup"><span data-stu-id="56b18-417">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="56b18-418">To wymaganie dotyczy środowiska uruchomieniowego .NET Core, zestaw .NET Core SDK i oprogramowania utworzonego za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="56b18-418">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="56b18-419">Instalatory dla programu .NET Core (zarówno środowisko uruchomieniowe, jak i zestaw SDK) w wersji 3,1, 3,0 i 2,1 zostały zgłoszone od 18 lutego 2020.</span><span class="sxs-lookup"><span data-stu-id="56b18-419">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="56b18-420">Wcześniejsze wersje nie zostały ujawnione.</span><span class="sxs-lookup"><span data-stu-id="56b18-420">Prior released versions aren't notarized.</span></span> <span data-ttu-id="56b18-421">Jeśli uruchomisz zanotarialną aplikację, zobaczysz komunikat o błędzie podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="56b18-421">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![Alert notarization macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="56b18-423">Aby uzyskać więcej informacji na temat sposobu, w jaki wymuszone — notarization wpływa na platformę .NET Core (i aplikacje platformy .NET Core), zobacz [Praca z MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-423">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="56b18-424">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="56b18-424">libgdiplus</span></span>

<span data-ttu-id="56b18-425">Aplikacje .NET Core używające zestawu *System. Drawing. Common* wymagają zainstalowania libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="56b18-425">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="56b18-426">Łatwym sposobem uzyskania libgdiplus jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS.</span><span class="sxs-lookup"><span data-stu-id="56b18-426">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="56b18-427">Po zainstalowaniu *rozwiązania brew*Zainstaluj libgdiplus, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="56b18-427">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="56b18-428">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="56b18-428">Next steps</span></span>

- <span data-ttu-id="56b18-429">Aby opracowywać i uruchamiać aplikacje, zainstaluj [zestaw .NET Core SDK](sdk.md) (w tym środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="56b18-429">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="56b18-430">Aby uruchamiać aplikacje utworzone przez inne osoby, zainstaluj [środowisko uruchomieniowe programu .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="56b18-430">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
