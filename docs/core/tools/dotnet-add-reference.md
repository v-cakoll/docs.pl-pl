---
title: polecenia DotNet-Dodaj odwołania — polecenie
description: Dotnet Dodaj odwołanie do polecenia zapewnia wygodny sposób, aby dodać odwołania projektu do projektu.
ms.date: 12/04/2018
ms.openlocfilehash: 8df9fa3c9469f74b27a9cb8120936f03532b016c
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169771"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="67996-103">polecenia DotNet-Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="67996-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="67996-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="67996-104">Name</span></span>

<span data-ttu-id="67996-105">`dotnet add reference` -Dodaje odwołania do projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="67996-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="67996-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="67996-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="67996-107">Opis</span><span class="sxs-lookup"><span data-stu-id="67996-107">Description</span></span>

<span data-ttu-id="67996-108">`dotnet add reference` Polecenie zapewnia wygodny sposób, aby dodać odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="67996-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="67996-109">Po uruchomieniu polecenia [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) elementy są dodawane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="67996-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="67996-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="67996-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="67996-111">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="67996-111">Specifies the project file.</span></span> <span data-ttu-id="67996-112">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="67996-112">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="67996-113">Projekt do projektu (P2P) odwołuje się do dodania.</span><span class="sxs-lookup"><span data-stu-id="67996-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="67996-114">Określ co najmniej jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="67996-114">Specify one or more projects.</span></span> <span data-ttu-id="67996-115">[Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach opartych na systemie Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="67996-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="67996-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="67996-116">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="67996-117">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="67996-117">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67996-118">Dodaje odwołania do projektu tylko wtedy, gdy przeznaczonych dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="67996-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="67996-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="67996-119">Examples</span></span>

* <span data-ttu-id="67996-120">Dodaj odwołanie do projektu:</span><span class="sxs-lookup"><span data-stu-id="67996-120">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="67996-121">Dodaj wielu odwołania projektu do projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="67996-121">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="67996-122">Dodaj wielu odwołania do projektu przy użyciu wzorca obsługi symboli wieloznacznych w systemach Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="67996-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```