---
title: polecenie dotnet New
description: Polecenie dotnet New umożliwia tworzenie nowych projektów platformy .NET Core na podstawie określonego szablonu.
ms.date: 04/10/2020
ms.openlocfilehash: 9a68baafa7ac3e6ad2fdc8f1c6e8621d6e15f1ff
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506860"
---
# <a name="dotnet-new"></a><span data-ttu-id="67bfe-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="67bfe-103">dotnet new</span></span>

<span data-ttu-id="67bfe-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="67bfe-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="67bfe-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="67bfe-105">Name</span></span>

<span data-ttu-id="67bfe-106">`dotnet new`-Tworzy nowy projekt, plik konfiguracji lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="67bfe-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="67bfe-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="67bfe-108">Opis</span><span class="sxs-lookup"><span data-stu-id="67bfe-108">Description</span></span>

<span data-ttu-id="67bfe-109">`dotnet new` Polecenie tworzy projekt .NET Core lub inne artefakty na podstawie szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="67bfe-110">Polecenie wywołuje [aparat szablonu](https://github.com/dotnet/templating) , aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="67bfe-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="67bfe-111">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="67bfe-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="67bfe-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="67bfe-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="67bfe-113">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="67bfe-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="67bfe-114">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="67bfe-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="67bfe-115">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="67bfe-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="67bfe-116">Można uruchomić `dotnet new --list` lub `dotnet new -l` wyświetlić listę wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="67bfe-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="67bfe-117">Jeśli `TEMPLATE` wartość nie jest dokładnym dopasowaniem do tekstu w kolumnie **Szablony** lub **krótka nazwa** z zwróconej tabeli, do tych dwóch kolumn jest wykonywane dopasowanie podciągu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="67bfe-118">Począwszy od zestawu SDK platformy .NET Core 3,0, interfejs wiersza `dotnet new` polecenia wyszukuje szablony w NuGet.org, gdy wywoła polecenie w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="67bfe-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="67bfe-119">Jeśli interfejs wiersza polecenia nie może znaleźć dopasowania szablonu podczas wywoływania `dotnet new`, nie nawet częściowej.</span><span class="sxs-lookup"><span data-stu-id="67bfe-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="67bfe-120">Jeśli jest dostępna nowsza wersja szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="67bfe-121">W takim przypadku projekt lub artefakt jest tworzony, ale interfejs wiersza polecenia ostrzega użytkownika o zaktualizowanej wersji szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="67bfe-122">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane wraz z zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="67bfe-123">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="67bfe-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="67bfe-124">Kliknij link krótkiej nazwy, aby wyświetlić opcje konkretnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="67bfe-125">Szablony</span><span class="sxs-lookup"><span data-stu-id="67bfe-125">Templates</span></span>                                    | <span data-ttu-id="67bfe-126">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="67bfe-126">Short name</span></span>                      | <span data-ttu-id="67bfe-127">Język</span><span class="sxs-lookup"><span data-stu-id="67bfe-127">Language</span></span>     | <span data-ttu-id="67bfe-128">Tagi</span><span class="sxs-lookup"><span data-stu-id="67bfe-128">Tags</span></span>                                  | <span data-ttu-id="67bfe-129">Wraca</span><span class="sxs-lookup"><span data-stu-id="67bfe-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="67bfe-130">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="67bfe-130">Console Application</span></span>                          | [<span data-ttu-id="67bfe-131">konsoli</span><span class="sxs-lookup"><span data-stu-id="67bfe-131">console</span></span>](#console)             | <span data-ttu-id="67bfe-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="67bfe-132">[C#], F#, VB</span></span> | <span data-ttu-id="67bfe-133">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="67bfe-133">Common/Console</span></span>                        | <span data-ttu-id="67bfe-134">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-134">1.0</span></span>        |
| <span data-ttu-id="67bfe-135">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="67bfe-135">Class library</span></span>                                | [<span data-ttu-id="67bfe-136">określono</span><span class="sxs-lookup"><span data-stu-id="67bfe-136">classlib</span></span>](#classlib)           | <span data-ttu-id="67bfe-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="67bfe-137">[C#], F#, VB</span></span> | <span data-ttu-id="67bfe-138">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="67bfe-138">Common/Library</span></span>                        | <span data-ttu-id="67bfe-139">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-139">1.0</span></span>        |
| <span data-ttu-id="67bfe-140">Aplikacja WPF</span><span class="sxs-lookup"><span data-stu-id="67bfe-140">WPF Application</span></span>                              | [<span data-ttu-id="67bfe-141">kodow</span><span class="sxs-lookup"><span data-stu-id="67bfe-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="67bfe-142">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-142">[C#]</span></span>         | <span data-ttu-id="67bfe-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="67bfe-143">Common/WPF</span></span>                            | <span data-ttu-id="67bfe-144">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-144">3.0</span></span>        |
| <span data-ttu-id="67bfe-145">Biblioteka klas WPF</span><span class="sxs-lookup"><span data-stu-id="67bfe-145">WPF Class library</span></span>                            | [<span data-ttu-id="67bfe-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="67bfe-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="67bfe-147">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-147">[C#]</span></span>         | <span data-ttu-id="67bfe-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="67bfe-148">Common/WPF</span></span>                            | <span data-ttu-id="67bfe-149">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-149">3.0</span></span>        |
| <span data-ttu-id="67bfe-150">Biblioteka kontrolek niestandardowych WPF</span><span class="sxs-lookup"><span data-stu-id="67bfe-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="67bfe-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="67bfe-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="67bfe-152">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-152">[C#]</span></span>         | <span data-ttu-id="67bfe-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="67bfe-153">Common/WPF</span></span>                            | <span data-ttu-id="67bfe-154">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-154">3.0</span></span>        |
| <span data-ttu-id="67bfe-155">Biblioteka kontrolek użytkownika WPF</span><span class="sxs-lookup"><span data-stu-id="67bfe-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="67bfe-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="67bfe-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="67bfe-157">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-157">[C#]</span></span>         | <span data-ttu-id="67bfe-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="67bfe-158">Common/WPF</span></span>                            | <span data-ttu-id="67bfe-159">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-159">3.0</span></span>        |
| <span data-ttu-id="67bfe-160">Aplikacja Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="67bfe-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="67bfe-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="67bfe-161">winforms</span></span>](#winforms)           | <span data-ttu-id="67bfe-162">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-162">[C#]</span></span>         | <span data-ttu-id="67bfe-163">Typowe/WinForms</span><span class="sxs-lookup"><span data-stu-id="67bfe-163">Common/WinForms</span></span>                       | <span data-ttu-id="67bfe-164">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-164">3.0</span></span>        |
| <span data-ttu-id="67bfe-165">Biblioteka klas Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="67bfe-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="67bfe-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="67bfe-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="67bfe-167">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-167">[C#]</span></span>         | <span data-ttu-id="67bfe-168">Typowe/WinForms</span><span class="sxs-lookup"><span data-stu-id="67bfe-168">Common/WinForms</span></span>                       | <span data-ttu-id="67bfe-169">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-169">3.0</span></span>        |
| <span data-ttu-id="67bfe-170">Usługa procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="67bfe-170">Worker Service</span></span>                               | [<span data-ttu-id="67bfe-171">odpowiedzialn</span><span class="sxs-lookup"><span data-stu-id="67bfe-171">worker</span></span>](#web-others)           | <span data-ttu-id="67bfe-172">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-172">[C#]</span></span>         | <span data-ttu-id="67bfe-173">Common/Worker/sieć Web</span><span class="sxs-lookup"><span data-stu-id="67bfe-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="67bfe-174">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-174">3.0</span></span>        |
| <span data-ttu-id="67bfe-175">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="67bfe-175">Unit Test Project</span></span>                            | [<span data-ttu-id="67bfe-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="67bfe-176">mstest</span></span>](#test)                 | <span data-ttu-id="67bfe-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="67bfe-177">[C#], F#, VB</span></span> | <span data-ttu-id="67bfe-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="67bfe-178">Test/MSTest</span></span>                           | <span data-ttu-id="67bfe-179">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-179">1.0</span></span>        |
| <span data-ttu-id="67bfe-180">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="67bfe-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="67bfe-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="67bfe-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="67bfe-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="67bfe-182">[C#], F#, VB</span></span> | <span data-ttu-id="67bfe-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="67bfe-183">Test/NUnit</span></span>                            | <span data-ttu-id="67bfe-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="67bfe-184">2.1.400</span></span>    |
| <span data-ttu-id="67bfe-185">Element testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="67bfe-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="67bfe-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="67bfe-186">[C#], F#, VB</span></span> | <span data-ttu-id="67bfe-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="67bfe-187">Test/NUnit</span></span>                            | <span data-ttu-id="67bfe-188">2.2</span><span class="sxs-lookup"><span data-stu-id="67bfe-188">2.2</span></span>        |
| <span data-ttu-id="67bfe-189">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="67bfe-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="67bfe-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="67bfe-190">xunit</span></span>](#test)                  | <span data-ttu-id="67bfe-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="67bfe-191">[C#], F#, VB</span></span> | <span data-ttu-id="67bfe-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="67bfe-192">Test/xUnit</span></span>                            | <span data-ttu-id="67bfe-193">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-193">1.0</span></span>        |
| <span data-ttu-id="67bfe-194">Składnik Razor</span><span class="sxs-lookup"><span data-stu-id="67bfe-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="67bfe-195">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-195">[C#]</span></span>         | <span data-ttu-id="67bfe-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="67bfe-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="67bfe-197">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-197">3.0</span></span>        |
| <span data-ttu-id="67bfe-198">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="67bfe-198">Razor Page</span></span>                                   | [<span data-ttu-id="67bfe-199">stronic</span><span class="sxs-lookup"><span data-stu-id="67bfe-199">page</span></span>](#page)                   | <span data-ttu-id="67bfe-200">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-200">[C#]</span></span>         | <span data-ttu-id="67bfe-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="67bfe-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="67bfe-202">2.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-202">2.0</span></span>        |
| <span data-ttu-id="67bfe-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="67bfe-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="67bfe-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="67bfe-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="67bfe-205">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-205">[C#]</span></span>         | <span data-ttu-id="67bfe-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="67bfe-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="67bfe-207">2.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-207">2.0</span></span>        |
| <span data-ttu-id="67bfe-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="67bfe-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="67bfe-209">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-209">[C#]</span></span>         | <span data-ttu-id="67bfe-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="67bfe-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="67bfe-211">2.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-211">2.0</span></span>        |
| <span data-ttu-id="67bfe-212">Aplikacja serwera Blazor</span><span class="sxs-lookup"><span data-stu-id="67bfe-212">Blazor Server App</span></span>                            | [<span data-ttu-id="67bfe-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="67bfe-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="67bfe-214">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-214">[C#]</span></span>         | <span data-ttu-id="67bfe-215">Sieć Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="67bfe-215">Web/Blazor</span></span>                            | <span data-ttu-id="67bfe-216">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-216">3.0</span></span>        |
| <span data-ttu-id="67bfe-217">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="67bfe-217">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="67bfe-218">witrynę</span><span class="sxs-lookup"><span data-stu-id="67bfe-218">web</span></span>](#web)                     | <span data-ttu-id="67bfe-219">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="67bfe-219">[C#], F#</span></span>     | <span data-ttu-id="67bfe-220">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="67bfe-220">Web/Empty</span></span>                             | <span data-ttu-id="67bfe-221">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-221">1.0</span></span>        |
| <span data-ttu-id="67bfe-222">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="67bfe-222">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="67bfe-223">Standard</span><span class="sxs-lookup"><span data-stu-id="67bfe-223">mvc</span></span>](#web-options)             | <span data-ttu-id="67bfe-224">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="67bfe-224">[C#], F#</span></span>     | <span data-ttu-id="67bfe-225">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="67bfe-225">Web/MVC</span></span>                               | <span data-ttu-id="67bfe-226">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-226">1.0</span></span>        |
| <span data-ttu-id="67bfe-227">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67bfe-227">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="67bfe-228">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="67bfe-228">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="67bfe-229">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-229">[C#]</span></span>         | <span data-ttu-id="67bfe-230">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="67bfe-230">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="67bfe-231">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="67bfe-231">2.2, 2.0</span></span>   |
| <span data-ttu-id="67bfe-232">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="67bfe-232">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="67bfe-233">kątow</span><span class="sxs-lookup"><span data-stu-id="67bfe-233">angular</span></span>](#spa)                 | <span data-ttu-id="67bfe-234">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-234">[C#]</span></span>         | <span data-ttu-id="67bfe-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="67bfe-235">Web/MVC/SPA</span></span>                           | <span data-ttu-id="67bfe-236">2.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-236">2.0</span></span>        |
| <span data-ttu-id="67bfe-237">ASP.NET Core z usługą reaguj. js</span><span class="sxs-lookup"><span data-stu-id="67bfe-237">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="67bfe-238">biern</span><span class="sxs-lookup"><span data-stu-id="67bfe-238">react</span></span>](#spa)                   | <span data-ttu-id="67bfe-239">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-239">[C#]</span></span>         | <span data-ttu-id="67bfe-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="67bfe-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="67bfe-241">2.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-241">2.0</span></span>        |
| <span data-ttu-id="67bfe-242">ASP.NET Core z reakcjęmi. js i Redux</span><span class="sxs-lookup"><span data-stu-id="67bfe-242">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="67bfe-243">reactredux</span><span class="sxs-lookup"><span data-stu-id="67bfe-243">reactredux</span></span>](#reactredux)       | <span data-ttu-id="67bfe-244">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-244">[C#]</span></span>         | <span data-ttu-id="67bfe-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="67bfe-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="67bfe-246">2.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-246">2.0</span></span>        |
| <span data-ttu-id="67bfe-247">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="67bfe-247">Razor Class Library</span></span>                          | [<span data-ttu-id="67bfe-248">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="67bfe-248">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="67bfe-249">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-249">[C#]</span></span>         | <span data-ttu-id="67bfe-250">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="67bfe-250">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="67bfe-251">2.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-251">2.1</span></span>        |
| <span data-ttu-id="67bfe-252">Internetowy interfejs API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67bfe-252">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="67bfe-253">WebApi</span><span class="sxs-lookup"><span data-stu-id="67bfe-253">webapi</span></span>](#webapi)               | <span data-ttu-id="67bfe-254">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="67bfe-254">[C#], F#</span></span>     | <span data-ttu-id="67bfe-255">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="67bfe-255">Web/WebAPI</span></span>                            | <span data-ttu-id="67bfe-256">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-256">1.0</span></span>        |
| <span data-ttu-id="67bfe-257">ASP.NET Core usługi gRPC</span><span class="sxs-lookup"><span data-stu-id="67bfe-257">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="67bfe-258">grpc</span><span class="sxs-lookup"><span data-stu-id="67bfe-258">grpc</span></span>](#web-others)             | <span data-ttu-id="67bfe-259">Znajd</span><span class="sxs-lookup"><span data-stu-id="67bfe-259">[C#]</span></span>         | <span data-ttu-id="67bfe-260">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="67bfe-260">Web/gRPC</span></span>                              | <span data-ttu-id="67bfe-261">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-261">3.0</span></span>        |
| <span data-ttu-id="67bfe-262">plik GITIGNORE dotnet</span><span class="sxs-lookup"><span data-stu-id="67bfe-262">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="67bfe-263">Config</span><span class="sxs-lookup"><span data-stu-id="67bfe-263">Config</span></span>                                | <span data-ttu-id="67bfe-264">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-264">3.0</span></span>        |
| <span data-ttu-id="67bfe-265">plik Global. JSON</span><span class="sxs-lookup"><span data-stu-id="67bfe-265">global.json file</span></span>                             | [<span data-ttu-id="67bfe-266">globaljson</span><span class="sxs-lookup"><span data-stu-id="67bfe-266">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="67bfe-267">Config</span><span class="sxs-lookup"><span data-stu-id="67bfe-267">Config</span></span>                                | <span data-ttu-id="67bfe-268">2.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-268">2.0</span></span>        |
| <span data-ttu-id="67bfe-269">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="67bfe-269">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="67bfe-270">Config</span><span class="sxs-lookup"><span data-stu-id="67bfe-270">Config</span></span>                                | <span data-ttu-id="67bfe-271">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-271">1.0</span></span>        |
| <span data-ttu-id="67bfe-272">Plik manifestu narzędzia lokalnego dotnet</span><span class="sxs-lookup"><span data-stu-id="67bfe-272">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="67bfe-273">Config</span><span class="sxs-lookup"><span data-stu-id="67bfe-273">Config</span></span>                                | <span data-ttu-id="67bfe-274">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-274">3.0</span></span>        |
| <span data-ttu-id="67bfe-275">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="67bfe-275">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="67bfe-276">Config</span><span class="sxs-lookup"><span data-stu-id="67bfe-276">Config</span></span>                                | <span data-ttu-id="67bfe-277">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-277">1.0</span></span>        |
| <span data-ttu-id="67bfe-278">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="67bfe-278">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="67bfe-279">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="67bfe-279">Solution</span></span>                              | <span data-ttu-id="67bfe-280">1.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-280">1.0</span></span>        |
| <span data-ttu-id="67bfe-281">Plik buforu protokołu</span><span class="sxs-lookup"><span data-stu-id="67bfe-281">Protocol Buffer File</span></span>                         | [<span data-ttu-id="67bfe-282">proto</span><span class="sxs-lookup"><span data-stu-id="67bfe-282">proto</span></span>](#namespace)             |              | <span data-ttu-id="67bfe-283">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="67bfe-283">Web/gRPC</span></span>                              | <span data-ttu-id="67bfe-284">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-284">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="67bfe-285">Opcje</span><span class="sxs-lookup"><span data-stu-id="67bfe-285">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="67bfe-286">Wyświetla podsumowanie tego, co się stanie w przypadku uruchomienia danego polecenia, jeśli mogłoby to spowodować utworzenie szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-286">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="67bfe-287">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-287">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="67bfe-288">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="67bfe-288">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="67bfe-289">Jest to wymagane, gdy wybrany szablon spowoduje zastąpienie istniejących plików w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="67bfe-289">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="67bfe-290">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="67bfe-290">Prints out help for the command.</span></span> <span data-ttu-id="67bfe-291">Może być wywoływana dla samego `dotnet new` polecenia lub dla dowolnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-291">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="67bfe-292">Na przykład `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-292">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="67bfe-293">Instaluje pakiet szablonów z `PATH` lub `NUGET_ID` dostarczone.</span><span class="sxs-lookup"><span data-stu-id="67bfe-293">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="67bfe-294">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-294">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="67bfe-295">Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje najnowszą stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-295">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="67bfe-296">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="67bfe-296">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="67bfe-297">Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej wersji stabilnej, jeśli nie określono żadnej wersji.</span><span class="sxs-lookup"><span data-stu-id="67bfe-297">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="67bfe-298">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="67bfe-298">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="67bfe-299">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="67bfe-299">Lists templates containing the specified name.</span></span> <span data-ttu-id="67bfe-300">Jeśli nazwa nie zostanie określona, program wyświetli listę wszystkich szablonów.</span><span class="sxs-lookup"><span data-stu-id="67bfe-300">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="67bfe-301">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="67bfe-301">The language of the template to create.</span></span> <span data-ttu-id="67bfe-302">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="67bfe-302">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="67bfe-303">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="67bfe-303">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="67bfe-304">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="67bfe-304">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="67bfe-305">W takich przypadkach należy ująć wartość parametru Language w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="67bfe-305">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="67bfe-306">Na przykład `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-306">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="67bfe-307">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="67bfe-307">The name for the created output.</span></span> <span data-ttu-id="67bfe-308">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-308">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="67bfe-309">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="67bfe-309">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="67bfe-310">Dostępne od wersji .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-310">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="67bfe-311">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="67bfe-311">Location to place the generated output.</span></span> <span data-ttu-id="67bfe-312">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="67bfe-312">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="67bfe-313">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="67bfe-313">Filters templates based on available types.</span></span> <span data-ttu-id="67bfe-314">Wstępnie zdefiniowane wartości `project`to `item`,, `other`i.</span><span class="sxs-lookup"><span data-stu-id="67bfe-314">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="67bfe-315">Odinstalowuje pakiet szablonów w `PATH` lub `NUGET_ID` udostępniony.</span><span class="sxs-lookup"><span data-stu-id="67bfe-315">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="67bfe-316">Gdy `<PATH|NUGET_ID>` wartość nie jest określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="67bfe-316">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="67bfe-317">Podczas określania `NUGET_ID`nie należy umieszczać numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="67bfe-317">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="67bfe-318">Jeśli nie określisz parametru do tej opcji, polecenie wyświetli listę zainstalowanych szablonów i szczegółowe informacje o nich.</span><span class="sxs-lookup"><span data-stu-id="67bfe-318">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="67bfe-319">Aby odinstalować szablon przy użyciu programu `PATH`, należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="67bfe-319">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="67bfe-320">Na przykład *C:/Users/\<User>/Documents/templates/garciasoftware.consoletemplate.CSharp* będzie działał, ale */GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="67bfe-320">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="67bfe-321">Nie dołączaj ostatecznego ukośnika katalogu w ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-321">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="67bfe-322">Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane i instaluje je.</span><span class="sxs-lookup"><span data-stu-id="67bfe-322">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="67bfe-323">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-323">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="67bfe-324">Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="67bfe-324">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="67bfe-325">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-325">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="67bfe-326">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="67bfe-326">Template options</span></span>

<span data-ttu-id="67bfe-327">Każdy szablon projektu może mieć dodatkowe opcje dostępne.</span><span class="sxs-lookup"><span data-stu-id="67bfe-327">Each project template may have additional options available.</span></span> <span data-ttu-id="67bfe-328">Szablony podstawowe mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="67bfe-328">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="67bfe-329">console</span><span class="sxs-lookup"><span data-stu-id="67bfe-329">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-330">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-330">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-331">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-331">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="67bfe-332">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="67bfe-332">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="67bfe-333">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="67bfe-333">SDK version</span></span> | <span data-ttu-id="67bfe-334">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="67bfe-334">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="67bfe-335">3.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-335">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="67bfe-336">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-336">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="67bfe-337">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-337">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="67bfe-338">Na przykład użyj `--langVersion 7.3` , aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="67bfe-338">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="67bfe-339">Nieobsługiwane dla języka F #.</span><span class="sxs-lookup"><span data-stu-id="67bfe-339">Not supported for F#.</span></span> <span data-ttu-id="67bfe-340">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-340">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="67bfe-341">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="67bfe-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-342">Jeśli określony, nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-342">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="67bfe-343">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-343">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="67bfe-344">określono</span><span class="sxs-lookup"><span data-stu-id="67bfe-344">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-345">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-345">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-346">Wartości: `netcoreapp<version>` aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard<version>` utworzyć bibliotekę klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="67bfe-346">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="67bfe-347">Wartością domyślną jest `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-347">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="67bfe-348">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-348">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="67bfe-349">Na przykład użyj `--langVersion 7.3` , aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="67bfe-349">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="67bfe-350">Nieobsługiwane dla języka F #.</span><span class="sxs-lookup"><span data-stu-id="67bfe-350">Not supported for F#.</span></span> <span data-ttu-id="67bfe-351">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-351">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="67bfe-352">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="67bfe-352">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-353">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-353">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="67bfe-354">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="67bfe-354">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-355">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-355">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-356">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-356">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="67bfe-357">Dostępne od wersji .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-357">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="67bfe-358">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-358">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="67bfe-359">Na przykład użyj `--langVersion 7.3` , aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="67bfe-359">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="67bfe-360">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="67bfe-360">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-361">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-361">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="67bfe-362">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="67bfe-362">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="67bfe-363">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-363">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="67bfe-364">Na przykład użyj `--langVersion 7.3` , aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="67bfe-364">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="67bfe-365">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="67bfe-365">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-366">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-366">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="67bfe-367">proces roboczy, GRPC</span><span class="sxs-lookup"><span data-stu-id="67bfe-367">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-368">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-368">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-369">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-369">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="67bfe-370">Dostępne od wersji .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-370">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="67bfe-371">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-371">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-372">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-372">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="67bfe-373">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="67bfe-373">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-374">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-374">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-375">Opcja dostępna od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-375">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="67bfe-376">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="67bfe-376">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="67bfe-377">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="67bfe-377">SDK version</span></span> | <span data-ttu-id="67bfe-378">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="67bfe-378">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="67bfe-379">3.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-379">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="67bfe-380">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-380">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="67bfe-381">Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="67bfe-381">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-382">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-382">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="67bfe-383">NUnit</span><span class="sxs-lookup"><span data-stu-id="67bfe-383">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-384">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-384">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="67bfe-385">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="67bfe-385">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="67bfe-386">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="67bfe-386">SDK version</span></span> | <span data-ttu-id="67bfe-387">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="67bfe-387">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="67bfe-388">3.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-388">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="67bfe-389">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-389">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="67bfe-390">2.2</span><span class="sxs-lookup"><span data-stu-id="67bfe-390">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="67bfe-391">2.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-391">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="67bfe-392">Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="67bfe-392">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-393">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-393">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="67bfe-394">stronic</span><span class="sxs-lookup"><span data-stu-id="67bfe-394">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="67bfe-395">Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-395">Namespace for the generated code.</span></span> <span data-ttu-id="67bfe-396">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-396">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="67bfe-397">Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="67bfe-397">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="67bfe-398">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="67bfe-398">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="67bfe-399">Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-399">Namespace for the generated code.</span></span> <span data-ttu-id="67bfe-400">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-400">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="67bfe-401">blazorserver</span><span class="sxs-lookup"><span data-stu-id="67bfe-401">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="67bfe-402">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="67bfe-402">The type of authentication to use.</span></span> <span data-ttu-id="67bfe-403">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="67bfe-403">The possible values are:</span></span>

  - <span data-ttu-id="67bfe-404">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="67bfe-404">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="67bfe-405">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="67bfe-405">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="67bfe-406">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="67bfe-406">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="67bfe-407">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="67bfe-407">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="67bfe-408">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="67bfe-408">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="67bfe-409">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="67bfe-409">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="67bfe-410">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-410">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="67bfe-411">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="67bfe-412">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="67bfe-413">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-413">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="67bfe-414">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-414">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="67bfe-415">Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-415">The reset password policy ID for this project.</span></span> <span data-ttu-id="67bfe-416">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-416">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="67bfe-417">Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-417">The edit profile policy ID for this project.</span></span> <span data-ttu-id="67bfe-418">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-418">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="67bfe-419">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-419">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="67bfe-420">Używanie z `SingleOrg` usługą `MultiOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-420">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="67bfe-421">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-421">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="67bfe-422">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-422">The Client ID for this project.</span></span> <span data-ttu-id="67bfe-423">Użyj z `IndividualB2C`, `SingleOrg`lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-423">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="67bfe-424">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-424">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="67bfe-425">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-425">The domain for the directory tenant.</span></span> <span data-ttu-id="67bfe-426">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-426">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67bfe-427">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-427">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="67bfe-428">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-428">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="67bfe-429">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-429">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67bfe-430">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-430">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="67bfe-431">Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-431">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="67bfe-432">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-432">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67bfe-433">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-433">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="67bfe-434">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-434">Allows this application read-access to the directory.</span></span> <span data-ttu-id="67bfe-435">Dotyczy `SingleOrg` tylko `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-435">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="67bfe-436">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-436">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="67bfe-437">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="67bfe-437">Turns off HTTPS.</span></span> <span data-ttu-id="67bfe-438">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C`, `SingleOrg`gdy, `MultiOrg` , lub nie są `--auth`używane w programie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-438">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="67bfe-439">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="67bfe-439">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="67bfe-440">Dotyczy `Individual` tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-440">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-441">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-441">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="67bfe-442">web</span><span class="sxs-lookup"><span data-stu-id="67bfe-442">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="67bfe-443">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-443">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-444">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-444">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-445">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="67bfe-445">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="67bfe-446">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="67bfe-446">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="67bfe-447">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="67bfe-447">SDK version</span></span> | <span data-ttu-id="67bfe-448">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="67bfe-448">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="67bfe-449">3.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-449">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="67bfe-450">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-450">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="67bfe-451">2.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-451">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="67bfe-452">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-452">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="67bfe-453">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="67bfe-453">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="67bfe-454">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="67bfe-454">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="67bfe-455">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="67bfe-455">The type of authentication to use.</span></span> <span data-ttu-id="67bfe-456">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="67bfe-456">The possible values are:</span></span>

  - <span data-ttu-id="67bfe-457">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="67bfe-457">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="67bfe-458">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="67bfe-458">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="67bfe-459">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="67bfe-459">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="67bfe-460">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="67bfe-460">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="67bfe-461">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="67bfe-461">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="67bfe-462">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="67bfe-462">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="67bfe-463">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-463">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="67bfe-464">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-464">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="67bfe-465">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-465">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="67bfe-466">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-466">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="67bfe-467">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-467">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="67bfe-468">Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-468">The reset password policy ID for this project.</span></span> <span data-ttu-id="67bfe-469">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-469">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="67bfe-470">Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-470">The edit profile policy ID for this project.</span></span> <span data-ttu-id="67bfe-471">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-471">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="67bfe-472">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-472">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="67bfe-473">Używanie z `SingleOrg` usługą `MultiOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-473">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="67bfe-474">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-474">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="67bfe-475">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-475">The Client ID for this project.</span></span> <span data-ttu-id="67bfe-476">Użyj z `IndividualB2C`, `SingleOrg`lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-476">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="67bfe-477">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-477">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="67bfe-478">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-478">The domain for the directory tenant.</span></span> <span data-ttu-id="67bfe-479">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67bfe-480">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-480">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="67bfe-481">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-481">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="67bfe-482">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-482">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67bfe-483">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-483">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="67bfe-484">Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-484">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="67bfe-485">Używanie z `SingleOrg` usługą `IndividualB2C` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-485">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67bfe-486">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-486">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="67bfe-487">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-487">Allows this application read-access to the directory.</span></span> <span data-ttu-id="67bfe-488">Dotyczy `SingleOrg` tylko `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-488">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="67bfe-489">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-489">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="67bfe-490">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="67bfe-490">Turns off HTTPS.</span></span> <span data-ttu-id="67bfe-491">Ta opcja ma zastosowanie tylko `Individual`wtedy `IndividualB2C`, `SingleOrg`gdy, `MultiOrg` , lub nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="67bfe-491">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="67bfe-492">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="67bfe-492">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="67bfe-493">Dotyczy `Individual` tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-493">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-494">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-494">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-495">Opcja dostępna od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-495">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="67bfe-496">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="67bfe-496">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="67bfe-497">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="67bfe-497">SDK version</span></span> | <span data-ttu-id="67bfe-498">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="67bfe-498">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="67bfe-499">3.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-499">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="67bfe-500">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-500">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="67bfe-501">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-501">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="67bfe-502">Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-502">Includes BrowserLink in the project.</span></span> <span data-ttu-id="67bfe-503">Opcja nie jest dostępna w programie .NET Core 2,2 i 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-503">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="67bfe-504">Określa, czy projekt jest skonfigurowany do używania [kompilacji środowiska uruchomieniowego Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) w kompilacjach debugowania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-504">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="67bfe-505">Opcja dostępna od wersji .NET Core 3.1.201 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-505">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="67bfe-506">kątowy, reagowanie</span><span class="sxs-lookup"><span data-stu-id="67bfe-506">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="67bfe-507">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="67bfe-507">The type of authentication to use.</span></span> <span data-ttu-id="67bfe-508">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-508">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="67bfe-509">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="67bfe-509">The possible values are:</span></span>

  - <span data-ttu-id="67bfe-510">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="67bfe-510">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="67bfe-511">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="67bfe-511">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="67bfe-512">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-512">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-513">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-513">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="67bfe-514">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="67bfe-514">Turns off HTTPS.</span></span> <span data-ttu-id="67bfe-515">Ta opcja ma zastosowanie tylko wtedy, `None`gdy uwierzytelnianie jest.</span><span class="sxs-lookup"><span data-stu-id="67bfe-515">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="67bfe-516">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="67bfe-516">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="67bfe-517">Dotyczy `Individual` tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-517">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="67bfe-518">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-518">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-519">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-519">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-520">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="67bfe-520">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="67bfe-521">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="67bfe-521">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="67bfe-522">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="67bfe-522">SDK version</span></span> | <span data-ttu-id="67bfe-523">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="67bfe-523">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="67bfe-524">3.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-524">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="67bfe-525">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-525">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="67bfe-526">2.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-526">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="67bfe-527">reactredux</span><span class="sxs-lookup"><span data-stu-id="67bfe-527">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="67bfe-528">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-528">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-529">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-529">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-530">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="67bfe-530">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="67bfe-531">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="67bfe-531">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="67bfe-532">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="67bfe-532">SDK version</span></span> | <span data-ttu-id="67bfe-533">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="67bfe-533">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="67bfe-534">3.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="67bfe-535">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-535">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="67bfe-536">2.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-536">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="67bfe-537">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-537">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="67bfe-538">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="67bfe-538">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="67bfe-539">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="67bfe-539">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="67bfe-540">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-540">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="67bfe-541">Obsługuje dodawanie tradycyjnych stron Razor i widoków oprócz składników do tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="67bfe-541">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="67bfe-542">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="67bfe-542">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="67bfe-543">WebApi</span><span class="sxs-lookup"><span data-stu-id="67bfe-543">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="67bfe-544">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="67bfe-544">The type of authentication to use.</span></span> <span data-ttu-id="67bfe-545">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="67bfe-545">The possible values are:</span></span>

  - <span data-ttu-id="67bfe-546">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="67bfe-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="67bfe-547">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="67bfe-547">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="67bfe-548">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="67bfe-548">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="67bfe-549">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="67bfe-549">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="67bfe-550">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-550">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="67bfe-551">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-551">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="67bfe-552">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-552">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="67bfe-553">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-553">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="67bfe-554">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-554">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="67bfe-555">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-555">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="67bfe-556">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-556">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67bfe-557">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-557">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="67bfe-558">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-558">The Client ID for this project.</span></span> <span data-ttu-id="67bfe-559">Używanie z `IndividualB2C` usługą `SingleOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-559">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="67bfe-560">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-560">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="67bfe-561">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-561">The domain for the directory tenant.</span></span> <span data-ttu-id="67bfe-562">Używanie z `IndividualB2C` usługą `SingleOrg` lub uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-562">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="67bfe-563">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-563">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="67bfe-564">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="67bfe-564">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="67bfe-565">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="67bfe-565">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="67bfe-566">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="67bfe-566">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="67bfe-567">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-567">Allows this application read-access to the directory.</span></span> <span data-ttu-id="67bfe-568">Dotyczy tylko `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-568">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="67bfe-569">Wyklucza plik *profilu launchsettings. JSON* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-569">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="67bfe-570">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="67bfe-570">Turns off HTTPS.</span></span> <span data-ttu-id="67bfe-571">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane `Startup.Configure`do.</span><span class="sxs-lookup"><span data-stu-id="67bfe-571">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="67bfe-572">Ta opcja ma zastosowanie tylko `IndividualB2C` wtedy `SingleOrg` , gdy lub nie są używane do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-572">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="67bfe-573">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="67bfe-573">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="67bfe-574">Dotyczy tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="67bfe-574">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="67bfe-575">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="67bfe-575">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="67bfe-576">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="67bfe-576">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="67bfe-577">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="67bfe-577">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="67bfe-578">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="67bfe-578">SDK version</span></span> | <span data-ttu-id="67bfe-579">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="67bfe-579">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="67bfe-580">3.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-580">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="67bfe-581">3.0</span><span class="sxs-lookup"><span data-stu-id="67bfe-581">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="67bfe-582">2.1</span><span class="sxs-lookup"><span data-stu-id="67bfe-582">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="67bfe-583">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-583">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="67bfe-584">globaljson</span><span class="sxs-lookup"><span data-stu-id="67bfe-584">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="67bfe-585">Określa wersję zestaw .NET Core SDK, która ma być używana w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="67bfe-585">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="67bfe-586">Przykłady</span><span class="sxs-lookup"><span data-stu-id="67bfe-586">Examples</span></span>

- <span data-ttu-id="67bfe-587">Utwórz projekt aplikacji konsolowej w języku C#, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="67bfe-587">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="67bfe-588">Utwórz projekt aplikacji konsolowej F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="67bfe-588">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="67bfe-589">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu:</span><span class="sxs-lookup"><span data-stu-id="67bfe-589">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="67bfe-590">Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="67bfe-590">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="67bfe-591">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="67bfe-591">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="67bfe-592">Wyświetl listę wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):</span><span class="sxs-lookup"><span data-stu-id="67bfe-592">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="67bfe-593">Wyświetl listę wszystkich szablonów pasujących *do* podciągu.</span><span class="sxs-lookup"><span data-stu-id="67bfe-593">List all templates matching the *we* substring.</span></span> <span data-ttu-id="67bfe-594">Nie znaleziono dokładnego dopasowania, więc Dopasowywanie podciągów działa w odniesieniu do kolumn krótkich nazw i nazw.</span><span class="sxs-lookup"><span data-stu-id="67bfe-594">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="67bfe-595">Podjęto próbę wywołania szablonu zgodnego z parametrem *ng*.</span><span class="sxs-lookup"><span data-stu-id="67bfe-595">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="67bfe-596">Jeśli nie można ustalić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są dopasowań częściowych.</span><span class="sxs-lookup"><span data-stu-id="67bfe-596">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="67bfe-597">Zainstaluj wersję 2,0 szablonów SPA dla ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="67bfe-597">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="67bfe-598">Wyświetl listę zainstalowanych szablonów i szczegółowe informacje o nich, w tym sposoby ich odinstalowywania:</span><span class="sxs-lookup"><span data-stu-id="67bfe-598">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="67bfe-599">Utwórz plik *Global. JSON* w bieżącym katalogu, ustawiając wersję zestawu SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="67bfe-599">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="67bfe-600">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67bfe-600">See also</span></span>

- [<span data-ttu-id="67bfe-601">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="67bfe-601">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="67bfe-602">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="67bfe-602">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="67bfe-603">dotnet/dotnet-Template-przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="67bfe-603">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="67bfe-604">Dostępne szablony dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="67bfe-604">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
