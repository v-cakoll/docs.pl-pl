---
title: polecenia DotNet-Dodaj odwołania — polecenie
description: Dotnet Dodaj odwołanie do polecenia zapewnia wygodny sposób, aby dodać odwołania projektu do projektu.
ms.date: 04/24/2019
ms.openlocfilehash: e90f95527d4f14c7851ccd8d30201daaaaefa2ae
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631936"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="66edd-103">polecenia DotNet-Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="66edd-103">dotnet-add reference</span></span>

<span data-ttu-id="66edd-104">**Ten artykuł dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="66edd-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="66edd-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="66edd-105">Name</span></span>

<span data-ttu-id="66edd-106">`dotnet add reference` -Dodaje odwołania do projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="66edd-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="66edd-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="66edd-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="66edd-108">Opis</span><span class="sxs-lookup"><span data-stu-id="66edd-108">Description</span></span>

<span data-ttu-id="66edd-109">`dotnet add reference` Polecenie zapewnia wygodny sposób, aby dodać odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="66edd-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="66edd-110">Po uruchomieniu polecenia [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) elementy są dodawane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="66edd-110">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="66edd-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="66edd-111">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="66edd-112">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="66edd-112">Specifies the project file.</span></span> <span data-ttu-id="66edd-113">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="66edd-113">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="66edd-114">Projekt do projektu (P2P) odwołuje się do dodania.</span><span class="sxs-lookup"><span data-stu-id="66edd-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="66edd-115">Określ co najmniej jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="66edd-115">Specify one or more projects.</span></span> <span data-ttu-id="66edd-116">[Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach opartych na systemie Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="66edd-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="66edd-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="66edd-117">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="66edd-118">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="66edd-118">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="66edd-119">Dodaje odwołania do projektu tylko wtedy, gdy przeznaczonych dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="66edd-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="66edd-120">Przykłady</span><span class="sxs-lookup"><span data-stu-id="66edd-120">Examples</span></span>

* <span data-ttu-id="66edd-121">Dodaj odwołanie do projektu:</span><span class="sxs-lookup"><span data-stu-id="66edd-121">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="66edd-122">Dodaj wielu odwołania projektu do projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="66edd-122">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="66edd-123">Dodaj wielu odwołania do projektu przy użyciu wzorca obsługi symboli wieloznacznych w systemach Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="66edd-123">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
