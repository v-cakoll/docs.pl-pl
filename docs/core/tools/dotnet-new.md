---
title: dotnet nowe polecenie
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399127"
---
# <a name="dotnet-new"></a><span data-ttu-id="ce51b-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ce51b-103">dotnet new</span></span>

<span data-ttu-id="ce51b-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="ce51b-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ce51b-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ce51b-105">Name</span></span>

<span data-ttu-id="ce51b-106">`dotnet new`- Tworzy nowy projekt, plik konfiguracyjny lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ce51b-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ce51b-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ce51b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ce51b-108">Description</span></span>

<span data-ttu-id="ce51b-109">Polecenie `dotnet new` tworzy projekt .NET Core lub inne artefakty na podstawie szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="ce51b-110">Polecenie wywołuje [aparat szablonu,](https://github.com/dotnet/templating) aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="ce51b-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="ce51b-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ce51b-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="ce51b-112">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ce51b-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ce51b-113">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="ce51b-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ce51b-114">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ce51b-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="ce51b-115">Można uruchomić, `dotnet new --list` aby wyświetlić listę wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ce51b-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="ce51b-116">Jeśli `TEMPLATE` wartość nie jest dokładne dopasowanie tekstu w **szablony** lub **krótka nazwa** kolumna z tabeli zwracanej, dopasowanie podciągu jest wykonywane na tych dwóch kolumnach.</span><span class="sxs-lookup"><span data-stu-id="ce51b-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="ce51b-117">Począwszy od sdk .NET Core 3.0, wiersz wiersza polecenia `dotnet new` wyszukuje szablony w NuGet.org wywołania polecenia w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="ce51b-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="ce51b-118">Jeśli wiersz wiersza wiersza wiersza nie `dotnet new`może znaleźć dopasowania szablonu podczas wywoływania , nawet częściowe.</span><span class="sxs-lookup"><span data-stu-id="ce51b-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="ce51b-119">Jeśli jest dostępna nowsza wersja szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="ce51b-120">W takim przypadku projekt lub artefakt jest tworzony, ale cli ostrzega o zaktualizowanej wersji szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="ce51b-121">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="ce51b-121">The command contains a default list of templates.</span></span> <span data-ttu-id="ce51b-122">Służy `dotnet new -l` do uzyskiwania listy dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ce51b-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ce51b-123">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane z .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ce51b-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="ce51b-124">Domyślny język szablonu jest wyświetlany wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="ce51b-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="ce51b-125">Kliknij łącze krótkiej nazwy, aby wyświetlić określone opcje szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="ce51b-126">Szablony</span><span class="sxs-lookup"><span data-stu-id="ce51b-126">Templates</span></span>                                    | <span data-ttu-id="ce51b-127">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="ce51b-127">Short name</span></span>                      | <span data-ttu-id="ce51b-128">Język</span><span class="sxs-lookup"><span data-stu-id="ce51b-128">Language</span></span>     | <span data-ttu-id="ce51b-129">Tagi</span><span class="sxs-lookup"><span data-stu-id="ce51b-129">Tags</span></span>                                  | <span data-ttu-id="ce51b-130">Wprowadzone</span><span class="sxs-lookup"><span data-stu-id="ce51b-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="ce51b-131">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="ce51b-131">Console Application</span></span>                          | [<span data-ttu-id="ce51b-132">Konsoli</span><span class="sxs-lookup"><span data-stu-id="ce51b-132">console</span></span>](#console)             | <span data-ttu-id="ce51b-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce51b-133">[C#], F#, VB</span></span> | <span data-ttu-id="ce51b-134">Często/Konsola</span><span class="sxs-lookup"><span data-stu-id="ce51b-134">Common/Console</span></span>                        | <span data-ttu-id="ce51b-135">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-135">1.0</span></span>        |
| <span data-ttu-id="ce51b-136">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="ce51b-136">Class library</span></span>                                | [<span data-ttu-id="ce51b-137">Classlib</span><span class="sxs-lookup"><span data-stu-id="ce51b-137">classlib</span></span>](#classlib)           | <span data-ttu-id="ce51b-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce51b-138">[C#], F#, VB</span></span> | <span data-ttu-id="ce51b-139">Wspólne/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="ce51b-139">Common/Library</span></span>                        | <span data-ttu-id="ce51b-140">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-140">1.0</span></span>        |
| <span data-ttu-id="ce51b-141">Aplikacja WPF</span><span class="sxs-lookup"><span data-stu-id="ce51b-141">WPF Application</span></span>                              | [<span data-ttu-id="ce51b-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="ce51b-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="ce51b-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-143">[C#]</span></span>         | <span data-ttu-id="ce51b-144">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="ce51b-144">Common/WPF</span></span>                            | <span data-ttu-id="ce51b-145">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-145">3.0</span></span>        |
| <span data-ttu-id="ce51b-146">Biblioteka klas WPF</span><span class="sxs-lookup"><span data-stu-id="ce51b-146">WPF Class library</span></span>                            | [<span data-ttu-id="ce51b-147">wpflib (wpflib)</span><span class="sxs-lookup"><span data-stu-id="ce51b-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="ce51b-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-148">[C#]</span></span>         | <span data-ttu-id="ce51b-149">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="ce51b-149">Common/WPF</span></span>                            | <span data-ttu-id="ce51b-150">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-150">3.0</span></span>        |
| <span data-ttu-id="ce51b-151">Biblioteka kontrolek niestandardowych WPF</span><span class="sxs-lookup"><span data-stu-id="ce51b-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="ce51b-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="ce51b-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="ce51b-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-153">[C#]</span></span>         | <span data-ttu-id="ce51b-154">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="ce51b-154">Common/WPF</span></span>                            | <span data-ttu-id="ce51b-155">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-155">3.0</span></span>        |
| <span data-ttu-id="ce51b-156">Biblioteka kontroli użytkownika WPF</span><span class="sxs-lookup"><span data-stu-id="ce51b-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="ce51b-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ce51b-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="ce51b-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-158">[C#]</span></span>         | <span data-ttu-id="ce51b-159">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="ce51b-159">Common/WPF</span></span>                            | <span data-ttu-id="ce51b-160">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-160">3.0</span></span>        |
| <span data-ttu-id="ce51b-161">Aplikacja formularzy systemu Windows (Formularze WinForms)</span><span class="sxs-lookup"><span data-stu-id="ce51b-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="ce51b-162">Winforms</span><span class="sxs-lookup"><span data-stu-id="ce51b-162">winforms</span></span>](#winforms)           | <span data-ttu-id="ce51b-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-163">[C#]</span></span>         | <span data-ttu-id="ce51b-164">Formularze wspólne/win</span><span class="sxs-lookup"><span data-stu-id="ce51b-164">Common/WinForms</span></span>                       | <span data-ttu-id="ce51b-165">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-165">3.0</span></span>        |
| <span data-ttu-id="ce51b-166">Biblioteka klas formularzy systemu Windows (WinForms)</span><span class="sxs-lookup"><span data-stu-id="ce51b-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="ce51b-167">winformslib (winformslib)</span><span class="sxs-lookup"><span data-stu-id="ce51b-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="ce51b-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-168">[C#]</span></span>         | <span data-ttu-id="ce51b-169">Formularze wspólne/win</span><span class="sxs-lookup"><span data-stu-id="ce51b-169">Common/WinForms</span></span>                       | <span data-ttu-id="ce51b-170">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-170">3.0</span></span>        |
| <span data-ttu-id="ce51b-171">Obsługa pracowników</span><span class="sxs-lookup"><span data-stu-id="ce51b-171">Worker Service</span></span>                               | [<span data-ttu-id="ce51b-172">Pracownik</span><span class="sxs-lookup"><span data-stu-id="ce51b-172">worker</span></span>](#web-others)           | <span data-ttu-id="ce51b-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-173">[C#]</span></span>         | <span data-ttu-id="ce51b-174">Wspólne/Pracownik/Sieć Web</span><span class="sxs-lookup"><span data-stu-id="ce51b-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="ce51b-175">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-175">3.0</span></span>        |
| <span data-ttu-id="ce51b-176">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="ce51b-176">Unit Test Project</span></span>                            | [<span data-ttu-id="ce51b-177">Mstest</span><span class="sxs-lookup"><span data-stu-id="ce51b-177">mstest</span></span>](#test)                 | <span data-ttu-id="ce51b-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce51b-178">[C#], F#, VB</span></span> | <span data-ttu-id="ce51b-179">Test/TEST</span><span class="sxs-lookup"><span data-stu-id="ce51b-179">Test/MSTest</span></span>                           | <span data-ttu-id="ce51b-180">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-180">1.0</span></span>        |
| <span data-ttu-id="ce51b-181">Projekt testowy Jednostki 3</span><span class="sxs-lookup"><span data-stu-id="ce51b-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="ce51b-182">Nunit</span><span class="sxs-lookup"><span data-stu-id="ce51b-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="ce51b-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce51b-183">[C#], F#, VB</span></span> | <span data-ttu-id="ce51b-184">Test/NJednostka</span><span class="sxs-lookup"><span data-stu-id="ce51b-184">Test/NUnit</span></span>                            | <span data-ttu-id="ce51b-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="ce51b-185">2.1.400</span></span>    |
| <span data-ttu-id="ce51b-186">Element testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ce51b-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="ce51b-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce51b-187">[C#], F#, VB</span></span> | <span data-ttu-id="ce51b-188">Test/NJednostka</span><span class="sxs-lookup"><span data-stu-id="ce51b-188">Test/NUnit</span></span>                            | <span data-ttu-id="ce51b-189">2.2</span><span class="sxs-lookup"><span data-stu-id="ce51b-189">2.2</span></span>        |
| <span data-ttu-id="ce51b-190">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="ce51b-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="ce51b-191">Xunit</span><span class="sxs-lookup"><span data-stu-id="ce51b-191">xunit</span></span>](#test)                  | <span data-ttu-id="ce51b-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ce51b-192">[C#], F#, VB</span></span> | <span data-ttu-id="ce51b-193">Test/jednostka xUnit</span><span class="sxs-lookup"><span data-stu-id="ce51b-193">Test/xUnit</span></span>                            | <span data-ttu-id="ce51b-194">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-194">1.0</span></span>        |
| <span data-ttu-id="ce51b-195">Komponent maszynki do golenia</span><span class="sxs-lookup"><span data-stu-id="ce51b-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="ce51b-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-196">[C#]</span></span>         | <span data-ttu-id="ce51b-197">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ce51b-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="ce51b-198">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-198">3.0</span></span>        |
| <span data-ttu-id="ce51b-199">Strona brzytwy</span><span class="sxs-lookup"><span data-stu-id="ce51b-199">Razor Page</span></span>                                   | [<span data-ttu-id="ce51b-200">Strona</span><span class="sxs-lookup"><span data-stu-id="ce51b-200">page</span></span>](#page)                   | <span data-ttu-id="ce51b-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-201">[C#]</span></span>         | <span data-ttu-id="ce51b-202">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ce51b-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="ce51b-203">2.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-203">2.0</span></span>        |
| <span data-ttu-id="ce51b-204">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="ce51b-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="ce51b-205">viewimports (import widoku)</span><span class="sxs-lookup"><span data-stu-id="ce51b-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="ce51b-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-206">[C#]</span></span>         | <span data-ttu-id="ce51b-207">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ce51b-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="ce51b-208">2.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-208">2.0</span></span>        |
| <span data-ttu-id="ce51b-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ce51b-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="ce51b-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-210">[C#]</span></span>         | <span data-ttu-id="ce51b-211">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ce51b-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="ce51b-212">2.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-212">2.0</span></span>        |
| <span data-ttu-id="ce51b-213">Aplikacja Blazor Server</span><span class="sxs-lookup"><span data-stu-id="ce51b-213">Blazor Server App</span></span>                            | [<span data-ttu-id="ce51b-214">serwer blazorserver</span><span class="sxs-lookup"><span data-stu-id="ce51b-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="ce51b-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-215">[C#]</span></span>         | <span data-ttu-id="ce51b-216">Strona internetowa/Blazor</span><span class="sxs-lookup"><span data-stu-id="ce51b-216">Web/Blazor</span></span>                            | <span data-ttu-id="ce51b-217">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-217">3.0</span></span>        |
| <span data-ttu-id="ce51b-218">ASP.NET Rdzeń pusty</span><span class="sxs-lookup"><span data-stu-id="ce51b-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="ce51b-219">Sieci web</span><span class="sxs-lookup"><span data-stu-id="ce51b-219">web</span></span>](#web)                     | <span data-ttu-id="ce51b-220">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ce51b-220">[C#], F#</span></span>     | <span data-ttu-id="ce51b-221">Sieć Web/Pusta</span><span class="sxs-lookup"><span data-stu-id="ce51b-221">Web/Empty</span></span>                             | <span data-ttu-id="ce51b-222">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-222">1.0</span></span>        |
| <span data-ttu-id="ce51b-223">ASP.NET Core Web App (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="ce51b-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="ce51b-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="ce51b-224">mvc</span></span>](#web-options)             | <span data-ttu-id="ce51b-225">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ce51b-225">[C#], F#</span></span>     | <span data-ttu-id="ce51b-226">Sieć Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ce51b-226">Web/MVC</span></span>                               | <span data-ttu-id="ce51b-227">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-227">1.0</span></span>        |
| <span data-ttu-id="ce51b-228">ASP.NET Podstawowa aplikacja sieci Web</span><span class="sxs-lookup"><span data-stu-id="ce51b-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="ce51b-229">webapp, brzytwa</span><span class="sxs-lookup"><span data-stu-id="ce51b-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="ce51b-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-230">[C#]</span></span>         | <span data-ttu-id="ce51b-231">Strony internetowe/MVC/Razor</span><span class="sxs-lookup"><span data-stu-id="ce51b-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="ce51b-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="ce51b-233">ASP.NET rdzeń z kanciastym</span><span class="sxs-lookup"><span data-stu-id="ce51b-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="ce51b-234">Kątowe</span><span class="sxs-lookup"><span data-stu-id="ce51b-234">angular</span></span>](#spa)                 | <span data-ttu-id="ce51b-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-235">[C#]</span></span>         | <span data-ttu-id="ce51b-236">Sieć Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ce51b-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ce51b-237">2.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-237">2.0</span></span>        |
| <span data-ttu-id="ce51b-238">ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="ce51b-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="ce51b-239">Reagować</span><span class="sxs-lookup"><span data-stu-id="ce51b-239">react</span></span>](#spa)                   | <span data-ttu-id="ce51b-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-240">[C#]</span></span>         | <span data-ttu-id="ce51b-241">Sieć Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ce51b-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ce51b-242">2.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-242">2.0</span></span>        |
| <span data-ttu-id="ce51b-243">ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="ce51b-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="ce51b-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="ce51b-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="ce51b-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-245">[C#]</span></span>         | <span data-ttu-id="ce51b-246">Sieć Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ce51b-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ce51b-247">2.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-247">2.0</span></span>        |
| <span data-ttu-id="ce51b-248">Biblioteka klas brzytwy</span><span class="sxs-lookup"><span data-stu-id="ce51b-248">Razor Class Library</span></span>                          | [<span data-ttu-id="ce51b-249">brzytwaclasslib</span><span class="sxs-lookup"><span data-stu-id="ce51b-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="ce51b-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-250">[C#]</span></span>         | <span data-ttu-id="ce51b-251">Biblioteka klas Web/Razor/Library/Razor</span><span class="sxs-lookup"><span data-stu-id="ce51b-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="ce51b-252">2.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-252">2.1</span></span>        |
| <span data-ttu-id="ce51b-253">Internetowy interfejs API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce51b-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="ce51b-254">Webapi</span><span class="sxs-lookup"><span data-stu-id="ce51b-254">webapi</span></span>](#webapi)               | <span data-ttu-id="ce51b-255">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ce51b-255">[C#], F#</span></span>     | <span data-ttu-id="ce51b-256">Witryna sieci Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ce51b-256">Web/WebAPI</span></span>                            | <span data-ttu-id="ce51b-257">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-257">1.0</span></span>        |
| <span data-ttu-id="ce51b-258">ASP.NET Podstawowa usługa gRPC</span><span class="sxs-lookup"><span data-stu-id="ce51b-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="ce51b-259">grpc (grpc)</span><span class="sxs-lookup"><span data-stu-id="ce51b-259">grpc</span></span>](#web-others)             | <span data-ttu-id="ce51b-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="ce51b-260">[C#]</span></span>         | <span data-ttu-id="ce51b-261">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ce51b-261">Web/gRPC</span></span>                              | <span data-ttu-id="ce51b-262">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-262">3.0</span></span>        |
| <span data-ttu-id="ce51b-263">Plik buforu protokołu</span><span class="sxs-lookup"><span data-stu-id="ce51b-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="ce51b-264">Proto</span><span class="sxs-lookup"><span data-stu-id="ce51b-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="ce51b-265">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ce51b-265">Web/gRPC</span></span>                              | <span data-ttu-id="ce51b-266">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-266">3.0</span></span>        |
| <span data-ttu-id="ce51b-267">dotnet gitignore plik</span><span class="sxs-lookup"><span data-stu-id="ce51b-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="ce51b-268">Config</span><span class="sxs-lookup"><span data-stu-id="ce51b-268">Config</span></span>                                | <span data-ttu-id="ce51b-269">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-269">3.0</span></span>        |
| <span data-ttu-id="ce51b-270">plik global.json</span><span class="sxs-lookup"><span data-stu-id="ce51b-270">global.json file</span></span>                             | [<span data-ttu-id="ce51b-271">globaljson (globaljson)</span><span class="sxs-lookup"><span data-stu-id="ce51b-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="ce51b-272">Config</span><span class="sxs-lookup"><span data-stu-id="ce51b-272">Config</span></span>                                | <span data-ttu-id="ce51b-273">2.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-273">2.0</span></span>        |
| <span data-ttu-id="ce51b-274">Konfigurator NuGet</span><span class="sxs-lookup"><span data-stu-id="ce51b-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="ce51b-275">Config</span><span class="sxs-lookup"><span data-stu-id="ce51b-275">Config</span></span>                                | <span data-ttu-id="ce51b-276">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-276">1.0</span></span>        |
| <span data-ttu-id="ce51b-277">dotnet plik manifestu narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="ce51b-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="ce51b-278">Config</span><span class="sxs-lookup"><span data-stu-id="ce51b-278">Config</span></span>                                | <span data-ttu-id="ce51b-279">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-279">3.0</span></span>        |
| <span data-ttu-id="ce51b-280">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="ce51b-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="ce51b-281">Config</span><span class="sxs-lookup"><span data-stu-id="ce51b-281">Config</span></span>                                | <span data-ttu-id="ce51b-282">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-282">1.0</span></span>        |
| <span data-ttu-id="ce51b-283">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ce51b-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="ce51b-284">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ce51b-284">Solution</span></span>                              | <span data-ttu-id="ce51b-285">1.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="ce51b-286">Opcje</span><span class="sxs-lookup"><span data-stu-id="ce51b-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="ce51b-287">Wyświetla podsumowanie tego, co by się stało, gdyby dane polecenie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="ce51b-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="ce51b-288">Dostępne od sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="ce51b-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="ce51b-289">Wymusza generowanie zawartości, nawet jeśli spowoduje to zmianę istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="ce51b-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ce51b-290">Jest to wymagane, gdy wybrany szablon zastąpi istniejące pliki w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="ce51b-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ce51b-291">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ce51b-291">Prints out help for the command.</span></span> <span data-ttu-id="ce51b-292">Można go wywołać `dotnet new` dla samego polecenia lub dla dowolnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="ce51b-293">Na przykład `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="ce51b-294">Instaluje pakiet szablonów z `PATH` lub `NUGET_ID` dostarczonego.</span><span class="sxs-lookup"><span data-stu-id="ce51b-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ce51b-295">Jeśli chcesz zainstalować wersję wwersji wstępnej pakietu szablonu, musisz określić `<package-name>::<package-version>`wersję w formacie .</span><span class="sxs-lookup"><span data-stu-id="ce51b-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ce51b-296">Domyślnie `dotnet new` przekazuje \* dla wersji, która reprezentuje najnowszą wersję pakietu stabilnego.</span><span class="sxs-lookup"><span data-stu-id="ce51b-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="ce51b-297">Zobacz przykład w sekcji [Przykłady.](#examples)</span><span class="sxs-lookup"><span data-stu-id="ce51b-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="ce51b-298">Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej stabilnej wersji, jeśli nie określono żadnej wersji.</span><span class="sxs-lookup"><span data-stu-id="ce51b-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="ce51b-299">Aby uzyskać informacje dotyczące tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ce51b-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="ce51b-300">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="ce51b-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="ce51b-301">Jeśli nie określono nazwy, wyświetla listę wszystkich szablonów.</span><span class="sxs-lookup"><span data-stu-id="ce51b-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="ce51b-302">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ce51b-302">The language of the template to create.</span></span> <span data-ttu-id="ce51b-303">Akceptowany język różni się w zależności od szablonu (zobacz ustawienia domyślne w sekcji [argumentów).](#arguments)</span><span class="sxs-lookup"><span data-stu-id="ce51b-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ce51b-304">Nie dotyczy niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ce51b-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ce51b-305">Niektóre skorupy `#` interpretują jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="ce51b-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ce51b-306">W takich przypadkach załączaj wartość parametru języka w cudzysłowie.</span><span class="sxs-lookup"><span data-stu-id="ce51b-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="ce51b-307">Na przykład `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="ce51b-308">Nazwa utworzonego wyjścia.</span><span class="sxs-lookup"><span data-stu-id="ce51b-308">The name for the created output.</span></span> <span data-ttu-id="ce51b-309">Jeśli nie określono nazwy, używana jest nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="ce51b-310">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="ce51b-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="ce51b-311">Dostępne od sdk .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="ce51b-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ce51b-312">Lokalizacja, aby umieścić wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ce51b-312">Location to place the generated output.</span></span> <span data-ttu-id="ce51b-313">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="ce51b-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="ce51b-314">Filtruje szablony na podstawie dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="ce51b-314">Filters templates based on available types.</span></span> <span data-ttu-id="ce51b-315">Wstępnie zdefiniowane wartości to "projekt", "element" lub "inny".</span><span class="sxs-lookup"><span data-stu-id="ce51b-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="ce51b-316">Odinstalowuje pakiet szablonów w dostarczonym `PATH` lub `NUGET_ID` dostarczonym.</span><span class="sxs-lookup"><span data-stu-id="ce51b-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ce51b-317">Jeśli `<PATH|NUGET_ID>` wartość nie jest określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="ce51b-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="ce51b-318">Określając `NUGET_ID`numer wersji, nie należy umieszczać.</span><span class="sxs-lookup"><span data-stu-id="ce51b-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="ce51b-319">Jeśli nie określisz parametru tej opcji, polecenie wyświetla listę zainstalowanych szablonów i szczegółowe informacje o nich.</span><span class="sxs-lookup"><span data-stu-id="ce51b-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ce51b-320">Aby odinstalować `PATH`szablon przy użyciu , musisz w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="ce51b-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ce51b-321">Na przykład *\<C:/Users/ USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="ce51b-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="ce51b-322">Nie należy uwzględniać końcowego ukośnika katalogu zakończenia na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="ce51b-323">Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane, i instaluje je.</span><span class="sxs-lookup"><span data-stu-id="ce51b-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="ce51b-324">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce51b-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="ce51b-325">Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ce51b-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="ce51b-326">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce51b-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="ce51b-327">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="ce51b-327">Template options</span></span>

<span data-ttu-id="ce51b-328">Każdy szablon projektu może mieć dodatkowe opcje dostępne.</span><span class="sxs-lookup"><span data-stu-id="ce51b-328">Each project template may have additional options available.</span></span> <span data-ttu-id="ce51b-329">Podstawowe szablony mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="ce51b-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="ce51b-330">console</span><span class="sxs-lookup"><span data-stu-id="ce51b-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-331">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-332">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce51b-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ce51b-333">W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:</span><span class="sxs-lookup"><span data-stu-id="ce51b-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce51b-334">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce51b-334">SDK version</span></span> | <span data-ttu-id="ce51b-335">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce51b-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce51b-336">3.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce51b-337">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ce51b-338">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ce51b-339">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="ce51b-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ce51b-340">Nie jest obsługiwana dla Języka F#.</span><span class="sxs-lookup"><span data-stu-id="ce51b-340">Not supported for F#.</span></span> <span data-ttu-id="ce51b-341">Dostępne od sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="ce51b-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce51b-342">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne ustawienia](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ce51b-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-343">Jeśli określono, nie wykonuje przywracanie niejawne podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="ce51b-344">Dostępne od sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="ce51b-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="ce51b-345">Classlib</span><span class="sxs-lookup"><span data-stu-id="ce51b-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-346">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-347">Wartości: `netcoreapp<version>` aby utworzyć bibliotekę klas `netstandard<version>` rdzenia .NET lub utworzyć bibliotekę klas standardowych .NET.</span><span class="sxs-lookup"><span data-stu-id="ce51b-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ce51b-348">Wartością domyślną jest `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ce51b-349">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ce51b-350">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="ce51b-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ce51b-351">Nie jest obsługiwana dla Języka F#.</span><span class="sxs-lookup"><span data-stu-id="ce51b-351">Not supported for F#.</span></span> <span data-ttu-id="ce51b-352">Dostępne od sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="ce51b-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce51b-353">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne ustawienia](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ce51b-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-354">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="ce51b-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ce51b-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-356">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-357">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ce51b-358">Dostępne od sdk .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="ce51b-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ce51b-359">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ce51b-360">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="ce51b-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ce51b-361">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne ustawienia](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ce51b-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-362">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="ce51b-363">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="ce51b-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ce51b-364">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ce51b-365">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="ce51b-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ce51b-366">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne ustawienia](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ce51b-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-367">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="ce51b-368">pracownik, grpc</span><span class="sxs-lookup"><span data-stu-id="ce51b-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-369">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-370">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ce51b-371">Dostępne od sdk .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="ce51b-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce51b-372">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-373">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="ce51b-374">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="ce51b-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-375">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-376">Opcja dostępna od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce51b-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ce51b-377">W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:</span><span class="sxs-lookup"><span data-stu-id="ce51b-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce51b-378">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce51b-378">SDK version</span></span> | <span data-ttu-id="ce51b-379">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce51b-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce51b-380">3.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce51b-381">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ce51b-382">Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ce51b-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-383">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="ce51b-384">Nunit</span><span class="sxs-lookup"><span data-stu-id="ce51b-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-385">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="ce51b-386">W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:</span><span class="sxs-lookup"><span data-stu-id="ce51b-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce51b-387">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce51b-387">SDK version</span></span> | <span data-ttu-id="ce51b-388">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce51b-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce51b-389">3.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce51b-390">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce51b-391">2.2</span><span class="sxs-lookup"><span data-stu-id="ce51b-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="ce51b-392">2.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ce51b-393">Umożliwia pakowanie dla projektu przy użyciu [pakietu dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ce51b-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-394">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="ce51b-395">Strona</span><span class="sxs-lookup"><span data-stu-id="ce51b-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ce51b-396">Obszar nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-396">Namespace for the generated code.</span></span> <span data-ttu-id="ce51b-397">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="ce51b-398">Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ce51b-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="ce51b-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="ce51b-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ce51b-400">Obszar nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-400">Namespace for the generated code.</span></span> <span data-ttu-id="ce51b-401">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="ce51b-402">serwer blazorserver</span><span class="sxs-lookup"><span data-stu-id="ce51b-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ce51b-403">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ce51b-403">The type of authentication to use.</span></span> <span data-ttu-id="ce51b-404">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ce51b-404">The possible values are:</span></span>

  - <span data-ttu-id="ce51b-405">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="ce51b-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ce51b-406">`Individual`- Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="ce51b-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ce51b-407">`IndividualB2C`- Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ce51b-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ce51b-408">`SingleOrg`- Uwierzytelnianie organizacyjne dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ce51b-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ce51b-409">`MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="ce51b-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ce51b-410">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ce51b-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ce51b-411">Wystąpienie usługi Azure Active Directory B2C, z którym chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ce51b-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ce51b-412">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce51b-413">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ce51b-414">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ce51b-415">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ce51b-416">Identyfikator zasad resetowania haseł dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="ce51b-417">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ce51b-418">Identyfikator zasad profilu edit dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ce51b-419">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ce51b-420">Wystąpienie usługi Azure Active Directory, z którym chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ce51b-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ce51b-421">Użyj `SingleOrg` z `MultiOrg` uwierzytelnianiem lub uwierzytelniaj.</span><span class="sxs-lookup"><span data-stu-id="ce51b-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce51b-422">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ce51b-423">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-423">The Client ID for this project.</span></span> <span data-ttu-id="ce51b-424">Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce51b-425">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ce51b-426">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-426">The domain for the directory tenant.</span></span> <span data-ttu-id="ce51b-427">Użyj `SingleOrg` z `IndividualB2C` uwierzytelnianiem lub uwierzytelniaj.</span><span class="sxs-lookup"><span data-stu-id="ce51b-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce51b-428">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ce51b-429">Identyfikator identyfikatora tenantid katalogu, z którymi chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ce51b-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ce51b-430">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce51b-431">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ce51b-432">Ścieżka żądania w ścieżce podstawowej aplikacji identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ce51b-433">Użyj `SingleOrg` z `IndividualB2C` uwierzytelnianiem lub uwierzytelniaj.</span><span class="sxs-lookup"><span data-stu-id="ce51b-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce51b-434">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ce51b-435">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ce51b-436">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce51b-437">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce51b-438">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce51b-438">Turns off HTTPS.</span></span> <span data-ttu-id="ce51b-439">Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , `--auth`, , lub nie są używane do .</span><span class="sxs-lookup"><span data-stu-id="ce51b-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ce51b-440">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="ce51b-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce51b-441">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-442">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="ce51b-443">web</span><span class="sxs-lookup"><span data-stu-id="ce51b-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce51b-444">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-445">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-446">Opcja nie jest dostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="ce51b-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce51b-447">W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:</span><span class="sxs-lookup"><span data-stu-id="ce51b-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce51b-448">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce51b-448">SDK version</span></span> | <span data-ttu-id="ce51b-449">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce51b-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce51b-450">3.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce51b-451">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce51b-452">2.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ce51b-453">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce51b-454">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce51b-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="ce51b-455">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="ce51b-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ce51b-456">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ce51b-456">The type of authentication to use.</span></span> <span data-ttu-id="ce51b-457">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ce51b-457">The possible values are:</span></span>

  - <span data-ttu-id="ce51b-458">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="ce51b-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ce51b-459">`Individual`- Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="ce51b-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ce51b-460">`IndividualB2C`- Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ce51b-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ce51b-461">`SingleOrg`- Uwierzytelnianie organizacyjne dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ce51b-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ce51b-462">`MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="ce51b-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ce51b-463">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ce51b-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ce51b-464">Wystąpienie usługi Azure Active Directory B2C, z którym chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ce51b-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ce51b-465">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce51b-466">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ce51b-467">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ce51b-468">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ce51b-469">Identyfikator zasad resetowania haseł dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="ce51b-470">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ce51b-471">Identyfikator zasad profilu edit dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ce51b-472">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ce51b-473">Wystąpienie usługi Azure Active Directory, z którym chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ce51b-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ce51b-474">Użyj `SingleOrg` z `MultiOrg` uwierzytelnianiem lub uwierzytelniaj.</span><span class="sxs-lookup"><span data-stu-id="ce51b-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce51b-475">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ce51b-476">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-476">The Client ID for this project.</span></span> <span data-ttu-id="ce51b-477">Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce51b-478">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ce51b-479">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-479">The domain for the directory tenant.</span></span> <span data-ttu-id="ce51b-480">Użyj `SingleOrg` z `IndividualB2C` uwierzytelnianiem lub uwierzytelniaj.</span><span class="sxs-lookup"><span data-stu-id="ce51b-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce51b-481">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ce51b-482">Identyfikator identyfikatora tenantid katalogu, z którymi chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ce51b-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ce51b-483">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce51b-484">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ce51b-485">Ścieżka żądania w ścieżce podstawowej aplikacji identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ce51b-486">Użyj `SingleOrg` z `IndividualB2C` uwierzytelnianiem lub uwierzytelniaj.</span><span class="sxs-lookup"><span data-stu-id="ce51b-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce51b-487">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ce51b-488">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ce51b-489">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce51b-490">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce51b-491">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce51b-491">Turns off HTTPS.</span></span> <span data-ttu-id="ce51b-492">Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , , , lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="ce51b-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ce51b-493">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="ce51b-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce51b-494">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-495">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-496">Opcja dostępna od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce51b-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ce51b-497">W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:</span><span class="sxs-lookup"><span data-stu-id="ce51b-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce51b-498">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce51b-498">SDK version</span></span> | <span data-ttu-id="ce51b-499">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce51b-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce51b-500">3.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce51b-501">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="ce51b-502">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="ce51b-503">Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ce51b-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="ce51b-504">Opcja nie jest dostępna w sdk .NET Core 2.2 i 3.1.</span><span class="sxs-lookup"><span data-stu-id="ce51b-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="ce51b-505">kątowe, reagować</span><span class="sxs-lookup"><span data-stu-id="ce51b-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ce51b-506">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ce51b-506">The type of authentication to use.</span></span> <span data-ttu-id="ce51b-507">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce51b-507">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="ce51b-508">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ce51b-508">The possible values are:</span></span>

  - <span data-ttu-id="ce51b-509">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="ce51b-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ce51b-510">`Individual`- Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="ce51b-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce51b-511">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-511">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-512">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce51b-513">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce51b-513">Turns off HTTPS.</span></span> <span data-ttu-id="ce51b-514">Ta opcja ma zastosowanie `None`tylko wtedy, gdy uwierzytelnianie jest .</span><span class="sxs-lookup"><span data-stu-id="ce51b-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ce51b-515">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="ce51b-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce51b-516">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce51b-517">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce51b-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-518">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-519">Opcja nie jest dostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="ce51b-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce51b-520">W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:</span><span class="sxs-lookup"><span data-stu-id="ce51b-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce51b-521">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce51b-521">SDK version</span></span> | <span data-ttu-id="ce51b-522">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce51b-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce51b-523">3.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce51b-524">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce51b-525">2.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="ce51b-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="ce51b-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce51b-527">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-527">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-528">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-529">Opcja nie jest dostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="ce51b-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce51b-530">W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:</span><span class="sxs-lookup"><span data-stu-id="ce51b-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce51b-531">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce51b-531">SDK version</span></span> | <span data-ttu-id="ce51b-532">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce51b-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce51b-533">3.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce51b-534">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce51b-535">2.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="ce51b-536">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce51b-537">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce51b-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="ce51b-538">brzytwaclasslib</span><span class="sxs-lookup"><span data-stu-id="ce51b-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce51b-539">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="ce51b-540">Obsługuje dodawanie tradycyjnych stron razor i widoki oprócz składników do tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ce51b-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="ce51b-541">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce51b-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="ce51b-542">Webapi</span><span class="sxs-lookup"><span data-stu-id="ce51b-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ce51b-543">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ce51b-543">The type of authentication to use.</span></span> <span data-ttu-id="ce51b-544">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ce51b-544">The possible values are:</span></span>

  - <span data-ttu-id="ce51b-545">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="ce51b-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ce51b-546">`IndividualB2C`- Uwierzytelnianie indywidualne za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ce51b-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ce51b-547">`SingleOrg`- Uwierzytelnianie organizacyjne dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ce51b-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ce51b-548">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ce51b-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ce51b-549">Wystąpienie usługi Azure Active Directory B2C, z którym chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ce51b-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ce51b-550">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce51b-551">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ce51b-552">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ce51b-553">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ce51b-554">Wystąpienie usługi Azure Active Directory, z którym chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ce51b-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ce51b-555">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce51b-556">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ce51b-557">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-557">The Client ID for this project.</span></span> <span data-ttu-id="ce51b-558">Użyj `IndividualB2C` z `SingleOrg` uwierzytelnianiem lub uwierzytelniaj.</span><span class="sxs-lookup"><span data-stu-id="ce51b-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ce51b-559">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ce51b-560">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-560">The domain for the directory tenant.</span></span> <span data-ttu-id="ce51b-561">Użyj `IndividualB2C` z `SingleOrg` uwierzytelnianiem lub uwierzytelniaj.</span><span class="sxs-lookup"><span data-stu-id="ce51b-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ce51b-562">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ce51b-563">Identyfikator identyfikatora tenantid katalogu, z którymi chcesz się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ce51b-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ce51b-564">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce51b-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce51b-565">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ce51b-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ce51b-566">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ce51b-567">Dotyczy tylko `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce51b-568">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce51b-569">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce51b-569">Turns off HTTPS.</span></span> <span data-ttu-id="ce51b-570">`app.UseHsts`i `app.UseHttpsRedirection` nie są `Startup.Configure`dodawane do .</span><span class="sxs-lookup"><span data-stu-id="ce51b-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ce51b-571">Ta opcja ma `IndividualB2C` zastosowanie `SingleOrg` tylko wtedy, gdy nie są używane do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ce51b-572">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="ce51b-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce51b-573">Dotyczy tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce51b-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce51b-574">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce51b-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce51b-575">Opcja nie jest dostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="ce51b-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce51b-576">W poniższej tabeli wymieniono wartości domyślne zgodnie z numerem wersji sdk, którego używasz:</span><span class="sxs-lookup"><span data-stu-id="ce51b-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce51b-577">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce51b-577">SDK version</span></span> | <span data-ttu-id="ce51b-578">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce51b-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce51b-579">3.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce51b-580">3.0</span><span class="sxs-lookup"><span data-stu-id="ce51b-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce51b-581">2.1</span><span class="sxs-lookup"><span data-stu-id="ce51b-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ce51b-582">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce51b-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="ce51b-583">globaljson (globaljson)</span><span class="sxs-lookup"><span data-stu-id="ce51b-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="ce51b-584">Określa wersję sdk .NET Core do użycia w pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="ce51b-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="ce51b-585">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ce51b-585">Examples</span></span>

- <span data-ttu-id="ce51b-586">Utwórz projekt aplikacji konsoli C#, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="ce51b-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="ce51b-587">Utwórz projekt aplikacji konsoli F# w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ce51b-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="ce51b-588">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ce51b-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="ce51b-589">Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="ce51b-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="ce51b-590">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="ce51b-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="ce51b-591">Lista wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):</span><span class="sxs-lookup"><span data-stu-id="ce51b-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="ce51b-592">Lista wszystkich szablonów pasujących *do podciągu we.*</span><span class="sxs-lookup"><span data-stu-id="ce51b-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="ce51b-593">Nie znaleziono dokładnego dopasowania, więc dopasowanie podciągów jest uruchamiane zarówno względem kolumn krótkiej nazwy, jak i nazwy.</span><span class="sxs-lookup"><span data-stu-id="ce51b-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="ce51b-594">Spróbuj wywołać szablon pasujący *ng*.</span><span class="sxs-lookup"><span data-stu-id="ce51b-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="ce51b-595">Jeśli nie można określić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są częściowymi dopasowaniami.</span><span class="sxs-lookup"><span data-stu-id="ce51b-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="ce51b-596">Zainstaluj wersję 2.0 szablonów SPA dla ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="ce51b-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="ce51b-597">Lista zainstalowanych szablonów i szczegóły na ich temat, w tym jak je odinstalować:</span><span class="sxs-lookup"><span data-stu-id="ce51b-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="ce51b-598">Utwórz *global.json* w bieżącym katalogu, ustawiając wersję sdk na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="ce51b-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="ce51b-599">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce51b-599">See also</span></span>

- [<span data-ttu-id="ce51b-600">Szablony niestandardowe dla dotnet nowy</span><span class="sxs-lookup"><span data-stu-id="ce51b-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="ce51b-601">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="ce51b-601">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="ce51b-602">dotnet/dotnet-template-samples GitHub repo</span><span class="sxs-lookup"><span data-stu-id="ce51b-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="ce51b-603">Dostępne szablony dla dotnet nowych</span><span class="sxs-lookup"><span data-stu-id="ce51b-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
