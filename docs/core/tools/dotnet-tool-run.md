---
title: polecenie uruchom narzędzie dotnet
description: Polecenie uruchamiania narzędzia dotnet wywołuje narzędzie lokalne.
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847849"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="488f4-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="488f4-103">dotnet tool run</span></span>

<span data-ttu-id="488f4-104">**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="488f4-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="488f4-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="488f4-105">Name</span></span>

<span data-ttu-id="488f4-106">`dotnet tool run`- Wywołuje lokalne narzędzie.</span><span class="sxs-lookup"><span data-stu-id="488f4-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="488f4-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="488f4-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="488f4-108">Opis</span><span class="sxs-lookup"><span data-stu-id="488f4-108">Description</span></span>

<span data-ttu-id="488f4-109">Polecenie `dotnet tool run` wyszukuje pliki manifestu narzędzia, które znajdują się w zakresie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="488f4-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="488f4-110">Po znalezieniu odwołania do określonego narzędzia uruchamia narzędzie.</span><span class="sxs-lookup"><span data-stu-id="488f4-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="488f4-111">Aby uzyskać więcej informacji, zobacz [Wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="488f4-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="488f4-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="488f4-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="488f4-113">Nazwa polecenia narzędzia do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="488f4-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="488f4-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="488f4-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="488f4-115">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="488f4-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="488f4-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="488f4-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="488f4-117">Uruchamia `dotnetsay` narzędzie lokalne.</span><span class="sxs-lookup"><span data-stu-id="488f4-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="488f4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="488f4-118">See also</span></span>

- [<span data-ttu-id="488f4-119">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="488f4-119">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="488f4-120">Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="488f4-120">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
