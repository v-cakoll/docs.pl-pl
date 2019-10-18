---
title: Kompilacja dotnet — polecenie serwera
description: Polecenie programu dotnet Build-Server współdziała z serwerami uruchomionymi przez kompilację.
ms.date: 04/24/2019
ms.openlocfilehash: 1c6c6dcdb53d779426daf5daa470d2ad0470a7a1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523016"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="1ea67-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="1ea67-103">dotnet build-server</span></span>

<span data-ttu-id="1ea67-104">**Ten artykuł dotyczy: ✓** .net Core 2,1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="1ea67-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="1ea67-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1ea67-105">Name</span></span>

<span data-ttu-id="1ea67-106">`dotnet build-server` — współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="1ea67-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1ea67-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="1ea67-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="1ea67-108">Polecenia</span><span class="sxs-lookup"><span data-stu-id="1ea67-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="1ea67-109">Zamyka serwery kompilacji uruchomione z programu dotnet.</span><span class="sxs-lookup"><span data-stu-id="1ea67-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="1ea67-110">Domyślnie wszystkie serwery są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="1ea67-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="1ea67-111">Opcje</span><span class="sxs-lookup"><span data-stu-id="1ea67-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="1ea67-112">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="1ea67-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="1ea67-113">Zamyka serwer kompilacji MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1ea67-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="1ea67-114">Zamyka serwer kompilacji Razor.</span><span class="sxs-lookup"><span data-stu-id="1ea67-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="1ea67-115">Zamyka serwer kompilacji VB/C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1ea67-115">Shuts down the VB/C# compiler build server.</span></span>
