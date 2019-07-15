---
title: Utwórz szablon elementu dla platformy dotnet new - interfejsu wiersza polecenia platformy .NET Core
description: Dowiedz się, jak utworzyć szablon elementu dla nowego polecenia dotnet. Szablony elementów może zawierać dowolną liczbę plików.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: c50aaf413f08c2e4cbe3f8ce8c057e5841067c92
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877178"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="5a48e-104">Samouczek: Utworzyć szablon elementu</span><span class="sxs-lookup"><span data-stu-id="5a48e-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="5a48e-105">Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projektów, plików i nawet zasobów.</span><span class="sxs-lookup"><span data-stu-id="5a48e-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="5a48e-106">Niniejszy samouczek jest drugą częścią serii, pokazujący sposób tworzenia, instalowanie i odinstalowywanie szablonów do użytku z programem `dotnet new` polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a48e-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="5a48e-107">W tej części serii, dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="5a48e-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="5a48e-108">Utwórz klasę dla szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="5a48e-108">Create a class for an item template</span></span>
> * <span data-ttu-id="5a48e-109">Utwórz folder konfiguracji szablonu i pliku</span><span class="sxs-lookup"><span data-stu-id="5a48e-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="5a48e-110">Zainstaluj szablon ze ścieżki plików</span><span class="sxs-lookup"><span data-stu-id="5a48e-110">Install a template from a file path</span></span>
> * <span data-ttu-id="5a48e-111">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="5a48e-111">Test an item template</span></span>
> * <span data-ttu-id="5a48e-112">Odinstaluj szablon elementu</span><span class="sxs-lookup"><span data-stu-id="5a48e-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a48e-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5a48e-113">Prerequisites</span></span>

* <span data-ttu-id="5a48e-114">[Zestaw SDK programu .NET core 2.2](https://www.microsoft.com/net/core) lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="5a48e-114">[.NET Core 2.2 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
* <span data-ttu-id="5a48e-115">Zapoznaj się z artykułami odwołanie [szablonów niestandardowych dla platformy dotnet nowe](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5a48e-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="5a48e-116">Dokumentacja wyjaśniono podstawowe informacje o szablonach i jak są one Podsumowując.</span><span class="sxs-lookup"><span data-stu-id="5a48e-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="5a48e-117">Niektóre z tych informacji będzie powtarzać w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="5a48e-118">Otwórz terminal i przejdź do _working\templates\\_  folderu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-118">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="5a48e-119">Utwórz wymagane foldery</span><span class="sxs-lookup"><span data-stu-id="5a48e-119">Create the required folders</span></span>

<span data-ttu-id="5a48e-120">W tej serii używa "folderu roboczego" gdzie znajduje się Twoje źródło szablonu i używane do testowania szablonów "testowania folderu".</span><span class="sxs-lookup"><span data-stu-id="5a48e-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="5a48e-121">Folder roboczy i folder testowania powinny znajdować się w tym samym folderze nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="5a48e-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="5a48e-122">Najpierw utwórz folder nadrzędny, nazwa nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="5a48e-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="5a48e-123">Następnie utwórz podfolder o nazwie _pracy_.</span><span class="sxs-lookup"><span data-stu-id="5a48e-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="5a48e-124">Wewnątrz _pracy_ folderze utwórz podfolder o nazwie _szablony_.</span><span class="sxs-lookup"><span data-stu-id="5a48e-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="5a48e-125">Następnie utwórz folder w folderze nadrzędnym, o nazwie _testu_.</span><span class="sxs-lookup"><span data-stu-id="5a48e-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="5a48e-126">Struktura folderów powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5a48e-126">The folder structure should look like the following:</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="5a48e-127">Utworzyć szablon elementu</span><span class="sxs-lookup"><span data-stu-id="5a48e-127">Create an item template</span></span>

<span data-ttu-id="5a48e-128">Szablon elementu jest określonego typu szablonu, który zawiera jeden lub więcej plików.</span><span class="sxs-lookup"><span data-stu-id="5a48e-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="5a48e-129">Te typy szablonów są przydatne, gdy chcesz wygenerować coś, takich jak konfiguracja, kodu lub pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5a48e-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="5a48e-130">W tym przykładzie utworzysz klasę, która dodaje metodę rozszerzenia typu string.</span><span class="sxs-lookup"><span data-stu-id="5a48e-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="5a48e-131">W terminalu przejdź do _working\templates\\_  folderze i utworzyć nowy podfolder o nazwie _rozszerzenia_.</span><span class="sxs-lookup"><span data-stu-id="5a48e-131">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="5a48e-132">Wprowadź folder.</span><span class="sxs-lookup"><span data-stu-id="5a48e-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="5a48e-133">Utwórz nowy plik o nazwie _CommonExtensions.cs_ i otwórz go za pomocą ulubionego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="5a48e-134">Ta klasa zapewni metodę rozszerzenia o nazwie `Reverse` który odwraca zawartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="5a48e-135">Wklej następujący kod, a następnie zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="5a48e-135">Paste in the following code and save the file:</span></span>

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

<span data-ttu-id="5a48e-136">Teraz, gdy zawartość utworzony szablon, musisz utworzyć konfiguracji szablonu w folderze głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="5a48e-137">Tworzenie konfiguracji szablonu</span><span class="sxs-lookup"><span data-stu-id="5a48e-137">Create the template config</span></span>

<span data-ttu-id="5a48e-138">Szablony są rozpoznawane w programie .NET Core, przez plik specjalny folder i konfiguracji, który istnieje w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="5a48e-139">W tym samouczku folderu szablon znajduje się w _working\templates\extensions\\_ .</span><span class="sxs-lookup"><span data-stu-id="5a48e-139">In this tutorial, your template folder is located at _working\templates\extensions\\_.</span></span>

<span data-ttu-id="5a48e-140">Podczas tworzenia szablonu, wszystkie pliki i foldery w folderze szablonu są dołączane jako część szablonu z wyjątkiem folder konfiguracji specjalnych.</span><span class="sxs-lookup"><span data-stu-id="5a48e-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="5a48e-141">Ten folder konfiguracji nosi nazwę _. template.config_.</span><span class="sxs-lookup"><span data-stu-id="5a48e-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="5a48e-142">Najpierw utwórz nowy podfolder o nazwie _. template.config_, wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="5a48e-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="5a48e-143">Następnie utwórz nowy plik o nazwie _template.json_.</span><span class="sxs-lookup"><span data-stu-id="5a48e-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="5a48e-144">Twoja struktura folderów powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5a48e-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="5a48e-145">Otwórz _template.json_ tekstem ulubionym edytorze i wklej następujący kod JSON kod i zapisz go:</span><span class="sxs-lookup"><span data-stu-id="5a48e-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it:</span></span>

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

<span data-ttu-id="5a48e-146">Ten plik konfiguracji zawiera ustawienia szablonu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="5a48e-147">Widać podstawowe ustawienia, takie jak `name` i `shortName`, ale jest również `tags/type` wartość, która jest równa `item`.</span><span class="sxs-lookup"><span data-stu-id="5a48e-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="5a48e-148">Ta klasyfikuje szablon jako szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="5a48e-149">Nie ma żadnych ograniczeń na typ tworzonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="5a48e-150">`item` i `project` wartości to pospolite nazwy, które platformy .NET Core zaleca, aby użytkownicy z łatwością można filtrować szablonu są wyszukiwane.</span><span class="sxs-lookup"><span data-stu-id="5a48e-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="5a48e-151">`classifications` Element reprezentuje **tagi** kolumny zostanie wyświetlony po uruchomieniu `dotnet new` i Uzyskaj listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="5a48e-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="5a48e-152">Użytkownicy mogą również przeszukiwać na podstawie klasyfikacji tagów.</span><span class="sxs-lookup"><span data-stu-id="5a48e-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="5a48e-153">Nie należy mylić `tags` właściwość \*plik JSON z `classifications` lista tagów.</span><span class="sxs-lookup"><span data-stu-id="5a48e-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="5a48e-154">Są one dwie różne rzeczy Niestety o nazwie podobnie.</span><span class="sxs-lookup"><span data-stu-id="5a48e-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="5a48e-155">Pełnego schematu dla *template.json* plik znajduje się na [Store schematu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="5a48e-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="5a48e-156">Aby uzyskać więcej informacji na temat *template.json* plików, zobacz [wiki szablonów dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="5a48e-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="5a48e-157">Teraz, gdy masz prawidłową _.template.config/template.json_ pliku, szablon będzie gotowy do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="5a48e-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="5a48e-158">W terminalu przejdź do _rozszerzenia_ folderu i uruchom następujące polecenie, aby zainstalować szablon znajdujący się w bieżącym folderze:</span><span class="sxs-lookup"><span data-stu-id="5a48e-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="5a48e-159">**Na Windows**: `dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="5a48e-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="5a48e-160">**W systemie Linux lub macOS**: `dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="5a48e-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="5a48e-161">To polecenie wyświetla listę zainstalowane, szablony, które powinien zawierać należy do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="5a48e-161">This command outputs the list of templates installed, which should include yours.</span></span>

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

## <a name="test-the-item-template"></a><span data-ttu-id="5a48e-162">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="5a48e-162">Test the item template</span></span>

<span data-ttu-id="5a48e-163">Teraz, gdy szablon elementu, który jest zainstalowany, należy go przetestować.</span><span class="sxs-lookup"><span data-stu-id="5a48e-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="5a48e-164">Przejdź do _testów /_ folderze i utworzyć nową aplikację konsoli przy użyciu `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="5a48e-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="5a48e-165">Spowoduje to wygenerowanie projektu pracy, możesz łatwo przeprowadzić test za `dotnet run` polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a48e-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

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

<span data-ttu-id="5a48e-166">Następnie uruchom `dotnet new stringext` do generowania _CommonExtensions.cs_ z szablonu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-166">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="5a48e-167">Zmień kod w _Program.cs_ odwrócić `"Hello World"` ciągu przy użyciu metody rozszerzenia udostępniane przez szablon.</span><span class="sxs-lookup"><span data-stu-id="5a48e-167">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="5a48e-168">Ponownie uruchom program i zobaczysz, że wynik zostanie odwrócony.</span><span class="sxs-lookup"><span data-stu-id="5a48e-168">Run the program again and you'll see that the result is reversed.</span></span>

```console
C:\test> dotnet run
!dlroW olleH
```

<span data-ttu-id="5a48e-169">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="5a48e-169">Congratulations!</span></span> <span data-ttu-id="5a48e-170">Utworzyć i wdrożyć szablon elementu za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a48e-170">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="5a48e-171">W ramach przygotowania do następnej części tej serii samouczków należy odinstalować szablon, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="5a48e-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="5a48e-172">Upewnij się usunąć wszystkie pliki z _test_ folderu zbyt.</span><span class="sxs-lookup"><span data-stu-id="5a48e-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="5a48e-173">To będzie wrócić do stanu czystego gotowy do następnej sekcji głównej części tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="5a48e-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="5a48e-174">Odinstaluj szablonu</span><span class="sxs-lookup"><span data-stu-id="5a48e-174">Uninstall the template</span></span>

<span data-ttu-id="5a48e-175">Ponieważ szablon został zainstalowany przy użyciu ścieżki pliku, należy odinstalować ją za pomocą **bezwzględne** ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="5a48e-175">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="5a48e-176">Można wyświetlić listę szablonów zainstalowane, uruchamiając `dotnet new -u` polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a48e-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="5a48e-177">Szablon powinien zostać wyświetlony ostatnio.</span><span class="sxs-lookup"><span data-stu-id="5a48e-177">Your template should be listed last.</span></span> <span data-ttu-id="5a48e-178">Użyj ścieżki wymienionymi w celu odinstalowania szablon, korzystając z `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a48e-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="5a48e-179">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5a48e-179">Next steps</span></span>

<span data-ttu-id="5a48e-180">W tym samouczku utworzono szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="5a48e-180">In this tutorial, you created an item template.</span></span> <span data-ttu-id="5a48e-181">Aby dowiedzieć się, jak utworzyć szablon projektu, przejdź w tej serii samouczków.</span><span class="sxs-lookup"><span data-stu-id="5a48e-181">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a48e-182">Tworzenie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="5a48e-182">Create a project template</span></span>](cli-templates-create-project-template.md)
