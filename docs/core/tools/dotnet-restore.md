---
title: polecenie restore DotNet - .NET Core interfejsu wiersza polecenia
description: "Dowiedz się, jak przywrócić narzędzia specyficzne dla projektu przy użyciu polecenia przywracania dotnet i zależności."
keywords: polecenia interfejsu wiersza polecenia przywracania DotNet, interfejsu wiersza polecenia, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 82a78dcb0cc85e2ba087b6df5ee029cbfb687358
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-restore"></a><span data-ttu-id="a4ed3-104">Przywracanie DotNet</span><span class="sxs-lookup"><span data-stu-id="a4ed3-104">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a4ed3-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a4ed3-105">Name</span></span>

<span data-ttu-id="a4ed3-106">`dotnet restore`-Przywraca zależności i narzędzia do projektu.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a4ed3-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a4ed3-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a4ed3-108">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="a4ed3-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a4ed3-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="a4ed3-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="a4ed3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a4ed3-110">Description</span></span>

<span data-ttu-id="a4ed3-111">`dotnet restore` Polecenie używa NuGet, aby przywrócić zależności, a także narzędzia specyficzne dla projektu, które są określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-111">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="a4ed3-112">Domyślnie przywracania zależności oraz narzędzia są wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-112">By default, the restoration of dependencies and tools are performed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a4ed3-113">Aby przywrócić zależności, NuGet musi źródeł danych, w którym znajdują się pakiety.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-113">In order to restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="a4ed3-114">Źródła danych zwykle są udostępniane za pośrednictwem *NuGet.config* pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-114">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="a4ed3-115">Domyślny plik konfiguracji jest udostępniane po zainstalowaniu narzędzi interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-115">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="a4ed3-116">Określ dodatkowe źródła danych, tworząc własne *NuGet.config* pliku w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-116">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="a4ed3-117">Należy także określić dodatkowych źródeł danych dla wywołania w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-117">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="a4ed3-118">Dla zależności, należy określić rozmieszczenia przywróconej pakietów podczas przy użyciu operacji przywracania `--packages` argumentu.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-118">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="a4ed3-119">Jeśli nie jest określony, pamięć podręczną pakietów NuGet domyślnej jest używana, znajdującej się w `.nuget/packages` katalogu w katalogu macierzystego użytkownika we wszystkich systemach operacyjnych (na przykład */home/Użytkownik1* w systemie Linux lub *C:\Users\user1*  w systemie Windows).</span><span class="sxs-lookup"><span data-stu-id="a4ed3-119">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, */home/user1* on Linux or *C:\Users\user1* on Windows).</span></span>

<span data-ttu-id="a4ed3-120">Dla narzędzia specyficzne dla projektu `dotnet restore` najpierw przywraca pakietu, w którym narzędzie jest spakowane, a następnie przywrócić zależności narzędzia określone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="a4ed3-121">Zachowanie `dotnet restore` polecenia wpływ na niektóre ustawienia w *Nuget.Config* pliku, jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="a4ed3-122">Na przykład ustawienie `globalPackagesFolder` w *NuGet.Config* umieszcza przywróconej pakietów NuGet w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="a4ed3-123">Jest to alternatywa do określania `--packages` opcja `dotnet restore` polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="a4ed3-124">Aby uzyskać więcej informacji, zobacz [odwołanie do pliku NuGet.Config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="a4ed3-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="arguments"></a><span data-ttu-id="a4ed3-125">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a4ed3-125">Arguments</span></span>

`ROOT`

<span data-ttu-id="a4ed3-126">Opcjonalna ścieżka do pliku projektu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-126">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="a4ed3-127">Opcje</span><span class="sxs-lookup"><span data-stu-id="a4ed3-127">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a4ed3-128">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="a4ed3-128">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="a4ed3-129">Plik konfiguracji NuGet (*NuGet.config*) do użycia dla operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-129">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="a4ed3-130">Wyłącza Przywracanie wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-130">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="a4ed3-131">Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a4ed3-132">Jest to równoważne usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-132">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="a4ed3-133">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-133">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="a4ed3-134">Jeśli ma spełnia wymagania wersji pakietów tylko Ostrzegaj o źródła nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-134">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="a4ed3-135">Określa, że nie pamięci podręcznej pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-135">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="a4ed3-136">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-136">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="a4ed3-137">Określa katalog dla przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-137">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a4ed3-138">Określa środowisko uruchomieniowe dla Przywracanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-138">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="a4ed3-139">Umożliwia przywracanie pakietów dla środowisk uruchomieniowych nie są jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-139">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="a4ed3-140">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a4ed3-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="a4ed3-141">Podaj wielu identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-141">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="a4ed3-142">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-142">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="a4ed3-143">Przesłania wszystkie źródła określone w *NuGet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-143">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="a4ed3-144">Wiele źródeł można podać, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-144">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="a4ed3-145">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a4ed3-146">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a4ed3-147">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="a4ed3-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="a4ed3-148">Plik konfiguracji NuGet (*NuGet.config*) do użycia dla operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-148">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="a4ed3-149">Wyłącza Przywracanie wielu projektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-149">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="a4ed3-150">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-150">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="a4ed3-151">Jeśli ma spełnia wymagania wersji pakietów tylko Ostrzegaj o źródła nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-151">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="a4ed3-152">Określa, że nie pamięci podręcznej pakietów i żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-152">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="a4ed3-153">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-153">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="a4ed3-154">Określa katalog dla przywróconych pakietów.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-154">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a4ed3-155">Określa środowisko uruchomieniowe dla Przywracanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-155">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="a4ed3-156">Umożliwia przywracanie pakietów dla środowisk uruchomieniowych nie są jawnie wymienione w `<RuntimeIdentifiers>` tagów w *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-156">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="a4ed3-157">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a4ed3-157">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="a4ed3-158">Podaj wielu identyfikatorów RID, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-158">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="a4ed3-159">Określa źródło pakietu NuGet do użycia podczas operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-159">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="a4ed3-160">Przesłania wszystkie źródła określone w *NuGet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-160">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="a4ed3-161">Wiele źródeł można podać, określając tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-161">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="a4ed3-162">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a4ed3-163">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a4ed3-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="a4ed3-164">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a4ed3-164">Examples</span></span>

<span data-ttu-id="a4ed3-165">Przywróć zależności i narzędzi dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a4ed3-165">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="a4ed3-166">Przywróć zależności i narzędzia do `app1` znaleziono projektu w podanej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="a4ed3-166">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="a4ed3-167">Przywróć zależności i narzędzi dla projektu w bieżącym katalogu przy użyciu ścieżki pliku w źródle:</span><span class="sxs-lookup"><span data-stu-id="a4ed3-167">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="a4ed3-168">Przywróć zależności i narzędzi dla projektu w bieżącym katalogu przy użyciu ścieżek plików dostarczana jako źródeł:</span><span class="sxs-lookup"><span data-stu-id="a4ed3-168">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="a4ed3-169">Przywróć zależności i narzędzi dla projektu w bieżącym katalogu i pokazuje tylko minimalne dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a4ed3-169">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
