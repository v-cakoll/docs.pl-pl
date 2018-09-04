---
title: polecenia DotNet nowego polecenia — interfejs wiersza polecenia platformy .NET Core
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core, na podstawie określonego szablonu.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 2c82dda2d93225edb360316637e22964135cd5e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512558"
---
# <a name="dotnet-new"></a><span data-ttu-id="f8826-103">nowe polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="f8826-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f8826-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f8826-104">Name</span></span>

<span data-ttu-id="f8826-105">`dotnet new` -Tworzy nowy projekt, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="f8826-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f8826-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="f8826-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f8826-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="f8826-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f8826-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f8826-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8826-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8826-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="f8826-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f8826-110">Description</span></span>

<span data-ttu-id="f8826-111">`dotnet new` Polecenia oferuje wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f8826-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="f8826-112">Wywołuje polecenie [aparatu szablonów](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="f8826-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="f8826-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f8826-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="f8826-114">Szablon do utworzenia wystąpienia podczas wywoływania polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8826-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="f8826-115">Każdy szablon może być określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="f8826-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="f8826-116">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="f8826-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f8826-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="f8826-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="f8826-118">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-118">The command contains a default list of templates.</span></span> <span data-ttu-id="f8826-119">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="f8826-120">W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="f8826-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="f8826-121">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="f8826-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="f8826-122">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="f8826-122">Template description</span></span>                          | <span data-ttu-id="f8826-123">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="f8826-123">Template name</span></span>   | <span data-ttu-id="f8826-124">Języki</span><span class="sxs-lookup"><span data-stu-id="f8826-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="f8826-125">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="f8826-125">Console application</span></span>                          | `console`       | <span data-ttu-id="f8826-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f8826-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f8826-127">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="f8826-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="f8826-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f8826-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f8826-129">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="f8826-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="f8826-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f8826-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f8826-131">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="f8826-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="f8826-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f8826-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f8826-133">Strona razor</span><span class="sxs-lookup"><span data-stu-id="f8826-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="f8826-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-134">[C#]</span></span>          |
| <span data-ttu-id="f8826-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="f8826-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="f8826-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-136">[C#]</span></span>          |
| <span data-ttu-id="f8826-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="f8826-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="f8826-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-138">[C#]</span></span>          |
| <span data-ttu-id="f8826-139">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="f8826-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="f8826-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-140">[C#], F#</span></span>      |
| <span data-ttu-id="f8826-141">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="f8826-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="f8826-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-142">[C#], F#</span></span>      |
| <span data-ttu-id="f8826-143">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f8826-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="f8826-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-144">[C#]</span></span>          |
| <span data-ttu-id="f8826-145">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="f8826-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="f8826-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-146">[C#]</span></span>          |
| <span data-ttu-id="f8826-147">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="f8826-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="f8826-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-148">[C#]</span></span>          |
| <span data-ttu-id="f8826-149">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="f8826-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="f8826-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-150">[C#]</span></span>          |
| <span data-ttu-id="f8826-151">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f8826-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="f8826-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-152">[C#], F#</span></span>      |
| <span data-ttu-id="f8826-153">Biblioteki klas razor</span><span class="sxs-lookup"><span data-stu-id="f8826-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="f8826-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-154">[C#]</span></span>          |
| <span data-ttu-id="f8826-155">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="f8826-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="f8826-156">NuGet config</span><span class="sxs-lookup"><span data-stu-id="f8826-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="f8826-157">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="f8826-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="f8826-158">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f8826-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f8826-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f8826-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="f8826-160">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-160">The command contains a default list of templates.</span></span> <span data-ttu-id="f8826-161">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="f8826-162">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą platformy .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="f8826-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="f8826-163">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="f8826-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="f8826-164">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="f8826-164">Template description</span></span>                          | <span data-ttu-id="f8826-165">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="f8826-165">Template name</span></span> | <span data-ttu-id="f8826-166">Języki</span><span class="sxs-lookup"><span data-stu-id="f8826-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="f8826-167">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="f8826-167">Console application</span></span>                          | `console`     | <span data-ttu-id="f8826-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f8826-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f8826-169">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="f8826-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="f8826-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f8826-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f8826-171">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="f8826-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="f8826-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f8826-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f8826-173">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="f8826-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="f8826-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f8826-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f8826-175">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="f8826-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="f8826-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-176">[C#], F#</span></span>      |
| <span data-ttu-id="f8826-177">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="f8826-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="f8826-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-178">[C#], F#</span></span>      |
| <span data-ttu-id="f8826-179">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f8826-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="f8826-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-180">[C#]</span></span>          |
| <span data-ttu-id="f8826-181">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="f8826-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="f8826-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-182">[C#]</span></span>          |
| <span data-ttu-id="f8826-183">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="f8826-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="f8826-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-184">[C#]</span></span>          |
| <span data-ttu-id="f8826-185">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="f8826-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="f8826-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-186">[C#]</span></span>          |
| <span data-ttu-id="f8826-187">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f8826-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="f8826-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-188">[C#], F#</span></span>      |
| <span data-ttu-id="f8826-189">plik Global.JSON</span><span class="sxs-lookup"><span data-stu-id="f8826-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="f8826-190">NuGet config</span><span class="sxs-lookup"><span data-stu-id="f8826-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="f8826-191">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="f8826-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="f8826-192">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f8826-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="f8826-193">Strona razor</span><span class="sxs-lookup"><span data-stu-id="f8826-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="f8826-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="f8826-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="f8826-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="f8826-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8826-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8826-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f8826-197">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-197">The command contains a default list of templates.</span></span> <span data-ttu-id="f8826-198">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="f8826-199">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą zestawu SDK programu .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="f8826-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="f8826-200">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="f8826-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="f8826-201">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="f8826-201">Template description</span></span>  | <span data-ttu-id="f8826-202">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="f8826-202">Template name</span></span> | <span data-ttu-id="f8826-203">Języki</span><span class="sxs-lookup"><span data-stu-id="f8826-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="f8826-204">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="f8826-204">Console application</span></span>  | `console`     | <span data-ttu-id="f8826-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-205">[C#], F#</span></span>  |
| <span data-ttu-id="f8826-206">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="f8826-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="f8826-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-207">[C#], F#</span></span>  |
| <span data-ttu-id="f8826-208">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="f8826-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="f8826-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-209">[C#], F#</span></span>  |
| <span data-ttu-id="f8826-210">projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="f8826-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="f8826-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-211">[C#], F#</span></span>  |
| <span data-ttu-id="f8826-212">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="f8826-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="f8826-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-213">[C#]</span></span>      |
| <span data-ttu-id="f8826-214">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f8826-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="f8826-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f8826-215">[C#], F#</span></span>  |
| <span data-ttu-id="f8826-216">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f8826-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="f8826-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="f8826-217">[C#]</span></span>      |
| <span data-ttu-id="f8826-218">NuGet config</span><span class="sxs-lookup"><span data-stu-id="f8826-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="f8826-219">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="f8826-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="f8826-220">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f8826-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="f8826-221">Opcje</span><span class="sxs-lookup"><span data-stu-id="f8826-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f8826-222">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="f8826-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="f8826-223">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="f8826-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="f8826-224">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="f8826-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="f8826-225">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8826-225">Prints out help for the command.</span></span> <span data-ttu-id="f8826-226">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="f8826-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="f8826-227">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="f8826-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f8826-228">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="f8826-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="f8826-229">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="f8826-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="f8826-230">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="f8826-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="f8826-231">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="f8826-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="f8826-232">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f8826-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="f8826-233">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="f8826-234">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="f8826-235">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="f8826-235">The language of the template to create.</span></span> <span data-ttu-id="f8826-236">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="f8826-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f8826-237">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="f8826-238">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="f8826-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="f8826-239">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="f8826-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="f8826-240">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f8826-240">The name for the created output.</span></span> <span data-ttu-id="f8826-241">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="f8826-242">Określa źródła pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="f8826-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f8826-243">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f8826-243">Location to place the generated output.</span></span> <span data-ttu-id="f8826-244">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="f8826-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="f8826-245">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-245">Filters templates based on available types.</span></span> <span data-ttu-id="f8826-246">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="f8826-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="f8826-247">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="f8826-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="f8826-248">Aby odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f8826-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="f8826-249">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="f8826-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="f8826-250">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="f8826-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f8826-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f8826-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="f8826-252">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="f8826-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="f8826-253">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="f8826-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="f8826-254">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8826-254">Prints out help for the command.</span></span> <span data-ttu-id="f8826-255">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="f8826-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="f8826-256">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="f8826-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f8826-257">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="f8826-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="f8826-258">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="f8826-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="f8826-259">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="f8826-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="f8826-260">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="f8826-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="f8826-261">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f8826-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="f8826-262">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="f8826-263">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="f8826-264">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="f8826-264">The language of the template to create.</span></span> <span data-ttu-id="f8826-265">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="f8826-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f8826-266">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="f8826-267">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="f8826-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="f8826-268">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="f8826-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="f8826-269">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f8826-269">The name for the created output.</span></span> <span data-ttu-id="f8826-270">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f8826-271">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f8826-271">Location to place the generated output.</span></span> <span data-ttu-id="f8826-272">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="f8826-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="f8826-273">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-273">Filters templates based on available types.</span></span> <span data-ttu-id="f8826-274">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="f8826-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="f8826-275">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="f8826-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="f8826-276">Aby odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f8826-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="f8826-277">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="f8826-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="f8826-278">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="f8826-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8826-279">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8826-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="f8826-280">Przedstawia wszystkie szablony dla określonego typu projektu, podczas uruchamiania w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8826-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="f8826-281">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="f8826-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="f8826-282">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="f8826-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="f8826-283">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8826-283">Prints out help for the command.</span></span> <span data-ttu-id="f8826-284">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="f8826-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="f8826-285">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f8826-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="f8826-286">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="f8826-287">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="f8826-288">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="f8826-288">The language of the template to create.</span></span> <span data-ttu-id="f8826-289">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="f8826-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f8826-290">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8826-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="f8826-291">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="f8826-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="f8826-292">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="f8826-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="f8826-293">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f8826-293">The name for the created output.</span></span> <span data-ttu-id="f8826-294">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f8826-295">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f8826-295">Location to place the generated output.</span></span> <span data-ttu-id="f8826-296">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="f8826-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="f8826-297">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="f8826-297">Template options</span></span>

<span data-ttu-id="f8826-298">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="f8826-298">Each project template may have additional options available.</span></span> <span data-ttu-id="f8826-299">Szablony core są dostępne następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="f8826-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f8826-300">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="f8826-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="f8826-301">**Konsola usługi angular, react, reactredux dla platformy, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="f8826-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="f8826-302">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-303">**classlib**</span><span class="sxs-lookup"><span data-stu-id="f8826-303">**classlib**</span></span>

<span data-ttu-id="f8826-304">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f8826-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f8826-305">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f8826-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="f8826-306">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="f8826-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="f8826-307">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-308">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="f8826-308">**mstest, xunit**</span></span>

<span data-ttu-id="f8826-309">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f8826-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="f8826-310">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="f8826-311">**globaljson**</span></span>

<span data-ttu-id="f8826-312">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="f8826-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="f8826-313">**web**</span><span class="sxs-lookup"><span data-stu-id="f8826-313">**web**</span></span>

<span data-ttu-id="f8826-314">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="f8826-314">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="f8826-315">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-316">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f8826-316">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="f8826-317">Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualAuth` lub `OrganizationalAuth` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="f8826-317">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="f8826-318">**webapi**</span><span class="sxs-lookup"><span data-stu-id="f8826-318">**webapi**</span></span>

<span data-ttu-id="f8826-319">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="f8826-319">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f8826-320">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="f8826-320">The possible values are:</span></span>

- <span data-ttu-id="f8826-321">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f8826-321">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f8826-322">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f8826-322">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f8826-323">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="f8826-323">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f8826-324">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="f8826-324">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f8826-325">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-325">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f8826-326">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-326">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-327">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f8826-327">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="f8826-328">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-328">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f8826-329">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-329">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-330">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-330">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f8826-331">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-331">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f8826-332">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f8826-332">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f8826-333">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-333">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f8826-334">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-334">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f8826-335">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f8826-335">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f8826-336">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-336">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f8826-337">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-337">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-338">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f8826-338">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f8826-339">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-339">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f8826-340">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-340">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f8826-341">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f8826-341">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f8826-342">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8826-342">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f8826-343">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-343">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f8826-344">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="f8826-344">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="f8826-345">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="f8826-345">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f8826-346">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-346">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-347">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-347">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-348">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f8826-348">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="f8826-349">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="f8826-349">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="f8826-350">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="f8826-350">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="f8826-351">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="f8826-351">**mvc, razor**</span></span>

<span data-ttu-id="f8826-352">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="f8826-352">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f8826-353">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="f8826-353">The possible values are:</span></span>

- <span data-ttu-id="f8826-354">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f8826-354">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f8826-355">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="f8826-355">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="f8826-356">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f8826-356">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f8826-357">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="f8826-357">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f8826-358">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="f8826-358">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="f8826-359">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="f8826-359">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f8826-360">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-360">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f8826-361">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-361">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-362">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f8826-362">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="f8826-363">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-363">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f8826-364">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-364">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-365">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-365">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="f8826-366">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-367">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-367">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="f8826-368">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-369">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-369">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f8826-370">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-370">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f8826-371">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f8826-371">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f8826-372">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-372">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f8826-373">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-373">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f8826-374">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f8826-374">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f8826-375">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-375">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f8826-376">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-376">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-377">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f8826-377">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f8826-378">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-378">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f8826-379">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-379">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f8826-380">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f8826-380">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f8826-381">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8826-381">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f8826-382">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-382">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-383">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="f8826-383">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="f8826-384">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8826-384">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f8826-385">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-385">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f8826-386">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="f8826-386">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="f8826-387">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f8826-387">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="f8826-388">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="f8826-388">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f8826-389">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-389">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-390">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-390">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-391">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f8826-391">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="f8826-392">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="f8826-392">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="f8826-393">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="f8826-393">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="f8826-394">**Strona**</span><span class="sxs-lookup"><span data-stu-id="f8826-394">**page**</span></span>

<span data-ttu-id="f8826-395">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="f8826-395">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f8826-396">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="f8826-396">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="f8826-397">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="f8826-397">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="f8826-398">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="f8826-398">**viewimports**</span></span>

<span data-ttu-id="f8826-399">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="f8826-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f8826-400">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="f8826-400">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f8826-401">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f8826-401">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="f8826-402">**Konsola, angular, react reactredux dla platformy**</span><span class="sxs-lookup"><span data-stu-id="f8826-402">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="f8826-403">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-404">**classlib**</span><span class="sxs-lookup"><span data-stu-id="f8826-404">**classlib**</span></span>

<span data-ttu-id="f8826-405">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f8826-405">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f8826-406">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f8826-406">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="f8826-407">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="f8826-407">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="f8826-408">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-409">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="f8826-409">**mstest, xunit**</span></span>

<span data-ttu-id="f8826-410">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f8826-410">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="f8826-411">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-411">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-412">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="f8826-412">**globaljson**</span></span>

<span data-ttu-id="f8826-413">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="f8826-413">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="f8826-414">**web**</span><span class="sxs-lookup"><span data-stu-id="f8826-414">**web**</span></span>

<span data-ttu-id="f8826-415">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="f8826-415">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f8826-416">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-416">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-417">**webapi**</span><span class="sxs-lookup"><span data-stu-id="f8826-417">**webapi**</span></span>

<span data-ttu-id="f8826-418">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="f8826-418">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f8826-419">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="f8826-419">The possible values are:</span></span>

- <span data-ttu-id="f8826-420">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f8826-420">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f8826-421">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f8826-421">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f8826-422">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="f8826-422">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f8826-423">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="f8826-423">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f8826-424">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-424">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f8826-425">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-425">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-426">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f8826-426">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="f8826-427">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-427">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f8826-428">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-428">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-429">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-429">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f8826-430">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f8826-431">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f8826-431">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f8826-432">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-432">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f8826-433">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-433">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f8826-434">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f8826-434">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f8826-435">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-435">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f8826-436">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-437">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f8826-437">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f8826-438">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-438">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f8826-439">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-439">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f8826-440">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f8826-440">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f8826-441">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8826-441">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f8826-442">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-442">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f8826-443">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="f8826-443">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f8826-444">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="f8826-444">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f8826-445">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-445">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-446">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-446">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-447">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="f8826-447">**mvc, razor**</span></span>

<span data-ttu-id="f8826-448">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="f8826-448">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f8826-449">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="f8826-449">The possible values are:</span></span>

- <span data-ttu-id="f8826-450">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f8826-450">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f8826-451">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="f8826-451">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="f8826-452">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="f8826-452">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f8826-453">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="f8826-453">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f8826-454">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="f8826-454">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="f8826-455">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="f8826-455">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f8826-456">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-456">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f8826-457">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-457">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-458">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="f8826-458">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="f8826-459">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-459">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f8826-460">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-460">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-461">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-461">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="f8826-462">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-463">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-463">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="f8826-464">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-465">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-465">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f8826-466">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-466">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f8826-467">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="f8826-467">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f8826-468">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-468">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f8826-469">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-469">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f8826-470">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="f8826-470">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f8826-471">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8826-471">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f8826-472">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-472">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-473">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="f8826-473">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f8826-474">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f8826-474">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f8826-475">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-475">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f8826-476">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="f8826-476">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f8826-477">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8826-477">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f8826-478">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-478">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f8826-479">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="f8826-479">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="f8826-480">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8826-480">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f8826-481">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-481">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f8826-482">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="f8826-482">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f8826-483">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f8826-483">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="f8826-484">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="f8826-484">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f8826-485">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f8826-485">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f8826-486">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="f8826-486">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f8826-487">**Strona**</span><span class="sxs-lookup"><span data-stu-id="f8826-487">**page**</span></span>

<span data-ttu-id="f8826-488">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="f8826-488">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f8826-489">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="f8826-489">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="f8826-490">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="f8826-490">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="f8826-491">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="f8826-491">**viewimports**</span></span>

<span data-ttu-id="f8826-492">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="f8826-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f8826-493">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="f8826-493">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f8826-494">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f8826-494">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f8826-495">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="f8826-495">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="f8826-496">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f8826-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f8826-497">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="f8826-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="f8826-498">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="f8826-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="f8826-499">**classlib**</span><span class="sxs-lookup"><span data-stu-id="f8826-499">**classlib**</span></span>

<span data-ttu-id="f8826-500">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f8826-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f8826-501">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="f8826-501">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="f8826-502">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="f8826-502">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="f8826-503">**mvc**</span><span class="sxs-lookup"><span data-stu-id="f8826-503">**mvc**</span></span>

<span data-ttu-id="f8826-504">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f8826-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f8826-505">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="f8826-505">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="f8826-506">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="f8826-506">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="f8826-507">`-au|--auth` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="f8826-507">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="f8826-508">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="f8826-508">Values: `None` or `Individual`.</span></span> <span data-ttu-id="f8826-509">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="f8826-509">The default value is `None`.</span></span>

<span data-ttu-id="f8826-510">`-uld|--use-local-db` -Określa, czy należy użyć programu LocalDB zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="f8826-510">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="f8826-511">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="f8826-511">Values: `true` or `false`.</span></span> <span data-ttu-id="f8826-512">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f8826-512">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="f8826-513">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f8826-513">Examples</span></span>

<span data-ttu-id="f8826-514">Utwórz projekt aplikacji konsoli F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="f8826-514">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="f8826-515">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="f8826-515">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="f8826-516">Utwórz nowy projekt aplikacji w języku C# MVC ASP.NET Core w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="f8826-516">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="f8826-517">Utwórz nową aplikację xUnit:</span><span class="sxs-lookup"><span data-stu-id="f8826-517">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="f8826-518">Wyświetl wszystkie szablony dostępne dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="f8826-518">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="f8826-519">Zainstaluj wersję 2.0 szablonów aplikacji jednostronicowej dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="f8826-519">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="f8826-520">Tworzenie *global.json* w bieżącym katalogu, ustawienie wersji zestawu SDK 2.0.0 (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="f8826-520">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="f8826-521">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8826-521">See also</span></span>

* [<span data-ttu-id="f8826-522">Szablony niestandardowe dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="f8826-522">Custom templates for dotnet new</span></span>](custom-templates.md)  
* [<span data-ttu-id="f8826-523">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="f8826-523">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
* [<span data-ttu-id="f8826-524">repozytorium GitHub DotNet/dotnet-— przykłady szablonów</span><span class="sxs-lookup"><span data-stu-id="f8826-524">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="f8826-525">Dostępne szablony dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="f8826-525">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
