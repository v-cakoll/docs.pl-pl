---
title: Szablony niestandardowe dla nowego dotnet
description: "Więcej informacji na temat szablonów niestandardowych dla dowolnego typu .NET projektu lub plików."
keywords: "DotNet nowe, interfejsu wiersza polecenia, interfejsu wiersza polecenia polecenia .NET Core, szablon, tworzenia szablonów"
author: guardrex
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.openlocfilehash: c68e382450a763fd0521b7defdd79d8433e1acde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-templates-for-dotnet-new"></a>Szablony niestandardowe dla nowego dotnet

[.NET Core SDK](https://www.microsoft.com/net/download/core) zawiera wiele szablonów, aby móc korzystać z wstępnie zainstalować [ `dotnet new` polecenia](dotnet-new.md). Począwszy od programu .NET Core 2.0, można utworzyć szablony niestandardowe dla dowolnego typu projektu, takie jak aplikacji, usługi, narzędzie lub biblioteki klas. Można nawet utworzyć szablon, który wyprowadza co najmniej jeden niezależnych plikach, takich jak plik konfiguracji.

Szablony niestandardowe można zainstalować z pakietu NuGet w dowolnym NuGet źródła danych, odwołując NuGet *nupkg* pliku bezpośrednio lub przez określenie katalog systemu plików, który zawiera szablon. Aparat szablonów udostępnia funkcje, które umożliwiają Zastąp wartości, Dołącz i Wyklucz pliki i regiony plików i wykonuje operacje przetwarzania niestandardowych, gdy szablon jest używany.

Aparat szablonów typu open source, a repozytorium online kodu jest w [dotnet/tworzenia szablonów](https://github.com/dotnet/templating/) w witrynie GitHub. Odwiedź stronę [dotnet/dotnet szablonu — przykłady](https://github.com/dotnet/dotnet-template-samples) repozytorium, aby wyświetlić przykłady szablonów. Znaleziono więcej szablonów, w tym szablony od osób trzecich, na [dostępnych szablonów dla platformy dotnet nowe](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) w witrynie GitHub. Aby uzyskać więcej informacji na temat tworzenia i używania szablonów niestandardowych, zobacz [sposobu tworzenia nowych szablonów dla platformy dotnet](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/) i [repozytorium GitHub dotnet/tworzenia szablonów Wiki](https://github.com/dotnet/templating/wiki).

Aby wykonać wskazówki i tworzenia szablonu, zobacz [Utwórz nowy szablon niestandardowy dla platformy dotnet](~/docs/core/tutorials/create-custom-template.md) samouczka.

## <a name="configuration"></a>Konfiguracja

Szablon składa się z następujących składników:

- Pliki źródłowe i folderów
- Plik konfiguracji (*template.json*)

### <a name="source-files-and-folders"></a>Pliki źródłowe i folderów

Pliki źródłowe i foldery obejmują wszelkie pliki i foldery szablon aparat do użycia podczas `dotnet new <TEMPLATE>` polecenie jest wykonywane. Aparat szablon jest przeznaczony do użycia *do uruchomienia projektów* jako źródło kodu do tworzenia projektów. To ma wiele zalet:

- Aparat szablonów nie wymaga iniekcję specjalne tokeny do kodu źródłowego projektu.
- Pliki kodu są specjalne pliki lub zmodyfikowane w dowolny sposób, aby pracować z aparatu szablonu. Tak narzędzia, która zwykle jest używana podczas pracy z projektami również współpracować z zawartości szablonu.
- Tworzenie, uruchamiania i debugowanie projektów szablonu, podobnie jak w przypadku wszystkich innych projektów.
- Można szybko utworzyć szablon z istniejącego projektu, po prostu dodając *template.json* pliku konfiguracji do projektu.

Pliki i foldery przechowywane w szablonie nie są ograniczone do formalnego typy projektu platformy .NET, takie jak rozwiązań platformy .NET Core lub .NET Framework. Pliki źródłowe i folderów może składać się z zawartość, która ma zostać utworzony, kiedy szablon jest używany, nawet wtedy, gdy aparat szablon tworzy tylko jednego pliku danych wyjściowych, takich jak plik konfiguracji lub pliku rozwiązania. Na przykład można utworzyć szablon, który zawiera *web.config* plik źródłowy i tworzy zmodyfikowanych *web.config* pliku dla projektów, w którym szablon jest używany. Te zmiany do plików źródłowych na podstawie logiki i ustawienia podane w *template.json* przekazany plik konfiguracji oraz wartości podanych przez użytkownika jako opcje `dotnet new <TEMPLATE>` polecenia.

### <a name="templatejson"></a>Template.JSON

*Template.json* plik jest umieszczany w *. template.config* folder w katalogu głównym szablonu. Plik zawiera informacje o konfiguracji do aparatu szablonu. Minimalna konfiguracja wymaga członków pokazano w poniższej tabeli są wystarczające, aby utworzyć szablon funkcjonalności.

| Element członkowski            | Typ          | Opis |
| ----------------- | ------------- | ----------- |
| `$schema`         | Identyfikator URI           | Schematu JSON dla *template.json* pliku. Edytory, które obsługują schematów JSON włączyć funkcje edycji JSON, gdy określono schemat. Na przykład [Visual Studio Code](https://code.visualstudio.com/) wymaga tego elementu członkowskiego włączyć IntelliSense. Użyj wartości elementu `http://json.schemastore.org/template`. |
| `author`          | string        | Autor szablonu. |
| `classifications` | Array(String) | Zero lub więcej właściwości szablonu, który użytkownik może użyć można znaleźć szablonu podczas wyszukiwania dla niego. Klasyfikacje są również wyświetlane w *tagi* kolumny, gdy pojawi się on na liście szablony utworzone za pomocą <code>dotnet new -l&#124;--list</code> polecenia. |
| `identity`        | string        | Unikatowa nazwa tego szablonu. |
| `name`            | string        | Nazwa szablonu, która powinna zostać wyświetlona użytkowników. |
| `shortName`       | string        | Domyślne skróconą formą wybór szablonu, która ma zastosowanie do środowiska, w którym nazwa szablonu jest określona przez wybrany przez użytkownika, nie za pomocą graficznego interfejsu użytkownika. Na przykład krótka nazwa jest przydatne, gdy za pomocą szablonów z wiersza polecenia za pomocą polecenia interfejsu wiersza polecenia. |

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

Pełna schematu *template.json* plik znajduje się w [magazynu schematu JSON](http://json.schemastore.org/template).

## <a name="net-default-templates"></a>Szablony domyślne .NET

Po zainstalowaniu [.NET Core SDK](https://www.microsoft.com/net/download/core), pojawi się powyżej dwanaście wbudowane szablony do tworzenia projektów i pliki, w tym aplikacji konsoli, biblioteki klas, jednostka przetestowania projektów aplikacji platformy ASP.NET Core (w tym [kątową](https://angular.io/) i [React](https://facebook.github.io/react/) projektów) oraz plików konfiguracji. Aby wyświetlić listę wbudowanych szablonów, należy wykonać `dotnet new` z `-l|--list` opcji:

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Pakowanie szablonu w pakiecie NuGet (pliku nupkg)

Obecnie szablonu niestandardowego są pakowane w systemie Windows z [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (nie [pakiet dotnet](dotnet-pack.md)). Opakowanie i platform, należy rozważyć użycie [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).

Zawartość folderu projektu, wraz z jego *.template.config/template.json* plików, są umieszczane w folderze o nazwie *zawartości*. Obok pozycji *zawartości* folderu, Dodaj [ *nuspec* pliku](/nuget/create-packages/creating-a-package), czyli plik manifestu XML, który opisuje zawartość pakietu i dyskach proces tworzenia pakietu NuGet. Wewnątrz  **\<packageTypes >** element *nuspec* plików, obejmują  **\<packageType >** element z `name` wartość atrybutu `Template`. Zarówno *zawartości* folderu i *nuspec* plik powinien znajdować się w tym samym katalogu. W tabeli przedstawiono minimum *nuspec* pliku elementy wymagane do tworzenia szablonu jako pakietu NuGet.

| Element            | Typ   | Opis |
| ------------------ | ------ | ----------- |
| **\<Autorzy >**     | string | Rozdzielana przecinkami lista autorzy pakietów, zgodne z nazwami profilu na nuget.org. Autorzy są wyświetlane w galerii NuGet w nuget.org i są odwoływania się do pakietów przez tego samego autorów. |
| **\<Opis elementu >** | string | Długi opis pakietu do wyświetlenia interfejsu użytkownika. |
| **\<Identyfikator >**          | string | Identyfikator pakietu bez uwzględniania wielkości liter, który musi być unikatowa w nuget.org lub niezależnie od pakietu będą znajdować się w galerii. Identyfikatory nie może zawierać spacji ani znaków, które nie są prawidłowe dla danego adresu URL i ogólnie zgodne reguły obszaru nazw .NET. Zobacz [wybranie identyfikator unikatowy pakiet i ustawianie numeru wersji](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) orientacji. |
| **\<packageType >** | string | Umieść ten element wewnątrz  **\<packageTypes >** element między  **\<metadanych >** elementów. Ustaw `name` atrybutu  **\<packageType >** elementu `Template`. |
| **\<Wersja >**     | string | Wersja pakietu, następujące wzorzec Wersja_główna.WERSJA_POMOCNICZA.poprawka. Numery wersji może zawierać sufiks wersji wstępnej, zgodnie z opisem w [wersje wstępne](/nuget/create-packages/prerelease-packages#semantic-versioning) tematu. |

Zobacz [odwołania .nuspec](/nuget/schema/nuspec) dla pełnej *nuspec* pliku schematu. Przykład *nuspec* plik szablonu jest wyświetlana w [Utwórz nowy szablon niestandardowy dla platformy dotnet](~/docs/core/tutorials/create-custom-template.md) samouczka.

[Utwórz pakiet](/nuget/create-packages/creating-a-package#creating-the-package) przy użyciu `nuget pack <PATH_TO_NUSPEC_FILE>` polecenia.

## <a name="installing-a-template"></a>Instalowanie szablonu

Zainstaluj szablon niestandardowy z pakietu NuGet w dowolnym NuGet źródła danych za pomocą odwołań do *nupkg* pliku bezpośrednio lub za pośrednictwem katalogu systemu plików, który zawiera konfigurację tworzenia szablonów. Użyj `-i|--install` opcję z [dotnet nowe](dotnet-new.md) polecenia.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Aby zainstalować szablonu z pakietem NuGet przechowywane w nuget.org

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Aby zainstalować szablonu z pliku lokalnego nupkg

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Aby zainstalować szablonu z katalogu w systemie plików

`FILE_SYSTEM_DIRECTORY` Jest folder projekt zawierający projekt i *. template.config* folderu:

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>Odinstalowywanie szablonu

Odinstaluj szablon niestandardowy, umieszczając odwołanie do pakietu NuGet przez jego `id` lub określając katalog systemu plików, który zawiera konfigurację tworzenia szablonów. Użyj `-u|--uninstall` opcji z [dotnet nowe](dotnet-new.md) polecenia.

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Aby odinstalować szablonu z pakietem NuGet przechowywane w nuget.org

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>Aby odinstalować szablonu z pliku lokalnego nupkg

Jeśli chcesz odinstalować szablonu nie próbuj Użyj ścieżki do *nupkg* pliku. *Podjęto próbę ją odinstalować przy użyciu szablonu `dotnet new -u <PATH_TO_NUPKG_FILE>` zakończy się niepowodzeniem.* Odwołują się do pakietu przez jego `id`:

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>Aby odinstalować szablonu z katalogu w systemie plików

`FILE_SYSTEM_DIRECTORY` Jest folder projekt zawierający projekt i *. template.config* folderu:

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Tworzenie projektu przy użyciu szablonu niestandardowego

Po zainstalowaniu szablonu, za pomocą szablonu, wykonując `dotnet new <TEMPLATE>` polecenia jak każdy inny szablon wstępnie zainstalowane. Można również określić [opcje](dotnet-new.md#options) do `dotnet new` polecenia, w tym szablonie określonych opcji skonfigurowanych w ustawieniach szablonu. Podaj krótką nazwę szablonu bezpośrednio do polecenia:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Zobacz także

[Utwórz niestandardowy szablon dla nowych dotnet (samouczek)](../tutorials/create-custom-template.md)  
[repozytorium GitHub DotNet/tworzenia szablonów Wiki](https://github.com/dotnet/templating/wiki)  
[repozytorium GitHub DotNet/dotnet szablonu — przykłady](https://github.com/dotnet/dotnet-template-samples)  
[Jak utworzyć nowe szablony dla platformy dotnet](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[*Template.JSON* schematu w magazynie schematów JSON](http://json.schemastore.org/template)  
