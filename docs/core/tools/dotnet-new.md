---
title: dotnet nowe polecenie
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu.
ms.date: 04/10/2020
ms.openlocfilehash: 4ad0d7e54f93582237ed9457b562957018916d36
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463613"
---
# <a name="dotnet-new"></a><span data-ttu-id="c2e38-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c2e38-103">dotnet new</span></span>

<span data-ttu-id="c2e38-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="c2e38-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c2e38-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c2e38-105">Name</span></span>

<span data-ttu-id="c2e38-106">`dotnet new`- Tworzy nowy projekt, plik konfiguracyjny lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c2e38-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c2e38-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="c2e38-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c2e38-108">Description</span></span>

<span data-ttu-id="c2e38-109">Polecenie `dotnet new` tworzy projekt .NET Core lub inne artefakty oparte na szablonie.</span><span class="sxs-lookup"><span data-stu-id="c2e38-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="c2e38-110">Polecenie wywołuje [aparat szablonów,](https://github.com/dotnet/templating) aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="c2e38-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="c2e38-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c2e38-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="c2e38-112">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c2e38-113">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="c2e38-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c2e38-114">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="c2e38-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="c2e38-115">Można uruchomić, `dotnet new --list` aby wyświetlić listę wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="c2e38-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="c2e38-116">Jeśli `TEMPLATE` wartość nie jest dokładne dopasowanie tekstu w **szablony** lub **nazwa skrócona** kolumny z tabeli zwracanej, dopasowanie podciąg jest wykonywane na tych dwóch kolumnach.</span><span class="sxs-lookup"><span data-stu-id="c2e38-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="c2e38-117">Począwszy od pliku .NET Core 3.0 SDK, funkcja CLI wyszukuje szablony w NuGet.org podczas wywoływania `dotnet new` polecenia w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="c2e38-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="c2e38-118">Jeśli cli nie można znaleźć dopasowania szablonu podczas wywoływania `dotnet new`, nawet częściowe.</span><span class="sxs-lookup"><span data-stu-id="c2e38-118">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="c2e38-119">Jeśli dostępna jest nowsza wersja szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-119">If there's a newer version of the template available.</span></span> <span data-ttu-id="c2e38-120">W takim przypadku tworzony jest projekt lub artefakt, ale cli ostrzega o zaktualizowanej wersji szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="c2e38-121">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="c2e38-121">The command contains a default list of templates.</span></span> <span data-ttu-id="c2e38-122">Służy `dotnet new -l` do uzyskiwania listy dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="c2e38-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c2e38-123">W poniższej tabeli przedstawiono szablony, które są fabrycznie zainstalowane z pakietem .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="c2e38-124">Domyślny język szablonu jest wyświetlany wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="c2e38-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="c2e38-125">Kliknij łącze do krótkiej nazwy, aby wyświetlić określone opcje szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="c2e38-126">Szablony</span><span class="sxs-lookup"><span data-stu-id="c2e38-126">Templates</span></span>                                    | <span data-ttu-id="c2e38-127">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="c2e38-127">Short name</span></span>                      | <span data-ttu-id="c2e38-128">Język</span><span class="sxs-lookup"><span data-stu-id="c2e38-128">Language</span></span>     | <span data-ttu-id="c2e38-129">Tagi</span><span class="sxs-lookup"><span data-stu-id="c2e38-129">Tags</span></span>                                  | <span data-ttu-id="c2e38-130">Wprowadzone</span><span class="sxs-lookup"><span data-stu-id="c2e38-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="c2e38-131">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="c2e38-131">Console Application</span></span>                          | [<span data-ttu-id="c2e38-132">Konsoli</span><span class="sxs-lookup"><span data-stu-id="c2e38-132">console</span></span>](#console)             | <span data-ttu-id="c2e38-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c2e38-133">[C#], F#, VB</span></span> | <span data-ttu-id="c2e38-134">Wspólne/konsolowe</span><span class="sxs-lookup"><span data-stu-id="c2e38-134">Common/Console</span></span>                        | <span data-ttu-id="c2e38-135">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-135">1.0</span></span>        |
| <span data-ttu-id="c2e38-136">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="c2e38-136">Class library</span></span>                                | [<span data-ttu-id="c2e38-137">Classlib</span><span class="sxs-lookup"><span data-stu-id="c2e38-137">classlib</span></span>](#classlib)           | <span data-ttu-id="c2e38-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c2e38-138">[C#], F#, VB</span></span> | <span data-ttu-id="c2e38-139">Wspólne/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="c2e38-139">Common/Library</span></span>                        | <span data-ttu-id="c2e38-140">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-140">1.0</span></span>        |
| <span data-ttu-id="c2e38-141">Aplikacja WPF</span><span class="sxs-lookup"><span data-stu-id="c2e38-141">WPF Application</span></span>                              | [<span data-ttu-id="c2e38-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="c2e38-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="c2e38-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-143">[C#]</span></span>         | <span data-ttu-id="c2e38-144">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="c2e38-144">Common/WPF</span></span>                            | <span data-ttu-id="c2e38-145">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-145">3.0</span></span>        |
| <span data-ttu-id="c2e38-146">Biblioteka klas WPF</span><span class="sxs-lookup"><span data-stu-id="c2e38-146">WPF Class library</span></span>                            | [<span data-ttu-id="c2e38-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="c2e38-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="c2e38-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-148">[C#]</span></span>         | <span data-ttu-id="c2e38-149">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="c2e38-149">Common/WPF</span></span>                            | <span data-ttu-id="c2e38-150">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-150">3.0</span></span>        |
| <span data-ttu-id="c2e38-151">Biblioteka kontrolek niestandardowych WPF</span><span class="sxs-lookup"><span data-stu-id="c2e38-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="c2e38-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="c2e38-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="c2e38-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-153">[C#]</span></span>         | <span data-ttu-id="c2e38-154">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="c2e38-154">Common/WPF</span></span>                            | <span data-ttu-id="c2e38-155">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-155">3.0</span></span>        |
| <span data-ttu-id="c2e38-156">Biblioteka kontroli użytkownika WPF</span><span class="sxs-lookup"><span data-stu-id="c2e38-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="c2e38-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c2e38-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="c2e38-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-158">[C#]</span></span>         | <span data-ttu-id="c2e38-159">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="c2e38-159">Common/WPF</span></span>                            | <span data-ttu-id="c2e38-160">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-160">3.0</span></span>        |
| <span data-ttu-id="c2e38-161">Aplikacja Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="c2e38-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="c2e38-162">Winforms</span><span class="sxs-lookup"><span data-stu-id="c2e38-162">winforms</span></span>](#winforms)           | <span data-ttu-id="c2e38-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-163">[C#]</span></span>         | <span data-ttu-id="c2e38-164">Wspólne/WinForms</span><span class="sxs-lookup"><span data-stu-id="c2e38-164">Common/WinForms</span></span>                       | <span data-ttu-id="c2e38-165">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-165">3.0</span></span>        |
| <span data-ttu-id="c2e38-166">Biblioteka klas formularzy Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="c2e38-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="c2e38-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="c2e38-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="c2e38-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-168">[C#]</span></span>         | <span data-ttu-id="c2e38-169">Wspólne/WinForms</span><span class="sxs-lookup"><span data-stu-id="c2e38-169">Common/WinForms</span></span>                       | <span data-ttu-id="c2e38-170">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-170">3.0</span></span>        |
| <span data-ttu-id="c2e38-171">Usługa dla pracowników</span><span class="sxs-lookup"><span data-stu-id="c2e38-171">Worker Service</span></span>                               | [<span data-ttu-id="c2e38-172">Pracownik</span><span class="sxs-lookup"><span data-stu-id="c2e38-172">worker</span></span>](#web-others)           | <span data-ttu-id="c2e38-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-173">[C#]</span></span>         | <span data-ttu-id="c2e38-174">Często/Pracownik/Sieć Web</span><span class="sxs-lookup"><span data-stu-id="c2e38-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="c2e38-175">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-175">3.0</span></span>        |
| <span data-ttu-id="c2e38-176">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="c2e38-176">Unit Test Project</span></span>                            | [<span data-ttu-id="c2e38-177">Mstest</span><span class="sxs-lookup"><span data-stu-id="c2e38-177">mstest</span></span>](#test)                 | <span data-ttu-id="c2e38-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c2e38-178">[C#], F#, VB</span></span> | <span data-ttu-id="c2e38-179">Test/TEST MSTest</span><span class="sxs-lookup"><span data-stu-id="c2e38-179">Test/MSTest</span></span>                           | <span data-ttu-id="c2e38-180">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-180">1.0</span></span>        |
| <span data-ttu-id="c2e38-181">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c2e38-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="c2e38-182">Nunit</span><span class="sxs-lookup"><span data-stu-id="c2e38-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="c2e38-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c2e38-183">[C#], F#, VB</span></span> | <span data-ttu-id="c2e38-184">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="c2e38-184">Test/NUnit</span></span>                            | <span data-ttu-id="c2e38-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="c2e38-185">2.1.400</span></span>    |
| <span data-ttu-id="c2e38-186">NUnit 3 Przedmiot testowy</span><span class="sxs-lookup"><span data-stu-id="c2e38-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="c2e38-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c2e38-187">[C#], F#, VB</span></span> | <span data-ttu-id="c2e38-188">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="c2e38-188">Test/NUnit</span></span>                            | <span data-ttu-id="c2e38-189">2.2</span><span class="sxs-lookup"><span data-stu-id="c2e38-189">2.2</span></span>        |
| <span data-ttu-id="c2e38-190">xUnit Projekt testowy</span><span class="sxs-lookup"><span data-stu-id="c2e38-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="c2e38-191">Xunit</span><span class="sxs-lookup"><span data-stu-id="c2e38-191">xunit</span></span>](#test)                  | <span data-ttu-id="c2e38-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c2e38-192">[C#], F#, VB</span></span> | <span data-ttu-id="c2e38-193">Test/xJednostka</span><span class="sxs-lookup"><span data-stu-id="c2e38-193">Test/xUnit</span></span>                            | <span data-ttu-id="c2e38-194">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-194">1.0</span></span>        |
| <span data-ttu-id="c2e38-195">Komponent maszynki do golenia</span><span class="sxs-lookup"><span data-stu-id="c2e38-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="c2e38-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-196">[C#]</span></span>         | <span data-ttu-id="c2e38-197">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c2e38-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="c2e38-198">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-198">3.0</span></span>        |
| <span data-ttu-id="c2e38-199">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="c2e38-199">Razor Page</span></span>                                   | [<span data-ttu-id="c2e38-200">Strona</span><span class="sxs-lookup"><span data-stu-id="c2e38-200">page</span></span>](#page)                   | <span data-ttu-id="c2e38-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-201">[C#]</span></span>         | <span data-ttu-id="c2e38-202">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c2e38-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="c2e38-203">2.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-203">2.0</span></span>        |
| <span data-ttu-id="c2e38-204">Porty widoków MVC</span><span class="sxs-lookup"><span data-stu-id="c2e38-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="c2e38-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="c2e38-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="c2e38-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-206">[C#]</span></span>         | <span data-ttu-id="c2e38-207">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c2e38-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="c2e38-208">2.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-208">2.0</span></span>        |
| <span data-ttu-id="c2e38-209">Początek widoku MVC</span><span class="sxs-lookup"><span data-stu-id="c2e38-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="c2e38-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-210">[C#]</span></span>         | <span data-ttu-id="c2e38-211">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c2e38-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="c2e38-212">2.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-212">2.0</span></span>        |
| <span data-ttu-id="c2e38-213">Aplikacja serwera Blazor</span><span class="sxs-lookup"><span data-stu-id="c2e38-213">Blazor Server App</span></span>                            | [<span data-ttu-id="c2e38-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c2e38-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="c2e38-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-215">[C#]</span></span>         | <span data-ttu-id="c2e38-216">Sieć Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="c2e38-216">Web/Blazor</span></span>                            | <span data-ttu-id="c2e38-217">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-217">3.0</span></span>        |
| <span data-ttu-id="c2e38-218">ASP.NET rdzeń pusty</span><span class="sxs-lookup"><span data-stu-id="c2e38-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="c2e38-219">Sieci web</span><span class="sxs-lookup"><span data-stu-id="c2e38-219">web</span></span>](#web)                     | <span data-ttu-id="c2e38-220">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="c2e38-220">[C#], F#</span></span>     | <span data-ttu-id="c2e38-221">Sieć Web/Puste</span><span class="sxs-lookup"><span data-stu-id="c2e38-221">Web/Empty</span></span>                             | <span data-ttu-id="c2e38-222">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-222">1.0</span></span>        |
| <span data-ttu-id="c2e38-223">ASP.NET Core Web App (kontroler widoku modelu)</span><span class="sxs-lookup"><span data-stu-id="c2e38-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="c2e38-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="c2e38-224">mvc</span></span>](#web-options)             | <span data-ttu-id="c2e38-225">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="c2e38-225">[C#], F#</span></span>     | <span data-ttu-id="c2e38-226">Sieć Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c2e38-226">Web/MVC</span></span>                               | <span data-ttu-id="c2e38-227">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-227">1.0</span></span>        |
| <span data-ttu-id="c2e38-228">ASP.NET podstawowa aplikacja sieci Web</span><span class="sxs-lookup"><span data-stu-id="c2e38-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="c2e38-229">webapp, brzytwa</span><span class="sxs-lookup"><span data-stu-id="c2e38-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="c2e38-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-230">[C#]</span></span>         | <span data-ttu-id="c2e38-231">Strony internetowe/MVC/Brzytwa</span><span class="sxs-lookup"><span data-stu-id="c2e38-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="c2e38-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="c2e38-233">ASP.NET rdzeń z kątowym</span><span class="sxs-lookup"><span data-stu-id="c2e38-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="c2e38-234">Kątowe</span><span class="sxs-lookup"><span data-stu-id="c2e38-234">angular</span></span>](#spa)                 | <span data-ttu-id="c2e38-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-235">[C#]</span></span>         | <span data-ttu-id="c2e38-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c2e38-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c2e38-237">2.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-237">2.0</span></span>        |
| <span data-ttu-id="c2e38-238">ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="c2e38-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="c2e38-239">Reagować</span><span class="sxs-lookup"><span data-stu-id="c2e38-239">react</span></span>](#spa)                   | <span data-ttu-id="c2e38-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-240">[C#]</span></span>         | <span data-ttu-id="c2e38-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c2e38-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c2e38-242">2.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-242">2.0</span></span>        |
| <span data-ttu-id="c2e38-243">ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="c2e38-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="c2e38-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="c2e38-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="c2e38-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-245">[C#]</span></span>         | <span data-ttu-id="c2e38-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c2e38-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c2e38-247">2.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-247">2.0</span></span>        |
| <span data-ttu-id="c2e38-248">Biblioteka klas razor</span><span class="sxs-lookup"><span data-stu-id="c2e38-248">Razor Class Library</span></span>                          | [<span data-ttu-id="c2e38-249">brzytwaklasyb</span><span class="sxs-lookup"><span data-stu-id="c2e38-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="c2e38-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-250">[C#]</span></span>         | <span data-ttu-id="c2e38-251">Web/ Razor/Biblioteka/Razor Klasa Biblioteka</span><span class="sxs-lookup"><span data-stu-id="c2e38-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="c2e38-252">2.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-252">2.1</span></span>        |
| <span data-ttu-id="c2e38-253">Internetowy interfejs API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c2e38-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="c2e38-254">Webapi</span><span class="sxs-lookup"><span data-stu-id="c2e38-254">webapi</span></span>](#webapi)               | <span data-ttu-id="c2e38-255">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="c2e38-255">[C#], F#</span></span>     | <span data-ttu-id="c2e38-256">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c2e38-256">Web/WebAPI</span></span>                            | <span data-ttu-id="c2e38-257">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-257">1.0</span></span>        |
| <span data-ttu-id="c2e38-258">ASP.NET podstawowa usługa gRPC</span><span class="sxs-lookup"><span data-stu-id="c2e38-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="c2e38-259">grpc (grpc)</span><span class="sxs-lookup"><span data-stu-id="c2e38-259">grpc</span></span>](#web-others)             | <span data-ttu-id="c2e38-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="c2e38-260">[C#]</span></span>         | <span data-ttu-id="c2e38-261">Sieć/gRPC</span><span class="sxs-lookup"><span data-stu-id="c2e38-261">Web/gRPC</span></span>                              | <span data-ttu-id="c2e38-262">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-262">3.0</span></span>        |
| <span data-ttu-id="c2e38-263">Plik buforu protokołu</span><span class="sxs-lookup"><span data-stu-id="c2e38-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="c2e38-264">Proto</span><span class="sxs-lookup"><span data-stu-id="c2e38-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="c2e38-265">Sieć/gRPC</span><span class="sxs-lookup"><span data-stu-id="c2e38-265">Web/gRPC</span></span>                              | <span data-ttu-id="c2e38-266">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-266">3.0</span></span>        |
| <span data-ttu-id="c2e38-267">plik dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="c2e38-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="c2e38-268">Config</span><span class="sxs-lookup"><span data-stu-id="c2e38-268">Config</span></span>                                | <span data-ttu-id="c2e38-269">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-269">3.0</span></span>        |
| <span data-ttu-id="c2e38-270">plik global.json</span><span class="sxs-lookup"><span data-stu-id="c2e38-270">global.json file</span></span>                             | [<span data-ttu-id="c2e38-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="c2e38-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="c2e38-272">Config</span><span class="sxs-lookup"><span data-stu-id="c2e38-272">Config</span></span>                                | <span data-ttu-id="c2e38-273">2.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-273">2.0</span></span>        |
| <span data-ttu-id="c2e38-274">Konfiguracja NuGet</span><span class="sxs-lookup"><span data-stu-id="c2e38-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="c2e38-275">Config</span><span class="sxs-lookup"><span data-stu-id="c2e38-275">Config</span></span>                                | <span data-ttu-id="c2e38-276">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-276">1.0</span></span>        |
| <span data-ttu-id="c2e38-277">plik manifestu narzędzia lokalnego dotnet</span><span class="sxs-lookup"><span data-stu-id="c2e38-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="c2e38-278">Config</span><span class="sxs-lookup"><span data-stu-id="c2e38-278">Config</span></span>                                | <span data-ttu-id="c2e38-279">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-279">3.0</span></span>        |
| <span data-ttu-id="c2e38-280">Konfigurga internetowa</span><span class="sxs-lookup"><span data-stu-id="c2e38-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="c2e38-281">Config</span><span class="sxs-lookup"><span data-stu-id="c2e38-281">Config</span></span>                                | <span data-ttu-id="c2e38-282">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-282">1.0</span></span>        |
| <span data-ttu-id="c2e38-283">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="c2e38-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="c2e38-284">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="c2e38-284">Solution</span></span>                              | <span data-ttu-id="c2e38-285">1.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="c2e38-286">Opcje</span><span class="sxs-lookup"><span data-stu-id="c2e38-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="c2e38-287">Wyświetla podsumowanie tego, co by się stało, gdyby dane polecenie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="c2e38-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="c2e38-288">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="c2e38-289">Wymusza generowanie zawartości, nawet jeśli spowoduje to zmianę istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="c2e38-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c2e38-290">Jest to wymagane, gdy wybrany szablon zastąpi istniejące pliki w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="c2e38-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c2e38-291">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-291">Prints out help for the command.</span></span> <span data-ttu-id="c2e38-292">Można go wywołać `dotnet new` dla samego polecenia lub dla dowolnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="c2e38-293">Na przykład `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="c2e38-294">Instaluje pakiet `PATH` szablonów `NUGET_ID` z lub dostarczone.</span><span class="sxs-lookup"><span data-stu-id="c2e38-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c2e38-295">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w `<package-name>::<package-version>`formacie .</span><span class="sxs-lookup"><span data-stu-id="c2e38-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c2e38-296">Domyślnie `dotnet new` przechodzi \* do wersji, która reprezentuje najnowszą stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="c2e38-297">Zobacz przykład w sekcji [Przykłady.](#examples)</span><span class="sxs-lookup"><span data-stu-id="c2e38-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="c2e38-298">Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej wersji stabilnej, jeśli nie określono żadnej wersji.</span><span class="sxs-lookup"><span data-stu-id="c2e38-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="c2e38-299">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="c2e38-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="c2e38-300">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="c2e38-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="c2e38-301">Jeśli nazwa nie zostanie określona, wyświetla listę wszystkich szablonów.</span><span class="sxs-lookup"><span data-stu-id="c2e38-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="c2e38-302">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-302">The language of the template to create.</span></span> <span data-ttu-id="c2e38-303">Akceptowany język różni się w zależności od szablonu (zobacz wartości domyślne w sekcji [argumenty).](#arguments)</span><span class="sxs-lookup"><span data-stu-id="c2e38-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c2e38-304">Nie dotyczy niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="c2e38-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c2e38-305">Niektóre skorupy `#` interpretują jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="c2e38-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c2e38-306">W takich przypadkach należy ująć wartość parametru języka w cudzysłowach.</span><span class="sxs-lookup"><span data-stu-id="c2e38-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="c2e38-307">Na przykład `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="c2e38-308">Nazwa utworzonego wyjścia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-308">The name for the created output.</span></span> <span data-ttu-id="c2e38-309">Jeśli nazwa nie zostanie określona, używana jest nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="c2e38-310">Określa źródło NuGet, które ma być używane podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="c2e38-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="c2e38-311">Dostępne od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c2e38-312">Lokalizacja, aby umieścić wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c2e38-312">Location to place the generated output.</span></span> <span data-ttu-id="c2e38-313">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="c2e38-313">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="c2e38-314">Filtruje szablony na podstawie dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="c2e38-314">Filters templates based on available types.</span></span> <span data-ttu-id="c2e38-315">Wstępnie zdefiniowane wartości `project` `item`to `other`, lub .</span><span class="sxs-lookup"><span data-stu-id="c2e38-315">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="c2e38-316">Odinstalowuje pakiet szablonów w `PATH` lub `NUGET_ID` pod warunkiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c2e38-317">Gdy `<PATH|NUGET_ID>` wartość nie zostanie określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="c2e38-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="c2e38-318">Podczas określania `NUGET_ID`, nie należy dołączać numer wersji.</span><span class="sxs-lookup"><span data-stu-id="c2e38-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="c2e38-319">Jeśli nie określisz parametru tej opcji, polecenie zawiera listę zainstalowanych szablonów i szczegółowe informacje o nich.</span><span class="sxs-lookup"><span data-stu-id="c2e38-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c2e38-320">Aby odinstalować `PATH`szablon przy użyciu programu , musisz w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="c2e38-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c2e38-321">Na przykład *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="c2e38-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="c2e38-322">Nie dołączaj ostatecznego ukośnika katalogu kończącego na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="c2e38-323">Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane, i instaluje je.</span><span class="sxs-lookup"><span data-stu-id="c2e38-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="c2e38-324">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="c2e38-325">Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="c2e38-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="c2e38-326">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="c2e38-327">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="c2e38-327">Template options</span></span>

<span data-ttu-id="c2e38-328">Każdy szablon projektu może mieć dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="c2e38-328">Each project template may have additional options available.</span></span> <span data-ttu-id="c2e38-329">Podstawowe szablony mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="c2e38-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="c2e38-330">console</span><span class="sxs-lookup"><span data-stu-id="c2e38-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-331">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-332">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c2e38-333">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="c2e38-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c2e38-334">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c2e38-334">SDK version</span></span> | <span data-ttu-id="c2e38-335">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="c2e38-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c2e38-336">3.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c2e38-337">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c2e38-338">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c2e38-339">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c2e38-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c2e38-340">Nie jest obsługiwany dla języka F#.</span><span class="sxs-lookup"><span data-stu-id="c2e38-340">Not supported for F#.</span></span> <span data-ttu-id="c2e38-341">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c2e38-342">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c2e38-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-343">Jeśli określono, nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="c2e38-344">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="c2e38-345">Classlib</span><span class="sxs-lookup"><span data-stu-id="c2e38-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-346">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-347">Wartości: `netcoreapp<version>` aby utworzyć bibliotekę klas `netstandard<version>` .NET Core lub utworzyć bibliotekę klas standardowych platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c2e38-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c2e38-348">Wartością domyślną jest `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c2e38-349">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c2e38-350">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c2e38-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c2e38-351">Nie jest obsługiwany dla języka F#.</span><span class="sxs-lookup"><span data-stu-id="c2e38-351">Not supported for F#.</span></span> <span data-ttu-id="c2e38-352">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c2e38-353">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c2e38-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-354">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="c2e38-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c2e38-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-356">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-357">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c2e38-358">Dostępne od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c2e38-359">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c2e38-360">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c2e38-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c2e38-361">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c2e38-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-362">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="c2e38-363">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="c2e38-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c2e38-364">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c2e38-365">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c2e38-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c2e38-366">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c2e38-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-367">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="c2e38-368">pracownik, grpc</span><span class="sxs-lookup"><span data-stu-id="c2e38-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-369">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-370">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c2e38-371">Dostępne od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c2e38-372">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-373">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="c2e38-374">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="c2e38-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-375">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-376">Opcja dostępna od pliku .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c2e38-377">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="c2e38-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c2e38-378">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c2e38-378">SDK version</span></span> | <span data-ttu-id="c2e38-379">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="c2e38-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c2e38-380">3.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c2e38-381">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c2e38-382">Umożliwia pakowanie dla projektu za pomocą [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c2e38-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-383">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="c2e38-384">Nunit</span><span class="sxs-lookup"><span data-stu-id="c2e38-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-385">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="c2e38-386">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="c2e38-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c2e38-387">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c2e38-387">SDK version</span></span> | <span data-ttu-id="c2e38-388">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="c2e38-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c2e38-389">3.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c2e38-390">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c2e38-391">2.2</span><span class="sxs-lookup"><span data-stu-id="c2e38-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="c2e38-392">2.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c2e38-393">Umożliwia pakowanie dla projektu za pomocą [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c2e38-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-394">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="c2e38-395">Strona</span><span class="sxs-lookup"><span data-stu-id="c2e38-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="c2e38-396">Obszar nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-396">Namespace for the generated code.</span></span> <span data-ttu-id="c2e38-397">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="c2e38-398">Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="c2e38-398">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="c2e38-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="c2e38-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="c2e38-400">Obszar nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-400">Namespace for the generated code.</span></span> <span data-ttu-id="c2e38-401">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="c2e38-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c2e38-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c2e38-403">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-403">The type of authentication to use.</span></span> <span data-ttu-id="c2e38-404">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="c2e38-404">The possible values are:</span></span>

  - <span data-ttu-id="c2e38-405">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="c2e38-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c2e38-406">`Individual`- Indywidualne uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="c2e38-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c2e38-407">`IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c2e38-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c2e38-408">`SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="c2e38-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c2e38-409">`MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="c2e38-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c2e38-410">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c2e38-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c2e38-411">Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c2e38-412">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c2e38-413">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c2e38-414">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c2e38-415">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c2e38-416">Identyfikator zasad resetowania haseł dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="c2e38-417">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c2e38-418">Identyfikator zasad profilu edycji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c2e38-419">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c2e38-420">Wystąpienie usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c2e38-421">Użyj `SingleOrg` z `MultiOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c2e38-422">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c2e38-423">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-423">The Client ID for this project.</span></span> <span data-ttu-id="c2e38-424">Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c2e38-425">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c2e38-426">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-426">The domain for the directory tenant.</span></span> <span data-ttu-id="c2e38-427">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c2e38-428">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c2e38-429">Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="c2e38-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c2e38-430">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c2e38-431">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c2e38-432">Ścieżka żądania w podstawowej ścieżce aplikacji identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c2e38-433">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c2e38-434">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c2e38-435">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c2e38-436">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c2e38-437">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c2e38-438">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c2e38-438">Turns off HTTPS.</span></span> <span data-ttu-id="c2e38-439">Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , `--auth`, lub nie są używane do .</span><span class="sxs-lookup"><span data-stu-id="c2e38-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c2e38-440">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="c2e38-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c2e38-441">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-442">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="c2e38-443">web</span><span class="sxs-lookup"><span data-stu-id="c2e38-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c2e38-444">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-445">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-446">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c2e38-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c2e38-447">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="c2e38-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c2e38-448">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c2e38-448">SDK version</span></span> | <span data-ttu-id="c2e38-449">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="c2e38-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c2e38-450">3.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c2e38-451">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c2e38-452">2.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c2e38-453">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c2e38-454">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c2e38-454">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="c2e38-455">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="c2e38-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c2e38-456">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-456">The type of authentication to use.</span></span> <span data-ttu-id="c2e38-457">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="c2e38-457">The possible values are:</span></span>

  - <span data-ttu-id="c2e38-458">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="c2e38-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c2e38-459">`Individual`- Indywidualne uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="c2e38-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c2e38-460">`IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c2e38-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c2e38-461">`SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="c2e38-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c2e38-462">`MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="c2e38-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c2e38-463">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c2e38-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c2e38-464">Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c2e38-465">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c2e38-466">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c2e38-467">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c2e38-468">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c2e38-469">Identyfikator zasad resetowania haseł dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="c2e38-470">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c2e38-471">Identyfikator zasad profilu edycji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c2e38-472">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c2e38-473">Wystąpienie usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c2e38-474">Użyj `SingleOrg` z `MultiOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c2e38-475">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c2e38-476">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-476">The Client ID for this project.</span></span> <span data-ttu-id="c2e38-477">Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c2e38-478">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c2e38-479">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-479">The domain for the directory tenant.</span></span> <span data-ttu-id="c2e38-480">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c2e38-481">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c2e38-482">Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="c2e38-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c2e38-483">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c2e38-484">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c2e38-485">Ścieżka żądania w podstawowej ścieżce aplikacji identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c2e38-486">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c2e38-487">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c2e38-488">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c2e38-489">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c2e38-490">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c2e38-491">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c2e38-491">Turns off HTTPS.</span></span> <span data-ttu-id="c2e38-492">Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , , lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="c2e38-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c2e38-493">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="c2e38-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c2e38-494">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-495">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-496">Opcja dostępna od pliku .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c2e38-497">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="c2e38-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c2e38-498">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c2e38-498">SDK version</span></span> | <span data-ttu-id="c2e38-499">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="c2e38-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c2e38-500">3.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c2e38-501">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="c2e38-502">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="c2e38-503">Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="c2e38-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="c2e38-504">Opcja niedostępna w zestawach SDK .NET Core 2.2 i 3.1.</span><span class="sxs-lookup"><span data-stu-id="c2e38-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="c2e38-505">Określa, czy projekt jest skonfigurowany do używania [kompilacji środowiska uruchomieniowego Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) w kompilacjach debugowania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-505">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="c2e38-506">Opcja dostępna od pliku .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-506">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="c2e38-507">kątowe, reagować</span><span class="sxs-lookup"><span data-stu-id="c2e38-507">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c2e38-508">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-508">The type of authentication to use.</span></span> <span data-ttu-id="c2e38-509">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-509">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="c2e38-510">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="c2e38-510">The possible values are:</span></span>

  - <span data-ttu-id="c2e38-511">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="c2e38-511">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c2e38-512">`Individual`- Indywidualne uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="c2e38-512">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c2e38-513">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-514">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-514">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c2e38-515">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c2e38-515">Turns off HTTPS.</span></span> <span data-ttu-id="c2e38-516">Ta opcja ma zastosowanie `None`tylko wtedy, gdy uwierzytelnianie jest .</span><span class="sxs-lookup"><span data-stu-id="c2e38-516">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c2e38-517">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="c2e38-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c2e38-518">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c2e38-519">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-519">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-520">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-521">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c2e38-521">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c2e38-522">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="c2e38-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c2e38-523">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c2e38-523">SDK version</span></span> | <span data-ttu-id="c2e38-524">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="c2e38-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c2e38-525">3.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c2e38-526">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-526">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c2e38-527">2.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-527">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="c2e38-528">reactredux</span><span class="sxs-lookup"><span data-stu-id="c2e38-528">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c2e38-529">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-529">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-530">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-530">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-531">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c2e38-531">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c2e38-532">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="c2e38-532">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c2e38-533">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c2e38-533">SDK version</span></span> | <span data-ttu-id="c2e38-534">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="c2e38-534">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c2e38-535">3.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-535">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c2e38-536">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-536">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c2e38-537">2.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-537">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="c2e38-538">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-538">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c2e38-539">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c2e38-539">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="c2e38-540">brzytwaklasyb</span><span class="sxs-lookup"><span data-stu-id="c2e38-540">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="c2e38-541">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="c2e38-542">Obsługuje dodawanie tradycyjnych stron razor i widoki oprócz składników do tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c2e38-542">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="c2e38-543">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c2e38-543">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="c2e38-544">Webapi</span><span class="sxs-lookup"><span data-stu-id="c2e38-544">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c2e38-545">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-545">The type of authentication to use.</span></span> <span data-ttu-id="c2e38-546">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="c2e38-546">The possible values are:</span></span>

  - <span data-ttu-id="c2e38-547">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="c2e38-547">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c2e38-548">`IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c2e38-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c2e38-549">`SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="c2e38-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c2e38-550">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c2e38-550">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c2e38-551">Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-551">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c2e38-552">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-552">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c2e38-553">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-553">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c2e38-554">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-554">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c2e38-555">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-555">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c2e38-556">Wystąpienie usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="c2e38-556">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c2e38-557">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-557">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c2e38-558">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-558">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c2e38-559">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-559">The Client ID for this project.</span></span> <span data-ttu-id="c2e38-560">Użyj `IndividualB2C` z `SingleOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-560">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c2e38-561">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-561">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c2e38-562">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-562">The domain for the directory tenant.</span></span> <span data-ttu-id="c2e38-563">Użyj `IndividualB2C` z `SingleOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c2e38-564">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-564">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c2e38-565">Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="c2e38-565">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c2e38-566">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="c2e38-566">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c2e38-567">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-567">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c2e38-568">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-568">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c2e38-569">Dotyczy tylko `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-569">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c2e38-570">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-570">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c2e38-571">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c2e38-571">Turns off HTTPS.</span></span> <span data-ttu-id="c2e38-572">`app.UseHsts`i `app.UseHttpsRedirection` nie są `Startup.Configure`dodawane do .</span><span class="sxs-lookup"><span data-stu-id="c2e38-572">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c2e38-573">Ta opcja ma `IndividualB2C` zastosowanie `SingleOrg` tylko wtedy, gdy lub nie są używane do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-573">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c2e38-574">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="c2e38-574">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c2e38-575">Dotyczy tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c2e38-575">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c2e38-576">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="c2e38-576">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c2e38-577">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c2e38-577">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c2e38-578">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="c2e38-578">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c2e38-579">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c2e38-579">SDK version</span></span> | <span data-ttu-id="c2e38-580">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="c2e38-580">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c2e38-581">3.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-581">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c2e38-582">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e38-582">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c2e38-583">2.1</span><span class="sxs-lookup"><span data-stu-id="c2e38-583">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c2e38-584">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c2e38-584">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="c2e38-585">globaljson</span><span class="sxs-lookup"><span data-stu-id="c2e38-585">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="c2e38-586">Określa wersję pliku .NET Core SDK, który ma być używany w pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="c2e38-586">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="c2e38-587">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c2e38-587">Examples</span></span>

- <span data-ttu-id="c2e38-588">Utwórz projekt aplikacji konsoli języka C#, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="c2e38-588">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="c2e38-589">Utwórz projekt aplikacji konsoli F# w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="c2e38-589">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="c2e38-590">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu:</span><span class="sxs-lookup"><span data-stu-id="c2e38-590">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="c2e38-591">Utwórz nowy projekt core ASP.NET c# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="c2e38-591">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="c2e38-592">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="c2e38-592">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="c2e38-593">Wyświetl listę wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):List all templates available for Single Page Application (SPA) templates:</span><span class="sxs-lookup"><span data-stu-id="c2e38-593">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="c2e38-594">Wyświetl listę wszystkich szablonów pasujących do podciągów *my.*</span><span class="sxs-lookup"><span data-stu-id="c2e38-594">List all templates matching the *we* substring.</span></span> <span data-ttu-id="c2e38-595">Nie znaleziono dokładnego dopasowania, więc dopasowanie podciągu działa zarówno względem krótkiej nazwy, jak i kolumn nazw.</span><span class="sxs-lookup"><span data-stu-id="c2e38-595">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="c2e38-596">Próba wywołania szablonu pasującego *ng*.</span><span class="sxs-lookup"><span data-stu-id="c2e38-596">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="c2e38-597">Jeśli nie można określić pojedynczego dopasowania, wyświetl listę szablonów, które są częściowymi dopasowaniami.</span><span class="sxs-lookup"><span data-stu-id="c2e38-597">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="c2e38-598">Zainstaluj wersję 2.0 szablonów SPA dla ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="c2e38-598">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="c2e38-599">Wyświetl listę zainstalowanych szablonów i szczegółowe informacje na ich temat, w tym sposób ich odinstalowania:</span><span class="sxs-lookup"><span data-stu-id="c2e38-599">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="c2e38-600">Utwórz *global.json* w bieżącym katalogu ustawienie wersji SDK do 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="c2e38-600">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="c2e38-601">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2e38-601">See also</span></span>

- [<span data-ttu-id="c2e38-602">Szablony niestandardowe dla dotnet new</span><span class="sxs-lookup"><span data-stu-id="c2e38-602">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="c2e38-603">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="c2e38-603">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="c2e38-604">dotnet/dotnet-template-samples Repo GitHub</span><span class="sxs-lookup"><span data-stu-id="c2e38-604">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="c2e38-605">Dostępne szablony dla dotnet new</span><span class="sxs-lookup"><span data-stu-id="c2e38-605">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
