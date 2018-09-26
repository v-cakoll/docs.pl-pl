---
title: polecenia DotNet nowego polecenia — interfejs wiersza polecenia platformy .NET Core
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core, na podstawie określonego szablonu.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 396c4ddf09854fa4582226bdb1422f8c929e459b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208636"
---
# <a name="dotnet-new"></a><span data-ttu-id="49e24-103">nowe polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="49e24-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="49e24-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="49e24-104">Name</span></span>

<span data-ttu-id="49e24-105">`dotnet new` -Tworzy nowy projekt, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="49e24-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="49e24-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="49e24-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49e24-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="49e24-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49e24-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="49e24-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49e24-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="49e24-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="49e24-110">Opis</span><span class="sxs-lookup"><span data-stu-id="49e24-110">Description</span></span>

<span data-ttu-id="49e24-111">`dotnet new` Polecenia oferuje wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49e24-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="49e24-112">Wywołuje polecenie [aparatu szablonów](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="49e24-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="49e24-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="49e24-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="49e24-114">Szablon do utworzenia wystąpienia podczas wywoływania polecenia.</span><span class="sxs-lookup"><span data-stu-id="49e24-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="49e24-115">Każdy szablon może być określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="49e24-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="49e24-116">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="49e24-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49e24-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="49e24-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="49e24-118">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-118">The command contains a default list of templates.</span></span> <span data-ttu-id="49e24-119">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="49e24-120">W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="49e24-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="49e24-121">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="49e24-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="49e24-122">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="49e24-122">Template description</span></span>                          | <span data-ttu-id="49e24-123">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="49e24-123">Template name</span></span>   | <span data-ttu-id="49e24-124">Języki</span><span class="sxs-lookup"><span data-stu-id="49e24-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="49e24-125">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="49e24-125">Console application</span></span>                          | `console`       | <span data-ttu-id="49e24-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="49e24-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="49e24-127">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="49e24-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="49e24-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="49e24-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="49e24-129">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="49e24-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="49e24-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="49e24-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="49e24-131">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="49e24-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="49e24-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="49e24-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="49e24-133">Strona razor</span><span class="sxs-lookup"><span data-stu-id="49e24-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="49e24-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-134">[C#]</span></span>          |
| <span data-ttu-id="49e24-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="49e24-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="49e24-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-136">[C#]</span></span>          |
| <span data-ttu-id="49e24-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="49e24-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="49e24-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-138">[C#]</span></span>          |
| <span data-ttu-id="49e24-139">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="49e24-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="49e24-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-140">[C#], F#</span></span>      |
| <span data-ttu-id="49e24-141">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="49e24-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="49e24-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-142">[C#], F#</span></span>      |
| <span data-ttu-id="49e24-143">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49e24-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="49e24-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-144">[C#]</span></span>          |
| <span data-ttu-id="49e24-145">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="49e24-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="49e24-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-146">[C#]</span></span>          |
| <span data-ttu-id="49e24-147">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="49e24-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="49e24-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-148">[C#]</span></span>          |
| <span data-ttu-id="49e24-149">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="49e24-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="49e24-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-150">[C#]</span></span>          |
| <span data-ttu-id="49e24-151">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49e24-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="49e24-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-152">[C#], F#</span></span>      |
| <span data-ttu-id="49e24-153">Biblioteki klas razor</span><span class="sxs-lookup"><span data-stu-id="49e24-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="49e24-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-154">[C#]</span></span>          |
| <span data-ttu-id="49e24-155">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="49e24-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="49e24-156">NuGet config</span><span class="sxs-lookup"><span data-stu-id="49e24-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="49e24-157">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="49e24-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="49e24-158">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="49e24-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49e24-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="49e24-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="49e24-160">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-160">The command contains a default list of templates.</span></span> <span data-ttu-id="49e24-161">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="49e24-162">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą platformy .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="49e24-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="49e24-163">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="49e24-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="49e24-164">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="49e24-164">Template description</span></span>                          | <span data-ttu-id="49e24-165">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="49e24-165">Template name</span></span> | <span data-ttu-id="49e24-166">Języki</span><span class="sxs-lookup"><span data-stu-id="49e24-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="49e24-167">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="49e24-167">Console application</span></span>                          | `console`     | <span data-ttu-id="49e24-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="49e24-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="49e24-169">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="49e24-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="49e24-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="49e24-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="49e24-171">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="49e24-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="49e24-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="49e24-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="49e24-173">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="49e24-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="49e24-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="49e24-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="49e24-175">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="49e24-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="49e24-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-176">[C#], F#</span></span>      |
| <span data-ttu-id="49e24-177">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="49e24-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="49e24-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-178">[C#], F#</span></span>      |
| <span data-ttu-id="49e24-179">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49e24-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="49e24-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-180">[C#]</span></span>          |
| <span data-ttu-id="49e24-181">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="49e24-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="49e24-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-182">[C#]</span></span>          |
| <span data-ttu-id="49e24-183">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="49e24-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="49e24-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-184">[C#]</span></span>          |
| <span data-ttu-id="49e24-185">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="49e24-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="49e24-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-186">[C#]</span></span>          |
| <span data-ttu-id="49e24-187">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49e24-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="49e24-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-188">[C#], F#</span></span>      |
| <span data-ttu-id="49e24-189">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="49e24-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="49e24-190">NuGet config</span><span class="sxs-lookup"><span data-stu-id="49e24-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="49e24-191">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="49e24-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="49e24-192">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="49e24-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="49e24-193">Strona razor</span><span class="sxs-lookup"><span data-stu-id="49e24-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="49e24-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="49e24-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="49e24-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="49e24-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49e24-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="49e24-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="49e24-197">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-197">The command contains a default list of templates.</span></span> <span data-ttu-id="49e24-198">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="49e24-199">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą zestawu SDK programu .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="49e24-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="49e24-200">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="49e24-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="49e24-201">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="49e24-201">Template description</span></span>  | <span data-ttu-id="49e24-202">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="49e24-202">Template name</span></span> | <span data-ttu-id="49e24-203">Języki</span><span class="sxs-lookup"><span data-stu-id="49e24-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="49e24-204">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="49e24-204">Console application</span></span>  | `console`     | <span data-ttu-id="49e24-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-205">[C#], F#</span></span>  |
| <span data-ttu-id="49e24-206">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="49e24-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="49e24-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-207">[C#], F#</span></span>  |
| <span data-ttu-id="49e24-208">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="49e24-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="49e24-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-209">[C#], F#</span></span>  |
| <span data-ttu-id="49e24-210">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="49e24-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="49e24-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-211">[C#], F#</span></span>  |
| <span data-ttu-id="49e24-212">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="49e24-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="49e24-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-213">[C#]</span></span>      |
| <span data-ttu-id="49e24-214">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49e24-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="49e24-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="49e24-215">[C#], F#</span></span>  |
| <span data-ttu-id="49e24-216">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49e24-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="49e24-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="49e24-217">[C#]</span></span>      |
| <span data-ttu-id="49e24-218">NuGet config</span><span class="sxs-lookup"><span data-stu-id="49e24-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="49e24-219">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="49e24-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="49e24-220">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="49e24-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="49e24-221">Opcje</span><span class="sxs-lookup"><span data-stu-id="49e24-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49e24-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="49e24-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="49e24-223">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="49e24-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="49e24-224">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="49e24-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="49e24-225">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="49e24-225">Prints out help for the command.</span></span> <span data-ttu-id="49e24-226">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="49e24-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="49e24-227">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="49e24-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="49e24-228">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="49e24-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="49e24-229">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="49e24-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="49e24-230">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="49e24-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="49e24-231">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="49e24-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="49e24-232">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="49e24-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="49e24-233">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="49e24-234">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="49e24-235">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="49e24-235">The language of the template to create.</span></span> <span data-ttu-id="49e24-236">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="49e24-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="49e24-237">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="49e24-238">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="49e24-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="49e24-239">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="49e24-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="49e24-240">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49e24-240">The name for the created output.</span></span> <span data-ttu-id="49e24-241">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="49e24-242">Określa źródła pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="49e24-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="49e24-243">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49e24-243">Location to place the generated output.</span></span> <span data-ttu-id="49e24-244">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="49e24-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="49e24-245">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-245">Filters templates based on available types.</span></span> <span data-ttu-id="49e24-246">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="49e24-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="49e24-247">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="49e24-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="49e24-248">Aby odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="49e24-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="49e24-249">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="49e24-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="49e24-250">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="49e24-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49e24-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="49e24-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="49e24-252">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="49e24-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="49e24-253">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="49e24-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="49e24-254">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="49e24-254">Prints out help for the command.</span></span> <span data-ttu-id="49e24-255">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="49e24-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="49e24-256">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="49e24-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="49e24-257">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="49e24-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="49e24-258">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="49e24-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="49e24-259">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="49e24-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="49e24-260">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="49e24-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="49e24-261">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="49e24-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="49e24-262">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="49e24-263">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="49e24-264">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="49e24-264">The language of the template to create.</span></span> <span data-ttu-id="49e24-265">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="49e24-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="49e24-266">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="49e24-267">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="49e24-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="49e24-268">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="49e24-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="49e24-269">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49e24-269">The name for the created output.</span></span> <span data-ttu-id="49e24-270">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="49e24-271">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49e24-271">Location to place the generated output.</span></span> <span data-ttu-id="49e24-272">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="49e24-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="49e24-273">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-273">Filters templates based on available types.</span></span> <span data-ttu-id="49e24-274">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="49e24-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="49e24-275">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="49e24-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="49e24-276">Aby odinstalować szablonu korzystanie ze źródła `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="49e24-276">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="49e24-277">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="49e24-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="49e24-278">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="49e24-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="49e24-279">Jeśli nie można określić `PATH` lub `NUGET_ID` argument niezbędnych do odinstalowania szablon systemem `dotnet new --uninstall` bez argumentu, spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argument, trzeba je odinstalować.</span><span class="sxs-lookup"><span data-stu-id="49e24-279">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49e24-280">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="49e24-280">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="49e24-281">Przedstawia wszystkie szablony dla określonego typu projektu, podczas uruchamiania w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="49e24-281">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="49e24-282">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="49e24-282">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="49e24-283">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="49e24-283">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="49e24-284">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="49e24-284">Prints out help for the command.</span></span> <span data-ttu-id="49e24-285">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="49e24-285">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="49e24-286">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="49e24-286">Lists templates containing the specified name.</span></span> <span data-ttu-id="49e24-287">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-287">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="49e24-288">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-288">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="49e24-289">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="49e24-289">The language of the template to create.</span></span> <span data-ttu-id="49e24-290">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="49e24-290">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="49e24-291">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="49e24-291">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="49e24-292">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="49e24-292">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="49e24-293">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="49e24-293">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="49e24-294">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49e24-294">The name for the created output.</span></span> <span data-ttu-id="49e24-295">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-295">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="49e24-296">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49e24-296">Location to place the generated output.</span></span> <span data-ttu-id="49e24-297">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="49e24-297">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="49e24-298">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="49e24-298">Template options</span></span>

<span data-ttu-id="49e24-299">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="49e24-299">Each project template may have additional options available.</span></span> <span data-ttu-id="49e24-300">Szablony core są dostępne następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="49e24-300">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="49e24-301">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="49e24-301">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="49e24-302">**Konsola usługi angular, react, reactredux dla platformy, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="49e24-302">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="49e24-303">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-303">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-304">**classlib**</span><span class="sxs-lookup"><span data-stu-id="49e24-304">**classlib**</span></span>

<span data-ttu-id="49e24-305">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="49e24-305">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="49e24-306">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="49e24-306">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="49e24-307">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="49e24-307">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="49e24-308">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-308">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-309">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="49e24-309">**mstest, xunit**</span></span>

<span data-ttu-id="49e24-310">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="49e24-310">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="49e24-311">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-312">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="49e24-312">**globaljson**</span></span>

<span data-ttu-id="49e24-313">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="49e24-313">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="49e24-314">**web**</span><span class="sxs-lookup"><span data-stu-id="49e24-314">**web**</span></span>

<span data-ttu-id="49e24-315">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="49e24-315">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="49e24-316">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-316">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-317">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="49e24-317">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="49e24-318">Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualAuth` lub `OrganizationalAuth` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="49e24-318">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="49e24-319">**webapi**</span><span class="sxs-lookup"><span data-stu-id="49e24-319">**webapi**</span></span>

<span data-ttu-id="49e24-320">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="49e24-320">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="49e24-321">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="49e24-321">The possible values are:</span></span>

- <span data-ttu-id="49e24-322">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="49e24-322">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="49e24-323">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="49e24-323">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="49e24-324">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="49e24-324">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="49e24-325">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="49e24-325">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="49e24-326">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-326">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="49e24-327">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-327">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-328">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="49e24-328">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="49e24-329">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-329">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="49e24-330">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-330">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-331">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-331">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="49e24-332">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="49e24-333">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="49e24-333">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="49e24-334">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-334">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="49e24-335">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-335">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="49e24-336">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="49e24-336">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="49e24-337">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-337">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="49e24-338">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-338">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-339">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="49e24-339">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="49e24-340">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-340">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="49e24-341">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-341">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="49e24-342">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="49e24-342">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="49e24-343">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49e24-343">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="49e24-344">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-344">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="49e24-345">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="49e24-345">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="49e24-346">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="49e24-346">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="49e24-347">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-347">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-348">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-348">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-349">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="49e24-349">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="49e24-350">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="49e24-350">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="49e24-351">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="49e24-351">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="49e24-352">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="49e24-352">**mvc, razor**</span></span>

<span data-ttu-id="49e24-353">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="49e24-353">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="49e24-354">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="49e24-354">The possible values are:</span></span>

- <span data-ttu-id="49e24-355">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="49e24-355">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="49e24-356">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="49e24-356">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="49e24-357">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="49e24-357">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="49e24-358">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="49e24-358">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="49e24-359">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="49e24-359">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="49e24-360">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="49e24-360">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="49e24-361">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-361">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="49e24-362">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-362">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-363">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="49e24-363">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="49e24-364">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-364">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="49e24-365">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-365">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-366">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-366">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="49e24-367">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-367">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-368">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-368">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="49e24-369">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-369">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-370">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-370">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="49e24-371">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-371">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="49e24-372">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="49e24-372">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="49e24-373">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-373">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="49e24-374">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-374">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="49e24-375">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="49e24-375">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="49e24-376">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-376">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="49e24-377">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-378">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="49e24-378">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="49e24-379">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-379">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="49e24-380">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-380">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="49e24-381">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="49e24-381">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="49e24-382">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49e24-382">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="49e24-383">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-383">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-384">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="49e24-384">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="49e24-385">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49e24-385">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="49e24-386">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-386">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="49e24-387">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="49e24-387">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="49e24-388">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="49e24-388">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="49e24-389">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="49e24-389">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="49e24-390">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-390">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-391">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-391">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-392">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="49e24-392">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="49e24-393">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="49e24-393">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="49e24-394">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="49e24-394">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="49e24-395">**Strona**</span><span class="sxs-lookup"><span data-stu-id="49e24-395">**page**</span></span>

<span data-ttu-id="49e24-396">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="49e24-396">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="49e24-397">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="49e24-397">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="49e24-398">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="49e24-398">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="49e24-399">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="49e24-399">**viewimports**</span></span>

<span data-ttu-id="49e24-400">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="49e24-400">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="49e24-401">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="49e24-401">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="49e24-402">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="49e24-402">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="49e24-403">**Konsola, angular, react reactredux dla platformy**</span><span class="sxs-lookup"><span data-stu-id="49e24-403">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="49e24-404">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-404">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-405">**classlib**</span><span class="sxs-lookup"><span data-stu-id="49e24-405">**classlib**</span></span>

<span data-ttu-id="49e24-406">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="49e24-406">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="49e24-407">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="49e24-407">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="49e24-408">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="49e24-408">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="49e24-409">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-409">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-410">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="49e24-410">**mstest, xunit**</span></span>

<span data-ttu-id="49e24-411">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="49e24-411">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="49e24-412">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-413">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="49e24-413">**globaljson**</span></span>

<span data-ttu-id="49e24-414">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="49e24-414">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="49e24-415">**web**</span><span class="sxs-lookup"><span data-stu-id="49e24-415">**web**</span></span>

<span data-ttu-id="49e24-416">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="49e24-416">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="49e24-417">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-417">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-418">**webapi**</span><span class="sxs-lookup"><span data-stu-id="49e24-418">**webapi**</span></span>

<span data-ttu-id="49e24-419">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="49e24-419">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="49e24-420">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="49e24-420">The possible values are:</span></span>

- <span data-ttu-id="49e24-421">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="49e24-421">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="49e24-422">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="49e24-422">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="49e24-423">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="49e24-423">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="49e24-424">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="49e24-424">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="49e24-425">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-425">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="49e24-426">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-426">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-427">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="49e24-427">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="49e24-428">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-428">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="49e24-429">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-429">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-430">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-430">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="49e24-431">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="49e24-432">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="49e24-432">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="49e24-433">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-433">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="49e24-434">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-434">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="49e24-435">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="49e24-435">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="49e24-436">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-436">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="49e24-437">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-437">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-438">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="49e24-438">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="49e24-439">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-439">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="49e24-440">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="49e24-441">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="49e24-441">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="49e24-442">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49e24-442">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="49e24-443">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-443">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="49e24-444">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="49e24-444">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="49e24-445">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="49e24-445">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="49e24-446">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-446">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-447">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-447">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-448">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="49e24-448">**mvc, razor**</span></span>

<span data-ttu-id="49e24-449">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="49e24-449">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="49e24-450">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="49e24-450">The possible values are:</span></span>

- <span data-ttu-id="49e24-451">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="49e24-451">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="49e24-452">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="49e24-452">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="49e24-453">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="49e24-453">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="49e24-454">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="49e24-454">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="49e24-455">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="49e24-455">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="49e24-456">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="49e24-456">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="49e24-457">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-457">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="49e24-458">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-458">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-459">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="49e24-459">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="49e24-460">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-460">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="49e24-461">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-461">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-462">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-462">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="49e24-463">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-463">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-464">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-464">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="49e24-465">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-465">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-466">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-466">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="49e24-467">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-467">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="49e24-468">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="49e24-468">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="49e24-469">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-469">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="49e24-470">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-470">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="49e24-471">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="49e24-471">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="49e24-472">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="49e24-472">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="49e24-473">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-473">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-474">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="49e24-474">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="49e24-475">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="49e24-475">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="49e24-476">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-476">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="49e24-477">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="49e24-477">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="49e24-478">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49e24-478">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="49e24-479">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="49e24-480">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="49e24-480">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="49e24-481">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49e24-481">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="49e24-482">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-482">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="49e24-483">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="49e24-483">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="49e24-484">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="49e24-484">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="49e24-485">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="49e24-485">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="49e24-486">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="49e24-486">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="49e24-487">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="49e24-487">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="49e24-488">**Strona**</span><span class="sxs-lookup"><span data-stu-id="49e24-488">**page**</span></span>

<span data-ttu-id="49e24-489">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="49e24-489">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="49e24-490">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="49e24-490">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="49e24-491">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="49e24-491">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="49e24-492">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="49e24-492">**viewimports**</span></span>

<span data-ttu-id="49e24-493">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="49e24-493">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="49e24-494">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="49e24-494">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="49e24-495">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="49e24-495">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="49e24-496">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="49e24-496">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="49e24-497">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="49e24-497">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="49e24-498">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="49e24-498">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="49e24-499">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="49e24-499">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="49e24-500">**classlib**</span><span class="sxs-lookup"><span data-stu-id="49e24-500">**classlib**</span></span>

<span data-ttu-id="49e24-501">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="49e24-501">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="49e24-502">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="49e24-502">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="49e24-503">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="49e24-503">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="49e24-504">**mvc**</span><span class="sxs-lookup"><span data-stu-id="49e24-504">**mvc**</span></span>

<span data-ttu-id="49e24-505">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="49e24-505">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="49e24-506">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="49e24-506">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="49e24-507">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="49e24-507">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="49e24-508">`-au|--auth` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="49e24-508">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="49e24-509">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="49e24-509">Values: `None` or `Individual`.</span></span> <span data-ttu-id="49e24-510">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="49e24-510">The default value is `None`.</span></span>

<span data-ttu-id="49e24-511">`-uld|--use-local-db` -Określa, czy należy użyć programu LocalDB zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="49e24-511">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="49e24-512">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="49e24-512">Values: `true` or `false`.</span></span> <span data-ttu-id="49e24-513">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="49e24-513">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="49e24-514">Przykłady</span><span class="sxs-lookup"><span data-stu-id="49e24-514">Examples</span></span>

<span data-ttu-id="49e24-515">Utwórz projekt aplikacji konsoli F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="49e24-515">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="49e24-516">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="49e24-516">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="49e24-517">Utwórz nowy projekt aplikacji w języku C# MVC ASP.NET Core w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="49e24-517">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="49e24-518">Utwórz nową aplikację xUnit:</span><span class="sxs-lookup"><span data-stu-id="49e24-518">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="49e24-519">Wyświetl wszystkie szablony dostępne dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="49e24-519">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="49e24-520">Zainstaluj wersję 2.0 szablonów aplikacji jednostronicowej dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="49e24-520">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="49e24-521">Tworzenie *global.json* w bieżącym katalogu, ustawienie wersji zestawu SDK 2.0.0 (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="49e24-521">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="49e24-522">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49e24-522">See also</span></span>

* [<span data-ttu-id="49e24-523">Szablony niestandardowe dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="49e24-523">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="49e24-524">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="49e24-524">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="49e24-525">repozytorium GitHub DotNet/dotnet-— przykłady szablonów</span><span class="sxs-lookup"><span data-stu-id="49e24-525">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="49e24-526">Dostępne szablony dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="49e24-526">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
