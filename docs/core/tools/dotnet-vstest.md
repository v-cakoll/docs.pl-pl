---
title: dotnet vstest, polecenie
description: Polecenie dotnet vstest tworzy projekt i wszystkie jego zależności.
ms.date: 02/27/2020
ms.openlocfilehash: e8fa94cf12ca2fe5fb99c6e3c1dcdb52185798c0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463283"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet-vstest`- Uruchamia testy z określonych plików.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a>Opis

Polecenie `dotnet-vstest` uruchamia `VSTest.Console` aplikację wiersza polecenia w celu uruchomienia automatycznych testów jednostkowych.

## <a name="arguments"></a>Argumenty

- **`TEST_FILE_NAMES`**

  Uruchom testy z określonych zestawów. Oddziel wiele nazw zestawów testowych spacjami. Obsługiwane są symbole wieloznaczne.

## <a name="options"></a>Opcje

- **`--Blame`**

  Uruchamia testy w trybie winy. Ta opcja jest przydatna w izolowaniu problematycznych testów powodujących awarię hosta testowego. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml,* który przechwytuje kolejność wykonywania testów przed awarią.

- **`--Diag <PATH_TO_LOG_FILE>`**

  Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane w podanym pliku.

- **`--Framework <FRAMEWORK>`**

  Docelowa wersja programu .NET Framework używana do wykonywania testów. Przykładami prawidłowych `.NETFramework,Version=v4.6` wartości `.NETCoreApp,Version=v1.0`są lub . Inne obsługiwane wartości `Framework40` `Framework45`to `FrameworkCore10`, `FrameworkUap10`, i .

- **`--InIsolation`**

  Uruchamia testy w procesie izolowanym. To sprawia, że proces *vstest.console.exe* jest mniej prawdopodobne, aby zatrzymać się na błąd w testach, ale testy mogą działać wolniej.

- **`-lt|--ListTests <FILE_NAME>`**

  Wyświetla listę wszystkich wykrytych testów z danego kontenera testowego.

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Określ rejestrator dla wyników testów.

  - Aby opublikować wyniki testów na `TfsPublisher` serwerze Team Foundation Server, użyj dostawcy rejestratora:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Aby rejestrować wyniki w pliku wyników testów programu `trx` Visual Studio (TRX), należy użyć dostawcy rejestratora. Ten przełącznik tworzy plik w katalogu wyników testów o podanej nazwie pliku dziennika. Jeśli `LogFileName` nie podano, zostanie utworzona unikatowa nazwa pliku w celu przechowywania wyników testów.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  Uruchom testy równolegle. Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia. Określ jawną liczbę rdzeni, `MaxCpuCount` ustawiając `RunConfiguration` właściwość pod węzłem w pliku *runsettings.*

- **`--ParentProcessId <PROCESS_ID>`**

  Identyfikator procesu nadrzędnego odpowiedzialnego za uruchomienie bieżącego procesu.

- **`--Platform <PLATFORM_TYPE>`**

  Architektura platformy docelowej używana do wykonywania testów. Prawidłowe `x86`wartości `x64`to `ARM`, i .

- **`--Port <PORT>`**

  Określa port połączenia gniazda i odbieranie komunikatów o zdarzeniu.

- **`--ResultsDirectory:<PATH>`**

  Katalog wyników testów zostanie utworzony w określonej ścieżce, jeśli nie istnieje.

- **`--Settings <SETTINGS_FILE>`**

  Ustawienia, które mają być używane podczas uruchamiania testów.

- **`--TestAdapterPath <PATH>`**

  Użyj niestandardowych kart testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.

- **`--TestCaseFilter <EXPRESSION>`**

  Uruchom testy, które pasują do danego wyrażenia. `<EXPRESSION>`ma format, `<property>Operator<value>[|&<EXPRESSION>]`w którym Operator `=` `!=`jest `~`jednym z , lub . Operator `~` ma "zawiera" semantykę i ma `DisplayName`zastosowanie do właściwości ciągu, takich jak . Nawiasy `()` są używane do grupowanie podwyrażenia. Aby uzyskać więcej informacji, zobacz [Filtr Skrzynia testowa](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

- **`--Tests <TEST_NAMES>`**

  Uruchom testy z nazwami, które odpowiadają podanym wartościom. Oddziel wiele wartości przecinkami.

- **`-?|--Help`**

  Drukuje krótką pomoc dla polecenia.

- **`@<file>`**

  Odczytuje plik odpowiedzi, aby uzyskać więcej opcji.

- **`args`**

  Określa dodatkowe argumenty, które mają być przerzucene do karty. Argumenty są określane jako pary nazwa-wartość `<n>=<v>` `<n>` formularza , gdzie `<v>` jest nazwą argumentu i jest wartością argumentu. Użyj spacji, aby oddzielić wiele argumentów.

## <a name="examples"></a>Przykłady

Uruchom testy w *mytestproject.dll*:

```dotnetcli
dotnet vstest mytestproject.dll
```

Uruchom testy w *pliku mytestproject.dll*, eksportując do folderu niestandardowego o niestandardowej nazwie:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

Uruchom testy w *mytestproject.dll* i *myothertestproject.exe*:

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

Uruchom `TestMethod1` testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

`TestMethod1` Uruchamianie `TestMethod2` i testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a>Zobacz też

- [Opcje wiersza poleceń narzędzia VSTest.Console.exe](/visualstudio/test/vstest-console-options)
