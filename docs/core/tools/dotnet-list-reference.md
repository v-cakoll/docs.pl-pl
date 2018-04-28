---
title: polecenie odwołania listy DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie dotnet listy odwołania zapewnia to wygodny sposób na liście odwołań projektów.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 946d3d523443fbe673b95dba95dbca327fde1699
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="a896f-103">Odwołanie do listy DotNet</span><span class="sxs-lookup"><span data-stu-id="a896f-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a896f-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a896f-104">Name</span></span>

<span data-ttu-id="a896f-105">`dotnet list reference` -Listy odwołań projektów.</span><span class="sxs-lookup"><span data-stu-id="a896f-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a896f-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a896f-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="a896f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a896f-107">Description</span></span>

<span data-ttu-id="a896f-108">`dotnet list reference` Polecenie zapewnia to wygodny sposób na liście odwołań do projektu dla danego projektu.</span><span class="sxs-lookup"><span data-stu-id="a896f-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="a896f-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a896f-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a896f-110">Określa plik projektu, który będzie używany do wyświetlania listy odwołania.</span><span class="sxs-lookup"><span data-stu-id="a896f-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="a896f-111">Jeśli nie zostanie określony, polecenie będzie szukał bieżący katalog dla pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a896f-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="a896f-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="a896f-112">Options</span></span>

`-h|--help`

<span data-ttu-id="a896f-113">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a896f-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="a896f-114">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a896f-114">Examples</span></span>

<span data-ttu-id="a896f-115">Lista odwołań do projektu dla określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="a896f-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="a896f-116">Lista odwołań do projektu dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a896f-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
