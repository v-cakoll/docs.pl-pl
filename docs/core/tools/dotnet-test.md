---
title: polecenie test DotNet — interfejs wiersza polecenia platformy .NET Core
description: Polecenia dotnet test służy do wykonywania testów jednostkowych w danym projekcie.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: e80ba874ec8d0fbc49858719dc3b9b6e02254c78
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696459"
---
# <a name="dotnet-test"></a>polecenia DotNet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet test` -Sterownik test .NET służących do wykonywania testów jednostkowych.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie. `dotnet test` Polecenie uruchamia aplikację konsolową modułu uruchamiającego test, określony dla projektu. Moduł uruchamiający testy zdefiniowane dla środowiska testów jednostkowych (np. MSTest, NUnit lub xUnit) są wykonywane i zgłasza powodzenie lub niepowodzenie każdego testu. Jeśli wszystkie testy zakończą się powodzeniem, narzędzia test runner zwraca wartość 0, kod zakończenia; Jeśli dowolny test zakończy się niepowodzeniem, w przeciwnym razie zwraca 1. Narzędzie test runner Biblioteka testów jednostkowych jest spakowany jako pakiety NuGet i zostaną przywrócone jako zwykłe zależności projektu.

Projekty testowe określić modułu uruchamiającego testy przy użyciu zwykłej `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Argumenty

`PROJECT`

Ścieżka do projektu testowego. Jeśli nie zostanie określony, domyślnie bieżącego katalogu.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.

`--blame`

Uruchamia testy w trybie polecenia blame. Ta opcja jest przydatna polega na wyizolowaniu problematyczne testy, powodując hosta testów ulega awarii. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* , przechwytuje kolejność wykonywania testów przed awarią.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Włącza moduł zbierający dane dla przebiegu testu. Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.

`-f|--framework <FRAMEWORK>`

Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia. Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji. Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-l|--logger <LoggerUri/FriendlyName>`

Określa Rejestrator dla wyników badań.

`--no-build`

Nie da się skompilować projektu testowego przed jego uruchomieniem. Ustawia ona również niejawne `--no-restore` flagi.

`--no-restore`

Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można znaleźć plików binarnych do uruchomienia.

`-r|--results-directory <PATH>`

Katalog, gdzie wyników testu do umieszczenia. Jeśli określony katalog nie istnieje, zostanie utworzony.

`-s|--settings <SETTINGS_FILE>`

Ustawienia używane podczas uruchamiania testów.

`-t|--list-tests`

Listę wszystkich odnalezionych testów w bieżącym projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Włącza moduł zbierający dane dla przebiegu testu. Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testu](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.

`-f|--framework <FRAMEWORK>`

Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia. Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji. Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-l|--logger <LoggerUri/FriendlyName>`

Określa Rejestrator dla wyników badań.

`--no-build`

Nie da się skompilować projektu testowego przed jego uruchomieniem. Ustawia ona również niejawne `--no-restore` flagi.

`--no-restore`

Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można znaleźć plików binarnych do uruchomienia.

`-r|--results-directory <PATH>`

Katalog, gdzie wyników testu do umieszczenia. Jeśli określony katalog nie istnieje, zostanie utworzony.

`-s|--settings <SETTINGS_FILE>`

Ustawienia używane podczas uruchamiania testów.

`-t|--list-tests`

Listę wszystkich odnalezionych testów w bieżącym projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Używa niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale konfiguracji projektu można zastąpić to ustawienie SDK domyślne.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Włącza tryb diagnostycznych dla testu platformy i zapisu komunikaty diagnostyczne do określonego pliku.

`-f|--framework <FRAMEWORK>`

Wyszukuje pliki binarne testu dla określonego [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy w bieżącym projekcie za pomocą podanego wyrażenia. Aby uzyskać więcej informacji, zobacz [szczegóły opcji filtru](#filter-option-details) sekcji. Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-l|--logger <LoggerUri/FriendlyName>`

Określa Rejestrator dla wyników badań.

`--no-build`

Nie da się skompilować projektu testowego przed jego uruchomieniem.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można znaleźć plików binarnych do uruchomienia.

`-s|--settings <SETTINGS_FILE>`

Ustawienia używane podczas uruchamiania testów.

`-t|--list-tests`

Listę wszystkich odnalezionych testów w bieżącym projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

---

## <a name="examples"></a>Przykłady

Uruchom testy w projekcie w bieżącym katalogu:

`dotnet test`

Uruchom testy `test1` projektu:

`dotnet test ~/projects/test1/test1.csproj`

Uruchom testy w projekcie w bieżącym katalogu i wygenerować plik wyników testu w formacie trx:

`dotnet test --logger:trx`

## <a name="filter-option-details"></a>Szczegóły opcji filtru

`--filter <EXPRESSION>`

`<Expression>` ma format `<property><operator><value>[|&<Expression>]`.

`<property>` jest to atrybut `Test Case`. Poniżej przedstawiono właściwości obsługiwanych przez platform testów jednostkowych innych popularnych:

| Struktury testowej | Obsługiwanych właściwości                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Nazwa</li><li>className</li><li>Priorytet</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>Nazwa wyświetlana</li><li>Cechy</li></ul>                                   |

`<operator>` Opisuje relację między właściwości i wartości:

| Operator | Funkcja        |
| :------: | --------------- |
| `=`      | Dokładne dopasowanie     |
| `!=`     | Nie dokładne dopasowanie |
| `~`      | Zawiera        |

`<value>` jest to ciąg. Wszystkie wyszukiwania jest rozróżniana wielkość liter.

Wyrażenie bez `<operator>` jest automatycznie traktowane jako `contains` na `FullyQualifiedName` właściwości (na przykład `dotnet test --filter xyz` jest taka sama jak `dotnet test --filter FullyQualifiedName~xyz`).

Wyrażenia może być łączone z operatorów warunkowych:

| Operator            | Funkcja |
| ------------------- | -------- |
| <code>&#124;</code> | LUB       |
| `&`                 | AND      |

Może być częścią wyrażenia w nawiasach przy użyciu operatorów warunkowych (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).

Aby uzyskać dodatkowe informacje i przykłady dotyczące korzystania z jednostki selektywne testowanie filtrowania, zobacz [uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Zobacz także

* [Struktury i obiekty docelowe](../../standard/frameworks.md)  
* [Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)
