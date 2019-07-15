---
title: Utwórz nową szablonowego pakietu dla platformy dotnet
description: Dowiedz się, jak utworzyć plik csproj, który zostanie skompilowany szablonowego pakietu dla nowego polecenia dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: df8c33856195ba7feacd32203e4a885997b50ad2
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877184"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="247b8-103">Samouczek: Tworzenie szablonowego pakietu</span><span class="sxs-lookup"><span data-stu-id="247b8-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="247b8-104">Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projektów, plików i nawet zasobów.</span><span class="sxs-lookup"><span data-stu-id="247b8-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="247b8-105">Niniejszy samouczek jest trzecią częścią serii, pokazujący sposób tworzenia, instalowanie i odinstalowywanie szablonów do użytku z programem `dotnet new` polecenia.</span><span class="sxs-lookup"><span data-stu-id="247b8-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="247b8-106">W tej części serii dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="247b8-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="247b8-107">Utwórz projekt _.csproj\* tworzenie szablonowego pakietu</span><span class="sxs-lookup"><span data-stu-id="247b8-107">Create a _.csproj\* project to build a template pack</span></span>
> * <span data-ttu-id="247b8-108">Konfigurowanie pliku projektu do pakowania</span><span class="sxs-lookup"><span data-stu-id="247b8-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="247b8-109">Zainstaluj szablonu z pliku pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="247b8-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="247b8-110">Odinstaluj szablonu według Identyfikatora pakietu</span><span class="sxs-lookup"><span data-stu-id="247b8-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="247b8-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="247b8-111">Prerequisites</span></span>

* <span data-ttu-id="247b8-112">Pełne [część 1](cli-templates-create-item-template.md) i [część 2](cli-templates-create-project-template.md) z tej serii samouczka.</span><span class="sxs-lookup"><span data-stu-id="247b8-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="247b8-113">Ten samouczek używa dwóch szablonów utworzonych w dwie pierwsze części tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="247b8-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="247b8-114">Jest to możliwe, można użyć innego szablonu, tak długo, jak skopiować szablon jako folder do _working\templates\\_  folderu.</span><span class="sxs-lookup"><span data-stu-id="247b8-114">It's possible you can use a different template as long as you copy the template as a folder into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="247b8-115">Otwórz terminal i przejdź do _working\templates\\_  folderu.</span><span class="sxs-lookup"><span data-stu-id="247b8-115">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="247b8-116">Utwórz szablon projektu pakietu</span><span class="sxs-lookup"><span data-stu-id="247b8-116">Create a template pack project</span></span>

<span data-ttu-id="247b8-117">Pakiet szablonu jest co najmniej jeden szablon umieszczonych w pliku.</span><span class="sxs-lookup"><span data-stu-id="247b8-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="247b8-118">Podczas instalowania lub odinstalowania pakiet wszystkie szablony zawartych w pakiecie są dodane lub usunięte odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="247b8-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="247b8-119">Za pomocą szablonów poszczególnych działało tylko poprzedniej części tej serii samouczków.</span><span class="sxs-lookup"><span data-stu-id="247b8-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="247b8-120">Aby udostępnić szablon nieopakowanych, należy skopiować folder szablonów i zainstalować za pośrednictwem tego folderu.</span><span class="sxs-lookup"><span data-stu-id="247b8-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="247b8-121">Ponieważ szablonowego pakietu może mieć więcej niż jeden szablon w nim, a to pojedynczy plik, udostępnianie jest łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="247b8-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="247b8-122">Szablonowe pakiety są reprezentowane przez pakiet NuGet ( _.nupkg_) pliku.</span><span class="sxs-lookup"><span data-stu-id="247b8-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="247b8-123">I podobnie jak dowolny pakiet NuGet, możesz przekazać szablonowego pakietu do NuGet źródła danych.</span><span class="sxs-lookup"><span data-stu-id="247b8-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="247b8-124">`dotnet new -i` Polecenie obsługuje instalowanie pakietu szablonów z pakietu NuGet, źródła danych.</span><span class="sxs-lookup"><span data-stu-id="247b8-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="247b8-125">Ponadto można zainstalować szablonowego pakietu z _.nupkg_ pliku bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="247b8-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="247b8-126">Zazwyczaj używasz C# pliku projektu, aby skompilować kod i utworzyć plik binarny.</span><span class="sxs-lookup"><span data-stu-id="247b8-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="247b8-127">Jednak projektu można również wygenerować szablonowego pakietu.</span><span class="sxs-lookup"><span data-stu-id="247b8-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="247b8-128">Zmieniając ustawienia _.csproj_, mogą uniemożliwić kompilowanie kodu i zamiast tego zawierają wszystkie zasoby szablonów jako zasoby.</span><span class="sxs-lookup"><span data-stu-id="247b8-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="247b8-129">Podczas kompilowania projektu tworzy pakiet szablonu pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="247b8-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="247b8-130">Pakiet należy utworzyć będzie zawierać [szablon elementu](cli-templates-create-item-template.md) i [szablonu pakietu](cli-templates-create-project-template.md) utworzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="247b8-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="247b8-131">Firma Microsoft pogrupowane dwa szablony do _working\templates\\_  folderu, możemy użyć _pracy_ folder _.csproj_ pliku.</span><span class="sxs-lookup"><span data-stu-id="247b8-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="247b8-132">W terminalu przejdź do _pracy_ folderu.</span><span class="sxs-lookup"><span data-stu-id="247b8-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="247b8-133">Utwórz nowy projekt i ustaw nazwę na `templatepack` i folderze wyjściowym do bieżącego folderu.</span><span class="sxs-lookup"><span data-stu-id="247b8-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```console
dotnet new console -n templatepack -o .
```

<span data-ttu-id="247b8-134">`-n` Zestawów parametrów _.csproj_ nazwę pliku, aby _templatepack.csproj_ i `-o` parametrów tworzy pliki w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="247b8-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_ and the `-o` parameters creates the files in the current directory.</span></span> <span data-ttu-id="247b8-135">Powinien pojawić się wyniki podobne do następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="247b8-135">You should see a result similar to the following output.</span></span>

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="247b8-136">Następnie otwórz _templatepack.csproj_ plik w ulubionym edytorze i Zastąp zawartość następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="247b8-136">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

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

<span data-ttu-id="247b8-137">`<PropertyGroup>` Ustawienia w pliku XML powyżej jest dzielony na trzy grupy.</span><span class="sxs-lookup"><span data-stu-id="247b8-137">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="247b8-138">Pierwsza grupa zawiera właściwości wymagane dla pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="247b8-138">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="247b8-139">Trzy `<Package` ustawienia trzeba przy użyciu pakietu NuGet pakiet właściwości w celu zidentyfikowania pakietu na kanał informacyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="247b8-139">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="247b8-140">W szczególności `<PacakgeId>` wartości można odinstalować pakietu szablonu pod jedną nazwą, a nie ścieżkę katalogu.</span><span class="sxs-lookup"><span data-stu-id="247b8-140">Specifically the `<PacakgeId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="247b8-141">Może również służyć do zainstalowania pakietu szablonów z NuGet źródła danych.</span><span class="sxs-lookup"><span data-stu-id="247b8-141">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="247b8-142">Pozostałe ustawienia, takie jak `<Title>` i `<Tags>` trzeba z metadanymi wyświetlany na NuGet źródła danych.</span><span class="sxs-lookup"><span data-stu-id="247b8-142">The remaining settings such as `<Title>` and `<Tags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="247b8-143">Aby uzyskać więcej informacji o ustawieniach NuGet, zobacz [właściwości programu MSBuild i NuGet](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="247b8-143">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="247b8-144">`<TargetFramework>` Ustawienia należy wybrać opcję, aby po uruchomieniu polecenia pakietu, aby skompilować i pakietu projektu programu MSBuild będą działały poprawnie.</span><span class="sxs-lookup"><span data-stu-id="247b8-144">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="247b8-145">Ostatnie trzy ustawienia muszą poprawnie konfigurowania projektu do uwzględnienia w szablonach w odpowiedni folder w NuGet pakiet podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="247b8-145">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="247b8-146">`<ItemGroup>` Zawiera dwa ustawienia.</span><span class="sxs-lookup"><span data-stu-id="247b8-146">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="247b8-147">Po pierwsze, `<Content>` ustawienie obejmuje wszystko, co w _szablony_ folder jako zawartość.</span><span class="sxs-lookup"><span data-stu-id="247b8-147">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="247b8-148">Ma również ustawienie, aby wykluczać żadnych _bin_ folderu lub _obj_ folder, aby zapobiec kompilowania kodu (jeśli przetestowane i skompilowanych szablonów) zostaną uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="247b8-148">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="247b8-149">Drugi `<Compile>` wyklucza wszystkie pliki kodu z kompilacji, niezależnie od tego, gdzie są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="247b8-149">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="247b8-150">To ustawienie zapobiega projektu użyte do utworzenia pakietu szablonów się skompilować kod w _szablony_ hierarchii folderów.</span><span class="sxs-lookup"><span data-stu-id="247b8-150">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="247b8-151">Kompilowanie i instalacji</span><span class="sxs-lookup"><span data-stu-id="247b8-151">Build and install</span></span>

<span data-ttu-id="247b8-152">Zapisz ten plik, a następnie uruchom polecenie pakietu</span><span class="sxs-lookup"><span data-stu-id="247b8-152">Save this file and then run the pack command</span></span>

```console
dotnet pack
```

<span data-ttu-id="247b8-153">To polecenie skompilować projekt i Utwórz pakiet, w tym powinien być NuGet _working\bin\Debug_ folderu.</span><span class="sxs-lookup"><span data-stu-id="247b8-153">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="247b8-154">Następnie zainstaluj plik pakietu szablonu przy użyciu `dotnet new -i PATH_TO_NUPKG_FILE` polecenia.</span><span class="sxs-lookup"><span data-stu-id="247b8-154">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
```

<span data-ttu-id="247b8-155">Pakiet NuGet jest przekazywane do źródła NuGet, można użyć `dotnet new -i PACKAGEID` polecenie gdzie `PACKAGEID` jest taka sama jak `<PackageId>` z _.csproj_ pliku.</span><span class="sxs-lookup"><span data-stu-id="247b8-155">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="247b8-156">Ten identyfikator pakietu jest taki sam jak identyfikator pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="247b8-156">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="247b8-157">Odinstaluj pakiet szablonu</span><span class="sxs-lookup"><span data-stu-id="247b8-157">Uninstall the template pack</span></span>

<span data-ttu-id="247b8-158">Niezależnie od tego, jak zainstalowany pakiet szablonu, albo za pomocą _.nupkg_ pliku, bezpośrednio lub przez NuGet źródła danych, usuwanie pakietu szablonu jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="247b8-158">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="247b8-159">Użyj `<PackageId>` szablonu chcesz odinstalować.</span><span class="sxs-lookup"><span data-stu-id="247b8-159">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="247b8-160">Możesz uzyskać listę szablonów, które są zainstalowane, uruchamiając `dotnet new -u` polecenia.</span><span class="sxs-lookup"><span data-stu-id="247b8-160">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

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
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

<span data-ttu-id="247b8-161">Uruchom `dotnet new -u AdatumCorporation.Utility.Templates` odinstalować szablonu.</span><span class="sxs-lookup"><span data-stu-id="247b8-161">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="247b8-162">`dotnet new` Polecenie zwróci informacje, które należy pominąć znak szablonów została wcześniej zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="247b8-162">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="247b8-163">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="247b8-163">Congratulations!</span></span> <span data-ttu-id="247b8-164">już instalowana i odinstalowywana szablonowego pakietu.</span><span class="sxs-lookup"><span data-stu-id="247b8-164">you've installed and uninstalled a template pack.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="247b8-165">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="247b8-165">Next steps</span></span>

<span data-ttu-id="247b8-166">Aby dowiedzieć się więcej o szablonach, większość z nich już wiesz, zobacz [szablonów niestandardowych dla platformy dotnet nowe](../tools/custom-templates.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="247b8-166">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="247b8-167">repozytorium GitHub DotNet/szablonów witryny typu Wiki</span><span class="sxs-lookup"><span data-stu-id="247b8-167">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="247b8-168">repozytorium GitHub DotNet/dotnet-— przykłady szablonów</span><span class="sxs-lookup"><span data-stu-id="247b8-168">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="247b8-169">*Template.JSON* schemat w Store schematu JSON</span><span class="sxs-lookup"><span data-stu-id="247b8-169">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
