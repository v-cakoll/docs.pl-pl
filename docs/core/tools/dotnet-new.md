---
title: nowe polecenia DotNet
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core, na podstawie określonego szablonu.
ms.date: 05/06/2019
ms.openlocfilehash: f8bc8cb59ae6e421f4e9bd05925376399939056d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878313"
---
# <a name="dotnet-new"></a><span data-ttu-id="78c7e-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="78c7e-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="78c7e-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="78c7e-104">Name</span></span>

<span data-ttu-id="78c7e-105">`dotnet new` -Tworzy nowy projekt, pliku konfiguracji lub rozwiązania na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="78c7e-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="78c7e-106">Synopsis</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="78c7e-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="78c7e-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="78c7e-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="78c7e-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="78c7e-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="78c7e-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="78c7e-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="78c7e-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="78c7e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="78c7e-111">Description</span></span>

<span data-ttu-id="78c7e-112">`dotnet new` Polecenia oferuje wygodny sposób zainicjować prawidłowy projekt .NET Core.</span><span class="sxs-lookup"><span data-stu-id="78c7e-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="78c7e-113">Wywołuje polecenie [aparatu szablonów](https://github.com/dotnet/templating) do tworzenia artefaktów na dysku, na podstawie określonego szablonu i opcje.</span><span class="sxs-lookup"><span data-stu-id="78c7e-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="78c7e-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="78c7e-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="78c7e-115">Szablon do utworzenia wystąpienia podczas wywoływania polecenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="78c7e-116">Każdy szablon może być określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="78c7e-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="78c7e-117">Aby uzyskać więcej informacji, zobacz [opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="78c7e-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="78c7e-118">Jeśli `TEMPLATE` wartość nie jest identyczny z tekstem **szablony** lub **krótką nazwę** kolumnie dopasowania podciągu odbywa się na tych dwóch kolumn.</span><span class="sxs-lookup"><span data-stu-id="78c7e-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="78c7e-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="78c7e-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="78c7e-120">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-120">The command contains a default list of templates.</span></span> <span data-ttu-id="78c7e-121">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="78c7e-122">W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="78c7e-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="78c7e-123">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="78c7e-124">Szablony</span><span class="sxs-lookup"><span data-stu-id="78c7e-124">Templates</span></span>                                    | <span data-ttu-id="78c7e-125">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="78c7e-125">Short Name</span></span>        | <span data-ttu-id="78c7e-126">Język</span><span class="sxs-lookup"><span data-stu-id="78c7e-126">Language</span></span>     | <span data-ttu-id="78c7e-127">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="78c7e-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="78c7e-128">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="78c7e-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="78c7e-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-129">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-130">Typowe/konsoli</span><span class="sxs-lookup"><span data-stu-id="78c7e-130">Common/Console</span></span>                        |
| <span data-ttu-id="78c7e-131">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="78c7e-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="78c7e-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-132">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-133">Typowe/biblioteki</span><span class="sxs-lookup"><span data-stu-id="78c7e-133">Common/Library</span></span>                        |
| <span data-ttu-id="78c7e-134">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="78c7e-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="78c7e-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-135">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-136">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="78c7e-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="78c7e-137">NUnit 3 Test Project</span><span class="sxs-lookup"><span data-stu-id="78c7e-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="78c7e-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-138">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-139">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="78c7e-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="78c7e-140">Element testu NUnit 3</span><span class="sxs-lookup"><span data-stu-id="78c7e-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="78c7e-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-141">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-142">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="78c7e-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="78c7e-143">xUnit Test Project</span><span class="sxs-lookup"><span data-stu-id="78c7e-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="78c7e-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-144">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-145">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="78c7e-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="78c7e-146">Strona razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="78c7e-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-147">[C#]</span></span>         | <span data-ttu-id="78c7e-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78c7e-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="78c7e-149">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="78c7e-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="78c7e-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-150">[C#]</span></span>         | <span data-ttu-id="78c7e-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78c7e-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="78c7e-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="78c7e-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="78c7e-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-153">[C#]</span></span>         | <span data-ttu-id="78c7e-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78c7e-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="78c7e-155">ASP.NET Core — puste</span><span class="sxs-lookup"><span data-stu-id="78c7e-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="78c7e-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-156">[C#], F#</span></span>     | <span data-ttu-id="78c7e-157">W sieci Web lub są puste</span><span class="sxs-lookup"><span data-stu-id="78c7e-157">Web/Empty</span></span>                             |
| <span data-ttu-id="78c7e-158">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="78c7e-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="78c7e-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-159">[C#], F#</span></span>     | <span data-ttu-id="78c7e-160">W sieci Web/MVC</span><span class="sxs-lookup"><span data-stu-id="78c7e-160">Web/MVC</span></span>                               |
| <span data-ttu-id="78c7e-161">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78c7e-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="78c7e-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="78c7e-162">`webapp`, `razor`</span></span> | <span data-ttu-id="78c7e-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-163">[C#]</span></span>         | <span data-ttu-id="78c7e-164">Strony sieci Web/MVC/Razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="78c7e-165">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="78c7e-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="78c7e-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-166">[C#]</span></span>         | <span data-ttu-id="78c7e-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="78c7e-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="78c7e-168">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="78c7e-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="78c7e-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-169">[C#]</span></span>         | <span data-ttu-id="78c7e-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="78c7e-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="78c7e-171">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="78c7e-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="78c7e-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-172">[C#]</span></span>         | <span data-ttu-id="78c7e-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="78c7e-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="78c7e-174">Biblioteki klas razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="78c7e-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-175">[C#]</span></span>         | <span data-ttu-id="78c7e-176">Biblioteka klas w sieci Web/Razor/biblioteki/Razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="78c7e-177">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78c7e-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="78c7e-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-178">[C#], F#</span></span>     | <span data-ttu-id="78c7e-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="78c7e-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="78c7e-180">global.json file</span><span class="sxs-lookup"><span data-stu-id="78c7e-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="78c7e-181">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-181">Config</span></span>                                |
| <span data-ttu-id="78c7e-182">NuGet Config</span><span class="sxs-lookup"><span data-stu-id="78c7e-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="78c7e-183">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-183">Config</span></span>                                |
| <span data-ttu-id="78c7e-184">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="78c7e-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="78c7e-185">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-185">Config</span></span>                                |
| <span data-ttu-id="78c7e-186">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="78c7e-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="78c7e-187">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="78c7e-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="78c7e-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="78c7e-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="78c7e-189">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-189">The command contains a default list of templates.</span></span> <span data-ttu-id="78c7e-190">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="78c7e-191">W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="78c7e-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="78c7e-192">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="78c7e-193">Szablony</span><span class="sxs-lookup"><span data-stu-id="78c7e-193">Templates</span></span>                                    | <span data-ttu-id="78c7e-194">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="78c7e-194">Short Name</span></span>      | <span data-ttu-id="78c7e-195">Język</span><span class="sxs-lookup"><span data-stu-id="78c7e-195">Language</span></span>     | <span data-ttu-id="78c7e-196">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="78c7e-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="78c7e-197">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="78c7e-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="78c7e-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-198">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-199">Typowe/konsoli</span><span class="sxs-lookup"><span data-stu-id="78c7e-199">Common/Console</span></span>                        |
| <span data-ttu-id="78c7e-200">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="78c7e-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="78c7e-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-201">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-202">Typowe/biblioteki</span><span class="sxs-lookup"><span data-stu-id="78c7e-202">Common/Library</span></span>                        |
| <span data-ttu-id="78c7e-203">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="78c7e-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="78c7e-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-204">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-205">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="78c7e-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="78c7e-206">xUnit Test Project</span><span class="sxs-lookup"><span data-stu-id="78c7e-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="78c7e-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-207">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-208">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="78c7e-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="78c7e-209">Strona razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="78c7e-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-210">[C#]</span></span>         | <span data-ttu-id="78c7e-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78c7e-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="78c7e-212">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="78c7e-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="78c7e-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-213">[C#]</span></span>         | <span data-ttu-id="78c7e-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78c7e-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="78c7e-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="78c7e-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="78c7e-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-216">[C#]</span></span>         | <span data-ttu-id="78c7e-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78c7e-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="78c7e-218">ASP.NET Core — puste</span><span class="sxs-lookup"><span data-stu-id="78c7e-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="78c7e-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-219">[C#], F#</span></span>     | <span data-ttu-id="78c7e-220">W sieci Web lub są puste</span><span class="sxs-lookup"><span data-stu-id="78c7e-220">Web/Empty</span></span>                             |
| <span data-ttu-id="78c7e-221">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="78c7e-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="78c7e-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-222">[C#], F#</span></span>     | <span data-ttu-id="78c7e-223">W sieci Web/MVC</span><span class="sxs-lookup"><span data-stu-id="78c7e-223">Web/MVC</span></span>                               |
| <span data-ttu-id="78c7e-224">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78c7e-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="78c7e-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-225">[C#]</span></span>         | <span data-ttu-id="78c7e-226">Strony sieci Web/MVC/Razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="78c7e-227">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="78c7e-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="78c7e-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-228">[C#]</span></span>         | <span data-ttu-id="78c7e-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="78c7e-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="78c7e-230">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="78c7e-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="78c7e-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-231">[C#]</span></span>         | <span data-ttu-id="78c7e-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="78c7e-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="78c7e-233">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="78c7e-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="78c7e-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-234">[C#]</span></span>         | <span data-ttu-id="78c7e-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="78c7e-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="78c7e-236">Biblioteki klas razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="78c7e-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-237">[C#]</span></span>         | <span data-ttu-id="78c7e-238">Biblioteka klas w sieci Web/Razor/biblioteki/Razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="78c7e-239">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78c7e-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="78c7e-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-240">[C#], F#</span></span>     | <span data-ttu-id="78c7e-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="78c7e-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="78c7e-242">global.json file</span><span class="sxs-lookup"><span data-stu-id="78c7e-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="78c7e-243">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-243">Config</span></span>                                |
| <span data-ttu-id="78c7e-244">NuGet Config</span><span class="sxs-lookup"><span data-stu-id="78c7e-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="78c7e-245">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-245">Config</span></span>                                |
| <span data-ttu-id="78c7e-246">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="78c7e-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="78c7e-247">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-247">Config</span></span>                                |
| <span data-ttu-id="78c7e-248">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="78c7e-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="78c7e-249">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="78c7e-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="78c7e-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="78c7e-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="78c7e-251">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-251">The command contains a default list of templates.</span></span> <span data-ttu-id="78c7e-252">Użyj `dotnet new -l` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="78c7e-253">W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="78c7e-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="78c7e-254">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="78c7e-255">Szablony</span><span class="sxs-lookup"><span data-stu-id="78c7e-255">Templates</span></span>                                    | <span data-ttu-id="78c7e-256">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="78c7e-256">Short Name</span></span>    | <span data-ttu-id="78c7e-257">Język</span><span class="sxs-lookup"><span data-stu-id="78c7e-257">Language</span></span>     | <span data-ttu-id="78c7e-258">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="78c7e-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="78c7e-259">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="78c7e-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="78c7e-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-260">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-261">Typowe/konsoli</span><span class="sxs-lookup"><span data-stu-id="78c7e-261">Common/Console</span></span>      |
| <span data-ttu-id="78c7e-262">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="78c7e-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="78c7e-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-263">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-264">Typowe/biblioteki</span><span class="sxs-lookup"><span data-stu-id="78c7e-264">Common/Library</span></span>      |
| <span data-ttu-id="78c7e-265">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="78c7e-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="78c7e-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-266">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-267">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="78c7e-267">Test/MSTest</span></span>         |
| <span data-ttu-id="78c7e-268">xUnit Test Project</span><span class="sxs-lookup"><span data-stu-id="78c7e-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="78c7e-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="78c7e-269">[C#], F#, VB</span></span> | <span data-ttu-id="78c7e-270">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="78c7e-270">Test/xUnit</span></span>          |
| <span data-ttu-id="78c7e-271">ASP.NET Core — puste</span><span class="sxs-lookup"><span data-stu-id="78c7e-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="78c7e-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-272">[C#], F#</span></span>     | <span data-ttu-id="78c7e-273">W sieci Web lub są puste</span><span class="sxs-lookup"><span data-stu-id="78c7e-273">Web/Empty</span></span>           |
| <span data-ttu-id="78c7e-274">Aplikacja sieci Web platformy ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="78c7e-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="78c7e-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-275">[C#], F#</span></span>     | <span data-ttu-id="78c7e-276">W sieci Web/MVC</span><span class="sxs-lookup"><span data-stu-id="78c7e-276">Web/MVC</span></span>             |
| <span data-ttu-id="78c7e-277">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78c7e-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="78c7e-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-278">[C#]</span></span>         | <span data-ttu-id="78c7e-279">Strony sieci Web/MVC/Razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="78c7e-280">Platforma ASP.NET Core przy użyciu usługi Angular</span><span class="sxs-lookup"><span data-stu-id="78c7e-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="78c7e-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-281">[C#]</span></span>         | <span data-ttu-id="78c7e-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="78c7e-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="78c7e-283">Platforma ASP.NET Core z użyciem biblioteki React.js</span><span class="sxs-lookup"><span data-stu-id="78c7e-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="78c7e-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-284">[C#]</span></span>         | <span data-ttu-id="78c7e-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="78c7e-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="78c7e-286">Platforma ASP.NET Core z użyciem biblioteki React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="78c7e-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="78c7e-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-287">[C#]</span></span>         | <span data-ttu-id="78c7e-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="78c7e-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="78c7e-289">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78c7e-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="78c7e-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-290">[C#], F#</span></span>     | <span data-ttu-id="78c7e-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="78c7e-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="78c7e-292">global.json file</span><span class="sxs-lookup"><span data-stu-id="78c7e-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="78c7e-293">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-293">Config</span></span>              |
| <span data-ttu-id="78c7e-294">Nuget Config</span><span class="sxs-lookup"><span data-stu-id="78c7e-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="78c7e-295">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-295">Config</span></span>              |
| <span data-ttu-id="78c7e-296">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="78c7e-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="78c7e-297">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-297">Config</span></span>              |
| <span data-ttu-id="78c7e-298">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="78c7e-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="78c7e-299">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="78c7e-299">Solution</span></span>            |
| <span data-ttu-id="78c7e-300">Strona razor</span><span class="sxs-lookup"><span data-stu-id="78c7e-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="78c7e-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78c7e-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="78c7e-302">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="78c7e-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="78c7e-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78c7e-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="78c7e-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="78c7e-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="78c7e-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="78c7e-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="78c7e-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="78c7e-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="78c7e-307">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-307">The command contains a default list of templates.</span></span> <span data-ttu-id="78c7e-308">Użyj `dotnet new -all` Aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="78c7e-309">W poniższej tabeli przedstawiono szablony, które są zainstalowane przy użyciu zestawu .NET Core SDK 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="78c7e-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="78c7e-310">Domyślny język dla szablonu jest wyświetlany w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="78c7e-311">Szablony</span><span class="sxs-lookup"><span data-stu-id="78c7e-311">Templates</span></span>            | <span data-ttu-id="78c7e-312">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="78c7e-312">Short Name</span></span>    | <span data-ttu-id="78c7e-313">Język</span><span class="sxs-lookup"><span data-stu-id="78c7e-313">Language</span></span> | <span data-ttu-id="78c7e-314">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="78c7e-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="78c7e-315">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="78c7e-315">Console Application</span></span>  | `console`     | <span data-ttu-id="78c7e-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-316">[C#], F#</span></span> | <span data-ttu-id="78c7e-317">Typowe/konsoli</span><span class="sxs-lookup"><span data-stu-id="78c7e-317">Common/Console</span></span> |
| <span data-ttu-id="78c7e-318">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="78c7e-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="78c7e-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-319">[C#], F#</span></span> | <span data-ttu-id="78c7e-320">Typowe/biblioteki</span><span class="sxs-lookup"><span data-stu-id="78c7e-320">Common/Library</span></span> |
| <span data-ttu-id="78c7e-321">Projekt testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="78c7e-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="78c7e-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-322">[C#], F#</span></span> | <span data-ttu-id="78c7e-323">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="78c7e-323">Test/MSTest</span></span>    |
| <span data-ttu-id="78c7e-324">xUnit Test Project</span><span class="sxs-lookup"><span data-stu-id="78c7e-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="78c7e-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-325">[C#], F#</span></span> | <span data-ttu-id="78c7e-326">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="78c7e-326">Test/xUnit</span></span>     |
| <span data-ttu-id="78c7e-327">ASP.NET Core — puste</span><span class="sxs-lookup"><span data-stu-id="78c7e-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="78c7e-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-328">[C#]</span></span>     | <span data-ttu-id="78c7e-329">W sieci Web lub są puste</span><span class="sxs-lookup"><span data-stu-id="78c7e-329">Web/Empty</span></span>      |
| <span data-ttu-id="78c7e-330">Aplikacja sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78c7e-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="78c7e-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="78c7e-331">[C#], F#</span></span> | <span data-ttu-id="78c7e-332">W sieci Web/MVC</span><span class="sxs-lookup"><span data-stu-id="78c7e-332">Web/MVC</span></span>        |
| <span data-ttu-id="78c7e-333">Interfejs API sieci Web platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78c7e-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="78c7e-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="78c7e-334">[C#]</span></span>     | <span data-ttu-id="78c7e-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="78c7e-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="78c7e-336">Nuget Config</span><span class="sxs-lookup"><span data-stu-id="78c7e-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="78c7e-337">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-337">Config</span></span>         |
| <span data-ttu-id="78c7e-338">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="78c7e-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="78c7e-339">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="78c7e-339">Config</span></span>         |
| <span data-ttu-id="78c7e-340">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="78c7e-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="78c7e-341">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="78c7e-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="78c7e-342">Opcje</span><span class="sxs-lookup"><span data-stu-id="78c7e-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="78c7e-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="78c7e-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="78c7e-344">Wyświetla podsumowanie co się stanie, jeśli dane polecenie zostały uruchomione, jeśli mogłoby spowodować tworzenie szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="78c7e-345">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="78c7e-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="78c7e-346">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="78c7e-347">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-347">Prints out help for the command.</span></span> <span data-ttu-id="78c7e-348">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="78c7e-349">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="78c7e-350">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="78c7e-351">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="78c7e-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="78c7e-352">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="78c7e-353">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="78c7e-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="78c7e-354">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="78c7e-355">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="78c7e-356">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="78c7e-357">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-357">The language of the template to create.</span></span> <span data-ttu-id="78c7e-358">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="78c7e-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="78c7e-359">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="78c7e-360">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="78c7e-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="78c7e-361">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="78c7e-362">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="78c7e-362">The name for the created output.</span></span> <span data-ttu-id="78c7e-363">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="78c7e-364">Określa źródła pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="78c7e-365">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="78c7e-365">Location to place the generated output.</span></span> <span data-ttu-id="78c7e-366">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="78c7e-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="78c7e-367">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-367">Filters templates based on available types.</span></span> <span data-ttu-id="78c7e-368">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="78c7e-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="78c7e-369">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="78c7e-370">Przy wykluczaniu `<PATH|NUGET_ID>` wartości, wszystkie pakiety z aktualnie zainstalowanych szablonów i ich skojarzone szablony są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="78c7e-371">Aby odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="78c7e-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="78c7e-372">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="78c7e-373">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="78c7e-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="78c7e-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="78c7e-375">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="78c7e-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="78c7e-376">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="78c7e-377">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-377">Prints out help for the command.</span></span> <span data-ttu-id="78c7e-378">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="78c7e-379">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="78c7e-380">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="78c7e-381">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="78c7e-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="78c7e-382">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="78c7e-383">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="78c7e-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="78c7e-384">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="78c7e-385">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="78c7e-386">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="78c7e-387">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-387">The language of the template to create.</span></span> <span data-ttu-id="78c7e-388">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="78c7e-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="78c7e-389">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="78c7e-390">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="78c7e-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="78c7e-391">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="78c7e-392">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="78c7e-392">The name for the created output.</span></span> <span data-ttu-id="78c7e-393">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="78c7e-394">Określa źródła pakietów NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="78c7e-395">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="78c7e-395">Location to place the generated output.</span></span> <span data-ttu-id="78c7e-396">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="78c7e-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="78c7e-397">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-397">Filters templates based on available types.</span></span> <span data-ttu-id="78c7e-398">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="78c7e-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="78c7e-399">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="78c7e-400">Aby odinstalować przy użyciu szablonu `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="78c7e-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="78c7e-401">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="78c7e-402">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="78c7e-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="78c7e-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="78c7e-404">Wymusza zawartość do wygenerowania nawet wtedy, gdy go zmienić istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="78c7e-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="78c7e-405">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="78c7e-406">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-406">Prints out help for the command.</span></span> <span data-ttu-id="78c7e-407">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="78c7e-408">Instaluje pakiet źródła lub szablonu z `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="78c7e-409">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, należy określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="78c7e-410">Domyślnie `dotnet new` przekazuje \* wersję, która reprezentuje ostatnią wersję stabilny pakiet.</span><span class="sxs-lookup"><span data-stu-id="78c7e-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="78c7e-411">Zobacz przykład w [przykłady](#examples) sekcji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="78c7e-412">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [szablonów niestandardowych dla platformy dotnet nowe](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="78c7e-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="78c7e-413">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="78c7e-414">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="78c7e-415">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="78c7e-416">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-416">The language of the template to create.</span></span> <span data-ttu-id="78c7e-417">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="78c7e-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="78c7e-418">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="78c7e-419">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="78c7e-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="78c7e-420">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="78c7e-421">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="78c7e-421">The name for the created output.</span></span> <span data-ttu-id="78c7e-422">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="78c7e-423">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="78c7e-423">Location to place the generated output.</span></span> <span data-ttu-id="78c7e-424">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="78c7e-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="78c7e-425">Filtrowanie na podstawie typów dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-425">Filters templates based on available types.</span></span> <span data-ttu-id="78c7e-426">Wstępnie zdefiniowane wartości to "Projekt", "element" lub "other".</span><span class="sxs-lookup"><span data-stu-id="78c7e-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="78c7e-427">Odinstalowuje pakiet źródła lub szablonu w `PATH` lub `NUGET_ID` podane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="78c7e-428">Aby odinstalować szablonu korzystanie ze źródła `PATH`, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="78c7e-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="78c7e-429">Na przykład *C:/Users/\<użytkownika > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z zawierającego folder nie będzie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="78c7e-430">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="78c7e-431">Jeśli nie można określić `PATH` lub `NUGET_ID` argument niezbędnych do odinstalowania szablon systemem `dotnet new --uninstall` bez argumentu, spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów i argument, trzeba je odinstalować.</span><span class="sxs-lookup"><span data-stu-id="78c7e-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="78c7e-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="78c7e-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="78c7e-433">Przedstawia wszystkie szablony dla określonego typu projektu, podczas uruchamiania w kontekście `dotnet new` tylko polecenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="78c7e-434">Podczas uruchamiania w kontekście określonego szablonu, takie jak `dotnet new web -all`, `-all` jest interpretowany jako flagi tworzenia force.</span><span class="sxs-lookup"><span data-stu-id="78c7e-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="78c7e-435">Jest to wymagane, gdy projekt zawiera już katalog wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="78c7e-436">Drukuje pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-436">Prints out help for the command.</span></span> <span data-ttu-id="78c7e-437">Może być wywołana dla `dotnet new` polecenia sam lub dowolnego szablonu, takie jak `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="78c7e-438">Wyświetla listę szablonów zawierających określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="78c7e-439">Jeśli wywołany dla `dotnet new` polecenie wyświetla listę możliwych szablonów dostępnych dla danego katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="78c7e-440">Na przykład jeśli katalog zawiera już projekt, nie ma w niej wszystkie szablony projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="78c7e-441">Język szablonu w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-441">The language of the template to create.</span></span> <span data-ttu-id="78c7e-442">Język zaakceptowane, zależą od szablonu (Zobacz ustawienia domyślne w [argumenty](#arguments) sekcji).</span><span class="sxs-lookup"><span data-stu-id="78c7e-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="78c7e-443">Nie jest prawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="78c7e-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="78c7e-444">Interpretowanie niektóre powłoki `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="78c7e-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="78c7e-445">W takich przypadkach należy dołączyć wartość parametru języka, takich jak `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="78c7e-446">Nazwa utworzonej danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="78c7e-446">The name for the created output.</span></span> <span data-ttu-id="78c7e-447">Jeśli nazwa nie zostanie określona, jest używana nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="78c7e-448">Lokalizacja, aby umieścić wygenerowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="78c7e-448">Location to place the generated output.</span></span> <span data-ttu-id="78c7e-449">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="78c7e-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="78c7e-450">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="78c7e-450">Template options</span></span>

<span data-ttu-id="78c7e-451">Każdy szablon projektu może być dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="78c7e-451">Each project template may have additional options available.</span></span> <span data-ttu-id="78c7e-452">Szablony core są dostępne następujące opcje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="78c7e-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="78c7e-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="78c7e-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="78c7e-454">**console**</span><span class="sxs-lookup"><span data-stu-id="78c7e-454">**console**</span></span>

<span data-ttu-id="78c7e-455">`--langVersion <VERSION_NUMBER>` -Ustawia `LangVersion` właściwości w pliku utworzonego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="78c7e-456">Na przykład użyć `--langVersion 7.3` używać C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="78c7e-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="78c7e-457">Nieobsługiwane dla F#.</span><span class="sxs-lookup"><span data-stu-id="78c7e-457">Not supported for F#.</span></span>

<span data-ttu-id="78c7e-458">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-459">**platformy angular, react reactredux dla platformy**</span><span class="sxs-lookup"><span data-stu-id="78c7e-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="78c7e-460">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="78c7e-461">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-462">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="78c7e-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="78c7e-463">Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualAuth` lub `OrganizationalAuth` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="78c7e-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="78c7e-464">**razorclasslib**</span></span>

<span data-ttu-id="78c7e-465">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="78c7e-466">**classlib**</span></span>

<span data-ttu-id="78c7e-467">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="78c7e-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="78c7e-468">Wartości: `netcoreapp2.2` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="78c7e-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="78c7e-469">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="78c7e-470">`--langVersion <VERSION_NUMBER>` -Ustawia `LangVersion` właściwości w pliku utworzonego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="78c7e-471">Na przykład użyć `--langVersion 7.3` używać C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="78c7e-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="78c7e-472">Nieobsługiwane dla F#.</span><span class="sxs-lookup"><span data-stu-id="78c7e-472">Not supported for F#.</span></span>

<span data-ttu-id="78c7e-473">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="78c7e-474">**mstest, xunit**</span></span>

<span data-ttu-id="78c7e-475">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="78c7e-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="78c7e-476">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-477">**rozszerzenie nunit**</span><span class="sxs-lookup"><span data-stu-id="78c7e-477">**nunit**</span></span>

<span data-ttu-id="78c7e-478">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="78c7e-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="78c7e-479">Wartość domyślna to `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="78c7e-480">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="78c7e-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="78c7e-481">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-482">**page**</span><span class="sxs-lookup"><span data-stu-id="78c7e-482">**page**</span></span>

<span data-ttu-id="78c7e-483">`-na|--namespace <NAMESPACE_NAME>` -Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="78c7e-484">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="78c7e-485">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="78c7e-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="78c7e-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="78c7e-486">**viewimports**</span></span>

<span data-ttu-id="78c7e-487">`-na|--namespace <NAMESPACE_NAME>` -Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="78c7e-488">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="78c7e-489">**web**</span><span class="sxs-lookup"><span data-stu-id="78c7e-489">**web**</span></span>

<span data-ttu-id="78c7e-490">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="78c7e-491">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-492">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="78c7e-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="78c7e-493">Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualAuth` lub `OrganizationalAuth` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="78c7e-494">**MVC, aplikacji sieci Web**</span><span class="sxs-lookup"><span data-stu-id="78c7e-494">**mvc, webapp**</span></span>

<span data-ttu-id="78c7e-495">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="78c7e-496">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="78c7e-496">The possible values are:</span></span>

- <span data-ttu-id="78c7e-497">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="78c7e-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="78c7e-498">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="78c7e-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="78c7e-499">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="78c7e-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="78c7e-500">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="78c7e-501">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="78c7e-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="78c7e-502">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="78c7e-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="78c7e-503">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="78c7e-504">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-505">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="78c7e-506">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="78c7e-507">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-508">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="78c7e-509">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-510">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="78c7e-511">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-512">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="78c7e-513">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="78c7e-514">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="78c7e-515">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="78c7e-516">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="78c7e-517">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="78c7e-518">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="78c7e-519">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-520">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="78c7e-521">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="78c7e-522">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-523">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="78c7e-524">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="78c7e-525">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-526">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="78c7e-527">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="78c7e-528">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="78c7e-529">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="78c7e-530">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="78c7e-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="78c7e-531">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="78c7e-532">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="78c7e-533">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="78c7e-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="78c7e-534">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-535">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="78c7e-536">**webapi**</span></span>

<span data-ttu-id="78c7e-537">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="78c7e-538">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="78c7e-538">The possible values are:</span></span>

- <span data-ttu-id="78c7e-539">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="78c7e-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="78c7e-540">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="78c7e-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="78c7e-541">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="78c7e-542">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="78c7e-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="78c7e-543">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="78c7e-544">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-545">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="78c7e-546">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="78c7e-547">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-548">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="78c7e-549">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-550">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="78c7e-551">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="78c7e-552">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-553">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="78c7e-554">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="78c7e-555">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-556">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="78c7e-557">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="78c7e-558">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-559">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="78c7e-560">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="78c7e-561">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="78c7e-562">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="78c7e-563">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="78c7e-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="78c7e-564">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="78c7e-565">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="78c7e-566">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="78c7e-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="78c7e-567">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-568">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="78c7e-569">**globaljson**</span></span>

<span data-ttu-id="78c7e-570">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="78c7e-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="78c7e-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="78c7e-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="78c7e-572">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="78c7e-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="78c7e-573">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="78c7e-574">**classlib**</span></span>

<span data-ttu-id="78c7e-575">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="78c7e-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="78c7e-576">Wartości: `netcoreapp2.1` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="78c7e-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="78c7e-577">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="78c7e-578">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="78c7e-579">**mstest, xunit**</span></span>

<span data-ttu-id="78c7e-580">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="78c7e-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="78c7e-581">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="78c7e-582">**globaljson**</span></span>

<span data-ttu-id="78c7e-583">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="78c7e-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="78c7e-584">**web**</span><span class="sxs-lookup"><span data-stu-id="78c7e-584">**web**</span></span>

<span data-ttu-id="78c7e-585">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="78c7e-586">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-587">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="78c7e-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="78c7e-588">Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualAuth` lub `OrganizationalAuth` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="78c7e-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="78c7e-589">**webapi**</span></span>

<span data-ttu-id="78c7e-590">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="78c7e-591">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="78c7e-591">The possible values are:</span></span>

- <span data-ttu-id="78c7e-592">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="78c7e-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="78c7e-593">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="78c7e-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="78c7e-594">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="78c7e-595">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="78c7e-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="78c7e-596">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="78c7e-597">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-598">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="78c7e-599">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="78c7e-600">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-601">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="78c7e-602">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-603">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="78c7e-604">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="78c7e-605">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-606">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="78c7e-607">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="78c7e-608">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-609">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="78c7e-610">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="78c7e-611">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-612">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="78c7e-613">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="78c7e-614">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="78c7e-615">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="78c7e-616">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="78c7e-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="78c7e-617">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-618">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-619">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="78c7e-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="78c7e-620">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="78c7e-621">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="78c7e-622">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="78c7e-622">**mvc, razor**</span></span>

<span data-ttu-id="78c7e-623">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="78c7e-624">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="78c7e-624">The possible values are:</span></span>

- <span data-ttu-id="78c7e-625">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="78c7e-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="78c7e-626">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="78c7e-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="78c7e-627">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="78c7e-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="78c7e-628">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="78c7e-629">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="78c7e-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="78c7e-630">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="78c7e-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="78c7e-631">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="78c7e-632">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-633">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="78c7e-634">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="78c7e-635">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-636">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="78c7e-637">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-638">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="78c7e-639">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-640">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="78c7e-641">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="78c7e-642">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="78c7e-643">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="78c7e-644">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="78c7e-645">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="78c7e-646">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="78c7e-647">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-648">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="78c7e-649">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="78c7e-650">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-651">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="78c7e-652">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="78c7e-653">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-654">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="78c7e-655">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="78c7e-656">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="78c7e-657">`--exclude-launch-settings` — Wyłączyć z wyszukiwania *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="78c7e-658">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="78c7e-659">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="78c7e-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="78c7e-660">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-661">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-662">`--no-https` -Projekt nie wymaga protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="78c7e-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="78c7e-663">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="78c7e-664">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`, lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="78c7e-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="78c7e-665">**page**</span><span class="sxs-lookup"><span data-stu-id="78c7e-665">**page**</span></span>

<span data-ttu-id="78c7e-666">`-na|--namespace <NAMESPACE_NAME>` -Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="78c7e-667">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="78c7e-668">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="78c7e-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="78c7e-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="78c7e-669">**viewimports**</span></span>

<span data-ttu-id="78c7e-670">`-na|--namespace <NAMESPACE_NAME>` -Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="78c7e-671">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="78c7e-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="78c7e-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="78c7e-673">**Konsola, angular, react reactredux dla platformy**</span><span class="sxs-lookup"><span data-stu-id="78c7e-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="78c7e-674">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="78c7e-675">**classlib**</span></span>

<span data-ttu-id="78c7e-676">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="78c7e-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="78c7e-677">Wartości: `netcoreapp2.0` do tworzenia biblioteki klas .NET Core lub `netstandard2.0` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="78c7e-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="78c7e-678">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="78c7e-679">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="78c7e-680">**mstest, xunit**</span></span>

<span data-ttu-id="78c7e-681">`-p|--enable-pack` — Umożliwia tworzenie pakietów dla projektu za pomocą [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="78c7e-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="78c7e-682">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="78c7e-683">**globaljson**</span></span>

<span data-ttu-id="78c7e-684">`--sdk-version <VERSION_NUMBER>` -Określa wersję programu .NET Core SDK do użycia w *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="78c7e-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="78c7e-685">**web**</span><span class="sxs-lookup"><span data-stu-id="78c7e-685">**web**</span></span>

<span data-ttu-id="78c7e-686">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="78c7e-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="78c7e-687">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="78c7e-688">**webapi**</span></span>

<span data-ttu-id="78c7e-689">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="78c7e-690">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="78c7e-690">The possible values are:</span></span>

- <span data-ttu-id="78c7e-691">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="78c7e-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="78c7e-692">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="78c7e-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="78c7e-693">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="78c7e-694">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="78c7e-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="78c7e-695">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="78c7e-696">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-697">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="78c7e-698">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="78c7e-699">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-700">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="78c7e-701">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-702">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="78c7e-703">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="78c7e-704">Za pomocą `IndividualB2C` lub `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-705">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="78c7e-706">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="78c7e-707">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-708">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="78c7e-709">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="78c7e-710">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-711">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="78c7e-712">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="78c7e-713">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="78c7e-714">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="78c7e-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="78c7e-715">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="78c7e-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="78c7e-716">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-717">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-718">**MVC, razor**</span><span class="sxs-lookup"><span data-stu-id="78c7e-718">**mvc, razor**</span></span>

<span data-ttu-id="78c7e-719">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="78c7e-720">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="78c7e-720">The possible values are:</span></span>

- <span data-ttu-id="78c7e-721">`None` — Bez uwierzytelniania (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="78c7e-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="78c7e-722">`Individual` -Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="78c7e-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="78c7e-723">`IndividualB2C` -Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="78c7e-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="78c7e-724">`SingleOrg` -Uwierzytelnianie organizacji dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="78c7e-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="78c7e-725">`MultiOrg` -Uwierzytelnianie organizacji dla wielu dzierżaw.</span><span class="sxs-lookup"><span data-stu-id="78c7e-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="78c7e-726">`Windows` -Uwierzytelnianie Windows.</span><span class="sxs-lookup"><span data-stu-id="78c7e-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="78c7e-727">`--aad-b2c-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory B2C Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="78c7e-728">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-729">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="78c7e-730">`-ssp|--susi-policy-id <ID>` Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="78c7e-731">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-732">`-rp|--reset-password-policy-id <ID>` — Resetowanie hasła zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="78c7e-733">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-734">`-ep|--edit-profile-policy-id <ID>` — Edytowanie profilu zasad identyfikator dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="78c7e-735">Za pomocą `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-736">`--aad-instance <INSTANCE>` Wystąpienie usługi Azure Active Directory Aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="78c7e-737">Za pomocą `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="78c7e-738">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="78c7e-739">`--client-id <ID>` — Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="78c7e-740">Za pomocą `IndividualB2C`, `SingleOrg`, lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="78c7e-741">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="78c7e-742">`--domain <DOMAIN>` -Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="78c7e-743">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-744">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="78c7e-745">`--tenant-id <ID>` — Identyfikator dzierżawy identyfikator katalogu, aby nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="78c7e-746">Za pomocą `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="78c7e-747">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="78c7e-748">`--callback-path <PATH>` — Ścieżka żądania w podstawowej ścieżka identyfikatora URI przekierowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="78c7e-749">Za pomocą `SingleOrg` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="78c7e-750">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="78c7e-751">`-r|--org-read-access` — Umożliwia dostęp do odczytu do katalogu tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78c7e-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="78c7e-752">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="78c7e-753">`--use-launch-settings` -Zawiera *launchSettings.json* w danych wyjściowych wygenerowany szablon.</span><span class="sxs-lookup"><span data-stu-id="78c7e-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="78c7e-754">`--use-browserlink` -Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="78c7e-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="78c7e-755">`-uld|--use-local-db` -Określa, że LocalDB powinny być używane zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="78c7e-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="78c7e-756">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="78c7e-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="78c7e-757">`--no-restore` — Nie jest wykonywana niejawna przywracania, podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="78c7e-758">**page**</span><span class="sxs-lookup"><span data-stu-id="78c7e-758">**page**</span></span>

<span data-ttu-id="78c7e-759">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="78c7e-760">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="78c7e-761">`-np|--no-pagemodel` -Tworzy tę stronę bez klasy PageModel.</span><span class="sxs-lookup"><span data-stu-id="78c7e-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="78c7e-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="78c7e-762">**viewimports**</span></span>

<span data-ttu-id="78c7e-763">`-na|--namespace <NAMESPACE_NAME>`-Namespace dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="78c7e-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="78c7e-764">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="78c7e-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="78c7e-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="78c7e-766">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="78c7e-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="78c7e-767">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="78c7e-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="78c7e-768">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="78c7e-769">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="78c7e-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="78c7e-770">**classlib**</span></span>

<span data-ttu-id="78c7e-771">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="78c7e-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="78c7e-772">Wartości: `netcoreapp1.0`, `netcoreapp1.1`, lub `netstandard1.0` do `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="78c7e-773">Wartość domyślna to `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="78c7e-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="78c7e-774">**mvc**</span></span>

<span data-ttu-id="78c7e-775">`-f|--framework <FRAMEWORK>` -Określa [framework](../../standard/frameworks.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="78c7e-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="78c7e-776">Wartości: `netcoreapp1.0` lub `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="78c7e-777">Wartość domyślna to `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="78c7e-778">`-au|--auth <AUTHENTICATION_TYPE>` -Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="78c7e-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="78c7e-779">Wartości: `None` lub `Individual`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="78c7e-780">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-780">The default value is `None`.</span></span>

<span data-ttu-id="78c7e-781">`-uld|--use-local-db` -Określa, czy należy użyć programu LocalDB zamiast bazy danych SQLite.</span><span class="sxs-lookup"><span data-stu-id="78c7e-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="78c7e-782">Wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-782">Values: `true` or `false`.</span></span> <span data-ttu-id="78c7e-783">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="78c7e-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="78c7e-784">Przykłady</span><span class="sxs-lookup"><span data-stu-id="78c7e-784">Examples</span></span>

<span data-ttu-id="78c7e-785">Tworzenie C# projekt aplikacji konsoli, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="78c7e-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="78c7e-786">Tworzenie F# projekt aplikacji konsoli w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="78c7e-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="78c7e-787">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="78c7e-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="78c7e-788">Utwórz nowe platformy ASP.NET Core C# projektu MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="78c7e-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="78c7e-789">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="78c7e-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="78c7e-790">Wyświetl wszystkie szablony dostępne dla platformy MVC:</span><span class="sxs-lookup"><span data-stu-id="78c7e-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="78c7e-791">Lista wszystkich szablonów pasujących *możemy* podciąg.</span><span class="sxs-lookup"><span data-stu-id="78c7e-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="78c7e-792">Nie dokładnego dopasowania zostanie znaleziony, więc dopasowywanie podciągów uruchamiana nazwę krótką i nazwę kolumny.</span><span class="sxs-lookup"><span data-stu-id="78c7e-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="78c7e-793">Próba wywołania szablonu zgodnej *ng*.</span><span class="sxs-lookup"><span data-stu-id="78c7e-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="78c7e-794">Jeśli nie można ustalić pojedyncze dopasowanie, Utwórz listę szablonów, które są udanych dopasowań.</span><span class="sxs-lookup"><span data-stu-id="78c7e-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="78c7e-795">Zainstaluj wersję 2.0 szablonów aplikacji jednostronicowej dla platformy ASP.NET Core (opcji polecenia dostępne dla platformy .NET Core SDK 1.1 i tylko nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="78c7e-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="78c7e-796">Tworzenie *global.json* w bieżącym katalogu, ustawienie wersji zestawu SDK 2.0.0 (dostępne tylko w przypadku platformy .NET Core SDK 2.0 lub nowszy):</span><span class="sxs-lookup"><span data-stu-id="78c7e-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="78c7e-797">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78c7e-797">See also</span></span>

- [<span data-ttu-id="78c7e-798">Szablony niestandardowe dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="78c7e-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="78c7e-799">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="78c7e-799">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)
- [<span data-ttu-id="78c7e-800">repozytorium GitHub DotNet/dotnet-— przykłady szablonów</span><span class="sxs-lookup"><span data-stu-id="78c7e-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="78c7e-801">Dostępne szablony dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="78c7e-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
