---
title: Sposób użycia i debugować unloadability zestawu w programie .NET Core
description: Dowiedz się, jak używać kolekcjonowane AssemblyLoadContext zarządzane zestawy, ładowanie i zwalnianie i jak debugować problemy, zapobiegając powodzeniu zwalnianie.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 2929110952feb0913f21a9c69975cc605f49c646
ms.sourcegitcommit: a532e8314c3a4b5b039656567fedff9787a31957
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251487"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Sposób użycia i debugować unloadability zestawu w programie .NET Core

Począwszy od .NET Core 3.0 to możliwość ładowanie i zwalnianie później zbiór zestawów jest obsługiwane. W programie .NET Framework domen niestandardowych aplikacji zostały użyte w tym celu, ale program .NET Core obsługuje tylko jednej domyślnej domeny aplikacji.

.NET core 3.0 i nowsze wersje obsługują unloadability za pośrednictwem <xref:System.Runtime.Loader.AssemblyLoadContext>. Możesz załadować zbiór zestawów, do kolekcjonowane `AssemblyLoadContext`, wykonywanie metod w nich lub po prostu je sprawdzić przy użyciu odbicia, a na koniec Zwolnij `AssemblyLoadContext`. Zwalnia, zestawy, ładowane `AssemblyLoadContext`.

Brak warte zauważenia różnicy usuwaniu z niej za pomocą `AssemblyLoadContext` i używanie domen aplikacji. Zwalnianie jest wymuszone za pomocą domen aplikacji. W czasie Zwolnij wszystkie wątki uruchomione w docelowej domenie aplikacji zostało przerwane, zarządzanych obiektów COM, utworzone w docelowej domeny aplikacji są niszczone, itp. Za pomocą `AssemblyLoadContext`, zwolnij jest "wspólne". Wywoływanie <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> metoda po prostu inicjuje zwolnienie. Zwalnianie zostanie zakończone po:

- Żadne wątki nie mają metod z zestawy, ładowane `AssemblyLoadContext` na ich stosy wywołań.
- Żaden z typów z zestawy ładowane `AssemblyLoadContext`, wystąpień tych typów i zestawy, samodzielnie poza `AssemblyLoadContext` są przywoływane przez:
  - Odwołuje się poza `AssemblyLoadContext`, z wyjątkiem słabe odwołania (<xref:System.WeakReference> lub <xref:System.WeakReference%601>).
  - Uchwyty silne GC (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal> lub <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) z obu wewnątrz lub poza `AssemblyLoadContext`.

## <a name="using-collectible-assemblyloadcontext"></a>Za pomocą AssemblyLoadContext kolekcjonowane

Ta sekcja zawiera szczegółowy samouczek krok po kroku, który pokazuje prosty sposób ładowania aplikacji .NET Core kolekcjonowane `AssemblyLoadContext`, wykonaj jego punktu wejścia, a następnie zwolnienia. Możesz znaleźć pełny przykład o <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.

### <a name="create-a-collectible-assemblyloadcontext"></a>Tworzenie AssemblyLoadContext kolekcjonowane

Muszą pochodzić z klasy <xref:System.Runtime.Loader.AssemblyLoadContext> i przeciążenia jego <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metody. Czy metoda jest rozpoznawana jako odwołania do wszystkich zestawów, które zależności zestawów są ładowane, które `AssemblyLoadContext`.
Poniższy kod jest przykładem najprostszym niestandardowe `AssemblyLoadContext`:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Jak widać, `Load` metoda zwraca `null`. Oznacza to, że wszystkie zespoły zależności są ładowane w kontekście domyślnym, a nowy kontekst zawiera tylko zestawy jawnie załadowane do niego.

Jeśli chcesz załadować niektóre lub wszystkie zależności do `AssemblyLoadContext` , możesz użyć `AssemblyDependencyResolver` w `Load` metody. `AssemblyDependencyResolver` Jest rozpoznawany jako nazwy zestawów zestawu bezwzględnej ścieżki plików przy użyciu `*.deps.json` pliku znajdującego się w katalogu głównym zestawie ładowane do kontekstu i korzystanie z zestawu plików, w tym katalogu.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Użyj niestandardowego AssemblyLoadContext kolekcjonowane

W tej sekcji założono prostszej wersji `TestAssemblyLoadContext` jest używana.

Można utworzyć wystąpienia niestandardowego `AssemblyLoadContext` i załadować zestawu do niego w następujący sposób:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Dla każdego zestawy przywoływane przez załadowany zestaw `TestAssemblyLoadContext.Load` metoda jest wywoływana, aby `TestAssemblyLoadContext` zdecydować, gdzie można pobrać zestawu z. W naszym przypadku zwraca `null` do wskazania, że jej powinny być załadowane do domyślnego kontekstu z lokalizacji, używanych przez środowisko uruchomieniowe ładować zestawy domyślnie.

Teraz, że zestaw został załadowany, można wykonać metody z niego. Uruchom `Main` metody:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Po `Main` metoda zwróci wartość, możesz zainicjować zwalnianie za pośrednictwem dowolnego wywołania `Unload` metody na niestandardowej `AssemblyLoadContext` lub pozbycia się odwołania trzeba `AssemblyLoadContext`:

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Jest to wystarczające zwolnić zestaw testowy. Faktycznie umieśćmy wszystko to w oddzielnych metodach inlineable, aby upewnić się, że `TestAssemblyLoadContext`, `Assembly`, i `MethodInfo` ( `Assembly.EntryPoint`) nie może utrzymywać ich aktywność stosu miejsca odwołania (zmiennych lokalnych wprowadzone rzeczywistym lub JIT). Można zachować `TestAssemblyLoadContext` aktywności i zapobiec zwolnienia.

Ponadto Zwróć słabe odwołanie do `AssemblyLoadContext` tak, aby można było jej użyć później do wykrycia ukończenia zwolnienia.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Teraz możesz uruchamiać tę funkcję, aby załadować, wykonywanie i zwolnić zestaw.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Jednak zwolnienie nie wykona natychmiast. Jak wspomniano wcześniej opiera się na GC, aby zbierać wszystkie obiekty z zestawu testowego. W wielu przypadkach nie trzeba czekać na ukończenie zwolnienia. Jednak istnieją przypadki, w których warto wiedzieć, że zwolnienie została zakończona. Na przykład, można usunąć pliku zestawu, który został załadowany do niestandardowej `AssemblyLoadContext` z dysku. W takim przypadku służy poniższy fragment kodu. Wyzwala wykazem Globalnym i czeka na oczekujące finalizatory w pętli do momentu słabe odwołanie do niestandardowej `AssemblyLoadContext` ustawiono `null`, wskazujące obiekt docelowy został zebrany. Należy zauważyć, że tylko jeden przebieg za pomocą pętli w większości przypadków jest wymagane. Jednak w przypadku bardziej złożonych przypadkach, w których obiekty są tworzone przez kod uruchomiony w `AssemblyLoadContext` mają finalizatory, może być wymagane więcej przebiegów.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Zwalnianie zdarzenia

W niektórych przypadkach może być konieczne dla kodu załadowane do niestandardowego `AssemblyLoadContext` do wykonania niektórych oczyszczania po zainicjowaniu zwolnienie. Na przykład może wymagać zatrzymać wątków, czyszczenie niektóre silne uchwyty GC itp. `Unloading` Zdarzenia mogą być używane w takich przypadkach. Program obsługi, który wykonuje niezbędne czyszczenia mogą być dołączane do tego zdarzenia.

### <a name="troubleshoot-unloadability-issues"></a>Rozwiązywanie problemów unloadability

Ze względu na charakter współpracy rozładowania, to można łatwo zapomnieć o odwołaniach do pamiętając zebrać kolekcjonowane `AssemblyLoadContext` aktywności i zapobieganie zwolnienia. Poniżej przedstawiono podsumowanie elementów (niektóre z nich nie jest oczywisty), jaką może zawierać odwołania:

- Odwołania do regularnego przechowywane z poza kolekcjonowane `AssemblyLoadContext`, przechowywanych w miejsca na stosie lub rejestrze procesora (metoda zmiennych lokalnych, albo jawnie tworzone przez kod użytkownika, albo niejawnie przez kompilator JIT), zmienna statyczna lub uchwyt GC silne / przypinania, i Wskazuje sposób przechodni:
  - Zestaw jest ładowany do kolekcjonowane `AssemblyLoadContext`.
  - Typ z takiego zestawu.
  - Wystąpienie typu z takiego zestawu.
- Wątki uruchamiania kodu z zestawu, o których ładowane kolekcjonowane `AssemblyLoadContext`.
- Wystąpienia elementu niestandardowego kolekcjonowane `AssemblyLoadContext` typy utworzone wewnątrz kolekcjonowane `AssemblyLoadContext`
- Oczekujące <xref:System.Threading.RegisteredWaitHandle> wystąpień przy użyciu wywołania zwrotne równa metod w niestandardowej `AssemblyLoadContext`

Wskazówki można znaleźć miejsca na stosie / procesora register zakorzenienia obiektu:

- Przekazywanie wywołanie funkcji wyniki bezpośrednio do innej funkcji może utworzyć katalog główny, nawet jeśli nie jest zmienna lokalna nie utworzone przez użytkownika.
- Jeśli odwołanie do obiektu była dostępna w dowolnym momencie w metodzie, kompilator JIT może zdecydował się utrzymywać odwołania w gnieździe stosu / procesora Zarejestruj się, aby tak długo, jak należy utworzyć w bieżącej funkcji.

## <a name="debug-unloading-issues"></a>Debugowanie problemów zwalnianie

Debugowanie problemów z zwalnianie może być żmudne. Możesz znaleźć się w sytuacjach, w których nie wiesz, co może być zawierający `AssemblyLoadContext` aktywne, ale Zwolnij kończy się niepowodzeniem.
Najlepsze broń pomoże Ci, jest WinDbg (LLDB w systemach Unix) za pomocą wtyczki SOS. Należy określić, co może być utrzymywanie `LoaderAllocator` należące do konkretnej `AssemblyLoadContext` podtrzymywania połączenia.
Ta wtyczka umożliwia Spójrz na obiektach sterty GC, hierarchie i katalogi główne.
Aby załadować wtyczkę do debugera, wprowadź następujące polecenie w wierszu polecenia debugera:

W WinDbg (prawdopodobnie WinDbg robi to w automatycznie przy okazji do aplikacji .NET Core):

```console
.loadby sos coreclr
```

W LLDB:

```console
plugin load /path/to/libsosplugin.so
```

Spróbujmy przykładowy program, który ma problemy z zwalnianie debugowania. Kod źródłowy znajduje się poniżej. Po uruchomieniu go w obszarze WinDbg program dzieli się na debuger po prawej stronie po próby sprawdzenia w celu osiągnięcia sukcesu zwolnienia. Możesz następnie rozpocząć wyszukiwanie sprawcami.

Należy pamiętać, że w przypadku debugowania za pomocą LLDB w systemach Unix, nie ma poleceń SOS w poniższych przykładach `!` przed nimi.

```console
!dumpheap -type LoaderAllocator
```

To polecenie zrzuca wszystkie obiekty z zawierający nazwę typu `LoaderAllocator` znajdujących się w stercie GC. Oto przykład:

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

W "statystyki:" wchodzi w skład poniżej wyboru `MT` (`MethodTable`) należące do `System.Reflection.LoaderAllocator`, który jest obiektem Dbamy o. Następnie na liście na początku, znajdź wpis o `MT` dopasowanie ten. i Uzyskaj adres samego obiektu. W naszym przypadku jest "000002b78000ce40"

Teraz, gdy wiemy adres `LoaderAllocator` obiektu, możemy użyć innego polecenia, aby znaleźć korzenie jego GC

```console
!gcroot -all 0x000002b78000ce40 
```

To polecenie zrzuca łańcuch odwołania do obiektów, które mogą prowadzić do `LoaderAllocator` wystąpienia. Lista zaczyna się od katalogu głównego, który jest obiektem, który utrzymuje naszych `LoaderAllocator` aktywny i w związku z tym to podstawowe rozwiązanie problemu debugowania. Katalog główny może być miejsca na stosie, rejestrze procesora, uchwyt GC lub zmienna statyczna.

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

Teraz należy ustalić, której głównym znajduje się więc można go naprawić. Najprostszym przypadku to główny miejsca na stosie lub rejestrze procesora. W takim przypadku `gcroot` Wyświetla nazwę funkcji, w których ramka nie zawiera katalog główny i wątek wykonywania tej funkcji. Tak trudne jest, gdy katalog główny jest zmienna statyczna lub uchwyt GC. 

W poprzednim przykładzie pierwszy katalog główny jest lokalne o typie `System.Reflection.RuntimeMethodInfo` przechowywane w ramce funkcja `example.Program.Main(System.String[])` pod adresem `rbp-20` (`rbp` jest rejestrze procesora `rbp` i -20 jest szesnastkowe przesunięcie z tego rejestru).

Drugi katalog główny jest jako normalny (silną) `GCHandle` zawierający odwołanie do wystąpienia `test.Test` klasy. 

Trzeci główny jest przypięty `GCHandle`. Ten zestaw jest faktycznie zmienną statyczną. Niestety nie ma możliwości mówić. Danych statycznych dla typów odwołania są przechowywane w tablicy obiektu zarządzanego w strukturach wewnętrznego środowiska uruchomieniowego.

Inny przypadek, które mogą uniemożliwić zwalniania `AssemblyLoadContext` , gdy wątek ma ramkę metodę z zestawu załadowaniu do `AssemblyLoadContext` na swój stos. Aby sprawdzić, czy przez zrzucanie zarządzane stosy wywołań wszystkich wątków:

```console
~*e !clrstack
```

Oznacza, że polecenie "Zastosuj do wszystkich wątków `!clrstack` polecenia". Oto dane wyjściowe tego polecenia dla przykładu. Niestety, LLDB w systemach Unix nie ma żadnego sposobu zastosowanie polecenia do wszystkich wątków, więc należy odwołać się do ręcznego przełączania wątków i powtórzenie `clrstack` polecenia.
Ignoruj wszystkich wątków, w której debuger jest wyświetlany komunikat "Niemożliwości zapoznaj się z zarządzanego stosu."

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

Jak widać, ostatni wątek ma `test.Program.ThreadProc()`. Jest to funkcja z zestawu ładowany `AssemblyLoadContext`, i dlatego zapewnia `AssemblyLoadContext` podtrzymywania połączenia.

## <a name="example-source-with-unloadability-issues"></a>Przykładowe źródła z problemami unloadability

Poniższy kod jest używany w poprzednim przykładzie debugowania.

### <a name="main-testing-program"></a>Główny program testowania

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Program ładowany TestAssemblyLoadContext

Poniższy kod przedstawia `test.dll` przekazany do `ExecuteAndUnload` metody w głównym program testów.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
