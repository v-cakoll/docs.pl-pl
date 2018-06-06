---
title: polecenie vstest DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie vstest dotnet tworzy projekt i wszystkie jego zależności.
author: guardrex
ms.author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 84b9d9eebfbf20fefe8153dd3ae9bec0f34986c8
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696341"
---
# <a name="dotnet-vstest"></a>DotNet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet-vstest` -Uruchamia testy z określonych plików.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)
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

`dotnet-vstest` Polecenia `VSTest.Console` wiersza polecenia do uruchomienia aplikacji zautomatyzowane jednostkowe i kodowane testy interfejsu użytkownika aplikacji.

## <a name="arguments"></a>Argumenty

`TEST_FILE_NAMES`

Uruchom testy z określonych zestawów. Oddziel wiele nazw zestawów testów ze spacjami.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Ustawienia używane podczas uruchamiania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy o nazwach odpowiadających podanych wartości. Wiele wartości należy oddzielić przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Używa niestandardowych adapterów testowych z danej ścieżce (jeśli istnieją) w uruchomieniu testu.

`--Platform|/Platform:<Platform type>`

Docelowa architektura platformy, używany do wykonywania testów. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Docelowy .NET Framework w wersji używany do wykonywania testów. Przykłady prawidłowych wartości `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework35`, `Framework40`, `Framework45`, `FrameworkCore10`, i `FrameworkUap10`.

`--Parallel|/Parallel`

Wykonywać testy równolegle. Domyślnie wszystkie dostępne rdzenie komputera są dostępne do użycia. Ustaw jawne liczba rdzeni z pliku ustawień.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy, które odpowiada danemu wyrażeniu. `<Expression>` jest w formacie `<property>Operator<value>[|&<Expression>]`, w którym Operator jest jednym z `=`, `!=`, lub `~`. Operator `~` ma semantykę "zawiera" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`. Nawias `()` służą do grupy wyrażeń podrzędnych.

`-?|--Help|/?|/Help`

Drukuje krótkich pomocy dla polecenia.

`--logger|/logger:<Logger Uri/FriendlyName>`

Określ Rejestrator dla wyników testu.

* Aby opublikować wyniki testu z Team Foundation Server, należy użyć `TfsPublisher` rejestratora dostawcy:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), należy użyć `trx` dostawcy rejestratora. Ten przełącznik tworzy plik w wynikach testów katalogu z podana nazwa pliku dziennika. Jeśli `LogFileName` nie jest podana unikatowa nazwa pliku jest tworzony dla wyników testu.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Wyświetla listę wszystkich wykrytych testów w danym kontenerze testowym.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port na potrzeby połączenia gniazda i odbieranie komunikatów zdarzeń.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane do podanego pliku.

`--Blame|/Blame`

Uruchamia testy w trybie winy. Ta opcja jest pomocna w izolowanie testów problemy powodujące hosta testów do awarii. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence.xml* który przechwytuje kolejność wykonywania testów przed tej awarii.

`--InIsolation|/InIsolation`

Uruchamia testy w proces izolowanym. Dzięki temu *vstest.console.exe* przetworzyć mniej prawdopodobne w przypadku błędu w testach, ale testy mogą być wykonywane wolniej.

`@<file>`

Odczytuje plik odpowiedzi, aby wyświetlić więcej opcji.


`args`

Określa dodatkowe argumenty do przekazania do karty sieciowej. Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu. Użyj miejscem do oddzielania wielu argumentów.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Ustawienia używane podczas uruchamiania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy o nazwach odpowiadających podanych wartości. Wiele wartości należy oddzielić przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Używa niestandardowych adapterów testowych z danej ścieżce (jeśli istnieją) w uruchomieniu testu.

`--Platform|/Platform:<Platform type>`

Docelowa architektura platformy, używany do wykonywania testów. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Docelowy .NET Framework w wersji używany do wykonywania testów. Przykłady prawidłowych wartości `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework35`, `Framework40`, `Framework45`, i `FrameworkCore10`.

`--Parallel|/Parallel`

Wykonywać testy równolegle. Domyślnie wszystkie dostępne rdzenie komputera są dostępne do użycia. Ustaw jawne liczba rdzeni z pliku ustawień.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy, które odpowiada danemu wyrażeniu. `<Expression>` jest w formacie `<property>Operator<value>[|&<Expression>]`, w którym Operator jest jednym z `=`, `!=`, lub `~`. Operator `~` ma semantykę "zawiera" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`. Nawias `()` służą do grupy wyrażeń podrzędnych.

`-?|--Help|/?|/Help`

Drukuje krótkich pomocy dla polecenia.

`--logger|/logger:<Logger Uri/FriendlyName>`

Określ Rejestrator dla wyników testu.

* Aby opublikować wyniki testu z Team Foundation Server, należy użyć `TfsPublisher` rejestratora dostawcy:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), należy użyć `trx` dostawcy rejestratora. Ten przełącznik tworzy plik w wynikach testów katalogu z podana nazwa pliku dziennika. Jeśli `LogFileName` nie jest podana unikatowa nazwa pliku jest tworzony dla wyników testu.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Wyświetla listę wszystkich wykrytych testów w danym kontenerze testowym.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port na potrzeby połączenia gniazda i odbieranie komunikatów zdarzeń.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane do podanego pliku.

`args`

Określa dodatkowe argumenty do przekazania do karty sieciowej. Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu. Użyj miejscem do oddzielania wielu argumentów.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Ustawienia używane podczas uruchamiania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy o nazwach odpowiadających podanych wartości. Wiele wartości należy oddzielić przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Używa niestandardowych adapterów testowych z danej ścieżce (jeśli istnieją) w uruchomieniu testu.

`--Platform|/Platform:<Platform type>`

Docelowa architektura platformy, używany do wykonywania testów. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Docelowy .NET Framework w wersji używany do wykonywania testów. Przykłady prawidłowych wartości `.NETFramework,Version=v4.6` lub `.NETCoreApp,Version=v1.0`. Inne obsługiwane wartości to `Framework35`, `Framework40`, `Framework45`, i `FrameworkCore10`.

`--Parallel|/Parallel`

Wykonywać testy równolegle. Domyślnie wszystkie dostępne rdzenie komputera są dostępne do użycia. Ustaw jawne liczba rdzeni z pliku ustawień.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy, które odpowiada danemu wyrażeniu. `<Expression>` jest w formacie `<property>Operator<value>[|&<Expression>]`, w którym Operator jest jednym z `=`, `!=`, lub `~`. Operator `~` ma semantykę "zawiera" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`. Nawias `()` służą do grupy wyrażeń podrzędnych.

`-?|--Help|/?|/Help`

Drukuje krótkich pomocy dla polecenia.

`--logger|/logger:<Logger Uri/FriendlyName>`

Określ Rejestrator dla wyników testu.

* Aby opublikować wyniki testu z Team Foundation Server, należy użyć `TfsPublisher` rejestratora dostawcy:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Aby rejestrować wyniki do programu Visual Studio Test wyniki pliku (TRX), należy użyć `trx` dostawcy rejestratora. Ten przełącznik tworzy plik w wynikach testów katalogu z podana nazwa pliku dziennika. Jeśli `LogFileName` nie jest podana unikatowa nazwa pliku jest tworzony dla wyników testu.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Wyświetla listę wszystkich wykrytych testów w danym kontenerze testowym.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port na potrzeby połączenia gniazda i odbieranie komunikatów zdarzeń.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane do podanego pliku.

`args`

Określa dodatkowe argumenty do przekazania do karty sieciowej. Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu. Użyj miejscem do oddzielania wielu argumentów.

---

## <a name="examples"></a>Przykłady

Uruchom testy w `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Uruchom testy w `mytestproject.dll`, eksportowanie do niestandardowego folderu o nazwie niestandardowych:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Uruchom testy w `mytestproject.dll` i `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Uruchom `TestMethod1` testów:

`dotnet vstest /Tests:TestMethod1`

Uruchom `TestMethod1` i `TestMethod2` testów:

`dotnet vstest /Tests:TestMethod1,TestMethod2`