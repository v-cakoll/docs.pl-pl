---
title: polecenie przywracanie dotnet
description: Dowiedz się, jak przywrócić zależności i narzędzia specyficzne dla projektu za pomocą polecenia przywracania dotnet.
ms.date: 02/27/2020
ms.openlocfilehash: f49f0cda4424a4cc54ab7d4d4c6f729919dc7e60
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463429"
---
# <a name="dotnet-restore"></a><span data-ttu-id="9672e-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="9672e-103">dotnet restore</span></span>

<span data-ttu-id="9672e-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="9672e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9672e-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9672e-105">Name</span></span>

<span data-ttu-id="9672e-106">`dotnet restore`- Przywraca zależności i narzędzia projektu.</span><span class="sxs-lookup"><span data-stu-id="9672e-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9672e-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9672e-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="9672e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9672e-108">Description</span></span>

<span data-ttu-id="9672e-109">Polecenie `dotnet restore` używa NuGet do przywracania zależności, a także narzędzi specyficznych dla projektu, które są określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9672e-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="9672e-110">Domyślnie przywracanie zależności i narzędzia są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="9672e-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="9672e-111">Aby przywrócić zależności, NuGet potrzebuje źródeł danych, w których znajdują się pakiety.</span><span class="sxs-lookup"><span data-stu-id="9672e-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="9672e-112">Kanały informacyjne są zwykle dostarczane za pośrednictwem pliku konfiguracyjnego *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="9672e-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="9672e-113">Domyślny plik konfiguracyjny jest dostarczany po zainstalowaniu narzędzia .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9672e-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="9672e-114">Dodatkowe źródła danych można określić, tworząc własny plik *nuget.config* w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="9672e-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="9672e-115">Można zastąpić *nuget.config* kanałów z - `-s` opcja.</span><span class="sxs-lookup"><span data-stu-id="9672e-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="9672e-116">Dla zależności należy określić, gdzie przywrócone pakiety są `--packages` umieszczane podczas operacji przywracania przy użyciu argumentu.</span><span class="sxs-lookup"><span data-stu-id="9672e-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="9672e-117">Jeśli nie zostanie określony, używana jest domyślna pamięć `.nuget/packages` podręczna pakietów NuGet, która znajduje się w katalogu w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="9672e-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="9672e-118">Na przykład */home/user1* w systemie Linux lub *C:\Users\user1* w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="9672e-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="9672e-119">W przypadku narzędzi specyficznych dla projektu najpierw przywraca pakiet, `dotnet restore` w którym narzędzie jest spakowane, a następnie przechodzi do przywracania zależności narzędzia, jak określono w jego pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9672e-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="9672e-120">różnice nuget.config</span><span class="sxs-lookup"><span data-stu-id="9672e-120">nuget.config differences</span></span>

<span data-ttu-id="9672e-121">Na zachowanie `dotnet restore` polecenia mają wpływ ustawienia w pliku *nuget.config,* jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="9672e-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="9672e-122">Na przykład ustawienie `globalPackagesFolder` w *nuget.config* umieszcza przywrócone pakiety NuGet w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="9672e-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="9672e-123">Jest to alternatywa dla `--packages` określenia `dotnet restore` opcji w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="9672e-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="9672e-124">Aby uzyskać więcej informacji, zobacz [nuget.config reference](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="9672e-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="9672e-125">Istnieją trzy określone `dotnet restore` ustawienia, które ignorują:</span><span class="sxs-lookup"><span data-stu-id="9672e-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="9672e-126">bindingRedirects (przekierowanie)</span><span class="sxs-lookup"><span data-stu-id="9672e-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="9672e-127">Przekierowania powiązania nie działają `<PackageReference>` z elementami, `<PackageReference>` a program .NET Core obsługuje tylko elementy dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="9672e-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="9672e-128">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="9672e-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="9672e-129">To ustawienie jest specyficzne dla programu Visual Studio i nie dotyczy programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9672e-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="9672e-130">.NET Core nie używa `packages.config` pliku i zamiast `<PackageReference>` tego używa elementów dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="9672e-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="9672e-131">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="9672e-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="9672e-132">To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji zaufanych](https://github.com/NuGet/Home/issues/7939) pakietów na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="9672e-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="9672e-133">Niejawne przywracanie</span><span class="sxs-lookup"><span data-stu-id="9672e-133">Implicit restore</span></span>

<span data-ttu-id="9672e-134">Polecenie `dotnet restore` jest uruchamiane niejawnie, jeśli to konieczne po uruchomieniu następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="9672e-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="9672e-135">W większości przypadków nie trzeba jawnie używać `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="9672e-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="9672e-136">Czasami może być niewygodne do uruchomienia `dotnet restore` niejawnie.</span><span class="sxs-lookup"><span data-stu-id="9672e-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="9672e-137">Na przykład niektóre zautomatyzowane systemy, takie jak `dotnet restore` systemy kompilacji, muszą jawnie wywoływać, aby kontrolować, kiedy nastąpi przywracanie, aby mogły kontrolować użycie sieci.</span><span class="sxs-lookup"><span data-stu-id="9672e-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="9672e-138">Aby `dotnet restore` zapobiec niejawnie, można `--no-restore` użyć flagi z dowolnym z tych poleceń, aby wyłączyć niejawne przywracanie.</span><span class="sxs-lookup"><span data-stu-id="9672e-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="9672e-139">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9672e-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="9672e-140">Opcjonalna ścieżka do pliku projektu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="9672e-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="9672e-141">Opcje</span><span class="sxs-lookup"><span data-stu-id="9672e-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="9672e-142">Plik konfiguracyjny NuGet (*nuget.config*) do użycia w operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="9672e-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="9672e-143">Wyłącza przywracanie wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="9672e-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="9672e-144">Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9672e-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9672e-145">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="9672e-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="9672e-146">Wymusza przywracanie, aby ponownie ocenić wszystkie zależności, nawet jeśli plik blokady już istnieje.</span><span class="sxs-lookup"><span data-stu-id="9672e-146">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9672e-147">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9672e-147">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="9672e-148">O nieudanych źródłach należy tylko ostrzec, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="9672e-148">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="9672e-149">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="9672e-149">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="9672e-150">Od .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="9672e-150">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="9672e-151">Lokalizacja wyjściowa, w której zapisywany jest plik blokady projektu.</span><span class="sxs-lookup"><span data-stu-id="9672e-151">Output location where project lock file is written.</span></span> <span data-ttu-id="9672e-152">Domyślnie jest to *PROJECT_ROOT\packages.lock.json*.</span><span class="sxs-lookup"><span data-stu-id="9672e-152">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="9672e-153">Nie zezwalaj na aktualizowanie pliku blokady projektu.</span><span class="sxs-lookup"><span data-stu-id="9672e-153">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="9672e-154">Określa, że nie ma buforowania pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="9672e-154">Specifies to not cache packages and HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="9672e-155">Podczas przywracania projektu z odwołaniami do projektu do projektu (P2P), przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="9672e-155">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="9672e-156">Określa katalog przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="9672e-156">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="9672e-157">Określa środowisko uruchomieniowe przywracania pakietu.</span><span class="sxs-lookup"><span data-stu-id="9672e-157">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="9672e-158">Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są jawnie wymienione w tagu `<RuntimeIdentifiers>` w pliku *csproj.*</span><span class="sxs-lookup"><span data-stu-id="9672e-158">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="9672e-159">Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9672e-159">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9672e-160">Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="9672e-160">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="9672e-161">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="9672e-161">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="9672e-162">To ustawienie zastępuje wszystkie źródła określone w plikach *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="9672e-162">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="9672e-163">Wiele źródeł można podać, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="9672e-163">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="9672e-164">Umożliwia generowanie i używane go z przywracania pliku blokady projektu.</span><span class="sxs-lookup"><span data-stu-id="9672e-164">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9672e-165">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="9672e-165">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9672e-166">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="9672e-166">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9672e-167">Wartością `minimal`domyślną jest .</span><span class="sxs-lookup"><span data-stu-id="9672e-167">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="9672e-168">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9672e-168">Examples</span></span>

- <span data-ttu-id="9672e-169">Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="9672e-169">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="9672e-170">Przywróć zależności `app1` i narzędzia dla projektu znajdującego się w danej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="9672e-170">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="9672e-171">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu ścieżki pliku podanej jako źródło:</span><span class="sxs-lookup"><span data-stu-id="9672e-171">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="9672e-172">Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu przy użyciu dwóch ścieżek plików dostarczonych jako źródła:</span><span class="sxs-lookup"><span data-stu-id="9672e-172">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="9672e-173">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przedstawiającym szczegółowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="9672e-173">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
