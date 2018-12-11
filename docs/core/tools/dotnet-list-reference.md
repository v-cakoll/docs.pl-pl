---
title: polecenie odwołania list DotNet
description: Polecenia dotnet list odwołania zapewnia wygodny sposób do listy odwołania projekt-projekt.
ms.date: 12/03/2018
ms.openlocfilehash: d22ea27f8e8f6b94d763e44a6d8644f814663797
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169836"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="a91cf-103">Odwołanie do listy DotNet</span><span class="sxs-lookup"><span data-stu-id="a91cf-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a91cf-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a91cf-104">Name</span></span>

<span data-ttu-id="a91cf-105">`dotnet list reference` — Wyświetla listę odwołania projekt projekt.</span><span class="sxs-lookup"><span data-stu-id="a91cf-105">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a91cf-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a91cf-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="a91cf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a91cf-107">Description</span></span>

<span data-ttu-id="a91cf-108">`dotnet list reference` Polecenia oferuje wygodne opcję do listy odwołań projektu dla danego projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a91cf-108">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="a91cf-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a91cf-109">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="a91cf-110">Określa plik projektu na potrzeby wyświetlania listy odwołania.</span><span class="sxs-lookup"><span data-stu-id="a91cf-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="a91cf-111">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a91cf-111">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="a91cf-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="a91cf-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="a91cf-113">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="a91cf-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="a91cf-114">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a91cf-114">Examples</span></span>

* <span data-ttu-id="a91cf-115">Utwórz listę odwołań projektu dla określonego projektu.</span><span class="sxs-lookup"><span data-stu-id="a91cf-115">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="a91cf-116">Listy odwołań projektu dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a91cf-116">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```