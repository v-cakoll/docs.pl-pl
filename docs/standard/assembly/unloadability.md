---
title: Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core
description: Dowiedz się, jak używać programu AssemblyLoadContexte kolekcjonowane do ładowania i zwalniania zestawów zarządzanych oraz jak debugować problemy uniemożliwiające pomyślne wyładowywanie.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 462e6d2c7f135d2ba274d78fe31ad27391eac416
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740448"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core

Począwszy od platformy .NET Core 3,0, możliwość załadowania i późniejszego zwolnienia zestawu zestawów jest obsługiwana. W tym celu w .NET Framework użyto niestandardowych domen aplikacji, ale program .NET Core obsługuje tylko jedną domyślną domenę aplikacji.

Program .NET Core 3,0 i jego nowsze wersje obsługują możliwości zwalniania za pomocą <xref:System.Runtime.Loader.AssemblyLoadContext>. Można załadować zestaw zestawów do `AssemblyLoadContext`kolekcjonowanych, wykonać metody w nich lub po prostu sprawdzić je przy użyciu odbicia, a następnie zwolnić `AssemblyLoadContext`. To zwalnia zestawy ładowane do `AssemblyLoadContext`.

Istnieje jedna istotna różnica między rozładunkiem przy użyciu `AssemblyLoadContext` i używania domen aplikacji. W przypadku domen aplikacji wyładowywanie jest wymuszane. W czasie zwalniania wszystkie wątki działające w docelowej domenie AppDomain są przerywane, zarządzane obiekty COM utworzone w docelowej domenie AppDomain są niszczone i tak dalej. W przypadku `AssemblyLoadContext`Unload to "spółdzielnie". Wywołanie metody <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> po prostu inicjuje zwolnienie. Zwalnianie kończy się po:

- Żadne wątki nie mają metod z zestawów załadowanych do `AssemblyLoadContext` na ich stosach wywołań.
- Żaden z typów zestawów nie został załadowany do `AssemblyLoadContext`, wystąpienia tych typów i same zestawy są przywoływane przez:
  - Odwołania poza `AssemblyLoadContext`, z wyjątkiem słabych odwołań (<xref:System.WeakReference> lub <xref:System.WeakReference%601>).
  - Dojścia silnego modułu wyrzucania elementów bezużytecznych (GC) ([GCHandleType. Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) lub [GCHandleType. przypięto](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) zarówno wewnątrz, jak i na zewnątrz `AssemblyLoadContext`.

## <a name="use-collectible-assemblyloadcontext"></a>Użyj AssemblyLoadContextów kolekcjonowanych

Ta sekcja zawiera szczegółowy samouczek krok po kroku, który pokazuje prosty sposób ładowania aplikacji .NET Core do `AssemblyLoadContext`ej kolekcjonowanej, wykonywania punktu wejścia, a następnie zwalniania go. Kompletny przykład można znaleźć w [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).

### <a name="create-a-collectible-assemblyloadcontext"></a>Utwórz kolekcjonowaną AssemblyLoadContext

Należy utworzyć klasę z <xref:System.Runtime.Loader.AssemblyLoadContext> i przeciążyć jej metodę <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>. Ta metoda rozwiązuje odwołania do wszystkich zestawów, które są zależnościami od zestawów ładowanych do tego `AssemblyLoadContext`.

Poniższy kod jest przykładem najprostszego `AssemblyLoadContext`niestandardowego:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Jak widać, Metoda `Load` zwraca `null`. Oznacza to, że wszystkie zestawy zależności są ładowane do domyślnego kontekstu, a nowy kontekst zawiera tylko zestawy, które są w nim jawnie załadowane.

Jeśli chcesz załadować niektóre lub wszystkie zależności do `AssemblyLoadContext`, możesz użyć `AssemblyDependencyResolver` w metodzie `Load`. `AssemblyDependencyResolver` rozwiązuje nazwy zestawów do bezwzględnych ścieżek plików zestawów. Mechanizm rozwiązywania konfliktów używa pliku *. deps. JSON* i plików zestawów w katalogu głównym zestawu załadowanym do kontekstu.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Korzystanie z niestandardowego AssemblyLoadContextego kolekcjonowania

W tej sekcji założono, że prostsza wersja `TestAssemblyLoadContext` jest używana.

Można utworzyć wystąpienie `AssemblyLoadContext` niestandardowego i załadować do niego zestaw w następujący sposób:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Dla każdego z zestawów, do którego odwołuje się załadowany zestaw, wywoływana jest metoda `TestAssemblyLoadContext.Load`, aby `TestAssemblyLoadContext` mógł zdecydować, skąd ma zostać pobrany zestaw. W naszym przypadku zwraca `null`, aby wskazać, że powinien zostać załadowany do domyślnego kontekstu z lokalizacji używanych przez środowisko uruchomieniowe do domyślnego ładowania zestawów.

Teraz, gdy zestaw został załadowany, można wykonać z niego metodę. Uruchom metodę `Main`:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Po powrocie metody `Main` można zainicjować zwalnianie, wywołując metodę `Unload` na niestandardowym `AssemblyLoadContext` lub pozbyć się odwołania do `AssemblyLoadContext`:

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Jest to wystarczające do zwolnienia zestawu testowego. W rzeczywistości przeniesiemy wszystkie te elementy do oddzielnej metody nieliniowej, aby upewnić się, że `TestAssemblyLoadContext`, `Assembly`i `MethodInfo` (`Assembly.EntryPoint`) nie mogą być utrzymywane przez odwołania do miejsca na stosie (dane lokalne w języku rzeczywistym lub JIT). Może to spowodować, że `TestAssemblyLoadContext` działa i uniemożliwia zwolnienie.

Należy również zwrócić słabe odwołanie do `AssemblyLoadContext`, aby można było użyć go później do wykrywania zakończenia zwalniania.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Teraz można uruchomić tę funkcję w celu załadowania, wykonania i zwolnienia zestawu.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Jednak zwalnianie nie zakończy się natychmiast. Jak wspomniano wcześniej, polega na wykorzystaniu modułu wyrzucania elementów bezużytecznych w celu zebrania wszystkich obiektów z zestawu testowego. W wielu przypadkach nie trzeba czekać na ukończenie zwalniania. Istnieją jednak przypadki, w których warto wiedzieć, że zwolnienie zostało zakończone. Na przykład możesz chcieć usunąć plik zestawu, który został załadowany do `AssemblyLoadContext` niestandardowego z dysku. W takim przypadku można użyć poniższego fragmentu kodu. Wyzwala wyrzucanie elementów bezużytecznych i oczekuje na oczekujące finalizatory w pętli do momentu, gdy słabe odwołanie do `AssemblyLoadContext` niestandardowego zostanie ustawione na `null`, co wskazuje na to, że obiekt docelowy został zebrany. W większości przypadków wymagane jest tylko jedno przejście przez pętlę. Jednak w przypadku bardziej złożonych przypadków, gdy obiekty utworzone za pomocą kodu uruchomionego w `AssemblyLoadContext` mają finalizatory, może być konieczne wykonanie większej liczby przebiegów.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Zdarzenie wyładowywania

W niektórych przypadkach może być konieczne, aby kod został załadowany do niestandardowego `AssemblyLoadContext`, aby przeprowadzić oczyszczanie po zainicjowaniu zwalniania. Na przykład może być konieczne zatrzymanie wątków lub oczyszczenie silnych dojść GC. W takich przypadkach można użyć zdarzenia `Unloading`. Do tego zdarzenia można podłączyć procedurę obsługi, która wykonuje wymagane oczyszczanie.

### <a name="troubleshoot-unloadability-issues"></a>Rozwiązywanie problemów z możliwością ponownego ładowania

Ze względu na spółdzielnię zwalniającą, można łatwo zapomnieć o odwołaniach, które mogą mieć na celu przechowywanie `AssemblyLoadContext` aktywności i zapobiegania zwolnieniu. Poniżej znajduje się podsumowanie jednostek (niektóre z nich nie są oczywiste), które mogą zawierać odwołania:

- Regularne odwołania przechowywane z zewnątrz kolekcjonowanych `AssemblyLoadContext` przechowywanych w gnieździe stosu lub w rejestrze procesora (metody lokalne, jawnie utworzone przez kod użytkownika lub niejawnie przez kompilator just-in-Time (JIT), zmienna statyczna lub silne ( Przypinanie do uchwytu GC i przechodnie wskazywanie:
  - Zestaw załadowany do `AssemblyLoadContext`u kolekcjonowanego.
  - Typ z takiego zestawu.
  - Wystąpienie typu z takiego zestawu.
- Wątki uruchamiające kod z zestawu załadowanego do `AssemblyLoadContext`kolekcjonowania.
- Wystąpienia niestandardowych, niekolekcjonowanych typów `AssemblyLoadContext` utworzonych wewnątrz `AssemblyLoadContext`kolekcjonowanych.
- Oczekujące wystąpienia <xref:System.Threading.RegisteredWaitHandle> z wywołaniami zwrotnymi ustawionymi na metody w `AssemblyLoadContext`niestandardowym.

> [!TIP]
> Odwołania do obiektów, które są przechowywane w gniazdach stosu lub rejestrach procesora i mogą uniemożliwiać zwolnienie `AssemblyLoadContext` mogą wystąpić w następujących sytuacjach:
>
> - Gdy wyniki wywołań funkcji są przesyłane bezpośrednio do innej funkcji, nawet jeśli nie istnieje zmienna lokalna utworzona przez użytkownika.
> - Gdy kompilator JIT przechowuje odwołanie do obiektu, który był dostępny w pewnym momencie w metodzie.

## <a name="debug-unloading-issues"></a>Debuguj problemy z zwalnianiem

Problemy z debugowaniem z rozładowywaniem mogą być żmudnym. Możesz przejść do sytuacji, w których nie wiesz, co może być utrzymywane w `AssemblyLoadContext` aktywności, ale zwalnianie kończy się niepowodzeniem. Najlepsza broń, która pomoże Ci to WinDbg (LLDB w systemie UNIX) z wtyczką SOS. Należy się dowiedzieć, co zachowuje `LoaderAllocator` należące do konkretnej `AssemblyLoadContext` aktywności. Wtyczka SOS umożliwia przeglądanie obiektów sterty GC, ich hierarchii i katalogów głównych.

Aby załadować wtyczkę do debugera, wprowadź następujące polecenie w wierszu polecenia debugera:

W programie WinDbg (po załamaniu do aplikacji .NET Core) automatycznie

```console
.loadby sos coreclr
```

W LLDB:

```console
plugin load /path/to/libsosplugin.so
```

Debugujmy Przykładowy program, który ma problemy z wyładunkiem. Kod źródłowy jest uwzględniony poniżej. Gdy uruchamiasz go w ramach usługi WinDbg, program przerwie się w debugerze po podjęciu próby sprawdzenia powodzenia zwolnienia. Następnie można rozpocząć wyszukiwanie culprits.

> [!TIP]
> Jeśli debugujesz przy użyciu LLDB w systemie UNIX, polecenia SOS w poniższych przykładach nie mają `!` przed nimi.

```console
!dumpheap -type LoaderAllocator
```

To polecenie zrzuca wszystkie obiekty o nazwie typu zawierającego `LoaderAllocator`, które znajdują się na stercie GC. Oto przykład:

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

W poniższym składniku "Statistics:" Sprawdź `MT` (`MethodTable`) należących do `System.Reflection.LoaderAllocator`, który jest obiektem, którego potrzebujemy. Następnie na liście na początku Znajdź wpis z `MT` pasującym do tego samego obiektu i uzyskaj adres samego samego siebie. W naszym przypadku jest to "000002b78000ce40".

Teraz, gdy wiemy, że znasz adres `LoaderAllocator` obiektu, można użyć innego polecenia, aby znaleźć jego elementy główne GC:

```console
!gcroot -all 0x000002b78000ce40
```

To polecenie zrzuca łańcuch odwołań do obiektów, które prowadzą do wystąpienia `LoaderAllocator`. Lista rozpoczyna się od elementu głównego, który jest jednostką, która utrzymuje `LoaderAllocator` aktywności i w ten sposób stanowi rdzeń problemu. Katalogiem głównym może być gniazdo stosu, rejestr procesora, dojście GC lub zmienna statyczna.

Oto przykład danych wyjściowych polecenia `gcroot`:

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

Następnym krokiem jest określenie, gdzie znajduje się katalog główny, aby można go było usunąć. Najłatwiejszym przypadkiem jest to, że katalog główny to gniazdo stosu lub rejestr procesora. W takim przypadku `gcroot` wyświetla nazwę funkcji, której ramka zawiera element główny i wątek wykonujący tę funkcję. Trudnym przypadkiem jest to, że element główny jest zmienną statyczną lub dojściem GC.

W poprzednim przykładzie pierwszy element główny jest lokalnym typem `System.Reflection.RuntimeMethodInfo` przechowywanym w ramce `example.Program.Main(System.String[])` funkcji pod adresem `rbp-20` (`rbp` jest rejestrem procesora `rbp` i-20 to szesnastkowe przesunięcie z tego rejestru).

Drugi katalog główny to normalna (silna) `GCHandle`, która przechowuje odwołanie do wystąpienia klasy `test.Test`.

Trzeci katalog główny jest przypięty `GCHandle`. Ten element jest w rzeczywistości zmienną statyczną, ale niestety, nie ma możliwości poinformowania. Elementy statyczne dla typów referencyjnych są przechowywane w tablicy obiektów zarządzanych w wewnętrznych strukturach środowiska uruchomieniowego.

Innym przypadkiem, który może uniemożliwić wyładowywanie `AssemblyLoadContext`, jest to, kiedy wątek ma ramkę metody z zestawu załadowanego do `AssemblyLoadContext` na jego stosie. Można sprawdzić, czy są używane stosy wywołań zarządzanych wszystkich wątków:

```console
~*e !clrstack
```

Polecenie oznacza "Zastosuj do wszystkich wątków `!clrstack` polecenie". Poniżej znajduje się dane wyjściowe tego polecenia dla przykładu. Niestety, LLDB w systemie UNIX nie ma żadnego sposobu zastosowania polecenia do wszystkich wątków, więc musisz ręcznie przełączać wątki i powtórzyć `clrstack` polecenie. Ignoruj wszystkie wątki, w których debuger "nie może przeprowadzić zarządzanego stosu".

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

Jak widać, ostatni wątek ma `test.Program.ThreadProc()`. Jest to funkcja z zestawu, która została załadowana do `AssemblyLoadContext`i dlatego utrzymuje `AssemblyLoadContext` aktywności.

## <a name="example-source-with-unloadability-issues"></a>Przykładowe źródło z problemami z możliwością załadowania

Poniższy kod jest używany w poprzednim przykładzie debugowania.

### <a name="main-testing-program"></a>Główny program do testowania

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Program został załadowany do TestAssemblyLoadContext

Poniższy kod przedstawia *test. dll* przekazaną do metody `ExecuteAndUnload` w głównym programie testowym.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
