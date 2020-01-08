---
title: Utwórz szablon elementu dla nowego interfejs wiersza polecenia platformy .NET Core dotnet
description: Dowiedz się, jak utworzyć szablon elementu dla nowego polecenia dotnet. Szablony elementów mogą zawierać dowolną liczbę plików.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: fa0ae18221c33d196960239411f8860a561b20ee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340373"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="d193b-104">Samouczek: Tworzenie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="d193b-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="d193b-105">Za pomocą platformy .NET Core można tworzyć i wdrażać szablony generujące projekty, pliki, nawet zasoby.</span><span class="sxs-lookup"><span data-stu-id="d193b-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="d193b-106">Ten samouczek jest częścią jednej z serii, która uczy się, jak tworzyć, instalować i odinstalowywać szablony do użycia z poleceniem `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="d193b-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="d193b-107">W tej części serii dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="d193b-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d193b-108">Tworzenie klasy dla szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="d193b-108">Create a class for an item template</span></span>
> * <span data-ttu-id="d193b-109">Tworzenie folderu i pliku konfiguracji szablonu</span><span class="sxs-lookup"><span data-stu-id="d193b-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="d193b-110">Instalowanie szablonu ze ścieżki pliku</span><span class="sxs-lookup"><span data-stu-id="d193b-110">Install a template from a file path</span></span>
> * <span data-ttu-id="d193b-111">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="d193b-111">Test an item template</span></span>
> * <span data-ttu-id="d193b-112">Odinstaluj szablon elementu</span><span class="sxs-lookup"><span data-stu-id="d193b-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d193b-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d193b-113">Prerequisites</span></span>

* <span data-ttu-id="d193b-114">[Zestaw .NET Core 2,2 SDK](https://dotnet.microsoft.com/download) lub jego nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="d193b-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
* <span data-ttu-id="d193b-115">Przeczytaj artykuł referencyjny [Szablony niestandardowe dla usługi dotnet New](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="d193b-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="d193b-116">W artykule referencyjnym objaśniono podstawowe informacje dotyczące szablonów i sposobu ich umieszczania.</span><span class="sxs-lookup"><span data-stu-id="d193b-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="d193b-117">Niektóre z tych informacji zostaną ponownie powtórzone w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="d193b-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="d193b-118">Otwórz Terminal i przejdź do folderu _working\templates_ .</span><span class="sxs-lookup"><span data-stu-id="d193b-118">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="d193b-119">Tworzenie wymaganych folderów</span><span class="sxs-lookup"><span data-stu-id="d193b-119">Create the required folders</span></span>

<span data-ttu-id="d193b-120">Ta seria używa "folderu roboczego", w którym znajduje się źródło szablonu, oraz "folderu testowego" używanego do testowania szablonów.</span><span class="sxs-lookup"><span data-stu-id="d193b-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="d193b-121">Folder roboczy i folder testowania powinny znajdować się w tym samym folderze nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="d193b-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="d193b-122">Najpierw utwórz folder nadrzędny, a nazwa nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="d193b-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="d193b-123">Następnie utwórz podfolder o nazwie _Work_.</span><span class="sxs-lookup"><span data-stu-id="d193b-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="d193b-124">W folderze _roboczym_ utwórz podfolder o nazwie _templates_.</span><span class="sxs-lookup"><span data-stu-id="d193b-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="d193b-125">Następnie utwórz folder w folderze nadrzędnym o nazwie _test_.</span><span class="sxs-lookup"><span data-stu-id="d193b-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="d193b-126">Struktura folderów powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d193b-126">The folder structure should look like the following:</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="d193b-127">Utwórz szablon elementu</span><span class="sxs-lookup"><span data-stu-id="d193b-127">Create an item template</span></span>

<span data-ttu-id="d193b-128">Szablon elementu jest określonym typem szablonu, który zawiera jeden lub więcej plików.</span><span class="sxs-lookup"><span data-stu-id="d193b-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="d193b-129">Te typy szablonów są przydatne, gdy chcesz wygenerować coś takiego jak konfiguracja, kod lub plik rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d193b-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="d193b-130">W tym przykładzie utworzysz klasę, która dodaje metodę rozszerzenia do typu ciągu.</span><span class="sxs-lookup"><span data-stu-id="d193b-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="d193b-131">W terminalu przejdź do folderu _working\templates_ i Utwórz nowy podfolder o nazwie _extensionss_.</span><span class="sxs-lookup"><span data-stu-id="d193b-131">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="d193b-132">Wprowadź folder.</span><span class="sxs-lookup"><span data-stu-id="d193b-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="d193b-133">Utwórz nowy plik o nazwie _CommonExtensions.cs_ i otwórz go za pomocą ulubionego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="d193b-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="d193b-134">Ta klasa zapewni metodę rozszerzenia o nazwie `Reverse`, która odwraca zawartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="d193b-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="d193b-135">Wklej następujący kod i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="d193b-135">Paste in the following code and save the file:</span></span>

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

<span data-ttu-id="d193b-136">Teraz, gdy masz już utworzoną zawartość szablonu, musisz utworzyć konfigurację szablonu w folderze głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="d193b-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="d193b-137">Utwórz konfigurację szablonu</span><span class="sxs-lookup"><span data-stu-id="d193b-137">Create the template config</span></span>

<span data-ttu-id="d193b-138">Szablony są rozpoznawane w programie .NET Core za pomocą specjalnego folderu i pliku konfiguracji, który istnieje w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="d193b-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="d193b-139">W tym samouczku folder szablonu znajduje się w lokalizacji _working\templates\extensions_.</span><span class="sxs-lookup"><span data-stu-id="d193b-139">In this tutorial, your template folder is located at _working\templates\extensions_.</span></span>

<span data-ttu-id="d193b-140">Podczas tworzenia szablonu wszystkie pliki i foldery znajdujące się w folderze szablonów są uwzględniane jako część szablonu, z wyjątkiem folderu specjalnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d193b-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="d193b-141">Ten folder konfiguracji ma nazwę _. Template. config_.</span><span class="sxs-lookup"><span data-stu-id="d193b-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="d193b-142">Najpierw utwórz nowy podfolder o nazwie _. Template. config_, a następnie wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="d193b-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="d193b-143">Następnie utwórz nowy plik o nazwie _Template. JSON_.</span><span class="sxs-lookup"><span data-stu-id="d193b-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="d193b-144">Struktura folderów powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d193b-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="d193b-145">Otwórz plik _Template. JSON_ przy użyciu ulubionego edytora tekstu i wklej go w poniższym kodzie JSON i Zapisz go:</span><span class="sxs-lookup"><span data-stu-id="d193b-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

<span data-ttu-id="d193b-146">Ten plik konfiguracji zawiera wszystkie ustawienia szablonu.</span><span class="sxs-lookup"><span data-stu-id="d193b-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="d193b-147">Można wyświetlić ustawienia podstawowe, takie jak `name` i `shortName`, ale istnieje również `tags/type` wartość, która jest ustawiona na `item`.</span><span class="sxs-lookup"><span data-stu-id="d193b-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="d193b-148">Spowoduje to kategoryzację szablonu jako szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="d193b-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="d193b-149">Nie ma ograniczeń dotyczących typu tworzonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="d193b-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="d193b-150">Wartości `item` i `project` są typowymi nazwami zalecanymi przez platformę .NET Core, dzięki czemu użytkownicy mogą łatwo filtrować typ szukanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="d193b-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="d193b-151">Element `classifications` reprezentuje kolumnę **Tagi** , która pojawia się po uruchomieniu `dotnet new` i wyświetleniu listy szablonów.</span><span class="sxs-lookup"><span data-stu-id="d193b-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="d193b-152">Użytkownicy mogą również wyszukiwać w oparciu o znaczniki klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="d193b-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="d193b-153">Nie należy mylić właściwości `tags` w pliku \*. JSON z listą tagów `classifications`.</span><span class="sxs-lookup"><span data-stu-id="d193b-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="d193b-154">Te dwa różne rzeczy są uważane za podobne.</span><span class="sxs-lookup"><span data-stu-id="d193b-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="d193b-155">Pełny Schemat pliku *Template. JSON* znajduje się w [magazynie schematów JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="d193b-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="d193b-156">Aby uzyskać więcej informacji na temat pliku *Template. JSON* , zobacz stronę [typu tworzenia szablonów programu dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="d193b-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="d193b-157">Teraz, gdy masz prawidłowy plik _Template. config/Template. JSON_ , szablon jest gotowy do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="d193b-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="d193b-158">W terminalu przejdź do folderu _Extensions_ i uruchom następujące polecenie, aby zainstalować szablon znajdujący się w bieżącym folderze:</span><span class="sxs-lookup"><span data-stu-id="d193b-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="d193b-159">**W systemie Windows**: `dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="d193b-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="d193b-160">**W systemie Linux lub macOS**: `dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="d193b-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="d193b-161">To polecenie wyświetla listę zainstalowanych szablonów, które powinny obejmować użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d193b-161">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a><span data-ttu-id="d193b-162">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="d193b-162">Test the item template</span></span>

<span data-ttu-id="d193b-163">Teraz, gdy masz zainstalowany szablon elementu, przetestuj go.</span><span class="sxs-lookup"><span data-stu-id="d193b-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="d193b-164">Przejdź do folderu _test/_ folder i Utwórz nową aplikację konsolową z `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="d193b-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="d193b-165">Spowoduje to wygenerowanie projektu roboczego, który można łatwo przetestować przy użyciu polecenia `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="d193b-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

<span data-ttu-id="d193b-166">Następnie uruchom `dotnet new stringext`, aby wygenerować _CommonExtensions.cs_ na podstawie szablonu.</span><span class="sxs-lookup"><span data-stu-id="d193b-166">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="d193b-167">Zmień kod w _program.cs_ , aby odwrócić ciąg `"Hello World"` przy użyciu metody rozszerzającej dostarczonej przez szablon.</span><span class="sxs-lookup"><span data-stu-id="d193b-167">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="d193b-168">Ponownie uruchom program i zobaczysz, że wynik jest odwrócony.</span><span class="sxs-lookup"><span data-stu-id="d193b-168">Run the program again and you'll see that the result is reversed.</span></span>

```console
C:\test> dotnet run
!dlroW olleH
```

<span data-ttu-id="d193b-169">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="d193b-169">Congratulations!</span></span> <span data-ttu-id="d193b-170">Utworzono i wdrożono szablon elementu z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d193b-170">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="d193b-171">W ramach przygotowania do następnej części tej serii samouczków należy odinstalować utworzony szablon.</span><span class="sxs-lookup"><span data-stu-id="d193b-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="d193b-172">Pamiętaj, aby usunąć wszystkie pliki z folderu _testowego_ .</span><span class="sxs-lookup"><span data-stu-id="d193b-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="d193b-173">Spowoduje to powrót do stanu czystego gotowego do następnej głównej sekcji tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="d193b-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="d193b-174">Odinstaluj szablon</span><span class="sxs-lookup"><span data-stu-id="d193b-174">Uninstall the template</span></span>

<span data-ttu-id="d193b-175">Ponieważ szablon został zainstalowany według ścieżki pliku, należy go odinstalować z **bezwzględną** ścieżką pliku.</span><span class="sxs-lookup"><span data-stu-id="d193b-175">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="d193b-176">Listę zainstalowanych szablonów można wyświetlić, uruchamiając polecenie `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="d193b-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="d193b-177">Szablon powinien zostać wyświetlony jako ostatni.</span><span class="sxs-lookup"><span data-stu-id="d193b-177">Your template should be listed last.</span></span> <span data-ttu-id="d193b-178">Użyj podanej ścieżki, aby odinstalować szablon przy użyciu polecenia `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="d193b-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```console
C:\working> dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="d193b-179">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d193b-179">Next steps</span></span>

<span data-ttu-id="d193b-180">W tym samouczku utworzono szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="d193b-180">In this tutorial, you created an item template.</span></span> <span data-ttu-id="d193b-181">Aby dowiedzieć się, jak utworzyć szablon projektu, Kontynuuj tę serię samouczków.</span><span class="sxs-lookup"><span data-stu-id="d193b-181">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d193b-182">Utwórz szablon projektu</span><span class="sxs-lookup"><span data-stu-id="d193b-182">Create a project template</span></span>](cli-templates-create-project-template.md)
