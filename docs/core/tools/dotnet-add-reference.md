---
title: dotnet dodaj polecenie odwołania
description: Polecenie dotnet add reference zapewnia wygodną opcję dodawania projektu do odwołań do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: f2bd67d181784c4858b8971d05053d196df7818e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463744"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="3b8fe-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="3b8fe-103">dotnet add reference</span></span>

<span data-ttu-id="3b8fe-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="3b8fe-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3b8fe-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3b8fe-105">Name</span></span>

<span data-ttu-id="3b8fe-106">`dotnet add reference`- Dodaje odwołania projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="3b8fe-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b8fe-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3b8fe-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a><span data-ttu-id="3b8fe-108">Opis</span><span class="sxs-lookup"><span data-stu-id="3b8fe-108">Description</span></span>

<span data-ttu-id="3b8fe-109">Polecenie `dotnet add reference` zapewnia wygodną opcję dodawania odwołań do projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8fe-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="3b8fe-110">Po uruchomieniu polecenia `<ProjectReference>` elementy są dodawane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8fe-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="3b8fe-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3b8fe-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="3b8fe-112">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="3b8fe-112">Specifies the project file.</span></span> <span data-ttu-id="3b8fe-113">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego.</span><span class="sxs-lookup"><span data-stu-id="3b8fe-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="3b8fe-114">Odwołania do projektu do projektu (P2P) do dodania.</span><span class="sxs-lookup"><span data-stu-id="3b8fe-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="3b8fe-115">Określ jeden lub więcej projektów.</span><span class="sxs-lookup"><span data-stu-id="3b8fe-115">Specify one or more projects.</span></span> <span data-ttu-id="3b8fe-116">[Wzorce Glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach opartych na systemie Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="3b8fe-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="3b8fe-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="3b8fe-117">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="3b8fe-118">Dodaje odwołania do projektu tylko wtedy, gdy kierowanie na określoną [platformę](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="3b8fe-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="3b8fe-119">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3b8fe-119">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="3b8fe-120">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="3b8fe-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="3b8fe-121">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="3b8fe-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="3b8fe-122">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3b8fe-122">Examples</span></span>

- <span data-ttu-id="3b8fe-123">Dodaj odwołanie do projektu:</span><span class="sxs-lookup"><span data-stu-id="3b8fe-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="3b8fe-124">Dodaj wiele odwołań do projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="3b8fe-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="3b8fe-125">Dodaj wiele odwołań do projektu przy użyciu wzorca globbingu w systemie Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="3b8fe-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
