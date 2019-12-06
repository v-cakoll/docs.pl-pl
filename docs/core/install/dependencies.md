---
title: Zależności zestaw .NET Core SDK i środowiska uruchomieniowego — .NET Core
description: Szczegółowe informacje na temat wymagań wstępnych dotyczących architektury procesora i systemu operacyjnego w celu zainstalowania zestaw .NET Core SDK i środowiska uruchomieniowego w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a535048fc8756b55068098ad61fdc37fc8c1f04e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837004"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="fe133-103">Zależności i wymagania dotyczące platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe133-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="fe133-104">W tym artykule szczegółowo przedstawiono systemy operacyjne i architekturę procesora CPU obsługiwane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe133-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="fe133-105">Supported operating systems</span><span class="sxs-lookup"><span data-stu-id="fe133-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31tabnetcore31"></a>[<span data-ttu-id="fe133-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="fe133-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="fe133-107">W przypadku programu .NET Core 3,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="fe133-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="fe133-108">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="fe133-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fe133-109">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="fe133-109">OS</span></span>                            | <span data-ttu-id="fe133-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="fe133-110">Version</span></span>                        | <span data-ttu-id="fe133-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="fe133-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fe133-112">Klient z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="fe133-112">Windows Client</span></span>                | <span data-ttu-id="fe133-113">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="fe133-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fe133-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-114">x64, x86</span></span>        |
| <span data-ttu-id="fe133-115">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="fe133-115">Windows 10 Client</span></span>             | <span data-ttu-id="fe133-116">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="fe133-116">Version 1607+</span></span>                  | <span data-ttu-id="fe133-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-117">x64, x86</span></span>        |
| <span data-ttu-id="fe133-118">Windows Server dla</span><span class="sxs-lookup"><span data-stu-id="fe133-118">Windows Server</span></span>                | <span data-ttu-id="fe133-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="fe133-119">2012 R2+</span></span>                       | <span data-ttu-id="fe133-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-120">x64, x86</span></span>        |
| <span data-ttu-id="fe133-121">Serwer Nano Server</span><span class="sxs-lookup"><span data-stu-id="fe133-121">Nano Server</span></span>                   | <span data-ttu-id="fe133-122">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="fe133-122">Version 1803+</span></span>                  | <span data-ttu-id="fe133-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fe133-123">x64, ARM32</span></span>      |

<span data-ttu-id="fe133-124">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="fe133-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fe133-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="fe133-126">W przypadku programu .NET Core 3,0 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="fe133-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="fe133-127">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="fe133-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fe133-128">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="fe133-128">OS</span></span>                            | <span data-ttu-id="fe133-129">Wersja</span><span class="sxs-lookup"><span data-stu-id="fe133-129">Version</span></span>                        | <span data-ttu-id="fe133-130">Architektury</span><span class="sxs-lookup"><span data-stu-id="fe133-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fe133-131">Klient z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="fe133-131">Windows Client</span></span>                | <span data-ttu-id="fe133-132">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="fe133-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fe133-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-133">x64, x86</span></span>        |
| <span data-ttu-id="fe133-134">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="fe133-134">Windows 10 Client</span></span>             | <span data-ttu-id="fe133-135">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="fe133-135">Version 1607+</span></span>                  | <span data-ttu-id="fe133-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-136">x64, x86</span></span>        |
| <span data-ttu-id="fe133-137">Windows Server dla</span><span class="sxs-lookup"><span data-stu-id="fe133-137">Windows Server</span></span>                | <span data-ttu-id="fe133-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="fe133-138">2012 R2+</span></span>                       | <span data-ttu-id="fe133-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-139">x64, x86</span></span>        |
| <span data-ttu-id="fe133-140">Serwer Nano Server</span><span class="sxs-lookup"><span data-stu-id="fe133-140">Nano Server</span></span>                   | <span data-ttu-id="fe133-141">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="fe133-141">Version 1803+</span></span>                  | <span data-ttu-id="fe133-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fe133-142">x64, ARM32</span></span>      |

<span data-ttu-id="fe133-143">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="fe133-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="fe133-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="fe133-145">W przypadku programu .NET Core 2,2 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="fe133-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="fe133-146">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="fe133-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fe133-147">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="fe133-147">OS</span></span>                            | <span data-ttu-id="fe133-148">Wersja</span><span class="sxs-lookup"><span data-stu-id="fe133-148">Version</span></span>                        | <span data-ttu-id="fe133-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="fe133-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fe133-150">Klient z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="fe133-150">Windows Client</span></span>                | <span data-ttu-id="fe133-151">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="fe133-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fe133-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-152">x64, x86</span></span>        |
| <span data-ttu-id="fe133-153">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="fe133-153">Windows 10 Client</span></span>             | <span data-ttu-id="fe133-154">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="fe133-154">Version 1607+</span></span>                  | <span data-ttu-id="fe133-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-155">x64, x86</span></span>        |
| <span data-ttu-id="fe133-156">Windows Server dla</span><span class="sxs-lookup"><span data-stu-id="fe133-156">Windows Server</span></span>                | <span data-ttu-id="fe133-157">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="fe133-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="fe133-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-158">x64, x86</span></span>        |
| <span data-ttu-id="fe133-159">Serwer Nano Server</span><span class="sxs-lookup"><span data-stu-id="fe133-159">Nano Server</span></span>                   | <span data-ttu-id="fe133-160">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="fe133-160">Version 1803+</span></span>                   | <span data-ttu-id="fe133-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fe133-161">x64, ARM32</span></span>      |

<span data-ttu-id="fe133-162">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fe133-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fe133-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fe133-164">W przypadku programu .NET Core 2,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="fe133-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="fe133-165">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="fe133-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fe133-166">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="fe133-166">OS</span></span>                            | <span data-ttu-id="fe133-167">Wersja</span><span class="sxs-lookup"><span data-stu-id="fe133-167">Version</span></span>                        | <span data-ttu-id="fe133-168">Architektury</span><span class="sxs-lookup"><span data-stu-id="fe133-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="fe133-169">Klient z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="fe133-169">Windows Client</span></span>                | <span data-ttu-id="fe133-170">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="fe133-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="fe133-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-171">x64, x86</span></span>        |
| <span data-ttu-id="fe133-172">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="fe133-172">Windows 10 Client</span></span>             | <span data-ttu-id="fe133-173">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="fe133-173">Version 1607+</span></span>                  | <span data-ttu-id="fe133-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-174">x64, x86</span></span>        |
| <span data-ttu-id="fe133-175">Windows Server dla</span><span class="sxs-lookup"><span data-stu-id="fe133-175">Windows Server</span></span>                | <span data-ttu-id="fe133-176">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="fe133-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="fe133-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="fe133-177">x64, x86</span></span>        |
| <span data-ttu-id="fe133-178">Serwer Nano Server</span><span class="sxs-lookup"><span data-stu-id="fe133-178">Nano Server</span></span>                   | <span data-ttu-id="fe133-179">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="fe133-179">Version 1803+</span></span>                  | <span data-ttu-id="fe133-180">procesorów</span><span class="sxs-lookup"><span data-stu-id="fe133-180">x64,</span></span>            |

<span data-ttu-id="fe133-181">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="fe133-182">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="fe133-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="fe133-183">Jeśli instalujesz zestaw .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows, wymagane są dodatkowe zależności:</span><span class="sxs-lookup"><span data-stu-id="fe133-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="fe133-184">Dodatek SP1 dla systemu Windows 7</span><span class="sxs-lookup"><span data-stu-id="fe133-184">Windows 7 SP1</span></span>
- <span data-ttu-id="fe133-185">Windows Vista z dodatkiem SP 2</span><span class="sxs-lookup"><span data-stu-id="fe133-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="fe133-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="fe133-186">Windows 8.1</span></span>
- <span data-ttu-id="fe133-187">Windows Server 2008 z dodatkiem R2</span><span class="sxs-lookup"><span data-stu-id="fe133-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="fe133-188">Windows Server 2012 z dodatkiem R2</span><span class="sxs-lookup"><span data-stu-id="fe133-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="fe133-189">Zainstaluj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fe133-189">Install the following:</span></span>

- <span data-ttu-id="fe133-190">Pakiet [redystrybucyjny Microsoft Visual C++ 2015 z aktualizacją Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="fe133-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="fe133-191">POPRAWKI KB2533623</span><span class="sxs-lookup"><span data-stu-id="fe133-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="fe133-192">Powyższe wymagania są również wymagane w przypadku wystąpienia jednego z następujących błędów:</span><span class="sxs-lookup"><span data-stu-id="fe133-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="fe133-193">Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-CRT-Runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="fe133-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="fe133-194">Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="fe133-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="fe133-195">\- lub —</span><span class="sxs-lookup"><span data-stu-id="fe133-195">\- or -</span></span>
>
> <span data-ttu-id="fe133-196">Znaleziono bibliotekę *hostfxr. dll* , ale ładowanie jej z *dysku C:\\\<path_to_app >\\hostfxr. dll* nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="fe133-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31tabnetcore31"></a>[<span data-ttu-id="fe133-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="fe133-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="fe133-198">Program .NET Core 3,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="fe133-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="fe133-199">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="fe133-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="fe133-200">Platforma .NET Core 3,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="fe133-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="fe133-201">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="fe133-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fe133-202">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="fe133-202">OS</span></span>                             | <span data-ttu-id="fe133-203">Wersja</span><span class="sxs-lookup"><span data-stu-id="fe133-203">Version</span></span>               | <span data-ttu-id="fe133-204">Architektury</span><span class="sxs-lookup"><span data-stu-id="fe133-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="fe133-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="fe133-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="fe133-206">6, 7, 8</span></span>               | <span data-ttu-id="fe133-207">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-207">x64</span></span> |
| <span data-ttu-id="fe133-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="fe133-208">CentOS</span></span>                         | <span data-ttu-id="fe133-209">7+</span><span class="sxs-lookup"><span data-stu-id="fe133-209">7+</span></span>                    | <span data-ttu-id="fe133-210">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-210">x64</span></span> |
| <span data-ttu-id="fe133-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-211">Oracle Linux</span></span>                   | <span data-ttu-id="fe133-212">7+</span><span class="sxs-lookup"><span data-stu-id="fe133-212">7+</span></span>                    | <span data-ttu-id="fe133-213">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-213">x64</span></span> |
| <span data-ttu-id="fe133-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="fe133-214">Fedora</span></span>                         | <span data-ttu-id="fe133-215">29 +</span><span class="sxs-lookup"><span data-stu-id="fe133-215">29+</span></span>                   | <span data-ttu-id="fe133-216">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-216">x64</span></span> |
| <span data-ttu-id="fe133-217">Debian</span><span class="sxs-lookup"><span data-stu-id="fe133-217">Debian</span></span>                         | <span data-ttu-id="fe133-218">9+</span><span class="sxs-lookup"><span data-stu-id="fe133-218">9+</span></span>                    | <span data-ttu-id="fe133-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="fe133-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="fe133-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fe133-220">Ubuntu</span></span>                         | <span data-ttu-id="fe133-221">16.04 +</span><span class="sxs-lookup"><span data-stu-id="fe133-221">16.04+</span></span>                | <span data-ttu-id="fe133-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="fe133-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="fe133-223">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-223">Linux Mint</span></span>                     | <span data-ttu-id="fe133-224">18 +</span><span class="sxs-lookup"><span data-stu-id="fe133-224">18+</span></span>                   | <span data-ttu-id="fe133-225">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-225">x64</span></span> |
| <span data-ttu-id="fe133-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="fe133-226">openSUSE</span></span>                       | <span data-ttu-id="fe133-227">15 +</span><span class="sxs-lookup"><span data-stu-id="fe133-227">15+</span></span>                   | <span data-ttu-id="fe133-228">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-228">x64</span></span> |
| <span data-ttu-id="fe133-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="fe133-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="fe133-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="fe133-230">12 SP2+</span></span>               | <span data-ttu-id="fe133-231">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-231">x64</span></span> |
| <span data-ttu-id="fe133-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-232">Alpine Linux</span></span>                   | <span data-ttu-id="fe133-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="fe133-233">3.10+</span></span>                 | <span data-ttu-id="fe133-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="fe133-234">x64, ARM64</span></span> |

<span data-ttu-id="fe133-235">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="fe133-236">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,1 w systemie ARM64 (jądro 4.14 +), zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="fe133-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fe133-237">Obsługa ARM64 wymaga jądra systemu Linux 4,14 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="fe133-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="fe133-238">Niektóre dystrybucje systemu Linux spełniają to wymaganie, a inne nie.</span><span class="sxs-lookup"><span data-stu-id="fe133-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="fe133-239">Na przykład Ubuntu 18,04 jest obsługiwany, ale Ubuntu 16,04 nie jest.</span><span class="sxs-lookup"><span data-stu-id="fe133-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="fe133-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fe133-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="fe133-241">Program .NET Core 3,0 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="fe133-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="fe133-242">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="fe133-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="fe133-243">Platforma .NET Core 3,0 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="fe133-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="fe133-244">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="fe133-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fe133-245">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="fe133-245">OS</span></span>                             | <span data-ttu-id="fe133-246">Wersja</span><span class="sxs-lookup"><span data-stu-id="fe133-246">Version</span></span>               | <span data-ttu-id="fe133-247">Architektury</span><span class="sxs-lookup"><span data-stu-id="fe133-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="fe133-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="fe133-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="fe133-249">6, 7, 8</span></span>               | <span data-ttu-id="fe133-250">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-250">x64</span></span> |
| <span data-ttu-id="fe133-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="fe133-251">CentOS</span></span>                         | <span data-ttu-id="fe133-252">7+</span><span class="sxs-lookup"><span data-stu-id="fe133-252">7+</span></span>                    | <span data-ttu-id="fe133-253">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-253">x64</span></span> |
| <span data-ttu-id="fe133-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-254">Oracle Linux</span></span>                   | <span data-ttu-id="fe133-255">7+</span><span class="sxs-lookup"><span data-stu-id="fe133-255">7+</span></span>                    | <span data-ttu-id="fe133-256">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-256">x64</span></span> |
| <span data-ttu-id="fe133-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="fe133-257">Fedora</span></span>                         | <span data-ttu-id="fe133-258">29 +</span><span class="sxs-lookup"><span data-stu-id="fe133-258">29+</span></span>                   | <span data-ttu-id="fe133-259">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-259">x64</span></span> |
| <span data-ttu-id="fe133-260">Debian</span><span class="sxs-lookup"><span data-stu-id="fe133-260">Debian</span></span>                         | <span data-ttu-id="fe133-261">9+</span><span class="sxs-lookup"><span data-stu-id="fe133-261">9+</span></span>                    | <span data-ttu-id="fe133-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="fe133-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="fe133-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fe133-263">Ubuntu</span></span>                         | <span data-ttu-id="fe133-264">16.04 +</span><span class="sxs-lookup"><span data-stu-id="fe133-264">16.04+</span></span>                | <span data-ttu-id="fe133-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="fe133-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="fe133-266">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-266">Linux Mint</span></span>                     | <span data-ttu-id="fe133-267">18 +</span><span class="sxs-lookup"><span data-stu-id="fe133-267">18+</span></span>                   | <span data-ttu-id="fe133-268">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-268">x64</span></span> |
| <span data-ttu-id="fe133-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="fe133-269">openSUSE</span></span>                       | <span data-ttu-id="fe133-270">15 +</span><span class="sxs-lookup"><span data-stu-id="fe133-270">15+</span></span>                   | <span data-ttu-id="fe133-271">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-271">x64</span></span> |
| <span data-ttu-id="fe133-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="fe133-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="fe133-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="fe133-273">12 SP2+</span></span>               | <span data-ttu-id="fe133-274">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-274">x64</span></span> |
| <span data-ttu-id="fe133-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-275">Alpine Linux</span></span>                   | <span data-ttu-id="fe133-276">3.8 +</span><span class="sxs-lookup"><span data-stu-id="fe133-276">3.8+</span></span>                  | <span data-ttu-id="fe133-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="fe133-277">x64, ARM64</span></span> |

<span data-ttu-id="fe133-278">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="fe133-279">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="fe133-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="fe133-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="fe133-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="fe133-281">Program .NET Core 2,2 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="fe133-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="fe133-282">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="fe133-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="fe133-283">Platforma .NET Core 2,2 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="fe133-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="fe133-284">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="fe133-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fe133-285">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="fe133-285">OS</span></span>                             |  <span data-ttu-id="fe133-286">Wersja</span><span class="sxs-lookup"><span data-stu-id="fe133-286">Version</span></span>                |  <span data-ttu-id="fe133-287">Architektury</span><span class="sxs-lookup"><span data-stu-id="fe133-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="fe133-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="fe133-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="fe133-289">6, 7</span></span>                   | <span data-ttu-id="fe133-290">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-290">x64</span></span> |
| <span data-ttu-id="fe133-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="fe133-291">CentOS</span></span>                         |  <span data-ttu-id="fe133-292">7</span><span class="sxs-lookup"><span data-stu-id="fe133-292">7</span></span>                      | <span data-ttu-id="fe133-293">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-293">x64</span></span> |
| <span data-ttu-id="fe133-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-294">Oracle Linux</span></span>                   |  <span data-ttu-id="fe133-295">7</span><span class="sxs-lookup"><span data-stu-id="fe133-295">7</span></span>                      | <span data-ttu-id="fe133-296">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-296">x64</span></span> |
| <span data-ttu-id="fe133-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="fe133-297">Fedora</span></span>                         |  <span data-ttu-id="fe133-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="fe133-298">29, 30</span></span>                 | <span data-ttu-id="fe133-299">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-299">x64</span></span> |
| <span data-ttu-id="fe133-300">Debian</span><span class="sxs-lookup"><span data-stu-id="fe133-300">Debian</span></span>                         |  <span data-ttu-id="fe133-301">9</span><span class="sxs-lookup"><span data-stu-id="fe133-301">9</span></span>                      | <span data-ttu-id="fe133-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fe133-302">x64, ARM32</span></span> |
| <span data-ttu-id="fe133-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fe133-303">Ubuntu</span></span>                         |  <span data-ttu-id="fe133-304">16,04, 18,04, 18,10, 19,04</span><span class="sxs-lookup"><span data-stu-id="fe133-304">16.04, 18.04, 18.10, 19.04</span></span>    | <span data-ttu-id="fe133-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fe133-305">x64, ARM32</span></span> |
| <span data-ttu-id="fe133-306">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-306">Linux Mint</span></span>                     |  <span data-ttu-id="fe133-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="fe133-307">17, 18</span></span>                 | <span data-ttu-id="fe133-308">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-308">x64</span></span> |
| <span data-ttu-id="fe133-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="fe133-309">openSUSE</span></span>                       |  <span data-ttu-id="fe133-310">15 +</span><span class="sxs-lookup"><span data-stu-id="fe133-310">15+</span></span>                    | <span data-ttu-id="fe133-311">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-311">x64</span></span> |
| <span data-ttu-id="fe133-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="fe133-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="fe133-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="fe133-313">12 SP2+</span></span>                | <span data-ttu-id="fe133-314">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-314">x64</span></span> |
| <span data-ttu-id="fe133-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-315">Alpine Linux</span></span>                   |  <span data-ttu-id="fe133-316">3.8 +</span><span class="sxs-lookup"><span data-stu-id="fe133-316">3.8+</span></span>                   | <span data-ttu-id="fe133-317">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-317">x64</span></span> |

<span data-ttu-id="fe133-318">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fe133-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fe133-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fe133-320">Program .NET Core 2,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="fe133-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="fe133-321">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="fe133-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="fe133-322">Platforma .NET Core 2,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="fe133-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="fe133-323">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="fe133-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fe133-324">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="fe133-324">OS</span></span>                             |  <span data-ttu-id="fe133-325">Wersja</span><span class="sxs-lookup"><span data-stu-id="fe133-325">Version</span></span>                |  <span data-ttu-id="fe133-326">Architektury</span><span class="sxs-lookup"><span data-stu-id="fe133-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="fe133-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="fe133-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="fe133-328">6, 7, 8</span></span>                | <span data-ttu-id="fe133-329">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-329">x64</span></span> |
| <span data-ttu-id="fe133-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="fe133-330">CentOS</span></span>                         |  <span data-ttu-id="fe133-331">7+</span><span class="sxs-lookup"><span data-stu-id="fe133-331">7+</span></span>                     | <span data-ttu-id="fe133-332">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-332">x64</span></span> |
| <span data-ttu-id="fe133-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-333">Oracle Linux</span></span>                   |  <span data-ttu-id="fe133-334">7+</span><span class="sxs-lookup"><span data-stu-id="fe133-334">7+</span></span>                     | <span data-ttu-id="fe133-335">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-335">x64</span></span> |
| <span data-ttu-id="fe133-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="fe133-336">Fedora</span></span>                         |  <span data-ttu-id="fe133-337">29 +</span><span class="sxs-lookup"><span data-stu-id="fe133-337">29+</span></span>                    | <span data-ttu-id="fe133-338">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-338">x64</span></span> |
| <span data-ttu-id="fe133-339">Debian</span><span class="sxs-lookup"><span data-stu-id="fe133-339">Debian</span></span>                         |  <span data-ttu-id="fe133-340">9</span><span class="sxs-lookup"><span data-stu-id="fe133-340">9</span></span>                      | <span data-ttu-id="fe133-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fe133-341">x64, ARM32</span></span> |
| <span data-ttu-id="fe133-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fe133-342">Ubuntu</span></span>                         |  <span data-ttu-id="fe133-343">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="fe133-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="fe133-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="fe133-344">x64, ARM32</span></span> |
| <span data-ttu-id="fe133-345">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-345">Linux Mint</span></span>                     |  <span data-ttu-id="fe133-346">17 +</span><span class="sxs-lookup"><span data-stu-id="fe133-346">17+</span></span>                    | <span data-ttu-id="fe133-347">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-347">x64</span></span> |
| <span data-ttu-id="fe133-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="fe133-348">openSUSE</span></span>                       |  <span data-ttu-id="fe133-349">15 +</span><span class="sxs-lookup"><span data-stu-id="fe133-349">15+</span></span>                    | <span data-ttu-id="fe133-350">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-350">x64</span></span> |
| <span data-ttu-id="fe133-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="fe133-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="fe133-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="fe133-352">12 SP2+</span></span>                | <span data-ttu-id="fe133-353">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-353">x64</span></span> |
| <span data-ttu-id="fe133-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-354">Alpine Linux</span></span>                   |  <span data-ttu-id="fe133-355">3.8 +</span><span class="sxs-lookup"><span data-stu-id="fe133-355">3.8+</span></span>                   | <span data-ttu-id="fe133-356">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-356">x64</span></span> |

<span data-ttu-id="fe133-357">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="fe133-358">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="fe133-358">Linux distribution dependencies</span></span>

<span data-ttu-id="fe133-359">W zależności od dystrybucji systemu Linux może być konieczne zainstalowanie dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="fe133-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fe133-360">Dokładne wersje i nazwy mogą się nieco różnić w zależności od wybranej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="fe133-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="fe133-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fe133-361">Ubuntu</span></span>

<span data-ttu-id="fe133-362">W przypadku dystrybucji Ubuntu wymagane jest zainstalowanie następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="fe133-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="fe133-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="fe133-363">liblttng-ust0</span></span>
- <span data-ttu-id="fe133-364">libcurl3 (dla 14. x i 16. x)</span><span class="sxs-lookup"><span data-stu-id="fe133-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="fe133-365">libcurl4 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="fe133-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="fe133-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="fe133-366">libssl1.0.0</span></span>
- <span data-ttu-id="fe133-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="fe133-367">libkrb5-3</span></span>
- <span data-ttu-id="fe133-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="fe133-368">zlib1g</span></span>
- <span data-ttu-id="fe133-369">libicu52 (dla 14. x)</span><span class="sxs-lookup"><span data-stu-id="fe133-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="fe133-370">libicu55 (dla 16. x)</span><span class="sxs-lookup"><span data-stu-id="fe133-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="fe133-371">libicu57 (dla 17. x)</span><span class="sxs-lookup"><span data-stu-id="fe133-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="fe133-372">libicu60 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="fe133-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="fe133-373">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:</span><span class="sxs-lookup"><span data-stu-id="fe133-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="fe133-374">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="fe133-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="fe133-375">Większość wersji programu Ubuntu obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="fe133-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="fe133-376">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="fe133-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="fe133-377">Aby uzyskać więcej informacji, zobacz temat <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="fe133-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="fe133-378">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="fe133-378">CentOS and Fedora</span></span>

<span data-ttu-id="fe133-379">Dystrybucje CentOS wymagają zainstalowanych następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="fe133-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="fe133-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="fe133-380">lttng-ust</span></span>
- <span data-ttu-id="fe133-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="fe133-381">libcurl</span></span>
- <span data-ttu-id="fe133-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="fe133-382">openssl-libs</span></span>
- <span data-ttu-id="fe133-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="fe133-383">krb5-libs</span></span>
- <span data-ttu-id="fe133-384">libicu</span><span class="sxs-lookup"><span data-stu-id="fe133-384">libicu</span></span>
- <span data-ttu-id="fe133-385">zlib</span><span class="sxs-lookup"><span data-stu-id="fe133-385">zlib</span></span>

<span data-ttu-id="fe133-386">Fedora użytkownicy: Jeśli OpenSSL wersja > = 1,1, należy zainstalować polecenie **COMPAT-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="fe133-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="fe133-387">W przypadku platformy .NET Core 2,0 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="fe133-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="fe133-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="fe133-388">libunwind</span></span>
- <span data-ttu-id="fe133-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="fe133-389">libuuid</span></span>

<span data-ttu-id="fe133-390">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="fe133-391">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="fe133-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="fe133-392">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="fe133-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="fe133-393">Większość wersji CentOS i Fedora obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="fe133-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="fe133-394">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="fe133-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="fe133-395">Aby uzyskać więcej informacji, zobacz temat <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="fe133-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="fe133-396">Platforma .NET Core jest obsługiwana w następujących wersjach macOS:</span><span class="sxs-lookup"><span data-stu-id="fe133-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="fe133-397">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="fe133-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="fe133-398">Wersja platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="fe133-398">.NET Core Version</span></span> | <span data-ttu-id="fe133-399">macOS</span><span class="sxs-lookup"><span data-stu-id="fe133-399">macOS</span></span>                 | <span data-ttu-id="fe133-400">Architektury</span><span class="sxs-lookup"><span data-stu-id="fe133-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="fe133-401">3.1</span><span class="sxs-lookup"><span data-stu-id="fe133-401">3.1</span></span>               | <span data-ttu-id="fe133-402">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="fe133-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="fe133-403">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-403">x64</span></span> | [<span data-ttu-id="fe133-404">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="fe133-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="fe133-405">3.0</span><span class="sxs-lookup"><span data-stu-id="fe133-405">3.0</span></span>               | <span data-ttu-id="fe133-406">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="fe133-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="fe133-407">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-407">x64</span></span> | [<span data-ttu-id="fe133-408">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="fe133-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="fe133-409">2.2</span><span class="sxs-lookup"><span data-stu-id="fe133-409">2.2</span></span>               | <span data-ttu-id="fe133-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="fe133-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="fe133-411">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-411">x64</span></span> | [<span data-ttu-id="fe133-412">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="fe133-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="fe133-413">2.1</span><span class="sxs-lookup"><span data-stu-id="fe133-413">2.1</span></span>               | <span data-ttu-id="fe133-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="fe133-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="fe133-415">X64</span><span class="sxs-lookup"><span data-stu-id="fe133-415">x64</span></span> | [<span data-ttu-id="fe133-416">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="fe133-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="fe133-417">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="fe133-417">libgdiplus</span></span>

<span data-ttu-id="fe133-418">Aplikacje .NET Core używające zestawu *System. Drawing. Common* wymagają zainstalowania libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="fe133-418">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="fe133-419">Łatwym sposobem uzyskania libgdiplus jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS.</span><span class="sxs-lookup"><span data-stu-id="fe133-419">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="fe133-420">Po zainstalowaniu *rozwiązania brew*Zainstaluj libgdiplus, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="fe133-420">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="fe133-421">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fe133-421">Next steps</span></span>

- <span data-ttu-id="fe133-422">Aby opracowywać i uruchamiać aplikacje, zainstaluj [zestaw .NET Core SDK](sdk.md) (w tym środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="fe133-422">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="fe133-423">Aby uruchamiać aplikacje utworzone przez inne osoby, zainstaluj [środowisko uruchomieniowe programu .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="fe133-423">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
