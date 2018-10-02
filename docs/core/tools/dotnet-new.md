---
title: polecenia DotNet nowego polecenia — interfejs wiersza polecenia platformy .NET Core
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core, na podstawie określonego szablonu.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 396c4ddf09854fa4582226bdb1422f8c929e459b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036133"
---
# <a name="dotnet-new"></a><span data-ttu-id="4fad1-103">nowe polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="4fad1-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4fad1-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4fad1-104">Name</span></span>

<span data-ttu-id="4fad1-105">`dotnet new` -Tworzy nowy projekt, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4fad1-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="4fad1-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4fad1-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4fad1-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4fad1-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4fad1-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4fad1-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4fad1-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="4fad1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4fad1-110">Description</span></span>

<span data-ttu-id="4fad1-111">`dotnet new` Polecenia oferuje wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4fad1-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="4fad1-112">Wywołuje polecenie [aparatu szablonów](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="4fad1-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="4fad1-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4fad1-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="4fad1-114">Szablon do utworzenia wystąpienia podczas wywoływania polecenia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="4fad1-115">Każdy szablon może być określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="4fad1-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="4fad1-116">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="4fad1-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4fad1-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4fad1-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="4fad1-118">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-118">The command contains a default list of templates.</span></span> <span data-ttu-id="4fad1-119">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4fad1-120">W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="4fad1-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="4fad1-121">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="4fad1-122">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="4fad1-122">Template description</span></span>                          | <span data-ttu-id="4fad1-123">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="4fad1-123">Template name</span></span>   | <span data-ttu-id="4fad1-124">Języki</span><span class="sxs-lookup"><span data-stu-id="4fad1-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="4fad1-125">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="4fad1-125">Console application</span></span>                          | `console`       | <span data-ttu-id="4fad1-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4fad1-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4fad1-127">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="4fad1-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="4fad1-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4fad1-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4fad1-129">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="4fad1-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="4fad1-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4fad1-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4fad1-131">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="4fad1-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="4fad1-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4fad1-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4fad1-133">Strona razor</span><span class="sxs-lookup"><span data-stu-id="4fad1-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="4fad1-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-134">[C#]</span></span>          |
| <span data-ttu-id="4fad1-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="4fad1-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="4fad1-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-136">[C#]</span></span>          |
| <span data-ttu-id="4fad1-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="4fad1-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="4fad1-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-138">[C#]</span></span>          |
| <span data-ttu-id="4fad1-139">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="4fad1-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="4fad1-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-140">[C#], F#</span></span>      |
| <span data-ttu-id="4fad1-141">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="4fad1-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="4fad1-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-142">[C#], F#</span></span>      |
| <span data-ttu-id="4fad1-143">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4fad1-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="4fad1-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-144">[C#]</span></span>          |
| <span data-ttu-id="4fad1-145">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="4fad1-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="4fad1-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-146">[C#]</span></span>          |
| <span data-ttu-id="4fad1-147">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="4fad1-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="4fad1-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-148">[C#]</span></span>          |
| <span data-ttu-id="4fad1-149">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="4fad1-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="4fad1-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-150">[C#]</span></span>          |
| <span data-ttu-id="4fad1-151">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4fad1-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="4fad1-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-152">[C#], F#</span></span>      |
| <span data-ttu-id="4fad1-153">Biblioteki klas razor</span><span class="sxs-lookup"><span data-stu-id="4fad1-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="4fad1-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-154">[C#]</span></span>          |
| <span data-ttu-id="4fad1-155">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="4fad1-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="4fad1-156">NuGet config</span><span class="sxs-lookup"><span data-stu-id="4fad1-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="4fad1-157">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="4fad1-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="4fad1-158">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4fad1-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4fad1-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4fad1-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="4fad1-160">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-160">The command contains a default list of templates.</span></span> <span data-ttu-id="4fad1-161">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="4fad1-162">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą platformy .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="4fad1-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="4fad1-163">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="4fad1-164">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="4fad1-164">Template description</span></span>                          | <span data-ttu-id="4fad1-165">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="4fad1-165">Template name</span></span> | <span data-ttu-id="4fad1-166">Języki</span><span class="sxs-lookup"><span data-stu-id="4fad1-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="4fad1-167">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="4fad1-167">Console application</span></span>                          | `console`     | <span data-ttu-id="4fad1-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4fad1-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4fad1-169">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="4fad1-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="4fad1-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4fad1-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4fad1-171">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="4fad1-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="4fad1-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4fad1-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4fad1-173">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="4fad1-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="4fad1-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="4fad1-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="4fad1-175">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="4fad1-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="4fad1-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-176">[C#], F#</span></span>      |
| <span data-ttu-id="4fad1-177">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="4fad1-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="4fad1-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-178">[C#], F#</span></span>      |
| <span data-ttu-id="4fad1-179">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4fad1-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="4fad1-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-180">[C#]</span></span>          |
| <span data-ttu-id="4fad1-181">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="4fad1-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="4fad1-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-182">[C#]</span></span>          |
| <span data-ttu-id="4fad1-183">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="4fad1-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="4fad1-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-184">[C#]</span></span>          |
| <span data-ttu-id="4fad1-185">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="4fad1-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="4fad1-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-186">[C#]</span></span>          |
| <span data-ttu-id="4fad1-187">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4fad1-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="4fad1-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-188">[C#], F#</span></span>      |
| <span data-ttu-id="4fad1-189">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="4fad1-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="4fad1-190">NuGet config</span><span class="sxs-lookup"><span data-stu-id="4fad1-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="4fad1-191">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="4fad1-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="4fad1-192">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4fad1-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="4fad1-193">Strona razor</span><span class="sxs-lookup"><span data-stu-id="4fad1-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="4fad1-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="4fad1-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="4fad1-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="4fad1-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4fad1-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4fad1-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4fad1-197">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-197">The command contains a default list of templates.</span></span> <span data-ttu-id="4fad1-198">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="4fad1-199">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą zestawu SDK programu .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="4fad1-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="4fad1-200">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="4fad1-201">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="4fad1-201">Template description</span></span>  | <span data-ttu-id="4fad1-202">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="4fad1-202">Template name</span></span> | <span data-ttu-id="4fad1-203">Języki</span><span class="sxs-lookup"><span data-stu-id="4fad1-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="4fad1-204">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="4fad1-204">Console application</span></span>  | `console`     | <span data-ttu-id="4fad1-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-205">[C#], F#</span></span>  |
| <span data-ttu-id="4fad1-206">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="4fad1-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="4fad1-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-207">[C#], F#</span></span>  |
| <span data-ttu-id="4fad1-208">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="4fad1-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="4fad1-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-209">[C#], F#</span></span>  |
| <span data-ttu-id="4fad1-210">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="4fad1-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="4fad1-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-211">[C#], F#</span></span>  |
| <span data-ttu-id="4fad1-212">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="4fad1-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="4fad1-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-213">[C#]</span></span>      |
| <span data-ttu-id="4fad1-214">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4fad1-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="4fad1-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="4fad1-215">[C#], F#</span></span>  |
| <span data-ttu-id="4fad1-216">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4fad1-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="4fad1-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="4fad1-217">[C#]</span></span>      |
| <span data-ttu-id="4fad1-218">NuGet config</span><span class="sxs-lookup"><span data-stu-id="4fad1-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="4fad1-219">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="4fad1-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="4fad1-220">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4fad1-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="4fad1-221">Opcje</span><span class="sxs-lookup"><span data-stu-id="4fad1-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4fad1-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4fad1-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="4fad1-223">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="4fad1-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4fad1-224">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4fad1-225">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-225">Prints out help for the command.</span></span> <span data-ttu-id="4fad1-226">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="4fad1-227">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="4fad1-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4fad1-228">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4fad1-229">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="4fad1-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="4fad1-230">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="4fad1-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="4fad1-231">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4fad1-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="4fad1-232">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="4fad1-233">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4fad1-234">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="4fad1-235">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-235">The language of the template to create.</span></span> <span data-ttu-id="4fad1-236">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="4fad1-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4fad1-237">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4fad1-238">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="4fad1-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4fad1-239">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4fad1-240">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4fad1-240">The name for the created output.</span></span> <span data-ttu-id="4fad1-241">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="4fad1-242">Określa źródła pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="4fad1-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4fad1-243">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4fad1-243">Location to place the generated output.</span></span> <span data-ttu-id="4fad1-244">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="4fad1-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="4fad1-245">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-245">Filters templates based on available types.</span></span> <span data-ttu-id="4fad1-246">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="4fad1-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="4fad1-247">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="4fad1-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="4fad1-248">Aby odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4fad1-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4fad1-249">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="4fad1-250">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4fad1-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4fad1-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="4fad1-252">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="4fad1-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="4fad1-253">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4fad1-254">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-254">Prints out help for the command.</span></span> <span data-ttu-id="4fad1-255">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="4fad1-256">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="4fad1-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="4fad1-257">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="4fad1-258">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="4fad1-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="4fad1-259">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="4fad1-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="4fad1-260">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4fad1-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="4fad1-261">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="4fad1-262">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4fad1-263">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="4fad1-264">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-264">The language of the template to create.</span></span> <span data-ttu-id="4fad1-265">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="4fad1-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4fad1-266">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4fad1-267">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="4fad1-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4fad1-268">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4fad1-269">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4fad1-269">The name for the created output.</span></span> <span data-ttu-id="4fad1-270">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4fad1-271">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4fad1-271">Location to place the generated output.</span></span> <span data-ttu-id="4fad1-272">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="4fad1-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="4fad1-273">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-273">Filters templates based on available types.</span></span> <span data-ttu-id="4fad1-274">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="4fad1-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="4fad1-275">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="4fad1-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="4fad1-276">Aby odinstalować szablonu korzystanie ze źródła `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4fad1-276">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="4fad1-277">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="4fad1-278">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="4fad1-279">Jeśli nie można określić `PATH` lub `NUGET_ID` argument niezbędnych do odinstalowania szablon systemem `dotnet new --uninstall` bez argumentu, spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argument, trzeba je odinstalować.</span><span class="sxs-lookup"><span data-stu-id="4fad1-279">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4fad1-280">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4fad1-280">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="4fad1-281">Przedstawia wszystkie szablony dla określonego typu projektu, podczas uruchamiania w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-281">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="4fad1-282">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="4fad1-282">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="4fad1-283">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-283">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="4fad1-284">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-284">Prints out help for the command.</span></span> <span data-ttu-id="4fad1-285">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-285">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="4fad1-286">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-286">Lists templates containing the specified name.</span></span> <span data-ttu-id="4fad1-287">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-287">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="4fad1-288">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-288">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="4fad1-289">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-289">The language of the template to create.</span></span> <span data-ttu-id="4fad1-290">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="4fad1-290">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="4fad1-291">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="4fad1-291">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="4fad1-292">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="4fad1-292">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="4fad1-293">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-293">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="4fad1-294">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4fad1-294">The name for the created output.</span></span> <span data-ttu-id="4fad1-295">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-295">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4fad1-296">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4fad1-296">Location to place the generated output.</span></span> <span data-ttu-id="4fad1-297">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="4fad1-297">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="4fad1-298">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="4fad1-298">Template options</span></span>

<span data-ttu-id="4fad1-299">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="4fad1-299">Each project template may have additional options available.</span></span> <span data-ttu-id="4fad1-300">Szablony core są dostępne następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="4fad1-300">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4fad1-301">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4fad1-301">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="4fad1-302">**Konsola usługi angular, react, reactredux dla platformy, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="4fad1-302">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="4fad1-303">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-303">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-304">**classlib**</span><span class="sxs-lookup"><span data-stu-id="4fad1-304">**classlib**</span></span>

<span data-ttu-id="4fad1-305">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4fad1-305">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4fad1-306">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4fad1-306">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4fad1-307">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-307">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="4fad1-308">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-308">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-309">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="4fad1-309">**mstest, xunit**</span></span>

<span data-ttu-id="4fad1-310">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4fad1-310">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4fad1-311">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-312">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="4fad1-312">**globaljson**</span></span>

<span data-ttu-id="4fad1-313">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="4fad1-313">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="4fad1-314">**web**</span><span class="sxs-lookup"><span data-stu-id="4fad1-314">**web**</span></span>

<span data-ttu-id="4fad1-315">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-315">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4fad1-316">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-316">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-317">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4fad1-317">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4fad1-318">Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualAuth` lub `OrganizationalAuth` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="4fad1-318">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="4fad1-319">**webapi**</span><span class="sxs-lookup"><span data-stu-id="4fad1-319">**webapi**</span></span>

<span data-ttu-id="4fad1-320">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-320">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4fad1-321">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="4fad1-321">The possible values are:</span></span>

- <span data-ttu-id="4fad1-322">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4fad1-322">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4fad1-323">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4fad1-323">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4fad1-324">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-324">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4fad1-325">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="4fad1-325">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4fad1-326">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-326">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4fad1-327">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-327">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-328">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-328">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4fad1-329">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-329">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4fad1-330">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-330">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-331">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-331">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4fad1-332">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4fad1-333">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-333">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4fad1-334">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-334">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4fad1-335">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-335">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4fad1-336">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-336">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4fad1-337">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-337">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4fad1-338">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-338">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-339">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-339">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4fad1-340">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-340">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4fad1-341">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-341">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4fad1-342">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-342">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4fad1-343">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4fad1-343">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4fad1-344">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-344">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4fad1-345">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-345">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4fad1-346">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="4fad1-346">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4fad1-347">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-347">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-348">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-348">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-349">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4fad1-349">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4fad1-350">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-350">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4fad1-351">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="4fad1-351">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4fad1-352">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="4fad1-352">**mvc, razor**</span></span>

<span data-ttu-id="4fad1-353">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-353">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4fad1-354">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="4fad1-354">The possible values are:</span></span>

- <span data-ttu-id="4fad1-355">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4fad1-355">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4fad1-356">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="4fad1-356">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="4fad1-357">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4fad1-357">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4fad1-358">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-358">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4fad1-359">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="4fad1-359">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="4fad1-360">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="4fad1-360">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4fad1-361">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-361">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4fad1-362">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-362">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-363">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-363">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4fad1-364">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-364">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4fad1-365">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-365">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-366">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-366">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="4fad1-367">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-367">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-368">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-368">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="4fad1-369">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-369">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-370">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-370">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4fad1-371">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-371">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4fad1-372">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-372">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4fad1-373">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-373">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4fad1-374">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-374">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4fad1-375">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-375">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4fad1-376">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-376">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4fad1-377">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-378">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-378">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4fad1-379">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-379">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4fad1-380">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-380">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4fad1-381">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-381">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4fad1-382">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4fad1-382">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4fad1-383">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-383">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-384">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-384">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="4fad1-385">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4fad1-385">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4fad1-386">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-386">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4fad1-387">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-387">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="4fad1-388">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-388">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="4fad1-389">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="4fad1-389">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4fad1-390">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-390">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-391">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-391">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-392">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4fad1-392">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="4fad1-393">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-393">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="4fad1-394">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="4fad1-394">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="4fad1-395">**Strona**</span><span class="sxs-lookup"><span data-stu-id="4fad1-395">**page**</span></span>

<span data-ttu-id="4fad1-396">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-396">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4fad1-397">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-397">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4fad1-398">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="4fad1-398">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="4fad1-399">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="4fad1-399">**viewimports**</span></span>

<span data-ttu-id="4fad1-400">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-400">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4fad1-401">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-401">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4fad1-402">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4fad1-402">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="4fad1-403">**Konsola, angular, react reactredux dla platformy**</span><span class="sxs-lookup"><span data-stu-id="4fad1-403">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="4fad1-404">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-404">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-405">**classlib**</span><span class="sxs-lookup"><span data-stu-id="4fad1-405">**classlib**</span></span>

<span data-ttu-id="4fad1-406">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4fad1-406">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4fad1-407">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4fad1-407">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="4fad1-408">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-408">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="4fad1-409">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-409">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-410">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="4fad1-410">**mstest, xunit**</span></span>

<span data-ttu-id="4fad1-411">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4fad1-411">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="4fad1-412">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-413">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="4fad1-413">**globaljson**</span></span>

<span data-ttu-id="4fad1-414">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="4fad1-414">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="4fad1-415">**web**</span><span class="sxs-lookup"><span data-stu-id="4fad1-415">**web**</span></span>

<span data-ttu-id="4fad1-416">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="4fad1-416">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4fad1-417">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-417">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-418">**webapi**</span><span class="sxs-lookup"><span data-stu-id="4fad1-418">**webapi**</span></span>

<span data-ttu-id="4fad1-419">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-419">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4fad1-420">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="4fad1-420">The possible values are:</span></span>

- <span data-ttu-id="4fad1-421">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4fad1-421">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4fad1-422">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4fad1-422">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4fad1-423">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-423">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4fad1-424">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="4fad1-424">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4fad1-425">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-425">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4fad1-426">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-426">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-427">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-427">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4fad1-428">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-428">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4fad1-429">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-429">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-430">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-430">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4fad1-431">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4fad1-432">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-432">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4fad1-433">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-433">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4fad1-434">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-434">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="4fad1-435">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-435">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4fad1-436">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-436">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4fad1-437">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-437">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-438">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-438">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4fad1-439">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-439">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4fad1-440">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4fad1-441">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-441">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4fad1-442">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4fad1-442">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4fad1-443">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-443">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4fad1-444">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="4fad1-444">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4fad1-445">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="4fad1-445">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4fad1-446">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-446">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-447">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-447">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-448">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="4fad1-448">**mvc, razor**</span></span>

<span data-ttu-id="4fad1-449">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-449">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="4fad1-450">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="4fad1-450">The possible values are:</span></span>

- <span data-ttu-id="4fad1-451">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4fad1-451">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="4fad1-452">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="4fad1-452">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="4fad1-453">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="4fad1-453">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="4fad1-454">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="4fad1-454">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="4fad1-455">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="4fad1-455">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="4fad1-456">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="4fad1-456">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="4fad1-457">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-457">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="4fad1-458">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-458">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-459">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-459">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="4fad1-460">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-460">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="4fad1-461">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-461">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-462">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-462">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="4fad1-463">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-463">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-464">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-464">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="4fad1-465">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-465">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-466">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-466">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="4fad1-467">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-467">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="4fad1-468">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-468">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="4fad1-469">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-469">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="4fad1-470">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-470">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="4fad1-471">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-471">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="4fad1-472">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-472">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="4fad1-473">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-473">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-474">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-474">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="4fad1-475">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-475">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="4fad1-476">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-476">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="4fad1-477">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-477">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="4fad1-478">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4fad1-478">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="4fad1-479">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="4fad1-480">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-480">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="4fad1-481">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4fad1-481">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="4fad1-482">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-482">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="4fad1-483">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="4fad1-483">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="4fad1-484">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4fad1-484">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="4fad1-485">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="4fad1-485">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="4fad1-486">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4fad1-486">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="4fad1-487">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-487">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="4fad1-488">**Strona**</span><span class="sxs-lookup"><span data-stu-id="4fad1-488">**page**</span></span>

<span data-ttu-id="4fad1-489">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-489">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4fad1-490">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-490">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="4fad1-491">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="4fad1-491">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="4fad1-492">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="4fad1-492">**viewimports**</span></span>

<span data-ttu-id="4fad1-493">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="4fad1-493">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="4fad1-494">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-494">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4fad1-495">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4fad1-495">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="4fad1-496">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="4fad1-496">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="4fad1-497">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4fad1-497">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4fad1-498">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-498">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="4fad1-499">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-499">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="4fad1-500">**classlib**</span><span class="sxs-lookup"><span data-stu-id="4fad1-500">**classlib**</span></span>

<span data-ttu-id="4fad1-501">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4fad1-501">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4fad1-502">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-502">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="4fad1-503">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-503">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="4fad1-504">**mvc**</span><span class="sxs-lookup"><span data-stu-id="4fad1-504">**mvc**</span></span>

<span data-ttu-id="4fad1-505">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4fad1-505">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="4fad1-506">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-506">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="4fad1-507">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-507">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="4fad1-508">`-au|--auth` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="4fad1-508">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="4fad1-509">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-509">Values: `None` or `Individual`.</span></span> <span data-ttu-id="4fad1-510">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-510">The default value is `None`.</span></span>

<span data-ttu-id="4fad1-511">`-uld|--use-local-db` -Określa, czy należy użyć programu LocalDB zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="4fad1-511">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="4fad1-512">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-512">Values: `true` or `false`.</span></span> <span data-ttu-id="4fad1-513">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="4fad1-513">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="4fad1-514">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4fad1-514">Examples</span></span>

<span data-ttu-id="4fad1-515">Utwórz projekt aplikacji konsoli F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="4fad1-515">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="4fad1-516">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="4fad1-516">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="4fad1-517">Utwórz nowy projekt aplikacji w języku C# MVC ASP.NET Core w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="4fad1-517">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="4fad1-518">Utwórz nową aplikację xUnit:</span><span class="sxs-lookup"><span data-stu-id="4fad1-518">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="4fad1-519">Wyświetl wszystkie szablony dostępne dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="4fad1-519">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="4fad1-520">Zainstaluj wersję 2.0 szablonów aplikacji jednostronicowej dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="4fad1-520">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="4fad1-521">Tworzenie *global.json* w bieżącym katalogu, ustawienie wersji zestawu SDK 2.0.0 (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="4fad1-521">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="4fad1-522">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fad1-522">See also</span></span>

* [<span data-ttu-id="4fad1-523">Szablony niestandardowe dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="4fad1-523">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="4fad1-524">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="4fad1-524">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="4fad1-525">repozytorium GitHub DotNet/dotnet-— przykłady szablonów</span><span class="sxs-lookup"><span data-stu-id="4fad1-525">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="4fad1-526">Dostępne szablony dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="4fad1-526">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
