---
title: Tworzenie pakietu szablonów dla nowego dotnet
description: Dowiedz się, jak utworzyć plik CSPROJ, który będzie kompilować pakiet szablonów dla nowego polecenia dotnet.
author: thraka
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: a4723d6d63c5739123fad774bc75fae7c9fd6703
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340181"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="96075-103">Samouczek: Tworzenie pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="96075-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="96075-104">Za pomocą platformy .NET Core można tworzyć i wdrażać szablony generujące projekty, pliki, nawet zasoby.</span><span class="sxs-lookup"><span data-stu-id="96075-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="96075-105">Ten samouczek jest trzecią częścią serii, która uczy się, jak tworzyć, instalować i odinstalowywać szablony do użycia z poleceniem `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="96075-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="96075-106">W tej części serii dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="96075-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="96075-107">Utwórz projekt \*. csproj, aby skompilować pakiet szablonów</span><span class="sxs-lookup"><span data-stu-id="96075-107">Create a \*.csproj project to build a template pack</span></span>
> * <span data-ttu-id="96075-108">Konfigurowanie pliku projektu do pakowania</span><span class="sxs-lookup"><span data-stu-id="96075-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="96075-109">Instalowanie szablonu z pliku pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="96075-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="96075-110">Odinstalowywanie szablonu według identyfikatora pakietu</span><span class="sxs-lookup"><span data-stu-id="96075-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96075-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="96075-111">Prerequisites</span></span>

* <span data-ttu-id="96075-112">Ukończ [część 1](cli-templates-create-item-template.md) i [część 2](cli-templates-create-project-template.md) tej serii samouczków.</span><span class="sxs-lookup"><span data-stu-id="96075-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="96075-113">Ten samouczek używa dwóch szablonów utworzonych w pierwszych dwóch częściach tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="96075-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="96075-114">Możesz użyć innego szablonu, dopóki szablon zostanie skopiowany do folderu _working\templates\\_ .</span><span class="sxs-lookup"><span data-stu-id="96075-114">You can use a different template as long as you copy the template, as a folder, into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="96075-115">Otwórz Terminal i przejdź do folderu _roboczego\\_ .</span><span class="sxs-lookup"><span data-stu-id="96075-115">Open a terminal and navigate to the _working\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="96075-116">Tworzenie projektu pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="96075-116">Create a template pack project</span></span>

<span data-ttu-id="96075-117">Pakiet szablonów to jeden lub więcej szablonów pakowanych do pliku.</span><span class="sxs-lookup"><span data-stu-id="96075-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="96075-118">Podczas instalowania lub odinstalowywania pakietu wszystkie szablony zawarte w pakiecie są dodawane lub usuwane odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="96075-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="96075-119">Poprzednie części tej serii samouczków działały tylko z poszczególnymi szablonami.</span><span class="sxs-lookup"><span data-stu-id="96075-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="96075-120">Aby udostępnić niespakowany szablon, należy skopiować folder szablonu i zainstalować go za pośrednictwem tego folderu.</span><span class="sxs-lookup"><span data-stu-id="96075-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="96075-121">Ponieważ pakiet szablonów może mieć więcej niż jeden szablon w tym samym pliku, udostępnianie jest łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="96075-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="96075-122">Pakiety szablonów są reprezentowane przez plik pakietu NuGet ( _. nupkg_).</span><span class="sxs-lookup"><span data-stu-id="96075-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="96075-123">Podobnie jak każdy pakiet NuGet, można przekazać pakiet szablonów do źródła danych NuGet.</span><span class="sxs-lookup"><span data-stu-id="96075-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="96075-124">Polecenie `dotnet new -i` obsługuje instalowanie pakietu Template Pack z kanału informacyjnego pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="96075-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="96075-125">Ponadto można bezpośrednio zainstalować pakiet szablonów z pliku _. nupkg_ .</span><span class="sxs-lookup"><span data-stu-id="96075-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="96075-126">Zwykle plik C# projektu jest używany do kompilowania kodu i tworzenia danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="96075-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="96075-127">Jednak projekt może być również używany do generowania pakietu szablonów.</span><span class="sxs-lookup"><span data-stu-id="96075-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="96075-128">Zmieniając ustawienia elementu _. csproj_, można zapobiec kompilacji dowolnego kodu, a zamiast tego dołączyć wszystkie zasoby szablonów jako zasoby.</span><span class="sxs-lookup"><span data-stu-id="96075-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="96075-129">Po skompilowaniu tego projektu tworzy pakiet NuGet pakietu szablonów.</span><span class="sxs-lookup"><span data-stu-id="96075-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="96075-130">Tworzony pakiet będzie obejmował [szablon elementu](cli-templates-create-item-template.md) i [szablon pakietu](cli-templates-create-project-template.md) utworzony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="96075-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="96075-131">Ze względu na to, że dwa szablony są zgrupowane w folderze _working\templates\\_ , możemy użyć folderu _roboczego_ dla pliku _. csproj_ .</span><span class="sxs-lookup"><span data-stu-id="96075-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="96075-132">W terminalu przejdź do folderu _roboczego_ .</span><span class="sxs-lookup"><span data-stu-id="96075-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="96075-133">Utwórz nowy projekt i ustaw dla niego nazwę `templatepack` i folder wyjściowy do bieżącego folderu.</span><span class="sxs-lookup"><span data-stu-id="96075-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```dotnetcli
dotnet new console -n templatepack -o .
```

<span data-ttu-id="96075-134">Parametr `-n` ustawia nazwę pliku _. csproj_ na _templatepack. csproj_ , a `-o` parametry tworzy pliki w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="96075-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_ and the `-o` parameters creates the files in the current directory.</span></span> <span data-ttu-id="96075-135">Powinien zostać wyświetlony wynik podobny do następującego: dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="96075-135">You should see a result similar to the following output.</span></span>

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="96075-136">Następnie otwórz plik _templatepack. csproj_ w ulubionym edytorze i Zastąp zawartość następującym kodem XML:</span><span class="sxs-lookup"><span data-stu-id="96075-136">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

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

<span data-ttu-id="96075-137">Ustawienia `<PropertyGroup>` w pliku XML powyżej są podzielone na trzy grupy.</span><span class="sxs-lookup"><span data-stu-id="96075-137">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="96075-138">Pierwsza grupa zajmuje się właściwościami wymaganymi dla pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="96075-138">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="96075-139">Trzy `<Package` ustawienia muszą wykonać przy użyciu właściwości pakietu NuGet, aby zidentyfikować pakiet w źródle danych NuGet.</span><span class="sxs-lookup"><span data-stu-id="96075-139">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="96075-140">W celu odinstalowania pakietu Template Pack o pojedynczej nazwie zamiast ścieżki do katalogu zostanie użyta wartość `<PacakgeId>`.</span><span class="sxs-lookup"><span data-stu-id="96075-140">Specifically the `<PacakgeId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="96075-141">Można go również użyć do zainstalowania pakietu Template Pack ze źródła danych NuGet.</span><span class="sxs-lookup"><span data-stu-id="96075-141">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="96075-142">Pozostałe ustawienia, takie jak `<Title>` i `<Tags>`, muszą zrobić z metadanymi wyświetlanymi w źródle danych NuGet.</span><span class="sxs-lookup"><span data-stu-id="96075-142">The remaining settings such as `<Title>` and `<Tags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="96075-143">Aby uzyskać więcej informacji na temat ustawień NuGet, zobacz [Właściwości narzędzia NuGet i programu MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="96075-143">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="96075-144">Ustawienie `<TargetFramework>` musi być ustawione tak, aby program MSBuild działał prawidłowo po uruchomieniu polecenia Pack w celu skompilowania i spakowania projektu.</span><span class="sxs-lookup"><span data-stu-id="96075-144">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="96075-145">Ostatnie trzy ustawienia należy wykonać w celu poprawnego skonfigurowania projektu w celu uwzględnienia szablonów w odpowiednim folderze w pakiecie NuGet, gdy zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="96075-145">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="96075-146">`<ItemGroup>` zawiera dwa ustawienia.</span><span class="sxs-lookup"><span data-stu-id="96075-146">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="96075-147">Najpierw ustawienie `<Content>` obejmuje wszystko w folderze _templates_ jako zawartość.</span><span class="sxs-lookup"><span data-stu-id="96075-147">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="96075-148">Jest również ustawiony na wykluczenie dowolnego folderu _bin_ lub _obj_ , aby zapobiec dołączeniu kodu skompilowanego (w przypadku przetestowania i skompilowania szablonów).</span><span class="sxs-lookup"><span data-stu-id="96075-148">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="96075-149">Po drugie, ustawienie `<Compile>` wyklucza wszystkie pliki kodu z kompilacji niezależnie od tego, gdzie się znajdują.</span><span class="sxs-lookup"><span data-stu-id="96075-149">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="96075-150">To ustawienie uniemożliwia projekt używany do tworzenia pakietu szablonów na podstawie próby skompilowania kodu w hierarchii folderów _szablonów_ .</span><span class="sxs-lookup"><span data-stu-id="96075-150">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="96075-151">Kompiluj i zainstaluj</span><span class="sxs-lookup"><span data-stu-id="96075-151">Build and install</span></span>

<span data-ttu-id="96075-152">Zapisz ten plik, a następnie uruchom polecenie Pack</span><span class="sxs-lookup"><span data-stu-id="96075-152">Save this file and then run the pack command</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="96075-153">To polecenie spowoduje skompilowanie projektu i utworzenie pakietu NuGet w tym folderze _working\bin\Debug_ .</span><span class="sxs-lookup"><span data-stu-id="96075-153">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="96075-154">Następnie Zainstaluj plik pakietu szablonów przy użyciu polecenia `dotnet new -i PATH_TO_NUPKG_FILE`.</span><span class="sxs-lookup"><span data-stu-id="96075-154">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

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

<span data-ttu-id="96075-155">Jeśli pakiet NuGet został przekazany do źródła danych NuGet, można użyć polecenia `dotnet new -i PACKAGEID`, gdzie `PACKAGEID` jest taka sama jak wartość ustawienia `<PackageId>` z pliku _. csproj_ .</span><span class="sxs-lookup"><span data-stu-id="96075-155">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="96075-156">Ten identyfikator pakietu jest taki sam jak identyfikator pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="96075-156">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="96075-157">Odinstalowywanie pakietu szablonów</span><span class="sxs-lookup"><span data-stu-id="96075-157">Uninstall the template pack</span></span>

<span data-ttu-id="96075-158">Niezależnie od tego, jak został zainstalowany pakiet szablonów, z plikiem _. nupkg_ bezpośrednio lub przez źródło danych NuGet, usunięcie pakietu szablonu jest takie samo.</span><span class="sxs-lookup"><span data-stu-id="96075-158">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="96075-159">Użyj `<PackageId>` szablonu, który chcesz odinstalować.</span><span class="sxs-lookup"><span data-stu-id="96075-159">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="96075-160">Listę zainstalowanych szablonów można uzyskać, uruchamiając polecenie `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="96075-160">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

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

<span data-ttu-id="96075-161">Uruchom `dotnet new -u AdatumCorporation.Utility.Templates`, aby odinstalować szablon.</span><span class="sxs-lookup"><span data-stu-id="96075-161">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="96075-162">Polecenie `dotnet new` będzie wyprowadzać informacje pomocy, które powinny pominąć wcześniej zainstalowane szablony.</span><span class="sxs-lookup"><span data-stu-id="96075-162">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="96075-163">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="96075-163">Congratulations!</span></span> <span data-ttu-id="96075-164">Pakiet szablonów został zainstalowany i odinstalowany.</span><span class="sxs-lookup"><span data-stu-id="96075-164">you've installed and uninstalled a template pack.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="96075-165">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="96075-165">Next steps</span></span>

<span data-ttu-id="96075-166">Aby dowiedzieć się więcej o szablonach, z których większość już wiesz, zobacz [Szablony niestandardowe dla nowego](../tools/custom-templates.md) artykułu usługi dotnet.</span><span class="sxs-lookup"><span data-stu-id="96075-166">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="96075-167">Witryna typu wiki repozytorium usługi GitHub/tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="96075-167">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="96075-168">dotnet/dotnet-Template-przykłady repozytorium GitHub</span><span class="sxs-lookup"><span data-stu-id="96075-168">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* [<span data-ttu-id="96075-169">*szablon Template. JSON* w magazynie schematów JSON</span><span class="sxs-lookup"><span data-stu-id="96075-169">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
