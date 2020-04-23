---
title: dotnet dodaj pakiet, polecenie
description: Polecenie 'dotnet add package' zapewnia wygodną opcję dodawania odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 1d57aed59ccd45417c88f9b6a2f9dd768fda9b58
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102856"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="3780b-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="3780b-103">dotnet add package</span></span>

<span data-ttu-id="3780b-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="3780b-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3780b-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3780b-105">Name</span></span>

<span data-ttu-id="3780b-106">`dotnet add package`- Dodaje odwołanie do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3780b-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3780b-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3780b-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="3780b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="3780b-108">Description</span></span>

<span data-ttu-id="3780b-109">Polecenie `dotnet add package` zapewnia wygodną opcję dodawania odwołania do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3780b-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="3780b-110">Po uruchomieniu polecenia, istnieje sprawdzenie zgodności, aby upewnić się, że pakiet jest zgodny z platformami w projekcie.</span><span class="sxs-lookup"><span data-stu-id="3780b-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="3780b-111">Jeśli sprawdzanie przejdzie, `<PackageReference>` element jest dodawany do pliku projektu i [dotnet restore](dotnet-restore.md) jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="3780b-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="3780b-112">Na przykład `Newtonsoft.Json` dodanie do *pliku ToDo.csproj* tworzy dane wyjściowe podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="3780b-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="3780b-113">Plik *ToDo.csproj* zawiera [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) teraz element pakietu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="3780b-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="3780b-114">Niejawne przywracanie</span><span class="sxs-lookup"><span data-stu-id="3780b-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="3780b-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3780b-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="3780b-116">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="3780b-116">Specifies the project file.</span></span> <span data-ttu-id="3780b-117">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego.</span><span class="sxs-lookup"><span data-stu-id="3780b-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="3780b-118">Odwołanie do pakietu, aby dodać.</span><span class="sxs-lookup"><span data-stu-id="3780b-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="3780b-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="3780b-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="3780b-120">Dodaje odwołanie do pakietu tylko wtedy, gdy kierowanie określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="3780b-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="3780b-121">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3780b-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="3780b-122">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="3780b-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="3780b-123">Dostępne od .NET Core 2.1 SDK, wersja 2.1.400 lub nowsza.</span><span class="sxs-lookup"><span data-stu-id="3780b-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="3780b-124">Dodaje odwołanie do pakietu bez wykonywania sprawdzania podglądu przywracania i zgodności.</span><span class="sxs-lookup"><span data-stu-id="3780b-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="3780b-125">Katalog, w którym można przywrócić pakiety.</span><span class="sxs-lookup"><span data-stu-id="3780b-125">The directory where to restore the packages.</span></span> <span data-ttu-id="3780b-126">Domyślna lokalizacja przywracania pakietu jest `%userprofile%\.nuget\packages` w systemie Windows oraz `~/.nuget/packages` na komputerach macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="3780b-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="3780b-127">Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w nuget](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="3780b-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="3780b-128">Źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="3780b-128">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="3780b-129">Wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="3780b-129">Version of the package.</span></span> <span data-ttu-id="3780b-130">Zobacz [NuGet wersji pakietu](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="3780b-130">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="3780b-131">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3780b-131">Examples</span></span>

- <span data-ttu-id="3780b-132">Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="3780b-132">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="3780b-133">Dodawanie określonej wersji pakietu do projektu:</span><span class="sxs-lookup"><span data-stu-id="3780b-133">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="3780b-134">Dodaj pakiet przy użyciu określonego źródła NuGet:</span><span class="sxs-lookup"><span data-stu-id="3780b-134">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="3780b-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3780b-135">See also</span></span>

- [<span data-ttu-id="3780b-136">Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w nuget</span><span class="sxs-lookup"><span data-stu-id="3780b-136">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="3780b-137">Przechowywanie wersji pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="3780b-137">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
