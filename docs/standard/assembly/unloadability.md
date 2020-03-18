---
title: Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core
description: Dowiedz się, jak używać kolekcjonowania AssemblyLoadContext do załadunku i zwalniania zarządzanych zestawów i jak debugować problemy uniemożliwiające powodzenie zwalniania.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159744"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core

Począwszy od .NET Core 3.0, możliwość załadowania, a później zwolnić zestaw zestawów jest obsługiwana. W ramach programu .NET Framework w tym celu użyto domen aplikacji niestandardowych, ale program .NET Core obsługuje tylko jedną domyślną domenę aplikacji.

.NET Core 3.0 i nowsze wersje obsługują rozładunek za pośrednictwem <xref:System.Runtime.Loader.AssemblyLoadContext>programu . Można załadować zestaw zestawów do kolekcji, `AssemblyLoadContext`wykonać w nich metody lub po prostu sprawdzić `AssemblyLoadContext`je za pomocą odbicia, a na koniec zwolnić . To zwalnia zespoły załadowane `AssemblyLoadContext`do pliku .

Istnieje jedna godna uwagi różnica między `AssemblyLoadContext` rozładunku przy użyciu i przy użyciu AppDomains. Z AppDomains rozładunku jest wymuszone. W czasie zwalniania wszystkie wątki uruchomione w docelowej appdomain są przerywane, zarządzane obiekty COM utworzone w docelowej AppDomain są niszczone i tak dalej. Z `AssemblyLoadContext`, rozładunek jest "spółdzielnia". Wywołanie <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> metody po prostu inicjuje rozładunku. Rozładunek kończy się po:

- Żadne wątki nie mają metod z `AssemblyLoadContext` zestawów załadowanych do ich stosów wywołań.
- Żaden z typów z zestawów załadowanych do `AssemblyLoadContext`, wystąpień tych typów, a same zestawy są przywoływane przez:
  - Odniesienia poza `AssemblyLoadContext`, z wyjątkiem<xref:System.WeakReference> słabych odniesień ( lub <xref:System.WeakReference%601>).
  - Silne uchwyty modułu odśmiecania pamięci (GCHandleType.Normal lub [GCHandleType.Pinned)](xref:System.Runtime.InteropServices.GCHandleType.Pinned)zarówno wewnątrz, jak i na zewnątrz pliku `AssemblyLoadContext`.[GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal)

## <a name="use-collectible-assemblyloadcontext"></a>Korzystanie z kolekcjonowania AssemblyLoadContext

Ta sekcja zawiera szczegółowy samouczek krok po kroku, który pokazuje prosty sposób `AssemblyLoadContext`załadowania aplikacji .NET Core do kolekcji, wykonać jej punkt wejścia, a następnie zwolnić go. Pełną próbkę można [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)znaleźć pod adresem .

### <a name="create-a-collectible-assemblyloadcontext"></a>Tworzenie kolekcjonowania AssemblyLoadContext

Musisz wyprowadzić swoją klasę <xref:System.Runtime.Loader.AssemblyLoadContext> z i <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> przeciążać jej metody. Ta metoda rozwiązuje odwołania do wszystkich zestawów, które są `AssemblyLoadContext`zależnościzestawów załadowanych do tego .

Poniższy kod jest przykładem najprostszego `AssemblyLoadContext`niestandardowego:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Jak widać, `Load` metoda zwraca `null`. Oznacza to, że wszystkie zestawy zależności są ładowane do kontekstu domyślnego, a nowy kontekst zawiera tylko zestawy jawnie załadowane do niego.

Jeśli chcesz załadować niektóre lub wszystkie zależności `AssemblyLoadContext` do zbyt, `AssemblyDependencyResolver` można `Load` użyć w tej metody. Określa `AssemblyDependencyResolver` nazwy zestawów do bezwzględnych ścieżek plików złożenia. Program rozpoznawania nazw używa plików pliku i zestawu *.deps.json* w katalogu głównego zestawu załadowanego do kontekstu.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Używanie niestandardowego elementu zestawu kolekcji AssemblyLoadContext

W tej sekcji przyjęto założenie, że używana jest prostsza `TestAssemblyLoadContext` wersja.

Można utworzyć wystąpienie niestandardowego `AssemblyLoadContext` i załadować do niego zestaw w następujący sposób:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Dla każdego z zestawów, do których odwołuje `TestAssemblyLoadContext.Load` się załadowany `TestAssemblyLoadContext` zespół, metoda jest wywoływana tak, aby można było zdecydować, skąd uzyskać zestaw. W naszym przypadku `null` zwraca, aby wskazać, że powinien być ładowany do domyślnego kontekstu z lokalizacji, które czas wykonywania używa do załadowania zestawów domyślnie.

Teraz, gdy zestaw został załadowany, można wykonać metodę z niego. Uruchom `Main` metodę:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Po `Main` zwróceniu metody można zainicjować rozładunku `Unload` przez wywołanie metody na niestandardowy `AssemblyLoadContext` lub `AssemblyLoadContext`pozbycie się odwołania masz do :

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Jest to wystarczające do rozładowania zespołu testowego. Let's rzeczywiście umieścić to wszystko w oddzielnym non-inlineable metody `MethodInfo` w `Assembly.EntryPoint`celu `TestAssemblyLoadContext`zapewnienia, że , `Assembly`i () nie mogą być utrzymywane przy życiu przez stos umiejscowienia (real- lub JIT wprowadzone mieszkańców). To może `TestAssemblyLoadContext` utrzymać przy życiu i zapobiec rozładunku.

Ponadto zwrócić słabe odwołanie `AssemblyLoadContext` do tak, aby można go użyć później do wykrywania zakończenia rozładunku.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Teraz można uruchomić tę funkcję, aby załadować, wykonać i zwolnić zespół.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Jednak rozładunek nie kończy się natychmiast. Jak wcześniej wspomniano, opiera się na moduł zbierający elementy bezużyteczne, aby zebrać wszystkie obiekty z zestawu testowego. W wielu przypadkach nie trzeba czekać na zakończenie rozładunku. Istnieją jednak przypadki, w których warto wiedzieć, że rozładunek został zakończony. Na przykład można usunąć plik zestawu, który został `AssemblyLoadContext` załadowany do niestandardowego z dysku. W takim przypadku można użyć następującego fragmentu kodu. Wyzwala wyrzucanie elementów bezużytecznych i czeka na oczekujące finalizatorów `AssemblyLoadContext` w `null`pętli, dopóki słabe odwołanie do niestandardowego jest ustawiona na , wskazując obiekt docelowy został zebrany. W większości przypadków wymagane jest tylko jedno przejście przez pętlę. Jednak w bardziej złożonych przypadkach, gdy obiekty `AssemblyLoadContext` utworzone przez kod uruchomiony w finalizatorów mają więcej przebiegów mogą być potrzebne.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Zdarzenie rozładunku

W niektórych przypadkach może być konieczne dla kodu `AssemblyLoadContext` załadowanego do niestandardowego do wykonania niektórych oczyszczania po zainicjowaniu rozładunku. Na przykład może być konieczne zatrzymanie wątków lub oczyszczenie silnych uchwytów GC. W `Unloading` takich przypadkach można wykorzystać zdarzenie. Program obsługi, który wykonuje niezbędne oczyszczania można podłączyć do tego zdarzenia.

### <a name="troubleshoot-unloadability-issues"></a>Rozwiązywanie problemów z rozładowaniem

Ze względu na kooperatywny charakter rozładunku, łatwo zapomnieć o referencjach, które mogą być utrzymanie rzeczy w kolekcjonowania `AssemblyLoadContext` żyje i zapobieganie rozładunku. Oto podsumowanie jednostek (niektóre z nich nieoczywiste), które mogą posiadać odniesienia:

- Regularne odwołania przechowywane spoza `AssemblyLoadContext` kolekcjonowania, które są przechowywane w gnieździe stosu lub rejestrze procesora (metoda locals, jawnie utworzone przez kod użytkownika lub niejawnie przez kompilator just-in-time (JIT), zmienną statyczną lub silne (przypinanie) gc uchwyt i przechodnie wskazując:
  - Zespół załadowany do `AssemblyLoadContext`kolekcji .
  - Typ z takiego złożenia.
  - Wystąpienie typu z takiego zestawu.
- Wątki uruchamiane kod z zestawu `AssemblyLoadContext`załadowany do kolekcjonowania .
- Wystąpienia niestandardowych typów niekolekcjonerskich `AssemblyLoadContext` utworzonych wewnątrz kolekcji `AssemblyLoadContext`.
- Oczekujące <xref:System.Threading.RegisteredWaitHandle> wystąpienia z wywołaniami zwrotu `AssemblyLoadContext`ustawiono na metody w niestandardowym pliku .

> [!TIP]
> Odwołania do obiektów, które są przechowywane w gniazdach stosu lub rejestrów procesora i które mogą zapobiec zwalnianiu może `AssemblyLoadContext` wystąpić w następujących sytuacjach:
>
> - Gdy wyniki wywołania funkcji są przekazywane bezpośrednio do innej funkcji, mimo że nie ma zmiennej lokalnej utworzonej przez użytkownika.
> - Gdy kompilator JIT przechowuje odwołanie do obiektu, który był dostępny w pewnym momencie w metodzie.

## <a name="debug-unloading-issues"></a>Problemy z rozładowaniem debugowania

Problemy z debugowaniem z rozładunkiem mogą być uciążliwe. Możesz dostać się do sytuacji, w których `AssemblyLoadContext` nie wiesz, co może być przy życiu, ale rozładunek nie powiedzie się. Najlepszą bronią do pomocy w tym jest WinDbg (LLDB na Unix) z pluginem SOS. Musisz znaleźć to, co `LoaderAllocator` utrzymuje przynależność do konkretnego `AssemblyLoadContext` żywcem. Wtyczka SOS pozwala spojrzeć na obiekty sterty GC, ich hierarchie i korzenie.

Aby załadować wtyczkę do debugera, wprowadź następujące polecenie w wierszu polecenia debugera:

W WinDbg (wydaje się, WinDbg robi to automatycznie po włamaniu się do aplikacji .NET Core):

```console
.loadby sos coreclr
```

W LLDB:

```console
plugin load /path/to/libsosplugin.so
```

Debugujmy przykładowy program, który ma problemy z rozładowywaniem. Kod źródłowy znajduje się poniżej. Po uruchomieniu go w obszarze WinDbg, program włamuje się do debugera zaraz po próbie sprawdzenia sukcesu rozładunku. Następnie możesz zacząć szukać winowajców.

> [!TIP]
> W przypadku debugowania przy użyciu LLDB w uniksie polecenia SOS `!` w poniższych przykładach nie mają przed nimi.

```console
!dumpheap -type LoaderAllocator
```

To polecenie zrzuca wszystkie obiekty `LoaderAllocator` o nazwie typu zawierającej, które znajdują się w stercie GC. Oto przykład:

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48
000002b78000ceb0 00007ffadc93a218       24

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

W części "Statystyki:" poniżej, `MT` `MethodTable`sprawdź ( `System.Reflection.LoaderAllocator`) należące do , który jest obiektem, na którym nam zależy. Następnie na liście na początku znajdź wpis `MT` z dopasowaniem tego i uzyskaj adres samego obiektu. W naszym przypadku jest to "000002b78000ce40".

Teraz, gdy znamy adres `LoaderAllocator` obiektu, możemy użyć innego polecenia, aby znaleźć jego korzenie GC:

```console
!gcroot -all 0x000002b78000ce40
```

To polecenie zrzuca łańcuch odwołań do `LoaderAllocator` obiektów, które prowadzą do wystąpienia. Lista zaczyna się od katalogu głównego, `LoaderAllocator` który jest jednostką, która utrzymuje naszą przy życiu, a tym samym jest sednem problemu. Katalog główny może być stosem, rejestrem procesora, uchwytem GC lub zmienną statyczną.

Oto przykład danych wyjściowych `gcroot` polecenia:

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

Następnym krokiem jest dowiedzieć się, gdzie znajduje się korzeń, dzięki czemu można go naprawić. Najprostszym przypadkiem jest, gdy korzeń jest gniazdo stosu lub rejestru procesora. W takim przypadku `gcroot` pokazuje nazwę funkcji, której ramka zawiera katalog główny i wątek wykonujący tę funkcję. Trudny przypadek jest, gdy korzeń jest zmienną statyczną lub gc uchwyt.

W poprzednim przykładzie pierwszy katalog główny jest `System.Reflection.RuntimeMethodInfo` lokalnym typu przechowywane `example.Program.Main(System.String[])` w `rbp-20` ramce funkcji na adres (`rbp` jest rejestr `rbp` procesora i -20 jest przesunięcie szesnastkowego z tego rejestru).

Drugi katalog główny jest normalne `GCHandle` (silne), który posiada `test.Test` odwołanie do wystąpienia klasy.

Trzeci korzeń jest `GCHandle`przypięty . Ten jest w rzeczywistości zmienną statyczną, ale niestety nie ma sposobu, aby powiedzieć. Statyka dla typów odwołań są przechowywane w tablicy obiektów zarządzanych w wewnętrznych strukturach wykonywania.

Innym przypadkiem, który może `AssemblyLoadContext` zapobiec rozładunku jest, gdy wątek ma `AssemblyLoadContext` ramkę metody z zestawu załadowany do jego stosu. Można sprawdzić, że przez dumpingu zarządzanych stosów wywołań wszystkich wątków:

```console
~*e !clrstack
```

Polecenie oznacza "zastosuj `!clrstack` do wszystkich wątków polecenie". Poniżej przedstawiono dane wyjściowe tego polecenia dla przykładu. Niestety, LLDB na Unix nie ma żadnego sposobu, aby zastosować polecenie do wszystkich wątków, `clrstack` więc należy ręcznie przełączyć wątki i powtórzyć polecenie. Ignoruj wszystkie wątki, w których debuger mówi "Nie można przejść przez zarządzany stos".

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998]
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28]
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0]
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568]
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0]

```

Jak widać, ostatni wątek `test.Program.ThreadProc()`ma . Jest to funkcja z zestawu `AssemblyLoadContext`załadowanego do , `AssemblyLoadContext` a więc utrzymuje przy życiu.

## <a name="example-source-with-unloadability-issues"></a>Przykładowe źródło z problemami z zwalnialnością

Poniższy kod jest używany w poprzednim przykładzie debugowania.

### <a name="main-testing-program"></a>Główny program testowy

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Program załadowany do modułu TestAssemblyLoadContext

Poniższy kod reprezentuje *test.dll* przekazany `ExecuteAndUnload` do metody w głównym programie testowym.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
