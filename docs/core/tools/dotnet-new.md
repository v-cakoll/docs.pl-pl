---
title: polecenia DotNet nowego polecenia — interfejs wiersza polecenia platformy .NET Core
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core, na podstawie określonego szablonu.
author: mairaw
ms.author: mairaw
ms.date: 10/24/2018
ms.openlocfilehash: 56d76f1dd54097f9cf20129d74057235290c273c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188208"
---
# <a name="dotnet-new"></a><span data-ttu-id="962fc-103">nowe polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="962fc-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="962fc-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="962fc-104">Name</span></span>

<span data-ttu-id="962fc-105">`dotnet new` -Tworzy nowy projekt, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="962fc-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="962fc-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="962fc-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="962fc-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="962fc-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="962fc-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="962fc-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="962fc-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="962fc-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="962fc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="962fc-110">Description</span></span>

<span data-ttu-id="962fc-111">`dotnet new` Polecenia oferuje wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="962fc-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="962fc-112">Wywołuje polecenie [aparatu szablonów](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="962fc-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="962fc-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="962fc-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="962fc-114">Szablon do utworzenia wystąpienia podczas wywoływania polecenia.</span><span class="sxs-lookup"><span data-stu-id="962fc-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="962fc-115">Każdy szablon może być określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="962fc-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="962fc-116">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="962fc-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="962fc-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="962fc-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="962fc-118">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-118">The command contains a default list of templates.</span></span> <span data-ttu-id="962fc-119">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="962fc-120">W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="962fc-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="962fc-121">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="962fc-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="962fc-122">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="962fc-122">Template description</span></span>                          | <span data-ttu-id="962fc-123">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="962fc-123">Template name</span></span>    | <span data-ttu-id="962fc-124">Języki</span><span class="sxs-lookup"><span data-stu-id="962fc-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="962fc-125">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="962fc-125">Console application</span></span>                          | `console`        | <span data-ttu-id="962fc-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="962fc-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="962fc-127">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="962fc-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="962fc-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="962fc-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="962fc-129">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="962fc-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="962fc-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="962fc-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="962fc-131">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="962fc-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="962fc-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="962fc-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="962fc-133">Strona razor</span><span class="sxs-lookup"><span data-stu-id="962fc-133">Razor page</span></span>                                   | `page`           | <span data-ttu-id="962fc-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-134">[C#]</span></span>          |
| <span data-ttu-id="962fc-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="962fc-135">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="962fc-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-136">[C#]</span></span>          |
| <span data-ttu-id="962fc-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="962fc-137">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="962fc-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-138">[C#]</span></span>          |
| <span data-ttu-id="962fc-139">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="962fc-139">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="962fc-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-140">[C#], F#</span></span>      |
| <span data-ttu-id="962fc-141">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="962fc-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="962fc-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-142">[C#], F#</span></span>      |
| <span data-ttu-id="962fc-143">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="962fc-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="962fc-144">`razor`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="962fc-144">`razor`, `webapp`</span></span>| <span data-ttu-id="962fc-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-145">[C#]</span></span>          |
| <span data-ttu-id="962fc-146">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="962fc-146">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="962fc-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-147">[C#]</span></span>          |
| <span data-ttu-id="962fc-148">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="962fc-148">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="962fc-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-149">[C#]</span></span>          |
| <span data-ttu-id="962fc-150">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="962fc-150">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="962fc-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-151">[C#]</span></span>          |
| <span data-ttu-id="962fc-152">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="962fc-152">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="962fc-153">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-153">[C#], F#</span></span>      |
| <span data-ttu-id="962fc-154">Biblioteki klas razor</span><span class="sxs-lookup"><span data-stu-id="962fc-154">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="962fc-155">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-155">[C#]</span></span>          |
| <span data-ttu-id="962fc-156">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="962fc-156">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="962fc-157">NuGet config</span><span class="sxs-lookup"><span data-stu-id="962fc-157">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="962fc-158">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="962fc-158">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="962fc-159">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="962fc-159">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="962fc-160">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="962fc-160">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="962fc-161">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-161">The command contains a default list of templates.</span></span> <span data-ttu-id="962fc-162">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-162">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="962fc-163">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą platformy .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="962fc-163">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="962fc-164">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="962fc-164">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="962fc-165">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="962fc-165">Template description</span></span>                          | <span data-ttu-id="962fc-166">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="962fc-166">Template name</span></span> | <span data-ttu-id="962fc-167">Języki</span><span class="sxs-lookup"><span data-stu-id="962fc-167">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="962fc-168">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="962fc-168">Console application</span></span>                          | `console`     | <span data-ttu-id="962fc-169">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="962fc-169">[C#], F#, VB</span></span>  |
| <span data-ttu-id="962fc-170">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="962fc-170">Class library</span></span>                                | `classlib`    | <span data-ttu-id="962fc-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="962fc-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="962fc-172">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="962fc-172">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="962fc-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="962fc-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="962fc-174">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="962fc-174">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="962fc-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="962fc-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="962fc-176">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="962fc-176">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="962fc-177">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-177">[C#], F#</span></span>      |
| <span data-ttu-id="962fc-178">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="962fc-178">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="962fc-179">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-179">[C#], F#</span></span>      |
| <span data-ttu-id="962fc-180">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="962fc-180">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="962fc-181">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-181">[C#]</span></span>          |
| <span data-ttu-id="962fc-182">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="962fc-182">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="962fc-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-183">[C#]</span></span>          |
| <span data-ttu-id="962fc-184">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="962fc-184">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="962fc-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-185">[C#]</span></span>          |
| <span data-ttu-id="962fc-186">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="962fc-186">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="962fc-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-187">[C#]</span></span>          |
| <span data-ttu-id="962fc-188">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="962fc-188">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="962fc-189">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-189">[C#], F#</span></span>      |
| <span data-ttu-id="962fc-190">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="962fc-190">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="962fc-191">NuGet config</span><span class="sxs-lookup"><span data-stu-id="962fc-191">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="962fc-192">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="962fc-192">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="962fc-193">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="962fc-193">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="962fc-194">Strona razor</span><span class="sxs-lookup"><span data-stu-id="962fc-194">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="962fc-195">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="962fc-195">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="962fc-196">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="962fc-196">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="962fc-197">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="962fc-197">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="962fc-198">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-198">The command contains a default list of templates.</span></span> <span data-ttu-id="962fc-199">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-199">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="962fc-200">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą zestawu SDK programu .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="962fc-200">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="962fc-201">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="962fc-201">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="962fc-202">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="962fc-202">Template description</span></span>  | <span data-ttu-id="962fc-203">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="962fc-203">Template name</span></span> | <span data-ttu-id="962fc-204">Języki</span><span class="sxs-lookup"><span data-stu-id="962fc-204">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="962fc-205">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="962fc-205">Console application</span></span>  | `console`     | <span data-ttu-id="962fc-206">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-206">[C#], F#</span></span>  |
| <span data-ttu-id="962fc-207">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="962fc-207">Class library</span></span>        | `classlib`    | <span data-ttu-id="962fc-208">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-208">[C#], F#</span></span>  |
| <span data-ttu-id="962fc-209">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="962fc-209">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="962fc-210">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-210">[C#], F#</span></span>  |
| <span data-ttu-id="962fc-211">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="962fc-211">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="962fc-212">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-212">[C#], F#</span></span>  |
| <span data-ttu-id="962fc-213">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="962fc-213">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="962fc-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-214">[C#]</span></span>      |
| <span data-ttu-id="962fc-215">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="962fc-215">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="962fc-216">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="962fc-216">[C#], F#</span></span>  |
| <span data-ttu-id="962fc-217">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="962fc-217">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="962fc-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="962fc-218">[C#]</span></span>      |
| <span data-ttu-id="962fc-219">NuGet config</span><span class="sxs-lookup"><span data-stu-id="962fc-219">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="962fc-220">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="962fc-220">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="962fc-221">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="962fc-221">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="962fc-222">Opcje</span><span class="sxs-lookup"><span data-stu-id="962fc-222">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="962fc-223">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="962fc-223">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="962fc-224">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="962fc-224">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="962fc-225">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="962fc-225">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="962fc-226">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="962fc-226">Prints out help for the command.</span></span> <span data-ttu-id="962fc-227">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="962fc-227">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="962fc-228">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="962fc-228">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="962fc-229">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="962fc-229">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="962fc-230">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="962fc-230">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="962fc-231">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="962fc-231">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="962fc-232">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="962fc-232">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="962fc-233">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="962fc-233">Lists templates containing the specified name.</span></span> <span data-ttu-id="962fc-234">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-234">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="962fc-235">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-235">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="962fc-236">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="962fc-236">The language of the template to create.</span></span> <span data-ttu-id="962fc-237">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="962fc-237">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="962fc-238">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-238">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="962fc-239">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="962fc-239">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="962fc-240">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="962fc-240">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="962fc-241">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="962fc-241">The name for the created output.</span></span> <span data-ttu-id="962fc-242">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-242">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="962fc-243">Określa źródła pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="962fc-243">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="962fc-244">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="962fc-244">Location to place the generated output.</span></span> <span data-ttu-id="962fc-245">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="962fc-245">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="962fc-246">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-246">Filters templates based on available types.</span></span> <span data-ttu-id="962fc-247">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="962fc-247">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="962fc-248">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="962fc-248">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="962fc-249">Aby odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="962fc-249">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="962fc-250">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="962fc-250">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="962fc-251">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="962fc-251">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="962fc-252">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="962fc-252">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="962fc-253">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="962fc-253">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="962fc-254">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="962fc-254">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="962fc-255">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="962fc-255">Prints out help for the command.</span></span> <span data-ttu-id="962fc-256">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="962fc-256">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="962fc-257">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="962fc-257">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="962fc-258">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="962fc-258">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="962fc-259">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="962fc-259">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="962fc-260">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="962fc-260">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="962fc-261">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="962fc-261">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="962fc-262">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="962fc-262">Lists templates containing the specified name.</span></span> <span data-ttu-id="962fc-263">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-263">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="962fc-264">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-264">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="962fc-265">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="962fc-265">The language of the template to create.</span></span> <span data-ttu-id="962fc-266">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="962fc-266">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="962fc-267">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-267">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="962fc-268">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="962fc-268">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="962fc-269">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="962fc-269">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="962fc-270">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="962fc-270">The name for the created output.</span></span> <span data-ttu-id="962fc-271">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-271">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="962fc-272">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="962fc-272">Location to place the generated output.</span></span> <span data-ttu-id="962fc-273">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="962fc-273">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="962fc-274">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-274">Filters templates based on available types.</span></span> <span data-ttu-id="962fc-275">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="962fc-275">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="962fc-276">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="962fc-276">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="962fc-277">Aby odinstalować szablonu korzystanie ze źródła `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="962fc-277">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="962fc-278">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="962fc-278">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="962fc-279">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="962fc-279">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="962fc-280">Jeśli nie można określić `PATH` lub `NUGET_ID` argument niezbędnych do odinstalowania szablon systemem `dotnet new --uninstall` bez argumentu, spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argument, trzeba je odinstalować.</span><span class="sxs-lookup"><span data-stu-id="962fc-280">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="962fc-281">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="962fc-281">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="962fc-282">Przedstawia wszystkie szablony dla określonego typu projektu, podczas uruchamiania w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="962fc-282">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="962fc-283">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="962fc-283">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="962fc-284">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="962fc-284">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="962fc-285">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="962fc-285">Prints out help for the command.</span></span> <span data-ttu-id="962fc-286">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="962fc-286">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="962fc-287">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="962fc-287">Lists templates containing the specified name.</span></span> <span data-ttu-id="962fc-288">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-288">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="962fc-289">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-289">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="962fc-290">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="962fc-290">The language of the template to create.</span></span> <span data-ttu-id="962fc-291">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="962fc-291">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="962fc-292">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="962fc-292">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="962fc-293">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="962fc-293">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="962fc-294">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="962fc-294">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="962fc-295">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="962fc-295">The name for the created output.</span></span> <span data-ttu-id="962fc-296">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-296">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="962fc-297">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="962fc-297">Location to place the generated output.</span></span> <span data-ttu-id="962fc-298">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="962fc-298">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="962fc-299">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="962fc-299">Template options</span></span>

<span data-ttu-id="962fc-300">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="962fc-300">Each project template may have additional options available.</span></span> <span data-ttu-id="962fc-301">Szablony core są dostępne następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="962fc-301">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="962fc-302">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="962fc-302">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="962fc-303">**Konsola usługi angular, react, reactredux dla platformy, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="962fc-303">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="962fc-304">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-305">**classlib**</span><span class="sxs-lookup"><span data-stu-id="962fc-305">**classlib**</span></span>

<span data-ttu-id="962fc-306">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="962fc-306">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="962fc-307">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="962fc-307">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="962fc-308">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="962fc-308">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="962fc-309">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-310">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="962fc-310">**mstest, xunit**</span></span>

<span data-ttu-id="962fc-311">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="962fc-311">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="962fc-312">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-312">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-313">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="962fc-313">**globaljson**</span></span>

<span data-ttu-id="962fc-314">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="962fc-314">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="962fc-315">**web**</span><span class="sxs-lookup"><span data-stu-id="962fc-315">**web**</span></span>

<span data-ttu-id="962fc-316">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="962fc-316">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="962fc-317">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-317">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-318">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="962fc-318">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="962fc-319">Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualAuth` lub `OrganizationalAuth` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="962fc-319">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="962fc-320">**webapi**</span><span class="sxs-lookup"><span data-stu-id="962fc-320">**webapi**</span></span>

<span data-ttu-id="962fc-321">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="962fc-321">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="962fc-322">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="962fc-322">The possible values are:</span></span>

- <span data-ttu-id="962fc-323">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="962fc-323">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="962fc-324">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="962fc-324">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="962fc-325">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="962fc-325">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="962fc-326">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="962fc-326">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="962fc-327">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-327">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="962fc-328">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-328">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-329">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="962fc-329">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="962fc-330">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-330">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="962fc-331">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-331">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-332">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-332">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="962fc-333">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-333">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="962fc-334">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="962fc-334">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="962fc-335">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-335">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="962fc-336">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-336">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="962fc-337">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="962fc-337">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="962fc-338">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-338">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="962fc-339">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-339">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-340">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="962fc-340">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="962fc-341">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-341">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="962fc-342">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-342">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="962fc-343">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="962fc-343">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="962fc-344">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="962fc-344">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="962fc-345">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-345">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="962fc-346">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="962fc-346">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="962fc-347">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="962fc-347">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="962fc-348">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-348">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-349">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-349">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-350">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="962fc-350">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="962fc-351">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="962fc-351">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="962fc-352">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="962fc-352">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="962fc-353">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="962fc-353">**mvc, razor**</span></span>

<span data-ttu-id="962fc-354">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="962fc-354">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="962fc-355">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="962fc-355">The possible values are:</span></span>

- <span data-ttu-id="962fc-356">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="962fc-356">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="962fc-357">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="962fc-357">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="962fc-358">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="962fc-358">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="962fc-359">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="962fc-359">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="962fc-360">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="962fc-360">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="962fc-361">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="962fc-361">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="962fc-362">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-362">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="962fc-363">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-363">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-364">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="962fc-364">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="962fc-365">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-365">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="962fc-366">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-367">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-367">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="962fc-368">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-369">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-369">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="962fc-370">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-371">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-371">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="962fc-372">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-372">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="962fc-373">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="962fc-373">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="962fc-374">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-374">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="962fc-375">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-375">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="962fc-376">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="962fc-376">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="962fc-377">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-377">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="962fc-378">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-378">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-379">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="962fc-379">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="962fc-380">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-380">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="962fc-381">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-381">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="962fc-382">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="962fc-382">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="962fc-383">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="962fc-383">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="962fc-384">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-384">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-385">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="962fc-385">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="962fc-386">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="962fc-386">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="962fc-387">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-387">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="962fc-388">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="962fc-388">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="962fc-389">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="962fc-389">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="962fc-390">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="962fc-390">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="962fc-391">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-391">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-392">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-392">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-393">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="962fc-393">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="962fc-394">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="962fc-394">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="962fc-395">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="962fc-395">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="962fc-396">**Strona**</span><span class="sxs-lookup"><span data-stu-id="962fc-396">**page**</span></span>

<span data-ttu-id="962fc-397">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="962fc-397">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="962fc-398">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="962fc-398">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="962fc-399">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="962fc-399">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="962fc-400">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="962fc-400">**viewimports**</span></span>

<span data-ttu-id="962fc-401">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="962fc-401">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="962fc-402">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="962fc-402">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="962fc-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="962fc-403">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="962fc-404">**Konsola, angular, react reactredux dla platformy**</span><span class="sxs-lookup"><span data-stu-id="962fc-404">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="962fc-405">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-405">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-406">**classlib**</span><span class="sxs-lookup"><span data-stu-id="962fc-406">**classlib**</span></span>

<span data-ttu-id="962fc-407">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="962fc-407">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="962fc-408">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="962fc-408">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="962fc-409">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="962fc-409">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="962fc-410">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-410">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-411">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="962fc-411">**mstest, xunit**</span></span>

<span data-ttu-id="962fc-412">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="962fc-412">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="962fc-413">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-413">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-414">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="962fc-414">**globaljson**</span></span>

<span data-ttu-id="962fc-415">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="962fc-415">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="962fc-416">**web**</span><span class="sxs-lookup"><span data-stu-id="962fc-416">**web**</span></span>

<span data-ttu-id="962fc-417">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="962fc-417">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="962fc-418">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-418">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-419">**webapi**</span><span class="sxs-lookup"><span data-stu-id="962fc-419">**webapi**</span></span>

<span data-ttu-id="962fc-420">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="962fc-420">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="962fc-421">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="962fc-421">The possible values are:</span></span>

- <span data-ttu-id="962fc-422">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="962fc-422">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="962fc-423">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="962fc-423">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="962fc-424">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="962fc-424">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="962fc-425">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="962fc-425">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="962fc-426">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-426">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="962fc-427">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-427">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-428">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="962fc-428">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="962fc-429">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-429">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="962fc-430">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-430">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-431">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-431">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="962fc-432">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-432">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="962fc-433">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="962fc-433">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="962fc-434">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-434">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="962fc-435">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-435">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="962fc-436">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="962fc-436">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="962fc-437">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-437">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="962fc-438">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-438">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-439">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="962fc-439">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="962fc-440">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-440">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="962fc-441">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-441">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="962fc-442">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="962fc-442">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="962fc-443">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="962fc-443">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="962fc-444">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-444">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="962fc-445">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="962fc-445">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="962fc-446">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="962fc-446">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="962fc-447">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-447">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-448">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-448">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-449">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="962fc-449">**mvc, razor**</span></span>

<span data-ttu-id="962fc-450">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="962fc-450">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="962fc-451">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="962fc-451">The possible values are:</span></span>

- <span data-ttu-id="962fc-452">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="962fc-452">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="962fc-453">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="962fc-453">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="962fc-454">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="962fc-454">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="962fc-455">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="962fc-455">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="962fc-456">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="962fc-456">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="962fc-457">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="962fc-457">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="962fc-458">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-458">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="962fc-459">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-459">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-460">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="962fc-460">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="962fc-461">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-461">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="962fc-462">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-463">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-463">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="962fc-464">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-465">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-465">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="962fc-466">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-467">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-467">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="962fc-468">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-468">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="962fc-469">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="962fc-469">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="962fc-470">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-470">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="962fc-471">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-471">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="962fc-472">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="962fc-472">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="962fc-473">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="962fc-473">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="962fc-474">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-474">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-475">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="962fc-475">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="962fc-476">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="962fc-476">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="962fc-477">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-477">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="962fc-478">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="962fc-478">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="962fc-479">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="962fc-479">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="962fc-480">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="962fc-481">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="962fc-481">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="962fc-482">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="962fc-482">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="962fc-483">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-483">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="962fc-484">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="962fc-484">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="962fc-485">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="962fc-485">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="962fc-486">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="962fc-486">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="962fc-487">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="962fc-487">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="962fc-488">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="962fc-488">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="962fc-489">**Strona**</span><span class="sxs-lookup"><span data-stu-id="962fc-489">**page**</span></span>

<span data-ttu-id="962fc-490">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="962fc-490">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="962fc-491">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="962fc-491">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="962fc-492">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="962fc-492">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="962fc-493">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="962fc-493">**viewimports**</span></span>

<span data-ttu-id="962fc-494">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="962fc-494">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="962fc-495">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="962fc-495">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="962fc-496">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="962fc-496">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="962fc-497">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="962fc-497">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="962fc-498">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="962fc-498">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="962fc-499">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="962fc-499">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="962fc-500">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="962fc-500">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="962fc-501">**classlib**</span><span class="sxs-lookup"><span data-stu-id="962fc-501">**classlib**</span></span>

<span data-ttu-id="962fc-502">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="962fc-502">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="962fc-503">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="962fc-503">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="962fc-504">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="962fc-504">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="962fc-505">**mvc**</span><span class="sxs-lookup"><span data-stu-id="962fc-505">**mvc**</span></span>

<span data-ttu-id="962fc-506">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="962fc-506">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="962fc-507">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="962fc-507">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="962fc-508">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="962fc-508">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="962fc-509">`-au|--auth` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="962fc-509">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="962fc-510">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="962fc-510">Values: `None` or `Individual`.</span></span> <span data-ttu-id="962fc-511">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="962fc-511">The default value is `None`.</span></span>

<span data-ttu-id="962fc-512">`-uld|--use-local-db` -Określa, czy należy użyć programu LocalDB zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="962fc-512">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="962fc-513">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="962fc-513">Values: `true` or `false`.</span></span> <span data-ttu-id="962fc-514">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="962fc-514">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="962fc-515">Przykłady</span><span class="sxs-lookup"><span data-stu-id="962fc-515">Examples</span></span>

<span data-ttu-id="962fc-516">Utwórz projekt aplikacji konsoli F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="962fc-516">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="962fc-517">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="962fc-517">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="962fc-518">Utwórz nowy projekt aplikacji w języku C# MVC ASP.NET Core w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="962fc-518">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="962fc-519">Utwórz nową aplikację xUnit:</span><span class="sxs-lookup"><span data-stu-id="962fc-519">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="962fc-520">Wyświetl wszystkie szablony dostępne dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="962fc-520">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="962fc-521">Zainstaluj wersję 2.0 szablonów aplikacji jednostronicowej dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="962fc-521">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="962fc-522">Tworzenie *global.json* w bieżącym katalogu, ustawienie wersji zestawu SDK 2.0.0 (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="962fc-522">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="962fc-523">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="962fc-523">See also</span></span>

* [<span data-ttu-id="962fc-524">Szablony niestandardowe dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="962fc-524">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="962fc-525">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="962fc-525">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="962fc-526">repozytorium GitHub DotNet/dotnet-— przykłady szablonów</span><span class="sxs-lookup"><span data-stu-id="962fc-526">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="962fc-527">Dostępne szablony dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="962fc-527">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
