---
title: polecenie "Usuń odwołanie" dotnet
description: Polecenie "Usuń odwołanie" dotnet zapewnia wygodną opcję usuwania projektu do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: a45153376d7d6eb764c1d2c6b473d04a273a2de1
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158336"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="89786-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="89786-103">dotnet remove reference</span></span>

<span data-ttu-id="89786-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="89786-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="89786-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="89786-105">Name</span></span>

<span data-ttu-id="89786-106">`dotnet remove reference`-Usuwa odwołania z projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="89786-106">`dotnet remove reference` - Removes project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="89786-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="89786-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     <PROJECT_REFERENCES>

dotnet remove reference -h|--help
```

## <a name="description"></a><span data-ttu-id="89786-108">Opis</span><span class="sxs-lookup"><span data-stu-id="89786-108">Description</span></span>

<span data-ttu-id="89786-109">`dotnet remove reference` Polecenie zapewnia wygodną opcję usuwania odwołań projektu z projektu.</span><span class="sxs-lookup"><span data-stu-id="89786-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="89786-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="89786-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="89786-111">Docelowy plik projektu.</span><span class="sxs-lookup"><span data-stu-id="89786-111">Target project file.</span></span> <span data-ttu-id="89786-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="89786-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="89786-113">Odwołania między projektami i projektami (P2P) do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="89786-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="89786-114">Można określić jeden lub wiele projektów.</span><span class="sxs-lookup"><span data-stu-id="89786-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="89786-115">[Wzorce globalizowania](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminalach opartych na systemie UNIX/Linux.</span><span class="sxs-lookup"><span data-stu-id="89786-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="89786-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="89786-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="89786-117">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="89786-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="89786-118">Usuwa odwołanie tylko w przypadku określania konkretnej [struktury](../../standard/frameworks.md) przy użyciu formatu TFM.</span><span class="sxs-lookup"><span data-stu-id="89786-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md) using the TFM format.</span></span>

## <a name="examples"></a><span data-ttu-id="89786-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="89786-119">Examples</span></span>

- <span data-ttu-id="89786-120">Usuń odwołanie do projektu z określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="89786-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="89786-121">Usuń odwołania do wielu projektów z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="89786-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="89786-122">Usuń odwołania do wielu projektów za pomocą wzorca globalizowania w systemie UNIX/Linux:</span><span class="sxs-lookup"><span data-stu-id="89786-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
