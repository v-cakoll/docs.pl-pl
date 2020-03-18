---
title: Tworzenie szablonu projektu dla dotnet nowy
description: Dowiedz się, jak utworzyć szablon projektu dla polecenia dotnet new.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503537"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="5cda8-103">Samouczek: Tworzenie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="5cda8-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="5cda8-104">Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projekty, pliki, a nawet zasoby.</span><span class="sxs-lookup"><span data-stu-id="5cda8-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="5cda8-105">Ten samouczek jest częścią drugiej serii, która uczy, jak tworzyć, instalować `dotnet new` i odinstalowywać szablony do użycia z poleceniem.</span><span class="sxs-lookup"><span data-stu-id="5cda8-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="5cda8-106">W tej części serii dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="5cda8-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="5cda8-107">Tworzenie zasobów szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="5cda8-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="5cda8-108">Tworzenie folderu i pliku konfiguracji szablonu</span><span class="sxs-lookup"><span data-stu-id="5cda8-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="5cda8-109">Instalowanie szablonu ze ścieżki pliku</span><span class="sxs-lookup"><span data-stu-id="5cda8-109">Install a template from a file path</span></span>
> * <span data-ttu-id="5cda8-110">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="5cda8-110">Test an item template</span></span>
> * <span data-ttu-id="5cda8-111">Odinstalowywanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="5cda8-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5cda8-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5cda8-112">Prerequisites</span></span>

* <span data-ttu-id="5cda8-113">Ukończ [część 1](cli-templates-create-item-template.md) tej serii samouczków.</span><span class="sxs-lookup"><span data-stu-id="5cda8-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="5cda8-114">Otwórz terminal i przejdź do folderu _working\templates._</span><span class="sxs-lookup"><span data-stu-id="5cda8-114">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="5cda8-115">Tworzenie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="5cda8-115">Create a project template</span></span>

<span data-ttu-id="5cda8-116">Szablony projektów tworzą gotowe do uruchomienia projekty, które ułatwiają użytkownikom uruchamianie z roboczym zestawem kodu.</span><span class="sxs-lookup"><span data-stu-id="5cda8-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="5cda8-117">.NET Core zawiera kilka szablonów projektów, takich jak aplikacja konsoli lub biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="5cda8-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="5cda8-118">W tym przykładzie utworzysz nowy projekt konsoli, który umożliwia C# 8.0 i tworzy punkt `async main` wejścia.</span><span class="sxs-lookup"><span data-stu-id="5cda8-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="5cda8-119">W terminalu przejdź do folderu _working\templates_ i utwórz nowy podfolder o nazwie _consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="5cda8-119">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="5cda8-120">Wprowadź podfolder i `dotnet new console` uruchom, aby wygenerować standardową aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="5cda8-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="5cda8-121">Będziesz edytować pliki utworzone przez ten szablon, aby utworzyć nowy szablon.</span><span class="sxs-lookup"><span data-stu-id="5cda8-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="5cda8-122">Modyfikowanie Program.cs</span><span class="sxs-lookup"><span data-stu-id="5cda8-122">Modify Program.cs</span></span>

<span data-ttu-id="5cda8-123">Otwórz _plik program.cs._</span><span class="sxs-lookup"><span data-stu-id="5cda8-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="5cda8-124">Projekt konsoli nie używa asynchronicznego punktu wejścia, więc dodajmy to.</span><span class="sxs-lookup"><span data-stu-id="5cda8-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="5cda8-125">Zmień kod na następujący i zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="5cda8-125">Change your code to the following and save the file.</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="5cda8-126">Modyfikowanie consoleasync.csproj</span><span class="sxs-lookup"><span data-stu-id="5cda8-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="5cda8-127">Zaktualizujmy wersję języka C#, która jest używana do wersji 8.0.</span><span class="sxs-lookup"><span data-stu-id="5cda8-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="5cda8-128">Edytować plik _consoleasync.csproj_ i `<LangVersion>` dodać `<PropertyGroup>` ustawienie do węzła.</span><span class="sxs-lookup"><span data-stu-id="5cda8-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="5cda8-129">Kompilowanie projektu</span><span class="sxs-lookup"><span data-stu-id="5cda8-129">Build the project</span></span>

<span data-ttu-id="5cda8-130">Przed ukończeniem szablonu projektu należy przetestować go, aby upewnić się, że kompiluje i działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="5cda8-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span>

<span data-ttu-id="5cda8-131">W terminalu uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="5cda8-131">In your terminal, run the following command.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="5cda8-132">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5cda8-132">You get the following output.</span></span>

```console
Hello World with C# 8.0!
```

<span data-ttu-id="5cda8-133">Foldery _obj_ i _bin_ utworzone za `dotnet run`pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="5cda8-133">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="5cda8-134">Usunięcie tych plików gwarantuje, że szablon zawiera tylko pliki związane z szablonem, a nie wszystkie pliki, które są wynikiem akcji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5cda8-134">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="5cda8-135">Teraz, gdy masz zawartość szablonu utworzone, należy utworzyć konfigurację szablonu w folderze głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="5cda8-135">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="5cda8-136">Tworzenie konfiguracji szablonu</span><span class="sxs-lookup"><span data-stu-id="5cda8-136">Create the template config</span></span>

<span data-ttu-id="5cda8-137">Szablony są rozpoznawane w .NET Core przez specjalny folder i plik konfiguracyjny, które istnieją w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="5cda8-137">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="5cda8-138">W tym samouczku folder szablonu znajduje się w _obszarze roboczy\templates\consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="5cda8-138">In this tutorial, your template folder is located at _working\templates\consoleasync_.</span></span>

<span data-ttu-id="5cda8-139">Podczas tworzenia szablonu wszystkie pliki i foldery w folderze szablonu są uwzględniane jako część szablonu z wyjątkiem specjalnego folderu konfiguratornego.</span><span class="sxs-lookup"><span data-stu-id="5cda8-139">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="5cda8-140">Ten folder konfiguracyjny nosi nazwę _.template.config_.</span><span class="sxs-lookup"><span data-stu-id="5cda8-140">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="5cda8-141">Najpierw utwórz nowy podfolder o nazwie _.template.config_, wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="5cda8-141">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="5cda8-142">Następnie utwórz nowy plik o nazwie _template.json_.</span><span class="sxs-lookup"><span data-stu-id="5cda8-142">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="5cda8-143">Struktura folderów powinna wyglądać tak.</span><span class="sxs-lookup"><span data-stu-id="5cda8-143">Your folder structure should look like this.</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="5cda8-144">Otwórz _szablon.json_ z ulubionym edytorem tekstu i wklej w poniższym kodzie json i zapisz go.</span><span class="sxs-lookup"><span data-stu-id="5cda8-144">Open the _template.json_ with your favorite text editor and paste in the following json code and save it.</span></span>

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

<span data-ttu-id="5cda8-145">Ten plik konfiguracyjny zawiera wszystkie ustawienia szablonu.</span><span class="sxs-lookup"><span data-stu-id="5cda8-145">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="5cda8-146">Możesz zobaczyć podstawowe ustawienia, `name` `shortName` takie jak i `tags/type` ale jest też `project`wartość, która jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="5cda8-146">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="5cda8-147">Oznacza to szablon jako szablon projektu.</span><span class="sxs-lookup"><span data-stu-id="5cda8-147">This designates your template as a project template.</span></span> <span data-ttu-id="5cda8-148">Nie ma żadnych ograniczeń co do typu tworzonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="5cda8-148">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="5cda8-149">Wartości `item` `project` i są wspólne nazwy, które program .NET Core zaleca, dzięki czemu użytkownicy mogą łatwo filtrować typ szablonu, którego szukają.</span><span class="sxs-lookup"><span data-stu-id="5cda8-149">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="5cda8-150">Element `classifications` reprezentuje kolumnę **tagów** wyświetlaną `dotnet new` po uruchomieniu i uzyskanie listy szablonów.</span><span class="sxs-lookup"><span data-stu-id="5cda8-150">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="5cda8-151">Użytkownicy mogą również wyszukiwać na podstawie tagów klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="5cda8-151">Users can also search based on classification tags.</span></span> <span data-ttu-id="5cda8-152">Nie należy mylić `tags` właściwości w pliku json z listą `classifications` tagów.</span><span class="sxs-lookup"><span data-stu-id="5cda8-152">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="5cda8-153">Są to dwie różne rzeczy, które niestety mają podobną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5cda8-153">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="5cda8-154">Pełny schemat pliku *template.json* znajduje się w [Magazynie schematów JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="5cda8-154">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="5cda8-155">Aby uzyskać więcej informacji na temat pliku *template.json,* zobacz [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="5cda8-155">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="5cda8-156">Teraz, gdy masz prawidłowy plik _.template.config/template.json,_ szablon jest gotowy do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="5cda8-156">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="5cda8-157">Przed zainstalowaniem szablonu upewnij się, że usunięto wszystkie dodatkowe foldery plików i pliki, których nie chcesz uwzględnić w szablonie, takie jak _foldery bin_ lub _obj._</span><span class="sxs-lookup"><span data-stu-id="5cda8-157">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="5cda8-158">W terminalu przejdź do folderu _consoleasync_ i uruchom, `dotnet new -i .\` aby zainstalować szablon znajdujący się w bieżącym folderze.</span><span class="sxs-lookup"><span data-stu-id="5cda8-158">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="5cda8-159">Jeśli używasz systemu operacyjnego Linux lub macOS, użyj `dotnet new -i ./`ukośnika do przodu: .</span><span class="sxs-lookup"><span data-stu-id="5cda8-159">If you're using a Linux or macOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="5cda8-160">To polecenie wyświetla listę zainstalowanych szablonów, która powinna zawierać twoje.</span><span class="sxs-lookup"><span data-stu-id="5cda8-160">This command outputs the list of templates installed, which should include yours.</span></span>

```dotnetcli
dotnet new -i .\
```

<span data-ttu-id="5cda8-161">Otrzymasz dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="5cda8-161">You get output similar to the following.</span></span>

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

### <a name="test-the-project-template"></a><span data-ttu-id="5cda8-162">Testowanie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="5cda8-162">Test the project template</span></span>

<span data-ttu-id="5cda8-163">Teraz, gdy masz zainstalowany szablon elementu, przetestuj go.</span><span class="sxs-lookup"><span data-stu-id="5cda8-163">Now that you have an item template installed, test it.</span></span>

1. <span data-ttu-id="5cda8-164">Przejdź do folderu _testowego_</span><span class="sxs-lookup"><span data-stu-id="5cda8-164">Navigate to the _test_ folder</span></span>

1. <span data-ttu-id="5cda8-165">Utwórz nową aplikację konsoli za pomocą następującego polecenia, które `dotnet run` generuje projekt roboczy, który można łatwo przetestować za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5cda8-165">Create a new console application with the following command which generates a working project you can easily test with the `dotnet run` command.</span></span>

    ```dotnetcli
    dotnet new consoleasync
    ```

    <span data-ttu-id="5cda8-166">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5cda8-166">You get the following output.</span></span>

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. <span data-ttu-id="5cda8-167">Uruchom projekt za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5cda8-167">Run the project using the following command.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="5cda8-168">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5cda8-168">You get the following output.</span></span>

    ```console
    Hello World with C# 8.0!
    ```

<span data-ttu-id="5cda8-169">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="5cda8-169">Congratulations!</span></span> <span data-ttu-id="5cda8-170">Utworzono i wdrożono szablon projektu za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cda8-170">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="5cda8-171">W ramach przygotowań do następnej części tej serii samouczków należy odinstalować utworzony szablon.</span><span class="sxs-lookup"><span data-stu-id="5cda8-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="5cda8-172">Upewnij się, że wszystkie pliki z folderu _testowego_ też.</span><span class="sxs-lookup"><span data-stu-id="5cda8-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="5cda8-173">Spowoduje to powrót do stanu czystego gotowego do następnej głównej sekcji tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="5cda8-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="5cda8-174">Odinstalowywanie szablonu</span><span class="sxs-lookup"><span data-stu-id="5cda8-174">Uninstall the template</span></span>

<span data-ttu-id="5cda8-175">Ponieważ szablon został zainstalowany przy użyciu ścieżki pliku, należy go odinstalować przy **użyciu bezwzględnej** ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="5cda8-175">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="5cda8-176">Możesz zobaczyć listę szablonów zainstalowanych `dotnet new -u` przez uruchomienie polecenia.</span><span class="sxs-lookup"><span data-stu-id="5cda8-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="5cda8-177">Szablon powinien być wymieniony jako ostatni.</span><span class="sxs-lookup"><span data-stu-id="5cda8-177">Your template should be listed last.</span></span> <span data-ttu-id="5cda8-178">Użyj ścieżki wymienionej, aby odinstalować szablon za `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5cda8-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="5cda8-179">Otrzymasz dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="5cda8-179">You get output similar to the following.</span></span>

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

<span data-ttu-id="5cda8-180">Aby odinstalować szablon, uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="5cda8-180">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a><span data-ttu-id="5cda8-181">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5cda8-181">Next steps</span></span>

<span data-ttu-id="5cda8-182">W tym samouczku utworzono szablon projektu.</span><span class="sxs-lookup"><span data-stu-id="5cda8-182">In this tutorial, you created a project template.</span></span> <span data-ttu-id="5cda8-183">Aby dowiedzieć się, jak spakować szablony elementów i projektu do łatwego w użyciu pliku, kontynuuj tę serię samouczków.</span><span class="sxs-lookup"><span data-stu-id="5cda8-183">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cda8-184">Tworzenie pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="5cda8-184">Create a template pack</span></span>](cli-templates-create-template-pack.md)
