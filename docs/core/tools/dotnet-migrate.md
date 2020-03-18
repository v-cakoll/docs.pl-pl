---
title: polecenie migracji dotnet
description: Polecenie migracji dotnetu migruje projekt i wszystkie jego zależności.
ms.date: 02/14/2020
ms.openlocfilehash: 6148048c469c43320cc4459352fd2fb62f101740
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503699"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="745f1-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="745f1-103">dotnet migrate</span></span>

<span data-ttu-id="745f1-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="745f1-104">**This article applies to:** ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="745f1-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="745f1-105">Name</span></span>

<span data-ttu-id="745f1-106">`dotnet migrate`- Migruje projekt Preview 2 .NET Core do projektu w stylu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="745f1-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="745f1-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="745f1-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="745f1-108">Opis</span><span class="sxs-lookup"><span data-stu-id="745f1-108">Description</span></span>

<span data-ttu-id="745f1-109">To polecenie jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="745f1-109">This command is deprecated.</span></span> <span data-ttu-id="745f1-110">Polecenie `dotnet migrate` nie jest już dostępne, począwszy od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="745f1-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="745f1-111">Można migrować tylko podgląd 2 .NET Core projektu do 1.x .NET Core projektu, który jest bez obsługi.</span><span class="sxs-lookup"><span data-stu-id="745f1-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="745f1-112">Domyślnie polecenie migruje projekt główny i wszelkie odwołania do projektu, które zawiera projekt główny.</span><span class="sxs-lookup"><span data-stu-id="745f1-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="745f1-113">To zachowanie jest wyłączone `--skip-project-references` przy użyciu opcji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="745f1-113">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="745f1-114">Migracja może być wykonywana na następujących zasobach:</span><span class="sxs-lookup"><span data-stu-id="745f1-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="745f1-115">Pojedynczy projekt, określając plik *project.json* do migracji.</span><span class="sxs-lookup"><span data-stu-id="745f1-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="745f1-116">Wszystkie katalogi określone w pliku *global.json* przez przekazywanie w ścieżce do pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="745f1-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="745f1-117">Plik *solution.sln,* w którym przeprowadza migrację projektów, do których odwołuje się rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="745f1-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="745f1-118">We wszystkich podkatalogach danego katalogu rekurencyjne.</span><span class="sxs-lookup"><span data-stu-id="745f1-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="745f1-119">Polecenie `dotnet migrate` przechowuje zmigrowany plik *project.json* wewnątrz `backup` katalogu, który tworzy, jeśli katalog nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="745f1-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="745f1-120">To zachowanie jest zastępowane `--skip-backup` przy użyciu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="745f1-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="745f1-121">Domyślnie operacja migracji wyprowadza stan procesu migracji do standardowego wyjścia (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="745f1-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="745f1-122">Jeśli użyjesz `--report-file <REPORT_FILE>` tej opcji, dane wyjściowe zostaną zapisane w pliku określ.</span><span class="sxs-lookup"><span data-stu-id="745f1-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="745f1-123">Polecenie `dotnet migrate` obsługuje tylko prawidłowe projekty oparte na *programie Project.json*w wersji Preview 2.</span><span class="sxs-lookup"><span data-stu-id="745f1-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="745f1-124">Oznacza to, że nie można go używać do migracji projektów opartych na programie DNX lub Preview 1 *project.json*bezpośrednio do projektów MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="745f1-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="745f1-125">Najpierw należy ręcznie przeprowadzić migrację projektu do projektu opartego na projekcie Preview `dotnet migrate` *2,json,* a następnie użyć polecenia do migracji projektu.</span><span class="sxs-lookup"><span data-stu-id="745f1-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="745f1-126">Argumenty</span><span class="sxs-lookup"><span data-stu-id="745f1-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="745f1-127">Ścieżka do jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="745f1-127">The path to one of the following:</span></span>

* <span data-ttu-id="745f1-128">pliku *project.json* do migracji.</span><span class="sxs-lookup"><span data-stu-id="745f1-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="745f1-129">plik *global.json:* foldery określone w *global.json* są migrowane.</span><span class="sxs-lookup"><span data-stu-id="745f1-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="745f1-130">plik *solution.sln:* projekty, do których odwołuje się rozwiązanie, są migrowane.</span><span class="sxs-lookup"><span data-stu-id="745f1-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="745f1-131">katalog do migracji: rekurencyjne wyszukiwanie plików *project.json* do migracji wewnątrz określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="745f1-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="745f1-132">Domyślnie do bieżącego katalogu, jeśli nic nie jest określone.</span><span class="sxs-lookup"><span data-stu-id="745f1-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="745f1-133">Opcje</span><span class="sxs-lookup"><span data-stu-id="745f1-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="745f1-134">Plik raportu migracji wyjściowej jako JSON, a nie komunikaty użytkownika.</span><span class="sxs-lookup"><span data-stu-id="745f1-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="745f1-135">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="745f1-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="745f1-136">Raport migracji wyjściowej do pliku oprócz konsoli.</span><span class="sxs-lookup"><span data-stu-id="745f1-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="745f1-137">Pomiń migracji odwołań do projektu.</span><span class="sxs-lookup"><span data-stu-id="745f1-137">Skip migrating project references.</span></span> <span data-ttu-id="745f1-138">Domyślnie odwołania do projektu są migrowane cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="745f1-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="745f1-139">Po zakończeniu migracji pomiń *przenoszenie project.json*, `backup` *global.json*i \* \*.xproj\* do katalogu.</span><span class="sxs-lookup"><span data-stu-id="745f1-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="745f1-140">Szablon pliku csproj do użycia do migracji.</span><span class="sxs-lookup"><span data-stu-id="745f1-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="745f1-141">Domyślnie używany jest ten sam szablon, który został usunięty. `dotnet new console`</span><span class="sxs-lookup"><span data-stu-id="745f1-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="745f1-142">Wersja pakietu sdk, do której odwołuje się zmigrowana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="745f1-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="745f1-143">Wartością domyślną jest wersja sdk w `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="745f1-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="745f1-144">Ścieżka do pliku xproj do użycia.</span><span class="sxs-lookup"><span data-stu-id="745f1-144">The path to the xproj file to use.</span></span> <span data-ttu-id="745f1-145">Wymagane, gdy w katalogu projektu znajduje się więcej niż jeden xproj.</span><span class="sxs-lookup"><span data-stu-id="745f1-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="745f1-146">Przykłady</span><span class="sxs-lookup"><span data-stu-id="745f1-146">Examples</span></span>

<span data-ttu-id="745f1-147">Migracja projektu w bieżącym katalogu i wszystkich jego zależności projektu do projektu:</span><span class="sxs-lookup"><span data-stu-id="745f1-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="745f1-148">Migracja wszystkich projektów, które zawiera plik *global.json:*</span><span class="sxs-lookup"><span data-stu-id="745f1-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="745f1-149">Migracja tylko bieżącego projektu i żadnych zależności projektu do projektu (P2P).</span><span class="sxs-lookup"><span data-stu-id="745f1-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="745f1-150">Należy również użyć określonej wersji sdk:</span><span class="sxs-lookup"><span data-stu-id="745f1-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
