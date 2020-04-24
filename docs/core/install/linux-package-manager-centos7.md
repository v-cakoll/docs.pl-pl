---
title: Zainstaluj .NET Core na CentOS 7 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować pakiet .NET Core SDK i środowisko wykonawcze w programie CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: f8c4115b9d85edc36809f0daed5f6825149c8411
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645405"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="398a7-103">Menedżer pakietów CentOS 7 — instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="398a7-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="398a7-104">W tym artykule opisano sposób instalowania programu .NET Core w programie CentOS 7 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="398a7-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="398a7-105">Dodawanie klucza repozytorium firmy Microsoft i kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="398a7-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="398a7-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="398a7-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="398a7-107">Dodaj klucz podpisywania pakietu firmy Microsoft do listy zaufanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="398a7-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="398a7-108">Dodaj repozytorium do menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="398a7-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="398a7-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="398a7-109">Install required dependencies.</span></span>

<span data-ttu-id="398a7-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="398a7-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="398a7-111">Otwórz terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="398a7-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="398a7-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="398a7-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="398a7-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="398a7-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="398a7-114">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="398a7-114">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="398a7-115">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="398a7-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="398a7-116">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="398a7-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="398a7-117">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="398a7-117">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="398a7-118">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="398a7-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="398a7-119">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="398a7-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="398a7-120">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="398a7-120">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="398a7-121">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="398a7-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="398a7-122">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="398a7-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="398a7-123">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="398a7-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="398a7-124">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="398a7-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
