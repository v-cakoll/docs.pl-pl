---
title: polecenie dotnet restore
description: Informacje o sposobie przywracania zależności i narzędzi specyficznych dla projektu przy użyciu polecenia dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: 29f81b09a01e689d3f6d86c16b1f134c9fe6b6a0
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840939"
---
# <a name="dotnet-restore"></a><span data-ttu-id="a07b7-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a07b7-103">dotnet restore</span></span>

<span data-ttu-id="a07b7-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="a07b7-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a07b7-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a07b7-105">Name</span></span>

<span data-ttu-id="a07b7-106">`dotnet restore`— Przywraca zależności i narzędzia projektu.</span><span class="sxs-lookup"><span data-stu-id="a07b7-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a07b7-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a07b7-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="a07b7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a07b7-108">Description</span></span>

<span data-ttu-id="a07b7-109">`dotnet restore`Polecenie używa narzędzia NuGet do przywracania zależności oraz narzędzi specyficznych dla projektu, które są określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a07b7-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span>  <span data-ttu-id="a07b7-110">W większości przypadków nie trzeba jawnie używać `dotnet restore` polecenia, ponieważ przywracanie NuGet jest uruchamiane niejawnie w razie potrzeby podczas uruchamiania następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="a07b7-110">In most cases, you don't need to explicitly use the `dotnet restore` command, since a NuGet restore is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="a07b7-111">Czasami może być niewygodne uruchamianie niejawnego przywracania NuGet przy użyciu tych poleceń.</span><span class="sxs-lookup"><span data-stu-id="a07b7-111">Sometimes, it might be inconvenient to run the implicit NuGet restore with these commands.</span></span> <span data-ttu-id="a07b7-112">Na przykład niektóre zautomatyzowane systemy, takie jak systemy kompilacji, muszą jawnie wywołać, `dotnet restore` Aby określić, kiedy następuje przywracanie, aby można było kontrolować użycie sieci.</span><span class="sxs-lookup"><span data-stu-id="a07b7-112">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="a07b7-113">Aby zapobiec niejawnemu przywracaniu NuGet, można użyć `--no-restore` flagi z dowolnym z tych poleceń, aby wyłączyć Przywracanie niejawne.</span><span class="sxs-lookup"><span data-stu-id="a07b7-113">To prevent the implicit NuGet restore, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="a07b7-114">Określ źródła danych</span><span class="sxs-lookup"><span data-stu-id="a07b7-114">Specify feeds</span></span>

<span data-ttu-id="a07b7-115">Aby przywrócić zależności, program NuGet potrzebuje kanałów informacyjnych, w których znajdują się pakiety.</span><span class="sxs-lookup"><span data-stu-id="a07b7-115">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="a07b7-116">Kanały informacyjne są zazwyczaj udostępniane za pośrednictwem pliku konfiguracyjnego *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="a07b7-116">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="a07b7-117">Domyślny plik konfiguracji jest dostarczany, gdy zainstalowano zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a07b7-117">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="a07b7-118">Aby określić dodatkowe źródła danych, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a07b7-118">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="a07b7-119">Utwórz własny plik *NuGet. config* w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="a07b7-119">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="a07b7-120">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](/nuget/consume-packages/configuring-nuget-behavior) i [NuGet. config różnice](#nugetconfig-differences) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="a07b7-120">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="a07b7-121">Użyj `dotnet nuget` poleceń, takich jak [`dotnet nuget add source`](dotnet-nuget-add-source.md) .</span><span class="sxs-lookup"><span data-stu-id="a07b7-121">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="a07b7-122">Można zastąpić źródła danych *NuGet. config* `-s` opcją.</span><span class="sxs-lookup"><span data-stu-id="a07b7-122">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="a07b7-123">Informacje o sposobach korzystania z uwierzytelnionych źródeł danych znajdują się w temacie Używanie [pakietów z uwierzytelnionych kanałów informacyjnych](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span><span class="sxs-lookup"><span data-stu-id="a07b7-123">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="global-packages-folder"></a><span data-ttu-id="a07b7-124">Folder pakietów globalnych</span><span class="sxs-lookup"><span data-stu-id="a07b7-124">Global packages folder</span></span>

<span data-ttu-id="a07b7-125">W przypadku zależności można określić miejsce, w którym przywrócone pakiety są umieszczane podczas operacji przywracania przy użyciu `--packages` argumentu.</span><span class="sxs-lookup"><span data-stu-id="a07b7-125">For dependencies, you can specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="a07b7-126">Jeśli nie zostanie określony, zostanie użyta domyślna pamięć podręczna pakietów NuGet, która znajduje się w katalogu `.nuget/packages` w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="a07b7-126">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="a07b7-127">Na przykład */home/user1* na system Linux lub *C:\Users\user1* w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="a07b7-127">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="a07b7-128">Narzędzia specyficzne dla projektu</span><span class="sxs-lookup"><span data-stu-id="a07b7-128">Project-specific tooling</span></span>

<span data-ttu-id="a07b7-129">W przypadku narzędzi specyficznych dla projektu program `dotnet restore` najpierw przywraca pakiet, w którym narzędzie jest spakowane, a następnie przechodzi do przywracania zależności narzędzia, jak określono w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a07b7-129">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="a07b7-130">różnice NuGet. config</span><span class="sxs-lookup"><span data-stu-id="a07b7-130">nuget.config differences</span></span>

<span data-ttu-id="a07b7-131">Zachowanie `dotnet restore` polecenia ma wpływ na ustawienia w pliku *NuGet. config* , jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="a07b7-131">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="a07b7-132">Na przykład ustawienie `globalPackagesFolder` w *pliku NuGet. config* powoduje umieszczenie przywróconych pakietów NuGet w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="a07b7-132">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="a07b7-133">Jest to alternatywa dla określenia `--packages` opcji `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="a07b7-133">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="a07b7-134">Aby uzyskać więcej informacji, zobacz [Dokumentacja NuGet. config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="a07b7-134">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="a07b7-135">Istnieją trzy określone ustawienia, które `dotnet restore` ignorują:</span><span class="sxs-lookup"><span data-stu-id="a07b7-135">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="a07b7-136">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="a07b7-136">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="a07b7-137">Przekierowania powiązań nie działają z `<PackageReference>` elementami i .NET Core obsługuje tylko `<PackageReference>` elementy dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="a07b7-137">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="a07b7-138">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="a07b7-138">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="a07b7-139">To ustawienie dotyczy programu Visual Studio i nie ma zastosowania do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a07b7-139">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="a07b7-140">Platforma .NET Core nie używa `packages.config` pliku, a zamiast tego używa `<PackageReference>` elementów dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="a07b7-140">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="a07b7-141">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="a07b7-141">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="a07b7-142">To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji](https://github.com/NuGet/Home/issues/7939) zaufanych pakietów przez wiele platform.</span><span class="sxs-lookup"><span data-stu-id="a07b7-142">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="arguments"></a><span data-ttu-id="a07b7-143">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a07b7-143">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="a07b7-144">Opcjonalna ścieżka do pliku projektu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="a07b7-144">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="a07b7-145">Opcje</span><span class="sxs-lookup"><span data-stu-id="a07b7-145">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="a07b7-146">Plik konfiguracji NuGet (*NuGet. config*) do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="a07b7-146">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="a07b7-147">Wyłącza przywracanie równolegle wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="a07b7-147">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="a07b7-148">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a07b7-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a07b7-149">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="a07b7-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="a07b7-150">Wymusza przywrócenie przez Przywracanie wszystkich zależności, nawet jeśli plik blokady już istnieje.</span><span class="sxs-lookup"><span data-stu-id="a07b7-150">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a07b7-151">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a07b7-151">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="a07b7-152">Ostrzegaj o nieudanych źródłach, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="a07b7-152">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="a07b7-153">Umożliwia zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład zakończenie uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="a07b7-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="a07b7-154">Od programu .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="a07b7-154">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="a07b7-155">Lokalizacja wyjściowa, w której jest zapisywana plik blokady projektu.</span><span class="sxs-lookup"><span data-stu-id="a07b7-155">Output location where project lock file is written.</span></span> <span data-ttu-id="a07b7-156">Domyślnie jest to *PROJECT_ROOT \packages.Lock.JSON*.</span><span class="sxs-lookup"><span data-stu-id="a07b7-156">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="a07b7-157">Nie Zezwalaj na aktualizowanie pliku blokady projektu.</span><span class="sxs-lookup"><span data-stu-id="a07b7-157">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="a07b7-158">Określa, że nie mają być buforowane żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="a07b7-158">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="a07b7-159">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="a07b7-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="a07b7-160">Określa katalog przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="a07b7-160">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="a07b7-161">Określa środowisko uruchomieniowe przywracania pakietu.</span><span class="sxs-lookup"><span data-stu-id="a07b7-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="a07b7-162">Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są jawnie wymienione w `<RuntimeIdentifiers>` tagu w pliku *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="a07b7-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="a07b7-163">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a07b7-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="a07b7-164">Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="a07b7-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="a07b7-165">Określa identyfikator URI źródła pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="a07b7-165">Specifies the URI of the NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="a07b7-166">To ustawienie zastępuje wszystkie źródła określone w plikach *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="a07b7-166">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="a07b7-167">Można podać wiele źródeł, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="a07b7-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="a07b7-168">Umożliwia generowanie i używanie pliku blokady projektu z przywracaniem.</span><span class="sxs-lookup"><span data-stu-id="a07b7-168">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a07b7-169">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a07b7-169">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a07b7-170">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="a07b7-170">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a07b7-171">Wartość domyślna to `minimal` .</span><span class="sxs-lookup"><span data-stu-id="a07b7-171">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="a07b7-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a07b7-172">Examples</span></span>

- <span data-ttu-id="a07b7-173">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a07b7-173">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="a07b7-174">Przywróć zależności i narzędzia dla `app1` projektu Znalezione w danej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="a07b7-174">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="a07b7-175">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu ścieżki pliku dostarczonej jako Źródło:</span><span class="sxs-lookup"><span data-stu-id="a07b7-175">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="a07b7-176">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu dwóch ścieżek plików dostarczonych jako źródła:</span><span class="sxs-lookup"><span data-stu-id="a07b7-176">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="a07b7-177">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przedstawiające szczegółowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a07b7-177">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
