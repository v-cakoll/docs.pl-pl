---
title: polecenie - .NET Core interfejsu wiersza polecenia migracji DotNet
description: Migrowanie dotnet polecenia migruje projekt i wszystkie jego zależności.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 67a845f7604dededd00746fa6b74a320b3e134fa
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697108"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="ec3b7-103">Migrowanie DotNet</span><span class="sxs-lookup"><span data-stu-id="ec3b7-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ec3b7-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ec3b7-104">Name</span></span>

<span data-ttu-id="ec3b7-105">`dotnet migrate` -Wykonuje migrację projektu Preview 2 .NET Core projekt .NET Core SDK 1.0.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ec3b7-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ec3b7-106">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ec3b7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ec3b7-107">Description</span></span>

<span data-ttu-id="ec3b7-108">`dotnet migrate` Polecenia migruje prawidłowy Preview 2 *project.json*— na podstawie projektu prawidłowy 1.0 zestawu SDK .NET Core *csproj* projektu.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span>

<span data-ttu-id="ec3b7-109">Domyślnie polecenia migruje głównego projektu i odwołań do projektu, które zawiera główny projekt.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="ec3b7-110">To zachowanie zostało wyłączone za pomocą `--skip-project-references` opcji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="ec3b7-111">Można wykonać migracji na następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="ec3b7-111">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="ec3b7-112">Pojedynczego projektu za pośrednictwem *project.json* plik do migracji.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="ec3b7-113">Wszystkie katalogi określone w *global.json* pliku, przekazując ścieżkę do *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="ec3b7-114">A *solution.sln* pliku, w którym migracją projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="ec3b7-115">W podkatalogach rekursywnie podanym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-115">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="ec3b7-116">`dotnet migrate` Polecenia śledzi migrowanych *project.json* pliku wewnątrz `backup` katalogu, który tworzy Jeśli katalog nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="ec3b7-117">To zachowanie jest zastępowany przy użyciu `--skip-backup` opcji.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="ec3b7-118">Domyślnie operacji migracji Wyświetla stan procesu migracji na wyjście standardowe (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="ec3b7-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="ec3b7-119">Jeśli używasz `--report-file <REPORT_FILE>` opcji dane wyjściowe są zapisywane do pliku określić.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="ec3b7-120">`dotnet migrate` Polecenia obsługuje tylko prawidłowe Preview 2 *project.json*— na podstawie projektów.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="ec3b7-121">Oznacza to, że nie można użyć go do migracji DNX lub Preview 1 *project.json*— na podstawie projektów bezpośrednio do projektów MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="ec3b7-122">Najpierw należy ręcznie wykonać migrację projektu do Preview 2 *project.json*— na podstawie projektu, a następnie użycie `dotnet migrate` polecenie, aby wykonać migrację projektu.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="ec3b7-123">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ec3b7-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="ec3b7-124">Ścieżka do jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ec3b7-124">The path to one of the following:</span></span>

* <span data-ttu-id="ec3b7-125">*project.json* plik do migracji.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="ec3b7-126">*global.json* plik: foldery określone w *global.json* są migrowane.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-126">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="ec3b7-127">*solution.sln* plik: projekty w rozwiązaniu są migrowane.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-127">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="ec3b7-128">katalog do migracji: rekursywnie wyszukuje *project.json* plików do migracji w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-128">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="ec3b7-129">Wartość domyślna to bieżącego katalogu, jeśli nie określono żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="ec3b7-130">Opcje</span><span class="sxs-lookup"><span data-stu-id="ec3b7-130">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="ec3b7-131">Plik raportu migracji dane wyjściowe jako komunikaty JSON zamiast użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-131">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="ec3b7-132">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-132">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="ec3b7-133">Raport migracji dane wyjściowe do pliku oprócz konsoli.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-133">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="ec3b7-134">Odwołuje się do migracji projektu SKIP.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-134">Skip migrating project references.</span></span> <span data-ttu-id="ec3b7-135">Domyślnie odwołania projektu są migrowane rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-135">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="ec3b7-136">Pomiń przenoszenie *project.json*, *global.json*, i  *\*xproj* do `backup` katalogu po pomyślnej migracji.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-136">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="ec3b7-137">Plik csproj szablon do użycia na potrzeby migracji.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-137">Template csproj file to use for migration.</span></span> <span data-ttu-id="ec3b7-138">Domyślnie tego samego szablonu co porzuconych przez `dotnet new console` jest używany.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-138">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="ec3b7-139">Wersja pakietu sdk, który odwołuje się do migrowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-139">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="ec3b7-140">Wartość domyślna to wersja zestawu SDK w `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-140">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="ec3b7-141">Ścieżka do pliku xproj do użycia.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-141">The path to the xproj file to use.</span></span> <span data-ttu-id="ec3b7-142">Wymagana, gdy istnieje więcej niż jeden xproj w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="ec3b7-142">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="ec3b7-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ec3b7-143">Examples</span></span>

<span data-ttu-id="ec3b7-144">Migracja projekt w bieżącym katalogu i wszystkich jego zależności projektu do projektu:</span><span class="sxs-lookup"><span data-stu-id="ec3b7-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="ec3b7-145">Migracja wszystkich projektów, które *global.json* plik zawiera:</span><span class="sxs-lookup"><span data-stu-id="ec3b7-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="ec3b7-146">Przeprowadź migrację tylko dla bieżącego projektu i bez zależności projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="ec3b7-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="ec3b7-147">Ponadto należy użyć określonej wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ec3b7-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`