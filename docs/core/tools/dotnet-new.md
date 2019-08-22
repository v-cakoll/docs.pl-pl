---
title: polecenie dotnet New
description: Polecenie dotnet New umożliwia tworzenie nowych projektów platformy .NET Core na podstawie określonego szablonu.
ms.date: 05/06/2019
ms.openlocfilehash: c9e960bab0e28e88b0cc8d431dad3b9f3f00c9c0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660540"
---
# <a name="dotnet-new"></a><span data-ttu-id="ae71c-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ae71c-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ae71c-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ae71c-104">Name</span></span>

<span data-ttu-id="ae71c-105">`dotnet new`-Tworzy nowy projekt, plik konfiguracji lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ae71c-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ae71c-106">Synopsis</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="ae71c-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ae71c-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ae71c-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ae71c-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ae71c-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ae71c-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ae71c-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ae71c-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="ae71c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ae71c-111">Description</span></span>

<span data-ttu-id="ae71c-112">`dotnet new` Polecenie zapewnia wygodny sposób inicjowania prawidłowego projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae71c-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="ae71c-113">Polecenie wywołuje [aparat szablonu](https://github.com/dotnet/templating) , aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="ae71c-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="ae71c-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ae71c-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="ae71c-115">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ae71c-116">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="ae71c-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ae71c-117">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ae71c-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="ae71c-118">Jeśli wartość nie jest dokładnym dopasowaniem do tekstu w kolumnie Templates lub **short name** , do tych dwóch kolumn jest wykonywane dopasowanie podciągów. `TEMPLATE`</span><span class="sxs-lookup"><span data-stu-id="ae71c-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="ae71c-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ae71c-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="ae71c-120">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-120">The command contains a default list of templates.</span></span> <span data-ttu-id="ae71c-121">Użyj `dotnet new -l` , aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ae71c-122">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="ae71c-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="ae71c-123">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="ae71c-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="ae71c-124">Szablony</span><span class="sxs-lookup"><span data-stu-id="ae71c-124">Templates</span></span>                                    | <span data-ttu-id="ae71c-125">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="ae71c-125">Short Name</span></span>        | <span data-ttu-id="ae71c-126">Język</span><span class="sxs-lookup"><span data-stu-id="ae71c-126">Language</span></span>     | <span data-ttu-id="ae71c-127">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="ae71c-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="ae71c-128">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="ae71c-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="ae71c-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-129">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-130">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="ae71c-130">Common/Console</span></span>                        |
| <span data-ttu-id="ae71c-131">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="ae71c-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="ae71c-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-132">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-133">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="ae71c-133">Common/Library</span></span>                        |
| <span data-ttu-id="ae71c-134">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="ae71c-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="ae71c-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-135">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="ae71c-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="ae71c-137">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ae71c-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="ae71c-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-138">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="ae71c-140">Element testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ae71c-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="ae71c-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-141">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="ae71c-143">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="ae71c-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-144">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="ae71c-146">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="ae71c-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="ae71c-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-147">[C#]</span></span>         | <span data-ttu-id="ae71c-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ae71c-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ae71c-149">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="ae71c-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-150">[C#]</span></span>         | <span data-ttu-id="ae71c-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ae71c-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ae71c-152">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="ae71c-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-153">[C#]</span></span>         | <span data-ttu-id="ae71c-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ae71c-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ae71c-155">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="ae71c-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="ae71c-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-156">[C#], F#</span></span>     | <span data-ttu-id="ae71c-157">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="ae71c-157">Web/Empty</span></span>                             |
| <span data-ttu-id="ae71c-158">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="ae71c-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="ae71c-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-159">[C#], F#</span></span>     | <span data-ttu-id="ae71c-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-160">Web/MVC</span></span>                               |
| <span data-ttu-id="ae71c-161">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae71c-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="ae71c-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="ae71c-162">`webapp`, `razor`</span></span> | <span data-ttu-id="ae71c-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-163">[C#]</span></span>         | <span data-ttu-id="ae71c-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ae71c-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="ae71c-165">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="ae71c-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="ae71c-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-166">[C#]</span></span>         | <span data-ttu-id="ae71c-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ae71c-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ae71c-168">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="ae71c-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="ae71c-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-169">[C#]</span></span>         | <span data-ttu-id="ae71c-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ae71c-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ae71c-171">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="ae71c-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="ae71c-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-172">[C#]</span></span>         | <span data-ttu-id="ae71c-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ae71c-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ae71c-174">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="ae71c-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="ae71c-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-175">[C#]</span></span>         | <span data-ttu-id="ae71c-176">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="ae71c-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="ae71c-177">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae71c-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="ae71c-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-178">[C#], F#</span></span>     | <span data-ttu-id="ae71c-179">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ae71c-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="ae71c-180">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="ae71c-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="ae71c-181">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-181">Config</span></span>                                |
| <span data-ttu-id="ae71c-182">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="ae71c-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="ae71c-183">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-183">Config</span></span>                                |
| <span data-ttu-id="ae71c-184">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="ae71c-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="ae71c-185">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-185">Config</span></span>                                |
| <span data-ttu-id="ae71c-186">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ae71c-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="ae71c-187">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ae71c-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ae71c-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ae71c-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ae71c-189">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-189">The command contains a default list of templates.</span></span> <span data-ttu-id="ae71c-190">Użyj `dotnet new -l` , aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ae71c-191">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="ae71c-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="ae71c-192">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="ae71c-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="ae71c-193">Szablony</span><span class="sxs-lookup"><span data-stu-id="ae71c-193">Templates</span></span>                                    | <span data-ttu-id="ae71c-194">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="ae71c-194">Short Name</span></span>      | <span data-ttu-id="ae71c-195">Język</span><span class="sxs-lookup"><span data-stu-id="ae71c-195">Language</span></span>     | <span data-ttu-id="ae71c-196">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="ae71c-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="ae71c-197">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="ae71c-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="ae71c-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-198">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-199">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="ae71c-199">Common/Console</span></span>                        |
| <span data-ttu-id="ae71c-200">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="ae71c-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="ae71c-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-201">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-202">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="ae71c-202">Common/Library</span></span>                        |
| <span data-ttu-id="ae71c-203">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="ae71c-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="ae71c-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-204">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="ae71c-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="ae71c-206">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="ae71c-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-207">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="ae71c-209">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="ae71c-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="ae71c-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-210">[C#]</span></span>         | <span data-ttu-id="ae71c-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ae71c-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ae71c-212">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="ae71c-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-213">[C#]</span></span>         | <span data-ttu-id="ae71c-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ae71c-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ae71c-215">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="ae71c-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-216">[C#]</span></span>         | <span data-ttu-id="ae71c-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ae71c-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ae71c-218">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="ae71c-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="ae71c-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-219">[C#], F#</span></span>     | <span data-ttu-id="ae71c-220">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="ae71c-220">Web/Empty</span></span>                             |
| <span data-ttu-id="ae71c-221">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="ae71c-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="ae71c-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-222">[C#], F#</span></span>     | <span data-ttu-id="ae71c-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-223">Web/MVC</span></span>                               |
| <span data-ttu-id="ae71c-224">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae71c-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="ae71c-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-225">[C#]</span></span>         | <span data-ttu-id="ae71c-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ae71c-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="ae71c-227">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="ae71c-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="ae71c-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-228">[C#]</span></span>         | <span data-ttu-id="ae71c-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ae71c-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ae71c-230">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="ae71c-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="ae71c-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-231">[C#]</span></span>         | <span data-ttu-id="ae71c-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ae71c-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ae71c-233">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="ae71c-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="ae71c-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-234">[C#]</span></span>         | <span data-ttu-id="ae71c-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ae71c-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="ae71c-236">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="ae71c-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="ae71c-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-237">[C#]</span></span>         | <span data-ttu-id="ae71c-238">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="ae71c-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="ae71c-239">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae71c-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="ae71c-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-240">[C#], F#</span></span>     | <span data-ttu-id="ae71c-241">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ae71c-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="ae71c-242">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="ae71c-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="ae71c-243">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-243">Config</span></span>                                |
| <span data-ttu-id="ae71c-244">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="ae71c-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="ae71c-245">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-245">Config</span></span>                                |
| <span data-ttu-id="ae71c-246">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="ae71c-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="ae71c-247">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-247">Config</span></span>                                |
| <span data-ttu-id="ae71c-248">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ae71c-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="ae71c-249">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ae71c-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ae71c-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ae71c-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="ae71c-251">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-251">The command contains a default list of templates.</span></span> <span data-ttu-id="ae71c-252">Użyj `dotnet new -l` , aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ae71c-253">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="ae71c-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="ae71c-254">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="ae71c-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="ae71c-255">Szablony</span><span class="sxs-lookup"><span data-stu-id="ae71c-255">Templates</span></span>                                    | <span data-ttu-id="ae71c-256">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="ae71c-256">Short Name</span></span>    | <span data-ttu-id="ae71c-257">Język</span><span class="sxs-lookup"><span data-stu-id="ae71c-257">Language</span></span>     | <span data-ttu-id="ae71c-258">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="ae71c-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="ae71c-259">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="ae71c-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="ae71c-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-260">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-261">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="ae71c-261">Common/Console</span></span>      |
| <span data-ttu-id="ae71c-262">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="ae71c-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="ae71c-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-263">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-264">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="ae71c-264">Common/Library</span></span>      |
| <span data-ttu-id="ae71c-265">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="ae71c-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="ae71c-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-266">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="ae71c-267">Test/MSTest</span></span>         |
| <span data-ttu-id="ae71c-268">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="ae71c-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ae71c-269">[C#], F#, VB</span></span> | <span data-ttu-id="ae71c-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-270">Test/xUnit</span></span>          |
| <span data-ttu-id="ae71c-271">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="ae71c-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="ae71c-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-272">[C#], F#</span></span>     | <span data-ttu-id="ae71c-273">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="ae71c-273">Web/Empty</span></span>           |
| <span data-ttu-id="ae71c-274">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="ae71c-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="ae71c-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-275">[C#], F#</span></span>     | <span data-ttu-id="ae71c-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-276">Web/MVC</span></span>             |
| <span data-ttu-id="ae71c-277">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae71c-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="ae71c-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-278">[C#]</span></span>         | <span data-ttu-id="ae71c-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ae71c-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="ae71c-280">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="ae71c-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="ae71c-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-281">[C#]</span></span>         | <span data-ttu-id="ae71c-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ae71c-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="ae71c-283">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="ae71c-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="ae71c-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-284">[C#]</span></span>         | <span data-ttu-id="ae71c-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ae71c-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="ae71c-286">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="ae71c-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="ae71c-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-287">[C#]</span></span>         | <span data-ttu-id="ae71c-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ae71c-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="ae71c-289">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae71c-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="ae71c-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-290">[C#], F#</span></span>     | <span data-ttu-id="ae71c-291">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ae71c-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="ae71c-292">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="ae71c-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="ae71c-293">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-293">Config</span></span>              |
| <span data-ttu-id="ae71c-294">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="ae71c-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="ae71c-295">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-295">Config</span></span>              |
| <span data-ttu-id="ae71c-296">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="ae71c-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="ae71c-297">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-297">Config</span></span>              |
| <span data-ttu-id="ae71c-298">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ae71c-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="ae71c-299">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ae71c-299">Solution</span></span>            |
| <span data-ttu-id="ae71c-300">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="ae71c-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="ae71c-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ae71c-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="ae71c-302">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="ae71c-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ae71c-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="ae71c-304">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="ae71c-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ae71c-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ae71c-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ae71c-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ae71c-307">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-307">The command contains a default list of templates.</span></span> <span data-ttu-id="ae71c-308">Użyj `dotnet new -all` , aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="ae71c-309">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane przy użyciu zestaw .NET Core SDK 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="ae71c-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="ae71c-310">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="ae71c-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="ae71c-311">Szablony</span><span class="sxs-lookup"><span data-stu-id="ae71c-311">Templates</span></span>            | <span data-ttu-id="ae71c-312">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="ae71c-312">Short Name</span></span>    | <span data-ttu-id="ae71c-313">Język</span><span class="sxs-lookup"><span data-stu-id="ae71c-313">Language</span></span> | <span data-ttu-id="ae71c-314">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="ae71c-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="ae71c-315">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="ae71c-315">Console Application</span></span>  | `console`     | <span data-ttu-id="ae71c-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-316">[C#], F#</span></span> | <span data-ttu-id="ae71c-317">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="ae71c-317">Common/Console</span></span> |
| <span data-ttu-id="ae71c-318">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="ae71c-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="ae71c-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-319">[C#], F#</span></span> | <span data-ttu-id="ae71c-320">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="ae71c-320">Common/Library</span></span> |
| <span data-ttu-id="ae71c-321">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="ae71c-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="ae71c-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-322">[C#], F#</span></span> | <span data-ttu-id="ae71c-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="ae71c-323">Test/MSTest</span></span>    |
| <span data-ttu-id="ae71c-324">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="ae71c-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-325">[C#], F#</span></span> | <span data-ttu-id="ae71c-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="ae71c-326">Test/xUnit</span></span>     |
| <span data-ttu-id="ae71c-327">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="ae71c-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="ae71c-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-328">[C#]</span></span>     | <span data-ttu-id="ae71c-329">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="ae71c-329">Web/Empty</span></span>      |
| <span data-ttu-id="ae71c-330">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae71c-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="ae71c-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ae71c-331">[C#], F#</span></span> | <span data-ttu-id="ae71c-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ae71c-332">Web/MVC</span></span>        |
| <span data-ttu-id="ae71c-333">Interfejs API sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae71c-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="ae71c-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="ae71c-334">[C#]</span></span>     | <span data-ttu-id="ae71c-335">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ae71c-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="ae71c-336">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="ae71c-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="ae71c-337">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-337">Config</span></span>         |
| <span data-ttu-id="ae71c-338">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="ae71c-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="ae71c-339">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae71c-339">Config</span></span>         |
| <span data-ttu-id="ae71c-340">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ae71c-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="ae71c-341">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ae71c-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="ae71c-342">Opcje</span><span class="sxs-lookup"><span data-stu-id="ae71c-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="ae71c-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ae71c-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="ae71c-344">Wyświetla podsumowanie tego, co się stanie w przypadku uruchomienia danego polecenia, jeśli mogłoby to spowodować utworzenie szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="ae71c-345">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="ae71c-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ae71c-346">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="ae71c-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ae71c-347">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-347">Prints out help for the command.</span></span> <span data-ttu-id="ae71c-348">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu, takiego jak. `dotnet new mvc --help`</span><span class="sxs-lookup"><span data-stu-id="ae71c-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ae71c-349">Instaluje pakiet źródłowy lub szablon z `PATH` lub `NUGET_ID` udostępnione.</span><span class="sxs-lookup"><span data-stu-id="ae71c-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ae71c-350">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ae71c-351">Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ae71c-352">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="ae71c-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ae71c-353">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ae71c-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ae71c-354">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="ae71c-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="ae71c-355">Jeśli zostanie wywołana dla `dotnet new` polecenia, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ae71c-356">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ae71c-357">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-357">The language of the template to create.</span></span> <span data-ttu-id="ae71c-358">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="ae71c-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ae71c-359">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ae71c-360">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="ae71c-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ae71c-361">W takich przypadkach należy ująć wartość parametru języka, np `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ae71c-362">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ae71c-362">The name for the created output.</span></span> <span data-ttu-id="ae71c-363">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="ae71c-364">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="ae71c-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ae71c-365">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ae71c-365">Location to place the generated output.</span></span> <span data-ttu-id="ae71c-366">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="ae71c-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ae71c-367">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="ae71c-367">Filters templates based on available types.</span></span> <span data-ttu-id="ae71c-368">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="ae71c-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ae71c-369">Odinstalowuje pakiet źródłowy lub szablonowy w `PATH` udostępnionym lub. `NUGET_ID`</span><span class="sxs-lookup"><span data-stu-id="ae71c-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ae71c-370">Podczas wykluczania `<PATH|NUGET_ID>` wartości są wyświetlane wszystkie aktualnie zainstalowane pakiety szablonów i powiązane z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="ae71c-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="ae71c-371">Aby odinstalować szablon przy użyciu programu `PATH`, należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="ae71c-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ae71c-372">Na przykład *C:/Users/\<user >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="ae71c-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="ae71c-373">Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ae71c-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ae71c-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="ae71c-375">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="ae71c-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ae71c-376">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="ae71c-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ae71c-377">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-377">Prints out help for the command.</span></span> <span data-ttu-id="ae71c-378">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu, takiego jak. `dotnet new mvc --help`</span><span class="sxs-lookup"><span data-stu-id="ae71c-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ae71c-379">Instaluje pakiet źródłowy lub szablon z `PATH` lub `NUGET_ID` udostępnione.</span><span class="sxs-lookup"><span data-stu-id="ae71c-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ae71c-380">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ae71c-381">Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ae71c-382">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="ae71c-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ae71c-383">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ae71c-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ae71c-384">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="ae71c-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="ae71c-385">Jeśli zostanie wywołana dla `dotnet new` polecenia, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ae71c-386">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ae71c-387">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-387">The language of the template to create.</span></span> <span data-ttu-id="ae71c-388">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="ae71c-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ae71c-389">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ae71c-390">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="ae71c-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ae71c-391">W takich przypadkach należy ująć wartość parametru języka, np `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ae71c-392">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ae71c-392">The name for the created output.</span></span> <span data-ttu-id="ae71c-393">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="ae71c-394">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="ae71c-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ae71c-395">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ae71c-395">Location to place the generated output.</span></span> <span data-ttu-id="ae71c-396">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="ae71c-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ae71c-397">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="ae71c-397">Filters templates based on available types.</span></span> <span data-ttu-id="ae71c-398">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="ae71c-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ae71c-399">Odinstalowuje pakiet źródłowy lub szablonowy w `PATH` udostępnionym lub. `NUGET_ID`</span><span class="sxs-lookup"><span data-stu-id="ae71c-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ae71c-400">Aby odinstalować szablon przy użyciu programu `PATH`, należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="ae71c-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ae71c-401">Na przykład *C:/Users/\<user >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="ae71c-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="ae71c-402">Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ae71c-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ae71c-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="ae71c-404">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="ae71c-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ae71c-405">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="ae71c-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ae71c-406">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-406">Prints out help for the command.</span></span> <span data-ttu-id="ae71c-407">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu, takiego jak. `dotnet new mvc --help`</span><span class="sxs-lookup"><span data-stu-id="ae71c-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ae71c-408">Instaluje pakiet źródłowy lub szablon z `PATH` lub `NUGET_ID` udostępnione.</span><span class="sxs-lookup"><span data-stu-id="ae71c-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ae71c-409">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ae71c-410">Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ae71c-411">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="ae71c-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ae71c-412">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ae71c-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ae71c-413">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="ae71c-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="ae71c-414">Jeśli zostanie wywołana dla `dotnet new` polecenia, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ae71c-415">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ae71c-416">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-416">The language of the template to create.</span></span> <span data-ttu-id="ae71c-417">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="ae71c-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ae71c-418">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ae71c-419">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="ae71c-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ae71c-420">W takich przypadkach należy ująć wartość parametru języka, np `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ae71c-421">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ae71c-421">The name for the created output.</span></span> <span data-ttu-id="ae71c-422">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ae71c-423">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ae71c-423">Location to place the generated output.</span></span> <span data-ttu-id="ae71c-424">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="ae71c-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ae71c-425">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="ae71c-425">Filters templates based on available types.</span></span> <span data-ttu-id="ae71c-426">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="ae71c-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ae71c-427">Odinstalowuje pakiet źródłowy lub szablonowy w `PATH` udostępnionym lub. `NUGET_ID`</span><span class="sxs-lookup"><span data-stu-id="ae71c-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ae71c-428">Aby odinstalować szablon przy użyciu źródła `PATH`, należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="ae71c-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ae71c-429">Na przykład *C:/Users/\<user >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="ae71c-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="ae71c-430">Ponadto nie należy umieszczać końcowych ukośników katalogów na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="ae71c-431">Jeśli nie możesz określić `PATH` argumentu lub `NUGET_ID` wymaganego do odinstalowania szablonu, uruchomienie `dotnet new --uninstall` bez argumentu spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argumentu wymaganego do ich odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ae71c-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ae71c-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="ae71c-433">Pokazuje wszystkie szablony dla określonego typu projektu, gdy działa w kontekście `dotnet new` samego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="ae71c-434">Gdy jest uruchamiany w kontekście określonego szablonu, na przykład `dotnet new web -all`, `-all` jest interpretowany jako flaga tworzenia siły.</span><span class="sxs-lookup"><span data-stu-id="ae71c-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="ae71c-435">Jest to wymagane, gdy katalog wyjściowy zawiera już projekt.</span><span class="sxs-lookup"><span data-stu-id="ae71c-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ae71c-436">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-436">Prints out help for the command.</span></span> <span data-ttu-id="ae71c-437">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu, takiego jak. `dotnet new mvc --help`</span><span class="sxs-lookup"><span data-stu-id="ae71c-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="ae71c-438">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="ae71c-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="ae71c-439">Jeśli zostanie wywołana dla `dotnet new` polecenia, wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ae71c-440">Na przykład jeśli katalog zawiera już projekt, nie wyświetla wszystkich szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="ae71c-441">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-441">The language of the template to create.</span></span> <span data-ttu-id="ae71c-442">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="ae71c-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ae71c-443">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ae71c-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ae71c-444">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="ae71c-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ae71c-445">W takich przypadkach należy ująć wartość parametru języka, np `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ae71c-446">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ae71c-446">The name for the created output.</span></span> <span data-ttu-id="ae71c-447">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ae71c-448">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ae71c-448">Location to place the generated output.</span></span> <span data-ttu-id="ae71c-449">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="ae71c-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="ae71c-450">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="ae71c-450">Template options</span></span>

<span data-ttu-id="ae71c-451">Każdy szablon projektu może mieć dodatkowe opcje dostępne.</span><span class="sxs-lookup"><span data-stu-id="ae71c-451">Each project template may have additional options available.</span></span> <span data-ttu-id="ae71c-452">Szablony podstawowe mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="ae71c-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="ae71c-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ae71c-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="ae71c-454">**konsoli**</span><span class="sxs-lookup"><span data-stu-id="ae71c-454">**console**</span></span>

<span data-ttu-id="ae71c-455">`--langVersion <VERSION_NUMBER>`-Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ae71c-456">Na przykład użyj `--langVersion 7.3` , aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ae71c-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ae71c-457">Nieobsługiwane w F#programie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-457">Not supported for F#.</span></span>

<span data-ttu-id="ae71c-458">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-459">**kątowy, reagowanie, reactredux**</span><span class="sxs-lookup"><span data-stu-id="ae71c-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="ae71c-460">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ae71c-461">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-462">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae71c-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ae71c-463">Ta opcja ma zastosowanie tylko `IndividualAuth` wtedy `OrganizationalAuth` , gdy lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="ae71c-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="ae71c-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="ae71c-464">**razorclasslib**</span></span>

<span data-ttu-id="ae71c-465">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ae71c-466">**classlib**</span></span>

<span data-ttu-id="ae71c-467">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ae71c-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ae71c-468">Wartości: `netcoreapp2.2` aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard2.0` utworzyć bibliotekę klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ae71c-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ae71c-469">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ae71c-470">`--langVersion <VERSION_NUMBER>`-Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ae71c-471">Na przykład użyj `--langVersion 7.3` , aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ae71c-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ae71c-472">Nieobsługiwane w F#programie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-472">Not supported for F#.</span></span>

<span data-ttu-id="ae71c-473">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ae71c-474">**mstest, xunit**</span></span>

<span data-ttu-id="ae71c-475">`-p|--enable-pack`— Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ae71c-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ae71c-476">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-477">**NUnit**</span><span class="sxs-lookup"><span data-stu-id="ae71c-477">**nunit**</span></span>

<span data-ttu-id="ae71c-478">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ae71c-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ae71c-479">Wartość domyślna to `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="ae71c-480">`-p|--enable-pack`— Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ae71c-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ae71c-481">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-482">**stronic**</span><span class="sxs-lookup"><span data-stu-id="ae71c-482">**page**</span></span>

<span data-ttu-id="ae71c-483">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="ae71c-484">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ae71c-485">`-np|--no-pagemodel`-Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ae71c-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ae71c-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ae71c-486">**viewimports**</span></span>

<span data-ttu-id="ae71c-487">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="ae71c-488">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ae71c-489">**web**</span><span class="sxs-lookup"><span data-stu-id="ae71c-489">**web**</span></span>

<span data-ttu-id="ae71c-490">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ae71c-491">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-492">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae71c-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ae71c-493">Ta opcja ma zastosowanie tylko `IndividualAuth` wtedy `OrganizationalAuth` , gdy lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="ae71c-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="ae71c-494">**MVC, webapp**</span><span class="sxs-lookup"><span data-stu-id="ae71c-494">**mvc, webapp**</span></span>

<span data-ttu-id="ae71c-495">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ae71c-496">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ae71c-496">The possible values are:</span></span>

- <span data-ttu-id="ae71c-497">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ae71c-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ae71c-498">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="ae71c-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ae71c-499">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ae71c-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ae71c-500">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ae71c-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ae71c-501">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="ae71c-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ae71c-502">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae71c-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ae71c-503">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ae71c-504">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-505">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ae71c-506">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ae71c-507">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-508">`-rp|--reset-password-policy-id <ID>`— Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ae71c-509">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-510">`-ep|--edit-profile-policy-id <ID>`-Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ae71c-511">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-512">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ae71c-513">Używanie z `SingleOrg` usługą `MultiOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ae71c-514">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ae71c-515">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ae71c-516">Użyj z `IndividualB2C`, `SingleOrg`lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ae71c-517">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ae71c-518">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ae71c-519">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-520">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ae71c-521">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ae71c-522">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-523">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ae71c-524">`--callback-path <PATH>`-Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ae71c-525">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-526">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ae71c-527">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ae71c-528">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ae71c-529">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ae71c-530">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae71c-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ae71c-531">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane `Startup.Configure`do.</span><span class="sxs-lookup"><span data-stu-id="ae71c-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ae71c-532">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C` `SingleOrg`, gdy, `MultiOrg` , lub nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="ae71c-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ae71c-533">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ae71c-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ae71c-534">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-535">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-536">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="ae71c-536">**webapi**</span></span>

<span data-ttu-id="ae71c-537">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ae71c-538">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ae71c-538">The possible values are:</span></span>

- <span data-ttu-id="ae71c-539">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ae71c-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ae71c-540">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ae71c-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ae71c-541">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ae71c-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ae71c-542">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae71c-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ae71c-543">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ae71c-544">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-545">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ae71c-546">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ae71c-547">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-548">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ae71c-549">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-550">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ae71c-551">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ae71c-552">Używanie z `IndividualB2C` usługą `SingleOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-553">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ae71c-554">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ae71c-555">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-556">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ae71c-557">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ae71c-558">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-559">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ae71c-560">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ae71c-561">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ae71c-562">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ae71c-563">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae71c-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ae71c-564">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane `Startup.Configure`do.</span><span class="sxs-lookup"><span data-stu-id="ae71c-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ae71c-565">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C` `SingleOrg`, gdy, `MultiOrg` , lub nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="ae71c-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ae71c-566">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ae71c-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ae71c-567">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-568">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ae71c-569">**globaljson**</span></span>

<span data-ttu-id="ae71c-570">`--sdk-version <VERSION_NUMBER>`-Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ae71c-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ae71c-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ae71c-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ae71c-572">**konsole, kątowe, reagowanie, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="ae71c-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="ae71c-573">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ae71c-574">**classlib**</span></span>

<span data-ttu-id="ae71c-575">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ae71c-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ae71c-576">Wartości: `netcoreapp2.1` aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard2.0` utworzyć bibliotekę klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ae71c-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ae71c-577">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ae71c-578">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ae71c-579">**mstest, xunit**</span></span>

<span data-ttu-id="ae71c-580">`-p|--enable-pack`— Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ae71c-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ae71c-581">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ae71c-582">**globaljson**</span></span>

<span data-ttu-id="ae71c-583">`--sdk-version <VERSION_NUMBER>`-Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ae71c-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ae71c-584">**web**</span><span class="sxs-lookup"><span data-stu-id="ae71c-584">**web**</span></span>

<span data-ttu-id="ae71c-585">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ae71c-586">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-587">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae71c-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ae71c-588">Ta opcja ma zastosowanie tylko `IndividualAuth` wtedy `OrganizationalAuth` , gdy lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="ae71c-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="ae71c-589">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="ae71c-589">**webapi**</span></span>

<span data-ttu-id="ae71c-590">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ae71c-591">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ae71c-591">The possible values are:</span></span>

- <span data-ttu-id="ae71c-592">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ae71c-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ae71c-593">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ae71c-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ae71c-594">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ae71c-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ae71c-595">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae71c-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ae71c-596">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ae71c-597">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-598">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ae71c-599">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ae71c-600">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-601">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ae71c-602">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-603">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ae71c-604">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ae71c-605">Używanie z `IndividualB2C` usługą `SingleOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-606">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ae71c-607">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ae71c-608">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-609">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ae71c-610">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ae71c-611">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-612">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ae71c-613">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ae71c-614">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ae71c-615">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ae71c-616">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ae71c-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ae71c-617">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-618">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-619">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae71c-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ae71c-620">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane `Startup.Configure`do.</span><span class="sxs-lookup"><span data-stu-id="ae71c-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ae71c-621">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C` `SingleOrg`, gdy, `MultiOrg` , lub nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="ae71c-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ae71c-622">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="ae71c-622">**mvc, razor**</span></span>

<span data-ttu-id="ae71c-623">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ae71c-624">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ae71c-624">The possible values are:</span></span>

- <span data-ttu-id="ae71c-625">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ae71c-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ae71c-626">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="ae71c-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ae71c-627">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ae71c-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ae71c-628">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ae71c-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ae71c-629">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="ae71c-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ae71c-630">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae71c-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ae71c-631">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ae71c-632">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-633">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ae71c-634">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ae71c-635">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-636">`-rp|--reset-password-policy-id <ID>`— Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ae71c-637">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-638">`-ep|--edit-profile-policy-id <ID>`-Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ae71c-639">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-640">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ae71c-641">Używanie z `SingleOrg` usługą `MultiOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ae71c-642">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ae71c-643">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ae71c-644">Użyj z `IndividualB2C`, `SingleOrg`lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ae71c-645">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ae71c-646">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ae71c-647">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-648">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ae71c-649">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ae71c-650">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-651">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ae71c-652">`--callback-path <PATH>`-Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ae71c-653">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-654">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ae71c-655">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ae71c-656">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ae71c-657">`--exclude-launch-settings`-Exclude *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ae71c-658">`--use-browserlink`-Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ae71c-659">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ae71c-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ae71c-660">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-661">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-662">`--no-https`-Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae71c-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ae71c-663">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane `Startup.Configure`do.</span><span class="sxs-lookup"><span data-stu-id="ae71c-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ae71c-664">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C` `SingleOrg`, gdy, `MultiOrg` , lub nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="ae71c-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ae71c-665">**stronic**</span><span class="sxs-lookup"><span data-stu-id="ae71c-665">**page**</span></span>

<span data-ttu-id="ae71c-666">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="ae71c-667">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ae71c-668">`-np|--no-pagemodel`-Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ae71c-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ae71c-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ae71c-669">**viewimports**</span></span>

<span data-ttu-id="ae71c-670">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="ae71c-671">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ae71c-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ae71c-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="ae71c-673">**konsole, kątowe, reagowanie, reactredux**</span><span class="sxs-lookup"><span data-stu-id="ae71c-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="ae71c-674">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ae71c-675">**classlib**</span></span>

<span data-ttu-id="ae71c-676">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ae71c-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ae71c-677">Wartości: `netcoreapp2.0` aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard2.0` utworzyć bibliotekę klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ae71c-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ae71c-678">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ae71c-679">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ae71c-680">**mstest, xunit**</span></span>

<span data-ttu-id="ae71c-681">`-p|--enable-pack`— Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ae71c-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ae71c-682">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ae71c-683">**globaljson**</span></span>

<span data-ttu-id="ae71c-684">`--sdk-version <VERSION_NUMBER>`-Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ae71c-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ae71c-685">**web**</span><span class="sxs-lookup"><span data-stu-id="ae71c-685">**web**</span></span>

<span data-ttu-id="ae71c-686">`--use-launch-settings`-Zawiera *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ae71c-687">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-688">**WebApi**</span><span class="sxs-lookup"><span data-stu-id="ae71c-688">**webapi**</span></span>

<span data-ttu-id="ae71c-689">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ae71c-690">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ae71c-690">The possible values are:</span></span>

- <span data-ttu-id="ae71c-691">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ae71c-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ae71c-692">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ae71c-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ae71c-693">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ae71c-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ae71c-694">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae71c-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ae71c-695">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ae71c-696">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-697">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ae71c-698">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ae71c-699">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-700">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ae71c-701">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-702">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ae71c-703">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ae71c-704">Używanie z `IndividualB2C` usługą `SingleOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-705">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ae71c-706">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ae71c-707">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-708">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ae71c-709">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ae71c-710">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-711">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ae71c-712">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ae71c-713">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ae71c-714">`--use-launch-settings`-Zawiera *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ae71c-715">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ae71c-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ae71c-716">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-717">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-718">**MVC, Razor**</span><span class="sxs-lookup"><span data-stu-id="ae71c-718">**mvc, razor**</span></span>

<span data-ttu-id="ae71c-719">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ae71c-720">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ae71c-720">The possible values are:</span></span>

- <span data-ttu-id="ae71c-721">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ae71c-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ae71c-722">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="ae71c-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ae71c-723">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ae71c-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ae71c-724">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ae71c-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ae71c-725">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="ae71c-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ae71c-726">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae71c-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ae71c-727">`--aad-b2c-instance <INSTANCE>`— Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ae71c-728">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-729">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ae71c-730">`-ssp|--susi-policy-id <ID>`— Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ae71c-731">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-732">`-rp|--reset-password-policy-id <ID>`— Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ae71c-733">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-734">`-ep|--edit-profile-policy-id <ID>`-Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ae71c-735">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-736">`--aad-instance <INSTANCE>`— Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ae71c-737">Używanie z `SingleOrg` usługą `MultiOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ae71c-738">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ae71c-739">`--client-id <ID>`— Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ae71c-740">Użyj z `IndividualB2C`, `SingleOrg`lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ae71c-741">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ae71c-742">`--domain <DOMAIN>`— Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ae71c-743">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-744">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ae71c-745">`--tenant-id <ID>`— Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ae71c-746">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ae71c-747">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ae71c-748">`--callback-path <PATH>`-Ścieżka żądania w ścieżce podstawowej aplikacji URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ae71c-749">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ae71c-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ae71c-750">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ae71c-751">`-r|--org-read-access`-Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ae71c-752">`SingleOrg` Dotyczy`MultiOrg` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ae71c-753">`--use-launch-settings`-Zawiera *profilu launchsettings. JSON* w wygenerowanym wyjściu szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ae71c-754">`--use-browserlink`-Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ae71c-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ae71c-755">`-uld|--use-local-db`-Określa LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ae71c-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ae71c-756">`Individual` Dotyczy`IndividualB2C` tylko uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ae71c-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ae71c-757">`--no-restore`— Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ae71c-758">**stronic**</span><span class="sxs-lookup"><span data-stu-id="ae71c-758">**page**</span></span>

<span data-ttu-id="ae71c-759">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ae71c-760">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ae71c-761">`-np|--no-pagemodel`-Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ae71c-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ae71c-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ae71c-762">**viewimports**</span></span>

<span data-ttu-id="ae71c-763">`-na|--namespace <NAMESPACE_NAME>`-Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ae71c-764">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ae71c-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ae71c-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ae71c-766">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="ae71c-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="ae71c-767">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ae71c-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ae71c-768">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ae71c-769">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ae71c-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ae71c-770">**classlib**</span></span>

<span data-ttu-id="ae71c-771">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ae71c-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ae71c-772">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="ae71c-773">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="ae71c-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="ae71c-774">**mvc**</span></span>

<span data-ttu-id="ae71c-775">`-f|--framework <FRAMEWORK>`-Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ae71c-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ae71c-776">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ae71c-777">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ae71c-778">`-au|--auth <AUTHENTICATION_TYPE>`— Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ae71c-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ae71c-779">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="ae71c-780">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-780">The default value is `None`.</span></span>

<span data-ttu-id="ae71c-781">`-uld|--use-local-db`-Określa, czy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ae71c-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="ae71c-782">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-782">Values: `true` or `false`.</span></span> <span data-ttu-id="ae71c-783">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ae71c-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ae71c-784">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ae71c-784">Examples</span></span>

<span data-ttu-id="ae71c-785">Utwórz projekt C# aplikacji konsolowej, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="ae71c-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="ae71c-786">Utwórz projekt F# aplikacji konsolowej w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ae71c-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="ae71c-787">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku wersji zestaw .NET Core SDK 2,0 lub nowszej):</span><span class="sxs-lookup"><span data-stu-id="ae71c-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="ae71c-788">Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="ae71c-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="ae71c-789">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="ae71c-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="ae71c-790">Wyświetl listę wszystkich szablonów dostępnych dla MVC:</span><span class="sxs-lookup"><span data-stu-id="ae71c-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="ae71c-791">Wyświetl listę wszystkich szablonów pasujących do podciągu.</span><span class="sxs-lookup"><span data-stu-id="ae71c-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="ae71c-792">Nie znaleziono dokładnego dopasowania, więc Dopasowywanie podciągów działa w odniesieniu do kolumn krótkich nazw i nazw.</span><span class="sxs-lookup"><span data-stu-id="ae71c-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="ae71c-793">Podjęto próbę wywołania szablonu zgodnego z parametrem *ng*.</span><span class="sxs-lookup"><span data-stu-id="ae71c-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="ae71c-794">Jeśli nie można ustalić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są dopasowań częściowych.</span><span class="sxs-lookup"><span data-stu-id="ae71c-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="ae71c-795">Zainstaluj wersję 2,0 szablonów aplikacji jednostronicowych dla ASP.NET Core (opcja polecenia dostępna tylko dla zestaw .NET Core SDK 1,1 i nowszych wersji):</span><span class="sxs-lookup"><span data-stu-id="ae71c-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="ae71c-796">Utwórz plik *Global. JSON* w bieżącym katalogu, ustawiając wersję zestawu SDK na 2.0.0 (dostępne tylko w zestaw .NET Core SDK 2,0 lub nowszych wersjach):</span><span class="sxs-lookup"><span data-stu-id="ae71c-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="ae71c-797">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae71c-797">See also</span></span>

- [<span data-ttu-id="ae71c-798">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="ae71c-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="ae71c-799">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="ae71c-799">Create a custom template for dotnet new</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="ae71c-800">dotnet/dotnet-Template-przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="ae71c-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="ae71c-801">Dostępne szablony dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="ae71c-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
