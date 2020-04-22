---
title: Debugowanie samouczka przecieku pamięci
description: Dowiedz się, jak debugować przeciek pamięci w .NET Core.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: d47992bab9dab64cf7f88ff679eef407dd891b5a
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021359"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>Samouczek: Debugowanie przecieku pamięci w rdzeniu .NET

**Ten artykuł dotyczy:** ✔️.NET Core 3.0 SDK i nowszych wersjach

W tym samouczku przedstawiono narzędzia do analizowania przecieku pamięci .NET Core.

W tym samouczku użyto przykładowej aplikacji, która jest przeznaczona do celowo przeciek pamięci. Próbka jest dostarczana jako ćwiczenie. Można analizować aplikację, która jest przypadkowo przecieka pamięci zbyt.

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
>
> - Sprawdź użycie pamięci zarządzanej za pomocą [liczników dotnet](dotnet-counters.md).
> - Generowanie pliku zrzutu.
> - Analizowanie użycia pamięci przy użyciu pliku zrzutu.

## <a name="prerequisites"></a>Wymagania wstępne

W samouczku użyto:

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowszej wersji.
- [dotnet-trace](dotnet-trace.md) do listy procesów.
- [liczniki dotnet,](dotnet-counters.md) aby sprawdzić użycie pamięci zarządzanej.
- [dotnet-dump](dotnet-dump.md) do zbierania i analizowania pliku zrzutu.
- Przykładowa aplikacja [docelowa debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) do zdiagnozowania.

Samouczek zakłada, że przykład i narzędzia są zainstalowane i gotowe do użycia.

## <a name="examine-managed-memory-usage"></a>Sprawdzanie użycia pamięci zarządzanej

Przed rozpoczęciem zbierania danych diagnostycznych, aby pomóc nam główną przyczyną tego scenariusza, należy upewnić się, że rzeczywiście widzisz przeciek pamięci (wzrost pamięci). Aby to potwierdzić, można użyć narzędzia [liczników dotnet.](dotnet-counters.md)

Otwórz okno konsoli i przejdź do katalogu, w którym pobrano i rozpakowałeś [przykładowy cel debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/). Uruchom cel:

```dotnetcli
dotnet run
```

W osobnej konsoli znajdź identyfikator procesu za pomocą narzędzia [dotnet-trace:](dotnet-trace.md)

```console
dotnet-trace ps
```

Dane wyjściowe powinny być podobne do:

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Teraz sprawdź użycie pamięci zarządzanej za pomocą narzędzia [liczniki dotnet.](dotnet-counters.md) Określa `--refresh-interval` liczbę sekund między odświeżeniami:

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

Widać, że pamięć zarządzanego sterty jest 4 MB zaraz po uruchomieniu.

Teraz naciśnij adres `http://localhost:5000/api/diagscenario/memleak/20000`URL .

Należy zauważyć, że użycie pamięci wzrosła do 30 MB.

```console
    GC Heap Size (MB)                                 30
```

Obserwując użycie pamięci, można bezpiecznie powiedzieć, że pamięć rośnie lub przecieka. Następnym krokiem jest zebranie odpowiednich danych do analizy pamięci.

### <a name="generate-memory-dump"></a>Generowanie zrzutu pamięci

Podczas analizowania możliwych przecieków pamięci, należy uzyskać dostęp do sterty pamięci aplikacji. Następnie można analizować zawartość pamięci. Patrząc na relacje między obiektami, można tworzyć teorie na temat tego, dlaczego pamięć nie jest zwalniana. Typowym źródłem danych diagnostycznych jest zrzut pamięci w systemie Windows lub równoważny zrzut rdzenia w systemie Linux. Aby wygenerować zrzut aplikacji .NET Core, można użyć narzędzia [dotnet-dump).](dotnet-dump.md)

Przy użyciu [przykładowego obiektu docelowego debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) wcześniej rozpoczęte, uruchom następujące polecenie do generowania zrzutu rdzenia Systemu Linux:

```dotnetcli
dotnet-dump collect -p 4807
```

Wynikiem jest zrzut podstawowy znajdujący się w tym samym folderze.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Ponowne uruchamianie procesu nie powiodło się

Po zebraniu zrzutu należy mieć wystarczające informacje, aby zdiagnozować nieudany proces. Jeśli nieudany proces jest uruchomiony na serwerze produkcyjnym, teraz jest to idealny czas na krótkoterminowe korygowanie przez ponowne uruchomienie procesu.

W tym samouczku, teraz zrobić z [przykładowego obiektu docelowego debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) i można go zamknąć. Przejdź do terminalu, który `Control-C`uruchomił serwer i naciśnij przycisk .

### <a name="analyze-the-core-dump"></a>Analizowanie zrzutu rdzenia

Teraz, gdy masz wygenerowany zrzut rdzenia, użyj narzędzia [dotnet-dump](dotnet-dump.md) do analizy zrzutu:

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Gdzie `core_20190430_185145` jest nazwa zrzutu podstawowego, który chcesz przeanalizować.

> [!NOTE]
> Jeśli zostanie wyświetlony błąd narzekający, że nie można odnaleźć *libdl.so,* może być trzeba zainstalować pakiet *libc6-dev.* Aby uzyskać więcej informacji, zobacz [Wymagania wstępne dla platformy .NET Core w systemie Linux](../install/dependencies.md?pivots=os-linux).

Zostanie wyświetlony monit, w którym można wprowadzić polecenia SOS. Zazwyczaj pierwszą rzeczą, którą chcesz przyjrzeć się jest ogólny stan zarządzanego stosu:

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

Tutaj widać, że większość obiektów `String` `Customer` to obiekty lub obiekty.

Można użyć `dumpheap` polecenia ponownie z tabeli metody (MT), aby `String` uzyskać listę wszystkich wystąpień:

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

Widać, że `String` jest bezpośrednio utrzymywane `Customer` przez obiekt i `CustomerCache` pośrednio utrzymywane przez obiekt.

Można kontynuować wyrzucanie obiektów, `String` aby zobaczyć, że większość obiektów podąża za podobnym wzorcem. W tym momencie dochodzenie dostarczyło wystarczających informacji, aby zidentyfikować przyczynę w kodzie.

Ta ogólna procedura pozwala zidentyfikować źródło głównych przecieków pamięci.

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W tym samouczku uruchomiono przykładowy serwer sieci web. Ten serwer powinien zostać zamknięty, jak wyjaśniono w sekcji [Uruchom ponownie nieudany proces.](#restart-the-failed-process)

Można również usunąć plik zrzutu, który został utworzony.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka.

Nadal publikujemy więcej samouczków diagnostycznych. Wersje robocze można odczytać na repozytorium [dotnet/diagnostics.](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

W tym samouczku okryły się podstawy kluczowych narzędzi diagnostycznych platformy .NET. Aby uzyskać użycie zaawansowane, zobacz następującą dokumentację referencyjną:

* [dotnet-trace](dotnet-trace.md) do listy procesów.
* [liczniki dotnet,](dotnet-counters.md) aby sprawdzić użycie pamięci zarządzanej.
* [dotnet-dump](dotnet-dump.md) do zbierania i analizowania pliku zrzutu.
