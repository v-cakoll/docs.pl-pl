---
title: polecenie vstest DotNet
description: Polecenia dotnet vstest kompiluje projekt i wszystkie jego zależności.
author: guardrex
ms.date: 05/30/2018
ms.openlocfilehash: d41e901f70b4a3d0647c693fdd8076f771466073
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747732"
---
# <a name="dotnet-vstest"></a>DotNet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet-vstest` -Uruchamia testy z określonych plików.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a>Opis

`dotnet-vstest` Polecenia `VSTest.Console` aplikacji wiersza polecenia, aby uruchomić automatyczne testy jednostkowe.

## <a name="arguments"></a>Argumenty

`TEST_FILE_NAMES`

Uruchom testy z określonych zestawów. Oddziel wiele nazw zestawów testowych spacjami.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Ustawienia używane podczas uruchamiania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy o nazwach odpowiadających podanej wartości. Wiele wartości należy oddzielić przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.

`--Platform|/Platform:<Platform type>`

Docelowa platforma architektury używanej do wykonania testu. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Wersja docelowa.NET Framework używanego do wykonania testu. Prawidłowe wartości należą do nich `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework40`, `Framework45`, `FrameworkCore10`, i `FrameworkUap10`.

`--Parallel|/Parallel`

Wykonuj testy równolegle. Domyślnie wszystkie dostępne rdzenie maszyny są dostępne do użycia. Określ jawną liczby rdzeni, ustawiając właściwość MaxCpuCount w węźle RunConfiguration w pliku runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy, które odpowiadają danemu wyrażeniu. `<Expression>` Format `<property>Operator<value>[|&<Expression>]`, w której Operator jest jednym z `=`, `!=`, lub `~`. Operator `~` ma "zawiera" semantykę i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`. Nawias `()` służą do podrzędną wyrażeniach grupy.

`-?|--Help|/?|/Help`

Drukuje krótki pomoc dotyczącą polecenia.

`--logger|/logger:<Logger Uri/FriendlyName>`

Określ Rejestrator dla wyników badań.

* Aby opublikować wyniki testu z Team Foundation Server, użyj `TfsPublisher` rejestratora dostawcy:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), użyj `trx` dostawcy rejestratora. Ten przełącznik tworzy plik w wynikach testu katalogu przy użyciu danej nazwy pliku dziennika. Jeśli `LogFileName` nie jest udostępniany unikatowej nazwy pliku jest utworzona w celu przechowywania wyników testów.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Wyświetla listę wszystkich odnalezionych testów z podanego kontenera testowego.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port do połączenia z gniazdem i odbierania komunikatów zdarzeń.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki platformy testów. Dzienniki są zapisywane do podanego pliku.

`--Blame|/Blame`

Uruchamia testy w trybie polecenia blame. Ta opcja jest przydatna polega na wyizolowaniu problematyczne testy, powodując hosta testów ulega awarii. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* , przechwytuje kolejność wykonywania testów przed awarią.

`--InIsolation|/InIsolation`

Uruchamia testy w procesie izolowanym. To sprawia, że *vstest.console.exe* procesu mniej prawdopodobne zatrzymane w przypadku błędu w testach, ale testy mogą działać wolniej.

`@<file>`

Odczytuje plik odpowiedzi, aby wyświetlić więcej opcji.


`args`

Określa dodatkowe argumenty do przekazania do adaptera. Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu. Użyj spacji do oddzielania wielu argumentów.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Ustawienia używane podczas uruchamiania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy o nazwach odpowiadających podanej wartości. Wiele wartości należy oddzielić przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.

`--Platform|/Platform:<Platform type>`

Docelowa platforma architektury używanej do wykonania testu. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Wersja docelowa.NET Framework używanego do wykonania testu. Prawidłowe wartości należą do nich `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.

`--Parallel|/Parallel`

Wykonuj testy równolegle. Domyślnie wszystkie dostępne rdzenie maszyny są dostępne do użycia. Określ jawną liczby rdzeni, ustawiając właściwość MaxCpuCount w węźle RunConfiguration w pliku runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy, które odpowiadają danemu wyrażeniu. `<Expression>` Format `<property>Operator<value>[|&<Expression>]`, w której Operator jest jednym z `=`, `!=`, lub `~`. Operator `~` ma "zawiera" semantykę i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`. Nawias `()` służą do podrzędną wyrażeniach grupy.

`-?|--Help|/?|/Help`

Drukuje krótki pomoc dotyczącą polecenia.

`--logger|/logger:<Logger Uri/FriendlyName>`

Określ Rejestrator dla wyników badań.

* Aby opublikować wyniki testu z Team Foundation Server, użyj `TfsPublisher` rejestratora dostawcy:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), użyj `trx` dostawcy rejestratora. Ten przełącznik tworzy plik w wynikach testu katalogu przy użyciu danej nazwy pliku dziennika. Jeśli `LogFileName` nie jest udostępniany unikatowej nazwy pliku jest utworzona w celu przechowywania wyników testów.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Wyświetla listę wszystkich odnalezionych testów z podanego kontenera testowego.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port do połączenia z gniazdem i odbierania komunikatów zdarzeń.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki platformy testów. Dzienniki są zapisywane do podanego pliku.

`args`

Określa dodatkowe argumenty do przekazania do adaptera. Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu. Użyj spacji do oddzielania wielu argumentów.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Ustawienia używane podczas uruchamiania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy o nazwach odpowiadających podanej wartości. Wiele wartości należy oddzielić przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.

`--Platform|/Platform:<Platform type>`

Docelowa platforma architektury używanej do wykonania testu. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Wersja docelowa.NET Framework używanego do wykonania testu. Prawidłowe wartości należą do nich `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework40`, `Framework45`, i `FrameworkCore10`.

`--Parallel|/Parallel`

Wykonuj testy równolegle. Domyślnie wszystkie dostępne rdzenie maszyny są dostępne do użycia. Określ jawną liczby rdzeni, ustawiając właściwość MaxCpuCount w węźle RunConfiguration w pliku runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy, które odpowiadają danemu wyrażeniu. `<Expression>` Format `<property>Operator<value>[|&<Expression>]`, w której Operator jest jednym z `=`, `!=`, lub `~`. Operator `~` ma "zawiera" semantykę i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`. Nawias `()` służą do podrzędną wyrażeniach grupy.

`-?|--Help|/?|/Help`

Drukuje krótki pomoc dotyczącą polecenia.

`--logger|/logger:<Logger Uri/FriendlyName>`

Określ Rejestrator dla wyników badań.

* Aby opublikować wyniki testu z Team Foundation Server, użyj `TfsPublisher` rejestratora dostawcy:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), użyj `trx` dostawcy rejestratora. Ten przełącznik tworzy plik w wynikach testu katalogu przy użyciu danej nazwy pliku dziennika. Jeśli `LogFileName` nie jest udostępniany unikatowej nazwy pliku jest utworzona w celu przechowywania wyników testów.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Wyświetla listę wszystkich odnalezionych testów z podanego kontenera testowego.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port do połączenia z gniazdem i odbierania komunikatów zdarzeń.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki platformy testów. Dzienniki są zapisywane do podanego pliku.

`args`

Określa dodatkowe argumenty do przekazania do adaptera. Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu. Użyj spacji do oddzielania wielu argumentów.

---

## <a name="examples"></a>Przykłady

Uruchom testy w `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Uruchom testy w `mytestproject.dll`, eksportowania do niestandardowego folderu o nazwie niestandardowy:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Uruchom testy w `mytestproject.dll` i `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Uruchom `TestMethod1` testów:

`dotnet vstest /Tests:TestMethod1`

Uruchom `TestMethod1` i `TestMethod2` testów:

`dotnet vstest /Tests:TestMethod1,TestMethod2`
