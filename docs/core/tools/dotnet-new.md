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
ms.openlocfilehash: f5815e1ad2a36a8ef3279f6ff83465dba9ec5d50
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="3470f-104">nowe DotNet</span><span class="sxs-lookup"><span data-stu-id="3470f-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3470f-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3470f-105">Name</span></span>

<span data-ttu-id="3470f-106">`dotnet new`— Umożliwia utworzenie nowego projektu, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="3470f-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3470f-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3470f-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3470f-108">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="3470f-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3470f-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3470f-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="3470f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3470f-110">Description</span></span>

<span data-ttu-id="3470f-111">`dotnet new` Polecenia oferują wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3470f-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="3470f-112">Wywołania polecenia [aparatu szablonu](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="3470f-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="3470f-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3470f-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="3470f-114">Szablon można utworzyć wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="3470f-115">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="3470f-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="3470f-116">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="3470f-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3470f-117">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="3470f-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="3470f-118">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="3470f-118">The command contains a default list of templates.</span></span> <span data-ttu-id="3470f-119">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="3470f-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="3470f-120">W poniższej tabeli przedstawiono szablonów, które są zainstalowane przy użyciu zestawu SDK programu .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="3470f-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="3470f-121">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="3470f-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="3470f-122">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="3470f-122">Template description</span></span>                          | <span data-ttu-id="3470f-123">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="3470f-123">Template name</span></span>  | <span data-ttu-id="3470f-124">Języki</span><span class="sxs-lookup"><span data-stu-id="3470f-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="3470f-125">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="3470f-125">Console application</span></span>                          | <span data-ttu-id="3470f-126">konsola</span><span class="sxs-lookup"><span data-stu-id="3470f-126">console</span></span>        | <span data-ttu-id="3470f-127">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="3470f-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3470f-128">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="3470f-128">Class library</span></span>                                | <span data-ttu-id="3470f-129">biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="3470f-129">classlib</span></span>       | <span data-ttu-id="3470f-130">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="3470f-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3470f-131">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="3470f-131">Unit test project</span></span>                            | <span data-ttu-id="3470f-132">mstest</span><span class="sxs-lookup"><span data-stu-id="3470f-132">mstest</span></span>         | <span data-ttu-id="3470f-133">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="3470f-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3470f-134">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="3470f-134">xUnit test project</span></span>                           | <span data-ttu-id="3470f-135">Xunit</span><span class="sxs-lookup"><span data-stu-id="3470f-135">xunit</span></span>          | <span data-ttu-id="3470f-136">[C#] F #, VB</span><span class="sxs-lookup"><span data-stu-id="3470f-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="3470f-137">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3470f-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="3470f-138">sieci Web</span><span class="sxs-lookup"><span data-stu-id="3470f-138">web</span></span>            | <span data-ttu-id="3470f-139">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="3470f-139">[C#], F#</span></span>      |
| <span data-ttu-id="3470f-140">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="3470f-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="3470f-141">MVC</span><span class="sxs-lookup"><span data-stu-id="3470f-141">mvc</span></span>            | <span data-ttu-id="3470f-142">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="3470f-142">[C#], F#</span></span>      |
| <span data-ttu-id="3470f-143">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3470f-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="3470f-144">razor</span><span class="sxs-lookup"><span data-stu-id="3470f-144">razor</span></span>          | <span data-ttu-id="3470f-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="3470f-145">[C#]</span></span>          |
| <span data-ttu-id="3470f-146">Platformy ASP.NET Core z dyrektywy Angular</span><span class="sxs-lookup"><span data-stu-id="3470f-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="3470f-147">dyrektywy angular</span><span class="sxs-lookup"><span data-stu-id="3470f-147">angular</span></span>        | <span data-ttu-id="3470f-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="3470f-148">[C#]</span></span>          |
| <span data-ttu-id="3470f-149">Platformy ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="3470f-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="3470f-150">Reakcji</span><span class="sxs-lookup"><span data-stu-id="3470f-150">react</span></span>          | <span data-ttu-id="3470f-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="3470f-151">[C#]</span></span>          |
| <span data-ttu-id="3470f-152">Platformy ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="3470f-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="3470f-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="3470f-153">reactredux</span></span>     | <span data-ttu-id="3470f-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="3470f-154">[C#]</span></span>          |
| <span data-ttu-id="3470f-155">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3470f-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="3470f-156">webapi</span><span class="sxs-lookup"><span data-stu-id="3470f-156">webapi</span></span>         | <span data-ttu-id="3470f-157">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="3470f-157">[C#], F#</span></span>      |
| <span data-ttu-id="3470f-158">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="3470f-158">global.json file</span></span>                             | <span data-ttu-id="3470f-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="3470f-159">globaljson</span></span>     |               |
| <span data-ttu-id="3470f-160">Konfiguracja Nuget</span><span class="sxs-lookup"><span data-stu-id="3470f-160">Nuget config</span></span>                                 | <span data-ttu-id="3470f-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="3470f-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="3470f-162">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="3470f-162">Web config</span></span>                                   | <span data-ttu-id="3470f-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="3470f-163">webconfig</span></span>      |               |
| <span data-ttu-id="3470f-164">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="3470f-164">Solution file</span></span>                                | <span data-ttu-id="3470f-165">SLN</span><span class="sxs-lookup"><span data-stu-id="3470f-165">sln</span></span>            |               |
| <span data-ttu-id="3470f-166">Strona razor</span><span class="sxs-lookup"><span data-stu-id="3470f-166">Razor page</span></span>                                   | <span data-ttu-id="3470f-167">strona</span><span class="sxs-lookup"><span data-stu-id="3470f-167">page</span></span>           |               |
| <span data-ttu-id="3470f-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="3470f-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="3470f-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="3470f-169">viewimports</span></span>    |               |
| <span data-ttu-id="3470f-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="3470f-170">MVC ViewStart</span></span>                                | <span data-ttu-id="3470f-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="3470f-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3470f-172">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3470f-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3470f-173">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="3470f-173">The command contains a default list of templates.</span></span> <span data-ttu-id="3470f-174">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="3470f-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="3470f-175">W poniższej tabeli przedstawiono szablonów, które są zainstalowane z platformą .NET Core 1.x zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="3470f-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="3470f-176">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="3470f-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="3470f-177">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="3470f-177">Template description</span></span>  | <span data-ttu-id="3470f-178">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="3470f-178">Template name</span></span>  | <span data-ttu-id="3470f-179">Języki</span><span class="sxs-lookup"><span data-stu-id="3470f-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="3470f-180">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="3470f-180">Console application</span></span>  | <span data-ttu-id="3470f-181">konsola</span><span class="sxs-lookup"><span data-stu-id="3470f-181">console</span></span>        | <span data-ttu-id="3470f-182">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="3470f-182">[C#], F#</span></span>  |
| <span data-ttu-id="3470f-183">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="3470f-183">Class library</span></span>        | <span data-ttu-id="3470f-184">biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="3470f-184">classlib</span></span>       | <span data-ttu-id="3470f-185">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="3470f-185">[C#], F#</span></span>  |
| <span data-ttu-id="3470f-186">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="3470f-186">Unit test project</span></span>    | <span data-ttu-id="3470f-187">mstest</span><span class="sxs-lookup"><span data-stu-id="3470f-187">mstest</span></span>         | <span data-ttu-id="3470f-188">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="3470f-188">[C#], F#</span></span>  |
| <span data-ttu-id="3470f-189">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="3470f-189">xUnit test project</span></span>   | <span data-ttu-id="3470f-190">Xunit</span><span class="sxs-lookup"><span data-stu-id="3470f-190">xunit</span></span>          | <span data-ttu-id="3470f-191">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="3470f-191">[C#], F#</span></span>  |
| <span data-ttu-id="3470f-192">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3470f-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="3470f-193">sieci Web</span><span class="sxs-lookup"><span data-stu-id="3470f-193">web</span></span>            | <span data-ttu-id="3470f-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="3470f-194">[C#]</span></span>      |
| <span data-ttu-id="3470f-195">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3470f-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="3470f-196">MVC</span><span class="sxs-lookup"><span data-stu-id="3470f-196">mvc</span></span>            | <span data-ttu-id="3470f-197">[C#] F #</span><span class="sxs-lookup"><span data-stu-id="3470f-197">[C#], F#</span></span>  |
| <span data-ttu-id="3470f-198">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3470f-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="3470f-199">webapi</span><span class="sxs-lookup"><span data-stu-id="3470f-199">webapi</span></span>         | <span data-ttu-id="3470f-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="3470f-200">[C#]</span></span>      |
| <span data-ttu-id="3470f-201">Konfiguracja Nuget</span><span class="sxs-lookup"><span data-stu-id="3470f-201">Nuget config</span></span>         | <span data-ttu-id="3470f-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="3470f-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="3470f-203">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="3470f-203">Web config</span></span>           | <span data-ttu-id="3470f-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="3470f-204">webconfig</span></span>      |           |
| <span data-ttu-id="3470f-205">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="3470f-205">Solution file</span></span>        | <span data-ttu-id="3470f-206">SLN</span><span class="sxs-lookup"><span data-stu-id="3470f-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="3470f-207">Opcje</span><span class="sxs-lookup"><span data-stu-id="3470f-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3470f-208">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="3470f-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="3470f-209">Wymusza zawartość ma być generowany nawet wtedy, gdy mogłoby to zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="3470f-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="3470f-210">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="3470f-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="3470f-211">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-211">Prints out help for the command.</span></span> <span data-ttu-id="3470f-212">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="3470f-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="3470f-213">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="3470f-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="3470f-214">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [dotnet nowych szablonów niestandardowych](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="3470f-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="3470f-215">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3470f-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="3470f-216">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="3470f-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="3470f-217">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="3470f-218">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-218">The language of the template to create.</span></span> <span data-ttu-id="3470f-219">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="3470f-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="3470f-220">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="3470f-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="3470f-221">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="3470f-221">The name for the created output.</span></span> <span data-ttu-id="3470f-222">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="3470f-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3470f-223">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3470f-223">Location to place the generated output.</span></span> <span data-ttu-id="3470f-224">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="3470f-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="3470f-225">Filtruje szablony oparte na dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="3470f-225">Filters templates based on available types.</span></span> <span data-ttu-id="3470f-226">Wstępnie zdefiniowane wartości to "Projekt", "item" lub "inne".</span><span class="sxs-lookup"><span data-stu-id="3470f-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="3470f-227">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="3470f-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="3470f-228">Aby ją odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="3470f-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="3470f-229">Na przykład *użytkowników/C:/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierający folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="3470f-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="3470f-230">Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.</span><span class="sxs-lookup"><span data-stu-id="3470f-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3470f-231">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3470f-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="3470f-232">Przedstawia wszystkie szablony dla określonego typu projektu, gdy działają w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="3470f-233">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="3470f-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="3470f-234">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="3470f-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="3470f-235">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-235">Prints out help for the command.</span></span> <span data-ttu-id="3470f-236">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="3470f-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="3470f-237">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3470f-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="3470f-238">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="3470f-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="3470f-239">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="3470f-240">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-240">The language of the template to create.</span></span> <span data-ttu-id="3470f-241">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="3470f-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="3470f-242">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="3470f-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="3470f-243">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="3470f-243">The name for the created output.</span></span> <span data-ttu-id="3470f-244">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="3470f-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3470f-245">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3470f-245">Location to place the generated output.</span></span> <span data-ttu-id="3470f-246">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="3470f-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="3470f-247">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="3470f-247">Template options</span></span>

<span data-ttu-id="3470f-248">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="3470f-248">Each project template may have additional options available.</span></span> <span data-ttu-id="3470f-249">Szablony core są następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="3470f-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3470f-250">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="3470f-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="3470f-251">**Konsola kątowego, reagować, reactredux**</span><span class="sxs-lookup"><span data-stu-id="3470f-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="3470f-252">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="3470f-253">**biblioteki klas**</span><span class="sxs-lookup"><span data-stu-id="3470f-253">**classlib**</span></span>

<span data-ttu-id="3470f-254">`-f|--framework <FRAMEWORK>`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3470f-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3470f-255">Wartości: `netcoreapp2.0` można utworzyć podstawowej biblioteki klas .NET lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3470f-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="3470f-256">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="3470f-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="3470f-257">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="3470f-258">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="3470f-258">**mstest, xunit**</span></span>

<span data-ttu-id="3470f-259">`-p|--enable-pack`— Umożliwia tworzenie pakietów dla projektu za pomocą [pakiet dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="3470f-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="3470f-260">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="3470f-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="3470f-261">**globaljson**</span></span>

<span data-ttu-id="3470f-262">`--sdk-version <VERSION_NUMBER>`— Określa wersję platformy .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="3470f-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="3470f-263">**sieci Web**</span><span class="sxs-lookup"><span data-stu-id="3470f-263">**web**</span></span>

<span data-ttu-id="3470f-264">`--use-launch-settings`-Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3470f-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="3470f-265">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="3470f-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="3470f-266">**webapi**</span></span>

<span data-ttu-id="3470f-267">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="3470f-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3470f-268">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="3470f-268">The possible values are:</span></span>

- <span data-ttu-id="3470f-269">`None`-Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3470f-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3470f-270">`IndividualB2C`-Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="3470f-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3470f-271">`SingleOrg`-Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="3470f-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3470f-272">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3470f-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3470f-273">`--aad-b2c-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3470f-274">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3470f-275">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="3470f-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="3470f-276">`-ssp|--susi-policy-id <ID>`Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3470f-277">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3470f-278">`--aad-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3470f-279">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3470f-280">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="3470f-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3470f-281">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3470f-282">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="3470f-283">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="3470f-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3470f-284">`--domain <DOMAIN>`-Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="3470f-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3470f-285">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="3470f-286">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="3470f-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3470f-287">`--tenant-id <ID>`-TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3470f-288">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="3470f-289">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="3470f-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3470f-290">`-r|--org-read-access`— Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3470f-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3470f-291">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3470f-292">`--use-launch-settings`-Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3470f-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="3470f-293">`-uld|--use-local-db`— Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="3470f-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3470f-294">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3470f-295">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="3470f-296">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="3470f-296">**mvc, razor**</span></span>

<span data-ttu-id="3470f-297">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="3470f-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="3470f-298">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="3470f-298">The possible values are:</span></span>

- <span data-ttu-id="3470f-299">`None`-Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3470f-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="3470f-300">`Individual`-Poszczególnych uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="3470f-301">`IndividualB2C`-Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="3470f-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="3470f-302">`SingleOrg`-Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="3470f-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="3470f-303">`MultiOrg`-Organizacji uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="3470f-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="3470f-304">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3470f-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="3470f-305">`--aad-b2c-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="3470f-306">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="3470f-307">Wartość domyślna to `https://login.microsoftonline.com/tfp/` .</span><span class="sxs-lookup"><span data-stu-id="3470f-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="3470f-308">`-ssp|--susi-policy-id <ID>`Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="3470f-309">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3470f-310">`-rp|--reset-password-policy-id <ID>`-Resetowania hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="3470f-311">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3470f-312">`-ep|--edit-profile-policy-id <ID>`-Edycji profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="3470f-313">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3470f-314">`--aad-instance <INSTANCE>`Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="3470f-315">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="3470f-316">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="3470f-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="3470f-317">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="3470f-318">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="3470f-319">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="3470f-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="3470f-320">`--domain <DOMAIN>`-Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="3470f-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="3470f-321">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="3470f-322">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="3470f-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="3470f-323">`--tenant-id <ID>`-TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="3470f-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="3470f-324">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="3470f-325">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="3470f-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="3470f-326">`--callback-path <PATH>`— Ścieżka żądania w podstawowej ścieżce aplikacji przekierowania URI.</span><span class="sxs-lookup"><span data-stu-id="3470f-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="3470f-327">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="3470f-328">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="3470f-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="3470f-329">`-r|--org-read-access`— Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3470f-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="3470f-330">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="3470f-331">`--use-launch-settings`-Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3470f-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="3470f-332">`--use-browserlink`-Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="3470f-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="3470f-333">`-uld|--use-local-db`— Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="3470f-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="3470f-334">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3470f-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="3470f-335">`--no-restore`-Nie wykonać przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="3470f-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="3470f-336">**Strona**</span><span class="sxs-lookup"><span data-stu-id="3470f-336">**page**</span></span>

<span data-ttu-id="3470f-337">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="3470f-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3470f-338">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="3470f-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="3470f-339">`-np|--no-pagemodel`-Tworzy tę stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="3470f-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="3470f-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="3470f-340">**viewimports**</span></span>

<span data-ttu-id="3470f-341">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="3470f-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="3470f-342">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="3470f-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3470f-343">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3470f-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3470f-344">**Konsola, xunit, mstest, sieci web, webapi**</span><span class="sxs-lookup"><span data-stu-id="3470f-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="3470f-345">`-f|--framework`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3470f-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3470f-346">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="3470f-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="3470f-347">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="3470f-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="3470f-348">**biblioteki klas**</span><span class="sxs-lookup"><span data-stu-id="3470f-348">**classlib**</span></span>

<span data-ttu-id="3470f-349">`-f|--framework`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3470f-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3470f-350">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="3470f-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="3470f-351">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="3470f-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="3470f-352">**MVC**</span><span class="sxs-lookup"><span data-stu-id="3470f-352">**mvc**</span></span>

<span data-ttu-id="3470f-353">`-f|--framework`— Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3470f-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="3470f-354">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="3470f-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="3470f-355">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="3470f-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="3470f-356">`-au|--auth`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="3470f-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="3470f-357">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="3470f-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="3470f-358">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="3470f-358">The default value is `None`.</span></span>

<span data-ttu-id="3470f-359">`-uld|--use-local-db`— Określa, czy do korzystania z bazy danych LocalDB zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="3470f-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="3470f-360">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="3470f-360">Values: `true` or `false`.</span></span> <span data-ttu-id="3470f-361">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="3470f-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="3470f-362">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3470f-362">Examples</span></span>

<span data-ttu-id="3470f-363">Utworzyć projekt aplikacji konsoli F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="3470f-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="3470f-364">Utwórz .NET Standard projektu biblioteki klas w określonym katalogu (dostępne tylko z zestawu SDK programu .NET Core 2.0 lub nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="3470f-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="3470f-365">Bez uwierzytelniania przeznaczonych dla platformy .NET Core 2.0, Utwórz nowy projekt aplikacji platformy ASP.NET Core C# MVC w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="3470f-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="3470f-366">Utwórz nową aplikację xUnit przeznaczonych dla platformy .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="3470f-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="3470f-367">Lista wszystkich dostępnych szablonów dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="3470f-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="3470f-368">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3470f-368">See also</span></span>

[<span data-ttu-id="3470f-369">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="3470f-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="3470f-370">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="3470f-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="3470f-371">repozytorium GitHub DotNet/dotnet szablonu — przykłady</span><span class="sxs-lookup"><span data-stu-id="3470f-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="3470f-372">Dostępne szablony dla nowych dotnet</span><span class="sxs-lookup"><span data-stu-id="3470f-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
