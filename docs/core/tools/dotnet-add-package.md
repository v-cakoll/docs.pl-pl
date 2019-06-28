---
title: polecenia DotNet Dodaj pakiet — polecenie
description: Polecenie "dotnet Dodaj pakiet" zapewnia wygodny sposób, aby dodać odwołanie do pakietu NuGet do projektu.
ms.date: 06/26/2019
ms.openlocfilehash: f387d32cbf706e1711439e393c1a7811bc8f47bd
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422053"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="90561-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="90561-103">dotnet add package</span></span>

<span data-ttu-id="90561-104">**Ten artykuł dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="90561-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="90561-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="90561-105">Name</span></span>

<span data-ttu-id="90561-106">`dotnet add package` -Dodaje odwołania do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="90561-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="90561-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="90561-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="90561-108">Opis</span><span class="sxs-lookup"><span data-stu-id="90561-108">Description</span></span>

<span data-ttu-id="90561-109">`dotnet add package` Polecenia oferuje wygodne możliwość dodania odwołania do pakietu do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="90561-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="90561-110">Po uruchomieniu polecenia, istnieje sprawdzania zgodności w celu zapewnienia, że pakiet jest zgodna ze strukturami w projekcie.</span><span class="sxs-lookup"><span data-stu-id="90561-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="90561-111">Jeśli sprawdzenie zakończy się pomyślnie, `<PackageReference>` element zostanie dodany do pliku projektu i [dotnet restore](dotnet-restore.md) jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="90561-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="90561-112">Na przykład dodanie `Newtonsoft.Json` do *ToDo.csproj* generuje dane wyjściowe podobne do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="90561-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="90561-113">*ToDo.csproj* plik zawiera teraz [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) element dla odpowiedniego pakietu.</span><span class="sxs-lookup"><span data-stu-id="90561-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="90561-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="90561-114">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="90561-115">Określa plik projektu.</span><span class="sxs-lookup"><span data-stu-id="90561-115">Specifies the project file.</span></span> <span data-ttu-id="90561-116">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="90561-116">If not specified, the command searches the current directory for one.</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="90561-117">Odwołania pakietu do dodania.</span><span class="sxs-lookup"><span data-stu-id="90561-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="90561-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="90561-118">Options</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="90561-119">Dodaje odwołanie do pakietu tylko wtedy, gdy przeznaczonych dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="90561-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

* **`-h|--help`**

  <span data-ttu-id="90561-120">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="90561-120">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="90561-121">Umożliwia polecenie, aby zatrzymać i czeka na dane wejściowe użytkownika lub akcji (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="90561-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="90561-122">Dostępne od .NET Core SDK 2.1, wersja 2.1.400 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="90561-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

* **`-n|--no-restore`**

  <span data-ttu-id="90561-123">Dodaje odwołanie do pakietu bez sprawdzanie przywracania (wersja zapoznawcza) i zgodności.</span><span class="sxs-lookup"><span data-stu-id="90561-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

* **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="90561-124">Katalog miejsca w celu przywrócenia pakietów.</span><span class="sxs-lookup"><span data-stu-id="90561-124">The directory where to restore the packages.</span></span> <span data-ttu-id="90561-125">Domyślna lokalizacja przywracania pakietów `%userprofile%\.nuget\packages` na Windows i `~/.nuget/packages` w systemach macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="90561-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="90561-126">Aby uzyskać więcej informacji, zobacz [Zarządzanie globalnymi pakietami, pamięci podręcznej i folderów tymczasowych w programie NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="90561-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="90561-127">Źródło pakietu NuGet, która ma być używany podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="90561-127">The NuGet package source to use during the restore operation.</span></span>

* **`-v|--version <VERSION>`**

  <span data-ttu-id="90561-128">Wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="90561-128">Version of the package.</span></span> <span data-ttu-id="90561-129">Zobacz [przechowywanie wersji pakietów NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="90561-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="90561-130">Przykłady</span><span class="sxs-lookup"><span data-stu-id="90561-130">Examples</span></span>

* <span data-ttu-id="90561-131">Dodaj `Newtonsoft.Json` pakiet NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="90561-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```console
  dotnet add package Newtonsoft.Json
  ```

* <span data-ttu-id="90561-132">Dodaj określoną wersję pakietu do projektu:</span><span class="sxs-lookup"><span data-stu-id="90561-132">Add a specific version of a package to a project:</span></span>

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

* <span data-ttu-id="90561-133">Dodaj pakiet przy użyciu określonego źródła NuGet:</span><span class="sxs-lookup"><span data-stu-id="90561-133">Add a package using a specific NuGet source:</span></span>

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="90561-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90561-134">See also</span></span>

- [<span data-ttu-id="90561-135">Zarządzanie globalnymi pakietami, pamięci podręcznej i folderów tymczasowych w programie NuGet</span><span class="sxs-lookup"><span data-stu-id="90561-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="90561-136">Przechowywanie wersji pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="90561-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)