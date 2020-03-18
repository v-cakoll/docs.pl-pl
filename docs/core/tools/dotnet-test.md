---
title: polecenie testu dotnet
description: Polecenie testu dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 02/27/2020
ms.openlocfilehash: bac2f0e613c34bc9f657551a5eac4038207a93ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847901"
---
# <a name="dotnet-test"></a>dotnet test

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet test`- Sterownik testowy .NET używany do wykonywania testów jednostkowych.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path] [--blame] [-c|--configuration]
    [--collect] [-d|--diag] [-f|--framework] [--filter]
    [--interactive] [-l|--logger] [--no-build] [--nologo]
    [--no-restore] [-o|--output] [-r|--results-directory]
    [--runtime] [-s|--settings] [-t|--list-tests]
    [-v|--verbosity] [[--] <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet test` służy do wykonywania testów jednostkowych w danym projekcie. Polecenie `dotnet test` uruchamia aplikację konsoli programu testowego określonej dla projektu. Test runner wykonuje testy zdefiniowane dla struktury testu jednostkowego (na przykład MSTest, NUnit lub xUnit) i zgłasza powodzenie lub niepowodzenie każdego testu. Jeśli wszystkie testy się powiodą, test runner zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli jakikolwiek test nie powiedzie się, zwraca 1. Narzędzie do testowania i biblioteka testów jednostkowych są pakowane jako pakiety NuGet i są przywracane jako zwykłe zależności dla projektu.

Projekty testowe określają testrunner `<PackageReference>` przy użyciu zwykłego elementu, jak widać w następującym przykładowym pliku projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Argumenty

- **`PROJECT | SOLUTION`**

  Ścieżka do projektu testowego lub rozwiązania. Jeśli nie zostanie określony, domyślnie jest to bieżący katalog.

## <a name="options"></a>Opcje

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Użyj niestandardowych kart testowych z określonej ścieżki w przebiegu testowym.

- **`-blame`**

  Uruchamia testy w trybie winy. Ta opcja jest pomocna w izolowaniu problematycznych testów, które powodują awarię hosta testowego. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml,* który przechwytuje kolejność wykonywania testów przed awarią.

- **`c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartością domyślną jest `Debug`, ale konfiguracja projektu może zastąpić to domyślne ustawienie sdk.

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Włącza moduł zbierający dane dla przebiegu testowego. Aby uzyskać więcej informacji, zobacz [Monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Włącza tryb diagnostyczny dla platformy testowej i zapisu komunikatów diagnostycznych do określonego pliku.

- **`f|--framework <FRAMEWORK>`**

  Wyszna testowe pliki binarne dla określonej [struktury](../../standard/frameworks.md).

- **`--filter <EXPRESSION>`**

  Odfiltrowuje testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz sekcję [Szczegóły opcji filtrowania.](#filter-option-details) Aby uzyskać więcej informacji i przykłady dotyczące używania selektywnego filtrowania testu jednostkowego, zobacz [Uruchamianie testów jednostkowych selektywnych](../testing/selective-unit-tests.md).

- **`h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zatrzymanie polecenia i oczekiwanie na wejście użytkownika lub akcję. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od sdk .NET Core 3.0.

- **`l|--logger <LoggerUri/FriendlyName>`**

  Określa rejestrator dla wyników testów.

- **`--no-build`**

  Nie tworzy projekt testowy przed uruchomieniem go. To również niejawnie `--no-restore` ustawia - flaga.

- **`--nologo`**

  Uruchom testy bez wyświetlania banera Microsoft TestPlatform. Dostępne od sdk .NET Core 3.0.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas uruchamiania polecenia.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w którym można znaleźć pliki binarne do uruchomienia.

- **`-r|--results-directory <PATH>`**

  Katalog, w którym zostaną umieszczone wyniki testów. Jeśli określony katalog nie istnieje, jest tworzony.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Docelowy czas uruchomieniowy do testowania.

- **`-s|--settings <SETTINGS_FILE>`**

  Plik `.runsettings` do użycia do uruchamiania testów. [Konfigurowanie testów `.runsettings` jednostkowych przy użyciu pliku.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  Lista wszystkich odnalezionych testów w bieżącym projekcie.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .

- `RunSettings`Argumenty

  Argumenty są `RunSettings` przekazywane jako konfiguracje dla testu. Argumenty są `[name]=[value]` określane jako pary po "-- " (zwróć uwagę na spacja po --). Spacja służy do `[name]=[value]` oddzielania wielu par.

  Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Aby uzyskać więcej informacji, zobacz [vstest.console.exe: Przekazywanie RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Przykłady

- Uruchom testy w projekcie w bieżącym katalogu:

  ```dotnetcli
  dotnet test
  ```

- Uruchom testy w `test1` projekcie:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testów w formacie trx:

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a>Szczegóły opcji filtrowania

`--filter <EXPRESSION>`

`<Expression>`ma format `<property><operator><value>[|&<Expression>]`.

`<property>`jest atrybutem `Test Case`pliku . Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:

| Struktura testów | Obsługiwane właściwości                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>Nazwa w pełni kwalifikowana</li><li>Nazwa</li><li>ClassName</li><li>Priorytet</li><li>Kategoria testowa</li></ul> |
| Xunit          | <ul><li>Nazwa w pełni kwalifikowana</li><li>DisplayName</li><li>Cechy</li></ul>                                   |

Opisuje `<operator>` relację między właściwością a wartością:

| Operator | Funkcja        |
| :------: | --------------- |
| `=`      | Pełna zgodność     |
| `!=`     | Nie dokładne dopasowanie |
| `~`      | Contains        |
| `!~`     | Nie zawiera    |

`<value>`jest ciągiem znaków. Wszystkie wyszukiwania są bez uwzględniania wielkości liter.

Wyrażenie bez `<operator>` jest automatycznie traktowane `contains` jako `FullyQualifiedName` na właściwość `dotnet test --filter xyz` (na `dotnet test --filter FullyQualifiedName~xyz`przykład jest taka sama jak ).

Wyrażenia można łączyć z operatorami warunkowymi:

| Operator            | Funkcja |
| ------------------- | -------- |
| <code>&#124;</code> | LUB       |
| `&`                 | AND      |

Wyrażenia można ująć w nawias y podczas korzystania z `(Name~TestMethod1) | (Name~TestMethod2)`operatorów warunkowych (na przykład).

Aby uzyskać więcej informacji i przykłady dotyczące używania selektywnego filtrowania testu jednostkowego, zobacz [Uruchamianie testów jednostkowych selektywnych](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Zobacz też

- [Ramy i cele](../../standard/frameworks.md)
- [Wykaz identyfikatora środowiska uruchomienionowego programu .NET Core (RID)](../rid-catalog.md)
