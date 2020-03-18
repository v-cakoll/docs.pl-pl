---
title: polecenie dotnet build-server
description: Polecenie dotnet build-server współdziała z serwerami uruchomionymi przez kompilację.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503778"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="53275-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="53275-103">dotnet build-server</span></span>

<span data-ttu-id="53275-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="53275-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="53275-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="53275-105">Name</span></span>

<span data-ttu-id="53275-106">`dotnet build-server`- Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="53275-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="53275-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="53275-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="53275-108">Polecenia</span><span class="sxs-lookup"><span data-stu-id="53275-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="53275-109">Zamyka serwery kompilacji, które są uruchamiane z dotnet.</span><span class="sxs-lookup"><span data-stu-id="53275-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="53275-110">Domyślnie wszystkie serwery są zamykane.</span><span class="sxs-lookup"><span data-stu-id="53275-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="53275-111">Opcje</span><span class="sxs-lookup"><span data-stu-id="53275-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="53275-112">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="53275-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="53275-113">Zamyka serwer kompilacji MSBuild.</span><span class="sxs-lookup"><span data-stu-id="53275-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="53275-114">Zamyka serwer kompilacji Razor.</span><span class="sxs-lookup"><span data-stu-id="53275-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="53275-115">Zamyka serwer kompilacji kompilatora VB/C#.</span><span class="sxs-lookup"><span data-stu-id="53275-115">Shuts down the VB/C# compiler build server.</span></span>
