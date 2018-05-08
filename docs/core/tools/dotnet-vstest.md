---
title: polecenie vstest DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie vstest dotnet tworzy projekt i wszystkie jego zależności.
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 981b56aa46afd5ca313ee0be0ca10843ef70e939
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-vstest"></a>DotNet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet-vstest` -Uruchamia testy z określonych plików.

## <a name="synopsis"></a>Streszczenie

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a>Opis

`dotnet-vstest` Polecenia `VSTest.Console` wiersza polecenia do uruchomienia aplikacji zautomatyzowane jednostkowe i kodowane testy interfejsu użytkownika aplikacji.

## <a name="arguments"></a>Argumenty

`TEST_FILE_NAMES`

Uruchom testy z określonych zestawów. Oddziel wiele nazw zestawów testów ze spacjami.

## <a name="options"></a>Opcje

`--Settings|/Settings:<Settings File>`

Ustawienia używane podczas uruchamiania testów.

`--Tests|/Tests:<Test Names>`

Uruchom testy o nazwach odpowiadających podanych wartości. Wiele wartości należy oddzielić przecinkami.

`--TestAdapterPath|/TestAdapterPath`

Używa niestandardowych adapterów testowych z danej ścieżce (jeśli istnieją) w uruchomieniu testu.

`--Platform|/Platform:<Platform type>`

Docelowa architektura platformy, używany do wykonywania testów. Prawidłowe wartości to `x86`, `x64`, i `ARM`.

`--Framework|/Framework:<Framework Version>`

Docelowy .NET Framework w wersji używany do wykonywania testów. Przykłady prawidłowych wartości `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`itp. Inne obsługiwane wartości to `Framework35`, `Framework40`, `Framework45`, i `FrameworkCore10`.

`--Parallel|/Parallel`

Wykonywać testy równolegle. Domyślnie wszystkie dostępne rdzenie komputera są dostępne do użycia. Ustaw jawne liczba rdzeni z pliku ustawień.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Uruchom testy, które odpowiada danemu wyrażeniu. `<Expression>` jest w formacie `<property>Operator<value>[|&<Expression>]`, w którym Operator jest jednym z `=`, `!=`, lub `~`.  Operator `~` ma semantykę "zawiera" i ma zastosowanie do właściwości ciągów, takich jak `DisplayName`. Nawias `()` służą do grupy wyrażeń podrzędnych.

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

Listy wykrytych testów w danym kontenerze testowym.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.

`--Port|/Port:<Port>`

Określa port na potrzeby połączenia gniazda i odbieranie komunikatów zdarzeń.

`--Diag|/Diag:<Path to log file>`

Włącza pełne dzienniki dla platformy testowej. Dzienniki są zapisywane do podanego pliku.

`args`

Określa dodatkowe argumenty do przekazania do karty sieciowej. Argumenty są określone jako pary nazwa wartość w formie `<n>=<v>`, gdzie `<n>` jest nazwa argumentu i `<v>` jest wartość argumentu. Użyj miejscem do oddzielania wielu argumentów.

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

