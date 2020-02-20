---
title: polecenie usunięcia pakietu dotnet
description: Polecenie Narzędzia dotnet Remove Package udostępnia wygodną opcję usunięcia odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503631"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="cd9aa-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="cd9aa-103">dotnet remove package</span></span>

<span data-ttu-id="cd9aa-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="cd9aa-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cd9aa-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="cd9aa-105">Name</span></span>

<span data-ttu-id="cd9aa-106">`dotnet remove package` — usuwa odwołanie do pakietu z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="cd9aa-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cd9aa-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="cd9aa-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="cd9aa-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cd9aa-108">Description</span></span>

<span data-ttu-id="cd9aa-109">Polecenie `dotnet remove package` udostępnia wygodną opcję usunięcia odwołania do pakietu NuGet z projektu.</span><span class="sxs-lookup"><span data-stu-id="cd9aa-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="cd9aa-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cd9aa-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="cd9aa-111">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="cd9aa-111">Specifies the project file.</span></span> <span data-ttu-id="cd9aa-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="cd9aa-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="cd9aa-113">Odwołanie do pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="cd9aa-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="cd9aa-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="cd9aa-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="cd9aa-115">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="cd9aa-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="cd9aa-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cd9aa-116">Examples</span></span>

- <span data-ttu-id="cd9aa-117">Usuń `Newtonsoft.Json` pakiet NuGet z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="cd9aa-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
