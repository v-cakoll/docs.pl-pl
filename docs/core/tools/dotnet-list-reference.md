---
title: polecenie odwołania do listy dotnet
description: Polecenie referencyjne listy dotnet zapewnia wygodną opcję listy odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: c0ea46298123e69ae527870e50d204d8fcf5cc85
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463645"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="5dddd-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="5dddd-103">dotnet list reference</span></span>

<span data-ttu-id="5dddd-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="5dddd-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5dddd-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5dddd-105">Name</span></span>

<span data-ttu-id="5dddd-106">`dotnet list reference`- Wyświetla listę odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="5dddd-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5dddd-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5dddd-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="5dddd-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5dddd-108">Description</span></span>

<span data-ttu-id="5dddd-109">Polecenie `dotnet list reference` zapewnia wygodną opcję listy odwołań do projektu dla danego projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5dddd-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="5dddd-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5dddd-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="5dddd-111">Określa plik projektu lub rozwiązania, który ma być używany do wyświetlania odwołań do listy.</span><span class="sxs-lookup"><span data-stu-id="5dddd-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="5dddd-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="5dddd-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="5dddd-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="5dddd-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="5dddd-114">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5dddd-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5dddd-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5dddd-115">Examples</span></span>

* <span data-ttu-id="5dddd-116">Lista odwołań do projektu dla określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="5dddd-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="5dddd-117">Wyświetl listę odwołań do projektu dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="5dddd-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
