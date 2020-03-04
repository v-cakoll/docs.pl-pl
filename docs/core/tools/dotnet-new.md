---
title: polecenie dotnet New
description: Polecenie dotnet New umożliwia tworzenie nowych projektów platformy .NET Core na podstawie określonego szablonu.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157222"
---
# <a name="dotnet-new"></a><span data-ttu-id="ebc19-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ebc19-103">dotnet new</span></span>

<span data-ttu-id="ebc19-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="ebc19-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ebc19-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="ebc19-105">Name</span></span>

<span data-ttu-id="ebc19-106">`dotnet new` — tworzy nowy projekt, plik konfiguracji lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ebc19-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ebc19-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ebc19-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ebc19-108">Description</span></span>

<span data-ttu-id="ebc19-109">`dotnet new` polecenie tworzy projekt .NET Core lub inne artefakty na podstawie szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="ebc19-110">Polecenie wywołuje [aparat szablonu](https://github.com/dotnet/templating) , aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="ebc19-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="ebc19-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ebc19-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="ebc19-112">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebc19-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ebc19-113">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="ebc19-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ebc19-114">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ebc19-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="ebc19-115">Aby wyświetlić listę wszystkich zainstalowanych szablonów, można uruchomić `dotnet new --list`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="ebc19-116">Jeśli wartość `TEMPLATE` nie jest dokładnym dopasowaniem do tekstu w **szablonie** lub kolumnie **krótkiej nazwy** z zwróconej tabeli, do tych dwóch kolumn jest wykonywane dopasowanie podciągów.</span><span class="sxs-lookup"><span data-stu-id="ebc19-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="ebc19-117">Począwszy od zestawu SDK platformy .NET Core 3,0, interfejs wiersza polecenia wyszukuje szablony w NuGet.org, gdy wywoła polecenie `dotnet new` w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="ebc19-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="ebc19-118">Jeśli interfejs wiersza polecenia nie może znaleźć dopasowania szablonu podczas wywoływania `dotnet new`, a nie nawet częściowej.</span><span class="sxs-lookup"><span data-stu-id="ebc19-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="ebc19-119">Jeśli jest dostępna nowsza wersja szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="ebc19-120">W takim przypadku projekt lub artefakt jest tworzony, ale interfejs wiersza polecenia ostrzega użytkownika o zaktualizowanej wersji szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="ebc19-121">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="ebc19-121">The command contains a default list of templates.</span></span> <span data-ttu-id="ebc19-122">Użyj `dotnet new -l`, aby uzyskać listę dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ebc19-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ebc19-123">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane wraz z zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="ebc19-124">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="ebc19-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="ebc19-125">Kliknij link krótkiej nazwy, aby wyświetlić opcje konkretnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="ebc19-126">Szablony</span><span class="sxs-lookup"><span data-stu-id="ebc19-126">Templates</span></span>                                    | <span data-ttu-id="ebc19-127">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="ebc19-127">Short name</span></span>                      | <span data-ttu-id="ebc19-128">Język</span><span class="sxs-lookup"><span data-stu-id="ebc19-128">Language</span></span>     | <span data-ttu-id="ebc19-129">Tagi</span><span class="sxs-lookup"><span data-stu-id="ebc19-129">Tags</span></span>                                  | <span data-ttu-id="ebc19-130">Wraca</span><span class="sxs-lookup"><span data-stu-id="ebc19-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="ebc19-131">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="ebc19-131">Console Application</span></span>                          | [<span data-ttu-id="ebc19-132">konsoli</span><span class="sxs-lookup"><span data-stu-id="ebc19-132">console</span></span>](#console)             | <span data-ttu-id="ebc19-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ebc19-133">[C#], F#, VB</span></span> | <span data-ttu-id="ebc19-134">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="ebc19-134">Common/Console</span></span>                        | <span data-ttu-id="ebc19-135">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-135">1.0</span></span>        |
| <span data-ttu-id="ebc19-136">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="ebc19-136">Class library</span></span>                                | [<span data-ttu-id="ebc19-137">określono</span><span class="sxs-lookup"><span data-stu-id="ebc19-137">classlib</span></span>](#classlib)           | <span data-ttu-id="ebc19-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ebc19-138">[C#], F#, VB</span></span> | <span data-ttu-id="ebc19-139">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="ebc19-139">Common/Library</span></span>                        | <span data-ttu-id="ebc19-140">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-140">1.0</span></span>        |
| <span data-ttu-id="ebc19-141">Aplikacja WPF</span><span class="sxs-lookup"><span data-stu-id="ebc19-141">WPF Application</span></span>                              | [<span data-ttu-id="ebc19-142">kodow</span><span class="sxs-lookup"><span data-stu-id="ebc19-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="ebc19-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-143">[C#]</span></span>         | <span data-ttu-id="ebc19-144">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ebc19-144">Common/WPF</span></span>                            | <span data-ttu-id="ebc19-145">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-145">3.0</span></span>        |
| <span data-ttu-id="ebc19-146">Biblioteka klas WPF</span><span class="sxs-lookup"><span data-stu-id="ebc19-146">WPF Class library</span></span>                            | [<span data-ttu-id="ebc19-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="ebc19-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="ebc19-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-148">[C#]</span></span>         | <span data-ttu-id="ebc19-149">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ebc19-149">Common/WPF</span></span>                            | <span data-ttu-id="ebc19-150">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-150">3.0</span></span>        |
| <span data-ttu-id="ebc19-151">Biblioteka kontrolek niestandardowych WPF</span><span class="sxs-lookup"><span data-stu-id="ebc19-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="ebc19-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="ebc19-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="ebc19-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-153">[C#]</span></span>         | <span data-ttu-id="ebc19-154">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ebc19-154">Common/WPF</span></span>                            | <span data-ttu-id="ebc19-155">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-155">3.0</span></span>        |
| <span data-ttu-id="ebc19-156">Biblioteka kontrolek użytkownika WPF</span><span class="sxs-lookup"><span data-stu-id="ebc19-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="ebc19-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ebc19-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="ebc19-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-158">[C#]</span></span>         | <span data-ttu-id="ebc19-159">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ebc19-159">Common/WPF</span></span>                            | <span data-ttu-id="ebc19-160">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-160">3.0</span></span>        |
| <span data-ttu-id="ebc19-161">Aplikacja Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="ebc19-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="ebc19-162">WinForms</span><span class="sxs-lookup"><span data-stu-id="ebc19-162">winforms</span></span>](#winforms)           | <span data-ttu-id="ebc19-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-163">[C#]</span></span>         | <span data-ttu-id="ebc19-164">Typowe/WinForms</span><span class="sxs-lookup"><span data-stu-id="ebc19-164">Common/WinForms</span></span>                       | <span data-ttu-id="ebc19-165">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-165">3.0</span></span>        |
| <span data-ttu-id="ebc19-166">Biblioteka klas Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="ebc19-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="ebc19-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="ebc19-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="ebc19-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-168">[C#]</span></span>         | <span data-ttu-id="ebc19-169">Typowe/WinForms</span><span class="sxs-lookup"><span data-stu-id="ebc19-169">Common/WinForms</span></span>                       | <span data-ttu-id="ebc19-170">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-170">3.0</span></span>        |
| <span data-ttu-id="ebc19-171">Usługa procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="ebc19-171">Worker Service</span></span>                               | [<span data-ttu-id="ebc19-172">odpowiedzialn</span><span class="sxs-lookup"><span data-stu-id="ebc19-172">worker</span></span>](#web-others)           | <span data-ttu-id="ebc19-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-173">[C#]</span></span>         | <span data-ttu-id="ebc19-174">Common/Worker/sieć Web</span><span class="sxs-lookup"><span data-stu-id="ebc19-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="ebc19-175">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-175">3.0</span></span>        |
| <span data-ttu-id="ebc19-176">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="ebc19-176">Unit Test Project</span></span>                            | [<span data-ttu-id="ebc19-177">MSTest</span><span class="sxs-lookup"><span data-stu-id="ebc19-177">mstest</span></span>](#test)                 | <span data-ttu-id="ebc19-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ebc19-178">[C#], F#, VB</span></span> | <span data-ttu-id="ebc19-179">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="ebc19-179">Test/MSTest</span></span>                           | <span data-ttu-id="ebc19-180">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-180">1.0</span></span>        |
| <span data-ttu-id="ebc19-181">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ebc19-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="ebc19-182">NUnit</span><span class="sxs-lookup"><span data-stu-id="ebc19-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="ebc19-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ebc19-183">[C#], F#, VB</span></span> | <span data-ttu-id="ebc19-184">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ebc19-184">Test/NUnit</span></span>                            | <span data-ttu-id="ebc19-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="ebc19-185">2.1.400</span></span>    |
| <span data-ttu-id="ebc19-186">Element testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ebc19-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="ebc19-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ebc19-187">[C#], F#, VB</span></span> | <span data-ttu-id="ebc19-188">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ebc19-188">Test/NUnit</span></span>                            | <span data-ttu-id="ebc19-189">2.2</span><span class="sxs-lookup"><span data-stu-id="ebc19-189">2.2</span></span>        |
| <span data-ttu-id="ebc19-190">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="ebc19-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="ebc19-191">xUnit</span><span class="sxs-lookup"><span data-stu-id="ebc19-191">xunit</span></span>](#test)                  | <span data-ttu-id="ebc19-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ebc19-192">[C#], F#, VB</span></span> | <span data-ttu-id="ebc19-193">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="ebc19-193">Test/xUnit</span></span>                            | <span data-ttu-id="ebc19-194">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-194">1.0</span></span>        |
| <span data-ttu-id="ebc19-195">Składnik Razor</span><span class="sxs-lookup"><span data-stu-id="ebc19-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="ebc19-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-196">[C#]</span></span>         | <span data-ttu-id="ebc19-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ebc19-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="ebc19-198">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-198">3.0</span></span>        |
| <span data-ttu-id="ebc19-199">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="ebc19-199">Razor Page</span></span>                                   | [<span data-ttu-id="ebc19-200">stronic</span><span class="sxs-lookup"><span data-stu-id="ebc19-200">page</span></span>](#page)                   | <span data-ttu-id="ebc19-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-201">[C#]</span></span>         | <span data-ttu-id="ebc19-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ebc19-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="ebc19-203">2.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-203">2.0</span></span>        |
| <span data-ttu-id="ebc19-204">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="ebc19-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="ebc19-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="ebc19-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="ebc19-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-206">[C#]</span></span>         | <span data-ttu-id="ebc19-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ebc19-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="ebc19-208">2.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-208">2.0</span></span>        |
| <span data-ttu-id="ebc19-209">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="ebc19-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="ebc19-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-210">[C#]</span></span>         | <span data-ttu-id="ebc19-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ebc19-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="ebc19-212">2.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-212">2.0</span></span>        |
| <span data-ttu-id="ebc19-213">Aplikacja serwera Blazor</span><span class="sxs-lookup"><span data-stu-id="ebc19-213">Blazor Server App</span></span>                            | [<span data-ttu-id="ebc19-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ebc19-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="ebc19-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-215">[C#]</span></span>         | <span data-ttu-id="ebc19-216">Sieć Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="ebc19-216">Web/Blazor</span></span>                            | <span data-ttu-id="ebc19-217">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-217">3.0</span></span>        |
| <span data-ttu-id="ebc19-218">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="ebc19-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="ebc19-219">witrynę</span><span class="sxs-lookup"><span data-stu-id="ebc19-219">web</span></span>](#web)                     | <span data-ttu-id="ebc19-220">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ebc19-220">[C#], F#</span></span>     | <span data-ttu-id="ebc19-221">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="ebc19-221">Web/Empty</span></span>                             | <span data-ttu-id="ebc19-222">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-222">1.0</span></span>        |
| <span data-ttu-id="ebc19-223">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="ebc19-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="ebc19-224">Standard</span><span class="sxs-lookup"><span data-stu-id="ebc19-224">mvc</span></span>](#web-options)             | <span data-ttu-id="ebc19-225">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ebc19-225">[C#], F#</span></span>     | <span data-ttu-id="ebc19-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ebc19-226">Web/MVC</span></span>                               | <span data-ttu-id="ebc19-227">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-227">1.0</span></span>        |
| <span data-ttu-id="ebc19-228">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ebc19-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="ebc19-229">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="ebc19-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="ebc19-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-230">[C#]</span></span>         | <span data-ttu-id="ebc19-231">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ebc19-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="ebc19-232">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="ebc19-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="ebc19-233">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="ebc19-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="ebc19-234">kątow</span><span class="sxs-lookup"><span data-stu-id="ebc19-234">angular</span></span>](#spa)                 | <span data-ttu-id="ebc19-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-235">[C#]</span></span>         | <span data-ttu-id="ebc19-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ebc19-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ebc19-237">2.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-237">2.0</span></span>        |
| <span data-ttu-id="ebc19-238">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="ebc19-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="ebc19-239">biern</span><span class="sxs-lookup"><span data-stu-id="ebc19-239">react</span></span>](#spa)                   | <span data-ttu-id="ebc19-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-240">[C#]</span></span>         | <span data-ttu-id="ebc19-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ebc19-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ebc19-242">2.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-242">2.0</span></span>        |
| <span data-ttu-id="ebc19-243">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="ebc19-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="ebc19-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="ebc19-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="ebc19-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-245">[C#]</span></span>         | <span data-ttu-id="ebc19-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ebc19-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ebc19-247">2.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-247">2.0</span></span>        |
| <span data-ttu-id="ebc19-248">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="ebc19-248">Razor Class Library</span></span>                          | [<span data-ttu-id="ebc19-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ebc19-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="ebc19-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-250">[C#]</span></span>         | <span data-ttu-id="ebc19-251">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="ebc19-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="ebc19-252">2.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-252">2.1</span></span>        |
| <span data-ttu-id="ebc19-253">Internetowy interfejs API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ebc19-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="ebc19-254">WebApi</span><span class="sxs-lookup"><span data-stu-id="ebc19-254">webapi</span></span>](#webapi)               | <span data-ttu-id="ebc19-255">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ebc19-255">[C#], F#</span></span>     | <span data-ttu-id="ebc19-256">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ebc19-256">Web/WebAPI</span></span>                            | <span data-ttu-id="ebc19-257">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-257">1.0</span></span>        |
| <span data-ttu-id="ebc19-258">ASP.NET Core usługi gRPC</span><span class="sxs-lookup"><span data-stu-id="ebc19-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="ebc19-259">grpc</span><span class="sxs-lookup"><span data-stu-id="ebc19-259">grpc</span></span>](#web-others)             | <span data-ttu-id="ebc19-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="ebc19-260">[C#]</span></span>         | <span data-ttu-id="ebc19-261">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ebc19-261">Web/gRPC</span></span>                              | <span data-ttu-id="ebc19-262">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-262">3.0</span></span>        |
| <span data-ttu-id="ebc19-263">Plik buforu protokołu</span><span class="sxs-lookup"><span data-stu-id="ebc19-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="ebc19-264">proto</span><span class="sxs-lookup"><span data-stu-id="ebc19-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="ebc19-265">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ebc19-265">Web/gRPC</span></span>                              | <span data-ttu-id="ebc19-266">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-266">3.0</span></span>        |
| <span data-ttu-id="ebc19-267">plik GITIGNORE dotnet</span><span class="sxs-lookup"><span data-stu-id="ebc19-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="ebc19-268">Config</span><span class="sxs-lookup"><span data-stu-id="ebc19-268">Config</span></span>                                | <span data-ttu-id="ebc19-269">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-269">3.0</span></span>        |
| <span data-ttu-id="ebc19-270">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="ebc19-270">global.json file</span></span>                             | [<span data-ttu-id="ebc19-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="ebc19-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="ebc19-272">Config</span><span class="sxs-lookup"><span data-stu-id="ebc19-272">Config</span></span>                                | <span data-ttu-id="ebc19-273">2.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-273">2.0</span></span>        |
| <span data-ttu-id="ebc19-274">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="ebc19-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="ebc19-275">Config</span><span class="sxs-lookup"><span data-stu-id="ebc19-275">Config</span></span>                                | <span data-ttu-id="ebc19-276">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-276">1.0</span></span>        |
| <span data-ttu-id="ebc19-277">plik manifestu narzędzia lokalnego dotnet</span><span class="sxs-lookup"><span data-stu-id="ebc19-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="ebc19-278">Config</span><span class="sxs-lookup"><span data-stu-id="ebc19-278">Config</span></span>                                | <span data-ttu-id="ebc19-279">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-279">3.0</span></span>        |
| <span data-ttu-id="ebc19-280">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="ebc19-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="ebc19-281">Config</span><span class="sxs-lookup"><span data-stu-id="ebc19-281">Config</span></span>                                | <span data-ttu-id="ebc19-282">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-282">1.0</span></span>        |
| <span data-ttu-id="ebc19-283">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ebc19-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="ebc19-284">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ebc19-284">Solution</span></span>                              | <span data-ttu-id="ebc19-285">1.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="ebc19-286">Opcje</span><span class="sxs-lookup"><span data-stu-id="ebc19-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="ebc19-287">Wyświetla podsumowanie tego, co się stanie w przypadku uruchomienia danego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebc19-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="ebc19-288">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="ebc19-289">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="ebc19-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ebc19-290">Jest to wymagane, gdy wybrany szablon spowoduje zastąpienie istniejących plików w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="ebc19-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ebc19-291">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebc19-291">Prints out help for the command.</span></span> <span data-ttu-id="ebc19-292">Może być wywoływana dla samego polecenia `dotnet new` lub dla dowolnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="ebc19-293">Na przykład `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="ebc19-294">Instaluje pakiet szablonów z podanej `PATH` lub `NUGET_ID`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ebc19-295">Jeśli chcesz zainstalować wstępną wersję pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ebc19-296">Domyślnie `dotnet new` przekazuje \* wersji, co reprezentuje najnowszą stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="ebc19-297">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="ebc19-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="ebc19-298">Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej wersji stabilnej, jeśli nie określono żadnej wersji.</span><span class="sxs-lookup"><span data-stu-id="ebc19-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="ebc19-299">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ebc19-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="ebc19-300">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="ebc19-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="ebc19-301">Jeśli nazwa nie zostanie określona, program wyświetli listę wszystkich szablonów.</span><span class="sxs-lookup"><span data-stu-id="ebc19-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="ebc19-302">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ebc19-302">The language of the template to create.</span></span> <span data-ttu-id="ebc19-303">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="ebc19-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ebc19-304">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ebc19-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ebc19-305">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="ebc19-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ebc19-306">W takich przypadkach należy ująć wartość parametru Language w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="ebc19-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="ebc19-307">Na przykład `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="ebc19-308">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ebc19-308">The name for the created output.</span></span> <span data-ttu-id="ebc19-309">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="ebc19-310">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="ebc19-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="ebc19-311">Dostępne od wersji .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ebc19-312">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ebc19-312">Location to place the generated output.</span></span> <span data-ttu-id="ebc19-313">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="ebc19-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="ebc19-314">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="ebc19-314">Filters templates based on available types.</span></span> <span data-ttu-id="ebc19-315">Wstępnie zdefiniowane wartości to "Project", "Item" lub "Other".</span><span class="sxs-lookup"><span data-stu-id="ebc19-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="ebc19-316">Odinstalowuje pakiet szablonów na `PATH` lub `NUGET_ID`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ebc19-317">Jeśli wartość `<PATH|NUGET_ID>` nie zostanie określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="ebc19-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="ebc19-318">Podczas określania `NUGET_ID`nie Uwzględniaj numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="ebc19-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="ebc19-319">Jeśli nie określisz parametru do tej opcji, polecenie wyświetli listę zainstalowanych szablonów i szczegółowe informacje o nich.</span><span class="sxs-lookup"><span data-stu-id="ebc19-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ebc19-320">Aby odinstalować szablon przy użyciu `PATH`, musisz w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="ebc19-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ebc19-321">Na przykład *C:/Users/\<USER >/Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="ebc19-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="ebc19-322">Nie dołączaj ostatecznego ukośnika katalogu w ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="ebc19-323">Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane i instaluje je.</span><span class="sxs-lookup"><span data-stu-id="ebc19-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="ebc19-324">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="ebc19-325">Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ebc19-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="ebc19-326">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="ebc19-327">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="ebc19-327">Template options</span></span>

<span data-ttu-id="ebc19-328">Każdy szablon projektu może mieć dodatkowe opcje dostępne.</span><span class="sxs-lookup"><span data-stu-id="ebc19-328">Each project template may have additional options available.</span></span> <span data-ttu-id="ebc19-329">Szablony podstawowe mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="ebc19-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="ebc19-330">console</span><span class="sxs-lookup"><span data-stu-id="ebc19-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-331">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-332">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ebc19-333">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ebc19-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ebc19-334">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ebc19-334">SDK version</span></span> | <span data-ttu-id="ebc19-335">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ebc19-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ebc19-336">3.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ebc19-337">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ebc19-338">Ustawia właściwość `LangVersion` w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ebc19-339">Na przykład użyj `--langVersion 7.3`, aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ebc19-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ebc19-340">Nieobsługiwane w F#programie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-340">Not supported for F#.</span></span> <span data-ttu-id="ebc19-341">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ebc19-342">Listę wersji domyślnych C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ebc19-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-343">Jeśli określony, nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="ebc19-344">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="ebc19-345">określono</span><span class="sxs-lookup"><span data-stu-id="ebc19-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-346">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-347">Wartości: `netcoreapp<version>` do tworzenia biblioteki klas .NET Core lub `netstandard<version>` do tworzenia biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ebc19-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ebc19-348">Wartością domyślną jest `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ebc19-349">Ustawia właściwość `LangVersion` w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ebc19-350">Na przykład użyj `--langVersion 7.3`, aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ebc19-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ebc19-351">Nieobsługiwane w F#programie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-351">Not supported for F#.</span></span> <span data-ttu-id="ebc19-352">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ebc19-353">Listę wersji domyślnych C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ebc19-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-354">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="ebc19-355">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ebc19-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-356">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-357">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ebc19-358">Dostępne od wersji .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ebc19-359">Ustawia właściwość `LangVersion` w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ebc19-360">Na przykład użyj `--langVersion 7.3`, aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ebc19-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ebc19-361">Listę wersji domyślnych C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ebc19-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-362">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="ebc19-363">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="ebc19-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ebc19-364">Ustawia właściwość `LangVersion` w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ebc19-365">Na przykład użyj `--langVersion 7.3`, aby użyć C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ebc19-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ebc19-366">Listę wersji domyślnych C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ebc19-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-367">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="ebc19-368">proces roboczy, GRPC</span><span class="sxs-lookup"><span data-stu-id="ebc19-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-369">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-370">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ebc19-371">Dostępne od wersji .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ebc19-372">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-373">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="ebc19-374">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="ebc19-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-375">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-376">Opcja dostępna od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ebc19-377">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ebc19-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ebc19-378">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ebc19-378">SDK version</span></span> | <span data-ttu-id="ebc19-379">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ebc19-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ebc19-380">3.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ebc19-381">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ebc19-382">Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ebc19-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-383">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="ebc19-384">NUnit</span><span class="sxs-lookup"><span data-stu-id="ebc19-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-385">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="ebc19-386">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ebc19-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ebc19-387">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ebc19-387">SDK version</span></span> | <span data-ttu-id="ebc19-388">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ebc19-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ebc19-389">3.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ebc19-390">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ebc19-391">2.2</span><span class="sxs-lookup"><span data-stu-id="ebc19-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="ebc19-392">2.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ebc19-393">Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ebc19-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-394">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="ebc19-395">strona</span><span class="sxs-lookup"><span data-stu-id="ebc19-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ebc19-396">Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-396">Namespace for the generated code.</span></span> <span data-ttu-id="ebc19-397">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="ebc19-398">Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ebc19-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="ebc19-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="ebc19-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ebc19-400">Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-400">Namespace for the generated code.</span></span> <span data-ttu-id="ebc19-401">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="ebc19-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ebc19-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ebc19-403">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ebc19-403">The type of authentication to use.</span></span> <span data-ttu-id="ebc19-404">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ebc19-404">The possible values are:</span></span>

  - <span data-ttu-id="ebc19-405">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ebc19-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ebc19-406">Uwierzytelnianie indywidualne `Individual`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ebc19-407">`IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ebc19-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ebc19-408">`SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ebc19-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ebc19-409">`MultiOrg` — uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="ebc19-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ebc19-410">`Windows` — uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ebc19-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ebc19-411">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ebc19-412">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ebc19-413">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ebc19-414">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ebc19-415">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ebc19-416">Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="ebc19-417">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ebc19-418">Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ebc19-419">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ebc19-420">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ebc19-421">Użyj z uwierzytelnianiem `SingleOrg` lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ebc19-422">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ebc19-423">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-423">The Client ID for this project.</span></span> <span data-ttu-id="ebc19-424">Użyj z uwierzytelnianiem `IndividualB2C`, `SingleOrg`lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ebc19-425">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ebc19-426">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-426">The domain for the directory tenant.</span></span> <span data-ttu-id="ebc19-427">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ebc19-428">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ebc19-429">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ebc19-430">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ebc19-431">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ebc19-432">Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ebc19-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ebc19-433">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ebc19-434">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ebc19-435">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ebc19-436">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ebc19-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ebc19-437">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ebc19-438">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ebc19-438">Turns off HTTPS.</span></span> <span data-ttu-id="ebc19-439">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane na potrzeby `--auth`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ebc19-440">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ebc19-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ebc19-441">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ebc19-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-442">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="ebc19-443">web</span><span class="sxs-lookup"><span data-stu-id="ebc19-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ebc19-444">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-445">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-446">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="ebc19-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ebc19-447">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ebc19-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ebc19-448">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ebc19-448">SDK version</span></span> | <span data-ttu-id="ebc19-449">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ebc19-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ebc19-450">3.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ebc19-451">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ebc19-452">2.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ebc19-453">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ebc19-454">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ebc19-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="ebc19-455">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="ebc19-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ebc19-456">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ebc19-456">The type of authentication to use.</span></span> <span data-ttu-id="ebc19-457">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ebc19-457">The possible values are:</span></span>

  - <span data-ttu-id="ebc19-458">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ebc19-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ebc19-459">Uwierzytelnianie indywidualne `Individual`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ebc19-460">`IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ebc19-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ebc19-461">`SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ebc19-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ebc19-462">`MultiOrg` — uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="ebc19-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ebc19-463">`Windows` — uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ebc19-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ebc19-464">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ebc19-465">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ebc19-466">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ebc19-467">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ebc19-468">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ebc19-469">Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="ebc19-470">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ebc19-471">Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ebc19-472">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ebc19-473">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ebc19-474">Użyj z uwierzytelnianiem `SingleOrg` lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ebc19-475">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ebc19-476">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-476">The Client ID for this project.</span></span> <span data-ttu-id="ebc19-477">Użyj z uwierzytelnianiem `IndividualB2C`, `SingleOrg`lub `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ebc19-478">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ebc19-479">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-479">The domain for the directory tenant.</span></span> <span data-ttu-id="ebc19-480">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ebc19-481">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ebc19-482">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ebc19-483">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ebc19-484">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ebc19-485">Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ebc19-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ebc19-486">Użyj z uwierzytelnianiem `SingleOrg` lub `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ebc19-487">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ebc19-488">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ebc19-489">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ebc19-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ebc19-490">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ebc19-491">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ebc19-491">Turns off HTTPS.</span></span> <span data-ttu-id="ebc19-492">Ta opcja ma zastosowanie tylko wtedy, gdy `Individual`, `IndividualB2C`, `SingleOrg`lub `MultiOrg` nie są używane.</span><span class="sxs-lookup"><span data-stu-id="ebc19-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ebc19-493">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ebc19-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ebc19-494">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ebc19-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-495">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-496">Opcja dostępna od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ebc19-497">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ebc19-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ebc19-498">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ebc19-498">SDK version</span></span> | <span data-ttu-id="ebc19-499">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ebc19-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ebc19-500">3.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ebc19-501">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="ebc19-502">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="ebc19-503">Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="ebc19-504">Opcja nie jest dostępna w programie .NET Core 2,2 i 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="ebc19-505">kątowy, reagowanie</span><span class="sxs-lookup"><span data-stu-id="ebc19-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ebc19-506">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ebc19-506">The type of authentication to use.</span></span> <span data-ttu-id="ebc19-507">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-507">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="ebc19-508">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ebc19-508">The possible values are:</span></span>

  - <span data-ttu-id="ebc19-509">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ebc19-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ebc19-510">Uwierzytelnianie indywidualne `Individual`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ebc19-511">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-511">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-512">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ebc19-513">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ebc19-513">Turns off HTTPS.</span></span> <span data-ttu-id="ebc19-514">Ta opcja ma zastosowanie tylko wtedy, gdy uwierzytelnianie jest `None`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ebc19-515">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ebc19-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ebc19-516">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ebc19-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ebc19-517">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-518">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-519">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="ebc19-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ebc19-520">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ebc19-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ebc19-521">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ebc19-521">SDK version</span></span> | <span data-ttu-id="ebc19-522">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ebc19-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ebc19-523">3.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ebc19-524">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ebc19-525">2.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="ebc19-526">reactredux dla platformy</span><span class="sxs-lookup"><span data-stu-id="ebc19-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ebc19-527">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-527">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-528">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-529">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="ebc19-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ebc19-530">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ebc19-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ebc19-531">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ebc19-531">SDK version</span></span> | <span data-ttu-id="ebc19-532">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ebc19-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ebc19-533">3.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ebc19-534">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ebc19-535">2.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="ebc19-536">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ebc19-537">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ebc19-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="ebc19-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ebc19-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="ebc19-539">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="ebc19-540">Obsługuje dodawanie tradycyjnych stron Razor i widoków oprócz składników do tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ebc19-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="ebc19-541">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ebc19-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="ebc19-542">WebApi</span><span class="sxs-lookup"><span data-stu-id="ebc19-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ebc19-543">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ebc19-543">The type of authentication to use.</span></span> <span data-ttu-id="ebc19-544">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ebc19-544">The possible values are:</span></span>

  - <span data-ttu-id="ebc19-545">`None` — brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ebc19-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ebc19-546">`IndividualB2C` — uwierzytelnianie indywidualne z Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ebc19-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ebc19-547">`SingleOrg` — uwierzytelnianie organizacji dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ebc19-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ebc19-548">`Windows` — uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ebc19-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ebc19-549">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ebc19-550">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ebc19-551">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ebc19-552">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ebc19-553">Użyj z uwierzytelnianiem `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ebc19-554">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ebc19-555">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ebc19-556">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ebc19-557">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-557">The Client ID for this project.</span></span> <span data-ttu-id="ebc19-558">Użyj z uwierzytelnianiem `IndividualB2C` lub `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ebc19-559">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ebc19-560">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-560">The domain for the directory tenant.</span></span> <span data-ttu-id="ebc19-561">Użyj z uwierzytelnianiem `IndividualB2C` lub `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ebc19-562">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ebc19-563">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ebc19-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ebc19-564">Użyj z uwierzytelnianiem `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ebc19-565">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ebc19-566">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ebc19-567">Dotyczy tylko uwierzytelniania `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ebc19-568">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ebc19-569">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ebc19-569">Turns off HTTPS.</span></span> <span data-ttu-id="ebc19-570">`app.UseHsts` i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ebc19-571">Ta opcja ma zastosowanie tylko wtedy, gdy `IndividualB2C` lub `SingleOrg` nie są używane do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ebc19-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ebc19-572">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ebc19-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ebc19-573">Dotyczy tylko uwierzytelniania `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ebc19-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc19-574">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ebc19-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ebc19-575">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="ebc19-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ebc19-576">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ebc19-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ebc19-577">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ebc19-577">SDK version</span></span> | <span data-ttu-id="ebc19-578">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ebc19-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ebc19-579">3.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ebc19-580">3.0</span><span class="sxs-lookup"><span data-stu-id="ebc19-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ebc19-581">2.1</span><span class="sxs-lookup"><span data-stu-id="ebc19-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ebc19-582">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="ebc19-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="ebc19-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="ebc19-584">Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ebc19-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="ebc19-585">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ebc19-585">Examples</span></span>

- <span data-ttu-id="ebc19-586">Utwórz projekt C# aplikacji konsolowej, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="ebc19-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="ebc19-587">Utwórz projekt F# aplikacji konsolowej w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ebc19-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="ebc19-588">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ebc19-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="ebc19-589">Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="ebc19-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="ebc19-590">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="ebc19-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="ebc19-591">Wyświetl listę wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):</span><span class="sxs-lookup"><span data-stu-id="ebc19-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="ebc19-592">Wyświetl listę wszystkich szablonów pasujących *do* podciągu.</span><span class="sxs-lookup"><span data-stu-id="ebc19-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="ebc19-593">Nie znaleziono dokładnego dopasowania, więc Dopasowywanie podciągów działa w odniesieniu do kolumn krótkich nazw i nazw.</span><span class="sxs-lookup"><span data-stu-id="ebc19-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="ebc19-594">Podjęto próbę wywołania szablonu zgodnego z parametrem *ng*.</span><span class="sxs-lookup"><span data-stu-id="ebc19-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="ebc19-595">Jeśli nie można ustalić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są dopasowań częściowych.</span><span class="sxs-lookup"><span data-stu-id="ebc19-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="ebc19-596">Zainstaluj wersję 2,0 szablonów SPA dla ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="ebc19-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="ebc19-597">Wyświetl listę zainstalowanych szablonów i szczegółowe informacje o nich, w tym sposoby ich odinstalowywania:</span><span class="sxs-lookup"><span data-stu-id="ebc19-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="ebc19-598">Utwórz plik *Global. JSON* w bieżącym katalogu, ustawiając wersję zestawu SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="ebc19-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="ebc19-599">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebc19-599">See also</span></span>

- [<span data-ttu-id="ebc19-600">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="ebc19-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="ebc19-601">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="ebc19-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="ebc19-602">dotnet/dotnet-Template-przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="ebc19-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="ebc19-603">Dostępne szablony dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="ebc19-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
