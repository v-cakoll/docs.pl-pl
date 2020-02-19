---
title: Zależności zestaw .NET Core SDK i środowiska uruchomieniowego — .NET Core
description: Szczegółowe informacje na temat wymagań wstępnych dotyczących architektury procesora i systemu operacyjnego w celu zainstalowania zestaw .NET Core SDK i środowiska uruchomieniowego w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 4164ea5a04d80ab20109168a225b793b02ee616a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448896"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="ccc79-103">Zależności i wymagania dotyczące platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ccc79-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="ccc79-104">W tym artykule szczegółowo przedstawiono systemy operacyjne i architekturę procesora CPU obsługiwane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ccc79-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="ccc79-105">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="ccc79-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="ccc79-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ccc79-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="ccc79-107">W przypadku programu .NET Core 3,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="ccc79-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="ccc79-108">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="ccc79-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ccc79-109">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="ccc79-109">OS</span></span>                            | <span data-ttu-id="ccc79-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="ccc79-110">Version</span></span>                        | <span data-ttu-id="ccc79-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="ccc79-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ccc79-112">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ccc79-112">Windows Client</span></span>                | <span data-ttu-id="ccc79-113">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="ccc79-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ccc79-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-114">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-115">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="ccc79-115">Windows 10 Client</span></span>             | <span data-ttu-id="ccc79-116">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-116">Version 1607+</span></span>                  | <span data-ttu-id="ccc79-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-117">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-118">Oprogramowanie Windows Server</span><span class="sxs-lookup"><span data-stu-id="ccc79-118">Windows Server</span></span>                | <span data-ttu-id="ccc79-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-119">2012 R2+</span></span>                       | <span data-ttu-id="ccc79-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-120">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ccc79-121">Nano Server</span></span>                   | <span data-ttu-id="ccc79-122">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-122">Version 1803+</span></span>                  | <span data-ttu-id="ccc79-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ccc79-123">x64, ARM32</span></span>      |

<span data-ttu-id="ccc79-124">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="ccc79-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ccc79-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="ccc79-126">W przypadku programu .NET Core 3,0 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="ccc79-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="ccc79-127">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="ccc79-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ccc79-128">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="ccc79-128">OS</span></span>                            | <span data-ttu-id="ccc79-129">Wersja</span><span class="sxs-lookup"><span data-stu-id="ccc79-129">Version</span></span>                        | <span data-ttu-id="ccc79-130">Architektury</span><span class="sxs-lookup"><span data-stu-id="ccc79-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ccc79-131">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ccc79-131">Windows Client</span></span>                | <span data-ttu-id="ccc79-132">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="ccc79-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ccc79-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-133">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-134">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="ccc79-134">Windows 10 Client</span></span>             | <span data-ttu-id="ccc79-135">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-135">Version 1607+</span></span>                  | <span data-ttu-id="ccc79-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-136">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-137">Oprogramowanie Windows Server</span><span class="sxs-lookup"><span data-stu-id="ccc79-137">Windows Server</span></span>                | <span data-ttu-id="ccc79-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-138">2012 R2+</span></span>                       | <span data-ttu-id="ccc79-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-139">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ccc79-140">Nano Server</span></span>                   | <span data-ttu-id="ccc79-141">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-141">Version 1803+</span></span>                  | <span data-ttu-id="ccc79-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ccc79-142">x64, ARM32</span></span>      |

<span data-ttu-id="ccc79-143">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="ccc79-144">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="ccc79-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="ccc79-145">W przypadku programu .NET Core 2,2 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="ccc79-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="ccc79-146">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="ccc79-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ccc79-147">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="ccc79-147">OS</span></span>                            | <span data-ttu-id="ccc79-148">Wersja</span><span class="sxs-lookup"><span data-stu-id="ccc79-148">Version</span></span>                        | <span data-ttu-id="ccc79-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="ccc79-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ccc79-150">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ccc79-150">Windows Client</span></span>                | <span data-ttu-id="ccc79-151">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="ccc79-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ccc79-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-152">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-153">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="ccc79-153">Windows 10 Client</span></span>             | <span data-ttu-id="ccc79-154">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-154">Version 1607+</span></span>                  | <span data-ttu-id="ccc79-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-155">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-156">Oprogramowanie Windows Server</span><span class="sxs-lookup"><span data-stu-id="ccc79-156">Windows Server</span></span>                | <span data-ttu-id="ccc79-157">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="ccc79-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-158">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ccc79-159">Nano Server</span></span>                   | <span data-ttu-id="ccc79-160">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-160">Version 1803+</span></span>                   | <span data-ttu-id="ccc79-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ccc79-161">x64, ARM32</span></span>      |

<span data-ttu-id="ccc79-162">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="ccc79-163">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="ccc79-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ccc79-164">W przypadku programu .NET Core 2,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="ccc79-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="ccc79-165">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="ccc79-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ccc79-166">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="ccc79-166">OS</span></span>                            | <span data-ttu-id="ccc79-167">Wersja</span><span class="sxs-lookup"><span data-stu-id="ccc79-167">Version</span></span>                        | <span data-ttu-id="ccc79-168">Architektury</span><span class="sxs-lookup"><span data-stu-id="ccc79-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ccc79-169">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ccc79-169">Windows Client</span></span>                | <span data-ttu-id="ccc79-170">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="ccc79-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ccc79-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-171">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-172">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="ccc79-172">Windows 10 Client</span></span>             | <span data-ttu-id="ccc79-173">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-173">Version 1607+</span></span>                  | <span data-ttu-id="ccc79-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-174">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-175">Oprogramowanie Windows Server</span><span class="sxs-lookup"><span data-stu-id="ccc79-175">Windows Server</span></span>                | <span data-ttu-id="ccc79-176">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="ccc79-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ccc79-177">x64, x86</span></span>        |
| <span data-ttu-id="ccc79-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ccc79-178">Nano Server</span></span>                   | <span data-ttu-id="ccc79-179">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-179">Version 1803+</span></span>                  | <span data-ttu-id="ccc79-180">procesorów</span><span class="sxs-lookup"><span data-stu-id="ccc79-180">x64,</span></span>            |

<span data-ttu-id="ccc79-181">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="ccc79-182">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ccc79-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="ccc79-183">Jeśli instalujesz zestaw .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows, wymagane są dodatkowe zależności:</span><span class="sxs-lookup"><span data-stu-id="ccc79-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="ccc79-184">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="ccc79-184">Windows 7 SP1</span></span>
- <span data-ttu-id="ccc79-185">Windows Vista z dodatkiem SP 2</span><span class="sxs-lookup"><span data-stu-id="ccc79-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="ccc79-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ccc79-186">Windows 8.1</span></span>
- <span data-ttu-id="ccc79-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ccc79-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="ccc79-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ccc79-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="ccc79-189">Zainstaluj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ccc79-189">Install the following:</span></span>

- <span data-ttu-id="ccc79-190">Pakiet [redystrybucyjny Microsoft Visual C++ 2015 z aktualizacją Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="ccc79-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="ccc79-191">POPRAWKI KB2533623</span><span class="sxs-lookup"><span data-stu-id="ccc79-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="ccc79-192">Powyższe wymagania są również wymagane w przypadku wystąpienia jednego z następujących błędów:</span><span class="sxs-lookup"><span data-stu-id="ccc79-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="ccc79-193">Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-CRT-Runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="ccc79-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="ccc79-194">Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="ccc79-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="ccc79-195">\- lub-</span><span class="sxs-lookup"><span data-stu-id="ccc79-195">\- or -</span></span>
>
> <span data-ttu-id="ccc79-196">Znaleziono bibliotekę *hostfxr. dll* , ale ładowanie jej z *dysku C:\\\<path_to_app >\\hostfxr. dll* nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="ccc79-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="ccc79-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ccc79-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="ccc79-198">Program .NET Core 3,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ccc79-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="ccc79-199">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ccc79-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="ccc79-200">Platforma .NET Core 3,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="ccc79-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="ccc79-201">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="ccc79-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ccc79-202">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="ccc79-202">OS</span></span>                             | <span data-ttu-id="ccc79-203">Wersja</span><span class="sxs-lookup"><span data-stu-id="ccc79-203">Version</span></span>               | <span data-ttu-id="ccc79-204">Architektury</span><span class="sxs-lookup"><span data-stu-id="ccc79-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="ccc79-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="ccc79-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="ccc79-206">6, 7, 8</span></span>               | <span data-ttu-id="ccc79-207">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-207">x64</span></span> |
| <span data-ttu-id="ccc79-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="ccc79-208">CentOS</span></span>                         | <span data-ttu-id="ccc79-209">7+</span><span class="sxs-lookup"><span data-stu-id="ccc79-209">7+</span></span>                    | <span data-ttu-id="ccc79-210">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-210">x64</span></span> |
| <span data-ttu-id="ccc79-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-211">Oracle Linux</span></span>                   | <span data-ttu-id="ccc79-212">7+</span><span class="sxs-lookup"><span data-stu-id="ccc79-212">7+</span></span>                    | <span data-ttu-id="ccc79-213">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-213">x64</span></span> |
| <span data-ttu-id="ccc79-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="ccc79-214">Fedora</span></span>                         | <span data-ttu-id="ccc79-215">29 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-215">29+</span></span>                   | <span data-ttu-id="ccc79-216">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-216">x64</span></span> |
| <span data-ttu-id="ccc79-217">Debian</span><span class="sxs-lookup"><span data-stu-id="ccc79-217">Debian</span></span>                         | <span data-ttu-id="ccc79-218">9+</span><span class="sxs-lookup"><span data-stu-id="ccc79-218">9+</span></span>                    | <span data-ttu-id="ccc79-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="ccc79-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="ccc79-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ccc79-220">Ubuntu</span></span>                         | <span data-ttu-id="ccc79-221">16.04 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-221">16.04+</span></span>                | <span data-ttu-id="ccc79-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="ccc79-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="ccc79-223">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-223">Linux Mint</span></span>                     | <span data-ttu-id="ccc79-224">18 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-224">18+</span></span>                   | <span data-ttu-id="ccc79-225">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-225">x64</span></span> |
| <span data-ttu-id="ccc79-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ccc79-226">openSUSE</span></span>                       | <span data-ttu-id="ccc79-227">15 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-227">15+</span></span>                   | <span data-ttu-id="ccc79-228">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-228">x64</span></span> |
| <span data-ttu-id="ccc79-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="ccc79-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="ccc79-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="ccc79-230">12 SP2+</span></span>               | <span data-ttu-id="ccc79-231">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-231">x64</span></span> |
| <span data-ttu-id="ccc79-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-232">Alpine Linux</span></span>                   | <span data-ttu-id="ccc79-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-233">3.10+</span></span>                 | <span data-ttu-id="ccc79-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="ccc79-234">x64, ARM64</span></span> |

<span data-ttu-id="ccc79-235">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="ccc79-236">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,1 w systemie ARM64 (jądro 4.14 +), zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="ccc79-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ccc79-237">Obsługa ARM64 wymaga jądra systemu Linux 4,14 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="ccc79-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="ccc79-238">Niektóre dystrybucje systemu Linux spełniają to wymaganie, a inne nie.</span><span class="sxs-lookup"><span data-stu-id="ccc79-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="ccc79-239">Na przykład Ubuntu 18,04 jest obsługiwany, ale Ubuntu 16,04 nie jest.</span><span class="sxs-lookup"><span data-stu-id="ccc79-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="ccc79-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ccc79-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="ccc79-241">Program .NET Core 3,0 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ccc79-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="ccc79-242">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ccc79-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="ccc79-243">Platforma .NET Core 3,0 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="ccc79-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="ccc79-244">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="ccc79-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ccc79-245">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="ccc79-245">OS</span></span>                             | <span data-ttu-id="ccc79-246">Wersja</span><span class="sxs-lookup"><span data-stu-id="ccc79-246">Version</span></span>               | <span data-ttu-id="ccc79-247">Architektury</span><span class="sxs-lookup"><span data-stu-id="ccc79-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="ccc79-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="ccc79-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="ccc79-249">6, 7, 8</span></span>               | <span data-ttu-id="ccc79-250">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-250">x64</span></span> |
| <span data-ttu-id="ccc79-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="ccc79-251">CentOS</span></span>                         | <span data-ttu-id="ccc79-252">7+</span><span class="sxs-lookup"><span data-stu-id="ccc79-252">7+</span></span>                    | <span data-ttu-id="ccc79-253">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-253">x64</span></span> |
| <span data-ttu-id="ccc79-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-254">Oracle Linux</span></span>                   | <span data-ttu-id="ccc79-255">7+</span><span class="sxs-lookup"><span data-stu-id="ccc79-255">7+</span></span>                    | <span data-ttu-id="ccc79-256">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-256">x64</span></span> |
| <span data-ttu-id="ccc79-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="ccc79-257">Fedora</span></span>                         | <span data-ttu-id="ccc79-258">29 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-258">29+</span></span>                   | <span data-ttu-id="ccc79-259">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-259">x64</span></span> |
| <span data-ttu-id="ccc79-260">Debian</span><span class="sxs-lookup"><span data-stu-id="ccc79-260">Debian</span></span>                         | <span data-ttu-id="ccc79-261">9+</span><span class="sxs-lookup"><span data-stu-id="ccc79-261">9+</span></span>                    | <span data-ttu-id="ccc79-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="ccc79-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="ccc79-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ccc79-263">Ubuntu</span></span>                         | <span data-ttu-id="ccc79-264">16.04 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-264">16.04+</span></span>                | <span data-ttu-id="ccc79-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="ccc79-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="ccc79-266">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-266">Linux Mint</span></span>                     | <span data-ttu-id="ccc79-267">18 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-267">18+</span></span>                   | <span data-ttu-id="ccc79-268">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-268">x64</span></span> |
| <span data-ttu-id="ccc79-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ccc79-269">openSUSE</span></span>                       | <span data-ttu-id="ccc79-270">15 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-270">15+</span></span>                   | <span data-ttu-id="ccc79-271">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-271">x64</span></span> |
| <span data-ttu-id="ccc79-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="ccc79-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="ccc79-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="ccc79-273">12 SP2+</span></span>               | <span data-ttu-id="ccc79-274">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-274">x64</span></span> |
| <span data-ttu-id="ccc79-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-275">Alpine Linux</span></span>                   | <span data-ttu-id="ccc79-276">3.8 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-276">3.8+</span></span>                  | <span data-ttu-id="ccc79-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="ccc79-277">x64, ARM64</span></span> |

<span data-ttu-id="ccc79-278">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="ccc79-279">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="ccc79-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="ccc79-280">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="ccc79-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="ccc79-281">Program .NET Core 2,2 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ccc79-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="ccc79-282">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ccc79-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="ccc79-283">Platforma .NET Core 2,2 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="ccc79-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="ccc79-284">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="ccc79-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ccc79-285">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="ccc79-285">OS</span></span>                             |  <span data-ttu-id="ccc79-286">Wersja</span><span class="sxs-lookup"><span data-stu-id="ccc79-286">Version</span></span>                |  <span data-ttu-id="ccc79-287">Architektury</span><span class="sxs-lookup"><span data-stu-id="ccc79-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="ccc79-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="ccc79-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="ccc79-289">6, 7</span></span>                   | <span data-ttu-id="ccc79-290">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-290">x64</span></span> |
| <span data-ttu-id="ccc79-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="ccc79-291">CentOS</span></span>                         |  <span data-ttu-id="ccc79-292">7</span><span class="sxs-lookup"><span data-stu-id="ccc79-292">7</span></span>                      | <span data-ttu-id="ccc79-293">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-293">x64</span></span> |
| <span data-ttu-id="ccc79-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-294">Oracle Linux</span></span>                   |  <span data-ttu-id="ccc79-295">7</span><span class="sxs-lookup"><span data-stu-id="ccc79-295">7</span></span>                      | <span data-ttu-id="ccc79-296">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-296">x64</span></span> |
| <span data-ttu-id="ccc79-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="ccc79-297">Fedora</span></span>                         |  <span data-ttu-id="ccc79-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="ccc79-298">29, 30</span></span>                 | <span data-ttu-id="ccc79-299">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-299">x64</span></span> |
| <span data-ttu-id="ccc79-300">Debian</span><span class="sxs-lookup"><span data-stu-id="ccc79-300">Debian</span></span>                         |  <span data-ttu-id="ccc79-301">9</span><span class="sxs-lookup"><span data-stu-id="ccc79-301">9</span></span>                      | <span data-ttu-id="ccc79-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ccc79-302">x64, ARM32</span></span> |
| <span data-ttu-id="ccc79-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ccc79-303">Ubuntu</span></span>                         |  <span data-ttu-id="ccc79-304">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="ccc79-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="ccc79-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ccc79-305">x64, ARM32</span></span> |
| <span data-ttu-id="ccc79-306">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-306">Linux Mint</span></span>                     |  <span data-ttu-id="ccc79-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="ccc79-307">17, 18</span></span>                 | <span data-ttu-id="ccc79-308">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-308">x64</span></span> |
| <span data-ttu-id="ccc79-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ccc79-309">openSUSE</span></span>                       |  <span data-ttu-id="ccc79-310">15 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-310">15+</span></span>                    | <span data-ttu-id="ccc79-311">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-311">x64</span></span> |
| <span data-ttu-id="ccc79-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="ccc79-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="ccc79-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="ccc79-313">12 SP2+</span></span>                | <span data-ttu-id="ccc79-314">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-314">x64</span></span> |
| <span data-ttu-id="ccc79-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-315">Alpine Linux</span></span>                   |  <span data-ttu-id="ccc79-316">3.8 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-316">3.8+</span></span>                   | <span data-ttu-id="ccc79-317">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-317">x64</span></span> |

<span data-ttu-id="ccc79-318">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="ccc79-319">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="ccc79-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ccc79-320">Program .NET Core 2,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ccc79-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="ccc79-321">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ccc79-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="ccc79-322">Platforma .NET Core 2,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="ccc79-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="ccc79-323">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="ccc79-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ccc79-324">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="ccc79-324">OS</span></span>                             |  <span data-ttu-id="ccc79-325">Wersja</span><span class="sxs-lookup"><span data-stu-id="ccc79-325">Version</span></span>                |  <span data-ttu-id="ccc79-326">Architektury</span><span class="sxs-lookup"><span data-stu-id="ccc79-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="ccc79-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="ccc79-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="ccc79-328">6, 7, 8</span></span>                | <span data-ttu-id="ccc79-329">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-329">x64</span></span> |
| <span data-ttu-id="ccc79-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="ccc79-330">CentOS</span></span>                         |  <span data-ttu-id="ccc79-331">7+</span><span class="sxs-lookup"><span data-stu-id="ccc79-331">7+</span></span>                     | <span data-ttu-id="ccc79-332">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-332">x64</span></span> |
| <span data-ttu-id="ccc79-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-333">Oracle Linux</span></span>                   |  <span data-ttu-id="ccc79-334">7+</span><span class="sxs-lookup"><span data-stu-id="ccc79-334">7+</span></span>                     | <span data-ttu-id="ccc79-335">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-335">x64</span></span> |
| <span data-ttu-id="ccc79-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="ccc79-336">Fedora</span></span>                         |  <span data-ttu-id="ccc79-337">29 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-337">29+</span></span>                    | <span data-ttu-id="ccc79-338">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-338">x64</span></span> |
| <span data-ttu-id="ccc79-339">Debian</span><span class="sxs-lookup"><span data-stu-id="ccc79-339">Debian</span></span>                         |  <span data-ttu-id="ccc79-340">9</span><span class="sxs-lookup"><span data-stu-id="ccc79-340">9</span></span>                      | <span data-ttu-id="ccc79-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ccc79-341">x64, ARM32</span></span> |
| <span data-ttu-id="ccc79-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ccc79-342">Ubuntu</span></span>                         |  <span data-ttu-id="ccc79-343">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="ccc79-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="ccc79-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ccc79-344">x64, ARM32</span></span> |
| <span data-ttu-id="ccc79-345">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-345">Linux Mint</span></span>                     |  <span data-ttu-id="ccc79-346">17 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-346">17+</span></span>                    | <span data-ttu-id="ccc79-347">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-347">x64</span></span> |
| <span data-ttu-id="ccc79-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ccc79-348">openSUSE</span></span>                       |  <span data-ttu-id="ccc79-349">15 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-349">15+</span></span>                    | <span data-ttu-id="ccc79-350">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-350">x64</span></span> |
| <span data-ttu-id="ccc79-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="ccc79-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="ccc79-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="ccc79-352">12 SP2+</span></span>                | <span data-ttu-id="ccc79-353">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-353">x64</span></span> |
| <span data-ttu-id="ccc79-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-354">Alpine Linux</span></span>                   |  <span data-ttu-id="ccc79-355">3.8 +</span><span class="sxs-lookup"><span data-stu-id="ccc79-355">3.8+</span></span>                   | <span data-ttu-id="ccc79-356">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-356">x64</span></span> |

<span data-ttu-id="ccc79-357">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="ccc79-358">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="ccc79-358">Linux distribution dependencies</span></span>

<span data-ttu-id="ccc79-359">W zależności od dystrybucji systemu Linux może być konieczne zainstalowanie dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="ccc79-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ccc79-360">Dokładne wersje i nazwy mogą się nieco różnić w zależności od wybranej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ccc79-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="ccc79-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ccc79-361">Ubuntu</span></span>

<span data-ttu-id="ccc79-362">W przypadku dystrybucji Ubuntu wymagane jest zainstalowanie następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="ccc79-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="ccc79-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="ccc79-363">liblttng-ust0</span></span>
- <span data-ttu-id="ccc79-364">libcurl3 (dla 14. x i 16. x)</span><span class="sxs-lookup"><span data-stu-id="ccc79-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="ccc79-365">libcurl4 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="ccc79-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="ccc79-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="ccc79-366">libssl1.0.0</span></span>
- <span data-ttu-id="ccc79-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="ccc79-367">libkrb5-3</span></span>
- <span data-ttu-id="ccc79-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="ccc79-368">zlib1g</span></span>
- <span data-ttu-id="ccc79-369">libicu52 (dla 14. x)</span><span class="sxs-lookup"><span data-stu-id="ccc79-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="ccc79-370">libicu55 (dla 16. x)</span><span class="sxs-lookup"><span data-stu-id="ccc79-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="ccc79-371">libicu57 (dla 17. x)</span><span class="sxs-lookup"><span data-stu-id="ccc79-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="ccc79-372">libicu60 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="ccc79-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="ccc79-373">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:</span><span class="sxs-lookup"><span data-stu-id="ccc79-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="ccc79-374">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="ccc79-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="ccc79-375">Większość wersji programu Ubuntu obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="ccc79-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="ccc79-376">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="ccc79-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="ccc79-377">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="ccc79-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="ccc79-378">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="ccc79-378">CentOS and Fedora</span></span>

<span data-ttu-id="ccc79-379">Dystrybucje CentOS wymagają zainstalowanych następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="ccc79-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="ccc79-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="ccc79-380">lttng-ust</span></span>
- <span data-ttu-id="ccc79-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="ccc79-381">libcurl</span></span>
- <span data-ttu-id="ccc79-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="ccc79-382">openssl-libs</span></span>
- <span data-ttu-id="ccc79-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="ccc79-383">krb5-libs</span></span>
- <span data-ttu-id="ccc79-384">libicu</span><span class="sxs-lookup"><span data-stu-id="ccc79-384">libicu</span></span>
- <span data-ttu-id="ccc79-385">zlib</span><span class="sxs-lookup"><span data-stu-id="ccc79-385">zlib</span></span>

<span data-ttu-id="ccc79-386">Fedora użytkownicy: Jeśli OpenSSL wersja > = 1,1, należy zainstalować polecenie **COMPAT-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="ccc79-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="ccc79-387">W przypadku platformy .NET Core 2,0 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="ccc79-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="ccc79-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="ccc79-388">libunwind</span></span>
- <span data-ttu-id="ccc79-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="ccc79-389">libuuid</span></span>

<span data-ttu-id="ccc79-390">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="ccc79-391">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="ccc79-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="ccc79-392">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="ccc79-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="ccc79-393">Większość wersji CentOS i Fedora obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="ccc79-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="ccc79-394">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="ccc79-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="ccc79-395">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="ccc79-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="ccc79-396">Platforma .NET Core jest obsługiwana w następujących wersjach macOS:</span><span class="sxs-lookup"><span data-stu-id="ccc79-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="ccc79-397">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="ccc79-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ccc79-398">Wersja platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ccc79-398">.NET Core Version</span></span> | <span data-ttu-id="ccc79-399">macOS</span><span class="sxs-lookup"><span data-stu-id="ccc79-399">macOS</span></span>                 | <span data-ttu-id="ccc79-400">Architektury</span><span class="sxs-lookup"><span data-stu-id="ccc79-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="ccc79-401">3.1</span><span class="sxs-lookup"><span data-stu-id="ccc79-401">3.1</span></span>               | <span data-ttu-id="ccc79-402">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="ccc79-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="ccc79-403">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-403">x64</span></span> | [<span data-ttu-id="ccc79-404">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="ccc79-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="ccc79-405">3.0</span><span class="sxs-lookup"><span data-stu-id="ccc79-405">3.0</span></span>               | <span data-ttu-id="ccc79-406">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="ccc79-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="ccc79-407">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-407">x64</span></span> | [<span data-ttu-id="ccc79-408">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="ccc79-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="ccc79-409">2.2</span><span class="sxs-lookup"><span data-stu-id="ccc79-409">2.2</span></span>               | <span data-ttu-id="ccc79-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="ccc79-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="ccc79-411">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-411">x64</span></span> | [<span data-ttu-id="ccc79-412">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="ccc79-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="ccc79-413">2.1</span><span class="sxs-lookup"><span data-stu-id="ccc79-413">2.1</span></span>               | <span data-ttu-id="ccc79-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="ccc79-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="ccc79-415">x64</span><span class="sxs-lookup"><span data-stu-id="ccc79-415">x64</span></span> | [<span data-ttu-id="ccc79-416">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="ccc79-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="ccc79-417">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="ccc79-417">libgdiplus</span></span>

<span data-ttu-id="ccc79-418">Aplikacje .NET Core używające zestawu *System. Drawing. Common* wymagają zainstalowania libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="ccc79-418">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="ccc79-419">Łatwym sposobem uzyskania libgdiplus jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS.</span><span class="sxs-lookup"><span data-stu-id="ccc79-419">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="ccc79-420">Po zainstalowaniu *rozwiązania brew*Zainstaluj libgdiplus, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="ccc79-420">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="ccc79-421">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ccc79-421">Next steps</span></span>

- <span data-ttu-id="ccc79-422">Aby opracowywać i uruchamiać aplikacje, zainstaluj [zestaw .NET Core SDK](sdk.md) (w tym środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="ccc79-422">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="ccc79-423">Aby uruchamiać aplikacje utworzone przez inne osoby, zainstaluj [środowisko uruchomieniowe programu .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="ccc79-423">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
