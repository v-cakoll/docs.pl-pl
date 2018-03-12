---
title: "Utwórz nowy szablon niestandardowy dla platformy dotnet"
description: "Dowiedz się, jak utworzyć szablon niestandardowy dla platformy dotnet nowe polecenie w fun tego samouczka."
keywords: "Szablonu .NET i .NET core, tworzenia szablonów, samouczek, dotnet nowy"
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 519b910a-6efe-4394-9b81-0546aa3e7462
ms.workload:
- dotnetcore
ms.openlocfilehash: bf523ead40d0e3cc9148b48d5c7a4a84d3d5cb81
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="create-a-custom-template-for-dotnet-new"></a><span data-ttu-id="2827b-104">Utwórz nowy szablon niestandardowy dla platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="2827b-104">Create a custom template for dotnet new</span></span>

<span data-ttu-id="2827b-105">W tym samouczku przedstawiono sposób do:</span><span class="sxs-lookup"><span data-stu-id="2827b-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="2827b-106">Utwórz szablon podstawowy z istniejącego projektu lub nowy projekt aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="2827b-106">Create a basic template from an existing project or a new console app project.</span></span>
- <span data-ttu-id="2827b-107">Pakiet szablonu w celu dystrybucji w nuget.org lub z lokalnego *nupkg* pliku.</span><span class="sxs-lookup"><span data-stu-id="2827b-107">Pack the template for distribution at nuget.org or from a local *nupkg* file.</span></span>
- <span data-ttu-id="2827b-108">Zainstaluj szablonu z nuget.org, lokalnym *nupkg* pliku lub lokalnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="2827b-108">Install the template from nuget.org, a local *nupkg* file, or the local file system.</span></span>
- <span data-ttu-id="2827b-109">Odinstaluj szablonu.</span><span class="sxs-lookup"><span data-stu-id="2827b-109">Uninstall the template.</span></span>

<span data-ttu-id="2827b-110">Jeśli wolisz przejdź przez samouczek z kompletnego przykładu, Pobierz [przykładowy szablon projektu](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span><span class="sxs-lookup"><span data-stu-id="2827b-110">If you prefer to proceed through the tutorial with a complete sample, download the [sample project template](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span></span> <span data-ttu-id="2827b-111">Przykładowy szablon jest skonfigurowany do dystrybucji NuGet.</span><span class="sxs-lookup"><span data-stu-id="2827b-111">The sample template is configured for NuGet distribution.</span></span>

<span data-ttu-id="2827b-112">Jeśli chcesz użyć przykładowego pobranego z dystrybucji systemu plików, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2827b-112">If you wish to use the downloaded sample with file system distribution, do the following:</span></span>

- <span data-ttu-id="2827b-113">Przenieś zawartość *zawartości* folderu próbki o jeden poziom w górę *GarciaSoftware.ConsoleTemplate.CSharp* folderu.</span><span class="sxs-lookup"><span data-stu-id="2827b-113">Move the contents of the *content* folder of the sample up one level into the *GarciaSoftware.ConsoleTemplate.CSharp* folder.</span></span>
- <span data-ttu-id="2827b-114">Usuń wszystkie puste *zawartości* folderu.</span><span class="sxs-lookup"><span data-stu-id="2827b-114">Delete the empty *content* folder.</span></span>
- <span data-ttu-id="2827b-115">Usuń *nuspec* pliku.</span><span class="sxs-lookup"><span data-stu-id="2827b-115">Delete the *nuspec* file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2827b-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2827b-116">Prerequisites</span></span>

- <span data-ttu-id="2827b-117">Zainstaluj [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="2827b-117">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
- <span data-ttu-id="2827b-118">Przeczytaj temat odwołanie [dotnet nowych szablonów niestandardowych](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="2827b-118">Read the reference topic [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

## <a name="create-a-template-from-a-project"></a><span data-ttu-id="2827b-119">Tworzenie szablonu z projektu</span><span class="sxs-lookup"><span data-stu-id="2827b-119">Create a template from a project</span></span>

<span data-ttu-id="2827b-120">Użyj istniejącego projektu, który został potwierdzony kompiluje i uruchamia lub Utwórz nowy projekt aplikacji konsoli w folderze na dysku twardym.</span><span class="sxs-lookup"><span data-stu-id="2827b-120">Use an existing project that you've confirmed compiles and runs, or create a new console app project in a folder on your hard drive.</span></span> <span data-ttu-id="2827b-121">Ten samouczek zakłada, że nazwa folderu projektu *GarciaSoftware.ConsoleTemplate.CSharp* przechowywane w *Documents\Templates* w profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2827b-121">This tutorial assumes that the name of the project folder is *GarciaSoftware.ConsoleTemplate.CSharp* stored at *Documents\Templates* in the user's profile.</span></span> <span data-ttu-id="2827b-122">Projekt samouczka Nazwa szablonu jest w formacie  *\<nazwa firmy >.\< Typ szablonu >. \<Języka programowania >*, ale można go dowolnie nazwa szablon i projektu niczego ma.</span><span class="sxs-lookup"><span data-stu-id="2827b-122">The tutorial project template name is in the format *\<Company Name>.\<Template Type>.\<Programming Language>*, but you're free to name your project and template anything you wish.</span></span>

1. <span data-ttu-id="2827b-123">Dodaj folder do katalogu głównego projektu o nazwie *. template.config*.</span><span class="sxs-lookup"><span data-stu-id="2827b-123">Add a folder to the root of the project named *.template.config*.</span></span>
1. <span data-ttu-id="2827b-124">Wewnątrz *. template.config* folderu, Utwórz *template.json* plik, aby skonfigurować szablon.</span><span class="sxs-lookup"><span data-stu-id="2827b-124">Inside the *.template.config* folder, create a *template.json* file to configure your template.</span></span> <span data-ttu-id="2827b-125">Więcej informacji i element członkowski definicje dla *template.json* plików, zobacz [dotnet nowych szablonów niestandardowych](../tools/custom-templates.md#templatejson) tematu i [ *template.json* schemat w magazynie schematów JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="2827b-125">For more information and member definitions for the *template.json* file, see the [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) topic and the [*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template).</span></span>

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

<span data-ttu-id="2827b-126">Szablon został zakończony.</span><span class="sxs-lookup"><span data-stu-id="2827b-126">The template is finished.</span></span> <span data-ttu-id="2827b-127">W tym momencie masz dwie opcje dystrybucji szablonu.</span><span class="sxs-lookup"><span data-stu-id="2827b-127">At this point, you have two options for template distribution.</span></span> <span data-ttu-id="2827b-128">Aby kontynuować, w tym samouczku, wybierz jedną ścieżkę lub innych:</span><span class="sxs-lookup"><span data-stu-id="2827b-128">To continue this tutorial, choose one path or the other:</span></span>

1. <span data-ttu-id="2827b-129">[Dystrybucji NuGet](#use-nuget-distribution): Zainstaluj szablonu z NuGet lub lokalnej *nupkg* i użycie szablonu zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="2827b-129">[NuGet distribution](#use-nuget-distribution): install the template from NuGet or from the local *nupkg* file, and use the installed template.</span></span>
2. <span data-ttu-id="2827b-130">[Plik dystrybucji systemu](#use-file-system-distribution).</span><span class="sxs-lookup"><span data-stu-id="2827b-130">[File system distribution](#use-file-system-distribution).</span></span>

## <a name="use-nuget-distribution"></a><span data-ttu-id="2827b-131">Użyj dystrybucji NuGet</span><span class="sxs-lookup"><span data-stu-id="2827b-131">Use NuGet Distribution</span></span>

### <a name="pack-the-template-into-a-nuget-package"></a><span data-ttu-id="2827b-132">Pakiet szablonu do pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="2827b-132">Pack the template into a NuGet package</span></span>

1. <span data-ttu-id="2827b-133">Utwórz folder pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="2827b-133">Create a folder for the NuGet package.</span></span> <span data-ttu-id="2827b-134">Samouczek, nazwy folderu *GarciaSoftware.ConsoleTemplate.CSharp* jest używany, oraz folder jest tworzony w *Documents\NuGetTemplates* folderu w profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2827b-134">For the tutorial, the folder name *GarciaSoftware.ConsoleTemplate.CSharp* is used, and the folder is created inside a *Documents\NuGetTemplates* folder in the user's profile.</span></span> <span data-ttu-id="2827b-135">Utwórz folder o nazwie *zawartości* wewnątrz nowego szablonu folderu do przechowywania plików projektu.</span><span class="sxs-lookup"><span data-stu-id="2827b-135">Create a folder named *content* inside of the new template folder to hold the project files.</span></span>
1. <span data-ttu-id="2827b-136">Kopiuj zawartość folderu projektu, wraz z jego *.template.config/template.json* pliku, do *zawartości* utworzony folder.</span><span class="sxs-lookup"><span data-stu-id="2827b-136">Copy the contents of your project folder, together with its *.template.config/template.json* file, into the *content* folder you created.</span></span>
1. <span data-ttu-id="2827b-137">Obok pozycji *zawartości* folderu, Dodaj [ *nuspec* pliku](/nuget/create-packages/creating-a-package).</span><span class="sxs-lookup"><span data-stu-id="2827b-137">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package).</span></span> <span data-ttu-id="2827b-138">Plik nuspec jest plik manifestu XML, który opisuje zawartość pakietu i dyskach proces tworzenia pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="2827b-138">The nuspec file is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span>
   
   ![Struktura katalogów przedstawiający układ pakietu NuGet](./media/create-custom-template/nugetdirectorylayout.png)

1. <span data-ttu-id="2827b-140">Wewnątrz  **\<packageTypes >** element *nuspec* plików, obejmują  **\<packageType >** element z `name` wartość atrybutu `Template`.</span><span class="sxs-lookup"><span data-stu-id="2827b-140">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="2827b-141">Zarówno *zawartości* folderu i *nuspec* plik powinien znajdować się w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2827b-141">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="2827b-142">W tabeli przedstawiono minimum *nuspec* pliku elementy wymagane do tworzenia szablonu jako pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="2827b-142">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

   | <span data-ttu-id="2827b-143">Element</span><span class="sxs-lookup"><span data-stu-id="2827b-143">Element</span></span>            | <span data-ttu-id="2827b-144">Typ</span><span class="sxs-lookup"><span data-stu-id="2827b-144">Type</span></span>   | <span data-ttu-id="2827b-145">Opis</span><span class="sxs-lookup"><span data-stu-id="2827b-145">Description</span></span> |
   | ------------------ | ------ | ----------- |
   | <span data-ttu-id="2827b-146">**\<Autorzy >**</span><span class="sxs-lookup"><span data-stu-id="2827b-146">**\<authors>**</span></span>     | <span data-ttu-id="2827b-147">string</span><span class="sxs-lookup"><span data-stu-id="2827b-147">string</span></span> | <span data-ttu-id="2827b-148">Rozdzielana przecinkami lista autorzy pakietów, zgodne z nazwami profilu na nuget.org. Autorzy są wyświetlane w galerii NuGet w nuget.org i są odwoływania się do pakietów przez tego samego autorów.</span><span class="sxs-lookup"><span data-stu-id="2827b-148">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
   | <span data-ttu-id="2827b-149">**\<Opis elementu >**</span><span class="sxs-lookup"><span data-stu-id="2827b-149">**\<description>**</span></span> | <span data-ttu-id="2827b-150">string</span><span class="sxs-lookup"><span data-stu-id="2827b-150">string</span></span> | <span data-ttu-id="2827b-151">Długi opis pakietu do wyświetlenia interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2827b-151">A long description of the package for UI display.</span></span> |
   | <span data-ttu-id="2827b-152">**\<id>**</span><span class="sxs-lookup"><span data-stu-id="2827b-152">**\<id>**</span></span>          | <span data-ttu-id="2827b-153">string</span><span class="sxs-lookup"><span data-stu-id="2827b-153">string</span></span> | <span data-ttu-id="2827b-154">Identyfikator pakietu bez uwzględniania wielkości liter, który musi być unikatowa w nuget.org lub niezależnie od pakietu będą znajdować się w galerii.</span><span class="sxs-lookup"><span data-stu-id="2827b-154">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="2827b-155">Identyfikatory nie może zawierać spacji ani znaków, które nie są prawidłowe dla danego adresu URL i ogólnie zgodne reguły obszaru nazw .NET.</span><span class="sxs-lookup"><span data-stu-id="2827b-155">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="2827b-156">Zobacz [wybranie identyfikator unikatowy pakiet i ustawianie numeru wersji](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) orientacji.</span><span class="sxs-lookup"><span data-stu-id="2827b-156">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
   | <span data-ttu-id="2827b-157">**\<packageType>**</span><span class="sxs-lookup"><span data-stu-id="2827b-157">**\<packageType>**</span></span> | <span data-ttu-id="2827b-158">string</span><span class="sxs-lookup"><span data-stu-id="2827b-158">string</span></span> | <span data-ttu-id="2827b-159">Umieść ten element wewnątrz  **\<packageTypes >** element między  **\<metadanych >** elementów.</span><span class="sxs-lookup"><span data-stu-id="2827b-159">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="2827b-160">Ustaw `name` atrybutu  **\<packageType >** elementu `Template`.</span><span class="sxs-lookup"><span data-stu-id="2827b-160">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
   | <span data-ttu-id="2827b-161">**\<Wersja >**</span><span class="sxs-lookup"><span data-stu-id="2827b-161">**\<version>**</span></span>     | <span data-ttu-id="2827b-162">string</span><span class="sxs-lookup"><span data-stu-id="2827b-162">string</span></span> | <span data-ttu-id="2827b-163">Wersja pakietu, następujące wzorzec Wersja_główna.WERSJA_POMOCNICZA.poprawka.</span><span class="sxs-lookup"><span data-stu-id="2827b-163">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="2827b-164">Numery wersji może zawierać sufiks wersji wstępnej, zgodnie z opisem w [wersje wstępne](/nuget/create-packages/prerelease-packages#semantic-versioning).</span><span class="sxs-lookup"><span data-stu-id="2827b-164">Version numbers may include a pre-release suffix as described in [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span></span> |

   <span data-ttu-id="2827b-165">Zobacz [odwołania .nuspec](/nuget/schema/nuspec) dla pełnej *nuspec* pliku schematu.</span><span class="sxs-lookup"><span data-stu-id="2827b-165">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span>

   <span data-ttu-id="2827b-166">*Nuspec* plik o nazwie samouczka *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* i zawiera następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="2827b-166">The *nuspec* file for the tutorial is named *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* and contains the following content:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. <span data-ttu-id="2827b-167">[Utwórz pakiet](/nuget/create-packages/creating-a-package#creating-the-package) przy użyciu `nuget pack <PATH_TO_NUSPEC_FILE>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="2827b-167">[Create the package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span> <span data-ttu-id="2827b-168">Polecenie zakłada, że folder, który zawiera zasoby NuGet w * C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp\*.</span><span class="sxs-lookup"><span data-stu-id="2827b-168">The following command assumes that the folder that holds the NuGet assets is at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp\*.</span></span> <span data-ttu-id="2827b-169">Ale wszędzie tam, gdzie umieścić folder w systemie, `nuget pack` polecenie akceptuje ścieżkę do *nuspec* pliku:</span><span class="sxs-lookup"><span data-stu-id="2827b-169">But wherever you place the folder on your system, the `nuget pack` command accepts the path to the *nuspec* file:</span></span>

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a><span data-ttu-id="2827b-170">Publikowanie pakietu nuget.org</span><span class="sxs-lookup"><span data-stu-id="2827b-170">Publishing the package to nuget.org</span></span>

<span data-ttu-id="2827b-171">Aby opublikować pakietu NuGet, postępuj zgodnie z instrukcjami w [tworzenie i publikowanie pakietu](/nuget/quickstart/create-and-publish-a-package#publish-the-package) tematu.</span><span class="sxs-lookup"><span data-stu-id="2827b-171">To publish a NuGet package, follow the instructions in the [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) topic.</span></span> <span data-ttu-id="2827b-172">Firma Microsoft zaleca jednak nie opublikowanie samouczek szablonu NuGet jako nigdy nie można usunąć go po opublikowaniu tylko delisted.</span><span class="sxs-lookup"><span data-stu-id="2827b-172">However, we recommend that you don't publish the tutorial template to NuGet as it can never be deleted once published, only delisted.</span></span> <span data-ttu-id="2827b-173">Teraz, gdy masz pakiet NuGet w formie *nupkg* plików, zalecamy postępuj zgodnie z instrukcjami poniżej, aby zainstalować szablon bezpośrednio z lokalnej *nupkg* pliku.</span><span class="sxs-lookup"><span data-stu-id="2827b-173">Now that you have the NuGet package in the form of a *nupkg* file, we suggest that you follow the instructions below to install the template directly from the local *nupkg* file.</span></span>

### <a name="install-the-template-from-a-nuget-package"></a><span data-ttu-id="2827b-174">Zainstaluj szablonu z pakietem NuGet</span><span class="sxs-lookup"><span data-stu-id="2827b-174">Install the template from a NuGet package</span></span>

#### <a name="install-the-template-from-the-local-nupkg-file"></a><span data-ttu-id="2827b-175">Zainstaluj szablonu z lokalnej *nupkg* pliku</span><span class="sxs-lookup"><span data-stu-id="2827b-175">Install the template from the local *nupkg* file</span></span>

<span data-ttu-id="2827b-176">Aby zainstalować szablon z *nupkg* pliku wytworzonego, użyj `dotnet new` z `-i|--install` opcję i wprowadź ścieżkę do *nupkg* pliku:</span><span class="sxs-lookup"><span data-stu-id="2827b-176">To install the template from the *nupkg* file that you produced, use the `dotnet new` command with the `-i|--install` option and provide the path to the *nupkg* file:</span></span>

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="2827b-177">Zainstaluj szablonu z pakietem NuGet przechowywane w nuget.org</span><span class="sxs-lookup"><span data-stu-id="2827b-177">Install the template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="2827b-178">Jeśli chcesz zainstalować szablonu z przechowywanych na nuget.org, użyj pakietu NuGet `dotnet new` z `-i|--install` opcji i podaj nazwę pakietu NuGet:</span><span class="sxs-lookup"><span data-stu-id="2827b-178">If you wish to install a template from a NuGet package stored at nuget.org, use the `dotnet new` command with the `-i|--install` option and supply the name of the NuGet package:</span></span>

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="2827b-179">Przykładem jest tylko w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="2827b-179">The example is for demonstration purposes only.</span></span> <span data-ttu-id="2827b-180">Nie ma `GarciaSoftware.ConsoleTemplate.CSharp` pakietu NuGet w nuget.org, i nie zaleca się można opublikować i korzystać z szablonów testu z NuGet.</span><span class="sxs-lookup"><span data-stu-id="2827b-180">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org, and we don't recommend that you publish and consume test templates from NuGet.</span></span> <span data-ttu-id="2827b-181">Jeśli polecenie zostanie uruchomione, jest zainstalowany żaden szablon.</span><span class="sxs-lookup"><span data-stu-id="2827b-181">If you run the command, no template is installed.</span></span> <span data-ttu-id="2827b-182">Można jednak zainstalować szablon, który nie został opublikowany nuget.org odwołując *nupkg* pliku bezpośrednio w lokalnym systemie plików, jak pokazano w poprzedniej sekcji [zainstalować szablon z lokalnym nupkg plik](#install-the-template-from-the-local-nupkg-file).</span><span class="sxs-lookup"><span data-stu-id="2827b-182">However, you can install a template that hasn't been published to nuget.org by referencing the *nupkg* file directly on your local file system as shown in the previous section [Install the template from the local nupkg file](#install-the-template-from-the-local-nupkg-file).</span></span>

<span data-ttu-id="2827b-183">Jeśli chcesz na żywo przykład sposobu instalowania szablonu z pakietu w nuget.org, możesz użyć [NUnit 3 szablon dla nowych dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span><span class="sxs-lookup"><span data-stu-id="2827b-183">If you'd like a live example of how to install a template from a package at nuget.org, you can use the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span></span> <span data-ttu-id="2827b-184">Ten szablon ustawia się na projekt do przeprowadzania testów jednostkowych NUnit użycia.</span><span class="sxs-lookup"><span data-stu-id="2827b-184">This template sets up a project to use NUnit unit testing.</span></span> <span data-ttu-id="2827b-185">Aby go zainstalować, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="2827b-185">Use the following command to install it:</span></span>

```console
dotnet new -i NUnit3.DotNetNew.Template
```

<span data-ttu-id="2827b-186">Podczas wyświetlania szablonów `dotnet new -l`, zostanie wyświetlony *projekt testowy 3 NUnit* z krótką nazwę *nunit* na liście szablonów.</span><span class="sxs-lookup"><span data-stu-id="2827b-186">When you list the templates with `dotnet new -l`, you see the *NUnit 3 Test Project* with a short name of *nunit* in the template list.</span></span> <span data-ttu-id="2827b-187">Możesz użyć szablonu w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="2827b-187">You're ready to use the template in the next section.</span></span>

![Wyświetlana NUnit szablonu na liście z innych szablonów zainstalowanych w oknie konsoli](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="2827b-189">Tworzenie projektu z szablonu</span><span class="sxs-lookup"><span data-stu-id="2827b-189">Create a project from the template</span></span>

<span data-ttu-id="2827b-190">Po zainstalowaniu szablonu z pakietu NuGet, należy użyć szablonu, wykonując `dotnet new <TEMPLATE>` umieścić wyjściowy polecenia z katalogu, w którym ma zostać aparatu szablonu (chyba że `-o|--output` opcję, aby określić określonego katalogu).</span><span class="sxs-lookup"><span data-stu-id="2827b-190">After the template is installed from NuGet, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="2827b-191">Aby uzyskać więcej informacji, zobacz [ `dotnet new` opcje](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="2827b-191">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="2827b-192">Podaj krótką nazwę szablonu bezpośrednio do `dotnet new` polecenia.</span><span class="sxs-lookup"><span data-stu-id="2827b-192">Supply the template's short name directly to the `dotnet new` command.</span></span> <span data-ttu-id="2827b-193">Aby utworzyć projekt z szablonu NUnit, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="2827b-193">To create a project from the NUnit template, run the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="2827b-194">Konsoli Pokazuje tworzenia projektu i przywracania pakietów projektu.</span><span class="sxs-lookup"><span data-stu-id="2827b-194">The console shows that the project is created and that the project's packages are restored.</span></span> <span data-ttu-id="2827b-195">Po uruchomieniu polecenia Projekt jest gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="2827b-195">After the command is run, the project is ready for use.</span></span>

![Okno konsoli wyświetlane dane wyjściowe polecenia Nowy dotnet tworzy projekt NUnit i przywraca zależności projektu](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="2827b-197">Aby odinstalować szablonu z pakietem NuGet przechowywane w nuget.org</span><span class="sxs-lookup"><span data-stu-id="2827b-197">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="2827b-198">Przykładem jest tylko w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="2827b-198">The example is for demonstration purposes only.</span></span> <span data-ttu-id="2827b-199">Nie ma `GarciaSoftware.ConsoleTemplate.CSharp` NuGet zainstalowany przy użyciu zestawu .NET Core SDK lub pakietu w nuget.org.</span><span class="sxs-lookup"><span data-stu-id="2827b-199">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org or installed with the .NET Core SDK.</span></span> <span data-ttu-id="2827b-200">Po uruchomieniu polecenia pakietu/szablonu zostanie odinstalowana i pojawi się następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2827b-200">If you run the command, no package/template is uninstalled and you receive the following exception:</span></span>
> 
> > <span data-ttu-id="2827b-201">Nie można znaleźć elementu odinstalować o nazwie "GarciaSoftware.ConsoleTemplate.CSharp".</span><span class="sxs-lookup"><span data-stu-id="2827b-201">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'.</span></span>

<span data-ttu-id="2827b-202">Jeśli zainstalowano [NUnit 3 szablon dla nowych dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) i chcesz go odinstalować, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="2827b-202">If you installed the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) and wish to uninstall it, use the following command:</span></span>

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a><span data-ttu-id="2827b-203">Odinstaluj szablonu z pliku lokalnego nupkg</span><span class="sxs-lookup"><span data-stu-id="2827b-203">Uninstall the template from a local nupkg file</span></span>

<span data-ttu-id="2827b-204">Jeśli chcesz odinstalować szablonu nie próbuj Użyj ścieżki do *nupkg* pliku.</span><span class="sxs-lookup"><span data-stu-id="2827b-204">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="2827b-205">*Podjęto próbę ją odinstalować przy użyciu szablonu `dotnet new -u <PATH_TO_NUPKG_FILE>` zakończy się niepowodzeniem.*</span><span class="sxs-lookup"><span data-stu-id="2827b-205">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="2827b-206">Odwołują się do pakietu przez jego `id`:</span><span class="sxs-lookup"><span data-stu-id="2827b-206">Reference the package by its `id`:</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a><span data-ttu-id="2827b-207">Użyj dystrybucji systemu plików</span><span class="sxs-lookup"><span data-stu-id="2827b-207">Use file system distribution</span></span>

<span data-ttu-id="2827b-208">Do dystrybucji szablonu, umieścić w folderze szablonów projektu w lokalizacji dostępne dla użytkowników w sieci.</span><span class="sxs-lookup"><span data-stu-id="2827b-208">To distribute the template, place the project template folder in a location accessible to users on your network.</span></span> <span data-ttu-id="2827b-209">Użyj `dotnet new` z `-i|--install` opcji i określ ścieżkę do folderu szablonu (folder projekt zawierający projekt i *. template.config* folderu).</span><span class="sxs-lookup"><span data-stu-id="2827b-209">Use the `dotnet new` command with the `-i|--install` option and specify the path to the template folder (the project folder containing the project and the *.template.config* folder).</span></span>

<span data-ttu-id="2827b-210">W tym samouczku założono szablon projektu jest przechowywany w *dokumenty/szablonów* folderu profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2827b-210">The tutorial assumes the project template is stored in the *Documents/Templates* folder of the user's profile.</span></span> <span data-ttu-id="2827b-211">Z tej lokalizacji, należy zainstalować szablon z zastąpienia następujące polecenia \<użytkownika > o nazwie profilu użytkownika:</span><span class="sxs-lookup"><span data-stu-id="2827b-211">From that location, install the template with the following command replacing \<USER> with the user's profile name:</span></span>

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="2827b-212">Tworzenie projektu z szablonu</span><span class="sxs-lookup"><span data-stu-id="2827b-212">Create a project from the template</span></span>

<span data-ttu-id="2827b-213">Po zainstalowaniu szablonu z systemu plików za pomocą szablonu, wykonując `dotnet new <TEMPLATE>` umieścić wyjściowy polecenia z katalogu, w którym ma zostać aparatu szablonu (chyba że `-o|--output` opcję, aby określić określonego katalogu).</span><span class="sxs-lookup"><span data-stu-id="2827b-213">After the template is installed from the file system, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="2827b-214">Aby uzyskać więcej informacji, zobacz [ `dotnet new` opcje](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="2827b-214">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="2827b-215">Podaj krótką nazwę szablonu bezpośrednio do `dotnet new` polecenia.</span><span class="sxs-lookup"><span data-stu-id="2827b-215">Supply the template's short name directly to the `dotnet new` command.</span></span>

<span data-ttu-id="2827b-216">Z folderu projektu utworzonego w dniu *C:\Users\\\<użytkownika > \Documents\Projects\MyConsoleApp*, Utwórz projekt z `garciaconsole` szablonu:</span><span class="sxs-lookup"><span data-stu-id="2827b-216">From a new project folder created at *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, create a project from the `garciaconsole` template:</span></span>

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a><span data-ttu-id="2827b-217">Odinstaluj szablonu</span><span class="sxs-lookup"><span data-stu-id="2827b-217">Uninstall the template</span></span>

<span data-ttu-id="2827b-218">Jeśli szablon został utworzony w lokalnym systemie plików w *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, odinstaluj je z `-u|--uninstall` przełącznika i ścieżki folder szablonu:</span><span class="sxs-lookup"><span data-stu-id="2827b-218">If you created the template on your local file system at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, uninstall it with the `-u|--uninstall` switch and the path to the template folder:</span></span>

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="2827b-219">Aby odinstalować szablonu z lokalnego systemu plików, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2827b-219">To uninstall the template from your local file system, you need to fully qualify the path.</span></span> <span data-ttu-id="2827b-220">Na przykład *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie.</span><span class="sxs-lookup"><span data-stu-id="2827b-220">For example, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="2827b-221">Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.</span><span class="sxs-lookup"><span data-stu-id="2827b-221">Additionally, do not include a final terminating directory slash on your template path.</span></span>

## <a name="see-also"></a><span data-ttu-id="2827b-222">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2827b-222">See also</span></span>

[<span data-ttu-id="2827b-223">repozytorium GitHub DotNet/tworzenia szablonów Wiki</span><span class="sxs-lookup"><span data-stu-id="2827b-223">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)  
[<span data-ttu-id="2827b-224">repozytorium GitHub DotNet/dotnet szablonu — przykłady</span><span class="sxs-lookup"><span data-stu-id="2827b-224">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="2827b-225">Jak utworzyć nowe szablony dla platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="2827b-225">How to create your own templates for dotnet new</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[<span data-ttu-id="2827b-226">*Template.JSON* schematu w magazynie schematów JSON</span><span class="sxs-lookup"><span data-stu-id="2827b-226">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)  
