---
title: dotnet VSTest — polecenie
description: Polecenie dotnet VSTest kompiluje projekt i wszystkie jego zależności.
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975397"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

> [!IMPORTANT]
> `dotnet vstest` Polecenie jest zastępowane przez `dotnet test`, co może być teraz używane do uruchamiania zestawów. Zobacz [`dotnet test`](dotnet-test.md).

## <a name="name"></a>Nazwa

`dotnet-vstest`-Uruchamia testy z określonych zestawów.

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

`dotnet-vstest` Polecenie uruchamia aplikację wiersza `VSTest.Console` polecenia w celu uruchomienia zautomatyzowanych testów jednostkowych.

## <a name="arguments"></a>Argumenty

- **`TEST_FILE_NAMES`**

  Uruchom testy z określonych zestawów. Oddziel wiele nazw zestawów testowych spacjami. Symbole wieloznaczne są obsługiwane.

## <a name="options"></a>Opcje

- **`--Blame`**

  Uruchamia testy w trybie polecenia Blame. Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.

- **`--Diag <PATH_TO_LOG_FILE>`**

  Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane do podanego pliku.

- **`--Framework <FRAMEWORK>`**

  Docelowa wersja .NET Framework używana do wykonania testu. Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework40`, `Framework45`, `FrameworkCore10`, i `FrameworkUap10`.

- **`--InIsolation`**

  Uruchamia testy w procesie izolowanym. Powoduje to, że proces *VSTest. Console. exe* jest mniej prawdopodobnie zatrzymany w przypadku błędu w testach, ale testy mogą działać wolniej.

- **`-lt|--ListTests <FILE_NAME>`**

  Wyświetla wszystkie odnalezione testy z danego kontenera testowego.

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Określ Rejestrator dla wyników testu.

  - Aby opublikować wyniki testów w Team Foundation Server, użyj dostawcy `TfsPublisher` rejestratora:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Aby zarejestrować wyniki do pliku Wyniki testów programu Visual Studio (TRX), użyj dostawcy `trx` rejestratora. Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika. Jeśli `LogFileName` nie zostanie podany, unikatowa nazwa pliku zostanie utworzona w celu przechowywania wyników testu.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  Uruchom testy równolegle. Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia. Określ jawną liczbę rdzeni przez ustawienie `MaxCpuCount` właściwości w `RunConfiguration` węźle w pliku *runsettings* .

- **`--ParentProcessId <PROCESS_ID>`**

  Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.

- **`--Platform <PLATFORM_TYPE>`**

  Architektura platformy docelowej używana do wykonywania testów. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

- **`--Port <PORT>`**

  Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.

- **`--ResultsDirectory:<PATH>`**

  Katalog wyników testu zostanie utworzony w określonej ścieżce, jeśli nie istnieje.

- **`--Settings <SETTINGS_FILE>`**

  Ustawienia do użycia podczas przeprowadzania testów.

- **`--TestAdapterPath <PATH>`**

  Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.

- **`--TestCaseFilter <EXPRESSION>`**

  Uruchom testy zgodne z podanym wyrażeniem. `<EXPRESSION>`ma format `<property>Operator<value>[|&<EXPRESSION>]`, gdzie operator jest jednym z `=`, `!=`lub. `~` Operator `~` ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, `DisplayName`takich jak. `()` Nawiasy służą do grupowania podwyrażeń. Aby uzyskać więcej informacji, zobacz [przypadku testowego Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

- **`--Tests <TEST_NAMES>`**

  Uruchom testy z nazwami, które pasują do podanych wartości. Użyj przecinków, aby oddzielić wiele wartości.

- **`-?|--Help`**

  Drukuje krótką pomoc dla polecenia.

- **`@<file>`**

  Odczytuje plik odpowiedzi w celu uzyskania dodatkowych opcji.

- **`args`**

  Określa dodatkowe argumenty do przekazania do adaptera. Argumenty są określane jako pary nazwa-wartość formularza `<n>=<v>`, gdzie `<n>` jest nazwą argumentu i `<v>` jest wartością argumentu. Użyj spacji, aby rozdzielić wiele argumentów.

## <a name="examples"></a>Przykłady

Uruchom testy w *mytestproject. dll*:

```dotnetcli
dotnet vstest mytestproject.dll
```

Uruchom testy w *mytestproject. dll*, eksportując do folderu niestandardowego z nazwą niestandardową:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

Uruchom testy w *mytestproject. dll* i *myothertestproject. exe*:

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

Uruchom `TestMethod1` testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

Uruchom `TestMethod1` i `TestMethod2` testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a>Zobacz też

- [Opcje wiersza poleceń narzędzia VSTest.Console.exe](/visualstudio/test/vstest-console-options)
