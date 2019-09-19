---
title: polecenie dotnet Add Package
description: Polecenie "dotnet Add Package" udostępnia wygodną opcję dodawania odwołania do pakietu NuGet do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: 9445cf686ec1733f5a8b3403b7efea3a544fbc99
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117797"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="f0761-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="f0761-103">dotnet add package</span></span>

<span data-ttu-id="f0761-104">**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="f0761-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="f0761-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f0761-105">Name</span></span>

<span data-ttu-id="f0761-106">`dotnet add package`-Dodaje odwołanie do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="f0761-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f0761-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="f0761-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="f0761-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f0761-108">Description</span></span>

<span data-ttu-id="f0761-109">`dotnet add package` Polecenie udostępnia wygodną opcję dodawania odwołania do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="f0761-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="f0761-110">Po uruchomieniu polecenia jest sprawdzanie zgodności, aby upewnić się, że pakiet jest zgodny z strukturami w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f0761-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="f0761-111">Jeśli sprawdzanie przebiega, `<PackageReference>` element jest dodawany do pliku projektu i [dotnet Restore](dotnet-restore.md) jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="f0761-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="f0761-112">Na przykład dodanie `Newtonsoft.Json` do zadania do *zrobienia. csproj* generuje dane wyjściowe podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="f0761-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
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

<span data-ttu-id="f0761-113">Plik do *zrobienia. csproj* zawiera [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) teraz element dla przywoływanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="f0761-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="f0761-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f0761-114">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="f0761-115">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="f0761-115">Specifies the project file.</span></span> <span data-ttu-id="f0761-116">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="f0761-116">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="f0761-117">Odwołanie do pakietu do dodania.</span><span class="sxs-lookup"><span data-stu-id="f0761-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="f0761-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="f0761-118">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f0761-119">Dodaje odwołanie do pakietu tylko w przypadku określania konkretnej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f0761-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="f0761-120">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="f0761-120">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f0761-121">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="f0761-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="f0761-122">Dostępne od wersji .NET Core 2,1 SDK, wersja 2.1.400 lub nowsza.</span><span class="sxs-lookup"><span data-stu-id="f0761-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="f0761-123">Dodaje odwołanie do pakietu bez wykonywania podglądu przywracania i sprawdzania zgodności.</span><span class="sxs-lookup"><span data-stu-id="f0761-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="f0761-124">Katalog, w którym mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="f0761-124">The directory where to restore the packages.</span></span> <span data-ttu-id="f0761-125">Domyślna lokalizacja przywracania pakietu znajduje się `%userprofile%\.nuget\packages` w systemach Windows `~/.nuget/packages` i Linux.</span><span class="sxs-lookup"><span data-stu-id="f0761-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="f0761-126">Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w pakiecie NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="f0761-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="f0761-127">Źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="f0761-127">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="f0761-128">Wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="f0761-128">Version of the package.</span></span> <span data-ttu-id="f0761-129">Zobacz [przechowywanie wersji pakietów NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="f0761-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="f0761-130">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f0761-130">Examples</span></span>

- <span data-ttu-id="f0761-131">Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="f0761-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="f0761-132">Dodaj określoną wersję pakietu do projektu:</span><span class="sxs-lookup"><span data-stu-id="f0761-132">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="f0761-133">Dodaj pakiet przy użyciu określonego źródła NuGet:</span><span class="sxs-lookup"><span data-stu-id="f0761-133">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="f0761-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0761-134">See also</span></span>

- [<span data-ttu-id="f0761-135">Zarządzanie pakietami globalnymi, pamięcią podręczną i folderami tymczasowymi w pakiecie NuGet</span><span class="sxs-lookup"><span data-stu-id="f0761-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="f0761-136">Przechowywanie wersji pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="f0761-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
