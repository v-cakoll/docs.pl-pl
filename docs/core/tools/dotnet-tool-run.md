---
title: Uruchom polecenie Narzędzia dotnet
description: Polecenie Uruchom narzędzie dotnet wywołuje narzędzie lokalne.
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543881"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="3a78b-103">uruchomienie narzędzia dotnet</span><span class="sxs-lookup"><span data-stu-id="3a78b-103">dotnet tool run</span></span>

<span data-ttu-id="3a78b-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="3a78b-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3a78b-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="3a78b-105">Name</span></span>

<span data-ttu-id="3a78b-106">`dotnet tool run` — wywołuje narzędzie lokalne.</span><span class="sxs-lookup"><span data-stu-id="3a78b-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3a78b-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3a78b-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME> 
dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="3a78b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="3a78b-108">Description</span></span>

<span data-ttu-id="3a78b-109">Polecenie `dotnet tool run` przeszukuje pliki manifestu narzędzia, które znajdują się w zakresie dla bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="3a78b-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="3a78b-110">Po znalezieniu odwołania do określonego narzędzia zostanie uruchomione narzędzie.</span><span class="sxs-lookup"><span data-stu-id="3a78b-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="3a78b-111">Aby uzyskać więcej informacji, zobacz [wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="3a78b-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="3a78b-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3a78b-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="3a78b-113">Nazwa polecenia narzędzia do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="3a78b-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="3a78b-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="3a78b-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="3a78b-115">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3a78b-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="3a78b-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a78b-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="3a78b-117">Uruchamia narzędzie `dotnetsay` lokalnego.</span><span class="sxs-lookup"><span data-stu-id="3a78b-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a78b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a78b-118">See also</span></span>

- [<span data-ttu-id="3a78b-119">Narzędzia .NET Core</span><span class="sxs-lookup"><span data-stu-id="3a78b-119">.NET Core tools</span></span>](global-tools.md)
