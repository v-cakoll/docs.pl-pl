---
title: DotNet Usuń polecenie pakietu - .NET Core interfejsu wiersza polecenia
description: Polecenie pakietu Usuń dotnet zapewnia to wygodny sposób, aby usunąć odwołanie do pakietu NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: bdb66a24526b04e8300e654a991719bb607971b8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="70cd5-103">Pakiet Usuń DotNet</span><span class="sxs-lookup"><span data-stu-id="70cd5-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="70cd5-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="70cd5-104">Name</span></span>

<span data-ttu-id="70cd5-105">`dotnet remove package` — Usuwa odwołanie do pakietu z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="70cd5-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="70cd5-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="70cd5-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="70cd5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="70cd5-107">Description</span></span>

<span data-ttu-id="70cd5-108">`dotnet remove package` Polecenie zapewnia to wygodny sposób, aby usunąć odwołanie do pakietu NuGet z projektu.</span><span class="sxs-lookup"><span data-stu-id="70cd5-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="70cd5-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="70cd5-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="70cd5-110">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="70cd5-110">Specifies the project file.</span></span> <span data-ttu-id="70cd5-111">Jeśli nie zostanie określony, polecenie będzie wyszukać bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="70cd5-111">If not specified, the command will search the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="70cd5-112">Odwołanie pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="70cd5-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="70cd5-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="70cd5-113">Options</span></span>

`-h|--help`

<span data-ttu-id="70cd5-114">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="70cd5-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="70cd5-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="70cd5-115">Examples</span></span>

<span data-ttu-id="70cd5-116">Usuwa `Newtonsoft.Json` pakietu NuGet z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="70cd5-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
