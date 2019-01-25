---
title: Utwórz nowy szablon niestandardowy dla platformy dotnet
description: Dowiedz się, jak utworzyć niestandardowy szablon dla nowego polecenia dotnet w tę zabawną samouczka.
author: guardrex
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: 72cafab774187cf8c59b2a00d8adcc5028974c88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714061"
---
# <a name="create-a-custom-template-for-dotnet-new"></a><span data-ttu-id="f8125-103">Utwórz nowy szablon niestandardowy dla platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="f8125-103">Create a custom template for dotnet new</span></span>

<span data-ttu-id="f8125-104">Ten samouczek pokazuje, jak do:</span><span class="sxs-lookup"><span data-stu-id="f8125-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="f8125-105">Utwórz szablon podstawowy z istniejący projekt lub nowy projekt aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="f8125-105">Create a basic template from an existing project or a new console app project.</span></span>
- <span data-ttu-id="f8125-106">Pakiet szablonu do dystrybucji, w witrynie nuget.org lub z lokalnym *nupkg* pliku.</span><span class="sxs-lookup"><span data-stu-id="f8125-106">Pack the template for distribution at nuget.org or from a local *nupkg* file.</span></span>
- <span data-ttu-id="f8125-107">Zainstalować szablon z witryny nuget.org-lokalnego *nupkg* pliku lub w lokalnym systemie plików.</span><span class="sxs-lookup"><span data-stu-id="f8125-107">Install the template from nuget.org, a local *nupkg* file, or the local file system.</span></span>
- <span data-ttu-id="f8125-108">Odinstaluj szablonu.</span><span class="sxs-lookup"><span data-stu-id="f8125-108">Uninstall the template.</span></span>

<span data-ttu-id="f8125-109">Jeśli wolisz postępuj zgodnie z instrukcjami samouczek z pełny przykład, Pobierz [przykładowy szablon projektu](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span><span class="sxs-lookup"><span data-stu-id="f8125-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample project template](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span></span> <span data-ttu-id="f8125-110">Przykładowy szablon jest skonfigurowany do dystrybucji NuGet.</span><span class="sxs-lookup"><span data-stu-id="f8125-110">The sample template is configured for NuGet distribution.</span></span>

<span data-ttu-id="f8125-111">Jeśli chcesz korzystać z pobranych próbki z dystrybucją systemu plików, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f8125-111">If you wish to use the downloaded sample with file system distribution, do the following:</span></span>

- <span data-ttu-id="f8125-112">Przenieś zawartość *zawartości* folderu próbki do góry o jeden poziom do *GarciaSoftware.ConsoleTemplate.CSharp* folderu.</span><span class="sxs-lookup"><span data-stu-id="f8125-112">Move the contents of the *content* folder of the sample up one level into the *GarciaSoftware.ConsoleTemplate.CSharp* folder.</span></span>
- <span data-ttu-id="f8125-113">Usuwanie pustych *zawartości* folderu.</span><span class="sxs-lookup"><span data-stu-id="f8125-113">Delete the empty *content* folder.</span></span>
- <span data-ttu-id="f8125-114">Usuń *nuspec* pliku.</span><span class="sxs-lookup"><span data-stu-id="f8125-114">Delete the *nuspec* file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f8125-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f8125-115">Prerequisites</span></span>

- <span data-ttu-id="f8125-116">Zainstaluj [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="f8125-116">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
- <span data-ttu-id="f8125-117">Zapoznaj się z tematem odwołanie [szablonów niestandardowych dla platformy dotnet nowe](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="f8125-117">Read the reference topic [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

## <a name="create-a-template-from-a-project"></a><span data-ttu-id="f8125-118">Utwórz szablon z projektu</span><span class="sxs-lookup"><span data-stu-id="f8125-118">Create a template from a project</span></span>

<span data-ttu-id="f8125-119">Użyj istniejącego projektu, który został potwierdzony kompiluje i uruchamia lub utworzyć nowy projekt aplikacji konsoli w folderze na dysku twardym.</span><span class="sxs-lookup"><span data-stu-id="f8125-119">Use an existing project that you've confirmed compiles and runs, or create a new console app project in a folder on your hard drive.</span></span> <span data-ttu-id="f8125-120">Ten samouczek zakłada, że nazwa folderu projektu jest *GarciaSoftware.ConsoleTemplate.CSharp* przechowywaną w *Documents\Templates* w profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f8125-120">This tutorial assumes that the name of the project folder is *GarciaSoftware.ConsoleTemplate.CSharp* stored at *Documents\Templates* in the user's profile.</span></span> <span data-ttu-id="f8125-121">Nazwa szablonu w projekcie samouczka jest w formacie  *\<nazwa firmy >.\< Typ szablonu >. \<Język programowania >*, ale możesz nazwę projektu i szablon wszystko chcesz.</span><span class="sxs-lookup"><span data-stu-id="f8125-121">The tutorial project template name is in the format *\<Company Name>.\<Template Type>.\<Programming Language>*, but you're free to name your project and template anything you wish.</span></span>

1. <span data-ttu-id="f8125-122">Dodawanie folderu do katalogu głównego projektu o nazwie *. template.config*.</span><span class="sxs-lookup"><span data-stu-id="f8125-122">Add a folder to the root of the project named *.template.config*.</span></span>
1. <span data-ttu-id="f8125-123">Wewnątrz *. template.config* folderze utwórz *template.json* pliku, aby skonfigurować szablon.</span><span class="sxs-lookup"><span data-stu-id="f8125-123">Inside the *.template.config* folder, create a *template.json* file to configure your template.</span></span> <span data-ttu-id="f8125-124">Aby uzyskać więcej informacji i elementów członkowskich definicje *template.json* plików, zobacz [szablonów niestandardowych dla platformy dotnet nowe](../tools/custom-templates.md#templatejson) tematu i [ *template.json* schemat w Store schematu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="f8125-124">For more information and member definitions for the *template.json* file, see the [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) topic and the [*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template).</span></span>

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

<span data-ttu-id="f8125-125">Szablon jest ukończona.</span><span class="sxs-lookup"><span data-stu-id="f8125-125">The template is finished.</span></span> <span data-ttu-id="f8125-126">W tym momencie masz dwie opcje dystrybucji szablonu.</span><span class="sxs-lookup"><span data-stu-id="f8125-126">At this point, you have two options for template distribution.</span></span> <span data-ttu-id="f8125-127">Aby kontynuować z tego samouczka, wybierz jedną ścieżkę lub innych:</span><span class="sxs-lookup"><span data-stu-id="f8125-127">To continue this tutorial, choose one path or the other:</span></span>

1. <span data-ttu-id="f8125-128">[NuGet dystrybucji](#use-nuget-distribution): Zainstaluj szablonu z pakietów NuGet lub z lokalnego *nupkg* i użycie zainstalowanych szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8125-128">[NuGet distribution](#use-nuget-distribution): install the template from NuGet or from the local *nupkg* file, and use the installed template.</span></span>
2. <span data-ttu-id="f8125-129">[Plik dystrybucji systemu](#use-file-system-distribution).</span><span class="sxs-lookup"><span data-stu-id="f8125-129">[File system distribution](#use-file-system-distribution).</span></span>

## <a name="use-nuget-distribution"></a><span data-ttu-id="f8125-130">Użyj rozkładu NuGet</span><span class="sxs-lookup"><span data-stu-id="f8125-130">Use NuGet Distribution</span></span>

### <a name="pack-the-template-into-a-nuget-package"></a><span data-ttu-id="f8125-131">Pakiet szablonu do pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="f8125-131">Pack the template into a NuGet package</span></span>

1. <span data-ttu-id="f8125-132">Utwórz folder dla pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="f8125-132">Create a folder for the NuGet package.</span></span> <span data-ttu-id="f8125-133">Samouczek, nazwa folderu *GarciaSoftware.ConsoleTemplate.CSharp* jest używany, oraz folder jest tworzony w *Documents\NuGetTemplates* folderu w profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f8125-133">For the tutorial, the folder name *GarciaSoftware.ConsoleTemplate.CSharp* is used, and the folder is created inside a *Documents\NuGetTemplates* folder in the user's profile.</span></span> <span data-ttu-id="f8125-134">Utwórz folder o nazwie *zawartości* wewnątrz folder szablonów do przechowywania plików projektu.</span><span class="sxs-lookup"><span data-stu-id="f8125-134">Create a folder named *content* inside of the new template folder to hold the project files.</span></span>
1. <span data-ttu-id="f8125-135">Skopiuj zawartość do folderu projektu, łącznie z jej *.template.config/template.json* pliku do *zawartości* utworzony folder.</span><span class="sxs-lookup"><span data-stu-id="f8125-135">Copy the contents of your project folder, together with its *.template.config/template.json* file, into the *content* folder you created.</span></span>
1. <span data-ttu-id="f8125-136">Obok pozycji *zawartości* folderu, Dodaj [ *nuspec* pliku](/nuget/create-packages/creating-a-package).</span><span class="sxs-lookup"><span data-stu-id="f8125-136">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package).</span></span> <span data-ttu-id="f8125-137">Soubor nuspec jest plik manifestu XML, który opisuje zawartość pakietu i dyski proces tworzenia pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="f8125-137">The nuspec file is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span>

   ![Struktura katalogów przedstawiający układ pakietu NuGet](./media/create-custom-template/nuget-directory-layout.png)

1. <span data-ttu-id="f8125-139">Wewnątrz  **\<packageTypes >** element *nuspec* plików, obejmują  **\<packageType >** element z `name` wartość atrybutu `Template`.</span><span class="sxs-lookup"><span data-stu-id="f8125-139">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="f8125-140">Zarówno *zawartości* folder i *nuspec* plik powinien znajdować się w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f8125-140">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="f8125-141">W tabeli przedstawiono minimalne *nuspec* pliku elementów wymaganych do utworzenia szablonu jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="f8125-141">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

   | <span data-ttu-id="f8125-142">Element</span><span class="sxs-lookup"><span data-stu-id="f8125-142">Element</span></span>            | <span data-ttu-id="f8125-143">Typ</span><span class="sxs-lookup"><span data-stu-id="f8125-143">Type</span></span>   | <span data-ttu-id="f8125-144">Opis</span><span class="sxs-lookup"><span data-stu-id="f8125-144">Description</span></span> |
   | ------------------ | ------ | ----------- |
   | <span data-ttu-id="f8125-145">**\<authors>**</span><span class="sxs-lookup"><span data-stu-id="f8125-145">**\<authors>**</span></span>     | <span data-ttu-id="f8125-146">string</span><span class="sxs-lookup"><span data-stu-id="f8125-146">string</span></span> | <span data-ttu-id="f8125-147">Rozdzielana przecinkami lista autorów pakietów, pasujące nazwy profilu w witrynie nuget.org. Autorzy są wyświetlane w galerii pakietów NuGet w witrynie nuget.org i są odwoływania się do pakietów przez ten sam autorów.</span><span class="sxs-lookup"><span data-stu-id="f8125-147">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
   | <span data-ttu-id="f8125-148">**\<description>**</span><span class="sxs-lookup"><span data-stu-id="f8125-148">**\<description>**</span></span> | <span data-ttu-id="f8125-149">string</span><span class="sxs-lookup"><span data-stu-id="f8125-149">string</span></span> | <span data-ttu-id="f8125-150">Długi opis pakietu do wyświetlania w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f8125-150">A long description of the package for UI display.</span></span> |
   | <span data-ttu-id="f8125-151">**\<id>**</span><span class="sxs-lookup"><span data-stu-id="f8125-151">**\<id>**</span></span>          | <span data-ttu-id="f8125-152">string</span><span class="sxs-lookup"><span data-stu-id="f8125-152">string</span></span> | <span data-ttu-id="f8125-153">Identyfikator pakietu bez uwzględniania wielkości liter, który musi być unikatowa w witrynie nuget.org lub cokolwiek innego pakietu będą znajdować się w galerii.</span><span class="sxs-lookup"><span data-stu-id="f8125-153">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="f8125-154">Identyfikatory nie może zawierać spacji ani znaków, które nie są prawidłowe dla danego adresu URL i zazwyczaj korzystają z reguły w przestrzeni nazw .NET.</span><span class="sxs-lookup"><span data-stu-id="f8125-154">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="f8125-155">Zobacz [wybierając identyfikator unikatowy pakiet i ustawiania numeru wersji](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) wskazówki.</span><span class="sxs-lookup"><span data-stu-id="f8125-155">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
   | <span data-ttu-id="f8125-156">**\<packageType>**</span><span class="sxs-lookup"><span data-stu-id="f8125-156">**\<packageType>**</span></span> | <span data-ttu-id="f8125-157">string</span><span class="sxs-lookup"><span data-stu-id="f8125-157">string</span></span> | <span data-ttu-id="f8125-158">Umieść ten element wewnątrz  **\<packageTypes >** element między  **\<metadanych >** elementów.</span><span class="sxs-lookup"><span data-stu-id="f8125-158">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="f8125-159">Ustaw `name` atrybutu  **\<packageType >** elementu `Template`.</span><span class="sxs-lookup"><span data-stu-id="f8125-159">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
   | <span data-ttu-id="f8125-160">**\<version>**</span><span class="sxs-lookup"><span data-stu-id="f8125-160">**\<version>**</span></span>     | <span data-ttu-id="f8125-161">string</span><span class="sxs-lookup"><span data-stu-id="f8125-161">string</span></span> | <span data-ttu-id="f8125-162">Wersja pakietu, następujące Wersja_główna.WERSJA_POMOCNICZA.poprawka.</span><span class="sxs-lookup"><span data-stu-id="f8125-162">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="f8125-163">Numery wersji mogą zawierać sufiks wersji wstępnej, zgodnie z opisem w [wersje wstępne](/nuget/create-packages/prerelease-packages#semantic-versioning).</span><span class="sxs-lookup"><span data-stu-id="f8125-163">Version numbers may include a pre-release suffix as described in [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span></span> |

   <span data-ttu-id="f8125-164">Zobacz [odwołania .nuspec](/nuget/schema/nuspec) dla pełnego *nuspec* pliku schematu.</span><span class="sxs-lookup"><span data-stu-id="f8125-164">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span>

   <span data-ttu-id="f8125-165">*Nuspec* plik o nazwie samouczka *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* i zawiera następujące treści:</span><span class="sxs-lookup"><span data-stu-id="f8125-165">The *nuspec* file for the tutorial is named *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* and contains the following content:</span></span>

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

1. <span data-ttu-id="f8125-166">[Utwórz pakiet](/nuget/create-packages/creating-a-package#creating-the-package) przy użyciu `nuget pack <PATH_TO_NUSPEC_FILE>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8125-166">[Create the package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span> <span data-ttu-id="f8125-167">Poniższego polecenia założono, że folder, który zawiera zasoby NuGet jest na *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span><span class="sxs-lookup"><span data-stu-id="f8125-167">The following command assumes that the folder that holds the NuGet assets is at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span></span> <span data-ttu-id="f8125-168">Jednak wszędzie tam, gdzie umieścić folder, w tym systemie `nuget pack` polecenie akceptuje ścieżkę do *nuspec* pliku:</span><span class="sxs-lookup"><span data-stu-id="f8125-168">But wherever you place the folder on your system, the `nuget pack` command accepts the path to the *nuspec* file:</span></span>

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a><span data-ttu-id="f8125-169">Publikowanie pakietu na stronie nuget.org</span><span class="sxs-lookup"><span data-stu-id="f8125-169">Publishing the package to nuget.org</span></span>

<span data-ttu-id="f8125-170">Aby opublikować pakiet NuGet, postępuj zgodnie z instrukcjami [tworzenie i publikowanie pakietu](/nuget/quickstart/create-and-publish-a-package#publish-the-package) tematu.</span><span class="sxs-lookup"><span data-stu-id="f8125-170">To publish a NuGet package, follow the instructions in the [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) topic.</span></span> <span data-ttu-id="f8125-171">Firma Microsoft zaleca jednak nie opublikowanie szablonu samouczek NuGet jako nigdy nie można usunąć go po opublikowaniu tylko delisted.</span><span class="sxs-lookup"><span data-stu-id="f8125-171">However, we recommend that you don't publish the tutorial template to NuGet as it can never be deleted once published, only delisted.</span></span> <span data-ttu-id="f8125-172">Teraz, gdy pakiet NuGet w formie *nupkg* plików, zalecamy postępuj zgodnie z poniższymi instrukcjami, aby zainstalować szablon bezpośrednio z poziomu lokalnej *nupkg* pliku.</span><span class="sxs-lookup"><span data-stu-id="f8125-172">Now that you have the NuGet package in the form of a *nupkg* file, we suggest that you follow the instructions below to install the template directly from the local *nupkg* file.</span></span>

### <a name="install-the-template-from-a-nuget-package"></a><span data-ttu-id="f8125-173">Zainstaluj szablonu z pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="f8125-173">Install the template from a NuGet package</span></span>

#### <a name="install-the-template-from-the-local-nupkg-file"></a><span data-ttu-id="f8125-174">Zainstaluj szablonu z lokalnego *nupkg* pliku</span><span class="sxs-lookup"><span data-stu-id="f8125-174">Install the template from the local *nupkg* file</span></span>

<span data-ttu-id="f8125-175">Aby zainstalować szablonu z *nupkg* pliku wytworzonego, użyj `dotnet new` polecenia `-i|--install` opcji i podaj ścieżkę do *nupkg* pliku:</span><span class="sxs-lookup"><span data-stu-id="f8125-175">To install the template from the *nupkg* file that you produced, use the `dotnet new` command with the `-i|--install` option and provide the path to the *nupkg* file:</span></span>

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="f8125-176">Zainstaluj szablonu z pakietu NuGet, przechowywane w witrynie nuget.org</span><span class="sxs-lookup"><span data-stu-id="f8125-176">Install the template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="f8125-177">Jeśli chcesz zainstalować szablonu z przechowywaną w witrynie nuget.org, użyj pakietu NuGet `dotnet new` polecenia `-i|--install` opcji, a następnie podaj nazwę pakietu NuGet:</span><span class="sxs-lookup"><span data-stu-id="f8125-177">If you wish to install a template from a NuGet package stored at nuget.org, use the `dotnet new` command with the `-i|--install` option and supply the name of the NuGet package:</span></span>

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="f8125-178">W przykładzie występuje tylko w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f8125-178">The example is for demonstration purposes only.</span></span> <span data-ttu-id="f8125-179">Nie ma `GarciaSoftware.ConsoleTemplate.CSharp` pakietu NuGet w witrynie nuget.org, a firma Microsoft nie jest zalecane, możesz publikować i korzystanie z szablonów testowych z pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="f8125-179">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org, and we don't recommend that you publish and consume test templates from NuGet.</span></span> <span data-ttu-id="f8125-180">Jeśli zostanie uruchomione polecenie szablon nie jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="f8125-180">If you run the command, no template is installed.</span></span> <span data-ttu-id="f8125-181">Można jednak zainstalować szablon, który nie został opublikowany na stronie nuget.org, odwołując się do *nupkg* plików bezpośrednio w lokalnym systemie plików, jak pokazano w poprzedniej sekcji [zainstalować szablon z lokalnym nupkg plik](#install-the-template-from-the-local-nupkg-file).</span><span class="sxs-lookup"><span data-stu-id="f8125-181">However, you can install a template that hasn't been published to nuget.org by referencing the *nupkg* file directly on your local file system as shown in the previous section [Install the template from the local nupkg file](#install-the-template-from-the-local-nupkg-file).</span></span>

<span data-ttu-id="f8125-182">Jeśli chcesz na żywo przykładem sposobu instalowania szablonu z pakietu w witrynie nuget.org, możesz użyć [szablon NUnit 3-dotnet new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span><span class="sxs-lookup"><span data-stu-id="f8125-182">If you'd like a live example of how to install a template from a package at nuget.org, you can use the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span></span> <span data-ttu-id="f8125-183">Ten szablon konfiguruje projektu, aby użyć testów jednostkowych NUnit.</span><span class="sxs-lookup"><span data-stu-id="f8125-183">This template sets up a project to use NUnit unit testing.</span></span> <span data-ttu-id="f8125-184">Aby go zainstalować, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="f8125-184">Use the following command to install it:</span></span>

```console
dotnet new -i NUnit3.DotNetNew.Template
```

<span data-ttu-id="f8125-185">Po wyświetleniu listy szablonów za pomocą `dotnet new -l`, zostanie wyświetlony *NUnit 3 Test projekt* nazwą krótkim *nunit* na liście szablonów.</span><span class="sxs-lookup"><span data-stu-id="f8125-185">When you list the templates with `dotnet new -l`, you see the *NUnit 3 Test Project* with a short name of *nunit* in the template list.</span></span> <span data-ttu-id="f8125-186">Możesz użyć szablonu w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f8125-186">You're ready to use the template in the next section.</span></span>

![Okno konsoli przedstawiający szablon NUnit z innych szablonów](./media/create-custom-template/nunit-template-console-window.png)

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="f8125-188">Tworzenie projektu z szablonu</span><span class="sxs-lookup"><span data-stu-id="f8125-188">Create a project from the template</span></span>

<span data-ttu-id="f8125-189">Po zainstalowaniu szablonu z pakietów NuGet, należy użyć szablonu, wykonując `dotnet new <TEMPLATE>` polecenie z katalogu, w którym chcesz aparatu szablonów danych wyjściowych umieszczone (chyba że `-o|--output` opcję, aby określić określonego katalogu).</span><span class="sxs-lookup"><span data-stu-id="f8125-189">After the template is installed from NuGet, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="f8125-190">Aby uzyskać więcej informacji, zobacz [ `dotnet new` opcje](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="f8125-190">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="f8125-191">Podaj krótką nazwę szablonu bezpośrednio do `dotnet new` polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8125-191">Supply the template's short name directly to the `dotnet new` command.</span></span> <span data-ttu-id="f8125-192">Aby utworzyć projekt z szablonu NUnit, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f8125-192">To create a project from the NUnit template, run the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="f8125-193">Konsolę pokazuje, że projekt zostanie utworzony i czy projektu pakiety zostaną przywrócone.</span><span class="sxs-lookup"><span data-stu-id="f8125-193">The console shows that the project is created and that the project's packages are restored.</span></span> <span data-ttu-id="f8125-194">Po uruchomieniu polecenia Projekt jest gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="f8125-194">After the command is run, the project is ready for use.</span></span>

![Oknie konsoli zostaną wyświetlone dane wyjściowe nunit nowe dotnet, w tym Przywracanie zależności projektu](./media/create-custom-template/dotnet-new-nunit-console-output.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="f8125-196">Aby odinstalować szablonu z pakietu NuGet, przechowywane w witrynie nuget.org</span><span class="sxs-lookup"><span data-stu-id="f8125-196">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="f8125-197">W przykładzie występuje tylko w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f8125-197">The example is for demonstration purposes only.</span></span> <span data-ttu-id="f8125-198">Nie ma `GarciaSoftware.ConsoleTemplate.CSharp` NuGet zainstalowany przy użyciu zestawu .NET Core SDK lub pakietu w witrynie nuget.org.</span><span class="sxs-lookup"><span data-stu-id="f8125-198">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org or installed with the .NET Core SDK.</span></span> <span data-ttu-id="f8125-199">Jeśli zostanie uruchomione polecenie pakietu/szablon nie zostanie odinstalowany i pojawi się następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="f8125-199">If you run the command, no package/template is uninstalled and you receive the following exception:</span></span>
>
> > <span data-ttu-id="f8125-200">Nie można odnaleźć coś do odinstalowania o nazwie "GarciaSoftware.ConsoleTemplate.CSharp".</span><span class="sxs-lookup"><span data-stu-id="f8125-200">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'.</span></span>

<span data-ttu-id="f8125-201">Po zainstalowaniu [NUnit 3 szablon dla nowych dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) i chcesz je odinstalować, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="f8125-201">If you installed the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) and wish to uninstall it, use the following command:</span></span>

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a><span data-ttu-id="f8125-202">Odinstaluj szablonu z pliku lokalnego nupkg</span><span class="sxs-lookup"><span data-stu-id="f8125-202">Uninstall the template from a local nupkg file</span></span>

<span data-ttu-id="f8125-203">Jeśli chcesz odinstalować szablonu nie próbują użyć ścieżki do *nupkg* pliku.</span><span class="sxs-lookup"><span data-stu-id="f8125-203">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="f8125-204">*Podjęto próbę ją odinstalować przy użyciu szablonu `dotnet new -u <PATH_TO_NUPKG_FILE>` zakończy się niepowodzeniem.*</span><span class="sxs-lookup"><span data-stu-id="f8125-204">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="f8125-205">Odwołują się do pakietu, jego `id`:</span><span class="sxs-lookup"><span data-stu-id="f8125-205">Reference the package by its `id`:</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a><span data-ttu-id="f8125-206">Użyj dystrybucji systemu plików</span><span class="sxs-lookup"><span data-stu-id="f8125-206">Use file system distribution</span></span>

<span data-ttu-id="f8125-207">Aby dystrybuować szablonu, umieść folderu szablonu projektu w lokalizacji dostępne dla użytkowników w sieci.</span><span class="sxs-lookup"><span data-stu-id="f8125-207">To distribute the template, place the project template folder in a location accessible to users on your network.</span></span> <span data-ttu-id="f8125-208">Użyj `dotnet new` polecenia `-i|--install` opcji, a następnie określ ścieżkę do folderu szablonu (folder projektu, zawierający projekt i *. template.config* folder).</span><span class="sxs-lookup"><span data-stu-id="f8125-208">Use the `dotnet new` command with the `-i|--install` option and specify the path to the template folder (the project folder containing the project and the *.template.config* folder).</span></span>

<span data-ttu-id="f8125-209">W samouczku przyjęto założenie, szablon projektu jest przechowywany w *dokumenty/szablonów* folderu profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f8125-209">The tutorial assumes the project template is stored in the *Documents/Templates* folder of the user's profile.</span></span> <span data-ttu-id="f8125-210">Z tej lokalizacji, należy zainstalować szablon przy użyciu polecenia następujących, zastępując \<użytkownika > o nazwie profilu użytkownika:</span><span class="sxs-lookup"><span data-stu-id="f8125-210">From that location, install the template with the following command replacing \<USER> with the user's profile name:</span></span>

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="f8125-211">Tworzenie projektu z szablonu</span><span class="sxs-lookup"><span data-stu-id="f8125-211">Create a project from the template</span></span>

<span data-ttu-id="f8125-212">Po zainstalowaniu szablonu z systemu plików, należy użyć szablonu, wykonując `dotnet new <TEMPLATE>` polecenie z katalogu, w którym chcesz aparatu szablonów danych wyjściowych umieszczone (chyba że `-o|--output` opcję, aby określić określonego katalogu).</span><span class="sxs-lookup"><span data-stu-id="f8125-212">After the template is installed from the file system, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="f8125-213">Aby uzyskać więcej informacji, zobacz [ `dotnet new` opcje](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="f8125-213">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="f8125-214">Podaj krótką nazwę szablonu bezpośrednio do `dotnet new` polecenia.</span><span class="sxs-lookup"><span data-stu-id="f8125-214">Supply the template's short name directly to the `dotnet new` command.</span></span>

<span data-ttu-id="f8125-215">Z folderu projektu utworzono *C:\Users\\\<użytkownika > \Documents\Projects\MyConsoleApp*, Utwórz projekt z `garciaconsole` szablonu:</span><span class="sxs-lookup"><span data-stu-id="f8125-215">From a new project folder created at *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, create a project from the `garciaconsole` template:</span></span>

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a><span data-ttu-id="f8125-216">Odinstaluj szablonu</span><span class="sxs-lookup"><span data-stu-id="f8125-216">Uninstall the template</span></span>

<span data-ttu-id="f8125-217">Jeśli szablon został utworzony w lokalnym systemie plików w *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, odinstaluj je za pomocą `-u|--uninstall` przełącznika i ścieżki do folderu szablonu:</span><span class="sxs-lookup"><span data-stu-id="f8125-217">If you created the template on your local file system at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, uninstall it with the `-u|--uninstall` switch and the path to the template folder:</span></span>

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="f8125-218">Aby odinstalować szablonu z lokalnego systemu plików, należy do pełnej kwalifikacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f8125-218">To uninstall the template from your local file system, you need to fully qualify the path.</span></span> <span data-ttu-id="f8125-219">Na przykład *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie.</span><span class="sxs-lookup"><span data-stu-id="f8125-219">For example, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="f8125-220">Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.</span><span class="sxs-lookup"><span data-stu-id="f8125-220">Additionally, do not include a final terminating directory slash on your template path.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8125-221">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8125-221">See also</span></span>

- [<span data-ttu-id="f8125-222">repozytorium GitHub DotNet/szablonów witryny typu Wiki</span><span class="sxs-lookup"><span data-stu-id="f8125-222">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="f8125-223">repozytorium GitHub DotNet/dotnet-— przykłady szablonów</span><span class="sxs-lookup"><span data-stu-id="f8125-223">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="f8125-224">Jak utworzyć nowe szablony dla platformy dotnet</span><span class="sxs-lookup"><span data-stu-id="f8125-224">How to create your own templates for dotnet new</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="f8125-225">*Template.JSON* schemat w Store schematu JSON</span><span class="sxs-lookup"><span data-stu-id="f8125-225">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
