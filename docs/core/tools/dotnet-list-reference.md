---
title: polecenie odwołania do listy dotnet
description: Polecenie odwołania do listy dotnet udostępnia wygodną opcję wyświetlania listy odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503719"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="25fbf-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="25fbf-103">dotnet list reference</span></span>

<span data-ttu-id="25fbf-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="25fbf-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="25fbf-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="25fbf-105">Name</span></span>

<span data-ttu-id="25fbf-106">`dotnet list reference` — wyświetla odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="25fbf-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="25fbf-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="25fbf-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="25fbf-108">Opis</span><span class="sxs-lookup"><span data-stu-id="25fbf-108">Description</span></span>

<span data-ttu-id="25fbf-109">Polecenie `dotnet list reference` udostępnia wygodną opcję wyświetlania listy odwołań projektu dla danego projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="25fbf-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="25fbf-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="25fbf-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="25fbf-111">Określa plik projektu lub rozwiązania, który ma być używany na potrzeby wyświetlania listy odwołań.</span><span class="sxs-lookup"><span data-stu-id="25fbf-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="25fbf-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="25fbf-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="25fbf-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="25fbf-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="25fbf-114">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="25fbf-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="25fbf-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="25fbf-115">Examples</span></span>

* <span data-ttu-id="25fbf-116">Wyświetl listę odwołań projektu dla określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="25fbf-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="25fbf-117">Wyświetl listę odwołań projektu dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="25fbf-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
