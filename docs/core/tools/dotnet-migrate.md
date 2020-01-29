---
title: polecenie migracji dotnet
description: Polecenie Migruj z programu dotnet migruje projekt i wszystkie jego zależności.
ms.date: 01/07/2020
ms.openlocfilehash: b81669d3e4cffeaf10bea39639410d5f06579d84
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734143"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="04608-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="04608-103">dotnet migrate</span></span>

<span data-ttu-id="04608-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK ✔️ .NET Core 2. x SDK</span><span class="sxs-lookup"><span data-stu-id="04608-104">**This article applies to:** ✔️ .NET Core 1.x SDK ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="04608-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="04608-105">Name</span></span>

<span data-ttu-id="04608-106">`dotnet migrate` — migruje projekt programu .NET Core w wersji zapoznawczej 2 do projektu w stylu zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="04608-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="04608-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="04608-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="04608-108">Opis</span><span class="sxs-lookup"><span data-stu-id="04608-108">Description</span></span>

<span data-ttu-id="04608-109">To polecenie jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="04608-109">This command is deprecated.</span></span> <span data-ttu-id="04608-110">Polecenie `dotnet migrate` nie jest już dostępne począwszy od zestawu SDK programu .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="04608-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="04608-111">Może jedynie migrować projekt .NET Core w wersji zapoznawczej 2 do projektu 1. x platformy .NET Core, który nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="04608-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="04608-112">Domyślnie polecenie migruje projekt główny i wszystkie odwołania do projektu, które zawiera projekt główny.</span><span class="sxs-lookup"><span data-stu-id="04608-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="04608-113">To zachowanie jest wyłączone przy użyciu opcji `--skip-project-references` w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="04608-113">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="04608-114">Można przeprowadzić migrację na następujących zasobach:</span><span class="sxs-lookup"><span data-stu-id="04608-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="04608-115">Pojedynczy projekt, określając plik *Project. JSON* do migracji.</span><span class="sxs-lookup"><span data-stu-id="04608-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="04608-116">Wszystkie katalogi określone w pliku *Global. JSON* przez przekazanie ścieżki do pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="04608-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="04608-117">Plik *. sln rozwiązania* , w którym migruje projekty, do których odwołuje się rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="04608-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="04608-118">Wszystkie podkatalogi danego katalogu cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="04608-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="04608-119">`dotnet migrate` polecenie zachowuje zmigrowany plik *Project. JSON* w katalogu `backup`, który tworzy, jeśli katalog nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="04608-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="04608-120">To zachowanie jest zastępowane przy użyciu opcji `--skip-backup`.</span><span class="sxs-lookup"><span data-stu-id="04608-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="04608-121">Domyślnie operacja migracji wyprowadza stan procesu migracji do wyjścia standardowego (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="04608-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="04608-122">Jeśli używasz opcji `--report-file <REPORT_FILE>`, dane wyjściowe są zapisywane w pliku Określ.</span><span class="sxs-lookup"><span data-stu-id="04608-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="04608-123">Polecenie `dotnet migrate` obsługuje tylko prawidłowe projekty w formacie *JSON*(wersja zapoznawcza 2).</span><span class="sxs-lookup"><span data-stu-id="04608-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="04608-124">Oznacza to, że nie można używać go do migrowania środowiska DNX lub podglądu 1 projektów opartych na formacie *JSON*bezpośrednio do projektów MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="04608-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="04608-125">Najpierw należy ręcznie zmigrować projekt do projektu w wersji zapoznawczej 2 *projektu. JSON*, a następnie użyć polecenia `dotnet migrate`, aby przeprowadzić migrację projektu.</span><span class="sxs-lookup"><span data-stu-id="04608-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="04608-126">Argumenty</span><span class="sxs-lookup"><span data-stu-id="04608-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="04608-127">Ścieżka do jednego z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="04608-127">The path to one of the following:</span></span>

* <span data-ttu-id="04608-128">plik *Project. JSON* do migracji.</span><span class="sxs-lookup"><span data-stu-id="04608-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="04608-129">plik *Global. JSON* : foldery określone w pliku *Global. JSON* są migrowane.</span><span class="sxs-lookup"><span data-stu-id="04608-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="04608-130">plik *. sln rozwiązania* : projekty, do których odwołuje się rozwiązanie, są migrowane.</span><span class="sxs-lookup"><span data-stu-id="04608-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="04608-131">Katalog do migracji: rekursywnie wyszukuje pliki *Project. JSON* do migracji w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="04608-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="04608-132">Jeśli nie określono niczego, domyślnie jest używany bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="04608-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="04608-133">Opcje</span><span class="sxs-lookup"><span data-stu-id="04608-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="04608-134">Wyjściowy plik raportu migracji w formacie JSON zamiast komunikatów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="04608-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="04608-135">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="04608-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="04608-136">Raport z migracji danych wyjściowych do pliku poza konsolą programu.</span><span class="sxs-lookup"><span data-stu-id="04608-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="04608-137">Pomiń Migrowanie odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="04608-137">Skip migrating project references.</span></span> <span data-ttu-id="04608-138">Domyślnie odwołania do projektu są migrowane cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="04608-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="04608-139">Pomiń przenoszenie pliku *Project. JSON*, *Global. JSON*i *\*. xproj* do katalogu `backup` po pomyślnej migracji.</span><span class="sxs-lookup"><span data-stu-id="04608-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="04608-140">Plik CSPROJ szablonu do użycia na potrzeby migracji.</span><span class="sxs-lookup"><span data-stu-id="04608-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="04608-141">Domyślnie używany jest ten sam szablon, który został porzucony przez `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="04608-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="04608-142">Wersja pakietu SDK, do którego odwołuje się migrowana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="04608-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="04608-143">Wartość domyślna to wersja zestawu SDK w `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="04608-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="04608-144">Ścieżka do pliku xproj, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="04608-144">The path to the xproj file to use.</span></span> <span data-ttu-id="04608-145">Wymagane, gdy w katalogu projektu znajduje się więcej niż jeden xproj.</span><span class="sxs-lookup"><span data-stu-id="04608-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="04608-146">Przykłady</span><span class="sxs-lookup"><span data-stu-id="04608-146">Examples</span></span>

<span data-ttu-id="04608-147">Migruj projekt w bieżącym katalogu i wszystkie jego zależności między projektami:</span><span class="sxs-lookup"><span data-stu-id="04608-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="04608-148">Migruj wszystkie projekty, które zawierają plik *Global. JSON* :</span><span class="sxs-lookup"><span data-stu-id="04608-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="04608-149">Migruj tylko bieżący projekt i bez zależności projekt-projekt (P2P).</span><span class="sxs-lookup"><span data-stu-id="04608-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="04608-150">Należy również użyć określonej wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="04608-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
