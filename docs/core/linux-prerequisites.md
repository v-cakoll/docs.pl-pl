---
title: "Wymagania wstępne dotyczące platformy .NET Core w systemie Linux"
description: "Obsługiwane wersje systemu Linux i zależności platformy .NET Core na tworzenie, wdrażanie i uruchamianie aplikacji .NET Core na maszynach z systemem Linux."
keywords: Debian, ubuntu Linux, .NET i .NET core RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: 1a698516ae2aea9242fe929cd213e9dac0b1119d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="193d8-104">Wymagania wstępne dotyczące platformy .NET Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="193d8-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="193d8-105">W tym artykule opisano zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="193d8-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="193d8-106">Obsługiwane Linux dystrybucje wersje i zależności, które należy wykonać dotyczą dwa sposoby tworzenia aplikacji platformy .NET Core w systemie Linux:</span><span class="sxs-lookup"><span data-stu-id="193d8-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="193d8-107">Wiersza polecenia z ulubionego edytora</span><span class="sxs-lookup"><span data-stu-id="193d8-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="193d8-108">Kod Visual Studio</span><span class="sxs-lookup"><span data-stu-id="193d8-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="193d8-109">Obsługiwane wersje systemu Linux</span><span class="sxs-lookup"><span data-stu-id="193d8-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="193d8-110">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="193d8-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="193d8-111">.NET core 2.0 traktuje Linux jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="193d8-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="193d8-112">Brak jednej kompilacji systemu Linux (na architektura mikroukładu) dla obsługiwanych dystrybucjach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="193d8-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="193d8-113">NET Core 2.x jest obsługiwana w systemie Linux 64-bitowej (`x86_64` lub `amd64`) dystrybucje/wersji:</span><span class="sxs-lookup"><span data-stu-id="193d8-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="193d8-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="193d8-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="193d8-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="193d8-115">CentOS 7</span></span>
 * <span data-ttu-id="193d8-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="193d8-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="193d8-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="193d8-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="193d8-118">Debian 8.7 lub nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="193d8-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="193d8-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="193d8-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="193d8-120">Linux mennic 18, Linux mennic 17</span><span class="sxs-lookup"><span data-stu-id="193d8-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="193d8-121">openSUSE 42,2 lub nowszej wersji</span><span class="sxs-lookup"><span data-stu-id="193d8-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="193d8-122">SUSE Linux Enterprise (SLES) 12 z dodatkiem SP2 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="193d8-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="193d8-123">Zobacz [2.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) Pełna lista .NET Core 2.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="193d8-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="193d8-124">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="193d8-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="193d8-125">Oprogramowanie .NET core 1.x jest obsługiwana w systemie Linux 64-bitowej (`x86_64` lub `amd64`) dystrybucje/wersji:</span><span class="sxs-lookup"><span data-stu-id="193d8-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="193d8-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="193d8-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="193d8-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="193d8-127">CentOS 7</span></span>
* <span data-ttu-id="193d8-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="193d8-128">Oracle Linux 7</span></span>
* <span data-ttu-id="193d8-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="193d8-129">Fedora 24</span></span>
* <span data-ttu-id="193d8-130">Debian 8.2 lub nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="193d8-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="193d8-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="193d8-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="193d8-132">Ubuntu 16.10 jest obsługiwana przez najnowszej wersji poprawki .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="193d8-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="193d8-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="193d8-133">Linux Mint 17</span></span>
* <span data-ttu-id="193d8-134">openSUSE 42.1 lub nowszej wersji (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="193d8-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="193d8-135">Zobacz [1.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) Pełna lista .NET Core 1.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="193d8-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="193d8-136">Zależności dystrybucji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="193d8-136">Linux distribution dependencies</span></span>

<span data-ttu-id="193d8-137">Poniżej mają być przykłady.</span><span class="sxs-lookup"><span data-stu-id="193d8-137">The following are intended to be examples.</span></span> <span data-ttu-id="193d8-138">Na wybranym dystrybucji systemu Linux, nazwy i wersje dokładne mogą się nieco różnić.</span><span class="sxs-lookup"><span data-stu-id="193d8-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="193d8-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="193d8-139">Ubuntu</span></span>

<span data-ttu-id="193d8-140">Ubuntu dystrybucji wymagają następujących bibliotek zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="193d8-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="193d8-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="193d8-141">libunwind8</span></span>
* <span data-ttu-id="193d8-142">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="193d8-142">liblttng-ust0</span></span>
* <span data-ttu-id="193d8-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="193d8-143">libcurl3</span></span>
* <span data-ttu-id="193d8-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="193d8-144">libssl1.0.0</span></span>
* <span data-ttu-id="193d8-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="193d8-145">libuuid1</span></span>
* <span data-ttu-id="193d8-146">libkrb5</span><span class="sxs-lookup"><span data-stu-id="193d8-146">libkrb5</span></span>
* <span data-ttu-id="193d8-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="193d8-147">zlib1g</span></span>
* <span data-ttu-id="193d8-148">libicu52 (dla 14.X)</span><span class="sxs-lookup"><span data-stu-id="193d8-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="193d8-149">libicu55 (dla 16.X)</span><span class="sxs-lookup"><span data-stu-id="193d8-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="193d8-150">libicu57 (dla 17.X)</span><span class="sxs-lookup"><span data-stu-id="193d8-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="193d8-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="193d8-151">CentOS</span></span>

<span data-ttu-id="193d8-152">CentOS dystrybucji wymagają następujących bibliotek zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="193d8-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="193d8-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="193d8-153">libunwind</span></span>
* <span data-ttu-id="193d8-154">lttng ust</span><span class="sxs-lookup"><span data-stu-id="193d8-154">lttng-ust</span></span>
* <span data-ttu-id="193d8-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="193d8-155">libcurl</span></span>
* <span data-ttu-id="193d8-156">biblioteki openssl</span><span class="sxs-lookup"><span data-stu-id="193d8-156">openssl-libs</span></span>
* <span data-ttu-id="193d8-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="193d8-157">libuuid</span></span>
* <span data-ttu-id="193d8-158">krb5 biblioteki</span><span class="sxs-lookup"><span data-stu-id="193d8-158">krb5-libs</span></span>
* <span data-ttu-id="193d8-159">libicu</span><span class="sxs-lookup"><span data-stu-id="193d8-159">libicu</span></span>
* <span data-ttu-id="193d8-160">Zlib</span><span class="sxs-lookup"><span data-stu-id="193d8-160">zlib</span></span>

<span data-ttu-id="193d8-161">Aby uzyskać więcej informacji o zależnościach, zobacz [aplikacje w systemie Linux Self-contained](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="193d8-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="193d8-162">Instalowanie zależności .NET Core za pomocą natywnego instalatorów</span><span class="sxs-lookup"><span data-stu-id="193d8-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="193d8-163">Oprogramowanie .NET core, natywnego instalatory są dostępne dla obsługiwane dystrybucje systemu Linux/wersji.</span><span class="sxs-lookup"><span data-stu-id="193d8-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="193d8-164">Natywny instalatorów wymagają dostępu administratora (sudo) na serwerze.</span><span class="sxs-lookup"><span data-stu-id="193d8-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="193d8-165">Zaletą używania Instalatora natywnych jest wszystkie zależności natywnego platformy .NET Core są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="193d8-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="193d8-166">Natywny instalatorów również zainstalować całego systemu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="193d8-167">W systemie Linux istnieją dwie opcje pakiet Instalatora:</span><span class="sxs-lookup"><span data-stu-id="193d8-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="193d8-168">Za pomocą Menedżera pakietu na podstawie źródła danych, takich jak stanie get dla Ubuntu lub yum dla CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="193d8-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="193d8-169">Używanie pakietów, DEB lub obr. / min.</span><span class="sxs-lookup"><span data-stu-id="193d8-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="193d8-170">Wykonywanie skryptów instalacji przy użyciu skryptu Instalatora .NET Core</span><span class="sxs-lookup"><span data-stu-id="193d8-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="193d8-171">`dotnet-install` Skrypty są używane do wykonywania instalacji bez uprawnień administratora, łańcuch narzędzi interfejsu wiersza polecenia i udostępnionych środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="193d8-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="193d8-172">Można pobrać skryptu z: https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="193d8-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="193d8-173">Skrypt Instalatora bash jest używany w scenariuszach automatyzacji i instalacji bez uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="193d8-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="193d8-174">Ten skrypt również odczytuje przełączników programu PowerShell, dzięki czemu mogą być używane w przypadku skryptu w systemach Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="193d8-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="193d8-175">Przed uruchomieniem skryptu, zainstalować wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="193d8-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="193d8-176">Zainstaluj oprogramowanie .NET Core Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="193d8-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="193d8-177">Aby zainstalować oprogramowanie .NET Core na RHEL 7:</span><span class="sxs-lookup"><span data-stu-id="193d8-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="193d8-178">Włącz kanału Red Hat .NET, dostępne w ramach Twojej subskrypcji RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="193d8-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="193d8-179">Red Hat Enterprise 7 Server użyć:</span><span class="sxs-lookup"><span data-stu-id="193d8-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="193d8-180">Red Hat Enterprise 7 stacji roboczej użyć:</span><span class="sxs-lookup"><span data-stu-id="193d8-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="193d8-181">Red Hat Enterprise 7 HPC obliczeniowe węzła należy użyć:</span><span class="sxs-lookup"><span data-stu-id="193d8-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="193d8-182">Zainstaluj narzędzie scl.</span><span class="sxs-lookup"><span data-stu-id="193d8-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="193d8-183">Zainstaluj oprogramowanie .NET Core</span><span class="sxs-lookup"><span data-stu-id="193d8-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="193d8-184">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="193d8-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="193d8-185">Zainstaluj oprogramowanie .NET Core 2.0 SDK i środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="193d8-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="193d8-186">Włącz .NET Core SDK/środowiska uruchomieniowego 2.0 w danym środowisku:</span><span class="sxs-lookup"><span data-stu-id="193d8-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="193d8-187">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="193d8-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="193d8-188">**Oprogramowanie .NET core 1.1**</span><span class="sxs-lookup"><span data-stu-id="193d8-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="193d8-189">Zainstaluj oprogramowanie .NET Core 1.1 SDK i środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="193d8-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="193d8-190">Włącz zestawu SDK programu .NET Core 1.1 i środowiska uruchomieniowego w danym środowisku:</span><span class="sxs-lookup"><span data-stu-id="193d8-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="193d8-191">**Oprogramowanie .NET core 1.0**</span><span class="sxs-lookup"><span data-stu-id="193d8-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="193d8-192">Zainstaluj program .NET Core 1.0 SDK i środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="193d8-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="193d8-193">Włącz .NET Core 1.0 SDK i środowiska uruchomieniowego w danym środowisku:</span><span class="sxs-lookup"><span data-stu-id="193d8-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="193d8-194">Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="193d8-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="193d8-195">Red Hat .NET kanał dostępu do rejestracji Pomoc [rozdział 1 .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) w Red Hat.</span><span class="sxs-lookup"><span data-stu-id="193d8-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="193d8-196">Zainstaluj oprogramowanie .NET Core dla Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 i Linux mennic 17, 18 mennic systemu Linux (64-bitowy)</span><span class="sxs-lookup"><span data-stu-id="193d8-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="193d8-197">Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="193d8-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="193d8-198">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="193d8-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="193d8-199">Zarejestruj klucz Product Microsoft jako zaufany.</span><span class="sxs-lookup"><span data-stu-id="193d8-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="193d8-200">Skonfiguruj pakietów hosta żądanej wersji źródła danych.</span><span class="sxs-lookup"><span data-stu-id="193d8-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="193d8-201">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="193d8-201">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="193d8-202">**Ubuntu 16.04 / Linux mennic 18**</span><span class="sxs-lookup"><span data-stu-id="193d8-202">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="193d8-203">**Ubuntu 14.04 / Linux mennic 17**</span><span class="sxs-lookup"><span data-stu-id="193d8-203">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="193d8-204">Zainstaluj oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="193d8-204">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="193d8-205">Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="193d8-205">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="193d8-206">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="193d8-206">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="193d8-207">Skonfiguruj pakietów hosta żądanej wersji źródła danych.</span><span class="sxs-lookup"><span data-stu-id="193d8-207">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="193d8-208">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="193d8-208">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="193d8-209">**Ubuntu 16.04 / Linux mennic 18**</span><span class="sxs-lookup"><span data-stu-id="193d8-209">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="193d8-210">**Ubuntu 14.04 / Linux mennic 17**</span><span class="sxs-lookup"><span data-stu-id="193d8-210">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="193d8-211">Zainstaluj program .NET Core 1.x Ubuntu lub mennic Linux:</span><span class="sxs-lookup"><span data-stu-id="193d8-211">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="193d8-212">Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="193d8-212">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="193d8-213">Zainstaluj oprogramowanie .NET Core Debian 8 lub Debian 9 (64-bitowy)</span><span class="sxs-lookup"><span data-stu-id="193d8-213">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="193d8-214">Aby zainstalować oprogramowanie .NET Core na Debian 8 lub Debian 9 (64 bity):</span><span class="sxs-lookup"><span data-stu-id="193d8-214">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="193d8-215">Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="193d8-215">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="193d8-216">Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.</span><span class="sxs-lookup"><span data-stu-id="193d8-216">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="193d8-217">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="193d8-217">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="193d8-218">Zainstaluj składniki systemu.</span><span class="sxs-lookup"><span data-stu-id="193d8-218">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="193d8-219">Zarejestruj zaufanego klucza Product firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="193d8-219">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="193d8-220">Zarejestruj Product Microsoft źródła danych.</span><span class="sxs-lookup"><span data-stu-id="193d8-220">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="193d8-221">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="193d8-221">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="193d8-222">**Debian 8 (Joasia)**</span><span class="sxs-lookup"><span data-stu-id="193d8-222">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="193d8-223">Zainstaluj oprogramowanie .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-223">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="193d8-224">Dodaj dotnet do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="193d8-224">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="193d8-225">Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="193d8-225">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="193d8-226">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="193d8-226">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="193d8-227">Pobierz wymagania wstępne.</span><span class="sxs-lookup"><span data-stu-id="193d8-227">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="193d8-228">Pobierz pliki binarne .NET Core SDK (tarball).</span><span class="sxs-lookup"><span data-stu-id="193d8-228">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="193d8-229">Wyodrębnij pliki binarne .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-229">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="193d8-230">Dodaj dotnet do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="193d8-230">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="193d8-231">Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="193d8-231">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="193d8-232">Zainstaluj oprogramowanie .NET Core dla Fedora 24, Fedora 25 lub Fedora 26 (64-bitowy)</span><span class="sxs-lookup"><span data-stu-id="193d8-232">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="193d8-233">Aby zainstalować oprogramowanie .NET Core 2.x Fedora 26 lub Fedora 25 lub .NET Core 1.x na Fedora 24:</span><span class="sxs-lookup"><span data-stu-id="193d8-233">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="193d8-234">Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="193d8-234">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="193d8-235">Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.</span><span class="sxs-lookup"><span data-stu-id="193d8-235">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="193d8-236">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="193d8-236">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="193d8-237">**Fedora 26 lub Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="193d8-237">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="193d8-238">Zarejestruj klucz podpisu firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="193d8-238">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="193d8-239">Dodaj produkt dotnet źródła danych.</span><span class="sxs-lookup"><span data-stu-id="193d8-239">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="193d8-240">Zainstaluj oprogramowanie .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-240">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="193d8-241">Dodaj dotnet do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="193d8-241">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="193d8-242">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="193d8-242">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="193d8-243">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="193d8-243">**Fedora 24**</span></span>

2. <span data-ttu-id="193d8-244">Pobierz wymagania wstępne.</span><span class="sxs-lookup"><span data-stu-id="193d8-244">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="193d8-245">Pobierz plik binarny .NET Core SDK (tarball).</span><span class="sxs-lookup"><span data-stu-id="193d8-245">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="193d8-246">Wyodrębnij pliki binarne .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-246">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="193d8-247">Dodaj dotnet do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="193d8-247">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="193d8-248">Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="193d8-248">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="193d8-249">Zainstaluj oprogramowanie .NET Core CentOS 7.1 (64-bitowym) i Oracle Linux 7.1 (64-bitowy)</span><span class="sxs-lookup"><span data-stu-id="193d8-249">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="193d8-250">Aby zainstalować oprogramowanie .NET Core CentOS 7.1 (64-bitowym) i Oracle Linux 7.1 (64 bity):</span><span class="sxs-lookup"><span data-stu-id="193d8-250">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="193d8-251">Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="193d8-251">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="193d8-252">Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.</span><span class="sxs-lookup"><span data-stu-id="193d8-252">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="193d8-253">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="193d8-253">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="193d8-254">Zarejestruj klucz podpisu firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="193d8-254">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="193d8-255">Dodaj Product firmy Microsoft, źródła danych.</span><span class="sxs-lookup"><span data-stu-id="193d8-255">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="193d8-256">Zainstaluj oprogramowanie .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-256">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="193d8-257">Dodaj do ścieżki dotnet</span><span class="sxs-lookup"><span data-stu-id="193d8-257">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="193d8-258">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="193d8-258">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="193d8-259">Pobierz wymagania wstępne.</span><span class="sxs-lookup"><span data-stu-id="193d8-259">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="193d8-260">Pobierz plik binarny .NET Core SDK (tarball).</span><span class="sxs-lookup"><span data-stu-id="193d8-260">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="193d8-261">Wyodrębnij pliki binarne .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-261">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="193d8-262">Dodaj dotnet do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="193d8-262">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="193d8-263">Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="193d8-263">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="193d8-264">Zainstaluj oprogramowanie .NET Core dla systemu SUSE Linux Enterprise Server (64-bitowy)</span><span class="sxs-lookup"><span data-stu-id="193d8-264">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="193d8-265">Aby zainstalować oprogramowanie .NET Core 2.x dla SUSE Linux Enterprise Server (SLES) 12 z dodatkiem SP2 (64 bity):</span><span class="sxs-lookup"><span data-stu-id="193d8-265">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="193d8-266">Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="193d8-266">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="193d8-267">Dodaj produkt dotnet źródła danych.</span><span class="sxs-lookup"><span data-stu-id="193d8-267">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="193d8-268">Zainstaluj oprogramowanie .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-268">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="193d8-269">Dodaj dotnet do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="193d8-269">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="193d8-270">Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="193d8-270">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="193d8-271">Zainstaluj oprogramowanie .NET Core dla openSUSE (64-bitowy)</span><span class="sxs-lookup"><span data-stu-id="193d8-271">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="193d8-272">Aby zainstalować oprogramowanie .NET Core 2.x openSUSE lub .NET Core 1.x dla openSUSE (64 bity):</span><span class="sxs-lookup"><span data-stu-id="193d8-272">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="193d8-273">Usuń wszystkie **poprzedniej wersji zapoznawczej** wersji platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="193d8-273">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="193d8-274">Katalog kontrolowane przez użytkownika jest wymagana dla systemu Linux instaluje system z tar.gz.</span><span class="sxs-lookup"><span data-stu-id="193d8-274">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="193d8-275">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="193d8-275">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="193d8-276">Zarejestruj klucz podpisu firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="193d8-276">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="193d8-277">Dodaj produkt dotnet źródła danych.</span><span class="sxs-lookup"><span data-stu-id="193d8-277">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="193d8-278">Zainstaluj oprogramowanie .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-278">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="193d8-279">Dodaj dotnet do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="193d8-279">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="193d8-280">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="193d8-280">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="193d8-281">Pobierz wymagania wstępne.</span><span class="sxs-lookup"><span data-stu-id="193d8-281">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="193d8-282">Pobierz plik binarny .NET Core SDK (tarball).</span><span class="sxs-lookup"><span data-stu-id="193d8-282">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="193d8-283">Wyodrębnij pliki binarne .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="193d8-283">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="193d8-284">Dodaj dotnet do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="193d8-284">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="193d8-285">Uruchom `dotnet --version` polecenie, aby udowodnić, Instalacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="193d8-285">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="193d8-286">Jeśli masz problemy z instalacją 2.x .NET Core w obsługiwanych dystrybucji systemu Linux/wersji, należy skontaktować się [2.0 znane problemy](https://github.com/dotnet/core/tree/master/release-notes/2.0) tematu dla programu zainstalowanych dystrybucje/wersji.</span><span class="sxs-lookup"><span data-stu-id="193d8-286">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="193d8-287">Jeśli masz problemy z instalacją 1.x .NET Core w obsługiwanych dystrybucji systemu Linux/wersji, należy skontaktować się [1.0.0 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) i [1.0.1 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) tematy z zainstalowanych dystrybucji / wersje.</span><span class="sxs-lookup"><span data-stu-id="193d8-287">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
