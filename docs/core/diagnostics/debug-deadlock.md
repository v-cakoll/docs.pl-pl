---
title: Zakleszczenie debugowania — .NET Core
description: Samouczek, który przeprowadzi Cię przez debugowanie problemu blokowania w programie .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 247521176297254180d794d4d4fc850f30e343b0
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86926421"
---
# <a name="debug-a-deadlock-in-net-core"></a>Debugowanie zakleszczenia w programie .NET Core

**Ten artykuł ma zastosowanie do: ✔️** .net Core 3,1 SDK i nowszych wersjach

W tym samouczku dowiesz się, jak debugować scenariusz zakleszczenia. Korzystając z podanego ASP.NET Core przykładowego repozytorium kodu źródłowego [aplikacji sieci Web](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) , można przypadkowo zaistnieć zakleszczenie. Punkt końcowy będzie miał Rozwieszanie i kumulację wątków. Dowiesz się, jak można użyć różnych narzędzi do analizowania problemu, takiego jak zrzuty podstawowe, analiza zrzutów podstawowych i śledzenie procesów.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
>
> - Badanie zawieszenia aplikacji
> - Generuj podstawowy plik zrzutu
> - Analizuj wątki procesu w pliku zrzutu
> - Analizowanie bloków stosy wywołań i Sync
> - Diagnozowanie i rozwiązywanie zakleszczenia

## <a name="prerequisites"></a>Wymagania wstępne

Samouczek używa:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja
- [Przykładowy element docelowy debugowania — aplikacja internetowa](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) do wyzwolenia scenariusza
- [dotnet-Trace](dotnet-trace.md) do procesów list
- [dotnet-dump](dotnet-dump.md) do zbierania i analizowania pliku zrzutu

## <a name="core-dump-generation"></a>Generowanie zrzutu rdzeni

Aby zbadać czas braku odpowiedzi aplikacji, zrzut rdzenia lub zrzut pamięci umożliwia sprawdzenie stanu wątków i ewentualnych blokad, które mogą mieć problemy z rywalizacją. Uruchom [przykładową](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) aplikację do debugowania przy użyciu następującego polecenia z przykładowego katalogu głównego:

```dotnetcli
dotnet run
```

Aby znaleźć identyfikator procesu, użyj następującego polecenia:

```dotnetcli
dotnet-trace ps
```

Zanotuj identyfikator procesu z danych wyjściowych polecenia. Nasz identyfikator procesu został utworzony `4807` , ale będzie się różnić. Przejdź do następującego adresu URL, który jest punktem końcowym interfejsu API w witrynie przykładowej:

[https://localhost:5001/api/diagscenario/deadlock](https://localhost:5001/api/diagscenario/deadlock)

Żądanie interfejsu API do witryny zostanie zawieszone i nie będzie odpowiadać. Pozwól na uruchamianie żądania przez około 10-15 sekund. Następnie Utwórz zrzut rdzenia przy użyciu następującego polecenia:

### <a name="linux"></a>[Linux](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[Windows](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a>Analizowanie zrzutu rdzeni

Aby rozpocząć analizę podstawowego zrzutu, Otwórz zrzut rdzenia przy użyciu następującego `dotnet-dump analyze` polecenia. Argument jest ścieżką do głównego pliku zrzutu, który został zebrany wcześniej.

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

Ponieważ masz wrażenie potencjalnego zawieszenia, chcesz mieć ogólny wpływ na działanie wątku w procesie. Możesz użyć `threads` polecenia, jak pokazano poniżej:

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

W danych wyjściowych są wyświetlane wszystkie wątki aktualnie uruchomione w procesie ze skojarzonym IDENTYFIKATORem wątku debugera i IDENTYFIKATORem wątku systemu operacyjnego. Na podstawie danych wyjściowych jest ponad 300 wątków.

Następnym krokiem jest uzyskanie lepszych informacji o tym, co aktualnie robi wątki, pobierając stosu wywołań każdego wątku. `clrstack`Polecenie może służyć do wyprowadzania stosy wywołań. Może on wyprowadzać pojedyncze stosu wywołań lub wszystkie stosy wywołań. Użyj poniższego polecenia, aby wyprowadzić wszystkie stosy wywołań dla wszystkich wątków w procesie:

```console
clrstack -all
```

Reprezentatywna część danych wyjściowych wygląda następująco:

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

Obserwowanie stosy wywołań dla wszystkich ponad 300 wątków pokazuje wzorzec, w którym większość wątków współużytkuje wspólny stosu wywołań:

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

Stosu wywołań wydaje się, że żądanie dotarło do naszej metody zakleszczenia, która z kolei wywołuje wywołanie `Monitor.ReliableEnter` . Ta metoda wskazuje, że wątki próbują wprowadzić blokadę monitora. Czekają na dostępność blokady. Prawdopodobnie jest on zablokowany przez inny wątek.

Następnym krokiem jest znalezienie, który wątek rzeczywiście utrzymuje blokadę monitora. Ponieważ monitory zwykle przechowują informacje o blokowaniu w tabeli bloków synchronizacji, można użyć `syncblk` polecenia, aby uzyskać więcej informacji:

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

Dwie interesujące kolumny to **MonitorHeld** i **właściciel informacji o wątkach**. Kolumna **MonitorHeld** pokazuje, czy blokada monitora jest pobierana przez wątek i liczbę oczekujących wątków. Kolumna **Informacje o wątkach będących właścicielem** wskazuje, który wątek jest aktualnie właścicielem blokady monitora. Informacje o wątku mają trzy różne podkolumny. Druga Podkolumna zawiera identyfikator wątku systemu operacyjnego.

W tym momencie wiemy, że dwa różne wątki (0x5634 i 0x51d4) przechowują blokadę monitora. Następnym krokiem jest zaplanowanie działania tych wątków. Musimy sprawdzić, czy blokada nie jest zablokowana. Użyjmy `setthread` poleceń i, `clrstack` Aby przełączyć się do każdego z wątków i wyświetlić stosy wywołań.

Aby sprawdzić pierwszy wątek, uruchom `setthread` polecenie i Znajdź indeks wątku 0x5634 (nasz indeks to 28). Funkcja zakleszczenia oczekuje na uzyskanie blokady, ale jest już właścicielem blokady. Jest to zakleszczenie oczekujące na blokadę, która już się utrzymuje.

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

Drugi wątek jest podobny. Próbuje on również uzyskać blokadę, która jest już własnością. Pozostałe 300 wątków, które oczekują na to, najprawdopodobniej czekają na jedną z blokad, które spowodowały zakleszczenie.

## <a name="see-also"></a>Zobacz także

- [dotnet-Trace](dotnet-trace.md) do procesów list
- [dotnet-Counters](dotnet-counters.md) , aby sprawdzić użycie pamięci zarządzanej
- [dotnet-dump](dotnet-dump.md) aby zebrać i przeanalizować plik zrzutu
- [dotnet/Diagnostyka](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Jakie narzędzia diagnostyczne są dostępne w programie .NET Core](index.md)
