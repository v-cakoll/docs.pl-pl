---
title: polecenie Serwer kompilacji DotNet - interfejsu wiersza polecenia platformy .NET Core
description: Polecenia dotnet serwer kompilacji wchodzi w interakcję z serwerami, uruchomione przez kompilację.
author: mairaw
ms.author: mairaw
ms.date: 07/02/2018
ms.openlocfilehash: 1c59c85f246b79c7e2552f704db5b4f076f9b502
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404336"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="a9c97-103">Serwer kompilacji DotNet</span><span class="sxs-lookup"><span data-stu-id="a9c97-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="a9c97-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a9c97-104">Name</span></span>

<span data-ttu-id="a9c97-105">`dotnet build-server` -Współdziała z serwerami, uruchomione przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="a9c97-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a9c97-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a9c97-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="a9c97-107">Polecenia</span><span class="sxs-lookup"><span data-stu-id="a9c97-107">Commands</span></span>

`shutdown`

<span data-ttu-id="a9c97-108">Zamyka serwerów kompilacji, które są uruchamiane z dotnet.</span><span class="sxs-lookup"><span data-stu-id="a9c97-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="a9c97-109">Domyślnie wszystkie serwery są zamykane.</span><span class="sxs-lookup"><span data-stu-id="a9c97-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="a9c97-110">Opcje</span><span class="sxs-lookup"><span data-stu-id="a9c97-110">Options</span></span>

`-h|--help`

<span data-ttu-id="a9c97-111">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="a9c97-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="a9c97-112">Serwer kompilacji zostanie zamknięte MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a9c97-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="a9c97-113">Serwer kompilacji zamknięciem elementu Razor.</span><span class="sxs-lookup"><span data-stu-id="a9c97-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="a9c97-114">Zamyka VB / serwer kompilacji kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="a9c97-114">Shuts down the VB/C# compiler build server.</span></span>
