---
title: Szablony niestandardowe dla nowej platformy dotnet
description: Dowiedz się więcej na temat szablonów niestandardowych dla dowolnego typu projektu .NET lub plików.
author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: 19211d1ac45bbd2e5838c5ee30e380d7d10c3f1c
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2019
ms.locfileid: "67151950"
---
# <a name="custom-templates-for-dotnet-new"></a>Szablony niestandardowe dla nowej platformy dotnet

[Zestawu .NET Core SDK](https://www.microsoft.com/net/download/core) jest powiązana z wielu szablonów już zainstalowany i gotowy do użycia. [ `dotnet new` Polecenia](dotnet-new.md) nie tylko sposób używania szablonu, ale także sposób instalowania i odinstalowywania szablonów. Począwszy od programu .NET Core 2.0, można utworzyć własne szablony niestandardowe dla każdego typu projektu, takie jak aplikacja, usługi, narzędzia lub biblioteki klas. Możesz nawet utworzyć szablon, który generuje co najmniej jeden niezależnych plikach, takich jak plik konfiguracji.

Można zainstalować niestandardowe szablony z pakietu NuGet dla dowolnego narzędzia NuGet kanału informacyjnego, odwołując się do NuGet *.nupkg* plików bezpośrednio lub przez określenie katalogu systemu plików, który zawiera szablon. Aparat szablonów oferuje funkcje, które umożliwiają zastępować wartości, dołączanie i wykluczanie plików i wykonywanie niestandardowych operacji, gdy szablon jest używany.

Aparat szablonów "open source", a repozytorium kodu w trybie online jest w [dotnet/szablonów](https://github.com/dotnet/templating/) w witrynie GitHub. Odwiedź stronę [dotnet/dotnet szablonu samples](https://github.com/dotnet/dotnet-template-samples) repozytorium przykładów szablonów. Więcej szablonów, w tym szablony innych firm, znajdują się w [dostępnych szablonów dla platformy dotnet nowe](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) w witrynie GitHub. Aby uzyskać więcej informacji na temat tworzenia i używania niestandardowych szablonów, zobacz [sposobu tworzenia nowych szablonów dla platformy dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) i [repozytorium GitHub dotnet/szablonów Wiki](https://github.com/dotnet/templating/wiki).

Aby wykonać przewodnik i utworzyć szablon, zobacz [Utwórz nowy szablon niestandardowy dla platformy dotnet](~/docs/core/tutorials/create-custom-template.md) samouczka.

### <a name="net-default-templates"></a>Szablony domyślne platformy .NET

Po zainstalowaniu [zestawu .NET Core SDK](https://www.microsoft.com/net/download/core), pojawi się ponad tuzina wbudowanych szablonów do tworzenia projektów i plików, w tym aplikacje konsoli, bibliotekach klas, jednostka testowanie projektów, aplikacje platformy ASP.NET Core (w tym [Angular](https://angular.io/) i [React](https://facebook.github.io/react/) projektów) i pliki konfiguracyjne. Aby wyświetlić listę wbudowanych szablonów, należy uruchomić `dotnet new` polecenia `-l|--list` opcji:

```console
dotnet new --list
```

## <a name="configuration"></a>Konfiguracja

Szablon składa się z następujących elementów:

- Pliki źródłowe i foldery.
- Plik konfiguracji (*template.json*).

### <a name="source-files-and-folders"></a>Źródło plików i folderów

Pliki źródłowe i foldery obejmują dowolnych pliki i foldery, które mają szablonu aparatu do użycia podczas `dotnet new <TEMPLATE>` jest uruchamiane polecenie. Aparat szablonów jest przeznaczony do stosowania *możliwy do uruchomienia projektów* jako źródło kodu do tworzenia projektów. To ma kilka zalet:

- Aparat szablonów nie wymaga wstrzyknąć specjalne tokeny do kodu źródłowego projektu.
- Pliki kodu nie są specjalne pliki lub zmodyfikowane w dowolny sposób, aby pracować z aparatu szablonów. Tak narzędzi, które normalnie używane podczas pracy z projektami również działać przy użyciu szablonu zawartości.
- Tworzenie, uruchamianie i debugowanie projektów szablonu, podobnie jak w przypadku wszystkich innych projektów.
- Możesz szybko utworzyć szablon z istniejącego projektu, po prostu przez dodanie *./.template.config/template.json* pliku konfiguracji do projektu.

Plików i folderów przechowywanych w szablonie nie ma ograniczenia dla formalnych typów projektów .NET. Źródło plików i folderów może zawierać dowolną zawartość, która ma zostać utworzony, gdy szablon jest używany, nawet wtedy, gdy aparat szablonów tworzy pojedynczy plik jako dane wyjściowe.

Pliki generowane przez szablon może być modyfikowany na podstawie logiki i ustawień, które podano w *template.json* pliku konfiguracji. Użytkownika można zastąpić te ustawienia, przekazując opcje `dotnet new <TEMPLATE>` polecenia. Typowym przykładem logiki niestandardowej jest podanie nazwy dla klasy lub zmiennej w pliku kodu, który jest wdrożony przez szablon.

### <a name="templatejson"></a>template.json

*Template.json* plik zostanie umieszczony w *. template.config* folder w katalogu głównym szablonu. Plik zawiera informacje o konfiguracji do aparatu szablonu. Minimalna konfiguracja wymaga od członków, pokazano w poniższej tabeli, która jest wystarczające, aby utworzyć szablon funkcjonalności.

| Element członkowski            | Typ          | Opis |
| ----------------- | ------------- | ----------- |
| `$schema`         | Identyfikator URI           | Schemat JSON dla *template.json* pliku. Edytory, które obsługują schematów JSON Włącz funkcje Edycja JSON, jeśli nie określono schematu. Na przykład [programu Visual Studio Code](https://code.visualstudio.com/) wymaga tego elementu członkowskiego włączyć technologię IntelliSense. Użyj wartości `http://json.schemastore.org/template`. |
| `author`          | string        | Autor szablonu. |
| `classifications` | Array(String) | Zero lub więcej właściwości szablon, którego użytkownik może znaleźć szablonu podczas wyszukiwania dla niego. Klasyfikacje są również wyświetlane w *tagi* kolumny, gdy się pojawi się na liście szablony utworzone za pomocą `dotnet new -l|--list` polecenia. |
| `identity`        | string        | Unikatowa nazwa dla tego szablonu. |
| `name`            | string        | Nazwa szablonu, która powinna być widoczna. |
| `shortName`       | string        | Domyślna nazwa skrócona do wybierania szablonu, który ma zastosowanie do środowiska, w którym nazwa szablonu jest określony przez użytkownika nie są wybrane za pomocą graficznego interfejsu użytkownika. Na przykład krótką nazwę przydaje się podczas korzystania z szablonów z poziomu wiersza polecenia przy użyciu interfejsu wiersza polecenia. |

Pełnego schematu dla *template.json* plik znajduje się na [Store schematu JSON](http://json.schemastore.org/template). Aby uzyskać więcej informacji na temat *template.json* plików, zobacz [wiki szablonów dotnet](https://github.com/dotnet/templating/wiki).

#### <a name="example"></a>Przykład

Na przykład, w tym miejscu jest folder szablonu, który zawiera dwa pliki zawartości: *console.cs* i *readme.txt*. Zwróć uwagę, że nie ma wymaganego folderu o nazwie *. template.config* zawierający *template.json* pliku.

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

*Template.json* pliku wygląda podobnie do następującej:

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

*Mytemplate* folder znajduje się pakiet do zainstalowania szablonu. Po zainstalowaniu pakietu `shortName` mogą być używane z `dotnet new` polecenia. Na przykład `dotnet new adatumconsole` będą dane wyjściowe `console.cs` i `readme.txt` pliki do bieżącego folderu.

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Pakowanie szablonu do pakietu NuGet (plik nupkg)

Szablon niestandardowy jest wypełniona [pakietu dotnet](dotnet-pack.md) polecenia i *.csproj* pliku. Alternatywnie [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) mogą być używane z [pakiet nuget](https://docs.microsoft.com/nuget/tools/cli-ref-pack) polecenia wraz z *.nuspec* pliku. Jednak NuGet wymaga programu .NET Framework na Windows i [Mono](https://www.mono-project.com/) w systemie Linux i MacOS.

*.Csproj* pliku różni się nieco od tradycyjnych projekt kodu *.csproj* pliku. Zwróć uwagę na następujące ustawienia:

01. `<PackageType>` Ustawienie zostanie dodane i ustawiona `Template`.
01. `<PackageVersion>` Ustawienia zostaną dodane i ustawić prawidłową [numer wersji NuGet](/nuget/reference/package-versioning).
01. `<PackageId>` Ustawienia zostaną dodane i Ustaw unikatowy identyfikator. Ten identyfikator służy do odinstalowania szablonowego pakietu i jest używany przez NuGet źródeł danych, aby zarejestrować Twój pakiet szablonu.
01. Ustawienia ogólne metadanych powinna być ustawiona: `<Title>`, `<Authors>`, `<Description>`, i `<Tags>`.
01. `<TargetFramework>` Ustawienia należy wybrać opcję, nawet jeśli nie jest używany plik binarny, generowane przez szablon procesu. W poniższym przykładzie ustawiono go `netstandard2.0`.

Pakiet szablonu w formie *.nupkg* pakietu NuGet, wymaga, że wszystkie szablony znajdować się w *zawartości* folder w pakiecie. Istnieje kilka więcej ustawień, aby dodać do *.csproj* plik, aby upewnić się, że wygenerowany *.nupkg* można zainstalować jako szablonowego pakietu:

01. `<IncludeContentInPack>` Jest ustawiana `true` obejmujący dowolny plik projektu ustawia jako **zawartości** pakietu NuGet.
01. `<IncludeBuildOutput>` Jest ustawiana `false` wykluczyć wszystkie pliki binarne wygenerowane przez kompilator z pakietu NuGet.
01. `<ContentTargetFolders>` Ustawienie ma wartość `content`. Daje to pewność, że pliki są ustawione jako **zawartości** są przechowywane w *zawartości* folderu pakietu NuGet. Ten folder w pakiecie NuGet jest analizowany przez system szablonów dotnet.

Prosty sposób Wyklucz wszystkie pliki kodu z jest kompilowane przez projekt szablonu polega na użyciu `<Compile Remove="**\*" />` wewnątrz elementu w pliku projektu `<ItemGroup>` elementu.

Prosty sposób struktury dany pakiet szablonu jest umieścić wszystkie szablony w poszczególnych folderów, a następnie każdy folder szablonu wewnątrz *szablony* folder, który znajduje się w tym samym katalogu co Twoje *.csproj* plik. W ten sposób można użyć elementu pojedynczego projektu aby uwzględnić wszystkie pliki i foldery w *szablony* jako **zawartości**. Wewnątrz `<ItemGroup>` elementu, Utwórz `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` elementu.

Oto przykład *.csproj* pliku, który następuje po wszystkich powyższych wytycznych. Jego pakiety *szablony* folder podrzędny do *zawartości* pakiet folderu, a pomija każdy plik kodu kompilowanego.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <Tags>dotnet-new;templates;contoso</Tags>
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

W poniższym przykładzie pokazano strukturę plików i folderów przy użyciu *.csproj* utworzenie pakietu szablonu. *MyDotnetTemplates.csproj* pliku i *szablony* folder w katalogu głównym katalogu o nazwie znajdują się *project_folder*. *Szablony* folder zawiera dwa szablony *mytemplate1* i *mytemplate2*. Każdy szablon ma pliki zawartości i *. template.config* folder z *template.json* pliku konfiguracji.

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

Użyj [nowe dotnet -i | — instalowanie](dotnet-new.md) polecenie, aby zainstalować pakiet.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Aby zainstalować szablonu z pakietu NuGet, przechowywane w witrynie nuget.org

Użyj identyfikatora pakietu NuGet można zainstalować pakietu szablonu.

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Aby zainstalować szablonu z pliku lokalnego nupkg

Podaj ścieżkę do *.nupkg* plik pakietu NuGet.

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Aby zainstalować szablonu z katalogu w systemie plików

Szablony mogą być instalowane z folderu szablonu, takie jak *mytemplate1* folderu w powyższym przykładzie. Określ ścieżkę do folderu *. template.config* folderu. Ścieżka do katalogu szablonu nie musi być bezwzględna. Aby odinstalować szablon, który jest instalowany z folderu są jednak wymagane ścieżką bezwzględną.

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>Pobierz listę zainstalowanych szablonów

Polecenie odinstalowania, bez żadnych parametrów, spowoduje wyświetlenie listy wszystkich zainstalowanych szablonów.

```console
dotnet new -u
```

To polecenie zwraca coś podobnego do następujących danych wyjściowych:

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

Pierwszy poziom elementów po `Currently installed items:` to identyfikatory używane w odinstalowywanie szablonu. W powyższym przykładzie `Microsoft.DotNet.Common.ItemTemplates` i `Microsoft.DotNet.Common.ProjectTemplates.3.0` są wyświetlane. Jeśli szablon został zainstalowany przy użyciu ścieżki systemu plików, ten identyfikator będzie ścieżkę folderu *. template.config* folderu.

## <a name="uninstalling-a-template"></a>Odinstalowywanie szablonu

Użyj [nowe dotnet -u |--odinstalować](dotnet-new.md) polecenie, aby odinstalować pakiet.

Jeśli pakiet został zainstalowany przez kanał informacyjny NuGet lub przez *.nupkg* plików bezpośrednio, podaj identyfikator.

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

Jeśli pakiet został zainstalowany, określając ścieżkę do *. template.config* folderu, użycie **bezwzględne** ścieżki można odinstalować pakietu. Możesz zobaczyć ścieżkę bezwzględną szablonu w danych wyjściowych, dostarczone przez `dotnet new -u` polecenia. Aby uzyskać więcej informacji, zobacz [uzyskać listę zainstalowanych szablonów](#get-a-list-of-installed-templates) powyższej sekcji.

```console
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Tworzenie projektu przy użyciu szablonu niestandardowego

Po zainstalowaniu szablonu, należy użyć szablonu, wykonując `dotnet new <TEMPLATE>` polecenia jak każdego innego szablonu wstępnie zainstalowane. Można również określić [opcje](dotnet-new.md#options) do `dotnet new` polecenia, w tym opcje specyficzne dla szablonu, skonfigurowanego w ustawieniach szablonu. Podaj krótką nazwę szablonu bezpośrednio do polecenia:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonu niestandardowego dla platformy dotnet w nowych (samouczek)](../tutorials/create-custom-template.md)
- [repozytorium GitHub DotNet/szablonów witryny typu Wiki](https://github.com/dotnet/templating/wiki)
- [repozytorium GitHub DotNet/dotnet-— przykłady szablonów](https://github.com/dotnet/dotnet-template-samples)
- [Jak utworzyć nowe szablony dla platformy dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*Template.JSON* schemat w Store schematu JSON](http://json.schemastore.org/template)
