---
title: polecenie dotnet New
description: Polecenie dotnet New umożliwia tworzenie nowych projektów platformy .NET Core na podstawie określonego szablonu.
no-loc:
- Blazor
- WebAssembly
ms.date: 04/10/2020
ms.openlocfilehash: ec41b3b79ed5eded7c9124d3e4d95c658ee39580
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173123"
---
# <a name="dotnet-new"></a><span data-ttu-id="6663f-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6663f-103">dotnet new</span></span>

<span data-ttu-id="6663f-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="6663f-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6663f-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6663f-105">Name</span></span>

<span data-ttu-id="6663f-106">`dotnet new`-Tworzy nowy projekt, plik konfiguracji lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6663f-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="6663f-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="6663f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6663f-108">Description</span></span>

<span data-ttu-id="6663f-109">`dotnet new`Polecenie tworzy projekt .NET Core lub inne artefakty na podstawie szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="6663f-110">Polecenie wywołuje [aparat szablonu](https://github.com/dotnet/templating) , aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="6663f-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="6663f-111">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="6663f-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="6663f-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6663f-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="6663f-113">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6663f-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="6663f-114">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="6663f-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="6663f-115">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="6663f-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="6663f-116">Można uruchomić `dotnet new --list` lub `dotnet new -l` wyświetlić listę wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="6663f-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="6663f-117">Jeśli `TEMPLATE` wartość nie jest dokładnym dopasowaniem do tekstu w kolumnie **Szablony** lub **krótka nazwa** z zwróconej tabeli, do tych dwóch kolumn jest wykonywane dopasowanie podciągu.</span><span class="sxs-lookup"><span data-stu-id="6663f-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="6663f-118">Począwszy od zestawu SDK platformy .NET Core 3,0, interfejs wiersza polecenia wyszukuje szablony w NuGet.org, gdy wywoła `dotnet new` polecenie w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="6663f-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="6663f-119">Jeśli interfejs wiersza polecenia nie może znaleźć dopasowania szablonu podczas wywoływania `dotnet new` , nie nawet częściowej.</span><span class="sxs-lookup"><span data-stu-id="6663f-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="6663f-120">Jeśli jest dostępna nowsza wersja szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="6663f-121">W takim przypadku projekt lub artefakt jest tworzony, ale interfejs wiersza polecenia ostrzega użytkownika o zaktualizowanej wersji szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="6663f-122">W poniższej tabeli przedstawiono szablony, które są wstępnie zainstalowane wraz z zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="6663f-123">Język domyślny dla szablonu jest pokazywany w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="6663f-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="6663f-124">Kliknij link krótkiej nazwy, aby wyświetlić opcje konkretnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="6663f-125">Szablony</span><span class="sxs-lookup"><span data-stu-id="6663f-125">Templates</span></span>                                    | <span data-ttu-id="6663f-126">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="6663f-126">Short name</span></span>                      | <span data-ttu-id="6663f-127">Language</span><span class="sxs-lookup"><span data-stu-id="6663f-127">Language</span></span>     | <span data-ttu-id="6663f-128">Tagi</span><span class="sxs-lookup"><span data-stu-id="6663f-128">Tags</span></span>                                  | <span data-ttu-id="6663f-129">Wraca</span><span class="sxs-lookup"><span data-stu-id="6663f-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="6663f-130">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="6663f-130">Console Application</span></span>                          | [<span data-ttu-id="6663f-131">konsoli</span><span class="sxs-lookup"><span data-stu-id="6663f-131">console</span></span>](#console)             | <span data-ttu-id="6663f-132">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6663f-132">[C#], F#, VB</span></span> | <span data-ttu-id="6663f-133">Wspólna/konsola</span><span class="sxs-lookup"><span data-stu-id="6663f-133">Common/Console</span></span>                        | <span data-ttu-id="6663f-134">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-134">1.0</span></span>        |
| <span data-ttu-id="6663f-135">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="6663f-135">Class library</span></span>                                | [<span data-ttu-id="6663f-136">określono</span><span class="sxs-lookup"><span data-stu-id="6663f-136">classlib</span></span>](#classlib)           | <span data-ttu-id="6663f-137">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6663f-137">[C#], F#, VB</span></span> | <span data-ttu-id="6663f-138">Wspólna/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="6663f-138">Common/Library</span></span>                        | <span data-ttu-id="6663f-139">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-139">1.0</span></span>        |
| <span data-ttu-id="6663f-140">Aplikacja WPF</span><span class="sxs-lookup"><span data-stu-id="6663f-140">WPF Application</span></span>                              | [<span data-ttu-id="6663f-141">kodow</span><span class="sxs-lookup"><span data-stu-id="6663f-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="6663f-142">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-142">[C#]</span></span>         | <span data-ttu-id="6663f-143">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="6663f-143">Common/WPF</span></span>                            | <span data-ttu-id="6663f-144">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-144">3.0</span></span>        |
| <span data-ttu-id="6663f-145">Biblioteka klas WPF</span><span class="sxs-lookup"><span data-stu-id="6663f-145">WPF Class library</span></span>                            | [<span data-ttu-id="6663f-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="6663f-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="6663f-147">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-147">[C#]</span></span>         | <span data-ttu-id="6663f-148">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="6663f-148">Common/WPF</span></span>                            | <span data-ttu-id="6663f-149">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-149">3.0</span></span>        |
| <span data-ttu-id="6663f-150">Biblioteka kontrolek niestandardowych WPF</span><span class="sxs-lookup"><span data-stu-id="6663f-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="6663f-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="6663f-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="6663f-152">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-152">[C#]</span></span>         | <span data-ttu-id="6663f-153">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="6663f-153">Common/WPF</span></span>                            | <span data-ttu-id="6663f-154">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-154">3.0</span></span>        |
| <span data-ttu-id="6663f-155">Biblioteka kontrolek użytkownika WPF</span><span class="sxs-lookup"><span data-stu-id="6663f-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="6663f-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="6663f-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="6663f-157">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-157">[C#]</span></span>         | <span data-ttu-id="6663f-158">Common/WPF</span><span class="sxs-lookup"><span data-stu-id="6663f-158">Common/WPF</span></span>                            | <span data-ttu-id="6663f-159">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-159">3.0</span></span>        |
| <span data-ttu-id="6663f-160">Aplikacja Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="6663f-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="6663f-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="6663f-161">winforms</span></span>](#winforms)           | <span data-ttu-id="6663f-162">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-162">[C#]</span></span>         | <span data-ttu-id="6663f-163">Typowe/WinForms</span><span class="sxs-lookup"><span data-stu-id="6663f-163">Common/WinForms</span></span>                       | <span data-ttu-id="6663f-164">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-164">3.0</span></span>        |
| <span data-ttu-id="6663f-165">Biblioteka klas Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="6663f-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="6663f-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="6663f-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="6663f-167">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-167">[C#]</span></span>         | <span data-ttu-id="6663f-168">Typowe/WinForms</span><span class="sxs-lookup"><span data-stu-id="6663f-168">Common/WinForms</span></span>                       | <span data-ttu-id="6663f-169">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-169">3.0</span></span>        |
| <span data-ttu-id="6663f-170">Usługa procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="6663f-170">Worker Service</span></span>                               | [<span data-ttu-id="6663f-171">odpowiedzialn</span><span class="sxs-lookup"><span data-stu-id="6663f-171">worker</span></span>](#web-others)           | <span data-ttu-id="6663f-172">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-172">[C#]</span></span>         | <span data-ttu-id="6663f-173">Common/Worker/sieć Web</span><span class="sxs-lookup"><span data-stu-id="6663f-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="6663f-174">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-174">3.0</span></span>        |
| <span data-ttu-id="6663f-175">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="6663f-175">Unit Test Project</span></span>                            | [<span data-ttu-id="6663f-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="6663f-176">mstest</span></span>](#test)                 | <span data-ttu-id="6663f-177">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6663f-177">[C#], F#, VB</span></span> | <span data-ttu-id="6663f-178">Test/MSTest</span><span class="sxs-lookup"><span data-stu-id="6663f-178">Test/MSTest</span></span>                           | <span data-ttu-id="6663f-179">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-179">1.0</span></span>        |
| <span data-ttu-id="6663f-180">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="6663f-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="6663f-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="6663f-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="6663f-182">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6663f-182">[C#], F#, VB</span></span> | <span data-ttu-id="6663f-183">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="6663f-183">Test/NUnit</span></span>                            | <span data-ttu-id="6663f-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="6663f-184">2.1.400</span></span>    |
| <span data-ttu-id="6663f-185">Element testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="6663f-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="6663f-186">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6663f-186">[C#], F#, VB</span></span> | <span data-ttu-id="6663f-187">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="6663f-187">Test/NUnit</span></span>                            | <span data-ttu-id="6663f-188">2.2</span><span class="sxs-lookup"><span data-stu-id="6663f-188">2.2</span></span>        |
| <span data-ttu-id="6663f-189">Projekt testu xUnit</span><span class="sxs-lookup"><span data-stu-id="6663f-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="6663f-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="6663f-190">xunit</span></span>](#test)                  | <span data-ttu-id="6663f-191">[C#], F #, VB</span><span class="sxs-lookup"><span data-stu-id="6663f-191">[C#], F#, VB</span></span> | <span data-ttu-id="6663f-192">Test/xUnit</span><span class="sxs-lookup"><span data-stu-id="6663f-192">Test/xUnit</span></span>                            | <span data-ttu-id="6663f-193">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-193">1.0</span></span>        |
| <span data-ttu-id="6663f-194">Składnik Razor</span><span class="sxs-lookup"><span data-stu-id="6663f-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="6663f-195">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-195">[C#]</span></span>         | <span data-ttu-id="6663f-196">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="6663f-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="6663f-197">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-197">3.0</span></span>        |
| <span data-ttu-id="6663f-198">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="6663f-198">Razor Page</span></span>                                   | [<span data-ttu-id="6663f-199">stronic</span><span class="sxs-lookup"><span data-stu-id="6663f-199">page</span></span>](#page)                   | <span data-ttu-id="6663f-200">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-200">[C#]</span></span>         | <span data-ttu-id="6663f-201">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="6663f-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="6663f-202">2.0</span><span class="sxs-lookup"><span data-stu-id="6663f-202">2.0</span></span>        |
| <span data-ttu-id="6663f-203">ViewImports MVC</span><span class="sxs-lookup"><span data-stu-id="6663f-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="6663f-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="6663f-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="6663f-205">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-205">[C#]</span></span>         | <span data-ttu-id="6663f-206">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="6663f-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="6663f-207">2.0</span><span class="sxs-lookup"><span data-stu-id="6663f-207">2.0</span></span>        |
| <span data-ttu-id="6663f-208">ViewStart MVC</span><span class="sxs-lookup"><span data-stu-id="6663f-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="6663f-209">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-209">[C#]</span></span>         | <span data-ttu-id="6663f-210">Web/ASP. NET</span><span class="sxs-lookup"><span data-stu-id="6663f-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="6663f-211">2.0</span><span class="sxs-lookup"><span data-stu-id="6663f-211">2.0</span></span>        |
| Blazor<span data-ttu-id="6663f-212">Aplikacja serwera</span><span class="sxs-lookup"><span data-stu-id="6663f-212"> Server App</span></span>                            | [<span data-ttu-id="6663f-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="6663f-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="6663f-214">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-214">[C#]</span></span>         | <span data-ttu-id="6663f-215">WitrynęBlazor</span><span class="sxs-lookup"><span data-stu-id="6663f-215">Web/Blazor</span></span>                            | <span data-ttu-id="6663f-216">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-216">3.0</span></span>        |
| Blazor<span data-ttu-id="6663f-217">WebAssemblyAplikacja</span><span class="sxs-lookup"><span data-stu-id="6663f-217"> WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="6663f-218">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-218">[C#]</span></span>         | <span data-ttu-id="6663f-219">WitrynęBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="6663f-219">Web/Blazor/WebAssembly</span></span>                            | <span data-ttu-id="6663f-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="6663f-220">3.1.300</span></span>    |
| <span data-ttu-id="6663f-221">ASP.NET Core puste</span><span class="sxs-lookup"><span data-stu-id="6663f-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="6663f-222">witrynę</span><span class="sxs-lookup"><span data-stu-id="6663f-222">web</span></span>](#web)                     | <span data-ttu-id="6663f-223">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6663f-223">[C#], F#</span></span>     | <span data-ttu-id="6663f-224">Sieć Web/pusta</span><span class="sxs-lookup"><span data-stu-id="6663f-224">Web/Empty</span></span>                             | <span data-ttu-id="6663f-225">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-225">1.0</span></span>        |
| <span data-ttu-id="6663f-226">Aplikacja sieci Web ASP.NET Core (Model-View-Controller)</span><span class="sxs-lookup"><span data-stu-id="6663f-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="6663f-227">Standard</span><span class="sxs-lookup"><span data-stu-id="6663f-227">mvc</span></span>](#web-options)             | <span data-ttu-id="6663f-228">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6663f-228">[C#], F#</span></span>     | <span data-ttu-id="6663f-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6663f-229">Web/MVC</span></span>                               | <span data-ttu-id="6663f-230">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-230">1.0</span></span>        |
| <span data-ttu-id="6663f-231">Aplikacja sieci Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6663f-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="6663f-232">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="6663f-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="6663f-233">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-233">[C#]</span></span>         | <span data-ttu-id="6663f-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="6663f-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="6663f-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="6663f-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="6663f-236">ASP.NET Core ze Skośnością</span><span class="sxs-lookup"><span data-stu-id="6663f-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="6663f-237">kątow</span><span class="sxs-lookup"><span data-stu-id="6663f-237">angular</span></span>](#spa)                 | <span data-ttu-id="6663f-238">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-238">[C#]</span></span>         | <span data-ttu-id="6663f-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6663f-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="6663f-240">2.0</span><span class="sxs-lookup"><span data-stu-id="6663f-240">2.0</span></span>        |
| <span data-ttu-id="6663f-241">ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="6663f-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="6663f-242">biern</span><span class="sxs-lookup"><span data-stu-id="6663f-242">react</span></span>](#spa)                   | <span data-ttu-id="6663f-243">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-243">[C#]</span></span>         | <span data-ttu-id="6663f-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6663f-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="6663f-245">2.0</span><span class="sxs-lookup"><span data-stu-id="6663f-245">2.0</span></span>        |
| <span data-ttu-id="6663f-246">ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="6663f-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="6663f-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="6663f-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="6663f-248">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-248">[C#]</span></span>         | <span data-ttu-id="6663f-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6663f-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="6663f-250">2.0</span><span class="sxs-lookup"><span data-stu-id="6663f-250">2.0</span></span>        |
| <span data-ttu-id="6663f-251">Biblioteka klas Razor</span><span class="sxs-lookup"><span data-stu-id="6663f-251">Razor Class Library</span></span>                          | [<span data-ttu-id="6663f-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="6663f-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="6663f-253">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-253">[C#]</span></span>         | <span data-ttu-id="6663f-254">Biblioteka klas sieci Web/Razor/Biblioteka/Razor</span><span class="sxs-lookup"><span data-stu-id="6663f-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="6663f-255">2.1</span><span class="sxs-lookup"><span data-stu-id="6663f-255">2.1</span></span>        |
| <span data-ttu-id="6663f-256">Internetowy interfejs API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6663f-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="6663f-257">WebApi</span><span class="sxs-lookup"><span data-stu-id="6663f-257">webapi</span></span>](#webapi)               | <span data-ttu-id="6663f-258">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6663f-258">[C#], F#</span></span>     | <span data-ttu-id="6663f-259">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="6663f-259">Web/WebAPI</span></span>                            | <span data-ttu-id="6663f-260">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-260">1.0</span></span>        |
| <span data-ttu-id="6663f-261">ASP.NET Core usługi gRPC</span><span class="sxs-lookup"><span data-stu-id="6663f-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="6663f-262">grpc</span><span class="sxs-lookup"><span data-stu-id="6663f-262">grpc</span></span>](#web-others)             | <span data-ttu-id="6663f-263">Znajd</span><span class="sxs-lookup"><span data-stu-id="6663f-263">[C#]</span></span>         | <span data-ttu-id="6663f-264">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="6663f-264">Web/gRPC</span></span>                              | <span data-ttu-id="6663f-265">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-265">3.0</span></span>        |
| <span data-ttu-id="6663f-266">plik GITIGNORE dotnet</span><span class="sxs-lookup"><span data-stu-id="6663f-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="6663f-267">Config</span><span class="sxs-lookup"><span data-stu-id="6663f-267">Config</span></span>                                | <span data-ttu-id="6663f-268">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-268">3.0</span></span>        |
| <span data-ttu-id="6663f-269">global.jspliku</span><span class="sxs-lookup"><span data-stu-id="6663f-269">global.json file</span></span>                             | [<span data-ttu-id="6663f-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="6663f-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="6663f-271">Config</span><span class="sxs-lookup"><span data-stu-id="6663f-271">Config</span></span>                                | <span data-ttu-id="6663f-272">2.0</span><span class="sxs-lookup"><span data-stu-id="6663f-272">2.0</span></span>        |
| <span data-ttu-id="6663f-273">Konfiguracja narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="6663f-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="6663f-274">Config</span><span class="sxs-lookup"><span data-stu-id="6663f-274">Config</span></span>                                | <span data-ttu-id="6663f-275">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-275">1.0</span></span>        |
| <span data-ttu-id="6663f-276">Plik manifestu narzędzia lokalnego dotnet</span><span class="sxs-lookup"><span data-stu-id="6663f-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="6663f-277">Config</span><span class="sxs-lookup"><span data-stu-id="6663f-277">Config</span></span>                                | <span data-ttu-id="6663f-278">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-278">3.0</span></span>        |
| <span data-ttu-id="6663f-279">Konfiguracja sieci Web</span><span class="sxs-lookup"><span data-stu-id="6663f-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="6663f-280">Config</span><span class="sxs-lookup"><span data-stu-id="6663f-280">Config</span></span>                                | <span data-ttu-id="6663f-281">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-281">1.0</span></span>        |
| <span data-ttu-id="6663f-282">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6663f-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="6663f-283">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="6663f-283">Solution</span></span>                              | <span data-ttu-id="6663f-284">1.0</span><span class="sxs-lookup"><span data-stu-id="6663f-284">1.0</span></span>        |
| <span data-ttu-id="6663f-285">Plik buforu protokołu</span><span class="sxs-lookup"><span data-stu-id="6663f-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="6663f-286">proto</span><span class="sxs-lookup"><span data-stu-id="6663f-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="6663f-287">Sieć Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="6663f-287">Web/gRPC</span></span>                              | <span data-ttu-id="6663f-288">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="6663f-289">Opcje</span><span class="sxs-lookup"><span data-stu-id="6663f-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="6663f-290">Wyświetla podsumowanie tego, co się stanie w przypadku uruchomienia danego polecenia, jeśli mogłoby to spowodować utworzenie szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="6663f-291">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="6663f-292">Wymusza wygenerowanie zawartości nawet w przypadku zmiany istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="6663f-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6663f-293">Jest to wymagane, gdy wybrany szablon spowoduje zastąpienie istniejących plików w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="6663f-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6663f-294">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="6663f-294">Prints out help for the command.</span></span> <span data-ttu-id="6663f-295">Może być wywoływana dla `dotnet new` samego polecenia lub dla dowolnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="6663f-296">Na przykład `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6663f-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="6663f-297">Instaluje pakiet szablonów z `PATH` lub `NUGET_ID` dostarczone.</span><span class="sxs-lookup"><span data-stu-id="6663f-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6663f-298">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w formacie `<package-name>::<package-version>` .</span><span class="sxs-lookup"><span data-stu-id="6663f-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6663f-299">Domyślnie program `dotnet new` przekazuje \* wersję, która reprezentuje najnowszą stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="6663f-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="6663f-300">Zobacz przykład w sekcji [przykładów](#examples) .</span><span class="sxs-lookup"><span data-stu-id="6663f-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="6663f-301">Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej wersji stabilnej, jeśli nie określono żadnej wersji.</span><span class="sxs-lookup"><span data-stu-id="6663f-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="6663f-302">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla usługi dotnet New](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6663f-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="6663f-303">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="6663f-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="6663f-304">Jeśli nazwa nie zostanie określona, program wyświetli listę wszystkich szablonów.</span><span class="sxs-lookup"><span data-stu-id="6663f-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="6663f-305">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="6663f-305">The language of the template to create.</span></span> <span data-ttu-id="6663f-306">Zaakceptowany język zależy od szablonu (zobacz wartości domyślne w sekcji [argumenty](#arguments) ).</span><span class="sxs-lookup"><span data-stu-id="6663f-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6663f-307">Nieprawidłowy dla niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="6663f-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6663f-308">Niektóre powłoki interpretują `#` jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="6663f-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6663f-309">W takich przypadkach należy ująć wartość parametru Language w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="6663f-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="6663f-310">Na przykład `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6663f-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="6663f-311">Nazwa dla utworzonych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="6663f-311">The name for the created output.</span></span> <span data-ttu-id="6663f-312">Jeśli nazwa nie zostanie określona, zostanie użyta nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="6663f-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="6663f-313">Określa źródło NuGet do użycia podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="6663f-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="6663f-314">Dostępne od wersji .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="6663f-315">Lokalizacja, w której mają zostać umieszczone wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6663f-315">Location to place the generated output.</span></span> <span data-ttu-id="6663f-316">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="6663f-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="6663f-317">Filtruje szablony w oparciu o dostępne typy.</span><span class="sxs-lookup"><span data-stu-id="6663f-317">Filters templates based on available types.</span></span> <span data-ttu-id="6663f-318">Wstępnie zdefiniowane wartości to `project` , `item` , i `other` .</span><span class="sxs-lookup"><span data-stu-id="6663f-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="6663f-319">Odinstalowuje pakiet szablonów w `PATH` lub `NUGET_ID` udostępniony.</span><span class="sxs-lookup"><span data-stu-id="6663f-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6663f-320">Gdy `<PATH|NUGET_ID>` wartość nie jest określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="6663f-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="6663f-321">Podczas określania `NUGET_ID` nie należy umieszczać numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="6663f-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="6663f-322">Jeśli nie określisz parametru do tej opcji, polecenie wyświetli listę zainstalowanych szablonów i szczegółowe informacje o nich.</span><span class="sxs-lookup"><span data-stu-id="6663f-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6663f-323">Aby odinstalować szablon przy użyciu programu `PATH` , należy w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="6663f-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6663f-324">Na przykład *C:/Users/ \<USER> /Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działał, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie.</span><span class="sxs-lookup"><span data-stu-id="6663f-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="6663f-325">Nie dołączaj ostatecznego ukośnika katalogu w ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="6663f-326">Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane i instaluje je.</span><span class="sxs-lookup"><span data-stu-id="6663f-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="6663f-327">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="6663f-328">Sprawdza, czy są dostępne aktualizacje pakietów szablonów, które są obecnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="6663f-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="6663f-329">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="6663f-330">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="6663f-330">Template options</span></span>

<span data-ttu-id="6663f-331">Każdy szablon projektu może mieć dodatkowe opcje dostępne.</span><span class="sxs-lookup"><span data-stu-id="6663f-331">Each project template may have additional options available.</span></span> <span data-ttu-id="6663f-332">Szablony podstawowe mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="6663f-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="6663f-333">console</span><span class="sxs-lookup"><span data-stu-id="6663f-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-334">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-335">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="6663f-336">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6663f-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6663f-337">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6663f-337">SDK version</span></span> | <span data-ttu-id="6663f-338">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6663f-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6663f-339">3,1</span><span class="sxs-lookup"><span data-stu-id="6663f-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6663f-340">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="6663f-341">Ustawia `LangVersion` Właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6663f-342">Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="6663f-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="6663f-343">Nieobsługiwane dla języka F #.</span><span class="sxs-lookup"><span data-stu-id="6663f-343">Not supported for F#.</span></span> <span data-ttu-id="6663f-344">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6663f-345">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="6663f-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-346">Jeśli określony, nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="6663f-347">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="6663f-348">określono</span><span class="sxs-lookup"><span data-stu-id="6663f-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-349">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-350">Wartości: `netcoreapp<version>` Aby utworzyć bibliotekę klas platformy .NET Core lub `netstandard<version>` utworzyć bibliotekę klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6663f-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6663f-351">Wartość domyślna to `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6663f-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="6663f-352">Ustawia `LangVersion` Właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6663f-353">Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="6663f-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="6663f-354">Nieobsługiwane dla języka F #.</span><span class="sxs-lookup"><span data-stu-id="6663f-354">Not supported for F#.</span></span> <span data-ttu-id="6663f-355">Dostępne od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6663f-356">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="6663f-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-357">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="6663f-358">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="6663f-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-359">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-360">Wartość domyślna to `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="6663f-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="6663f-361">Dostępne od wersji .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="6663f-362">Ustawia `LangVersion` Właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6663f-363">Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="6663f-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="6663f-364">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="6663f-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-365">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="6663f-366">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="6663f-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="6663f-367">Ustawia `LangVersion` Właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6663f-368">Na przykład użyj, `--langVersion 7.3` Aby użyć języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="6663f-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="6663f-369">Listę domyślnych wersji języka C# można znaleźć w temacie [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="6663f-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-370">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="6663f-371">proces roboczy, GRPC</span><span class="sxs-lookup"><span data-stu-id="6663f-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-372">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-373">Wartość domyślna to `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="6663f-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="6663f-374">Dostępne od wersji .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6663f-375">Wyklucza *launchSettings.js* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-376">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="6663f-377">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="6663f-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-378">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-379">Opcja dostępna od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="6663f-380">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6663f-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6663f-381">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6663f-381">SDK version</span></span> | <span data-ttu-id="6663f-382">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6663f-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6663f-383">3,1</span><span class="sxs-lookup"><span data-stu-id="6663f-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6663f-384">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="6663f-385">Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6663f-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-386">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="6663f-387">NUnit</span><span class="sxs-lookup"><span data-stu-id="6663f-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-388">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="6663f-389">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6663f-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6663f-390">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6663f-390">SDK version</span></span> | <span data-ttu-id="6663f-391">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6663f-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6663f-392">3,1</span><span class="sxs-lookup"><span data-stu-id="6663f-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6663f-393">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6663f-394">2.2</span><span class="sxs-lookup"><span data-stu-id="6663f-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="6663f-395">2.1</span><span class="sxs-lookup"><span data-stu-id="6663f-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="6663f-396">Włącza pakowanie dla projektu przy użyciu [pakietu dotnet Pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6663f-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-397">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="6663f-398">stronic</span><span class="sxs-lookup"><span data-stu-id="6663f-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="6663f-399">Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6663f-399">Namespace for the generated code.</span></span> <span data-ttu-id="6663f-400">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6663f-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="6663f-401">Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="6663f-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="6663f-402">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="6663f-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="6663f-403">Przestrzeń nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6663f-403">Namespace for the generated code.</span></span> <span data-ttu-id="6663f-404">Wartość domyślna to `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6663f-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="6663f-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="6663f-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="6663f-406">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="6663f-406">The type of authentication to use.</span></span> <span data-ttu-id="6663f-407">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6663f-407">The possible values are:</span></span>

  - <span data-ttu-id="6663f-408">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="6663f-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="6663f-409">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="6663f-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="6663f-410">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6663f-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="6663f-411">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="6663f-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="6663f-412">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="6663f-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="6663f-413">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6663f-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="6663f-414">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="6663f-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6663f-415">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6663f-416">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6663f-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="6663f-417">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6663f-418">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="6663f-419">Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="6663f-420">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="6663f-421">Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="6663f-422">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="6663f-423">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="6663f-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6663f-424">Używanie z usługą `SingleOrg` lub `MultiOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6663f-425">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6663f-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="6663f-426">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-426">The Client ID for this project.</span></span> <span data-ttu-id="6663f-427">Użyj z `IndividualB2C` , `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6663f-428">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6663f-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="6663f-429">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="6663f-429">The domain for the directory tenant.</span></span> <span data-ttu-id="6663f-430">Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6663f-431">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6663f-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="6663f-432">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="6663f-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6663f-433">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6663f-434">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6663f-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="6663f-435">Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="6663f-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6663f-436">Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6663f-437">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6663f-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="6663f-438">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="6663f-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="6663f-439">Dotyczy tylko `SingleOrg` `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6663f-440">Wyklucza *launchSettings.js* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="6663f-441">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6663f-441">Turns off HTTPS.</span></span> <span data-ttu-id="6663f-442">Ta opcja ma zastosowanie tylko wtedy, gdy,, `Individual` `IndividualB2C` `SingleOrg` lub `MultiOrg` nie są używane w programie `--auth` .</span><span class="sxs-lookup"><span data-stu-id="6663f-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="6663f-443">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="6663f-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6663f-444">Dotyczy tylko `Individual` `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-445">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="6663f-446">web</span><span class="sxs-lookup"><span data-stu-id="6663f-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6663f-447">Wyklucza *launchSettings.js* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-448">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-449">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="6663f-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6663f-450">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6663f-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6663f-451">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6663f-451">SDK version</span></span> | <span data-ttu-id="6663f-452">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6663f-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6663f-453">3,1</span><span class="sxs-lookup"><span data-stu-id="6663f-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6663f-454">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6663f-455">2.1</span><span class="sxs-lookup"><span data-stu-id="6663f-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="6663f-456">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="6663f-457">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6663f-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="6663f-458">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="6663f-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="6663f-459">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="6663f-459">The type of authentication to use.</span></span> <span data-ttu-id="6663f-460">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6663f-460">The possible values are:</span></span>

  - <span data-ttu-id="6663f-461">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="6663f-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="6663f-462">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="6663f-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="6663f-463">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6663f-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="6663f-464">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="6663f-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="6663f-465">`MultiOrg`-Organizacja uwierzytelnianie dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="6663f-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="6663f-466">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6663f-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="6663f-467">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="6663f-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6663f-468">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6663f-469">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6663f-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="6663f-470">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6663f-471">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="6663f-472">Identyfikator zasad resetowania hasła dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="6663f-473">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="6663f-474">Edytuj identyfikator zasad profilu dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="6663f-475">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="6663f-476">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="6663f-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6663f-477">Używanie z usługą `SingleOrg` lub `MultiOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6663f-478">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6663f-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="6663f-479">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-479">The Client ID for this project.</span></span> <span data-ttu-id="6663f-480">Użyj z `IndividualB2C` , `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6663f-481">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6663f-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="6663f-482">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="6663f-482">The domain for the directory tenant.</span></span> <span data-ttu-id="6663f-483">Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6663f-484">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6663f-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="6663f-485">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="6663f-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6663f-486">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6663f-487">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6663f-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="6663f-488">Ścieżka żądania w ścieżce podstawowej identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="6663f-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6663f-489">Używanie z usługą `SingleOrg` lub `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6663f-490">Wartość domyślna to `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6663f-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="6663f-491">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="6663f-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="6663f-492">Dotyczy tylko `SingleOrg` `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6663f-493">Wyklucza *launchSettings.js* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="6663f-494">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6663f-494">Turns off HTTPS.</span></span> <span data-ttu-id="6663f-495">Ta opcja ma zastosowanie tylko wtedy, gdy,, `Individual` `IndividualB2C` `SingleOrg` lub `MultiOrg` nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="6663f-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="6663f-496">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="6663f-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6663f-497">Dotyczy tylko `Individual` `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-498">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-499">Opcja dostępna od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="6663f-500">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6663f-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6663f-501">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6663f-501">SDK version</span></span> | <span data-ttu-id="6663f-502">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6663f-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6663f-503">3,1</span><span class="sxs-lookup"><span data-stu-id="6663f-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6663f-504">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="6663f-505">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="6663f-506">Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="6663f-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="6663f-507">Opcja nie jest dostępna w programie .NET Core 2,2 i 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="6663f-508">Określa, czy projekt jest skonfigurowany do używania [kompilacji środowiska uruchomieniowego Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) w kompilacjach debugowania.</span><span class="sxs-lookup"><span data-stu-id="6663f-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="6663f-509">Opcja dostępna od wersji .NET Core 3.1.201 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="6663f-510">kątowy, reagowanie</span><span class="sxs-lookup"><span data-stu-id="6663f-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="6663f-511">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="6663f-511">The type of authentication to use.</span></span> <span data-ttu-id="6663f-512">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="6663f-513">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6663f-513">The possible values are:</span></span>

  - <span data-ttu-id="6663f-514">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="6663f-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="6663f-515">`Individual`-Uwierzytelnianie indywidualne.</span><span class="sxs-lookup"><span data-stu-id="6663f-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6663f-516">Wyklucza *launchSettings.js* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-517">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="6663f-518">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6663f-518">Turns off HTTPS.</span></span> <span data-ttu-id="6663f-519">Ta opcja ma zastosowanie tylko wtedy, gdy uwierzytelnianie jest `None` .</span><span class="sxs-lookup"><span data-stu-id="6663f-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="6663f-520">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="6663f-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6663f-521">Dotyczy tylko `Individual` `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6663f-522">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-523">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-524">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="6663f-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6663f-525">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6663f-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6663f-526">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6663f-526">SDK version</span></span> | <span data-ttu-id="6663f-527">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6663f-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6663f-528">3,1</span><span class="sxs-lookup"><span data-stu-id="6663f-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6663f-529">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6663f-530">2.1</span><span class="sxs-lookup"><span data-stu-id="6663f-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="6663f-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="6663f-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6663f-532">Wyklucza *launchSettings.js* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-533">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-534">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="6663f-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6663f-535">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6663f-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6663f-536">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6663f-536">SDK version</span></span> | <span data-ttu-id="6663f-537">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6663f-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6663f-538">3,1</span><span class="sxs-lookup"><span data-stu-id="6663f-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6663f-539">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6663f-540">2.1</span><span class="sxs-lookup"><span data-stu-id="6663f-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="6663f-541">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="6663f-542">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6663f-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="6663f-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="6663f-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="6663f-544">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="6663f-545">Obsługuje dodawanie tradycyjnych stron Razor i widoków oprócz składników do tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="6663f-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="6663f-546">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6663f-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="6663f-547">WebApi</span><span class="sxs-lookup"><span data-stu-id="6663f-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="6663f-548">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="6663f-548">The type of authentication to use.</span></span> <span data-ttu-id="6663f-549">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6663f-549">The possible values are:</span></span>

  - <span data-ttu-id="6663f-550">`None`-Brak uwierzytelniania (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="6663f-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="6663f-551">`IndividualB2C`-Uwierzytelnianie indywidualne przy użyciu Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6663f-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="6663f-552">`SingleOrg`-Organizacja uwierzytelnianie dla pojedynczej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="6663f-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="6663f-553">`Windows`— Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6663f-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="6663f-554">Wystąpienie Azure Active Directory B2C, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="6663f-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6663f-555">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6663f-556">Wartość domyślna to `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6663f-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="6663f-557">Identyfikator zasad logowania i rejestrowania dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6663f-558">Użyj z `IndividualB2C` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="6663f-559">Wystąpienie Azure Active Directory, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="6663f-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6663f-560">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6663f-561">Wartość domyślna to `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6663f-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="6663f-562">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-562">The Client ID for this project.</span></span> <span data-ttu-id="6663f-563">Używanie z usługą `IndividualB2C` lub `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6663f-564">Wartość domyślna to `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6663f-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="6663f-565">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="6663f-565">The domain for the directory tenant.</span></span> <span data-ttu-id="6663f-566">Używanie z usługą `IndividualB2C` lub `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6663f-567">Wartość domyślna to `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6663f-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="6663f-568">Identyfikator TenantId katalogu, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="6663f-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6663f-569">Użyj z `SingleOrg` uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6663f-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6663f-570">Wartość domyślna to `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6663f-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="6663f-571">Zezwala tej aplikacji na dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="6663f-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="6663f-572">Dotyczy tylko `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6663f-573">Wyklucza *launchSettings.js* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6663f-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="6663f-574">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6663f-574">Turns off HTTPS.</span></span> <span data-ttu-id="6663f-575">`app.UseHsts`i `app.UseHttpsRedirection` nie są dodawane do `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="6663f-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6663f-576">Ta opcja ma zastosowanie tylko wtedy `IndividualB2C` , gdy lub `SingleOrg` nie są używane do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="6663f-577">Należy używać LocalDB zamiast oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="6663f-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6663f-578">Dotyczy tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6663f-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6663f-579">Określa [platformę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6663f-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6663f-580">Opcja nie jest dostępna w zestawie SDK platformy .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="6663f-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6663f-581">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6663f-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6663f-582">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6663f-582">SDK version</span></span> | <span data-ttu-id="6663f-583">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6663f-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6663f-584">3,1</span><span class="sxs-lookup"><span data-stu-id="6663f-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6663f-585">3.0</span><span class="sxs-lookup"><span data-stu-id="6663f-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6663f-586">2.1</span><span class="sxs-lookup"><span data-stu-id="6663f-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="6663f-587">Nie wykonuje przywracania niejawnego podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6663f-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="6663f-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="6663f-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="6663f-589">Określa wersję zestaw .NET Core SDK, która ma być używana w *global.js* pliku.</span><span class="sxs-lookup"><span data-stu-id="6663f-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="6663f-590">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6663f-590">Examples</span></span>

- <span data-ttu-id="6663f-591">Utwórz projekt aplikacji konsolowej w języku C#, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="6663f-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="6663f-592">Utwórz projekt aplikacji konsolowej F # w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="6663f-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="6663f-593">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu:</span><span class="sxs-lookup"><span data-stu-id="6663f-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="6663f-594">Utwórz nowy projekt ASP.NET Core C# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="6663f-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="6663f-595">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="6663f-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="6663f-596">Wyświetl listę wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):</span><span class="sxs-lookup"><span data-stu-id="6663f-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="6663f-597">Wyświetl listę wszystkich szablonów pasujących *do* podciągu.</span><span class="sxs-lookup"><span data-stu-id="6663f-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="6663f-598">Nie znaleziono dokładnego dopasowania, więc Dopasowywanie podciągów działa w odniesieniu do kolumn krótkich nazw i nazw.</span><span class="sxs-lookup"><span data-stu-id="6663f-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="6663f-599">Podjęto próbę wywołania szablonu zgodnego z parametrem *ng*.</span><span class="sxs-lookup"><span data-stu-id="6663f-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="6663f-600">Jeśli nie można ustalić pojedynczego dopasowania, należy wyświetlić listę szablonów, które są dopasowań częściowych.</span><span class="sxs-lookup"><span data-stu-id="6663f-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="6663f-601">Zainstaluj wersję 2,0 szablonów SPA dla ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="6663f-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="6663f-602">Wyświetl listę zainstalowanych szablonów i szczegółowe informacje o nich, w tym sposoby ich odinstalowywania:</span><span class="sxs-lookup"><span data-stu-id="6663f-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="6663f-603">Utwórz *global.js* w bieżącym katalogu, ustawiając wersję zestawu SDK na 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="6663f-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="6663f-604">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6663f-604">See also</span></span>

- [<span data-ttu-id="6663f-605">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="6663f-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="6663f-606">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="6663f-606">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="6663f-607">dotnet/dotnet-Template-przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="6663f-607">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="6663f-608">Dostępne szablony dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="6663f-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
