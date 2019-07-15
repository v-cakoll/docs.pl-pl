---
title: Utwórz nowy szablon projektu służący do dotnet
description: Dowiedz się, jak utworzyć szablon projektu służący do nowego polecenia dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 31a6189c0126d6dff000bb84978c1527dbe4e2ae
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877181"
---
# <a name="tutorial-create-a-project-template"></a><span data-ttu-id="f48b3-103">Samouczek: Tworzenie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="f48b3-103">Tutorial: Create a project template</span></span>

<span data-ttu-id="f48b3-104">Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projektów, plików i nawet zasobów.</span><span class="sxs-lookup"><span data-stu-id="f48b3-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="f48b3-105">Niniejszy samouczek jest drugą częścią serii, pokazujący sposób tworzenia, instalowanie i odinstalowywanie szablonów do użytku z programem `dotnet new` polecenia.</span><span class="sxs-lookup"><span data-stu-id="f48b3-105">This tutorial is part two of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="f48b3-106">W tej części serii dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="f48b3-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="f48b3-107">Tworzenie zasobów szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="f48b3-107">Create the resources of a project template</span></span>
> * <span data-ttu-id="f48b3-108">Utwórz folder konfiguracji szablonu i pliku</span><span class="sxs-lookup"><span data-stu-id="f48b3-108">Create the template config folder and file</span></span>
> * <span data-ttu-id="f48b3-109">Zainstaluj szablon ze ścieżki plików</span><span class="sxs-lookup"><span data-stu-id="f48b3-109">Install a template from a file path</span></span>
> * <span data-ttu-id="f48b3-110">Testowanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="f48b3-110">Test an item template</span></span>
> * <span data-ttu-id="f48b3-111">Odinstaluj szablon elementu</span><span class="sxs-lookup"><span data-stu-id="f48b3-111">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f48b3-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f48b3-112">Prerequisites</span></span>

* <span data-ttu-id="f48b3-113">Pełne [część 1](cli-templates-create-item-template.md) z tej serii samouczka.</span><span class="sxs-lookup"><span data-stu-id="f48b3-113">Complete [part 1](cli-templates-create-item-template.md) of this tutorial series.</span></span>
* <span data-ttu-id="f48b3-114">Otwórz terminal i przejdź do _working\templates\\_  folderu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-114">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-project-template"></a><span data-ttu-id="f48b3-115">Tworzenie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="f48b3-115">Create a project template</span></span>

<span data-ttu-id="f48b3-116">Projekt szablony produktu gotowe do uruchomienia projektów, które ułatwiają użytkownikom na początek z zestawu roboczego kodu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-116">Project templates produce ready-to-run projects that make it easy for users to start with a working set of code.</span></span> <span data-ttu-id="f48b3-117">.NET core zawiera kilka szablonów projektu, np. aplikację konsolową w języku lub biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="f48b3-117">.NET Core includes a few project templates such as a console application or a class library.</span></span> <span data-ttu-id="f48b3-118">W tym przykładzie utworzysz nowy projekt konsoli, która umożliwia C# 8.0 i tworzy `async main` punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="f48b3-118">In this example, you'll create a new console project that enables C# 8.0 and produces an `async main` entry point.</span></span>

<span data-ttu-id="f48b3-119">W terminalu przejdź do _working\templates\\_  folderze i utworzyć nowy podfolder o nazwie _consoleasync_.</span><span class="sxs-lookup"><span data-stu-id="f48b3-119">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _consoleasync_.</span></span> <span data-ttu-id="f48b3-120">Wprowadź podfolderu, a następnie uruchom `dotnet new console` do generowania aplikacji konsoli standardowej.</span><span class="sxs-lookup"><span data-stu-id="f48b3-120">Enter the subfolder and run `dotnet new console` to generate the standard console application.</span></span> <span data-ttu-id="f48b3-121">Pliki tworzone przez ten szablon, aby utworzyć nowy szablon będzie edycji.</span><span class="sxs-lookup"><span data-stu-id="f48b3-121">You'll be editing the files produced by this template to create a new template.</span></span>

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a><span data-ttu-id="f48b3-122">Modyfikowanie pliku Program.cs</span><span class="sxs-lookup"><span data-stu-id="f48b3-122">Modify Program.cs</span></span>

<span data-ttu-id="f48b3-123">Otwórz _program.cs_ pliku.</span><span class="sxs-lookup"><span data-stu-id="f48b3-123">Open up the _program.cs_ file.</span></span> <span data-ttu-id="f48b3-124">Projekt konsoli nie Użyj punktu wejścia asynchroniczne, więc dodać.</span><span class="sxs-lookup"><span data-stu-id="f48b3-124">The console project doesn't use an asynchronous entry point, so let's add that.</span></span> <span data-ttu-id="f48b3-125">Zmień swój kod do następujących, a następnie zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="f48b3-125">Change your code to the following and save the file:</span></span>

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

## <a name="modify-consoleasynccsproj"></a><span data-ttu-id="f48b3-126">Modyfikowanie consoleasync.csproj</span><span class="sxs-lookup"><span data-stu-id="f48b3-126">Modify consoleasync.csproj</span></span>

<span data-ttu-id="f48b3-127">Zaktualizujmy C# wersji językowej projektu używa do wersji 8.0.</span><span class="sxs-lookup"><span data-stu-id="f48b3-127">Let's update the C# language version the project uses to version 8.0.</span></span> <span data-ttu-id="f48b3-128">Edytuj _consoleasync.csproj_ pliku i Dodaj `<LangVersion>` ustawienie `<PropertyGroup>` węzła.</span><span class="sxs-lookup"><span data-stu-id="f48b3-128">Edit the _consoleasync.csproj_ file and add the `<LangVersion>` setting to a `<PropertyGroup>` node.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a><span data-ttu-id="f48b3-129">Skompiluj projekt</span><span class="sxs-lookup"><span data-stu-id="f48b3-129">Build the project</span></span>

<span data-ttu-id="f48b3-130">Przed ukończeniem szablonu projektu należy przetestować ją, aby upewnić się, że kompiluje i działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="f48b3-130">Before you complete a project template, you should test it to make sure it compiles and runs correctly.</span></span> <span data-ttu-id="f48b3-131">W terminalu Uruchom `dotnet run` polecenia i powinien zostać wyświetlony następujący komunikat:</span><span class="sxs-lookup"><span data-stu-id="f48b3-131">In your terminal, run the `dotnet run` command and you should see the following output:</span></span>

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="f48b3-132">Możesz usunąć _obj_ i _bin_ foldery utworzone za pomocą `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="f48b3-132">You can delete the _obj_ and _bin_ folders created by using `dotnet run`.</span></span> <span data-ttu-id="f48b3-133">Usunięcie tych plików gwarantuje, że szablon zawiera tylko pliki związane z szablonu i nie wszystkie pliki wynik akcji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f48b3-133">Deleting these files ensures your template only includes the files related to your template and not any files that result of a build action.</span></span>

<span data-ttu-id="f48b3-134">Teraz, gdy zawartość utworzony szablon, musisz utworzyć konfiguracji szablonu w folderze głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-134">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="f48b3-135">Tworzenie konfiguracji szablonu</span><span class="sxs-lookup"><span data-stu-id="f48b3-135">Create the template config</span></span>

<span data-ttu-id="f48b3-136">Szablony są rozpoznawane w programie .NET Core, przez plik specjalny folder i konfiguracji, który istnieje w katalogu głównym szablonu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-136">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="f48b3-137">W tym samouczku folderu szablon znajduje się w _working\templates\consoleasync\\_ .</span><span class="sxs-lookup"><span data-stu-id="f48b3-137">In this tutorial, your template folder is located at _working\templates\consoleasync\\_.</span></span>

<span data-ttu-id="f48b3-138">Podczas tworzenia szablonu, wszystkie pliki i foldery w folderze szablonu są dołączane jako część szablonu z wyjątkiem folder konfiguracji specjalnych.</span><span class="sxs-lookup"><span data-stu-id="f48b3-138">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="f48b3-139">Ten folder konfiguracji nosi nazwę _. template.config_.</span><span class="sxs-lookup"><span data-stu-id="f48b3-139">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="f48b3-140">Najpierw utwórz nowy podfolder o nazwie _. template.config_, wprowadź go.</span><span class="sxs-lookup"><span data-stu-id="f48b3-140">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="f48b3-141">Następnie utwórz nowy plik o nazwie _template.json_.</span><span class="sxs-lookup"><span data-stu-id="f48b3-141">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="f48b3-142">Twoja struktura folderów powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f48b3-142">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

<span data-ttu-id="f48b3-143">Otwórz _template.json_ tekstem ulubionym edytorze i wklej następujący kod json kod i zapisz go:</span><span class="sxs-lookup"><span data-stu-id="f48b3-143">Open the _template.json_ with your favorite text editor and paste in the following json code and save it:</span></span>

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

<span data-ttu-id="f48b3-144">Ten plik konfiguracji zawiera wszystkie ustawienia dla szablonu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-144">This config file contains all of the settings for your template.</span></span> <span data-ttu-id="f48b3-145">Widać podstawowe ustawienia, takie jak `name` i `shortName` , ale również istnieje `tags/type` wartość, która jest równa `project`.</span><span class="sxs-lookup"><span data-stu-id="f48b3-145">You can see the basic settings such as `name` and `shortName` but also there's a `tags/type` value that's set to `project`.</span></span> <span data-ttu-id="f48b3-146">Określa szablon jako szablon projektu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-146">This designates your template as a project template.</span></span> <span data-ttu-id="f48b3-147">Nie ma żadnych ograniczeń na typ tworzonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-147">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="f48b3-148">`item` i `project` wartości to pospolite nazwy, które platformy .NET Core zaleca, aby użytkownicy z łatwością można filtrować szablonu są wyszukiwane.</span><span class="sxs-lookup"><span data-stu-id="f48b3-148">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="f48b3-149">`classifications` Element reprezentuje **tagi** kolumny zostanie wyświetlony po uruchomieniu `dotnet new` i Uzyskaj listę szablonów.</span><span class="sxs-lookup"><span data-stu-id="f48b3-149">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="f48b3-150">Użytkownicy mogą również przeszukiwać na podstawie klasyfikacji tagów.</span><span class="sxs-lookup"><span data-stu-id="f48b3-150">Users can also search based on classification tags.</span></span> <span data-ttu-id="f48b3-151">Nie należy mylić `tags` właściwości w pliku json z `classifications` lista tagów.</span><span class="sxs-lookup"><span data-stu-id="f48b3-151">Don't confuse the `tags` property in the json file with the `classifications` tags list.</span></span> <span data-ttu-id="f48b3-152">Są one dwie różne rzeczy Niestety o nazwie podobnie.</span><span class="sxs-lookup"><span data-stu-id="f48b3-152">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="f48b3-153">Pełnego schematu dla *template.json* plik znajduje się na [Store schematu JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="f48b3-153">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="f48b3-154">Aby uzyskać więcej informacji na temat *template.json* plików, zobacz [wiki szablonów dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="f48b3-154">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="f48b3-155">Teraz, gdy masz prawidłową _.template.config/template.json_ pliku, szablon będzie gotowy do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="f48b3-155">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="f48b3-156">Przed zainstalowaniem tego szablonu, upewnij się, że usuniesz wszelkie dodatkowe pliki folderów i plików, nie chcesz, zawarte w szablonie, takie jak _bin_ lub _obj_ folderów.</span><span class="sxs-lookup"><span data-stu-id="f48b3-156">Before you install the template, make sure that you delete any extra files folders and files you don't want included in your template, like the _bin_ or _obj_ folders.</span></span> <span data-ttu-id="f48b3-157">W terminalu przejdź do _consoleasync_ folderu i uruchom `dotnet new -i .\` zainstalował szablonu znajdujący się w bieżącym folderze.</span><span class="sxs-lookup"><span data-stu-id="f48b3-157">In your terminal, navigate to the _consoleasync_ folder and run `dotnet new -i .\` to install the template located at the current folder.</span></span> <span data-ttu-id="f48b3-158">Jeśli używasz systemu operacyjnego Linux lub MacOS, należy użyć ukośnika: `dotnet new -i ./`.</span><span class="sxs-lookup"><span data-stu-id="f48b3-158">If you're using a Linux or MacOS operating system, use a forward slash: `dotnet new -i ./`.</span></span>

<span data-ttu-id="f48b3-159">To polecenie wyświetla listę zainstalowane, szablony, które powinien zawierać należy do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="f48b3-159">This command outputs the list of templates installed, which should include yours.</span></span>

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

### <a name="test-the-project-template"></a><span data-ttu-id="f48b3-160">Testowanie szablonu projektu</span><span class="sxs-lookup"><span data-stu-id="f48b3-160">Test the project template</span></span>

<span data-ttu-id="f48b3-161">Teraz, gdy szablon elementu, który jest zainstalowany, należy go przetestować.</span><span class="sxs-lookup"><span data-stu-id="f48b3-161">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="f48b3-162">Przejdź do _test_ folderze i utworzyć nową aplikację konsoli przy użyciu `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="f48b3-162">Navigate to the _test_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="f48b3-163">Spowoduje to wygenerowanie projektu pracy, możesz łatwo przeprowadzić test za `dotnet run` polecenia.</span><span class="sxs-lookup"><span data-stu-id="f48b3-163">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

<span data-ttu-id="f48b3-164">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="f48b3-164">Congratulations!</span></span> <span data-ttu-id="f48b3-165">Utworzyć i wdrożyć szablon projektu za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f48b3-165">You created and deployed a project template with .NET Core.</span></span> <span data-ttu-id="f48b3-166">W ramach przygotowania do następnej części tej serii samouczków należy odinstalować szablon, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="f48b3-166">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="f48b3-167">Upewnij się usunąć wszystkie pliki z _test_ folderu zbyt.</span><span class="sxs-lookup"><span data-stu-id="f48b3-167">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="f48b3-168">To będzie wrócić do stanu czystego gotowy do następnej sekcji głównej części tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="f48b3-168">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

### <a name="uninstall-the-template"></a><span data-ttu-id="f48b3-169">Odinstaluj szablonu</span><span class="sxs-lookup"><span data-stu-id="f48b3-169">Uninstall the template</span></span>

<span data-ttu-id="f48b3-170">Ponieważ szablon został zainstalowany przy użyciu ścieżki pliku, należy odinstalować ją za pomocą **bezwzględne** ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="f48b3-170">Because you installed the template by using a file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="f48b3-171">Można wyświetlić listę szablonów zainstalowane, uruchamiając `dotnet new -u` polecenia.</span><span class="sxs-lookup"><span data-stu-id="f48b3-171">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="f48b3-172">Szablon powinien zostać wyświetlony ostatnio.</span><span class="sxs-lookup"><span data-stu-id="f48b3-172">Your template should be listed last.</span></span> <span data-ttu-id="f48b3-173">Użyj ścieżki wymienionymi w celu odinstalowania szablon, korzystając z `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="f48b3-173">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="f48b3-174">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f48b3-174">Next steps</span></span>

<span data-ttu-id="f48b3-175">W tym samouczku utworzono szablon projektu.</span><span class="sxs-lookup"><span data-stu-id="f48b3-175">In this tutorial, you created a project template.</span></span> <span data-ttu-id="f48b3-176">Aby dowiedzieć się, jak spakować szablonów elementów i projektów w pliku łatwy w użyciu, przejdź w tej serii samouczków.</span><span class="sxs-lookup"><span data-stu-id="f48b3-176">To learn how to package both the item and project templates into an easy-to-use file, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f48b3-177">Tworzenie szablonowego pakietu</span><span class="sxs-lookup"><span data-stu-id="f48b3-177">Create a template pack</span></span>](cli-templates-create-template-pack.md)
