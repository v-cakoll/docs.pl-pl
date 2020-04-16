---
title: polecenie pomocy dotnet
description: Polecenie pomocy dotnet zawiera bardziej szczegółową dokumentację dla określonego polecenia.
ms.date: 02/14/2020
ms.openlocfilehash: a59e74a318118b6fd39d1895df02d76daa6fc9e1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463690"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="87fc8-103">odwołanie do pomocy dotnet</span><span class="sxs-lookup"><span data-stu-id="87fc8-103">dotnet help reference</span></span>

<span data-ttu-id="87fc8-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="87fc8-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="87fc8-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="87fc8-105">Name</span></span>

<span data-ttu-id="87fc8-106">`dotnet help`- Pokazuje bardziej szczegółową dokumentację online dla określonego polecenia.</span><span class="sxs-lookup"><span data-stu-id="87fc8-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="87fc8-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="87fc8-107">Synopsis</span></span>

```dotnetcli
dotnet help <COMMAND_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="87fc8-108">Opis</span><span class="sxs-lookup"><span data-stu-id="87fc8-108">Description</span></span>

<span data-ttu-id="87fc8-109">Polecenie `dotnet help` otwiera stronę referencyjną, aby uzyskać bardziej szczegółowe informacje o określonym poleceniu w docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="87fc8-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="87fc8-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="87fc8-110">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="87fc8-111">Nazwa polecenia .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="87fc8-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="87fc8-112">Aby uzyskać listę prawidłowych poleceń interfejsu wiersza polecenia, zobacz [polecenia interfejsu wiersza polecenia](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="87fc8-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="87fc8-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="87fc8-113">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="87fc8-114">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="87fc8-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="87fc8-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="87fc8-115">Examples</span></span>

- <span data-ttu-id="87fc8-116">Otwiera stronę dokumentacji nowego polecenia [dotnet:](dotnet-new.md)</span><span class="sxs-lookup"><span data-stu-id="87fc8-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
