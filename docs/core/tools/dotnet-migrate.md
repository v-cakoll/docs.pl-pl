---
title: polecenie migracji dotnetu
description: Polecenie migracji dotnet migruje projekt i wszystkie jego zależności.
ms.date: 02/14/2020
ms.openlocfilehash: 71f587c1bfadd445aca818448bdd5f136f009fe0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463636"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="bf0de-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="bf0de-103">dotnet migrate</span></span>

<span data-ttu-id="bf0de-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="bf0de-104">**This article applies to:** ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="bf0de-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="bf0de-105">Name</span></span>

<span data-ttu-id="bf0de-106">`dotnet migrate`- Migruje projekt w wersji zapoznawczej 2 .NET Core do projektu w stylu sdk .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bf0de-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bf0de-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="bf0de-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a><span data-ttu-id="bf0de-108">Opis</span><span class="sxs-lookup"><span data-stu-id="bf0de-108">Description</span></span>

<span data-ttu-id="bf0de-109">To polecenie jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="bf0de-109">This command is deprecated.</span></span> <span data-ttu-id="bf0de-110">Polecenie `dotnet migrate` nie jest już dostępne począwszy od pliku .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="bf0de-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="bf0de-111">Można przeprowadzić migrację tylko projektu programu Preview 2 .NET Core do projektu core 1.x .NET, który jest niew pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="bf0de-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="bf0de-112">Domyślnie polecenie migruje projekt główny i wszelkie odwołania do projektu, które zawiera projekt główny.</span><span class="sxs-lookup"><span data-stu-id="bf0de-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="bf0de-113">To zachowanie jest `--skip-project-references` wyłączone przy użyciu opcji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bf0de-113">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="bf0de-114">Migrację można przeprowadzić na następujących zasobach:</span><span class="sxs-lookup"><span data-stu-id="bf0de-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="bf0de-115">Pojedynczy projekt, określając plik *project.json* do migracji.</span><span class="sxs-lookup"><span data-stu-id="bf0de-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="bf0de-116">Wszystkie katalogi określone w pliku *global.json,* przechodząc w ścieżce do pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="bf0de-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="bf0de-117">Plik *solution.sln,* w którym migruje projekty, do których odwołuje się rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="bf0de-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="bf0de-118">We wszystkich podkatalogach danego katalogu rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="bf0de-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="bf0de-119">Polecenie `dotnet migrate` przechowuje zmigrowany plik *project.json* wewnątrz `backup` katalogu, który tworzy, jeśli katalog nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="bf0de-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="bf0de-120">To zachowanie jest zastępowane `--skip-backup` przy użyciu opcji.</span><span class="sxs-lookup"><span data-stu-id="bf0de-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="bf0de-121">Domyślnie operacja migracji wyprowadza stan procesu migracji do danych wyjściowych standardowych (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="bf0de-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="bf0de-122">Jeśli użyjesz `--report-file <REPORT_FILE>` tej opcji, dane wyjściowe są zapisywane w pliku określić.</span><span class="sxs-lookup"><span data-stu-id="bf0de-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="bf0de-123">Polecenie `dotnet migrate` obsługuje tylko prawidłowe projekty oparte na *programie Project.json*w wersji Preview 2.</span><span class="sxs-lookup"><span data-stu-id="bf0de-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="bf0de-124">Oznacza to, że nie można go używać do migracji projektów opartych na programie DNX lub Preview 1 *project.json*bezpośrednio do projektów MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="bf0de-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="bf0de-125">Najpierw należy ręcznie przeprowadzić migrację projektu do projektu opartego na programie Preview `dotnet migrate` 2 *project.json,* a następnie użyć polecenia do migracji projektu.</span><span class="sxs-lookup"><span data-stu-id="bf0de-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="bf0de-126">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bf0de-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="bf0de-127">Ścieżka do jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bf0de-127">The path to one of the following:</span></span>

* <span data-ttu-id="bf0de-128">pliku *project.json* do migracji.</span><span class="sxs-lookup"><span data-stu-id="bf0de-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="bf0de-129">plik *global.json:* foldery określone w *pliku global.json* są migrowane.</span><span class="sxs-lookup"><span data-stu-id="bf0de-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="bf0de-130">plik *solution.sln:* projekty, do których odwołuje się rozwiązanie, są migrowane.</span><span class="sxs-lookup"><span data-stu-id="bf0de-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="bf0de-131">katalog do migracji: rekursywnie wyszukuje pliki *project.json* do migracji wewnątrz określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="bf0de-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="bf0de-132">Domyślnie bieżący katalog, jeśli nic nie jest określone.</span><span class="sxs-lookup"><span data-stu-id="bf0de-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="bf0de-133">Opcje</span><span class="sxs-lookup"><span data-stu-id="bf0de-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="bf0de-134">Plik raportu migracji danych wyjściowych jako JSON, a nie wiadomości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf0de-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="bf0de-135">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="bf0de-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="bf0de-136">Raport migracji danych wyjściowych do pliku oprócz konsoli.</span><span class="sxs-lookup"><span data-stu-id="bf0de-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="bf0de-137">Pomiń migrację odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="bf0de-137">Skip migrating project references.</span></span> <span data-ttu-id="bf0de-138">Domyślnie odwołania do projektu są migrowane rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="bf0de-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="bf0de-139">Po przemień przenoszenie *pliku project.json*, *global.json*i \* \*.xproj\* do katalogu po pomyślnej `backup` migracji.</span><span class="sxs-lookup"><span data-stu-id="bf0de-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="bf0de-140">Szablon pliku csproj do użycia do migracji.</span><span class="sxs-lookup"><span data-stu-id="bf0de-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="bf0de-141">Domyślnie używany jest ten sam `dotnet new console` szablon, który został usunięty przez.</span><span class="sxs-lookup"><span data-stu-id="bf0de-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="bf0de-142">Wersja pakietu sdk, do którego odwołuje się w zmigrowanym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf0de-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="bf0de-143">Domyślna jest wersja SDK `dotnet new`w pliku .</span><span class="sxs-lookup"><span data-stu-id="bf0de-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="bf0de-144">Ścieżka do pliku xproj do użycia.</span><span class="sxs-lookup"><span data-stu-id="bf0de-144">The path to the xproj file to use.</span></span> <span data-ttu-id="bf0de-145">Wymagane, gdy w katalogu projektu znajduje się więcej niż jeden xproj.</span><span class="sxs-lookup"><span data-stu-id="bf0de-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="bf0de-146">Przykłady</span><span class="sxs-lookup"><span data-stu-id="bf0de-146">Examples</span></span>

<span data-ttu-id="bf0de-147">Migrowanie projektu w bieżącym katalogu i wszystkich jego zależnościach między projektami:</span><span class="sxs-lookup"><span data-stu-id="bf0de-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="bf0de-148">Migrowanie wszystkich projektów, które zawiera plik *global.json:*</span><span class="sxs-lookup"><span data-stu-id="bf0de-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="bf0de-149">Migrowanie tylko bieżącego projektu i bez zależności między projektem (P2P).</span><span class="sxs-lookup"><span data-stu-id="bf0de-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="bf0de-150">Należy również użyć określonej wersji SDK:</span><span class="sxs-lookup"><span data-stu-id="bf0de-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
