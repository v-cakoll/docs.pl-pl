---
title: polecenie dotnet restore
description: Informacje o sposobie przywracania zależności i narzędzi specyficznych dla projektu przy użyciu polecenia dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: 347ad691b8d439fdf1696f790d4a838a73c57b5a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105152"
---
# <a name="dotnet-restore"></a><span data-ttu-id="3cd08-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3cd08-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3cd08-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3cd08-104">Name</span></span>

<span data-ttu-id="3cd08-105">`dotnet restore`— Przywraca zależności i narzędzia projektu.</span><span class="sxs-lookup"><span data-stu-id="3cd08-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3cd08-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3cd08-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3cd08-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3cd08-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3cd08-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3cd08-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="3cd08-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3cd08-109">Description</span></span>

<span data-ttu-id="3cd08-110">`dotnet restore` Polecenie używa narzędzia NuGet do przywracania zależności oraz narzędzi specyficznych dla projektu, które są określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3cd08-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="3cd08-111">Domyślnie przywracanie zależności i narzędzi jest wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="3cd08-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="3cd08-112">Aby przywrócić zależności, program NuGet potrzebuje kanałów informacyjnych, w których znajdują się pakiety.</span><span class="sxs-lookup"><span data-stu-id="3cd08-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="3cd08-113">Kanały informacyjne są zazwyczaj udostępniane za pośrednictwem pliku konfiguracyjnego *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="3cd08-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="3cd08-114">Domyślny plik konfiguracji jest dostarczany podczas instalacji narzędzi interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cd08-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="3cd08-115">Możesz określić dodatkowe źródła danych, tworząc własny plik *NuGet. config* w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="3cd08-115">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="3cd08-116">W wierszu polecenia można także określić dodatkowe źródła danych dla każdego wywołania.</span><span class="sxs-lookup"><span data-stu-id="3cd08-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="3cd08-117">W przypadku zależności należy określić miejsce, w którym przywrócone pakiety są umieszczane podczas operacji `--packages` przywracania przy użyciu argumentu.</span><span class="sxs-lookup"><span data-stu-id="3cd08-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="3cd08-118">Jeśli nie zostanie określony, zostanie użyta domyślna pamięć podręczna pakietów NuGet, która znajduje `.nuget/packages` się w katalogu w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="3cd08-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="3cd08-119">Na przykład */home/user1* na system Linux lub *C:\Users\user1* w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="3cd08-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="3cd08-120">W przypadku narzędzi specyficznych dla projektu `dotnet restore` program najpierw przywraca pakiet, w którym narzędzie jest spakowane, a następnie przechodzi do przywracania zależności narzędzia, jak określono w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3cd08-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="3cd08-121">różnice NuGet. config</span><span class="sxs-lookup"><span data-stu-id="3cd08-121">nuget.config differences</span></span>

<span data-ttu-id="3cd08-122">Zachowanie `dotnet restore` polecenia ma wpływ na ustawienia w pliku *NuGet. config* , jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="3cd08-122">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="3cd08-123">Na przykład ustawienie `globalPackagesFolder` w *pliku NuGet. config* powoduje umieszczenie przywróconych pakietów NuGet w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="3cd08-123">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="3cd08-124">Jest to alternatywa dla określenia `--packages` opcji `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cd08-124">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="3cd08-125">Aby uzyskać więcej informacji, zobacz [Dokumentacja NuGet. config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="3cd08-125">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="3cd08-126">Istnieją trzy określone ustawienia, które `dotnet restore` ignorują:</span><span class="sxs-lookup"><span data-stu-id="3cd08-126">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="3cd08-127">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="3cd08-127">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="3cd08-128">Przekierowania powiązań nie działają z `<PackageReference>` elementami i .NET Core obsługuje `<PackageReference>` tylko elementy dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="3cd08-128">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="3cd08-129">Narzędzie</span><span class="sxs-lookup"><span data-stu-id="3cd08-129">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="3cd08-130">To ustawienie dotyczy programu Visual Studio i nie ma zastosowania do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3cd08-130">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="3cd08-131">Platforma .NET Core nie używa `packages.config` pliku, a zamiast `<PackageReference>` tego używa elementów dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="3cd08-131">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="3cd08-132">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="3cd08-132">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="3cd08-133">To ustawienie nie ma zastosowania, ponieważ [NuGet nie obsługuje jeszcze weryfikacji](https://github.com/NuGet/Home/issues/7939) zaufanych pakietów przez wiele platform.</span><span class="sxs-lookup"><span data-stu-id="3cd08-133">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="3cd08-134">Konwersja`dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="3cd08-134">Implicit `dotnet restore`</span></span>

<span data-ttu-id="3cd08-135">Począwszy od platformy .NET Core 2,0 `dotnet restore` , jest uruchamiany niejawnie, jeśli to konieczne, w przypadku wydawania następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="3cd08-135">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="3cd08-136">W większości przypadków nie trzeba już jawnie używać `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cd08-136">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="3cd08-137">Czasami może być niewygodne uruchamianie `dotnet restore` niejawnie.</span><span class="sxs-lookup"><span data-stu-id="3cd08-137">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="3cd08-138">Na przykład niektóre zautomatyzowane systemy, takie jak systemy kompilacji, muszą jawnie wywołać `dotnet restore` , aby określić, kiedy następuje przywracanie, aby można było kontrolować użycie sieci.</span><span class="sxs-lookup"><span data-stu-id="3cd08-138">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="3cd08-139">Aby zapobiec `dotnet restore` uruchamianiu niejawnie, można `--no-restore` użyć flagi z dowolnym z tych poleceń, aby wyłączyć Przywracanie niejawne.</span><span class="sxs-lookup"><span data-stu-id="3cd08-139">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="3cd08-140">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3cd08-140">Arguments</span></span>

`ROOT`

<span data-ttu-id="3cd08-141">Opcjonalna ścieżka do pliku projektu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="3cd08-141">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="3cd08-142">Opcje</span><span class="sxs-lookup"><span data-stu-id="3cd08-142">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3cd08-143">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3cd08-143">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="3cd08-144">Plik konfiguracji NuGet (*NuGet. config*) do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="3cd08-144">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="3cd08-145">Wyłącza przywracanie równolegle wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="3cd08-145">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="3cd08-146">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3cd08-146">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="3cd08-147">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="3cd08-147">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="3cd08-148">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cd08-148">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="3cd08-149">Ostrzegaj o nieudanych źródłach, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="3cd08-149">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="3cd08-150">Określa, aby nie buforować pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="3cd08-150">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="3cd08-151">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="3cd08-151">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="3cd08-152">Określa katalog przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="3cd08-152">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3cd08-153">Określa środowisko uruchomieniowe przywracania pakietu.</span><span class="sxs-lookup"><span data-stu-id="3cd08-153">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="3cd08-154">Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są `<RuntimeIdentifiers>` jawnie wymienione w tagu w pliku *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="3cd08-154">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="3cd08-155">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="3cd08-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="3cd08-156">Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="3cd08-156">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="3cd08-157">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="3cd08-157">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="3cd08-158">To ustawienie zastępuje wszystkie źródła określone w plikach *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="3cd08-158">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="3cd08-159">Można podać wiele źródeł, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="3cd08-159">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="3cd08-160">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cd08-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3cd08-161">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="3cd08-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--interactive`

<span data-ttu-id="3cd08-162">Umożliwia zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład zakończenie uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="3cd08-162">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="3cd08-163">Since .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="3cd08-163">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3cd08-164">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3cd08-164">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="3cd08-165">Plik konfiguracji NuGet (*NuGet. config*) do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="3cd08-165">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="3cd08-166">Wyłącza przywracanie równolegle wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="3cd08-166">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="3cd08-167">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cd08-167">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="3cd08-168">Ostrzegaj o nieudanych źródłach, jeśli istnieją pakiety spełniające wymagania dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="3cd08-168">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="3cd08-169">Określa, aby nie buforować pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="3cd08-169">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="3cd08-170">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="3cd08-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="3cd08-171">Określa katalog przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="3cd08-171">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3cd08-172">Określa środowisko uruchomieniowe przywracania pakietu.</span><span class="sxs-lookup"><span data-stu-id="3cd08-172">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="3cd08-173">Służy do przywracania pakietów dla środowiska uruchomieniowego, które nie są `<RuntimeIdentifiers>` jawnie wymienione w tagu w pliku *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="3cd08-173">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="3cd08-174">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="3cd08-174">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="3cd08-175">Podaj wiele identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="3cd08-175">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="3cd08-176">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="3cd08-176">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="3cd08-177">Spowoduje to zastąpienie wszystkich źródeł określonych w plikach *NuGet. config* .</span><span class="sxs-lookup"><span data-stu-id="3cd08-177">This overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="3cd08-178">Można podać wiele źródeł, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="3cd08-178">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="3cd08-179">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cd08-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3cd08-180">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="3cd08-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="3cd08-181">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3cd08-181">Examples</span></span>

<span data-ttu-id="3cd08-182">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="3cd08-182">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="3cd08-183">Przywróć zależności i narzędzia dla `app1` projektu Znalezione w danej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="3cd08-183">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="3cd08-184">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu ścieżki pliku dostarczonej jako Źródło:</span><span class="sxs-lookup"><span data-stu-id="3cd08-184">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="3cd08-185">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu przy użyciu dwóch ścieżek plików dostarczonych jako źródła:</span><span class="sxs-lookup"><span data-stu-id="3cd08-185">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="3cd08-186">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu i Wyświetlaj tylko minimalne dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="3cd08-186">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
