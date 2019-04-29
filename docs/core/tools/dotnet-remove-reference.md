---
title: polecenie odwołania remove DotNet
description: Polecenia dotnet Usuń odwołanie zapewnia wygodny sposób, aby usunąć odwołania projekt-projekt.
ms.date: 05/29/2018
ms.openlocfilehash: bfac4721743babcf48fd8e86a50c8df136e1bfce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648597"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="ccf2a-103">polecenia DotNet Usuń odwołanie</span><span class="sxs-lookup"><span data-stu-id="ccf2a-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ccf2a-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ccf2a-104">Name</span></span>

<span data-ttu-id="ccf2a-105">`dotnet remove reference` -Usuwa odwołania projekt projekt.</span><span class="sxs-lookup"><span data-stu-id="ccf2a-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ccf2a-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ccf2a-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="ccf2a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ccf2a-107">Description</span></span>

<span data-ttu-id="ccf2a-108">`dotnet remove reference` Polecenie zapewnia wygodny sposób, aby usunąć odwołania do projektu z projektu.</span><span class="sxs-lookup"><span data-stu-id="ccf2a-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="ccf2a-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ccf2a-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="ccf2a-110">Docelowy plik projektu.</span><span class="sxs-lookup"><span data-stu-id="ccf2a-110">Target project file.</span></span> <span data-ttu-id="ccf2a-111">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="ccf2a-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="ccf2a-112">Projekt do projektu (P2P) odwołuje się do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="ccf2a-112">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="ccf2a-113">Można określić jeden lub wiele projektów.</span><span class="sxs-lookup"><span data-stu-id="ccf2a-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="ccf2a-114">[Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminale systemu Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="ccf2a-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="ccf2a-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="ccf2a-115">Options</span></span>

`-h|--help`

<span data-ttu-id="ccf2a-116">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="ccf2a-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ccf2a-117">Usuwa odwołanie, tylko wtedy, gdy przeznaczonych dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ccf2a-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="ccf2a-118">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ccf2a-118">Examples</span></span>

<span data-ttu-id="ccf2a-119">Usuń odwołanie do projektu z określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="ccf2a-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="ccf2a-120">Usuń wiele odwołań do projektu z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ccf2a-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="ccf2a-121">Usuń wiele odwołania do projektu przy użyciu wzorca glob w systemie Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="ccf2a-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
