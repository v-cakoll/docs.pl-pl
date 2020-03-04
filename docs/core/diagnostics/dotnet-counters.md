---
title: dotnet-Counters — .NET Core
description: Dowiedz się, jak zainstalować i użyć narzędzia wiersza polecenia programu dotnet-Counter.
ms.date: 02/26/2020
ms.openlocfilehash: 88f701a60d0ee03dd0236ae54c57679943e14939
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157885"
---
# <a name="dotnet-counters"></a>dotnet-counters

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach

## <a name="install-dotnet-counters"></a>Zainstaluj dotnet-Counters

Aby zainstalować najnowszą wersję wydania [pakietu NuGet](https://www.nuget.org/packages/dotnet-counters)`dotnet-counters`, użyj [Narzędzia dotnet Install](../tools/dotnet-tool-install.md) Command:

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Streszczenie

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Opis

`dotnet-counters` to narzędzie do monitorowania wydajności dla monitorowania kondycji ad hoc i badania wydajności pierwszego poziomu. Może obserwować wartości liczników wydajności, które są publikowane za pośrednictwem interfejsu API <xref:System.Diagnostics.Tracing.EventCounter>. Można na przykład szybko monitorować elementy, takie jak użycie procesora CPU lub częstotliwość zgłaszania wyjątków w aplikacji .NET Core, aby sprawdzić, czy istnieją jakieś podejrzane informacje przed uzyskaniem większej wydajności, przy użyciu `PerfView` lub `dotnet-trace`.

## <a name="options"></a>Opcje

- **`--version`**

  Wyświetla wersję narzędzia dotnet-Counters.

- **`-h|--help`**

  Wyświetla pomoc w wierszu polecenia.

## <a name="commands"></a>Polecenia

| Polecenie                                             |
| --------------------------------------------------- |
| [dotnet — Zbieranie liczników](#dotnet-counters-collect) |
| [dotnet-lista liczników](#dotnet-counters-list)       |
| [Monitor dotnet-Counters](#dotnet-counters-monitor) |
| [dotnet-liczniki PS](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a>dotnet — Zbieranie liczników

Okresowo Zbieraj wybrane wartości licznika i Eksportuj je do określonego formatu pliku na potrzeby przetwarzania końcowego.

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

  Rozdzielana spacjami lista liczników. Liczniki można określić `provider_name[:counter_name]`. Jeśli `provider_name` jest używany bez kwalifikowania `counter_name`, zostaną wyświetlone wszystkie liczniki. Aby odnaleźć nazwy dostawcy i licznika, użyj polecenia [dotnet-Counters](#dotnet-counters-list) .

- **`--format <csv|json>`**

  Format tnie do wyeksportowania. Obecnie dostępne: CSV, JSON.

- **`-o|--output <output>`**

  Nazwa pliku wyjściowego.

### <a name="examples"></a>Przykłady

- Zbieraj wszystkie liczniki z interwałem odświeżania równym 3 sekund i Generuj wolumin CSV jako dane wyjściowe:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>dotnet-lista liczników

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

## <a name="dotnet-counters-monitor"></a>Monitor dotnet-Counters

Wyświetla okresowe odświeżanie wartości wybranych liczników.

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

  Rozdzielana spacjami lista liczników. Liczniki można określić `provider_name[:counter_name]`. Jeśli `provider_name` jest używany bez kwalifikowania `counter_name`, zostaną wyświetlone wszystkie liczniki. Aby odnaleźć nazwy dostawcy i licznika, użyj polecenia [dotnet-Counters](#dotnet-counters-list) .

### <a name="examples"></a>Przykłady

- Monitoruj wszystkie liczniki z `System.Runtime` w interwałie odświeżania równym 3 sekund:

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

- Monitoruj tylko użycie procesora CPU i rozmiar sterty GC na podstawie `System.Runtime`:

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Monitoruj wartości `EventCounter` z `EventSource`zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji, zobacz [Samouczek: jak mierzyć wydajność dla bardzo częstych zdarzeń przy użyciu EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>dotnet-liczniki PS 

Wyświetl listę procesów dotnet, które mogą być monitorowane.

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
