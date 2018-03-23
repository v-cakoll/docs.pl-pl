---
title: polecenie Nowy DotNet - .NET Core interfejsu wiersza polecenia
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu.
author: mairaw
ms.author: mairaw
ms.date: 03/21/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2cbd42195d0ec713d2ccb4af823075ece950ceff
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="a206a-103">nowe DotNet</span><span class="sxs-lookup"><span data-stu-id="a206a-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a206a-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a206a-104">Name</span></span>

<span data-ttu-id="a206a-105">`dotnet new` — Umożliwia utworzenie nowego projektu, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="a206a-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a206a-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a206a-106">Synopsis</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="a206a-107">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a206a-107">.NET Core 2.0</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a206a-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a206a-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="a206a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a206a-109">Description</span></span>

<span data-ttu-id="a206a-110">`dotnet new` Polecenia oferują wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a206a-110">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="a206a-111">Wywołania polecenia [aparatu szablonu](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="a206a-111">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="a206a-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a206a-112">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="a206a-113">Szablon można utworzyć wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="a206a-114">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="a206a-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="a206a-115">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="a206a-115">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="a206a-116">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a206a-116">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="a206a-117">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="a206a-117">The command contains a default list of templates.</span></span> <span data-ttu-id="a206a-118">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="a206a-118">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="a206a-119">W poniższej tabeli przedstawiono szablonów, które są zainstalowane przy użyciu zestawu SDK programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="a206a-119">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="a206a-120">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="a206a-120">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="a206a-121">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="a206a-121">Template description</span></span>                          | <span data-ttu-id="a206a-122">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="a206a-122">Template name</span></span> | <span data-ttu-id="a206a-123">Języki</span><span class="sxs-lookup"><span data-stu-id="a206a-123">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="a206a-124">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="a206a-124">Console application</span></span>                          | `console`     | <span data-ttu-id="a206a-125">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a206a-125">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a206a-126">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="a206a-126">Class library</span></span>                                | `classlib`    | <span data-ttu-id="a206a-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a206a-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a206a-128">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="a206a-128">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="a206a-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a206a-129">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a206a-130">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="a206a-130">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="a206a-131">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="a206a-131">[C#], F#, VB</span></span>  |
| <span data-ttu-id="a206a-132">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a206a-132">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="a206a-133">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a206a-133">[C#], F#</span></span>      |
| <span data-ttu-id="a206a-134">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="a206a-134">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="a206a-135">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a206a-135">[C#], F#</span></span>      |
| <span data-ttu-id="a206a-136">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a206a-136">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="a206a-137">[C#]</span><span class="sxs-lookup"><span data-stu-id="a206a-137">[C#]</span></span>          |
| <span data-ttu-id="a206a-138">Platformy ASP.NET Core z dyrektywy Angular</span><span class="sxs-lookup"><span data-stu-id="a206a-138">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="a206a-139">[C#]</span><span class="sxs-lookup"><span data-stu-id="a206a-139">[C#]</span></span>          |
| <span data-ttu-id="a206a-140">Platformy ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="a206a-140">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="a206a-141">[C#]</span><span class="sxs-lookup"><span data-stu-id="a206a-141">[C#]</span></span>          |
| <span data-ttu-id="a206a-142">Platformy ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="a206a-142">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="a206a-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="a206a-143">[C#]</span></span>          |
| <span data-ttu-id="a206a-144">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a206a-144">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="a206a-145">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a206a-145">[C#], F#</span></span>      |
| <span data-ttu-id="a206a-146">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="a206a-146">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="a206a-147">Konfiguracja Nuget</span><span class="sxs-lookup"><span data-stu-id="a206a-147">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="a206a-148">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="a206a-148">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="a206a-149">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a206a-149">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="a206a-150">Strona razor</span><span class="sxs-lookup"><span data-stu-id="a206a-150">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="a206a-151">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="a206a-151">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="a206a-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="a206a-152">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a206a-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a206a-153">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="a206a-154">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="a206a-154">The command contains a default list of templates.</span></span> <span data-ttu-id="a206a-155">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="a206a-155">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="a206a-156">W poniższej tabeli przedstawiono szablonów, które są zainstalowane z platformą .NET Core 1.x zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a206a-156">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="a206a-157">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="a206a-157">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="a206a-158">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="a206a-158">Template description</span></span>  | <span data-ttu-id="a206a-159">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="a206a-159">Template name</span></span> | <span data-ttu-id="a206a-160">Języki</span><span class="sxs-lookup"><span data-stu-id="a206a-160">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="a206a-161">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="a206a-161">Console application</span></span>  | `console`     | <span data-ttu-id="a206a-162">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a206a-162">[C#], F#</span></span>  |
| <span data-ttu-id="a206a-163">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="a206a-163">Class library</span></span>        | `classlib`    | <span data-ttu-id="a206a-164">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a206a-164">[C#], F#</span></span>  |
| <span data-ttu-id="a206a-165">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="a206a-165">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="a206a-166">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a206a-166">[C#], F#</span></span>  |
| <span data-ttu-id="a206a-167">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="a206a-167">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="a206a-168">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a206a-168">[C#], F#</span></span>  |
| <span data-ttu-id="a206a-169">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a206a-169">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="a206a-170">[C#]</span><span class="sxs-lookup"><span data-stu-id="a206a-170">[C#]</span></span>      |
| <span data-ttu-id="a206a-171">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a206a-171">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="a206a-172">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="a206a-172">[C#], F#</span></span>  |
| <span data-ttu-id="a206a-173">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a206a-173">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="a206a-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="a206a-174">[C#]</span></span>      |
| <span data-ttu-id="a206a-175">Konfiguracja Nuget</span><span class="sxs-lookup"><span data-stu-id="a206a-175">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="a206a-176">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="a206a-176">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="a206a-177">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a206a-177">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="a206a-178">Opcje</span><span class="sxs-lookup"><span data-stu-id="a206a-178">Options</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="a206a-179">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a206a-179">.NET Core 2.0</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="a206a-180">Wymusza zawartość ma być generowany nawet wtedy, gdy mogłoby to zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="a206a-180">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="a206a-181">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a206a-181">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="a206a-182">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-182">Prints out help for the command.</span></span> <span data-ttu-id="a206a-183">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="a206a-183">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="a206a-184">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="a206a-184">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="a206a-185">Jeśli chcesz zainstalować wersji wstępnej programu pakietem szablonów, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="a206a-185">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="a206a-186">Domyślnie `dotnet new` przekazuje \* dla używanej wersji, który reprezentuje ostatniej wersji stabilnej pakietu.</span><span class="sxs-lookup"><span data-stu-id="a206a-186">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="a206a-187">Na przykład [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="a206a-187">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="a206a-188">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [dotnet nowych szablonów niestandardowych](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="a206a-188">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="a206a-189">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a206a-189">Lists templates containing the specified name.</span></span> <span data-ttu-id="a206a-190">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a206a-190">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="a206a-191">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-191">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="a206a-192">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-192">The language of the template to create.</span></span> <span data-ttu-id="a206a-193">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="a206a-193">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="a206a-194">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="a206a-194">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="a206a-195">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a206a-195">The name for the created output.</span></span> <span data-ttu-id="a206a-196">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a206a-196">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a206a-197">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a206a-197">Location to place the generated output.</span></span> <span data-ttu-id="a206a-198">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="a206a-198">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="a206a-199">Filtruje szablony oparte na dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="a206a-199">Filters templates based on available types.</span></span> <span data-ttu-id="a206a-200">Wstępnie zdefiniowane wartości to "Projekt", "item" lub "inne".</span><span class="sxs-lookup"><span data-stu-id="a206a-200">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="a206a-201">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="a206a-201">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="a206a-202">Aby ją odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a206a-202">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="a206a-203">Na przykład *użytkowników/C:/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierający folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="a206a-203">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="a206a-204">Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.</span><span class="sxs-lookup"><span data-stu-id="a206a-204">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a206a-205">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a206a-205">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="a206a-206">Przedstawia wszystkie szablony dla określonego typu projektu, gdy działają w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-206">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="a206a-207">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="a206a-207">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="a206a-208">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a206a-208">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="a206a-209">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-209">Prints out help for the command.</span></span> <span data-ttu-id="a206a-210">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="a206a-210">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="a206a-211">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a206a-211">Lists templates containing the specified name.</span></span> <span data-ttu-id="a206a-212">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a206a-212">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="a206a-213">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-213">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="a206a-214">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-214">The language of the template to create.</span></span> <span data-ttu-id="a206a-215">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="a206a-215">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="a206a-216">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="a206a-216">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="a206a-217">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a206a-217">The name for the created output.</span></span> <span data-ttu-id="a206a-218">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a206a-218">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a206a-219">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a206a-219">Location to place the generated output.</span></span> <span data-ttu-id="a206a-220">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="a206a-220">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="a206a-221">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="a206a-221">Template options</span></span>

<span data-ttu-id="a206a-222">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="a206a-222">Each project template may have additional options available.</span></span> <span data-ttu-id="a206a-223">Szablony core są następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="a206a-223">The core templates have the following additional options:</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="a206a-224">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a206a-224">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="a206a-225">**Konsola kątowego, reagować, reactredux**</span><span class="sxs-lookup"><span data-stu-id="a206a-225">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="a206a-226">`--no-restore` -Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-226">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="a206a-227">**classlib**</span><span class="sxs-lookup"><span data-stu-id="a206a-227">**classlib**</span></span>

<span data-ttu-id="a206a-228">`-f|--framework <FRAMEWORK>` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a206a-228">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a206a-229">Wartości: `netcoreapp2.0` można utworzyć podstawowej biblioteki klas .NET lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a206a-229">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="a206a-230">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="a206a-230">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="a206a-231">`--no-restore` -Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-231">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="a206a-232">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="a206a-232">**mstest, xunit**</span></span>

<span data-ttu-id="a206a-233">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakiet dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="a206a-233">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="a206a-234">`--no-restore` -Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-234">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="a206a-235">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="a206a-235">**globaljson**</span></span>

<span data-ttu-id="a206a-236">`--sdk-version <VERSION_NUMBER>` — Określa wersję platformy .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="a206a-236">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="a206a-237">**web**</span><span class="sxs-lookup"><span data-stu-id="a206a-237">**web**</span></span>

<span data-ttu-id="a206a-238">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a206a-238">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="a206a-239">`--no-restore` -Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-239">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="a206a-240">**webapi**</span><span class="sxs-lookup"><span data-stu-id="a206a-240">**webapi**</span></span>

<span data-ttu-id="a206a-241">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="a206a-241">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="a206a-242">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="a206a-242">The possible values are:</span></span>

- <span data-ttu-id="a206a-243">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a206a-243">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="a206a-244">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="a206a-244">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="a206a-245">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="a206a-245">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="a206a-246">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a206a-246">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="a206a-247">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-247">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a206a-248">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-248">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a206a-249">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="a206a-249">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="a206a-250">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-250">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a206a-251">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-251">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a206a-252">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-252">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a206a-253">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-253">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a206a-254">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="a206a-254">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="a206a-255">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-255">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="a206a-256">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-256">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="a206a-257">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="a206a-257">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="a206a-258">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="a206a-258">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="a206a-259">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-259">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="a206a-260">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="a206a-260">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="a206a-261">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-261">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a206a-262">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-262">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="a206a-263">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="a206a-263">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="a206a-264">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a206a-264">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="a206a-265">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-265">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="a206a-266">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a206a-266">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="a206a-267">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="a206a-267">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a206a-268">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-268">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a206a-269">`--no-restore` -Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-269">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="a206a-270">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="a206a-270">**mvc, razor**</span></span>

<span data-ttu-id="a206a-271">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="a206a-271">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="a206a-272">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="a206a-272">The possible values are:</span></span>

- <span data-ttu-id="a206a-273">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a206a-273">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="a206a-274">`Individual` -Poszczególnych uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-274">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="a206a-275">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="a206a-275">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="a206a-276">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="a206a-276">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="a206a-277">`MultiOrg` -Organizacji uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="a206a-277">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="a206a-278">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a206a-278">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="a206a-279">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-279">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="a206a-280">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-280">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="a206a-281">Wartość domyślna to `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="a206a-281">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="a206a-282">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-282">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="a206a-283">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a206a-284">`-rp|--reset-password-policy-id <ID>` -Resetowania hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-284">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="a206a-285">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a206a-286">`-ep|--edit-profile-policy-id <ID>` -Edycji profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-286">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="a206a-287">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-287">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a206a-288">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-288">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="a206a-289">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-289">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="a206a-290">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="a206a-290">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="a206a-291">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-291">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="a206a-292">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-292">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="a206a-293">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="a206a-293">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="a206a-294">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="a206a-294">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="a206a-295">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-295">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="a206a-296">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="a206a-296">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="a206a-297">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="a206a-297">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="a206a-298">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-298">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="a206a-299">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="a206a-299">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="a206a-300">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżce aplikacji przekierowania URI.</span><span class="sxs-lookup"><span data-stu-id="a206a-300">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="a206a-301">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-301">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="a206a-302">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="a206a-302">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="a206a-303">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a206a-303">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="a206a-304">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-304">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="a206a-305">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a206a-305">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="a206a-306">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="a206a-306">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="a206a-307">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="a206a-307">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="a206a-308">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a206a-308">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="a206a-309">`--no-restore` -Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="a206a-309">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="a206a-310">**Strona**</span><span class="sxs-lookup"><span data-stu-id="a206a-310">**page**</span></span>

<span data-ttu-id="a206a-311">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="a206a-311">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="a206a-312">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="a206a-312">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="a206a-313">`-np|--no-pagemodel` -Tworzy tę stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="a206a-313">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="a206a-314">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="a206a-314">**viewimports**</span></span>

<span data-ttu-id="a206a-315">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="a206a-315">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="a206a-316">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="a206a-316">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a206a-317">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a206a-317">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="a206a-318">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="a206a-318">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="a206a-319">`-f|--framework` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a206a-319">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a206a-320">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="a206a-320">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="a206a-321">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="a206a-321">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="a206a-322">**classlib**</span><span class="sxs-lookup"><span data-stu-id="a206a-322">**classlib**</span></span>

<span data-ttu-id="a206a-323">`-f|--framework` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a206a-323">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a206a-324">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="a206a-324">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="a206a-325">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="a206a-325">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="a206a-326">**mvc**</span><span class="sxs-lookup"><span data-stu-id="a206a-326">**mvc**</span></span>

<span data-ttu-id="a206a-327">`-f|--framework` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a206a-327">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="a206a-328">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="a206a-328">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="a206a-329">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="a206a-329">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="a206a-330">`-au|--auth` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="a206a-330">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="a206a-331">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="a206a-331">Values: `None` or `Individual`.</span></span> <span data-ttu-id="a206a-332">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="a206a-332">The default value is `None`.</span></span>

<span data-ttu-id="a206a-333">`-uld|--use-local-db` — Określa, czy do korzystania z bazy danych LocalDB zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="a206a-333">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="a206a-334">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="a206a-334">Values: `true` or `false`.</span></span> <span data-ttu-id="a206a-335">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="a206a-335">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="a206a-336">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a206a-336">Examples</span></span>

<span data-ttu-id="a206a-337">Utworzyć projekt aplikacji konsoli F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a206a-337">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="a206a-338">Utwórz .NET Standard projektu biblioteki klas w określonym katalogu (dostępne tylko z zestawu SDK programu .NET Core 2.0 lub nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="a206a-338">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="a206a-339">Bez uwierzytelniania przeznaczonych dla platformy .NET Core 2.0, Utwórz nowy projekt aplikacji platformy ASP.NET Core C# MVC w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="a206a-339">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="a206a-340">Utwórz nową aplikację xUnit przeznaczonych dla platformy .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="a206a-340">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="a206a-341">Lista wszystkich dostępnych szablonów dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="a206a-341">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="a206a-342">Zainstaluj w wersji 2.0 szablony jednej strony aplikacji dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="a206a-342">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

## <a name="see-also"></a><span data-ttu-id="a206a-343">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a206a-343">See also</span></span>

[<span data-ttu-id="a206a-344">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="a206a-344">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="a206a-345">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="a206a-345">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="a206a-346">repozytorium GitHub DotNet/dotnet szablonu — przykłady</span><span class="sxs-lookup"><span data-stu-id="a206a-346">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="a206a-347">Dostępne szablony dla nowych dotnet</span><span class="sxs-lookup"><span data-stu-id="a206a-347">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
