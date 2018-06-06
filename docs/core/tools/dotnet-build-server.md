---
title: polecenie serwera kompilacji DotNet - .NET Core interfejsu wiersza polecenia
description: Serwer kompilacji dotnet wchodzi w interakcję z serwerami uruchomione przez kompilację.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 929b8d74aa5f3f0ad73b108be8a5bf22f86e30d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696257"
---
# <a name="dotnet-build"></a><span data-ttu-id="39afa-103">dotnet-build</span><span class="sxs-lookup"><span data-stu-id="39afa-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="39afa-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="39afa-104">Name</span></span>

<span data-ttu-id="39afa-105">`dotnet build-server` -Współdziała z serwerami uruchomione przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="39afa-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="39afa-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="39afa-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="39afa-107">Polecenia</span><span class="sxs-lookup"><span data-stu-id="39afa-107">Commands</span></span>

`shutdown`

<span data-ttu-id="39afa-108">Zamyka serwery kompilacji, które są uruchamiane z dotnet.</span><span class="sxs-lookup"><span data-stu-id="39afa-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="39afa-109">Domyślnie wszystkie serwery są zamknięte.</span><span class="sxs-lookup"><span data-stu-id="39afa-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="39afa-110">Opcje</span><span class="sxs-lookup"><span data-stu-id="39afa-110">Options</span></span>

`-h|--help`

<span data-ttu-id="39afa-111">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="39afa-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="39afa-112">Serwer kompilacji zamknięciu programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="39afa-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="39afa-113">Serwer kompilacji zamknięciu elementu Razor.</span><span class="sxs-lookup"><span data-stu-id="39afa-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="39afa-114">Zamyka VB / serwer kompilacji kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="39afa-114">Shuts down the VB/C# compiler build server.</span></span>
