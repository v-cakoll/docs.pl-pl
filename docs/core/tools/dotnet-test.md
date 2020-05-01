---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624894"
---
# <a name="dotnet-test"></a>dotnet test

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet test`— Sterownik testowy .NET używany do wykonywania testów jednostkowych.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a>Opis

`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie. `dotnet test` Polecenie uruchamia aplikację konsolową Test Runner określoną dla projektu. Moduł uruchamiający testy wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raportuje sukces lub niepowodzenie każdego testu. Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1. W przypadku projektów wielowymiarowych testy są uruchamiane dla każdej platformy dostosowanej. Moduł uruchamiający testy i Biblioteka testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.

Projekty testowe określają Test Runner przy użyciu zwykłego `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a>Przywracanie niejawne

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumenty

- **`PROJECT | SOLUTION`**

  Ścieżka do projektu testowego lub rozwiązania. Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.

## <a name="options"></a>Opcje

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.

- **`--blame`**

  Uruchamia testy w trybie polecenia Blame. Ta opcja jest przydatna do izolowania problematycznych testów, które powodują awarię hosta testowego. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Włącza moduł zbierający dane dla przebiegu testu. Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.

- **`-f|--framework <FRAMEWORK>`**

  Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).

- **`--filter <EXPRESSION>`**

  Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) . Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. Dostępne od wersji .NET Core 3,0 SDK.

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Określa Rejestrator dla wyników testu. W przeciwieństwie do programu MSBuild, test dotnet nie akceptuje skrótów: `-l "console;v=d"` zamiast `-l "console;verbosity=detailed"`używać.

- **`--no-build`**

  Nie kompiluje projektu testowego przed jego uruchomieniem. Również niejawnie ustawia `--no-restore` flagę.

- **`--nologo`**

  Uruchom testy bez wyświetlania transparentu Microsoft TestPlatform. Dostępne od wersji .NET Core 3,0 SDK.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w którym można znaleźć pliki binarne do uruchomienia. Jeśli nie zostanie określony, ścieżka domyślna to `./bin/<configuration>/<framework>/`.  W przypadku projektów z wieloma platformami docelowymi ( `TargetFrameworks` za pośrednictwem właściwości) należy również zdefiniować `--framework` , kiedy należy określić tę opcję. `dotnet test`Zawsze uruchamiaj testy z katalogu wyjściowego. Można użyć <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> do korzystania z zasobów testowych w katalogu wyjściowym.

- **`-r|--results-directory <PATH>`**

  Katalog, w którym zostaną umieszczone wyniki testu. Jeśli określony katalog nie istnieje, zostanie utworzony. Wartość domyślna znajduje `TestResults` się w katalogu, który zawiera plik projektu.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Docelowy środowisko uruchomieniowe do przetestowania.

- **`-s|--settings <SETTINGS_FILE>`**

  Plik `.runsettings` , który ma być używany do uruchamiania testów. Należy zauważyć, `TargetPlatform` że element (x86 | x64) nie ma wpływu `dotnet test`na. Aby uruchomić testy, które są przeznaczone dla architektury x86, Zainstaluj wersję x86 programu .NET Core. Liczba bitów programu *dotnet. exe* , która znajduje się na ścieżce, będzie używana do uruchamiania testów. Aby uzyskać więcej informacji, zobacz następujące zasoby:

  - [Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [Konfigurowanie przebiegu testowego](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `minimal`. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- **`RunSettings`** argumentu

  Argumenty są przekazane jako `RunSettings` konfiguracje dla testu. Argumenty są określane jako `[name]=[value]` pary po "--" (należy zwrócić uwagę na spację po--). Spacja jest używana do rozdzielania wielu `[name]=[value]` par.

  Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów runsettings przy użyciu wiersza polecenia](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Przykłady

- Uruchom testy w projekcie w bieżącym katalogu:

  ```dotnetcli
  dotnet test
  ```

- Uruchom testy w `test1` projekcie:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie TRX:

  ```dotnetcli
  dotnet test --logger trx
  ```

- Uruchom testy w projekcie w bieżącym katalogu i zaloguj się ze szczegółowymi informacjami o konsoli programu:

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a>Szczegóły opcji filtrowania

`--filter <EXPRESSION>`

`<Expression>`ma format `<property><operator><value>[|&<Expression>]`.

`<property>`jest atrybutem klasy `Test Case`. Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:

| Platforma testowa | Obsługiwane właściwości                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Nazwa</li><li>ClassName</li><li>Priorytet</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>Nazwa wyświetlana</li><li>Cech</li></ul>                                   |

`<operator>` Opisuje relację między właściwością a wartością:

| Operator | Funkcja        |
| :------: | --------------- |
| `=`      | Pełna zgodność     |
| `!=`     | Niedokładne dopasowanie |
| `~`      | Contains        |
| `!~`     | Nie zawiera    |

`<value>`jest ciągiem. Wszystkie wyszukiwania są rozróżniane wielkości liter.

Wyrażenie bez `<operator>` elementu jest automatycznie uznawane za Właściwość `contains` on `FullyQualifiedName` (na przykład `dotnet test --filter xyz` jest takie samo jak `dotnet test --filter FullyQualifiedName~xyz`).

Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:

| Operator            | Funkcja |
| ------------------- | -------- |
| <code>&#124;</code> | LUB       |
| `&`                 | AND      |

Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).

Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Zobacz także

- [Struktury i elementy docelowe](../../standard/frameworks.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)](../rid-catalog.md)
- [Przekazywanie argumentów runsettings za poorednictwem wiersza polecenia](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
