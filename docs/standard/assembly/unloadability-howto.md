---
title: Jak używać i debugować możliwość odciążania zestawów w programie .NET Core
description: Dowiedz się, jak używać programu AssemblyLoadContexte kolekcjonowane do ładowania i zwalniania zestawów zarządzanych oraz jak debugować problemy uniemożliwiające pomyślne wyładowywanie.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: a3ba2c2809aedd0af03ec965089f8779c430a335
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331523"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Jak używać i debugować możliwość odciążania zestawów w programie .NET Core

Począwszy od platformy .NET Core 3,0, możliwość załadowania i późniejszego zwolnienia zestawu zestawów jest obsługiwana. W tym celu w .NET Framework użyto niestandardowych domen aplikacji, ale program .NET Core obsługuje tylko jedną domyślną domenę aplikacji.

Program .NET Core 3,0 i jego nowsze wersje obsługują możliwości zwalniania w <xref:System.Runtime.Loader.AssemblyLoadContext>programie. Zestaw zestawów można załadować do `AssemblyLoadContext`w nich lub po prostu przeprowadzić ich kontrolę przy użyciu odbicia, a wreszcie `AssemblyLoadContext`Zwolnij. To zwalnia zestawy ładowane do tego `AssemblyLoadContext`.

Istnieje jedna istotna różnica między zwalnianiem przy `AssemblyLoadContext` użyciu i używania domen aplikacji. W przypadku domen aplikacji wyładowywanie jest wymuszane. W momencie zwolnienia wszystkie wątki działające w docelowej domenie aplikacji są przerywane, zarządzane obiekty COM utworzone w docelowej domenie aplikacji są niszczone itp. W `AssemblyLoadContext`przypadku, Unload to "spółdzielnie". <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> Wywołanie metody po prostu inicjuje zwolnienie. Zwalnianie kończy się po:

- Żadne wątki nie mają metod z zestawów załadowanych `AssemblyLoadContext` na stosy wywołań.
- Żaden z typów zestawów nie został załadowany do `AssemblyLoadContext`, wystąpienia tych typów i zestawy same poza `AssemblyLoadContext` nie są przywoływane przez:
  - Odwołania poza `AssemblyLoadContext`z, z wyjątkiem słabych odwołań (<xref:System.WeakReference> lub <xref:System.WeakReference%601>).
  - Mocne uchwyty GC<xref:System.Runtime.InteropServices.GCHandleType>(.<xref:System.Runtime.InteropServices.GCHandleType.Normal> lub <xref:System.Runtime.InteropServices.GCHandleType>)zarównowewnątrz,jakipoza.<xref:System.Runtime.InteropServices.GCHandleType.Pinned> `AssemblyLoadContext`

## <a name="using-collectible-assemblyloadcontext"></a>Korzystanie z AssemblyLoadContextów kolekcjonowanych

Ta sekcja zawiera szczegółowy samouczek krok po kroku, w którym przedstawiono prosty sposób ładowania aplikacji platformy .NET Core do elementu "kolekcjonowania `AssemblyLoadContext`", wykonywania jego punktu wejścia, a następnie jego zwolnienia. Kompletny przykład można znaleźć pod adresem <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.

### <a name="create-a-collectible-assemblyloadcontext"></a>Utwórz kolekcjonowaną AssemblyLoadContext

Należy utworzyć klasę z <xref:System.Runtime.Loader.AssemblyLoadContext> i przeciążyć jej <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodę. Ta metoda rozwiązuje odwołania do wszystkich zestawów, które są zależnościami zestawów ładowanych do `AssemblyLoadContext`tego elementu.
Poniższy kod jest przykładem najprostszego niestandardowego `AssemblyLoadContext`:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Jak widać, `Load` Metoda zwraca `null`. Oznacza to, że wszystkie zestawy zależności są ładowane do domyślnego kontekstu, a nowy kontekst zawiera tylko zestawy, które są w nim jawnie załadowane.

Jeśli chcesz załadować niektóre lub wszystkie zależności do tego `AssemblyLoadContext` , możesz `AssemblyDependencyResolver` użyć w `Load` metodzie. Program rozpoznaje nazwy zestawów dla bezwzględnych ścieżek plików zestawów przy użyciu pliku *. deps. JSON* zawartego w katalogu głównego zestawu załadowanym do kontekstu i przy użyciu plików zestawów w tym katalogu. `AssemblyDependencyResolver`

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Korzystanie z niestandardowego AssemblyLoadContextego kolekcjonowania

W tej sekcji założono, że prostsza `TestAssemblyLoadContext` wersja jest używana.

Można utworzyć wystąpienie niestandardowego `AssemblyLoadContext` i załadować do niego zestaw w następujący sposób:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Dla każdego z zestawów, do którego odwołuje się załadowany zestaw `TestAssemblyLoadContext.Load` , metoda jest wywoływana, aby `TestAssemblyLoadContext` można było określić miejsce, z którego ma zostać pobrany zestaw. W naszym przypadku zwraca wartość `null` wskazującą, że powinna zostać załadowana do domyślnego kontekstu z lokalizacji używanych przez środowisko uruchomieniowe do domyślnego ładowania zestawów.

Teraz, gdy zestaw został załadowany, można wykonać z niego metodę. `Main` Uruchom metodę:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Po powrocie `Unload` `AssemblyLoadContext` `AssemblyLoadContext`metody można zainicjować zwalnianie przez wywołanie metody na Custom lub pozbyć się odwołania do: `Main`

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Jest to wystarczające do zwolnienia zestawu testowego. W rzeczywistości przeniesiemy wszystkie te elementy do oddzielnej metody nieliniowej `TestAssemblyLoadContext`, aby upewnić się, że, `MethodInfo` `Assembly`i ( `Assembly.EntryPoint`) nie mogą być utrzymywane przez odwołania do gniazda stosu (wartości lokalne lub JIT). Może to prowadzić do `TestAssemblyLoadContext` utrzymania aktywności i uniemożliwić zwolnienie.

Należy również zwrócić słabe odwołanie do, `AssemblyLoadContext` aby można było użyć go później do wykrywania zakończenia zwalniania.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Teraz można uruchomić tę funkcję w celu załadowania, wykonania i zwolnienia zestawu.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Jednak zwalnianie nie zakończy się natychmiast. Jak wspomniano wcześniej, opiera się on na GC, aby zebrać wszystkie obiekty z zestawu testowego. W wielu przypadkach nie trzeba czekać na ukończenie zwalniania. Istnieją jednak przypadki, w których warto wiedzieć, że zwolnienie zostało zakończone. Na przykład możesz chcieć usunąć plik zestawu, który został załadowany do niestandardowego `AssemblyLoadContext` z dysku. W takim przypadku można użyć poniższego fragmentu kodu. Wyzwala on GC i czeka na oczekujące finalizatory w pętli do momentu, gdy słabe odwołanie do `AssemblyLoadContext` niego jest `null`ustawione na, co wskazuje na to, że obiekt docelowy został zebrany. Należy pamiętać, że w większości przypadków wymagane jest tylko jedno przejście przez pętlę. Jednak w przypadku bardziej złożonych przypadków, w których obiekty utworzone przez kod działający `AssemblyLoadContext` w programie mają finalizatory, może być konieczne wykonanie większej liczby przebiegów.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Zdarzenie wyładowywania

W niektórych przypadkach może być konieczne, aby kod został załadowany do niestandardowym `AssemblyLoadContext` w celu wykonania pewnego oczyszczania po zainicjowaniu zwalniania. Na przykład może być konieczne zatrzymanie wątków, oczyszczenie niektórych silnych dojść GC itd. W takich przypadkach można użyć zdarzenia.`Unloading` Do tego zdarzenia można podłączyć procedurę obsługi, która wykonuje wymagane oczyszczanie.

### <a name="troubleshoot-unloadability-issues"></a>Rozwiązywanie problemów z możliwością ponownego ładowania

Ze względu na spółdzielnię zwalniającą, można łatwo zapomnieć o odwołaniach, które ułatwiają odprowadzenie `AssemblyLoadContext` aktywności i uniemożliwiają zwolnienie. Poniżej znajduje się podsumowanie elementów (niektóre z nich nie są oczywiste), które mogą zawierać odwołania:

- Regularne odwołania przechowywane poza firmą kolekcjonowaną `AssemblyLoadContext`, przechowywaną w gnieździe stosu lub w rejestrze procesora (metody lokalne, jawnie utworzone przez kod użytkownika lub niejawnie przez JIT), zmiennej statycznej lub dojścia do usługi GC o silnej lub przypinaniu. przechodnie wskazywanie:
  - Zestaw załadowany do elementu "kolekcjonowane `AssemblyLoadContext`".
  - Typ z takiego zestawu.
  - Wystąpienie typu z takiego zestawu.
- Wątki uruchamiające kod z zestawu zostały załadowane do `AssemblyLoadContext`kolekcjonowania.
- Wystąpienia niestandardowych niekolekcjonowanych `AssemblyLoadContext` typów utworzonych wewnątrz elementu kolekcjonowanego`AssemblyLoadContext`
- Wystąpienia <xref:System.Threading.RegisteredWaitHandle> oczekujące z wywołaniami zwrotnymi ustawionymi na metody w niestandardowej`AssemblyLoadContext`

Wskazówki dotyczące znajdowania miejsca na stosie/rejestr procesora dla obiektu:

- Przekazywanie wyników wywołania funkcji bezpośrednio do innej funkcji może utworzyć katalog główny, nawet jeśli nie istnieje zmienna lokalna utworzona przez użytkownika.
- Jeśli odwołanie do obiektu było dostępne w dowolnym momencie w metodzie, kompilator JIT może postanowić o zachowaniu odwołania w gnieździe stosu/rejestrze procesora tak długo, jak w bieżącej funkcji.

## <a name="debug-unloading-issues"></a>Debuguj problemy z zwalnianiem

Problemy z debugowaniem z rozładowywaniem mogą być żmudnym. Możesz się dowiedzieć, gdzie nie wiesz, co może być `AssemblyLoadContext` utrzymywane, ale zwolnienie nie powiedzie się.
Najlepsza broń, która pomoże Ci to WinDbg (LLDB w systemie UNIX) z wtyczką SOS. Należy się dowiedzieć, co zachowuje `LoaderAllocator` się z konkretną `AssemblyLoadContext` aktywnością.
Ta wtyczka umożliwia przeglądanie obiektów sterty GC, ich hierarchii i katalogów głównych.
Aby załadować wtyczkę do debugera, wprowadź następujące polecenie w wierszu polecenia debugera:

W programie WinDbg (po załamaniu do aplikacji .NET Core) automatycznie

```console
.loadby sos coreclr
```

W LLDB:

```console
plugin load /path/to/libsosplugin.so
```

Spróbujmy debugować Przykładowy program, który ma problemy z wyładunkiem. Kod źródłowy jest uwzględniony poniżej. Gdy uruchamiasz go w ramach usługi WinDbg, program przerwie się w debugerze po podjęciu próby sprawdzenia powodzenia zwolnienia. Następnie można rozpocząć wyszukiwanie culprits.

Należy pamiętać, że jeśli debugujesz przy użyciu LLDB w systemie UNIX, polecenia sos w poniższych przykładach `!` nie mają przed nimi.

```console
!dumpheap -type LoaderAllocator
```

To polecenie zrzuca wszystkie obiekty o nazwie typu zawierającego `LoaderAllocator` te, które znajdują się w stercie GC. Oto przykład:

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

W poniższym składniku "Statistics:" Sprawdź `MT` (`MethodTable`) należący do `System.Reflection.LoaderAllocator`obiektu, który jest obiektem, którego potrzebujemy. Następnie na liście na początku Znajdź wpis ze zgodną z `MT` nim i uzyskaj adres samego obiektu. W naszym przypadku jest to "000002b78000ce40"

Teraz, gdy wiemy adres `LoaderAllocator` obiektu, możemy użyć innego polecenia, aby znaleźć jego elementy główne GC

```console
!gcroot -all 0x000002b78000ce40 
```

To polecenie zrzuca łańcuch odwołań do obiektów, które prowadzą do `LoaderAllocator` wystąpienia. Lista rozpoczyna się od elementu głównego, który jest obiektem, który utrzymuje `LoaderAllocator` naszą aktywność i w ten sposób stanowi rdzeń debugowanego problemu. Katalogiem głównym może być gniazdo stosu, rejestr procesora, dojście GC lub zmienna statyczna.

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

Teraz musisz ustalić, gdzie znajduje się katalog główny, aby można go było usunąć. Najłatwiejszym przypadkiem jest to, że katalog główny to gniazdo stosu lub rejestr procesora. W takim przypadku `gcroot` pokazuje nazwę funkcji, której ramka zawiera element główny i wątek wykonujący tę funkcję. Trudnym przypadkiem jest to, że element główny jest zmienną statyczną lub dojściem GC. 

W poprzednim przykładzie pierwszy element główny jest lokalnym typem `System.Reflection.RuntimeMethodInfo` przechowywanym w ramce funkcji `example.Program.Main(System.String[])` pod adresem `rbp-20` (`rbp` jest to rejestr `rbp` procesora i-20 to szesnastkowe przesunięcie z tego rejestru).

Drugi katalog główny to normalna (silna `GCHandle` ), która przechowuje odwołanie do wystąpienia `test.Test` klasy. 

Trzeci element główny jest przypięty `GCHandle`. Ten element jest w rzeczywistości zmienną statyczną. Niestety, nie ma możliwości poinformowania. Elementy statyczne dla typów referencyjnych są przechowywane w tablicy obiektów zarządzanych w wewnętrznych strukturach środowiska uruchomieniowego.

Innym przypadkiem, który może uniemożliwiać `AssemblyLoadContext` zwolnienie, jest, gdy wątek ma ramkę metody z zestawu załadowanego `AssemblyLoadContext` do obiektu na jego stosie. Można sprawdzić, czy są używane stosy wywołań zarządzanych wszystkich wątków:

```console
~*e !clrstack
```

Polecenie oznacza "Zastosuj do wszystkich wątków `!clrstack` polecenia". Poniżej znajduje się dane wyjściowe tego polecenia dla przykładu. Niestety, LLDB w systemie UNIX nie ma żadnego sposobu, aby zastosować polecenie do wszystkich wątków, więc musisz ręcznie przełączać wątki i powtarzać `clrstack` polecenie.
Ignoruj wszystkie wątki, w których ten debuger brzmi "nie można przeprowadzić zarządzanego stosu".

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

Jak widać, ostatni wątek ma `test.Program.ThreadProc()`. Jest to funkcja z zestawu `AssemblyLoadContext`, która została załadowana do, i dlatego `AssemblyLoadContext` utrzymuje aktywności.

## <a name="example-source-with-unloadability-issues"></a>Przykładowe źródło z problemami z możliwością załadowania

Poniższy kod jest używany w poprzednim przykładzie debugowania.

### <a name="main-testing-program"></a>Główny program do testowania

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Program został załadowany do TestAssemblyLoadContext

Poniższy kod reprezentuje `test.dll` przekazaną `ExecuteAndUnload` do metody w głównym programie testowym.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
