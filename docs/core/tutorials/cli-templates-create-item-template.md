---
title: Tworzenie szablonu elementu dla dotnet nowy - .NET Core CLI
description: Dowiedz się, jak utworzyć szablon elementu dla nowego polecenia dotnet. Szablony elementów mogą zawierać dowolną liczbę plików.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503556"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="7f627-104">Samouczek: Tworzenie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="7f627-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="7f627-105">Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projekty, pliki, a nawet zasoby.</span><span class="sxs-lookup"><span data-stu-id="7f627-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="7f627-106">Ten samouczek jest częścią pierwszej serii, która uczy, jak tworzyć, instalować i odinstalowywać szablony do użycia z poleceniem. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="7f627-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="7f627-107">W tej części serii dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="7f627-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="7f627-108">Tworzenie klasy dla szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="7f627-108">Create a class for an item template</span></span>
> * <span data-ttu-id="7f627-109">Tworzenie folderu i pliku konfiguracji szablonu</span><span class="sxs-lookup"><span data-stu-id="7f627-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="7f627-110">Instalowanie szablonu ze ścieżki pliku</span><span class="sxs-lookup"><span data-stu-id="7f627-110">Install a template from a file path</span></span>
> * <span data-ttu-id="7f627-111">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="7f627-111">Test an item template</span></span>
> * <span data-ttu-id="7f627-112">Odinstalowywanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="7f627-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f627-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7f627-113">Prerequisites</span></span>

* <span data-ttu-id="7f627-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) lub nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="7f627-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
* <span data-ttu-id="7f627-115">Przeczytaj artykuł [referencyjny Niestandardowe szablony dla dotnet nowy](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="7f627-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="7f627-116">W artykule referencyjnym wyjaśniono podstawy dotyczące szablonów i sposobu ich łączenia.</span><span class="sxs-lookup"><span data-stu-id="7f627-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="7f627-117">Niektóre z tych informacji zostaną powtórzone tutaj.</span><span class="sxs-lookup"><span data-stu-id="7f627-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="7f627-118">Otwórz terminal i przejdź do folderu _working\templates._</span><span class="sxs-lookup"><span data-stu-id="7f627-118">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="7f627-119">Tworzenie wymaganych folderów</span><span class="sxs-lookup"><span data-stu-id="7f627-119">Create the required folders</span></span>

<span data-ttu-id="7f627-120">Ta seria używa "folderu roboczego", w którym znajduje się źródło szablonu, oraz "folderu testowego" używanego do testowania szablonów.</span><span class="sxs-lookup"><span data-stu-id="7f627-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="7f627-121">Folder roboczy i folder testów powinny znajdować się w tym samym folderze nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="7f627-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="7f627-122">Najpierw utwórz folder nadrzędny, nazwa nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="7f627-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="7f627-123">Następnie utwórz podfolder o nazwie _praca_.</span><span class="sxs-lookup"><span data-stu-id="7f627-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="7f627-124">Wewnątrz folderu _roboczego_ utwórz podfolder o nazwie _szablony_.</span><span class="sxs-lookup"><span data-stu-id="7f627-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="7f627-125">Następnie utwórz folder w folderze nadrzędnym o nazwie _test_.</span><span class="sxs-lookup"><span data-stu-id="7f627-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="7f627-126">Struktura folderów powinna wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="7f627-126">The folder structure should look like the following.</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="7f627-127">Tworzenie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="7f627-127">Create an item template</span></span>

<span data-ttu-id="7f627-128">Szablon elementu jest określonym typem szablonu, który zawiera jeden lub więcej plików.</span><span class="sxs-lookup"><span data-stu-id="7f627-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="7f627-129">Te typy szablonów są przydatne, gdy chcesz wygenerować coś takiego jak plik konfiguracyjny, kod lub plik rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7f627-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="7f627-130">W tym przykładzie utworzysz klasę, która dodaje metodę rozszerzenia do typu ciągu.</span><span class="sxs-lookup"><span data-stu-id="7f627-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="7f627-131">W terminalu przejdź do folderu _working\templates_ i utwórz nowy podfolder o nazwie _rozszerzenia_.</span><span class="sxs-lookup"><span data-stu-id="7f627-131">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="7f627-132">Wprowadź folder.</span><span class="sxs-lookup"><span data-stu-id="7f627-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="7f627-133">Utwórz nowy plik o nazwie _CommonExtensions.cs_ i otwórz go za pomocą ulubionego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="7f627-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="7f627-134">Ta klasa zapewni metodę `Reverse` rozszerzenia o nazwie, która odwraca zawartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="7f627-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="7f627-135">Wklej w następującym kodzie i zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="7f627-135">Paste in the following code and save the file:</span></span>

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

<span data-ttu-id="7f627-136">Teraz, gdy masz zawartość szablonu utworzone, należy utworzyć konfigurację szablonu w folderze głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="7f627-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="7f627-137">Tworzenie konfiguracji szablonu</span><span class="sxs-lookup"><span data-stu-id="7f627-137">Create the template config</span></span>

<span data-ttu-id="7f627-138">Szablony są rozpoznawane w .NET Core przez specjalny folder i plik konfiguracyjny, które istnieją w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="7f627-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="7f627-139">W tym samouczku folder szablonu znajduje się w _obszarze roboczo-szablony\rozszerzenia_.</span><span class="sxs-lookup"><span data-stu-id="7f627-139">In this tutorial, your template folder is located at _working\templates\extensions_.</span></span>

<span data-ttu-id="7f627-140">Podczas tworzenia szablonu wszystkie pliki i foldery w folderze szablonu są uwzględniane jako część szablonu z wyjątkiem specjalnego folderu konfiguratornego.</span><span class="sxs-lookup"><span data-stu-id="7f627-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="7f627-141">Ten folder konfiguracyjny nosi nazwę _.template.config_.</span><span class="sxs-lookup"><span data-stu-id="7f627-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="7f627-142">Najpierw utwórz nowy podfolder o nazwie _.template.config_, wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="7f627-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="7f627-143">Następnie utwórz nowy plik o nazwie _template.json_.</span><span class="sxs-lookup"><span data-stu-id="7f627-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="7f627-144">Struktura folderów powinna wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="7f627-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="7f627-145">Otwórz _szablon.json_ za pomocą ulubionego edytora tekstu i wklej w poniższym kodzie JSON i zapisz go.</span><span class="sxs-lookup"><span data-stu-id="7f627-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it.</span></span>

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

<span data-ttu-id="7f627-146">Ten plik konfiguracyjny zawiera wszystkie ustawienia szablonu.</span><span class="sxs-lookup"><span data-stu-id="7f627-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="7f627-147">Możesz zobaczyć podstawowe ustawienia, `name` takie `shortName`jak i , `tags/type` ale jest też `item`wartość, która jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="7f627-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="7f627-148">Ta kategoryzuje szablon jako szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="7f627-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="7f627-149">Nie ma żadnych ograniczeń co do typu tworzonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="7f627-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="7f627-150">Wartości `item` `project` i są wspólne nazwy, które program .NET Core zaleca, dzięki czemu użytkownicy mogą łatwo filtrować typ szablonu, którego szukają.</span><span class="sxs-lookup"><span data-stu-id="7f627-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="7f627-151">Element `classifications` reprezentuje kolumnę **tagów** wyświetlaną `dotnet new` po uruchomieniu i uzyskanie listy szablonów.</span><span class="sxs-lookup"><span data-stu-id="7f627-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="7f627-152">Użytkownicy mogą również wyszukiwać na podstawie tagów klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="7f627-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="7f627-153">Nie należy mylić `tags` właściwości \*w pliku json `classifications` z listą tagów.</span><span class="sxs-lookup"><span data-stu-id="7f627-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="7f627-154">Są to dwie różne rzeczy, które niestety mają podobną nazwę.</span><span class="sxs-lookup"><span data-stu-id="7f627-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="7f627-155">Pełny schemat pliku *template.json* znajduje się w [Magazynie schematów JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="7f627-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="7f627-156">Aby uzyskać więcej informacji na temat pliku *template.json,* zobacz [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="7f627-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="7f627-157">Teraz, gdy masz prawidłowy plik _.template.config/template.json,_ szablon jest gotowy do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="7f627-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="7f627-158">W terminalu przejdź do folderu _rozszerzeń_ i uruchom następujące polecenie, aby zainstalować szablon znajdujący się w bieżącym folderze:</span><span class="sxs-lookup"><span data-stu-id="7f627-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="7f627-159">**W systemie Windows**:`dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="7f627-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="7f627-160">**W systemie Linux lub macOS**:`dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="7f627-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="7f627-161">To polecenie wyświetla listę zainstalowanych szablonów, która powinna zawierać twoje.</span><span class="sxs-lookup"><span data-stu-id="7f627-161">This command outputs the list of templates installed, which should include yours.</span></span>

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

## <a name="test-the-item-template"></a><span data-ttu-id="7f627-162">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="7f627-162">Test the item template</span></span>

<span data-ttu-id="7f627-163">Teraz, gdy masz zainstalowany szablon elementu, przetestuj go.</span><span class="sxs-lookup"><span data-stu-id="7f627-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="7f627-164">Przejdź do _folderu test/_ i utwórz nową aplikację konsoli z . `dotnet new console`</span><span class="sxs-lookup"><span data-stu-id="7f627-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="7f627-165">Spowoduje to wygenerowanie projektu roboczego, `dotnet run` który można łatwo przetestować za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f627-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="7f627-166">Otrzymasz dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="7f627-166">You get output similar to the following.</span></span>

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

<span data-ttu-id="7f627-167">Uruchom projekt za pomocą.</span><span class="sxs-lookup"><span data-stu-id="7f627-167">Run the project with.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="7f627-168">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="7f627-168">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="7f627-169">Następnie uruchom, `dotnet new stringext` aby wygenerować _CommonExtensions.cs_ z szablonu.</span><span class="sxs-lookup"><span data-stu-id="7f627-169">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```dotnetcli
dotnet new stringext
```

<span data-ttu-id="7f627-170">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="7f627-170">You get the following output.</span></span>

```console
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="7f627-171">Zmień kod w _Program.cs,_ aby odwrócić `"Hello World"` ciąg z metody rozszerzenia dostarczone przez szablon.</span><span class="sxs-lookup"><span data-stu-id="7f627-171">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="7f627-172">Uruchom program ponownie, a zobaczysz, że wynik jest odwrócony.</span><span class="sxs-lookup"><span data-stu-id="7f627-172">Run the program again and you'll see that the result is reversed.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="7f627-173">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="7f627-173">You get the following output.</span></span>

```console
!dlroW olleH
```

<span data-ttu-id="7f627-174">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="7f627-174">Congratulations!</span></span> <span data-ttu-id="7f627-175">Utworzono i wdrożono szablon elementu za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7f627-175">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="7f627-176">W ramach przygotowań do następnej części tej serii samouczków należy odinstalować utworzony szablon.</span><span class="sxs-lookup"><span data-stu-id="7f627-176">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="7f627-177">Upewnij się, że wszystkie pliki z folderu _testowego_ też.</span><span class="sxs-lookup"><span data-stu-id="7f627-177">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="7f627-178">Spowoduje to powrót do stanu czystego gotowego do następnej głównej sekcji tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="7f627-178">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="7f627-179">Odinstalowywanie szablonu</span><span class="sxs-lookup"><span data-stu-id="7f627-179">Uninstall the template</span></span>

<span data-ttu-id="7f627-180">Ponieważ szablon został zainstalowany według ścieżki pliku, należy go odinstalować za pomocą **bezwzględnej** ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="7f627-180">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="7f627-181">Możesz zobaczyć listę szablonów zainstalowanych `dotnet new -u` przez uruchomienie polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f627-181">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="7f627-182">Szablon powinien być wymieniony jako ostatni.</span><span class="sxs-lookup"><span data-stu-id="7f627-182">Your template should be listed last.</span></span> <span data-ttu-id="7f627-183">Użyj ścieżki wymienionej, aby odinstalować szablon za `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f627-183">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="7f627-184">Otrzymasz dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="7f627-184">You get output similar to the following.</span></span>

```console
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

<span data-ttu-id="7f627-185">Aby odinstalować szablon, uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7f627-185">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="7f627-186">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7f627-186">Next steps</span></span>

<span data-ttu-id="7f627-187">W tym samouczku utworzono szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="7f627-187">In this tutorial, you created an item template.</span></span> <span data-ttu-id="7f627-188">Aby dowiedzieć się, jak utworzyć szablon projektu, kontynuuj tę serię samouczków.</span><span class="sxs-lookup"><span data-stu-id="7f627-188">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7f627-189">Tworzenie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="7f627-189">Create a project template</span></span>](cli-templates-create-project-template.md)
