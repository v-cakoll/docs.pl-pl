---
title: Szablony niestandardowe dla dotnet nowy
description: Dowiedz się więcej o szablonach niestandardowych dla dowolnego typu projektu lub plików programu .NET.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 8e1ac4ca21a8a90ad0f7c9bd3dd11281eb4a6e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73420884"
---
# <a name="custom-templates-for-dotnet-new"></a>Szablony niestandardowe dla dotnet nowy

Zestaw [SDK .NET Core](https://dotnet.microsoft.com/download) jest dostarczany z wieloma już zainstalowanymi szablonami i gotowymi do użycia. [ `dotnet new` Polecenie](dotnet-new.md) to nie tylko sposób używania szablonu, ale także sposób instalowania i odinstalowywania szablonów. Począwszy od .NET Core 2.0, można utworzyć własne szablony niestandardowe dla dowolnego typu projektu, takich jak aplikacja, usługa, narzędzie lub biblioteka klas. Można nawet utworzyć szablon, który generuje jeden lub więcej niezależnych plików, takich jak plik konfiguracyjny.

Szablony niestandardowe z pakietu NuGet można instalować w dowolnym kanale informacyjnym NuGet, odwołując się bezpośrednio do pliku NuGet *.nupkg* lub określając katalog systemu plików zawierający szablon. Aparat szablonów oferuje funkcje, które umożliwiają zastępowanie wartości, dołączanie i wykluczanie plików oraz wykonywanie niestandardowych operacji przetwarzania, gdy używany jest szablon.

Aparat szablonów jest open source, a repozytorium kodu online jest na [dotnet/templating](https://github.com/dotnet/templating/) na GitHub. Odwiedź repówce [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) dla przykładów szablonów. Więcej szablonów, w tym szablony od osób trzecich, znajdują się w [dostępnych szablonach dla dotnet nowy](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) na GitHub. Aby uzyskać więcej informacji na temat tworzenia i używania szablonów niestandardowych, zobacz [Jak tworzyć własne szablony dla dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) i [dotnet /templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).

Aby wykonać instruktaż i utworzyć szablon, zobacz [Tworzenie niestandardowego szablonu dla dotnet nowy](../tutorials/cli-templates-create-item-template.md) samouczek.

### <a name="net-default-templates"></a>Domyślne szablony .NET

Po zainstalowaniu [.NET Core SDK,](https://dotnet.microsoft.com/download)otrzymasz ponad tuzin wbudowanych szablonów do tworzenia projektów i plików, w tym aplikacji konsoli, bibliotek klas, projektów testów jednostkowych, ASP.NET aplikacje Core (w tym projekty [Angular](https://angular.io/) i [React)](https://facebook.github.io/react/) i pliki konfiguracyjne. Aby wyświetlić listę wbudowanych szablonów, `dotnet new` uruchom `-l|--list` polecenie z opcją:

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a>Konfigurowanie

Szablon składa się z następujących części:

- Pliki źródłowe i foldery.
- Plik konfiguracyjny *(template.json).*

### <a name="source-files-and-folders"></a>Pliki źródłowe i foldery

Pliki źródłowe i foldery zawierają wszystkie pliki i foldery, `dotnet new <TEMPLATE>` których aparat szablonów ma używać podczas uruchamiania polecenia. Aparat szablonów jest przeznaczony do używania *projektów uruchamianych* jako kodu źródłowego do tworzenia projektów. Ma to kilka zalet:

- Aparat szablonu nie wymaga wstrzyknąć specjalne tokeny do kodu źródłowego projektu.
- Pliki kodu nie są specjalnymi plikami ani nie są modyfikowane w żaden sposób do pracy z aparatem szablonów. Tak więc narzędzia, których zwykle używasz podczas pracy z projektami, działają również z zawartością szablonu.
- Tworzenie, uruchamianie i debugowanie projektów szablonów, tak jak w przypadku innych projektów.
- Szablon można szybko utworzyć z istniejącego projektu, dodając do projektu plik konfiguracyjny *./.template.config/template.json.*

Pliki i foldery przechowywane w szablonie nie są ograniczone do formalnych typów projektów .NET. Pliki źródłowe i foldery mogą składać się z dowolnej zawartości, którą chcesz utworzyć, gdy szablon jest używany, nawet jeśli aparat szablonu tworzy tylko jeden plik jako dane wyjściowe.

Pliki generowane przez szablon można modyfikować na podstawie logiki i ustawień podanych w pliku konfiguracyjnym *template.json.* Użytkownik może zastąpić te ustawienia, przekazując opcje do `dotnet new <TEMPLATE>` polecenia. Typowym przykładem logiki niestandardowej jest podanie nazwy klasy lub zmiennej w pliku kodu, który jest wdrażany przez szablon.

### <a name="templatejson"></a>template.json

Plik *template.json* jest umieszczany w folderze *.template.config* w katalogu głównym szablonu. Plik udostępnia informacje o konfiguracji do aparatu szablonu. Minimalna konfiguracja wymaga elementów członkowskich przedstawionych w poniższej tabeli, co jest wystarczające do utworzenia szablonu funkcjonalnego.

| Członek            | Typ          | Opis |
| ----------------- | ------------- | ----------- |
| `$schema`         | Identyfikator URI           | Schemat JSON dla pliku *template.json.* Edytory obsługujące schematy JSON umożliwiają funkcje edycji JSON po określeniu schematu. Na przykład [Kod programu Visual Studio](https://code.visualstudio.com/) wymaga tego elementu członkowskiego, aby włączyć IntelliSense. Użyj wartości `http://json.schemastore.org/template`. |
| `author`          | ciąg        | Autor szablonu. |
| `classifications` | tablica(ciąg) | Zero lub więcej cech szablonu, które użytkownik może użyć do znalezienia szablonu podczas wyszukiwania. Klasyfikacje są również wyświetlane w *kolumnie Znaczniki,* gdy pojawiają `dotnet new -l|--list` się na liście szablonów tworzonych przy użyciu polecenia. |
| `identity`        | ciąg        | Unikatowa nazwa tego szablonu. |
| `name`            | ciąg        | Nazwa szablonu, który użytkownicy powinni zobaczyć. |
| `shortName`       | ciąg        | Domyślna skrócona nazwa wyboru szablonu, który ma zastosowanie do środowisk, w których nazwa szablonu jest określona przez użytkownika, a nie wybrany za pomocą graficznego interfejsu użytkownika. Na przykład krótka nazwa jest przydatna podczas korzystania z szablonów z wiersza polecenia z poleceniami wiersza polecenia. |

Pełny schemat pliku *template.json* znajduje się w [Magazynie schematów JSON](http://json.schemastore.org/template). Aby uzyskać więcej informacji na temat pliku *template.json,* zobacz [dotnet templating wiki](https://github.com/dotnet/templating/wiki).

#### <a name="example"></a>Przykład

Na przykład oto folder szablonu, który zawiera dwa pliki zawartości: *console.cs* i *readme.txt*. Zwróć uwagę, że istnieje wymagany folder o nazwie *.template.config,* który zawiera plik *template.json.*

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

Plik *template.json* wygląda następująco:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

Folder *mytemplate* jest instalowalnym pakietem szablonów. Po zainstalowaniu pakietu `shortName` można użyć polecenia. `dotnet new` Na przykład `dotnet new adatumconsole` będzie `console.cs` wyprowadzać pliki i `readme.txt` do bieżącego folderu.

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Pakowanie szablonu do pakietu NuGet (plik nupkg)

Szablon niestandardowy jest zapakowany z poleceniem [dotnet pack](dotnet-pack.md) i plikiem *csproj.* Alternatywnie [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) może być używany z poleceniem [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) wraz z plikiem *nuspec.* Jednak NuGet wymaga .NET Framework w systemach Windows i [Mono](https://www.mono-project.com/) w systemach Linux i MacOS.

Plik *.csproj* różni się nieco od tradycyjnego pliku *.csproj* code-project. Zwróć uwagę na następujące ustawienia:

01. Ustawienie `<PackageType>` zostanie dodane `Template`i ustawione na wartość .
01. Ustawienie `<PackageVersion>` zostanie dodane i ustawione na prawidłowy [numer wersji NuGet](/nuget/reference/package-versioning).
01. Ustawienie `<PackageId>` zostanie dodane i ustawione na unikatowy identyfikator. Ten identyfikator jest używany do odinstalowania pakietu szablonów i jest używany przez źródła danych NuGet do rejestrowania pakietu szablonów.
01. Ogólne ustawienia metadanych powinny `<Title>` `<Authors>`być `<Description>`ustawione: , , , i `<PackageTags>`.
01. Ustawienie `<TargetFramework>` musi być ustawione, nawet jeśli plik binarny wyprodukowany przez proces szablonu nie jest używany. W poniższym przykładzie jest `netstandard2.0`ustawiona na .

Pakiet szablonów w postaci pakietu NuGet *.nupkg* wymaga, aby wszystkie szablony były przechowywane w folderze *zawartości* w pakiecie. Istnieje kilka ustawień do dodania do pliku *.csproj,* aby upewnić się, że wygenerowany *plik .nupkg* można zainstalować jako pakiet szablonów:

01. Ustawienie `<IncludeContentInPack>` jest ustawiona `true` na uwzględnienie dowolnego pliku, który projekt ustawia jako **zawartość** w pakiecie NuGet.
01. Ustawienie `<IncludeBuildOutput>` jest ustawiona `false` na wykluczenie wszystkich plików binarnych generowanych przez kompilator z pakietu NuGet.
01. Ustawienie `<ContentTargetFolders>` jest ustawione `content`na . Daje to pewność, że pliki ustawione jako **zawartość** są przechowywane w folderze *zawartości* w pakiecie NuGet. Ten folder w pakiecie NuGet jest analizowany przez system szablonów dotnet.

Łatwym sposobem wykluczenia wszystkich plików kodu z kompilowania przez `<Compile Remove="**\*" />` projekt szablonu jest `<ItemGroup>` użycie elementu w pliku projektu, wewnątrz elementu.

Łatwym sposobem na uporządkowanie pakietu szablonów jest umieszczenie wszystkich szablonów w poszczególnych folderach, a następnie każdy folder szablonu w folderze *szablonów,* który znajduje się w tym samym katalogu co plik *csproj.* W ten sposób można użyć pojedynczego elementu projektu, aby uwzględnić wszystkie pliki i foldery w *szablonach* jako **zawartość**. Wewnątrz elementu `<ItemGroup>` utwórz `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` element.

Oto przykładowy plik *csproj,* który jest zgodny ze wszystkimi powyższymi wskazówkami. Pakuje folder podrzędny *szablonów* do folderu pakietu *zawartości* i wyklucza ze kompilowania dowolny plik kodu.

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

Poniższy przykład przedstawia strukturę plików i folderów przy użyciu *.csproj* do tworzenia pakietu szablonów. Folder plików i *szablonów* *MyDotnetTemplates.csproj* znajduje się w katalogu głównym katalogu o nazwie *project_folder*. Folder *szablonów* zawiera dwa szablony: *mytemplate1* i *mytemplate2*. Każdy szablon zawiera pliki zawartości i folder *.template.config* z plikiem konfiguracyjnym *template.json.*

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a>Instalowanie szablonu

Użyj polecenia [dotnet new -i|-install,](dotnet-new.md) aby zainstalować pakiet.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Aby zainstalować szablon z pakietu NuGet przechowywanego w nuget.org

Użyj identyfikatora pakietu NuGet, aby zainstalować pakiet szablonu.

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Aby zainstalować szablon z lokalnego pliku nupkg

Podaj ścieżkę do pliku pakietu NuGet *nupkg.*

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Aby zainstalować szablon z katalogu systemu plików

Szablony można instalować z folderu szablonu, takiego jak folder *mytemplate1* z powyższego przykładu. Określ ścieżkę folderu folderu *.template.config.* Ścieżka do katalogu szablonów nie musi być bezwzględna. Jednak do odinstalowania szablonu zainstalowanego z folderu wymagana jest ścieżka bezwzględna.

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>Pobierz listę zainstalowanych szablonów

Polecenie odinstalowywania, bez żadnych innych parametrów, wyświetli listę wszystkich zainstalowanych szablonów.

```dotnetcli
dotnet new -u
```

To polecenie zwraca coś podobnego do następującego wyjścia:

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

Pierwszy poziom elementów `Currently installed items:` po są identyfikatory używane w odinstalowywaniu szablonu. I w powyższym `Microsoft.DotNet.Common.ItemTemplates` `Microsoft.DotNet.Common.ProjectTemplates.3.0` przykładzie i są wymienione. Jeśli szablon został zainstalowany przy użyciu ścieżki systemu plików, ten identyfikator będzie ścieżką folderu folderu *.template.config.*

## <a name="uninstalling-a-template"></a>Odinstalowywanie szablonu

Użyj polecenia [dotnet new -u|--uninstall,](dotnet-new.md) aby odinstalować pakiet.

Jeśli pakiet został zainstalowany przez źródło danych NuGet lub plik *.nupkg* bezpośrednio, podaj identyfikator.

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

Jeśli pakiet został zainstalowany przez określenie ścieżki do folderu *.template.config,* użyj tej ścieżki **bezwzględnej,** aby odinstalować pakiet. Ścieżkę bezwzględną szablonu można wyświetlić w `dotnet new -u` danych wyjściowych dostarczonych przez polecenie. Aby uzyskać więcej informacji, zobacz [Pobierz listę zainstalowanych szablonów](#get-a-list-of-installed-templates) sekcji powyżej.

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Tworzenie projektu przy użyciu szablonu niestandardowego

Po zainstalowaniu szablonu użyj szablonu, `dotnet new <TEMPLATE>` wykonując polecenie tak, jak w przypadku każdego innego wstępnie zainstalowanego szablonu. Można również [options](dotnet-new.md#options) określić opcje `dotnet new` polecenia, w tym opcje specyficzne dla szablonu skonfigurowane w ustawieniach szablonu. Podaj krótką nazwę szablonu bezpośrednio do polecenia:

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Zobacz też

- [Tworzenie niestandardowego szablonu dla dotnet nowy (samouczek)](../tutorials/cli-templates-create-item-template.md)
- [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki)
- [dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)
- [Jak tworzyć własne szablony dla dotnet nowych](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*schemat template.json* w Sklepie Schematów JSON](http://json.schemastore.org/template)
