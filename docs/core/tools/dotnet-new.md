---
title: polecenie dotnet New
description: Polecenie dotnet New umożliwia tworzenie nowych projektów platformy .NET Core na podstawie określonego szablonu.
ms.date: 05/06/2019
ms.openlocfilehash: 57b198d13984fb4585e1df6303afe481e7e0552d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969736"
---
# <a name="dotnet-new"></a><span data-ttu-id="5bdba-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5bdba-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5bdba-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5bdba-104">Name</span></span>

<span data-ttu-id="5bdba-105">`dotnet new`-Tworzy nowy projekt, plik konfiguracji lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5bdba-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5bdba-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5bdba-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5bdba-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5bdba-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5bdba-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5bdba-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5bdba-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5bdba-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5bdba-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="5bdba-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5bdba-111">Description</span></span>

<span data-ttu-id="5bdba-112">`dotnet new` Polecenie zapewnia wygodny sposób inicjowania prawidłowego projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bdba-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="5bdba-113">Polecenie wywołuje [aparat szablonu](https://github.com/dotnet/templating) , aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="5bdba-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="5bdba-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5bdba-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="5bdba-115">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="5bdba-116">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="5bdba-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="5bdba-117">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="5bdba-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="5bdba-118">Jeśli wartość nie jest dokładnym dopasowaniem do tekstu w kolumnie **templates** lub **short name** , do tych dwóch kolumn jest wykonywane dopasowanie podciągów. `TEMPLATE`</span><span class="sxs-lookup"><span data-stu-id="5bdba-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5bdba-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5bdba-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5bdba-120">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-120">The command contains a default list of templates.</span></span> <span data-ttu-id="5bdba-121">Użyj `dotnet new -l` , aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5bdba-122">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="5bdba-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="5bdba-123">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5bdba-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="5bdba-124">Szablony</span><span class="sxs-lookup"><span data-stu-id="5bdba-124">Templates</span></span>                                    | <span data-ttu-id="5bdba-125">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="5bdba-125">Short Name</span></span>        | <span data-ttu-id="5bdba-126">Język</span><span class="sxs-lookup"><span data-stu-id="5bdba-126">Language</span></span>     | <span data-ttu-id="5bdba-127">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="5bdba-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="5bdba-128">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="5bdba-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="5bdba-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-129">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-130">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="5bdba-130">Common/Console</span></span>                        |
| <span data-ttu-id="5bdba-131">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="5bdba-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="5bdba-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-132">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-133">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="5bdba-133">Common/Library</span></span>                        |
| <span data-ttu-id="5bdba-134">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="5bdba-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="5bdba-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-135">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="5bdba-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="5bdba-137">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="5bdba-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="5bdba-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-138">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="5bdba-140">Element testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="5bdba-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="5bdba-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-141">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="5bdba-143">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="5bdba-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-144">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="5bdba-146">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="5bdba-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="5bdba-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-147">[C#]</span></span>         | <span data-ttu-id="5bdba-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bdba-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5bdba-149">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="5bdba-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-150">[C#]</span></span>         | <span data-ttu-id="5bdba-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bdba-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5bdba-152">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="5bdba-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-153">[C#]</span></span>         | <span data-ttu-id="5bdba-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bdba-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5bdba-155">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="5bdba-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="5bdba-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-156">[C#], F#</span></span>     | <span data-ttu-id="5bdba-157">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="5bdba-157">Web/Empty</span></span>                             |
| <span data-ttu-id="5bdba-158">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="5bdba-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="5bdba-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-159">[C#], F#</span></span>     | <span data-ttu-id="5bdba-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-160">Web/MVC</span></span>                               |
| <span data-ttu-id="5bdba-161">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bdba-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="5bdba-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="5bdba-162">`webapp`, `razor`</span></span> | <span data-ttu-id="5bdba-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-163">[C#]</span></span>         | <span data-ttu-id="5bdba-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="5bdba-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="5bdba-165">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="5bdba-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="5bdba-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-166">[C#]</span></span>         | <span data-ttu-id="5bdba-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5bdba-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5bdba-168">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="5bdba-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="5bdba-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-169">[C#]</span></span>         | <span data-ttu-id="5bdba-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5bdba-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5bdba-171">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="5bdba-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="5bdba-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-172">[C#]</span></span>         | <span data-ttu-id="5bdba-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5bdba-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5bdba-174">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="5bdba-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="5bdba-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-175">[C#]</span></span>         | <span data-ttu-id="5bdba-176">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="5bdba-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="5bdba-177">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bdba-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="5bdba-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-178">[C#], F#</span></span>     | <span data-ttu-id="5bdba-179">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="5bdba-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="5bdba-180">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="5bdba-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="5bdba-181">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-181">Config</span></span>                                |
| <span data-ttu-id="5bdba-182">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="5bdba-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="5bdba-183">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-183">Config</span></span>                                |
| <span data-ttu-id="5bdba-184">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="5bdba-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="5bdba-185">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-185">Config</span></span>                                |
| <span data-ttu-id="5bdba-186">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5bdba-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="5bdba-187">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="5bdba-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5bdba-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5bdba-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5bdba-189">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-189">The command contains a default list of templates.</span></span> <span data-ttu-id="5bdba-190">Użyj `dotnet new -l` , aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5bdba-191">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="5bdba-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="5bdba-192">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5bdba-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="5bdba-193">Szablony</span><span class="sxs-lookup"><span data-stu-id="5bdba-193">Templates</span></span>                                    | <span data-ttu-id="5bdba-194">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="5bdba-194">Short Name</span></span>      | <span data-ttu-id="5bdba-195">Język</span><span class="sxs-lookup"><span data-stu-id="5bdba-195">Language</span></span>     | <span data-ttu-id="5bdba-196">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="5bdba-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="5bdba-197">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="5bdba-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="5bdba-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-198">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-199">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="5bdba-199">Common/Console</span></span>                        |
| <span data-ttu-id="5bdba-200">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="5bdba-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="5bdba-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-201">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-202">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="5bdba-202">Common/Library</span></span>                        |
| <span data-ttu-id="5bdba-203">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="5bdba-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="5bdba-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-204">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="5bdba-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="5bdba-206">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="5bdba-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-207">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="5bdba-209">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="5bdba-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="5bdba-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-210">[C#]</span></span>         | <span data-ttu-id="5bdba-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bdba-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5bdba-212">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="5bdba-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-213">[C#]</span></span>         | <span data-ttu-id="5bdba-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bdba-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5bdba-215">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="5bdba-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-216">[C#]</span></span>         | <span data-ttu-id="5bdba-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bdba-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="5bdba-218">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="5bdba-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="5bdba-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-219">[C#], F#</span></span>     | <span data-ttu-id="5bdba-220">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="5bdba-220">Web/Empty</span></span>                             |
| <span data-ttu-id="5bdba-221">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="5bdba-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="5bdba-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-222">[C#], F#</span></span>     | <span data-ttu-id="5bdba-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-223">Web/MVC</span></span>                               |
| <span data-ttu-id="5bdba-224">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bdba-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="5bdba-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-225">[C#]</span></span>         | <span data-ttu-id="5bdba-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="5bdba-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="5bdba-227">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="5bdba-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="5bdba-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-228">[C#]</span></span>         | <span data-ttu-id="5bdba-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5bdba-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5bdba-230">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="5bdba-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="5bdba-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-231">[C#]</span></span>         | <span data-ttu-id="5bdba-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5bdba-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="5bdba-233">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="5bdba-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="5bdba-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-234">[C#]</span></span>         | <span data-ttu-id="5bdba-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5bdba-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="5bdba-236">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="5bdba-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="5bdba-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-237">[C#]</span></span>         | <span data-ttu-id="5bdba-238">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="5bdba-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="5bdba-239">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bdba-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="5bdba-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-240">[C#], F#</span></span>     | <span data-ttu-id="5bdba-241">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="5bdba-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="5bdba-242">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="5bdba-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="5bdba-243">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-243">Config</span></span>                                |
| <span data-ttu-id="5bdba-244">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="5bdba-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="5bdba-245">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-245">Config</span></span>                                |
| <span data-ttu-id="5bdba-246">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="5bdba-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="5bdba-247">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-247">Config</span></span>                                |
| <span data-ttu-id="5bdba-248">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5bdba-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="5bdba-249">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="5bdba-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5bdba-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5bdba-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="5bdba-251">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-251">The command contains a default list of templates.</span></span> <span data-ttu-id="5bdba-252">Użyj `dotnet new -l` , aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5bdba-253">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="5bdba-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="5bdba-254">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5bdba-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="5bdba-255">Szablony</span><span class="sxs-lookup"><span data-stu-id="5bdba-255">Templates</span></span>                                    | <span data-ttu-id="5bdba-256">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="5bdba-256">Short Name</span></span>    | <span data-ttu-id="5bdba-257">Język</span><span class="sxs-lookup"><span data-stu-id="5bdba-257">Language</span></span>     | <span data-ttu-id="5bdba-258">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="5bdba-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="5bdba-259">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="5bdba-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="5bdba-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-260">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-261">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="5bdba-261">Common/Console</span></span>      |
| <span data-ttu-id="5bdba-262">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="5bdba-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="5bdba-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-263">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-264">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="5bdba-264">Common/Library</span></span>      |
| <span data-ttu-id="5bdba-265">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="5bdba-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="5bdba-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-266">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="5bdba-267">Test/MSTest</span></span>         |
| <span data-ttu-id="5bdba-268">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="5bdba-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5bdba-269">[C#], F#, VB</span></span> | <span data-ttu-id="5bdba-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-270">Test/xUnit</span></span>          |
| <span data-ttu-id="5bdba-271">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="5bdba-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="5bdba-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-272">[C#], F#</span></span>     | <span data-ttu-id="5bdba-273">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="5bdba-273">Web/Empty</span></span>           |
| <span data-ttu-id="5bdba-274">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="5bdba-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="5bdba-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-275">[C#], F#</span></span>     | <span data-ttu-id="5bdba-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-276">Web/MVC</span></span>             |
| <span data-ttu-id="5bdba-277">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bdba-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="5bdba-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-278">[C#]</span></span>         | <span data-ttu-id="5bdba-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="5bdba-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="5bdba-280">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="5bdba-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="5bdba-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-281">[C#]</span></span>         | <span data-ttu-id="5bdba-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5bdba-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="5bdba-283">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="5bdba-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="5bdba-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-284">[C#]</span></span>         | <span data-ttu-id="5bdba-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5bdba-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="5bdba-286">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="5bdba-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="5bdba-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-287">[C#]</span></span>         | <span data-ttu-id="5bdba-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="5bdba-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="5bdba-289">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bdba-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="5bdba-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-290">[C#], F#</span></span>     | <span data-ttu-id="5bdba-291">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="5bdba-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="5bdba-292">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="5bdba-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="5bdba-293">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-293">Config</span></span>              |
| <span data-ttu-id="5bdba-294">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="5bdba-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="5bdba-295">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-295">Config</span></span>              |
| <span data-ttu-id="5bdba-296">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="5bdba-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="5bdba-297">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-297">Config</span></span>              |
| <span data-ttu-id="5bdba-298">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5bdba-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="5bdba-299">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="5bdba-299">Solution</span></span>            |
| <span data-ttu-id="5bdba-300">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="5bdba-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="5bdba-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bdba-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="5bdba-302">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="5bdba-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bdba-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="5bdba-304">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="5bdba-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bdba-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5bdba-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5bdba-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="5bdba-307">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-307">The command contains a default list of templates.</span></span> <span data-ttu-id="5bdba-308">Użyj `dotnet new -all` , aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="5bdba-309">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="5bdba-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="5bdba-310">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5bdba-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="5bdba-311">Szablony</span><span class="sxs-lookup"><span data-stu-id="5bdba-311">Templates</span></span>            | <span data-ttu-id="5bdba-312">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="5bdba-312">Short Name</span></span>    | <span data-ttu-id="5bdba-313">Język</span><span class="sxs-lookup"><span data-stu-id="5bdba-313">Language</span></span> | <span data-ttu-id="5bdba-314">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="5bdba-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="5bdba-315">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="5bdba-315">Console Application</span></span>  | `console`     | <span data-ttu-id="5bdba-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-316">[C#], F#</span></span> | <span data-ttu-id="5bdba-317">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="5bdba-317">Common/Console</span></span> |
| <span data-ttu-id="5bdba-318">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="5bdba-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="5bdba-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-319">[C#], F#</span></span> | <span data-ttu-id="5bdba-320">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="5bdba-320">Common/Library</span></span> |
| <span data-ttu-id="5bdba-321">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="5bdba-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="5bdba-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-322">[C#], F#</span></span> | <span data-ttu-id="5bdba-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="5bdba-323">Test/MSTest</span></span>    |
| <span data-ttu-id="5bdba-324">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="5bdba-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-325">[C#], F#</span></span> | <span data-ttu-id="5bdba-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="5bdba-326">Test/xUnit</span></span>     |
| <span data-ttu-id="5bdba-327">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="5bdba-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="5bdba-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-328">[C#]</span></span>     | <span data-ttu-id="5bdba-329">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="5bdba-329">Web/Empty</span></span>      |
| <span data-ttu-id="5bdba-330">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bdba-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="5bdba-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5bdba-331">[C#], F#</span></span> | <span data-ttu-id="5bdba-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="5bdba-332">Web/MVC</span></span>        |
| <span data-ttu-id="5bdba-333">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bdba-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="5bdba-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="5bdba-334">[C#]</span></span>     | <span data-ttu-id="5bdba-335">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="5bdba-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="5bdba-336">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="5bdba-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="5bdba-337">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-337">Config</span></span>         |
| <span data-ttu-id="5bdba-338">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="5bdba-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="5bdba-339">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5bdba-339">Config</span></span>         |
| <span data-ttu-id="5bdba-340">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5bdba-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="5bdba-341">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="5bdba-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="5bdba-342">Opcje</span><span class="sxs-lookup"><span data-stu-id="5bdba-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5bdba-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5bdba-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="5bdba-344">Wyświetla podsumowanie tego, co się stanie w przypadku uruchomienia danego polecenia, jeśli mogłoby to spowodować utworzenie szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="5bdba-345">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="5bdba-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5bdba-346">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="5bdba-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5bdba-347">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-347">Prints out help for the command.</span></span> <span data-ttu-id="5bdba-348">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu, takiego jak. `dotnet new mvc --help`</span><span class="sxs-lookup"><span data-stu-id="5bdba-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="5bdba-349">Instaluje pakiet źródłowy lub szablon z `PATH` lub `NUGET_ID` udostępnione.</span><span class="sxs-lookup"><span data-stu-id="5bdba-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5bdba-350">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5bdba-351">Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="5bdba-352">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="5bdba-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="5bdba-353">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5bdba-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="5bdba-354">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5bdba-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="5bdba-355">Jeśli zostanie wywołana dla `dotnet new` polecenia, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5bdba-356">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="5bdba-357">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-357">The language of the template to create.</span></span> <span data-ttu-id="5bdba-358">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="5bdba-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5bdba-359">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="5bdba-360">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="5bdba-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="5bdba-361">W takich przypadkach należy ująć wartość parametru języka, np `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5bdba-362">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5bdba-362">The name for the created output.</span></span> <span data-ttu-id="5bdba-363">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="5bdba-364">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="5bdba-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5bdba-365">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5bdba-365">Location to place the generated output.</span></span> <span data-ttu-id="5bdba-366">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="5bdba-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="5bdba-367">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="5bdba-367">Filters templates based on available types.</span></span> <span data-ttu-id="5bdba-368">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="5bdba-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="5bdba-369">Odinstalowuje pakiet źródłowy lub szablonowy w `PATH` udostępnionym lub. `NUGET_ID`</span><span class="sxs-lookup"><span data-stu-id="5bdba-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5bdba-370">Podczas wykluczania `<PATH|NUGET_ID>` wartości są wyświetlane wszystkie aktualnie zainstalowane pakiety szablonów i powiązane z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="5bdba-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="5bdba-371">Aby odinstalować szablon przy użyciu programu `PATH`, należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="5bdba-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5bdba-372">Na przykład *C:/Users/\<user >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="5bdba-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="5bdba-373">Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5bdba-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5bdba-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="5bdba-375">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="5bdba-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5bdba-376">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="5bdba-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5bdba-377">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-377">Prints out help for the command.</span></span> <span data-ttu-id="5bdba-378">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu, takiego jak. `dotnet new mvc --help`</span><span class="sxs-lookup"><span data-stu-id="5bdba-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="5bdba-379">Instaluje pakiet źródłowy lub szablon z `PATH` lub `NUGET_ID` udostępnione.</span><span class="sxs-lookup"><span data-stu-id="5bdba-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5bdba-380">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5bdba-381">Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="5bdba-382">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="5bdba-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="5bdba-383">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5bdba-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="5bdba-384">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5bdba-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="5bdba-385">Jeśli zostanie wywołana dla `dotnet new` polecenia, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5bdba-386">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="5bdba-387">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-387">The language of the template to create.</span></span> <span data-ttu-id="5bdba-388">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="5bdba-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5bdba-389">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="5bdba-390">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="5bdba-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="5bdba-391">W takich przypadkach należy ująć wartość parametru języka, np `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5bdba-392">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5bdba-392">The name for the created output.</span></span> <span data-ttu-id="5bdba-393">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="5bdba-394">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="5bdba-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5bdba-395">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5bdba-395">Location to place the generated output.</span></span> <span data-ttu-id="5bdba-396">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="5bdba-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="5bdba-397">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="5bdba-397">Filters templates based on available types.</span></span> <span data-ttu-id="5bdba-398">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="5bdba-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="5bdba-399">Odinstalowuje pakiet źródłowy lub szablonowy w `PATH` udostępnionym lub. `NUGET_ID`</span><span class="sxs-lookup"><span data-stu-id="5bdba-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="5bdba-400">Aby odinstalować szablon przy użyciu programu `PATH`, należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="5bdba-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5bdba-401">Na przykład *C:/Users/\<user >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="5bdba-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="5bdba-402">Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5bdba-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5bdba-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="5bdba-404">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="5bdba-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5bdba-405">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="5bdba-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5bdba-406">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-406">Prints out help for the command.</span></span> <span data-ttu-id="5bdba-407">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu, takiego jak. `dotnet new mvc --help`</span><span class="sxs-lookup"><span data-stu-id="5bdba-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="5bdba-408">Instaluje pakiet źródłowy lub szablon z `PATH` lub `NUGET_ID` udostępnione.</span><span class="sxs-lookup"><span data-stu-id="5bdba-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5bdba-409">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5bdba-410">Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="5bdba-411">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="5bdba-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="5bdba-412">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5bdba-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="5bdba-413">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5bdba-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="5bdba-414">Jeśli zostanie wywołana dla `dotnet new` polecenia, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5bdba-415">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="5bdba-416">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-416">The language of the template to create.</span></span> <span data-ttu-id="5bdba-417">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="5bdba-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5bdba-418">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="5bdba-419">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="5bdba-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="5bdba-420">W takich przypadkach należy ująć wartość parametru języka, np `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5bdba-421">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5bdba-421">The name for the created output.</span></span> <span data-ttu-id="5bdba-422">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5bdba-423">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5bdba-423">Location to place the generated output.</span></span> <span data-ttu-id="5bdba-424">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="5bdba-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="5bdba-425">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="5bdba-425">Filters templates based on available types.</span></span> <span data-ttu-id="5bdba-426">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="5bdba-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="5bdba-427">Odinstalowuje pakiet źródłowy lub szablonowy w `PATH` udostępnionym lub. `NUGET_ID`</span><span class="sxs-lookup"><span data-stu-id="5bdba-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="5bdba-428">Aby odinstalować szablon przy użyciu źródła `PATH`, należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="5bdba-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5bdba-429">Na przykład *C:/Users/\<user >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="5bdba-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="5bdba-430">Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="5bdba-431">Jeśli nie możesz określić `PATH` argumentu lub `NUGET_ID` wymaganego do odinstalowania szablonu, uruchomienie `dotnet new --uninstall` bez argumentu spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argumentu wymaganego do ich odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5bdba-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5bdba-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="5bdba-433">Pokazuje wszystkie szablony dla określonego typu projektu, gdy działa w kontekście `dotnet new` samego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="5bdba-434">Gdy jest uruchamiany w kontekście określonego szablonu, na przykład `dotnet new web -all`, `-all` jest interpretowany jako flaga tworzenia siły.</span><span class="sxs-lookup"><span data-stu-id="5bdba-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="5bdba-435">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="5bdba-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5bdba-436">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-436">Prints out help for the command.</span></span> <span data-ttu-id="5bdba-437">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu, takiego jak. `dotnet new mvc --help`</span><span class="sxs-lookup"><span data-stu-id="5bdba-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="5bdba-438">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5bdba-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="5bdba-439">Jeśli zostanie wywołana dla `dotnet new` polecenia, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5bdba-440">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="5bdba-441">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-441">The language of the template to create.</span></span> <span data-ttu-id="5bdba-442">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="5bdba-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5bdba-443">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="5bdba-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="5bdba-444">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="5bdba-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="5bdba-445">W takich przypadkach należy ująć wartość parametru języka, np `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5bdba-446">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5bdba-446">The name for the created output.</span></span> <span data-ttu-id="5bdba-447">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5bdba-448">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5bdba-448">Location to place the generated output.</span></span> <span data-ttu-id="5bdba-449">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="5bdba-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="5bdba-450">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="5bdba-450">Template options</span></span>

<span data-ttu-id="5bdba-451">Każdy szablon projektu może mieć dodatkowe opcje dostępne.</span><span class="sxs-lookup"><span data-stu-id="5bdba-451">Each project template may have additional options available.</span></span> <span data-ttu-id="5bdba-452">Szablony podstawowe mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="5bdba-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5bdba-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5bdba-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5bdba-454">**konsoli**</span><span class="sxs-lookup"><span data-stu-id="5bdba-454">**console**</span></span>

<span data-ttu-id="5bdba-455">`--langVersion <VERSION_NUMBER>`-Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="5bdba-456">Na przykład użyj `--langVersion 7.3` , aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="5bdba-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="5bdba-457">Nieobsługiwane w F#programie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-457">Not supported for F#.</span></span>

<span data-ttu-id="5bdba-458">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-459">**kątowy, reagowanie, reactredux**</span><span class="sxs-lookup"><span data-stu-id="5bdba-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="5bdba-460">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5bdba-461">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-462">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5bdba-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5bdba-463">Ta opcja ma zastosowanie tylko `IndividualAuth` wtedy `OrganizationalAuth` , gdy lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="5bdba-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="5bdba-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="5bdba-464">**razorclasslib**</span></span>

<span data-ttu-id="5bdba-465">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5bdba-466">**classlib**</span></span>

<span data-ttu-id="5bdba-467">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="5bdba-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5bdba-468">Wartości: `netcoreapp2.2` aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard2.0` utworzyć bibliotekę klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5bdba-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5bdba-469">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="5bdba-470">`--langVersion <VERSION_NUMBER>`-Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="5bdba-471">Na przykład użyj `--langVersion 7.3` , aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="5bdba-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="5bdba-472">Nieobsługiwane w F#programie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-472">Not supported for F#.</span></span>

<span data-ttu-id="5bdba-473">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="5bdba-474">**mstest, xunit**</span></span>

<span data-ttu-id="5bdba-475">`-p|--enable-pack`— Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5bdba-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5bdba-476">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-477">**NUnit**</span><span class="sxs-lookup"><span data-stu-id="5bdba-477">**nunit**</span></span>

<span data-ttu-id="5bdba-478">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="5bdba-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5bdba-479">Wartość domyślna to `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="5bdba-480">`-p|--enable-pack`— Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5bdba-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5bdba-481">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-482">**stronic**</span><span class="sxs-lookup"><span data-stu-id="5bdba-482">**page**</span></span>

<span data-ttu-id="5bdba-483">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="5bdba-484">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5bdba-485">`-np|--no-pagemodel`-Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="5bdba-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="5bdba-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="5bdba-486">**viewimports**</span></span>

<span data-ttu-id="5bdba-487">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="5bdba-488">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5bdba-489">**web**</span><span class="sxs-lookup"><span data-stu-id="5bdba-489">**web**</span></span>

<span data-ttu-id="5bdba-490">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5bdba-491">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-492">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5bdba-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5bdba-493">Ta opcja ma zastosowanie tylko `IndividualAuth` wtedy `OrganizationalAuth` , gdy lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="5bdba-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="5bdba-494">**MVC, webapp**</span><span class="sxs-lookup"><span data-stu-id="5bdba-494">**mvc, webapp**</span></span>

<span data-ttu-id="5bdba-495">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5bdba-496">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="5bdba-496">The possible values are:</span></span>

- <span data-ttu-id="5bdba-497">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="5bdba-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5bdba-498">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="5bdba-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="5bdba-499">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5bdba-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5bdba-500">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="5bdba-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5bdba-501">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="5bdba-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="5bdba-502">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5bdba-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5bdba-503">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5bdba-504">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-505">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5bdba-506">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5bdba-507">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-508">`-rp|--reset-password-policy-id <ID>`— Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="5bdba-509">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-510">`-ep|--edit-profile-policy-id <ID>`-Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="5bdba-511">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-512">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5bdba-513">Używanie z `SingleOrg` usługą `MultiOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5bdba-514">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5bdba-515">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5bdba-516">Użyj z `IndividualB2C`, `SingleOrg`lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5bdba-517">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5bdba-518">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5bdba-519">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-520">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5bdba-521">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5bdba-522">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-523">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5bdba-524">`--callback-path <PATH>`-Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5bdba-525">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-526">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="5bdba-527">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5bdba-528">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5bdba-529">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5bdba-530">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5bdba-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5bdba-531">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane `Startup.Configure`do.</span><span class="sxs-lookup"><span data-stu-id="5bdba-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="5bdba-532">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C` `SingleOrg`, gdy, `MultiOrg` , lub nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="5bdba-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="5bdba-533">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="5bdba-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5bdba-534">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-535">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-536">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="5bdba-536">**webapi**</span></span>

<span data-ttu-id="5bdba-537">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5bdba-538">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="5bdba-538">The possible values are:</span></span>

- <span data-ttu-id="5bdba-539">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="5bdba-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5bdba-540">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5bdba-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5bdba-541">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="5bdba-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5bdba-542">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5bdba-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5bdba-543">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5bdba-544">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-545">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5bdba-546">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5bdba-547">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-548">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5bdba-549">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-550">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5bdba-551">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5bdba-552">Używanie z `IndividualB2C` usługą `SingleOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-553">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5bdba-554">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5bdba-555">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-556">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5bdba-557">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5bdba-558">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-559">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5bdba-560">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5bdba-561">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5bdba-562">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5bdba-563">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5bdba-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5bdba-564">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane `Startup.Configure`do.</span><span class="sxs-lookup"><span data-stu-id="5bdba-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="5bdba-565">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C` `SingleOrg`, gdy, `MultiOrg` , lub nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="5bdba-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="5bdba-566">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="5bdba-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5bdba-567">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-568">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="5bdba-569">**globaljson**</span></span>

<span data-ttu-id="5bdba-570">`--sdk-version <VERSION_NUMBER>`-Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5bdba-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5bdba-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5bdba-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5bdba-572">**konsole, kątowe, reagowanie, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="5bdba-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="5bdba-573">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5bdba-574">**classlib**</span></span>

<span data-ttu-id="5bdba-575">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="5bdba-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5bdba-576">Wartości: `netcoreapp2.1` aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard2.0` utworzyć bibliotekę klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5bdba-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5bdba-577">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="5bdba-578">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="5bdba-579">**mstest, xunit**</span></span>

<span data-ttu-id="5bdba-580">`-p|--enable-pack`— Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5bdba-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5bdba-581">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="5bdba-582">**globaljson**</span></span>

<span data-ttu-id="5bdba-583">`--sdk-version <VERSION_NUMBER>`-Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5bdba-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="5bdba-584">**web**</span><span class="sxs-lookup"><span data-stu-id="5bdba-584">**web**</span></span>

<span data-ttu-id="5bdba-585">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5bdba-586">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-587">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5bdba-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5bdba-588">Ta opcja ma zastosowanie tylko `IndividualAuth` wtedy `OrganizationalAuth` , gdy lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="5bdba-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="5bdba-589">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="5bdba-589">**webapi**</span></span>

<span data-ttu-id="5bdba-590">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5bdba-591">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="5bdba-591">The possible values are:</span></span>

- <span data-ttu-id="5bdba-592">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="5bdba-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5bdba-593">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5bdba-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5bdba-594">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="5bdba-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5bdba-595">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5bdba-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5bdba-596">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5bdba-597">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-598">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5bdba-599">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5bdba-600">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-601">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5bdba-602">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-603">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5bdba-604">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5bdba-605">Używanie z `IndividualB2C` usługą `SingleOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-606">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5bdba-607">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5bdba-608">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-609">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5bdba-610">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5bdba-611">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-612">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5bdba-613">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5bdba-614">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5bdba-615">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5bdba-616">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="5bdba-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5bdba-617">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-618">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-619">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5bdba-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5bdba-620">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane `Startup.Configure`do.</span><span class="sxs-lookup"><span data-stu-id="5bdba-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="5bdba-621">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C` `SingleOrg`, gdy, `MultiOrg` , lub nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="5bdba-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="5bdba-622">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="5bdba-622">**mvc, razor**</span></span>

<span data-ttu-id="5bdba-623">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5bdba-624">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="5bdba-624">The possible values are:</span></span>

- <span data-ttu-id="5bdba-625">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="5bdba-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5bdba-626">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="5bdba-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="5bdba-627">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5bdba-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5bdba-628">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="5bdba-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5bdba-629">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="5bdba-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="5bdba-630">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5bdba-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5bdba-631">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5bdba-632">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-633">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5bdba-634">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5bdba-635">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-636">`-rp|--reset-password-policy-id <ID>`— Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="5bdba-637">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-638">`-ep|--edit-profile-policy-id <ID>`-Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="5bdba-639">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-640">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5bdba-641">Używanie z `SingleOrg` usługą `MultiOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5bdba-642">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5bdba-643">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5bdba-644">Użyj z `IndividualB2C`, `SingleOrg`lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5bdba-645">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5bdba-646">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5bdba-647">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-648">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5bdba-649">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5bdba-650">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-651">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5bdba-652">`--callback-path <PATH>`-Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5bdba-653">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-654">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="5bdba-655">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5bdba-656">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5bdba-657">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="5bdba-658">`--use-browserlink`-Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="5bdba-659">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="5bdba-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5bdba-660">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-661">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-662">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5bdba-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="5bdba-663">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane `Startup.Configure`do.</span><span class="sxs-lookup"><span data-stu-id="5bdba-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="5bdba-664">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C` `SingleOrg`, gdy, `MultiOrg` , lub nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="5bdba-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="5bdba-665">**stronic**</span><span class="sxs-lookup"><span data-stu-id="5bdba-665">**page**</span></span>

<span data-ttu-id="5bdba-666">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="5bdba-667">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5bdba-668">`-np|--no-pagemodel`-Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="5bdba-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="5bdba-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="5bdba-669">**viewimports**</span></span>

<span data-ttu-id="5bdba-670">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="5bdba-671">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5bdba-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5bdba-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="5bdba-673">**konsole, kątowe, reagowanie, reactredux**</span><span class="sxs-lookup"><span data-stu-id="5bdba-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="5bdba-674">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5bdba-675">**classlib**</span></span>

<span data-ttu-id="5bdba-676">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="5bdba-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5bdba-677">Wartości: `netcoreapp2.0` aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard2.0` utworzyć bibliotekę klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5bdba-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5bdba-678">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="5bdba-679">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="5bdba-680">**mstest, xunit**</span></span>

<span data-ttu-id="5bdba-681">`-p|--enable-pack`— Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="5bdba-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5bdba-682">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="5bdba-683">**globaljson**</span></span>

<span data-ttu-id="5bdba-684">`--sdk-version <VERSION_NUMBER>`-Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5bdba-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="5bdba-685">**web**</span><span class="sxs-lookup"><span data-stu-id="5bdba-685">**web**</span></span>

<span data-ttu-id="5bdba-686">`--use-launch-settings`-Zawiera *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5bdba-687">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-688">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="5bdba-688">**webapi**</span></span>

<span data-ttu-id="5bdba-689">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5bdba-690">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="5bdba-690">The possible values are:</span></span>

- <span data-ttu-id="5bdba-691">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="5bdba-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5bdba-692">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5bdba-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5bdba-693">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="5bdba-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5bdba-694">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5bdba-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5bdba-695">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5bdba-696">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-697">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5bdba-698">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5bdba-699">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-700">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5bdba-701">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-702">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5bdba-703">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5bdba-704">Używanie z `IndividualB2C` usługą `SingleOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-705">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5bdba-706">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5bdba-707">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-708">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5bdba-709">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5bdba-710">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-711">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5bdba-712">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5bdba-713">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5bdba-714">`--use-launch-settings`-Zawiera *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5bdba-715">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="5bdba-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5bdba-716">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-717">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-718">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="5bdba-718">**mvc, razor**</span></span>

<span data-ttu-id="5bdba-719">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5bdba-720">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="5bdba-720">The possible values are:</span></span>

- <span data-ttu-id="5bdba-721">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="5bdba-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5bdba-722">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="5bdba-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="5bdba-723">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="5bdba-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5bdba-724">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="5bdba-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5bdba-725">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="5bdba-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="5bdba-726">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5bdba-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5bdba-727">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5bdba-728">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-729">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5bdba-730">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5bdba-731">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-732">`-rp|--reset-password-policy-id <ID>`— Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="5bdba-733">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-734">`-ep|--edit-profile-policy-id <ID>`-Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="5bdba-735">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-736">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5bdba-737">Używanie z `SingleOrg` usługą `MultiOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5bdba-738">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5bdba-739">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5bdba-740">Użyj z `IndividualB2C`, `SingleOrg`lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5bdba-741">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5bdba-742">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5bdba-743">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-744">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5bdba-745">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5bdba-746">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5bdba-747">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5bdba-748">`--callback-path <PATH>`-Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5bdba-749">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="5bdba-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5bdba-750">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="5bdba-751">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5bdba-752">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5bdba-753">`--use-launch-settings`-Zawiera *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5bdba-754">`--use-browserlink`-Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="5bdba-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="5bdba-755">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="5bdba-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5bdba-756">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="5bdba-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5bdba-757">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="5bdba-758">**stronic**</span><span class="sxs-lookup"><span data-stu-id="5bdba-758">**page**</span></span>

<span data-ttu-id="5bdba-759">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5bdba-760">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5bdba-761">`-np|--no-pagemodel`-Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="5bdba-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="5bdba-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="5bdba-762">**viewimports**</span></span>

<span data-ttu-id="5bdba-763">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5bdba-764">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5bdba-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5bdba-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="5bdba-766">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="5bdba-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="5bdba-767">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="5bdba-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5bdba-768">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="5bdba-769">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="5bdba-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5bdba-770">**classlib**</span></span>

<span data-ttu-id="5bdba-771">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="5bdba-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5bdba-772">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="5bdba-773">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="5bdba-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="5bdba-774">**mvc**</span></span>

<span data-ttu-id="5bdba-775">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="5bdba-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5bdba-776">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="5bdba-777">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="5bdba-778">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="5bdba-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5bdba-779">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="5bdba-780">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-780">The default value is `None`.</span></span>

<span data-ttu-id="5bdba-781">`-uld|--use-local-db`-Określa, czy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="5bdba-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="5bdba-782">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-782">Values: `true` or `false`.</span></span> <span data-ttu-id="5bdba-783">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5bdba-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="5bdba-784">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5bdba-784">Examples</span></span>

<span data-ttu-id="5bdba-785">Utwórz projekt C# aplikacji konsolowej, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="5bdba-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="5bdba-786">Utwórz projekt F# aplikacji konsolowej w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="5bdba-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="5bdba-787">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku wersji zestaw .NET Core SDK 2,0 lub nowszej):</span><span class="sxs-lookup"><span data-stu-id="5bdba-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="5bdba-788">Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="5bdba-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="5bdba-789">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="5bdba-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="5bdba-790">Wyświetl listę wszystkich szablonów dostępnych dla MVC:</span><span class="sxs-lookup"><span data-stu-id="5bdba-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="5bdba-791">Wyświetl listę wszystkich szablonów pasujących *do* podciągu.</span><span class="sxs-lookup"><span data-stu-id="5bdba-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="5bdba-792">Nie znaleziono dokładnego dopasowania, więc Dopasowywanie podciągów działa w odniesieniu do kolumn krótkich nazw i nazw.</span><span class="sxs-lookup"><span data-stu-id="5bdba-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="5bdba-793">Podjęto próbę wywołania szablonu zgodnego z parametrem *ng*.</span><span class="sxs-lookup"><span data-stu-id="5bdba-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="5bdba-794">Jeśli nie można ustalić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są dopasowań częściowych.</span><span class="sxs-lookup"><span data-stu-id="5bdba-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="5bdba-795">Zainstaluj wersję 2,0 szablonów aplikacji jednostronicowych dla ASP.NET Core (opcja polecenia dostępna tylko dla zestaw .NET Core SDK 1,1 i nowszych wersji):</span><span class="sxs-lookup"><span data-stu-id="5bdba-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="5bdba-796">Utwórz plik *Global. JSON* w bieżącym katalogu, ustawiając wersję zestawu SDK na 2.0.0 (dostępne tylko w zestaw .NET Core SDK 2,0 lub nowszych wersjach):</span><span class="sxs-lookup"><span data-stu-id="5bdba-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="5bdba-797">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bdba-797">See also</span></span>

- [<span data-ttu-id="5bdba-798">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="5bdba-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="5bdba-799">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="5bdba-799">Create a custom template for dotnet new</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="5bdba-800">dotnet/dotnet-Template-przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="5bdba-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="5bdba-801">Dostępne szablony dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="5bdba-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
