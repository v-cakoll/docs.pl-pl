---
title: Zainstaluj .NET Core na SLES 12 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować zestaw SDK .NET Core i program runtime na sles 12.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a6c10c6b11bc57ae4bbe814c66c563b85ce3c22b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920731"
---
# <a name="sles-12-package-manager---install-net-core"></a><span data-ttu-id="9089a-103">SLES 12 Menedżer pakietów — instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="9089a-103">SLES 12 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="9089a-104">W tym artykule opisano sposób instalowania programu .NET Core za pomocą menedżera pakietów w sles 12.</span><span class="sxs-lookup"><span data-stu-id="9089a-104">This article describes how to use a package manager to install .NET Core on SLES 12.</span></span> <span data-ttu-id="9089a-105">Jeśli instalujesz program runtime, zalecamy zainstalowanie [ASP.NET core runtime](#install-the-aspnet-core-runtime), ponieważ zawiera zarówno .NET Core, jak i ASP.NET core.</span><span class="sxs-lookup"><span data-stu-id="9089a-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="9089a-106">Rejestrowanie klucza firmy Microsoft i źródła danych</span><span class="sxs-lookup"><span data-stu-id="9089a-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="9089a-107">Przed zainstalowaniem programu .NET należy:</span><span class="sxs-lookup"><span data-stu-id="9089a-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="9089a-108">Zarejestruj klucz firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9089a-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="9089a-109">Zarejestruj repozytorium produktów.</span><span class="sxs-lookup"><span data-stu-id="9089a-109">Register the product repository.</span></span>
- <span data-ttu-id="9089a-110">Zainstaluj wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="9089a-110">Install required dependencies.</span></span>

<span data-ttu-id="9089a-111">Te operacje należy wykonać tylko jeden raz na każdej maszynie.</span><span class="sxs-lookup"><span data-stu-id="9089a-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="9089a-112">Otwórz terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="9089a-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="9089a-113">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="9089a-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="9089a-114">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9089a-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="9089a-115">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="9089a-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="9089a-116">Instalowanie ASP.NET core</span><span class="sxs-lookup"><span data-stu-id="9089a-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="9089a-117">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9089a-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="9089a-118">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="9089a-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="9089a-119">Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="9089a-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="9089a-120">Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9089a-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="9089a-121">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="9089a-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9089a-122">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="9089a-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="9089a-123">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="9089a-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="9089a-124">Ta sekcja zawiera informacje o typowych błędach, które mogą pojawić się podczas instalowania programu .NET Core za pomocą Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="9089a-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="9089a-125">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="9089a-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
