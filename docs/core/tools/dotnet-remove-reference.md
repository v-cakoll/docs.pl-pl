---
title: polecenie odwołania Usuń DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie dotnet Usuń odwołanie zapewnia to wygodny sposób, aby usunąć odwołania projektu do projektu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: b281b255be7f49a99a6b4928c340cd4fb085f085
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696234"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="c85df-103">DotNet Usuń odwołanie</span><span class="sxs-lookup"><span data-stu-id="c85df-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c85df-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c85df-104">Name</span></span>

<span data-ttu-id="c85df-105">`dotnet remove reference` — Usuwa odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="c85df-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c85df-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c85df-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="c85df-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c85df-107">Description</span></span>

<span data-ttu-id="c85df-108">`dotnet remove reference` Polecenie zapewnia to wygodny sposób, aby usunąć odwołania do projektu z projektu.</span><span class="sxs-lookup"><span data-stu-id="c85df-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="c85df-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c85df-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="c85df-110">Docelowy plik projektu.</span><span class="sxs-lookup"><span data-stu-id="c85df-110">Target project file.</span></span> <span data-ttu-id="c85df-111">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="c85df-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="c85df-112">Projekt do projektu (P2P) odwołuje się do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="c85df-112">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="c85df-113">Można określić jedną lub wiele projektów.</span><span class="sxs-lookup"><span data-stu-id="c85df-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="c85df-114">[Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminali z systemem Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="c85df-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="c85df-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="c85df-115">Options</span></span>

`-h|--help`

<span data-ttu-id="c85df-116">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="c85df-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="c85df-117">Usuwa odwołanie tylko wtedy, gdy przeznaczonych dla określonej [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c85df-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="c85df-118">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c85df-118">Examples</span></span>

<span data-ttu-id="c85df-119">Usuń odwołanie do projektu z określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="c85df-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="c85df-120">Usuń wiele odwołań do projektu z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="c85df-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="c85df-121">Usuń wiele odwołań do projektu przy użyciu wzorca glob w systemie Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="c85df-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
