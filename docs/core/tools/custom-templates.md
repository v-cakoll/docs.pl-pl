---
title: Szablony niestandardowe dla dotnet nowy
description: Dowiedz się więcej o szablonach niestandardowych dla dowolnego typu projektu lub plików programu .NET.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 8e1ac4ca21a8a90ad0f7c9bd3dd11281eb4a6e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73420884"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="a5a0d-103">Szablony niestandardowe dla dotnet nowy</span><span class="sxs-lookup"><span data-stu-id="a5a0d-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="a5a0d-104">Zestaw [SDK .NET Core](https://dotnet.microsoft.com/download) jest dostarczany z wieloma już zainstalowanymi szablonami i gotowymi do użycia.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-104">The [.NET Core SDK](https://dotnet.microsoft.com/download) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="a5a0d-105">[ `dotnet new` Polecenie](dotnet-new.md) to nie tylko sposób używania szablonu, ale także sposób instalowania i odinstalowywania szablonów.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="a5a0d-106">Począwszy od .NET Core 2.0, można utworzyć własne szablony niestandardowe dla dowolnego typu projektu, takich jak aplikacja, usługa, narzędzie lub biblioteka klas.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="a5a0d-107">Można nawet utworzyć szablon, który generuje jeden lub więcej niezależnych plików, takich jak plik konfiguracyjny.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="a5a0d-108">Szablony niestandardowe z pakietu NuGet można instalować w dowolnym kanale informacyjnym NuGet, odwołując się bezpośrednio do pliku NuGet *.nupkg* lub określając katalog systemu plików zawierający szablon.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="a5a0d-109">Aparat szablonów oferuje funkcje, które umożliwiają zastępowanie wartości, dołączanie i wykluczanie plików oraz wykonywanie niestandardowych operacji przetwarzania, gdy używany jest szablon.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="a5a0d-110">Aparat szablonów jest open source, a repozytorium kodu online jest na [dotnet/templating](https://github.com/dotnet/templating/) na GitHub.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="a5a0d-111">Odwiedź repówce [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) dla przykładów szablonów.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="a5a0d-112">Więcej szablonów, w tym szablony od osób trzecich, znajdują się w [dostępnych szablonach dla dotnet nowy](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na GitHub.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="a5a0d-113">Aby uzyskać więcej informacji na temat tworzenia i używania szablonów niestandardowych, zobacz [Jak tworzyć własne szablony dla dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) i [dotnet /templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="a5a0d-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="a5a0d-114">Aby wykonać instruktaż i utworzyć szablon, zobacz [Tworzenie niestandardowego szablonu dla dotnet nowy](../tutorials/cli-templates-create-item-template.md) samouczek.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="a5a0d-115">Domyślne szablony .NET</span><span class="sxs-lookup"><span data-stu-id="a5a0d-115">.NET default templates</span></span>

<span data-ttu-id="a5a0d-116">Po zainstalowaniu [.NET Core SDK,](https://dotnet.microsoft.com/download)otrzymasz ponad tuzin wbudowanych szablonów do tworzenia projektów i plików, w tym aplikacji konsoli, bibliotek klas, projektów testów jednostkowych, ASP.NET aplikacje Core (w tym projekty [Angular](https://angular.io/) i [React)](https://facebook.github.io/react/) i pliki konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-116">When you install the [.NET Core SDK](https://dotnet.microsoft.com/download), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="a5a0d-117">Aby wyświetlić listę wbudowanych szablonów, `dotnet new` uruchom `-l|--list` polecenie z opcją:</span><span class="sxs-lookup"><span data-stu-id="a5a0d-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="a5a0d-118">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="a5a0d-118">Configuration</span></span>

<span data-ttu-id="a5a0d-119">Szablon składa się z następujących części:</span><span class="sxs-lookup"><span data-stu-id="a5a0d-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="a5a0d-120">Pliki źródłowe i foldery.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-120">Source files and folders.</span></span>
- <span data-ttu-id="a5a0d-121">Plik konfiguracyjny *(template.json).*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="a5a0d-122">Pliki źródłowe i foldery</span><span class="sxs-lookup"><span data-stu-id="a5a0d-122">Source files and folders</span></span>

<span data-ttu-id="a5a0d-123">Pliki źródłowe i foldery zawierają wszystkie pliki i foldery, `dotnet new <TEMPLATE>` których aparat szablonów ma używać podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="a5a0d-124">Aparat szablonów jest przeznaczony do używania *projektów uruchamianych* jako kodu źródłowego do tworzenia projektów.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="a5a0d-125">Ma to kilka zalet:</span><span class="sxs-lookup"><span data-stu-id="a5a0d-125">This has several benefits:</span></span>

- <span data-ttu-id="a5a0d-126">Aparat szablonu nie wymaga wstrzyknąć specjalne tokeny do kodu źródłowego projektu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="a5a0d-127">Pliki kodu nie są specjalnymi plikami ani nie są modyfikowane w żaden sposób do pracy z aparatem szablonów.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="a5a0d-128">Tak więc narzędzia, których zwykle używasz podczas pracy z projektami, działają również z zawartością szablonu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="a5a0d-129">Tworzenie, uruchamianie i debugowanie projektów szablonów, tak jak w przypadku innych projektów.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="a5a0d-130">Szablon można szybko utworzyć z istniejącego projektu, dodając do projektu plik konfiguracyjny *./.template.config/template.json.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="a5a0d-131">Pliki i foldery przechowywane w szablonie nie są ograniczone do formalnych typów projektów .NET.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="a5a0d-132">Pliki źródłowe i foldery mogą składać się z dowolnej zawartości, którą chcesz utworzyć, gdy szablon jest używany, nawet jeśli aparat szablonu tworzy tylko jeden plik jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="a5a0d-133">Pliki generowane przez szablon można modyfikować na podstawie logiki i ustawień podanych w pliku konfiguracyjnym *template.json.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="a5a0d-134">Użytkownik może zastąpić te ustawienia, przekazując opcje do `dotnet new <TEMPLATE>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="a5a0d-135">Typowym przykładem logiki niestandardowej jest podanie nazwy klasy lub zmiennej w pliku kodu, który jest wdrażany przez szablon.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="a5a0d-136">template.json</span><span class="sxs-lookup"><span data-stu-id="a5a0d-136">template.json</span></span>

<span data-ttu-id="a5a0d-137">Plik *template.json* jest umieszczany w folderze *.template.config* w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="a5a0d-138">Plik udostępnia informacje o konfiguracji do aparatu szablonu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="a5a0d-139">Minimalna konfiguracja wymaga elementów członkowskich przedstawionych w poniższej tabeli, co jest wystarczające do utworzenia szablonu funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="a5a0d-140">Członek</span><span class="sxs-lookup"><span data-stu-id="a5a0d-140">Member</span></span>            | <span data-ttu-id="a5a0d-141">Typ</span><span class="sxs-lookup"><span data-stu-id="a5a0d-141">Type</span></span>          | <span data-ttu-id="a5a0d-142">Opis</span><span class="sxs-lookup"><span data-stu-id="a5a0d-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="a5a0d-143">Identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="a5a0d-143">URI</span></span>           | <span data-ttu-id="a5a0d-144">Schemat JSON dla pliku *template.json.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="a5a0d-145">Edytory obsługujące schematy JSON umożliwiają funkcje edycji JSON po określeniu schematu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="a5a0d-146">Na przykład [Kod programu Visual Studio](https://code.visualstudio.com/) wymaga tego elementu członkowskiego, aby włączyć IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="a5a0d-147">Użyj wartości `http://json.schemastore.org/template`.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="a5a0d-148">ciąg</span><span class="sxs-lookup"><span data-stu-id="a5a0d-148">string</span></span>        | <span data-ttu-id="a5a0d-149">Autor szablonu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="a5a0d-150">tablica(ciąg)</span><span class="sxs-lookup"><span data-stu-id="a5a0d-150">array(string)</span></span> | <span data-ttu-id="a5a0d-151">Zero lub więcej cech szablonu, które użytkownik może użyć do znalezienia szablonu podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="a5a0d-152">Klasyfikacje są również wyświetlane w *kolumnie Znaczniki,* gdy pojawiają `dotnet new -l|--list` się na liście szablonów tworzonych przy użyciu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="a5a0d-153">ciąg</span><span class="sxs-lookup"><span data-stu-id="a5a0d-153">string</span></span>        | <span data-ttu-id="a5a0d-154">Unikatowa nazwa tego szablonu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="a5a0d-155">ciąg</span><span class="sxs-lookup"><span data-stu-id="a5a0d-155">string</span></span>        | <span data-ttu-id="a5a0d-156">Nazwa szablonu, który użytkownicy powinni zobaczyć.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="a5a0d-157">ciąg</span><span class="sxs-lookup"><span data-stu-id="a5a0d-157">string</span></span>        | <span data-ttu-id="a5a0d-158">Domyślna skrócona nazwa wyboru szablonu, który ma zastosowanie do środowisk, w których nazwa szablonu jest określona przez użytkownika, a nie wybrany za pomocą graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="a5a0d-159">Na przykład krótka nazwa jest przydatna podczas korzystania z szablonów z wiersza polecenia z poleceniami wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="a5a0d-160">Pełny schemat pliku *template.json* znajduje się w [Magazynie schematów JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="a5a0d-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="a5a0d-161">Aby uzyskać więcej informacji na temat pliku *template.json,* zobacz [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="a5a0d-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="a5a0d-162">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5a0d-162">Example</span></span>

<span data-ttu-id="a5a0d-163">Na przykład oto folder szablonu, który zawiera dwa pliki zawartości: *console.cs* i *readme.txt*.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="a5a0d-164">Zwróć uwagę, że istnieje wymagany folder o nazwie *.template.config,* który zawiera plik *template.json.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="a5a0d-165">Plik *template.json* wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="a5a0d-165">The *template.json* file looks like the following:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

<span data-ttu-id="a5a0d-166">Folder *mytemplate* jest instalowalnym pakietem szablonów.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="a5a0d-167">Po zainstalowaniu pakietu `shortName` można użyć polecenia. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="a5a0d-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="a5a0d-168">Na przykład `dotnet new adatumconsole` będzie `console.cs` wyprowadzać pliki i `readme.txt` do bieżącego folderu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="a5a0d-169">Pakowanie szablonu do pakietu NuGet (plik nupkg)</span><span class="sxs-lookup"><span data-stu-id="a5a0d-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="a5a0d-170">Szablon niestandardowy jest zapakowany z poleceniem [dotnet pack](dotnet-pack.md) i plikiem *csproj.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="a5a0d-171">Alternatywnie [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) może być używany z poleceniem [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) wraz z plikiem *nuspec.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="a5a0d-172">Jednak NuGet wymaga .NET Framework w systemach Windows i [Mono](https://www.mono-project.com/) w systemach Linux i MacOS.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="a5a0d-173">Plik *.csproj* różni się nieco od tradycyjnego pliku *.csproj* code-project.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="a5a0d-174">Zwróć uwagę na następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="a5a0d-174">Note the following settings:</span></span>

01. <span data-ttu-id="a5a0d-175">Ustawienie `<PackageType>` zostanie dodane `Template`i ustawione na wartość .</span><span class="sxs-lookup"><span data-stu-id="a5a0d-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="a5a0d-176">Ustawienie `<PackageVersion>` zostanie dodane i ustawione na prawidłowy [numer wersji NuGet](/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="a5a0d-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="a5a0d-177">Ustawienie `<PackageId>` zostanie dodane i ustawione na unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="a5a0d-178">Ten identyfikator jest używany do odinstalowania pakietu szablonów i jest używany przez źródła danych NuGet do rejestrowania pakietu szablonów.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="a5a0d-179">Ogólne ustawienia metadanych powinny `<Title>` `<Authors>`być `<Description>`ustawione: , , , i `<PackageTags>`.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<PackageTags>`.</span></span>
01. <span data-ttu-id="a5a0d-180">Ustawienie `<TargetFramework>` musi być ustawione, nawet jeśli plik binarny wyprodukowany przez proces szablonu nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="a5a0d-181">W poniższym przykładzie jest `netstandard2.0`ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="a5a0d-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="a5a0d-182">Pakiet szablonów w postaci pakietu NuGet *.nupkg* wymaga, aby wszystkie szablony były przechowywane w folderze *zawartości* w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="a5a0d-183">Istnieje kilka ustawień do dodania do pliku *.csproj,* aby upewnić się, że wygenerowany *plik .nupkg* można zainstalować jako pakiet szablonów:</span><span class="sxs-lookup"><span data-stu-id="a5a0d-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="a5a0d-184">Ustawienie `<IncludeContentInPack>` jest ustawiona `true` na uwzględnienie dowolnego pliku, który projekt ustawia jako **zawartość** w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="a5a0d-185">Ustawienie `<IncludeBuildOutput>` jest ustawiona `false` na wykluczenie wszystkich plików binarnych generowanych przez kompilator z pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="a5a0d-186">Ustawienie `<ContentTargetFolders>` jest ustawione `content`na .</span><span class="sxs-lookup"><span data-stu-id="a5a0d-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="a5a0d-187">Daje to pewność, że pliki ustawione jako **zawartość** są przechowywane w folderze *zawartości* w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="a5a0d-188">Ten folder w pakiecie NuGet jest analizowany przez system szablonów dotnet.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="a5a0d-189">Łatwym sposobem wykluczenia wszystkich plików kodu z kompilowania przez `<Compile Remove="**\*" />` projekt szablonu jest `<ItemGroup>` użycie elementu w pliku projektu, wewnątrz elementu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="a5a0d-190">Łatwym sposobem na uporządkowanie pakietu szablonów jest umieszczenie wszystkich szablonów w poszczególnych folderach, a następnie każdy folder szablonu w folderze *szablonów,* który znajduje się w tym samym katalogu co plik *csproj.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="a5a0d-191">W ten sposób można użyć pojedynczego elementu projektu, aby uwzględnić wszystkie pliki i foldery w *szablonach* jako **zawartość**.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="a5a0d-192">Wewnątrz elementu `<ItemGroup>` utwórz `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` element.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="a5a0d-193">Oto przykładowy plik *csproj,* który jest zgodny ze wszystkimi powyższymi wskazówkami.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="a5a0d-194">Pakuje folder podrzędny *szablonów* do folderu pakietu *zawartości* i wyklucza ze kompilowania dowolny plik kodu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>
    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="a5a0d-195">Poniższy przykład przedstawia strukturę plików i folderów przy użyciu *.csproj* do tworzenia pakietu szablonów.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="a5a0d-196">Folder plików i *szablonów* *MyDotnetTemplates.csproj* znajduje się w katalogu głównym katalogu o nazwie *project_folder*.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="a5a0d-197">Folder *szablonów* zawiera dwa szablony: *mytemplate1* i *mytemplate2*.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="a5a0d-198">Każdy szablon zawiera pliki zawartości i folder *.template.config* z plikiem konfiguracyjnym *template.json.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a><span data-ttu-id="a5a0d-199">Instalowanie szablonu</span><span class="sxs-lookup"><span data-stu-id="a5a0d-199">Installing a template</span></span>

<span data-ttu-id="a5a0d-200">Użyj polecenia [dotnet new -i|-install,](dotnet-new.md) aby zainstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="a5a0d-201">Aby zainstalować szablon z pakietu NuGet przechowywanego w nuget.org</span><span class="sxs-lookup"><span data-stu-id="a5a0d-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="a5a0d-202">Użyj identyfikatora pakietu NuGet, aby zainstalować pakiet szablonu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-202">Use the NuGet package identifier to install a template package.</span></span>

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="a5a0d-203">Aby zainstalować szablon z lokalnego pliku nupkg</span><span class="sxs-lookup"><span data-stu-id="a5a0d-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="a5a0d-204">Podaj ścieżkę do pliku pakietu NuGet *nupkg.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="a5a0d-205">Aby zainstalować szablon z katalogu systemu plików</span><span class="sxs-lookup"><span data-stu-id="a5a0d-205">To install a template from a file system directory</span></span>

<span data-ttu-id="a5a0d-206">Szablony można instalować z folderu szablonu, takiego jak folder *mytemplate1* z powyższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="a5a0d-207">Określ ścieżkę folderu folderu *.template.config.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="a5a0d-208">Ścieżka do katalogu szablonów nie musi być bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="a5a0d-209">Jednak do odinstalowania szablonu zainstalowanego z folderu wymagana jest ścieżka bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="a5a0d-210">Pobierz listę zainstalowanych szablonów</span><span class="sxs-lookup"><span data-stu-id="a5a0d-210">Get a list of installed templates</span></span>

<span data-ttu-id="a5a0d-211">Polecenie odinstalowywania, bez żadnych innych parametrów, wyświetli listę wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="a5a0d-212">To polecenie zwraca coś podobnego do następującego wyjścia:</span><span class="sxs-lookup"><span data-stu-id="a5a0d-212">That command returns something similar to the following output:</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

<span data-ttu-id="a5a0d-213">Pierwszy poziom elementów `Currently installed items:` po są identyfikatory używane w odinstalowywaniu szablonu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="a5a0d-214">I w powyższym `Microsoft.DotNet.Common.ItemTemplates` `Microsoft.DotNet.Common.ProjectTemplates.3.0` przykładzie i są wymienione.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="a5a0d-215">Jeśli szablon został zainstalowany przy użyciu ścieżki systemu plików, ten identyfikator będzie ścieżką folderu folderu *.template.config.*</span><span class="sxs-lookup"><span data-stu-id="a5a0d-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="a5a0d-216">Odinstalowywanie szablonu</span><span class="sxs-lookup"><span data-stu-id="a5a0d-216">Uninstalling a template</span></span>

<span data-ttu-id="a5a0d-217">Użyj polecenia [dotnet new -u|--uninstall,](dotnet-new.md) aby odinstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="a5a0d-218">Jeśli pakiet został zainstalowany przez źródło danych NuGet lub plik *.nupkg* bezpośrednio, podaj identyfikator.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="a5a0d-219">Jeśli pakiet został zainstalowany przez określenie ścieżki do folderu *.template.config,* użyj tej ścieżki **bezwzględnej,** aby odinstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="a5a0d-220">Ścieżkę bezwzględną szablonu można wyświetlić w `dotnet new -u` danych wyjściowych dostarczonych przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="a5a0d-221">Aby uzyskać więcej informacji, zobacz [Pobierz listę zainstalowanych szablonów](#get-a-list-of-installed-templates) sekcji powyżej.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="a5a0d-222">Tworzenie projektu przy użyciu szablonu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="a5a0d-222">Create a project using a custom template</span></span>

<span data-ttu-id="a5a0d-223">Po zainstalowaniu szablonu użyj szablonu, `dotnet new <TEMPLATE>` wykonując polecenie tak, jak w przypadku każdego innego wstępnie zainstalowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="a5a0d-224">Można również [options](dotnet-new.md#options) określić opcje `dotnet new` polecenia, w tym opcje specyficzne dla szablonu skonfigurowane w ustawieniach szablonu.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="a5a0d-225">Podaj krótką nazwę szablonu bezpośrednio do polecenia:</span><span class="sxs-lookup"><span data-stu-id="a5a0d-225">Supply the template's short name directly to the command:</span></span>

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="a5a0d-226">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5a0d-226">See also</span></span>

- [<span data-ttu-id="a5a0d-227">Tworzenie niestandardowego szablonu dla dotnet nowy (samouczek)</span><span class="sxs-lookup"><span data-stu-id="a5a0d-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="a5a0d-228">dotnet/templating GitHub repo Wiki</span><span class="sxs-lookup"><span data-stu-id="a5a0d-228">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="a5a0d-229">dotnet/dotnet-template-samples GitHub repo</span><span class="sxs-lookup"><span data-stu-id="a5a0d-229">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="a5a0d-230">Jak tworzyć własne szablony dla dotnet nowych</span><span class="sxs-lookup"><span data-stu-id="a5a0d-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="a5a0d-231">*schemat template.json* w Sklepie Schematów JSON</span><span class="sxs-lookup"><span data-stu-id="a5a0d-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
