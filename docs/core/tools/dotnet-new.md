---
title: dotnet nowe polecenie
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu.
ms.date: 04/10/2020
ms.openlocfilehash: 1b1a6efa7bf2753b6c23cc7af1e26867f8632b96
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242884"
---
# <a name="dotnet-new"></a><span data-ttu-id="75366-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="75366-103">dotnet new</span></span>

<span data-ttu-id="75366-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="75366-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="75366-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="75366-105">Name</span></span>

<span data-ttu-id="75366-106">`dotnet new`- Tworzy nowy projekt, plik konfiguracyjny lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="75366-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="75366-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="75366-108">Opis</span><span class="sxs-lookup"><span data-stu-id="75366-108">Description</span></span>

<span data-ttu-id="75366-109">Polecenie `dotnet new` tworzy projekt .NET Core lub inne artefakty oparte na szablonie.</span><span class="sxs-lookup"><span data-stu-id="75366-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="75366-110">Polecenie wywołuje [aparat szablonów,](https://github.com/dotnet/templating) aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="75366-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="75366-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="75366-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="75366-112">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="75366-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="75366-113">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="75366-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="75366-114">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="75366-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="75366-115">Można uruchomić, `dotnet new --list` aby wyświetlić listę wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="75366-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="75366-116">Jeśli `TEMPLATE` wartość nie jest dokładne dopasowanie tekstu w **szablony** lub **nazwa skrócona** kolumny z tabeli zwracanej, dopasowanie podciąg jest wykonywane na tych dwóch kolumnach.</span><span class="sxs-lookup"><span data-stu-id="75366-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="75366-117">Począwszy od pliku .NET Core 3.0 SDK, funkcja CLI wyszukuje szablony w NuGet.org podczas wywoływania `dotnet new` polecenia w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="75366-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="75366-118">Jeśli cli nie można znaleźć dopasowania szablonu podczas wywoływania `dotnet new`, nawet częściowe.</span><span class="sxs-lookup"><span data-stu-id="75366-118">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="75366-119">Jeśli dostępna jest nowsza wersja szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-119">If there's a newer version of the template available.</span></span> <span data-ttu-id="75366-120">W takim przypadku tworzony jest projekt lub artefakt, ale cli ostrzega o zaktualizowanej wersji szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="75366-121">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="75366-121">The command contains a default list of templates.</span></span> <span data-ttu-id="75366-122">Służy `dotnet new -l` do uzyskiwania listy dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="75366-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="75366-123">W poniższej tabeli przedstawiono szablony, które są fabrycznie zainstalowane z pakietem .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="75366-124">Domyślny język szablonu jest wyświetlany wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="75366-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="75366-125">Kliknij łącze do krótkiej nazwy, aby wyświetlić określone opcje szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="75366-126">Szablony</span><span class="sxs-lookup"><span data-stu-id="75366-126">Templates</span></span>                                    | <span data-ttu-id="75366-127">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="75366-127">Short name</span></span>                      | <span data-ttu-id="75366-128">Język</span><span class="sxs-lookup"><span data-stu-id="75366-128">Language</span></span>     | <span data-ttu-id="75366-129">Tagi</span><span class="sxs-lookup"><span data-stu-id="75366-129">Tags</span></span>                                  | <span data-ttu-id="75366-130">Wprowadzone</span><span class="sxs-lookup"><span data-stu-id="75366-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="75366-131">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="75366-131">Console Application</span></span>                          | [<span data-ttu-id="75366-132">Konsoli</span><span class="sxs-lookup"><span data-stu-id="75366-132">console</span></span>](#console)             | <span data-ttu-id="75366-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75366-133">[C#], F#, VB</span></span> | <span data-ttu-id="75366-134">Wspólne/konsolowe</span><span class="sxs-lookup"><span data-stu-id="75366-134">Common/Console</span></span>                        | <span data-ttu-id="75366-135">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-135">1.0</span></span>        |
| <span data-ttu-id="75366-136">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="75366-136">Class library</span></span>                                | [<span data-ttu-id="75366-137">Classlib</span><span class="sxs-lookup"><span data-stu-id="75366-137">classlib</span></span>](#classlib)           | <span data-ttu-id="75366-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75366-138">[C#], F#, VB</span></span> | <span data-ttu-id="75366-139">Wspólne/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="75366-139">Common/Library</span></span>                        | <span data-ttu-id="75366-140">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-140">1.0</span></span>        |
| <span data-ttu-id="75366-141">Aplikacja WPF</span><span class="sxs-lookup"><span data-stu-id="75366-141">WPF Application</span></span>                              | [<span data-ttu-id="75366-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="75366-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="75366-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-143">[C#]</span></span>         | <span data-ttu-id="75366-144">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="75366-144">Common/WPF</span></span>                            | <span data-ttu-id="75366-145">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-145">3.0</span></span>        |
| <span data-ttu-id="75366-146">Biblioteka klas WPF</span><span class="sxs-lookup"><span data-stu-id="75366-146">WPF Class library</span></span>                            | [<span data-ttu-id="75366-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="75366-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="75366-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-148">[C#]</span></span>         | <span data-ttu-id="75366-149">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="75366-149">Common/WPF</span></span>                            | <span data-ttu-id="75366-150">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-150">3.0</span></span>        |
| <span data-ttu-id="75366-151">Biblioteka kontrolek niestandardowych WPF</span><span class="sxs-lookup"><span data-stu-id="75366-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="75366-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="75366-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="75366-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-153">[C#]</span></span>         | <span data-ttu-id="75366-154">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="75366-154">Common/WPF</span></span>                            | <span data-ttu-id="75366-155">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-155">3.0</span></span>        |
| <span data-ttu-id="75366-156">Biblioteka kontroli użytkownika WPF</span><span class="sxs-lookup"><span data-stu-id="75366-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="75366-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="75366-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="75366-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-158">[C#]</span></span>         | <span data-ttu-id="75366-159">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="75366-159">Common/WPF</span></span>                            | <span data-ttu-id="75366-160">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-160">3.0</span></span>        |
| <span data-ttu-id="75366-161">Aplikacja Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="75366-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="75366-162">Winforms</span><span class="sxs-lookup"><span data-stu-id="75366-162">winforms</span></span>](#winforms)           | <span data-ttu-id="75366-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-163">[C#]</span></span>         | <span data-ttu-id="75366-164">Wspólne/WinForms</span><span class="sxs-lookup"><span data-stu-id="75366-164">Common/WinForms</span></span>                       | <span data-ttu-id="75366-165">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-165">3.0</span></span>        |
| <span data-ttu-id="75366-166">Biblioteka klas formularzy Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="75366-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="75366-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="75366-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="75366-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-168">[C#]</span></span>         | <span data-ttu-id="75366-169">Wspólne/WinForms</span><span class="sxs-lookup"><span data-stu-id="75366-169">Common/WinForms</span></span>                       | <span data-ttu-id="75366-170">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-170">3.0</span></span>        |
| <span data-ttu-id="75366-171">Usługa dla pracowników</span><span class="sxs-lookup"><span data-stu-id="75366-171">Worker Service</span></span>                               | [<span data-ttu-id="75366-172">Pracownik</span><span class="sxs-lookup"><span data-stu-id="75366-172">worker</span></span>](#web-others)           | <span data-ttu-id="75366-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-173">[C#]</span></span>         | <span data-ttu-id="75366-174">Często/Pracownik/Sieć Web</span><span class="sxs-lookup"><span data-stu-id="75366-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="75366-175">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-175">3.0</span></span>        |
| <span data-ttu-id="75366-176">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="75366-176">Unit Test Project</span></span>                            | [<span data-ttu-id="75366-177">Mstest</span><span class="sxs-lookup"><span data-stu-id="75366-177">mstest</span></span>](#test)                 | <span data-ttu-id="75366-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75366-178">[C#], F#, VB</span></span> | <span data-ttu-id="75366-179">Test/TEST MSTest</span><span class="sxs-lookup"><span data-stu-id="75366-179">Test/MSTest</span></span>                           | <span data-ttu-id="75366-180">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-180">1.0</span></span>        |
| <span data-ttu-id="75366-181">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="75366-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="75366-182">Nunit</span><span class="sxs-lookup"><span data-stu-id="75366-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="75366-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75366-183">[C#], F#, VB</span></span> | <span data-ttu-id="75366-184">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="75366-184">Test/NUnit</span></span>                            | <span data-ttu-id="75366-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="75366-185">2.1.400</span></span>    |
| <span data-ttu-id="75366-186">NUnit 3 Przedmiot testowy</span><span class="sxs-lookup"><span data-stu-id="75366-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="75366-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75366-187">[C#], F#, VB</span></span> | <span data-ttu-id="75366-188">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="75366-188">Test/NUnit</span></span>                            | <span data-ttu-id="75366-189">2.2</span><span class="sxs-lookup"><span data-stu-id="75366-189">2.2</span></span>        |
| <span data-ttu-id="75366-190">xUnit Projekt testowy</span><span class="sxs-lookup"><span data-stu-id="75366-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="75366-191">Xunit</span><span class="sxs-lookup"><span data-stu-id="75366-191">xunit</span></span>](#test)                  | <span data-ttu-id="75366-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="75366-192">[C#], F#, VB</span></span> | <span data-ttu-id="75366-193">Test/xJednostka</span><span class="sxs-lookup"><span data-stu-id="75366-193">Test/xUnit</span></span>                            | <span data-ttu-id="75366-194">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-194">1.0</span></span>        |
| <span data-ttu-id="75366-195">Komponent maszynki do golenia</span><span class="sxs-lookup"><span data-stu-id="75366-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="75366-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-196">[C#]</span></span>         | <span data-ttu-id="75366-197">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75366-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="75366-198">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-198">3.0</span></span>        |
| <span data-ttu-id="75366-199">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="75366-199">Razor Page</span></span>                                   | [<span data-ttu-id="75366-200">Strona</span><span class="sxs-lookup"><span data-stu-id="75366-200">page</span></span>](#page)                   | <span data-ttu-id="75366-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-201">[C#]</span></span>         | <span data-ttu-id="75366-202">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75366-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="75366-203">2.0</span><span class="sxs-lookup"><span data-stu-id="75366-203">2.0</span></span>        |
| <span data-ttu-id="75366-204">Porty widoków MVC</span><span class="sxs-lookup"><span data-stu-id="75366-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="75366-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="75366-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="75366-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-206">[C#]</span></span>         | <span data-ttu-id="75366-207">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75366-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="75366-208">2.0</span><span class="sxs-lookup"><span data-stu-id="75366-208">2.0</span></span>        |
| <span data-ttu-id="75366-209">Początek widoku MVC</span><span class="sxs-lookup"><span data-stu-id="75366-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="75366-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-210">[C#]</span></span>         | <span data-ttu-id="75366-211">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="75366-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="75366-212">2.0</span><span class="sxs-lookup"><span data-stu-id="75366-212">2.0</span></span>        |
| <span data-ttu-id="75366-213">Aplikacja serwera Blazor</span><span class="sxs-lookup"><span data-stu-id="75366-213">Blazor Server App</span></span>                            | [<span data-ttu-id="75366-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="75366-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="75366-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-215">[C#]</span></span>         | <span data-ttu-id="75366-216">Sieć Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="75366-216">Web/Blazor</span></span>                            | <span data-ttu-id="75366-217">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-217">3.0</span></span>        |
| <span data-ttu-id="75366-218">ASP.NET rdzeń pusty</span><span class="sxs-lookup"><span data-stu-id="75366-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="75366-219">Sieci web</span><span class="sxs-lookup"><span data-stu-id="75366-219">web</span></span>](#web)                     | <span data-ttu-id="75366-220">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="75366-220">[C#], F#</span></span>     | <span data-ttu-id="75366-221">Sieć Web/Puste</span><span class="sxs-lookup"><span data-stu-id="75366-221">Web/Empty</span></span>                             | <span data-ttu-id="75366-222">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-222">1.0</span></span>        |
| <span data-ttu-id="75366-223">ASP.NET Core Web App (kontroler widoku modelu)</span><span class="sxs-lookup"><span data-stu-id="75366-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="75366-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="75366-224">mvc</span></span>](#web-options)             | <span data-ttu-id="75366-225">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="75366-225">[C#], F#</span></span>     | <span data-ttu-id="75366-226">Sieć Web/MVC</span><span class="sxs-lookup"><span data-stu-id="75366-226">Web/MVC</span></span>                               | <span data-ttu-id="75366-227">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-227">1.0</span></span>        |
| <span data-ttu-id="75366-228">ASP.NET podstawowa aplikacja sieci Web</span><span class="sxs-lookup"><span data-stu-id="75366-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="75366-229">webapp, brzytwa</span><span class="sxs-lookup"><span data-stu-id="75366-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="75366-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-230">[C#]</span></span>         | <span data-ttu-id="75366-231">Strony internetowe/MVC/Brzytwa</span><span class="sxs-lookup"><span data-stu-id="75366-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="75366-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="75366-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="75366-233">ASP.NET rdzeń z kątowym</span><span class="sxs-lookup"><span data-stu-id="75366-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="75366-234">Kątowe</span><span class="sxs-lookup"><span data-stu-id="75366-234">angular</span></span>](#spa)                 | <span data-ttu-id="75366-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-235">[C#]</span></span>         | <span data-ttu-id="75366-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="75366-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="75366-237">2.0</span><span class="sxs-lookup"><span data-stu-id="75366-237">2.0</span></span>        |
| <span data-ttu-id="75366-238">ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="75366-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="75366-239">Reagować</span><span class="sxs-lookup"><span data-stu-id="75366-239">react</span></span>](#spa)                   | <span data-ttu-id="75366-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-240">[C#]</span></span>         | <span data-ttu-id="75366-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="75366-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="75366-242">2.0</span><span class="sxs-lookup"><span data-stu-id="75366-242">2.0</span></span>        |
| <span data-ttu-id="75366-243">ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="75366-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="75366-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="75366-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="75366-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-245">[C#]</span></span>         | <span data-ttu-id="75366-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="75366-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="75366-247">2.0</span><span class="sxs-lookup"><span data-stu-id="75366-247">2.0</span></span>        |
| <span data-ttu-id="75366-248">Biblioteka klas razor</span><span class="sxs-lookup"><span data-stu-id="75366-248">Razor Class Library</span></span>                          | [<span data-ttu-id="75366-249">brzytwaklasyb</span><span class="sxs-lookup"><span data-stu-id="75366-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="75366-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-250">[C#]</span></span>         | <span data-ttu-id="75366-251">Web/ Razor/Biblioteka/Razor Klasa Biblioteka</span><span class="sxs-lookup"><span data-stu-id="75366-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="75366-252">2.1</span><span class="sxs-lookup"><span data-stu-id="75366-252">2.1</span></span>        |
| <span data-ttu-id="75366-253">Internetowy interfejs API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="75366-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="75366-254">Webapi</span><span class="sxs-lookup"><span data-stu-id="75366-254">webapi</span></span>](#webapi)               | <span data-ttu-id="75366-255">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="75366-255">[C#], F#</span></span>     | <span data-ttu-id="75366-256">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="75366-256">Web/WebAPI</span></span>                            | <span data-ttu-id="75366-257">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-257">1.0</span></span>        |
| <span data-ttu-id="75366-258">ASP.NET podstawowa usługa gRPC</span><span class="sxs-lookup"><span data-stu-id="75366-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="75366-259">grpc (grpc)</span><span class="sxs-lookup"><span data-stu-id="75366-259">grpc</span></span>](#web-others)             | <span data-ttu-id="75366-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="75366-260">[C#]</span></span>         | <span data-ttu-id="75366-261">Sieć/gRPC</span><span class="sxs-lookup"><span data-stu-id="75366-261">Web/gRPC</span></span>                              | <span data-ttu-id="75366-262">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-262">3.0</span></span>        |
| <span data-ttu-id="75366-263">Plik buforu protokołu</span><span class="sxs-lookup"><span data-stu-id="75366-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="75366-264">Proto</span><span class="sxs-lookup"><span data-stu-id="75366-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="75366-265">Sieć/gRPC</span><span class="sxs-lookup"><span data-stu-id="75366-265">Web/gRPC</span></span>                              | <span data-ttu-id="75366-266">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-266">3.0</span></span>        |
| <span data-ttu-id="75366-267">plik dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="75366-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="75366-268">Config</span><span class="sxs-lookup"><span data-stu-id="75366-268">Config</span></span>                                | <span data-ttu-id="75366-269">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-269">3.0</span></span>        |
| <span data-ttu-id="75366-270">plik global.json</span><span class="sxs-lookup"><span data-stu-id="75366-270">global.json file</span></span>                             | [<span data-ttu-id="75366-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="75366-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="75366-272">Config</span><span class="sxs-lookup"><span data-stu-id="75366-272">Config</span></span>                                | <span data-ttu-id="75366-273">2.0</span><span class="sxs-lookup"><span data-stu-id="75366-273">2.0</span></span>        |
| <span data-ttu-id="75366-274">Konfiguracja NuGet</span><span class="sxs-lookup"><span data-stu-id="75366-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="75366-275">Config</span><span class="sxs-lookup"><span data-stu-id="75366-275">Config</span></span>                                | <span data-ttu-id="75366-276">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-276">1.0</span></span>        |
| <span data-ttu-id="75366-277">plik manifestu narzędzia lokalnego dotnet</span><span class="sxs-lookup"><span data-stu-id="75366-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="75366-278">Config</span><span class="sxs-lookup"><span data-stu-id="75366-278">Config</span></span>                                | <span data-ttu-id="75366-279">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-279">3.0</span></span>        |
| <span data-ttu-id="75366-280">Konfigurga internetowa</span><span class="sxs-lookup"><span data-stu-id="75366-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="75366-281">Config</span><span class="sxs-lookup"><span data-stu-id="75366-281">Config</span></span>                                | <span data-ttu-id="75366-282">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-282">1.0</span></span>        |
| <span data-ttu-id="75366-283">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="75366-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="75366-284">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="75366-284">Solution</span></span>                              | <span data-ttu-id="75366-285">1.0</span><span class="sxs-lookup"><span data-stu-id="75366-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="75366-286">Opcje</span><span class="sxs-lookup"><span data-stu-id="75366-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="75366-287">Wyświetla podsumowanie tego, co by się stało, gdyby dane polecenie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="75366-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="75366-288">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="75366-289">Wymusza generowanie zawartości, nawet jeśli spowoduje to zmianę istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="75366-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="75366-290">Jest to wymagane, gdy wybrany szablon zastąpi istniejące pliki w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="75366-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="75366-291">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="75366-291">Prints out help for the command.</span></span> <span data-ttu-id="75366-292">Można go wywołać `dotnet new` dla samego polecenia lub dla dowolnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="75366-293">Na przykład `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="75366-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="75366-294">Instaluje pakiet `PATH` szablonów `NUGET_ID` z lub dostarczone.</span><span class="sxs-lookup"><span data-stu-id="75366-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="75366-295">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w `<package-name>::<package-version>`formacie .</span><span class="sxs-lookup"><span data-stu-id="75366-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="75366-296">Domyślnie `dotnet new` przechodzi \* do wersji, która reprezentuje najnowszą stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="75366-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="75366-297">Zobacz przykład w sekcji [Przykłady.](#examples)</span><span class="sxs-lookup"><span data-stu-id="75366-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="75366-298">Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej wersji stabilnej, jeśli nie określono żadnej wersji.</span><span class="sxs-lookup"><span data-stu-id="75366-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="75366-299">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="75366-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="75366-300">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="75366-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="75366-301">Jeśli nazwa nie zostanie określona, wyświetla listę wszystkich szablonów.</span><span class="sxs-lookup"><span data-stu-id="75366-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="75366-302">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="75366-302">The language of the template to create.</span></span> <span data-ttu-id="75366-303">Akceptowany język różni się w zależności od szablonu (zobacz wartości domyślne w sekcji [argumenty).](#arguments)</span><span class="sxs-lookup"><span data-stu-id="75366-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="75366-304">Nie dotyczy niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="75366-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="75366-305">Niektóre skorupy `#` interpretują jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="75366-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="75366-306">W takich przypadkach należy ująć wartość parametru języka w cudzysłowach.</span><span class="sxs-lookup"><span data-stu-id="75366-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="75366-307">Na przykład `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="75366-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="75366-308">Nazwa utworzonego wyjścia.</span><span class="sxs-lookup"><span data-stu-id="75366-308">The name for the created output.</span></span> <span data-ttu-id="75366-309">Jeśli nazwa nie zostanie określona, używana jest nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="75366-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="75366-310">Określa źródło NuGet, które ma być używane podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="75366-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="75366-311">Dostępne od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="75366-312">Lokalizacja, aby umieścić wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="75366-312">Location to place the generated output.</span></span> <span data-ttu-id="75366-313">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="75366-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="75366-314">Filtruje szablony na podstawie dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="75366-314">Filters templates based on available types.</span></span> <span data-ttu-id="75366-315">Wstępnie zdefiniowane wartości to "projekt", "element" lub "inny".</span><span class="sxs-lookup"><span data-stu-id="75366-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="75366-316">Odinstalowuje pakiet szablonów w `PATH` lub `NUGET_ID` pod warunkiem.</span><span class="sxs-lookup"><span data-stu-id="75366-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="75366-317">Gdy `<PATH|NUGET_ID>` wartość nie zostanie określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="75366-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="75366-318">Podczas określania `NUGET_ID`, nie należy dołączać numer wersji.</span><span class="sxs-lookup"><span data-stu-id="75366-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="75366-319">Jeśli nie określisz parametru tej opcji, polecenie zawiera listę zainstalowanych szablonów i szczegółowe informacje o nich.</span><span class="sxs-lookup"><span data-stu-id="75366-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="75366-320">Aby odinstalować `PATH`szablon przy użyciu programu , musisz w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="75366-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="75366-321">Na przykład *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="75366-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="75366-322">Nie dołączaj ostatecznego ukośnika katalogu kończącego na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="75366-323">Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane, i instaluje je.</span><span class="sxs-lookup"><span data-stu-id="75366-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="75366-324">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="75366-325">Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="75366-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="75366-326">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="75366-327">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="75366-327">Template options</span></span>

<span data-ttu-id="75366-328">Każdy szablon projektu może mieć dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="75366-328">Each project template may have additional options available.</span></span> <span data-ttu-id="75366-329">Podstawowe szablony mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="75366-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="75366-330">console</span><span class="sxs-lookup"><span data-stu-id="75366-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-331">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-332">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="75366-333">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="75366-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="75366-334">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="75366-334">SDK version</span></span> | <span data-ttu-id="75366-335">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="75366-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="75366-336">3.1</span><span class="sxs-lookup"><span data-stu-id="75366-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="75366-337">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="75366-338">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="75366-339">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="75366-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="75366-340">Nie jest obsługiwany dla języka F#.</span><span class="sxs-lookup"><span data-stu-id="75366-340">Not supported for F#.</span></span> <span data-ttu-id="75366-341">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="75366-342">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="75366-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-343">Jeśli określono, nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="75366-344">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="75366-345">Classlib</span><span class="sxs-lookup"><span data-stu-id="75366-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-346">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-347">Wartości: `netcoreapp<version>` aby utworzyć bibliotekę klas `netstandard<version>` .NET Core lub utworzyć bibliotekę klas standardowych platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="75366-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="75366-348">Wartością domyślną jest `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="75366-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="75366-349">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="75366-350">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="75366-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="75366-351">Nie jest obsługiwany dla języka F#.</span><span class="sxs-lookup"><span data-stu-id="75366-351">Not supported for F#.</span></span> <span data-ttu-id="75366-352">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="75366-353">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="75366-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-354">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="75366-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="75366-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-356">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-357">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="75366-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="75366-358">Dostępne od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="75366-359">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="75366-360">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="75366-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="75366-361">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="75366-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-362">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="75366-363">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="75366-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="75366-364">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="75366-365">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="75366-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="75366-366">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="75366-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-367">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="75366-368">pracownik, grpc</span><span class="sxs-lookup"><span data-stu-id="75366-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-369">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-370">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="75366-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="75366-371">Dostępne od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="75366-372">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-373">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="75366-374">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="75366-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-375">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-376">Opcja dostępna od pliku .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="75366-377">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="75366-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="75366-378">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="75366-378">SDK version</span></span> | <span data-ttu-id="75366-379">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="75366-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="75366-380">3.1</span><span class="sxs-lookup"><span data-stu-id="75366-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="75366-381">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="75366-382">Umożliwia pakowanie dla projektu za pomocą [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="75366-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-383">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="75366-384">Nunit</span><span class="sxs-lookup"><span data-stu-id="75366-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-385">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="75366-386">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="75366-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="75366-387">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="75366-387">SDK version</span></span> | <span data-ttu-id="75366-388">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="75366-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="75366-389">3.1</span><span class="sxs-lookup"><span data-stu-id="75366-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="75366-390">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="75366-391">2.2</span><span class="sxs-lookup"><span data-stu-id="75366-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="75366-392">2.1</span><span class="sxs-lookup"><span data-stu-id="75366-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="75366-393">Umożliwia pakowanie dla projektu za pomocą [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="75366-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-394">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="75366-395">Strona</span><span class="sxs-lookup"><span data-stu-id="75366-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="75366-396">Obszar nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="75366-396">Namespace for the generated code.</span></span> <span data-ttu-id="75366-397">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="75366-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="75366-398">Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="75366-398">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="75366-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="75366-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="75366-400">Obszar nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="75366-400">Namespace for the generated code.</span></span> <span data-ttu-id="75366-401">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="75366-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="75366-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="75366-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="75366-403">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="75366-403">The type of authentication to use.</span></span> <span data-ttu-id="75366-404">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="75366-404">The possible values are:</span></span>

  - <span data-ttu-id="75366-405">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="75366-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="75366-406">`Individual`- Indywidualne uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="75366-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="75366-407">`IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="75366-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="75366-408">`SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="75366-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="75366-409">`MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="75366-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="75366-410">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="75366-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="75366-411">Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="75366-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="75366-412">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="75366-413">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="75366-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="75366-414">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="75366-415">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="75366-416">Identyfikator zasad resetowania haseł dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="75366-417">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="75366-418">Identyfikator zasad profilu edycji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="75366-419">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="75366-420">Wystąpienie usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="75366-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="75366-421">Użyj `SingleOrg` z `MultiOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="75366-422">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="75366-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="75366-423">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-423">The Client ID for this project.</span></span> <span data-ttu-id="75366-424">Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="75366-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="75366-425">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="75366-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="75366-426">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="75366-426">The domain for the directory tenant.</span></span> <span data-ttu-id="75366-427">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75366-428">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="75366-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="75366-429">Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="75366-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="75366-430">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75366-431">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="75366-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="75366-432">Ścieżka żądania w podstawowej ścieżce aplikacji identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="75366-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="75366-433">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75366-434">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="75366-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="75366-435">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="75366-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="75366-436">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="75366-437">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="75366-438">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75366-438">Turns off HTTPS.</span></span> <span data-ttu-id="75366-439">Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , `--auth`, lub nie są używane do .</span><span class="sxs-lookup"><span data-stu-id="75366-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="75366-440">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="75366-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="75366-441">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-442">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="75366-443">web</span><span class="sxs-lookup"><span data-stu-id="75366-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="75366-444">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-445">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-446">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="75366-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="75366-447">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="75366-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="75366-448">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="75366-448">SDK version</span></span> | <span data-ttu-id="75366-449">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="75366-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="75366-450">3.1</span><span class="sxs-lookup"><span data-stu-id="75366-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="75366-451">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="75366-452">2.1</span><span class="sxs-lookup"><span data-stu-id="75366-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="75366-453">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="75366-454">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75366-454">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="75366-455">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="75366-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="75366-456">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="75366-456">The type of authentication to use.</span></span> <span data-ttu-id="75366-457">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="75366-457">The possible values are:</span></span>

  - <span data-ttu-id="75366-458">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="75366-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="75366-459">`Individual`- Indywidualne uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="75366-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="75366-460">`IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="75366-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="75366-461">`SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="75366-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="75366-462">`MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="75366-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="75366-463">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="75366-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="75366-464">Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="75366-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="75366-465">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="75366-466">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="75366-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="75366-467">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="75366-468">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="75366-469">Identyfikator zasad resetowania haseł dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="75366-470">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="75366-471">Identyfikator zasad profilu edycji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="75366-472">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="75366-473">Wystąpienie usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="75366-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="75366-474">Użyj `SingleOrg` z `MultiOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="75366-475">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="75366-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="75366-476">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-476">The Client ID for this project.</span></span> <span data-ttu-id="75366-477">Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="75366-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="75366-478">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="75366-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="75366-479">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="75366-479">The domain for the directory tenant.</span></span> <span data-ttu-id="75366-480">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75366-481">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="75366-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="75366-482">Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="75366-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="75366-483">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75366-484">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="75366-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="75366-485">Ścieżka żądania w podstawowej ścieżce aplikacji identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="75366-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="75366-486">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75366-487">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="75366-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="75366-488">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="75366-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="75366-489">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="75366-490">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="75366-491">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75366-491">Turns off HTTPS.</span></span> <span data-ttu-id="75366-492">Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , , lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="75366-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="75366-493">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="75366-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="75366-494">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-495">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-496">Opcja dostępna od pliku .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="75366-497">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="75366-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="75366-498">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="75366-498">SDK version</span></span> | <span data-ttu-id="75366-499">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="75366-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="75366-500">3.1</span><span class="sxs-lookup"><span data-stu-id="75366-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="75366-501">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="75366-502">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="75366-503">Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="75366-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="75366-504">Opcja niedostępna w zestawach SDK .NET Core 2.2 i 3.1.</span><span class="sxs-lookup"><span data-stu-id="75366-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="75366-505">Określa, czy projekt jest skonfigurowany do używania [kompilacji środowiska uruchomieniowego Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) w kompilacjach debugowania.</span><span class="sxs-lookup"><span data-stu-id="75366-505">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="75366-506">Opcja dostępna od pliku .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-506">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="75366-507">kątowe, reagować</span><span class="sxs-lookup"><span data-stu-id="75366-507">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="75366-508">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="75366-508">The type of authentication to use.</span></span> <span data-ttu-id="75366-509">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-509">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="75366-510">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="75366-510">The possible values are:</span></span>

  - <span data-ttu-id="75366-511">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="75366-511">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="75366-512">`Individual`- Indywidualne uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="75366-512">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="75366-513">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-514">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-514">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="75366-515">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75366-515">Turns off HTTPS.</span></span> <span data-ttu-id="75366-516">Ta opcja ma zastosowanie `None`tylko wtedy, gdy uwierzytelnianie jest .</span><span class="sxs-lookup"><span data-stu-id="75366-516">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="75366-517">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="75366-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="75366-518">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="75366-519">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-519">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-520">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-521">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="75366-521">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="75366-522">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="75366-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="75366-523">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="75366-523">SDK version</span></span> | <span data-ttu-id="75366-524">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="75366-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="75366-525">3.1</span><span class="sxs-lookup"><span data-stu-id="75366-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="75366-526">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-526">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="75366-527">2.1</span><span class="sxs-lookup"><span data-stu-id="75366-527">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="75366-528">reactredux</span><span class="sxs-lookup"><span data-stu-id="75366-528">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="75366-529">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-529">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-530">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-530">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-531">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="75366-531">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="75366-532">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="75366-532">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="75366-533">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="75366-533">SDK version</span></span> | <span data-ttu-id="75366-534">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="75366-534">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="75366-535">3.1</span><span class="sxs-lookup"><span data-stu-id="75366-535">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="75366-536">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-536">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="75366-537">2.1</span><span class="sxs-lookup"><span data-stu-id="75366-537">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="75366-538">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-538">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="75366-539">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75366-539">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="75366-540">brzytwaklasyb</span><span class="sxs-lookup"><span data-stu-id="75366-540">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="75366-541">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="75366-542">Obsługuje dodawanie tradycyjnych stron razor i widoki oprócz składników do tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="75366-542">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="75366-543">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="75366-543">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="75366-544">Webapi</span><span class="sxs-lookup"><span data-stu-id="75366-544">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="75366-545">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="75366-545">The type of authentication to use.</span></span> <span data-ttu-id="75366-546">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="75366-546">The possible values are:</span></span>

  - <span data-ttu-id="75366-547">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="75366-547">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="75366-548">`IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="75366-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="75366-549">`SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="75366-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="75366-550">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="75366-550">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="75366-551">Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="75366-551">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="75366-552">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-552">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="75366-553">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="75366-553">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="75366-554">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-554">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="75366-555">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-555">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="75366-556">Wystąpienie usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="75366-556">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="75366-557">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-557">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75366-558">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="75366-558">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="75366-559">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-559">The Client ID for this project.</span></span> <span data-ttu-id="75366-560">Użyj `IndividualB2C` z `SingleOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-560">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="75366-561">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="75366-561">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="75366-562">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="75366-562">The domain for the directory tenant.</span></span> <span data-ttu-id="75366-563">Użyj `IndividualB2C` z `SingleOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="75366-564">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="75366-564">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="75366-565">Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="75366-565">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="75366-566">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="75366-566">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="75366-567">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="75366-567">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="75366-568">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="75366-568">Allows this application read-access to the directory.</span></span> <span data-ttu-id="75366-569">Dotyczy tylko `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-569">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="75366-570">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="75366-570">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="75366-571">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="75366-571">Turns off HTTPS.</span></span> <span data-ttu-id="75366-572">`app.UseHsts`i `app.UseHttpsRedirection` nie są `Startup.Configure`dodawane do .</span><span class="sxs-lookup"><span data-stu-id="75366-572">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="75366-573">Ta opcja ma `IndividualB2C` zastosowanie `SingleOrg` tylko wtedy, gdy lub nie są używane do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-573">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="75366-574">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="75366-574">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="75366-575">Dotyczy tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="75366-575">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="75366-576">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="75366-576">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="75366-577">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="75366-577">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="75366-578">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="75366-578">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="75366-579">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="75366-579">SDK version</span></span> | <span data-ttu-id="75366-580">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="75366-580">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="75366-581">3.1</span><span class="sxs-lookup"><span data-stu-id="75366-581">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="75366-582">3.0</span><span class="sxs-lookup"><span data-stu-id="75366-582">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="75366-583">2.1</span><span class="sxs-lookup"><span data-stu-id="75366-583">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="75366-584">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="75366-584">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="75366-585">globaljson</span><span class="sxs-lookup"><span data-stu-id="75366-585">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="75366-586">Określa wersję pliku .NET Core SDK, który ma być używany w pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="75366-586">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="75366-587">Przykłady</span><span class="sxs-lookup"><span data-stu-id="75366-587">Examples</span></span>

- <span data-ttu-id="75366-588">Utwórz projekt aplikacji konsoli języka C#, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="75366-588">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="75366-589">Utwórz projekt aplikacji konsoli F# w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="75366-589">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="75366-590">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu:</span><span class="sxs-lookup"><span data-stu-id="75366-590">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="75366-591">Utwórz nowy projekt core ASP.NET c# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="75366-591">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="75366-592">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="75366-592">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="75366-593">Wyświetl listę wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):List all templates available for Single Page Application (SPA) templates:</span><span class="sxs-lookup"><span data-stu-id="75366-593">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="75366-594">Wyświetl listę wszystkich szablonów pasujących do podciągów *my.*</span><span class="sxs-lookup"><span data-stu-id="75366-594">List all templates matching the *we* substring.</span></span> <span data-ttu-id="75366-595">Nie znaleziono dokładnego dopasowania, więc dopasowanie podciągu działa zarówno względem krótkiej nazwy, jak i kolumn nazw.</span><span class="sxs-lookup"><span data-stu-id="75366-595">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="75366-596">Próba wywołania szablonu pasującego *ng*.</span><span class="sxs-lookup"><span data-stu-id="75366-596">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="75366-597">Jeśli nie można określić pojedynczego dopasowania, wyświetl listę szablonów, które są częściowymi dopasowaniami.</span><span class="sxs-lookup"><span data-stu-id="75366-597">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="75366-598">Zainstaluj wersję 2.0 szablonów SPA dla ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="75366-598">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="75366-599">Wyświetl listę zainstalowanych szablonów i szczegółowe informacje na ich temat, w tym sposób ich odinstalowania:</span><span class="sxs-lookup"><span data-stu-id="75366-599">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="75366-600">Utwórz *global.json* w bieżącym katalogu ustawienie wersji SDK do 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="75366-600">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="75366-601">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75366-601">See also</span></span>

- [<span data-ttu-id="75366-602">Szablony niestandardowe dla dotnet new</span><span class="sxs-lookup"><span data-stu-id="75366-602">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="75366-603">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="75366-603">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="75366-604">dotnet/dotnet-template-samples Repo GitHub</span><span class="sxs-lookup"><span data-stu-id="75366-604">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="75366-605">Dostępne szablony dla dotnet new</span><span class="sxs-lookup"><span data-stu-id="75366-605">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
