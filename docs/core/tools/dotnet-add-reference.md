---
title: DotNet — Dodaj polecenie odwołanie - .NET Core interfejsu wiersza polecenia
description: Dotnet Dodaj odwołanie polecenie zapewnia to wygodny sposób, aby dodać odwołania projektu do projektu.
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: c82696eee2fbe4bbad86e59cf5de1c2e74d048f6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="cf1a8-103">DotNet — Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="cf1a8-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cf1a8-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cf1a8-104">Name</span></span>

<span data-ttu-id="cf1a8-105">`dotnet add reference` -Dodaje odwołania do projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="cf1a8-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cf1a8-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="cf1a8-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="cf1a8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cf1a8-107">Description</span></span>

<span data-ttu-id="cf1a8-108">`dotnet add reference` Polecenie zapewnia to wygodny sposób, aby dodać odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="cf1a8-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="cf1a8-109">Po uruchomieniu polecenia [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) elementy są dodawane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="cf1a8-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="cf1a8-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cf1a8-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="cf1a8-111">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="cf1a8-111">Specifies the project file.</span></span> <span data-ttu-id="cf1a8-112">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="cf1a8-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="cf1a8-113">Projekt do projektu (P2P) odwołuje się do dodania.</span><span class="sxs-lookup"><span data-stu-id="cf1a8-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="cf1a8-114">Określ co najmniej jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="cf1a8-114">Specify one or more projects.</span></span> <span data-ttu-id="cf1a8-115">[Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w systemach opartych na systemie Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="cf1a8-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="cf1a8-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="cf1a8-116">Options</span></span>

`-h|--help`

<span data-ttu-id="cf1a8-117">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf1a8-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cf1a8-118">Dodaje odwołania do projektu, tylko gdy jest określony [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="cf1a8-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="cf1a8-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cf1a8-119">Examples</span></span>

<span data-ttu-id="cf1a8-120">Dodaj odwołanie do projektu:</span><span class="sxs-lookup"><span data-stu-id="cf1a8-120">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="cf1a8-121">Dodaj wiele odwołań do projektu do projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="cf1a8-121">Add multiple project references to the project in the current directory:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="cf1a8-122">Dodaj wiele odwołań do projektu przy użyciu wzorca globbing na systemie Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="cf1a8-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`
