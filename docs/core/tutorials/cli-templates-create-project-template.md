---
title: Utwórz szablon projektu dla nowego dotnet
description: Dowiedz się, jak utworzyć szablon projektu dla nowego polecenia dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503537"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="5f1ed-103">Samouczek: Tworzenie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="5f1ed-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="5f1ed-104">Za pomocą platformy .NET Core można tworzyć i wdrażać szablony generujące projekty, pliki, nawet zasoby.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="5f1ed-105">Ten samouczek jest drugą częścią serii, która zawiera informacje na temat tworzenia, instalowania i odinstalowywania szablonów do użycia z poleceniem `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="5f1ed-106">W tej części serii dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="5f1ed-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="5f1ed-107">Tworzenie zasobów szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="5f1ed-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="5f1ed-108">Tworzenie folderu i pliku konfiguracji szablonu</span><span class="sxs-lookup"><span data-stu-id="5f1ed-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="5f1ed-109">Instalowanie szablonu ze ścieżki pliku</span><span class="sxs-lookup"><span data-stu-id="5f1ed-109">Install a template from a file path</span></span>
> * <span data-ttu-id="5f1ed-110">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="5f1ed-110">Test an item template</span></span>
> * <span data-ttu-id="5f1ed-111">Odinstaluj szablon elementu</span><span class="sxs-lookup"><span data-stu-id="5f1ed-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f1ed-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5f1ed-112">Prerequisites</span></span>

* <span data-ttu-id="5f1ed-113">Ukończ [część 1](cli-templates-create-item-template.md) tej serii samouczków.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="5f1ed-114">Otwórz Terminal i przejdź do folderu _working\templates_ .</span><span class="sxs-lookup"><span data-stu-id="5f1ed-114">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="5f1ed-115">Utwórz szablon projektu</span><span class="sxs-lookup"><span data-stu-id="5f1ed-115">Create a project template</span></span>

<span data-ttu-id="5f1ed-116">Szablony projektów tworzą gotowe do uruchomienia projekty, które ułatwiają użytkownikom rozpoczęcie pracy z zestawem roboczym kodu.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="5f1ed-117">Platforma .NET Core zawiera kilka szablonów projektu, takich jak Aplikacja konsolowa lub Biblioteka klas.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="5f1ed-118">W tym przykładzie utworzysz nowy projekt konsoli, który umożliwia C# 8,0 i generuje punkt wejścia `async main`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="5f1ed-119">W terminalu przejdź do folderu _working\templates_ i Utwórz nowy podfolder o nazwie _consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-119">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="5f1ed-120">Wprowadź podfolder i uruchom `dotnet new console` w celu wygenerowania standardowej aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="5f1ed-121">Będziesz edytować pliki utworzone przez ten szablon w celu utworzenia nowego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="5f1ed-122">Modyfikuj Program.cs</span><span class="sxs-lookup"><span data-stu-id="5f1ed-122">Modify Program.cs</span></span>

<span data-ttu-id="5f1ed-123">Otwórz plik _program.cs_ .</span><span class="sxs-lookup"><span data-stu-id="5f1ed-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="5f1ed-124">Projekt konsoli nie używa asynchronicznego punktu wejścia, więc Dodajmy ten element.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="5f1ed-125">Zmień kod na następujący i Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-125">Change your code to the following and save the file.</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="5f1ed-126">Modyfikuj consoleasync. csproj</span><span class="sxs-lookup"><span data-stu-id="5f1ed-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="5f1ed-127">Zaktualizujmy wersję C# językową używaną przez ten projekt do wersji 8,0.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="5f1ed-128">Edytuj plik _consoleasync. csproj_ i Dodaj `<LangVersion>` ustawienia do węzła `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="5f1ed-129">Kompilowanie projektu</span><span class="sxs-lookup"><span data-stu-id="5f1ed-129">Build the project</span></span>

<span data-ttu-id="5f1ed-130">Przed ukończeniem szablonu projektu należy go przetestować, aby upewnić się, że kompiluje i działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span>

<span data-ttu-id="5f1ed-131">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-131">In your terminal, run the following command.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="5f1ed-132">Otrzymujesz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-132">You get the following output.</span></span>

```console
Hello World with C# 8.0!
```

<span data-ttu-id="5f1ed-133">Można usunąć foldery _obj_ i _bin_ utworzone przy użyciu `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-133">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="5f1ed-134">Usunięcie tych plików gwarantuje, że szablon zawiera tylko pliki powiązane z szablonem, a nie wszystkie pliki, które powodują akcję kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-134">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="5f1ed-135">Teraz, gdy masz już utworzoną zawartość szablonu, musisz utworzyć konfigurację szablonu w folderze głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-135">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="5f1ed-136">Utwórz konfigurację szablonu</span><span class="sxs-lookup"><span data-stu-id="5f1ed-136">Create the template config</span></span>

<span data-ttu-id="5f1ed-137">Szablony są rozpoznawane w programie .NET Core za pomocą specjalnego folderu i pliku konfiguracji, który istnieje w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-137">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="5f1ed-138">W tym samouczku folder szablonu znajduje się w lokalizacji _working\templates\consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-138">In this tutorial, your template folder is located at _working\templates\consoleasync_.</span></span>

<span data-ttu-id="5f1ed-139">Podczas tworzenia szablonu wszystkie pliki i foldery znajdujące się w folderze szablonów są uwzględniane jako część szablonu, z wyjątkiem folderu specjalnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-139">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="5f1ed-140">Ten folder konfiguracji ma nazwę _. Template. config_.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-140">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="5f1ed-141">Najpierw utwórz nowy podfolder o nazwie _. Template. config_, a następnie wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-141">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="5f1ed-142">Następnie utwórz nowy plik o nazwie _Template. JSON_.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-142">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="5f1ed-143">Struktura folderów powinna wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-143">Your folder structure should look like this.</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="5f1ed-144">Otwórz plik _Template. JSON_ przy użyciu ulubionego edytora tekstu i wklej go w poniższym kodzie JSON i Zapisz go.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-144">Open the _template.json_ with your favorite text editor and paste in the following json code and save it.</span></span>

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

<span data-ttu-id="5f1ed-145">Ten plik konfiguracji zawiera wszystkie ustawienia szablonu.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-145">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="5f1ed-146">Można zobaczyć podstawowe ustawienia, takie jak `name` i `shortName`, ale również istnieje `tags/type` wartość, która jest ustawiona na `project`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-146">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="5f1ed-147">Spowoduje to wyznaczenie szablonu jako szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-147">This designates your template as a project template.</span></span> <span data-ttu-id="5f1ed-148">Nie ma ograniczeń dotyczących typu tworzonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-148">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="5f1ed-149">Wartości `item` i `project` są typowymi nazwami zalecanymi przez platformę .NET Core, dzięki czemu użytkownicy mogą łatwo filtrować typ szukanego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-149">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="5f1ed-150">Element `classifications` reprezentuje kolumnę **Tagi** , która pojawia się po uruchomieniu `dotnet new` i wyświetleniu listy szablonów.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-150">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="5f1ed-151">Użytkownicy mogą również wyszukiwać w oparciu o znaczniki klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-151">Users can also search based on classification tags.</span></span> <span data-ttu-id="5f1ed-152">Nie należy mylić właściwości `tags` w pliku JSON z listą tagów `classifications`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-152">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="5f1ed-153">Te dwa różne rzeczy są uważane za podobne.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-153">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="5f1ed-154">Pełny Schemat pliku *Template. JSON* znajduje się w [magazynie schematów JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="5f1ed-154">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="5f1ed-155">Aby uzyskać więcej informacji na temat pliku *Template. JSON* , zobacz stronę [typu tworzenia szablonów programu dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="5f1ed-155">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="5f1ed-156">Teraz, gdy masz prawidłowy plik _Template. config/Template. JSON_ , szablon jest gotowy do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-156">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="5f1ed-157">Przed zainstalowaniem szablonu upewnij się, że usunięto wszystkie foldery i pliki dodatkowe pliki, które nie mają być dołączone do szablonu, takie jak foldery _bin_ lub _obj_ .</span><span class="sxs-lookup"><span data-stu-id="5f1ed-157">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="5f1ed-158">W terminalu przejdź do folderu _consoleasync_ i uruchom `dotnet new -i .\`, aby zainstalować szablon znajdujący się w bieżącym folderze.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-158">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="5f1ed-159">Jeśli używasz systemu operacyjnego Linux lub macOS, użyj ukośnika: `dotnet new -i ./`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-159">If you're using a Linux or macOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="5f1ed-160">To polecenie wyświetla listę zainstalowanych szablonów, które powinny obejmować użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-160">This command outputs the list of templates installed, which should include yours.</span></span>

```dotnetcli
dotnet new -i .\
```

<span data-ttu-id="5f1ed-161">Dane wyjściowe są podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-161">You get output similar to the following.</span></span>

```console
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

### <a name="test-the-project-template"></a><span data-ttu-id="5f1ed-162">Testowanie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="5f1ed-162">Test the project template</span></span>

<span data-ttu-id="5f1ed-163">Teraz, gdy masz zainstalowany szablon elementu, przetestuj go.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-163">Now that you have an item template installed, test it.</span></span>

1. <span data-ttu-id="5f1ed-164">Przejdź do folderu _testowego_</span><span class="sxs-lookup"><span data-stu-id="5f1ed-164">Navigate to the _test_ folder</span></span>

1. <span data-ttu-id="5f1ed-165">Utwórz nową aplikację konsolową przy użyciu następującego polecenia, które generuje projekt roboczy, który można łatwo przetestować przy użyciu polecenia `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-165">Create a new console application with the following command which generates a working project you can easily test with the `dotnet run` command.</span></span>

    ```dotnetcli
    dotnet new consoleasync
    ```

    <span data-ttu-id="5f1ed-166">Otrzymujesz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-166">You get the following output.</span></span>

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. <span data-ttu-id="5f1ed-167">Uruchom projekt przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-167">Run the project using the following command.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="5f1ed-168">Otrzymujesz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-168">You get the following output.</span></span>

    ```console
    Hello World with C# 8.0!
    ```

<span data-ttu-id="5f1ed-169">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="5f1ed-169">Congratulations!</span></span> <span data-ttu-id="5f1ed-170">Szablon projektu został utworzony i wdrożony za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-170">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="5f1ed-171">W ramach przygotowania do następnej części tej serii samouczków należy odinstalować utworzony szablon.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="5f1ed-172">Pamiętaj, aby usunąć wszystkie pliki z folderu _testowego_ .</span><span class="sxs-lookup"><span data-stu-id="5f1ed-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="5f1ed-173">Spowoduje to powrót do stanu czystego gotowego do następnej głównej sekcji tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="5f1ed-174">Odinstaluj szablon</span><span class="sxs-lookup"><span data-stu-id="5f1ed-174">Uninstall the template</span></span>

<span data-ttu-id="5f1ed-175">Ponieważ szablon został zainstalowany przy użyciu ścieżki pliku, należy go odinstalować z **bezwzględną** ścieżką pliku.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-175">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="5f1ed-176">Listę zainstalowanych szablonów można wyświetlić, uruchamiając polecenie `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="5f1ed-177">Szablon powinien zostać wyświetlony jako ostatni.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-177">Your template should be listed last.</span></span> <span data-ttu-id="5f1ed-178">Użyj podanej ścieżki, aby odinstalować szablon przy użyciu polecenia `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="5f1ed-179">Dane wyjściowe są podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-179">You get output similar to the following.</span></span>

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
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

<span data-ttu-id="5f1ed-180">Aby odinstalować szablon, uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-180">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="5f1ed-181">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5f1ed-181">Next steps</span></span>

<span data-ttu-id="5f1ed-182">W tym samouczku utworzono szablon projektu.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-182">In this tutorial, you created a project template.</span></span> <span data-ttu-id="5f1ed-183">Aby dowiedzieć się, jak spakować szablon elementu i projektu do łatwego w użyciu pliku, Kontynuuj tę serię samouczków.</span><span class="sxs-lookup"><span data-stu-id="5f1ed-183">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5f1ed-184">Tworzenie pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="5f1ed-184">Create a template pack</span></span>](cli-templates-create-template-pack.md)
