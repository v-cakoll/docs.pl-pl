---
title: dotnet dodaj pakiet, polecenie
description: Polecenie 'dotnet add package' zapewnia wygodną opcję dodawania odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 24a25cdab2aab30d52f8407adfda437f47437290
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463753"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="807ca-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="807ca-103">dotnet add package</span></span>

<span data-ttu-id="807ca-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="807ca-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="807ca-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="807ca-105">Name</span></span>

<span data-ttu-id="807ca-106">`dotnet add package`- Dodaje odwołanie do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="807ca-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="807ca-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="807ca-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="807ca-108">Opis</span><span class="sxs-lookup"><span data-stu-id="807ca-108">Description</span></span>

<span data-ttu-id="807ca-109">Polecenie `dotnet add package` zapewnia wygodną opcję dodawania odwołania do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="807ca-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="807ca-110">Po uruchomieniu polecenia, istnieje sprawdzenie zgodności, aby upewnić się, że pakiet jest zgodny z platformami w projekcie.</span><span class="sxs-lookup"><span data-stu-id="807ca-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="807ca-111">Jeśli sprawdzanie przejdzie, `<PackageReference>` element jest dodawany do pliku projektu i [dotnet restore](dotnet-restore.md) jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="807ca-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="807ca-112">Na przykład `Newtonsoft.Json` dodanie do *pliku ToDo.csproj* tworzy dane wyjściowe podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="807ca-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="807ca-113">Plik *ToDo.csproj* zawiera [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) teraz element pakietu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="807ca-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="807ca-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="807ca-114">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="807ca-115">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="807ca-115">Specifies the project file.</span></span> <span data-ttu-id="807ca-116">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla jednego.</span><span class="sxs-lookup"><span data-stu-id="807ca-116">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="807ca-117">Odwołanie do pakietu, aby dodać.</span><span class="sxs-lookup"><span data-stu-id="807ca-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="807ca-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="807ca-118">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="807ca-119">Dodaje odwołanie do pakietu tylko wtedy, gdy kierowanie określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="807ca-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="807ca-120">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="807ca-120">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="807ca-121">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="807ca-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="807ca-122">Dostępne od .NET Core 2.1 SDK, wersja 2.1.400 lub nowsza.</span><span class="sxs-lookup"><span data-stu-id="807ca-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="807ca-123">Dodaje odwołanie do pakietu bez wykonywania sprawdzania podglądu przywracania i zgodności.</span><span class="sxs-lookup"><span data-stu-id="807ca-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="807ca-124">Katalog, w którym można przywrócić pakiety.</span><span class="sxs-lookup"><span data-stu-id="807ca-124">The directory where to restore the packages.</span></span> <span data-ttu-id="807ca-125">Domyślna lokalizacja przywracania pakietu jest `%userprofile%\.nuget\packages` w systemie Windows oraz `~/.nuget/packages` na komputerach macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="807ca-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="807ca-126">Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w nuget](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="807ca-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="807ca-127">Źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="807ca-127">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="807ca-128">Wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="807ca-128">Version of the package.</span></span> <span data-ttu-id="807ca-129">Zobacz [NuGet wersji pakietu](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="807ca-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="807ca-130">Przykłady</span><span class="sxs-lookup"><span data-stu-id="807ca-130">Examples</span></span>

- <span data-ttu-id="807ca-131">Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="807ca-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="807ca-132">Dodawanie określonej wersji pakietu do projektu:</span><span class="sxs-lookup"><span data-stu-id="807ca-132">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="807ca-133">Dodaj pakiet przy użyciu określonego źródła NuGet:</span><span class="sxs-lookup"><span data-stu-id="807ca-133">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="807ca-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="807ca-134">See also</span></span>

- [<span data-ttu-id="807ca-135">Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w nuget</span><span class="sxs-lookup"><span data-stu-id="807ca-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="807ca-136">Przechowywanie wersji pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="807ca-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
