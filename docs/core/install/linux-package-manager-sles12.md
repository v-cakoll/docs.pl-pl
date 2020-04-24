---
title: Zainstaluj .NET Core na SLES 12 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować pakiet .NET Core SDK i środowisko wykonawcze w sles 12.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 314688d60fb77e1b569dd037fb1d78c3f1f94dbc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645658"
---
# <a name="sles-12-package-manager---install-net-core"></a><span data-ttu-id="c739a-103">Menedżer pakietów SLES 12 — instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="c739a-103">SLES 12 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="c739a-104">W tym artykule opisano sposób instalowania programu .NET Core w sles 12 za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="c739a-104">This article describes how to use a package manager to install .NET Core on SLES 12.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="c739a-105">Dodawanie klucza repozytorium firmy Microsoft i kanału informacyjnego</span><span class="sxs-lookup"><span data-stu-id="c739a-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="c739a-106">Przed zainstalowaniem platformy .NET należy:</span><span class="sxs-lookup"><span data-stu-id="c739a-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="c739a-107">Dodaj klucz podpisywania pakietu firmy Microsoft do listy zaufanych kluczy.</span><span class="sxs-lookup"><span data-stu-id="c739a-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="c739a-108">Dodaj repozytorium do menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="c739a-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="c739a-109">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="c739a-109">Install required dependencies.</span></span>

<span data-ttu-id="c739a-110">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="c739a-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="c739a-111">Otwórz terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="c739a-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="c739a-112">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c739a-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="c739a-113">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c739a-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="c739a-114">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="c739a-114">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="c739a-115">Instalowanie ASP.NET core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c739a-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="c739a-116">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="c739a-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="c739a-117">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="c739a-117">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="c739a-118">Instalowanie środowiska wykonawczego .NET Core</span><span class="sxs-lookup"><span data-stu-id="c739a-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="c739a-119">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj środowisko uruchomieniowe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c739a-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="c739a-120">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="c739a-120">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c739a-121">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="c739a-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c739a-122">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="c739a-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="c739a-123">Ta sekcja zawiera informacje na temat typowych błędów, które można uzyskać podczas instalowania programu .NET Core za pomocą menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="c739a-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="c739a-124">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="c739a-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
