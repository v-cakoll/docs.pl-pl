---
title: Zależności sdk i runtime programu .NET Core — .NET Core
description: Szczegóły systemu operacyjnego i architektury procesora CPU wymagania wstępne do zainstalowania .NET Core SDK i środowiska uruchomieniowego w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157816"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="5bfe9-103">Zależności i wymagania programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="5bfe9-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="5bfe9-104">W tym artykule opisano, które systemy operacyjne i architektura procesora są obsługiwane przez program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="5bfe9-105">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="5bfe9-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="5bfe9-106">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="5bfe9-107">Następujące wersje systemu Windows są obsługiwane z .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="5bfe9-108">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5bfe9-109">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="5bfe9-109">OS</span></span>                            | <span data-ttu-id="5bfe9-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="5bfe9-110">Version</span></span>                        | <span data-ttu-id="5bfe9-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="5bfe9-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5bfe9-112">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5bfe9-112">Windows Client</span></span>                | <span data-ttu-id="5bfe9-113">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5bfe9-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-114">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-115">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="5bfe9-115">Windows 10 Client</span></span>             | <span data-ttu-id="5bfe9-116">Wersja 1607+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-116">Version 1607+</span></span>                  | <span data-ttu-id="5bfe9-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-117">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5bfe9-118">Windows Server</span></span>                | <span data-ttu-id="5bfe9-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-119">2012 R2+</span></span>                       | <span data-ttu-id="5bfe9-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-120">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5bfe9-121">Nano Server</span></span>                   | <span data-ttu-id="5bfe9-122">Wersja 1803+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-122">Version 1803+</span></span>                  | <span data-ttu-id="5bfe9-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5bfe9-123">x64, ARM32</span></span>      |

<span data-ttu-id="5bfe9-124">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3.1, zobacz [.NET Core 3.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="5bfe9-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5bfe9-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="5bfe9-126">Następujące wersje systemu Windows są obsługiwane z .NET Core 3.0:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="5bfe9-127">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5bfe9-128">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="5bfe9-128">OS</span></span>                            | <span data-ttu-id="5bfe9-129">Wersja</span><span class="sxs-lookup"><span data-stu-id="5bfe9-129">Version</span></span>                        | <span data-ttu-id="5bfe9-130">Architektury</span><span class="sxs-lookup"><span data-stu-id="5bfe9-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5bfe9-131">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5bfe9-131">Windows Client</span></span>                | <span data-ttu-id="5bfe9-132">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5bfe9-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-133">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-134">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="5bfe9-134">Windows 10 Client</span></span>             | <span data-ttu-id="5bfe9-135">Wersja 1607+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-135">Version 1607+</span></span>                  | <span data-ttu-id="5bfe9-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-136">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5bfe9-137">Windows Server</span></span>                | <span data-ttu-id="5bfe9-138">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-138">2012 R2+</span></span>                       | <span data-ttu-id="5bfe9-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-139">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5bfe9-140">Nano Server</span></span>                   | <span data-ttu-id="5bfe9-141">Wersja 1803+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-141">Version 1803+</span></span>                  | <span data-ttu-id="5bfe9-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5bfe9-142">x64, ARM32</span></span>      |

<span data-ttu-id="5bfe9-143">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3.0, zobacz [.NET Core 3.0 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="5bfe9-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5bfe9-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5bfe9-145">Następujące wersje systemu Windows są obsługiwane z .NET Core 2.2:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="5bfe9-146">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5bfe9-147">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="5bfe9-147">OS</span></span>                            | <span data-ttu-id="5bfe9-148">Wersja</span><span class="sxs-lookup"><span data-stu-id="5bfe9-148">Version</span></span>                        | <span data-ttu-id="5bfe9-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="5bfe9-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5bfe9-150">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5bfe9-150">Windows Client</span></span>                | <span data-ttu-id="5bfe9-151">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5bfe9-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-152">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-153">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="5bfe9-153">Windows 10 Client</span></span>             | <span data-ttu-id="5bfe9-154">Wersja 1607+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-154">Version 1607+</span></span>                  | <span data-ttu-id="5bfe9-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-155">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5bfe9-156">Windows Server</span></span>                | <span data-ttu-id="5bfe9-157">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="5bfe9-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-158">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5bfe9-159">Nano Server</span></span>                   | <span data-ttu-id="5bfe9-160">Wersja 1803+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-160">Version 1803+</span></span>                   | <span data-ttu-id="5bfe9-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5bfe9-161">x64, ARM32</span></span>      |

<span data-ttu-id="5bfe9-162">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2.2, zobacz [.NET Core 2.2 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="5bfe9-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5bfe9-164">Następujące wersje systemu Windows są obsługiwane z .NET Core 2.1:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="5bfe9-165">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5bfe9-166">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="5bfe9-166">OS</span></span>                            | <span data-ttu-id="5bfe9-167">Wersja</span><span class="sxs-lookup"><span data-stu-id="5bfe9-167">Version</span></span>                        | <span data-ttu-id="5bfe9-168">Architektury</span><span class="sxs-lookup"><span data-stu-id="5bfe9-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5bfe9-169">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5bfe9-169">Windows Client</span></span>                | <span data-ttu-id="5bfe9-170">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5bfe9-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-171">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-172">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="5bfe9-172">Windows 10 Client</span></span>             | <span data-ttu-id="5bfe9-173">Wersja 1607+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-173">Version 1607+</span></span>                  | <span data-ttu-id="5bfe9-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-174">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5bfe9-175">Windows Server</span></span>                | <span data-ttu-id="5bfe9-176">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="5bfe9-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5bfe9-177">x64, x86</span></span>        |
| <span data-ttu-id="5bfe9-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5bfe9-178">Nano Server</span></span>                   | <span data-ttu-id="5bfe9-179">Wersja 1803+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-179">Version 1803+</span></span>                  | <span data-ttu-id="5bfe9-180">x64,</span><span class="sxs-lookup"><span data-stu-id="5bfe9-180">x64,</span></span>            |

<span data-ttu-id="5bfe9-181">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2.1, zobacz [.NET Core 2.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="5bfe9-182">Windows 7 / Vista / 8.1 / Serwer 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5bfe9-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="5bfe9-183">Dodatkowe zależności są wymagane w przypadku instalowania sdk .NET lub środowiska uruchomieniowego w następujących wersjach systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="5bfe9-184">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-184">Windows 7 SP1</span></span>
- <span data-ttu-id="5bfe9-185">Dodatek SP 2 dla systemu Windows Vista</span><span class="sxs-lookup"><span data-stu-id="5bfe9-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="5bfe9-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-186">Windows 8.1</span></span>
- <span data-ttu-id="5bfe9-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5bfe9-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="5bfe9-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5bfe9-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="5bfe9-189">Zainstaluj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-189">Install the following:</span></span>

- <span data-ttu-id="5bfe9-190">[Aktualizacja redystrybucyjna programu Microsoft Visual C++ 2015 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="5bfe9-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="5bfe9-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="5bfe9-192">Powyższe wymagania są również wymagane, jeśli natkniesz się na jeden z następujących błędów:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="5bfe9-193">Nie można uruchomić programu, ponieważ na komputerze brakuje pliku *api-ms-win-crt-runtime-l1-1-0.dll.*</span><span class="sxs-lookup"><span data-stu-id="5bfe9-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="5bfe9-194">Spróbuj ponownie zainstalować program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="5bfe9-195">\-lub -</span><span class="sxs-lookup"><span data-stu-id="5bfe9-195">\- or -</span></span>
>
> <span data-ttu-id="5bfe9-196">Znaleziono *hostfxr.dll* biblioteki, ale ładowanie go z *C:\\\<path_to_app>\\hostfxr.dll* nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="5bfe9-197">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="5bfe9-198">.NET Core 3.1 traktuje Linuksa jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="5bfe9-199">Istnieje pojedyncza kompilacja Systemu Linux (na architekturę chipów) dla obsługiwanych dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5bfe9-200">.NET Core 3.1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5bfe9-201">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5bfe9-202">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="5bfe9-202">OS</span></span>                             | <span data-ttu-id="5bfe9-203">Wersja</span><span class="sxs-lookup"><span data-stu-id="5bfe9-203">Version</span></span>               | <span data-ttu-id="5bfe9-204">Architektury</span><span class="sxs-lookup"><span data-stu-id="5bfe9-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="5bfe9-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="5bfe9-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="5bfe9-206">6, 7, 8</span></span>               | <span data-ttu-id="5bfe9-207">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-207">x64</span></span> |
| <span data-ttu-id="5bfe9-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="5bfe9-208">CentOS</span></span>                         | <span data-ttu-id="5bfe9-209">7+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-209">7+</span></span>                    | <span data-ttu-id="5bfe9-210">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-210">x64</span></span> |
| <span data-ttu-id="5bfe9-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-211">Oracle Linux</span></span>                   | <span data-ttu-id="5bfe9-212">7+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-212">7+</span></span>                    | <span data-ttu-id="5bfe9-213">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-213">x64</span></span> |
| <span data-ttu-id="5bfe9-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="5bfe9-214">Fedora</span></span>                         | <span data-ttu-id="5bfe9-215">29+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-215">29+</span></span>                   | <span data-ttu-id="5bfe9-216">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-216">x64</span></span> |
| <span data-ttu-id="5bfe9-217">Debian</span><span class="sxs-lookup"><span data-stu-id="5bfe9-217">Debian</span></span>                         | <span data-ttu-id="5bfe9-218">9+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-218">9+</span></span>                    | <span data-ttu-id="5bfe9-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5bfe9-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5bfe9-220">Ubuntu</span></span>                         | <span data-ttu-id="5bfe9-221">16.04+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-221">16.04+</span></span>                | <span data-ttu-id="5bfe9-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5bfe9-223">Linux Mennica</span><span class="sxs-lookup"><span data-stu-id="5bfe9-223">Linux Mint</span></span>                     | <span data-ttu-id="5bfe9-224">18+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-224">18+</span></span>                   | <span data-ttu-id="5bfe9-225">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-225">x64</span></span> |
| <span data-ttu-id="5bfe9-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5bfe9-226">openSUSE</span></span>                       | <span data-ttu-id="5bfe9-227">15+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-227">15+</span></span>                   | <span data-ttu-id="5bfe9-228">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-228">x64</span></span> |
| <span data-ttu-id="5bfe9-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="5bfe9-230">12 sp2+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-230">12 SP2+</span></span>               | <span data-ttu-id="5bfe9-231">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-231">x64</span></span> |
| <span data-ttu-id="5bfe9-232">Alpejski Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-232">Alpine Linux</span></span>                   | <span data-ttu-id="5bfe9-233">3.10+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-233">3.10+</span></span>                 | <span data-ttu-id="5bfe9-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-234">x64, ARM64</span></span> |

<span data-ttu-id="5bfe9-235">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3.1, zobacz [.NET Core 3.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="5bfe9-236">Aby uzyskać więcej informacji na temat instalowania .NET Core 3.1 na ARM64 (jądro 4.14+), zobacz [Instalowanie .NET Core 3.0 w systemie Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5bfe9-237">Obsługa ARM64 wymaga jądra Systemu Linux 4.14 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="5bfe9-238">Niektóre dystrybucje linuksa spełniają to wymaganie, podczas gdy inne nie.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="5bfe9-239">Na przykład Ubuntu 18.04 jest obsługiwany, ale Ubuntu 16.04 nie.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="5bfe9-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5bfe9-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="5bfe9-241">.NET Core 3.0 traktuje Linuksa jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="5bfe9-242">Istnieje pojedyncza kompilacja Systemu Linux (na architekturę chipów) dla obsługiwanych dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5bfe9-243">.NET Core 3.0 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5bfe9-244">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5bfe9-245">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="5bfe9-245">OS</span></span>                             | <span data-ttu-id="5bfe9-246">Wersja</span><span class="sxs-lookup"><span data-stu-id="5bfe9-246">Version</span></span>               | <span data-ttu-id="5bfe9-247">Architektury</span><span class="sxs-lookup"><span data-stu-id="5bfe9-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="5bfe9-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="5bfe9-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="5bfe9-249">6, 7, 8</span></span>               | <span data-ttu-id="5bfe9-250">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-250">x64</span></span> |
| <span data-ttu-id="5bfe9-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="5bfe9-251">CentOS</span></span>                         | <span data-ttu-id="5bfe9-252">7+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-252">7+</span></span>                    | <span data-ttu-id="5bfe9-253">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-253">x64</span></span> |
| <span data-ttu-id="5bfe9-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-254">Oracle Linux</span></span>                   | <span data-ttu-id="5bfe9-255">7+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-255">7+</span></span>                    | <span data-ttu-id="5bfe9-256">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-256">x64</span></span> |
| <span data-ttu-id="5bfe9-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="5bfe9-257">Fedora</span></span>                         | <span data-ttu-id="5bfe9-258">29+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-258">29+</span></span>                   | <span data-ttu-id="5bfe9-259">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-259">x64</span></span> |
| <span data-ttu-id="5bfe9-260">Debian</span><span class="sxs-lookup"><span data-stu-id="5bfe9-260">Debian</span></span>                         | <span data-ttu-id="5bfe9-261">9+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-261">9+</span></span>                    | <span data-ttu-id="5bfe9-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5bfe9-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5bfe9-263">Ubuntu</span></span>                         | <span data-ttu-id="5bfe9-264">16.04+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-264">16.04+</span></span>                | <span data-ttu-id="5bfe9-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5bfe9-266">Linux Mennica</span><span class="sxs-lookup"><span data-stu-id="5bfe9-266">Linux Mint</span></span>                     | <span data-ttu-id="5bfe9-267">18+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-267">18+</span></span>                   | <span data-ttu-id="5bfe9-268">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-268">x64</span></span> |
| <span data-ttu-id="5bfe9-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5bfe9-269">openSUSE</span></span>                       | <span data-ttu-id="5bfe9-270">15+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-270">15+</span></span>                   | <span data-ttu-id="5bfe9-271">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-271">x64</span></span> |
| <span data-ttu-id="5bfe9-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="5bfe9-273">12 sp2+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-273">12 SP2+</span></span>               | <span data-ttu-id="5bfe9-274">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-274">x64</span></span> |
| <span data-ttu-id="5bfe9-275">Alpejski Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-275">Alpine Linux</span></span>                   | <span data-ttu-id="5bfe9-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-276">3.8+</span></span>                  | <span data-ttu-id="5bfe9-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-277">x64, ARM64</span></span> |

<span data-ttu-id="5bfe9-278">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3.0, zobacz [.NET Core 3.0 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="5bfe9-279">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3.0 na serwerze ARM64, zobacz [Instalowanie .NET Core 3.0 w systemie Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="5bfe9-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5bfe9-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5bfe9-281">.NET Core 2.2 traktuje Linuksa jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="5bfe9-282">Istnieje pojedyncza kompilacja Systemu Linux (na architekturę chipów) dla obsługiwanych dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5bfe9-283">.NET Core 2.2 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5bfe9-284">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5bfe9-285">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="5bfe9-285">OS</span></span>                             |  <span data-ttu-id="5bfe9-286">Wersja</span><span class="sxs-lookup"><span data-stu-id="5bfe9-286">Version</span></span>                |  <span data-ttu-id="5bfe9-287">Architektury</span><span class="sxs-lookup"><span data-stu-id="5bfe9-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="5bfe9-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="5bfe9-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="5bfe9-289">6, 7</span></span>                   | <span data-ttu-id="5bfe9-290">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-290">x64</span></span> |
| <span data-ttu-id="5bfe9-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="5bfe9-291">CentOS</span></span>                         |  <span data-ttu-id="5bfe9-292">7</span><span class="sxs-lookup"><span data-stu-id="5bfe9-292">7</span></span>                      | <span data-ttu-id="5bfe9-293">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-293">x64</span></span> |
| <span data-ttu-id="5bfe9-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-294">Oracle Linux</span></span>                   |  <span data-ttu-id="5bfe9-295">7</span><span class="sxs-lookup"><span data-stu-id="5bfe9-295">7</span></span>                      | <span data-ttu-id="5bfe9-296">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-296">x64</span></span> |
| <span data-ttu-id="5bfe9-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="5bfe9-297">Fedora</span></span>                         |  <span data-ttu-id="5bfe9-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="5bfe9-298">29, 30</span></span>                 | <span data-ttu-id="5bfe9-299">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-299">x64</span></span> |
| <span data-ttu-id="5bfe9-300">Debian</span><span class="sxs-lookup"><span data-stu-id="5bfe9-300">Debian</span></span>                         |  <span data-ttu-id="5bfe9-301">9</span><span class="sxs-lookup"><span data-stu-id="5bfe9-301">9</span></span>                      | <span data-ttu-id="5bfe9-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5bfe9-302">x64, ARM32</span></span> |
| <span data-ttu-id="5bfe9-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5bfe9-303">Ubuntu</span></span>                         |  <span data-ttu-id="5bfe9-304">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="5bfe9-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="5bfe9-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5bfe9-305">x64, ARM32</span></span> |
| <span data-ttu-id="5bfe9-306">Linux Mennica</span><span class="sxs-lookup"><span data-stu-id="5bfe9-306">Linux Mint</span></span>                     |  <span data-ttu-id="5bfe9-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="5bfe9-307">17, 18</span></span>                 | <span data-ttu-id="5bfe9-308">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-308">x64</span></span> |
| <span data-ttu-id="5bfe9-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5bfe9-309">openSUSE</span></span>                       |  <span data-ttu-id="5bfe9-310">15+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-310">15+</span></span>                    | <span data-ttu-id="5bfe9-311">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-311">x64</span></span> |
| <span data-ttu-id="5bfe9-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="5bfe9-313">12 sp2+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-313">12 SP2+</span></span>                | <span data-ttu-id="5bfe9-314">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-314">x64</span></span> |
| <span data-ttu-id="5bfe9-315">Alpejski Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-315">Alpine Linux</span></span>                   |  <span data-ttu-id="5bfe9-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-316">3.8+</span></span>                   | <span data-ttu-id="5bfe9-317">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-317">x64</span></span> |

<span data-ttu-id="5bfe9-318">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2.2, zobacz [.NET Core 2.2 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="5bfe9-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5bfe9-320">.NET Core 2.1 traktuje Linuksa jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="5bfe9-321">Istnieje pojedyncza kompilacja Systemu Linux (na architekturę chipów) dla obsługiwanych dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5bfe9-322">.NET Core 2.1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5bfe9-323">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5bfe9-324">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="5bfe9-324">OS</span></span>                             |  <span data-ttu-id="5bfe9-325">Wersja</span><span class="sxs-lookup"><span data-stu-id="5bfe9-325">Version</span></span>                |  <span data-ttu-id="5bfe9-326">Architektury</span><span class="sxs-lookup"><span data-stu-id="5bfe9-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="5bfe9-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="5bfe9-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="5bfe9-328">6, 7, 8</span></span>                | <span data-ttu-id="5bfe9-329">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-329">x64</span></span> |
| <span data-ttu-id="5bfe9-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="5bfe9-330">CentOS</span></span>                         |  <span data-ttu-id="5bfe9-331">7+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-331">7+</span></span>                     | <span data-ttu-id="5bfe9-332">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-332">x64</span></span> |
| <span data-ttu-id="5bfe9-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-333">Oracle Linux</span></span>                   |  <span data-ttu-id="5bfe9-334">7+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-334">7+</span></span>                     | <span data-ttu-id="5bfe9-335">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-335">x64</span></span> |
| <span data-ttu-id="5bfe9-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="5bfe9-336">Fedora</span></span>                         |  <span data-ttu-id="5bfe9-337">29+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-337">29+</span></span>                    | <span data-ttu-id="5bfe9-338">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-338">x64</span></span> |
| <span data-ttu-id="5bfe9-339">Debian</span><span class="sxs-lookup"><span data-stu-id="5bfe9-339">Debian</span></span>                         |  <span data-ttu-id="5bfe9-340">9</span><span class="sxs-lookup"><span data-stu-id="5bfe9-340">9</span></span>                      | <span data-ttu-id="5bfe9-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5bfe9-341">x64, ARM32</span></span> |
| <span data-ttu-id="5bfe9-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5bfe9-342">Ubuntu</span></span>                         |  <span data-ttu-id="5bfe9-343">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="5bfe9-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="5bfe9-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5bfe9-344">x64, ARM32</span></span> |
| <span data-ttu-id="5bfe9-345">Linux Mennica</span><span class="sxs-lookup"><span data-stu-id="5bfe9-345">Linux Mint</span></span>                     |  <span data-ttu-id="5bfe9-346">17+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-346">17+</span></span>                    | <span data-ttu-id="5bfe9-347">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-347">x64</span></span> |
| <span data-ttu-id="5bfe9-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5bfe9-348">openSUSE</span></span>                       |  <span data-ttu-id="5bfe9-349">15+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-349">15+</span></span>                    | <span data-ttu-id="5bfe9-350">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-350">x64</span></span> |
| <span data-ttu-id="5bfe9-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="5bfe9-352">12 sp2+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-352">12 SP2+</span></span>                | <span data-ttu-id="5bfe9-353">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-353">x64</span></span> |
| <span data-ttu-id="5bfe9-354">Alpejski Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-354">Alpine Linux</span></span>                   |  <span data-ttu-id="5bfe9-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="5bfe9-355">3.8+</span></span>                   | <span data-ttu-id="5bfe9-356">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-356">x64</span></span> |

<span data-ttu-id="5bfe9-357">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2.1, zobacz [.NET Core 2.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="5bfe9-358">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="5bfe9-358">Linux distribution dependencies</span></span>

<span data-ttu-id="5bfe9-359">Na podstawie dystrybucji systemu Linux może być konieczne zainstalowanie dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5bfe9-360">Dokładne wersje i nazwy mogą się nieznacznie różnić w wybranym przez Użytkownika dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="5bfe9-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5bfe9-361">Ubuntu</span></span>

<span data-ttu-id="5bfe9-362">Dystrybucje Ubuntu wymagają zainstalowania następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="5bfe9-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="5bfe9-363">liblttng-ust0</span></span>
- <span data-ttu-id="5bfe9-364">libcurl3 (dla 14.x i 16.x)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="5bfe9-365">libcurl4 (dla 18.x)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="5bfe9-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="5bfe9-366">libssl1.0.0</span></span>
- <span data-ttu-id="5bfe9-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="5bfe9-367">libkrb5-3</span></span>
- <span data-ttu-id="5bfe9-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="5bfe9-368">zlib1g</span></span>
- <span data-ttu-id="5bfe9-369">libicu52 (dla 14.x)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="5bfe9-370">libicu55 (dla 16.x)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="5bfe9-371">libicu57 (dla 17.x)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="5bfe9-372">libicu60 (dla 18.x)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="5bfe9-373">W przypadku aplikacji .NET Core korzystających z zestawu *System.Drawing.Common* należy również wykonać następującą zależność:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="5bfe9-374">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="5bfe9-375">Większość wersji Ubuntu zawiera wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="5bfe9-376">Możesz zainstalować najnowszą wersję libgdiplus, dodając repozytorium Mono do systemu.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="5bfe9-377">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="5bfe9-378">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="5bfe9-378">CentOS and Fedora</span></span>

<span data-ttu-id="5bfe9-379">Dystrybucje CentOS wymagają zainstalowania następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="5bfe9-380">lttng-ust ( lttng ust )</span><span class="sxs-lookup"><span data-stu-id="5bfe9-380">lttng-ust</span></span>
- <span data-ttu-id="5bfe9-381">Libcurl</span><span class="sxs-lookup"><span data-stu-id="5bfe9-381">libcurl</span></span>
- <span data-ttu-id="5bfe9-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="5bfe9-382">openssl-libs</span></span>
- <span data-ttu-id="5bfe9-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="5bfe9-383">krb5-libs</span></span>
- <span data-ttu-id="5bfe9-384">libicu</span><span class="sxs-lookup"><span data-stu-id="5bfe9-384">libicu</span></span>
- <span data-ttu-id="5bfe9-385">Zlib</span><span class="sxs-lookup"><span data-stu-id="5bfe9-385">zlib</span></span>

<span data-ttu-id="5bfe9-386">Użytkownicy Fedory: Jeśli wersja OpenSSL >= 1.1, musisz zainstalować **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="5bfe9-387">W przypadku programu .NET Core 2.0 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="5bfe9-388">libunwind ( libunwind )</span><span class="sxs-lookup"><span data-stu-id="5bfe9-388">libunwind</span></span>
- <span data-ttu-id="5bfe9-389">libuuid ( libuuid )</span><span class="sxs-lookup"><span data-stu-id="5bfe9-389">libuuid</span></span>

<span data-ttu-id="5bfe9-390">Aby uzyskać więcej informacji na temat zależności, zobacz [Niezależne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="5bfe9-391">W przypadku aplikacji .NET Core korzystających z zestawu *System.Drawing.Common* należy również wymagać następującej zależności:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="5bfe9-392">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="5bfe9-393">Większość wersji CentOS i Fedory zawiera wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="5bfe9-394">Możesz zainstalować najnowszą wersję libgdiplus, dodając repozytorium Mono do systemu.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="5bfe9-395">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="5bfe9-396">Program .NET Core jest obsługiwany w następujących wersjach systemu macOS:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="5bfe9-397">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5bfe9-398">Wersja podstawowa .NET</span><span class="sxs-lookup"><span data-stu-id="5bfe9-398">.NET Core Version</span></span> | <span data-ttu-id="5bfe9-399">macOS</span><span class="sxs-lookup"><span data-stu-id="5bfe9-399">macOS</span></span>                 | <span data-ttu-id="5bfe9-400">Architektury</span><span class="sxs-lookup"><span data-stu-id="5bfe9-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="5bfe9-401">3.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-401">3.1</span></span>               | <span data-ttu-id="5bfe9-402">Wysokie Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="5bfe9-403">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-403">x64</span></span> | [<span data-ttu-id="5bfe9-404">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="5bfe9-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="5bfe9-405">3.0</span><span class="sxs-lookup"><span data-stu-id="5bfe9-405">3.0</span></span>               | <span data-ttu-id="5bfe9-406">Wysokie Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="5bfe9-407">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-407">x64</span></span> | [<span data-ttu-id="5bfe9-408">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="5bfe9-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="5bfe9-409">2.2</span><span class="sxs-lookup"><span data-stu-id="5bfe9-409">2.2</span></span>               | <span data-ttu-id="5bfe9-410">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="5bfe9-411">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-411">x64</span></span> | [<span data-ttu-id="5bfe9-412">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="5bfe9-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="5bfe9-413">2.1</span><span class="sxs-lookup"><span data-stu-id="5bfe9-413">2.1</span></span>               | <span data-ttu-id="5bfe9-414">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="5bfe9-415">x64</span><span class="sxs-lookup"><span data-stu-id="5bfe9-415">x64</span></span> | [<span data-ttu-id="5bfe9-416">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="5bfe9-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="5bfe9-417">Począwszy od systemu macOS Catalina (wersja 10.15), całe oprogramowanie zbudowane po 1 czerwca 2019 r., które jest dystrybuowane z identyfikatorem dewelopera, musi zostać ponotowane powadnianiem notarialnie.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-417">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="5bfe9-418">To wymaganie dotyczy programu .NET Core, .NET Core SDK i oprogramowania utworzonego za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-418">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="5bfe9-419">Instalatory .NET Core (zarówno w czasie wykonywania, jak i SDK) w wersjach 3.1, 3.0 i 2.1 zostały notarialnie notarialnie od lutego 18, 2020.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-419">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="5bfe9-420">Wcześniej wydane wersje nie są notarialnie.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-420">Prior released versions aren't notarized.</span></span> <span data-ttu-id="5bfe9-421">Jeśli uruchomisz aplikację nienotarialnie, zobaczysz błąd podobny do następującego obrazu:</span><span class="sxs-lookup"><span data-stu-id="5bfe9-421">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![Alert notariacyjny macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="5bfe9-423">Aby uzyskać więcej informacji na temat wpływu wymuszanego notarializacji na program .NET Core (i aplikacje .NET Core), zobacz [Praca z notarialniem Catalina](macos-notarization-issues.md)w systemie macOS .</span><span class="sxs-lookup"><span data-stu-id="5bfe9-423">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="5bfe9-424">libgdiplus ( libgdiplus )</span><span class="sxs-lookup"><span data-stu-id="5bfe9-424">libgdiplus</span></span>

<span data-ttu-id="5bfe9-425">Aplikacje .NET Core korzystające z zestawu *System.Drawing.Common* wymagają zainstalowania programu libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-425">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="5bfe9-426">Łatwym sposobem uzyskania libgdiplus jest użycie menedżera pakietów [Homebrew ("brew")](https://brew.sh/) dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="5bfe9-426">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="5bfe9-427">Po zainstalowaniu *naparuzainstaluj*libgdiplus, wykonując następujące polecenia w wierszu Terminal (polecenie):</span><span class="sxs-lookup"><span data-stu-id="5bfe9-427">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="5bfe9-428">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5bfe9-428">Next steps</span></span>

- <span data-ttu-id="5bfe9-429">Aby tworzyć i uruchamiać aplikacje, zainstaluj [zestaw SDK .NET Core](sdk.md) (w tym czas wykonywania).</span><span class="sxs-lookup"><span data-stu-id="5bfe9-429">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="5bfe9-430">Aby uruchamiać aplikacje utworzone przez inne osoby, zainstaluj [program .NET Core .](runtime.md)</span><span class="sxs-lookup"><span data-stu-id="5bfe9-430">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
