---
title: polecenie restore DotNet — interfejs wiersza polecenia platformy .NET Core
description: Dowiedz się, jak przywrócić zależności i narzędzi specyficznych dla projektu za pomocą polecenia dotnet restore.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 0eaab1aa1bc52bd5b3c51a6ed2dd7a59c35a4aa5
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960598"
---
# <a name="dotnet-restore"></a><span data-ttu-id="8d11d-103">DotNet restore</span><span class="sxs-lookup"><span data-stu-id="8d11d-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8d11d-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8d11d-104">Name</span></span>

<span data-ttu-id="8d11d-105">`dotnet restore` -Przywraca zależności i narzędzia do projektu.</span><span class="sxs-lookup"><span data-stu-id="8d11d-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8d11d-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="8d11d-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8d11d-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8d11d-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8d11d-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8d11d-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="8d11d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8d11d-109">Description</span></span>

<span data-ttu-id="8d11d-110">`dotnet restore` Polecenie używa NuGet, aby przywrócić zależności, a także narzędzi specyficznych dla projektu, które są określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="8d11d-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="8d11d-111">Domyślnie przywrócenie zależności i narzędzia są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="8d11d-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="8d11d-112">Aby przywrócić zależności, NuGet wymaga źródła danych, gdzie znajdują się pakiety.</span><span class="sxs-lookup"><span data-stu-id="8d11d-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="8d11d-113">Źródła danych zwykle są udostępniane za pośrednictwem *NuGet.config* pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8d11d-113">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="8d11d-114">Domyślny plik konfiguracji znajduje się po zainstalowaniu narzędzi interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d11d-114">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="8d11d-115">Określ dodatkowe źródła danych, tworząc własne *NuGet.config* pliku w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="8d11d-115">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="8d11d-116">Należy również określić dodatkowych źródeł danych dla wywołania w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d11d-116">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="8d11d-117">Dla zależności, należy określić, gdzie przywróconej pakiety są wprowadzane w przy użyciu operacji przywracania `--packages` argumentu.</span><span class="sxs-lookup"><span data-stu-id="8d11d-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="8d11d-118">Jeśli nie zostanie określony, domyślny pakiet NuGet z pamięci podręcznej jest używany, który znajduje się w `.nuget/packages` katalogu w katalogu macierzystym użytkownika we wszystkich systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="8d11d-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="8d11d-119">Na przykład */home/Użytkownik1* w systemie Linux lub *C:\Users\user1* na Windows.</span><span class="sxs-lookup"><span data-stu-id="8d11d-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="8d11d-120">W przypadku narzędzi specyficznych dla projektu `dotnet restore` najpierw przywraca pakietu, w którym narzędzie jest pakowany, a następnie przywrócić narzędzia zależności, jak określono w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="8d11d-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="8d11d-121">Zachowanie `dotnet restore` polecenia jest zależna od niektórych ustawień w *Nuget.Config* pliku, jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="8d11d-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="8d11d-122">Na przykład ustawienie `globalPackagesFolder` w *NuGet.Config* umieszcza przywróconej pakietów NuGet w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="8d11d-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="8d11d-123">Jest to alternatywa do określania `--packages` opcja `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d11d-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="8d11d-124">Aby uzyskać więcej informacji, zobacz [odwołanie do pliku NuGet.Config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="8d11d-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="8d11d-125">Niejawne `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="8d11d-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="8d11d-126">Począwszy od programu .NET Core 2.0, `dotnet restore` zostanie ona uruchomiona niejawnie w razie potrzeby uruchom następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="8d11d-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="8d11d-127">W większości przypadków nie trzeba już jawnie użyć `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d11d-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="8d11d-128">Czasami może być niewygodne uruchomić `dotnet restore` niejawnie.</span><span class="sxs-lookup"><span data-stu-id="8d11d-128">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="8d11d-129">Na przykład, niektóre zautomatyzowane systemy, takich jak systemy kompilacji, należy wywołać `dotnet restore` jawnie, aby kontrolować, podczas przywracania odbywa się tak, aby kontrolować użycie sieci.</span><span class="sxs-lookup"><span data-stu-id="8d11d-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="8d11d-130">Aby zapobiec `dotnet restore` z niejawnie działa, możesz użyć `--no-restore` flagi z dowolnego z tych poleceń, aby wyłączyć niejawne przywracania.</span><span class="sxs-lookup"><span data-stu-id="8d11d-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="8d11d-131">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8d11d-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="8d11d-132">Opcjonalna ścieżka do pliku projektu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="8d11d-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="8d11d-133">Opcje</span><span class="sxs-lookup"><span data-stu-id="8d11d-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8d11d-134">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8d11d-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="8d11d-135">Plik konfiguracyjny NuGet (*NuGet.config*) na potrzeby operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="8d11d-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="8d11d-136">Wyłącza Przywracanie wielu projektów wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="8d11d-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="8d11d-137">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8d11d-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="8d11d-138">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="8d11d-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="8d11d-139">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d11d-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="8d11d-140">Tylko Ostrzegaj o źródłach nie powiodło się, jeśli ma pakietów spełniających wymaganie dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="8d11d-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="8d11d-141">Określa, że nie pamięci podręcznej pakietów oraz żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="8d11d-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="8d11d-142">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca projektu głównego, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="8d11d-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="8d11d-143">Określa katalog dla przywróconej pakietów.</span><span class="sxs-lookup"><span data-stu-id="8d11d-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="8d11d-144">Określa środowiska wykonawczego Przywracanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="8d11d-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="8d11d-145">Jest on używany do przywrócenia pakietów dla środowisk uruchomieniowych nie zostały jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="8d11d-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="8d11d-146">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="8d11d-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="8d11d-147">Użycie tej opcji wiele razy, aby przekazać wiele identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="8d11d-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="8d11d-148">Określa źródło pakietu NuGet ma być używany podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="8d11d-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="8d11d-149">Ustawienie to zastępuje wszystkie źródła określony w *NuGet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="8d11d-149">This setting overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="8d11d-150">Wiele źródeł może być udostępniane przez użycie tej opcji wiele razy.</span><span class="sxs-lookup"><span data-stu-id="8d11d-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="8d11d-151">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d11d-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8d11d-152">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8d11d-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8d11d-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8d11d-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="8d11d-154">Plik konfiguracyjny NuGet (*NuGet.config*) na potrzeby operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="8d11d-154">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="8d11d-155">Wyłącza Przywracanie wielu projektów wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="8d11d-155">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="8d11d-156">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d11d-156">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="8d11d-157">Tylko Ostrzegaj o źródłach nie powiodło się, jeśli ma pakietów spełniających wymaganie dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="8d11d-157">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="8d11d-158">Określa, że nie pamięci podręcznej pakietów oraz żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="8d11d-158">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="8d11d-159">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca projektu głównego, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="8d11d-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="8d11d-160">Określa katalog dla przywróconej pakietów.</span><span class="sxs-lookup"><span data-stu-id="8d11d-160">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="8d11d-161">Określa środowiska wykonawczego Przywracanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="8d11d-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="8d11d-162">Jest on używany do przywrócenia pakietów dla środowisk uruchomieniowych nie zostały jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="8d11d-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="8d11d-163">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="8d11d-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="8d11d-164">Użycie tej opcji wiele razy, aby przekazać wiele identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="8d11d-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="8d11d-165">Określa źródło pakietu NuGet ma być używany podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="8d11d-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="8d11d-166">Ustawienie to zastępuje wszystkie źródła określony w *NuGet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="8d11d-166">This overrides all of the sources specified in the *NuGet.config* files.</span></span> <span data-ttu-id="8d11d-167">Wiele źródeł może być udostępniane przez użycie tej opcji wiele razy.</span><span class="sxs-lookup"><span data-stu-id="8d11d-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="8d11d-168">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d11d-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8d11d-169">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8d11d-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="8d11d-170">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8d11d-170">Examples</span></span>

<span data-ttu-id="8d11d-171">Przywróć zależności i narzędzia dla projektów w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="8d11d-171">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="8d11d-172">Przywracanie zależności i narzędzia dla `app1` projekt znaleziony w podanej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="8d11d-172">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="8d11d-173">Przywróć zależności i narzędzia dla projektów w bieżącym katalogu przy użyciu ścieżki pliku w źródle:</span><span class="sxs-lookup"><span data-stu-id="8d11d-173">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="8d11d-174">Przywróć zależności i narzędzia dla projektów w bieżącym katalogu przy użyciu ścieżki dwóch plików, podana jako źródła:</span><span class="sxs-lookup"><span data-stu-id="8d11d-174">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="8d11d-175">Przywróć zależności i narzędzia dla projektów w bieżącym katalogu i pokazuje tylko minimalne dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8d11d-175">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
