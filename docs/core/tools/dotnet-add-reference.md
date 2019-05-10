---
title: polecenia DotNet-Dodaj odwołania — polecenie
description: Dotnet Dodaj odwołanie do polecenia zapewnia wygodny sposób, aby dodać odwołania projektu do projektu.
ms.date: 04/24/2019
ms.openlocfilehash: f33a379534dca88133babbb5ca78bca614e441c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755194"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="d5c9d-103">polecenia DotNet-Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="d5c9d-103">dotnet-add reference</span></span>

<span data-ttu-id="d5c9d-104">**Ten artykuł dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="d5c9d-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="d5c9d-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d5c9d-105">Name</span></span>

<span data-ttu-id="d5c9d-106">`dotnet add reference` -Dodaje odwołania do projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="d5c9d-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d5c9d-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d5c9d-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="d5c9d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d5c9d-108">Description</span></span>

<span data-ttu-id="d5c9d-109">`dotnet add reference` Polecenie zapewnia wygodny sposób, aby dodać odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="d5c9d-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="d5c9d-110">Po uruchomieniu polecenia [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) elementy są dodawane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d5c9d-110">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="d5c9d-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d5c9d-111">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="d5c9d-112">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="d5c9d-112">Specifies the project file.</span></span> <span data-ttu-id="d5c9d-113">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="d5c9d-113">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="d5c9d-114">Projekt do projektu (P2P) odwołuje się do dodania.</span><span class="sxs-lookup"><span data-stu-id="d5c9d-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="d5c9d-115">Określ co najmniej jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="d5c9d-115">Specify one or more projects.</span></span> <span data-ttu-id="d5c9d-116">[Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach opartych na systemie Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="d5c9d-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="d5c9d-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="d5c9d-117">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="d5c9d-118">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="d5c9d-118">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d5c9d-119">Dodaje odwołania do projektu tylko wtedy, gdy przeznaczonych dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d5c9d-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="d5c9d-120">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d5c9d-120">Examples</span></span>

* <span data-ttu-id="d5c9d-121">Dodaj odwołanie do projektu:</span><span class="sxs-lookup"><span data-stu-id="d5c9d-121">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="d5c9d-122">Dodaj wielu odwołania projektu do projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="d5c9d-122">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="d5c9d-123">Dodaj wielu odwołania do projektu przy użyciu wzorca obsługi symboli wieloznacznych w systemach Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="d5c9d-123">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```