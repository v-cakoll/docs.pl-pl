---
title: polecenie dotnet New
description: Polecenie dotnet New umożliwia tworzenie nowych projektów platformy .NET Core na podstawie określonego szablonu.
ms.date: 05/06/2019
ms.openlocfilehash: c9529e135f48c80f445c91038294a3e7266486f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420476"
---
# <a name="dotnet-new"></a><span data-ttu-id="dbc2f-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="dbc2f-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="dbc2f-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="dbc2f-104">Name</span></span>

<span data-ttu-id="dbc2f-105">`dotnet new` — tworzy nowy projekt, plik konfiguracji lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dbc2f-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="dbc2f-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="dbc2f-107">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="dbc2f-107">.NET Core 2.2</span></span>](#tab/netcore22)

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="dbc2f-108">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="dbc2f-108">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="dbc2f-109">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="dbc2f-109">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dbc2f-110">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="dbc2f-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="dbc2f-111">Opis</span><span class="sxs-lookup"><span data-stu-id="dbc2f-111">Description</span></span>

<span data-ttu-id="dbc2f-112">`dotnet new` polecenie zapewnia wygodny sposób zainicjowania prawidłowego projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="dbc2f-113">Polecenie wywołuje [aparat szablonu](https://github.com/dotnet/templating) , aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="dbc2f-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dbc2f-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="dbc2f-115">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="dbc2f-116">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="dbc2f-117">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="dbc2f-118">Jeśli wartość `TEMPLATE` nie jest dokładnym dopasowaniem do tekstu w kolumnie **templates** lub **short name** , do tych dwóch kolumn jest wykonywane dopasowanie podciągów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="dbc2f-119">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="dbc2f-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="dbc2f-120">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-120">The command contains a default list of templates.</span></span> <span data-ttu-id="dbc2f-121">Użyj `dotnet new -l`, aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="dbc2f-122">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="dbc2f-123">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="dbc2f-124">Szablony</span><span class="sxs-lookup"><span data-stu-id="dbc2f-124">Templates</span></span>                                    | <span data-ttu-id="dbc2f-125">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="dbc2f-125">Short Name</span></span>        | <span data-ttu-id="dbc2f-126">Język</span><span class="sxs-lookup"><span data-stu-id="dbc2f-126">Language</span></span>     | <span data-ttu-id="dbc2f-127">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="dbc2f-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="dbc2f-128">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="dbc2f-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="dbc2f-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-129">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-130">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="dbc2f-130">Common/Console</span></span>                        |
| <span data-ttu-id="dbc2f-131">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="dbc2f-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="dbc2f-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-132">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-133">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="dbc2f-133">Common/Library</span></span>                        |
| <span data-ttu-id="dbc2f-134">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="dbc2f-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="dbc2f-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-135">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="dbc2f-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="dbc2f-137">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="dbc2f-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="dbc2f-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-138">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="dbc2f-140">Element testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="dbc2f-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="dbc2f-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-141">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="dbc2f-143">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="dbc2f-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-144">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="dbc2f-146">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="dbc2f-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="dbc2f-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-147">[C#]</span></span>         | <span data-ttu-id="dbc2f-148">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dbc2f-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="dbc2f-149">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="dbc2f-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-150">[C#]</span></span>         | <span data-ttu-id="dbc2f-151">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dbc2f-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="dbc2f-152">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="dbc2f-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-153">[C#]</span></span>         | <span data-ttu-id="dbc2f-154">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dbc2f-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="dbc2f-155">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="dbc2f-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="dbc2f-156">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-156">[C#], F#</span></span>     | <span data-ttu-id="dbc2f-157">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="dbc2f-157">Web/Empty</span></span>                             |
| <span data-ttu-id="dbc2f-158">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="dbc2f-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="dbc2f-159">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-159">[C#], F#</span></span>     | <span data-ttu-id="dbc2f-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-160">Web/MVC</span></span>                               |
| <span data-ttu-id="dbc2f-161">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dbc2f-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="dbc2f-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="dbc2f-162">`webapp`, `razor`</span></span> | <span data-ttu-id="dbc2f-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-163">[C#]</span></span>         | <span data-ttu-id="dbc2f-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="dbc2f-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="dbc2f-165">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="dbc2f-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="dbc2f-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-166">[C#]</span></span>         | <span data-ttu-id="dbc2f-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dbc2f-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="dbc2f-168">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="dbc2f-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="dbc2f-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-169">[C#]</span></span>         | <span data-ttu-id="dbc2f-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dbc2f-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="dbc2f-171">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="dbc2f-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="dbc2f-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-172">[C#]</span></span>         | <span data-ttu-id="dbc2f-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dbc2f-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="dbc2f-174">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="dbc2f-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="dbc2f-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-175">[C#]</span></span>         | <span data-ttu-id="dbc2f-176">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="dbc2f-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="dbc2f-177">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dbc2f-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="dbc2f-178">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-178">[C#], F#</span></span>     | <span data-ttu-id="dbc2f-179">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="dbc2f-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="dbc2f-180">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="dbc2f-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="dbc2f-181">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-181">Config</span></span>                                |
| <span data-ttu-id="dbc2f-182">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="dbc2f-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="dbc2f-183">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-183">Config</span></span>                                |
| <span data-ttu-id="dbc2f-184">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="dbc2f-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="dbc2f-185">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-185">Config</span></span>                                |
| <span data-ttu-id="dbc2f-186">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="dbc2f-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="dbc2f-187">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="dbc2f-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="dbc2f-188">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="dbc2f-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="dbc2f-189">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-189">The command contains a default list of templates.</span></span> <span data-ttu-id="dbc2f-190">Użyj `dotnet new -l`, aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="dbc2f-191">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="dbc2f-192">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="dbc2f-193">Szablony</span><span class="sxs-lookup"><span data-stu-id="dbc2f-193">Templates</span></span>                                    | <span data-ttu-id="dbc2f-194">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="dbc2f-194">Short Name</span></span>      | <span data-ttu-id="dbc2f-195">Język</span><span class="sxs-lookup"><span data-stu-id="dbc2f-195">Language</span></span>     | <span data-ttu-id="dbc2f-196">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="dbc2f-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="dbc2f-197">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="dbc2f-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="dbc2f-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-198">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-199">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="dbc2f-199">Common/Console</span></span>                        |
| <span data-ttu-id="dbc2f-200">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="dbc2f-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="dbc2f-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-201">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-202">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="dbc2f-202">Common/Library</span></span>                        |
| <span data-ttu-id="dbc2f-203">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="dbc2f-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="dbc2f-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-204">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="dbc2f-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="dbc2f-206">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="dbc2f-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-207">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="dbc2f-209">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="dbc2f-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="dbc2f-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-210">[C#]</span></span>         | <span data-ttu-id="dbc2f-211">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dbc2f-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="dbc2f-212">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="dbc2f-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-213">[C#]</span></span>         | <span data-ttu-id="dbc2f-214">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dbc2f-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="dbc2f-215">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="dbc2f-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-216">[C#]</span></span>         | <span data-ttu-id="dbc2f-217">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dbc2f-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="dbc2f-218">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="dbc2f-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="dbc2f-219">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-219">[C#], F#</span></span>     | <span data-ttu-id="dbc2f-220">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="dbc2f-220">Web/Empty</span></span>                             |
| <span data-ttu-id="dbc2f-221">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="dbc2f-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="dbc2f-222">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-222">[C#], F#</span></span>     | <span data-ttu-id="dbc2f-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-223">Web/MVC</span></span>                               |
| <span data-ttu-id="dbc2f-224">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dbc2f-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="dbc2f-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-225">[C#]</span></span>         | <span data-ttu-id="dbc2f-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="dbc2f-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="dbc2f-227">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="dbc2f-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="dbc2f-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-228">[C#]</span></span>         | <span data-ttu-id="dbc2f-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dbc2f-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="dbc2f-230">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="dbc2f-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="dbc2f-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-231">[C#]</span></span>         | <span data-ttu-id="dbc2f-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dbc2f-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="dbc2f-233">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="dbc2f-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="dbc2f-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-234">[C#]</span></span>         | <span data-ttu-id="dbc2f-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dbc2f-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="dbc2f-236">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="dbc2f-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="dbc2f-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-237">[C#]</span></span>         | <span data-ttu-id="dbc2f-238">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="dbc2f-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="dbc2f-239">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dbc2f-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="dbc2f-240">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-240">[C#], F#</span></span>     | <span data-ttu-id="dbc2f-241">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="dbc2f-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="dbc2f-242">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="dbc2f-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="dbc2f-243">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-243">Config</span></span>                                |
| <span data-ttu-id="dbc2f-244">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="dbc2f-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="dbc2f-245">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-245">Config</span></span>                                |
| <span data-ttu-id="dbc2f-246">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="dbc2f-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="dbc2f-247">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-247">Config</span></span>                                |
| <span data-ttu-id="dbc2f-248">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="dbc2f-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="dbc2f-249">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="dbc2f-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="dbc2f-250">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="dbc2f-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="dbc2f-251">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-251">The command contains a default list of templates.</span></span> <span data-ttu-id="dbc2f-252">Użyj `dotnet new -l`, aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="dbc2f-253">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="dbc2f-254">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="dbc2f-255">Szablony</span><span class="sxs-lookup"><span data-stu-id="dbc2f-255">Templates</span></span>                                    | <span data-ttu-id="dbc2f-256">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="dbc2f-256">Short Name</span></span>    | <span data-ttu-id="dbc2f-257">Język</span><span class="sxs-lookup"><span data-stu-id="dbc2f-257">Language</span></span>     | <span data-ttu-id="dbc2f-258">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="dbc2f-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="dbc2f-259">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="dbc2f-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="dbc2f-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-260">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-261">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="dbc2f-261">Common/Console</span></span>      |
| <span data-ttu-id="dbc2f-262">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="dbc2f-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="dbc2f-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-263">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-264">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="dbc2f-264">Common/Library</span></span>      |
| <span data-ttu-id="dbc2f-265">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="dbc2f-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="dbc2f-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-266">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="dbc2f-267">Test/MSTest</span></span>         |
| <span data-ttu-id="dbc2f-268">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="dbc2f-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="dbc2f-269">[C#], F#, VB</span></span> | <span data-ttu-id="dbc2f-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-270">Test/xUnit</span></span>          |
| <span data-ttu-id="dbc2f-271">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="dbc2f-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="dbc2f-272">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-272">[C#], F#</span></span>     | <span data-ttu-id="dbc2f-273">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="dbc2f-273">Web/Empty</span></span>           |
| <span data-ttu-id="dbc2f-274">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="dbc2f-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="dbc2f-275">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-275">[C#], F#</span></span>     | <span data-ttu-id="dbc2f-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-276">Web/MVC</span></span>             |
| <span data-ttu-id="dbc2f-277">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dbc2f-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="dbc2f-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-278">[C#]</span></span>         | <span data-ttu-id="dbc2f-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="dbc2f-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="dbc2f-280">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="dbc2f-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="dbc2f-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-281">[C#]</span></span>         | <span data-ttu-id="dbc2f-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dbc2f-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="dbc2f-283">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="dbc2f-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="dbc2f-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-284">[C#]</span></span>         | <span data-ttu-id="dbc2f-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dbc2f-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="dbc2f-286">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="dbc2f-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="dbc2f-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-287">[C#]</span></span>         | <span data-ttu-id="dbc2f-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="dbc2f-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="dbc2f-289">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dbc2f-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="dbc2f-290">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-290">[C#], F#</span></span>     | <span data-ttu-id="dbc2f-291">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="dbc2f-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="dbc2f-292">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="dbc2f-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="dbc2f-293">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-293">Config</span></span>              |
| <span data-ttu-id="dbc2f-294">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="dbc2f-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="dbc2f-295">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-295">Config</span></span>              |
| <span data-ttu-id="dbc2f-296">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="dbc2f-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="dbc2f-297">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-297">Config</span></span>              |
| <span data-ttu-id="dbc2f-298">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="dbc2f-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="dbc2f-299">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="dbc2f-299">Solution</span></span>            |
| <span data-ttu-id="dbc2f-300">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="dbc2f-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="dbc2f-301">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dbc2f-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="dbc2f-302">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="dbc2f-303">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dbc2f-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="dbc2f-304">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="dbc2f-305">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="dbc2f-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dbc2f-306">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="dbc2f-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="dbc2f-307">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-307">The command contains a default list of templates.</span></span> <span data-ttu-id="dbc2f-308">Użyj `dotnet new -all`, aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="dbc2f-309">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="dbc2f-310">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="dbc2f-311">Szablony</span><span class="sxs-lookup"><span data-stu-id="dbc2f-311">Templates</span></span>            | <span data-ttu-id="dbc2f-312">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="dbc2f-312">Short Name</span></span>    | <span data-ttu-id="dbc2f-313">Język</span><span class="sxs-lookup"><span data-stu-id="dbc2f-313">Language</span></span> | <span data-ttu-id="dbc2f-314">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="dbc2f-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="dbc2f-315">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="dbc2f-315">Console Application</span></span>  | `console`     | <span data-ttu-id="dbc2f-316">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-316">[C#], F#</span></span> | <span data-ttu-id="dbc2f-317">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="dbc2f-317">Common/Console</span></span> |
| <span data-ttu-id="dbc2f-318">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="dbc2f-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="dbc2f-319">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-319">[C#], F#</span></span> | <span data-ttu-id="dbc2f-320">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="dbc2f-320">Common/Library</span></span> |
| <span data-ttu-id="dbc2f-321">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="dbc2f-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="dbc2f-322">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-322">[C#], F#</span></span> | <span data-ttu-id="dbc2f-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="dbc2f-323">Test/MSTest</span></span>    |
| <span data-ttu-id="dbc2f-324">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="dbc2f-325">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-325">[C#], F#</span></span> | <span data-ttu-id="dbc2f-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="dbc2f-326">Test/xUnit</span></span>     |
| <span data-ttu-id="dbc2f-327">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="dbc2f-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="dbc2f-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-328">[C#]</span></span>     | <span data-ttu-id="dbc2f-329">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="dbc2f-329">Web/Empty</span></span>      |
| <span data-ttu-id="dbc2f-330">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dbc2f-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="dbc2f-331">[C#],F#</span><span class="sxs-lookup"><span data-stu-id="dbc2f-331">[C#], F#</span></span> | <span data-ttu-id="dbc2f-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="dbc2f-332">Web/MVC</span></span>        |
| <span data-ttu-id="dbc2f-333">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dbc2f-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="dbc2f-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="dbc2f-334">[C#]</span></span>     | <span data-ttu-id="dbc2f-335">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="dbc2f-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="dbc2f-336">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="dbc2f-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="dbc2f-337">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-337">Config</span></span>         |
| <span data-ttu-id="dbc2f-338">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="dbc2f-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="dbc2f-339">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dbc2f-339">Config</span></span>         |
| <span data-ttu-id="dbc2f-340">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="dbc2f-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="dbc2f-341">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="dbc2f-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="dbc2f-342">Opcje</span><span class="sxs-lookup"><span data-stu-id="dbc2f-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="dbc2f-343">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="dbc2f-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="dbc2f-344">Wyświetla podsumowanie tego, co się stanie w przypadku uruchomienia danego polecenia, jeśli mogłoby to spowodować utworzenie szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="dbc2f-345">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="dbc2f-346">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="dbc2f-347">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-347">Prints out help for the command.</span></span> <span data-ttu-id="dbc2f-348">Może być wywoływana dla samego polecenia `dotnet new` lub dla dowolnego szablonu, takiego jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="dbc2f-349">Instaluje pakiet źródłowy lub szablon z podanej `PATH` lub `NUGET_ID`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="dbc2f-350">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="dbc2f-351">Domyślnie `dotnet new` przekazuje \* wersji, co reprezentuje ostatnią stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="dbc2f-352">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="dbc2f-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="dbc2f-353">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="dbc2f-354">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="dbc2f-355">Jeśli zostanie wywołana dla polecenia `dotnet new`, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="dbc2f-356">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="dbc2f-357">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-357">The language of the template to create.</span></span> <span data-ttu-id="dbc2f-358">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="dbc2f-359">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="dbc2f-360">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="dbc2f-361">W takich przypadkach należy ująć wartość parametru language, taką jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="dbc2f-362">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-362">The name for the created output.</span></span> <span data-ttu-id="dbc2f-363">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="dbc2f-364">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dbc2f-365">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-365">Location to place the generated output.</span></span> <span data-ttu-id="dbc2f-366">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="dbc2f-367">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-367">Filters templates based on available types.</span></span> <span data-ttu-id="dbc2f-368">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="dbc2f-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="dbc2f-369">Odinstalowuje pakiet źródłowy lub szablonowy na `PATH` lub `NUGET_ID` udostępniony.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="dbc2f-370">Podczas wykluczania wartości `<PATH|NUGET_ID>` są wyświetlane wszystkie aktualnie zainstalowane pakiety szablonów i powiązane z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="dbc2f-371">Aby odinstalować szablon przy użyciu `PATH`, musisz w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="dbc2f-372">Na przykład *C:/Users/\<USER >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="dbc2f-373">Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="dbc2f-374">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="dbc2f-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="dbc2f-375">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="dbc2f-376">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="dbc2f-377">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-377">Prints out help for the command.</span></span> <span data-ttu-id="dbc2f-378">Może być wywoływana dla samego polecenia `dotnet new` lub dla dowolnego szablonu, takiego jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="dbc2f-379">Instaluje pakiet źródłowy lub szablon z podanej `PATH` lub `NUGET_ID`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="dbc2f-380">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="dbc2f-381">Domyślnie `dotnet new` przekazuje \* wersji, co reprezentuje ostatnią stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="dbc2f-382">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="dbc2f-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="dbc2f-383">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="dbc2f-384">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="dbc2f-385">Jeśli zostanie wywołana dla polecenia `dotnet new`, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="dbc2f-386">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="dbc2f-387">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-387">The language of the template to create.</span></span> <span data-ttu-id="dbc2f-388">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="dbc2f-389">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="dbc2f-390">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="dbc2f-391">W takich przypadkach należy ująć wartość parametru language, taką jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="dbc2f-392">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-392">The name for the created output.</span></span> <span data-ttu-id="dbc2f-393">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="dbc2f-394">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dbc2f-395">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-395">Location to place the generated output.</span></span> <span data-ttu-id="dbc2f-396">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="dbc2f-397">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-397">Filters templates based on available types.</span></span> <span data-ttu-id="dbc2f-398">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="dbc2f-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="dbc2f-399">Odinstalowuje pakiet źródłowy lub szablonowy na `PATH` lub `NUGET_ID` udostępniony.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="dbc2f-400">Aby odinstalować szablon przy użyciu `PATH`, musisz w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="dbc2f-401">Na przykład *C:/Users/\<USER >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="dbc2f-402">Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="dbc2f-403">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="dbc2f-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="dbc2f-404">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="dbc2f-405">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="dbc2f-406">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-406">Prints out help for the command.</span></span> <span data-ttu-id="dbc2f-407">Może być wywoływana dla samego polecenia `dotnet new` lub dla dowolnego szablonu, takiego jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="dbc2f-408">Instaluje pakiet źródłowy lub szablon z podanej `PATH` lub `NUGET_ID`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="dbc2f-409">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="dbc2f-410">Domyślnie `dotnet new` przekazuje \* wersji, co reprezentuje ostatnią stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="dbc2f-411">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="dbc2f-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="dbc2f-412">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="dbc2f-413">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="dbc2f-414">Jeśli zostanie wywołana dla polecenia `dotnet new`, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="dbc2f-415">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="dbc2f-416">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-416">The language of the template to create.</span></span> <span data-ttu-id="dbc2f-417">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="dbc2f-418">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="dbc2f-419">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="dbc2f-420">W takich przypadkach należy ująć wartość parametru language, taką jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="dbc2f-421">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-421">The name for the created output.</span></span> <span data-ttu-id="dbc2f-422">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dbc2f-423">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-423">Location to place the generated output.</span></span> <span data-ttu-id="dbc2f-424">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="dbc2f-425">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-425">Filters templates based on available types.</span></span> <span data-ttu-id="dbc2f-426">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="dbc2f-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="dbc2f-427">Odinstalowuje pakiet źródłowy lub szablonowy na `PATH` lub `NUGET_ID` udostępniony.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="dbc2f-428">Aby odinstalować szablon przy użyciu `PATH`źródłowego, należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="dbc2f-429">Na przykład *C:/Users/\<USER >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="dbc2f-430">Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="dbc2f-431">Jeśli nie możesz określić argumentu `PATH` lub `NUGET_ID` wymaganego do odinstalowania szablonu, uruchomienie `dotnet new --uninstall` bez argumentu spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argumentu wymaganego do ich odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dbc2f-432">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="dbc2f-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="dbc2f-433">Wyświetla wszystkie szablony dla określonego typu projektu, gdy działa w kontekście polecenia `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="dbc2f-434">W przypadku uruchomienia w kontekście określonego szablonu, takiego jak `dotnet new web -all`, `-all` jest interpretowana jako flaga tworzenia siły.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="dbc2f-435">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="dbc2f-436">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-436">Prints out help for the command.</span></span> <span data-ttu-id="dbc2f-437">Może być wywoływana dla samego polecenia `dotnet new` lub dla dowolnego szablonu, takiego jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="dbc2f-438">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="dbc2f-439">Jeśli zostanie wywołana dla polecenia `dotnet new`, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="dbc2f-440">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="dbc2f-441">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-441">The language of the template to create.</span></span> <span data-ttu-id="dbc2f-442">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="dbc2f-443">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="dbc2f-444">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="dbc2f-445">W takich przypadkach należy ująć wartość parametru language, taką jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="dbc2f-446">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-446">The name for the created output.</span></span> <span data-ttu-id="dbc2f-447">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dbc2f-448">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-448">Location to place the generated output.</span></span> <span data-ttu-id="dbc2f-449">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="dbc2f-450">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="dbc2f-450">Template options</span></span>

<span data-ttu-id="dbc2f-451">Każdy szablon projektu może mieć dodatkowe opcje dostępne.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-451">Each project template may have additional options available.</span></span> <span data-ttu-id="dbc2f-452">Szablony podstawowe mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="dbc2f-453">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="dbc2f-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="dbc2f-454">**konsoli**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-454">**console**</span></span>

<span data-ttu-id="dbc2f-455">`--langVersion <VERSION_NUMBER>` — ustawia właściwość `LangVersion` w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="dbc2f-456">Na przykład użyj `--langVersion 7.3`, aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="dbc2f-457">Nieobsługiwane w F#programie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-457">Not supported for F#.</span></span>

<span data-ttu-id="dbc2f-458">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-459">**kątowy, reagowanie, reactredux**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="dbc2f-460">`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="dbc2f-461">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-462">`--no-https` — projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="dbc2f-463">Ta opcja ma zastosowanie tylko wtedy, gdy nie są używane `IndividualAuth` ani `OrganizationalAuth`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="dbc2f-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-464">**razorclasslib**</span></span>

<span data-ttu-id="dbc2f-465">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-466">**określono**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-466">**classlib**</span></span>

<span data-ttu-id="dbc2f-467">`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dbc2f-468">Wartości: `netcoreapp2.2` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="dbc2f-469">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="dbc2f-470">`--langVersion <VERSION_NUMBER>` — ustawia właściwość `LangVersion` w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="dbc2f-471">Na przykład użyj `--langVersion 7.3`, aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="dbc2f-472">Nieobsługiwane w F#programie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-472">Not supported for F#.</span></span>

<span data-ttu-id="dbc2f-473">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-474">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-474">**mstest, xunit**</span></span>

<span data-ttu-id="dbc2f-475">`-p|--enable-pack` — włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="dbc2f-476">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-477">**NUnit**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-477">**nunit**</span></span>

<span data-ttu-id="dbc2f-478">`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dbc2f-479">Wartość domyślna to `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="dbc2f-480">`-p|--enable-pack` — włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="dbc2f-481">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-482">**stronic**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-482">**page**</span></span>

<span data-ttu-id="dbc2f-483">Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>` dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="dbc2f-484">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="dbc2f-485">`-np|--no-pagemodel` — tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="dbc2f-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-486">**viewimports**</span></span>

<span data-ttu-id="dbc2f-487">Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>` dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="dbc2f-488">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="dbc2f-489">**witrynę**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-489">**web**</span></span>

<span data-ttu-id="dbc2f-490">`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="dbc2f-491">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-492">`--no-https` — projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="dbc2f-493">Ta opcja ma zastosowanie tylko wtedy, gdy nie są używane `IndividualAuth` ani `OrganizationalAuth`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="dbc2f-494">**MVC, webapp**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-494">**mvc, webapp**</span></span>

<span data-ttu-id="dbc2f-495">`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="dbc2f-496">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-496">The possible values are:</span></span>

- <span data-ttu-id="dbc2f-497">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="dbc2f-498">Uwierzytelnianie indywidualne `Individual`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="dbc2f-499">`IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="dbc2f-500">`SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="dbc2f-501">`MultiOrg` — uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="dbc2f-502">`Windows` — uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="dbc2f-503">`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="dbc2f-504">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-505">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="dbc2f-506">`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="dbc2f-507">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-508">`-rp|--reset-password-policy-id <ID>` — identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="dbc2f-509">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-510">`-ep|--edit-profile-policy-id <ID>` — Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="dbc2f-511">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-512">`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="dbc2f-513">Użyj z uwierzytelnianiem `SingleOrg` lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="dbc2f-514">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="dbc2f-515">`--client-id <ID>` — identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="dbc2f-516">Użyj z uwierzytelnianiem `IndividualB2C`, `SingleOrg`lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="dbc2f-517">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="dbc2f-518">`--domain <DOMAIN>` — domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="dbc2f-519">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-520">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="dbc2f-521">`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="dbc2f-522">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-523">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="dbc2f-524">`--callback-path <PATH>` — Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="dbc2f-525">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-526">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="dbc2f-527">`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="dbc2f-528">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="dbc2f-529">`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="dbc2f-530">`--no-https` — projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="dbc2f-531">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="dbc2f-532">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="dbc2f-533">`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dbc2f-534">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-535">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-536">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-536">**webapi**</span></span>

<span data-ttu-id="dbc2f-537">`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="dbc2f-538">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-538">The possible values are:</span></span>

- <span data-ttu-id="dbc2f-539">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="dbc2f-540">`IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="dbc2f-541">`SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="dbc2f-542">`Windows` — uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="dbc2f-543">`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="dbc2f-544">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-545">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="dbc2f-546">`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="dbc2f-547">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-548">`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="dbc2f-549">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-550">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="dbc2f-551">`--client-id <ID>` — identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="dbc2f-552">Użyj z uwierzytelnianiem `IndividualB2C` lub `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-553">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="dbc2f-554">`--domain <DOMAIN>` — domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="dbc2f-555">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-556">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="dbc2f-557">`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="dbc2f-558">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-559">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="dbc2f-560">`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="dbc2f-561">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="dbc2f-562">`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="dbc2f-563">`--no-https` — projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="dbc2f-564">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="dbc2f-565">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="dbc2f-566">`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dbc2f-567">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-568">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-569">**globaljson**</span></span>

<span data-ttu-id="dbc2f-570">`--sdk-version <VERSION_NUMBER>` — określa wersję zestaw .NET Core SDK do użycia w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="dbc2f-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="dbc2f-571">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="dbc2f-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="dbc2f-572">**konsole, kątowe, reagowanie, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="dbc2f-573">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-574">**określono**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-574">**classlib**</span></span>

<span data-ttu-id="dbc2f-575">`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dbc2f-576">Wartości: `netcoreapp2.1` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="dbc2f-577">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="dbc2f-578">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-579">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-579">**mstest, xunit**</span></span>

<span data-ttu-id="dbc2f-580">`-p|--enable-pack` — włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="dbc2f-581">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-582">**globaljson**</span></span>

<span data-ttu-id="dbc2f-583">`--sdk-version <VERSION_NUMBER>` — określa wersję zestaw .NET Core SDK do użycia w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="dbc2f-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="dbc2f-584">**witrynę**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-584">**web**</span></span>

<span data-ttu-id="dbc2f-585">`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="dbc2f-586">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-587">`--no-https` — projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="dbc2f-588">Ta opcja ma zastosowanie tylko wtedy, gdy nie są używane `IndividualAuth` ani `OrganizationalAuth`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="dbc2f-589">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-589">**webapi**</span></span>

<span data-ttu-id="dbc2f-590">`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="dbc2f-591">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-591">The possible values are:</span></span>

- <span data-ttu-id="dbc2f-592">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="dbc2f-593">`IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="dbc2f-594">`SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="dbc2f-595">`Windows` — uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="dbc2f-596">`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="dbc2f-597">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-598">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="dbc2f-599">`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="dbc2f-600">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-601">`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="dbc2f-602">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-603">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="dbc2f-604">`--client-id <ID>` — identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="dbc2f-605">Użyj z uwierzytelnianiem `IndividualB2C` lub `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-606">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="dbc2f-607">`--domain <DOMAIN>` — domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="dbc2f-608">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-609">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="dbc2f-610">`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="dbc2f-611">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-612">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="dbc2f-613">`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="dbc2f-614">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="dbc2f-615">`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="dbc2f-616">`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dbc2f-617">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-618">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-619">`--no-https` — projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="dbc2f-620">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="dbc2f-621">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="dbc2f-622">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-622">**mvc, razor**</span></span>

<span data-ttu-id="dbc2f-623">`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="dbc2f-624">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-624">The possible values are:</span></span>

- <span data-ttu-id="dbc2f-625">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="dbc2f-626">Uwierzytelnianie indywidualne `Individual`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="dbc2f-627">`IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="dbc2f-628">`SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="dbc2f-629">`MultiOrg` — uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="dbc2f-630">`Windows` — uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="dbc2f-631">`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="dbc2f-632">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-633">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="dbc2f-634">`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="dbc2f-635">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-636">`-rp|--reset-password-policy-id <ID>` — identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="dbc2f-637">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-638">`-ep|--edit-profile-policy-id <ID>` — Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="dbc2f-639">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-640">`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="dbc2f-641">Użyj z uwierzytelnianiem `SingleOrg` lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="dbc2f-642">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="dbc2f-643">`--client-id <ID>` — identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="dbc2f-644">Użyj z uwierzytelnianiem `IndividualB2C`, `SingleOrg`lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="dbc2f-645">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="dbc2f-646">`--domain <DOMAIN>` — domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="dbc2f-647">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-648">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="dbc2f-649">`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="dbc2f-650">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-651">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="dbc2f-652">`--callback-path <PATH>` — Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="dbc2f-653">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-654">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="dbc2f-655">`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="dbc2f-656">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="dbc2f-657">`--exclude-launch-settings` — Wyklucz plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="dbc2f-658">`--use-browserlink` — zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="dbc2f-659">`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dbc2f-660">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-661">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-662">`--no-https` — projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="dbc2f-663">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="dbc2f-664">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="dbc2f-665">**stronic**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-665">**page**</span></span>

<span data-ttu-id="dbc2f-666">Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>` dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="dbc2f-667">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="dbc2f-668">`-np|--no-pagemodel` — tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="dbc2f-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-669">**viewimports**</span></span>

<span data-ttu-id="dbc2f-670">Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>` dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="dbc2f-671">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="dbc2f-672">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="dbc2f-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="dbc2f-673">**konsole, kątowe, reagowanie, reactredux**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="dbc2f-674">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-675">**określono**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-675">**classlib**</span></span>

<span data-ttu-id="dbc2f-676">`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dbc2f-677">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="dbc2f-678">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="dbc2f-679">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-680">**MSTest, xUnit**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-680">**mstest, xunit**</span></span>

<span data-ttu-id="dbc2f-681">`-p|--enable-pack` — włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="dbc2f-682">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-683">**globaljson**</span></span>

<span data-ttu-id="dbc2f-684">`--sdk-version <VERSION_NUMBER>` — określa wersję zestaw .NET Core SDK do użycia w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="dbc2f-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="dbc2f-685">**witrynę**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-685">**web**</span></span>

<span data-ttu-id="dbc2f-686">`--use-launch-settings` — zawiera plik *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="dbc2f-687">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-688">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-688">**webapi**</span></span>

<span data-ttu-id="dbc2f-689">`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="dbc2f-690">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-690">The possible values are:</span></span>

- <span data-ttu-id="dbc2f-691">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="dbc2f-692">`IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="dbc2f-693">`SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="dbc2f-694">`Windows` — uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="dbc2f-695">`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="dbc2f-696">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-697">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="dbc2f-698">`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="dbc2f-699">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-700">`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="dbc2f-701">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-702">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="dbc2f-703">`--client-id <ID>` — identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="dbc2f-704">Użyj z uwierzytelnianiem `IndividualB2C` lub `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-705">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="dbc2f-706">`--domain <DOMAIN>` — domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="dbc2f-707">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-708">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="dbc2f-709">`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="dbc2f-710">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-711">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="dbc2f-712">`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="dbc2f-713">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="dbc2f-714">`--use-launch-settings` — zawiera plik *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="dbc2f-715">`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dbc2f-716">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-717">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-718">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-718">**mvc, razor**</span></span>

<span data-ttu-id="dbc2f-719">`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="dbc2f-720">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-720">The possible values are:</span></span>

- <span data-ttu-id="dbc2f-721">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="dbc2f-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="dbc2f-722">Uwierzytelnianie indywidualne `Individual`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="dbc2f-723">`IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="dbc2f-724">`SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="dbc2f-725">`MultiOrg` — uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="dbc2f-726">`Windows` — uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="dbc2f-727">`--aad-b2c-instance <INSTANCE>` — wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="dbc2f-728">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-729">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="dbc2f-730">`-ssp|--susi-policy-id <ID>` — identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="dbc2f-731">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-732">`-rp|--reset-password-policy-id <ID>` — identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="dbc2f-733">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-734">`-ep|--edit-profile-policy-id <ID>` — Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="dbc2f-735">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-736">`--aad-instance <INSTANCE>` — wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="dbc2f-737">Użyj z uwierzytelnianiem `SingleOrg` lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="dbc2f-738">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="dbc2f-739">`--client-id <ID>` — identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="dbc2f-740">Użyj z uwierzytelnianiem `IndividualB2C`, `SingleOrg`lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="dbc2f-741">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="dbc2f-742">`--domain <DOMAIN>` — domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="dbc2f-743">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-744">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="dbc2f-745">`--tenant-id <ID>` — identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="dbc2f-746">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="dbc2f-747">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="dbc2f-748">`--callback-path <PATH>` — Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="dbc2f-749">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="dbc2f-750">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="dbc2f-751">`-r|--org-read-access` — zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="dbc2f-752">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="dbc2f-753">`--use-launch-settings` — zawiera plik *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="dbc2f-754">`--use-browserlink` — zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="dbc2f-755">`-uld|--use-local-db`-Określ LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="dbc2f-756">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="dbc2f-757">`--no-restore` — nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="dbc2f-758">**stronic**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-758">**page**</span></span>

<span data-ttu-id="dbc2f-759">Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>`dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="dbc2f-760">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="dbc2f-761">`-np|--no-pagemodel` — tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="dbc2f-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-762">**viewimports**</span></span>

<span data-ttu-id="dbc2f-763">Przestrzeń nazw `-na|--namespace <NAMESPACE_NAME>`dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="dbc2f-764">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dbc2f-765">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="dbc2f-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="dbc2f-766">**konsole, xUnit, MSTest, Web, WebApi**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="dbc2f-767">`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dbc2f-768">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="dbc2f-769">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="dbc2f-770">**określono**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-770">**classlib**</span></span>

<span data-ttu-id="dbc2f-771">`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dbc2f-772">Wartości: `netcoreapp1.0`, `netcoreapp1.1`lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="dbc2f-773">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="dbc2f-774">**Standard**</span><span class="sxs-lookup"><span data-stu-id="dbc2f-774">**mvc**</span></span>

<span data-ttu-id="dbc2f-775">`-f|--framework <FRAMEWORK>` — określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="dbc2f-776">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="dbc2f-777">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="dbc2f-778">`-au|--auth <AUTHENTICATION_TYPE>` — typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="dbc2f-779">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="dbc2f-780">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-780">The default value is `None`.</span></span>

<span data-ttu-id="dbc2f-781">`-uld|--use-local-db` — określa, czy należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="dbc2f-782">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-782">Values: `true` or `false`.</span></span> <span data-ttu-id="dbc2f-783">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="dbc2f-784">Przykłady</span><span class="sxs-lookup"><span data-stu-id="dbc2f-784">Examples</span></span>

<span data-ttu-id="dbc2f-785">Utwórz projekt C# aplikacji konsolowej, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="dbc2f-786">Utwórz projekt F# aplikacji konsolowej w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="dbc2f-787">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku wersji zestaw .NET Core SDK 2,0 lub nowszej):</span><span class="sxs-lookup"><span data-stu-id="dbc2f-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="dbc2f-788">Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="dbc2f-789">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="dbc2f-790">Wyświetl listę wszystkich szablonów dostępnych dla MVC:</span><span class="sxs-lookup"><span data-stu-id="dbc2f-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="dbc2f-791">Wyświetl listę wszystkich szablonów pasujących *do* podciągu.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="dbc2f-792">Nie znaleziono dokładnego dopasowania, więc Dopasowywanie podciągów działa w odniesieniu do kolumn krótkich nazw i nazw.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="dbc2f-793">Podjęto próbę wywołania szablonu zgodnego z parametrem *ng*.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="dbc2f-794">Jeśli nie można ustalić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są dopasowań częściowych.</span><span class="sxs-lookup"><span data-stu-id="dbc2f-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="dbc2f-795">Zainstaluj wersję 2,0 szablonów aplikacji jednostronicowych dla ASP.NET Core (opcja polecenia dostępna tylko dla zestaw .NET Core SDK 1,1 i nowszych wersji):</span><span class="sxs-lookup"><span data-stu-id="dbc2f-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="dbc2f-796">Utwórz plik *Global. JSON* w bieżącym katalogu, ustawiając wersję zestawu SDK na 2.0.0 (dostępne tylko w zestaw .NET Core SDK 2,0 lub nowszych wersjach):</span><span class="sxs-lookup"><span data-stu-id="dbc2f-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="dbc2f-797">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbc2f-797">See also</span></span>

- [<span data-ttu-id="dbc2f-798">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="dbc2f-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="dbc2f-799">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="dbc2f-799">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="dbc2f-800">dotnet/dotnet-Template-przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="dbc2f-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="dbc2f-801">Dostępne szablony dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="dbc2f-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
