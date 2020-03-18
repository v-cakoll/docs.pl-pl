---
title: polecenie dotnet remove reference
description: Polecenie odwołania dotnet remove zapewnia wygodną opcję usuwania projektu do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503618"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="92a35-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="92a35-103">dotnet remove reference</span></span>

<span data-ttu-id="92a35-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="92a35-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="92a35-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="92a35-105">Name</span></span>

<span data-ttu-id="92a35-106">`dotnet remove reference`- Usuwa odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="92a35-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="92a35-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="92a35-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="92a35-108">Opis</span><span class="sxs-lookup"><span data-stu-id="92a35-108">Description</span></span>

<span data-ttu-id="92a35-109">Polecenie `dotnet remove reference` zapewnia wygodną opcję usuwania odwołań do projektu z projektu.</span><span class="sxs-lookup"><span data-stu-id="92a35-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="92a35-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="92a35-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="92a35-111">Docelowy plik projektu.</span><span class="sxs-lookup"><span data-stu-id="92a35-111">Target project file.</span></span> <span data-ttu-id="92a35-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego.</span><span class="sxs-lookup"><span data-stu-id="92a35-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="92a35-113">Odwołania do projektu (P2P) do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="92a35-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="92a35-114">Można określić jeden lub wiele projektów.</span><span class="sxs-lookup"><span data-stu-id="92a35-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="92a35-115">[Wzorce Glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane na terminalach unixowych/linuxowych.</span><span class="sxs-lookup"><span data-stu-id="92a35-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="92a35-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="92a35-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="92a35-117">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="92a35-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="92a35-118">Usuwa odwołanie tylko podczas określania określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="92a35-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="92a35-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="92a35-119">Examples</span></span>

- <span data-ttu-id="92a35-120">Usuń odwołanie do projektu z określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="92a35-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="92a35-121">Usuń wiele odwołań do projektu z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="92a35-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="92a35-122">Usuń wiele odwołań do projektu za pomocą wzoru glob na Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="92a35-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
