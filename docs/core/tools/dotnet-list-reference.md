---
title: polecenie odwołania list DotNet
description: Polecenia dotnet list odwołania zapewnia wygodny sposób do listy odwołania projekt-projekt.
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421830"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="77318-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="77318-103">dotnet list reference</span></span>

<span data-ttu-id="77318-104">**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="77318-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="77318-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="77318-105">Name</span></span>

<span data-ttu-id="77318-106">`dotnet list reference` — Wyświetla listę odwołania projekt projekt.</span><span class="sxs-lookup"><span data-stu-id="77318-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="77318-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="77318-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="77318-108">Opis</span><span class="sxs-lookup"><span data-stu-id="77318-108">Description</span></span>

<span data-ttu-id="77318-109">`dotnet list reference` Polecenia oferuje wygodne opcję do listy odwołań projektu dla danego projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="77318-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="77318-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="77318-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="77318-111">Określa plik projektu lub rozwiązania służące do wyświetlania listy odwołania.</span><span class="sxs-lookup"><span data-stu-id="77318-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="77318-112">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="77318-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="77318-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="77318-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="77318-114">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="77318-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="77318-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="77318-115">Examples</span></span>

* <span data-ttu-id="77318-116">Utwórz listę odwołań projektu dla określonego projektu.</span><span class="sxs-lookup"><span data-stu-id="77318-116">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="77318-117">Listy odwołań projektu dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="77318-117">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```
