---
title: dotnet usunąć polecenie odwołania
description: Polecenie dotnet remove reference zapewnia wygodną opcję usuwania odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 92d36bbbde64d806abc8f223c5f08e3f3d79ce9d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463442"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="91312-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="91312-103">dotnet remove reference</span></span>

<span data-ttu-id="91312-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="91312-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="91312-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="91312-105">Name</span></span>

<span data-ttu-id="91312-106">`dotnet remove reference`- Usuwa odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="91312-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="91312-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="91312-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>] <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a><span data-ttu-id="91312-108">Opis</span><span class="sxs-lookup"><span data-stu-id="91312-108">Description</span></span>

<span data-ttu-id="91312-109">Polecenie `dotnet remove reference` zapewnia wygodną opcję usuwania odwołań do projektu z projektu.</span><span class="sxs-lookup"><span data-stu-id="91312-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="91312-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="91312-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="91312-111">Docelowy plik projektu.</span><span class="sxs-lookup"><span data-stu-id="91312-111">Target project file.</span></span> <span data-ttu-id="91312-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego.</span><span class="sxs-lookup"><span data-stu-id="91312-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="91312-113">Odwołania do projektu do projektu (P2P) do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="91312-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="91312-114">Można określić jeden lub wiele projektów.</span><span class="sxs-lookup"><span data-stu-id="91312-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="91312-115">[Wzorce Glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane na terminalach opartych na systemie Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="91312-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="91312-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="91312-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="91312-117">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="91312-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="91312-118">Usuwa odwołanie tylko wtedy, gdy kierowanie na określoną [strukturę](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="91312-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="91312-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="91312-119">Examples</span></span>

- <span data-ttu-id="91312-120">Usuń odwołanie do projektu z określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="91312-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="91312-121">Usuń wiele odwołań do projektu z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="91312-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="91312-122">Usuń wiele odwołań do projektu przy użyciu wzorca glob w systemie Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="91312-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
