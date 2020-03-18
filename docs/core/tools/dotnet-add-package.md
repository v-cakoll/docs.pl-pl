---
title: polecenie dotnet add package
description: Polecenie "dotnet add package" zapewnia wygodną opcję dodawania odwołania do pakietu NuGet do projektu.
ms.date: 02/14/2020
ms.openlocfilehash: 8121539a50d2ac2837693ccc35581f7fde1d1fc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146609"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="e9d53-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="e9d53-103">dotnet add package</span></span>

<span data-ttu-id="e9d53-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="e9d53-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e9d53-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e9d53-105">Name</span></span>

<span data-ttu-id="e9d53-106">`dotnet add package`- Dodaje odwołanie do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e9d53-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e9d53-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e9d53-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="e9d53-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e9d53-108">Description</span></span>

<span data-ttu-id="e9d53-109">Polecenie `dotnet add package` zapewnia wygodną opcję dodawania odwołania do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e9d53-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="e9d53-110">Po uruchomieniu polecenia, jest sprawdzenie zgodności, aby upewnić się, że pakiet jest zgodny z ramach w projekcie.</span><span class="sxs-lookup"><span data-stu-id="e9d53-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="e9d53-111">Jeśli sprawdzanie przejdzie `<PackageReference>` pomyślnie, element jest dodawany do pliku projektu i uruchamiane jest [przywracanie dotnet.](dotnet-restore.md)</span><span class="sxs-lookup"><span data-stu-id="e9d53-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="e9d53-112">Na przykład `Newtonsoft.Json` dodanie do *ToDo.csproj* daje dane wyjściowe podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="e9d53-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="e9d53-113">Plik *ToDo.csproj* zawiera [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) teraz element pakietu, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="e9d53-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="e9d53-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e9d53-114">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="e9d53-115">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="e9d53-115">Specifies the project file.</span></span> <span data-ttu-id="e9d53-116">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu jednego.</span><span class="sxs-lookup"><span data-stu-id="e9d53-116">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="e9d53-117">Odwołanie do pakietu, aby dodać.</span><span class="sxs-lookup"><span data-stu-id="e9d53-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="e9d53-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="e9d53-118">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e9d53-119">Dodaje odwołanie do pakietu tylko podczas określania określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e9d53-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="e9d53-120">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e9d53-120">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="e9d53-121">Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie).</span><span class="sxs-lookup"><span data-stu-id="e9d53-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="e9d53-122">Dostępne od sdk .NET Core 2.1, wersja 2.1.400 lub nowsza.</span><span class="sxs-lookup"><span data-stu-id="e9d53-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="e9d53-123">Dodaje odwołanie do pakietu bez wykonywania podglądu przywracania i sprawdzania zgodności.</span><span class="sxs-lookup"><span data-stu-id="e9d53-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="e9d53-124">Katalog, w którym należy przywrócić pakiety.</span><span class="sxs-lookup"><span data-stu-id="e9d53-124">The directory where to restore the packages.</span></span> <span data-ttu-id="e9d53-125">Domyślna lokalizacja przywracania pakietów znajduje się `%userprofile%\.nuget\packages` w systemie Windows oraz `~/.nuget/packages` w systemach macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="e9d53-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="e9d53-126">Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowych w nuget](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="e9d53-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="e9d53-127">Źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="e9d53-127">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="e9d53-128">Wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="e9d53-128">Version of the package.</span></span> <span data-ttu-id="e9d53-129">Zobacz [NuGet przechowywanie wersji pakietu](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="e9d53-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="e9d53-130">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e9d53-130">Examples</span></span>

- <span data-ttu-id="e9d53-131">Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="e9d53-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="e9d53-132">Dodaj określoną wersję pakietu do projektu:</span><span class="sxs-lookup"><span data-stu-id="e9d53-132">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="e9d53-133">Dodaj pakiet przy użyciu określonego źródła NuGet:</span><span class="sxs-lookup"><span data-stu-id="e9d53-133">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="e9d53-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9d53-134">See also</span></span>

- [<span data-ttu-id="e9d53-135">Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowych w NuGet</span><span class="sxs-lookup"><span data-stu-id="e9d53-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="e9d53-136">Przechowywanie wersji pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="e9d53-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
