---
title: polecenia DotNet migracji polecenia
description: Migrowanie dotnet polecenia migrowana projekt i wszystkie jego zależności.
ms.date: 06/26/2019
ms.openlocfilehash: 3304f666d15d9188cdae76a401747d91791f817f
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539398"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="9fa11-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="9fa11-103">dotnet migrate</span></span>

<span data-ttu-id="9fa11-104">**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="9fa11-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="9fa11-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9fa11-105">Name</span></span>

<span data-ttu-id="9fa11-106">`dotnet migrate` -Wykonuje migrację projektów w wersji zapoznawczej 2 platformy .NET Core do projektu .NET Core SDK stylu.</span><span class="sxs-lookup"><span data-stu-id="9fa11-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

> [!NOTE]
> <span data-ttu-id="9fa11-107">`dotnet migrate` zostaną usunięte z zestawu .NET Core 3.0 SDK w następnej wersji (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="9fa11-107">`dotnet migrate` will be removed from the .NET Core 3.0 SDK in the next preview release.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9fa11-108">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9fa11-108">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9fa11-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9fa11-109">Description</span></span>

<span data-ttu-id="9fa11-110">`dotnet migrate` Polecenia migrowana prawidłowe 2 (wersja zapoznawcza) *project.json*— na podstawie projektu prawidłowy zestaw SDK platformy .NET Core — styl *csproj* projektu.</span><span class="sxs-lookup"><span data-stu-id="9fa11-110">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK-style *csproj* project.</span></span>

<span data-ttu-id="9fa11-111">Domyślnie polecenie jest migrowana projektu głównego i odwołania do projektu, które zawiera projekt główny.</span><span class="sxs-lookup"><span data-stu-id="9fa11-111">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="9fa11-112">To zachowanie jest wyłączone, za pomocą `--skip-project-references` opcji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9fa11-112">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="9fa11-113">Można wykonać migracji następujących zasobów:</span><span class="sxs-lookup"><span data-stu-id="9fa11-113">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="9fa11-114">Pojedynczego projektu, określając *project.json* pliku migracji.</span><span class="sxs-lookup"><span data-stu-id="9fa11-114">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="9fa11-115">Wszystkie katalogi określone w *global.json* pliku, przekazując ścieżkę do *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="9fa11-115">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="9fa11-116">A *przy* pliku, w którym przeprowadza migrację projektów, do którego odwołuje się rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9fa11-116">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="9fa11-117">W podkatalogach cyklicznie danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="9fa11-117">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="9fa11-118">`dotnet migrate` Polecenia utrzymuje zmigrowanych *project.json* pliku wewnątrz `backup` katalogu, który tworzy, jeśli katalog nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="9fa11-118">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="9fa11-119">To zachowanie jest zastępowany przy użyciu `--skip-backup` opcji.</span><span class="sxs-lookup"><span data-stu-id="9fa11-119">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="9fa11-120">Domyślnie operacji migracji Wyświetla stan procesu migracji do wyjścia standardowego (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="9fa11-120">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="9fa11-121">Jeśli używasz `--report-file <REPORT_FILE>` opcji dane wyjściowe są zapisywane do pliku określić.</span><span class="sxs-lookup"><span data-stu-id="9fa11-121">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="9fa11-122">`dotnet migrate` Prawidłowe 2 (wersja zapoznawcza) obsługuje tylko polecenia *project.json*— na projektach.</span><span class="sxs-lookup"><span data-stu-id="9fa11-122">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="9fa11-123">Oznacza to, że nie można użyć go do migracji środowiska DNX lub 1 (wersja zapoznawcza) *project.json*— na projektach bezpośrednio do projektów MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="9fa11-123">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="9fa11-124">Najpierw musisz ręcznie migrować projekt do wersji zapoznawczej 2 *project.json*— na podstawie projektu, a następnie użycie `dotnet migrate` polecenie, aby migrować projekt.</span><span class="sxs-lookup"><span data-stu-id="9fa11-124">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="9fa11-125">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9fa11-125">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="9fa11-126">Ścieżka do jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9fa11-126">The path to one of the following:</span></span>

* <span data-ttu-id="9fa11-127">*project.json* pliku migracji.</span><span class="sxs-lookup"><span data-stu-id="9fa11-127">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="9fa11-128">*global.json* pliku: foldery określone w *global.json* są migrowane.</span><span class="sxs-lookup"><span data-stu-id="9fa11-128">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="9fa11-129">*przy* pliku: projekty, do którego odwołuje się rozwiązania są migrowane.</span><span class="sxs-lookup"><span data-stu-id="9fa11-129">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="9fa11-130">katalog do migracji: rekursywnie wyszukuje *project.json* plików, aby przeprowadzić migrację w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9fa11-130">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="9fa11-131">Wartość domyślna to bieżącego katalogu, jeśli nie określono żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="9fa11-131">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="9fa11-132">Opcje</span><span class="sxs-lookup"><span data-stu-id="9fa11-132">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="9fa11-133">Dane wyjściowe pliku raportu migracji jako komunikaty JSON, a nie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9fa11-133">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="9fa11-134">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="9fa11-134">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="9fa11-135">Raport migracji dane wyjściowe do pliku, oprócz konsoli.</span><span class="sxs-lookup"><span data-stu-id="9fa11-135">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="9fa11-136">Odwołuje się do pomijania migracji projektu.</span><span class="sxs-lookup"><span data-stu-id="9fa11-136">Skip migrating project references.</span></span> <span data-ttu-id="9fa11-137">Domyślnie odwołania do projektu są migrowane cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="9fa11-137">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="9fa11-138">Pomiń przenoszenie *project.json*, *global.json*, i  *\*xproj* do `backup` katalogu po pomyślnej migracji.</span><span class="sxs-lookup"><span data-stu-id="9fa11-138">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="9fa11-139">Plik csproj szablonu do użycia podczas migracji.</span><span class="sxs-lookup"><span data-stu-id="9fa11-139">Template csproj file to use for migration.</span></span> <span data-ttu-id="9fa11-140">Domyślnie, tego samego szablonu co porzuconych przez `dotnet new console` jest używany.</span><span class="sxs-lookup"><span data-stu-id="9fa11-140">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="9fa11-141">Wersja pakietu sdk, w której podano odwołanie w migrowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9fa11-141">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="9fa11-142">Wartość domyślna to wersja zestawu SDK w `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="9fa11-142">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="9fa11-143">Ścieżka do pliku xproj do użycia.</span><span class="sxs-lookup"><span data-stu-id="9fa11-143">The path to the xproj file to use.</span></span> <span data-ttu-id="9fa11-144">Wymagana, gdy istnieje więcej niż jeden xproj w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="9fa11-144">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="9fa11-145">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9fa11-145">Examples</span></span>

<span data-ttu-id="9fa11-146">Migracja projektu w bieżącym katalogu i wszystkich jego zależności projektu do projektu:</span><span class="sxs-lookup"><span data-stu-id="9fa11-146">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="9fa11-147">Migrowanie wszystkich projektów, które *global.json* plik zawiera:</span><span class="sxs-lookup"><span data-stu-id="9fa11-147">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="9fa11-148">Przeprowadź migrację tylko bieżącego projektu i żadne zależności projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="9fa11-148">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="9fa11-149">Ponadto należy użyć określonej wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="9fa11-149">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
