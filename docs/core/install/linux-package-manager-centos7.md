---
title: Zainstaluj .NET Core na CentOS 7 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować pakiet .NET Core SDK i środowisko wykonawcze w programie CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d6cec51422dc59b7f667e36001b7db4742b53a6f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134351"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="c5d2c-103">Menedżer pakietów CentOS 7 — instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5d2c-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="c5d2c-104">W tym artykule opisano sposób instalowania programu .NET Core w programie CentOS 7 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="c5d2c-105">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="c5d2c-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="c5d2c-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="c5d2c-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="c5d2c-107">Zarejestruj klucz firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="c5d2c-108">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-108">Register the product repository.</span></span>
- <span data-ttu-id="c5d2c-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-109">Install required dependencies.</span></span>

<span data-ttu-id="c5d2c-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="c5d2c-111">Otwórz terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="c5d2c-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c5d2c-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="c5d2c-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="c5d2c-114">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-114">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="c5d2c-115">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c5d2c-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="c5d2c-116">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="c5d2c-117">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-117">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="c5d2c-118">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5d2c-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="c5d2c-119">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="c5d2c-120">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-120">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c5d2c-121">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="c5d2c-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c5d2c-122">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="c5d2c-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="c5d2c-123">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="c5d2c-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="c5d2c-124">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="c5d2c-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
