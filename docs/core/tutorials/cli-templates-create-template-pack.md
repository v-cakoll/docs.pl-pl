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
# <a name="tutorial-create-a-template-pack"></a>Samouczek: Tworzenie pakietu szablonów

Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projekty, pliki, a nawet zasoby. Ten samouczek jest częścią trzeciej serii, która uczy, jak tworzyć, instalować i odinstalowywać szablony do użycia z poleceniem. `dotnet new`

W tej części serii dowiesz się, jak:

> [!div class="checklist"]
>
> * Tworzenie \*projektu .csproj do tworzenia pakietu szablonów
> * Konfigurowanie pliku projektu do pakowania
> * Instalowanie szablonu z pliku pakietu NuGet
> * Odinstalowywanie szablonu według identyfikatora pakietu

## <a name="prerequisites"></a>Wymagania wstępne

* Ukończ [część 1](cli-templates-create-item-template.md) i [część 2](cli-templates-create-project-template.md) tej serii samouczków.

  Ten samouczek używa dwóch szablonów utworzonych w pierwszych dwóch częściach tego samouczka. Można użyć innego szablonu, o ile skopiujesz szablon jako folder do folderu _working\templates.\\ _

* Otwórz terminal i przejdź do folderu _\\ roboczego._

## <a name="create-a-template-pack-project"></a>Tworzenie projektu pakietu szablonów

Pakiet szablonów to jeden lub więcej szablonów zapakowanych do pliku. Podczas instalowania lub odinstalowywania pakietu wszystkie szablony zawarte w pakiecie są odpowiednio dodawane lub usuwane. Poprzednie części tej serii samouczków działały tylko z poszczególnymi szablonami. Aby udostępnić niespakowany szablon, należy skopiować folder szablonu i zainstalować go za pośrednictwem tego folderu. Ponieważ pakiet szablonów może mieć więcej niż jeden szablon i jest pojedynczym plikiem, udostępnianie jest łatwiejsze.

Pakiety szablonów są reprezentowane przez plik pakietu NuGet _(nupkg)._ I, podobnie jak każdy pakiet NuGet, można przekazać pakiet szablonów do źródła danych NuGet. Polecenie `dotnet new -i` obsługuje instalowanie pakietu szablonów z źródła danych pakietu NuGet. Ponadto pakiet szablonów można zainstalować bezpośrednio z pliku _.nupkg._

Zwykle używasz pliku projektu C# do kompilowania kodu i tworzenia pliku binarnego. Jednak projekt może również służyć do generowania pakietu szablonów. Zmieniając ustawienia _.csproj_, możesz uniemożliwić mu kompilowanie dowolnego kodu i zamiast tego uwzględnić wszystkie zasoby szablonów jako zasoby. Po skonstruowaniu tego projektu tworzy pakiet szablonów NuGet pakietu.

Utworzony pakiet będzie zawierał [szablon elementu](cli-templates-create-item-template.md) i [szablon pakietu](cli-templates-create-project-template.md) utworzony wcześniej. Ponieważ pogrupowaliśmy dwa szablony w folderze _working\templates,\\ _ możemy użyć folderu _roboczego_ dla pliku _csproj._

W terminalu przejdź do folderu _roboczego._ Utwórz nowy projekt i `templatepack` ustaw nazwę i folder wyjściowy na bieżący folder.

```dotnetcli
dotnet new console -n templatepack -o .
```

Parametr `-n` ustawia nazwę pliku _csproj_ na _templatepack.csproj_. Parametr `-o` tworzy pliki w bieżącym katalogu. Powinien zostać wyświetlony wynik podobny do następującego wyjścia.

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

Następnie otwórz plik _templatepack.csproj_ w swoim ulubionym edytorze i zastąp zawartość następującym plikiem XML:

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

Ustawienia `<PropertyGroup>` w powyższym pliku XML są podzielone na trzy grupy. Pierwsza grupa zajmuje się właściwości wymagane dla pakietu NuGet. Trzy `<Package` ustawienia mają do czynienia z nuget właściwości pakietu do identyfikowania pakietu w kanale informacyjnym NuGet. W szczególności `<PackageId>` wartość jest używana do odinstalowania pakietu szablonów o pojedynczej nazwie zamiast ścieżki katalogu. Może również służyć do instalowania pakietu szablonów z nuget źródła danych. Pozostałe ustawienia, `<Title>` takie `<PackageTags>` jak i mają do czynienia z metadanych wyświetlanych w kanale informacyjnym NuGet. Aby uzyskać więcej informacji na temat ustawień NuGet, zobacz [NuGet i MSBuild właściwości](/nuget/reference/msbuild-targets).

Ustawienie `<TargetFramework>` musi być ustawione tak, aby MSBuild będzie działać poprawnie po uruchomieniu polecenia pack do kompilacji i spakowania projektu.

Ostatnie trzy ustawienia mają do czynienia z konfigurowaniem projektu poprawnie, aby uwzględnić szablony w odpowiednim folderze w pakiecie NuGet po jego utworzeniu.

Zawiera `<ItemGroup>` dwa ustawienia. Po `<Content>` pierwsze, ustawienie zawiera wszystko w folderze _szablonów_ jako zawartość. Jest również ustawiona, aby wykluczyć dowolny folder _bin_ lub _folder obj,_ aby zapobiec uwzględnieniu skompilowanych kodów (jeśli zostały przetestowane i skompilowane szablony). Po `<Compile>` drugie, ustawienie wyklucza wszystkie pliki kodu ze kompilowania bez względu na to, gdzie się znajdują. To ustawienie zapobiega próbie skompilowania kodu w hierarchii _folderów szablonów_ przez projekt używany do tworzenia pakietu szablonów.

## <a name="build-and-install"></a>Tworzenie i instalowanie

Zapisz ten plik, a następnie uruchom polecenie pack

```dotnetcli
dotnet pack
```

To polecenie stworzy projekt i utworzy pakiet NuGet w folderze To powinno być _folder emanuje\bin\Debug._

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

Następnie zainstaluj plik pakietu szablonów za `dotnet new -i PATH_TO_NUPKG_FILE` pomocą polecenia.

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

Jeśli pakiet NuGet został przekazany do źródła danych NuGet, można użyć `dotnet new -i PACKAGEID` polecenia, `PACKAGEID` gdzie jest taki sam jak `<PackageId>` ustawienie z pliku _.csproj._ Ten identyfikator pakietu jest taki sam jak identyfikator pakietu NuGet.

## <a name="uninstall-the-template-pack"></a>Odinstalowywanie pakietu szablonów

Bez względu na to, jak zainstalowano pakiet szablonów, z plikiem _.nupkg_ bezpośrednio lub przez nuget kanału informacyjnego, usunięcie pakietu szablonów jest taka sama. Użyj `<PackageId>` szablonu, który chcesz odinstalować. Można uzyskać listę szablonów, które są `dotnet new -u` instalowane przez uruchomienie polecenia.

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

Uruchom, `dotnet new -u AdatumCorporation.Utility.Templates` aby odinstalować szablon. Polecenie `dotnet new` wygeneruje informacje pomocy, które powinny pominąć szablony, które zostały wcześniej zainstalowane.

Gratulacje! zainstalowano i odinstalowałeś pakiet szablonów.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o szablonach, z których większość już się nauczyłeś, zobacz nowy artykuł [Szablony niestandardowe dla dotnet.](../tools/custom-templates.md)

* [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki)
* [dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)
* [*schemat template.json* w Sklepie Schematów JSON](http://json.schemastore.org/template)
