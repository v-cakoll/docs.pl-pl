---
title: Szablony niestandardowe dla nowej platformy dotnet
description: Dowiedz się więcej na temat szablonów niestandardowych dla dowolnego typu projektu .NET lub plików.
author: guardrex
ms.date: 08/11/2017
ms.openlocfilehash: 23dac9f4efd64ff93b00e41b1f4195e964871a3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503929"
---
# <a name="custom-templates-for-dotnet-new"></a>Szablony niestandardowe dla nowej platformy dotnet

[Zestawu .NET Core SDK](https://www.microsoft.com/net/download/core) jest dostarczany z wielu szablonów wstępnie zainstalowane za pomocą [ `dotnet new` polecenia](dotnet-new.md). Począwszy od programu .NET Core 2.0, można utworzyć własne szablony niestandardowe dla każdego typu projektu, takie jak aplikacja, usługi, narzędzia lub biblioteki klas. Możesz nawet utworzyć szablon, który generuje co najmniej jeden niezależnych plikach, takich jak plik konfiguracji.

Można zainstalować niestandardowe szablony z pakietu NuGet dla dowolnego narzędzia NuGet kanału informacyjnego, odwołując się do NuGet *nupkg* plików bezpośrednio lub przez określenie katalogu systemu plików, który zawiera szablon. Aparat szablonów oferuje funkcje, które pozwala zastąpić wartości, dołączać i wykluczać, pliki i regiony plików, a wykonywanie niestandardowych operacji, gdy szablon jest używany.

Aparat szablonów "open source", a repozytorium kodu w trybie online jest w [dotnet/szablonów](https://github.com/dotnet/templating/) w witrynie GitHub. Odwiedź stronę [dotnet/dotnet szablonu samples](https://github.com/dotnet/dotnet-template-samples) repozytorium przykładów szablonów. Więcej szablonów, w tym szablony innych firm, znajdują się w [dostępnych szablonów dla platformy dotnet nowe](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) w witrynie GitHub. Aby uzyskać więcej informacji na temat tworzenia i używania niestandardowych szablonów, zobacz [sposobu tworzenia nowych szablonów dla platformy dotnet](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/) i [repozytorium GitHub dotnet/szablonów Wiki](https://github.com/dotnet/templating/wiki).

Aby wykonać przewodnik i utworzyć szablon, zobacz [Utwórz nowy szablon niestandardowy dla platformy dotnet](~/docs/core/tutorials/create-custom-template.md) samouczka.

## <a name="configuration"></a>Konfiguracja

Szablon składa się z następujących składników:

- Źródło plików i folderów
- Plik konfiguracji (*template.json*)

### <a name="source-files-and-folders"></a>Źródło plików i folderów

Pliki źródłowe i foldery obejmują dowolnych pliki i foldery, które mają szablonu aparatu do użycia podczas `dotnet new <TEMPLATE>` polecenie jest wykonywane. Aparat szablonów jest przeznaczony do stosowania *możliwy do uruchomienia projektów* jako źródło kodu do tworzenia projektów. To ma kilka zalet:

- Aparat szablonów nie wymaga wstrzyknąć specjalne tokeny do kodu źródłowego projektu.
- Pliki kodu nie są specjalne pliki lub zmodyfikowane w dowolny sposób, aby pracować z aparatu szablonów. Tak narzędzi, które normalnie używane podczas pracy z projektami również działać przy użyciu szablonu zawartości.
- Tworzenie, uruchamianie i debugowanie projektów szablonu, podobnie jak w przypadku wszystkich innych projektów.
- Możesz szybko utworzyć szablon z istniejącego projektu, po prostu przez dodanie *template.json* pliku konfiguracji do projektu.

Plików i folderów przechowywanych w szablonie nie ma ograniczenia dla formalnych typów projektów platformy .NET, takie jak rozwiązania .NET Core lub .NET Framework. Źródło plików i folderów może zawierać żadnej zawartości, którą chcesz utworzyć, gdy szablon jest używany, nawet wtedy, gdy aparat szablonów tworzy tylko jeden plik dla danych wyjściowych, takich jak plik konfiguracji lub plik rozwiązania. Na przykład można utworzyć szablon, który zawiera *web.config* pliku źródłowego i tworzy zmodyfikowane *web.config* pliku dla projektów, w których jest używany szablon. Zmiany do plików źródłowych na podstawie logiki i ustawienia podane w *template.json* pliku konfiguracji wraz z wartościami, dostarczone przez użytkownika jest przekazywany jako opcje `dotnet new <TEMPLATE>` polecenia.

### <a name="templatejson"></a>template.json

*Template.json* plik zostanie umieszczony w *. template.config* folder w katalogu głównym szablonu. Plik zawiera informacje o konfiguracji do aparatu szablonu. Minimalna konfiguracja wymaga od członków, pokazano w poniższej tabeli, która jest wystarczające, aby utworzyć szablon funkcjonalności.

| Element członkowski            | Typ          | Opis |
| ----------------- | ------------- | ----------- |
| `$schema`         | Identyfikator URI           | Schemat JSON dla *template.json* pliku. Edytory, które obsługują schematów JSON Włącz funkcje Edycja JSON, jeśli nie określono schematu. Na przykład [programu Visual Studio Code](https://code.visualstudio.com/) wymaga tego elementu członkowskiego włączyć technologię IntelliSense. Użyj wartości `http://json.schemastore.org/template`. |
| `author`          | string        | Autor szablonu. |
| `classifications` | Array(String) | Zero lub więcej właściwości szablon, którego użytkownik może znaleźć szablonu podczas wyszukiwania dla niego. Klasyfikacje są również wyświetlane w *tagi* kolumny, gdy się pojawi się na liście szablony utworzone za pomocą <code>dotnet new -l&#124;--list</code> polecenia. |
| `identity`        | string        | Unikatowa nazwa dla tego szablonu. |
| `name`            | string        | Nazwa szablonu, która powinna być widoczna. |
| `shortName`       | string        | Skrót właściwości domyślne służąca do wybierania szablonu, który ma zastosowanie do środowiska, w którym nazwa szablonu jest określony przez użytkownika nie są wybrane za pomocą graficznego interfejsu użytkownika. Na przykład krótką nazwę przydaje się podczas korzystania z szablonów z poziomu wiersza polecenia przy użyciu interfejsu wiersza polecenia. |

#### <a name="example"></a>Przykład:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Catalina Garcia",
  "classifications": [ "Common", "Console" ],
  "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
  "name": "Garcia Software Console Application",
  "shortName": "garciaconsole"
}
```

Pełnego schematu dla *template.json* plik znajduje się na [Store schematu JSON](http://json.schemastore.org/template).

## <a name="net-default-templates"></a>Szablony domyślne platformy .NET

Po zainstalowaniu [zestawu .NET Core SDK](https://www.microsoft.com/net/download/core), pojawi się ponad tuzina wbudowanych szablonów do tworzenia projektów i plików, w tym aplikacje konsoli, bibliotekach klas, jednostka testowanie projektów, aplikacje platformy ASP.NET Core (w tym [Angular](https://angular.io/) i [React](https://facebook.github.io/react/) projektów) i pliki konfiguracyjne. Aby wyświetlić listę wbudowanych szablonów, należy wykonać `dotnet new` polecenia `-l|--list` opcji:

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Pakowanie szablonu do pakietu NuGet (plik nupkg)

Obecnie szablon niestandardowy jest pakowany w Windows za pomocą [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (nie [pakietu dotnet](dotnet-pack.md)). Tworzenie pakietów dla wielu platform, rozważ użycie [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).

Zawartość folderu projektu, wraz z jego *.template.config/template.json* plików, są umieszczane w folderze o nazwie *zawartości*. Obok pozycji *zawartości* folderu, Dodaj [ *nuspec* pliku](/nuget/create-packages/creating-a-package), czyli pliku manifestu XML, który opisuje zawartość pakietu i dyski proces tworzenia pakietu NuGet. Wewnątrz  **\<packageTypes >** element *nuspec* plików, obejmują  **\<packageType >** element z `name` wartość atrybutu `Template`. Zarówno *zawartości* folder i *nuspec* plik powinien znajdować się w tym samym katalogu. W tabeli przedstawiono minimalne *nuspec* pliku elementów wymaganych do utworzenia szablonu jako pakiet NuGet.

| Element            | Typ   | Opis |
| ------------------ | ------ | ----------- |
| **\<authors>**     | string | Rozdzielana przecinkami lista autorów pakietów, pasujące nazwy profilu w witrynie nuget.org. Autorzy są wyświetlane w galerii pakietów NuGet w witrynie nuget.org i są odwoływania się do pakietów przez ten sam autorów. |
| **\<description>** | string | Długi opis pakietu do wyświetlania w interfejsie użytkownika. |
| **\<id>**          | string | Identyfikator pakietu bez uwzględniania wielkości liter, który musi być unikatowa w witrynie nuget.org lub cokolwiek innego pakietu będą znajdować się w galerii. Identyfikatory nie może zawierać spacji ani znaków, które nie są prawidłowe dla danego adresu URL i zazwyczaj korzystają z reguły w przestrzeni nazw .NET. Zobacz [wybierając identyfikator unikatowy pakiet i ustawiania numeru wersji](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) wskazówki. |
| **\<packageType>** | string | Umieść ten element wewnątrz  **\<packageTypes >** element między  **\<metadanych >** elementów. Ustaw `name` atrybutu  **\<packageType >** elementu `Template`. |
| **\<version>**     | string | Wersja pakietu, następujące Wersja_główna.WERSJA_POMOCNICZA.poprawka. Numery wersji mogą zawierać sufiks wersji wstępnej, zgodnie z opisem w [wersje wstępne](/nuget/create-packages/prerelease-packages#semantic-versioning) tematu. |

Zobacz [odwołania .nuspec](/nuget/schema/nuspec) dla pełnego *nuspec* pliku schematu. Przykład *nuspec* plik szablonu, który pojawia się w [Utwórz nowy szablon niestandardowy dla platformy dotnet](~/docs/core/tutorials/create-custom-template.md) samouczka.

[Utwórz pakiet](/nuget/create-packages/creating-a-package#creating-the-package) przy użyciu `nuget pack <PATH_TO_NUSPEC_FILE>` polecenia.

## <a name="installing-a-template"></a>Instalowanie szablonu

Instalowanie niestandardowego szablonu z pakietu NuGet dla dowolnego narzędzia NuGet kanału informacyjnego, odwołując się do *nupkg* plików bezpośrednio lub przez określenie katalogu systemu plików, który zawiera konfiguracji szablonów. Użyj `-i|--install` z opcją [dotnet nowe](dotnet-new.md) polecenia.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Aby zainstalować szablonu z pakietu NuGet, przechowywane w witrynie nuget.org

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Aby zainstalować szablonu z pliku lokalnego nupkg

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Aby zainstalować szablonu z katalogu w systemie plików

`FILE_SYSTEM_DIRECTORY` Jest folder projektu, zawierający projekt i *. template.config* folderu:

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>Odinstalowywanie szablonu

Odinstaluj niestandardowy szablon, odwołując się do pakietu NuGet przez jego `id` lub określając katalog systemu plików, który zawiera konfigurację szablonów. Użyj `-u|--uninstall` zainstalować opcji [dotnet nowe](dotnet-new.md) polecenia.

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Aby odinstalować szablonu z pakietu NuGet, przechowywane w witrynie nuget.org

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>Aby odinstalować szablonu z pliku lokalnego nupkg

Aby odinstalować szablonu, nie próbują użyć ścieżki do *nupkg* pliku. Podjęto próbę ją odinstalować przy użyciu szablonu `dotnet new -u <PATH_TO_NUPKG_FILE>` zakończy się niepowodzeniem. Odwołują się do pakietu, jego `id`:

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>Aby odinstalować szablonu z katalogu w systemie plików

`FILE_SYSTEM_DIRECTORY` Jest folder projektu, zawierający projekt i *. template.config* folderu. Ścieżka podana musi być ścieżką bezwzględną. Podjęto próbę odinstalowanie szablonu za pomocą ścieżki względnej zakończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz [dotnet nowe](dotnet-new.md) artykułu.

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Tworzenie projektu przy użyciu szablonu niestandardowego

Po zainstalowaniu szablonu, należy użyć szablonu, wykonując `dotnet new <TEMPLATE>` polecenia jak każdego innego szablonu wstępnie zainstalowane. Można również określić [opcje](dotnet-new.md#options) do `dotnet new` polecenia, w tym szablonie określonych opcji skonfigurowanych w ustawieniach szablonu. Podaj krótką nazwę szablonu bezpośrednio do polecenia:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonu niestandardowego dla platformy dotnet w nowych (samouczek)](../tutorials/create-custom-template.md)
- [repozytorium GitHub DotNet/szablonów witryny typu Wiki](https://github.com/dotnet/templating/wiki)
- [repozytorium GitHub DotNet/dotnet-— przykłady szablonów](https://github.com/dotnet/dotnet-template-samples)
- [Jak utworzyć nowe szablony dla platformy dotnet](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)
- [*Template.JSON* schemat w Store schematu JSON](http://json.schemastore.org/template)
