---
title: polecenie odwołania do listy dotnet
description: Polecenie odwołania do listy dotnet zapewnia wygodną opcję listy projektów do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503719"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="5c1f1-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="5c1f1-103">dotnet list reference</span></span>

<span data-ttu-id="5c1f1-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="5c1f1-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5c1f1-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5c1f1-105">Name</span></span>

<span data-ttu-id="5c1f1-106">`dotnet list reference`- Wyświetla listę odniesień do projektu.</span><span class="sxs-lookup"><span data-stu-id="5c1f1-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5c1f1-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5c1f1-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="5c1f1-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5c1f1-108">Description</span></span>

<span data-ttu-id="5c1f1-109">Polecenie `dotnet list reference` zapewnia wygodną opcję listy odwołań do projektu dla danego projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5c1f1-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="5c1f1-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5c1f1-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="5c1f1-111">Określa plik projektu lub rozwiązania, który ma być używany do wyświetlania odwołań do aukcji.</span><span class="sxs-lookup"><span data-stu-id="5c1f1-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="5c1f1-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="5c1f1-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="5c1f1-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="5c1f1-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="5c1f1-114">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5c1f1-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5c1f1-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5c1f1-115">Examples</span></span>

* <span data-ttu-id="5c1f1-116">Lista odwołań do projektu dla określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="5c1f1-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="5c1f1-117">Lista odwołań do projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="5c1f1-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
