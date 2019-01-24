---
title: nowe polecenia DotNet
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core, na podstawie określonego szablonu.
ms.date: 10/24/2018
ms.openlocfilehash: 5177c920fee6fa946d2bf5d96644f26309ed0a99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516151"
---
# <a name="dotnet-new"></a><span data-ttu-id="43d2c-103">nowe polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="43d2c-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="43d2c-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="43d2c-104">Name</span></span>

<span data-ttu-id="43d2c-105">`dotnet new` -Tworzy nowy projekt, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="43d2c-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="43d2c-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="43d2c-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="43d2c-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="43d2c-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="43d2c-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="43d2c-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="43d2c-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="43d2c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="43d2c-110">Description</span></span>

<span data-ttu-id="43d2c-111">`dotnet new` Polecenia oferuje wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43d2c-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="43d2c-112">Wywołuje polecenie [aparatu szablonów](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="43d2c-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="43d2c-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="43d2c-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="43d2c-114">Szablon do utworzenia wystąpienia podczas wywoływania polecenia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="43d2c-115">Każdy szablon może być określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="43d2c-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="43d2c-116">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="43d2c-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="43d2c-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="43d2c-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="43d2c-118">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-118">The command contains a default list of templates.</span></span> <span data-ttu-id="43d2c-119">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="43d2c-120">W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="43d2c-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="43d2c-121">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="43d2c-122">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="43d2c-122">Template description</span></span>                          | <span data-ttu-id="43d2c-123">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="43d2c-123">Template name</span></span>    | <span data-ttu-id="43d2c-124">Języki</span><span class="sxs-lookup"><span data-stu-id="43d2c-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="43d2c-125">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="43d2c-125">Console application</span></span>                          | `console`        | <span data-ttu-id="43d2c-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="43d2c-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="43d2c-127">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="43d2c-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="43d2c-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="43d2c-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="43d2c-129">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="43d2c-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="43d2c-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="43d2c-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="43d2c-131">xUnit test project</span><span class="sxs-lookup"><span data-stu-id="43d2c-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="43d2c-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="43d2c-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="43d2c-133">NUnit test project</span><span class="sxs-lookup"><span data-stu-id="43d2c-133">NUnit test project</span></span>                           | `nunit`          | <span data-ttu-id="43d2c-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="43d2c-134">[C#], F#, VB</span></span>  |
| <span data-ttu-id="43d2c-135">Strona razor</span><span class="sxs-lookup"><span data-stu-id="43d2c-135">Razor page</span></span>                                   | `page`           | <span data-ttu-id="43d2c-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-136">[C#]</span></span>          |
| <span data-ttu-id="43d2c-137">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="43d2c-137">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="43d2c-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-138">[C#]</span></span>          |
| <span data-ttu-id="43d2c-139">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="43d2c-139">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="43d2c-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-140">[C#]</span></span>          |
| <span data-ttu-id="43d2c-141">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="43d2c-141">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="43d2c-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-142">[C#], F#</span></span>      |
| <span data-ttu-id="43d2c-143">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="43d2c-143">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="43d2c-144">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-144">[C#], F#</span></span>      |
| <span data-ttu-id="43d2c-145">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43d2c-145">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="43d2c-146">`razor`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="43d2c-146">`razor`, `webapp`</span></span>| <span data-ttu-id="43d2c-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-147">[C#]</span></span>          |
| <span data-ttu-id="43d2c-148">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="43d2c-148">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="43d2c-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-149">[C#]</span></span>          |
| <span data-ttu-id="43d2c-150">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="43d2c-150">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="43d2c-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-151">[C#]</span></span>          |
| <span data-ttu-id="43d2c-152">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="43d2c-152">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="43d2c-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-153">[C#]</span></span>          |
| <span data-ttu-id="43d2c-154">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43d2c-154">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="43d2c-155">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-155">[C#], F#</span></span>      |
| <span data-ttu-id="43d2c-156">Biblioteki klas razor</span><span class="sxs-lookup"><span data-stu-id="43d2c-156">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="43d2c-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-157">[C#]</span></span>          |
| <span data-ttu-id="43d2c-158">global.json file</span><span class="sxs-lookup"><span data-stu-id="43d2c-158">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="43d2c-159">NuGet config</span><span class="sxs-lookup"><span data-stu-id="43d2c-159">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="43d2c-160">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="43d2c-160">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="43d2c-161">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="43d2c-161">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="43d2c-162">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="43d2c-162">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="43d2c-163">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-163">The command contains a default list of templates.</span></span> <span data-ttu-id="43d2c-164">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-164">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="43d2c-165">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą platformy .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="43d2c-165">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="43d2c-166">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-166">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="43d2c-167">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="43d2c-167">Template description</span></span>                          | <span data-ttu-id="43d2c-168">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="43d2c-168">Template name</span></span> | <span data-ttu-id="43d2c-169">Języki</span><span class="sxs-lookup"><span data-stu-id="43d2c-169">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="43d2c-170">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="43d2c-170">Console application</span></span>                          | `console`     | <span data-ttu-id="43d2c-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="43d2c-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="43d2c-172">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="43d2c-172">Class library</span></span>                                | `classlib`    | <span data-ttu-id="43d2c-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="43d2c-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="43d2c-174">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="43d2c-174">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="43d2c-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="43d2c-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="43d2c-176">xUnit test project</span><span class="sxs-lookup"><span data-stu-id="43d2c-176">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="43d2c-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="43d2c-177">[C#], F#, VB</span></span>  |
| <span data-ttu-id="43d2c-178">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="43d2c-178">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="43d2c-179">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-179">[C#], F#</span></span>      |
| <span data-ttu-id="43d2c-180">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="43d2c-180">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="43d2c-181">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-181">[C#], F#</span></span>      |
| <span data-ttu-id="43d2c-182">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43d2c-182">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="43d2c-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-183">[C#]</span></span>          |
| <span data-ttu-id="43d2c-184">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="43d2c-184">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="43d2c-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-185">[C#]</span></span>          |
| <span data-ttu-id="43d2c-186">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="43d2c-186">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="43d2c-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-187">[C#]</span></span>          |
| <span data-ttu-id="43d2c-188">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="43d2c-188">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="43d2c-189">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-189">[C#]</span></span>          |
| <span data-ttu-id="43d2c-190">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43d2c-190">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="43d2c-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-191">[C#], F#</span></span>      |
| <span data-ttu-id="43d2c-192">global.json file</span><span class="sxs-lookup"><span data-stu-id="43d2c-192">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="43d2c-193">NuGet config</span><span class="sxs-lookup"><span data-stu-id="43d2c-193">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="43d2c-194">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="43d2c-194">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="43d2c-195">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="43d2c-195">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="43d2c-196">Strona razor</span><span class="sxs-lookup"><span data-stu-id="43d2c-196">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="43d2c-197">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="43d2c-197">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="43d2c-198">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="43d2c-198">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="43d2c-199">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="43d2c-199">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="43d2c-200">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-200">The command contains a default list of templates.</span></span> <span data-ttu-id="43d2c-201">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-201">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="43d2c-202">W poniższej tabeli przedstawiono szablony, które są zainstalowane za pomocą zestawu SDK programu .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="43d2c-202">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="43d2c-203">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-203">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="43d2c-204">Opis szablonu</span><span class="sxs-lookup"><span data-stu-id="43d2c-204">Template description</span></span>  | <span data-ttu-id="43d2c-205">Nazwa szablonu</span><span class="sxs-lookup"><span data-stu-id="43d2c-205">Template name</span></span> | <span data-ttu-id="43d2c-206">Języki</span><span class="sxs-lookup"><span data-stu-id="43d2c-206">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="43d2c-207">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="43d2c-207">Console application</span></span>  | `console`     | <span data-ttu-id="43d2c-208">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-208">[C#], F#</span></span>  |
| <span data-ttu-id="43d2c-209">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="43d2c-209">Class library</span></span>        | `classlib`    | <span data-ttu-id="43d2c-210">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-210">[C#], F#</span></span>  |
| <span data-ttu-id="43d2c-211">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="43d2c-211">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="43d2c-212">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-212">[C#], F#</span></span>  |
| <span data-ttu-id="43d2c-213">xUnit test project</span><span class="sxs-lookup"><span data-stu-id="43d2c-213">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="43d2c-214">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-214">[C#], F#</span></span>  |
| <span data-ttu-id="43d2c-215">Platforma ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="43d2c-215">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="43d2c-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-216">[C#]</span></span>      |
| <span data-ttu-id="43d2c-217">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43d2c-217">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="43d2c-218">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="43d2c-218">[C#], F#</span></span>  |
| <span data-ttu-id="43d2c-219">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43d2c-219">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="43d2c-220">[C#]</span><span class="sxs-lookup"><span data-stu-id="43d2c-220">[C#]</span></span>      |
| <span data-ttu-id="43d2c-221">NuGet config</span><span class="sxs-lookup"><span data-stu-id="43d2c-221">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="43d2c-222">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="43d2c-222">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="43d2c-223">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="43d2c-223">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="43d2c-224">Opcje</span><span class="sxs-lookup"><span data-stu-id="43d2c-224">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="43d2c-225">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="43d2c-225">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="43d2c-226">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="43d2c-226">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="43d2c-227">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-227">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="43d2c-228">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-228">Prints out help for the command.</span></span> <span data-ttu-id="43d2c-229">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-229">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="43d2c-230">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="43d2c-230">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="43d2c-231">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-231">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="43d2c-232">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="43d2c-232">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="43d2c-233">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="43d2c-233">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="43d2c-234">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="43d2c-234">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="43d2c-235">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-235">Lists templates containing the specified name.</span></span> <span data-ttu-id="43d2c-236">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-236">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="43d2c-237">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-237">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="43d2c-238">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-238">The language of the template to create.</span></span> <span data-ttu-id="43d2c-239">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="43d2c-239">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="43d2c-240">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-240">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="43d2c-241">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="43d2c-241">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="43d2c-242">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-242">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="43d2c-243">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="43d2c-243">The name for the created output.</span></span> <span data-ttu-id="43d2c-244">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-244">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="43d2c-245">Określa źródła pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="43d2c-245">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="43d2c-246">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="43d2c-246">Location to place the generated output.</span></span> <span data-ttu-id="43d2c-247">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="43d2c-247">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="43d2c-248">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-248">Filters templates based on available types.</span></span> <span data-ttu-id="43d2c-249">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="43d2c-249">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="43d2c-250">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="43d2c-250">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="43d2c-251">Aby odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="43d2c-251">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="43d2c-252">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-252">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="43d2c-253">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-253">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="43d2c-254">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="43d2c-254">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="43d2c-255">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="43d2c-255">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="43d2c-256">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-256">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="43d2c-257">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-257">Prints out help for the command.</span></span> <span data-ttu-id="43d2c-258">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-258">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="43d2c-259">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="43d2c-259">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="43d2c-260">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-260">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="43d2c-261">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="43d2c-261">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="43d2c-262">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="43d2c-262">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="43d2c-263">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="43d2c-263">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="43d2c-264">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-264">Lists templates containing the specified name.</span></span> <span data-ttu-id="43d2c-265">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-265">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="43d2c-266">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-266">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="43d2c-267">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-267">The language of the template to create.</span></span> <span data-ttu-id="43d2c-268">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="43d2c-268">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="43d2c-269">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-269">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="43d2c-270">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="43d2c-270">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="43d2c-271">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-271">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="43d2c-272">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="43d2c-272">The name for the created output.</span></span> <span data-ttu-id="43d2c-273">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-273">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="43d2c-274">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="43d2c-274">Location to place the generated output.</span></span> <span data-ttu-id="43d2c-275">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="43d2c-275">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="43d2c-276">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-276">Filters templates based on available types.</span></span> <span data-ttu-id="43d2c-277">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="43d2c-277">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="43d2c-278">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="43d2c-278">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="43d2c-279">Aby odinstalować szablonu korzystanie ze źródła `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="43d2c-279">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="43d2c-280">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-280">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="43d2c-281">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-281">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="43d2c-282">Jeśli nie można określić `PATH` lub `NUGET_ID` argument niezbędnych do odinstalowania szablon systemem `dotnet new --uninstall` bez argumentu, spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argument, trzeba je odinstalować.</span><span class="sxs-lookup"><span data-stu-id="43d2c-282">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="43d2c-283">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="43d2c-283">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="43d2c-284">Przedstawia wszystkie szablony dla określonego typu projektu, podczas uruchamiania w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-284">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="43d2c-285">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="43d2c-285">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="43d2c-286">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-286">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="43d2c-287">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-287">Prints out help for the command.</span></span> <span data-ttu-id="43d2c-288">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-288">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="43d2c-289">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-289">Lists templates containing the specified name.</span></span> <span data-ttu-id="43d2c-290">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-290">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="43d2c-291">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-291">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="43d2c-292">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-292">The language of the template to create.</span></span> <span data-ttu-id="43d2c-293">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="43d2c-293">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="43d2c-294">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="43d2c-294">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="43d2c-295">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="43d2c-295">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="43d2c-296">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-296">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="43d2c-297">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="43d2c-297">The name for the created output.</span></span> <span data-ttu-id="43d2c-298">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-298">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="43d2c-299">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="43d2c-299">Location to place the generated output.</span></span> <span data-ttu-id="43d2c-300">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="43d2c-300">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="43d2c-301">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="43d2c-301">Template options</span></span>

<span data-ttu-id="43d2c-302">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="43d2c-302">Each project template may have additional options available.</span></span> <span data-ttu-id="43d2c-303">Szablony core są dostępne następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="43d2c-303">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="43d2c-304">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="43d2c-304">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="43d2c-305">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="43d2c-305">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="43d2c-306">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-306">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-307">**classlib**</span><span class="sxs-lookup"><span data-stu-id="43d2c-307">**classlib**</span></span>

<span data-ttu-id="43d2c-308">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="43d2c-308">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="43d2c-309">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="43d2c-309">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="43d2c-310">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-310">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="43d2c-311">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-312">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="43d2c-312">**mstest, xunit**</span></span>

<span data-ttu-id="43d2c-313">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="43d2c-313">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="43d2c-314">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-314">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-315">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="43d2c-315">**globaljson**</span></span>

<span data-ttu-id="43d2c-316">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="43d2c-316">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="43d2c-317">**web**</span><span class="sxs-lookup"><span data-stu-id="43d2c-317">**web**</span></span>

<span data-ttu-id="43d2c-318">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-318">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="43d2c-319">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-319">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-320">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="43d2c-320">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="43d2c-321">Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualAuth` lub `OrganizationalAuth` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="43d2c-321">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="43d2c-322">**webapi**</span><span class="sxs-lookup"><span data-stu-id="43d2c-322">**webapi**</span></span>

<span data-ttu-id="43d2c-323">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-323">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="43d2c-324">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="43d2c-324">The possible values are:</span></span>

- <span data-ttu-id="43d2c-325">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="43d2c-325">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="43d2c-326">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="43d2c-326">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="43d2c-327">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-327">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="43d2c-328">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="43d2c-328">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="43d2c-329">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-329">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="43d2c-330">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-330">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-331">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-331">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="43d2c-332">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-332">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="43d2c-333">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-333">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-334">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-334">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="43d2c-335">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-335">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="43d2c-336">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-336">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="43d2c-337">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-337">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="43d2c-338">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-338">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="43d2c-339">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-339">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="43d2c-340">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-340">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="43d2c-341">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-341">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-342">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-342">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="43d2c-343">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-343">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="43d2c-344">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-344">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="43d2c-345">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-345">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="43d2c-346">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43d2c-346">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="43d2c-347">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-347">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="43d2c-348">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-348">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="43d2c-349">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="43d2c-349">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="43d2c-350">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-350">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-351">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-351">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-352">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="43d2c-352">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="43d2c-353">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-353">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="43d2c-354">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="43d2c-354">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="43d2c-355">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="43d2c-355">**mvc, razor**</span></span>

<span data-ttu-id="43d2c-356">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-356">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="43d2c-357">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="43d2c-357">The possible values are:</span></span>

- <span data-ttu-id="43d2c-358">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="43d2c-358">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="43d2c-359">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="43d2c-359">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="43d2c-360">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="43d2c-360">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="43d2c-361">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-361">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="43d2c-362">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="43d2c-362">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="43d2c-363">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="43d2c-363">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="43d2c-364">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-364">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="43d2c-365">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-365">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-366">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-366">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="43d2c-367">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-367">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="43d2c-368">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-369">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-369">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="43d2c-370">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-371">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-371">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="43d2c-372">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-372">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-373">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-373">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="43d2c-374">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-374">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="43d2c-375">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-375">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="43d2c-376">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-376">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="43d2c-377">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-377">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="43d2c-378">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-378">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="43d2c-379">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-379">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="43d2c-380">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-380">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-381">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-381">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="43d2c-382">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-382">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="43d2c-383">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-383">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="43d2c-384">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-384">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="43d2c-385">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43d2c-385">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="43d2c-386">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-386">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-387">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-387">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="43d2c-388">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43d2c-388">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="43d2c-389">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-389">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="43d2c-390">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-390">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="43d2c-391">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-391">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="43d2c-392">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="43d2c-392">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="43d2c-393">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-393">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-394">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-395">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="43d2c-395">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="43d2c-396">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-396">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="43d2c-397">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="43d2c-397">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="43d2c-398">**page**</span><span class="sxs-lookup"><span data-stu-id="43d2c-398">**page**</span></span>

<span data-ttu-id="43d2c-399">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="43d2c-400">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-400">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="43d2c-401">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="43d2c-401">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="43d2c-402">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="43d2c-402">**viewimports**</span></span>

<span data-ttu-id="43d2c-403">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-403">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="43d2c-404">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-404">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="43d2c-405">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="43d2c-405">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="43d2c-406">**Konsola, angular, react reactredux dla platformy**</span><span class="sxs-lookup"><span data-stu-id="43d2c-406">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="43d2c-407">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-407">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-408">**classlib**</span><span class="sxs-lookup"><span data-stu-id="43d2c-408">**classlib**</span></span>

<span data-ttu-id="43d2c-409">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="43d2c-409">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="43d2c-410">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="43d2c-410">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="43d2c-411">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-411">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="43d2c-412">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-413">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="43d2c-413">**mstest, xunit**</span></span>

<span data-ttu-id="43d2c-414">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="43d2c-414">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="43d2c-415">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-415">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-416">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="43d2c-416">**globaljson**</span></span>

<span data-ttu-id="43d2c-417">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="43d2c-417">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="43d2c-418">**web**</span><span class="sxs-lookup"><span data-stu-id="43d2c-418">**web**</span></span>

<span data-ttu-id="43d2c-419">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="43d2c-419">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="43d2c-420">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-420">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-421">**webapi**</span><span class="sxs-lookup"><span data-stu-id="43d2c-421">**webapi**</span></span>

<span data-ttu-id="43d2c-422">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-422">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="43d2c-423">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="43d2c-423">The possible values are:</span></span>

- <span data-ttu-id="43d2c-424">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="43d2c-424">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="43d2c-425">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="43d2c-425">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="43d2c-426">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-426">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="43d2c-427">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="43d2c-427">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="43d2c-428">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-428">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="43d2c-429">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-429">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-430">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-430">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="43d2c-431">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-431">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="43d2c-432">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-432">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-433">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-433">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="43d2c-434">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-434">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="43d2c-435">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-435">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="43d2c-436">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-436">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="43d2c-437">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-437">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="43d2c-438">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-438">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="43d2c-439">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-439">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="43d2c-440">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-440">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-441">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-441">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="43d2c-442">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-442">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="43d2c-443">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-443">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="43d2c-444">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-444">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="43d2c-445">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43d2c-445">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="43d2c-446">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-446">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="43d2c-447">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="43d2c-447">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="43d2c-448">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="43d2c-448">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="43d2c-449">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-449">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-450">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-450">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-451">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="43d2c-451">**mvc, razor**</span></span>

<span data-ttu-id="43d2c-452">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-452">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="43d2c-453">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="43d2c-453">The possible values are:</span></span>

- <span data-ttu-id="43d2c-454">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="43d2c-454">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="43d2c-455">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="43d2c-455">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="43d2c-456">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="43d2c-456">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="43d2c-457">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="43d2c-457">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="43d2c-458">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="43d2c-458">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="43d2c-459">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="43d2c-459">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="43d2c-460">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-460">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="43d2c-461">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-461">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-462">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-462">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="43d2c-463">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-463">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="43d2c-464">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-465">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-465">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="43d2c-466">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-467">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-467">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="43d2c-468">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-468">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-469">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-469">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="43d2c-470">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-470">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="43d2c-471">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-471">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="43d2c-472">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-472">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="43d2c-473">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-473">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="43d2c-474">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-474">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="43d2c-475">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-475">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="43d2c-476">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-476">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-477">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-477">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="43d2c-478">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-478">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="43d2c-479">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-479">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="43d2c-480">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-480">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="43d2c-481">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43d2c-481">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="43d2c-482">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-482">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="43d2c-483">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-483">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="43d2c-484">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43d2c-484">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="43d2c-485">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-485">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="43d2c-486">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="43d2c-486">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="43d2c-487">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="43d2c-487">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="43d2c-488">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="43d2c-488">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="43d2c-489">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="43d2c-489">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="43d2c-490">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-490">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="43d2c-491">**page**</span><span class="sxs-lookup"><span data-stu-id="43d2c-491">**page**</span></span>

<span data-ttu-id="43d2c-492">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="43d2c-493">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-493">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="43d2c-494">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="43d2c-494">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="43d2c-495">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="43d2c-495">**viewimports**</span></span>

<span data-ttu-id="43d2c-496">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="43d2c-496">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="43d2c-497">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-497">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="43d2c-498">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="43d2c-498">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="43d2c-499">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="43d2c-499">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="43d2c-500">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="43d2c-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="43d2c-501">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-501">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="43d2c-502">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-502">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="43d2c-503">**classlib**</span><span class="sxs-lookup"><span data-stu-id="43d2c-503">**classlib**</span></span>

<span data-ttu-id="43d2c-504">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="43d2c-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="43d2c-505">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-505">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="43d2c-506">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-506">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="43d2c-507">**mvc**</span><span class="sxs-lookup"><span data-stu-id="43d2c-507">**mvc**</span></span>

<span data-ttu-id="43d2c-508">`-f|--framework` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="43d2c-508">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="43d2c-509">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-509">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="43d2c-510">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-510">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="43d2c-511">`-au|--auth` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="43d2c-511">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="43d2c-512">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-512">Values: `None` or `Individual`.</span></span> <span data-ttu-id="43d2c-513">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-513">The default value is `None`.</span></span>

<span data-ttu-id="43d2c-514">`-uld|--use-local-db` -Określa, czy należy użyć programu LocalDB zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="43d2c-514">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="43d2c-515">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-515">Values: `true` or `false`.</span></span> <span data-ttu-id="43d2c-516">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="43d2c-516">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="43d2c-517">Przykłady</span><span class="sxs-lookup"><span data-stu-id="43d2c-517">Examples</span></span>

<span data-ttu-id="43d2c-518">Tworzenie F# projekt aplikacji konsoli w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="43d2c-518">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="43d2c-519">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="43d2c-519">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="43d2c-520">Utwórz nowy projekt aplikacji w języku C# MVC ASP.NET Core w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="43d2c-520">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="43d2c-521">Utwórz nową aplikację xUnit:</span><span class="sxs-lookup"><span data-stu-id="43d2c-521">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="43d2c-522">Wyświetl wszystkie szablony dostępne dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="43d2c-522">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="43d2c-523">Zainstaluj wersję 2.0 szablonów aplikacji jednostronicowej dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="43d2c-523">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="43d2c-524">Tworzenie *global.json* w bieżącym katalogu, ustawienie wersji zestawu SDK 2.0.0 (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="43d2c-524">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="43d2c-525">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43d2c-525">See also</span></span>

- [<span data-ttu-id="43d2c-526">Szablony niestandardowe dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="43d2c-526">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="43d2c-527">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="43d2c-527">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)
- [<span data-ttu-id="43d2c-528">repozytorium GitHub DotNet/dotnet-— przykłady szablonów</span><span class="sxs-lookup"><span data-stu-id="43d2c-528">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="43d2c-529">Dostępne szablony dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="43d2c-529">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
