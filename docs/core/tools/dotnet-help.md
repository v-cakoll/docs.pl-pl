---
title: polecenie pomocy DotNet
description: Polecenia dotnet pomocy zawiera bardziej szczegółowe dokumentację online dla określonego polecenia.
ms.date: 12/04/2018
ms.openlocfilehash: 44274b698ed83bd3cdb58787f433eeb5c555bc6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665120"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="69205-103">Dokumentacja pomocy DotNet</span><span class="sxs-lookup"><span data-stu-id="69205-103">dotnet help reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="69205-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="69205-104">Name</span></span>

<span data-ttu-id="69205-105">`dotnet help` -Przedstawiono bardziej szczegółowe dokumentację online dla określonego polecenia.</span><span class="sxs-lookup"><span data-stu-id="69205-105">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="69205-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="69205-106">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="69205-107">Opis</span><span class="sxs-lookup"><span data-stu-id="69205-107">Description</span></span>

<span data-ttu-id="69205-108">`dotnet help` Polecenie otwiera stronę odwołania, aby uzyskać szczegółowe informacje dotyczące określonego polecenia w witrynie docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="69205-108">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="69205-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="69205-109">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="69205-110">Nazwa polecenia interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69205-110">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="69205-111">Aby uzyskać listę prawidłowych poleceń interfejsu wiersza polecenia, zobacz [poleceń interfejsu wiersza polecenia](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="69205-111">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="69205-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="69205-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="69205-113">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="69205-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="69205-114">Przykłady</span><span class="sxs-lookup"><span data-stu-id="69205-114">Examples</span></span>

* <span data-ttu-id="69205-115">Otwiera stronę dokumentacji [dotnet nowe](dotnet-new.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="69205-115">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```console
  dotnet help new
  ```