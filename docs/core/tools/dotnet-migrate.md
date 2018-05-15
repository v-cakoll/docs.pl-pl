---
title: polecenie - .NET Core interfejsu wiersza polecenia migracji DotNet
description: Migrowanie dotnet polecenia migruje projekt i wszystkie jego zależności.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: bdc1da5c1b70fdceac0170b2f002059a66ca5880
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-migrate"></a><span data-ttu-id="5c8f6-103">Migrowanie DotNet</span><span class="sxs-lookup"><span data-stu-id="5c8f6-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5c8f6-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5c8f6-104">Name</span></span>

<span data-ttu-id="5c8f6-105">`dotnet migrate` -Wykonuje migrację projektu Preview 2 .NET Core projekt .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5c8f6-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5c8f6-106">Synopsis</span></span>

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a><span data-ttu-id="5c8f6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5c8f6-107">Description</span></span>

<span data-ttu-id="5c8f6-108">`dotnet migrate` Polecenia migruje prawidłowy Preview 2 *project.json*— na podstawie projektu prawidłowy 1.0 zestawu SDK .NET Core *csproj* projektu.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span> 

<span data-ttu-id="5c8f6-109">Domyślnie polecenia migruje głównego projektu i odwołań do projektu, które zawiera główny projekt.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="5c8f6-110">To zachowanie zostało wyłączone za pomocą `--skip-project-references` opcji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span> 

<span data-ttu-id="5c8f6-111">Migracja odbywa się na następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5c8f6-111">Migration is performed on the following:</span></span>

* <span data-ttu-id="5c8f6-112">Pojedynczego projektu za pośrednictwem *project.json* plik do migracji.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="5c8f6-113">Wszystkie katalogi określone w *global.json* pliku, przekazując ścieżkę do *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="5c8f6-114">A *solution.sln* pliku, w którym migracją projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="5c8f6-115">Na wszystkie podkatalogi rekursywnie podanym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-115">On all sub-directories of the given directory recursively.</span></span>

<span data-ttu-id="5c8f6-116">`dotnet migrate` Polecenia śledzi migrowanych *project.json* pliku wewnątrz `backup` katalogu, który tworzy Jeśli katalog nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="5c8f6-117">To zachowanie jest zastępowany przy użyciu `--skip-backup` opcji.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="5c8f6-118">Domyślnie operacji migracji Wyświetla stan procesu migracji na wyjście standardowe (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="5c8f6-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="5c8f6-119">Jeśli używasz `--report-file <REPORT_FILE>` opcji dane wyjściowe są zapisywane do pliku określić.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span> 

<span data-ttu-id="5c8f6-120">`dotnet migrate` Polecenia obsługuje tylko prawidłowe Preview 2 *project.json*— na podstawie projektów.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="5c8f6-121">Oznacza to, że nie można użyć go do migracji DNX lub Preview 1 *project.json*— na podstawie projektów bezpośrednio do projektów MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="5c8f6-122">Najpierw należy ręcznie wykonać migrację projektu do Preview 2 *project.json*— na podstawie projektu, a następnie użycie `dotnet migrate` polecenie, aby wykonać migrację projektu.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="5c8f6-123">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5c8f6-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="5c8f6-124">Ścieżka do jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5c8f6-124">The path to one of the following:</span></span>

* <span data-ttu-id="5c8f6-125">*project.json* plik do migracji.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="5c8f6-126">*global.json* pliku, zostanie poddana migracji folderów określone w *global.json*.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-126">a *global.json* file, it will migrate the folders specified in *global.json*.</span></span>
* <span data-ttu-id="5c8f6-127">*solution.sln* pliku, zostaną zmigrowane projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-127">a *solution.sln* file, it will migrate the projects referenced in the solution.</span></span>
* <span data-ttu-id="5c8f6-128">katalog, aby przeprowadzić migrację, zostanie on rekursywnie Wyszukaj *project.json* pliki migracji.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-128">a directory to migrate, it will recursively search for *project.json* files to migrate.</span></span>

<span data-ttu-id="5c8f6-129">Wartość domyślna to bieżącego katalogu, jeśli nie określono żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="5c8f6-130">Opcje</span><span class="sxs-lookup"><span data-stu-id="5c8f6-130">Options</span></span>

`-h|--help`

<span data-ttu-id="5c8f6-131">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-131">Prints out a short help for the command.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="5c8f6-132">Plik csproj szablon do użycia na potrzeby migracji.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-132">Template csproj file to use for migration.</span></span> <span data-ttu-id="5c8f6-133">Domyślnie tego samego szablonu co porzuconych przez `dotnet new console` jest używany.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-133">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="5c8f6-134">Wersja pakietu sdk, który odwołuje się do migrowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-134">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="5c8f6-135">Wartość domyślna to wersja zestawu SDK w `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-135">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="5c8f6-136">Ścieżka do pliku xproj do użycia.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-136">The path to the xproj file to use.</span></span> <span data-ttu-id="5c8f6-137">Wymagana, gdy istnieje więcej niż jeden xproj w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-137">Required when there is more than one xproj in a project directory.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="5c8f6-138">Odwołuje się do migracji projektu SKIP.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-138">Skip migrating project references.</span></span> <span data-ttu-id="5c8f6-139">Domyślnie odwołania projektu są migrowane rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-139">By default, project references are migrated recursively.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="5c8f6-140">Raport migracji dane wyjściowe do pliku oprócz konsoli.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-140">Output migration report to a file in addition to the console.</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="5c8f6-141">Plik raportu migracji dane wyjściowe jako komunikaty JSON zamiast użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-141">Output migration report file as JSON rather than user messages.</span></span>

`--skip-backup`

<span data-ttu-id="5c8f6-142">Pomiń przenoszenie *project.json*, *global.json*, i  *\*xproj* do `backup` katalogu po pomyślnej migracji.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-142">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

## <a name="examples"></a><span data-ttu-id="5c8f6-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5c8f6-143">Examples</span></span>

<span data-ttu-id="5c8f6-144">Migracja projekt w bieżącym katalogu i wszystkich jego zależności projektu do projektu:</span><span class="sxs-lookup"><span data-stu-id="5c8f6-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="5c8f6-145">Migracja wszystkich projektów, które *global.json* plik zawiera:</span><span class="sxs-lookup"><span data-stu-id="5c8f6-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="5c8f6-146">Przeprowadź migrację tylko dla bieżącego projektu i bez zależności projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="5c8f6-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="5c8f6-147">Ponadto należy użyć określonej wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="5c8f6-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
