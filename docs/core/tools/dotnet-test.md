---
title: polecenie testu dotnet
description: Polecenie testu dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 02/27/2020
ms.openlocfilehash: a11814f9fdc6326e681a09d7d2654b968014f318
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507311"
---
# <a name="dotnet-test"></a>dotnet test

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

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

Polecenie `dotnet test` jest używane do wykonywania testów jednostkowych w danym projekcie. Polecenie `dotnet test` uruchamia aplikację konsoli testowej aplikacji dla programu runner określoną dla projektu. Test runner wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raportuje sukces lub niepowodzenie każdego testu. Jeśli wszystkie testy zakończą się pomyślnie, test runner zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca wartość 1. Program testowy i biblioteka testów jednostkowych są pakowane jako pakiety NuGet i są przywracane jako zwykłe zależności dla projektu.

Projekty testowe określają wynik `<PackageReference>` testu przy użyciu zwykłego elementu, jak widać w poniższym przykładowym pliku projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Argumenty

- **`PROJECT | SOLUTION`**

  Ścieżka do projektu testowego lub rozwiązania. Jeśli nie zostanie określony, domyślnie jest to bieżący katalog.

## <a name="options"></a>Opcje

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Użyj niestandardowych kart testowych z określonej ścieżki w przebiegu testu.

- **`--blame`**

  Uruchamia testy w trybie winy. Ta opcja jest przydatna w izolowaniu problematycznych testów, które powodują awarię hosta testowego. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml,* który przechwytuje kolejność wykonywania testów przed awarią.

- **`c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartością domyślną jest `Debug`, ale konfiguracja projektu może zastąpić to domyślne ustawienie SDK.

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Włącza moduł zbierający dane dla przebiegu testowego. Aby uzyskać więcej informacji, zobacz [Monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Włącza tryb diagnostyczny dla platformy testowej i zapisu komunikatów diagnostycznych do określonego pliku.

- **`f|--framework <FRAMEWORK>`**

  Wyszukuje pliki binarne testów dla określonej [struktury](../../standard/frameworks.md).

- **`--filter <EXPRESSION>`**

  Odfiltrowywają testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz sekcję [Szczegóły opcji filtru.](#filter-option-details) Aby uzyskać więcej informacji i przykładów dotyczących używania selektywnego filtrowania jednostek, zobacz [Uruchamianie testów jednostkowych selektywnych](../testing/selective-unit-tests.md).

- **`h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od .NET Core 3.0 SDK.

- **`l|--logger <LoggerUri/FriendlyName>`**

  Określa rejestrator dla wyników testów.

- **`--no-build`**

  Nie tworzy projektu testowego przed jego uruchomieniem. Również niejawnie ustawia `--no-restore` - flaga.

- **`--nologo`**

  Uruchom testy bez wyświetlania banera Microsoft TestPlatform. Dostępne od .NET Core 3.0 SDK.

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas uruchamiania polecenia.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w którym można znaleźć pliki binarne do uruchomienia.

- **`-r|--results-directory <PATH>`**

  Katalog, w którym zostaną umieszczone wyniki testów. Jeśli określony katalog nie istnieje, jest tworzony.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Docelowy czas wykonywania do przetestowania.

- **`-s|--settings <SETTINGS_FILE>`**

  Plik `.runsettings` do użycia do uruchamiania testów. [Konfigurowanie testów jednostkowych `.runsettings` przy użyciu pliku.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .

- `RunSettings`Argumenty

  Argumenty są `RunSettings` przekazywane jako konfiguracje dla testu. Argumenty są `[name]=[value]` określane jako pary po "-- " (zwróć uwagę na spację po --). Spacja służy do `[name]=[value]` oddzielania wielu par.

  Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Aby uzyskać więcej informacji, zobacz [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Przykłady

- Uruchom testy w projekcie w bieżącym katalogu:

  ```dotnetcli
  dotnet test
  ```

- Uruchom testy w `test1` projekcie:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie trx:

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a>Szczegóły opcji filtrowania

`--filter <EXPRESSION>`

`<Expression>`ma format `<property><operator><value>[|&<Expression>]`.

`<property>`jest atrybutem `Test Case`. Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:

| Struktura testów | Obsługiwane właściwości                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>Pełna w pełni zakwalifikowanananana nazwa</li><li>Nazwa</li><li>ClassName</li><li>Priorytet</li><li>Kategoria testowa</li></ul> |
| Xunit          | <ul><li>Pełna w pełni zakwalifikowanananana nazwa</li><li>DisplayName</li><li>Cechy</li></ul>                                   |

Opisuje `<operator>` relację między właściwością a wartością:

| Operator | Funkcja        |
| :------: | --------------- |
| `=`      | Pełna zgodność     |
| `!=`     | Nie dokładne dopasowanie |
| `~`      | Contains        |
| `!~`     | Nie zawiera    |

`<value>`jest ciągiem. Wszystkie wyszukiwania są niewrażliwe na wielkości liter.

Wyrażenie bez `<operator>` jest automatycznie traktowane `contains` jako `FullyQualifiedName` właściwość na `dotnet test --filter xyz` (na `dotnet test --filter FullyQualifiedName~xyz`przykład jest taka sama jak ).

Wyrażenia można łączyć z operatorami warunkowymi:

| Operator            | Funkcja |
| ------------------- | -------- |
| <code>&#124;</code> | LUB       |
| `&`                 | AND      |

Wyrażenia można ująć w nawiasy podczas korzystania z `(Name~TestMethod1) | (Name~TestMethod2)`operatorów warunkowych (na przykład ).

Aby uzyskać więcej informacji i przykładów dotyczących używania selektywnego filtrowania jednostek, zobacz [Uruchamianie testów jednostkowych selektywnych](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Zobacz też

- [Ramy i cele](../../standard/frameworks.md)
- [Katalog identyfikatora IDentifier (RID) programu .NET Core](../rid-catalog.md)
