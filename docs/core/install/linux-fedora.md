---
title: Instalowanie programu .NET Core w systemie Fedora — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie Fedora.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c90c08eefa074fa139642a268f879af79d7280da
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619484"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-fedora"></a><span data-ttu-id="fe574-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie Fedora</span><span class="sxs-lookup"><span data-stu-id="fe574-103">Install .NET Core SDK or .NET Core Runtime on Fedora</span></span>

<span data-ttu-id="fe574-104">Platforma .NET Core jest obsługiwana w systemie Fedora.</span><span class="sxs-lookup"><span data-stu-id="fe574-104">.NET Core is supported on Fedora.</span></span> <span data-ttu-id="fe574-105">W tym artykule opisano sposób instalowania programu .NET Core w systemie Fedora.</span><span class="sxs-lookup"><span data-stu-id="fe574-105">This article describes how to install .NET Core on Fedora.</span></span> <span data-ttu-id="fe574-106">Gdy wersja Fedora nie jest objęta wsparciem, platforma .NET Core nie jest już obsługiwana w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="fe574-106">When a Fedora version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="fe574-107">Te instrukcje mogą jednak ułatwić uzyskanie programu .NET Core działającego w tych wersjach, chociaż nie jest to obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="fe574-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="fe574-108">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="fe574-108">Supported distributions</span></span>

<span data-ttu-id="fe574-109">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core oraz wersji Fedora, na których są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="fe574-109">The following table is a list of currently supported .NET Core releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="fe574-110">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [Fedora osiągnie koniec cyklu życia](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="fe574-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="fe574-111">✔️ wskazuje, że wersja programu Fedora lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="fe574-111">A ✔️ indicates that the version of Fedora or .NET Core is still supported.</span></span>
- <span data-ttu-id="fe574-112">❌Wskazuje, że wersja Fedora lub .NET Core nie jest obsługiwana w tej wersji Fedora.</span><span class="sxs-lookup"><span data-stu-id="fe574-112">A ❌ indicates that the version of Fedora or .NET Core isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="fe574-113">Gdy wersja Fedora i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="fe574-113">When both a version of Fedora and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="fe574-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="fe574-114">Fedora</span></span>                   | <span data-ttu-id="fe574-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fe574-115">.NET Core 2.1</span></span> | <span data-ttu-id="fe574-116">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="fe574-116">.NET Core 3.1</span></span> | <span data-ttu-id="fe574-117">.NET 5 (wersja zapoznawcza) (tylko instalacja ręczna)</span><span class="sxs-lookup"><span data-stu-id="fe574-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="fe574-118">✔️ [32](linux-fedora.md#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="fe574-118">✔️ [32](linux-fedora.md#fedora-32-)</span></span> | <span data-ttu-id="fe574-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fe574-119">✔️ 2.1</span></span>        | <span data-ttu-id="fe574-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fe574-120">✔️ 3.1</span></span>        | <span data-ttu-id="fe574-121">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="fe574-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="fe574-122">✔️ [31](linux-fedora.md#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="fe574-122">✔️ [31](linux-fedora.md#fedora-31-)</span></span> | <span data-ttu-id="fe574-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fe574-123">✔️ 2.1</span></span>        | <span data-ttu-id="fe574-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fe574-124">✔️ 3.1</span></span>        | <span data-ttu-id="fe574-125">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="fe574-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="fe574-126">❌ [30](linux-fedora.md#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="fe574-126">❌ [30](linux-fedora.md#fedora-30-)</span></span> | <span data-ttu-id="fe574-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fe574-127">✔️ 2.1</span></span>        | <span data-ttu-id="fe574-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fe574-128">✔️ 3.1</span></span>        | <span data-ttu-id="fe574-129">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="fe574-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="fe574-130">❌[29](linux-fedora.md#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="fe574-130">❌ [29](linux-fedora.md#fedora-29-)</span></span> | <span data-ttu-id="fe574-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fe574-131">✔️ 2.1</span></span>        | <span data-ttu-id="fe574-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fe574-132">✔️ 3.1</span></span>        | <span data-ttu-id="fe574-133">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="fe574-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="fe574-134">❌[28](linux-fedora.md#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="fe574-134">❌ [28](linux-fedora.md#fedora-28-)</span></span> | <span data-ttu-id="fe574-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fe574-135">✔️ 2.1</span></span>        | <span data-ttu-id="fe574-136">❌3,1</span><span class="sxs-lookup"><span data-stu-id="fe574-136">❌ 3.1</span></span>        | <span data-ttu-id="fe574-137">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="fe574-137">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="fe574-138">❌[27](linux-fedora.md#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="fe574-138">❌ [27](linux-fedora.md#fedora-27-)</span></span> | <span data-ttu-id="fe574-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fe574-139">✔️ 2.1</span></span>        | <span data-ttu-id="fe574-140">❌3,1</span><span class="sxs-lookup"><span data-stu-id="fe574-140">❌ 3.1</span></span>        | <span data-ttu-id="fe574-141">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="fe574-141">❌ 5.0 Preview</span></span> |

<span data-ttu-id="fe574-142">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="fe574-142">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="fe574-143">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="fe574-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="fe574-144">3.0</span><span class="sxs-lookup"><span data-stu-id="fe574-144">3.0</span></span>
- <span data-ttu-id="fe574-145">2.2</span><span class="sxs-lookup"><span data-stu-id="fe574-145">2.2</span></span>
- <span data-ttu-id="fe574-146">2.0</span><span class="sxs-lookup"><span data-stu-id="fe574-146">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="fe574-147">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="fe574-147">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-32-"></a><span data-ttu-id="fe574-148">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="fe574-148">Fedora 32 ✔️</span></span>

<span data-ttu-id="fe574-149">Program .NET Core 3,1 jest dostępny w repozytoriach pakietów domyślnych dla Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="fe574-149">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="fe574-150">Fedora 31 ✔️</span><span class="sxs-lookup"><span data-stu-id="fe574-150">Fedora 31 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="fe574-151">Fedora 30❌</span><span class="sxs-lookup"><span data-stu-id="fe574-151">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="fe574-152">Fedora 29❌</span><span class="sxs-lookup"><span data-stu-id="fe574-152">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="fe574-153">Fedora 28❌</span><span class="sxs-lookup"><span data-stu-id="fe574-153">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="fe574-154">Fedora 27❌</span><span class="sxs-lookup"><span data-stu-id="fe574-154">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="fe574-155">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="fe574-155">Troubleshoot the package manager</span></span>

<span data-ttu-id="fe574-156">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fe574-156">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="fe574-157">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="fe574-157">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="fe574-158">Przystawki</span><span class="sxs-lookup"><span data-stu-id="fe574-158">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="fe574-159">Zależności</span><span class="sxs-lookup"><span data-stu-id="fe574-159">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="fe574-160">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="fe574-160">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="fe574-161">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="fe574-161">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="fe574-162">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fe574-162">Next steps</span></span>

- [<span data-ttu-id="fe574-163">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fe574-163">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
