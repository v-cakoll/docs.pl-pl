---
title: Zależności zestaw .NET Core SDK i środowiska uruchomieniowego — .NET Core
description: Szczegółowe informacje na temat wymagań wstępnych dotyczących architektury procesora i systemu operacyjnego w celu zainstalowania zestaw .NET Core SDK i środowiska uruchomieniowego w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 42765d4402dfa17d4e962b2ecaf7a83e91853c76
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140993"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="dfbf1-103">Zależności i wymagania dotyczące platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="dfbf1-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="dfbf1-104">W tym artykule szczegółowo przedstawiono systemy operacyjne i architekturę procesora CPU obsługiwane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="dfbf1-105">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="dfbf1-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="dfbf1-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="dfbf1-107">W przypadku programu .NET Core 3,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="dfbf1-108">`+` Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfbf1-109">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="dfbf1-109">OS</span></span>                            | <span data-ttu-id="dfbf1-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="dfbf1-110">Version</span></span>                        | <span data-ttu-id="dfbf1-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="dfbf1-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="dfbf1-112">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dfbf1-112">Windows Client</span></span>                | <span data-ttu-id="dfbf1-113">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="dfbf1-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-114">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-115">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="dfbf1-115">Windows 10 Client</span></span>             | <span data-ttu-id="dfbf1-116">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-116">Version 1607+</span></span>                  | <span data-ttu-id="dfbf1-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-117">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="dfbf1-118">Windows Server</span></span>                | <span data-ttu-id="dfbf1-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-119">2012 R2+</span></span>                       | <span data-ttu-id="dfbf1-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-120">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="dfbf1-121">Nano Server</span></span>                   | <span data-ttu-id="dfbf1-122">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-122">Version 1803+</span></span>                  | <span data-ttu-id="dfbf1-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfbf1-123">x64, ARM32</span></span>      |

<span data-ttu-id="dfbf1-124">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="dfbf1-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dfbf1-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="dfbf1-126">*Platforma .NET Core 3,0 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="dfbf1-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="dfbf1-127">W przypadku programu .NET Core 3,0 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="dfbf1-128">`+` Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfbf1-129">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="dfbf1-129">OS</span></span>                            | <span data-ttu-id="dfbf1-130">Wersja</span><span class="sxs-lookup"><span data-stu-id="dfbf1-130">Version</span></span>                        | <span data-ttu-id="dfbf1-131">Architektury</span><span class="sxs-lookup"><span data-stu-id="dfbf1-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="dfbf1-132">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dfbf1-132">Windows Client</span></span>                | <span data-ttu-id="dfbf1-133">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="dfbf1-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-134">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-135">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="dfbf1-135">Windows 10 Client</span></span>             | <span data-ttu-id="dfbf1-136">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-136">Version 1607+</span></span>                  | <span data-ttu-id="dfbf1-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-137">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="dfbf1-138">Windows Server</span></span>                | <span data-ttu-id="dfbf1-139">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-139">2012 R2+</span></span>                       | <span data-ttu-id="dfbf1-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-140">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="dfbf1-141">Nano Server</span></span>                   | <span data-ttu-id="dfbf1-142">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-142">Version 1803+</span></span>                  | <span data-ttu-id="dfbf1-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfbf1-143">x64, ARM32</span></span>      |

<span data-ttu-id="dfbf1-144">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="dfbf1-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="dfbf1-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="dfbf1-146">*Platforma .NET Core 2,2 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="dfbf1-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="dfbf1-147">W przypadku programu .NET Core 2,2 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="dfbf1-148">`+` Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfbf1-149">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="dfbf1-149">OS</span></span>                            | <span data-ttu-id="dfbf1-150">Wersja</span><span class="sxs-lookup"><span data-stu-id="dfbf1-150">Version</span></span>                        | <span data-ttu-id="dfbf1-151">Architektury</span><span class="sxs-lookup"><span data-stu-id="dfbf1-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="dfbf1-152">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dfbf1-152">Windows Client</span></span>                | <span data-ttu-id="dfbf1-153">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="dfbf1-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-154">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-155">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="dfbf1-155">Windows 10 Client</span></span>             | <span data-ttu-id="dfbf1-156">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-156">Version 1607+</span></span>                  | <span data-ttu-id="dfbf1-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-157">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="dfbf1-158">Windows Server</span></span>                | <span data-ttu-id="dfbf1-159">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="dfbf1-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-160">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="dfbf1-161">Nano Server</span></span>                   | <span data-ttu-id="dfbf1-162">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-162">Version 1803+</span></span>                   | <span data-ttu-id="dfbf1-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfbf1-163">x64, ARM32</span></span>      |

<span data-ttu-id="dfbf1-164">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="dfbf1-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="dfbf1-166">W przypadku programu .NET Core 2,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="dfbf1-167">`+` Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfbf1-168">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="dfbf1-168">OS</span></span>                            | <span data-ttu-id="dfbf1-169">Wersja</span><span class="sxs-lookup"><span data-stu-id="dfbf1-169">Version</span></span>                        | <span data-ttu-id="dfbf1-170">Architektury</span><span class="sxs-lookup"><span data-stu-id="dfbf1-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="dfbf1-171">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dfbf1-171">Windows Client</span></span>                | <span data-ttu-id="dfbf1-172">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="dfbf1-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-173">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-174">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="dfbf1-174">Windows 10 Client</span></span>             | <span data-ttu-id="dfbf1-175">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-175">Version 1607+</span></span>                  | <span data-ttu-id="dfbf1-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-176">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="dfbf1-177">Windows Server</span></span>                | <span data-ttu-id="dfbf1-178">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="dfbf1-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="dfbf1-179">x64, x86</span></span>        |
| <span data-ttu-id="dfbf1-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="dfbf1-180">Nano Server</span></span>                   | <span data-ttu-id="dfbf1-181">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-181">Version 1803+</span></span>                  | <span data-ttu-id="dfbf1-182">procesorów</span><span class="sxs-lookup"><span data-stu-id="dfbf1-182">x64,</span></span>            |

<span data-ttu-id="dfbf1-183">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="dfbf1-184">Windows 7/Vista/8,1/Server 2008 R2/serwer 2012 R2</span><span class="sxs-lookup"><span data-stu-id="dfbf1-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="dfbf1-185">Jeśli instalujesz zestaw .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows, wymagane są dodatkowe zależności:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="dfbf1-186">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-186">Windows 7 SP1</span></span>
- <span data-ttu-id="dfbf1-187">Windows Vista z dodatkiem SP 2</span><span class="sxs-lookup"><span data-stu-id="dfbf1-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="dfbf1-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-188">Windows 8.1</span></span>
- <span data-ttu-id="dfbf1-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="dfbf1-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="dfbf1-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="dfbf1-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="dfbf1-191">Zainstaluj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-191">Install the following:</span></span>

- <span data-ttu-id="dfbf1-192">[Microsoft Visual C++ 2015 redystrybucyjnej aktualizacji 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="dfbf1-193">POPRAWKI KB2533623</span><span class="sxs-lookup"><span data-stu-id="dfbf1-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="dfbf1-194">Powyższe wymagania są również wymagane w przypadku wystąpienia jednego z następujących błędów:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="dfbf1-195">Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-CRT-Runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="dfbf1-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="dfbf1-196">Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="dfbf1-197">\-oraz</span><span class="sxs-lookup"><span data-stu-id="dfbf1-197">\- or -</span></span>
>
> <span data-ttu-id="dfbf1-198">Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-cor-timezone-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="dfbf1-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="dfbf1-199">Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="dfbf1-200">\-oraz</span><span class="sxs-lookup"><span data-stu-id="dfbf1-200">\- or -</span></span>
>
> <span data-ttu-id="dfbf1-201">Znaleziono bibliotekę *hostfxr. dll* , ale ładowanie jej z *dysku C:\\\<path_to_app>\\hostfxr. dll* nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="dfbf1-202">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="dfbf1-203">Program .NET Core 3,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="dfbf1-204">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="dfbf1-205">Platforma .NET Core 3,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="dfbf1-206">`+` Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfbf1-207">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="dfbf1-207">OS</span></span>                             | <span data-ttu-id="dfbf1-208">Wersja</span><span class="sxs-lookup"><span data-stu-id="dfbf1-208">Version</span></span>               | <span data-ttu-id="dfbf1-209">Architektury</span><span class="sxs-lookup"><span data-stu-id="dfbf1-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="dfbf1-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="dfbf1-211">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="dfbf1-211">6, 7, 8</span></span>               | <span data-ttu-id="dfbf1-212">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-212">x64</span></span> |
| <span data-ttu-id="dfbf1-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="dfbf1-213">CentOS</span></span>                         | <span data-ttu-id="dfbf1-214">7 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-214">7+</span></span>                    | <span data-ttu-id="dfbf1-215">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-215">x64</span></span> |
| <span data-ttu-id="dfbf1-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-216">Oracle Linux</span></span>                   | <span data-ttu-id="dfbf1-217">7 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-217">7+</span></span>                    | <span data-ttu-id="dfbf1-218">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-218">x64</span></span> |
| <span data-ttu-id="dfbf1-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="dfbf1-219">Fedora</span></span>                         | <span data-ttu-id="dfbf1-220">30 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-220">30+</span></span>                   | <span data-ttu-id="dfbf1-221">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-221">x64</span></span> |
| <span data-ttu-id="dfbf1-222">Debian</span><span class="sxs-lookup"><span data-stu-id="dfbf1-222">Debian</span></span>                         | <span data-ttu-id="dfbf1-223">9 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-223">9+</span></span>                    | <span data-ttu-id="dfbf1-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="dfbf1-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfbf1-225">Ubuntu</span></span>                         | <span data-ttu-id="dfbf1-226">16.04 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-226">16.04+</span></span>                | <span data-ttu-id="dfbf1-227">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="dfbf1-228">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-228">Linux Mint</span></span>                     | <span data-ttu-id="dfbf1-229">18 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-229">18+</span></span>                   | <span data-ttu-id="dfbf1-230">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-230">x64</span></span> |
| <span data-ttu-id="dfbf1-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dfbf1-231">openSUSE</span></span>                       | <span data-ttu-id="dfbf1-232">15 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-232">15+</span></span>                   | <span data-ttu-id="dfbf1-233">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-233">x64</span></span> |
| <span data-ttu-id="dfbf1-234">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="dfbf1-235">12 Z DODATKIEM SP2 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-235">12 SP2+</span></span>               | <span data-ttu-id="dfbf1-236">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-236">x64</span></span> |
| <span data-ttu-id="dfbf1-237">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-237">Alpine Linux</span></span>                   | <span data-ttu-id="dfbf1-238">3.10 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-238">3.10+</span></span>                 | <span data-ttu-id="dfbf1-239">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-239">x64, ARM64</span></span> |

<span data-ttu-id="dfbf1-240">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="dfbf1-241">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,1 w systemie ARM64 (jądro 4.14 +), zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfbf1-242">Obsługa ARM64 wymaga jądra systemu Linux 4,14 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="dfbf1-243">Niektóre dystrybucje systemu Linux spełniają to wymaganie, a inne nie.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="dfbf1-244">Na przykład Ubuntu 18,04 jest obsługiwany, ale Ubuntu 16,04 nie jest.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="dfbf1-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dfbf1-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="dfbf1-246">*Platforma .NET Core 3,0 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="dfbf1-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="dfbf1-247">Program .NET Core 3,0 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="dfbf1-248">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="dfbf1-249">Platforma .NET Core 3,0 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="dfbf1-250">`+` Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfbf1-251">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="dfbf1-251">OS</span></span>                             | <span data-ttu-id="dfbf1-252">Wersja</span><span class="sxs-lookup"><span data-stu-id="dfbf1-252">Version</span></span>               | <span data-ttu-id="dfbf1-253">Architektury</span><span class="sxs-lookup"><span data-stu-id="dfbf1-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="dfbf1-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="dfbf1-255">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="dfbf1-255">6, 7, 8</span></span>               | <span data-ttu-id="dfbf1-256">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-256">x64</span></span> |
| <span data-ttu-id="dfbf1-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="dfbf1-257">CentOS</span></span>                         | <span data-ttu-id="dfbf1-258">7 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-258">7+</span></span>                    | <span data-ttu-id="dfbf1-259">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-259">x64</span></span> |
| <span data-ttu-id="dfbf1-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-260">Oracle Linux</span></span>                   | <span data-ttu-id="dfbf1-261">7 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-261">7+</span></span>                    | <span data-ttu-id="dfbf1-262">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-262">x64</span></span> |
| <span data-ttu-id="dfbf1-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="dfbf1-263">Fedora</span></span>                         | <span data-ttu-id="dfbf1-264">29 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-264">29+</span></span>                   | <span data-ttu-id="dfbf1-265">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-265">x64</span></span> |
| <span data-ttu-id="dfbf1-266">Debian</span><span class="sxs-lookup"><span data-stu-id="dfbf1-266">Debian</span></span>                         | <span data-ttu-id="dfbf1-267">9 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-267">9+</span></span>                    | <span data-ttu-id="dfbf1-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="dfbf1-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfbf1-269">Ubuntu</span></span>                         | <span data-ttu-id="dfbf1-270">16.04 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-270">16.04+</span></span>                | <span data-ttu-id="dfbf1-271">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="dfbf1-272">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-272">Linux Mint</span></span>                     | <span data-ttu-id="dfbf1-273">18 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-273">18+</span></span>                   | <span data-ttu-id="dfbf1-274">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-274">x64</span></span> |
| <span data-ttu-id="dfbf1-275">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dfbf1-275">openSUSE</span></span>                       | <span data-ttu-id="dfbf1-276">15 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-276">15+</span></span>                   | <span data-ttu-id="dfbf1-277">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-277">x64</span></span> |
| <span data-ttu-id="dfbf1-278">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="dfbf1-279">12 Z DODATKIEM SP2 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-279">12 SP2+</span></span>               | <span data-ttu-id="dfbf1-280">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-280">x64</span></span> |
| <span data-ttu-id="dfbf1-281">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-281">Alpine Linux</span></span>                   | <span data-ttu-id="dfbf1-282">3.8 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-282">3.8+</span></span>                  | <span data-ttu-id="dfbf1-283">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-283">x64, ARM64</span></span> |

<span data-ttu-id="dfbf1-284">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="dfbf1-285">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="dfbf1-286">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="dfbf1-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="dfbf1-287">*Platforma .NET Core 2,2 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="dfbf1-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="dfbf1-288">Program .NET Core 2,2 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="dfbf1-289">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="dfbf1-290">Platforma .NET Core 2,2 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="dfbf1-291">`+` Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfbf1-292">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="dfbf1-292">OS</span></span>                             |  <span data-ttu-id="dfbf1-293">Wersja</span><span class="sxs-lookup"><span data-stu-id="dfbf1-293">Version</span></span>                |  <span data-ttu-id="dfbf1-294">Architektury</span><span class="sxs-lookup"><span data-stu-id="dfbf1-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="dfbf1-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="dfbf1-296">6, 7</span><span class="sxs-lookup"><span data-stu-id="dfbf1-296">6, 7</span></span>                   | <span data-ttu-id="dfbf1-297">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-297">x64</span></span> |
| <span data-ttu-id="dfbf1-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="dfbf1-298">CentOS</span></span>                         |  <span data-ttu-id="dfbf1-299">7</span><span class="sxs-lookup"><span data-stu-id="dfbf1-299">7</span></span>                      | <span data-ttu-id="dfbf1-300">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-300">x64</span></span> |
| <span data-ttu-id="dfbf1-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-301">Oracle Linux</span></span>                   |  <span data-ttu-id="dfbf1-302">7</span><span class="sxs-lookup"><span data-stu-id="dfbf1-302">7</span></span>                      | <span data-ttu-id="dfbf1-303">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-303">x64</span></span> |
| <span data-ttu-id="dfbf1-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="dfbf1-304">Fedora</span></span>                         |  <span data-ttu-id="dfbf1-305">29, 30</span><span class="sxs-lookup"><span data-stu-id="dfbf1-305">29, 30</span></span>                 | <span data-ttu-id="dfbf1-306">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-306">x64</span></span> |
| <span data-ttu-id="dfbf1-307">Debian</span><span class="sxs-lookup"><span data-stu-id="dfbf1-307">Debian</span></span>                         |  <span data-ttu-id="dfbf1-308">9</span><span class="sxs-lookup"><span data-stu-id="dfbf1-308">9</span></span>                      | <span data-ttu-id="dfbf1-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfbf1-309">x64, ARM32</span></span> |
| <span data-ttu-id="dfbf1-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfbf1-310">Ubuntu</span></span>                         |  <span data-ttu-id="dfbf1-311">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="dfbf1-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="dfbf1-312">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfbf1-312">x64, ARM32</span></span> |
| <span data-ttu-id="dfbf1-313">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-313">Linux Mint</span></span>                     |  <span data-ttu-id="dfbf1-314">17, 18</span><span class="sxs-lookup"><span data-stu-id="dfbf1-314">17, 18</span></span>                 | <span data-ttu-id="dfbf1-315">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-315">x64</span></span> |
| <span data-ttu-id="dfbf1-316">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dfbf1-316">openSUSE</span></span>                       |  <span data-ttu-id="dfbf1-317">15 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-317">15+</span></span>                    | <span data-ttu-id="dfbf1-318">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-318">x64</span></span> |
| <span data-ttu-id="dfbf1-319">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="dfbf1-320">12 Z DODATKIEM SP2 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-320">12 SP2+</span></span>                | <span data-ttu-id="dfbf1-321">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-321">x64</span></span> |
| <span data-ttu-id="dfbf1-322">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-322">Alpine Linux</span></span>                   |  <span data-ttu-id="dfbf1-323">3.8 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-323">3.8+</span></span>                   | <span data-ttu-id="dfbf1-324">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-324">x64</span></span> |

<span data-ttu-id="dfbf1-325">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="dfbf1-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="dfbf1-327">Program .NET Core 2,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="dfbf1-328">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="dfbf1-329">Platforma .NET Core 2,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="dfbf1-330">`+` Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfbf1-331">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="dfbf1-331">OS</span></span>                             |  <span data-ttu-id="dfbf1-332">Wersja</span><span class="sxs-lookup"><span data-stu-id="dfbf1-332">Version</span></span>                |  <span data-ttu-id="dfbf1-333">Architektury</span><span class="sxs-lookup"><span data-stu-id="dfbf1-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="dfbf1-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="dfbf1-335">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="dfbf1-335">6, 7, 8</span></span>                | <span data-ttu-id="dfbf1-336">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-336">x64</span></span> |
| <span data-ttu-id="dfbf1-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="dfbf1-337">CentOS</span></span>                         |  <span data-ttu-id="dfbf1-338">7 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-338">7+</span></span>                     | <span data-ttu-id="dfbf1-339">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-339">x64</span></span> |
| <span data-ttu-id="dfbf1-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-340">Oracle Linux</span></span>                   |  <span data-ttu-id="dfbf1-341">7 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-341">7+</span></span>                     | <span data-ttu-id="dfbf1-342">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-342">x64</span></span> |
| <span data-ttu-id="dfbf1-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="dfbf1-343">Fedora</span></span>                         |  <span data-ttu-id="dfbf1-344">30 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-344">30+</span></span>                    | <span data-ttu-id="dfbf1-345">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-345">x64</span></span> |
| <span data-ttu-id="dfbf1-346">Debian</span><span class="sxs-lookup"><span data-stu-id="dfbf1-346">Debian</span></span>                         |  <span data-ttu-id="dfbf1-347">9</span><span class="sxs-lookup"><span data-stu-id="dfbf1-347">9</span></span>                      | <span data-ttu-id="dfbf1-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfbf1-348">x64, ARM32</span></span> |
| <span data-ttu-id="dfbf1-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfbf1-349">Ubuntu</span></span>                         |  <span data-ttu-id="dfbf1-350">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="dfbf1-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="dfbf1-351">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="dfbf1-351">x64, ARM32</span></span> |
| <span data-ttu-id="dfbf1-352">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-352">Linux Mint</span></span>                     |  <span data-ttu-id="dfbf1-353">17 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-353">17+</span></span>                    | <span data-ttu-id="dfbf1-354">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-354">x64</span></span> |
| <span data-ttu-id="dfbf1-355">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dfbf1-355">openSUSE</span></span>                       |  <span data-ttu-id="dfbf1-356">15 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-356">15+</span></span>                    | <span data-ttu-id="dfbf1-357">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-357">x64</span></span> |
| <span data-ttu-id="dfbf1-358">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="dfbf1-359">12 Z DODATKIEM SP2 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-359">12 SP2+</span></span>                | <span data-ttu-id="dfbf1-360">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-360">x64</span></span> |
| <span data-ttu-id="dfbf1-361">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-361">Alpine Linux</span></span>                   |  <span data-ttu-id="dfbf1-362">3.8 +</span><span class="sxs-lookup"><span data-stu-id="dfbf1-362">3.8+</span></span>                   | <span data-ttu-id="dfbf1-363">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-363">x64</span></span> |

<span data-ttu-id="dfbf1-364">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="dfbf1-365">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="dfbf1-365">Linux distribution dependencies</span></span>

<span data-ttu-id="dfbf1-366">W zależności od dystrybucji systemu Linux może być konieczne zainstalowanie dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfbf1-367">Dokładne wersje i nazwy mogą się nieco różnić w zależności od wybranej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="dfbf1-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfbf1-368">Ubuntu</span></span>

<span data-ttu-id="dfbf1-369">W przypadku dystrybucji Ubuntu wymagane jest zainstalowanie następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="dfbf1-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="dfbf1-370">liblttng-ust0</span></span>
- <span data-ttu-id="dfbf1-371">libcurl3 (dla 14. x i 16. x)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="dfbf1-372">libcurl4 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="dfbf1-373">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="dfbf1-373">libssl1.0.0</span></span>
- <span data-ttu-id="dfbf1-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="dfbf1-374">libkrb5-3</span></span>
- <span data-ttu-id="dfbf1-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="dfbf1-375">zlib1g</span></span>
- <span data-ttu-id="dfbf1-376">libicu52 (dla 14. x)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="dfbf1-377">libicu55 (dla 16. x)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="dfbf1-378">libicu57 (dla 17. x)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="dfbf1-379">libicu60 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="dfbf1-380">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="dfbf1-381">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="dfbf1-382">Większość wersji programu Ubuntu obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="dfbf1-383">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="dfbf1-384">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="dfbf1-385">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="dfbf1-385">CentOS and Fedora</span></span>

<span data-ttu-id="dfbf1-386">Dystrybucje CentOS wymagają zainstalowanych następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="dfbf1-387">LTTng — zespół sklepu uniwersalnego</span><span class="sxs-lookup"><span data-stu-id="dfbf1-387">lttng-ust</span></span>
- <span data-ttu-id="dfbf1-388">libcurl</span><span class="sxs-lookup"><span data-stu-id="dfbf1-388">libcurl</span></span>
- <span data-ttu-id="dfbf1-389">OpenSSL — libs</span><span class="sxs-lookup"><span data-stu-id="dfbf1-389">openssl-libs</span></span>
- <span data-ttu-id="dfbf1-390">krb5 — libs</span><span class="sxs-lookup"><span data-stu-id="dfbf1-390">krb5-libs</span></span>
- <span data-ttu-id="dfbf1-391">libicu</span><span class="sxs-lookup"><span data-stu-id="dfbf1-391">libicu</span></span>
- <span data-ttu-id="dfbf1-392">zlib</span><span class="sxs-lookup"><span data-stu-id="dfbf1-392">zlib</span></span>

<span data-ttu-id="dfbf1-393">Fedora użytkownicy: Jeśli OpenSSL wersja >= 1,1, należy zainstalować polecenie **COMPAT-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="dfbf1-394">W przypadku platformy .NET Core 2,0 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="dfbf1-395">libunwind</span><span class="sxs-lookup"><span data-stu-id="dfbf1-395">libunwind</span></span>
- <span data-ttu-id="dfbf1-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="dfbf1-396">libuuid</span></span>

<span data-ttu-id="dfbf1-397">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="dfbf1-398">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="dfbf1-399">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="dfbf1-400">Większość wersji CentOS i Fedora obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="dfbf1-401">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="dfbf1-402">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="dfbf1-403">Platforma .NET Core jest obsługiwana w następujących wersjach macOS:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-403">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="dfbf1-404">`+` Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-404">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="dfbf1-405">Wersja platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="dfbf1-405">.NET Core Version</span></span> | <span data-ttu-id="dfbf1-406">macOS</span><span class="sxs-lookup"><span data-stu-id="dfbf1-406">macOS</span></span>                 | <span data-ttu-id="dfbf1-407">Architektury</span><span class="sxs-lookup"><span data-stu-id="dfbf1-407">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="dfbf1-408">3.1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-408">3.1</span></span>               | <span data-ttu-id="dfbf1-409">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-409">High Sierra (10.13+)</span></span>  | <span data-ttu-id="dfbf1-410">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-410">x64</span></span> | [<span data-ttu-id="dfbf1-411">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="dfbf1-411">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="dfbf1-412">3.0</span><span class="sxs-lookup"><span data-stu-id="dfbf1-412">3.0</span></span>               | <span data-ttu-id="dfbf1-413">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-413">High Sierra (10.13+)</span></span>  | <span data-ttu-id="dfbf1-414">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-414">x64</span></span> | [<span data-ttu-id="dfbf1-415">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="dfbf1-415">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="dfbf1-416">2.2</span><span class="sxs-lookup"><span data-stu-id="dfbf1-416">2.2</span></span>               | <span data-ttu-id="dfbf1-417">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-417">Sierra (10.12+)</span></span>       | <span data-ttu-id="dfbf1-418">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-418">x64</span></span> | [<span data-ttu-id="dfbf1-419">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="dfbf1-419">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="dfbf1-420">2.1</span><span class="sxs-lookup"><span data-stu-id="dfbf1-420">2.1</span></span>               | <span data-ttu-id="dfbf1-421">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="dfbf1-421">Sierra (10.12+)</span></span>       | <span data-ttu-id="dfbf1-422">x64</span><span class="sxs-lookup"><span data-stu-id="dfbf1-422">x64</span></span> | [<span data-ttu-id="dfbf1-423">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="dfbf1-423">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="dfbf1-424">Począwszy od programu macOS Catalina (wersja 10,15), całe oprogramowanie skompilowane po 1 czerwca 2019, które jest dystrybuowane z IDENTYFIKATORem dewelopera, musi być notarialne.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-424">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="dfbf1-425">To wymaganie dotyczy środowiska uruchomieniowego .NET Core, zestaw .NET Core SDK i oprogramowania utworzonego za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-425">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="dfbf1-426">Instalatory dla programu .NET Core (zarówno środowisko uruchomieniowe, jak i zestaw SDK) w wersji 3,1, 3,0 i 2,1 zostały zgłoszone od 18 lutego 2020.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-426">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="dfbf1-427">Wcześniejsze wersje nie zostały ujawnione.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-427">Prior released versions aren't notarized.</span></span> <span data-ttu-id="dfbf1-428">Jeśli uruchomisz zanotarialną aplikację, zobaczysz komunikat o błędzie podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="dfbf1-428">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![Alert notarization macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="dfbf1-430">Aby uzyskać więcej informacji na temat sposobu, w jaki wymuszone — notarization wpływa na platformę .NET Core (i aplikacje platformy .NET Core), zobacz [Praca z MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-430">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="dfbf1-431">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="dfbf1-431">libgdiplus</span></span>

<span data-ttu-id="dfbf1-432">Aplikacje .NET Core używające zestawu *System. Drawing. Common* wymagają zainstalowania libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-432">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="dfbf1-433">Łatwym sposobem uzyskania libgdiplus jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS.</span><span class="sxs-lookup"><span data-stu-id="dfbf1-433">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="dfbf1-434">Po zainstalowaniu *rozwiązania brew*Zainstaluj libgdiplus, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="dfbf1-434">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="dfbf1-435">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="dfbf1-435">Next steps</span></span>

- <span data-ttu-id="dfbf1-436">Aby opracowywać i uruchamiać aplikacje, zainstaluj [zestaw .NET Core SDK](sdk.md) (w tym środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-436">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="dfbf1-437">Aby uruchamiać aplikacje utworzone przez inne osoby, zainstaluj [środowisko uruchomieniowe programu .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf1-437">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
