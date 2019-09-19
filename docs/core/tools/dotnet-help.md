---
title: polecenie pomocy dotnet
description: Polecenie pomocy dotnet zawiera bardziej szczegółową dokumentację w trybie online dla określonego polecenia.
ms.date: 08/08/2019
ms.openlocfilehash: 533f2c47fa7ec14d31368538092fec2490234820
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117719"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="2032e-103">informacje pomocy dotyczące dotnet</span><span class="sxs-lookup"><span data-stu-id="2032e-103">dotnet help reference</span></span>

<span data-ttu-id="2032e-104">**Ten artykuł dotyczy: ✓** .net Core 2,0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="2032e-104">**This article applies to: ✓** .NET Core 2.0 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a><span data-ttu-id="2032e-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2032e-105">Name</span></span>

<span data-ttu-id="2032e-106">`dotnet help`-Wyświetla bardziej szczegółową dokumentację w trybie online dla określonego polecenia.</span><span class="sxs-lookup"><span data-stu-id="2032e-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2032e-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2032e-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="2032e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2032e-108">Description</span></span>

<span data-ttu-id="2032e-109">`dotnet help` Polecenie otwiera stronę referencyjną, aby uzyskać bardziej szczegółowe informacje na temat określonego polecenia w docs.Microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="2032e-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="2032e-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2032e-110">Arguments</span></span>

* **`COMMAND_NAME`**

  <span data-ttu-id="2032e-111">Nazwa polecenia interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2032e-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="2032e-112">Aby uzyskać listę prawidłowych poleceń interfejsu wiersza polecenia, zobacz [poleceń interfejsu wiersza polecenia](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="2032e-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="2032e-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="2032e-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="2032e-114">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2032e-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="2032e-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2032e-115">Examples</span></span>

* <span data-ttu-id="2032e-116">Otwiera stronę dokumentacji dla nowego polecenia [dotnet](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="2032e-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
