---
title: polecenie migracji dotnet
description: Polecenie Migruj z programu dotnet migruje projekt i wszystkie jego zależności.
ms.date: 08/08/2019
ms.openlocfilehash: 790c607070ff348ca7cfe30137268de18dcb0293
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990430"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="99172-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="99172-103">dotnet migrate</span></span>

<span data-ttu-id="99172-104">**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK **✓** .NET Core 2. x SDK</span><span class="sxs-lookup"><span data-stu-id="99172-104">**This article applies to: ✓** .NET Core 1.x SDK **✓** .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="99172-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="99172-105">Name</span></span>

<span data-ttu-id="99172-106">`dotnet migrate`— Migruje projekt programu .NET Core w wersji zapoznawczej 2 do projektu w stylu zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="99172-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="99172-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="99172-107">Synopsis</span></span>

```console
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="99172-108">Opis</span><span class="sxs-lookup"><span data-stu-id="99172-108">Description</span></span>

<span data-ttu-id="99172-109">Polecenie migruje prawidłowy projekt w wersji zapoznawczej 2 projekt *. JSON*do zestaw .NET Core SDK prawidłowego projektu csproj w stylu. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="99172-109">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK-style *csproj* project.</span></span>

<span data-ttu-id="99172-110">Domyślnie polecenie migruje projekt główny i wszystkie odwołania do projektu, które zawiera projekt główny.</span><span class="sxs-lookup"><span data-stu-id="99172-110">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="99172-111">To zachowanie jest wyłączone przy użyciu `--skip-project-references` opcji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="99172-111">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="99172-112">Można przeprowadzić migrację na następujących zasobach:</span><span class="sxs-lookup"><span data-stu-id="99172-112">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="99172-113">Pojedynczy projekt, określając plik *Project. JSON* do migracji.</span><span class="sxs-lookup"><span data-stu-id="99172-113">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="99172-114">Wszystkie katalogi określone w pliku *Global. JSON* przez przekazanie ścieżki do pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="99172-114">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="99172-115">Plik *. sln rozwiązania* , w którym migruje projekty, do których odwołuje się rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="99172-115">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="99172-116">Wszystkie podkatalogi danego katalogu cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="99172-116">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="99172-117">Polecenie zachowuje zmigrowany plik *Project. JSON* w `backup` katalogu, który tworzy, jeśli katalog nie istnieje. `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="99172-117">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="99172-118">To zachowanie jest zastępowane przy `--skip-backup` użyciu opcji.</span><span class="sxs-lookup"><span data-stu-id="99172-118">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="99172-119">Domyślnie operacja migracji wyprowadza stan procesu migracji do wyjścia standardowego (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="99172-119">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="99172-120">Jeśli używasz `--report-file <REPORT_FILE>` opcji, dane wyjściowe są zapisywane w pliku Określ.</span><span class="sxs-lookup"><span data-stu-id="99172-120">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="99172-121">Polecenie obsługuje tylko prawidłowe projekty w wersji zapoznawczej 2 dla *projektu.* `dotnet migrate`</span><span class="sxs-lookup"><span data-stu-id="99172-121">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="99172-122">Oznacza to, że nie można używać go do migrowania środowiska DNX lub podglądu 1 projektów opartych na formacie *JSON*bezpośrednio do projektów MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="99172-122">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="99172-123">Najpierw należy ręcznie zmigrować projekt do projektu w wersji zapoznawczej 2 *projektu. JSON*, a następnie użyć `dotnet migrate` polecenia w celu przeprowadzenia migracji projektu.</span><span class="sxs-lookup"><span data-stu-id="99172-123">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

<span data-ttu-id="99172-124">`dotnet migrate` Polecenie nie jest już dostępne począwszy od zestawu SDK programu .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="99172-124">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span>

## <a name="arguments"></a><span data-ttu-id="99172-125">Argumenty</span><span class="sxs-lookup"><span data-stu-id="99172-125">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="99172-126">Ścieżka do jednego z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="99172-126">The path to one of the following:</span></span>

* <span data-ttu-id="99172-127">plik *Project. JSON* do migracji.</span><span class="sxs-lookup"><span data-stu-id="99172-127">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="99172-128">plik *Global. JSON* : foldery określone w pliku *Global. JSON* są migrowane.</span><span class="sxs-lookup"><span data-stu-id="99172-128">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="99172-129">plik *. sln rozwiązania* : projekty, do których odwołuje się rozwiązanie, są migrowane.</span><span class="sxs-lookup"><span data-stu-id="99172-129">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="99172-130">Katalog do migracji: rekursywnie wyszukuje pliki *Project. JSON* do migracji w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="99172-130">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="99172-131">Jeśli nie określono niczego, domyślnie jest używany bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="99172-131">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="99172-132">Opcje</span><span class="sxs-lookup"><span data-stu-id="99172-132">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="99172-133">Wyjściowy plik raportu migracji w formacie JSON zamiast komunikatów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99172-133">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="99172-134">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="99172-134">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="99172-135">Raport z migracji danych wyjściowych do pliku poza konsolą programu.</span><span class="sxs-lookup"><span data-stu-id="99172-135">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="99172-136">Pomiń Migrowanie odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="99172-136">Skip migrating project references.</span></span> <span data-ttu-id="99172-137">Domyślnie odwołania do projektu są migrowane cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="99172-137">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="99172-138">Pomiń przenoszenie pliku`backup` *Project. JSON*, *Global. JSON*i  *\*. xproj* do katalogu po pomyślnej migracji.</span><span class="sxs-lookup"><span data-stu-id="99172-138">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="99172-139">Plik CSPROJ szablonu do użycia na potrzeby migracji.</span><span class="sxs-lookup"><span data-stu-id="99172-139">Template csproj file to use for migration.</span></span> <span data-ttu-id="99172-140">Domyślnie używany jest ten sam szablon, który został usunięty przez `dotnet new console` .</span><span class="sxs-lookup"><span data-stu-id="99172-140">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="99172-141">Wersja pakietu SDK, do którego odwołuje się migrowana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="99172-141">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="99172-142">Wartość domyślna to wersja zestawu SDK w programie `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="99172-142">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="99172-143">Ścieżka do pliku xproj, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="99172-143">The path to the xproj file to use.</span></span> <span data-ttu-id="99172-144">Wymagane, gdy w katalogu projektu znajduje się więcej niż jeden xproj.</span><span class="sxs-lookup"><span data-stu-id="99172-144">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="99172-145">Przykłady</span><span class="sxs-lookup"><span data-stu-id="99172-145">Examples</span></span>

<span data-ttu-id="99172-146">Migruj projekt w bieżącym katalogu i wszystkie jego zależności między projektami:</span><span class="sxs-lookup"><span data-stu-id="99172-146">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="99172-147">Migruj wszystkie projekty, które zawierają plik *Global. JSON* :</span><span class="sxs-lookup"><span data-stu-id="99172-147">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="99172-148">Migruj tylko bieżący projekt i bez zależności projekt-projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="99172-148">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="99172-149">Należy również użyć określonej wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="99172-149">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
