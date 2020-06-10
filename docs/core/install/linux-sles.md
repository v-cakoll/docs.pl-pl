---
title: Instalowanie programu .NET Core w systemie SLES — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie SLES.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: b2eab6a0305d492e37e1b33d02be43ca41d42b6f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603035"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="415e1-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie SLES</span><span class="sxs-lookup"><span data-stu-id="415e1-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="415e1-104">Platforma .NET Core jest obsługiwana w systemie SLES.</span><span class="sxs-lookup"><span data-stu-id="415e1-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="415e1-105">W tym artykule opisano sposób instalowania programu .NET Core w systemie SLES.</span><span class="sxs-lookup"><span data-stu-id="415e1-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="415e1-106">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="415e1-106">Supported distributions</span></span>

<span data-ttu-id="415e1-107">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemach SLES 12 SP2 i SLES 15.</span><span class="sxs-lookup"><span data-stu-id="415e1-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="415e1-108">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu SLES nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="415e1-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="415e1-109">✔️ wskazuje, że wersja programu SLES lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="415e1-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="415e1-110">❌Wskazuje, że wersja SLES lub .NET Core nie jest obsługiwana w tej wersji SLES.</span><span class="sxs-lookup"><span data-stu-id="415e1-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="415e1-111">Gdy wersja SLES i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="415e1-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="415e1-112">SLES</span><span class="sxs-lookup"><span data-stu-id="415e1-112">SLES</span></span>                   | <span data-ttu-id="415e1-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="415e1-113">.NET Core 2.1</span></span> | <span data-ttu-id="415e1-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="415e1-114">.NET Core 3.1</span></span> | <span data-ttu-id="415e1-115">.NET 5 (wersja zapoznawcza) (tylko instalacja ręczna)</span><span class="sxs-lookup"><span data-stu-id="415e1-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="415e1-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="415e1-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="415e1-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="415e1-117">✔️ 2.1</span></span>        | <span data-ttu-id="415e1-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="415e1-118">✔️ 3.1</span></span>        | <span data-ttu-id="415e1-119">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="415e1-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="415e1-120">✔️ [12 z dodatkiem SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="415e1-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="415e1-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="415e1-121">✔️ 2.1</span></span>        | <span data-ttu-id="415e1-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="415e1-122">✔️ 3.1</span></span>        | <span data-ttu-id="415e1-123">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="415e1-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="415e1-124">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="415e1-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="415e1-125">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="415e1-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="415e1-126">3.0</span><span class="sxs-lookup"><span data-stu-id="415e1-126">3.0</span></span>
- <span data-ttu-id="415e1-127">2.2</span><span class="sxs-lookup"><span data-stu-id="415e1-127">2.2</span></span>
- <span data-ttu-id="415e1-128">2.0</span><span class="sxs-lookup"><span data-stu-id="415e1-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="415e1-129">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="415e1-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="415e1-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="415e1-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="415e1-131">Obecnie pakiet instalacyjny usługi Microsoft Repository SLES 15 zainstaluje plik *Microsoft-prod.* Repository w niewłaściwym katalogu, uniemożliwiając użyciu narzędzia zypper znalezienie pakietów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="415e1-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="415e1-132">Aby rozwiązać ten problem, Utwórz link symboliczny w poprawnym katalogu.</span><span class="sxs-lookup"><span data-stu-id="415e1-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="415e1-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="415e1-133">SLES 12 ✔️</span></span>

<span data-ttu-id="415e1-134">Program .NET Core wymaga programu SP2 jako minimum dla rodziny SLES 12.</span><span class="sxs-lookup"><span data-stu-id="415e1-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="415e1-135">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="415e1-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="415e1-136">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="415e1-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="415e1-137">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="415e1-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="415e1-138">Przystawki</span><span class="sxs-lookup"><span data-stu-id="415e1-138">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="415e1-139">Zależności</span><span class="sxs-lookup"><span data-stu-id="415e1-139">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="415e1-140">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="415e1-140">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="415e1-141">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="415e1-141">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="415e1-142">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="415e1-142">Next steps</span></span>

- [<span data-ttu-id="415e1-143">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="415e1-143">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
