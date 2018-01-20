---
title: polecenie Nowy DotNet - .NET Core interfejsu wiersza polecenia
description: "Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu."
keywords: DotNet nowe interfejsu wiersza polecenia, interfejsu wiersza polecenia polecenie .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: cf65dc80f135badcb1580726a12a9ae9d94ae3d7
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="89732-104">nowe DotNet</span><span class="sxs-lookup"><span data-stu-id="89732-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="89732-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="89732-105">Name</span></span>

<span data-ttu-id="89732-106">`dotnet new`— Umożliwia utworzenie nowego projektu, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="89732-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="89732-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="89732-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="89732-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="89732-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="89732-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="89732-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="89732-110">Opis</span><span class="sxs-lookup"><span data-stu-id="89732-110">Description</span></span>

<span data-ttu-id="89732-111">`dotnet new` Polecenia oferują wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="89732-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="89732-112">Wywołania polecenia [aparatu szablonu](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="89732-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="89732-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="89732-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="89732-114">Szablon można utworzyć wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="89732-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="89732-115">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="89732-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="89732-116">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="89732-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="89732-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="89732-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="89732-118">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="89732-118">The command contains a default list of templates.</span></span> <span data-ttu-id="89732-119">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="89732-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="89732-120">W poniższej tabeli przedstawiono szablonów, które są zainstalowane przy użyciu zestawu SDK programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="89732-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="89732-121">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="89732-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="89732-122">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="89732-122">Template description</span></span>                          | <span data-ttu-id="89732-123">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="89732-123">Template name</span></span> | <span data-ttu-id="89732-124">Języki</span><span class="sxs-lookup"><span data-stu-id="89732-124">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="89732-125">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="89732-125">Console application</span></span>                          | `console`     | <span data-ttu-id="89732-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="89732-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="89732-127">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="89732-127">Class library</span></span>                                | `classlib`    | <span data-ttu-id="89732-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="89732-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="89732-129">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="89732-129">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="89732-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="89732-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="89732-131">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="89732-131">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="89732-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="89732-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="89732-133">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89732-133">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="89732-134">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89732-134">[C#], F#</span></span>      |
| <span data-ttu-id="89732-135">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="89732-135">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="89732-136">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89732-136">[C#], F#</span></span>      |
| <span data-ttu-id="89732-137">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89732-137">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="89732-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="89732-138">[C#]</span></span>          |
| <span data-ttu-id="89732-139">Platformy ASP.NET Core z dyrektywy Angular</span><span class="sxs-lookup"><span data-stu-id="89732-139">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="89732-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="89732-140">[C#]</span></span>          |
| <span data-ttu-id="89732-141">Platformy ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="89732-141">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="89732-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="89732-142">[C#]</span></span>          |
| <span data-ttu-id="89732-143">Platformy ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="89732-143">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="89732-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="89732-144">[C#]</span></span>          |
| <span data-ttu-id="89732-145">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89732-145">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="89732-146">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89732-146">[C#], F#</span></span>      |
| <span data-ttu-id="89732-147">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="89732-147">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="89732-148">Konfiguracja Nuget</span><span class="sxs-lookup"><span data-stu-id="89732-148">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="89732-149">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="89732-149">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="89732-150">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="89732-150">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="89732-151">Strona razor</span><span class="sxs-lookup"><span data-stu-id="89732-151">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="89732-152">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="89732-152">MVC/ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="89732-153">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="89732-153">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="89732-154">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="89732-154">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="89732-155">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="89732-155">The command contains a default list of templates.</span></span> <span data-ttu-id="89732-156">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="89732-156">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="89732-157">W poniższej tabeli przedstawiono szablonów, które są zainstalowane z platformą .NET Core 1.x zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="89732-157">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="89732-158">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="89732-158">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="89732-159">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="89732-159">Template description</span></span>  | <span data-ttu-id="89732-160">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="89732-160">Template name</span></span> | <span data-ttu-id="89732-161">Języki</span><span class="sxs-lookup"><span data-stu-id="89732-161">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="89732-162">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="89732-162">Console application</span></span>  | `console`     | <span data-ttu-id="89732-163">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89732-163">[C#], F#</span></span>  |
| <span data-ttu-id="89732-164">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="89732-164">Class library</span></span>        | `classlib`    | <span data-ttu-id="89732-165">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89732-165">[C#], F#</span></span>  |
| <span data-ttu-id="89732-166">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="89732-166">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="89732-167">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89732-167">[C#], F#</span></span>  |
| <span data-ttu-id="89732-168">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="89732-168">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="89732-169">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89732-169">[C#], F#</span></span>  |
| <span data-ttu-id="89732-170">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89732-170">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="89732-171">[C#]</span><span class="sxs-lookup"><span data-stu-id="89732-171">[C#]</span></span>      |
| <span data-ttu-id="89732-172">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89732-172">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="89732-173">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="89732-173">[C#], F#</span></span>  |
| <span data-ttu-id="89732-174">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89732-174">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="89732-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="89732-175">[C#]</span></span>      |
| <span data-ttu-id="89732-176">Konfiguracja Nuget</span><span class="sxs-lookup"><span data-stu-id="89732-176">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="89732-177">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="89732-177">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="89732-178">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="89732-178">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="89732-179">Opcje</span><span class="sxs-lookup"><span data-stu-id="89732-179">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="89732-180">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="89732-180">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="89732-181">Wymusza zawartość ma być generowany nawet wtedy, gdy mogłoby to zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="89732-181">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="89732-182">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="89732-182">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="89732-183">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="89732-183">Prints out help for the command.</span></span> <span data-ttu-id="89732-184">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="89732-184">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="89732-185">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="89732-185">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="89732-186">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [dotnet nowych szablonów niestandardowych](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="89732-186">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="89732-187">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="89732-187">Lists templates containing the specified name.</span></span> <span data-ttu-id="89732-188">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="89732-188">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="89732-189">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-189">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="89732-190">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="89732-190">The language of the template to create.</span></span> <span data-ttu-id="89732-191">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="89732-191">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="89732-192">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="89732-192">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="89732-193">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="89732-193">The name for the created output.</span></span> <span data-ttu-id="89732-194">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="89732-194">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="89732-195">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="89732-195">Location to place the generated output.</span></span> <span data-ttu-id="89732-196">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="89732-196">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="89732-197">Filtruje szablony oparte na dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="89732-197">Filters templates based on available types.</span></span> <span data-ttu-id="89732-198">Wstępnie zdefiniowane wartości to "Projekt", "item" lub "inne".</span><span class="sxs-lookup"><span data-stu-id="89732-198">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="89732-199">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="89732-199">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="89732-200">Aby ją odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="89732-200">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="89732-201">Na przykład *użytkowników/C:/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierający folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="89732-201">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="89732-202">Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.</span><span class="sxs-lookup"><span data-stu-id="89732-202">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="89732-203">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="89732-203">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="89732-204">Przedstawia wszystkie szablony dla określonego typu projektu, gdy działają w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="89732-204">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="89732-205">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="89732-205">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="89732-206">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="89732-206">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="89732-207">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="89732-207">Prints out help for the command.</span></span> <span data-ttu-id="89732-208">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="89732-208">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="89732-209">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="89732-209">Lists templates containing the specified name.</span></span> <span data-ttu-id="89732-210">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="89732-210">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="89732-211">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-211">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="89732-212">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="89732-212">The language of the template to create.</span></span> <span data-ttu-id="89732-213">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="89732-213">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="89732-214">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="89732-214">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="89732-215">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="89732-215">The name for the created output.</span></span> <span data-ttu-id="89732-216">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="89732-216">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="89732-217">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="89732-217">Location to place the generated output.</span></span> <span data-ttu-id="89732-218">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="89732-218">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="89732-219">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="89732-219">Template options</span></span>

<span data-ttu-id="89732-220">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="89732-220">Each project template may have additional options available.</span></span> <span data-ttu-id="89732-221">Szablony core są następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="89732-221">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="89732-222">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="89732-222">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="89732-223">**Konsola kątowego, reagować, reactredux**</span><span class="sxs-lookup"><span data-stu-id="89732-223">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="89732-224">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-224">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89732-225">**classlib**</span><span class="sxs-lookup"><span data-stu-id="89732-225">**classlib**</span></span>

<span data-ttu-id="89732-226">`-f|--framework <FRAMEWORK>`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="89732-226">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="89732-227">Wartości: `netcoreapp2.0` można utworzyć podstawowej biblioteki klas .NET lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="89732-227">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="89732-228">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="89732-228">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="89732-229">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-229">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89732-230">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="89732-230">**mstest, xunit**</span></span>

<span data-ttu-id="89732-231">`-p|--enable-pack`— Umożliwia tworzenie pakietów dla projektu za pomocą [pakiet dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="89732-231">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="89732-232">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-232">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89732-233">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="89732-233">**globaljson**</span></span>

<span data-ttu-id="89732-234">`--sdk-version <VERSION_NUMBER>`— Określa wersję platformy .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="89732-234">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="89732-235">**web**</span><span class="sxs-lookup"><span data-stu-id="89732-235">**web**</span></span>

<span data-ttu-id="89732-236">`--use-launch-settings`-Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="89732-236">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="89732-237">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-237">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89732-238">**webapi**</span><span class="sxs-lookup"><span data-stu-id="89732-238">**webapi**</span></span>

<span data-ttu-id="89732-239">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="89732-239">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="89732-240">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="89732-240">The possible values are:</span></span>

- <span data-ttu-id="89732-241">`None`-Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="89732-241">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="89732-242">`IndividualB2C`-Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="89732-242">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="89732-243">`SingleOrg`-Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="89732-243">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="89732-244">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="89732-244">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="89732-245">`--aad-b2c-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="89732-245">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="89732-246">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-246">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="89732-247">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="89732-247">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="89732-248">`-ssp|--susi-policy-id <ID>`Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-248">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="89732-249">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-249">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89732-250">`--aad-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="89732-250">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="89732-251">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-251">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="89732-252">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="89732-252">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="89732-253">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-253">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="89732-254">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-254">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="89732-255">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="89732-255">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="89732-256">`--domain <DOMAIN>`-Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="89732-256">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="89732-257">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-257">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="89732-258">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="89732-258">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="89732-259">`--tenant-id <ID>`-TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="89732-259">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="89732-260">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-260">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="89732-261">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="89732-261">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="89732-262">`-r|--org-read-access`— Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="89732-262">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="89732-263">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-263">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="89732-264">`--use-launch-settings`-Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="89732-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="89732-265">`-uld|--use-local-db`— Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="89732-265">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="89732-266">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-266">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89732-267">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-267">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89732-268">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="89732-268">**mvc, razor**</span></span>

<span data-ttu-id="89732-269">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="89732-269">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="89732-270">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="89732-270">The possible values are:</span></span>

- <span data-ttu-id="89732-271">`None`-Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="89732-271">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="89732-272">`Individual`-Poszczególnych uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-272">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="89732-273">`IndividualB2C`-Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="89732-273">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="89732-274">`SingleOrg`-Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="89732-274">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="89732-275">`MultiOrg`-Organizacji uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="89732-275">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="89732-276">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="89732-276">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="89732-277">`--aad-b2c-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="89732-277">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="89732-278">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-278">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="89732-279">Wartość domyślna to `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="89732-279">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="89732-280">`-ssp|--susi-policy-id <ID>`Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-280">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="89732-281">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-281">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89732-282">`-rp|--reset-password-policy-id <ID>`-Resetowania hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-282">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="89732-283">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89732-284">`-ep|--edit-profile-policy-id <ID>`-Edycji profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-284">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="89732-285">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89732-286">`--aad-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="89732-286">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="89732-287">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-287">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="89732-288">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="89732-288">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="89732-289">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-289">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="89732-290">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-290">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="89732-291">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="89732-291">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="89732-292">`--domain <DOMAIN>`-Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="89732-292">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="89732-293">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-293">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="89732-294">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="89732-294">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="89732-295">`--tenant-id <ID>`-TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="89732-295">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="89732-296">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-296">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="89732-297">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="89732-297">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="89732-298">`--callback-path <PATH>`— Ścieżka żądania w podstawowej ścieżce aplikacji przekierowania URI.</span><span class="sxs-lookup"><span data-stu-id="89732-298">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="89732-299">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-299">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="89732-300">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="89732-300">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="89732-301">`-r|--org-read-access`— Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="89732-301">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="89732-302">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-302">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="89732-303">`--use-launch-settings`-Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="89732-303">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="89732-304">`--use-browserlink`-Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="89732-304">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="89732-305">`-uld|--use-local-db`— Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="89732-305">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="89732-306">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89732-306">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="89732-307">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="89732-307">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="89732-308">**Strona**</span><span class="sxs-lookup"><span data-stu-id="89732-308">**page**</span></span>

<span data-ttu-id="89732-309">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="89732-309">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="89732-310">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="89732-310">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="89732-311">`-np|--no-pagemodel`-Tworzy tę stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="89732-311">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="89732-312">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="89732-312">**viewimports**</span></span>

<span data-ttu-id="89732-313">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="89732-313">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="89732-314">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="89732-314">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="89732-315">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="89732-315">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="89732-316">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="89732-316">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="89732-317">`-f|--framework`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="89732-317">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="89732-318">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="89732-318">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="89732-319">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="89732-319">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="89732-320">**classlib**</span><span class="sxs-lookup"><span data-stu-id="89732-320">**classlib**</span></span>

<span data-ttu-id="89732-321">`-f|--framework`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="89732-321">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="89732-322">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="89732-322">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="89732-323">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="89732-323">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="89732-324">**mvc**</span><span class="sxs-lookup"><span data-stu-id="89732-324">**mvc**</span></span>

<span data-ttu-id="89732-325">`-f|--framework`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="89732-325">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="89732-326">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="89732-326">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="89732-327">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="89732-327">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="89732-328">`-au|--auth`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="89732-328">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="89732-329">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="89732-329">Values: `None` or `Individual`.</span></span> <span data-ttu-id="89732-330">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="89732-330">The default value is `None`.</span></span>

<span data-ttu-id="89732-331">`-uld|--use-local-db`— Określa, czy do korzystania z bazy danych LocalDB zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="89732-331">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="89732-332">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="89732-332">Values: `true` or `false`.</span></span> <span data-ttu-id="89732-333">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="89732-333">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="89732-334">Przykłady</span><span class="sxs-lookup"><span data-stu-id="89732-334">Examples</span></span>

<span data-ttu-id="89732-335">Utworzyć projekt aplikacji konsoli F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="89732-335">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="89732-336">Utwórz .NET Standard projektu biblioteki klas w określonym katalogu (dostępne tylko z zestawu SDK programu .NET Core 2.0 lub nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="89732-336">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="89732-337">Bez uwierzytelniania przeznaczonych dla platformy .NET Core 2.0, Utwórz nowy projekt aplikacji platformy ASP.NET Core C# MVC w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="89732-337">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="89732-338">Utwórz nową aplikację xUnit przeznaczonych dla platformy .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="89732-338">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="89732-339">Lista wszystkich dostępnych szablonów dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="89732-339">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="89732-340">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89732-340">See also</span></span>

[<span data-ttu-id="89732-341">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="89732-341">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="89732-342">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="89732-342">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="89732-343">repozytorium GitHub DotNet/dotnet szablonu — przykłady</span><span class="sxs-lookup"><span data-stu-id="89732-343">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="89732-344">Dostępne szablony dla nowych dotnet</span><span class="sxs-lookup"><span data-stu-id="89732-344">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
