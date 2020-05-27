---
title: polecenie odwołania do listy dotnet
description: Polecenie odwołania do listy dotnet udostępnia wygodną opcję wyświetlania listy odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802766"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="30355-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="30355-103">dotnet list reference</span></span>

<span data-ttu-id="30355-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="30355-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="30355-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="30355-105">Name</span></span>

<span data-ttu-id="30355-106">`dotnet list reference`-Wyświetla odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="30355-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="30355-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="30355-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="30355-108">Opis</span><span class="sxs-lookup"><span data-stu-id="30355-108">Description</span></span>

<span data-ttu-id="30355-109">`dotnet list reference`Polecenie udostępnia wygodną opcję wyświetlania listy odwołań projektu dla danego projektu.</span><span class="sxs-lookup"><span data-stu-id="30355-109">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="30355-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="30355-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="30355-111">Plik projektu do działania.</span><span class="sxs-lookup"><span data-stu-id="30355-111">The project file to operate on.</span></span> <span data-ttu-id="30355-112">Jeśli plik nie zostanie określony, polecenie przeszuka bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="30355-112">If a file is not specified, the command will search the current directory for one.</span></span>

## <a name="options"></a><span data-ttu-id="30355-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="30355-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="30355-114">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="30355-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="30355-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="30355-115">Examples</span></span>

* <span data-ttu-id="30355-116">Wyświetl listę odwołań projektu dla określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="30355-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="30355-117">Wyświetl listę odwołań projektu dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="30355-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
