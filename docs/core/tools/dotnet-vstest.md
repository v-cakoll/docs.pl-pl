---
title: polecenie dotnet vstest
description: Polecenie dotnet vstest tworzy projekt i wszystkie jego zależności.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156936"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet-vstest`- Uruchamia testy z określonych plików.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a>Opis

Polecenie `dotnet-vstest` uruchamia `VSTest.Console` aplikację wiersza polecenia w celu uruchomienia automatycznych testów jednostkowych.

## <a name="arguments"></a>Argumenty

- **`TEST_FILE_NAMES`**

  Uruchom testy z określonych zestawów. Oddziel wiele nazw zespołów testowych sposobnikami. Symbole wieloznaczne są obsługiwane.

## <a name="options"></a>Opcje

- **`--Settings <Settings File>`**

  Ustawienia używane podczas uruchamiania testów.

- **`--Tests <Test Names>`**

  Uruchom testy z nazwami, które pasują do podanych wartości. Oddziel wiele wartości przecinkami.

- **`--TestAdapterPath`**

  Użyj niestandardowych kart testowych z danej ścieżki (jeśli istnieje) w przebiegu testowym.

- **`--Platform <Platform type>`**

  Architektura platformy docelowej używana do wykonywania testów. Prawidłowe wartości `x86` `x64`to `ARM`, i .

- **`--Framework <Framework Version>`**

  Wersja docelowa .NET Framework używana do wykonywania testów. Przykładami prawidłowych `.NETFramework,Version=v4.6` wartości `.NETCoreApp,Version=v1.0`są lub . Inne obsługiwane wartości `Framework40` `Framework45`to `FrameworkCore10`, `FrameworkUap10`, i .

- **`--Parallel`**

  Uruchamiaj testy równolegle. Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użytku. Określ jawną liczbę rdzeni, `MaxCpuCount` ustawiając `RunConfiguration` właściwość pod węzłem w pliku *runsettings.*

- **`--TestCaseFilter <Expression>`**

  Uruchom testy, które pasują do danego wyrażenia. `<Expression>`jest w `<property>Operator<value>[|&<Expression>]`formacie, gdzie Operator `=` `!=`jest `~`jednym z , lub . Operator `~` ma semantyki "zawiera" i ma `DisplayName`zastosowanie do właściwości ciągu, takich jak . Nawiasy `()` są używane do grupowania podwyrażeń.

- **`-?|--Help`**

  Drukuje krótką pomoc dla polecenia.

- **`--logger <Logger Uri/FriendlyName>`**

  Określ rejestrator dla wyników testów.

  - Aby opublikować wyniki testów na `TfsPublisher` serwerze Team Foundation Server, należy użyć dostawcy rejestratora:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Aby zalogować wyniki do pliku wyników testów `trx` programu Visual Studio (TRX), należy użyć dostawcy rejestratora. Ten przełącznik tworzy plik w katalogu wyników testów z podaną nazwą pliku dziennika. Jeśli `LogFileName` nie jest podana, unikatowa nazwa pliku jest tworzona do przechowywania wyników testu.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  Wyświetla listę wszystkich odnalezionych testów z danego kontenera testowego.

- **`--ParentProcessId <ParentProcessId>`**

  Identyfikator procesu nadrzędnego odpowiedzialnego za uruchomienie bieżącego procesu.

- **`--Port <Port>`**

  Określa port dla połączenia gniazda i odbierania komunikatów o zdarzeniu.

- **`--Diag <Path to log file>`**

  Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane w podanych plikach.

- **`--Blame`**

  Uruchamia testy w trybie winy. Ta opcja jest pomocna w izolowaniu problematycznych testów powodujących awarię hosta testowego. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml,* który przechwytuje kolejność wykonywania testów przed awarią.

- **`--InIsolation`**

  Uruchamia testy w izolowanym procesie. To sprawia, że *vstest.console.exe* proces mniej prawdopodobne, aby być zatrzymane na błąd w testach, ale testy mogą działać wolniej.

- **`@<file>`**

  Odczytuje plik odpowiedzi, aby uzyskać więcej opcji.

- **`args`**

  Określa dodatkowe argumenty, które mają zostać przekazane do karty. Argumenty są określane jako pary name-value `<n>=<v>` `<n>` formularza , gdzie `<v>` jest nazwa argumentu i jest wartością argumentu. Spatonie służy do oddzielania wielu argumentów.

## <a name="examples"></a>Przykłady

Uruchom testy w *mytestproject.dll*:

```dotnetcli
dotnet vstest mytestproject.dll
```

Uruchom testy w *mytestproject.dll*, eksportowanie do folderu niestandardowego o nazwie niestandardowej:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

Uruchom testy w *mytestproject.dll* i *myothertestproject.exe:*

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

Uruchom `TestMethod1` testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

Uruchom `TestMethod1` `TestMethod2` i testy:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
