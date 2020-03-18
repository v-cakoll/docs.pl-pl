---
title: Debuguj samouczek przeciekać pamięci
description: Dowiedz się, jak debugować przeciek pamięci w .NET Core.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737730"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>Samouczek: Debugowanie przecieku pamięci w .NET Core

**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji

W tym samouczku przedstawiono narzędzia do analizowania przeciekpamięci .NET Core.

Ten samouczek używa przykładowej aplikacji, która została zaprojektowana do celowo przeciek pamięci. Próbka jest dostarczana jako ćwiczenie. Można analizować aplikację, która jest przypadkowo przecieka pamięci zbyt.

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
>
> - Sprawdź użycie pamięci zarządzanej za pomocą [liczników dotnet .](dotnet-counters.md)
> - Generowanie pliku zrzutu.
> - Analizowanie użycia pamięci przy użyciu pliku zrzutu.

## <a name="prerequisites"></a>Wymagania wstępne

Samouczek używa:

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.
- [dotnet-trace](dotnet-trace.md) do procesów listy.
- [dotnet-liczniki](dotnet-counters.md) do sprawdzania użycia pamięci zarządzanej.
- [dotnet-dump](dotnet-dump.md) do zbierania i analizowania pliku zrzutu.
- Przykładowa aplikacja [docelowa debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) do zdiagnozowania.

Samouczek zakłada, że przykład i narzędzia są zainstalowane i gotowe do użycia.

## <a name="examine-managed-memory-usage"></a>Sprawdź użycie pamięci zarządzanej

Przed rozpoczęciem zbierania danych diagnostycznych, aby pomóc nam spowodować ten scenariusz, należy upewnić się, że rzeczywiście widzisz przeciek pamięci (wzrost pamięci). Aby to potwierdzić, można użyć narzędzia [liczniki dotnet.](dotnet-counters.md)

Otwórz okno konsoli i przejdź do katalogu, w którym pobrano, i rozpakuj [przykładowy obiekt docelowy debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/). Uruchom obiekt docelowy:

```dotnetcli
dotnet run
```

Z oddzielnej konsoli znajdź identyfikator procesu za pomocą narzędzia [dotnet-trace:](dotnet-trace.md)

```console
dotnet-trace ps
```

Dane wyjściowe powinny być podobne do:

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Teraz sprawdź użycie pamięci zarządzanej za pomocą narzędzia [liczników dotnet.](dotnet-counters.md) Określa `--refresh-interval` liczbę sekund między odświeżeniami:

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

Dane wyjściowe na żywo powinny być podobne do:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

Koncentrując się na tej linii:

```console
    GC Heap Size (MB)                                  4
```

Widać, że zarządzana pamięć sterty wynosi 4 MB zaraz po uruchomieniu.

Teraz naciśnij adres `http://localhost:5000/api/diagscenario/memleak/20000`URL .

Należy zauważyć, że użycie pamięci wzrosła do 30 MB.

```console
    GC Heap Size (MB)                                 30
```

Obserwując użycie pamięci, można śmiało powiedzieć, że pamięć rośnie lub przecieka. Następnym krokiem jest zebranie odpowiednich danych do analizy pamięci.

### <a name="generate-memory-dump"></a>Generowanie zrzutu pamięci

Podczas analizowania możliwych przecieków pamięci potrzebny jest dostęp do sterty pamięci aplikacji. Następnie można analizować zawartość pamięci. Patrząc na relacje między obiektami, można tworzyć teorie na temat dlaczego pamięć nie jest zwalniana. Typowym źródłem danych diagnostyki jest zrzut pamięci w systemie Windows lub równoważne zrzut rdzenia w systemie Linux. Aby wygenerować zrzut aplikacji .NET Core, można użyć narzędzia [dotnet-dump).](dotnet-dump.md)

Przy użyciu [próbnego obiektu docelowego debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) wcześniej uruchomione, uruchom następujące polecenie, aby wygenerować zrzut rdzenia systemu Linux:

```dotnetcli
dotnet-dump collect -p 4807
```

Wynik jest zrzut rdzenia znajduje się w tym samym folderze.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Ponowne uruchomienie nieudanego procesu

Po zebraniu zrzutu należy mieć wystarczające informacje, aby zdiagnozować proces, który nie powiódł się. Jeśli proces nie powiodło się jest uruchomiony na serwerze produkcyjnym, teraz jest to idealny czas na krótkoterminowe korygowania przez ponowne uruchomienie procesu.

W tym samouczku gotowe są [przykładowe miejsce docelowe debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) i można go zamknąć. Przejdź do terminalu, który `Control-C`uruchomił serwer i naciśnij klawisz .

### <a name="analyze-the-core-dump"></a>Analizowanie zrzutu rdzenia

Teraz, gdy masz wygenerowany zrzut rdzenia, użyj narzędzia [dotnet-dump),](dotnet-dump.md) aby przeanalizować zrzut:

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Gdzie `core_20190430_185145` jest nazwa zrzutu rdzenia, który chcesz przeanalizować.

> [!NOTE]
> Jeśli widzisz błąd narzekający, że nie można odnaleźć *libdl.so,* może być trzeba zainstalować pakiet *libc6-dev.* Aby uzyskać więcej informacji, zobacz [Wymagania wstępne dotyczące programu .NET Core w systemie Linux](../linux-prerequisites.md).

Zostanie wyświetlony monit, w którym można wprowadzić polecenia SOS. Często pierwszą rzeczą, na którą chcesz spojrzeć, jest ogólny stan zarządzanej sterty:

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

W tym miejscu można zobaczyć, że większość obiektów są albo `String` lub `Customer` obiektów.

Za pomocą `dumpheap` polecenia można ponownie użyć tabeli metod (MT), `String` aby uzyskać listę wszystkich wystąpień:

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

Teraz można użyć `gcroot` polecenia `System.String` w wystąpieniu, aby zobaczyć, jak i dlaczego obiekt jest zakorzeniony. Bądź cierpliwy, ponieważ to polecenie trwa kilka minut ze stertą 30 MB:

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

Widać, że `String` jest bezpośrednio w `Customer` posiadaniu obiektu i `CustomerCache` pośrednio posiadanych przez obiekt.

Można kontynuować dumpingu obecnie obiektów, aby zobaczyć, że większość `String` obiektów po podobny wzorzec. W tym momencie dochodzenie dostarczyło wystarczających informacji, aby zidentyfikować główną przyczynę w kodzie.

Ta ogólna procedura pozwala zidentyfikować źródło głównych przecieków pamięci.

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W tym samouczku uruchomiono przykładowy serwer sieci Web. Ten serwer powinien zostać zamknięty, jak [wyjaśniono](#restart-the-failed-process) w sekcji Uruchom ponownie proces nie powiodło się.

Można również usunąć utworzony plik zrzutu.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka.

Nadal publikujemy więcej samouczków diagnostycznych. Wersje robocze można odczytać w repozytorium [dotnet/diagnostics.](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

W tym samouczku omówiono podstawy kluczowych narzędzi diagnostycznych .NET. Aby uzyskać informacje o zaawansowanym użyciu, zobacz następującą dokumentację referencyjną:

* [dotnet-trace](dotnet-trace.md) do procesów listy.
* [dotnet-liczniki](dotnet-counters.md) do sprawdzania użycia pamięci zarządzanej.
* [dotnet-dump](dotnet-dump.md) do zbierania i analizowania pliku zrzutu.
