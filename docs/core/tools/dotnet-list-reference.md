---
title: polecenie odwołania do listy dotnet
description: Polecenie odwołania do listy dotnet udostępnia wygodną opcję wyświetlania listy odwołań do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733225"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="f90a8-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="f90a8-103">dotnet list reference</span></span>

<span data-ttu-id="f90a8-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="f90a8-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="f90a8-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f90a8-105">Name</span></span>

<span data-ttu-id="f90a8-106">`dotnet list reference` — wyświetla odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="f90a8-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f90a8-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="f90a8-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="f90a8-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f90a8-108">Description</span></span>

<span data-ttu-id="f90a8-109">Polecenie `dotnet list reference` udostępnia wygodną opcję wyświetlania listy odwołań projektu dla danego projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f90a8-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="f90a8-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f90a8-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="f90a8-111">Określa plik projektu lub rozwiązania, który ma być używany na potrzeby wyświetlania listy odwołań.</span><span class="sxs-lookup"><span data-stu-id="f90a8-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="f90a8-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="f90a8-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="f90a8-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="f90a8-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="f90a8-114">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="f90a8-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="f90a8-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f90a8-115">Examples</span></span>

* <span data-ttu-id="f90a8-116">Wyświetl listę odwołań projektu dla określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="f90a8-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="f90a8-117">Wyświetl listę odwołań projektu dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="f90a8-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
