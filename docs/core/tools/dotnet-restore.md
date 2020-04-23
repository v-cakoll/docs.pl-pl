---
title: polecenie przywracanie dotnet
description: Dowiedz się, jak przywrócić zależności i narzędzia specyficzne dla projektu za pomocą polecenia przywracania dotnet.
ms.date: 02/27/2020
ms.openlocfilehash: 3deef68a9bcee389a52291c72e7e1a1019a739fd
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102791"
---
# <a name="dotnet-restore"></a><span data-ttu-id="f7644-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="f7644-103">dotnet restore</span></span>

<span data-ttu-id="f7644-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="f7644-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f7644-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f7644-105">Name</span></span>

<span data-ttu-id="f7644-106">`dotnet restore`- Przywraca zależności i narzędzia projektu.</span><span class="sxs-lookup"><span data-stu-id="f7644-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f7644-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="f7644-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="f7644-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f7644-108">Description</span></span>

<span data-ttu-id="f7644-109">Polecenie `dotnet restore` używa NuGet do przywracania zależności, a także narzędzi specyficznych dla projektu, które są określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="f7644-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="f7644-110">Domyślnie przywracanie zależności i narzędzia są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="f7644-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="f7644-111">Określanie kanałów informacyjnych</span><span class="sxs-lookup"><span data-stu-id="f7644-111">Specify feeds</span></span>

<span data-ttu-id="f7644-112">Aby przywrócić zależności, NuGet potrzebuje źródeł danych, w których znajdują się pakiety.</span><span class="sxs-lookup"><span data-stu-id="f7644-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="f7644-113">Kanały informacyjne są zwykle dostarczane za pośrednictwem pliku konfiguracyjnego *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="f7644-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="f7644-114">Domyślny plik konfiguracyjny jest dostarczany po zainstalowaniu narzędzia .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f7644-114">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="f7644-115">Aby określić dodatkowe źródła danych, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f7644-115">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="f7644-116">Utwórz własny plik *nuget.config* w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="f7644-116">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="f7644-117">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](/nuget/consume-packages/configuring-nuget-behavior) i [nuget.config różnice](#nugetconfig-differences) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="f7644-117">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="f7644-118">Użyj `dotnet nuget` poleceń, [`dotnet nuget add source`](dotnet-nuget-add-source.md)takich jak .</span><span class="sxs-lookup"><span data-stu-id="f7644-118">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="f7644-119">Można zastąpić *nuget.config* kanałów z `-s` opcją.</span><span class="sxs-lookup"><span data-stu-id="f7644-119">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="f7644-120">Aby uzyskać informacje dotyczące używania uwierzytelnionych kanałów informacyjnych, zobacz [Korzystanie z pakietów z uwierzytelnionych kanałów informacyjnych](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span><span class="sxs-lookup"><span data-stu-id="f7644-120">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="package-cache"></a><span data-ttu-id="f7644-121">Pamięć podręczna pakietów</span><span class="sxs-lookup"><span data-stu-id="f7644-121">Package cache</span></span>

<span data-ttu-id="f7644-122">Dla zależności należy określić, gdzie przywrócone pakiety są `--packages` umieszczane podczas operacji przywracania przy użyciu argumentu.</span><span class="sxs-lookup"><span data-stu-id="f7644-122">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="f7644-123">Jeśli nie zostanie określony, używana jest domyślna pamięć `.nuget/packages` podręczna pakietów NuGet, która znajduje się w katalogu w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="f7644-123">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="f7644-124">Na przykład */home/user1* w systemie Linux lub *C:\Users\user1* w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="f7644-124">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="f7644-125">Narzędzia specyficzne dla projektu</span><span class="sxs-lookup"><span data-stu-id="f7644-125">Project-specific tooling</span></span>

<span data-ttu-id="f7644-126">W przypadku narzędzi specyficznych dla projektu najpierw przywraca pakiet, `dotnet restore` w którym narzędzie jest spakowane, a następnie przechodzi do przywracania zależności narzędzia, jak określono w jego pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="f7644-126">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="f7644-127">różnice nuget.config</span><span class="sxs-lookup"><span data-stu-id="f7644-127">nuget.config differences</span></span>

<span data-ttu-id="f7644-128">Na zachowanie `dotnet restore` polecenia mają wpływ ustawienia w pliku *nuget.config,* jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="f7644-128">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="f7644-129">Na przykład ustawienie `globalPackagesFolder` w *nuget.config* umieszcza przywrócone pakiety NuGet w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="f7644-129">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="f7644-130">Jest to alternatywa dla `--packages` określenia `dotnet restore` opcji w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="f7644-130">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="f7644-131">Aby uzyskać więcej informacji, zobacz [nuget.config reference](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="f7644-131">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="f7644-132">Istnieją trzy określone `dotnet restore` ustawienia, które ignorują:</span><span class="sxs-lookup"><span data-stu-id="f7644-132">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="f7644-133">bindingRedirects (przekierowanie)</span><span class="sxs-lookup"><span data-stu-id="f7644-133">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="f7644-134">Przekierowania powiązania nie działają `<PackageReference>` z elementami, `<PackageReference>` a program .NET Core obsługuje tylko elementy dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="f7644-134">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="f7644-135">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f7644-135">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="f7644-136">To ustawienie jest specyficzne dla programu Visual Studio i nie dotyczy programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f7644-136">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="f7644-137">.NET Core nie używa `packages.config` pliku i zamiast `<PackageReference>` tego używa elementów dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="f7644-137">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="f7644-138">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="f7644-138">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="f7644-139">To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji zaufanych](https://github.com/NuGet/Home/issues/7939) pakietów na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="f7644-139">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="f7644-140">Niejawne przywracanie</span><span class="sxs-lookup"><span data-stu-id="f7644-140">Implicit restore</span></span>

<span data-ttu-id="f7644-141">Polecenie `dotnet restore` jest uruchamiane niejawnie, jeśli to konieczne po uruchomieniu następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="f7644-141">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="f7644-142">W większości przypadków nie trzeba jawnie używać `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="f7644-142">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="f7644-143">Czasami może być niewygodne do uruchomienia `dotnet restore` niejawnie.</span><span class="sxs-lookup"><span data-stu-id="f7644-143">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="f7644-144">Na przykład niektóre zautomatyzowane systemy, takie jak `dotnet restore` systemy kompilacji, muszą jawnie wywoływać, aby kontrolować, kiedy nastąpi przywracanie, aby mogły kontrolować użycie sieci.</span><span class="sxs-lookup"><span data-stu-id="f7644-144">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="f7644-145">Aby `dotnet restore` zapobiec niejawnie, można `--no-restore` użyć flagi z dowolnym z tych poleceń, aby wyłączyć niejawne przywracanie.</span><span class="sxs-lookup"><span data-stu-id="f7644-145">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="f7644-146">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f7644-146">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="f7644-147">Opcjonalna ścieżka do pliku projektu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="f7644-147">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="f7644-148">Opcje</span><span class="sxs-lookup"><span data-stu-id="f7644-148">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f7644-149">Plik konfiguracyjny NuGet (*nuget.config*) do użycia w operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="f7644-149">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="f7644-150">Wyłącza przywracanie wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="f7644-150">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="f7644-151">Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f7644-151">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="f7644-152">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="f7644-152">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="f7644-153">Wymusza przywracanie, aby ponownie ocenić wszystkie zależności, nawet jeśli plik blokady już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f7644-153">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f7644-154">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="f7644-154">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="f7644-155">O nieudanych źródłach należy tylko ostrzec, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="f7644-155">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="f7644-156">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="f7644-156">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="f7644-157">Od .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="f7644-157">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="f7644-158">Lokalizacja wyjściowa, w której zapisywany jest plik blokady projektu.</span><span class="sxs-lookup"><span data-stu-id="f7644-158">Output location where project lock file is written.</span></span> <span data-ttu-id="f7644-159">Domyślnie jest to *PROJECT_ROOT\packages.lock.json*.</span><span class="sxs-lookup"><span data-stu-id="f7644-159">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="f7644-160">Nie zezwalaj na aktualizowanie pliku blokady projektu.</span><span class="sxs-lookup"><span data-stu-id="f7644-160">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="f7644-161">Określa, że nie buforuje żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7644-161">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="f7644-162">Podczas przywracania projektu z odwołaniami do projektu do projektu (P2P), przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="f7644-162">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="f7644-163">Określa katalog przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="f7644-163">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f7644-164">Określa środowisko uruchomieniowe przywracania pakietu.</span><span class="sxs-lookup"><span data-stu-id="f7644-164">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="f7644-165">Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są jawnie wymienione w tagu `<RuntimeIdentifiers>` w pliku *csproj.*</span><span class="sxs-lookup"><span data-stu-id="f7644-165">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="f7644-166">Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="f7644-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="f7644-167">Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="f7644-167">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="f7644-168">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="f7644-168">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="f7644-169">To ustawienie zastępuje wszystkie źródła określone w plikach *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="f7644-169">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="f7644-170">Wiele źródeł można podać, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="f7644-170">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="f7644-171">Umożliwia generowanie i używane go z przywracania pliku blokady projektu.</span><span class="sxs-lookup"><span data-stu-id="f7644-171">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f7644-172">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="f7644-172">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f7644-173">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="f7644-173">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f7644-174">Wartością `minimal`domyślną jest .</span><span class="sxs-lookup"><span data-stu-id="f7644-174">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="f7644-175">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f7644-175">Examples</span></span>

- <span data-ttu-id="f7644-176">Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="f7644-176">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="f7644-177">Przywróć zależności `app1` i narzędzia dla projektu znajdującego się w danej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="f7644-177">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="f7644-178">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu ścieżki pliku podanej jako źródło:</span><span class="sxs-lookup"><span data-stu-id="f7644-178">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="f7644-179">Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu przy użyciu dwóch ścieżek plików dostarczonych jako źródła:</span><span class="sxs-lookup"><span data-stu-id="f7644-179">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="f7644-180">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przedstawiającym szczegółowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f7644-180">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
