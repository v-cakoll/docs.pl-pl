---
title: dotnet usunąć pakiet, polecenie
description: Polecenie dotnet remove package zapewnia wygodną opcję usunięcia odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463456"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="687e6-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="687e6-103">dotnet remove package</span></span>

<span data-ttu-id="687e6-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="687e6-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="687e6-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="687e6-105">Name</span></span>

<span data-ttu-id="687e6-106">`dotnet remove package`- Usuwa odwołanie do pakietu z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="687e6-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="687e6-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="687e6-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a><span data-ttu-id="687e6-108">Opis</span><span class="sxs-lookup"><span data-stu-id="687e6-108">Description</span></span>

<span data-ttu-id="687e6-109">Polecenie `dotnet remove package` zapewnia wygodną opcję, aby usunąć odwołanie do pakietu NuGet z projektu.</span><span class="sxs-lookup"><span data-stu-id="687e6-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="687e6-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="687e6-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="687e6-111">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="687e6-111">Specifies the project file.</span></span> <span data-ttu-id="687e6-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego.</span><span class="sxs-lookup"><span data-stu-id="687e6-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="687e6-113">Odwołanie do pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="687e6-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="687e6-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="687e6-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="687e6-115">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="687e6-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="687e6-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="687e6-116">Examples</span></span>

- <span data-ttu-id="687e6-117">Usuń `Newtonsoft.Json` pakiet NuGet z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="687e6-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
