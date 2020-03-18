---
title: Tworzenie pakietu szablonów dla dotnet nowy
description: Dowiedz się jak utworzyć plik csproj, który stworzy pakiet szablonów dla dotnet nowego polecenia.
author: thraka
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5bc926861dd6a501d7c2d24bd5f7c4116cc78b2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503492"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="36e17-103">Samouczek: Tworzenie pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="36e17-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="36e17-104">Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projekty, pliki, a nawet zasoby.</span><span class="sxs-lookup"><span data-stu-id="36e17-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="36e17-105">Ten samouczek jest częścią trzeciej serii, która uczy, jak tworzyć, instalować i odinstalowywać szablony do użycia z poleceniem. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="36e17-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="36e17-106">W tej części serii dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="36e17-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="36e17-107">Tworzenie \*projektu .csproj do tworzenia pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="36e17-107">Create a \*.csproj project to build a template pack</span></span>
> * <span data-ttu-id="36e17-108">Konfigurowanie pliku projektu do pakowania</span><span class="sxs-lookup"><span data-stu-id="36e17-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="36e17-109">Instalowanie szablonu z pliku pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="36e17-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="36e17-110">Odinstalowywanie szablonu według identyfikatora pakietu</span><span class="sxs-lookup"><span data-stu-id="36e17-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36e17-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="36e17-111">Prerequisites</span></span>

* <span data-ttu-id="36e17-112">Ukończ [część 1](cli-templates-create-item-template.md) i [część 2](cli-templates-create-project-template.md) tej serii samouczków.</span><span class="sxs-lookup"><span data-stu-id="36e17-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="36e17-113">Ten samouczek używa dwóch szablonów utworzonych w pierwszych dwóch częściach tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="36e17-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="36e17-114">Można użyć innego szablonu, o ile skopiujesz szablon jako folder do folderu _working\templates.\\ _</span><span class="sxs-lookup"><span data-stu-id="36e17-114">You can use a different template as long as you copy the template, as a folder, into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="36e17-115">Otwórz terminal i przejdź do folderu _\\ roboczego._</span><span class="sxs-lookup"><span data-stu-id="36e17-115">Open a terminal and navigate to the _working\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="36e17-116">Tworzenie projektu pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="36e17-116">Create a template pack project</span></span>

<span data-ttu-id="36e17-117">Pakiet szablonów to jeden lub więcej szablonów zapakowanych do pliku.</span><span class="sxs-lookup"><span data-stu-id="36e17-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="36e17-118">Podczas instalowania lub odinstalowywania pakietu wszystkie szablony zawarte w pakiecie są odpowiednio dodawane lub usuwane.</span><span class="sxs-lookup"><span data-stu-id="36e17-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="36e17-119">Poprzednie części tej serii samouczków działały tylko z poszczególnymi szablonami.</span><span class="sxs-lookup"><span data-stu-id="36e17-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="36e17-120">Aby udostępnić niespakowany szablon, należy skopiować folder szablonu i zainstalować go za pośrednictwem tego folderu.</span><span class="sxs-lookup"><span data-stu-id="36e17-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="36e17-121">Ponieważ pakiet szablonów może mieć więcej niż jeden szablon i jest pojedynczym plikiem, udostępnianie jest łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="36e17-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="36e17-122">Pakiety szablonów są reprezentowane przez plik pakietu NuGet _(nupkg)._</span><span class="sxs-lookup"><span data-stu-id="36e17-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="36e17-123">I, podobnie jak każdy pakiet NuGet, można przekazać pakiet szablonów do źródła danych NuGet.</span><span class="sxs-lookup"><span data-stu-id="36e17-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="36e17-124">Polecenie `dotnet new -i` obsługuje instalowanie pakietu szablonów z źródła danych pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="36e17-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="36e17-125">Ponadto pakiet szablonów można zainstalować bezpośrednio z pliku _.nupkg._</span><span class="sxs-lookup"><span data-stu-id="36e17-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="36e17-126">Zwykle używasz pliku projektu C# do kompilowania kodu i tworzenia pliku binarnego.</span><span class="sxs-lookup"><span data-stu-id="36e17-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="36e17-127">Jednak projekt może również służyć do generowania pakietu szablonów.</span><span class="sxs-lookup"><span data-stu-id="36e17-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="36e17-128">Zmieniając ustawienia _.csproj_, możesz uniemożliwić mu kompilowanie dowolnego kodu i zamiast tego uwzględnić wszystkie zasoby szablonów jako zasoby.</span><span class="sxs-lookup"><span data-stu-id="36e17-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="36e17-129">Po skonstruowaniu tego projektu tworzy pakiet szablonów NuGet pakietu.</span><span class="sxs-lookup"><span data-stu-id="36e17-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="36e17-130">Utworzony pakiet będzie zawierał [szablon elementu](cli-templates-create-item-template.md) i [szablon pakietu](cli-templates-create-project-template.md) utworzony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="36e17-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="36e17-131">Ponieważ pogrupowaliśmy dwa szablony w folderze _working\templates,\\ _ możemy użyć folderu _roboczego_ dla pliku _csproj._</span><span class="sxs-lookup"><span data-stu-id="36e17-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="36e17-132">W terminalu przejdź do folderu _roboczego._</span><span class="sxs-lookup"><span data-stu-id="36e17-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="36e17-133">Utwórz nowy projekt i `templatepack` ustaw nazwę i folder wyjściowy na bieżący folder.</span><span class="sxs-lookup"><span data-stu-id="36e17-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

<span data-ttu-id="36e17-134">Parametr `-n` ustawia nazwę pliku _csproj_ na _templatepack.csproj_.</span><span class="sxs-lookup"><span data-stu-id="36e17-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_.</span></span> <span data-ttu-id="36e17-135">Parametr `-o` tworzy pliki w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="36e17-135">The `-o` parameter creates the files in the current directory.</span></span> <span data-ttu-id="36e17-136">Powinien zostać wyświetlony wynik podobny do następującego wyjścia.</span><span class="sxs-lookup"><span data-stu-id="36e17-136">You should see a result similar to the following output.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="36e17-137">Następnie otwórz plik _templatepack.csproj_ w swoim ulubionym edytorze i zastąp zawartość następującym plikiem XML:</span><span class="sxs-lookup"><span data-stu-id="36e17-137">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

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

<span data-ttu-id="36e17-138">Ustawienia `<PropertyGroup>` w powyższym pliku XML są podzielone na trzy grupy.</span><span class="sxs-lookup"><span data-stu-id="36e17-138">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="36e17-139">Pierwsza grupa zajmuje się właściwości wymagane dla pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="36e17-139">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="36e17-140">Trzy `<Package` ustawienia mają do czynienia z nuget właściwości pakietu do identyfikowania pakietu w kanale informacyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="36e17-140">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="36e17-141">W szczególności `<PackageId>` wartość jest używana do odinstalowania pakietu szablonów o pojedynczej nazwie zamiast ścieżki katalogu.</span><span class="sxs-lookup"><span data-stu-id="36e17-141">Specifically the `<PackageId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="36e17-142">Może również służyć do instalowania pakietu szablonów z nuget źródła danych.</span><span class="sxs-lookup"><span data-stu-id="36e17-142">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="36e17-143">Pozostałe ustawienia, `<Title>` takie `<PackageTags>` jak i mają do czynienia z metadanych wyświetlanych w kanale informacyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="36e17-143">The remaining settings such as `<Title>` and `<PackageTags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="36e17-144">Aby uzyskać więcej informacji na temat ustawień NuGet, zobacz [NuGet i MSBuild właściwości](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="36e17-144">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="36e17-145">Ustawienie `<TargetFramework>` musi być ustawione tak, aby MSBuild będzie działać poprawnie po uruchomieniu polecenia pack do kompilacji i spakowania projektu.</span><span class="sxs-lookup"><span data-stu-id="36e17-145">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="36e17-146">Ostatnie trzy ustawienia mają do czynienia z konfigurowaniem projektu poprawnie, aby uwzględnić szablony w odpowiednim folderze w pakiecie NuGet po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="36e17-146">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="36e17-147">Zawiera `<ItemGroup>` dwa ustawienia.</span><span class="sxs-lookup"><span data-stu-id="36e17-147">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="36e17-148">Po `<Content>` pierwsze, ustawienie zawiera wszystko w folderze _szablonów_ jako zawartość.</span><span class="sxs-lookup"><span data-stu-id="36e17-148">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="36e17-149">Jest również ustawiona, aby wykluczyć dowolny folder _bin_ lub _folder obj,_ aby zapobiec uwzględnieniu skompilowanych kodów (jeśli zostały przetestowane i skompilowane szablony).</span><span class="sxs-lookup"><span data-stu-id="36e17-149">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="36e17-150">Po `<Compile>` drugie, ustawienie wyklucza wszystkie pliki kodu ze kompilowania bez względu na to, gdzie się znajdują.</span><span class="sxs-lookup"><span data-stu-id="36e17-150">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="36e17-151">To ustawienie zapobiega próbie skompilowania kodu w hierarchii _folderów szablonów_ przez projekt używany do tworzenia pakietu szablonów.</span><span class="sxs-lookup"><span data-stu-id="36e17-151">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="36e17-152">Tworzenie i instalowanie</span><span class="sxs-lookup"><span data-stu-id="36e17-152">Build and install</span></span>

<span data-ttu-id="36e17-153">Zapisz ten plik, a następnie uruchom polecenie pack</span><span class="sxs-lookup"><span data-stu-id="36e17-153">Save this file and then run the pack command</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="36e17-154">To polecenie stworzy projekt i utworzy pakiet NuGet w folderze To powinno być _folder emanuje\bin\Debug._</span><span class="sxs-lookup"><span data-stu-id="36e17-154">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```dotnetcli
dotnet pack
```

```console
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="36e17-155">Następnie zainstaluj plik pakietu szablonów za `dotnet new -i PATH_TO_NUPKG_FILE` pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="36e17-155">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

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

<span data-ttu-id="36e17-156">Jeśli pakiet NuGet został przekazany do źródła danych NuGet, można użyć `dotnet new -i PACKAGEID` polecenia, `PACKAGEID` gdzie jest taki sam jak `<PackageId>` ustawienie z pliku _.csproj._</span><span class="sxs-lookup"><span data-stu-id="36e17-156">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="36e17-157">Ten identyfikator pakietu jest taki sam jak identyfikator pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="36e17-157">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="36e17-158">Odinstalowywanie pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="36e17-158">Uninstall the template pack</span></span>

<span data-ttu-id="36e17-159">Bez względu na to, jak zainstalowano pakiet szablonów, z plikiem _.nupkg_ bezpośrednio lub przez nuget kanału informacyjnego, usunięcie pakietu szablonów jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="36e17-159">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="36e17-160">Użyj `<PackageId>` szablonu, który chcesz odinstalować.</span><span class="sxs-lookup"><span data-stu-id="36e17-160">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="36e17-161">Można uzyskać listę szablonów, które są `dotnet new -u` instalowane przez uruchomienie polecenia.</span><span class="sxs-lookup"><span data-stu-id="36e17-161">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

```dotnetcli
dotnet new -u
```

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
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

<span data-ttu-id="36e17-162">Uruchom, `dotnet new -u AdatumCorporation.Utility.Templates` aby odinstalować szablon.</span><span class="sxs-lookup"><span data-stu-id="36e17-162">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="36e17-163">Polecenie `dotnet new` wygeneruje informacje pomocy, które powinny pominąć szablony, które zostały wcześniej zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="36e17-163">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="36e17-164">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="36e17-164">Congratulations!</span></span> <span data-ttu-id="36e17-165">zainstalowano i odinstalowałeś pakiet szablonów.</span><span class="sxs-lookup"><span data-stu-id="36e17-165">you've installed and uninstalled a template pack.</span></span>

## <a name="next-steps"></a><span data-ttu-id="36e17-166">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="36e17-166">Next steps</span></span>

<span data-ttu-id="36e17-167">Aby dowiedzieć się więcej o szablonach, z których większość już się nauczyłeś, zobacz nowy artykuł [Szablony niestandardowe dla dotnet.](../tools/custom-templates.md)</span><span class="sxs-lookup"><span data-stu-id="36e17-167">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="36e17-168">dotnet/templating GitHub repo Wiki</span><span class="sxs-lookup"><span data-stu-id="36e17-168">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="36e17-169">dotnet/dotnet-template-samples GitHub repo</span><span class="sxs-lookup"><span data-stu-id="36e17-169">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="36e17-170">*schemat template.json* w Sklepie Schematów JSON</span><span class="sxs-lookup"><span data-stu-id="36e17-170">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
