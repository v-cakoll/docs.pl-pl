---
title: Tworzenie pakietu szablonów dla nowego dotnet
description: Dowiedz się, jak utworzyć plik CSPROJ, który będzie kompilować pakiet szablonów dla nowego polecenia dotnet.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 4bd51f579231b13b0831ef7114c2a648c55cd6a2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926083"
---
# <a name="tutorial-create-a-template-pack"></a>Samouczek: Tworzenie pakietu szablonów

Za pomocą platformy .NET Core można tworzyć i wdrażać szablony generujące projekty, pliki, nawet zasoby. Ten samouczek jest trzecią częścią serii, która uczy się, jak tworzyć, instalować i odinstalowywać szablony do użycia z `dotnet new` poleceniem.

W tej części serii dowiesz się, jak:

> [!div class="checklist"]
>
> * Utwórz projekt \*. csproj, aby skompilować pakiet szablonów
> * Konfigurowanie pliku projektu do pakowania
> * Instalowanie szablonu z pliku pakietu NuGet
> * Odinstalowywanie szablonu według identyfikatora pakietu

## <a name="prerequisites"></a>Wymagania wstępne

* Ukończ [część 1](cli-templates-create-item-template.md) i [część 2](cli-templates-create-project-template.md) tej serii samouczków.

  Ten samouczek używa dwóch szablonów utworzonych w pierwszych dwóch częściach tego samouczka. Możliwe jest użycie innego szablonu, dopóki szablon zostanie skopiowany do folderu _working\templates\\_  .

* Otwórz Terminal i przejdź do folderu _working\templates\\_  .

## <a name="create-a-template-pack-project"></a>Tworzenie projektu pakietu szablonów

Pakiet szablonów to jeden lub więcej szablonów pakowanych do pliku. Podczas instalowania lub odinstalowywania pakietu wszystkie szablony zawarte w pakiecie są dodawane lub usuwane odpowiednio. Poprzednie części tej serii samouczków działały tylko z poszczególnymi szablonami. Aby udostępnić niespakowany szablon, należy skopiować folder szablonu i zainstalować go za pośrednictwem tego folderu. Ponieważ pakiet szablonów może mieć więcej niż jeden szablon w tym samym pliku, udostępnianie jest łatwiejsze.

Pakiety szablonów są reprezentowane przez plik pakietu NuGet ( _. nupkg_). Podobnie jak każdy pakiet NuGet, można przekazać pakiet szablonów do źródła danych NuGet. `dotnet new -i` Polecenie obsługuje instalowanie pakietu Template Pack z kanału informacyjnego pakietu NuGet. Ponadto można bezpośrednio zainstalować pakiet szablonów z pliku _. nupkg_ .

Zwykle plik C# projektu jest używany do kompilowania kodu i tworzenia danych binarnych. Jednak projekt może być również używany do generowania pakietu szablonów. Zmieniając ustawienia elementu _. csproj_, można zapobiec kompilacji dowolnego kodu, a zamiast tego dołączyć wszystkie zasoby szablonów jako zasoby. Po skompilowaniu tego projektu tworzy pakiet NuGet pakietu szablonów.

Tworzony pakiet będzie obejmował [szablon elementu](cli-templates-create-item-template.md) i [szablon pakietu](cli-templates-create-project-template.md) utworzony wcześniej. Ze względu na to, że dwa szablony są pogrupowane w folderze _working\templates\\_  , możemy użyć folderu _roboczego_ dla pliku _. csproj_ .

W terminalu przejdź do folderu _roboczego_ . Utwórz nowy projekt i ustaw dla niego nazwę `templatepack` i folder wyjściowy w bieżącym folderze.

```console
dotnet new console -n templatepack -o .
```

Parametr ustawia nazwę pliku _. csproj_ na `-o` _templatepack. csproj_ , a parametry tworzą pliki w bieżącym katalogu. `-n` Powinien zostać wyświetlony wynik podobny do następującego: dane wyjściowe.

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Następnie otwórz plik _templatepack. csproj_ w ulubionym edytorze i Zastąp zawartość następującym kodem XML:

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

`<PropertyGroup>` Ustawienia w pliku XML powyżej są podzielone na trzy grupy. Pierwsza grupa zajmuje się właściwościami wymaganymi dla pakietu NuGet. Trzy `<Package` ustawienia muszą wykonać przy użyciu właściwości pakietu NuGet, aby zidentyfikować pakiet w źródle danych NuGet. W celu odinstalowania pakietu Template Pack o pojedynczej nazwie zamiast ścieżki do katalogu zostanie użyta wartość.`<PacakgeId>` Można go również użyć do zainstalowania pakietu Template Pack ze źródła danych NuGet. Pozostałe ustawienia, takie jak `<Title>` i `<Tags>` , muszą zawierać metadane wyświetlane w źródle danych NuGet. Aby uzyskać więcej informacji na temat ustawień NuGet, zobacz [Właściwości narzędzia NuGet i programu MSBuild](/nuget/reference/msbuild-targets).

`<TargetFramework>` Ustawienie musi być ustawione tak, aby program MSBuild działał prawidłowo po uruchomieniu polecenia Pack w celu skompilowania i spakowania projektu.

Ostatnie trzy ustawienia należy wykonać w celu poprawnego skonfigurowania projektu w celu uwzględnienia szablonów w odpowiednim folderze w pakiecie NuGet, gdy zostanie on utworzony.

`<ItemGroup>` Zawiera dwa ustawienia. Pierwsze ustawienie uwzględnia wszystkie elementy w folderze templates jako zawartość. `<Content>` Jest również ustawiony na wykluczenie dowolnego folderu _bin_ lub _obj_ , aby zapobiec dołączeniu kodu skompilowanego (w przypadku przetestowania i skompilowania szablonów). Po drugie, `<Compile>` ustawienie wyklucza wszystkie pliki kodu z kompilacji niezależnie od tego, gdzie się znajdują. To ustawienie uniemożliwia projekt używany do tworzenia pakietu szablonów na podstawie próby skompilowania kodu w hierarchii folderów _szablonów_ .

## <a name="build-and-install"></a>Kompiluj i zainstaluj

Zapisz ten plik, a następnie uruchom polecenie Pack

```console
dotnet pack
```

To polecenie spowoduje skompilowanie projektu i utworzenie pakietu NuGet w tym folderze _working\bin\Debug_ .

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

Następnie Zainstaluj plik pakietu szablonów przy użyciu `dotnet new -i PATH_TO_NUPKG_FILE` polecenia.

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

Jeśli pakiet NuGet został przekazany do źródła danych `dotnet new -i PACKAGEID` NuGet, można użyć polecenia, gdzie `PACKAGEID` `<PackageId>` jest taka sama jak ustawienie z pliku _. csproj_ . Ten identyfikator pakietu jest taki sam jak identyfikator pakietu NuGet.

## <a name="uninstall-the-template-pack"></a>Odinstalowywanie pakietu szablonów

Niezależnie od tego, jak został zainstalowany pakiet szablonów, z plikiem _. nupkg_ bezpośrednio lub przez źródło danych NuGet, usunięcie pakietu szablonu jest takie samo. `<PackageId>` Użyj szablonu, który chcesz odinstalować. Listę zainstalowanych szablonów można uzyskać, uruchamiając `dotnet new -u` polecenie.

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

Uruchom `dotnet new -u AdatumCorporation.Utility.Templates` , aby odinstalować szablon. `dotnet new` Polecenie będzie wyprowadzać informacje pomocy, które powinny pominąć wcześniej zainstalowane szablony.

Gratulacje! Pakiet szablonów został zainstalowany i odinstalowany. 

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o szablonach, z których większość już wiesz, zobacz [Szablony niestandardowe dla nowego](../tools/custom-templates.md) artykułu usługi dotnet.

* [Witryna typu wiki repozytorium usługi GitHub/tworzenia szablonów](https://github.com/dotnet/templating/wiki)
* [dotnet/dotnet-Template-przykłady repozytorium GitHub](https://github.com/dotnet/dotnet-template-samples)
* [*szablon Template. JSON* w magazynie schematów JSON](http://json.schemastore.org/template)
