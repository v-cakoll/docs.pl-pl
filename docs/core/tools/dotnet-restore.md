---
title: polecenie przywracania dotnet
description: Dowiedz się, jak przywrócić zależności i narzędzia specyficzne dla projektu za pomocą polecenia przywracania dotnet.
ms.date: 02/27/2020
ms.openlocfilehash: e74027ba70ddf6905a12f9691caeb0a406428ad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157027"
---
# <a name="dotnet-restore"></a><span data-ttu-id="69bdf-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="69bdf-103">dotnet restore</span></span>

<span data-ttu-id="69bdf-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="69bdf-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="69bdf-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="69bdf-105">Name</span></span>

<span data-ttu-id="69bdf-106">`dotnet restore`- Przywraca zależności i narzędzia projektu.</span><span class="sxs-lookup"><span data-stu-id="69bdf-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="69bdf-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="69bdf-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [-v|--verbosity] [--interactive]

dotnet restore [-h|--help]
```

## <a name="description"></a><span data-ttu-id="69bdf-108">Opis</span><span class="sxs-lookup"><span data-stu-id="69bdf-108">Description</span></span>

<span data-ttu-id="69bdf-109">Polecenie `dotnet restore` używa NuGet do przywracania zależności, a także narzędzi specyficznych dla projektu, które są określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="69bdf-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="69bdf-110">Domyślnie przywracanie zależności i narzędzi są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="69bdf-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="69bdf-111">Aby przywrócić zależności, NuGet potrzebuje źródeł danych, w których znajdują się pakiety.</span><span class="sxs-lookup"><span data-stu-id="69bdf-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="69bdf-112">Kanały informacyjne są zwykle dostarczane za pośrednictwem pliku konfiguracyjnego *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="69bdf-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="69bdf-113">Domyślny plik konfiguracyjny jest dostarczany po zainstalowaniu sdk .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69bdf-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="69bdf-114">Dodatkowe źródła danych można określić, tworząc własny plik *nuget.config* w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="69bdf-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="69bdf-115">Można zastąpić kanały *nuget.config* opcją `-s` - - można zastąpić.</span><span class="sxs-lookup"><span data-stu-id="69bdf-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="69bdf-116">W przypadku zależności należy określić, gdzie przywrócone pakiety są `--packages` umieszczane podczas operacji przywracania przy użyciu argumentu.</span><span class="sxs-lookup"><span data-stu-id="69bdf-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="69bdf-117">Jeśli nie zostanie określony, używana jest domyślna pamięć podręczna pakietu NuGet, która znajduje się w `.nuget/packages` katalogu w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="69bdf-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="69bdf-118">Na przykład */home/user1* w systemie Linux lub *C:\Users\user1* w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="69bdf-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="69bdf-119">W przypadku narzędzi specyficznych dla projektu najpierw przywraca pakiet, `dotnet restore` w którym narzędzie jest zapakowane, a następnie przechodzi do przywrócenia zależności narzędzia, jak określono w jego pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="69bdf-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="69bdf-120">różnice nuget.config</span><span class="sxs-lookup"><span data-stu-id="69bdf-120">nuget.config differences</span></span>

<span data-ttu-id="69bdf-121">Na zachowanie `dotnet restore` polecenia mają wpływ ustawienia pliku *nuget.config,* jeśli są obecne.</span><span class="sxs-lookup"><span data-stu-id="69bdf-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="69bdf-122">Na przykład ustawienie `globalPackagesFolder` in *nuget.config* umieszcza przywrócone pakiety NuGet w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="69bdf-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="69bdf-123">Jest to alternatywa dla `--packages` określenia `dotnet restore` opcji w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="69bdf-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="69bdf-124">Aby uzyskać więcej informacji, zobacz [odwołanie nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="69bdf-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="69bdf-125">Istnieją trzy specyficzne `dotnet restore` ustawienia, które ignorują:</span><span class="sxs-lookup"><span data-stu-id="69bdf-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="69bdf-126">bindingRedirects (Redirects)</span><span class="sxs-lookup"><span data-stu-id="69bdf-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="69bdf-127">Powiązanie przekierowania nie działają `<PackageReference>` z elementami i `<PackageReference>` .NET Core obsługuje tylko elementy dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="69bdf-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="69bdf-128">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="69bdf-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="69bdf-129">To ustawienie jest specyficzne dla programu Visual Studio i nie ma zastosowania do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69bdf-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="69bdf-130">.NET Core nie używa `packages.config` pliku i `<PackageReference>` zamiast tego używa elementów dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="69bdf-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="69bdf-131">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="69bdf-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="69bdf-132">To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji](https://github.com/NuGet/Home/issues/7939) zaufanych pakietów na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="69bdf-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="69bdf-133">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="69bdf-133">Implicit restore</span></span>

<span data-ttu-id="69bdf-134">W `dotnet restore` razie potrzeby po uruchomieniu następującepolecenia jest uruchamiane niejawnie:</span><span class="sxs-lookup"><span data-stu-id="69bdf-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="69bdf-135">W większości przypadków nie trzeba jawnie używać `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="69bdf-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="69bdf-136">Czasami może być niewygodne `dotnet restore` do uruchomienia niejawnie.</span><span class="sxs-lookup"><span data-stu-id="69bdf-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="69bdf-137">Na przykład niektóre zautomatyzowane systemy, takie jak `dotnet restore` systemy kompilacji, muszą jawnie wywołać, aby kontrolować, gdy nastąpi przywracanie, aby mogły kontrolować użycie sieci.</span><span class="sxs-lookup"><span data-stu-id="69bdf-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="69bdf-138">Aby `dotnet restore` zapobiec uruchamianiu niejawnie, można użyć `--no-restore` flagi z dowolnym z tych poleceń, aby wyłączyć przywracanie niejawne.</span><span class="sxs-lookup"><span data-stu-id="69bdf-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="69bdf-139">Argumenty</span><span class="sxs-lookup"><span data-stu-id="69bdf-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="69bdf-140">Opcjonalna ścieżka do pliku projektu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="69bdf-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="69bdf-141">Opcje</span><span class="sxs-lookup"><span data-stu-id="69bdf-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="69bdf-142">Plik konfiguracyjny NuGet (*nuget.config*) do użycia w operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="69bdf-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="69bdf-143">Wyłącza przywracanie wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="69bdf-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="69bdf-144">Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="69bdf-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="69bdf-145">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="69bdf-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="69bdf-146">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="69bdf-146">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="69bdf-147">Ostrzegaj tylko o źródłach, które nie powiodło się, jeśli istnieją pakiety spełniające wymagania wersji.</span><span class="sxs-lookup"><span data-stu-id="69bdf-147">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--no-cache`**

  <span data-ttu-id="69bdf-148">Określa, aby nie buforować pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="69bdf-148">Specifies to not cache packages and HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="69bdf-149">Podczas przywracania projektu z odwołaniami do projektu (P2P) przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="69bdf-149">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="69bdf-150">Określa katalog przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="69bdf-150">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="69bdf-151">Określa czas wykonywania przywracania pakietu.</span><span class="sxs-lookup"><span data-stu-id="69bdf-151">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="69bdf-152">Służy do przywracania pakietów dla krzepków `<RuntimeIdentifiers>` niejawnie wymienionych w tagu w pliku *csproj.*</span><span class="sxs-lookup"><span data-stu-id="69bdf-152">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="69bdf-153">Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="69bdf-153">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="69bdf-154">Podaj wiele identyfikatorów NIK, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="69bdf-154">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="69bdf-155">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="69bdf-155">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="69bdf-156">To ustawienie zastępuje wszystkie źródła określone w plikach *nuget.config.*</span><span class="sxs-lookup"><span data-stu-id="69bdf-156">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="69bdf-157">Można podać wiele źródeł, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="69bdf-157">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--verbosity <LEVEL>`**

  <span data-ttu-id="69bdf-158">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="69bdf-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="69bdf-159">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="69bdf-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="69bdf-160">Wartością `minimal`domyślną jest .</span><span class="sxs-lookup"><span data-stu-id="69bdf-160">Default value is `minimal`.</span></span>

- **`--interactive`**

  <span data-ttu-id="69bdf-161">Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie).</span><span class="sxs-lookup"><span data-stu-id="69bdf-161">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="69bdf-162">Od .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="69bdf-162">Since .NET Core 2.1.400.</span></span>

## <a name="examples"></a><span data-ttu-id="69bdf-163">Przykłady</span><span class="sxs-lookup"><span data-stu-id="69bdf-163">Examples</span></span>

- <span data-ttu-id="69bdf-164">Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="69bdf-164">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="69bdf-165">Przywracanie zależności i `app1` narzędzi dla projektu znalezionych w danej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="69bdf-165">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="69bdf-166">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu, używając ścieżki pliku dostarczonej jako źródło:</span><span class="sxs-lookup"><span data-stu-id="69bdf-166">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="69bdf-167">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu, używając dwóch ścieżek plików podanych jako źródła:</span><span class="sxs-lookup"><span data-stu-id="69bdf-167">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="69bdf-168">Przywracanie zależności i narzędzi dla projektu w bieżącym katalogu z szczegółowymi wynikami:</span><span class="sxs-lookup"><span data-stu-id="69bdf-168">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
