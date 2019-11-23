---
title: Utwórz szablon projektu dla nowego dotnet
description: Dowiedz się, jak utworzyć szablon projektu dla nowego polecenia dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 1f4e73287fca650b20ed5617c8dfd80e0bd8363c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318281"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="f1f93-103">Samouczek: Tworzenie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="f1f93-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="f1f93-104">Za pomocą platformy .NET Core można tworzyć i wdrażać szablony generujące projekty, pliki, nawet zasoby.</span><span class="sxs-lookup"><span data-stu-id="f1f93-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="f1f93-105">Ten samouczek jest drugą częścią serii, która zawiera informacje na temat tworzenia, instalowania i odinstalowywania szablonów do użycia z poleceniem `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="f1f93-106">W tej części serii dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="f1f93-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="f1f93-107">Tworzenie zasobów szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="f1f93-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="f1f93-108">Tworzenie folderu i pliku konfiguracji szablonu</span><span class="sxs-lookup"><span data-stu-id="f1f93-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="f1f93-109">Instalowanie szablonu ze ścieżki pliku</span><span class="sxs-lookup"><span data-stu-id="f1f93-109">Install a template from a file path</span></span>
> * <span data-ttu-id="f1f93-110">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="f1f93-110">Test an item template</span></span>
> * <span data-ttu-id="f1f93-111">Odinstaluj szablon elementu</span><span class="sxs-lookup"><span data-stu-id="f1f93-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f1f93-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f1f93-112">Prerequisites</span></span>

* <span data-ttu-id="f1f93-113">Ukończ [część 1](cli-templates-create-item-template.md) tej serii samouczków.</span><span class="sxs-lookup"><span data-stu-id="f1f93-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="f1f93-114">Otwórz Terminal i przejdź do folderu _working\templates\\_ .</span><span class="sxs-lookup"><span data-stu-id="f1f93-114">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="f1f93-115">Utwórz szablon projektu</span><span class="sxs-lookup"><span data-stu-id="f1f93-115">Create a project template</span></span>

<span data-ttu-id="f1f93-116">Szablony projektów tworzą gotowe do uruchomienia projekty, które ułatwiają użytkownikom rozpoczęcie pracy z zestawem roboczym kodu.</span><span class="sxs-lookup"><span data-stu-id="f1f93-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="f1f93-117">Platforma .NET Core zawiera kilka szablonów projektu, takich jak Aplikacja konsolowa lub Biblioteka klas.</span><span class="sxs-lookup"><span data-stu-id="f1f93-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="f1f93-118">W tym przykładzie utworzysz nowy projekt konsoli, który umożliwia C# 8,0 i generuje punkt wejścia `async main`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="f1f93-119">W terminalu przejdź do folderu _working\templates\\_ i Utwórz nowy podfolder o nazwie _consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="f1f93-119">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="f1f93-120">Wprowadź podfolder i uruchom `dotnet new console` w celu wygenerowania standardowej aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="f1f93-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="f1f93-121">Będziesz edytować pliki utworzone przez ten szablon w celu utworzenia nowego szablonu.</span><span class="sxs-lookup"><span data-stu-id="f1f93-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="f1f93-122">Modyfikuj Program.cs</span><span class="sxs-lookup"><span data-stu-id="f1f93-122">Modify Program.cs</span></span>

<span data-ttu-id="f1f93-123">Otwórz plik _program.cs_ .</span><span class="sxs-lookup"><span data-stu-id="f1f93-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="f1f93-124">Projekt konsoli nie używa asynchronicznego punktu wejścia, więc Dodajmy ten element.</span><span class="sxs-lookup"><span data-stu-id="f1f93-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="f1f93-125">Zmień kod na następujący i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="f1f93-125">Change your code to the following and save the file:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 8.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="f1f93-126">Modyfikuj consoleasync. csproj</span><span class="sxs-lookup"><span data-stu-id="f1f93-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="f1f93-127">Zaktualizujmy wersję C# językową używaną przez ten projekt do wersji 8,0.</span><span class="sxs-lookup"><span data-stu-id="f1f93-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="f1f93-128">Edytuj plik _consoleasync. csproj_ i Dodaj `<LangVersion>` ustawienia do węzła `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="f1f93-129">Skompiluj projekt</span><span class="sxs-lookup"><span data-stu-id="f1f93-129">Build the project</span></span>

<span data-ttu-id="f1f93-130">Przed ukończeniem szablonu projektu należy go przetestować, aby upewnić się, że kompiluje i działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="f1f93-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span> <span data-ttu-id="f1f93-131">W terminalu uruchom polecenie `dotnet run` i zobaczysz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f1f93-131">In your terminal, run the `dotnet run` command and you should see the following output:</span></span>

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="f1f93-132">Można usunąć foldery _obj_ i _bin_ utworzone przy użyciu `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-132">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="f1f93-133">Usunięcie tych plików gwarantuje, że szablon zawiera tylko pliki powiązane z szablonem, a nie wszystkie pliki, które powodują akcję kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f1f93-133">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="f1f93-134">Teraz, gdy masz już utworzoną zawartość szablonu, musisz utworzyć konfigurację szablonu w folderze głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="f1f93-134">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="f1f93-135">Utwórz konfigurację szablonu</span><span class="sxs-lookup"><span data-stu-id="f1f93-135">Create the template config</span></span>

<span data-ttu-id="f1f93-136">Szablony są rozpoznawane w programie .NET Core za pomocą specjalnego folderu i pliku konfiguracji, który istnieje w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="f1f93-136">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="f1f93-137">W tym samouczku folder szablonu znajduje się w witrynie _working\templates\consoleasync\\_ .</span><span class="sxs-lookup"><span data-stu-id="f1f93-137">In this tutorial, your template folder is located at _working\templates\consoleasync\\_.</span></span>

<span data-ttu-id="f1f93-138">Podczas tworzenia szablonu wszystkie pliki i foldery znajdujące się w folderze szablonów są uwzględniane jako część szablonu, z wyjątkiem folderu specjalnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1f93-138">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="f1f93-139">Ten folder konfiguracji ma nazwę _. Template. config_.</span><span class="sxs-lookup"><span data-stu-id="f1f93-139">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="f1f93-140">Najpierw utwórz nowy podfolder o nazwie _. Template. config_, a następnie wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="f1f93-140">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="f1f93-141">Następnie utwórz nowy plik o nazwie _Template. JSON_.</span><span class="sxs-lookup"><span data-stu-id="f1f93-141">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="f1f93-142">Struktura folderów powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f1f93-142">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="f1f93-143">Otwórz plik _Template. JSON_ przy użyciu ulubionego edytora tekstu i wklej go w poniższym kodzie JSON i Zapisz go:</span><span class="sxs-lookup"><span data-stu-id="f1f93-143">Open the _template.json_ with your favorite text editor and paste in the following json code and save it:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#8" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

<span data-ttu-id="f1f93-144">Ten plik konfiguracji zawiera wszystkie ustawienia szablonu.</span><span class="sxs-lookup"><span data-stu-id="f1f93-144">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="f1f93-145">Można zobaczyć podstawowe ustawienia, takie jak `name` i `shortName`, ale również istnieje `tags/type` wartość, która jest ustawiona na `project`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-145">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="f1f93-146">Spowoduje to wyznaczenie szablonu jako szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="f1f93-146">This designates your template as a project template.</span></span> <span data-ttu-id="f1f93-147">Nie ma ograniczeń dotyczących typu tworzonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="f1f93-147">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="f1f93-148">Wartości `item` i `project` są typowymi nazwami zalecanymi przez platformę .NET Core, dzięki czemu użytkownicy mogą łatwo filtrować typ szukanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="f1f93-148">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="f1f93-149">Element `classifications` reprezentuje kolumnę **Tagi** , która pojawia się po uruchomieniu `dotnet new` i wyświetleniu listy szablonów.</span><span class="sxs-lookup"><span data-stu-id="f1f93-149">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="f1f93-150">Użytkownicy mogą również wyszukiwać w oparciu o znaczniki klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f1f93-150">Users can also search based on classification tags.</span></span> <span data-ttu-id="f1f93-151">Nie należy mylić właściwości `tags` w pliku JSON z listą tagów `classifications`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-151">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="f1f93-152">Te dwa różne rzeczy są uważane za podobne.</span><span class="sxs-lookup"><span data-stu-id="f1f93-152">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="f1f93-153">Pełny Schemat pliku *Template. JSON* znajduje się w [magazynie schematów JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="f1f93-153">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="f1f93-154">Aby uzyskać więcej informacji na temat pliku *Template. JSON* , zobacz stronę [typu tworzenia szablonów programu dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="f1f93-154">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="f1f93-155">Teraz, gdy masz prawidłowy plik _Template. config/Template. JSON_ , szablon jest gotowy do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="f1f93-155">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="f1f93-156">Przed zainstalowaniem szablonu upewnij się, że usunięto wszystkie foldery i pliki dodatkowe pliki, które nie mają być dołączone do szablonu, takie jak foldery _bin_ lub _obj_ .</span><span class="sxs-lookup"><span data-stu-id="f1f93-156">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="f1f93-157">W terminalu przejdź do folderu _consoleasync_ i uruchom `dotnet new -i .\`, aby zainstalować szablon znajdujący się w bieżącym folderze.</span><span class="sxs-lookup"><span data-stu-id="f1f93-157">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="f1f93-158">Jeśli używasz systemu operacyjnego Linux lub MacOS, użyj ukośnika: `dotnet new -i ./`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-158">If you're using a Linux or MacOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="f1f93-159">To polecenie wyświetla listę zainstalowanych szablonów, które powinny obejmować użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f1f93-159">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\consoleasync> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

### <a name="test-the-project-template"></a><span data-ttu-id="f1f93-160">Testowanie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="f1f93-160">Test the project template</span></span>

<span data-ttu-id="f1f93-161">Teraz, gdy masz zainstalowany szablon elementu, przetestuj go.</span><span class="sxs-lookup"><span data-stu-id="f1f93-161">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="f1f93-162">Przejdź do folderu _test_ i Utwórz nową aplikację konsolową z `dotnet new consoleasync`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-162">Navigate to the _test_ folder and create a new console application with `dotnet new consoleasync`.</span></span> <span data-ttu-id="f1f93-163">Spowoduje to wygenerowanie projektu roboczego, który można łatwo przetestować przy użyciu polecenia `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-163">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="f1f93-164">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="f1f93-164">Congratulations!</span></span> <span data-ttu-id="f1f93-165">Szablon projektu został utworzony i wdrożony za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f1f93-165">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="f1f93-166">W ramach przygotowania do następnej części tej serii samouczków należy odinstalować utworzony szablon.</span><span class="sxs-lookup"><span data-stu-id="f1f93-166">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="f1f93-167">Pamiętaj, aby usunąć wszystkie pliki z folderu _testowego_ .</span><span class="sxs-lookup"><span data-stu-id="f1f93-167">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="f1f93-168">Spowoduje to powrót do stanu czystego gotowego do następnej głównej sekcji tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="f1f93-168">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="f1f93-169">Odinstaluj szablon</span><span class="sxs-lookup"><span data-stu-id="f1f93-169">Uninstall the template</span></span>

<span data-ttu-id="f1f93-170">Ponieważ szablon został zainstalowany przy użyciu ścieżki pliku, należy go odinstalować z **bezwzględną** ścieżką pliku.</span><span class="sxs-lookup"><span data-stu-id="f1f93-170">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="f1f93-171">Listę zainstalowanych szablonów można wyświetlić, uruchamiając polecenie `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-171">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="f1f93-172">Szablon powinien zostać wyświetlony jako ostatni.</span><span class="sxs-lookup"><span data-stu-id="f1f93-172">Your template should be listed last.</span></span> <span data-ttu-id="f1f93-173">Użyj podanej ścieżki, aby odinstalować szablon przy użyciu polecenia `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="f1f93-173">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

```console
C:\working> dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="f1f93-174">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f1f93-174">Next steps</span></span>

<span data-ttu-id="f1f93-175">W tym samouczku utworzono szablon projektu.</span><span class="sxs-lookup"><span data-stu-id="f1f93-175">In this tutorial, you created a project template.</span></span> <span data-ttu-id="f1f93-176">Aby dowiedzieć się, jak spakować szablon elementu i projektu do łatwego w użyciu pliku, Kontynuuj tę serię samouczków.</span><span class="sxs-lookup"><span data-stu-id="f1f93-176">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1f93-177">Tworzenie pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="f1f93-177">Create a template pack</span></span>](cli-templates-create-template-pack.md)
