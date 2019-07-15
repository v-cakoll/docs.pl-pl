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
# <a name="tutorial-create-a-template-pack"></a>Samouczek: Tworzenie szablonowego pakietu

Za pomocą programu .NET Core można tworzyć i wdrażać szablony, które generują projektów, plików i nawet zasobów. Niniejszy samouczek jest trzecią częścią serii, pokazujący sposób tworzenia, instalowanie i odinstalowywanie szablonów do użytku z programem `dotnet new` polecenia.

W tej części serii dowiesz się, jak:

> [!div class="checklist"]
> * Utwórz projekt _.csproj* tworzenie szablonowego pakietu
> * Konfigurowanie pliku projektu do pakowania
> * Zainstaluj szablonu z pliku pakietu NuGet
> * Odinstaluj szablonu według Identyfikatora pakietu

## <a name="prerequisites"></a>Wymagania wstępne

* Pełne [część 1](cli-templates-create-item-template.md) i [część 2](cli-templates-create-project-template.md) z tej serii samouczka.

  Ten samouczek używa dwóch szablonów utworzonych w dwie pierwsze części tego samouczka. Jest to możliwe, można użyć innego szablonu, tak długo, jak skopiować szablon jako folder do _working\templates\\_  folderu.

* Otwórz terminal i przejdź do _working\templates\\_  folderu.

## <a name="create-a-template-pack-project"></a>Utwórz szablon projektu pakietu

Pakiet szablonu jest co najmniej jeden szablon umieszczonych w pliku. Podczas instalowania lub odinstalowania pakiet wszystkie szablony zawartych w pakiecie są dodane lub usunięte odpowiednio. Za pomocą szablonów poszczególnych działało tylko poprzedniej części tej serii samouczków. Aby udostępnić szablon nieopakowanych, należy skopiować folder szablonów i zainstalować za pośrednictwem tego folderu. Ponieważ szablonowego pakietu może mieć więcej niż jeden szablon w nim, a to pojedynczy plik, udostępnianie jest łatwiejsze.

Szablonowe pakiety są reprezentowane przez pakiet NuGet ( _.nupkg_) pliku. I podobnie jak dowolny pakiet NuGet, możesz przekazać szablonowego pakietu do NuGet źródła danych. `dotnet new -i` Polecenie obsługuje instalowanie pakietu szablonów z pakietu NuGet, źródła danych. Ponadto można zainstalować szablonowego pakietu z _.nupkg_ pliku bezpośrednio.

Zazwyczaj używasz C# pliku projektu, aby skompilować kod i utworzyć plik binarny. Jednak projektu można również wygenerować szablonowego pakietu. Zmieniając ustawienia _.csproj_, mogą uniemożliwić kompilowanie kodu i zamiast tego zawierają wszystkie zasoby szablonów jako zasoby. Podczas kompilowania projektu tworzy pakiet szablonu pakietu NuGet.

Pakiet należy utworzyć będzie zawierać [szablon elementu](cli-templates-create-item-template.md) i [szablonu pakietu](cli-templates-create-project-template.md) utworzone wcześniej. Firma Microsoft pogrupowane dwa szablony do _working\templates\\_  folderu, możemy użyć _pracy_ folder _.csproj_ pliku.

W terminalu przejdź do _pracy_ folderu. Utwórz nowy projekt i ustaw nazwę na `templatepack` i folderze wyjściowym do bieżącego folderu.

```console
dotnet new console -n templatepack -o .
```

`-n` Zestawów parametrów _.csproj_ nazwę pliku, aby _templatepack.csproj_ i `-o` parametrów tworzy pliki w bieżącym katalogu. Powinien pojawić się wyniki podobne do następujących danych wyjściowych.

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Następnie otwórz _templatepack.csproj_ plik w ulubionym edytorze i Zastąp zawartość następujący kod XML:

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

`<PropertyGroup>` Ustawienia w pliku XML powyżej jest dzielony na trzy grupy. Pierwsza grupa zawiera właściwości wymagane dla pakietu NuGet. Trzy `<Package` ustawienia trzeba przy użyciu pakietu NuGet pakiet właściwości w celu zidentyfikowania pakietu na kanał informacyjny NuGet. W szczególności `<PacakgeId>` wartości można odinstalować pakietu szablonu pod jedną nazwą, a nie ścieżkę katalogu. Może również służyć do zainstalowania pakietu szablonów z NuGet źródła danych. Pozostałe ustawienia, takie jak `<Title>` i `<Tags>` trzeba z metadanymi wyświetlany na NuGet źródła danych. Aby uzyskać więcej informacji o ustawieniach NuGet, zobacz [właściwości programu MSBuild i NuGet](/nuget/reference/msbuild-targets).

`<TargetFramework>` Ustawienia należy wybrać opcję, aby po uruchomieniu polecenia pakietu, aby skompilować i pakietu projektu programu MSBuild będą działały poprawnie.

Ostatnie trzy ustawienia muszą poprawnie konfigurowania projektu do uwzględnienia w szablonach w odpowiedni folder w NuGet pakiet podczas jego tworzenia.

`<ItemGroup>` Zawiera dwa ustawienia. Po pierwsze, `<Content>` ustawienie obejmuje wszystko, co w _szablony_ folder jako zawartość. Ma również ustawienie, aby wykluczać żadnych _bin_ folderu lub _obj_ folder, aby zapobiec kompilowania kodu (jeśli przetestowane i skompilowanych szablonów) zostaną uwzględnione. Drugi `<Compile>` wyklucza wszystkie pliki kodu z kompilacji, niezależnie od tego, gdzie są przechowywane. To ustawienie zapobiega projektu użyte do utworzenia pakietu szablonów się skompilować kod w _szablony_ hierarchii folderów.

## <a name="build-and-install"></a>Kompilowanie i instalacji

Zapisz ten plik, a następnie uruchom polecenie pakietu

```console
dotnet pack
```

To polecenie skompilować projekt i Utwórz pakiet, w tym powinien być NuGet _working\bin\Debug_ folderu.

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

Następnie zainstaluj plik pakietu szablonu przy użyciu `dotnet new -i PATH_TO_NUPKG_FILE` polecenia.

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

Pakiet NuGet jest przekazywane do źródła NuGet, można użyć `dotnet new -i PACKAGEID` polecenie gdzie `PACKAGEID` jest taka sama jak `<PackageId>` z _.csproj_ pliku. Ten identyfikator pakietu jest taki sam jak identyfikator pakietu NuGet.

## <a name="uninstall-the-template-pack"></a>Odinstaluj pakiet szablonu

Niezależnie od tego, jak zainstalowany pakiet szablonu, albo za pomocą _.nupkg_ pliku, bezpośrednio lub przez NuGet źródła danych, usuwanie pakietu szablonu jest taka sama. Użyj `<PackageId>` szablonu chcesz odinstalować. Możesz uzyskać listę szablonów, które są zainstalowane, uruchamiając `dotnet new -u` polecenia.

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

Uruchom `dotnet new -u AdatumCorporation.Utility.Templates` odinstalować szablonu. `dotnet new` Polecenie zwróci informacje, które należy pominąć znak szablonów została wcześniej zainstalowana.

Gratulacje! już instalowana i odinstalowywana szablonowego pakietu. 

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o szablonach, większość z nich już wiesz, zobacz [szablonów niestandardowych dla platformy dotnet nowe](../tools/custom-templates.md) artykułu.

* [repozytorium GitHub DotNet/szablonów witryny typu Wiki](https://github.com/dotnet/templating/wiki)
* [repozytorium GitHub DotNet/dotnet-— przykłady szablonów](https://github.com/dotnet/dotnet-template-samples)
* [*Template.JSON* schemat w Store schematu JSON](http://json.schemastore.org/template)
