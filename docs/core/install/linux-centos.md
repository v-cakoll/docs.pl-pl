---
title: Instalowanie programu .NET Core w systemie CentOS — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie CentOS.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9f4de70b4989be1d162f384518a015816a3e75a9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324898"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-centos"></a><span data-ttu-id="ddd81-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie CentOS</span><span class="sxs-lookup"><span data-stu-id="ddd81-103">Install .NET Core SDK or .NET Core Runtime on CentOS</span></span>

<span data-ttu-id="ddd81-104">Platforma .NET Core jest obsługiwana w systemie CentOS.</span><span class="sxs-lookup"><span data-stu-id="ddd81-104">.NET Core is supported on CentOS.</span></span> <span data-ttu-id="ddd81-105">W tym artykule opisano sposób instalowania programu .NET Core w systemie CentOS.</span><span class="sxs-lookup"><span data-stu-id="ddd81-105">This article describes how to install .NET Core on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="ddd81-106">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="ddd81-106">Supported distributions</span></span>

<span data-ttu-id="ddd81-107">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemach CentOS 7 i CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="ddd81-107">The following table is a list of currently supported .NET Core releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="ddd81-108">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu CentOS nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="ddd81-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="ddd81-109">✔️ wskazuje, że wersja programu CentOS lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="ddd81-109">A ✔️ indicates that the version of CentOS or .NET Core is still supported.</span></span>
- <span data-ttu-id="ddd81-110">❌Wskazuje, że wersja CentOS lub .NET Core nie jest obsługiwana w tej wersji CentOS.</span><span class="sxs-lookup"><span data-stu-id="ddd81-110">A ❌ indicates that the version of CentOS or .NET Core isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="ddd81-111">Gdy wersja CentOS i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="ddd81-111">When both a version of CentOS and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="ddd81-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="ddd81-112">CentOS</span></span>                   | <span data-ttu-id="ddd81-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ddd81-113">.NET Core 2.1</span></span> | <span data-ttu-id="ddd81-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ddd81-114">.NET Core 3.1</span></span> | <span data-ttu-id="ddd81-115">.NET 5 (wersja zapoznawcza) (tylko instalacja ręczna)</span><span class="sxs-lookup"><span data-stu-id="ddd81-115">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="ddd81-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="ddd81-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="ddd81-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="ddd81-117">✔️ 2.1</span></span>        | <span data-ttu-id="ddd81-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="ddd81-118">✔️ 3.1</span></span>        | <span data-ttu-id="ddd81-119">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="ddd81-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="ddd81-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="ddd81-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="ddd81-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="ddd81-121">✔️ 2.1</span></span>        | <span data-ttu-id="ddd81-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="ddd81-122">✔️ 3.1</span></span>        | <span data-ttu-id="ddd81-123">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="ddd81-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="ddd81-124">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ddd81-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="ddd81-125">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="ddd81-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="ddd81-126">3.0</span><span class="sxs-lookup"><span data-stu-id="ddd81-126">3.0</span></span>
- <span data-ttu-id="ddd81-127">2.2</span><span class="sxs-lookup"><span data-stu-id="ddd81-127">2.2</span></span>
- <span data-ttu-id="ddd81-128">2.0</span><span class="sxs-lookup"><span data-stu-id="ddd81-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ddd81-129">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="ddd81-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="ddd81-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="ddd81-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="ddd81-131">Program .NET Core 3,1 jest dostępny w repozytoriach pakietów domyślnych dla CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="ddd81-131">.NET Core 3.1 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="ddd81-132">CentOS ✔️ 7</span><span class="sxs-lookup"><span data-stu-id="ddd81-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-31](includes/linux-install-31-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="ddd81-133">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="ddd81-133">Troubleshoot the package manager</span></span>

<span data-ttu-id="ddd81-134">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddd81-134">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="ddd81-135">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="ddd81-135">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="ddd81-136">Przystawki</span><span class="sxs-lookup"><span data-stu-id="ddd81-136">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="ddd81-137">Zależności</span><span class="sxs-lookup"><span data-stu-id="ddd81-137">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="ddd81-138">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="ddd81-138">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="ddd81-139">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="ddd81-139">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="ddd81-140">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ddd81-140">Next steps</span></span>

- [<span data-ttu-id="ddd81-141">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ddd81-141">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
