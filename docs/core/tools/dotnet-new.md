---
title: polecenie Nowy DotNet - .NET Core interfejsu wiersza polecenia
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ae24c4145cc67ca863c07e4d22af8a1c2c2dd732
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570466"
---
# <a name="dotnet-new"></a><span data-ttu-id="fb208-103">nowe DotNet</span><span class="sxs-lookup"><span data-stu-id="fb208-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="fb208-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fb208-104">Name</span></span>

<span data-ttu-id="fb208-105">`dotnet new` — Umożliwia utworzenie nowego projektu, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="fb208-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fb208-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="fb208-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fb208-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="fb208-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fb208-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fb208-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fb208-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fb208-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="fb208-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fb208-110">Description</span></span>

<span data-ttu-id="fb208-111">`dotnet new` Polecenia oferują wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fb208-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="fb208-112">Wywołania polecenia [aparatu szablonu](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="fb208-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="fb208-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fb208-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="fb208-114">Szablon można utworzyć wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="fb208-115">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="fb208-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="fb208-116">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="fb208-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fb208-117">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="fb208-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fb208-118">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="fb208-118">The command contains a default list of templates.</span></span> <span data-ttu-id="fb208-119">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="fb208-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="fb208-120">W poniższej tabeli przedstawiono szablonów, które są zainstalowane z .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="fb208-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="fb208-121">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="fb208-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="fb208-122">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="fb208-122">Template description</span></span>                          | <span data-ttu-id="fb208-123">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="fb208-123">Template name</span></span>   | <span data-ttu-id="fb208-124">Języki</span><span class="sxs-lookup"><span data-stu-id="fb208-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="fb208-125">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="fb208-125">Console application</span></span>                          | `console`       | <span data-ttu-id="fb208-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fb208-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fb208-127">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="fb208-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="fb208-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fb208-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fb208-129">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="fb208-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="fb208-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fb208-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fb208-131">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="fb208-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="fb208-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fb208-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fb208-133">Strona razor</span><span class="sxs-lookup"><span data-stu-id="fb208-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="fb208-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-134">[C#]</span></span>          |
| <span data-ttu-id="fb208-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="fb208-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="fb208-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-136">[C#]</span></span>          |
| <span data-ttu-id="fb208-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="fb208-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="fb208-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-138">[C#]</span></span>          |
| <span data-ttu-id="fb208-139">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb208-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="fb208-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-140">[C#], F#</span></span>      |
| <span data-ttu-id="fb208-141">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="fb208-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="fb208-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-142">[C#], F#</span></span>      |
| <span data-ttu-id="fb208-143">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb208-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="fb208-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-144">[C#]</span></span>          |
| <span data-ttu-id="fb208-145">Platformy ASP.NET Core z dyrektywy Angular</span><span class="sxs-lookup"><span data-stu-id="fb208-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="fb208-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-146">[C#]</span></span>          |
| <span data-ttu-id="fb208-147">Platformy ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="fb208-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="fb208-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-148">[C#]</span></span>          |
| <span data-ttu-id="fb208-149">Platformy ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="fb208-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="fb208-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-150">[C#]</span></span>          |
| <span data-ttu-id="fb208-151">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb208-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="fb208-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-152">[C#], F#</span></span>      |
| <span data-ttu-id="fb208-153">Biblioteka klas razor</span><span class="sxs-lookup"><span data-stu-id="fb208-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="fb208-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-154">[C#]</span></span>          |
| <span data-ttu-id="fb208-155">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="fb208-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="fb208-156">Konfiguracja NuGet</span><span class="sxs-lookup"><span data-stu-id="fb208-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="fb208-157">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="fb208-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="fb208-158">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fb208-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fb208-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fb208-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="fb208-160">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="fb208-160">The command contains a default list of templates.</span></span> <span data-ttu-id="fb208-161">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="fb208-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="fb208-162">W poniższej tabeli przedstawiono szablonów, które są zainstalowane .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="fb208-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="fb208-163">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="fb208-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="fb208-164">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="fb208-164">Template description</span></span>                          | <span data-ttu-id="fb208-165">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="fb208-165">Template name</span></span> | <span data-ttu-id="fb208-166">Języki</span><span class="sxs-lookup"><span data-stu-id="fb208-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="fb208-167">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="fb208-167">Console application</span></span>                          | `console`     | <span data-ttu-id="fb208-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fb208-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fb208-169">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="fb208-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="fb208-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fb208-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fb208-171">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="fb208-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="fb208-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fb208-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fb208-173">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="fb208-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="fb208-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fb208-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fb208-175">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb208-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="fb208-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-176">[C#], F#</span></span>      |
| <span data-ttu-id="fb208-177">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="fb208-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="fb208-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-178">[C#], F#</span></span>      |
| <span data-ttu-id="fb208-179">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb208-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="fb208-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-180">[C#]</span></span>          |
| <span data-ttu-id="fb208-181">Platformy ASP.NET Core z dyrektywy Angular</span><span class="sxs-lookup"><span data-stu-id="fb208-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="fb208-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-182">[C#]</span></span>          |
| <span data-ttu-id="fb208-183">Platformy ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="fb208-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="fb208-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-184">[C#]</span></span>          |
| <span data-ttu-id="fb208-185">Platformy ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="fb208-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="fb208-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-186">[C#]</span></span>          |
| <span data-ttu-id="fb208-187">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb208-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="fb208-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-188">[C#], F#</span></span>      |
| <span data-ttu-id="fb208-189">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="fb208-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="fb208-190">Konfiguracja NuGet</span><span class="sxs-lookup"><span data-stu-id="fb208-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="fb208-191">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="fb208-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="fb208-192">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fb208-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="fb208-193">Strona razor</span><span class="sxs-lookup"><span data-stu-id="fb208-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="fb208-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="fb208-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="fb208-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="fb208-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fb208-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fb208-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="fb208-197">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="fb208-197">The command contains a default list of templates.</span></span> <span data-ttu-id="fb208-198">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="fb208-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="fb208-199">W poniższej tabeli przedstawiono szablonów, które są zainstalowane przy użyciu zestawu .NET Core SDK 1.x.</span><span class="sxs-lookup"><span data-stu-id="fb208-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="fb208-200">Język domyślny dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="fb208-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="fb208-201">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="fb208-201">Template description</span></span>  | <span data-ttu-id="fb208-202">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="fb208-202">Template name</span></span> | <span data-ttu-id="fb208-203">Języki</span><span class="sxs-lookup"><span data-stu-id="fb208-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="fb208-204">Aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="fb208-204">Console application</span></span>  | `console`     | <span data-ttu-id="fb208-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-205">[C#], F#</span></span>  |
| <span data-ttu-id="fb208-206">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="fb208-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="fb208-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-207">[C#], F#</span></span>  |
| <span data-ttu-id="fb208-208">Jednostkowy projekt testowy</span><span class="sxs-lookup"><span data-stu-id="fb208-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="fb208-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-209">[C#], F#</span></span>  |
| <span data-ttu-id="fb208-210">Projekt testowy xUnit</span><span class="sxs-lookup"><span data-stu-id="fb208-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="fb208-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-211">[C#], F#</span></span>  |
| <span data-ttu-id="fb208-212">Pusty platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb208-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="fb208-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-213">[C#]</span></span>      |
| <span data-ttu-id="fb208-214">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb208-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="fb208-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fb208-215">[C#], F#</span></span>  |
| <span data-ttu-id="fb208-216">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb208-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="fb208-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="fb208-217">[C#]</span></span>      |
| <span data-ttu-id="fb208-218">Konfiguracja NuGet</span><span class="sxs-lookup"><span data-stu-id="fb208-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="fb208-219">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="fb208-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="fb208-220">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fb208-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="fb208-221">Opcje</span><span class="sxs-lookup"><span data-stu-id="fb208-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fb208-222">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="fb208-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="fb208-223">Wymusza zawartość ma być generowany nawet wtedy, gdy mogłoby to zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="fb208-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="fb208-224">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="fb208-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="fb208-225">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-225">Prints out help for the command.</span></span> <span data-ttu-id="fb208-226">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="fb208-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="fb208-227">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="fb208-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="fb208-228">Jeśli chcesz zainstalować wersji wstępnej programu pakietem szablonów, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="fb208-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="fb208-229">Domyślnie `dotnet new` przekazuje \* dla używanej wersji, który reprezentuje ostatniej wersji stabilnej pakietu.</span><span class="sxs-lookup"><span data-stu-id="fb208-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="fb208-230">Na przykład [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="fb208-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="fb208-231">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [dotnet nowych szablonów niestandardowych](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="fb208-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="fb208-232">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fb208-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="fb208-233">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="fb208-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="fb208-234">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="fb208-235">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-235">The language of the template to create.</span></span> <span data-ttu-id="fb208-236">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="fb208-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="fb208-237">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="fb208-237">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="fb208-238">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="fb208-238">The name for the created output.</span></span> <span data-ttu-id="fb208-239">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="fb208-239">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="fb208-240">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="fb208-240">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fb208-241">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb208-241">Location to place the generated output.</span></span> <span data-ttu-id="fb208-242">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="fb208-242">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="fb208-243">Filtruje szablony oparte na dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="fb208-243">Filters templates based on available types.</span></span> <span data-ttu-id="fb208-244">Wstępnie zdefiniowane wartości to "Projekt", "item" lub "inne".</span><span class="sxs-lookup"><span data-stu-id="fb208-244">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="fb208-245">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="fb208-245">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="fb208-246">Aby ją odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="fb208-246">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="fb208-247">Na przykład *użytkowników/C:/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierający folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="fb208-247">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="fb208-248">Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.</span><span class="sxs-lookup"><span data-stu-id="fb208-248">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fb208-249">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fb208-249">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="fb208-250">Wymusza zawartość ma być generowany nawet wtedy, gdy mogłoby to zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="fb208-250">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="fb208-251">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="fb208-251">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="fb208-252">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-252">Prints out help for the command.</span></span> <span data-ttu-id="fb208-253">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="fb208-253">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="fb208-254">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="fb208-254">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="fb208-255">Jeśli chcesz zainstalować wersji wstępnej programu pakietem szablonów, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="fb208-255">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="fb208-256">Domyślnie `dotnet new` przekazuje \* dla używanej wersji, który reprezentuje ostatniej wersji stabilnej pakietu.</span><span class="sxs-lookup"><span data-stu-id="fb208-256">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="fb208-257">Na przykład [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="fb208-257">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="fb208-258">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [dotnet nowych szablonów niestandardowych](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="fb208-258">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="fb208-259">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fb208-259">Lists templates containing the specified name.</span></span> <span data-ttu-id="fb208-260">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="fb208-260">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="fb208-261">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-261">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="fb208-262">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-262">The language of the template to create.</span></span> <span data-ttu-id="fb208-263">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="fb208-263">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="fb208-264">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="fb208-264">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="fb208-265">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="fb208-265">The name for the created output.</span></span> <span data-ttu-id="fb208-266">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="fb208-266">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fb208-267">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb208-267">Location to place the generated output.</span></span> <span data-ttu-id="fb208-268">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="fb208-268">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="fb208-269">Filtruje szablony oparte na dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="fb208-269">Filters templates based on available types.</span></span> <span data-ttu-id="fb208-270">Wstępnie zdefiniowane wartości to "Projekt", "item" lub "inne".</span><span class="sxs-lookup"><span data-stu-id="fb208-270">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="fb208-271">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="fb208-271">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="fb208-272">Aby ją odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="fb208-272">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="fb208-273">Na przykład *użytkowników/C:/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierający folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="fb208-273">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="fb208-274">Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.</span><span class="sxs-lookup"><span data-stu-id="fb208-274">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fb208-275">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fb208-275">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="fb208-276">Przedstawia wszystkie szablony dla określonego typu projektu, gdy działają w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-276">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="fb208-277">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="fb208-277">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="fb208-278">Jest to wymagane, jeśli projekt zawiera już do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="fb208-278">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="fb208-279">Drukuje pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-279">Prints out help for the command.</span></span> <span data-ttu-id="fb208-280">Może być wywoływany dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="fb208-280">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="fb208-281">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fb208-281">Lists templates containing the specified name.</span></span> <span data-ttu-id="fb208-282">Jeśli wywołane `dotnet new` polecenie wyświetla listę szablonów możliwości dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="fb208-282">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="fb208-283">Na przykład jeśli katalog zawiera już projekt, nie listy wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-283">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="fb208-284">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-284">The language of the template to create.</span></span> <span data-ttu-id="fb208-285">Język zaakceptowane, jest zależna od szablonu (zobacz ustawień domyślnych w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="fb208-285">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="fb208-286">Nie jest prawidłowy dla pewnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="fb208-286">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="fb208-287">Nazwa utworzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="fb208-287">The name for the created output.</span></span> <span data-ttu-id="fb208-288">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="fb208-288">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fb208-289">Lokalizacji do umieszczenia wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb208-289">Location to place the generated output.</span></span> <span data-ttu-id="fb208-290">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="fb208-290">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="fb208-291">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="fb208-291">Template options</span></span>

<span data-ttu-id="fb208-292">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="fb208-292">Each project template may have additional options available.</span></span> <span data-ttu-id="fb208-293">Szablony core są następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="fb208-293">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fb208-294">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="fb208-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fb208-295">**platformy react, reactredux, razorclasslib w konsoli, dyrektywy angular**</span><span class="sxs-lookup"><span data-stu-id="fb208-295">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="fb208-296">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-296">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-297">**classlib**</span><span class="sxs-lookup"><span data-stu-id="fb208-297">**classlib**</span></span>

<span data-ttu-id="fb208-298">`-f|--framework <FRAMEWORK>` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fb208-298">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fb208-299">Wartości: `netcoreapp2.0` można utworzyć podstawowej biblioteki klas .NET lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="fb208-299">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="fb208-300">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="fb208-300">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="fb208-301">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-301">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-302">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="fb208-302">**mstest, xunit**</span></span>

<span data-ttu-id="fb208-303">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakiet dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="fb208-303">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="fb208-304">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-305">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="fb208-305">**globaljson**</span></span>

<span data-ttu-id="fb208-306">`--sdk-version <VERSION_NUMBER>` — Określa wersję platformy .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="fb208-306">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="fb208-307">**web**</span><span class="sxs-lookup"><span data-stu-id="fb208-307">**web**</span></span>

<span data-ttu-id="fb208-308">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb208-308">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fb208-309">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-310">**webapi**</span><span class="sxs-lookup"><span data-stu-id="fb208-310">**webapi**</span></span>

<span data-ttu-id="fb208-311">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="fb208-311">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fb208-312">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="fb208-312">The possible values are:</span></span>

- <span data-ttu-id="fb208-313">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fb208-313">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fb208-314">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="fb208-314">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fb208-315">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="fb208-315">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fb208-316">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fb208-316">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fb208-317">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-317">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fb208-318">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-318">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-319">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="fb208-319">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="fb208-320">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-320">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fb208-321">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-321">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-322">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-322">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fb208-323">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-323">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fb208-324">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="fb208-324">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fb208-325">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-325">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fb208-326">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-326">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="fb208-327">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="fb208-327">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fb208-328">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="fb208-328">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fb208-329">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-329">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-330">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="fb208-330">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fb208-331">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-331">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fb208-332">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fb208-333">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="fb208-333">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fb208-334">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb208-334">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fb208-335">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-335">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fb208-336">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb208-336">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fb208-337">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="fb208-337">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fb208-338">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-338">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-339">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-339">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-340">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="fb208-340">**mvc, razor**</span></span>

<span data-ttu-id="fb208-341">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="fb208-341">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fb208-342">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="fb208-342">The possible values are:</span></span>

- <span data-ttu-id="fb208-343">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fb208-343">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fb208-344">`Individual` -Poszczególnych uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-344">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="fb208-345">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="fb208-345">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fb208-346">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="fb208-346">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fb208-347">`MultiOrg` -Organizacji uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="fb208-347">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="fb208-348">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fb208-348">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fb208-349">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-349">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fb208-350">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-350">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-351">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="fb208-351">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="fb208-352">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-352">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fb208-353">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-353">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-354">`-rp|--reset-password-policy-id <ID>` -Resetowania hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-354">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="fb208-355">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-355">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-356">`-ep|--edit-profile-policy-id <ID>` -Edycji profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-356">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="fb208-357">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-357">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-358">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-358">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fb208-359">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-359">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="fb208-360">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="fb208-360">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fb208-361">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-361">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fb208-362">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-362">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="fb208-363">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="fb208-363">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fb208-364">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="fb208-364">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fb208-365">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-365">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-366">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="fb208-366">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fb208-367">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-367">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fb208-368">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-368">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fb208-369">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="fb208-369">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fb208-370">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżce aplikacji przekierowania URI.</span><span class="sxs-lookup"><span data-stu-id="fb208-370">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="fb208-371">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-372">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="fb208-372">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="fb208-373">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb208-373">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fb208-374">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-374">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fb208-375">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb208-375">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fb208-376">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="fb208-376">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="fb208-377">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="fb208-377">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fb208-378">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-378">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-379">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-379">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-380">**Strona**</span><span class="sxs-lookup"><span data-stu-id="fb208-380">**page**</span></span>

<span data-ttu-id="fb208-381">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="fb208-381">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fb208-382">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="fb208-382">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="fb208-383">`-np|--no-pagemodel` -Tworzy tę stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="fb208-383">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="fb208-384">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="fb208-384">**viewimports**</span></span>

<span data-ttu-id="fb208-385">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="fb208-385">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fb208-386">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="fb208-386">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fb208-387">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fb208-387">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="fb208-388">**Konsola kątowego, reagować, reactredux**</span><span class="sxs-lookup"><span data-stu-id="fb208-388">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="fb208-389">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-389">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-390">**classlib**</span><span class="sxs-lookup"><span data-stu-id="fb208-390">**classlib**</span></span>

<span data-ttu-id="fb208-391">`-f|--framework <FRAMEWORK>` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fb208-391">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fb208-392">Wartości: `netcoreapp2.0` można utworzyć podstawowej biblioteki klas .NET lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="fb208-392">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="fb208-393">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="fb208-393">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="fb208-394">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-395">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="fb208-395">**mstest, xunit**</span></span>

<span data-ttu-id="fb208-396">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakiet dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="fb208-396">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="fb208-397">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-397">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-398">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="fb208-398">**globaljson**</span></span>

<span data-ttu-id="fb208-399">`--sdk-version <VERSION_NUMBER>` — Określa wersję platformy .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="fb208-399">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="fb208-400">**web**</span><span class="sxs-lookup"><span data-stu-id="fb208-400">**web**</span></span>

<span data-ttu-id="fb208-401">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb208-401">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fb208-402">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-402">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-403">**webapi**</span><span class="sxs-lookup"><span data-stu-id="fb208-403">**webapi**</span></span>

<span data-ttu-id="fb208-404">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="fb208-404">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fb208-405">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="fb208-405">The possible values are:</span></span>

- <span data-ttu-id="fb208-406">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fb208-406">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fb208-407">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="fb208-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fb208-408">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="fb208-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fb208-409">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fb208-409">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fb208-410">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-410">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fb208-411">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-412">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="fb208-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="fb208-413">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-413">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fb208-414">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-414">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-415">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-415">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fb208-416">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-416">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fb208-417">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="fb208-417">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fb208-418">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-418">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fb208-419">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-419">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="fb208-420">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="fb208-420">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fb208-421">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="fb208-421">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fb208-422">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-422">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-423">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="fb208-423">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fb208-424">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-424">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fb208-425">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-425">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fb208-426">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="fb208-426">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fb208-427">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb208-427">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fb208-428">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-428">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fb208-429">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb208-429">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fb208-430">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="fb208-430">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fb208-431">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-431">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-432">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-432">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-433">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="fb208-433">**mvc, razor**</span></span>

<span data-ttu-id="fb208-434">`-au|--auth <AUTHENTICATION_TYPE>` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="fb208-434">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fb208-435">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="fb208-435">The possible values are:</span></span>

- <span data-ttu-id="fb208-436">`None` -Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fb208-436">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fb208-437">`Individual` -Poszczególnych uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-437">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="fb208-438">`IndividualB2C` -Poszczególnych uwierzytelniania za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="fb208-438">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fb208-439">`SingleOrg` -Organizacji uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="fb208-439">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fb208-440">`MultiOrg` -Organizacji uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="fb208-440">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="fb208-441">`Windows` — Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fb208-441">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fb208-442">`--aad-b2c-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory B2C do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-442">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fb208-443">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-443">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-444">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="fb208-444">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="fb208-445">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-445">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fb208-446">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-446">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-447">`-rp|--reset-password-policy-id <ID>` -Resetowania hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-447">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="fb208-448">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-448">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-449">`-ep|--edit-profile-policy-id <ID>` -Edycji profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-449">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="fb208-450">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-450">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-451">`--aad-instance <INSTANCE>` Wystąpienia usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-451">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fb208-452">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-452">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="fb208-453">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="fb208-453">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fb208-454">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-454">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fb208-455">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-455">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="fb208-456">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="fb208-456">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fb208-457">`--domain <DOMAIN>` -Domeny dla katalogu dzierżawcy.</span><span class="sxs-lookup"><span data-stu-id="fb208-457">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fb208-458">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-458">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-459">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="fb208-459">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fb208-460">`--tenant-id <ID>` -TenantId identyfikator katalogu do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb208-460">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fb208-461">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-461">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fb208-462">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="fb208-462">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fb208-463">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżce aplikacji przekierowania URI.</span><span class="sxs-lookup"><span data-stu-id="fb208-463">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="fb208-464">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fb208-465">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="fb208-465">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="fb208-466">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb208-466">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fb208-467">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-467">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fb208-468">`--use-launch-settings` -Zawiera *launchSettings.json* w wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb208-468">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fb208-469">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="fb208-469">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="fb208-470">`-uld|--use-local-db` — Określa, że LocalDB powinna być używana zamiast funkcji SQLite.</span><span class="sxs-lookup"><span data-stu-id="fb208-470">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fb208-471">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb208-471">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fb208-472">`--no-restore` — Nie jest wykonywana niejawne przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="fb208-472">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fb208-473">**Strona**</span><span class="sxs-lookup"><span data-stu-id="fb208-473">**page**</span></span>

<span data-ttu-id="fb208-474">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="fb208-474">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fb208-475">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="fb208-475">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="fb208-476">`-np|--no-pagemodel` -Tworzy tę stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="fb208-476">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="fb208-477">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="fb208-477">**viewimports**</span></span>

<span data-ttu-id="fb208-478">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="fb208-478">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fb208-479">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="fb208-479">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fb208-480">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fb208-480">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="fb208-481">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="fb208-481">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="fb208-482">`-f|--framework` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fb208-482">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fb208-483">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="fb208-483">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="fb208-484">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="fb208-484">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="fb208-485">**classlib**</span><span class="sxs-lookup"><span data-stu-id="fb208-485">**classlib**</span></span>

<span data-ttu-id="fb208-486">`-f|--framework` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fb208-486">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fb208-487">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="fb208-487">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="fb208-488">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="fb208-488">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="fb208-489">**mvc**</span><span class="sxs-lookup"><span data-stu-id="fb208-489">**mvc**</span></span>

<span data-ttu-id="fb208-490">`-f|--framework` — Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fb208-490">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fb208-491">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="fb208-491">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="fb208-492">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="fb208-492">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="fb208-493">`-au|--auth` — Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="fb208-493">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="fb208-494">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="fb208-494">Values: `None` or `Individual`.</span></span> <span data-ttu-id="fb208-495">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="fb208-495">The default value is `None`.</span></span>

<span data-ttu-id="fb208-496">`-uld|--use-local-db` — Określa, czy do korzystania z bazy danych LocalDB zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="fb208-496">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="fb208-497">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="fb208-497">Values: `true` or `false`.</span></span> <span data-ttu-id="fb208-498">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="fb208-498">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="fb208-499">Przykłady</span><span class="sxs-lookup"><span data-stu-id="fb208-499">Examples</span></span>

<span data-ttu-id="fb208-500">Utworzyć projekt aplikacji konsoli F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="fb208-500">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="fb208-501">Utwórz .NET Standard projektu biblioteki klas w określonym katalogu (dostępne tylko z .NET Core SDK w wersji 2.0 lub nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="fb208-501">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="fb208-502">Bez uwierzytelniania przeznaczonych dla platformy .NET Core 2.0, Utwórz nowy projekt aplikacji platformy ASP.NET Core C# MVC w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="fb208-502">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="fb208-503">Utwórz nową aplikację xUnit przeznaczonych dla platformy .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="fb208-503">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="fb208-504">Lista wszystkich dostępnych szablonów dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="fb208-504">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="fb208-505">Zainstaluj w wersji 2.0 szablony jednej strony aplikacji dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="fb208-505">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="fb208-506">Utwórz *global.json* w bieżącym katalogu ustawienie zestawu SDK w wersji 2.0.0 (dostępne tylko z .NET Core SDK w wersji 2.0 lub nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="fb208-506">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="fb208-507">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb208-507">See also</span></span>

[<span data-ttu-id="fb208-508">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="fb208-508">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="fb208-509">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="fb208-509">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="fb208-510">repozytorium GitHub DotNet/dotnet szablonu — przykłady</span><span class="sxs-lookup"><span data-stu-id="fb208-510">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="fb208-511">Dostępne szablony dla nowych dotnet</span><span class="sxs-lookup"><span data-stu-id="fb208-511">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)