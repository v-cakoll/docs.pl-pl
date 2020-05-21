---
title: Szablony niestandardowe dla nowego dotnet
description: Dowiedz się więcej na temat szablonów niestandardowych dla dowolnego typu projektu lub plików platformy .NET.
author: thraka
ms.date: 05/20/2020
ms.openlocfilehash: 19855c99b240b66dfa819e70d4a1bee5c8ed14ed
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761918"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="e6868-103">Szablony niestandardowe dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="e6868-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="e6868-104">[Zestaw .NET Core SDK](https://dotnet.microsoft.com/download) zawiera wiele szablonów, które są już zainstalowane i gotowe do użycia.</span><span class="sxs-lookup"><span data-stu-id="e6868-104">The [.NET Core SDK](https://dotnet.microsoft.com/download) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="e6868-105">[ `dotnet new` Polecenie](dotnet-new.md) nie jest tylko sposobem korzystania z szablonu, ale także instalowania i odinstalowywania szablonów.</span><span class="sxs-lookup"><span data-stu-id="e6868-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="e6868-106">Począwszy od platformy .NET Core 2,0, można tworzyć własne szablony niestandardowe dla dowolnego typu projektu, takie jak aplikacja, usługa, narzędzie lub Biblioteka klas.</span><span class="sxs-lookup"><span data-stu-id="e6868-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="e6868-107">Można nawet utworzyć szablon, który wyprowadza jeden lub więcej niezależnych plików, na przykład plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e6868-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="e6868-108">Szablony niestandardowe można instalować z pakietu NuGet na dowolnym kanale informacyjnym NuGet, odwołując się bezpośrednio do pliku NuGet *. nupkg* lub określając katalog systemu plików zawierający szablon.</span><span class="sxs-lookup"><span data-stu-id="e6868-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="e6868-109">Aparat szablonów oferuje funkcje, które umożliwiają zamianę wartości, uwzględnianie i wykluczanie plików oraz wykonywanie niestandardowych operacji przetwarzania, gdy szablon jest używany.</span><span class="sxs-lookup"><span data-stu-id="e6868-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="e6868-110">Aparat szablonu jest otwartym źródłem, a repozytorium kodu online jest w witrynie GitHub [/tworzenia szablonów](https://github.com/dotnet/templating/) .</span><span class="sxs-lookup"><span data-stu-id="e6868-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="e6868-111">Więcej szablonów, w tym szablonów ze stron trzecich, znajduje się w [dostępnych szablonach dla platformy dotnet Nowość](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="e6868-111">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="e6868-112">Aby uzyskać więcej informacji na temat tworzenia i używania szablonów niestandardowych, zobacz [jak utworzyć własne szablony dla platformy dotnet New](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) i [typu wiki/tworzenia szablonów repozytorium GitHub](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="e6868-112">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

> [!NOTE]
> <span data-ttu-id="e6868-113">Przykłady szablonów są dostępne w repozytorium usługi [dotnet/dotnet-Template-Samples](https://github.com/dotnet/dotnet-template-samples) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="e6868-113">Template examples are available at the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) GitHub repository.</span></span> <span data-ttu-id="e6868-114">Mimo że te przykłady są dobrym zasobem do uczenia się, jak działają szablony, repozytorium jest archiwizowane i nie jest już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e6868-114">However, while these examples are good resource for learning how the templates work, the repository is archived and no longer maintained.</span></span> <span data-ttu-id="e6868-115">Przykłady mogą być nieaktualne i nie będą już działać.</span><span class="sxs-lookup"><span data-stu-id="e6868-115">The examples may be out of date and no longer working.</span></span>

<span data-ttu-id="e6868-116">Aby postępować zgodnie z przewodnikiem i utworzyć szablon, zobacz temat [Tworzenie niestandardowego szablonu dla dotnet nowy](../tutorials/cli-templates-create-item-template.md) samouczek.</span><span class="sxs-lookup"><span data-stu-id="e6868-116">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="e6868-117">Szablony domyślne .NET</span><span class="sxs-lookup"><span data-stu-id="e6868-117">.NET default templates</span></span>

<span data-ttu-id="e6868-118">Po zainstalowaniu [zestaw .NET Core SDK](https://dotnet.microsoft.com/download)otrzymujesz wiele wbudowanych szablonów służących do tworzenia projektów i plików, takich jak aplikacje konsolowe, biblioteki klas, projekty testów jednostkowych, aplikacje ASP.NET Core (w tym projekty [kątowe](https://angular.io/) i [reagowanie](https://facebook.github.io/react/) ) oraz pliki konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="e6868-118">When you install the [.NET Core SDK](https://dotnet.microsoft.com/download), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="e6868-119">Aby wyświetlić listę wbudowanych szablonów, uruchom `dotnet new` polecenie z `-l|--list` opcją:</span><span class="sxs-lookup"><span data-stu-id="e6868-119">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="e6868-120">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e6868-120">Configuration</span></span>

<span data-ttu-id="e6868-121">Szablon składa się z następujących części:</span><span class="sxs-lookup"><span data-stu-id="e6868-121">A template is composed of the following parts:</span></span>

- <span data-ttu-id="e6868-122">Pliki źródłowe i foldery.</span><span class="sxs-lookup"><span data-stu-id="e6868-122">Source files and folders.</span></span>
- <span data-ttu-id="e6868-123">Plik konfiguracji (*Template. JSON*).</span><span class="sxs-lookup"><span data-stu-id="e6868-123">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="e6868-124">Pliki źródłowe i foldery</span><span class="sxs-lookup"><span data-stu-id="e6868-124">Source files and folders</span></span>

<span data-ttu-id="e6868-125">Pliki i foldery źródłowe zawierają wszelkie pliki i foldery, które mają być używane przez aparat szablonów po `dotnet new <TEMPLATE>` uruchomieniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6868-125">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="e6868-126">Aparat szablonów jest przeznaczony do używania *projektów możliwy do uruchomienia* jako kod źródłowy do tworzenia projektów.</span><span class="sxs-lookup"><span data-stu-id="e6868-126">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="e6868-127">Ma to kilka korzyści:</span><span class="sxs-lookup"><span data-stu-id="e6868-127">This has several benefits:</span></span>

- <span data-ttu-id="e6868-128">Aparat szablonów nie wymaga dodawania specjalnych tokenów do kodu źródłowego projektu.</span><span class="sxs-lookup"><span data-stu-id="e6868-128">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="e6868-129">Pliki kodu nie są plikami specjalnymi ani modyfikowane w sposób umożliwiający współdziałanie z aparatem szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-129">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="e6868-130">Dlatego narzędzia zwykle używane podczas pracy z projektami również pracują z zawartością szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-130">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="e6868-131">Możesz tworzyć, uruchamiać i debugować projekty szablonów tak samo jak w przypadku innych projektów.</span><span class="sxs-lookup"><span data-stu-id="e6868-131">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="e6868-132">Możesz szybko utworzyć szablon na podstawie istniejącego projektu tylko przez dodanie pliku konfiguracji *./.Template.config/Template.JSON* do projektu.</span><span class="sxs-lookup"><span data-stu-id="e6868-132">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="e6868-133">Pliki i foldery przechowywane w szablonie nie są ograniczone do formalnych typów projektów .NET.</span><span class="sxs-lookup"><span data-stu-id="e6868-133">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="e6868-134">Pliki źródłowe i foldery mogą zawierać dowolną zawartość, którą chcesz utworzyć, gdy szablon jest używany, nawet jeśli aparat szablonu tworzy tylko jeden plik jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e6868-134">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="e6868-135">Pliki generowane przez szablon można modyfikować w oparciu o logikę i ustawienia podane w pliku konfiguracji *Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e6868-135">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="e6868-136">Użytkownik może przesłonić te ustawienia przez przekazanie opcji do `dotnet new <TEMPLATE>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6868-136">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="e6868-137">Typowym przykładem logiki niestandardowej jest podanie nazwy klasy lub zmiennej w pliku kodu, który jest wdrażany przez szablon.</span><span class="sxs-lookup"><span data-stu-id="e6868-137">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="e6868-138">Template. JSON</span><span class="sxs-lookup"><span data-stu-id="e6868-138">template.json</span></span>

<span data-ttu-id="e6868-139">Plik *Template. JSON* zostanie umieszczony w folderze *Template. config* w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-139">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="e6868-140">Plik zawiera informacje o konfiguracji do aparatu szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-140">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="e6868-141">Minimalna konfiguracja wymaga od członków pokazanych w poniższej tabeli, co jest wystarczające do utworzenia szablonu funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="e6868-141">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="e6868-142">Członek</span><span class="sxs-lookup"><span data-stu-id="e6868-142">Member</span></span>            | <span data-ttu-id="e6868-143">Typ</span><span class="sxs-lookup"><span data-stu-id="e6868-143">Type</span></span>          | <span data-ttu-id="e6868-144">Opis</span><span class="sxs-lookup"><span data-stu-id="e6868-144">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="e6868-145">Identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="e6868-145">URI</span></span>           | <span data-ttu-id="e6868-146">Schemat JSON dla pliku *Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e6868-146">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="e6868-147">Edytory obsługujące schematy JSON umożliwiają korzystanie z funkcji edytowania JSON, gdy schemat jest określony.</span><span class="sxs-lookup"><span data-stu-id="e6868-147">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="e6868-148">Na przykład [Visual Studio Code](https://code.visualstudio.com/) wymaga tego elementu członkowskiego, aby włączyć funkcję IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e6868-148">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="e6868-149">Użyj wartości `http://json.schemastore.org/template` .</span><span class="sxs-lookup"><span data-stu-id="e6868-149">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="e6868-150">ciąg</span><span class="sxs-lookup"><span data-stu-id="e6868-150">string</span></span>        | <span data-ttu-id="e6868-151">Autor szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-151">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="e6868-152">Array (ciąg)</span><span class="sxs-lookup"><span data-stu-id="e6868-152">array(string)</span></span> | <span data-ttu-id="e6868-153">Zero lub więcej charakterystyki szablonu, którego użytkownik może użyć, aby znaleźć szablon podczas jego wyszukania.</span><span class="sxs-lookup"><span data-stu-id="e6868-153">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="e6868-154">Klasyfikacje są również wyświetlane w kolumnie *Tagi* , gdy pojawiają się na liście szablonów utworzonych przy użyciu `dotnet new -l|--list` polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6868-154">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="e6868-155">ciąg</span><span class="sxs-lookup"><span data-stu-id="e6868-155">string</span></span>        | <span data-ttu-id="e6868-156">Unikatowa nazwa tego szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-156">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="e6868-157">ciąg</span><span class="sxs-lookup"><span data-stu-id="e6868-157">string</span></span>        | <span data-ttu-id="e6868-158">Nazwa szablonu, który użytkownicy powinni zobaczyć.</span><span class="sxs-lookup"><span data-stu-id="e6868-158">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="e6868-159">ciąg</span><span class="sxs-lookup"><span data-stu-id="e6868-159">string</span></span>        | <span data-ttu-id="e6868-160">Domyślna nazwa skrótu służąca do wybierania szablonu, który ma zastosowanie do środowisk, w których nazwa szablonu jest określona przez użytkownika, a nie wybierana za pośrednictwem graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e6868-160">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="e6868-161">Na przykład krótka nazwa jest przydatna w przypadku korzystania z szablonów z wiersza polecenia z poleceniami CLI.</span><span class="sxs-lookup"><span data-stu-id="e6868-161">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="e6868-162">Pełny Schemat pliku *Template. JSON* znajduje się w [magazynie schematów JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="e6868-162">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="e6868-163">Aby uzyskać więcej informacji na temat pliku *Template. JSON* , zobacz stronę [typu tworzenia szablonów programu dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="e6868-163">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="e6868-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6868-164">Example</span></span>

<span data-ttu-id="e6868-165">Na przykład poniżej znajduje się folder Template zawierający dwa pliki zawartości: *Console.cs* i *README. txt*.</span><span class="sxs-lookup"><span data-stu-id="e6868-165">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="e6868-166">Zwróć uwagę, że istnieje wymagany folder o nazwie *. Template. config* zawierający plik *Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e6868-166">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="e6868-167">Plik *Template. JSON* wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="e6868-167">The *template.json* file looks like the following:</span></span>

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

<span data-ttu-id="e6868-168">Folder Moje *Template* to instalowalny pakiet szablonów.</span><span class="sxs-lookup"><span data-stu-id="e6868-168">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="e6868-169">Po zainstalowaniu pakietu `shortName` można go użyć z `dotnet new` poleceniem.</span><span class="sxs-lookup"><span data-stu-id="e6868-169">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="e6868-170">Załóżmy na przykład, `dotnet new adatumconsole` że pliki są wyprowadzane `console.cs` `readme.txt` do bieżącego folderu.</span><span class="sxs-lookup"><span data-stu-id="e6868-170">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="e6868-171">Pakowanie szablonu do pakietu NuGet (plik NUPKG)</span><span class="sxs-lookup"><span data-stu-id="e6868-171">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="e6868-172">Szablon niestandardowy jest spakowany przy użyciu polecenia [pakietu dotnet](dotnet-pack.md) i pliku *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="e6868-172">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="e6868-173">Alternatywnie, można użyć polecenia [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) z [pakietem NuGet](https://docs.microsoft.com/nuget/tools/cli-ref-pack) z plikiem *. nuspec* .</span><span class="sxs-lookup"><span data-stu-id="e6868-173">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="e6868-174">Jednak program NuGet wymaga .NET Framework w systemie Windows i [mono](https://www.mono-project.com/) w systemie Linux i MacOS.</span><span class="sxs-lookup"><span data-stu-id="e6868-174">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="e6868-175">Plik *. csproj* różni się nieco od tradycyjnego pliku Code-Project *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="e6868-175">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="e6868-176">Zwróć uwagę na następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="e6868-176">Note the following settings:</span></span>

01. <span data-ttu-id="e6868-177">`<PackageType>`Ustawienie jest dodawane i ustawiane na `Template` .</span><span class="sxs-lookup"><span data-stu-id="e6868-177">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="e6868-178">`<PackageVersion>`Ustawienie zostanie dodane i ustawiony prawidłowy [numer wersji programu NuGet](/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="e6868-178">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="e6868-179">To `<PackageId>` ustawienie jest dodawane i ustawiane jako unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="e6868-179">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="e6868-180">Ten identyfikator służy do odinstalowywania pakietu szablonów i jest używany przez źródła danych NuGet do rejestrowania pakietu szablonów.</span><span class="sxs-lookup"><span data-stu-id="e6868-180">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="e6868-181">Ogólne ustawienia metadanych powinny być ustawione: `<Title>` , `<Authors>` , `<Description>` , i `<PackageTags>` .</span><span class="sxs-lookup"><span data-stu-id="e6868-181">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<PackageTags>`.</span></span>
01. <span data-ttu-id="e6868-182">`<TargetFramework>`Ustawienie musi być ustawione, nawet jeśli plik binarny tworzony przez proces szablonu nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="e6868-182">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="e6868-183">W poniższym przykładzie jest ustawiony na `netstandard2.0` .</span><span class="sxs-lookup"><span data-stu-id="e6868-183">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="e6868-184">Pakiet szablonów w formie pakietu NuGet *. nupkg* wymaga, aby wszystkie szablony były przechowywane w folderze *zawartości* w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="e6868-184">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="e6868-185">Istnieje kilka dodatkowych ustawień do dodania do pliku *. csproj* , aby upewnić się, że wygenerowane *. nupkg* można zainstalować jako pakiet szablonów:</span><span class="sxs-lookup"><span data-stu-id="e6868-185">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="e6868-186">`<IncludeContentInPack>`Ustawienie jest ustawione na `true` w celu uwzględnienia dowolnego pliku, który jest ustawiany jako **zawartość** pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="e6868-186">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="e6868-187">`<IncludeBuildOutput>`Ustawienie jest ustawione na `false` wykluczenie wszystkich plików binarnych generowanych przez kompilator z pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="e6868-187">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="e6868-188">`<ContentTargetFolders>`Ustawienie jest ustawione na `content` .</span><span class="sxs-lookup"><span data-stu-id="e6868-188">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="e6868-189">Daje to pewność, że pliki ustawione jako **zawartość** są przechowywane w folderze *zawartości* w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="e6868-189">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="e6868-190">Ten folder w pakiecie NuGet jest analizowany przez system szablonów dotnet.</span><span class="sxs-lookup"><span data-stu-id="e6868-190">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="e6868-191">Prostym sposobem wykluczenia wszystkich plików kodu z kompilowania przez projekt szablonu jest użycie `<Compile Remove="**\*" />` elementu w pliku projektu w obrębie `<ItemGroup>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e6868-191">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="e6868-192">Łatwym sposobem struktury pakietu Template Pack jest umieszczenie wszystkich szablonów w poszczególnych folderach, a następnie każdy folder szablonu wewnątrz folderu *templates* znajdującego się w tym samym katalogu, w którym znajduje się plik *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="e6868-192">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="e6868-193">W ten sposób można użyć pojedynczego elementu projektu, aby uwzględnić wszystkie pliki i foldery w *szablonach* jako **zawartość**.</span><span class="sxs-lookup"><span data-stu-id="e6868-193">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="e6868-194">Wewnątrz `<ItemGroup>` elementu, Utwórz `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` element.</span><span class="sxs-lookup"><span data-stu-id="e6868-194">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="e6868-195">Poniżej znajduje się przykładowy plik *csproj* , który jest zgodny ze wszystkimi powyższymi wskazówkami.</span><span class="sxs-lookup"><span data-stu-id="e6868-195">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="e6868-196">Program IT pakuje folder podrzędny *szablonów* do folderu pakietu *zawartości* i wyklucza każdy plik kodu z kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e6868-196">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

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

<span data-ttu-id="e6868-197">W poniższym przykładzie przedstawiono strukturę plików i folderów programu przy użyciu pliku *. csproj* , aby utworzyć pakiet szablonów.</span><span class="sxs-lookup"><span data-stu-id="e6868-197">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="e6868-198">Folder plików i *szablonów* *MyDotnetTemplates. csproj* znajduje się w katalogu głównym katalogu o nazwie *project_folder*.</span><span class="sxs-lookup"><span data-stu-id="e6868-198">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="e6868-199">Folder *szablonów* zawiera dwa szablony, *mytemplate1* i *mytemplate2*.</span><span class="sxs-lookup"><span data-stu-id="e6868-199">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="e6868-200">Każdy szablon zawiera pliki zawartości i folder *. Template. config* z plikiem konfiguracji *Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e6868-200">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

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

## <a name="installing-a-template"></a><span data-ttu-id="e6868-201">Instalowanie szablonu</span><span class="sxs-lookup"><span data-stu-id="e6868-201">Installing a template</span></span>

<span data-ttu-id="e6868-202">Użyj polecenia [dotnet New-i |--Install](dotnet-new.md) , aby zainstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="e6868-202">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="e6868-203">Aby zainstalować szablon z pakietu NuGet przechowywanego w nuget.org</span><span class="sxs-lookup"><span data-stu-id="e6868-203">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="e6868-204">Użyj identyfikatora pakietu NuGet, aby zainstalować pakiet szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-204">Use the NuGet package identifier to install a template package.</span></span>

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="e6868-205">Aby zainstalować szablon z lokalnego pliku NUPKG</span><span class="sxs-lookup"><span data-stu-id="e6868-205">To install a template from a local nupkg file</span></span>

<span data-ttu-id="e6868-206">Podaj ścieżkę do pliku pakietu NuGet *. nupkg* .</span><span class="sxs-lookup"><span data-stu-id="e6868-206">Provide the path to a *.nupkg* NuGet package file.</span></span>

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="e6868-207">Aby zainstalować szablon z katalogu systemu plików</span><span class="sxs-lookup"><span data-stu-id="e6868-207">To install a template from a file system directory</span></span>

<span data-ttu-id="e6868-208">Szablony można instalować z folderu szablonów, takiego jak folder *mytemplate1* , z powyższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e6868-208">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="e6868-209">Określ ścieżkę folderu folderu *Template. config* .</span><span class="sxs-lookup"><span data-stu-id="e6868-209">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="e6868-210">Ścieżka do katalogu szablonów nie musi być bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="e6868-210">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="e6868-211">Jednak do odinstalowania szablonu, który jest instalowany z folderu, wymagana jest ścieżka bezwzględna.</span><span class="sxs-lookup"><span data-stu-id="e6868-211">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="e6868-212">Pobierz listę zainstalowanych szablonów</span><span class="sxs-lookup"><span data-stu-id="e6868-212">Get a list of installed templates</span></span>

<span data-ttu-id="e6868-213">Polecenie odinstalowania bez żadnych innych parametrów spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="e6868-213">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="e6868-214">To polecenie zwraca coś podobnego do następującego:</span><span class="sxs-lookup"><span data-stu-id="e6868-214">That command returns something similar to the following output:</span></span>

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

<span data-ttu-id="e6868-215">Pierwszy poziom elementów po `Currently installed items:` są identyfikatorami używanymi podczas odinstalowywania szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-215">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="e6868-216">I w powyższym przykładzie `Microsoft.DotNet.Common.ItemTemplates` `Microsoft.DotNet.Common.ProjectTemplates.3.0` .</span><span class="sxs-lookup"><span data-stu-id="e6868-216">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="e6868-217">Jeśli szablon został zainstalowany przy użyciu ścieżki systemu plików, ten identyfikator będzie ścieżką folderu folderu *. Template. config* .</span><span class="sxs-lookup"><span data-stu-id="e6868-217">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="e6868-218">Odinstalowywanie szablonu</span><span class="sxs-lookup"><span data-stu-id="e6868-218">Uninstalling a template</span></span>

<span data-ttu-id="e6868-219">Aby odinstalować pakiet, użyj polecenia " [New-u |--Uninstall" dotnet](dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="e6868-219">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="e6868-220">Jeśli pakiet został zainstalowany bezpośrednio przez źródło danych NuGet lub plik *. nupkg* , podaj identyfikator.</span><span class="sxs-lookup"><span data-stu-id="e6868-220">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="e6868-221">Jeśli pakiet został zainstalowany przez określenie ścieżki do folderu *. Template. config* , Użyj tej ścieżki **bezwzględnej** w celu odinstalowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="e6868-221">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="e6868-222">Ścieżkę bezwzględną szablonu można zobaczyć w danych wyjściowych dostarczonych przez `dotnet new -u` polecenie.</span><span class="sxs-lookup"><span data-stu-id="e6868-222">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="e6868-223">Aby uzyskać więcej informacji, zobacz sekcję [Pobieranie listy zainstalowanych szablonów](#get-a-list-of-installed-templates) powyżej.</span><span class="sxs-lookup"><span data-stu-id="e6868-223">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="e6868-224">Tworzenie projektu przy użyciu szablonu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="e6868-224">Create a project using a custom template</span></span>

<span data-ttu-id="e6868-225">Po zainstalowaniu szablonu Użyj szablonu, wykonując `dotnet new <TEMPLATE>` polecenie tak jak w przypadku dowolnego innego wstępnie zainstalowanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-225">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="e6868-226">Możesz również określić [Opcje](dotnet-new.md#options) dla `dotnet new` polecenia, w tym opcje specyficzne dla szablonu, które zostały skonfigurowane w ustawieniach szablonu.</span><span class="sxs-lookup"><span data-stu-id="e6868-226">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="e6868-227">Podaj krótką nazwę szablonu bezpośrednio do polecenia:</span><span class="sxs-lookup"><span data-stu-id="e6868-227">Supply the template's short name directly to the command:</span></span>

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="e6868-228">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6868-228">See also</span></span>

- [<span data-ttu-id="e6868-229">Tworzenie szablonu niestandardowego dla nowego dotnet (samouczek)</span><span class="sxs-lookup"><span data-stu-id="e6868-229">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/cli-templates-create-item-template.md)
- [<span data-ttu-id="e6868-230">Witryna typu wiki repozytorium usługi GitHub/tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="e6868-230">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="e6868-231">dotnet/dotnet-Template-przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="e6868-231">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="e6868-232">Jak utworzyć własne szablony dla nowego dotnet</span><span class="sxs-lookup"><span data-stu-id="e6868-232">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="e6868-233">*szablon Template. JSON* w magazynie schematów JSON</span><span class="sxs-lookup"><span data-stu-id="e6868-233">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
