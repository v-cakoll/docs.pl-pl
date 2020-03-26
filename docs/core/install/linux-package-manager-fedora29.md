---
title: Zainstaluj .NET Core na Fedorze 29 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować .NET Core SDK i środowisko uruchomieniowe w Fedorze 29.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: bf75231ddf1cbf96668e949e20b24a0c0f6b4154
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134284"
---
# <a name="fedora-29-package-manager---install-net-core"></a><span data-ttu-id="530be-103">Menedżer pakietów Fedory 29 - Zainstaluj .NET Core</span><span class="sxs-lookup"><span data-stu-id="530be-103">Fedora 29 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="530be-104">W tym artykule opisano, jak zainstalować program .NET Core w fedorze 29 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="530be-104">This article describes how to use a package manager to install .NET Core on Fedora 29.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="530be-105">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="530be-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="530be-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="530be-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="530be-107">Zarejestruj klucz firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="530be-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="530be-108">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="530be-108">Register the product repository.</span></span>
- <span data-ttu-id="530be-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="530be-109">Install required dependencies.</span></span>

<span data-ttu-id="530be-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="530be-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="530be-111">Otwórz terminal i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="530be-111">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="530be-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="530be-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="530be-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="530be-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="530be-114">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="530be-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="530be-115">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="530be-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="530be-116">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="530be-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="530be-117">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="530be-117">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="530be-118">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="530be-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="530be-119">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="530be-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="530be-120">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="530be-120">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="530be-121">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="530be-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="530be-122">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="530be-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="530be-123">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="530be-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="530be-124">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="530be-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
