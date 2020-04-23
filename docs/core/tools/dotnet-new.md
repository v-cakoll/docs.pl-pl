---
title: dotnet nowe polecenie
description: Nowe polecenie dotnet tworzy nowe projekty .NET Core na podstawie określonego szablonu.
ms.date: 04/10/2020
ms.openlocfilehash: 1979f98a6005a414acc64c5eaa086a88aca9f033
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102830"
---
# <a name="dotnet-new"></a><span data-ttu-id="6b2d3-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6b2d3-103">dotnet new</span></span>

<span data-ttu-id="6b2d3-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="6b2d3-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6b2d3-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6b2d3-105">Name</span></span>

<span data-ttu-id="6b2d3-106">`dotnet new`- Tworzy nowy projekt, plik konfiguracyjny lub rozwiązanie na podstawie określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6b2d3-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="6b2d3-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="6b2d3-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6b2d3-108">Description</span></span>

<span data-ttu-id="6b2d3-109">Polecenie `dotnet new` tworzy projekt .NET Core lub inne artefakty oparte na szablonie.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="6b2d3-110">Polecenie wywołuje [aparat szablonów,](https://github.com/dotnet/templating) aby utworzyć artefakty na dysku na podstawie określonego szablonu i opcji.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="6b2d3-111">Niejawne przywracanie</span><span class="sxs-lookup"><span data-stu-id="6b2d3-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="6b2d3-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6b2d3-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="6b2d3-113">Szablon do wystąpienia po wywołaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="6b2d3-114">Każdy szablon może mieć określone opcje, które można przekazać.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="6b2d3-115">Aby uzyskać więcej informacji, zobacz [Opcje szablonu](#template-options).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="6b2d3-116">Można uruchomić, `dotnet new --list` aby wyświetlić listę wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-116">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="6b2d3-117">Jeśli `TEMPLATE` wartość nie jest dokładne dopasowanie tekstu w **szablony** lub **nazwa skrócona** kolumny z tabeli zwracanej, dopasowanie podciąg jest wykonywane na tych dwóch kolumnach.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="6b2d3-118">Począwszy od pliku .NET Core 3.0 SDK, funkcja CLI wyszukuje szablony w NuGet.org podczas wywoływania `dotnet new` polecenia w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="6b2d3-119">Jeśli cli nie można znaleźć dopasowania szablonu podczas wywoływania `dotnet new`, nawet częściowe.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="6b2d3-120">Jeśli dostępna jest nowsza wersja szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="6b2d3-121">W takim przypadku tworzony jest projekt lub artefakt, ale cli ostrzega o zaktualizowanej wersji szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="6b2d3-122">Polecenie zawiera domyślną listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-122">The command contains a default list of templates.</span></span> <span data-ttu-id="6b2d3-123">Służy `dotnet new -l` do uzyskiwania listy dostępnych szablonów.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-123">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6b2d3-124">W poniższej tabeli przedstawiono szablony, które są fabrycznie zainstalowane z pakietem .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-124">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="6b2d3-125">Domyślny język szablonu jest wyświetlany wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-125">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="6b2d3-126">Kliknij łącze do krótkiej nazwy, aby wyświetlić określone opcje szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-126">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="6b2d3-127">Szablony</span><span class="sxs-lookup"><span data-stu-id="6b2d3-127">Templates</span></span>                                    | <span data-ttu-id="6b2d3-128">Krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="6b2d3-128">Short name</span></span>                      | <span data-ttu-id="6b2d3-129">Język</span><span class="sxs-lookup"><span data-stu-id="6b2d3-129">Language</span></span>     | <span data-ttu-id="6b2d3-130">Tagi</span><span class="sxs-lookup"><span data-stu-id="6b2d3-130">Tags</span></span>                                  | <span data-ttu-id="6b2d3-131">Wprowadzone</span><span class="sxs-lookup"><span data-stu-id="6b2d3-131">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="6b2d3-132">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="6b2d3-132">Console Application</span></span>                          | [<span data-ttu-id="6b2d3-133">Konsoli</span><span class="sxs-lookup"><span data-stu-id="6b2d3-133">console</span></span>](#console)             | <span data-ttu-id="6b2d3-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6b2d3-134">[C#], F#, VB</span></span> | <span data-ttu-id="6b2d3-135">Wspólne/konsolowe</span><span class="sxs-lookup"><span data-stu-id="6b2d3-135">Common/Console</span></span>                        | <span data-ttu-id="6b2d3-136">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-136">1.0</span></span>        |
| <span data-ttu-id="6b2d3-137">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="6b2d3-137">Class library</span></span>                                | [<span data-ttu-id="6b2d3-138">Classlib</span><span class="sxs-lookup"><span data-stu-id="6b2d3-138">classlib</span></span>](#classlib)           | <span data-ttu-id="6b2d3-139">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6b2d3-139">[C#], F#, VB</span></span> | <span data-ttu-id="6b2d3-140">Wspólne/Biblioteka</span><span class="sxs-lookup"><span data-stu-id="6b2d3-140">Common/Library</span></span>                        | <span data-ttu-id="6b2d3-141">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-141">1.0</span></span>        |
| <span data-ttu-id="6b2d3-142">Aplikacja WPF</span><span class="sxs-lookup"><span data-stu-id="6b2d3-142">WPF Application</span></span>                              | [<span data-ttu-id="6b2d3-143">Wpf</span><span class="sxs-lookup"><span data-stu-id="6b2d3-143">wpf</span></span>](#wpf)                     | <span data-ttu-id="6b2d3-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-144">[C#]</span></span>         | <span data-ttu-id="6b2d3-145">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="6b2d3-145">Common/WPF</span></span>                            | <span data-ttu-id="6b2d3-146">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-146">3.0</span></span>        |
| <span data-ttu-id="6b2d3-147">Biblioteka klas WPF</span><span class="sxs-lookup"><span data-stu-id="6b2d3-147">WPF Class library</span></span>                            | [<span data-ttu-id="6b2d3-148">wpflib</span><span class="sxs-lookup"><span data-stu-id="6b2d3-148">wpflib</span></span>](#wpf)                  | <span data-ttu-id="6b2d3-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-149">[C#]</span></span>         | <span data-ttu-id="6b2d3-150">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="6b2d3-150">Common/WPF</span></span>                            | <span data-ttu-id="6b2d3-151">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-151">3.0</span></span>        |
| <span data-ttu-id="6b2d3-152">Biblioteka kontrolek niestandardowych WPF</span><span class="sxs-lookup"><span data-stu-id="6b2d3-152">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="6b2d3-153">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="6b2d3-153">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="6b2d3-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-154">[C#]</span></span>         | <span data-ttu-id="6b2d3-155">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="6b2d3-155">Common/WPF</span></span>                            | <span data-ttu-id="6b2d3-156">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-156">3.0</span></span>        |
| <span data-ttu-id="6b2d3-157">Biblioteka kontroli użytkownika WPF</span><span class="sxs-lookup"><span data-stu-id="6b2d3-157">WPF User Control Library</span></span>                     | [<span data-ttu-id="6b2d3-158">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="6b2d3-158">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="6b2d3-159">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-159">[C#]</span></span>         | <span data-ttu-id="6b2d3-160">Często/WPF</span><span class="sxs-lookup"><span data-stu-id="6b2d3-160">Common/WPF</span></span>                            | <span data-ttu-id="6b2d3-161">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-161">3.0</span></span>        |
| <span data-ttu-id="6b2d3-162">Aplikacja Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="6b2d3-162">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="6b2d3-163">Winforms</span><span class="sxs-lookup"><span data-stu-id="6b2d3-163">winforms</span></span>](#winforms)           | <span data-ttu-id="6b2d3-164">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-164">[C#]</span></span>         | <span data-ttu-id="6b2d3-165">Wspólne/WinForms</span><span class="sxs-lookup"><span data-stu-id="6b2d3-165">Common/WinForms</span></span>                       | <span data-ttu-id="6b2d3-166">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-166">3.0</span></span>        |
| <span data-ttu-id="6b2d3-167">Biblioteka klas formularzy Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="6b2d3-167">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="6b2d3-168">winformslib</span><span class="sxs-lookup"><span data-stu-id="6b2d3-168">winformslib</span></span>](#winforms)        | <span data-ttu-id="6b2d3-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-169">[C#]</span></span>         | <span data-ttu-id="6b2d3-170">Wspólne/WinForms</span><span class="sxs-lookup"><span data-stu-id="6b2d3-170">Common/WinForms</span></span>                       | <span data-ttu-id="6b2d3-171">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-171">3.0</span></span>        |
| <span data-ttu-id="6b2d3-172">Usługa dla pracowników</span><span class="sxs-lookup"><span data-stu-id="6b2d3-172">Worker Service</span></span>                               | [<span data-ttu-id="6b2d3-173">Pracownik</span><span class="sxs-lookup"><span data-stu-id="6b2d3-173">worker</span></span>](#web-others)           | <span data-ttu-id="6b2d3-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-174">[C#]</span></span>         | <span data-ttu-id="6b2d3-175">Często/Pracownik/Sieć Web</span><span class="sxs-lookup"><span data-stu-id="6b2d3-175">Common/Worker/Web</span></span>                     | <span data-ttu-id="6b2d3-176">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-176">3.0</span></span>        |
| <span data-ttu-id="6b2d3-177">Projekt testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="6b2d3-177">Unit Test Project</span></span>                            | [<span data-ttu-id="6b2d3-178">Mstest</span><span class="sxs-lookup"><span data-stu-id="6b2d3-178">mstest</span></span>](#test)                 | <span data-ttu-id="6b2d3-179">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6b2d3-179">[C#], F#, VB</span></span> | <span data-ttu-id="6b2d3-180">Test/TEST MSTest</span><span class="sxs-lookup"><span data-stu-id="6b2d3-180">Test/MSTest</span></span>                           | <span data-ttu-id="6b2d3-181">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-181">1.0</span></span>        |
| <span data-ttu-id="6b2d3-182">Projekt testowy NUnit 3</span><span class="sxs-lookup"><span data-stu-id="6b2d3-182">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="6b2d3-183">Nunit</span><span class="sxs-lookup"><span data-stu-id="6b2d3-183">nunit</span></span>](#nunit)                  | <span data-ttu-id="6b2d3-184">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6b2d3-184">[C#], F#, VB</span></span> | <span data-ttu-id="6b2d3-185">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="6b2d3-185">Test/NUnit</span></span>                            | <span data-ttu-id="6b2d3-186">2.1.400</span><span class="sxs-lookup"><span data-stu-id="6b2d3-186">2.1.400</span></span>    |
| <span data-ttu-id="6b2d3-187">NUnit 3 Przedmiot testowy</span><span class="sxs-lookup"><span data-stu-id="6b2d3-187">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="6b2d3-188">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6b2d3-188">[C#], F#, VB</span></span> | <span data-ttu-id="6b2d3-189">Test/NUnit</span><span class="sxs-lookup"><span data-stu-id="6b2d3-189">Test/NUnit</span></span>                            | <span data-ttu-id="6b2d3-190">2.2</span><span class="sxs-lookup"><span data-stu-id="6b2d3-190">2.2</span></span>        |
| <span data-ttu-id="6b2d3-191">xUnit Projekt testowy</span><span class="sxs-lookup"><span data-stu-id="6b2d3-191">xUnit Test Project</span></span>                           | [<span data-ttu-id="6b2d3-192">Xunit</span><span class="sxs-lookup"><span data-stu-id="6b2d3-192">xunit</span></span>](#test)                  | <span data-ttu-id="6b2d3-193">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6b2d3-193">[C#], F#, VB</span></span> | <span data-ttu-id="6b2d3-194">Test/xJednostka</span><span class="sxs-lookup"><span data-stu-id="6b2d3-194">Test/xUnit</span></span>                            | <span data-ttu-id="6b2d3-195">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-195">1.0</span></span>        |
| <span data-ttu-id="6b2d3-196">Komponent maszynki do golenia</span><span class="sxs-lookup"><span data-stu-id="6b2d3-196">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="6b2d3-197">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-197">[C#]</span></span>         | <span data-ttu-id="6b2d3-198">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6b2d3-198">Web/ASP.NET</span></span>                           | <span data-ttu-id="6b2d3-199">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-199">3.0</span></span>        |
| <span data-ttu-id="6b2d3-200">Strona Razor</span><span class="sxs-lookup"><span data-stu-id="6b2d3-200">Razor Page</span></span>                                   | [<span data-ttu-id="6b2d3-201">Strona</span><span class="sxs-lookup"><span data-stu-id="6b2d3-201">page</span></span>](#page)                   | <span data-ttu-id="6b2d3-202">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-202">[C#]</span></span>         | <span data-ttu-id="6b2d3-203">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6b2d3-203">Web/ASP.NET</span></span>                           | <span data-ttu-id="6b2d3-204">2.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-204">2.0</span></span>        |
| <span data-ttu-id="6b2d3-205">Porty widoków MVC</span><span class="sxs-lookup"><span data-stu-id="6b2d3-205">MVC ViewImports</span></span>                              | [<span data-ttu-id="6b2d3-206">viewimports</span><span class="sxs-lookup"><span data-stu-id="6b2d3-206">viewimports</span></span>](#namespace)       | <span data-ttu-id="6b2d3-207">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-207">[C#]</span></span>         | <span data-ttu-id="6b2d3-208">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6b2d3-208">Web/ASP.NET</span></span>                           | <span data-ttu-id="6b2d3-209">2.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-209">2.0</span></span>        |
| <span data-ttu-id="6b2d3-210">Początek widoku MVC</span><span class="sxs-lookup"><span data-stu-id="6b2d3-210">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="6b2d3-211">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-211">[C#]</span></span>         | <span data-ttu-id="6b2d3-212">Sieć Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6b2d3-212">Web/ASP.NET</span></span>                           | <span data-ttu-id="6b2d3-213">2.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-213">2.0</span></span>        |
| <span data-ttu-id="6b2d3-214">Aplikacja serwera Blazor</span><span class="sxs-lookup"><span data-stu-id="6b2d3-214">Blazor Server App</span></span>                            | [<span data-ttu-id="6b2d3-215">blazorserver</span><span class="sxs-lookup"><span data-stu-id="6b2d3-215">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="6b2d3-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-216">[C#]</span></span>         | <span data-ttu-id="6b2d3-217">Sieć Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="6b2d3-217">Web/Blazor</span></span>                            | <span data-ttu-id="6b2d3-218">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-218">3.0</span></span>        |
| <span data-ttu-id="6b2d3-219">ASP.NET rdzeń pusty</span><span class="sxs-lookup"><span data-stu-id="6b2d3-219">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="6b2d3-220">Sieci web</span><span class="sxs-lookup"><span data-stu-id="6b2d3-220">web</span></span>](#web)                     | <span data-ttu-id="6b2d3-221">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6b2d3-221">[C#], F#</span></span>     | <span data-ttu-id="6b2d3-222">Sieć Web/Puste</span><span class="sxs-lookup"><span data-stu-id="6b2d3-222">Web/Empty</span></span>                             | <span data-ttu-id="6b2d3-223">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-223">1.0</span></span>        |
| <span data-ttu-id="6b2d3-224">ASP.NET Core Web App (kontroler widoku modelu)</span><span class="sxs-lookup"><span data-stu-id="6b2d3-224">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="6b2d3-225">Mvc</span><span class="sxs-lookup"><span data-stu-id="6b2d3-225">mvc</span></span>](#web-options)             | <span data-ttu-id="6b2d3-226">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6b2d3-226">[C#], F#</span></span>     | <span data-ttu-id="6b2d3-227">Sieć Web/MVC</span><span class="sxs-lookup"><span data-stu-id="6b2d3-227">Web/MVC</span></span>                               | <span data-ttu-id="6b2d3-228">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-228">1.0</span></span>        |
| <span data-ttu-id="6b2d3-229">ASP.NET podstawowa aplikacja sieci Web</span><span class="sxs-lookup"><span data-stu-id="6b2d3-229">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="6b2d3-230">webapp, brzytwa</span><span class="sxs-lookup"><span data-stu-id="6b2d3-230">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="6b2d3-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-231">[C#]</span></span>         | <span data-ttu-id="6b2d3-232">Strony internetowe/MVC/Brzytwa</span><span class="sxs-lookup"><span data-stu-id="6b2d3-232">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="6b2d3-233">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-233">2.2, 2.0</span></span>   |
| <span data-ttu-id="6b2d3-234">ASP.NET rdzeń z kątowym</span><span class="sxs-lookup"><span data-stu-id="6b2d3-234">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="6b2d3-235">Kątowe</span><span class="sxs-lookup"><span data-stu-id="6b2d3-235">angular</span></span>](#spa)                 | <span data-ttu-id="6b2d3-236">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-236">[C#]</span></span>         | <span data-ttu-id="6b2d3-237">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6b2d3-237">Web/MVC/SPA</span></span>                           | <span data-ttu-id="6b2d3-238">2.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-238">2.0</span></span>        |
| <span data-ttu-id="6b2d3-239">ASP.NET Core z React.js</span><span class="sxs-lookup"><span data-stu-id="6b2d3-239">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="6b2d3-240">Reagować</span><span class="sxs-lookup"><span data-stu-id="6b2d3-240">react</span></span>](#spa)                   | <span data-ttu-id="6b2d3-241">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-241">[C#]</span></span>         | <span data-ttu-id="6b2d3-242">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6b2d3-242">Web/MVC/SPA</span></span>                           | <span data-ttu-id="6b2d3-243">2.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-243">2.0</span></span>        |
| <span data-ttu-id="6b2d3-244">ASP.NET Core z React.js i Redux</span><span class="sxs-lookup"><span data-stu-id="6b2d3-244">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="6b2d3-245">reactredux</span><span class="sxs-lookup"><span data-stu-id="6b2d3-245">reactredux</span></span>](#reactredux)       | <span data-ttu-id="6b2d3-246">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-246">[C#]</span></span>         | <span data-ttu-id="6b2d3-247">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="6b2d3-247">Web/MVC/SPA</span></span>                           | <span data-ttu-id="6b2d3-248">2.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-248">2.0</span></span>        |
| <span data-ttu-id="6b2d3-249">Biblioteka klas razor</span><span class="sxs-lookup"><span data-stu-id="6b2d3-249">Razor Class Library</span></span>                          | [<span data-ttu-id="6b2d3-250">brzytwaklasyb</span><span class="sxs-lookup"><span data-stu-id="6b2d3-250">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="6b2d3-251">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-251">[C#]</span></span>         | <span data-ttu-id="6b2d3-252">Web/ Razor/Biblioteka/Razor Klasa Biblioteka</span><span class="sxs-lookup"><span data-stu-id="6b2d3-252">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="6b2d3-253">2.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-253">2.1</span></span>        |
| <span data-ttu-id="6b2d3-254">Internetowy interfejs API platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b2d3-254">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="6b2d3-255">Webapi</span><span class="sxs-lookup"><span data-stu-id="6b2d3-255">webapi</span></span>](#webapi)               | <span data-ttu-id="6b2d3-256">[C#], F #</span><span class="sxs-lookup"><span data-stu-id="6b2d3-256">[C#], F#</span></span>     | <span data-ttu-id="6b2d3-257">Sieć Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="6b2d3-257">Web/WebAPI</span></span>                            | <span data-ttu-id="6b2d3-258">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-258">1.0</span></span>        |
| <span data-ttu-id="6b2d3-259">ASP.NET podstawowa usługa gRPC</span><span class="sxs-lookup"><span data-stu-id="6b2d3-259">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="6b2d3-260">grpc (grpc)</span><span class="sxs-lookup"><span data-stu-id="6b2d3-260">grpc</span></span>](#web-others)             | <span data-ttu-id="6b2d3-261">[C#]</span><span class="sxs-lookup"><span data-stu-id="6b2d3-261">[C#]</span></span>         | <span data-ttu-id="6b2d3-262">Sieć/gRPC</span><span class="sxs-lookup"><span data-stu-id="6b2d3-262">Web/gRPC</span></span>                              | <span data-ttu-id="6b2d3-263">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-263">3.0</span></span>        |
| <span data-ttu-id="6b2d3-264">Plik buforu protokołu</span><span class="sxs-lookup"><span data-stu-id="6b2d3-264">Protocol Buffer File</span></span>                         | [<span data-ttu-id="6b2d3-265">Proto</span><span class="sxs-lookup"><span data-stu-id="6b2d3-265">proto</span></span>](#namespace)             |              | <span data-ttu-id="6b2d3-266">Sieć/gRPC</span><span class="sxs-lookup"><span data-stu-id="6b2d3-266">Web/gRPC</span></span>                              | <span data-ttu-id="6b2d3-267">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-267">3.0</span></span>        |
| <span data-ttu-id="6b2d3-268">plik dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="6b2d3-268">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="6b2d3-269">Config</span><span class="sxs-lookup"><span data-stu-id="6b2d3-269">Config</span></span>                                | <span data-ttu-id="6b2d3-270">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-270">3.0</span></span>        |
| <span data-ttu-id="6b2d3-271">plik global.json</span><span class="sxs-lookup"><span data-stu-id="6b2d3-271">global.json file</span></span>                             | [<span data-ttu-id="6b2d3-272">globaljson</span><span class="sxs-lookup"><span data-stu-id="6b2d3-272">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="6b2d3-273">Config</span><span class="sxs-lookup"><span data-stu-id="6b2d3-273">Config</span></span>                                | <span data-ttu-id="6b2d3-274">2.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-274">2.0</span></span>        |
| <span data-ttu-id="6b2d3-275">Konfiguracja NuGet</span><span class="sxs-lookup"><span data-stu-id="6b2d3-275">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="6b2d3-276">Config</span><span class="sxs-lookup"><span data-stu-id="6b2d3-276">Config</span></span>                                | <span data-ttu-id="6b2d3-277">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-277">1.0</span></span>        |
| <span data-ttu-id="6b2d3-278">plik manifestu narzędzia lokalnego dotnet</span><span class="sxs-lookup"><span data-stu-id="6b2d3-278">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="6b2d3-279">Config</span><span class="sxs-lookup"><span data-stu-id="6b2d3-279">Config</span></span>                                | <span data-ttu-id="6b2d3-280">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-280">3.0</span></span>        |
| <span data-ttu-id="6b2d3-281">Konfigurga internetowa</span><span class="sxs-lookup"><span data-stu-id="6b2d3-281">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="6b2d3-282">Config</span><span class="sxs-lookup"><span data-stu-id="6b2d3-282">Config</span></span>                                | <span data-ttu-id="6b2d3-283">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-283">1.0</span></span>        |
| <span data-ttu-id="6b2d3-284">Plik rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6b2d3-284">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="6b2d3-285">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="6b2d3-285">Solution</span></span>                              | <span data-ttu-id="6b2d3-286">1.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-286">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="6b2d3-287">Opcje</span><span class="sxs-lookup"><span data-stu-id="6b2d3-287">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="6b2d3-288">Wyświetla podsumowanie tego, co by się stało, gdyby dane polecenie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-288">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="6b2d3-289">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-289">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="6b2d3-290">Wymusza generowanie zawartości, nawet jeśli spowoduje to zmianę istniejących plików.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-290">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6b2d3-291">Jest to wymagane, gdy wybrany szablon zastąpi istniejące pliki w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-291">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6b2d3-292">Drukuje pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-292">Prints out help for the command.</span></span> <span data-ttu-id="6b2d3-293">Można go wywołać `dotnet new` dla samego polecenia lub dla dowolnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-293">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="6b2d3-294">Na przykład `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-294">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="6b2d3-295">Instaluje pakiet `PATH` szablonów `NUGET_ID` z lub dostarczone.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-295">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6b2d3-296">Jeśli chcesz zainstalować wersję wstępną pakietu szablonu, musisz określić wersję w `<package-name>::<package-version>`formacie .</span><span class="sxs-lookup"><span data-stu-id="6b2d3-296">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6b2d3-297">Domyślnie `dotnet new` przechodzi \* do wersji, która reprezentuje najnowszą stabilną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-297">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="6b2d3-298">Zobacz przykład w sekcji [Przykłady.](#examples)</span><span class="sxs-lookup"><span data-stu-id="6b2d3-298">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="6b2d3-299">Jeśli wersja szablonu została już zainstalowana po uruchomieniu tego polecenia, szablon zostanie zaktualizowany do określonej wersji lub do najnowszej wersji stabilnej, jeśli nie określono żadnej wersji.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-299">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="6b2d3-300">Aby uzyskać informacje na temat tworzenia szablonów niestandardowych, zobacz [Szablony niestandardowe dla dotnet new](custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-300">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="6b2d3-301">Wyświetla listę szablonów zawierających określoną nazwę.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-301">Lists templates containing the specified name.</span></span> <span data-ttu-id="6b2d3-302">Jeśli nazwa nie zostanie określona, wyświetla listę wszystkich szablonów.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-302">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="6b2d3-303">Język szablonu do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-303">The language of the template to create.</span></span> <span data-ttu-id="6b2d3-304">Akceptowany język różni się w zależności od szablonu (zobacz wartości domyślne w sekcji [argumenty).](#arguments)</span><span class="sxs-lookup"><span data-stu-id="6b2d3-304">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6b2d3-305">Nie dotyczy niektórych szablonów.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-305">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6b2d3-306">Niektóre skorupy `#` interpretują jako znak specjalny.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-306">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6b2d3-307">W takich przypadkach należy ująć wartość parametru języka w cudzysłowach.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-307">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="6b2d3-308">Na przykład `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-308">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="6b2d3-309">Nazwa utworzonego wyjścia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-309">The name for the created output.</span></span> <span data-ttu-id="6b2d3-310">Jeśli nazwa nie zostanie określona, używana jest nazwa bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-310">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="6b2d3-311">Określa źródło NuGet, które ma być używane podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-311">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="6b2d3-312">Dostępne od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-312">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="6b2d3-313">Lokalizacja, aby umieścić wygenerowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-313">Location to place the generated output.</span></span> <span data-ttu-id="6b2d3-314">Ustawieniem domyślnym jest bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-314">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="6b2d3-315">Filtruje szablony na podstawie dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-315">Filters templates based on available types.</span></span> <span data-ttu-id="6b2d3-316">Wstępnie zdefiniowane wartości `project` `item`to `other`, lub .</span><span class="sxs-lookup"><span data-stu-id="6b2d3-316">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="6b2d3-317">Odinstalowuje pakiet szablonów w `PATH` lub `NUGET_ID` pod warunkiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-317">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6b2d3-318">Gdy `<PATH|NUGET_ID>` wartość nie zostanie określona, wyświetlane są wszystkie aktualnie zainstalowane pakiety szablonów i skojarzone z nimi szablony.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-318">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="6b2d3-319">Podczas określania `NUGET_ID`, nie należy dołączać numer wersji.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-319">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="6b2d3-320">Jeśli nie określisz parametru tej opcji, polecenie zawiera listę zainstalowanych szablonów i szczegółowe informacje o nich.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-320">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6b2d3-321">Aby odinstalować `PATH`szablon przy użyciu programu , musisz w pełni zakwalifikować ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-321">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6b2d3-322">Na przykład *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-322">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="6b2d3-323">Nie dołączaj ostatecznego ukośnika katalogu kończącego na ścieżce szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-323">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="6b2d3-324">Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane, i instaluje je.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-324">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="6b2d3-325">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-325">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="6b2d3-326">Sprawdza, czy są dostępne aktualizacje dla pakietów szablonów, które są aktualnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-326">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="6b2d3-327">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-327">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="6b2d3-328">Opcje szablonu</span><span class="sxs-lookup"><span data-stu-id="6b2d3-328">Template options</span></span>

<span data-ttu-id="6b2d3-329">Każdy szablon projektu może mieć dostępne dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-329">Each project template may have additional options available.</span></span> <span data-ttu-id="6b2d3-330">Podstawowe szablony mają następujące dodatkowe opcje:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-330">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="6b2d3-331">console</span><span class="sxs-lookup"><span data-stu-id="6b2d3-331">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-332">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-332">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-333">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-333">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="6b2d3-334">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-334">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6b2d3-335">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6b2d3-335">SDK version</span></span> | <span data-ttu-id="6b2d3-336">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6b2d3-336">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6b2d3-337">3.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-337">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6b2d3-338">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-338">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="6b2d3-339">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-339">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6b2d3-340">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-340">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="6b2d3-341">Nie jest obsługiwany dla języka F#.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-341">Not supported for F#.</span></span> <span data-ttu-id="6b2d3-342">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-342">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6b2d3-343">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-343">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-344">Jeśli określono, nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-344">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="6b2d3-345">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-345">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="6b2d3-346">Classlib</span><span class="sxs-lookup"><span data-stu-id="6b2d3-346">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-347">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-347">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-348">Wartości: `netcoreapp<version>` aby utworzyć bibliotekę klas `netstandard<version>` .NET Core lub utworzyć bibliotekę klas standardowych platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-348">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6b2d3-349">Wartością domyślną jest `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-349">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="6b2d3-350">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-350">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6b2d3-351">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-351">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="6b2d3-352">Nie jest obsługiwany dla języka F#.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-352">Not supported for F#.</span></span> <span data-ttu-id="6b2d3-353">Dostępne od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-353">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6b2d3-354">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-354">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-355">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-355">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="6b2d3-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="6b2d3-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-357">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-357">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-358">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-358">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="6b2d3-359">Dostępne od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-359">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="6b2d3-360">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-360">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6b2d3-361">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-361">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="6b2d3-362">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-362">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-363">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-363">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="6b2d3-364">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="6b2d3-364">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="6b2d3-365">Ustawia `LangVersion` właściwość w utworzonym pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-365">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="6b2d3-366">Na przykład `--langVersion 7.3` użyj do użycia języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-366">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="6b2d3-367">Aby uzyskać listę domyślnych wersji języka C#, zobacz [Domyślne](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-367">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-368">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-368">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="6b2d3-369">pracownik, grpc</span><span class="sxs-lookup"><span data-stu-id="6b2d3-369">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-370">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-370">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-371">Wartością domyślną jest `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-371">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="6b2d3-372">Dostępne od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-372">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6b2d3-373">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-373">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-374">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-374">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="6b2d3-375">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="6b2d3-375">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-376">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-376">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-377">Opcja dostępna od pliku .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-377">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="6b2d3-378">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-378">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6b2d3-379">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6b2d3-379">SDK version</span></span> | <span data-ttu-id="6b2d3-380">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6b2d3-380">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6b2d3-381">3.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-381">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6b2d3-382">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-382">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="6b2d3-383">Umożliwia pakowanie dla projektu za pomocą [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-383">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-384">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-384">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="6b2d3-385">Nunit</span><span class="sxs-lookup"><span data-stu-id="6b2d3-385">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-386">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-386">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="6b2d3-387">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-387">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6b2d3-388">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6b2d3-388">SDK version</span></span> | <span data-ttu-id="6b2d3-389">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6b2d3-389">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6b2d3-390">3.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-390">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6b2d3-391">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-391">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6b2d3-392">2.2</span><span class="sxs-lookup"><span data-stu-id="6b2d3-392">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="6b2d3-393">2.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-393">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="6b2d3-394">Umożliwia pakowanie dla projektu za pomocą [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-394">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-395">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-395">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="6b2d3-396">Strona</span><span class="sxs-lookup"><span data-stu-id="6b2d3-396">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="6b2d3-397">Obszar nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-397">Namespace for the generated code.</span></span> <span data-ttu-id="6b2d3-398">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-398">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="6b2d3-399">Tworzy stronę bez PageModel.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-399">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="6b2d3-400">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="6b2d3-400">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="6b2d3-401">Obszar nazw dla wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-401">Namespace for the generated code.</span></span> <span data-ttu-id="6b2d3-402">Wartością domyślną jest `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-402">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="6b2d3-403">blazorserver</span><span class="sxs-lookup"><span data-stu-id="6b2d3-403">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="6b2d3-404">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-404">The type of authentication to use.</span></span> <span data-ttu-id="6b2d3-405">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-405">The possible values are:</span></span>

  - <span data-ttu-id="6b2d3-406">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-406">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="6b2d3-407">`Individual`- Indywidualne uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-407">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="6b2d3-408">`IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-408">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="6b2d3-409">`SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-409">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="6b2d3-410">`MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-410">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="6b2d3-411">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-411">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="6b2d3-412">Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-412">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6b2d3-413">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-413">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6b2d3-414">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-414">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="6b2d3-415">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-415">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6b2d3-416">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-416">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="6b2d3-417">Identyfikator zasad resetowania haseł dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-417">The reset password policy ID for this project.</span></span> <span data-ttu-id="6b2d3-418">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-418">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="6b2d3-419">Identyfikator zasad profilu edycji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-419">The edit profile policy ID for this project.</span></span> <span data-ttu-id="6b2d3-420">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-420">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="6b2d3-421">Wystąpienie usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-421">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6b2d3-422">Użyj `SingleOrg` z `MultiOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-422">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6b2d3-423">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-423">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="6b2d3-424">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-424">The Client ID for this project.</span></span> <span data-ttu-id="6b2d3-425">Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-425">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6b2d3-426">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="6b2d3-427">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-427">The domain for the directory tenant.</span></span> <span data-ttu-id="6b2d3-428">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6b2d3-429">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-429">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="6b2d3-430">Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-430">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6b2d3-431">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6b2d3-432">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="6b2d3-433">Ścieżka żądania w podstawowej ścieżce aplikacji identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-433">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6b2d3-434">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-434">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6b2d3-435">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-435">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="6b2d3-436">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-436">Allows this application read-access to the directory.</span></span> <span data-ttu-id="6b2d3-437">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-437">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6b2d3-438">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-438">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="6b2d3-439">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-439">Turns off HTTPS.</span></span> <span data-ttu-id="6b2d3-440">Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , `--auth`, lub nie są używane do .</span><span class="sxs-lookup"><span data-stu-id="6b2d3-440">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="6b2d3-441">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-441">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6b2d3-442">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-442">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-443">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-443">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="6b2d3-444">web</span><span class="sxs-lookup"><span data-stu-id="6b2d3-444">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6b2d3-445">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-445">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-446">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-446">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-447">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-447">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6b2d3-448">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-448">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6b2d3-449">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6b2d3-449">SDK version</span></span> | <span data-ttu-id="6b2d3-450">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6b2d3-450">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6b2d3-451">3.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-451">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6b2d3-452">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-452">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6b2d3-453">2.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-453">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="6b2d3-454">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-454">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="6b2d3-455">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-455">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="6b2d3-456">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="6b2d3-456">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="6b2d3-457">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-457">The type of authentication to use.</span></span> <span data-ttu-id="6b2d3-458">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-458">The possible values are:</span></span>

  - <span data-ttu-id="6b2d3-459">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-459">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="6b2d3-460">`Individual`- Indywidualne uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-460">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="6b2d3-461">`IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-461">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="6b2d3-462">`SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-462">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="6b2d3-463">`MultiOrg`- Uwierzytelnianie organizacyjne dla wielu dzierżawców.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-463">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="6b2d3-464">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-464">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="6b2d3-465">Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-465">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6b2d3-466">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-466">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6b2d3-467">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-467">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="6b2d3-468">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-468">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6b2d3-469">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-469">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="6b2d3-470">Identyfikator zasad resetowania haseł dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-470">The reset password policy ID for this project.</span></span> <span data-ttu-id="6b2d3-471">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-471">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="6b2d3-472">Identyfikator zasad profilu edycji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-472">The edit profile policy ID for this project.</span></span> <span data-ttu-id="6b2d3-473">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-473">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="6b2d3-474">Wystąpienie usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-474">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6b2d3-475">Użyj `SingleOrg` z `MultiOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-475">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6b2d3-476">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-476">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="6b2d3-477">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-477">The Client ID for this project.</span></span> <span data-ttu-id="6b2d3-478">Użyj `IndividualB2C`z `SingleOrg`, `MultiOrg` lub uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-478">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6b2d3-479">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-479">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="6b2d3-480">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-480">The domain for the directory tenant.</span></span> <span data-ttu-id="6b2d3-481">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-481">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6b2d3-482">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-482">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="6b2d3-483">Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-483">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6b2d3-484">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-484">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6b2d3-485">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-485">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="6b2d3-486">Ścieżka żądania w podstawowej ścieżce aplikacji identyfikatora URI przekierowania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-486">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6b2d3-487">Użyj `SingleOrg` z `IndividualB2C` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-487">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6b2d3-488">Wartością domyślną jest `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-488">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="6b2d3-489">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-489">Allows this application read-access to the directory.</span></span> <span data-ttu-id="6b2d3-490">Dotyczy tylko `SingleOrg` lub `MultiOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-490">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6b2d3-491">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-491">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="6b2d3-492">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-492">Turns off HTTPS.</span></span> <span data-ttu-id="6b2d3-493">Ta opcja ma `Individual`zastosowanie `IndividualB2C` `SingleOrg`tylko `MultiOrg` wtedy, gdy , , lub nie są używane.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-493">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="6b2d3-494">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-494">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6b2d3-495">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-495">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-496">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-496">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-497">Opcja dostępna od pliku .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-497">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="6b2d3-498">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-498">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6b2d3-499">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6b2d3-499">SDK version</span></span> | <span data-ttu-id="6b2d3-500">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6b2d3-500">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6b2d3-501">3.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-501">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6b2d3-502">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-502">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="6b2d3-503">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-503">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="6b2d3-504">Zawiera BrowserLink w projekcie.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-504">Includes BrowserLink in the project.</span></span> <span data-ttu-id="6b2d3-505">Opcja niedostępna w zestawach SDK .NET Core 2.2 i 3.1.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-505">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="6b2d3-506">Określa, czy projekt jest skonfigurowany do używania [kompilacji środowiska uruchomieniowego Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) w kompilacjach debugowania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-506">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="6b2d3-507">Opcja dostępna od pliku .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-507">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="6b2d3-508">kątowe, reagować</span><span class="sxs-lookup"><span data-stu-id="6b2d3-508">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="6b2d3-509">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-509">The type of authentication to use.</span></span> <span data-ttu-id="6b2d3-510">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-510">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="6b2d3-511">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-511">The possible values are:</span></span>

  - <span data-ttu-id="6b2d3-512">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-512">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="6b2d3-513">`Individual`- Indywidualne uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-513">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6b2d3-514">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-514">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-515">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-515">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="6b2d3-516">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-516">Turns off HTTPS.</span></span> <span data-ttu-id="6b2d3-517">Ta opcja ma zastosowanie `None`tylko wtedy, gdy uwierzytelnianie jest .</span><span class="sxs-lookup"><span data-stu-id="6b2d3-517">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="6b2d3-518">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6b2d3-519">Dotyczy tylko `Individual` lub `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6b2d3-520">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-520">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-521">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-521">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-522">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-522">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6b2d3-523">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-523">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6b2d3-524">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6b2d3-524">SDK version</span></span> | <span data-ttu-id="6b2d3-525">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6b2d3-525">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6b2d3-526">3.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-526">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6b2d3-527">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-527">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6b2d3-528">2.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-528">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="6b2d3-529">reactredux</span><span class="sxs-lookup"><span data-stu-id="6b2d3-529">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6b2d3-530">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-531">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-532">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6b2d3-533">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6b2d3-534">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6b2d3-534">SDK version</span></span> | <span data-ttu-id="6b2d3-535">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6b2d3-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6b2d3-536">3.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6b2d3-537">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6b2d3-538">2.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-538">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="6b2d3-539">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="6b2d3-540">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-540">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="6b2d3-541">brzytwaklasyb</span><span class="sxs-lookup"><span data-stu-id="6b2d3-541">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="6b2d3-542">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="6b2d3-543">Obsługuje dodawanie tradycyjnych stron razor i widoki oprócz składników do tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-543">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="6b2d3-544">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-544">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="6b2d3-545">Webapi</span><span class="sxs-lookup"><span data-stu-id="6b2d3-545">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="6b2d3-546">Typ uwierzytelniania do użycia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-546">The type of authentication to use.</span></span> <span data-ttu-id="6b2d3-547">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-547">The possible values are:</span></span>

  - <span data-ttu-id="6b2d3-548">`None`- Brak uwierzytelniania (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="6b2d3-548">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="6b2d3-549">`IndividualB2C`- Indywidualne uwierzytelnianie za pomocą usługi Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-549">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="6b2d3-550">`SingleOrg`- Uwierzytelnianie organizacyjne dla jednej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-550">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="6b2d3-551">`Windows`- Uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="6b2d3-552">Wystąpienie B2C usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6b2d3-553">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6b2d3-554">Wartością domyślną jest `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="6b2d3-555">Identyfikator zasad logowania i rejestracji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6b2d3-556">Użyj `IndividualB2C` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-556">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="6b2d3-557">Wystąpienie usługi Azure Active Directory do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-557">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6b2d3-558">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6b2d3-559">Wartością domyślną jest `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-559">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="6b2d3-560">Identyfikator klienta dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-560">The Client ID for this project.</span></span> <span data-ttu-id="6b2d3-561">Użyj `IndividualB2C` z `SingleOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6b2d3-562">Wartością domyślną jest `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-562">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="6b2d3-563">Domena dzierżawy katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-563">The domain for the directory tenant.</span></span> <span data-ttu-id="6b2d3-564">Użyj `IndividualB2C` z `SingleOrg` lub uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-564">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6b2d3-565">Wartością domyślną jest `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-565">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="6b2d3-566">Identyfikator identyfikatora dzierżawcy katalogu, z który ma się łączyć.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-566">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6b2d3-567">Użyj `SingleOrg` z uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-567">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6b2d3-568">Wartością domyślną jest `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-568">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="6b2d3-569">Umożliwia tej aplikacji dostęp do odczytu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-569">Allows this application read-access to the directory.</span></span> <span data-ttu-id="6b2d3-570">Dotyczy tylko `SingleOrg` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-570">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="6b2d3-571">Wyklucza *launchSettings.json* z wygenerowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-571">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="6b2d3-572">Wyłącza protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-572">Turns off HTTPS.</span></span> <span data-ttu-id="6b2d3-573">`app.UseHsts`i `app.UseHttpsRedirection` nie są `Startup.Configure`dodawane do .</span><span class="sxs-lookup"><span data-stu-id="6b2d3-573">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6b2d3-574">Ta opcja ma `IndividualB2C` zastosowanie `SingleOrg` tylko wtedy, gdy lub nie są używane do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-574">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="6b2d3-575">Określa LocalDB powinny być używane zamiast SQLite.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-575">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6b2d3-576">Dotyczy tylko `IndividualB2C` uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-576">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6b2d3-577">Określa [strukturę](../../standard/frameworks.md) docelową.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-577">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6b2d3-578">Opcja niedostępna w sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-578">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="6b2d3-579">W poniższej tabeli wymieniono wartości domyślne zgodnie z używanym numerem wersji zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-579">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="6b2d3-580">Wersja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6b2d3-580">SDK version</span></span> | <span data-ttu-id="6b2d3-581">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6b2d3-581">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="6b2d3-582">3.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-582">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="6b2d3-583">3.0</span><span class="sxs-lookup"><span data-stu-id="6b2d3-583">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="6b2d3-584">2.1</span><span class="sxs-lookup"><span data-stu-id="6b2d3-584">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="6b2d3-585">Nie wykonuje niejawnego przywracania podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-585">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="6b2d3-586">globaljson</span><span class="sxs-lookup"><span data-stu-id="6b2d3-586">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="6b2d3-587">Określa wersję pliku .NET Core SDK, który ma być używany w pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="6b2d3-587">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="6b2d3-588">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6b2d3-588">Examples</span></span>

- <span data-ttu-id="6b2d3-589">Utwórz projekt aplikacji konsoli języka C#, określając nazwę szablonu:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-589">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="6b2d3-590">Utwórz projekt aplikacji konsoli F# w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-590">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="6b2d3-591">Utwórz projekt biblioteki klas .NET Standard w określonym katalogu:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-591">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="6b2d3-592">Utwórz nowy projekt core ASP.NET c# MVC w bieżącym katalogu bez uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-592">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="6b2d3-593">Utwórz nowy projekt xUnit:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-593">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="6b2d3-594">Wyświetl listę wszystkich szablonów dostępnych dla szablonów aplikacji jednostronicowych (SPA):List all templates available for Single Page Application (SPA) templates:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-594">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="6b2d3-595">Wyświetl listę wszystkich szablonów pasujących do podciągów *my.*</span><span class="sxs-lookup"><span data-stu-id="6b2d3-595">List all templates matching the *we* substring.</span></span> <span data-ttu-id="6b2d3-596">Nie znaleziono dokładnego dopasowania, więc dopasowanie podciągu działa zarówno względem krótkiej nazwy, jak i kolumn nazw.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-596">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="6b2d3-597">Próba wywołania szablonu pasującego *ng*.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-597">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="6b2d3-598">Jeśli nie można określić pojedynczego dopasowania, wyświetl listę szablonów, które są częściowymi dopasowaniami.</span><span class="sxs-lookup"><span data-stu-id="6b2d3-598">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="6b2d3-599">Zainstaluj wersję 2.0 szablonów SPA dla ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-599">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="6b2d3-600">Wyświetl listę zainstalowanych szablonów i szczegółowe informacje na ich temat, w tym sposób ich odinstalowania:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-600">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="6b2d3-601">Utwórz *global.json* w bieżącym katalogu ustawienie wersji SDK do 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="6b2d3-601">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="6b2d3-602">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b2d3-602">See also</span></span>

- [<span data-ttu-id="6b2d3-603">Szablony niestandardowe dla dotnet new</span><span class="sxs-lookup"><span data-stu-id="6b2d3-603">Custom templates for dotnet new</span></span>](custom-templates.md)
- [<span data-ttu-id="6b2d3-604">Tworzenie szablonu niestandardowego dla polecenia dotnet new</span><span class="sxs-lookup"><span data-stu-id="6b2d3-604">Create a custom template for dotnet new</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="6b2d3-605">dotnet/dotnet-template-samples Repo GitHub</span><span class="sxs-lookup"><span data-stu-id="6b2d3-605">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="6b2d3-606">Dostępne szablony dla dotnet new</span><span class="sxs-lookup"><span data-stu-id="6b2d3-606">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
