---
title: Instalowanie programu .NET Core w systemie Ubuntu — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c590bd89b718a5cd31dae9f83049eac910cb4049
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863894"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="b0380-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie Ubuntu</span><span class="sxs-lookup"><span data-stu-id="b0380-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="b0380-104">Platforma .NET Core jest obsługiwana w systemie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b0380-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="b0380-105">W tym artykule opisano sposób instalowania programu .NET Core w systemie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b0380-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="b0380-106">Gdy wersja Ubuntu nie jest objęta wsparciem, platforma .NET Core nie jest już obsługiwana w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="b0380-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="b0380-107">Te instrukcje mogą jednak ułatwić uzyskanie programu .NET Core działającego w tych wersjach, chociaż nie jest to obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b0380-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="b0380-108">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="b0380-108">Supported distributions</span></span>

<span data-ttu-id="b0380-109">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core oraz wersji Ubuntu, na których są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b0380-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="b0380-110">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [Ubuntu osiągnie koniec cyklu życia](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="b0380-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="b0380-111">✔️ wskazuje, że wersja programu Ubuntu lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="b0380-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="b0380-112">❌Wskazuje, że wersja Ubuntu lub .NET Core nie jest obsługiwana w tej wersji Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b0380-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="b0380-113">Gdy wersja Ubuntu i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="b0380-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="b0380-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="b0380-114">Ubuntu</span></span>                   | <span data-ttu-id="b0380-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b0380-115">.NET Core 2.1</span></span> | <span data-ttu-id="b0380-116">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-116">.NET Core 3.1</span></span> | <span data-ttu-id="b0380-117">.NET 5 (wersja zapoznawcza) (tylko instalacja ręczna)</span><span class="sxs-lookup"><span data-stu-id="b0380-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="b0380-118">✔️ [20,04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="b0380-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="b0380-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b0380-119">✔️ 2.1</span></span>        | <span data-ttu-id="b0380-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-120">✔️ 3.1</span></span>        | <span data-ttu-id="b0380-121">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b0380-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="b0380-122">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="b0380-122">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="b0380-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b0380-123">✔️ 2.1</span></span>        | <span data-ttu-id="b0380-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-124">✔️ 3.1</span></span>        | <span data-ttu-id="b0380-125">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b0380-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="b0380-126">❌[19,04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="b0380-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="b0380-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b0380-127">✔️ 2.1</span></span>        | <span data-ttu-id="b0380-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-128">✔️ 3.1</span></span>        | <span data-ttu-id="b0380-129">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="b0380-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="b0380-130">❌[18,10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="b0380-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="b0380-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b0380-131">✔️ 2.1</span></span>        | <span data-ttu-id="b0380-132">❌3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-132">❌ 3.1</span></span>        | <span data-ttu-id="b0380-133">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="b0380-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="b0380-134">✔️ [18,04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="b0380-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="b0380-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b0380-135">✔️ 2.1</span></span>        | <span data-ttu-id="b0380-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-136">✔️ 3.1</span></span>        | <span data-ttu-id="b0380-137">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b0380-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="b0380-138">❌[17,10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="b0380-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="b0380-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b0380-139">✔️ 2.1</span></span>        | <span data-ttu-id="b0380-140">❌3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-140">❌ 3.1</span></span>        | <span data-ttu-id="b0380-141">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="b0380-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="b0380-142">❌[17,04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="b0380-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="b0380-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b0380-143">✔️ 2.1</span></span>        | <span data-ttu-id="b0380-144">❌3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-144">❌ 3.1</span></span>        | <span data-ttu-id="b0380-145">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="b0380-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="b0380-146">❌[16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="b0380-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="b0380-147">❌2,1</span><span class="sxs-lookup"><span data-stu-id="b0380-147">❌ 2.1</span></span>        | <span data-ttu-id="b0380-148">❌3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-148">❌ 3.1</span></span>        | <span data-ttu-id="b0380-149">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="b0380-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="b0380-150">✔️ [16,04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="b0380-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="b0380-151">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b0380-151">✔️ 2.1</span></span>        | <span data-ttu-id="b0380-152">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b0380-152">✔️ 3.1</span></span>        | <span data-ttu-id="b0380-153">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b0380-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="b0380-154">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b0380-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="b0380-155">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="b0380-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="b0380-156">3.0</span><span class="sxs-lookup"><span data-stu-id="b0380-156">3.0</span></span>
- <span data-ttu-id="b0380-157">2.2</span><span class="sxs-lookup"><span data-stu-id="b0380-157">2.2</span></span>
- <span data-ttu-id="b0380-158">2,0</span><span class="sxs-lookup"><span data-stu-id="b0380-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="b0380-159">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="b0380-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="b0380-160">20,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="b0380-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="b0380-161">19,10❌</span><span class="sxs-lookup"><span data-stu-id="b0380-161">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="b0380-162">19,04❌</span><span class="sxs-lookup"><span data-stu-id="b0380-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="b0380-163">18,10❌</span><span class="sxs-lookup"><span data-stu-id="b0380-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="b0380-164">18,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="b0380-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="b0380-165">17,10❌</span><span class="sxs-lookup"><span data-stu-id="b0380-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="b0380-166">17,04❌</span><span class="sxs-lookup"><span data-stu-id="b0380-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="b0380-167">16,10❌</span><span class="sxs-lookup"><span data-stu-id="b0380-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="b0380-168">16,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="b0380-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="b0380-169">APT Update — zestaw SDK lub środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b0380-169">APT update SDK or runtime</span></span>

<span data-ttu-id="b0380-170">Gdy dostępna jest nowa wersja poprawek dla programu .NET Core, można po prostu uaktualnić ją za pomocą APT za pomocą następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="b0380-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="b0380-171">Rozwiązywanie problemów z APT</span><span class="sxs-lookup"><span data-stu-id="b0380-171">APT troubleshooting</span></span>

<span data-ttu-id="b0380-172">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas instalowania programu .NET Core przy użyciu programu APT.</span><span class="sxs-lookup"><span data-stu-id="b0380-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="b0380-173">Nie można zlokalizować</span><span class="sxs-lookup"><span data-stu-id="b0380-173">Unable to locate</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="b0380-174">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="b0380-174">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="b0380-175">Przystawki</span><span class="sxs-lookup"><span data-stu-id="b0380-175">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="b0380-176">Zależności</span><span class="sxs-lookup"><span data-stu-id="b0380-176">Dependencies</span></span>

<span data-ttu-id="b0380-177">Po zainstalowaniu programu przy użyciu Menedżera pakietów te biblioteki są instalowane dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="b0380-177">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="b0380-178">Jeśli jednak ręcznie zainstalujesz platformę .NET Core lub opublikujesz aplikację, musisz upewnić się, że te biblioteki są zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="b0380-178">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="b0380-179">libc6</span><span class="sxs-lookup"><span data-stu-id="b0380-179">libc6</span></span>
- <span data-ttu-id="b0380-180">libgcc1</span><span class="sxs-lookup"><span data-stu-id="b0380-180">libgcc1</span></span>
- <span data-ttu-id="b0380-181">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="b0380-181">libgssapi-krb5-2</span></span>
- <span data-ttu-id="b0380-182">libicu52 (dla 14. x)</span><span class="sxs-lookup"><span data-stu-id="b0380-182">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="b0380-183">libicu55 (dla 16. x)</span><span class="sxs-lookup"><span data-stu-id="b0380-183">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="b0380-184">libicu60 (dla 18. x)</span><span class="sxs-lookup"><span data-stu-id="b0380-184">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="b0380-185">libicu66 (dla 20. x)</span><span class="sxs-lookup"><span data-stu-id="b0380-185">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="b0380-186">libssl 1.0.0 (dla 14. x, 16. x)</span><span class="sxs-lookup"><span data-stu-id="b0380-186">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="b0380-187">libssl 1.1 (dla 18. x, 20. x)</span><span class="sxs-lookup"><span data-stu-id="b0380-187">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="b0380-188">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="b0380-188">libstdc++6</span></span>
- <span data-ttu-id="b0380-189">zlib1g</span><span class="sxs-lookup"><span data-stu-id="b0380-189">zlib1g</span></span>

<span data-ttu-id="b0380-190">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:</span><span class="sxs-lookup"><span data-stu-id="b0380-190">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="b0380-191">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="b0380-191">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="b0380-192">Aby zainstalować najnowszą wersję programu *libgdiplus* , można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="b0380-192">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="b0380-193">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="b0380-193">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="b0380-194">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="b0380-194">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="b0380-195">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="b0380-195">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="b0380-196">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b0380-196">Next steps</span></span>

- [<span data-ttu-id="b0380-197">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b0380-197">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
