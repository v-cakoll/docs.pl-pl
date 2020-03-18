---
title: dotnet-liczniki - .NET Core
description: Dowiedz się, jak zainstalować narzędzie wiersza polecenia dotnet-counter i używać go.
ms.date: 02/26/2020
ms.openlocfilehash: dc95297478784ca06fe442a939f8489a40b29da7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147181"
---
# <a name="dotnet-counters"></a>dotnet-counters

**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji

## <a name="install-dotnet-counters"></a>Instalowanie liczników dotnet

Aby zainstalować najnowszą `dotnet-counters` wersję [pakietu NuGet,](https://www.nuget.org/packages/dotnet-counters)użyj polecenia [instalacji narzędzia dotnet:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Streszczenie

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Opis

`dotnet-counters`jest narzędziem monitorowania wydajności do monitorowania stanu zdrowia ad hoc i badania wydajności pierwszego poziomu. Można obserwować wartości licznika wydajności, <xref:System.Diagnostics.Tracing.EventCounter> które są publikowane za pośrednictwem interfejsu API. Na przykład można szybko monitorować takie rzeczy, jak użycie procesora CPU lub szybkość wyjątków zgłaszanych w aplikacji .NET Core, aby sprawdzić, czy jest coś podejrzanego przed przejściem do poważniejszego badania wydajności przy użyciu `PerfView` lub `dotnet-trace`.

## <a name="options"></a>Opcje

- **`--version`**

  Wyświetla wersję narzędzia dotnet-counters.

- **`-h|--help`**

  Pokazuje pomoc wiersza polecenia.

## <a name="commands"></a>Polecenia

| Polecenie                                             |
| --------------------------------------------------- |
| [dotnet-liczniki zbierają](#dotnet-counters-collect) |
| [lista liczników dotnet](#dotnet-counters-list)       |
| [monitor dotnet-liczników](#dotnet-counters-monitor) |
| [dotnet-liczniki ps](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a>dotnet-liczniki zbierają

Okresowo zbieraj wybrane wartości liczników i eksportuj je do określonego formatu pliku do przetwarzania końcowego.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a>Opcje

- **`-p|--process-id <PID>`**

  Identyfikator procesu, który ma być monitorowany.

- **`--refresh-interval <SECONDS>`**

  Liczba sekund opóźnienia między aktualizacją wyświetlanych liczników

- **`counter_list <COUNTERS>`**

  Oddzielona spacjami lista liczników. Można określić liczniki `provider_name[:counter_name]`. Jeśli `provider_name` jest używany bez `counter_name`kwalifikacji, wyświetlane są wszystkie liczniki. Aby odnaleźć nazwy dostawcy i liczników, użyj polecenia [listy liczników dotnet.](#dotnet-counters-list)

- **`--format <csv|json>`**

  TFormat do wyeksportowania. Obecnie dostępne: csv, json.

- **`-o|--output <output>`**

  Nazwa pliku wyjściowego.

### <a name="examples"></a>Przykłady

- Zbierz wszystkie liczniki w interwale odświeżania 3 sekund i wygeneruj csv jako wyjście:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>lista liczników dotnet

Wyświetla listę nazw liczników i opisów pogrupowanych według dostawcy.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>Przykład

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a>monitor dotnet-liczników

Wyświetla okresowo odświeżające wartości wybranych liczników.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>Opcje

- **`-p|--process-id <PID>`**

  Identyfikator procesu, który ma być monitorowany.

- **`--refresh-interval <SECONDS>`**

  Liczba sekund opóźnienia między aktualizacją wyświetlanych liczników

- **`counter_list <COUNTERS>`**

  Oddzielona spacjami lista liczników. Można określić liczniki `provider_name[:counter_name]`. Jeśli `provider_name` jest używany bez `counter_name`kwalifikacji, wyświetlane są wszystkie liczniki. Aby odnaleźć nazwy dostawcy i liczników, użyj polecenia [listy liczników dotnet.](#dotnet-counters-list)

### <a name="examples"></a>Przykłady

- Monitoruj wszystkie `System.Runtime` liczniki z 3-sekundowym interwałem odświeżania:

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- Monitoruj tylko użycie procesora `System.Runtime`i rozmiar sterty GC od:

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Monitorowanie `EventCounter` wartości zdefiniowanych `EventSource`przez użytkownika . Aby uzyskać więcej informacji, zobacz [Samouczek: Jak mierzyć wydajność bardzo częstych zdarzeń przy użyciu EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>dotnet-liczniki ps

Wyświetla listę procesów dotnet, które mogą być monitorowane.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>Przykład

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
