---
title: polecenie Serwer kompilacji DotNet
description: Polecenia dotnet serwer kompilacji wchodzi w interakcję z serwerami, uruchomione przez kompilację.
ms.date: 04/24/2019
ms.openlocfilehash: fa663bc045e8abfc3375a0226be7d16331b49740
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632094"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="8983e-103">Serwer kompilacji DotNet</span><span class="sxs-lookup"><span data-stu-id="8983e-103">dotnet build-server</span></span>

<span data-ttu-id="8983e-104">**Ten artykuł dotyczy: ✓** zestawu SDK programu .NET Core 2.1 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="8983e-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="8983e-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8983e-105">Name</span></span>

<span data-ttu-id="8983e-106">`dotnet build-server` -Współdziała z serwerami, uruchomione przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="8983e-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8983e-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="8983e-107">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="8983e-108">Polecenia</span><span class="sxs-lookup"><span data-stu-id="8983e-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="8983e-109">Zamyka serwerów kompilacji, które są uruchamiane z dotnet.</span><span class="sxs-lookup"><span data-stu-id="8983e-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="8983e-110">Domyślnie wszystkie serwery są zamykane.</span><span class="sxs-lookup"><span data-stu-id="8983e-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="8983e-111">Opcje</span><span class="sxs-lookup"><span data-stu-id="8983e-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="8983e-112">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="8983e-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="8983e-113">Serwer kompilacji zostanie zamknięte MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8983e-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="8983e-114">Serwer kompilacji zamknięciem elementu Razor.</span><span class="sxs-lookup"><span data-stu-id="8983e-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="8983e-115">Zamyka VB / serwer kompilacji kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="8983e-115">Shuts down the VB/C# compiler build server.</span></span>
