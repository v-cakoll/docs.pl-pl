---
title: polecenia DotNet migracji polecenia
description: Migrowanie dotnet polecenia migrowana projekt i wszystkie jego zależności.
ms.date: 05/25/2018
ms.openlocfilehash: 73e0169e64be4b55e10127ecca0101885061767e
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170746"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="4dfcc-103">Migrowanie DotNet</span><span class="sxs-lookup"><span data-stu-id="4dfcc-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4dfcc-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4dfcc-104">Name</span></span>

<span data-ttu-id="4dfcc-105">`dotnet migrate` -Wykonuje migrację projektów w wersji zapoznawczej 2 platformy .NET Core do projektu .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4dfcc-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="4dfcc-106">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="4dfcc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4dfcc-107">Description</span></span>

<span data-ttu-id="4dfcc-108">`dotnet migrate` Polecenia migrowana prawidłowe 2 (wersja zapoznawcza) *project.json*— na podstawie projektu prawidłowe platformy .NET Core SDK 1.0 *csproj* projektu.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span>

<span data-ttu-id="4dfcc-109">Domyślnie polecenie jest migrowana projektu głównego i odwołania do projektu, które zawiera projekt główny.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="4dfcc-110">To zachowanie jest wyłączone, za pomocą `--skip-project-references` opcji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="4dfcc-111">Można wykonać migracji następujących zasobów:</span><span class="sxs-lookup"><span data-stu-id="4dfcc-111">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="4dfcc-112">Pojedynczego projektu, określając *project.json* pliku migracji.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="4dfcc-113">Wszystkie katalogi określone w *global.json* pliku, przekazując ścieżkę do *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="4dfcc-114">A *przy* pliku, w którym przeprowadza migrację projektów, do którego odwołuje się rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="4dfcc-115">W podkatalogach cyklicznie danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-115">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="4dfcc-116">`dotnet migrate` Polecenia utrzymuje zmigrowanych *project.json* pliku wewnątrz `backup` katalogu, który tworzy, jeśli katalog nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="4dfcc-117">To zachowanie jest zastępowany przy użyciu `--skip-backup` opcji.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="4dfcc-118">Domyślnie operacji migracji Wyświetla stan procesu migracji do wyjścia standardowego (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="4dfcc-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="4dfcc-119">Jeśli używasz `--report-file <REPORT_FILE>` opcji dane wyjściowe są zapisywane do pliku określić.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="4dfcc-120">`dotnet migrate` Prawidłowe 2 (wersja zapoznawcza) obsługuje tylko polecenia *project.json*— na projektach.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="4dfcc-121">Oznacza to, że nie można użyć go do migracji środowiska DNX lub 1 (wersja zapoznawcza) *project.json*— na projektach bezpośrednio do projektów MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="4dfcc-122">Najpierw musisz ręcznie migrować projekt do wersji zapoznawczej 2 *project.json*— na podstawie projektu, a następnie użycie `dotnet migrate` polecenie, aby migrować projekt.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="4dfcc-123">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4dfcc-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="4dfcc-124">Ścieżka do jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4dfcc-124">The path to one of the following:</span></span>

* <span data-ttu-id="4dfcc-125">*project.json* pliku migracji.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="4dfcc-126">*global.json* pliku: foldery określone w *global.json* są migrowane.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-126">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="4dfcc-127">*przy* pliku: projekty, do którego odwołuje się rozwiązania są migrowane.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-127">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="4dfcc-128">katalog do migracji: rekursywnie wyszukuje *project.json* plików, aby przeprowadzić migrację w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-128">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="4dfcc-129">Wartość domyślna to bieżącego katalogu, jeśli nie określono żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="4dfcc-130">Opcje</span><span class="sxs-lookup"><span data-stu-id="4dfcc-130">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="4dfcc-131">Dane wyjściowe pliku raportu migracji jako komunikaty JSON, a nie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-131">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="4dfcc-132">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-132">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="4dfcc-133">Raport migracji dane wyjściowe do pliku, oprócz konsoli.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-133">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="4dfcc-134">Odwołuje się do pomijania migracji projektu.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-134">Skip migrating project references.</span></span> <span data-ttu-id="4dfcc-135">Domyślnie odwołania do projektu są migrowane cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-135">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="4dfcc-136">Pomiń przenoszenie *project.json*, *global.json*, i  *\*xproj* do `backup` katalogu po pomyślnej migracji.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-136">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="4dfcc-137">Plik csproj szablonu do użycia podczas migracji.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-137">Template csproj file to use for migration.</span></span> <span data-ttu-id="4dfcc-138">Domyślnie, tego samego szablonu co porzuconych przez `dotnet new console` jest używany.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-138">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="4dfcc-139">Wersja pakietu sdk, w której podano odwołanie w migrowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-139">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="4dfcc-140">Wartość domyślna to wersja zestawu SDK w `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-140">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="4dfcc-141">Ścieżka do pliku xproj do użycia.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-141">The path to the xproj file to use.</span></span> <span data-ttu-id="4dfcc-142">Wymagana, gdy istnieje więcej niż jeden xproj w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="4dfcc-142">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="4dfcc-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4dfcc-143">Examples</span></span>

<span data-ttu-id="4dfcc-144">Migracja projektu w bieżącym katalogu i wszystkich jego zależności projektu do projektu:</span><span class="sxs-lookup"><span data-stu-id="4dfcc-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="4dfcc-145">Migrowanie wszystkich projektów, które *global.json* plik zawiera:</span><span class="sxs-lookup"><span data-stu-id="4dfcc-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="4dfcc-146">Przeprowadź migrację tylko bieżącego projektu i żadne zależności projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="4dfcc-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="4dfcc-147">Ponadto należy użyć określonej wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="4dfcc-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`