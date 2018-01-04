---
title: "polecenie odwołania Usuń DotNet - .NET Core interfejsu wiersza polecenia"
description: "Polecenie dotnet Usuń odwołanie zapewnia to wygodny sposób, aby usunąć odwołania projektu do projektu."
keywords: "Usuń DotNet, interfejsu wiersza polecenia, polecenia interfejsu wiersza polecenia, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 691fd77c7605b6476adc764f20e59b51abd7d914
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="6e6fb-104">DotNet Usuń odwołanie</span><span class="sxs-lookup"><span data-stu-id="6e6fb-104">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6e6fb-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6e6fb-105">Name</span></span>

<span data-ttu-id="6e6fb-106">`dotnet remove reference`— Usuwa odwołania projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6e6fb-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="6e6fb-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="6e6fb-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6e6fb-108">Description</span></span>

<span data-ttu-id="6e6fb-109">`dotnet remove reference` Polecenie zapewnia to wygodny sposób, aby usunąć odwołania do projektu z projektu.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="6e6fb-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6e6fb-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="6e6fb-111">Docelowy plik projektu.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-111">Target project file.</span></span> <span data-ttu-id="6e6fb-112">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="6e6fb-113">Projekt do projektu (P2P odwołania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-113">Project to project (P2P references to remove.</span></span> <span data-ttu-id="6e6fb-114">Można określić jedną lub wiele projektów.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="6e6fb-115">[Wzorce glob](https://en.wikipedia.org/wiki/Glob_(programming)) są obsługiwane w terminali z systemem Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="6e6fb-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="6e6fb-116">Options</span></span>

`-h|--help`

<span data-ttu-id="6e6fb-117">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="6e6fb-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6e6fb-118">Usuwa odwołanie tylko wtedy, gdy przeznaczonych dla określonej [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6e6fb-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="6e6fb-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6e6fb-119">Examples</span></span>

<span data-ttu-id="6e6fb-120">Usuń odwołanie do projektu z określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="6e6fb-120">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="6e6fb-121">Usuń wiele odwołań do projektu z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="6e6fb-121">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="6e6fb-122">Usuń wiele odwołań do projektu przy użyciu wzorca glob w systemie Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="6e6fb-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
