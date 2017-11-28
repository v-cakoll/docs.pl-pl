---
title: DotNet Dodaj polecenie pakietu - .NET Core interfejsu wiersza polecenia
description: "Polecenie \"dotnet Dodawanie pakietu\" zapewnia to wygodny sposób, aby dodać odwołanie pakiet NuGet do projektu."
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 7518ec32d669e64d713e77f687d285279b012967
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-add-package"></a><span data-ttu-id="c718d-103">DotNet Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="c718d-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c718d-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c718d-104">Name</span></span>

<span data-ttu-id="c718d-105">`dotnet add package`-Dodaje pakiet odwołanie do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c718d-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c718d-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c718d-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a><span data-ttu-id="c718d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c718d-107">Description</span></span>

<span data-ttu-id="c718d-108">`dotnet add package` Polecenie zapewnia to wygodny sposób, aby dodać pakiet odwołanie do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c718d-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="c718d-109">Po uruchomieniu polecenia jest sprawdzenie zgodności, aby upewnić się, że pakiet jest zgodny z platform w projekcie.</span><span class="sxs-lookup"><span data-stu-id="c718d-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="c718d-110">Jeśli sprawdzenie zakończy się pomyślnie, `<PackageReference>` element zostanie dodany do pliku projektu i [przywracania dotnet](dotnet-restore.md) jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="c718d-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="c718d-111">Na przykład dodać `Newtonsoft.Json` do *ToDo.csproj* generuje dane wyjściowe podobne do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="c718d-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="c718d-112">*ToDo.csproj* plik zawiera teraz [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) elementu dla odpowiedniego pakietu.</span><span class="sxs-lookup"><span data-stu-id="c718d-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="c718d-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c718d-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="c718d-114">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="c718d-114">Specifies the project file.</span></span> <span data-ttu-id="c718d-115">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="c718d-115">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="c718d-116">Odwołania pakietu do dodania.</span><span class="sxs-lookup"><span data-stu-id="c718d-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="c718d-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="c718d-117">Options</span></span>

`-h|--help`

<span data-ttu-id="c718d-118">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="c718d-118">Prints out a short help for the command.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="c718d-119">Wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="c718d-119">Version of the package.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="c718d-120">Dodaje odwołanie do pakietu, tylko gdy jest określony [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c718d-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="c718d-121">Dodaje odwołanie do pakietu bez sprawdzanie przywracania Podgląd i zgodności.</span><span class="sxs-lookup"><span data-stu-id="c718d-121">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="c718d-122">Korzysta z określonego źródła pakietu NuGet podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="c718d-122">Uses a specific NuGet package source during the restore operation.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="c718d-123">Przywraca pakietu do określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="c718d-123">Restores the package to the specified directory.</span></span>

## <a name="examples"></a><span data-ttu-id="c718d-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c718d-124">Examples</span></span>

<span data-ttu-id="c718d-125">Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="c718d-125">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="c718d-126">Dodawanie określonej wersji pakietu do projektu:</span><span class="sxs-lookup"><span data-stu-id="c718d-126">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="c718d-127">Dodaj pakiet przy użyciu określonego źródła NuGet:</span><span class="sxs-lookup"><span data-stu-id="c718d-127">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
