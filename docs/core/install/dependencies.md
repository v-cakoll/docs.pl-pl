---
title: Zależności zestaw .NET Core SDK i środowiska uruchomieniowego — .NET Core
description: Szczegółowe informacje na temat wymagań wstępnych dotyczących architektury procesora i systemu operacyjnego w celu zainstalowania zestaw .NET Core SDK i środowiska uruchomieniowego w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 06/01/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 81f6ab436428d71f71d9fd0f560bd2b0512a519b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590763"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="d6e0a-103">Zależności i wymagania dotyczące platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6e0a-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="d6e0a-104">W tym artykule szczegółowo przedstawiono systemy operacyjne i architekturę procesora CPU obsługiwane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="d6e0a-105">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="d6e0a-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="d6e0a-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="d6e0a-107">W przypadku programu .NET Core 3,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="d6e0a-108">`+`Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d6e0a-109">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="d6e0a-109">OS</span></span>                            | <span data-ttu-id="d6e0a-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="d6e0a-110">Version</span></span>                        | <span data-ttu-id="d6e0a-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="d6e0a-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="d6e0a-112">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d6e0a-112">Windows Client</span></span>                | <span data-ttu-id="d6e0a-113">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="d6e0a-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-114">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-115">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="d6e0a-115">Windows 10 Client</span></span>             | <span data-ttu-id="d6e0a-116">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-116">Version 1607+</span></span>                  | <span data-ttu-id="d6e0a-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-117">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="d6e0a-118">Windows Server</span></span>                | <span data-ttu-id="d6e0a-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-119">2012 R2+</span></span>                       | <span data-ttu-id="d6e0a-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-120">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="d6e0a-121">Nano Server</span></span>                   | <span data-ttu-id="d6e0a-122">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-122">Version 1803+</span></span>                  | <span data-ttu-id="d6e0a-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d6e0a-123">x64, ARM32</span></span>      |

<span data-ttu-id="d6e0a-124">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="d6e0a-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d6e0a-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="d6e0a-126">*Platforma .NET Core 3,0 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="d6e0a-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="d6e0a-127">W przypadku programu .NET Core 3,0 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="d6e0a-128">`+`Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d6e0a-129">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="d6e0a-129">OS</span></span>                            | <span data-ttu-id="d6e0a-130">Wersja</span><span class="sxs-lookup"><span data-stu-id="d6e0a-130">Version</span></span>                        | <span data-ttu-id="d6e0a-131">Architektury</span><span class="sxs-lookup"><span data-stu-id="d6e0a-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="d6e0a-132">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d6e0a-132">Windows Client</span></span>                | <span data-ttu-id="d6e0a-133">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="d6e0a-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-134">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-135">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="d6e0a-135">Windows 10 Client</span></span>             | <span data-ttu-id="d6e0a-136">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-136">Version 1607+</span></span>                  | <span data-ttu-id="d6e0a-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-137">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="d6e0a-138">Windows Server</span></span>                | <span data-ttu-id="d6e0a-139">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-139">2012 R2+</span></span>                       | <span data-ttu-id="d6e0a-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-140">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="d6e0a-141">Nano Server</span></span>                   | <span data-ttu-id="d6e0a-142">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-142">Version 1803+</span></span>                  | <span data-ttu-id="d6e0a-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d6e0a-143">x64, ARM32</span></span>      |

<span data-ttu-id="d6e0a-144">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="d6e0a-145">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="d6e0a-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="d6e0a-146">*Platforma .NET Core 2,2 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="d6e0a-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="d6e0a-147">W przypadku programu .NET Core 2,2 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="d6e0a-148">`+`Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d6e0a-149">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="d6e0a-149">OS</span></span>                            | <span data-ttu-id="d6e0a-150">Wersja</span><span class="sxs-lookup"><span data-stu-id="d6e0a-150">Version</span></span>                        | <span data-ttu-id="d6e0a-151">Architektury</span><span class="sxs-lookup"><span data-stu-id="d6e0a-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="d6e0a-152">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d6e0a-152">Windows Client</span></span>                | <span data-ttu-id="d6e0a-153">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="d6e0a-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-154">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-155">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="d6e0a-155">Windows 10 Client</span></span>             | <span data-ttu-id="d6e0a-156">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-156">Version 1607+</span></span>                  | <span data-ttu-id="d6e0a-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-157">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="d6e0a-158">Windows Server</span></span>                | <span data-ttu-id="d6e0a-159">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="d6e0a-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-160">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="d6e0a-161">Nano Server</span></span>                   | <span data-ttu-id="d6e0a-162">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-162">Version 1803+</span></span>                   | <span data-ttu-id="d6e0a-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d6e0a-163">x64, ARM32</span></span>      |

<span data-ttu-id="d6e0a-164">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="d6e0a-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="d6e0a-166">W przypadku programu .NET Core 2,1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="d6e0a-167">`+`Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d6e0a-168">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="d6e0a-168">OS</span></span>                            | <span data-ttu-id="d6e0a-169">Wersja</span><span class="sxs-lookup"><span data-stu-id="d6e0a-169">Version</span></span>                        | <span data-ttu-id="d6e0a-170">Architektury</span><span class="sxs-lookup"><span data-stu-id="d6e0a-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="d6e0a-171">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d6e0a-171">Windows Client</span></span>                | <span data-ttu-id="d6e0a-172">7 Z DODATKIEM SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="d6e0a-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-173">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-174">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="d6e0a-174">Windows 10 Client</span></span>             | <span data-ttu-id="d6e0a-175">Wersja 1607 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-175">Version 1607+</span></span>                  | <span data-ttu-id="d6e0a-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-176">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="d6e0a-177">Windows Server</span></span>                | <span data-ttu-id="d6e0a-178">2008 R2 Z DODATKIEM SP1 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="d6e0a-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="d6e0a-179">x64, x86</span></span>        |
| <span data-ttu-id="d6e0a-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="d6e0a-180">Nano Server</span></span>                   | <span data-ttu-id="d6e0a-181">Wersja 1803 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-181">Version 1803+</span></span>                  | <span data-ttu-id="d6e0a-182">procesorów</span><span class="sxs-lookup"><span data-stu-id="d6e0a-182">x64,</span></span>            |

<span data-ttu-id="d6e0a-183">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="d6e0a-184">Windows 7/Vista/8,1/Server 2008 R2/serwer 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d6e0a-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="d6e0a-185">Jeśli instalujesz zestaw .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows, wymagane są dodatkowe zależności:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="d6e0a-186">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-186">Windows 7 SP1</span></span>
- <span data-ttu-id="d6e0a-187">Windows Vista z dodatkiem SP 2</span><span class="sxs-lookup"><span data-stu-id="d6e0a-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="d6e0a-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-188">Windows 8.1</span></span>
- <span data-ttu-id="d6e0a-189">Windows Server 2008 z dodatkiem R2</span><span class="sxs-lookup"><span data-stu-id="d6e0a-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="d6e0a-190">Windows Server 2012 z dodatkiem R2</span><span class="sxs-lookup"><span data-stu-id="d6e0a-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="d6e0a-191">Zainstaluj następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-191">Install the following:</span></span>

- <span data-ttu-id="d6e0a-192">[Microsoft Visual C++ 2015 redystrybucyjnej aktualizacji 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="d6e0a-193">POPRAWKI KB2533623</span><span class="sxs-lookup"><span data-stu-id="d6e0a-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="d6e0a-194">Powyższe wymagania są również wymagane w przypadku wystąpienia jednego z następujących błędów:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="d6e0a-195">Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-CRT-Runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="d6e0a-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="d6e0a-196">Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="d6e0a-197">\-oraz</span><span class="sxs-lookup"><span data-stu-id="d6e0a-197">\- or -</span></span>
>
> <span data-ttu-id="d6e0a-198">Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-cor-timezone-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="d6e0a-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="d6e0a-199">Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="d6e0a-200">\-oraz</span><span class="sxs-lookup"><span data-stu-id="d6e0a-200">\- or -</span></span>
>
> <span data-ttu-id="d6e0a-201">Znaleziono bibliotekę *hostfxr. dll* , ale ładowanie jej z *dysku C: \\ \<path_to_app> \\ hostfxr. dll* nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="d6e0a-202">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="d6e0a-203">Program .NET Core 3,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="d6e0a-204">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="d6e0a-205">Platforma .NET Core 3,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="d6e0a-206">`+`Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d6e0a-207">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="d6e0a-207">OS</span></span>                             | <span data-ttu-id="d6e0a-208">Wersja</span><span class="sxs-lookup"><span data-stu-id="d6e0a-208">Version</span></span>               | <span data-ttu-id="d6e0a-209">Architektury</span><span class="sxs-lookup"><span data-stu-id="d6e0a-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="d6e0a-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="d6e0a-211">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="d6e0a-211">6, 7, 8</span></span>               | <span data-ttu-id="d6e0a-212">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-212">x64</span></span> |
| <span data-ttu-id="d6e0a-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="d6e0a-213">CentOS</span></span>                         | <span data-ttu-id="d6e0a-214">7 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-214">7+</span></span>                    | <span data-ttu-id="d6e0a-215">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-215">x64</span></span> |
| <span data-ttu-id="d6e0a-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-216">Oracle Linux</span></span>                   | <span data-ttu-id="d6e0a-217">7 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-217">7+</span></span>                    | <span data-ttu-id="d6e0a-218">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-218">x64</span></span> |
| <span data-ttu-id="d6e0a-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="d6e0a-219">Fedora</span></span>                         | <span data-ttu-id="d6e0a-220">30 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-220">30+</span></span>                   | <span data-ttu-id="d6e0a-221">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-221">x64</span></span> |
| <span data-ttu-id="d6e0a-222">Debian</span><span class="sxs-lookup"><span data-stu-id="d6e0a-222">Debian</span></span>                         | <span data-ttu-id="d6e0a-223">9 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-223">9+</span></span>                    | <span data-ttu-id="d6e0a-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="d6e0a-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d6e0a-225">Ubuntu</span></span>                         | <span data-ttu-id="d6e0a-226">16.04 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-226">16.04+</span></span>                | <span data-ttu-id="d6e0a-227">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="d6e0a-228">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-228">Linux Mint</span></span>                     | <span data-ttu-id="d6e0a-229">18 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-229">18+</span></span>                   | <span data-ttu-id="d6e0a-230">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-230">x64</span></span> |
| <span data-ttu-id="d6e0a-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d6e0a-231">openSUSE</span></span>                       | <span data-ttu-id="d6e0a-232">15 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-232">15+</span></span>                   | <span data-ttu-id="d6e0a-233">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-233">x64</span></span> |
| <span data-ttu-id="d6e0a-234">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="d6e0a-235">12 Z DODATKIEM SP2 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-235">12 SP2+</span></span>               | <span data-ttu-id="d6e0a-236">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-236">x64</span></span> |
| <span data-ttu-id="d6e0a-237">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-237">Alpine Linux</span></span>                   | <span data-ttu-id="d6e0a-238">3.10 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-238">3.10+</span></span>                 | <span data-ttu-id="d6e0a-239">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-239">x64, ARM64</span></span> |

<span data-ttu-id="d6e0a-240">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="d6e0a-241">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,1 w systemie ARM64 (jądro 4.14 +), zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6e0a-242">Obsługa ARM64 wymaga jądra systemu Linux 4,14 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="d6e0a-243">Niektóre dystrybucje systemu Linux spełniają to wymaganie, a inne nie.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="d6e0a-244">Na przykład Ubuntu 18,04 jest obsługiwany, ale Ubuntu 16,04 nie jest.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="d6e0a-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d6e0a-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="d6e0a-246">*Platforma .NET Core 3,0 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="d6e0a-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="d6e0a-247">Program .NET Core 3,0 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="d6e0a-248">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="d6e0a-249">Platforma .NET Core 3,0 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="d6e0a-250">`+`Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d6e0a-251">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="d6e0a-251">OS</span></span>                             | <span data-ttu-id="d6e0a-252">Wersja</span><span class="sxs-lookup"><span data-stu-id="d6e0a-252">Version</span></span>               | <span data-ttu-id="d6e0a-253">Architektury</span><span class="sxs-lookup"><span data-stu-id="d6e0a-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="d6e0a-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="d6e0a-255">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="d6e0a-255">6, 7, 8</span></span>               | <span data-ttu-id="d6e0a-256">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-256">x64</span></span> |
| <span data-ttu-id="d6e0a-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="d6e0a-257">CentOS</span></span>                         | <span data-ttu-id="d6e0a-258">7 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-258">7+</span></span>                    | <span data-ttu-id="d6e0a-259">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-259">x64</span></span> |
| <span data-ttu-id="d6e0a-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-260">Oracle Linux</span></span>                   | <span data-ttu-id="d6e0a-261">7 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-261">7+</span></span>                    | <span data-ttu-id="d6e0a-262">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-262">x64</span></span> |
| <span data-ttu-id="d6e0a-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="d6e0a-263">Fedora</span></span>                         | <span data-ttu-id="d6e0a-264">29 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-264">29+</span></span>                   | <span data-ttu-id="d6e0a-265">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-265">x64</span></span> |
| <span data-ttu-id="d6e0a-266">Debian</span><span class="sxs-lookup"><span data-stu-id="d6e0a-266">Debian</span></span>                         | <span data-ttu-id="d6e0a-267">9 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-267">9+</span></span>                    | <span data-ttu-id="d6e0a-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="d6e0a-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d6e0a-269">Ubuntu</span></span>                         | <span data-ttu-id="d6e0a-270">16.04 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-270">16.04+</span></span>                | <span data-ttu-id="d6e0a-271">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="d6e0a-272">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-272">Linux Mint</span></span>                     | <span data-ttu-id="d6e0a-273">18 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-273">18+</span></span>                   | <span data-ttu-id="d6e0a-274">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-274">x64</span></span> |
| <span data-ttu-id="d6e0a-275">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d6e0a-275">openSUSE</span></span>                       | <span data-ttu-id="d6e0a-276">15 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-276">15+</span></span>                   | <span data-ttu-id="d6e0a-277">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-277">x64</span></span> |
| <span data-ttu-id="d6e0a-278">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="d6e0a-279">12 Z DODATKIEM SP2 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-279">12 SP2+</span></span>               | <span data-ttu-id="d6e0a-280">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-280">x64</span></span> |
| <span data-ttu-id="d6e0a-281">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-281">Alpine Linux</span></span>                   | <span data-ttu-id="d6e0a-282">3.8 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-282">3.8+</span></span>                  | <span data-ttu-id="d6e0a-283">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-283">x64, ARM64</span></span> |

<span data-ttu-id="d6e0a-284">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="d6e0a-285">Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="d6e0a-286">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="d6e0a-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="d6e0a-287">*Platforma .NET Core 2,2 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="d6e0a-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="d6e0a-288">Program .NET Core 2,2 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="d6e0a-289">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="d6e0a-290">Platforma .NET Core 2,2 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="d6e0a-291">`+`Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d6e0a-292">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="d6e0a-292">OS</span></span>                             |  <span data-ttu-id="d6e0a-293">Wersja</span><span class="sxs-lookup"><span data-stu-id="d6e0a-293">Version</span></span>                |  <span data-ttu-id="d6e0a-294">Architektury</span><span class="sxs-lookup"><span data-stu-id="d6e0a-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="d6e0a-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="d6e0a-296">6, 7</span><span class="sxs-lookup"><span data-stu-id="d6e0a-296">6, 7</span></span>                   | <span data-ttu-id="d6e0a-297">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-297">x64</span></span> |
| <span data-ttu-id="d6e0a-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="d6e0a-298">CentOS</span></span>                         |  <span data-ttu-id="d6e0a-299">7</span><span class="sxs-lookup"><span data-stu-id="d6e0a-299">7</span></span>                      | <span data-ttu-id="d6e0a-300">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-300">x64</span></span> |
| <span data-ttu-id="d6e0a-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-301">Oracle Linux</span></span>                   |  <span data-ttu-id="d6e0a-302">7</span><span class="sxs-lookup"><span data-stu-id="d6e0a-302">7</span></span>                      | <span data-ttu-id="d6e0a-303">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-303">x64</span></span> |
| <span data-ttu-id="d6e0a-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="d6e0a-304">Fedora</span></span>                         |  <span data-ttu-id="d6e0a-305">29, 30</span><span class="sxs-lookup"><span data-stu-id="d6e0a-305">29, 30</span></span>                 | <span data-ttu-id="d6e0a-306">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-306">x64</span></span> |
| <span data-ttu-id="d6e0a-307">Debian</span><span class="sxs-lookup"><span data-stu-id="d6e0a-307">Debian</span></span>                         |  <span data-ttu-id="d6e0a-308">9</span><span class="sxs-lookup"><span data-stu-id="d6e0a-308">9</span></span>                      | <span data-ttu-id="d6e0a-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d6e0a-309">x64, ARM32</span></span> |
| <span data-ttu-id="d6e0a-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d6e0a-310">Ubuntu</span></span>                         |  <span data-ttu-id="d6e0a-311">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="d6e0a-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="d6e0a-312">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d6e0a-312">x64, ARM32</span></span> |
| <span data-ttu-id="d6e0a-313">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-313">Linux Mint</span></span>                     |  <span data-ttu-id="d6e0a-314">17, 18</span><span class="sxs-lookup"><span data-stu-id="d6e0a-314">17, 18</span></span>                 | <span data-ttu-id="d6e0a-315">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-315">x64</span></span> |
| <span data-ttu-id="d6e0a-316">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d6e0a-316">openSUSE</span></span>                       |  <span data-ttu-id="d6e0a-317">15 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-317">15+</span></span>                    | <span data-ttu-id="d6e0a-318">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-318">x64</span></span> |
| <span data-ttu-id="d6e0a-319">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="d6e0a-320">12 Z DODATKIEM SP2 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-320">12 SP2+</span></span>                | <span data-ttu-id="d6e0a-321">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-321">x64</span></span> |
| <span data-ttu-id="d6e0a-322">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-322">Alpine Linux</span></span>                   |  <span data-ttu-id="d6e0a-323">3.8 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-323">3.8+</span></span>                   | <span data-ttu-id="d6e0a-324">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-324">x64</span></span> |

<span data-ttu-id="d6e0a-325">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="d6e0a-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="d6e0a-327">Program .NET Core 2,1 traktuje system Linux jako pojedynczy systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="d6e0a-328">Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="d6e0a-329">Platforma .NET Core 2,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="d6e0a-330">`+`Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d6e0a-331">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="d6e0a-331">OS</span></span>                             |  <span data-ttu-id="d6e0a-332">Wersja</span><span class="sxs-lookup"><span data-stu-id="d6e0a-332">Version</span></span>                |  <span data-ttu-id="d6e0a-333">Architektury</span><span class="sxs-lookup"><span data-stu-id="d6e0a-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="d6e0a-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="d6e0a-335">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="d6e0a-335">6, 7, 8</span></span>                | <span data-ttu-id="d6e0a-336">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-336">x64</span></span> |
| <span data-ttu-id="d6e0a-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="d6e0a-337">CentOS</span></span>                         |  <span data-ttu-id="d6e0a-338">7 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-338">7+</span></span>                     | <span data-ttu-id="d6e0a-339">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-339">x64</span></span> |
| <span data-ttu-id="d6e0a-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-340">Oracle Linux</span></span>                   |  <span data-ttu-id="d6e0a-341">7 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-341">7+</span></span>                     | <span data-ttu-id="d6e0a-342">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-342">x64</span></span> |
| <span data-ttu-id="d6e0a-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="d6e0a-343">Fedora</span></span>                         |  <span data-ttu-id="d6e0a-344">30 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-344">30+</span></span>                    | <span data-ttu-id="d6e0a-345">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-345">x64</span></span> |
| <span data-ttu-id="d6e0a-346">Debian</span><span class="sxs-lookup"><span data-stu-id="d6e0a-346">Debian</span></span>                         |  <span data-ttu-id="d6e0a-347">9</span><span class="sxs-lookup"><span data-stu-id="d6e0a-347">9</span></span>                      | <span data-ttu-id="d6e0a-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d6e0a-348">x64, ARM32</span></span> |
| <span data-ttu-id="d6e0a-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d6e0a-349">Ubuntu</span></span>                         |  <span data-ttu-id="d6e0a-350">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="d6e0a-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="d6e0a-351">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="d6e0a-351">x64, ARM32</span></span> |
| <span data-ttu-id="d6e0a-352">Mennic systemu Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-352">Linux Mint</span></span>                     |  <span data-ttu-id="d6e0a-353">17 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-353">17+</span></span>                    | <span data-ttu-id="d6e0a-354">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-354">x64</span></span> |
| <span data-ttu-id="d6e0a-355">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d6e0a-355">openSUSE</span></span>                       |  <span data-ttu-id="d6e0a-356">15 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-356">15+</span></span>                    | <span data-ttu-id="d6e0a-357">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-357">x64</span></span> |
| <span data-ttu-id="d6e0a-358">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="d6e0a-359">12 Z DODATKIEM SP2 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-359">12 SP2+</span></span>                | <span data-ttu-id="d6e0a-360">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-360">x64</span></span> |
| <span data-ttu-id="d6e0a-361">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-361">Alpine Linux</span></span>                   |  <span data-ttu-id="d6e0a-362">3.8 +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-362">3.8+</span></span>                   | <span data-ttu-id="d6e0a-363">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-363">x64</span></span> |

<span data-ttu-id="d6e0a-364">Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="d6e0a-365">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="d6e0a-365">Linux distribution dependencies</span></span>

<span data-ttu-id="d6e0a-366">W zależności od dystrybucji systemu Linux może być konieczne zainstalowanie dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6e0a-367">Dokładne wersje i nazwy mogą się nieco różnić w zależności od wybranej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="d6e0a-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d6e0a-368">Ubuntu</span></span>

<span data-ttu-id="d6e0a-369">W przypadku dystrybucji Ubuntu wymagane jest zainstalowanie następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="d6e0a-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="d6e0a-370">liblttng-ust0</span></span>
- <span data-ttu-id="d6e0a-371">libcurl3 (dla 14. x i 16. x)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="d6e0a-372">libcurl4 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="d6e0a-373">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="d6e0a-373">libssl1.0.0</span></span>
- <span data-ttu-id="d6e0a-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="d6e0a-374">libkrb5-3</span></span>
- <span data-ttu-id="d6e0a-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="d6e0a-375">zlib1g</span></span>
- <span data-ttu-id="d6e0a-376">libicu52 (dla 14. x)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="d6e0a-377">libicu55 (dla 16. x)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="d6e0a-378">libicu57 (dla 17. x)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="d6e0a-379">libicu60 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="d6e0a-380">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="d6e0a-381">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="d6e0a-382">Większość wersji programu Ubuntu obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="d6e0a-383">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="d6e0a-384">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="d6e0a-385">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="d6e0a-385">CentOS and Fedora</span></span>

<span data-ttu-id="d6e0a-386">Dystrybucje CentOS wymagają zainstalowanych następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="d6e0a-387">LTTng — zespół sklepu uniwersalnego</span><span class="sxs-lookup"><span data-stu-id="d6e0a-387">lttng-ust</span></span>
- <span data-ttu-id="d6e0a-388">libcurl</span><span class="sxs-lookup"><span data-stu-id="d6e0a-388">libcurl</span></span>
- <span data-ttu-id="d6e0a-389">OpenSSL — libs</span><span class="sxs-lookup"><span data-stu-id="d6e0a-389">openssl-libs</span></span>
- <span data-ttu-id="d6e0a-390">krb5 — libs</span><span class="sxs-lookup"><span data-stu-id="d6e0a-390">krb5-libs</span></span>
- <span data-ttu-id="d6e0a-391">libicu</span><span class="sxs-lookup"><span data-stu-id="d6e0a-391">libicu</span></span>
- <span data-ttu-id="d6e0a-392">zlib</span><span class="sxs-lookup"><span data-stu-id="d6e0a-392">zlib</span></span>

<span data-ttu-id="d6e0a-393">Fedora użytkownicy: Jeśli OpenSSL wersja >= 1,1, należy zainstalować polecenie **COMPAT-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="d6e0a-394">W przypadku platformy .NET Core 2,0 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="d6e0a-395">libunwind</span><span class="sxs-lookup"><span data-stu-id="d6e0a-395">libunwind</span></span>
- <span data-ttu-id="d6e0a-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="d6e0a-396">libuuid</span></span>

<span data-ttu-id="d6e0a-397">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="d6e0a-398">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="d6e0a-399">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="d6e0a-400">Większość wersji CentOS i Fedora obejmuje wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="d6e0a-401">Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="d6e0a-402">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="alpine"></a><span data-ttu-id="d6e0a-403">Alp</span><span class="sxs-lookup"><span data-stu-id="d6e0a-403">Alpine</span></span>

<span data-ttu-id="d6e0a-404">Dystrybucje Alpine wymagają zainstalowania następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-404">Alpine distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="d6e0a-405">ICU-libs (nie jest to zbędne, jeśli Globalizacja jest wyłączona)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-405">icu-libs (this is not needed if globalization is disabled)</span></span>
- <span data-ttu-id="d6e0a-406">krb5 — libs</span><span class="sxs-lookup"><span data-stu-id="d6e0a-406">krb5-libs</span></span>
- <span data-ttu-id="d6e0a-407">libcurl</span><span class="sxs-lookup"><span data-stu-id="d6e0a-407">libcurl</span></span>
- <span data-ttu-id="d6e0a-408">libintl</span><span class="sxs-lookup"><span data-stu-id="d6e0a-408">libintl</span></span>
- <span data-ttu-id="d6e0a-409">libssl 1.1 (dla Alpine 3,9 lub nowszego) lub libssl 1.0 (dla starszych)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-409">libssl1.1 (for Alpine 3.9 or later) or libssl1.0 (for older ones)</span></span>
- <span data-ttu-id="d6e0a-410">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="d6e0a-410">libstdc++</span></span>
- <span data-ttu-id="d6e0a-411">LTTng — zespół sklepu uniwersalnego</span><span class="sxs-lookup"><span data-stu-id="d6e0a-411">lttng-ust</span></span>
- <span data-ttu-id="d6e0a-412">numactl (opcjonalne, przydatne tylko w przypadku urządzeń z włączoną architekturą NUMA)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-412">numactl (optional, useful only for devices with NUMA enabled)</span></span>
- <span data-ttu-id="d6e0a-413">zlib</span><span class="sxs-lookup"><span data-stu-id="d6e0a-413">zlib</span></span>

<span data-ttu-id="d6e0a-414">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-414">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="d6e0a-415">libgdiplus (jest dostępny tylko w repozytorium brzeg/testowanie)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-415">libgdiplus (it is available only in the edge/testing repository)</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="d6e0a-416">Platforma .NET Core jest obsługiwana w następujących wersjach macOS:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-416">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="d6e0a-417">`+`Symbol reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-417">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d6e0a-418">Wersja platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6e0a-418">.NET Core Version</span></span> | <span data-ttu-id="d6e0a-419">macOS</span><span class="sxs-lookup"><span data-stu-id="d6e0a-419">macOS</span></span>                 | <span data-ttu-id="d6e0a-420">Architektury</span><span class="sxs-lookup"><span data-stu-id="d6e0a-420">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="d6e0a-421">3,1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-421">3.1</span></span>               | <span data-ttu-id="d6e0a-422">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-422">High Sierra (10.13+)</span></span>  | <span data-ttu-id="d6e0a-423">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-423">x64</span></span> | [<span data-ttu-id="d6e0a-424">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="d6e0a-424">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="d6e0a-425">3.0</span><span class="sxs-lookup"><span data-stu-id="d6e0a-425">3.0</span></span>               | <span data-ttu-id="d6e0a-426">Wysoka firma Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-426">High Sierra (10.13+)</span></span>  | <span data-ttu-id="d6e0a-427">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-427">x64</span></span> | [<span data-ttu-id="d6e0a-428">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="d6e0a-428">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="d6e0a-429">2.2</span><span class="sxs-lookup"><span data-stu-id="d6e0a-429">2.2</span></span>               | <span data-ttu-id="d6e0a-430">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-430">Sierra (10.12+)</span></span>       | <span data-ttu-id="d6e0a-431">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-431">x64</span></span> | [<span data-ttu-id="d6e0a-432">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="d6e0a-432">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="d6e0a-433">2.1</span><span class="sxs-lookup"><span data-stu-id="d6e0a-433">2.1</span></span>               | <span data-ttu-id="d6e0a-434">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="d6e0a-434">Sierra (10.12+)</span></span>       | <span data-ttu-id="d6e0a-435">x64</span><span class="sxs-lookup"><span data-stu-id="d6e0a-435">x64</span></span> | [<span data-ttu-id="d6e0a-436">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="d6e0a-436">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="d6e0a-437">Począwszy od programu macOS Catalina (wersja 10,15), całe oprogramowanie skompilowane po 1 czerwca 2019, które jest dystrybuowane z IDENTYFIKATORem dewelopera, musi być notarialne.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-437">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="d6e0a-438">To wymaganie dotyczy środowiska uruchomieniowego .NET Core, zestaw .NET Core SDK i oprogramowania utworzonego za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-438">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="d6e0a-439">Instalatory dla programu .NET Core (zarówno środowisko uruchomieniowe, jak i zestaw SDK) w wersji 3,1, 3,0 i 2,1 zostały zgłoszone od 18 lutego 2020.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-439">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="d6e0a-440">Wcześniejsze wersje nie zostały ujawnione.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-440">Prior released versions aren't notarized.</span></span> <span data-ttu-id="d6e0a-441">Jeśli uruchomisz zanotarialną aplikację, zobaczysz komunikat o błędzie podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="d6e0a-441">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![Alert notarization macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="d6e0a-443">Aby uzyskać więcej informacji na temat sposobu, w jaki wymuszone — notarization wpływa na platformę .NET Core (i aplikacje platformy .NET Core), zobacz [Praca z MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-443">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="d6e0a-444">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="d6e0a-444">libgdiplus</span></span>

<span data-ttu-id="d6e0a-445">Aplikacje .NET Core używające zestawu *System. Drawing. Common* wymagają zainstalowania libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-445">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="d6e0a-446">Łatwym sposobem uzyskania libgdiplus jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS.</span><span class="sxs-lookup"><span data-stu-id="d6e0a-446">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="d6e0a-447">Po zainstalowaniu *rozwiązania brew*Zainstaluj libgdiplus, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="d6e0a-447">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="d6e0a-448">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d6e0a-448">Next steps</span></span>

- <span data-ttu-id="d6e0a-449">Aby opracowywać i uruchamiać aplikacje, zainstaluj [zestaw .NET Core SDK](sdk.md) (w tym środowisko uruchomieniowe).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-449">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="d6e0a-450">Aby uruchamiać aplikacje utworzone przez inne osoby, zainstaluj [środowisko uruchomieniowe programu .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="d6e0a-450">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
