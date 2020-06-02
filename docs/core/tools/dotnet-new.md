---
title: polecenie dotnet New
description: Polecenie dotnet New umożliwia tworzenie nowych projektów platformy .NET Core na podstawie określonego szablonu.
ms.date: 04/10/2020
ms.openlocfilehash: 39301ad95761848b60b45cb5c18ede937f70c32c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283978"
---
# <a name="dotnet-new"></a><span data-ttu-id="ce792-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ce792-103">dotnet new</span></span>

<span data-ttu-id="ce792-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="ce792-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ce792-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ce792-105">Name</span></span>

<span data-ttu-id="ce792-106">`dotnet new`-Tworzy nowy projekt, plik konfiguracji lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ce792-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ce792-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="ce792-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ce792-108">Description</span></span>

<span data-ttu-id="ce792-109">`dotnet new`Polecenie tworzy projekt .NET Core lub inne artefakty na podstawie szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="ce792-110">Polecenie wywołuje [aparat szablonu](https://github.com/dotnet/templating) , aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="ce792-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="ce792-111">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="ce792-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="ce792-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ce792-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="ce792-113">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ce792-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ce792-114">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="ce792-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ce792-115">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ce792-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="ce792-116">Można uruchomić `dotnet new --list` lub `dotnet new -l` wyświetlić listę wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ce792-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="ce792-117">Jeśli `TEMPLATE` wartość nie jest dokładnym dopasowaniem do tekstu w kolumnie **Szablony** lub **krótka nazwa** z zwróconej tabeli, do tych dwóch kolumn jest wykonywane dopasowanie podciągu.</span><span class="sxs-lookup"><span data-stu-id="ce792-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="ce792-118">Począwszy od zestawu SDK platformy .NET Core 3,0, interfejs wiersza polecenia wyszukuje szablony w NuGet.org, gdy wywoła `dotnet new` polecenie w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="ce792-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="ce792-119">Jeśli interfejs wiersza polecenia nie może znaleźć dopasowania szablonu podczas wywoływania `dotnet new` , nie nawet częściowej.</span><span class="sxs-lookup"><span data-stu-id="ce792-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="ce792-120">Jeśli jest dostępna nowsza wersja szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="ce792-121">W takim przypadku projekt lub artefakt jest tworzony, ale interfejs wiersza polecenia ostrzega użytkownika o zaktualizowanej wersji szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="ce792-122">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane wraz z zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="ce792-123">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="ce792-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="ce792-124">Kliknij link krótkiej nazwy, aby wyświetlić opcje konkretnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="ce792-125">Szablony</span><span class="sxs-lookup"><span data-stu-id="ce792-125">Templates</span></span>                                    | <span data-ttu-id="ce792-126">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="ce792-126">Short name</span></span>                      | <span data-ttu-id="ce792-127">Język</span><span class="sxs-lookup"><span data-stu-id="ce792-127">Language</span></span>     | <span data-ttu-id="ce792-128">Tagi</span><span class="sxs-lookup"><span data-stu-id="ce792-128">Tags</span></span>                                  | <span data-ttu-id="ce792-129">Wraca</span><span class="sxs-lookup"><span data-stu-id="ce792-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="ce792-130">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="ce792-130">Console Application</span></span>                          | [<span data-ttu-id="ce792-131">konsoli</span><span class="sxs-lookup"><span data-stu-id="ce792-131">console</span></span>](#console)             | <span data-ttu-id="ce792-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ce792-132">[C#], F#, VB</span></span> | <span data-ttu-id="ce792-133">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="ce792-133">Common/Console</span></span>                        | <span data-ttu-id="ce792-134">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-134">1.0</span></span>        |
| <span data-ttu-id="ce792-135">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="ce792-135">Class library</span></span>                                | [<span data-ttu-id="ce792-136">określono</span><span class="sxs-lookup"><span data-stu-id="ce792-136">classlib</span></span>](#classlib)           | <span data-ttu-id="ce792-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ce792-137">[C#], F#, VB</span></span> | <span data-ttu-id="ce792-138">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="ce792-138">Common/Library</span></span>                        | <span data-ttu-id="ce792-139">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-139">1.0</span></span>        |
| <span data-ttu-id="ce792-140">Aplikacja WPF</span><span class="sxs-lookup"><span data-stu-id="ce792-140">WPF Application</span></span>                              | [<span data-ttu-id="ce792-141">kodow</span><span class="sxs-lookup"><span data-stu-id="ce792-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="ce792-142">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-142">[C#]</span></span>         | <span data-ttu-id="ce792-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ce792-143">Common/WPF</span></span>                            | <span data-ttu-id="ce792-144">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-144">3.0</span></span>        |
| <span data-ttu-id="ce792-145">Biblioteka klas WPF</span><span class="sxs-lookup"><span data-stu-id="ce792-145">WPF Class library</span></span>                            | [<span data-ttu-id="ce792-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="ce792-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="ce792-147">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-147">[C#]</span></span>         | <span data-ttu-id="ce792-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ce792-148">Common/WPF</span></span>                            | <span data-ttu-id="ce792-149">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-149">3.0</span></span>        |
| <span data-ttu-id="ce792-150">Biblioteka kontrolek niestandardowych WPF</span><span class="sxs-lookup"><span data-stu-id="ce792-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="ce792-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="ce792-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="ce792-152">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-152">[C#]</span></span>         | <span data-ttu-id="ce792-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ce792-153">Common/WPF</span></span>                            | <span data-ttu-id="ce792-154">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-154">3.0</span></span>        |
| <span data-ttu-id="ce792-155">Biblioteka kontrolek użytkownika WPF</span><span class="sxs-lookup"><span data-stu-id="ce792-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="ce792-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ce792-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="ce792-157">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-157">[C#]</span></span>         | <span data-ttu-id="ce792-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="ce792-158">Common/WPF</span></span>                            | <span data-ttu-id="ce792-159">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-159">3.0</span></span>        |
| <span data-ttu-id="ce792-160">Aplikacja Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="ce792-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="ce792-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="ce792-161">winforms</span></span>](#winforms)           | <span data-ttu-id="ce792-162">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-162">[C#]</span></span>         | <span data-ttu-id="ce792-163">Typowe/WinForms</span><span class="sxs-lookup"><span data-stu-id="ce792-163">Common/WinForms</span></span>                       | <span data-ttu-id="ce792-164">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-164">3.0</span></span>        |
| <span data-ttu-id="ce792-165">Biblioteka klas Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="ce792-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="ce792-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="ce792-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="ce792-167">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-167">[C#]</span></span>         | <span data-ttu-id="ce792-168">Typowe/WinForms</span><span class="sxs-lookup"><span data-stu-id="ce792-168">Common/WinForms</span></span>                       | <span data-ttu-id="ce792-169">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-169">3.0</span></span>        |
| <span data-ttu-id="ce792-170">Usługa procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="ce792-170">Worker Service</span></span>                               | [<span data-ttu-id="ce792-171">odpowiedzialn</span><span class="sxs-lookup"><span data-stu-id="ce792-171">worker</span></span>](#web-others)           | <span data-ttu-id="ce792-172">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-172">[C#]</span></span>         | <span data-ttu-id="ce792-173">Common/Worker/sieć Web</span><span class="sxs-lookup"><span data-stu-id="ce792-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="ce792-174">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-174">3.0</span></span>        |
| <span data-ttu-id="ce792-175">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="ce792-175">Unit Test Project</span></span>                            | [<span data-ttu-id="ce792-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="ce792-176">mstest</span></span>](#test)                 | <span data-ttu-id="ce792-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ce792-177">[C#], F#, VB</span></span> | <span data-ttu-id="ce792-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="ce792-178">Test/MSTest</span></span>                           | <span data-ttu-id="ce792-179">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-179">1.0</span></span>        |
| <span data-ttu-id="ce792-180">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ce792-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="ce792-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="ce792-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="ce792-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ce792-182">[C#], F#, VB</span></span> | <span data-ttu-id="ce792-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ce792-183">Test/NUnit</span></span>                            | <span data-ttu-id="ce792-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="ce792-184">2.1.400</span></span>    |
| <span data-ttu-id="ce792-185">Element testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ce792-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="ce792-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ce792-186">[C#], F#, VB</span></span> | <span data-ttu-id="ce792-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="ce792-187">Test/NUnit</span></span>                            | <span data-ttu-id="ce792-188">2.2</span><span class="sxs-lookup"><span data-stu-id="ce792-188">2.2</span></span>        |
| <span data-ttu-id="ce792-189">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="ce792-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="ce792-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="ce792-190">xunit</span></span>](#test)                  | <span data-ttu-id="ce792-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="ce792-191">[C#], F#, VB</span></span> | <span data-ttu-id="ce792-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="ce792-192">Test/xUnit</span></span>                            | <span data-ttu-id="ce792-193">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-193">1.0</span></span>        |
| <span data-ttu-id="ce792-194">Składnik Razor</span><span class="sxs-lookup"><span data-stu-id="ce792-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="ce792-195">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-195">[C#]</span></span>         | <span data-ttu-id="ce792-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ce792-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="ce792-197">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-197">3.0</span></span>        |
| <span data-ttu-id="ce792-198">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="ce792-198">Razor Page</span></span>                                   | [<span data-ttu-id="ce792-199">stronic</span><span class="sxs-lookup"><span data-stu-id="ce792-199">page</span></span>](#page)                   | <span data-ttu-id="ce792-200">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-200">[C#]</span></span>         | <span data-ttu-id="ce792-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ce792-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="ce792-202">2.0</span><span class="sxs-lookup"><span data-stu-id="ce792-202">2.0</span></span>        |
| <span data-ttu-id="ce792-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="ce792-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="ce792-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="ce792-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="ce792-205">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-205">[C#]</span></span>         | <span data-ttu-id="ce792-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ce792-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="ce792-207">2.0</span><span class="sxs-lookup"><span data-stu-id="ce792-207">2.0</span></span>        |
| <span data-ttu-id="ce792-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="ce792-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="ce792-209">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-209">[C#]</span></span>         | <span data-ttu-id="ce792-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="ce792-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="ce792-211">2.0</span><span class="sxs-lookup"><span data-stu-id="ce792-211">2.0</span></span>        |
| <span data-ttu-id="ce792-212">Aplikacja serwera Blazor</span><span class="sxs-lookup"><span data-stu-id="ce792-212">Blazor Server App</span></span>                            | [<span data-ttu-id="ce792-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ce792-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="ce792-214">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-214">[C#]</span></span>         | <span data-ttu-id="ce792-215">Sieć Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="ce792-215">Web/Blazor</span></span>                            | <span data-ttu-id="ce792-216">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-216">3.0</span></span>        |
| <span data-ttu-id="ce792-217">Aplikacja webassembly Blazor</span><span class="sxs-lookup"><span data-stu-id="ce792-217">Blazor WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="ce792-218">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-218">[C#]</span></span>         | <span data-ttu-id="ce792-219">Sieć Web/Blazor/webassembly</span><span class="sxs-lookup"><span data-stu-id="ce792-219">Web/Blazor/WebAssembly</span></span>                            | <span data-ttu-id="ce792-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="ce792-220">3.1.300</span></span>    |
| <span data-ttu-id="ce792-221">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="ce792-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="ce792-222">witrynę</span><span class="sxs-lookup"><span data-stu-id="ce792-222">web</span></span>](#web)                     | <span data-ttu-id="ce792-223">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ce792-223">[C#], F#</span></span>     | <span data-ttu-id="ce792-224">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="ce792-224">Web/Empty</span></span>                             | <span data-ttu-id="ce792-225">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-225">1.0</span></span>        |
| <span data-ttu-id="ce792-226">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="ce792-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="ce792-227">Standard</span><span class="sxs-lookup"><span data-stu-id="ce792-227">mvc</span></span>](#web-options)             | <span data-ttu-id="ce792-228">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ce792-228">[C#], F#</span></span>     | <span data-ttu-id="ce792-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ce792-229">Web/MVC</span></span>                               | <span data-ttu-id="ce792-230">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-230">1.0</span></span>        |
| <span data-ttu-id="ce792-231">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce792-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="ce792-232">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="ce792-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="ce792-233">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-233">[C#]</span></span>         | <span data-ttu-id="ce792-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ce792-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="ce792-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="ce792-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="ce792-236">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="ce792-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="ce792-237">kątow</span><span class="sxs-lookup"><span data-stu-id="ce792-237">angular</span></span>](#spa)                 | <span data-ttu-id="ce792-238">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-238">[C#]</span></span>         | <span data-ttu-id="ce792-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ce792-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ce792-240">2.0</span><span class="sxs-lookup"><span data-stu-id="ce792-240">2.0</span></span>        |
| <span data-ttu-id="ce792-241">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="ce792-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="ce792-242">biern</span><span class="sxs-lookup"><span data-stu-id="ce792-242">react</span></span>](#spa)                   | <span data-ttu-id="ce792-243">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-243">[C#]</span></span>         | <span data-ttu-id="ce792-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ce792-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ce792-245">2.0</span><span class="sxs-lookup"><span data-stu-id="ce792-245">2.0</span></span>        |
| <span data-ttu-id="ce792-246">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="ce792-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="ce792-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="ce792-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="ce792-248">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-248">[C#]</span></span>         | <span data-ttu-id="ce792-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ce792-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="ce792-250">2.0</span><span class="sxs-lookup"><span data-stu-id="ce792-250">2.0</span></span>        |
| <span data-ttu-id="ce792-251">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="ce792-251">Razor Class Library</span></span>                          | [<span data-ttu-id="ce792-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ce792-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="ce792-253">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-253">[C#]</span></span>         | <span data-ttu-id="ce792-254">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="ce792-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="ce792-255">2.1</span><span class="sxs-lookup"><span data-stu-id="ce792-255">2.1</span></span>        |
| <span data-ttu-id="ce792-256">Internetowy interfejs API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce792-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="ce792-257">WebApi</span><span class="sxs-lookup"><span data-stu-id="ce792-257">webapi</span></span>](#webapi)               | <span data-ttu-id="ce792-258">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="ce792-258">[C#], F#</span></span>     | <span data-ttu-id="ce792-259">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ce792-259">Web/WebAPI</span></span>                            | <span data-ttu-id="ce792-260">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-260">1.0</span></span>        |
| <span data-ttu-id="ce792-261">ASP.NET Core usługi gRPC</span><span class="sxs-lookup"><span data-stu-id="ce792-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="ce792-262">grpc</span><span class="sxs-lookup"><span data-stu-id="ce792-262">grpc</span></span>](#web-others)             | <span data-ttu-id="ce792-263">Znajd</span><span class="sxs-lookup"><span data-stu-id="ce792-263">[C#]</span></span>         | <span data-ttu-id="ce792-264">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ce792-264">Web/gRPC</span></span>                              | <span data-ttu-id="ce792-265">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-265">3.0</span></span>        |
| <span data-ttu-id="ce792-266">plik GITIGNORE dotnet</span><span class="sxs-lookup"><span data-stu-id="ce792-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="ce792-267">Config</span><span class="sxs-lookup"><span data-stu-id="ce792-267">Config</span></span>                                | <span data-ttu-id="ce792-268">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-268">3.0</span></span>        |
| <span data-ttu-id="ce792-269">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="ce792-269">global.json file</span></span>                             | [<span data-ttu-id="ce792-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="ce792-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="ce792-271">Config</span><span class="sxs-lookup"><span data-stu-id="ce792-271">Config</span></span>                                | <span data-ttu-id="ce792-272">2.0</span><span class="sxs-lookup"><span data-stu-id="ce792-272">2.0</span></span>        |
| <span data-ttu-id="ce792-273">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="ce792-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="ce792-274">Config</span><span class="sxs-lookup"><span data-stu-id="ce792-274">Config</span></span>                                | <span data-ttu-id="ce792-275">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-275">1.0</span></span>        |
| <span data-ttu-id="ce792-276">Plik manifestu narzędzia lokalnego dotnet</span><span class="sxs-lookup"><span data-stu-id="ce792-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="ce792-277">Config</span><span class="sxs-lookup"><span data-stu-id="ce792-277">Config</span></span>                                | <span data-ttu-id="ce792-278">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-278">3.0</span></span>        |
| <span data-ttu-id="ce792-279">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="ce792-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="ce792-280">Config</span><span class="sxs-lookup"><span data-stu-id="ce792-280">Config</span></span>                                | <span data-ttu-id="ce792-281">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-281">1.0</span></span>        |
| <span data-ttu-id="ce792-282">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ce792-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="ce792-283">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ce792-283">Solution</span></span>                              | <span data-ttu-id="ce792-284">1.0</span><span class="sxs-lookup"><span data-stu-id="ce792-284">1.0</span></span>        |
| <span data-ttu-id="ce792-285">Plik buforu protokołu</span><span class="sxs-lookup"><span data-stu-id="ce792-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="ce792-286">proto</span><span class="sxs-lookup"><span data-stu-id="ce792-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="ce792-287">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="ce792-287">Web/gRPC</span></span>                              | <span data-ttu-id="ce792-288">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="ce792-289">Opcje</span><span class="sxs-lookup"><span data-stu-id="ce792-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="ce792-290">Wyświetla podsumowanie tego, co się stanie w przypadku uruchomienia danego polecenia, jeśli mogłoby to spowodować utworzenie szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="ce792-291">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="ce792-292">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="ce792-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ce792-293">Jest to wymagane, gdy wybrany szablon spowoduje zastąpienie istniejących plików w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="ce792-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ce792-294">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="ce792-294">Prints out help for the command.</span></span> <span data-ttu-id="ce792-295">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="ce792-296">Na przykład `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ce792-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="ce792-297">Instaluje pakiet szablonów z `PATH` lub `NUGET_ID` dostarczone.</span><span class="sxs-lookup"><span data-stu-id="ce792-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ce792-298">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="ce792-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ce792-299">Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje najnowszą stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="ce792-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="ce792-300">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="ce792-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="ce792-301">Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej wersji stabilnej, jeśli nie określono żadnej wersji.</span><span class="sxs-lookup"><span data-stu-id="ce792-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="ce792-302">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ce792-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="ce792-303">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="ce792-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="ce792-304">Jeśli nazwa nie zostanie określona, program wyświetli listę wszystkich szablonów.</span><span class="sxs-lookup"><span data-stu-id="ce792-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="ce792-305">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ce792-305">The language of the template to create.</span></span> <span data-ttu-id="ce792-306">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="ce792-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ce792-307">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="ce792-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ce792-308">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="ce792-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ce792-309">W takich przypadkach należy ująć wartość parametru Language w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="ce792-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="ce792-310">Na przykład `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ce792-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="ce792-311">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ce792-311">The name for the created output.</span></span> <span data-ttu-id="ce792-312">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce792-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="ce792-313">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="ce792-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="ce792-314">Dostępne od wersji .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ce792-315">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ce792-315">Location to place the generated output.</span></span> <span data-ttu-id="ce792-316">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="ce792-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="ce792-317">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="ce792-317">Filters templates based on available types.</span></span> <span data-ttu-id="ce792-318">Wstępnie zdefiniowane wartości to `project` , `item` , i `other` .</span><span class="sxs-lookup"><span data-stu-id="ce792-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="ce792-319">Odinstalowuje pakiet szablonów w `PATH` lub `NUGET_ID` udostępniony.</span><span class="sxs-lookup"><span data-stu-id="ce792-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ce792-320">Gdy `<PATH|NUGET_ID>` wartość nie jest określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="ce792-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="ce792-321">Podczas określania `NUGET_ID` nie należy umieszczać numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="ce792-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="ce792-322">Jeśli nie określisz parametru do tej opcji, polecenie wyświetli listę zainstalowanych szablonów i szczegółowe informacje o nich.</span><span class="sxs-lookup"><span data-stu-id="ce792-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ce792-323">Aby odinstalować szablon przy użyciu programu `PATH` , należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="ce792-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ce792-324">Na przykład *C:/Users/ \<USER> /Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie.</span><span class="sxs-lookup"><span data-stu-id="ce792-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="ce792-325">Nie dołączaj ostatecznego ukośnika katalogu w ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="ce792-326">Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane i instaluje je.</span><span class="sxs-lookup"><span data-stu-id="ce792-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="ce792-327">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="ce792-328">Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ce792-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="ce792-329">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="ce792-330">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="ce792-330">Template options</span></span>

<span data-ttu-id="ce792-331">Każdy szablon projektu może mieć dodatkowe opcje dostępne.</span><span class="sxs-lookup"><span data-stu-id="ce792-331">Each project template may have additional options available.</span></span> <span data-ttu-id="ce792-332">Szablony podstawowe mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="ce792-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="ce792-333">console</span><span class="sxs-lookup"><span data-stu-id="ce792-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-334">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-335">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ce792-336">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ce792-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce792-337">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce792-337">SDK version</span></span> | <span data-ttu-id="ce792-338">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce792-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce792-339">3,1</span><span class="sxs-lookup"><span data-stu-id="ce792-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce792-340">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ce792-341">Ustawia `LangVersion` Właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ce792-342">Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ce792-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ce792-343">Nieobsługiwane dla języka F #.</span><span class="sxs-lookup"><span data-stu-id="ce792-343">Not supported for F#.</span></span> <span data-ttu-id="ce792-344">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce792-345">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ce792-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-346">Jeśli określony, nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="ce792-347">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="ce792-348">określono</span><span class="sxs-lookup"><span data-stu-id="ce792-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-349">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-350">Wartości: `netcoreapp<version>` Aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard<version>` utworzyć bibliotekę klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ce792-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ce792-351">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ce792-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ce792-352">Ustawia `LangVersion` Właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ce792-353">Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ce792-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ce792-354">Nieobsługiwane dla języka F #.</span><span class="sxs-lookup"><span data-stu-id="ce792-354">Not supported for F#.</span></span> <span data-ttu-id="ce792-355">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce792-356">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ce792-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-357">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="ce792-358">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="ce792-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-359">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-360">Wartość domyślna to `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ce792-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ce792-361">Dostępne od wersji .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ce792-362">Ustawia `LangVersion` Właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ce792-363">Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ce792-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ce792-364">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ce792-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-365">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="ce792-366">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="ce792-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="ce792-367">Ustawia `LangVersion` Właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ce792-368">Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ce792-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="ce792-369">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="ce792-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-370">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="ce792-371">proces roboczy, GRPC</span><span class="sxs-lookup"><span data-stu-id="ce792-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-372">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-373">Wartość domyślna to `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="ce792-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="ce792-374">Dostępne od wersji .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce792-375">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-376">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="ce792-377">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="ce792-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-378">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-379">Opcja dostępna od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ce792-380">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ce792-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce792-381">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce792-381">SDK version</span></span> | <span data-ttu-id="ce792-382">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce792-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce792-383">3,1</span><span class="sxs-lookup"><span data-stu-id="ce792-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce792-384">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ce792-385">Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ce792-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-386">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="ce792-387">NUnit</span><span class="sxs-lookup"><span data-stu-id="ce792-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-388">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="ce792-389">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ce792-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce792-390">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce792-390">SDK version</span></span> | <span data-ttu-id="ce792-391">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce792-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce792-392">3,1</span><span class="sxs-lookup"><span data-stu-id="ce792-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce792-393">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce792-394">2.2</span><span class="sxs-lookup"><span data-stu-id="ce792-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="ce792-395">2.1</span><span class="sxs-lookup"><span data-stu-id="ce792-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="ce792-396">Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ce792-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-397">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="ce792-398">stronic</span><span class="sxs-lookup"><span data-stu-id="ce792-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ce792-399">Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ce792-399">Namespace for the generated code.</span></span> <span data-ttu-id="ce792-400">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ce792-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="ce792-401">Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="ce792-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="ce792-402">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="ce792-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="ce792-403">Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ce792-403">Namespace for the generated code.</span></span> <span data-ttu-id="ce792-404">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ce792-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="ce792-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="ce792-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ce792-406">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ce792-406">The type of authentication to use.</span></span> <span data-ttu-id="ce792-407">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ce792-407">The possible values are:</span></span>

  - <span data-ttu-id="ce792-408">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ce792-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ce792-409">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="ce792-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ce792-410">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ce792-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ce792-411">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ce792-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ce792-412">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="ce792-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ce792-413">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ce792-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ce792-414">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce792-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ce792-415">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce792-416">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ce792-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ce792-417">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ce792-418">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ce792-419">Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="ce792-420">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ce792-421">Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ce792-422">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ce792-423">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce792-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ce792-424">Używanie z usługą `SingleOrg` lub `MultiOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce792-425">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ce792-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ce792-426">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-426">The Client ID for this project.</span></span> <span data-ttu-id="ce792-427">Użyj z `IndividualB2C` , `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce792-428">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ce792-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ce792-429">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce792-429">The domain for the directory tenant.</span></span> <span data-ttu-id="ce792-430">Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce792-431">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ce792-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ce792-432">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce792-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ce792-433">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce792-434">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ce792-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ce792-435">Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ce792-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ce792-436">Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce792-437">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ce792-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ce792-438">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce792-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ce792-439">Dotyczy tylko `SingleOrg` `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce792-440">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce792-441">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce792-441">Turns off HTTPS.</span></span> <span data-ttu-id="ce792-442">Ta opcja ma zastosowanie tylko wtedy, gdy,, `Individual` `IndividualB2C` `SingleOrg` lub `MultiOrg` nie są używane w programie `--auth` .</span><span class="sxs-lookup"><span data-stu-id="ce792-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ce792-443">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ce792-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce792-444">Dotyczy tylko `Individual` `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-445">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="ce792-446">web</span><span class="sxs-lookup"><span data-stu-id="ce792-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce792-447">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-448">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-449">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="ce792-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce792-450">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ce792-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce792-451">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce792-451">SDK version</span></span> | <span data-ttu-id="ce792-452">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce792-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce792-453">3,1</span><span class="sxs-lookup"><span data-stu-id="ce792-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce792-454">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce792-455">2.1</span><span class="sxs-lookup"><span data-stu-id="ce792-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ce792-456">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce792-457">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce792-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="ce792-458">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="ce792-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ce792-459">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ce792-459">The type of authentication to use.</span></span> <span data-ttu-id="ce792-460">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ce792-460">The possible values are:</span></span>

  - <span data-ttu-id="ce792-461">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ce792-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ce792-462">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="ce792-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="ce792-463">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ce792-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ce792-464">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ce792-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ce792-465">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="ce792-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="ce792-466">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ce792-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ce792-467">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce792-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ce792-468">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce792-469">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ce792-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ce792-470">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ce792-471">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="ce792-472">Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="ce792-473">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="ce792-474">Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="ce792-475">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ce792-476">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce792-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ce792-477">Używanie z usługą `SingleOrg` lub `MultiOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce792-478">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ce792-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ce792-479">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-479">The Client ID for this project.</span></span> <span data-ttu-id="ce792-480">Użyj z `IndividualB2C` , `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ce792-481">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ce792-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ce792-482">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce792-482">The domain for the directory tenant.</span></span> <span data-ttu-id="ce792-483">Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce792-484">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ce792-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ce792-485">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce792-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ce792-486">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce792-487">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ce792-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="ce792-488">Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ce792-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ce792-489">Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce792-490">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ce792-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ce792-491">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce792-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ce792-492">Dotyczy tylko `SingleOrg` `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce792-493">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce792-494">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce792-494">Turns off HTTPS.</span></span> <span data-ttu-id="ce792-495">Ta opcja ma zastosowanie tylko wtedy, gdy,, `Individual` `IndividualB2C` `SingleOrg` lub `MultiOrg` nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="ce792-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ce792-496">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ce792-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce792-497">Dotyczy tylko `Individual` `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-498">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-499">Opcja dostępna od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ce792-500">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ce792-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce792-501">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce792-501">SDK version</span></span> | <span data-ttu-id="ce792-502">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce792-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce792-503">3,1</span><span class="sxs-lookup"><span data-stu-id="ce792-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce792-504">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="ce792-505">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="ce792-506">Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ce792-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="ce792-507">Opcja nie jest dostępna w programie .NET Core 2,2 i 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="ce792-508">Określa, czy projekt jest skonfigurowany do używania [kompilacji środowiska uruchomieniowego Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) w kompilacjach debugowania.</span><span class="sxs-lookup"><span data-stu-id="ce792-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="ce792-509">Opcja dostępna od wersji .NET Core 3.1.201 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="ce792-510">kątowy, reagowanie</span><span class="sxs-lookup"><span data-stu-id="ce792-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ce792-511">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ce792-511">The type of authentication to use.</span></span> <span data-ttu-id="ce792-512">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="ce792-513">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ce792-513">The possible values are:</span></span>

  - <span data-ttu-id="ce792-514">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ce792-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ce792-515">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="ce792-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce792-516">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-517">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce792-518">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce792-518">Turns off HTTPS.</span></span> <span data-ttu-id="ce792-519">Ta opcja ma zastosowanie tylko wtedy, gdy uwierzytelnianie jest `None` .</span><span class="sxs-lookup"><span data-stu-id="ce792-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ce792-520">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ce792-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce792-521">Dotyczy tylko `Individual` `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce792-522">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-523">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-524">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="ce792-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce792-525">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ce792-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce792-526">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce792-526">SDK version</span></span> | <span data-ttu-id="ce792-527">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce792-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce792-528">3,1</span><span class="sxs-lookup"><span data-stu-id="ce792-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce792-529">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce792-530">2.1</span><span class="sxs-lookup"><span data-stu-id="ce792-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="ce792-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="ce792-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce792-532">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-533">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-534">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="ce792-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce792-535">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ce792-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce792-536">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce792-536">SDK version</span></span> | <span data-ttu-id="ce792-537">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce792-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce792-538">3,1</span><span class="sxs-lookup"><span data-stu-id="ce792-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce792-539">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce792-540">2.1</span><span class="sxs-lookup"><span data-stu-id="ce792-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="ce792-541">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce792-542">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce792-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="ce792-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="ce792-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="ce792-544">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="ce792-545">Obsługuje dodawanie tradycyjnych stron Razor i widoków oprócz składników do tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ce792-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="ce792-546">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="ce792-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="ce792-547">WebApi</span><span class="sxs-lookup"><span data-stu-id="ce792-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="ce792-548">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ce792-548">The type of authentication to use.</span></span> <span data-ttu-id="ce792-549">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ce792-549">The possible values are:</span></span>

  - <span data-ttu-id="ce792-550">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="ce792-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="ce792-551">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ce792-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="ce792-552">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="ce792-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="ce792-553">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ce792-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="ce792-554">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce792-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ce792-555">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ce792-556">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ce792-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="ce792-557">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ce792-558">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="ce792-559">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce792-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ce792-560">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce792-561">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ce792-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="ce792-562">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-562">The Client ID for this project.</span></span> <span data-ttu-id="ce792-563">Używanie z usługą `IndividualB2C` lub `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ce792-564">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ce792-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="ce792-565">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce792-565">The domain for the directory tenant.</span></span> <span data-ttu-id="ce792-566">Używanie z usługą `IndividualB2C` lub `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ce792-567">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ce792-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="ce792-568">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ce792-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ce792-569">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="ce792-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ce792-570">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ce792-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="ce792-571">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce792-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="ce792-572">Dotyczy tylko `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="ce792-573">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="ce792-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="ce792-574">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce792-574">Turns off HTTPS.</span></span> <span data-ttu-id="ce792-575">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="ce792-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ce792-576">Ta opcja ma zastosowanie tylko wtedy `IndividualB2C` , gdy lub `SingleOrg` nie są używane do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="ce792-577">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="ce792-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ce792-578">Dotyczy tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ce792-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ce792-579">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="ce792-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ce792-580">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="ce792-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="ce792-581">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="ce792-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="ce792-582">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce792-582">SDK version</span></span> | <span data-ttu-id="ce792-583">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ce792-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="ce792-584">3,1</span><span class="sxs-lookup"><span data-stu-id="ce792-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="ce792-585">3.0</span><span class="sxs-lookup"><span data-stu-id="ce792-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="ce792-586">2.1</span><span class="sxs-lookup"><span data-stu-id="ce792-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="ce792-587">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="ce792-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="ce792-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="ce792-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="ce792-589">Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="ce792-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="ce792-590">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ce792-590">Examples</span></span>

- <span data-ttu-id="ce792-591">Utwórz projekt aplikacji konsolowej w języku C#, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="ce792-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="ce792-592">Utwórz projekt aplikacji konsolowej F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ce792-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="ce792-593">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ce792-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="ce792-594">Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="ce792-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="ce792-595">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="ce792-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="ce792-596">Wyświetl listę wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):</span><span class="sxs-lookup"><span data-stu-id="ce792-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="ce792-597">Wyświetl listę wszystkich szablonów pasujących *do* podciągu.</span><span class="sxs-lookup"><span data-stu-id="ce792-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="ce792-598">Nie znaleziono dokładnego dopasowania, więc Dopasowywanie podciągów działa w odniesieniu do kolumn krótkich nazw i nazw.</span><span class="sxs-lookup"><span data-stu-id="ce792-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="ce792-599">Podjęto próbę wywołania szablonu zgodnego z parametrem *ng*.</span><span class="sxs-lookup"><span data-stu-id="ce792-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="ce792-600">Jeśli nie można ustalić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są dopasowań częściowych.</span><span class="sxs-lookup"><span data-stu-id="ce792-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="ce792-601">Zainstaluj wersję 2,0 szablonów SPA dla ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="ce792-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="ce792-602">Wyświetl listę zainstalowanych szablonów i szczegółowe informacje o nich, w tym sposoby ich odinstalowywania:</span><span class="sxs-lookup"><span data-stu-id="ce792-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="ce792-603">Utwórz plik *Global. JSON* w bieżącym katalogu, ustawiając wersję zestawu SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="ce792-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="ce792-604">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce792-604">See also</span></span>

- [<span data-ttu-id="ce792-605">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="ce792-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="ce792-606">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="ce792-606">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="ce792-607">dotnet/dotnet-Template-przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="ce792-607">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="ce792-608">Dostępne szablony dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="ce792-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
