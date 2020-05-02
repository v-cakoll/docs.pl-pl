---
title: Instalowanie programu .NET Core w systemie Linux CentOS 8 Package Manager — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe w programie CentOS 8 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: b4cf5975e18aa8dfa8649c0d038caf38d648ad86
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728520"
---
# <a name="centos-8-package-manager---install-net-core"></a><span data-ttu-id="31d53-103">Menedżer pakietów CentOS 8 — Instalowanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="31d53-103">CentOS 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="31d53-104">W tym artykule opisano sposób użycia Menedżera pakietów do zainstalowania programu .NET Core w systemie CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="31d53-104">This article describes how to use a package manager to install .NET Core on CentOS 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="31d53-105">Zainstalowany zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="31d53-105">Install the .NET Core SDK</span></span>

<span data-ttu-id="31d53-106">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="31d53-106">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="31d53-107">Zainstaluj środowisko uruchomieniowe ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="31d53-107">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="31d53-108">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="31d53-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="31d53-109">Instalowanie środowiska uruchomieniowego platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="31d53-109">Install the .NET Core Runtime</span></span>

<span data-ttu-id="31d53-110">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="31d53-110">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="31d53-111">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="31d53-111">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
