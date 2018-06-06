---
title: DotNet Dodaj polecenie pakietu - .NET Core interfejsu wiersza polecenia
description: Polecenie "dotnet Dodawanie pakietu" zapewnia to wygodny sposób, aby dodać odwołanie pakiet NuGet do projektu.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 31dda9dbb101238b3a33d8b0d9a17765744480e0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696302"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="8384b-103">DotNet Dodaj pakiet</span><span class="sxs-lookup"><span data-stu-id="8384b-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8384b-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8384b-104">Name</span></span>

<span data-ttu-id="8384b-105">`dotnet add package` -Dodaje pakiet odwołanie do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="8384b-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8384b-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="8384b-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="8384b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8384b-107">Description</span></span>

<span data-ttu-id="8384b-108">`dotnet add package` Polecenie zapewnia to wygodny sposób, aby dodać pakiet odwołanie do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="8384b-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="8384b-109">Po uruchomieniu polecenia jest sprawdzenie zgodności, aby upewnić się, że pakiet jest zgodny z platform w projekcie.</span><span class="sxs-lookup"><span data-stu-id="8384b-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="8384b-110">Jeśli sprawdzenie zakończy się pomyślnie, `<PackageReference>` element zostanie dodany do pliku projektu i [przywracania dotnet](dotnet-restore.md) jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="8384b-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="8384b-111">Na przykład dodać `Newtonsoft.Json` do *ToDo.csproj* generuje dane wyjściowe podobne do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="8384b-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="8384b-112">*ToDo.csproj* plik zawiera teraz [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) elementu dla odpowiedniego pakietu.</span><span class="sxs-lookup"><span data-stu-id="8384b-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="8384b-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8384b-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="8384b-114">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="8384b-114">Specifies the project file.</span></span> <span data-ttu-id="8384b-115">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="8384b-115">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="8384b-116">Odwołania pakietu do dodania.</span><span class="sxs-lookup"><span data-stu-id="8384b-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="8384b-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="8384b-117">Options</span></span>

`-h|--help`

<span data-ttu-id="8384b-118">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="8384b-118">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="8384b-119">Dodaje odwołanie do pakietu, tylko gdy jest określony [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="8384b-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="8384b-120">Dodaje odwołanie do pakietu bez sprawdzanie przywracania Podgląd i zgodności.</span><span class="sxs-lookup"><span data-stu-id="8384b-120">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="8384b-121">Przywraca pakietu do określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="8384b-121">Restores the package to the specified directory.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="8384b-122">Korzysta z określonego źródła pakietu NuGet podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="8384b-122">Uses a specific NuGet package source during the restore operation.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="8384b-123">Wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="8384b-123">Version of the package.</span></span>

## <a name="examples"></a><span data-ttu-id="8384b-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8384b-124">Examples</span></span>

<span data-ttu-id="8384b-125">Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="8384b-125">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="8384b-126">Dodawanie określonej wersji pakietu do projektu:</span><span class="sxs-lookup"><span data-stu-id="8384b-126">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="8384b-127">Dodaj pakiet przy użyciu określonego źródła NuGet:</span><span class="sxs-lookup"><span data-stu-id="8384b-127">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
