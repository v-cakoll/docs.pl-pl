---
title: polecenie test DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8a10ac9175ee5fcf8649efbb07d8d382ac3afdc7
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696273"
---
# <a name="dotnet-test"></a>DotNet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet test` — .NET testowanie sterowników używane do wykonywania testów jednostkowych.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie. `dotnet test` Polecenie uruchamia aplikację konsoli test runner określony dla projektu. Moduł uruchamiający wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raporty powodzenie lub niepowodzenie każdego z testów. Moduł uruchamiający Biblioteka testów jednostkowych są dostarczane w pakietach NuGet i zostaną przywrócone jako zwykłej zależności projektu.

Projekty testowe Określ uruchamiający przy użyciu zwykłego `<PackageReference>` element, taki jak pokazano w poniższym przykładowym pliku projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Argumenty

`PROJECT`

Ścieżka do projektu testowego. Jeśli nie zostanie określony, domyślnie bieżącego katalogu.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.

`--blame`

Uruchamia testy w trybie winy. Ta opcja jest pomocna w izolowanie testów problemy powodujące hosta testów do awarii. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* który przechwytuje kolejność wykonywania testów przed tej awarii.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Włącza moduł zbierający dane dla uruchomienia testu. Aby uzyskać więcej informacji, zobacz [monitora i analizować uruchomienia testu](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.

`-f|--framework <FRAMEWORK>`

Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji. Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-l|--logger <LoggerUri/FriendlyName>`

Określa Rejestrator dla wyników testu.

`--no-build`

Nie można utworzyć projektu testowego przed jego uruchomieniem. Niejawne także ustawia `--no-restore` flagi.

`--no-restore`

Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można znaleźć plików binarnych do uruchomienia.

`-r|--results-directory <PATH>`

Katalog, w której będzie można umieścić wyników testu. Jeśli określony katalog nie istnieje, jest tworzony.

`-s|--settings <SETTINGS_FILE>`

Ustawienia używane podczas uruchamiania testów.

`-t|--list-tests`

Lista wszystkich odnalezionych testów w bieżącym projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Włącza moduł zbierający dane dla uruchomienia testu. Aby uzyskać więcej informacji, zobacz [monitora i analizować uruchomienia testu](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.

`-f|--framework <FRAMEWORK>`

Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji. Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-l|--logger <LoggerUri/FriendlyName>`

Określa Rejestrator dla wyników testu.

`--no-build`

Nie można utworzyć projektu testowego przed jego uruchomieniem. Niejawne także ustawia `--no-restore` flagi.

`--no-restore`

Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można znaleźć plików binarnych do uruchomienia.

`-r|--results-directory <PATH>`

Katalog, w której będzie można umieścić wyników testu. Jeśli określony katalog nie istnieje, jest tworzony.

`-s|--settings <SETTINGS_FILE>`

Ustawienia używane podczas uruchamiania testów.

`-t|--list-tests`

Lista wszystkich odnalezionych testów w bieżącym projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Używa niestandardowych adapterów testowych z określonej ścieżki w uruchomieniu testu.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale konfiguracja projektu można zastąpić to ustawienie domyślne zestawu SDK.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.

`-f|--framework <FRAMEWORK>`

Wyszukuje pliki binarne testów dla określonego [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz [opcję Szczegóły filtru](#filter-option-details) sekcji. Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-l|--logger <LoggerUri/FriendlyName>`

Określa Rejestrator dla wyników testu.

`--no-build`

Nie można utworzyć projektu testowego przed jego uruchomieniem.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można znaleźć plików binarnych do uruchomienia.

`-s|--settings <SETTINGS_FILE>`

Ustawienia używane podczas uruchamiania testów.

`-t|--list-tests`

Lista wszystkich odnalezionych testów w bieżącym projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

---

## <a name="examples"></a>Przykłady

Uruchom testy w projekcie w bieżącym katalogu:

`dotnet test`

Uruchom testy `test1` projektu:

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a>Szczegóły opcji filtru

`--filter <EXPRESSION>`

`<Expression>` ma format `<property><operator><value>[|&<Expression>]`.

`<property>` atrybut `Test Case`. Właściwości obsługiwanych przez platform testów jednostkowych popularnych są następujące:

| Struktury testowej | Obsługiwanych właściwości                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Nazwa</li><li>className</li><li>Priorytet</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>Nazwa wyświetlana</li><li>Cechy</li></ul>                                   |

`<operator>` Opisuje relację między właściwości i wartość:

| Operator | Funkcja        |
| :------: | --------------- |
| `=`      | Dokładnego dopasowania     |
| `!=`     | Nie dokładnego dopasowania |
| `~`      | Zawiera        |

`<value>` jest to ciąg. Wszystkie wyszukiwania są bez uwzględniania wielkości liter.

Wyrażenia bez `<operator>` jest automatycznie traktowane jako `contains` na `FullyQualifiedName` właściwości (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).

Może być częścią wyrażenia z operatorami warunkowego:

| Operator            | Funkcja |
| ------------------- | -------- |
| <code>&#124;</code> | LUB       |
| `&`                 | AND      |

Może być częścią wyrażenia w nawiasach przy użyciu operatorów warunkowych (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).

Aby uzyskać dodatkowe informacje i przykłady dotyczące sposobu używania filtrowanie testów jednostki selektywnego, zobacz [przeprowadzanie testów jednostkowych selektywne](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Zobacz także

[Struktury i cele](../../standard/frameworks.md)  
[Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)
