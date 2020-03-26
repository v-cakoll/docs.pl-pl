---
title: Zależności core sdk i środowiska uruchomieniowego platformy .NET — .NET Core
description: Szczegółowe informacje o wymaganiach wstępnych dotyczących systemu operacyjnego i architektury procesora, aby zainstalować pakiet .NET Core SDK i środowisko wykonawcze w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 023b8fdf029dd6b17fe2186296d87dd7507c60b5
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546565"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="96de2-103">Zależności i wymagania podstawowe platformy .NET</span><span class="sxs-lookup"><span data-stu-id="96de2-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="96de2-104">W tym artykule opisano, które systemy operacyjne i architektura procesora są obsługiwane przez program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96de2-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="96de2-105">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="96de2-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="96de2-106">.NET Rdzeń 3.1</span><span class="sxs-lookup"><span data-stu-id="96de2-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="96de2-107">Z programem .NET Core 3.1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="96de2-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="96de2-108">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="96de2-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="96de2-109">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="96de2-109">OS</span></span>                            | <span data-ttu-id="96de2-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="96de2-110">Version</span></span>                        | <span data-ttu-id="96de2-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="96de2-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="96de2-112">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="96de2-112">Windows Client</span></span>                | <span data-ttu-id="96de2-113">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="96de2-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="96de2-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-114">x64, x86</span></span>        |
| <span data-ttu-id="96de2-115">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="96de2-115">Windows 10 Client</span></span>             | <span data-ttu-id="96de2-116">Wersja 1607+</span><span class="sxs-lookup"><span data-stu-id="96de2-116">Version 1607+</span></span>                  | <span data-ttu-id="96de2-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-117">x64, x86</span></span>        |
| <span data-ttu-id="96de2-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="96de2-118">Windows Server</span></span>                | <span data-ttu-id="96de2-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="96de2-119">2012 R2+</span></span>                       | <span data-ttu-id="96de2-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-120">x64, x86</span></span>        |
| <span data-ttu-id="96de2-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="96de2-121">Nano Server</span></span>                   | <span data-ttu-id="96de2-122">Wersja 1803+</span><span class="sxs-lookup"><span data-stu-id="96de2-122">Version 1803+</span></span>                  | <span data-ttu-id="96de2-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="96de2-123">x64, ARM32</span></span>      |

<span data-ttu-id="96de2-124">Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 3.1 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 3.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="96de2-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="96de2-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="96de2-126">*Program .NET Core 3.0 jest obecnie niew pomocy technicznej. Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="96de2-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="96de2-127">Z programem .NET Core 3.0 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="96de2-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="96de2-128">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="96de2-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="96de2-129">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="96de2-129">OS</span></span>                            | <span data-ttu-id="96de2-130">Wersja</span><span class="sxs-lookup"><span data-stu-id="96de2-130">Version</span></span>                        | <span data-ttu-id="96de2-131">Architektury</span><span class="sxs-lookup"><span data-stu-id="96de2-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="96de2-132">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="96de2-132">Windows Client</span></span>                | <span data-ttu-id="96de2-133">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="96de2-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="96de2-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-134">x64, x86</span></span>        |
| <span data-ttu-id="96de2-135">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="96de2-135">Windows 10 Client</span></span>             | <span data-ttu-id="96de2-136">Wersja 1607+</span><span class="sxs-lookup"><span data-stu-id="96de2-136">Version 1607+</span></span>                  | <span data-ttu-id="96de2-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-137">x64, x86</span></span>        |
| <span data-ttu-id="96de2-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="96de2-138">Windows Server</span></span>                | <span data-ttu-id="96de2-139">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="96de2-139">2012 R2+</span></span>                       | <span data-ttu-id="96de2-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-140">x64, x86</span></span>        |
| <span data-ttu-id="96de2-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="96de2-141">Nano Server</span></span>                   | <span data-ttu-id="96de2-142">Wersja 1803+</span><span class="sxs-lookup"><span data-stu-id="96de2-142">Version 1803+</span></span>                  | <span data-ttu-id="96de2-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="96de2-143">x64, ARM32</span></span>      |

<span data-ttu-id="96de2-144">Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 3.0 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 3.0 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="96de2-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="96de2-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="96de2-146">*.NET Core 2.2 jest obecnie poza wsparciem. Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="96de2-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="96de2-147">Z programem .NET Core 2.2 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="96de2-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="96de2-148">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="96de2-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="96de2-149">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="96de2-149">OS</span></span>                            | <span data-ttu-id="96de2-150">Wersja</span><span class="sxs-lookup"><span data-stu-id="96de2-150">Version</span></span>                        | <span data-ttu-id="96de2-151">Architektury</span><span class="sxs-lookup"><span data-stu-id="96de2-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="96de2-152">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="96de2-152">Windows Client</span></span>                | <span data-ttu-id="96de2-153">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="96de2-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="96de2-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-154">x64, x86</span></span>        |
| <span data-ttu-id="96de2-155">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="96de2-155">Windows 10 Client</span></span>             | <span data-ttu-id="96de2-156">Wersja 1607+</span><span class="sxs-lookup"><span data-stu-id="96de2-156">Version 1607+</span></span>                  | <span data-ttu-id="96de2-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-157">x64, x86</span></span>        |
| <span data-ttu-id="96de2-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="96de2-158">Windows Server</span></span>                | <span data-ttu-id="96de2-159">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="96de2-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="96de2-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-160">x64, x86</span></span>        |
| <span data-ttu-id="96de2-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="96de2-161">Nano Server</span></span>                   | <span data-ttu-id="96de2-162">Wersja 1803+</span><span class="sxs-lookup"><span data-stu-id="96de2-162">Version 1803+</span></span>                   | <span data-ttu-id="96de2-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="96de2-163">x64, ARM32</span></span>      |

<span data-ttu-id="96de2-164">Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 2.2 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 2.2 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="96de2-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="96de2-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="96de2-166">Z programem .NET Core 2.1 obsługiwane są następujące wersje systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="96de2-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="96de2-167">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="96de2-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="96de2-168">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="96de2-168">OS</span></span>                            | <span data-ttu-id="96de2-169">Wersja</span><span class="sxs-lookup"><span data-stu-id="96de2-169">Version</span></span>                        | <span data-ttu-id="96de2-170">Architektury</span><span class="sxs-lookup"><span data-stu-id="96de2-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="96de2-171">Klient systemu Windows</span><span class="sxs-lookup"><span data-stu-id="96de2-171">Windows Client</span></span>                | <span data-ttu-id="96de2-172">7 SP1+, 8.1</span><span class="sxs-lookup"><span data-stu-id="96de2-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="96de2-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-173">x64, x86</span></span>        |
| <span data-ttu-id="96de2-174">Klient systemu Windows 10</span><span class="sxs-lookup"><span data-stu-id="96de2-174">Windows 10 Client</span></span>             | <span data-ttu-id="96de2-175">Wersja 1607+</span><span class="sxs-lookup"><span data-stu-id="96de2-175">Version 1607+</span></span>                  | <span data-ttu-id="96de2-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-176">x64, x86</span></span>        |
| <span data-ttu-id="96de2-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="96de2-177">Windows Server</span></span>                | <span data-ttu-id="96de2-178">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="96de2-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="96de2-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="96de2-179">x64, x86</span></span>        |
| <span data-ttu-id="96de2-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="96de2-180">Nano Server</span></span>                   | <span data-ttu-id="96de2-181">Wersja 1803+</span><span class="sxs-lookup"><span data-stu-id="96de2-181">Version 1803+</span></span>                  | <span data-ttu-id="96de2-182">x64,</span><span class="sxs-lookup"><span data-stu-id="96de2-182">x64,</span></span>            |

<span data-ttu-id="96de2-183">Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 2.1 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 2.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="96de2-184">Windows 7 / Vista / 8.1 / Serwer 2008 R2</span><span class="sxs-lookup"><span data-stu-id="96de2-184">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="96de2-185">Dodatkowe zależności są wymagane, jeśli instalujesz pakiet .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="96de2-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="96de2-186">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="96de2-186">Windows 7 SP1</span></span>
- <span data-ttu-id="96de2-187">Dodatek SP 2 dla systemu Windows Vista</span><span class="sxs-lookup"><span data-stu-id="96de2-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="96de2-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="96de2-188">Windows 8.1</span></span>
- <span data-ttu-id="96de2-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="96de2-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="96de2-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="96de2-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="96de2-191">Zainstaluj następujące instalacje:</span><span class="sxs-lookup"><span data-stu-id="96de2-191">Install the following:</span></span>

- <span data-ttu-id="96de2-192">[Microsoft Visual C++ 2015 Redystrybucjowa aktualizacja 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="96de2-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="96de2-193">aktualizacja kb2533623</span><span class="sxs-lookup"><span data-stu-id="96de2-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="96de2-194">Powyższe wymagania są również wymagane, jeśli natkniesz się na jeden z następujących błędów:</span><span class="sxs-lookup"><span data-stu-id="96de2-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="96de2-195">Program nie może się uruchomić, ponieważ na komputerze brakuje *pliku api-ms-win-crt-runtime-l1-1-0.dll.*</span><span class="sxs-lookup"><span data-stu-id="96de2-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="96de2-196">Spróbuj ponownie zainstalować program, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="96de2-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="96de2-197">\-lub -</span><span class="sxs-lookup"><span data-stu-id="96de2-197">\- or -</span></span>
>
> <span data-ttu-id="96de2-198">Znaleziono *hostfxr.dll* biblioteki, ale ładowanie go z *języka C:\\\<path_to_app>\\hostfxr.dll* nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="96de2-198">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="96de2-199">.NET Rdzeń 3.1</span><span class="sxs-lookup"><span data-stu-id="96de2-199">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="96de2-200">.NET Core 3.1 traktuje Linuksa jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="96de2-200">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="96de2-201">Istnieje jedna kompilacja Linuksa (na architekturę chipa) dla obsługiwanych dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="96de2-201">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="96de2-202">.NET Core 3.1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="96de2-202">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="96de2-203">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="96de2-203">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="96de2-204">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="96de2-204">OS</span></span>                             | <span data-ttu-id="96de2-205">Wersja</span><span class="sxs-lookup"><span data-stu-id="96de2-205">Version</span></span>               | <span data-ttu-id="96de2-206">Architektury</span><span class="sxs-lookup"><span data-stu-id="96de2-206">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="96de2-207">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-207">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="96de2-208">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="96de2-208">6, 7, 8</span></span>               | <span data-ttu-id="96de2-209">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-209">x64</span></span> |
| <span data-ttu-id="96de2-210">CentOS</span><span class="sxs-lookup"><span data-stu-id="96de2-210">CentOS</span></span>                         | <span data-ttu-id="96de2-211">7+</span><span class="sxs-lookup"><span data-stu-id="96de2-211">7+</span></span>                    | <span data-ttu-id="96de2-212">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-212">x64</span></span> |
| <span data-ttu-id="96de2-213">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-213">Oracle Linux</span></span>                   | <span data-ttu-id="96de2-214">7+</span><span class="sxs-lookup"><span data-stu-id="96de2-214">7+</span></span>                    | <span data-ttu-id="96de2-215">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-215">x64</span></span> |
| <span data-ttu-id="96de2-216">Fedora</span><span class="sxs-lookup"><span data-stu-id="96de2-216">Fedora</span></span>                         | <span data-ttu-id="96de2-217">30+</span><span class="sxs-lookup"><span data-stu-id="96de2-217">30+</span></span>                   | <span data-ttu-id="96de2-218">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-218">x64</span></span> |
| <span data-ttu-id="96de2-219">Debian</span><span class="sxs-lookup"><span data-stu-id="96de2-219">Debian</span></span>                         | <span data-ttu-id="96de2-220">9+</span><span class="sxs-lookup"><span data-stu-id="96de2-220">9+</span></span>                    | <span data-ttu-id="96de2-221">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="96de2-221">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="96de2-222">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="96de2-222">Ubuntu</span></span>                         | <span data-ttu-id="96de2-223">16.04+</span><span class="sxs-lookup"><span data-stu-id="96de2-223">16.04+</span></span>                | <span data-ttu-id="96de2-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="96de2-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="96de2-225">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="96de2-225">Linux Mint</span></span>                     | <span data-ttu-id="96de2-226">18+</span><span class="sxs-lookup"><span data-stu-id="96de2-226">18+</span></span>                   | <span data-ttu-id="96de2-227">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-227">x64</span></span> |
| <span data-ttu-id="96de2-228">openSUSE</span><span class="sxs-lookup"><span data-stu-id="96de2-228">openSUSE</span></span>                       | <span data-ttu-id="96de2-229">15+</span><span class="sxs-lookup"><span data-stu-id="96de2-229">15+</span></span>                   | <span data-ttu-id="96de2-230">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-230">x64</span></span> |
| <span data-ttu-id="96de2-231">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="96de2-231">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="96de2-232">12 sp2+</span><span class="sxs-lookup"><span data-stu-id="96de2-232">12 SP2+</span></span>               | <span data-ttu-id="96de2-233">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-233">x64</span></span> |
| <span data-ttu-id="96de2-234">Alpejski Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-234">Alpine Linux</span></span>                   | <span data-ttu-id="96de2-235">3.10+</span><span class="sxs-lookup"><span data-stu-id="96de2-235">3.10+</span></span>                 | <span data-ttu-id="96de2-236">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="96de2-236">x64, ARM64</span></span> |

<span data-ttu-id="96de2-237">Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 3.1 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 3.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-237">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="96de2-238">Aby uzyskać więcej informacji o tym, jak zainstalować .NET Core 3.1 na ARM64 (jądro 4.14+), zobacz [Instalowanie .NET Core 3.0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="96de2-238">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96de2-239">Obsługa ARM64 wymaga jądra Linuksa 4.14 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="96de2-239">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="96de2-240">Niektóre dystrybucje Linuksa spełniają to wymaganie, podczas gdy inne nie.</span><span class="sxs-lookup"><span data-stu-id="96de2-240">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="96de2-241">Na przykład Ubuntu 18.04 jest obsługiwany, ale Ubuntu 16.04 nie.</span><span class="sxs-lookup"><span data-stu-id="96de2-241">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="96de2-242">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="96de2-242">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="96de2-243">*Program .NET Core 3.0 jest obecnie niew pomocy technicznej. Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="96de2-243">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="96de2-244">.NET Core 3.0 traktuje Linuksa jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="96de2-244">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="96de2-245">Istnieje jedna kompilacja Linuksa (na architekturę chipa) dla obsługiwanych dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="96de2-245">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="96de2-246">.NET Core 3.0 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="96de2-246">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="96de2-247">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="96de2-247">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="96de2-248">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="96de2-248">OS</span></span>                             | <span data-ttu-id="96de2-249">Wersja</span><span class="sxs-lookup"><span data-stu-id="96de2-249">Version</span></span>               | <span data-ttu-id="96de2-250">Architektury</span><span class="sxs-lookup"><span data-stu-id="96de2-250">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="96de2-251">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-251">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="96de2-252">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="96de2-252">6, 7, 8</span></span>               | <span data-ttu-id="96de2-253">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-253">x64</span></span> |
| <span data-ttu-id="96de2-254">CentOS</span><span class="sxs-lookup"><span data-stu-id="96de2-254">CentOS</span></span>                         | <span data-ttu-id="96de2-255">7+</span><span class="sxs-lookup"><span data-stu-id="96de2-255">7+</span></span>                    | <span data-ttu-id="96de2-256">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-256">x64</span></span> |
| <span data-ttu-id="96de2-257">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-257">Oracle Linux</span></span>                   | <span data-ttu-id="96de2-258">7+</span><span class="sxs-lookup"><span data-stu-id="96de2-258">7+</span></span>                    | <span data-ttu-id="96de2-259">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-259">x64</span></span> |
| <span data-ttu-id="96de2-260">Fedora</span><span class="sxs-lookup"><span data-stu-id="96de2-260">Fedora</span></span>                         | <span data-ttu-id="96de2-261">29+</span><span class="sxs-lookup"><span data-stu-id="96de2-261">29+</span></span>                   | <span data-ttu-id="96de2-262">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-262">x64</span></span> |
| <span data-ttu-id="96de2-263">Debian</span><span class="sxs-lookup"><span data-stu-id="96de2-263">Debian</span></span>                         | <span data-ttu-id="96de2-264">9+</span><span class="sxs-lookup"><span data-stu-id="96de2-264">9+</span></span>                    | <span data-ttu-id="96de2-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="96de2-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="96de2-266">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="96de2-266">Ubuntu</span></span>                         | <span data-ttu-id="96de2-267">16.04+</span><span class="sxs-lookup"><span data-stu-id="96de2-267">16.04+</span></span>                | <span data-ttu-id="96de2-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="96de2-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="96de2-269">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="96de2-269">Linux Mint</span></span>                     | <span data-ttu-id="96de2-270">18+</span><span class="sxs-lookup"><span data-stu-id="96de2-270">18+</span></span>                   | <span data-ttu-id="96de2-271">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-271">x64</span></span> |
| <span data-ttu-id="96de2-272">openSUSE</span><span class="sxs-lookup"><span data-stu-id="96de2-272">openSUSE</span></span>                       | <span data-ttu-id="96de2-273">15+</span><span class="sxs-lookup"><span data-stu-id="96de2-273">15+</span></span>                   | <span data-ttu-id="96de2-274">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-274">x64</span></span> |
| <span data-ttu-id="96de2-275">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="96de2-275">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="96de2-276">12 sp2+</span><span class="sxs-lookup"><span data-stu-id="96de2-276">12 SP2+</span></span>               | <span data-ttu-id="96de2-277">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-277">x64</span></span> |
| <span data-ttu-id="96de2-278">Alpejski Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-278">Alpine Linux</span></span>                   | <span data-ttu-id="96de2-279">3,8+</span><span class="sxs-lookup"><span data-stu-id="96de2-279">3.8+</span></span>                  | <span data-ttu-id="96de2-280">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="96de2-280">x64, ARM64</span></span> |

<span data-ttu-id="96de2-281">Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 3.0 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 3.0 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-281">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="96de2-282">Aby uzyskać więcej informacji o tym, jak zainstalować .NET Core 3.0 na ARM64, zobacz [Instalowanie .NET Core 3.0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="96de2-282">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="96de2-283">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="96de2-283">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="96de2-284">*.NET Core 2.2 jest obecnie poza wsparciem. Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="96de2-284">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="96de2-285">.NET Core 2.2 traktuje Linuksa jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="96de2-285">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="96de2-286">Istnieje jedna kompilacja Linuksa (na architekturę chipa) dla obsługiwanych dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="96de2-286">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="96de2-287">.NET Core 2.2 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="96de2-287">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="96de2-288">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="96de2-288">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="96de2-289">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="96de2-289">OS</span></span>                             |  <span data-ttu-id="96de2-290">Wersja</span><span class="sxs-lookup"><span data-stu-id="96de2-290">Version</span></span>                |  <span data-ttu-id="96de2-291">Architektury</span><span class="sxs-lookup"><span data-stu-id="96de2-291">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="96de2-292">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-292">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="96de2-293">6, 7</span><span class="sxs-lookup"><span data-stu-id="96de2-293">6, 7</span></span>                   | <span data-ttu-id="96de2-294">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-294">x64</span></span> |
| <span data-ttu-id="96de2-295">CentOS</span><span class="sxs-lookup"><span data-stu-id="96de2-295">CentOS</span></span>                         |  <span data-ttu-id="96de2-296">7</span><span class="sxs-lookup"><span data-stu-id="96de2-296">7</span></span>                      | <span data-ttu-id="96de2-297">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-297">x64</span></span> |
| <span data-ttu-id="96de2-298">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-298">Oracle Linux</span></span>                   |  <span data-ttu-id="96de2-299">7</span><span class="sxs-lookup"><span data-stu-id="96de2-299">7</span></span>                      | <span data-ttu-id="96de2-300">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-300">x64</span></span> |
| <span data-ttu-id="96de2-301">Fedora</span><span class="sxs-lookup"><span data-stu-id="96de2-301">Fedora</span></span>                         |  <span data-ttu-id="96de2-302">29, 30</span><span class="sxs-lookup"><span data-stu-id="96de2-302">29, 30</span></span>                 | <span data-ttu-id="96de2-303">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-303">x64</span></span> |
| <span data-ttu-id="96de2-304">Debian</span><span class="sxs-lookup"><span data-stu-id="96de2-304">Debian</span></span>                         |  <span data-ttu-id="96de2-305">9</span><span class="sxs-lookup"><span data-stu-id="96de2-305">9</span></span>                      | <span data-ttu-id="96de2-306">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="96de2-306">x64, ARM32</span></span> |
| <span data-ttu-id="96de2-307">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="96de2-307">Ubuntu</span></span>                         |  <span data-ttu-id="96de2-308">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="96de2-308">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="96de2-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="96de2-309">x64, ARM32</span></span> |
| <span data-ttu-id="96de2-310">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="96de2-310">Linux Mint</span></span>                     |  <span data-ttu-id="96de2-311">17, 18</span><span class="sxs-lookup"><span data-stu-id="96de2-311">17, 18</span></span>                 | <span data-ttu-id="96de2-312">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-312">x64</span></span> |
| <span data-ttu-id="96de2-313">openSUSE</span><span class="sxs-lookup"><span data-stu-id="96de2-313">openSUSE</span></span>                       |  <span data-ttu-id="96de2-314">15+</span><span class="sxs-lookup"><span data-stu-id="96de2-314">15+</span></span>                    | <span data-ttu-id="96de2-315">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-315">x64</span></span> |
| <span data-ttu-id="96de2-316">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="96de2-316">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="96de2-317">12 sp2+</span><span class="sxs-lookup"><span data-stu-id="96de2-317">12 SP2+</span></span>                | <span data-ttu-id="96de2-318">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-318">x64</span></span> |
| <span data-ttu-id="96de2-319">Alpejski Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-319">Alpine Linux</span></span>                   |  <span data-ttu-id="96de2-320">3,8+</span><span class="sxs-lookup"><span data-stu-id="96de2-320">3.8+</span></span>                   | <span data-ttu-id="96de2-321">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-321">x64</span></span> |

<span data-ttu-id="96de2-322">Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 2.2 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 2.2 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-322">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="96de2-323">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="96de2-323">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="96de2-324">.NET Core 2.1 traktuje Linuksa jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="96de2-324">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="96de2-325">Istnieje jedna kompilacja Linuksa (na architekturę chipa) dla obsługiwanych dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="96de2-325">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="96de2-326">.NET Core 2.1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="96de2-326">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="96de2-327">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="96de2-327">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="96de2-328">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="96de2-328">OS</span></span>                             |  <span data-ttu-id="96de2-329">Wersja</span><span class="sxs-lookup"><span data-stu-id="96de2-329">Version</span></span>                |  <span data-ttu-id="96de2-330">Architektury</span><span class="sxs-lookup"><span data-stu-id="96de2-330">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="96de2-331">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-331">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="96de2-332">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="96de2-332">6, 7, 8</span></span>                | <span data-ttu-id="96de2-333">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-333">x64</span></span> |
| <span data-ttu-id="96de2-334">CentOS</span><span class="sxs-lookup"><span data-stu-id="96de2-334">CentOS</span></span>                         |  <span data-ttu-id="96de2-335">7+</span><span class="sxs-lookup"><span data-stu-id="96de2-335">7+</span></span>                     | <span data-ttu-id="96de2-336">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-336">x64</span></span> |
| <span data-ttu-id="96de2-337">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-337">Oracle Linux</span></span>                   |  <span data-ttu-id="96de2-338">7+</span><span class="sxs-lookup"><span data-stu-id="96de2-338">7+</span></span>                     | <span data-ttu-id="96de2-339">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-339">x64</span></span> |
| <span data-ttu-id="96de2-340">Fedora</span><span class="sxs-lookup"><span data-stu-id="96de2-340">Fedora</span></span>                         |  <span data-ttu-id="96de2-341">30+</span><span class="sxs-lookup"><span data-stu-id="96de2-341">30+</span></span>                    | <span data-ttu-id="96de2-342">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-342">x64</span></span> |
| <span data-ttu-id="96de2-343">Debian</span><span class="sxs-lookup"><span data-stu-id="96de2-343">Debian</span></span>                         |  <span data-ttu-id="96de2-344">9</span><span class="sxs-lookup"><span data-stu-id="96de2-344">9</span></span>                      | <span data-ttu-id="96de2-345">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="96de2-345">x64, ARM32</span></span> |
| <span data-ttu-id="96de2-346">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="96de2-346">Ubuntu</span></span>                         |  <span data-ttu-id="96de2-347">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="96de2-347">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="96de2-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="96de2-348">x64, ARM32</span></span> |
| <span data-ttu-id="96de2-349">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="96de2-349">Linux Mint</span></span>                     |  <span data-ttu-id="96de2-350">17+</span><span class="sxs-lookup"><span data-stu-id="96de2-350">17+</span></span>                    | <span data-ttu-id="96de2-351">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-351">x64</span></span> |
| <span data-ttu-id="96de2-352">openSUSE</span><span class="sxs-lookup"><span data-stu-id="96de2-352">openSUSE</span></span>                       |  <span data-ttu-id="96de2-353">15+</span><span class="sxs-lookup"><span data-stu-id="96de2-353">15+</span></span>                    | <span data-ttu-id="96de2-354">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-354">x64</span></span> |
| <span data-ttu-id="96de2-355">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="96de2-355">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="96de2-356">12 sp2+</span><span class="sxs-lookup"><span data-stu-id="96de2-356">12 SP2+</span></span>                | <span data-ttu-id="96de2-357">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-357">x64</span></span> |
| <span data-ttu-id="96de2-358">Alpejski Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-358">Alpine Linux</span></span>                   |  <span data-ttu-id="96de2-359">3,8+</span><span class="sxs-lookup"><span data-stu-id="96de2-359">3.8+</span></span>                   | <span data-ttu-id="96de2-360">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-360">x64</span></span> |

<span data-ttu-id="96de2-361">Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 2.1 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 2.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-361">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="96de2-362">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="96de2-362">Linux distribution dependencies</span></span>

<span data-ttu-id="96de2-363">Na podstawie dystrybucji linuksa może być konieczne zainstalowanie dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="96de2-363">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96de2-364">Dokładne wersje i nazwy mogą się nieznacznie różnić w wybranej dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="96de2-364">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="96de2-365">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="96de2-365">Ubuntu</span></span>

<span data-ttu-id="96de2-366">Dystrybucje Ubuntu wymagają zainstalowania następujących bibliotek:</span><span class="sxs-lookup"><span data-stu-id="96de2-366">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="96de2-367">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="96de2-367">liblttng-ust0</span></span>
- <span data-ttu-id="96de2-368">libcurl3 (dla 14.x i 16.x)</span><span class="sxs-lookup"><span data-stu-id="96de2-368">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="96de2-369">libcurl4 (dla 18.x)</span><span class="sxs-lookup"><span data-stu-id="96de2-369">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="96de2-370">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="96de2-370">libssl1.0.0</span></span>
- <span data-ttu-id="96de2-371">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="96de2-371">libkrb5-3</span></span>
- <span data-ttu-id="96de2-372">zlib1g</span><span class="sxs-lookup"><span data-stu-id="96de2-372">zlib1g</span></span>
- <span data-ttu-id="96de2-373">libicu52 (dla 14.x)</span><span class="sxs-lookup"><span data-stu-id="96de2-373">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="96de2-374">libicu55 (dla 16.x)</span><span class="sxs-lookup"><span data-stu-id="96de2-374">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="96de2-375">libicu57 (dla 17.x)</span><span class="sxs-lookup"><span data-stu-id="96de2-375">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="96de2-376">libicu60 (dla 18.x)</span><span class="sxs-lookup"><span data-stu-id="96de2-376">libicu60 (for 18.x)</span></span>

<span data-ttu-id="96de2-377">W przypadku aplikacji .NET Core korzystających z zestawu *System.Drawing.Common* potrzebne są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="96de2-377">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="96de2-378">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="96de2-378">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="96de2-379">Większość wersji Ubuntu zawiera wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="96de2-379">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="96de2-380">Najnowszą wersję libgdiplus można zainstalować, dodając do systemu repozytorium Mono.</span><span class="sxs-lookup"><span data-stu-id="96de2-380">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="96de2-381">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="96de2-381">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="96de2-382">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="96de2-382">CentOS and Fedora</span></span>

<span data-ttu-id="96de2-383">Dystrybucje centos wymagają następujących bibliotek zainstalowanych:</span><span class="sxs-lookup"><span data-stu-id="96de2-383">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="96de2-384">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="96de2-384">lttng-ust</span></span>
- <span data-ttu-id="96de2-385">Libcurl</span><span class="sxs-lookup"><span data-stu-id="96de2-385">libcurl</span></span>
- <span data-ttu-id="96de2-386">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="96de2-386">openssl-libs</span></span>
- <span data-ttu-id="96de2-387">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="96de2-387">krb5-libs</span></span>
- <span data-ttu-id="96de2-388">libicu</span><span class="sxs-lookup"><span data-stu-id="96de2-388">libicu</span></span>
- <span data-ttu-id="96de2-389">Zlib</span><span class="sxs-lookup"><span data-stu-id="96de2-389">zlib</span></span>

<span data-ttu-id="96de2-390">Użytkownicy Fedory: Jeśli wersja OpenSSL >= 1.1, musisz zainstalować **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="96de2-390">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="96de2-391">W przypadku platformy .NET Core 2.0 wymagane są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="96de2-391">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="96de2-392">libunwind</span><span class="sxs-lookup"><span data-stu-id="96de2-392">libunwind</span></span>
- <span data-ttu-id="96de2-393">libuuid</span><span class="sxs-lookup"><span data-stu-id="96de2-393">libuuid</span></span>

<span data-ttu-id="96de2-394">Aby uzyskać więcej informacji na temat zależności, zobacz [Samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-394">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="96de2-395">W przypadku aplikacji .NET Core korzystających z zestawu *System.Drawing.Common* potrzebne są również następujące zależności:</span><span class="sxs-lookup"><span data-stu-id="96de2-395">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="96de2-396">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="96de2-396">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="96de2-397">Większość wersji CentOS i Fedory zawiera wcześniejszą wersję libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="96de2-397">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="96de2-398">Najnowszą wersję libgdiplus można zainstalować, dodając do systemu repozytorium Mono.</span><span class="sxs-lookup"><span data-stu-id="96de2-398">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="96de2-399">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="96de2-399">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="96de2-400">Program .NET Core jest obsługiwany w następujących wersjach systemu macOS:</span><span class="sxs-lookup"><span data-stu-id="96de2-400">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="96de2-401">Symbol `+` reprezentuje wersję minimalną.</span><span class="sxs-lookup"><span data-stu-id="96de2-401">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="96de2-402">Wersja podstawowa .NET</span><span class="sxs-lookup"><span data-stu-id="96de2-402">.NET Core Version</span></span> | <span data-ttu-id="96de2-403">macOS</span><span class="sxs-lookup"><span data-stu-id="96de2-403">macOS</span></span>                 | <span data-ttu-id="96de2-404">Architektury</span><span class="sxs-lookup"><span data-stu-id="96de2-404">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="96de2-405">3.1</span><span class="sxs-lookup"><span data-stu-id="96de2-405">3.1</span></span>               | <span data-ttu-id="96de2-406">Wysoka Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="96de2-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="96de2-407">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-407">x64</span></span> | [<span data-ttu-id="96de2-408">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="96de2-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="96de2-409">3.0</span><span class="sxs-lookup"><span data-stu-id="96de2-409">3.0</span></span>               | <span data-ttu-id="96de2-410">Wysoka Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="96de2-410">High Sierra (10.13+)</span></span>  | <span data-ttu-id="96de2-411">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-411">x64</span></span> | [<span data-ttu-id="96de2-412">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="96de2-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="96de2-413">2.2</span><span class="sxs-lookup"><span data-stu-id="96de2-413">2.2</span></span>               | <span data-ttu-id="96de2-414">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="96de2-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="96de2-415">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-415">x64</span></span> | [<span data-ttu-id="96de2-416">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="96de2-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="96de2-417">2.1</span><span class="sxs-lookup"><span data-stu-id="96de2-417">2.1</span></span>               | <span data-ttu-id="96de2-418">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="96de2-418">Sierra (10.12+)</span></span>       | <span data-ttu-id="96de2-419">x64</span><span class="sxs-lookup"><span data-stu-id="96de2-419">x64</span></span> | [<span data-ttu-id="96de2-420">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="96de2-420">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="96de2-421">Począwszy od systemu macOS Catalina (wersja 10.15), wszystkie programy utworzone po 1 czerwca 2019 r., które są dystrybuowane z identyfikatorem dewelopera, muszą zostać poś poś poś poś pośowiane notapozycją.</span><span class="sxs-lookup"><span data-stu-id="96de2-421">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="96de2-422">To wymaganie dotyczy środowiska uruchomieniowego .NET Core, .NET Core SDK i oprogramowania utworzonego za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="96de2-422">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="96de2-423">Instalatory programu .NET Core (zarówno środowiska uruchomieniowego, jak i SDK) w wersji 3.1, 3.0 i 2.1 zostały poś pośpomniejsione notapozycją od 18 lutego 2020 r.</span><span class="sxs-lookup"><span data-stu-id="96de2-423">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="96de2-424">Wcześniej wydane wersje nie są pośa poś pośliczone notapozytem.</span><span class="sxs-lookup"><span data-stu-id="96de2-424">Prior released versions aren't notarized.</span></span> <span data-ttu-id="96de2-425">Jeśli uruchomisz aplikację nieobjętą notawią, zobaczysz błąd podobny do następującego obrazu:</span><span class="sxs-lookup"><span data-stu-id="96de2-425">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alert notagizowania macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="96de2-427">Aby uzyskać więcej informacji o tym, jak wymuszona notapozycja wpływa na program .NET Core (i aplikacje .NET Core), zobacz [Praca z systemem macOS Catalina Notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-427">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="96de2-428">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="96de2-428">libgdiplus</span></span>

<span data-ttu-id="96de2-429">Aplikacje .NET Core korzystające z *zestawu System.Drawing.Common* wymagają zainstalowania libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="96de2-429">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="96de2-430">Łatwym sposobem uzyskania libgdiplus jest użycie menedżera pakietów [Homebrew ("brew")](https://brew.sh/) dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="96de2-430">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="96de2-431">Po *zainstalowaniu naparu*zainstaluj libgdiplus, wykonując następujące polecenia w wierszu polecenia Terminal (polecenie):</span><span class="sxs-lookup"><span data-stu-id="96de2-431">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="96de2-432">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="96de2-432">Next steps</span></span>

- <span data-ttu-id="96de2-433">Aby tworzyć i uruchamiać aplikacje, zainstaluj [zestaw SDK .NET Core](sdk.md) (w tym środowisko wykonawcze).</span><span class="sxs-lookup"><span data-stu-id="96de2-433">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="96de2-434">Aby uruchomić aplikacje utworzone przez inne osoby, zainstaluj [środowisko uruchomieniowe .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="96de2-434">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
