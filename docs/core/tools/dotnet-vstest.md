---
title: dotnet VSTest — polecenie
description: Polecenie dotnet VSTest kompiluje projekt i wszystkie jego zależności.
ms.date: 05/30/2018
ms.openlocfilehash: fc0aa4f9abf069f78e27692ee84aea2559109c98
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626024"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet-vstest` — uruchamia testy z określonych plików.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a>Opis

Polecenie `dotnet-vstest` uruchamia `VSTest.Console` aplikację wiersza polecenia w celu uruchomienia zautomatyzowanych testów jednostkowych.

## <a name="arguments"></a>Argumenty

- **`TEST_FILE_NAMES`**

  Uruchom testy z określonych zestawów. Oddziel wiele nazw zestawów testowych spacjami. Symbole wieloznaczne są obsługiwane.

## <a name="options"></a>Opcje

- **`--Settings <Settings File>`**

  Ustawienia do użycia podczas przeprowadzania testów.

- **`--Tests <Test Names>`**

  Uruchom testy z nazwami, które pasują do podanych wartości. Rozdziel wiele wartości przecinkami.

- **`--TestAdapterPath`**

  Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.

- **`--Platform <Platform type>`**

  Architektura platformy docelowej używana do wykonywania testów. Prawidłowe wartości to `x86`, `x64`i `ARM`.

- **`--Framework <Framework Version>`**

  Docelowa wersja .NET Framework używana do wykonania testu. Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework40`, `Framework45`, `FrameworkCore10`i `FrameworkUap10`.

- **`--Parallel`**

  Uruchom testy równolegle. Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia. Określ jawną liczbę rdzeni przez ustawienie właściwości `MaxCpuCount` w węźle `RunConfiguration` w pliku *runsettings* .

- **`--TestCaseFilter <Expression>`**

  Uruchom testy zgodne z podanym wyrażeniem. `<Expression>` ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`. `~` operatora ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`. `()` nawiasów są używane do grupowania podwyrażeń.

- **`-?|--Help`**

  Drukuje krótką pomoc dla polecenia.

- **`--logger <Logger Uri/FriendlyName>`**

  Określ Rejestrator dla wyników testu.

  - Aby opublikować wyniki testów w Team Foundation Server, użyj dostawcy rejestratora `TfsPublisher`:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Aby zarejestrować wyniki do pliku Wyniki testów programu Visual Studio (TRX), użyj dostawcy rejestratora `trx`. Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika. Jeśli nie podano `LogFileName`, zostanie utworzona unikatowa nazwa pliku do przechowywania wyników testu.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  Wyświetla wszystkie odnalezione testy z danego kontenera testowego.

- **`--ParentProcessId <ParentProcessId>`**

  Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.

- **`--Port <Port>`**

  Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.

- **`--Diag <Path to log file>`**

  Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane do podanego pliku.

- **`--Blame`**

  Uruchamia testy w trybie polecenia Blame. Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.

- **`--InIsolation`**

  Uruchamia testy w procesie izolowanym. Powoduje to, że proces *VSTest. Console. exe* jest mniej prawdopodobnie zatrzymany w przypadku błędu w testach, ale testy mogą działać wolniej.

- **`@<file>`**

  Odczytuje plik odpowiedzi w celu uzyskania dodatkowych opcji.

- **`args`**

  Określa dodatkowe argumenty do przekazania do adaptera. Argumenty są określane jako pary nazwa-wartość w formularzu `<n>=<v>`, gdzie `<n>` jest nazwą argumentu, a `<v>` to wartość argumentu. Użyj spacji, aby rozdzielić wiele argumentów.

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

Uruchom testy `TestMethod1`:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

Uruchom testy `TestMethod1` i `TestMethod2`:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
