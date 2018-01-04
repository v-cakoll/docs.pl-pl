---
title: "DotNet Usuń polecenie pakietu - .NET Core interfejsu wiersza polecenia"
description: "Polecenie pakietu Usuń dotnet zapewnia to wygodny sposób, aby usunąć odwołanie do pakietu NuGet do projektu."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 1bc8d9cdc4db1f103b73116b43e630185a2c35de
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="74022-103">Pakiet Usuń DotNet</span><span class="sxs-lookup"><span data-stu-id="74022-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="74022-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="74022-104">Name</span></span>

<span data-ttu-id="74022-105">`dotnet remove package`— Usuwa odwołanie do pakietu z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="74022-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="74022-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="74022-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="74022-107">Opis</span><span class="sxs-lookup"><span data-stu-id="74022-107">Description</span></span>

<span data-ttu-id="74022-108">`dotnet remove package` Polecenie zapewnia to wygodny sposób, aby usunąć odwołanie do pakietu NuGet z projektu.</span><span class="sxs-lookup"><span data-stu-id="74022-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="74022-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="74022-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="74022-110">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="74022-110">Specifies the project file.</span></span> <span data-ttu-id="74022-111">Jeśli nie zostanie określony, polecenie będzie wyszukać bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="74022-111">If not specified, the command will search the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="74022-112">Odwołanie pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="74022-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="74022-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="74022-113">Options</span></span>

`-h|--help`

<span data-ttu-id="74022-114">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="74022-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="74022-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="74022-115">Examples</span></span>

<span data-ttu-id="74022-116">Usuwa `Newtonsoft.Json` pakietu NuGet z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="74022-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
