---
title: polecenie Serwer kompilacji DotNet
description: Polecenia dotnet serwer kompilacji wchodzi w interakcję z serwerami, uruchomione przez kompilację.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665315"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="c63b2-103">Serwer kompilacji DotNet</span><span class="sxs-lookup"><span data-stu-id="c63b2-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="c63b2-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c63b2-104">Name</span></span>

<span data-ttu-id="c63b2-105">`dotnet build-server` -Współdziała z serwerami, uruchomione przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="c63b2-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c63b2-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c63b2-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="c63b2-107">Polecenia</span><span class="sxs-lookup"><span data-stu-id="c63b2-107">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="c63b2-108">Zamyka serwerów kompilacji, które są uruchamiane z dotnet.</span><span class="sxs-lookup"><span data-stu-id="c63b2-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="c63b2-109">Domyślnie wszystkie serwery są zamykane.</span><span class="sxs-lookup"><span data-stu-id="c63b2-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="c63b2-110">Opcje</span><span class="sxs-lookup"><span data-stu-id="c63b2-110">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="c63b2-111">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="c63b2-111">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="c63b2-112">Serwer kompilacji zostanie zamknięte MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c63b2-112">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="c63b2-113">Serwer kompilacji zamknięciem elementu Razor.</span><span class="sxs-lookup"><span data-stu-id="c63b2-113">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="c63b2-114">Zamyka VB / serwer kompilacji kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="c63b2-114">Shuts down the VB/C# compiler build server.</span></span>