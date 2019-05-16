---
title: polecenia DotNet Usuń polecenie pakietu
description: Polecenia dotnet Usuń pakiet zapewnia wygodny sposób, aby usunąć odwołanie do pakietu NuGet do projektu.
ms.date: 05/29/2018
ms.openlocfilehash: cbdeacff78ef20c9a73010e10a771a724b23792e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632432"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="7da70-103">polecenia DotNet Usuń pakiet</span><span class="sxs-lookup"><span data-stu-id="7da70-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7da70-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7da70-104">Name</span></span>

<span data-ttu-id="7da70-105">`dotnet remove package` -Usuwa odwołanie do pakietu z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="7da70-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7da70-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="7da70-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="7da70-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7da70-107">Description</span></span>

<span data-ttu-id="7da70-108">`dotnet remove package` Polecenie zapewnia wygodny sposób, aby usunąć odwołanie do pakietu NuGet z projektu.</span><span class="sxs-lookup"><span data-stu-id="7da70-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="7da70-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7da70-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="7da70-110">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="7da70-110">Specifies the project file.</span></span> <span data-ttu-id="7da70-111">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="7da70-111">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="7da70-112">Odwołanie pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="7da70-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="7da70-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="7da70-113">Options</span></span>

`-h|--help`

<span data-ttu-id="7da70-114">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="7da70-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="7da70-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7da70-115">Examples</span></span>

<span data-ttu-id="7da70-116">Usuwa `Newtonsoft.Json` pakietu NuGet z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="7da70-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
