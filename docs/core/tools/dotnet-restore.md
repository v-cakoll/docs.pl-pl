---
title: polecenie restore DotNet - .NET Core interfejsu wiersza polecenia
description: Dowiedz się, jak przywrócić narzędzia specyficzne dla projektu przy użyciu polecenia przywracania dotnet i zależności.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: fcfa3f2f7133c3add2b02823937dd26fce690453
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696588"
---
# <a name="dotnet-restore"></a><span data-ttu-id="1f5e6-103">Przywracanie DotNet</span><span class="sxs-lookup"><span data-stu-id="1f5e6-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1f5e6-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1f5e6-104">Name</span></span>

<span data-ttu-id="1f5e6-105">`dotnet restore` -Przywraca zależności i narzędzia do projektu.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1f5e6-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="1f5e6-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1f5e6-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1f5e6-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1f5e6-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1f5e6-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="1f5e6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1f5e6-109">Description</span></span>

<span data-ttu-id="1f5e6-110">`dotnet restore` Polecenie używa NuGet, aby przywrócić zależności, a także narzędzia specyficzne dla projektu, które są określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="1f5e6-111">Domyślnie przywracania zależności oraz narzędzia są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1f5e6-112">Aby przywrócić zależności, NuGet musi źródeł danych, w którym znajdują się pakiety.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="1f5e6-113">Źródła danych zwykle są udostępniane za pośrednictwem *NuGet.config* pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-113">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="1f5e6-114">Domyślny plik konfiguracji jest udostępniane po zainstalowaniu narzędzi interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="1f5e6-115">Określ dodatkowe źródła danych, tworząc własne *NuGet.config* pliku w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-115">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="1f5e6-116">Należy także określić dodatkowych źródeł danych dla wywołania w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="1f5e6-117">Dla zależności, należy określić rozmieszczenia przywróconej pakietów podczas przy użyciu operacji przywracania `--packages` argumentu.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="1f5e6-118">Jeśli nie jest określony, pamięć podręczną pakietów NuGet domyślnej jest używana, znajdującej się w `.nuget/packages` katalogu w katalogu macierzystego użytkownika we wszystkich systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="1f5e6-119">Na przykład */home/Użytkownik1* w systemie Linux lub *C:\Users\user1* w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="1f5e6-120">Dla narzędzia specyficzne dla projektu `dotnet restore` najpierw przywraca pakietu, w którym narzędzie jest spakowane, a następnie przywrócić zależności narzędzia określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="1f5e6-121">Zachowanie `dotnet restore` polecenia wpływ na niektóre ustawienia w *Nuget.Config* pliku, jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="1f5e6-122">Na przykład ustawienie `globalPackagesFolder` w *NuGet.Config* umieszcza przywróconej pakietów NuGet w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="1f5e6-123">Jest to alternatywa do określania `--packages` opcja `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="1f5e6-124">Aby uzyskać więcej informacji, zobacz [odwołanie do pliku NuGet.Config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="1f5e6-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="1f5e6-125">Niejawne `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="1f5e6-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="1f5e6-126">Począwszy od programu .NET Core 2.0, `dotnet restore` uruchomieniu niejawnie w razie potrzeby w przypadku wysyłania następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="1f5e6-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="1f5e6-127">W większości przypadków, nie musisz jawnie użyć `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="1f5e6-128">Czasami może być niewygodne uruchomić `dotnet restore` niejawnie.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-128">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="1f5e6-129">Na przykład zautomatyzowanych systemów, takich jak systemy, należy wywołać `dotnet restore` jawnie w celu kontrolowania, podczas przywracania występuje decydować użycie sieci.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="1f5e6-130">Aby zapobiec `dotnet restore` z niejawnie działa, możesz użyć `--no-restore` flagi z dowolnego z tych poleceń, aby wyłączyć niejawne przywracania.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="1f5e6-131">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1f5e6-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="1f5e6-132">Opcjonalna ścieżka do pliku projektu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="1f5e6-133">Opcje</span><span class="sxs-lookup"><span data-stu-id="1f5e6-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1f5e6-134">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1f5e6-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="1f5e6-135">Plik konfiguracji NuGet (*NuGet.config*) do użycia dla operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="1f5e6-136">Wyłącza Przywracanie wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="1f5e6-137">Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="1f5e6-138">Określenie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="1f5e6-139">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="1f5e6-140">Jeśli ma spełnia wymagania wersji pakietów tylko Ostrzegaj o źródła nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="1f5e6-141">Określa, że nie pamięci podręcznej pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="1f5e6-142">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="1f5e6-143">Określa katalog dla przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="1f5e6-144">Określa środowisko uruchomieniowe dla Przywracanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="1f5e6-145">Umożliwia przywracanie pakietów dla środowisk uruchomieniowych nie są jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="1f5e6-146">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="1f5e6-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="1f5e6-147">Podaj wielu identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="1f5e6-148">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="1f5e6-149">To ustawienie przesłania wszystkie źródła określone w *NuGet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-149">This setting overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="1f5e6-150">Wiele źródeł można podać, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="1f5e6-151">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1f5e6-152">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1f5e6-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1f5e6-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="1f5e6-154">Plik konfiguracji NuGet (*NuGet.config*) do użycia dla operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-154">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="1f5e6-155">Wyłącza Przywracanie wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-155">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="1f5e6-156">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-156">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="1f5e6-157">Jeśli ma spełnia wymagania wersji pakietów tylko Ostrzegaj o źródła nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-157">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="1f5e6-158">Określa, że nie pamięci podręcznej pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-158">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="1f5e6-159">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="1f5e6-160">Określa katalog dla przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-160">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="1f5e6-161">Określa środowisko uruchomieniowe dla Przywracanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="1f5e6-162">Umożliwia przywracanie pakietów dla środowisk uruchomieniowych nie są jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="1f5e6-163">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="1f5e6-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="1f5e6-164">Podaj wielu identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="1f5e6-165">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="1f5e6-166">Przesłania wszystkie źródła określone w *NuGet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-166">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="1f5e6-167">Wiele źródeł można podać, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="1f5e6-168">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1f5e6-169">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1f5e6-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="1f5e6-170">Przykłady</span><span class="sxs-lookup"><span data-stu-id="1f5e6-170">Examples</span></span>

<span data-ttu-id="1f5e6-171">Przywróć zależności i narzędzi dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="1f5e6-171">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="1f5e6-172">Przywróć zależności i narzędzia do `app1` znaleziono projektu w podanej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="1f5e6-172">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="1f5e6-173">Przywróć zależności i narzędzi dla projektu w bieżącym katalogu przy użyciu ścieżki pliku w źródle:</span><span class="sxs-lookup"><span data-stu-id="1f5e6-173">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="1f5e6-174">Przywróć zależności i narzędzi dla projektu w bieżącym katalogu przy użyciu ścieżek plików dostarczana jako źródeł:</span><span class="sxs-lookup"><span data-stu-id="1f5e6-174">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="1f5e6-175">Przywróć zależności i narzędzi dla projektu w bieżącym katalogu i pokazuje tylko minimalne dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1f5e6-175">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
