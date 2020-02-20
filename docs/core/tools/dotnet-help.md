---
title: polecenie pomocy dotnet
description: Polecenie pomocy dotnet zawiera bardziej szczegółową dokumentację w trybie online dla określonego polecenia.
ms.date: 02/14/2020
ms.openlocfilehash: f5d9221ae18653451a3bf97dc82fae396ae4e288
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503728"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="2f360-103">informacje pomocy dotyczące dotnet</span><span class="sxs-lookup"><span data-stu-id="2f360-103">dotnet help reference</span></span>

<span data-ttu-id="2f360-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="2f360-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2f360-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="2f360-105">Name</span></span>

<span data-ttu-id="2f360-106">`dotnet help` — zawiera bardziej szczegółową dokumentację w trybie online dla określonego polecenia.</span><span class="sxs-lookup"><span data-stu-id="2f360-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2f360-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2f360-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="2f360-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2f360-108">Description</span></span>

<span data-ttu-id="2f360-109">`dotnet help` polecenie otwiera stronę referencyjną, aby uzyskać bardziej szczegółowe informacje na temat określonego polecenia w docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="2f360-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="2f360-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2f360-110">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="2f360-111">Nazwa polecenia interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f360-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="2f360-112">Aby uzyskać listę prawidłowych poleceń interfejsu wiersza polecenia, zobacz [poleceń interfejsu wiersza polecenia](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="2f360-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="2f360-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="2f360-113">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="2f360-114">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2f360-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="2f360-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2f360-115">Examples</span></span>

- <span data-ttu-id="2f360-116">Otwiera stronę dokumentacji dla nowego polecenia [dotnet](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="2f360-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
