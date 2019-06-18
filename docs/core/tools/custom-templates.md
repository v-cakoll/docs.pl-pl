---
title: Szablony niestandardowe dla nowej platformy dotnet
description: Dowiedz się więcej na temat szablonów niestandardowych dla dowolnego typu projektu .NET lub plików.
author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: 19211d1ac45bbd2e5838c5ee30e380d7d10c3f1c
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2019
ms.locfileid: "67151950"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="34fc9-103">Szablony niestandardowe dla nowej platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="34fc9-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="34fc9-104">[Zestawu .NET Core SDK](https://www.microsoft.com/net/download/core) jest powiązana z wielu szablonów już zainstalowany i gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="34fc9-104">The [.NET Core SDK](https://www.microsoft.com/net/download/core) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="34fc9-105">[ `dotnet new` Polecenia](dotnet-new.md) nie tylko sposób używania szablonu, ale także sposób instalowania i odinstalowywania szablonów.</span><span class="sxs-lookup"><span data-stu-id="34fc9-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="34fc9-106">Począwszy od programu .NET Core 2.0, można utworzyć własne szablony niestandardowe dla każdego typu projektu, takie jak aplikacja, usługi, narzędzia lub biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="34fc9-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="34fc9-107">Możesz nawet utworzyć szablon, który generuje co najmniej jeden niezależnych plikach, takich jak plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="34fc9-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="34fc9-108">Można zainstalować niestandardowe szablony z pakietu NuGet dla dowolnego narzędzia NuGet kanału informacyjnego, odwołując się do NuGet *.nupkg* plików bezpośrednio lub przez określenie katalogu systemu plików, który zawiera szablon.</span><span class="sxs-lookup"><span data-stu-id="34fc9-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="34fc9-109">Aparat szablonów oferuje funkcje, które umożliwiają zastępować wartości, dołączanie i wykluczanie plików i wykonywanie niestandardowych operacji, gdy szablon jest używany.</span><span class="sxs-lookup"><span data-stu-id="34fc9-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="34fc9-110">Aparat szablonów "open source", a repozytorium kodu w trybie online jest w [dotnet/szablonów](https://github.com/dotnet/templating/) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="34fc9-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="34fc9-111">Odwiedź stronę [dotnet/dotnet szablonu samples](https://github.com/dotnet/dotnet-template-samples) repozytorium przykładów szablonów.</span><span class="sxs-lookup"><span data-stu-id="34fc9-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="34fc9-112">Więcej szablonów, w tym szablony innych firm, znajdują się w [dostępnych szablonów dla platformy dotnet nowe](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="34fc9-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="34fc9-113">Aby uzyskać więcej informacji na temat tworzenia i używania niestandardowych szablonów, zobacz [sposobu tworzenia nowych szablonów dla platformy dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) i [repozytorium GitHub dotnet/szablonów Wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="34fc9-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="34fc9-114">Aby wykonać przewodnik i utworzyć szablon, zobacz [Utwórz nowy szablon niestandardowy dla platformy dotnet](~/docs/core/tutorials/create-custom-template.md) samouczka.</span><span class="sxs-lookup"><span data-stu-id="34fc9-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="34fc9-115">Szablony domyślne platformy .NET</span><span class="sxs-lookup"><span data-stu-id="34fc9-115">.NET default templates</span></span>

<span data-ttu-id="34fc9-116">Po zainstalowaniu [zestawu .NET Core SDK](https://www.microsoft.com/net/download/core), pojawi się ponad tuzina wbudowanych szablonów do tworzenia projektów i plików, w tym aplikacje konsoli, bibliotekach klas, jednostka testowanie projektów, aplikacje platformy ASP.NET Core (w tym [Angular](https://angular.io/) i [React](https://facebook.github.io/react/) projektów) i pliki konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="34fc9-116">When you install the [.NET Core SDK](https://www.microsoft.com/net/download/core), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="34fc9-117">Aby wyświetlić listę wbudowanych szablonów, należy uruchomić `dotnet new` polecenia `-l|--list` opcji:</span><span class="sxs-lookup"><span data-stu-id="34fc9-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```console
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="34fc9-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="34fc9-118">Configuration</span></span>

<span data-ttu-id="34fc9-119">Szablon składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="34fc9-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="34fc9-120">Pliki źródłowe i foldery.</span><span class="sxs-lookup"><span data-stu-id="34fc9-120">Source files and folders.</span></span>
- <span data-ttu-id="34fc9-121">Plik konfiguracji (*template.json*).</span><span class="sxs-lookup"><span data-stu-id="34fc9-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="34fc9-122">Źródło plików i folderów</span><span class="sxs-lookup"><span data-stu-id="34fc9-122">Source files and folders</span></span>

<span data-ttu-id="34fc9-123">Pliki źródłowe i foldery obejmują dowolnych pliki i foldery, które mają szablonu aparatu do użycia podczas `dotnet new <TEMPLATE>` jest uruchamiane polecenie.</span><span class="sxs-lookup"><span data-stu-id="34fc9-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="34fc9-124">Aparat szablonów jest przeznaczony do stosowania *możliwy do uruchomienia projektów* jako źródło kodu do tworzenia projektów.</span><span class="sxs-lookup"><span data-stu-id="34fc9-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="34fc9-125">To ma kilka zalet:</span><span class="sxs-lookup"><span data-stu-id="34fc9-125">This has several benefits:</span></span>

- <span data-ttu-id="34fc9-126">Aparat szablonów nie wymaga wstrzyknąć specjalne tokeny do kodu źródłowego projektu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="34fc9-127">Pliki kodu nie są specjalne pliki lub zmodyfikowane w dowolny sposób, aby pracować z aparatu szablonów.</span><span class="sxs-lookup"><span data-stu-id="34fc9-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="34fc9-128">Tak narzędzi, które normalnie używane podczas pracy z projektami również działać przy użyciu szablonu zawartości.</span><span class="sxs-lookup"><span data-stu-id="34fc9-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="34fc9-129">Tworzenie, uruchamianie i debugowanie projektów szablonu, podobnie jak w przypadku wszystkich innych projektów.</span><span class="sxs-lookup"><span data-stu-id="34fc9-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="34fc9-130">Możesz szybko utworzyć szablon z istniejącego projektu, po prostu przez dodanie *./.template.config/template.json* pliku konfiguracji do projektu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="34fc9-131">Plików i folderów przechowywanych w szablonie nie ma ograniczenia dla formalnych typów projektów .NET.</span><span class="sxs-lookup"><span data-stu-id="34fc9-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="34fc9-132">Źródło plików i folderów może zawierać dowolną zawartość, która ma zostać utworzony, gdy szablon jest używany, nawet wtedy, gdy aparat szablonów tworzy pojedynczy plik jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="34fc9-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="34fc9-133">Pliki generowane przez szablon może być modyfikowany na podstawie logiki i ustawień, które podano w *template.json* pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="34fc9-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="34fc9-134">Użytkownika można zastąpić te ustawienia, przekazując opcje `dotnet new <TEMPLATE>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="34fc9-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="34fc9-135">Typowym przykładem logiki niestandardowej jest podanie nazwy dla klasy lub zmiennej w pliku kodu, który jest wdrożony przez szablon.</span><span class="sxs-lookup"><span data-stu-id="34fc9-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="34fc9-136">template.json</span><span class="sxs-lookup"><span data-stu-id="34fc9-136">template.json</span></span>

<span data-ttu-id="34fc9-137">*Template.json* plik zostanie umieszczony w *. template.config* folder w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="34fc9-138">Plik zawiera informacje o konfiguracji do aparatu szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="34fc9-139">Minimalna konfiguracja wymaga od członków, pokazano w poniższej tabeli, która jest wystarczające, aby utworzyć szablon funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="34fc9-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="34fc9-140">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="34fc9-140">Member</span></span>            | <span data-ttu-id="34fc9-141">Typ</span><span class="sxs-lookup"><span data-stu-id="34fc9-141">Type</span></span>          | <span data-ttu-id="34fc9-142">Opis</span><span class="sxs-lookup"><span data-stu-id="34fc9-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="34fc9-143">Identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="34fc9-143">URI</span></span>           | <span data-ttu-id="34fc9-144">Schemat JSON dla *template.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="34fc9-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="34fc9-145">Edytory, które obsługują schematów JSON Włącz funkcje Edycja JSON, jeśli nie określono schematu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="34fc9-146">Na przykład [programu Visual Studio Code](https://code.visualstudio.com/) wymaga tego elementu członkowskiego włączyć technologię IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="34fc9-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="34fc9-147">Użyj wartości `http://json.schemastore.org/template`.</span><span class="sxs-lookup"><span data-stu-id="34fc9-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="34fc9-148">string</span><span class="sxs-lookup"><span data-stu-id="34fc9-148">string</span></span>        | <span data-ttu-id="34fc9-149">Autor szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="34fc9-150">Array(String)</span><span class="sxs-lookup"><span data-stu-id="34fc9-150">array(string)</span></span> | <span data-ttu-id="34fc9-151">Zero lub więcej właściwości szablon, którego użytkownik może znaleźć szablonu podczas wyszukiwania dla niego.</span><span class="sxs-lookup"><span data-stu-id="34fc9-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="34fc9-152">Klasyfikacje są również wyświetlane w *tagi* kolumny, gdy się pojawi się na liście szablony utworzone za pomocą `dotnet new -l|--list` polecenia.</span><span class="sxs-lookup"><span data-stu-id="34fc9-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="34fc9-153">string</span><span class="sxs-lookup"><span data-stu-id="34fc9-153">string</span></span>        | <span data-ttu-id="34fc9-154">Unikatowa nazwa dla tego szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="34fc9-155">string</span><span class="sxs-lookup"><span data-stu-id="34fc9-155">string</span></span>        | <span data-ttu-id="34fc9-156">Nazwa szablonu, która powinna być widoczna.</span><span class="sxs-lookup"><span data-stu-id="34fc9-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="34fc9-157">string</span><span class="sxs-lookup"><span data-stu-id="34fc9-157">string</span></span>        | <span data-ttu-id="34fc9-158">Domyślna nazwa skrócona do wybierania szablonu, który ma zastosowanie do środowiska, w którym nazwa szablonu jest określony przez użytkownika nie są wybrane za pomocą graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="34fc9-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="34fc9-159">Na przykład krótką nazwę przydaje się podczas korzystania z szablonów z poziomu wiersza polecenia przy użyciu interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="34fc9-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="34fc9-160">Pełnego schematu dla *template.json* plik znajduje się na [Store schematu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="34fc9-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="34fc9-161">Aby uzyskać więcej informacji na temat *template.json* plików, zobacz [wiki szablonów dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="34fc9-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="34fc9-162">Przykład</span><span class="sxs-lookup"><span data-stu-id="34fc9-162">Example</span></span>

<span data-ttu-id="34fc9-163">Na przykład, w tym miejscu jest folder szablonu, który zawiera dwa pliki zawartości: *console.cs* i *readme.txt*.</span><span class="sxs-lookup"><span data-stu-id="34fc9-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="34fc9-164">Zwróć uwagę, że nie ma wymaganego folderu o nazwie *. template.config* zawierający *template.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="34fc9-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="34fc9-165">*Template.json* pliku wygląda podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="34fc9-165">The *template.json* file looks like the following:</span></span>

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

<span data-ttu-id="34fc9-166">*Mytemplate* folder znajduje się pakiet do zainstalowania szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="34fc9-167">Po zainstalowaniu pakietu `shortName` mogą być używane z `dotnet new` polecenia.</span><span class="sxs-lookup"><span data-stu-id="34fc9-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="34fc9-168">Na przykład `dotnet new adatumconsole` będą dane wyjściowe `console.cs` i `readme.txt` pliki do bieżącego folderu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="34fc9-169">Pakowanie szablonu do pakietu NuGet (plik nupkg)</span><span class="sxs-lookup"><span data-stu-id="34fc9-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="34fc9-170">Szablon niestandardowy jest wypełniona [pakietu dotnet](dotnet-pack.md) polecenia i *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="34fc9-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="34fc9-171">Alternatywnie [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) mogą być używane z [pakiet nuget](https://docs.microsoft.com/nuget/tools/cli-ref-pack) polecenia wraz z *.nuspec* pliku.</span><span class="sxs-lookup"><span data-stu-id="34fc9-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="34fc9-172">Jednak NuGet wymaga programu .NET Framework na Windows i [Mono](https://www.mono-project.com/) w systemie Linux i MacOS.</span><span class="sxs-lookup"><span data-stu-id="34fc9-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="34fc9-173">*.Csproj* pliku różni się nieco od tradycyjnych projekt kodu *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="34fc9-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="34fc9-174">Zwróć uwagę na następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="34fc9-174">Note the following settings:</span></span>

01. <span data-ttu-id="34fc9-175">`<PackageType>` Ustawienie zostanie dodane i ustawiona `Template`.</span><span class="sxs-lookup"><span data-stu-id="34fc9-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="34fc9-176">`<PackageVersion>` Ustawienia zostaną dodane i ustawić prawidłową [numer wersji NuGet](/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="34fc9-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="34fc9-177">`<PackageId>` Ustawienia zostaną dodane i Ustaw unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="34fc9-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="34fc9-178">Ten identyfikator służy do odinstalowania szablonowego pakietu i jest używany przez NuGet źródeł danych, aby zarejestrować Twój pakiet szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="34fc9-179">Ustawienia ogólne metadanych powinna być ustawiona: `<Title>`, `<Authors>`, `<Description>`, i `<Tags>`.</span><span class="sxs-lookup"><span data-stu-id="34fc9-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<Tags>`.</span></span>
01. <span data-ttu-id="34fc9-180">`<TargetFramework>` Ustawienia należy wybrać opcję, nawet jeśli nie jest używany plik binarny, generowane przez szablon procesu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="34fc9-181">W poniższym przykładzie ustawiono go `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="34fc9-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="34fc9-182">Pakiet szablonu w formie *.nupkg* pakietu NuGet, wymaga, że wszystkie szablony znajdować się w *zawartości* folder w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="34fc9-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="34fc9-183">Istnieje kilka więcej ustawień, aby dodać do *.csproj* plik, aby upewnić się, że wygenerowany *.nupkg* można zainstalować jako szablonowego pakietu:</span><span class="sxs-lookup"><span data-stu-id="34fc9-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="34fc9-184">`<IncludeContentInPack>` Jest ustawiana `true` obejmujący dowolny plik projektu ustawia jako **zawartości** pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="34fc9-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="34fc9-185">`<IncludeBuildOutput>` Jest ustawiana `false` wykluczyć wszystkie pliki binarne wygenerowane przez kompilator z pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="34fc9-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="34fc9-186">`<ContentTargetFolders>` Ustawienie ma wartość `content`.</span><span class="sxs-lookup"><span data-stu-id="34fc9-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="34fc9-187">Daje to pewność, że pliki są ustawione jako **zawartości** są przechowywane w *zawartości* folderu pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="34fc9-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="34fc9-188">Ten folder w pakiecie NuGet jest analizowany przez system szablonów dotnet.</span><span class="sxs-lookup"><span data-stu-id="34fc9-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="34fc9-189">Prosty sposób Wyklucz wszystkie pliki kodu z jest kompilowane przez projekt szablonu polega na użyciu `<Compile Remove="**\*" />` wewnątrz elementu w pliku projektu `<ItemGroup>` elementu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="34fc9-190">Prosty sposób struktury dany pakiet szablonu jest umieścić wszystkie szablony w poszczególnych folderów, a następnie każdy folder szablonu wewnątrz *szablony* folder, który znajduje się w tym samym katalogu co Twoje *.csproj* plik.</span><span class="sxs-lookup"><span data-stu-id="34fc9-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="34fc9-191">W ten sposób można użyć elementu pojedynczego projektu aby uwzględnić wszystkie pliki i foldery w *szablony* jako **zawartości**.</span><span class="sxs-lookup"><span data-stu-id="34fc9-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="34fc9-192">Wewnątrz `<ItemGroup>` elementu, Utwórz `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` elementu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="34fc9-193">Oto przykład *.csproj* pliku, który następuje po wszystkich powyższych wytycznych.</span><span class="sxs-lookup"><span data-stu-id="34fc9-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="34fc9-194">Jego pakiety *szablony* folder podrzędny do *zawartości* pakiet folderu, a pomija każdy plik kodu kompilowanego.</span><span class="sxs-lookup"><span data-stu-id="34fc9-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <Tags>dotnet-new;templates;contoso</Tags>
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

<span data-ttu-id="34fc9-195">W poniższym przykładzie pokazano strukturę plików i folderów przy użyciu *.csproj* utworzenie pakietu szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="34fc9-196">*MyDotnetTemplates.csproj* pliku i *szablony* folder w katalogu głównym katalogu o nazwie znajdują się *project_folder*.</span><span class="sxs-lookup"><span data-stu-id="34fc9-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="34fc9-197">*Szablony* folder zawiera dwa szablony *mytemplate1* i *mytemplate2*.</span><span class="sxs-lookup"><span data-stu-id="34fc9-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="34fc9-198">Każdy szablon ma pliki zawartości i *. template.config* folder z *template.json* pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="34fc9-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

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

## <a name="installing-a-template"></a><span data-ttu-id="34fc9-199">Instalowanie szablonu</span><span class="sxs-lookup"><span data-stu-id="34fc9-199">Installing a template</span></span>

<span data-ttu-id="34fc9-200">Użyj [nowe dotnet -i | — instalowanie](dotnet-new.md) polecenie, aby zainstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="34fc9-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="34fc9-201">Aby zainstalować szablonu z pakietu NuGet, przechowywane w witrynie nuget.org</span><span class="sxs-lookup"><span data-stu-id="34fc9-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="34fc9-202">Użyj identyfikatora pakietu NuGet można zainstalować pakietu szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-202">Use the NuGet package identifier to install a template package.</span></span>

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="34fc9-203">Aby zainstalować szablonu z pliku lokalnego nupkg</span><span class="sxs-lookup"><span data-stu-id="34fc9-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="34fc9-204">Podaj ścieżkę do *.nupkg* plik pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="34fc9-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="34fc9-205">Aby zainstalować szablonu z katalogu w systemie plików</span><span class="sxs-lookup"><span data-stu-id="34fc9-205">To install a template from a file system directory</span></span>

<span data-ttu-id="34fc9-206">Szablony mogą być instalowane z folderu szablonu, takie jak *mytemplate1* folderu w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34fc9-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="34fc9-207">Określ ścieżkę do folderu *. template.config* folderu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="34fc9-208">Ścieżka do katalogu szablonu nie musi być bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="34fc9-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="34fc9-209">Aby odinstalować szablon, który jest instalowany z folderu są jednak wymagane ścieżką bezwzględną.</span><span class="sxs-lookup"><span data-stu-id="34fc9-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="34fc9-210">Pobierz listę zainstalowanych szablonów</span><span class="sxs-lookup"><span data-stu-id="34fc9-210">Get a list of installed templates</span></span>

<span data-ttu-id="34fc9-211">Polecenie odinstalowania, bez żadnych parametrów, spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="34fc9-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```console
dotnet new -u
```

<span data-ttu-id="34fc9-212">To polecenie zwraca coś podobnego do następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="34fc9-212">That command returns something similar to the following output:</span></span>

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

<span data-ttu-id="34fc9-213">Pierwszy poziom elementów po `Currently installed items:` to identyfikatory używane w odinstalowywanie szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="34fc9-214">W powyższym przykładzie `Microsoft.DotNet.Common.ItemTemplates` i `Microsoft.DotNet.Common.ProjectTemplates.3.0` są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="34fc9-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="34fc9-215">Jeśli szablon został zainstalowany przy użyciu ścieżki systemu plików, ten identyfikator będzie ścieżkę folderu *. template.config* folderu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="34fc9-216">Odinstalowywanie szablonu</span><span class="sxs-lookup"><span data-stu-id="34fc9-216">Uninstalling a template</span></span>

<span data-ttu-id="34fc9-217">Użyj [nowe dotnet -u |--odinstalować](dotnet-new.md) polecenie, aby odinstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="34fc9-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="34fc9-218">Jeśli pakiet został zainstalowany przez kanał informacyjny NuGet lub przez *.nupkg* plików bezpośrednio, podaj identyfikator.</span><span class="sxs-lookup"><span data-stu-id="34fc9-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="34fc9-219">Jeśli pakiet został zainstalowany, określając ścieżkę do *. template.config* folderu, użycie **bezwzględne** ścieżki można odinstalować pakietu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="34fc9-220">Możesz zobaczyć ścieżkę bezwzględną szablonu w danych wyjściowych, dostarczone przez `dotnet new -u` polecenia.</span><span class="sxs-lookup"><span data-stu-id="34fc9-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="34fc9-221">Aby uzyskać więcej informacji, zobacz [uzyskać listę zainstalowanych szablonów](#get-a-list-of-installed-templates) powyższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="34fc9-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```console
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="34fc9-222">Tworzenie projektu przy użyciu szablonu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="34fc9-222">Create a project using a custom template</span></span>

<span data-ttu-id="34fc9-223">Po zainstalowaniu szablonu, należy użyć szablonu, wykonując `dotnet new <TEMPLATE>` polecenia jak każdego innego szablonu wstępnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="34fc9-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="34fc9-224">Można również określić [opcje](dotnet-new.md#options) do `dotnet new` polecenia, w tym opcje specyficzne dla szablonu, skonfigurowanego w ustawieniach szablonu.</span><span class="sxs-lookup"><span data-stu-id="34fc9-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="34fc9-225">Podaj krótką nazwę szablonu bezpośrednio do polecenia:</span><span class="sxs-lookup"><span data-stu-id="34fc9-225">Supply the template's short name directly to the command:</span></span>

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="34fc9-226">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34fc9-226">See also</span></span>

- [<span data-ttu-id="34fc9-227">Tworzenie szablonu niestandardowego dla platformy dotnet w nowych (samouczek)</span><span class="sxs-lookup"><span data-stu-id="34fc9-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="34fc9-228">repozytorium GitHub DotNet/szablonów witryny typu Wiki</span><span class="sxs-lookup"><span data-stu-id="34fc9-228">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="34fc9-229">repozytorium GitHub DotNet/dotnet-— przykłady szablonów</span><span class="sxs-lookup"><span data-stu-id="34fc9-229">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="34fc9-230">Jak utworzyć nowe szablony dla platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="34fc9-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="34fc9-231">*Template.JSON* schemat w Store schematu JSON</span><span class="sxs-lookup"><span data-stu-id="34fc9-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
