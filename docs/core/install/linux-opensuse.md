---
title: Instalowanie programu .NET Core w systemie openSUSE — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 3a2ff1ca1519428f42c88048dde22aa11baaaa01
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324758"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="35fdd-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie openSUSE</span><span class="sxs-lookup"><span data-stu-id="35fdd-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="35fdd-104">Platforma .NET Core jest obsługiwana w systemie openSUSE.</span><span class="sxs-lookup"><span data-stu-id="35fdd-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="35fdd-105">W tym artykule opisano sposób instalowania programu .NET Core w systemie openSUSE.</span><span class="sxs-lookup"><span data-stu-id="35fdd-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="35fdd-106">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="35fdd-106">Supported distributions</span></span>

<span data-ttu-id="35fdd-107">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemie openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="35fdd-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="35fdd-108">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu openSUSE nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="35fdd-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="35fdd-109">✔️ wskazuje, że wersja programu openSUSE lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="35fdd-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="35fdd-110">❌Wskazuje, że wersja openSUSE lub .NET Core nie jest obsługiwana w tej wersji openSUSE.</span><span class="sxs-lookup"><span data-stu-id="35fdd-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="35fdd-111">Gdy wersja openSUSE i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="35fdd-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="35fdd-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="35fdd-112">openSUSE</span></span>                   | <span data-ttu-id="35fdd-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="35fdd-113">.NET Core 2.1</span></span> | <span data-ttu-id="35fdd-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="35fdd-114">.NET Core 3.1</span></span> | <span data-ttu-id="35fdd-115">.NET 5 (wersja zapoznawcza) (tylko instalacja ręczna)</span><span class="sxs-lookup"><span data-stu-id="35fdd-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="35fdd-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="35fdd-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="35fdd-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="35fdd-117">✔️ 2.1</span></span>        | <span data-ttu-id="35fdd-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="35fdd-118">✔️ 3.1</span></span>        | <span data-ttu-id="35fdd-119">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="35fdd-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="35fdd-120">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="35fdd-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="35fdd-121">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="35fdd-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="35fdd-122">3.0</span><span class="sxs-lookup"><span data-stu-id="35fdd-122">3.0</span></span>
- <span data-ttu-id="35fdd-123">2.2</span><span class="sxs-lookup"><span data-stu-id="35fdd-123">2.2</span></span>
- <span data-ttu-id="35fdd-124">2.0</span><span class="sxs-lookup"><span data-stu-id="35fdd-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="35fdd-125">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="35fdd-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="35fdd-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="35fdd-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="35fdd-127">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="35fdd-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="35fdd-128">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="35fdd-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="35fdd-129">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="35fdd-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="35fdd-130">Przystawki</span><span class="sxs-lookup"><span data-stu-id="35fdd-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="35fdd-131">Zależności</span><span class="sxs-lookup"><span data-stu-id="35fdd-131">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="35fdd-132">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="35fdd-132">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="35fdd-133">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="35fdd-133">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="35fdd-134">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="35fdd-134">Next steps</span></span>

- [<span data-ttu-id="35fdd-135">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="35fdd-135">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
