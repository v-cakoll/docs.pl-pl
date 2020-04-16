---
title: polecenie dotnet build-server
description: Polecenie dotnet build-server współdziała z serwerami uruchomionymi przez kompilację.
ms.date: 02/14/2020
ms.openlocfilehash: 882b697c07aac0e20266f3ad4e6c11888a0b7acc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463727"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="e385a-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="e385a-103">dotnet build-server</span></span>

<span data-ttu-id="e385a-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="e385a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e385a-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e385a-105">Name</span></span>

<span data-ttu-id="e385a-106">`dotnet build-server`- Współdziała z serwerami uruchomionymi przez kompilację.</span><span class="sxs-lookup"><span data-stu-id="e385a-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e385a-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e385a-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]

dotnet build-server shutdown -h|--help

dotnet build-server -h|--help
```

## <a name="commands"></a><span data-ttu-id="e385a-108">Polecenia</span><span class="sxs-lookup"><span data-stu-id="e385a-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="e385a-109">Zamyka serwery kompilacji, które są uruchamiane z dotnet.</span><span class="sxs-lookup"><span data-stu-id="e385a-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="e385a-110">Domyślnie wszystkie serwery są zamykane.</span><span class="sxs-lookup"><span data-stu-id="e385a-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="e385a-111">Opcje</span><span class="sxs-lookup"><span data-stu-id="e385a-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e385a-112">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e385a-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="e385a-113">Zamyka serwer kompilacji MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e385a-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="e385a-114">Wyłącza serwer kompilacji Razor.</span><span class="sxs-lookup"><span data-stu-id="e385a-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="e385a-115">Zamyka serwer kompilacji kompilatora VB/C#.</span><span class="sxs-lookup"><span data-stu-id="e385a-115">Shuts down the VB/C# compiler build server.</span></span>
