---
title: polecenie Serwer kompilacji DotNet
description: Polecenia dotnet serwer kompilacji wchodzi w interakcję z serwerami, uruchomione przez kompilację.
ms.date: 04/24/2019
ms.openlocfilehash: 491ac37e7f75f930423b3c7e43e3c090ec1ed07d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754276"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="8cbb6-103">Serwer kompilacji DotNet</span><span class="sxs-lookup"><span data-stu-id="8cbb6-103">dotnet build-server</span></span>

<span data-ttu-id="8cbb6-104">**Ten artykuł dotyczy: ✓** zestawu SDK programu .NET Core 2.1 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="8cbb6-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="8cbb6-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8cbb6-105">Name</span></span>

<span data-ttu-id="8cbb6-106">`dotnet build-server` -Współdziała z serwerami, uruchomione przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="8cbb6-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8cbb6-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="8cbb6-107">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="8cbb6-108">Polecenia</span><span class="sxs-lookup"><span data-stu-id="8cbb6-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="8cbb6-109">Zamyka serwerów kompilacji, które są uruchamiane z dotnet.</span><span class="sxs-lookup"><span data-stu-id="8cbb6-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="8cbb6-110">Domyślnie wszystkie serwery są zamykane.</span><span class="sxs-lookup"><span data-stu-id="8cbb6-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="8cbb6-111">Opcje</span><span class="sxs-lookup"><span data-stu-id="8cbb6-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="8cbb6-112">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="8cbb6-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="8cbb6-113">Serwer kompilacji zostanie zamknięte MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8cbb6-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="8cbb6-114">Serwer kompilacji zamknięciem elementu Razor.</span><span class="sxs-lookup"><span data-stu-id="8cbb6-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="8cbb6-115">Zamyka VB / serwer kompilacji kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="8cbb6-115">Shuts down the VB/C# compiler build server.</span></span>