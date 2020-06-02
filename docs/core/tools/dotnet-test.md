---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 04/29/2020
ms.openlocfilehash: 1190ecb75e83c9930c60726e7cd83203b11928cb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283939"
---
# <a name="dotnet-test"></a>dotnet test

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet test`— Sterownik testowy .NET używany do wykonywania testów jednostkowych.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
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

`dotnet test`Polecenie służy do wykonywania testów jednostkowych w danym rozwiązaniu. `dotnet test`Polecenie kompiluje rozwiązanie i uruchamia test aplikacji hosta dla każdego projektu testowego w rozwiązaniu. Host testowy wykonuje testy w danym projekcie przy użyciu struktury testowej, na przykład: MSTest, NUnit lub xUnit, i raportuje sukces lub niepowodzenie każdego testu. Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1.

W przypadku projektów wielowymiarowych testy są uruchamiane dla każdej platformy dostosowanej. Hosta testowego i struktury testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.

Projekty testowe określają Test Runner przy użyciu zwykłego `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

Gdzie `Microsoft.NET.Test.Sdk` jest hostem testowym, `xunit` jest to Platforma testowa. I `xunit.runner.visualstudio` jest adapterem testowym, który pozwala platformie xUnit na współdziałanie z hostem testowym.

### <a name="implicit-restore"></a>Przywracanie niejawne

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumenty

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - Ścieżka do projektu testowego.
  - Ścieżka do rozwiązania.
  - Ścieżka do katalogu, który zawiera projekt lub rozwiązanie.
  - Ścieżka do pliku projektu testowego. *dll* .

  Jeśli nie zostanie określony, wyszukuje projekt lub rozwiązanie w bieżącym katalogu.

## <a name="options"></a>Opcje

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Ścieżka do katalogu, który ma być przeszukiwany dla dodatkowych adapterów testowych. Sprawdzane są tylko pliki *. dll* z sufiksem `.TestAdapter.dll` . Jeśli nie zostanie określony, zostanie przeszukany katalog test *. dll* .

- **`--blame`**

  Uruchamia testy w trybie polecenia Blame. Ta opcja jest przydatna do izolowania problematycznych testów, które powodują awarię hosta testowego. Gdy zostanie wykryta awaria, tworzy plik sekwencji w programie `TestResults/<Guid>/<Guid>_Sequence.xml` , który przechwytuje kolejność testów, które zostały uruchomione przed awarią.

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug` , ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Włącza moduł zbierający dane dla przebiegu testu. Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).
  
  Aby zbierać pokrycie kodu na dowolnej platformie obsługiwanej przez platformę .NET Core, zainstaluj [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) i Użyj `--collect:"XPlat Code Coverage"` opcji.

  W systemie Windows można zbierać pokrycie kodu przy użyciu `--collect "Code Coverage"` opcji. Ta opcja generuje plik *. coverage* , który można otworzyć w programie Visual Studio 2019 Enterprise. Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) i [Dostosowywanie analizy pokrycia kodu](/visualstudio/test/customizing-code-coverage-analysis).

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku oraz do plików obok niego. Proces rejestrowania komunikatów określa, które pliki są tworzone, takie jak `*.host_<date>.txt` Dziennik hosta testowego i `*.datacollector_<date>.txt` Dziennik modułu zbierającego dane.

- **`-f|--framework <FRAMEWORK>`**

  Wymusza użycie `dotnet` lub .NET Framework hosta testowego dla plików binarnych testu. Ta opcja określa tylko typ hosta, który ma być używany. Rzeczywista wersja platformy, która ma zostać użyta, jest określana przez *runtimeconfig. JSON* projektu testowego. Gdy nie zostanie określony, [atrybut zestawu TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) jest używany do określenia typu hosta. Gdy ten atrybut jest usuwany z *biblioteki DLL*, używany jest host .NET Framework.

- **`--filter <EXPRESSION>`**

  Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) . Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. Dostępne od wersji .NET Core 3,0 SDK.

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Określa Rejestrator dla wyników testu. W przeciwieństwie do programu MSBuild, test dotnet nie akceptuje skrótów: zamiast `-l "console;v=d"` używać `-l "console;verbosity=detailed"` .

- **`--no-build`**

  Nie kompiluje projektu testowego przed jego uruchomieniem. Również niejawnie ustawia `--no-restore` flagę.

- **`--nologo`**

  Uruchom testy bez wyświetlania transparentu Microsoft TestPlatform. Dostępne od wersji .NET Core 3,0 SDK.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w którym można znaleźć pliki binarne do uruchomienia. Jeśli nie zostanie określony, ścieżka domyślna to `./bin/<configuration>/<framework>/` .  W przypadku projektów z wieloma platformami docelowymi (za pośrednictwem `TargetFrameworks` Właściwości) należy również zdefiniować, `--framework` kiedy należy określić tę opcję. `dotnet test`zawsze uruchamia testy z katalogu wyjściowego. Można użyć <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> do korzystania z zasobów testowych w katalogu wyjściowym.

- **`-r|--results-directory <PATH>`**

  Katalog, w którym zostaną umieszczone wyniki testu. Jeśli określony katalog nie istnieje, zostanie utworzony. Wartość domyślna znajduje się `TestResults` w katalogu, który zawiera plik projektu.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Docelowy środowisko uruchomieniowe do przetestowania.

- **`-s|--settings <SETTINGS_FILE>`**

  `.runsettings`Plik, który ma być używany do uruchamiania testów. `TargetPlatform`Element (x86 | x64) nie ma wpływu na `dotnet test` . Aby uruchomić testy, które są przeznaczone dla architektury x86, Zainstaluj wersję x86 programu .NET Core. Liczba bitów programu *dotnet. exe* , która znajduje się na ścieżce, będzie używana do uruchamiania testów. Więcej informacji zawierają następujące zasoby:

  - [Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [Konfigurowanie przebiegu testowego](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` . Wartość domyślna to `minimal`. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- **`RunSettings`** argumentu

 Wbudowane `RunSettings` są przekazane jako ostatni argument w wierszu polecenia po "--" (należy pamiętać, że spacja jest późniejsza niż--). Wbudowane `RunSettings` są określone jako `[name]=[value]` pary. Spacja jest używana do rozdzielania wielu `[name]=[value]` par.

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

- Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik pokrycia kodu (po zainstalowaniu [Coverlet](https://github.com/tonerdo/coverlet/blob/master/README.md)):

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik pokrycia kodu (tylko system Windows):

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- Uruchom testy w projekcie w bieżącym katalogu i zaloguj się ze szczegółowymi informacjami o konsoli programu:

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - Uruchom testy w projekcie w bieżącym katalogu i Raportuj testy, które były w toku w przypadku awarii hosta testowego:

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a>Szczegóły opcji filtrowania

`--filter <EXPRESSION>`

`<Expression>`ma format `<property><operator><value>[|&<Expression>]` .

`<property>`jest atrybutem klasy `Test Case` . Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:

| Platforma testowa | Obsługiwane właściwości                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Nazwa</li><li>ClassName</li><li>Priorytet</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>Nazwa wyświetlana</li><li>Cech</li></ul>                                   |
| NUnit          | <ul><li>FullyQualifiedName</li><li>Nazwa</li><li>TestCategory</li><li>Priorytet</li></ul>                                   |

`<operator>`Opisuje relację między właściwością a wartością:

| Operator | Funkcja        |
| :------: | --------------- |
| `=`      | Pełna zgodność     |
| `!=`     | Niedokładne dopasowanie |
| `~`      | Contains        |
| `!~`     | Nie zawiera    |

`<value>`jest ciągiem. Wszystkie wyszukiwania są rozróżniane wielkości liter.

Wyrażenie bez elementu `<operator>` jest automatycznie uznawane za `contains` Właściwość on `FullyQualifiedName` (na przykład `dotnet test --filter xyz` jest takie samo jak `dotnet test --filter FullyQualifiedName~xyz` ).

Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:

| Operator            | Funkcja |
| ------------------- | -------- |
| <code>&#124;</code> | OR       |
| `&`                 | AND      |

Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)` ).

Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Zobacz także

- [Struktury i elementy docelowe](../../standard/frameworks.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)](../rid-catalog.md)
- [Przekazywanie argumentów runsettings za poorednictwem wiersza polecenia](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
