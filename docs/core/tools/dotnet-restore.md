---
title: polecenie dotnet restore
description: Informacje o sposobie przywracania zależności i narzędzi specyficznych dla projektu przy użyciu polecenia dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: c221e8a34e844d0ad0482d2bb4aa6e1c795555ca
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626063"
---
# <a name="dotnet-restore"></a><span data-ttu-id="b1991-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b1991-103">dotnet restore</span></span>

<span data-ttu-id="b1991-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="b1991-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b1991-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="b1991-105">Name</span></span>

<span data-ttu-id="b1991-106">`dotnet restore` — przywraca zależności i narzędzia projektu.</span><span class="sxs-lookup"><span data-stu-id="b1991-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b1991-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="b1991-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [-v|--verbosity] [--interactive]

dotnet restore [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b1991-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b1991-108">Description</span></span>

<span data-ttu-id="b1991-109">Polecenie `dotnet restore` używa narzędzia NuGet do przywracania zależności oraz narzędzi specyficznych dla projektu, które są określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b1991-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="b1991-110">Domyślnie przywracanie zależności i narzędzi jest wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="b1991-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="b1991-111">Aby przywrócić zależności, program NuGet potrzebuje kanałów informacyjnych, w których znajdują się pakiety.</span><span class="sxs-lookup"><span data-stu-id="b1991-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="b1991-112">Kanały informacyjne są zazwyczaj udostępniane za pośrednictwem pliku konfiguracyjnego *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="b1991-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="b1991-113">Domyślny plik konfiguracji jest dostarczany, gdy zainstalowano zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b1991-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="b1991-114">Możesz określić dodatkowe źródła danych, tworząc własny plik *NuGet. config* w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="b1991-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="b1991-115">Można zastąpić źródła danych *NuGet. config* opcją-`-s`.</span><span class="sxs-lookup"><span data-stu-id="b1991-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="b1991-116">W przypadku zależności należy określić miejsce, w którym przywrócone pakiety są umieszczane podczas operacji przywracania przy użyciu argumentu `--packages`.</span><span class="sxs-lookup"><span data-stu-id="b1991-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="b1991-117">Jeśli nie zostanie określony, zostanie użyta domyślna pamięć podręczna pakietów NuGet, która znajduje się w katalogu `.nuget/packages` w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="b1991-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="b1991-118">Na przykład */home/user1* na system Linux lub *C:\Users\user1* w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="b1991-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="b1991-119">W przypadku narzędzi specyficznych dla projektu `dotnet restore` najpierw przywraca pakiet, w którym narzędzie jest spakowane, a następnie przechodzi do przywracania zależności narzędzia, jak określono w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b1991-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="b1991-120">różnice NuGet. config</span><span class="sxs-lookup"><span data-stu-id="b1991-120">nuget.config differences</span></span>

<span data-ttu-id="b1991-121">Na zachowanie polecenia `dotnet restore` są zależne od ustawień w pliku *NuGet. config* (jeśli istnieją).</span><span class="sxs-lookup"><span data-stu-id="b1991-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="b1991-122">Na przykład ustawienie `globalPackagesFolder` w *pliku NuGet. config* powoduje umieszczenie przywróconych pakietów NuGet w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="b1991-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="b1991-123">Jest to alternatywa dla określenia opcji `--packages` na `dotnet restore` polecenie.</span><span class="sxs-lookup"><span data-stu-id="b1991-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="b1991-124">Aby uzyskać więcej informacji, zobacz [Dokumentacja NuGet. config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="b1991-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="b1991-125">Istnieją trzy określone ustawienia, które `dotnet restore` ignoruje:</span><span class="sxs-lookup"><span data-stu-id="b1991-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="b1991-126">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="b1991-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="b1991-127">Przekierowania powiązań nie współpracują z `<PackageReference>` elementami, a platforma .NET Core obsługuje tylko `<PackageReference>` elementów dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1991-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="b1991-128">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="b1991-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="b1991-129">To ustawienie dotyczy programu Visual Studio i nie ma zastosowania do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1991-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="b1991-130">Platforma .NET Core nie używa pliku `packages.config` i zamiast tego używa elementów `<PackageReference>` dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1991-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="b1991-131">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="b1991-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="b1991-132">To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji](https://github.com/NuGet/Home/issues/7939) zaufanych pakietów przez wiele platform.</span><span class="sxs-lookup"><span data-stu-id="b1991-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="b1991-133">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="b1991-133">Implicit restore</span></span>

<span data-ttu-id="b1991-134">Polecenie `dotnet restore` jest uruchamiane niejawnie w razie potrzeby po uruchomieniu następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="b1991-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="b1991-135">W większości przypadków nie trzeba jawnie używać `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="b1991-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="b1991-136">Czasami może być niewygodne uruchamianie `dotnet restore` niejawnie.</span><span class="sxs-lookup"><span data-stu-id="b1991-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="b1991-137">Na przykład niektóre zautomatyzowane systemy, takie jak systemy kompilacji, muszą wywoływać `dotnet restore` jawnie, aby określić, kiedy następuje przywracanie, aby umożliwić im sterowanie użyciem sieci.</span><span class="sxs-lookup"><span data-stu-id="b1991-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="b1991-138">Aby zapobiec niejawnemu uruchamianiu `dotnet restore`, można użyć flagi `--no-restore` z dowolnym z tych poleceń, aby wyłączyć Przywracanie niejawne.</span><span class="sxs-lookup"><span data-stu-id="b1991-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="b1991-139">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b1991-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="b1991-140">Opcjonalna ścieżka do pliku projektu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="b1991-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="b1991-141">Opcje</span><span class="sxs-lookup"><span data-stu-id="b1991-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="b1991-142">Plik konfiguracji NuGet (*NuGet. config*) do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="b1991-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="b1991-143">Wyłącza przywracanie równolegle wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="b1991-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="b1991-144">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b1991-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="b1991-145">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b1991-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b1991-146">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="b1991-146">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="b1991-147">Ostrzegaj o nieudanych źródłach, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="b1991-147">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--no-cache`**

  <span data-ttu-id="b1991-148">Określa, aby nie buforować pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="b1991-148">Specifies to not cache packages and HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="b1991-149">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="b1991-149">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="b1991-150">Określa katalog przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="b1991-150">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="b1991-151">Określa środowisko uruchomieniowe przywracania pakietu.</span><span class="sxs-lookup"><span data-stu-id="b1991-151">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="b1991-152">Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są jawnie wymienione w tagu `<RuntimeIdentifiers>` w pliku *csproj* .</span><span class="sxs-lookup"><span data-stu-id="b1991-152">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="b1991-153">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="b1991-153">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="b1991-154">Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="b1991-154">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="b1991-155">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="b1991-155">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="b1991-156">To ustawienie zastępuje wszystkie źródła określone w plikach *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="b1991-156">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="b1991-157">Można podać wiele źródeł, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="b1991-157">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--verbosity <LEVEL>`**

  <span data-ttu-id="b1991-158">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="b1991-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b1991-159">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b1991-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b1991-160">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="b1991-160">Default value is `minimal`.</span></span>

- **`--interactive`**

  <span data-ttu-id="b1991-161">Umożliwia zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład zakończenie uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="b1991-161">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="b1991-162">Since .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="b1991-162">Since .NET Core 2.1.400.</span></span>

## <a name="examples"></a><span data-ttu-id="b1991-163">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b1991-163">Examples</span></span>

- <span data-ttu-id="b1991-164">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="b1991-164">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="b1991-165">Przywróć zależności i narzędzia dla projektu `app1` Znalezione w danej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="b1991-165">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="b1991-166">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu ścieżki pliku dostarczonej jako Źródło:</span><span class="sxs-lookup"><span data-stu-id="b1991-166">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="b1991-167">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu dwóch ścieżek plików dostarczonych jako źródła:</span><span class="sxs-lookup"><span data-stu-id="b1991-167">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="b1991-168">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przedstawiające szczegółowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b1991-168">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
