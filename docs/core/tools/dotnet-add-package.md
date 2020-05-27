---
title: polecenie dotnet Add Package
description: Polecenie "dotnet Add Package" udostępnia wygodną opcję dodawania odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: bc79fe8adf5f775ddce62f3877a8de945c6a18ab
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840900"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="2e1c5-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="2e1c5-103">dotnet add package</span></span>

<span data-ttu-id="2e1c5-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="2e1c5-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2e1c5-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2e1c5-105">Name</span></span>

<span data-ttu-id="2e1c5-106">`dotnet add package`-Dodaje odwołanie do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2e1c5-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2e1c5-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="2e1c5-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2e1c5-108">Description</span></span>

<span data-ttu-id="2e1c5-109">`dotnet add package`Polecenie udostępnia wygodną opcję dodawania odwołania do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="2e1c5-110">Po uruchomieniu polecenia jest sprawdzanie zgodności, aby upewnić się, że pakiet jest zgodny z strukturami w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="2e1c5-111">Jeśli sprawdzanie przebiega, `<PackageReference>` element jest dodawany do pliku projektu i [dotnet Restore](dotnet-restore.md) jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="2e1c5-112">Na przykład dodanie `Newtonsoft.Json` do zadania do *zrobienia. csproj* generuje dane wyjściowe podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="2e1c5-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="2e1c5-113">Plik do *zrobienia. csproj* zawiera teraz [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element dla przywoływanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="2e1c5-114">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="2e1c5-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="2e1c5-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2e1c5-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="2e1c5-116">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-116">Specifies the project file.</span></span> <span data-ttu-id="2e1c5-117">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="2e1c5-118">Odwołanie do pakietu do dodania.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="2e1c5-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="2e1c5-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2e1c5-120">Dodaje odwołanie do pakietu tylko w przypadku określania konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="2e1c5-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="2e1c5-121">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="2e1c5-122">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="2e1c5-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="2e1c5-123">Dostępne od wersji .NET Core 2,1 SDK, wersja 2.1.400 lub nowsza.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="2e1c5-124">Dodaje odwołanie do pakietu bez wykonywania podglądu przywracania i sprawdzania zgodności.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="2e1c5-125">Katalog, w którym mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-125">The directory where to restore the packages.</span></span> <span data-ttu-id="2e1c5-126">Domyślna lokalizacja przywracania pakietu znajduje się `%userprofile%\.nuget\packages` w systemach Windows i `~/.nuget/packages` Linux.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="2e1c5-127">Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w pakiecie NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="2e1c5-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="2e1c5-128">Identyfikator URI źródła pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-128">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="2e1c5-129">Wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e1c5-129">Version of the package.</span></span> <span data-ttu-id="2e1c5-130">Zobacz [przechowywanie wersji pakietów NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="2e1c5-130">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="2e1c5-131">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2e1c5-131">Examples</span></span>

- <span data-ttu-id="2e1c5-132">Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="2e1c5-132">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="2e1c5-133">Dodaj określoną wersję pakietu do projektu:</span><span class="sxs-lookup"><span data-stu-id="2e1c5-133">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="2e1c5-134">Dodaj pakiet przy użyciu określonego źródła NuGet:</span><span class="sxs-lookup"><span data-stu-id="2e1c5-134">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="2e1c5-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e1c5-135">See also</span></span>

- [<span data-ttu-id="2e1c5-136">Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w pakiecie NuGet</span><span class="sxs-lookup"><span data-stu-id="2e1c5-136">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="2e1c5-137">Przechowywanie wersji pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="2e1c5-137">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
