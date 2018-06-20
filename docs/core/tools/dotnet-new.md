---
title: polecenie Nowy DotNet - .NET Core interfejsu wiersza polecenia
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu.
author: mairaw
ms.author: mairaw
ms.date: 06/12/2018
ms.openlocfilehash: f0ef91361dfbc2c2ba5532fbd607786289e98c69
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208328"
---
# <a name="dotnet-new"></a><span data-ttu-id="64cfa-103">nowe DotNet</span><span class="sxs-lookup"><span data-stu-id="64cfa-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="64cfa-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="64cfa-104">Name</span></span>

<span data-ttu-id="64cfa-105">`dotnet new` — Umożliwia utworzenie nowego projektu, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="64cfa-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="64cfa-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="64cfa-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="64cfa-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="64cfa-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="64cfa-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="64cfa-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="64cfa-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="64cfa-110">Opis</span><span class="sxs-lookup"><span data-stu-id="64cfa-110">Description</span></span>

<span data-ttu-id="64cfa-111">`dotnet new` Polecenia oferują wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64cfa-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="64cfa-112">Wywołania polecenia [aparatu szablonu](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="64cfa-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="64cfa-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="64cfa-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="64cfa-114">Szablon można utworzyć wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="64cfa-115">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="64cfa-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="64cfa-116">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="64cfa-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="64cfa-117">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="64cfa-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="64cfa-118">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-118">The command contains a default list of templates.</span></span> <span data-ttu-id="64cfa-119">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="64cfa-120">W poniższej tabeli przedstawiono szablonów, które są zainstalowane z .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="64cfa-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="64cfa-121">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="64cfa-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="64cfa-122">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="64cfa-122">Template description</span></span>                          | <span data-ttu-id="64cfa-123">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="64cfa-123">Template name</span></span>   | <span data-ttu-id="64cfa-124">Języki</span><span class="sxs-lookup"><span data-stu-id="64cfa-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="64cfa-125">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="64cfa-125">Console application</span></span>                          | `console`       | <span data-ttu-id="64cfa-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="64cfa-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="64cfa-127">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="64cfa-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="64cfa-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="64cfa-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="64cfa-129">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="64cfa-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="64cfa-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="64cfa-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="64cfa-131">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="64cfa-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="64cfa-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="64cfa-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="64cfa-133">Strona razor</span><span class="sxs-lookup"><span data-stu-id="64cfa-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="64cfa-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-134">[C#]</span></span>          |
| <span data-ttu-id="64cfa-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="64cfa-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="64cfa-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-136">[C#]</span></span>          |
| <span data-ttu-id="64cfa-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="64cfa-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="64cfa-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-138">[C#]</span></span>          |
| <span data-ttu-id="64cfa-139">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64cfa-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="64cfa-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-140">[C#], F#</span></span>      |
| <span data-ttu-id="64cfa-141">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="64cfa-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="64cfa-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-142">[C#], F#</span></span>      |
| <span data-ttu-id="64cfa-143">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64cfa-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="64cfa-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-144">[C#]</span></span>          |
| <span data-ttu-id="64cfa-145">Platformy ASP.NET Core z dyrektywy Angular</span><span class="sxs-lookup"><span data-stu-id="64cfa-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="64cfa-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-146">[C#]</span></span>          |
| <span data-ttu-id="64cfa-147">Platformy ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="64cfa-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="64cfa-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-148">[C#]</span></span>          |
| <span data-ttu-id="64cfa-149">Platformy ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="64cfa-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="64cfa-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-150">[C#]</span></span>          |
| <span data-ttu-id="64cfa-151">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64cfa-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="64cfa-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-152">[C#], F#</span></span>      |
| <span data-ttu-id="64cfa-153">Biblioteka klas razor</span><span class="sxs-lookup"><span data-stu-id="64cfa-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="64cfa-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-154">[C#]</span></span>          |
| <span data-ttu-id="64cfa-155">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="64cfa-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="64cfa-156">Konfiguracja NuGet</span><span class="sxs-lookup"><span data-stu-id="64cfa-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="64cfa-157">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="64cfa-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="64cfa-158">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="64cfa-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="64cfa-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="64cfa-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="64cfa-160">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-160">The command contains a default list of templates.</span></span> <span data-ttu-id="64cfa-161">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="64cfa-162">W poniższej tabeli przedstawiono szablonów, które są zainstalowane .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="64cfa-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="64cfa-163">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="64cfa-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="64cfa-164">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="64cfa-164">Template description</span></span>                          | <span data-ttu-id="64cfa-165">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="64cfa-165">Template name</span></span> | <span data-ttu-id="64cfa-166">Języki</span><span class="sxs-lookup"><span data-stu-id="64cfa-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="64cfa-167">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="64cfa-167">Console application</span></span>                          | `console`     | <span data-ttu-id="64cfa-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="64cfa-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="64cfa-169">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="64cfa-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="64cfa-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="64cfa-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="64cfa-171">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="64cfa-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="64cfa-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="64cfa-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="64cfa-173">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="64cfa-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="64cfa-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="64cfa-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="64cfa-175">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64cfa-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="64cfa-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-176">[C#], F#</span></span>      |
| <span data-ttu-id="64cfa-177">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="64cfa-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="64cfa-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-178">[C#], F#</span></span>      |
| <span data-ttu-id="64cfa-179">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64cfa-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="64cfa-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-180">[C#]</span></span>          |
| <span data-ttu-id="64cfa-181">Platformy ASP.NET Core z dyrektywy Angular</span><span class="sxs-lookup"><span data-stu-id="64cfa-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="64cfa-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-182">[C#]</span></span>          |
| <span data-ttu-id="64cfa-183">Platformy ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="64cfa-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="64cfa-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-184">[C#]</span></span>          |
| <span data-ttu-id="64cfa-185">Platformy ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="64cfa-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="64cfa-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-186">[C#]</span></span>          |
| <span data-ttu-id="64cfa-187">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64cfa-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="64cfa-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-188">[C#], F#</span></span>      |
| <span data-ttu-id="64cfa-189">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="64cfa-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="64cfa-190">Konfiguracja NuGet</span><span class="sxs-lookup"><span data-stu-id="64cfa-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="64cfa-191">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="64cfa-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="64cfa-192">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="64cfa-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="64cfa-193">Strona razor</span><span class="sxs-lookup"><span data-stu-id="64cfa-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="64cfa-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="64cfa-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="64cfa-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="64cfa-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="64cfa-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="64cfa-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="64cfa-197">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-197">The command contains a default list of templates.</span></span> <span data-ttu-id="64cfa-198">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="64cfa-199">W poniższej tabeli przedstawiono szablonów, które są zainstalowane przy użyciu zestawu .NET Core SDK 1.x.</span><span class="sxs-lookup"><span data-stu-id="64cfa-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="64cfa-200">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="64cfa-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="64cfa-201">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="64cfa-201">Template description</span></span>  | <span data-ttu-id="64cfa-202">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="64cfa-202">Template name</span></span> | <span data-ttu-id="64cfa-203">Języki</span><span class="sxs-lookup"><span data-stu-id="64cfa-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="64cfa-204">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="64cfa-204">Console application</span></span>  | `console`     | <span data-ttu-id="64cfa-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-205">[C#], F#</span></span>  |
| <span data-ttu-id="64cfa-206">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="64cfa-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="64cfa-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-207">[C#], F#</span></span>  |
| <span data-ttu-id="64cfa-208">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="64cfa-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="64cfa-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-209">[C#], F#</span></span>  |
| <span data-ttu-id="64cfa-210">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="64cfa-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="64cfa-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-211">[C#], F#</span></span>  |
| <span data-ttu-id="64cfa-212">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64cfa-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="64cfa-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-213">[C#]</span></span>      |
| <span data-ttu-id="64cfa-214">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64cfa-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="64cfa-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="64cfa-215">[C#], F#</span></span>  |
| <span data-ttu-id="64cfa-216">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64cfa-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="64cfa-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="64cfa-217">[C#]</span></span>      |
| <span data-ttu-id="64cfa-218">Konfiguracja NuGet</span><span class="sxs-lookup"><span data-stu-id="64cfa-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="64cfa-219">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="64cfa-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="64cfa-220">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="64cfa-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="64cfa-221">Opcje</span><span class="sxs-lookup"><span data-stu-id="64cfa-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="64cfa-222">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="64cfa-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="64cfa-223">Wymusza zawartość ma być generowany nawet wtedy, gdy mogłoby to zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="64cfa-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="64cfa-224">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="64cfa-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="64cfa-225">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-225">Prints out help for the command.</span></span> <span data-ttu-id="64cfa-226">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="64cfa-227">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="64cfa-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="64cfa-228">Jeśli chcesz zainstalować wersji wstępnej programu pakietem szablonów, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="64cfa-229">Domyślnie `dotnet new` przekazuje \* dla używanej wersji, który reprezentuje ostatniej wersji stabilnej pakietu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="64cfa-230">Na przykład [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="64cfa-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="64cfa-231">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [dotnet nowych szablonów niestandardowych](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="64cfa-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="64cfa-232">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="64cfa-233">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="64cfa-234">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="64cfa-235">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-235">The language of the template to create.</span></span> <span data-ttu-id="64cfa-236">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="64cfa-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="64cfa-237">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="64cfa-238">Niektóre powłok zinterpretować `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="64cfa-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="64cfa-239">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="64cfa-240">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="64cfa-240">The name for the created output.</span></span> <span data-ttu-id="64cfa-241">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="64cfa-242">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="64cfa-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="64cfa-243">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64cfa-243">Location to place the generated output.</span></span> <span data-ttu-id="64cfa-244">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="64cfa-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="64cfa-245">Filtruje szablony oparte na dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-245">Filters templates based on available types.</span></span> <span data-ttu-id="64cfa-246">Wstępnie zdefiniowane wartości to "Projekt", "item" lub "inne".</span><span class="sxs-lookup"><span data-stu-id="64cfa-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="64cfa-247">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="64cfa-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="64cfa-248">Aby ją odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="64cfa-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="64cfa-249">Na przykład *użytkowników/C:/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierający folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="64cfa-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="64cfa-250">Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="64cfa-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="64cfa-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="64cfa-252">Wymusza zawartość ma być generowany nawet wtedy, gdy mogłoby to zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="64cfa-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="64cfa-253">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="64cfa-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="64cfa-254">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-254">Prints out help for the command.</span></span> <span data-ttu-id="64cfa-255">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="64cfa-256">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="64cfa-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="64cfa-257">Jeśli chcesz zainstalować wersji wstępnej programu pakietem szablonów, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="64cfa-258">Domyślnie `dotnet new` przekazuje \* dla używanej wersji, który reprezentuje ostatniej wersji stabilnej pakietu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="64cfa-259">Na przykład [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="64cfa-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="64cfa-260">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [dotnet nowych szablonów niestandardowych](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="64cfa-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="64cfa-261">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="64cfa-262">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="64cfa-263">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="64cfa-264">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-264">The language of the template to create.</span></span> <span data-ttu-id="64cfa-265">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="64cfa-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="64cfa-266">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="64cfa-267">Niektóre powłok zinterpretować `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="64cfa-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="64cfa-268">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="64cfa-269">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="64cfa-269">The name for the created output.</span></span> <span data-ttu-id="64cfa-270">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="64cfa-271">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64cfa-271">Location to place the generated output.</span></span> <span data-ttu-id="64cfa-272">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="64cfa-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="64cfa-273">Filtruje szablony oparte na dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-273">Filters templates based on available types.</span></span> <span data-ttu-id="64cfa-274">Wstępnie zdefiniowane wartości to "Projekt", "item" lub "inne".</span><span class="sxs-lookup"><span data-stu-id="64cfa-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="64cfa-275">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="64cfa-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="64cfa-276">Aby ją odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="64cfa-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="64cfa-277">Na przykład *użytkowników/C:/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierający folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="64cfa-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="64cfa-278">Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="64cfa-279">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="64cfa-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="64cfa-280">Przedstawia wszystkie szablony dla określonego typu projektu, gdy działają w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="64cfa-281">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="64cfa-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="64cfa-282">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="64cfa-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="64cfa-283">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-283">Prints out help for the command.</span></span> <span data-ttu-id="64cfa-284">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="64cfa-285">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="64cfa-286">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="64cfa-287">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="64cfa-288">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-288">The language of the template to create.</span></span> <span data-ttu-id="64cfa-289">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="64cfa-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="64cfa-290">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="64cfa-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="64cfa-291">Niektóre powłok zinterpretować `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="64cfa-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="64cfa-292">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="64cfa-293">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="64cfa-293">The name for the created output.</span></span> <span data-ttu-id="64cfa-294">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="64cfa-295">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64cfa-295">Location to place the generated output.</span></span> <span data-ttu-id="64cfa-296">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="64cfa-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="64cfa-297">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="64cfa-297">Template options</span></span>

<span data-ttu-id="64cfa-298">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="64cfa-298">Each project template may have additional options available.</span></span> <span data-ttu-id="64cfa-299">Szablony core są następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="64cfa-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="64cfa-300">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="64cfa-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="64cfa-301">**platformy react, reactredux, razorclasslib w konsoli, dyrektywy angular**</span><span class="sxs-lookup"><span data-stu-id="64cfa-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="64cfa-302">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-303">**classlib**</span><span class="sxs-lookup"><span data-stu-id="64cfa-303">**classlib**</span></span>

<span data-ttu-id="64cfa-304">`-f|--framework <FRAMEWORK>` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="64cfa-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="64cfa-305">Wartości: `netcoreapp2.0` można utworzyć podstawowej biblioteki klas .NET lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="64cfa-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="64cfa-306">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="64cfa-307">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-308">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="64cfa-308">**mstest, xunit**</span></span>

<span data-ttu-id="64cfa-309">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakiet dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="64cfa-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="64cfa-310">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="64cfa-311">**globaljson**</span></span>

<span data-ttu-id="64cfa-312">`--sdk-version <VERSION_NUMBER>` — Określa wersję platformy .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="64cfa-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="64cfa-313">**web**</span><span class="sxs-lookup"><span data-stu-id="64cfa-313">**web**</span></span>

<span data-ttu-id="64cfa-314">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64cfa-314">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="64cfa-315">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-316">**webapi**</span><span class="sxs-lookup"><span data-stu-id="64cfa-316">**webapi**</span></span>

<span data-ttu-id="64cfa-317">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-317">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="64cfa-318">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="64cfa-318">The possible values are:</span></span>

- <span data-ttu-id="64cfa-319">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="64cfa-319">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="64cfa-320">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="64cfa-320">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="64cfa-321">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-321">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="64cfa-322">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="64cfa-322">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="64cfa-323">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-323">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="64cfa-324">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-324">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-325">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-325">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="64cfa-326">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-326">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="64cfa-327">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-327">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-328">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-328">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="64cfa-329">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-329">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="64cfa-330">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-330">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="64cfa-331">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-331">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="64cfa-332">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-332">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="64cfa-333">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-333">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="64cfa-334">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-334">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="64cfa-335">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-335">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-336">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-336">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="64cfa-337">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-337">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="64cfa-338">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-338">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="64cfa-339">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-339">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="64cfa-340">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64cfa-340">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="64cfa-341">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-341">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="64cfa-342">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64cfa-342">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="64cfa-343">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="64cfa-343">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="64cfa-344">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-344">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-345">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-345">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-346">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="64cfa-346">**mvc, razor**</span></span>

<span data-ttu-id="64cfa-347">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-347">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="64cfa-348">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="64cfa-348">The possible values are:</span></span>

- <span data-ttu-id="64cfa-349">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="64cfa-349">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="64cfa-350">`Individual` -Poszczególnych uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-350">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="64cfa-351">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="64cfa-351">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="64cfa-352">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-352">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="64cfa-353">`MultiOrg` -Organizacji uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="64cfa-353">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="64cfa-354">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="64cfa-354">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="64cfa-355">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-355">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="64cfa-356">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-356">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-357">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-357">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="64cfa-358">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-358">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="64cfa-359">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-359">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-360">`-rp|--reset-password-policy-id <ID>` -Resetowania hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-360">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="64cfa-361">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-361">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-362">`-ep|--edit-profile-policy-id <ID>` -Edycji profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-362">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="64cfa-363">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-363">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-364">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-364">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="64cfa-365">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-365">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="64cfa-366">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-366">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="64cfa-367">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-367">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="64cfa-368">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-368">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="64cfa-369">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-369">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="64cfa-370">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-370">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="64cfa-371">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-372">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-372">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="64cfa-373">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-373">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="64cfa-374">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-374">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="64cfa-375">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-375">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="64cfa-376">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżce aplikacji przekierowania URI.</span><span class="sxs-lookup"><span data-stu-id="64cfa-376">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="64cfa-377">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-378">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-378">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="64cfa-379">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64cfa-379">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="64cfa-380">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-380">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="64cfa-381">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64cfa-381">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="64cfa-382">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="64cfa-382">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="64cfa-383">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="64cfa-383">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="64cfa-384">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-384">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-385">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-385">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-386">**Strona**</span><span class="sxs-lookup"><span data-stu-id="64cfa-386">**page**</span></span>

<span data-ttu-id="64cfa-387">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-387">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="64cfa-388">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-388">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="64cfa-389">`-np|--no-pagemodel` -Tworzy tę stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="64cfa-389">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="64cfa-390">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="64cfa-390">**viewimports**</span></span>

<span data-ttu-id="64cfa-391">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-391">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="64cfa-392">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-392">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="64cfa-393">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="64cfa-393">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="64cfa-394">**Konsola kątowego, reagować, reactredux**</span><span class="sxs-lookup"><span data-stu-id="64cfa-394">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="64cfa-395">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-395">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-396">**classlib**</span><span class="sxs-lookup"><span data-stu-id="64cfa-396">**classlib**</span></span>

<span data-ttu-id="64cfa-397">`-f|--framework <FRAMEWORK>` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="64cfa-397">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="64cfa-398">Wartości: `netcoreapp2.0` można utworzyć podstawowej biblioteki klas .NET lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="64cfa-398">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="64cfa-399">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-399">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="64cfa-400">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-400">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-401">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="64cfa-401">**mstest, xunit**</span></span>

<span data-ttu-id="64cfa-402">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakiet dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="64cfa-402">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="64cfa-403">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-404">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="64cfa-404">**globaljson**</span></span>

<span data-ttu-id="64cfa-405">`--sdk-version <VERSION_NUMBER>` — Określa wersję platformy .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="64cfa-405">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="64cfa-406">**web**</span><span class="sxs-lookup"><span data-stu-id="64cfa-406">**web**</span></span>

<span data-ttu-id="64cfa-407">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64cfa-407">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="64cfa-408">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-409">**webapi**</span><span class="sxs-lookup"><span data-stu-id="64cfa-409">**webapi**</span></span>

<span data-ttu-id="64cfa-410">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-410">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="64cfa-411">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="64cfa-411">The possible values are:</span></span>

- <span data-ttu-id="64cfa-412">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="64cfa-412">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="64cfa-413">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="64cfa-413">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="64cfa-414">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-414">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="64cfa-415">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="64cfa-415">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="64cfa-416">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-416">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="64cfa-417">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-417">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-418">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-418">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="64cfa-419">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-419">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="64cfa-420">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-420">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-421">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-421">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="64cfa-422">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-422">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="64cfa-423">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-423">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="64cfa-424">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-424">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="64cfa-425">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-425">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="64cfa-426">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="64cfa-427">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-427">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="64cfa-428">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-429">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-429">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="64cfa-430">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-430">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="64cfa-431">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="64cfa-432">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="64cfa-433">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64cfa-433">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="64cfa-434">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-434">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="64cfa-435">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64cfa-435">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="64cfa-436">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="64cfa-436">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="64cfa-437">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-437">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-438">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-438">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-439">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="64cfa-439">**mvc, razor**</span></span>

<span data-ttu-id="64cfa-440">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-440">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="64cfa-441">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="64cfa-441">The possible values are:</span></span>

- <span data-ttu-id="64cfa-442">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="64cfa-442">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="64cfa-443">`Individual` -Poszczególnych uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-443">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="64cfa-444">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="64cfa-444">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="64cfa-445">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-445">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="64cfa-446">`MultiOrg` -Organizacji uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="64cfa-446">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="64cfa-447">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="64cfa-447">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="64cfa-448">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-448">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="64cfa-449">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-449">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-450">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-450">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="64cfa-451">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-451">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="64cfa-452">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-452">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-453">`-rp|--reset-password-policy-id <ID>` -Resetowania hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-453">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="64cfa-454">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-454">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-455">`-ep|--edit-profile-policy-id <ID>` -Edycji profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-455">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="64cfa-456">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-456">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-457">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-457">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="64cfa-458">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-458">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="64cfa-459">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-459">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="64cfa-460">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-460">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="64cfa-461">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-461">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="64cfa-462">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-462">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="64cfa-463">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="64cfa-463">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="64cfa-464">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-465">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-465">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="64cfa-466">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-466">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="64cfa-467">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-467">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="64cfa-468">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-468">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="64cfa-469">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżce aplikacji przekierowania URI.</span><span class="sxs-lookup"><span data-stu-id="64cfa-469">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="64cfa-470">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-470">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="64cfa-471">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-471">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="64cfa-472">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64cfa-472">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="64cfa-473">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-473">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="64cfa-474">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64cfa-474">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="64cfa-475">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="64cfa-475">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="64cfa-476">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="64cfa-476">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="64cfa-477">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64cfa-477">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="64cfa-478">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-478">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="64cfa-479">**Strona**</span><span class="sxs-lookup"><span data-stu-id="64cfa-479">**page**</span></span>

<span data-ttu-id="64cfa-480">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-480">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="64cfa-481">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-481">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="64cfa-482">`-np|--no-pagemodel` -Tworzy tę stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="64cfa-482">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="64cfa-483">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="64cfa-483">**viewimports**</span></span>

<span data-ttu-id="64cfa-484">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="64cfa-484">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="64cfa-485">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-485">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="64cfa-486">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="64cfa-486">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="64cfa-487">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="64cfa-487">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="64cfa-488">`-f|--framework` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="64cfa-488">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="64cfa-489">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-489">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="64cfa-490">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-490">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="64cfa-491">**classlib**</span><span class="sxs-lookup"><span data-stu-id="64cfa-491">**classlib**</span></span>

<span data-ttu-id="64cfa-492">`-f|--framework` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="64cfa-492">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="64cfa-493">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-493">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="64cfa-494">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-494">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="64cfa-495">**mvc**</span><span class="sxs-lookup"><span data-stu-id="64cfa-495">**mvc**</span></span>

<span data-ttu-id="64cfa-496">`-f|--framework` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="64cfa-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="64cfa-497">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="64cfa-498">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="64cfa-499">`-au|--auth` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="64cfa-499">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="64cfa-500">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-500">Values: `None` or `Individual`.</span></span> <span data-ttu-id="64cfa-501">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-501">The default value is `None`.</span></span>

<span data-ttu-id="64cfa-502">`-uld|--use-local-db` — Określa, czy do korzystania z bazy danych LocalDB zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="64cfa-502">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="64cfa-503">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-503">Values: `true` or `false`.</span></span> <span data-ttu-id="64cfa-504">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="64cfa-504">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="64cfa-505">Przykłady</span><span class="sxs-lookup"><span data-stu-id="64cfa-505">Examples</span></span>

<span data-ttu-id="64cfa-506">Utworzyć projekt aplikacji konsoli F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="64cfa-506">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="64cfa-507">Utwórz .NET Standard projektu biblioteki klas w określonym katalogu (dostępne tylko z .NET Core SDK w wersji 2.0 lub nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="64cfa-507">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="64cfa-508">Utwórz nowy projekt aplikacji platformy ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="64cfa-508">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="64cfa-509">Utwórz nową aplikację xUnit:</span><span class="sxs-lookup"><span data-stu-id="64cfa-509">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="64cfa-510">Lista wszystkich dostępnych szablonów dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="64cfa-510">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="64cfa-511">Zainstaluj w wersji 2.0 szablony jednej strony aplikacji dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="64cfa-511">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="64cfa-512">Utwórz *global.json* w bieżącym katalogu ustawienie zestawu SDK w wersji 2.0.0 (dostępne tylko z .NET Core SDK w wersji 2.0 lub nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="64cfa-512">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="64cfa-513">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64cfa-513">See also</span></span>

[<span data-ttu-id="64cfa-514">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="64cfa-514">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="64cfa-515">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="64cfa-515">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="64cfa-516">repozytorium GitHub DotNet/dotnet szablonu — przykłady</span><span class="sxs-lookup"><span data-stu-id="64cfa-516">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="64cfa-517">Dostępne szablony dla nowych dotnet</span><span class="sxs-lookup"><span data-stu-id="64cfa-517">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
