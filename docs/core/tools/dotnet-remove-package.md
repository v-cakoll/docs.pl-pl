---
title: polecenie dotnet remove package
description: Polecenie dotnet remove package zapewnia wygodną opcję usunięcia odwołania nuget do pakietu do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503631"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="2a88a-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="2a88a-103">dotnet remove package</span></span>

<span data-ttu-id="2a88a-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="2a88a-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2a88a-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2a88a-105">Name</span></span>

<span data-ttu-id="2a88a-106">`dotnet remove package`- Usuwa odwołanie do pakietu z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2a88a-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2a88a-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2a88a-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="2a88a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2a88a-108">Description</span></span>

<span data-ttu-id="2a88a-109">Polecenie `dotnet remove package` zawiera wygodną opcję, aby usunąć odwołanie nuget pakietu z projektu.</span><span class="sxs-lookup"><span data-stu-id="2a88a-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="2a88a-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2a88a-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="2a88a-111">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="2a88a-111">Specifies the project file.</span></span> <span data-ttu-id="2a88a-112">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego.</span><span class="sxs-lookup"><span data-stu-id="2a88a-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="2a88a-113">Odwołanie do pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="2a88a-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="2a88a-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="2a88a-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="2a88a-115">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2a88a-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="2a88a-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2a88a-116">Examples</span></span>

- <span data-ttu-id="2a88a-117">Usuń `Newtonsoft.Json` pakiet NuGet z projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="2a88a-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
