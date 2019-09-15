---
title: dotnet VSTest — polecenie
description: Polecenie dotnet VSTest kompiluje projekt i wszystkie jego zależności.
author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: da18fda6419cb9eaa1f488a3576161c3054b4426
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969815"
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet-vstest`-Uruchamia testy z określonych plików.

## <a name="synopsis"></a>Streszczenie

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a>Opis

Polecenie uruchamia aplikację wiersza polecenia w celu uruchomienia zautomatyzowanych testów jednostkowych. `VSTest.Console` `dotnet-vstest`

## <a name="arguments"></a>Argumenty

`TEST_FILE_NAMES`

Uruchom testy z określonych zestawów. Oddziel wiele nazw zestawów testowych spacjami.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Ustawienia do użycia podczas przeprowadzania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy z nazwami, które pasują do podanych wartości. Rozdziel wiele wartości przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.

`--Platform|/Platform:<Platform type>`

Architektura platformy docelowej używana do wykonywania testów. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Docelowa wersja .NET Framework używana do wykonania testu. Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework40` `Framework45` `FrameworkCore10`,,, i. `FrameworkUap10`

`--Parallel|/Parallel`

Wykonaj testy równolegle. Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia. Określ jawną liczbę rdzeni przez ustawienie właściwości MaxCpuCount w węźle RunConfiguration w pliku runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy zgodne z podanym wyrażeniem. `<Expression>`ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`. Operator `~` ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, `DisplayName`takich jak. Nawiasy `()` są używane do grupowania wyrażeń podrzędnych.

`-?|--Help|/?|/Help`

Drukuje krótką pomoc dla polecenia.

`--logger|/logger:<Logger Uri/FriendlyName>`

Określ Rejestrator dla wyników testu.

* Aby opublikować wyniki testów w Team Foundation Server, użyj `TfsPublisher` dostawcy rejestratora:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Aby zarejestrować wyniki do pliku wyniki testów programu Visual Studio (TRX), użyj `trx` dostawcy rejestratora. Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika. Jeśli `LogFileName` nie zostanie podany, unikatowa nazwa pliku zostanie utworzona w celu przechowywania wyników testu.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Wyświetla wszystkie odnalezione testy z danego kontenera testowego.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane do podanego pliku.

`--Blame|/Blame`

Uruchamia testy w trybie polecenia Blame. Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.

`--InIsolation|/InIsolation`

Uruchamia testy w procesie izolowanym. Powoduje to, że proces *VSTest. Console. exe* jest mniej prawdopodobnie zatrzymany w przypadku błędu w testach, ale testy mogą działać wolniej.

`@<file>`

Odczytuje plik odpowiedzi w celu uzyskania dodatkowych opcji.

`args`

Określa dodatkowe argumenty do przekazania do adaptera. Argumenty są określane jako pary nazwa-wartość formularza `<n>=<v>`, gdzie `<n>` jest nazwą argumentu i `<v>` jest wartością argumentu. Użyj spacji, aby rozdzielić wiele argumentów.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Ustawienia do użycia podczas przeprowadzania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy z nazwami, które pasują do podanych wartości. Rozdziel wiele wartości przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.

`--Platform|/Platform:<Platform type>`

Architektura platformy docelowej używana do wykonywania testów. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Docelowa wersja .NET Framework używana do wykonania testu. Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.

`--Parallel|/Parallel`

Wykonaj testy równolegle. Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia. Określ jawną liczbę rdzeni przez ustawienie właściwości MaxCpuCount w węźle RunConfiguration w pliku runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy zgodne z podanym wyrażeniem. `<Expression>`ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`. Operator `~` ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, `DisplayName`takich jak. Nawiasy `()` są używane do grupowania wyrażeń podrzędnych.

`-?|--Help|/?|/Help`

Drukuje krótką pomoc dla polecenia.

`--logger|/logger:<Logger Uri/FriendlyName>`

Określ Rejestrator dla wyników testu.

* Aby opublikować wyniki testów w Team Foundation Server, użyj `TfsPublisher` dostawcy rejestratora:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Aby zarejestrować wyniki do pliku wyniki testów programu Visual Studio (TRX), użyj `trx` dostawcy rejestratora. Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika. Jeśli `LogFileName` nie zostanie podany, unikatowa nazwa pliku zostanie utworzona w celu przechowywania wyników testu.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Wyświetla wszystkie odnalezione testy z danego kontenera testowego.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane do podanego pliku.

`args`

Określa dodatkowe argumenty do przekazania do adaptera. Argumenty są określane jako pary nazwa-wartość formularza `<n>=<v>`, gdzie `<n>` jest nazwą argumentu i `<v>` jest wartością argumentu. Użyj spacji, aby rozdzielić wiele argumentów.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Ustawienia do użycia podczas przeprowadzania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy z nazwami, które pasują do podanych wartości. Rozdziel wiele wartości przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Użyj niestandardowych adapterów testowych z danej ścieżki (jeśli istnieje) w przebiegu testu.

`--Platform|/Platform:<Platform type>`

Architektura platformy docelowej używana do wykonywania testów. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Docelowa wersja .NET Framework używana do wykonania testu. Przykłady prawidłowych wartości to `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.

`--Parallel|/Parallel`

Wykonaj testy równolegle. Domyślnie wszystkie dostępne rdzenie na komputerze są dostępne do użycia. Określ jawną liczbę rdzeni przez ustawienie właściwości MaxCpuCount w węźle RunConfiguration w pliku runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy zgodne z podanym wyrażeniem. `<Expression>`ma format `<property>Operator<value>[|&<Expression>]`, gdzie operator jest jednym z `=`, `!=`lub `~`. Operator `~` ma semantykę "Contains" i ma zastosowanie do właściwości ciągów, `DisplayName`takich jak. Nawiasy `()` są używane do grupowania wyrażeń podrzędnych.

`-?|--Help|/?|/Help`

Drukuje krótką pomoc dla polecenia.

`--logger|/logger:<Logger Uri/FriendlyName>`

Określ Rejestrator dla wyników testu.

* Aby opublikować wyniki testów w Team Foundation Server, użyj `TfsPublisher` dostawcy rejestratora:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Aby zarejestrować wyniki do pliku wyniki testów programu Visual Studio (TRX), użyj `trx` dostawcy rejestratora. Ten przełącznik tworzy plik w katalogu wyników testu o podaną nazwę pliku dziennika. Jeśli `LogFileName` nie zostanie podany, unikatowa nazwa pliku zostanie utworzona w celu przechowywania wyników testu.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Wyświetla wszystkie odnalezione testy z danego kontenera testowego.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port dla połączenia gniazda i otrzymywania komunikatów o zdarzeniach.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane do podanego pliku.

`args`

Określa dodatkowe argumenty do przekazania do adaptera. Argumenty są określane jako pary nazwa-wartość formularza `<n>=<v>`, gdzie `<n>` jest nazwą argumentu i `<v>` jest wartością argumentu. Użyj spacji, aby rozdzielić wiele argumentów.

---

## <a name="examples"></a>Przykłady

Uruchom testy w `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Uruchom testy w `mytestproject.dll`, Eksportuj do folderu niestandardowego z nazwą niestandardową:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Uruchom testy w `mytestproject.dll` i `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Uruchom `TestMethod1` testy:

`dotnet vstest /Tests:TestMethod1`

Uruchom `TestMethod1` i`TestMethod2` testy:

`dotnet vstest /Tests:TestMethod1,TestMethod2`
