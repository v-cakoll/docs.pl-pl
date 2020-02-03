---
title: Debuguj samouczek przecieku pamięci
description: Informacje o debugowaniu przecieku pamięci w programie .NET Core.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737730"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>Samouczek: debugowanie przecieku pamięci w programie .NET Core

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach

W tym samouczku przedstawiono narzędzia służące do analizowania przecieków pamięci w środowisku .NET Core.

Ten samouczek korzysta z przykładowej aplikacji, która została zaprojektowana w celu celowego przecieku pamięci. Przykład jest udostępniany jako ćwiczenie. Można przeanalizować aplikację, która powoduje zbyt przypadkowe przecieki pamięci.

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
>
> - Sprawdzanie użycia pamięci zarządzanej przy użyciu [liczników dotnet-Counters](dotnet-counters.md).
> - Generuj plik zrzutu.
> - Analizuj użycie pamięci za pomocą pliku zrzutu.

## <a name="prerequisites"></a>Wymagania wstępne

Samouczek używa:

- [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.
- [dotnet-Trace](dotnet-trace.md) , aby wyświetlić listę procesów.
- [dotnet-Counters](dotnet-counters.md) , aby sprawdzić użycie pamięci zarządzanej.
- [dotnet-dump](dotnet-dump.md) , aby zebrać i przeanalizować plik zrzutu.
- [Przykładowa](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) aplikacja do debugowania do diagnozowania.

W samouczku założono, że przykład i narzędzia są zainstalowane i gotowe do użycia.

## <a name="examine-managed-memory-usage"></a>Sprawdzanie użycia pamięci zarządzanej

Przed rozpoczęciem zbierania danych diagnostycznych, aby pomóc nam w tym scenariuszu, należy się upewnić, że faktycznie widzisz przeciek pamięci (przyrost pamięci). Za pomocą narzędzia [dotnet-Counters](dotnet-counters.md) można potwierdzić, że.

Otwórz okno konsoli i przejdź do katalogu, w którym został pobrany i rozpakowany [przykładowy element docelowy debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/). Uruchom obiekt docelowy:

```dotnetcli
dotnet run
```

W oddzielnym konsoli Znajdź identyfikator procesu za pomocą narzędzia do [śledzenia dotnet](dotnet-trace.md) :

```console
dotnet-trace ps
```

Dane wyjściowe powinny wyglądać podobnie do:

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Teraz Sprawdź użycie pamięci zarządzanej za pomocą narzędzia [dotnet-Counters](dotnet-counters.md) . `--refresh-interval` określa liczbę sekund między odświeżeniami:

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

Na żywo dane wyjściowe powinny wyglądać podobnie do:

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

Skoncentrowanie się na tym wierszu:

```console
    GC Heap Size (MB)                                  4
```

Po uruchomieniu programu można zobaczyć, że pamięć sterty zarządzanej ma 4 MB.

Teraz naciśnij pozycję adres URL `http://localhost:5000/api/diagscenario/memleak/20000`.

Zwróć uwagę, że użycie pamięci wystąpiło do 30 MB.

```console
    GC Heap Size (MB)                                 30
```

Obserwując użycie pamięci, można bezpiecznie powiedzieć, że pamięć jest zwiększana lub wycieka. Następnym krokiem jest zebranie odpowiednich danych na potrzeby analizy pamięci.

### <a name="generate-memory-dump"></a>Generuj zrzut pamięci

Podczas analizowania potencjalnych przecieków pamięci potrzebny jest dostęp do sterty pamięci aplikacji. Następnie można analizować zawartość pamięci. Analizując relacje między obiektami, tworzysz teorie na Dlaczego pamięć nie jest zwalniana. Typowym źródłem danych diagnostyki jest zrzut pamięci w systemie Windows lub równoważny zrzut rdzenia w systemie Linux. Aby wygenerować zrzut aplikacji .NET Core, można użyć narzędzia [dotnet-dump)](dotnet-dump.md) .

Używając wcześniej uruchomionego [przykładowego elementu Debug](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) , uruchom następujące polecenie, aby wygenerować podstawowy zrzut systemu Linux:

```dotnetcli
dotnet-dump collect -p 4807
```

Wynik jest podstawowym zrzutem znajdującym się w tym samym folderze.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Uruchom ponownie proces zakończony niepowodzeniem

Po zebraniu zrzutu należy dysponować wystarczającą ilością informacji, aby zdiagnozować proces zakończony niepowodzeniem. Jeśli proces zakończony niepowodzeniem jest uruchomiony na serwerze produkcyjnym, teraz jest idealnym czasem do krótkoterminowego korygowania przez ponowne uruchomienie procesu.

W ramach tego samouczka nastąpi przetworzenie [przykładowego celu debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) i można go zamknąć. Przejdź do terminalu, który uruchomił serwer i naciśnij `Control-C`.

### <a name="analyze-the-core-dump"></a>Analizowanie zrzutu rdzeni

Teraz, gdy masz wygenerowany podstawowy zrzut, użyj narzędzia [dotnet-dump](dotnet-dump.md) , aby przeanalizować zrzut:

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Gdzie `core_20190430_185145` jest nazwą zrzutu podstawowego, który ma zostać przeanalizowany.

> [!NOTE]
> Jeśli zostanie wyświetlony błąd z skargą, że nie można znaleźć *libdl.so* , może być konieczne zainstalowanie pakietu *libc6-dev* . Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące platformy .NET Core w systemie Linux](../linux-prerequisites.md).

Zostanie wyświetlony monit z pytaniem, gdzie można wprowadzić polecenia SOS. Często pierwszym krokiem, jaki ma wyglądać, jest ogólny stan sterty zarządzanej:

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

W tym miejscu można zobaczyć, że większość obiektów jest `String` lub `Customer` obiektów.

Możesz użyć polecenia `dumpheap` ponownie z tabeli metod (MT), aby uzyskać listę wszystkich wystąpień `String`:

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

Teraz można użyć `gcroot` polecenia w wystąpieniu `System.String`, aby zobaczyć, jak i dlaczego obiekt jest odblokowany. Należy poczekać, ponieważ to polecenie zajmie kilka minut z stertą o rozmiarze 30 MB:

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

Można zobaczyć, że `String` jest bezpośrednio przechowywane przez obiekt `Customer` i pośrednio przechowywany przez obiekt `CustomerCache`.

Można kontynuować zrzucanie obiektów, aby zobaczyć, że większość `String` obiektów jest zgodna z podobnym wzorcem. W tym momencie Badanie dostarczyło wystarczające informacje umożliwiające zidentyfikowanie głównej przyczyny w kodzie.

Ta ogólna procedura umożliwia zidentyfikowanie źródła głównych przecieków pamięci.

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W tym samouczku uruchomiono przykładowy serwer sieci Web. Ten serwer powinien zostać wyłączony zgodnie z opisem w sekcji [Ponowne uruchamianie procesu zakończonego niepowodzeniem](#restart-the-failed-process) .

Można również usunąć utworzony plik zrzutu.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka.

Nadal publikujemy więcej samouczków diagnostycznych. Wersje robocze można odczytać w repozytorium [dotnet/Diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) .

W tym samouczku omówiono podstawy najważniejszych narzędzi diagnostycznych platformy .NET. Aby uzyskać zaawansowane informacje o użyciu, zobacz następującą dokumentację referencyjną:

* [dotnet-Trace](dotnet-trace.md) , aby wyświetlić listę procesów.
* [dotnet-Counters](dotnet-counters.md) , aby sprawdzić użycie pamięci zarządzanej.
* [dotnet-dump](dotnet-dump.md) , aby zebrać i przeanalizować plik zrzutu.
