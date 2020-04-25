---
title: Wytyczne dotyczące użycia struktur Memory<T> i Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: b89969f212da6ac90d0fb0d1bf388626e136b92e
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158596"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Wytyczne dotyczące użycia struktur Memory\<T > i Span\<T>

Platforma .NET Core zawiera wiele typów, które reprezentują dowolny ciągły region pamięci. Wdrożono <xref:System.Span%601> program .net core <xref:System.ReadOnlySpan%601>2,0 i są to lekkie bufory pamięci, które mogą być obsługiwane przez pamięć zarządzaną lub niezarządzaną. Ponieważ te typy mogą być przechowywane na stosie, są one nieodpowiednie dla wielu scenariuszy, w tym wywołań metod asynchronicznych. Program .NET Core 2,1 dodaje wiele typów dodatkowych, takich jak <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>i <xref:System.Buffers.MemoryPool%601>. Podobnie <xref:System.Span%601>jak <xref:System.Memory%601> w przypadku, gdy jego typy pokrewne mogą być obsługiwane przez pamięć zarządzaną i niezarządzaną. W <xref:System.Span%601>przeciwieństwie <xref:System.Memory%601> do programu, można je przechowywać na zarządzanym stosie.

Zarówno <xref:System.Span%601> , <xref:System.Memory%601> jak i są buforami danych strukturalnych, które mogą być używane w potokach. Oznacza to, że zostały zaprojektowane tak, aby niektóre lub wszystkie dane mogły być efektywnie przesyłane do składników w potoku, które mogą je przetworzyć i opcjonalnie zmodyfikować bufor. Ze <xref:System.Memory%601> względu na to, że i powiązane z nim typy są dostępne przez wiele składników lub przez wiele wątków, ważne jest, aby deweloperzy przestrzegali niektórych standardowych wytycznych dotyczących użycia w celu utworzenia niezawodnego kodu.

## <a name="owners-consumers-and-lifetime-management"></a>Właściciele, konsumenci i zarządzanie okresem istnienia

Ponieważ bufory mogą być przesyłane między interfejsami API, a ponieważ bufory mogą być dostępne z wielu wątków, ważne jest, aby wziąć pod uwagę zarządzanie okresem istnienia. Istnieją trzy podstawowe koncepcje:

- **Własność**. Właściciel wystąpienia buforu jest odpowiedzialny za zarządzanie okresem istnienia, w tym niszczenie bufora, gdy nie jest już używany. Wszystkie bufory mają jednego właściciela. Zazwyczaj właścicielem jest składnik, który utworzył bufor lub odebrał bufor od fabryki. Własność można także przenieść; **Składnik-a** może nawiązać kontrolę nad buforem ze **składnikiem B**, gdzie **składnik-a** nie może już korzystać z bufora, a **składnik-b** jest odpowiedzialny za niszczenie bufora, gdy nie jest już używany.

- **Użycie**. Odbiorca wystąpienia buforu może używać wystąpienia buforu przez odczyt z niego i prawdopodobnie zapis. Bufory mogą mieć jednego konsumenta w danym momencie, chyba że zostanie podany zewnętrzny mechanizm synchronizacji. Aktywny konsument buforu nie musi być właścicielem bufora.

- **Dzierżawa**. Dzierżawa to długość czasu, przez jaki dany składnik może być odbiorcą buforu.

Poniższy przykład pseudo kodu ilustruje te trzy koncepcje. Zawiera `Main` <xref:System.Memory%601> metodę, która tworzy wystąpienie buforu typu <xref:System.Char>, wywołuje `WriteInt32ToBuffer` metodę w celu zapisania ciągu reprezentującego liczbę całkowitą do bufora, a następnie wywołuje `DisplayBufferToConsole` metodę, aby wyświetlić wartość buforu.

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

`Main` Metoda tworzy bufor (w tym przypadku <xref:System.Span%601> wystąpienie) i dlatego jest jego właścicielem. W związku `Main` z tym, jest odpowiedzialny za niszczenie bufora, gdy nie jest już używany. Robi to przez wywołanie <xref:System.Span%601.Clear?displayProperty=nameWithType> metody buforu. (W <xref:System.Span%601.Clear> tym miejscu Metoda faktycznie czyści pamięć buforu; <xref:System.Span%601> struktura nie ma w rzeczywistości metody, która niszczy bufor).

Bufor ma dwóch użytkowników `WriteInt32ToBuffer` i. `DisplayBufferToConsole` W danym momencie istnieje tylko jeden użytkownik (pierwszy `WriteInt32ToBuffer` `DisplayBufferToConsole`), a żaden z nich nie jest właścicielem buforu. Należy zauważyć, że "konsument" w tym kontekście nie implikuje widoku tylko do odczytu buforu; Użytkownicy mogą modyfikować zawartość bufora, tak jak `WriteInt32ToBuffer` w przypadku widoku do odczytu/zapisu w buforze.

`WriteInt32ToBuffer` Metoda ma dzierżawę (może zużywać) bufor między początkiem wywołania metody a czasem zwracanym przez metodę. Podobnie, `DisplayBufferToConsole` ma dzierżawę w buforze podczas wykonywania, a dzierżawa jest wydawana, gdy metoda zostanie rozwinięcia. (Nie ma interfejsu API do zarządzania dzierżawą; "dzierżawa" jest kwestią koncepcyjną).

## <a name="memoryt-and-the-ownerconsumer-model"></a>Pamięć\<T> i model właściciel/odbiorca

W przypadku, gdy [właściciele, odbiorcy i informacje o zarządzaniu okresem istnienia](#owners-consumers-and-lifetime-management) są uwagi, bufor zawsze ma właściciela. Platforma .NET Core obsługuje dwa modele własności:

- Model, który obsługuje pojedyncze własności. Bufor ma jednego właściciela na cały okres istnienia.

- Model obsługujący przenoszenie własności. Własność buforu można przenieść z jego oryginalnego właściciela (jego twórcy) do innego składnika, który następnie jest odpowiedzialny za zarządzanie okresem istnienia bufora. Ten właściciel może zmienić własność transferu na inny składnik i tak dalej.

<xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> Interfejs umożliwia jawne Zarządzanie własnością bufora. <xref:System.Buffers.IMemoryOwner%601>obsługuje obydwa modele własności. Składnik zawierający <xref:System.Buffers.IMemoryOwner%601> odwołanie jest właścicielem bufora. Poniższy przykład używa <xref:System.Buffers.IMemoryOwner%601?> wystąpienia, aby odzwierciedlić własność <xref:System.Memory%601> bufora.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Możemy również napisać ten przykład z [`using`](../../csharp/language-reference/keywords/using-statement.md):

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

W tym kodzie:

- `Main` Metoda przechowuje odwołanie do <xref:System.Buffers.IMemoryOwner%601> wystąpienia, dlatego `Main` Metoda jest właścicielem buforu.

- Metody `WriteInt32ToBuffer` i `DisplayBufferToConsole` akceptują <xref:System.Memory%601> jako publiczny interfejs API. W związku z tym są użytkownikami bufora. I je zużywają jednocześnie.

Chociaż `WriteInt32ToBuffer` Metoda jest przeznaczona do zapisania wartości w buforze, `DisplayBufferToConsole` Metoda nie jest. W celu odzwierciedlenia tej wartości może zatwierdzić argument typu <xref:System.ReadOnlyMemory%601>. Aby uzyskać więcej informacji <xref:System.ReadOnlyMemory%601>na temat, zobacz temat [Rule #2\<: Użyj ReadOnlySpan t\<> lub ReadOnlyMemory t>, jeśli bufor powinien być tylko do odczytu](#rule-2).

### <a name="ownerless-memoryt-instances"></a>Wystąpienia "pamięć\<bezwłaściciel" T> wystąpień

Można utworzyć <xref:System.Memory%601> wystąpienie bez użycia <xref:System.Buffers.IMemoryOwner%601>. W takim przypadku własność buforu jest niejawna, a nie jawna, a tylko model jednego właściciela jest obsługiwany. Można to zrobić, wykonując następujące czynności:

- Wywołanie jednego z <xref:System.Memory%601> konstruktorów bezpośrednio, przekazanie w `T[]`, jak pokazano w poniższym przykładzie.

- Wywoływanie metody rozszerzenia [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) w celu utworzenia `ReadOnlyMemory<char>` wystąpienia.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Metoda, która początkowo tworzy <xref:System.Memory%601> wystąpienie, jest niejawnym właścicielem buforu. Własności nie można przenieść do żadnego innego składnika, ponieważ nie ma <xref:System.Buffers.IMemoryOwner%601> żadnego wystąpienia, aby ułatwić transfer. (Alternatywnie można również wyobrazić, że moduł wyrzucania elementów bezużytecznych środowiska uruchomieniowego jest właścicielem buforu, a wszystkie metody zużywają bufor).

## <a name="usage-guidelines"></a>Zalecenia dotyczące użycia

Ponieważ blok pamięci jest własnością, ale jest przeznaczony do przekazywania do wielu składników, a niektóre z nich mogą pracować w konkretnym bloku pamięci jednocześnie, ważne jest ustanowienie wytycznych dotyczących używania obu <xref:System.Memory%601> i. <xref:System.Span%601>  Wytyczne są niezbędne, ponieważ:

- Jest możliwe, że składnik zachowuje odwołanie do bloku pamięci po jego udostępnieniu przez jego właściciela.

- Składnik może działać w buforze w tym samym czasie, w którym działa inny składnik, w procesie uszkodzonym dane w buforze.

- Chociaż przydzielony przez stos charakter <xref:System.Span%601> optymalizuje wydajność i udostępnia <xref:System.Span%601> preferowany typ dla działania w bloku pamięci, to również <xref:System.Span%601> istotne ograniczenia. Ważne jest, aby wiedzieć, kiedy należy użyć <xref:System.Span%601> i kiedy należy używać <xref:System.Memory%601>programu.

Poniżej przedstawiono nasze zalecenia dotyczące pomyślnego <xref:System.Memory%601> użycia i powiązanych typów. Wskazówki odnoszące <xref:System.Memory%601> się <xref:System.Span%601> do programu i <xref:System.ReadOnlyMemory%601> dotyczą <xref:System.ReadOnlySpan%601> także i, chyba że jawnie zanotujemy inaczej.

**Reguła #1: w przypadku synchronicznego interfejsu API należy\<użyć funkcji Span t>\<zamiast pamięci t> jako parametru, jeśli jest to możliwe.**

<xref:System.Span%601>jest bardziej uniwersalny niż <xref:System.Memory%601> i może reprezentować szeroką gamę ciągłych buforów pamięci. <xref:System.Span%601>oferuje również lepszą wydajność niż <xref:System.Memory%601>. Na <xref:System.Memory%601.Span?displayProperty=nameWithType> koniec można użyć właściwości <xref:System.Memory%601> <xref:System.Span%601>, aby skonwertować wystąpienie na, chociaż\<nie jest możliwe przeprowadzenie konwersji z>> na\<pamięć. Dlatego jeśli obiekty wywołujące miały <xref:System.Memory%601> wystąpienie, będą mogły wywołać metody z <xref:System.Span%601> parametrami.

Użycie parametru typu <xref:System.Span%601> zamiast typu <xref:System.Memory%601> pomaga napisać poprawną implementację metody zużywanej. Będziesz automatycznie otrzymywać sprawdzenia czasu kompilacji, aby upewnić się, że nie próbujesz uzyskać dostępu do buforu poza dzierżawą metody (więcej informacji na ten temat).

Czasami musisz użyć <xref:System.Memory%601> parametru zamiast <xref:System.Span%601> parametru, nawet jeśli jest w pełni synchroniczne. Być może interfejs API, który jest zależny <xref:System.Memory%601> , akceptuje tylko argumenty. Jest to dokładne, ale należy pamiętać o kompromisach, które są wykorzystywane <xref:System.Memory%601> w przypadku synchronicznego korzystania z programu.

<a name="rule-2" />

**Reguła #2: Użyj ReadOnlySpan\<t> lub ReadOnlyMemory\<> t, jeśli bufor powinien być tylko do odczytu.**

We wcześniejszych przykładach `DisplayBufferToConsole` Metoda odczytuje tylko dane z buforu; nie modyfikuje zawartości buforu. Sygnaturę metody należy zmienić na następujący.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

W rzeczywistości, Jeśli połączymy tę regułę i #1 reguł, możemy jeszcze bardziej ulepszyć i napisać sygnaturę metody w następujący sposób:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

`DisplayBufferToConsole` Metoda działa teraz z niemal każdym typem bufora urojonym: `T[]`, magazynem przydzielonym z [stackalloc](../../csharp/language-reference/operators/stackalloc.md)i tak dalej. Możesz nawet przekazać bezpośrednio do <xref:System.String> programu!

**Reguła #3: Jeśli metoda akceptuje pamięć\<t> i zwraca `void`, nie należy używać wystąpienia pamięci\<t> po powrocie metody.**

Odnosi się to do pojęcia "Lease" wymienionego wcześniej. Dzierżawa metody zwracającej wartość void w <xref:System.Memory%601> wystąpieniu rozpoczyna się po wprowadzeniu metody i kończy się po zakończeniu metody. Rozważmy poniższy przykład, który wywołuje `Log` pętlę na podstawie danych wejściowych z konsoli.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Jeśli `Log` jest to w pełni synchroniczna Metoda, ten kod będzie zachowywać się zgodnie z oczekiwaniami, ponieważ w danym momencie istnieje tylko jeden aktywny użytkownik wystąpienia pamięci.
Ale Wyobraź sobie, `Log` że ta implementacja jest taka sama.

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

W tej implementacji narusza `Log` swoją dzierżawę, ponieważ nadal próbuje użyć <xref:System.Memory%601> wystąpienia w tle po zwróceniu pierwotnej metody. `Main` Metoda może być mutacją buforu podczas `Log` próby odczytu z niego, co może spowodować uszkodzenie danych.

Istnieje kilka sposobów rozwiązania tego problemu:

- `Log` Metoda może zwrócić <xref:System.Threading.Tasks.Task> zamiast `void`, ponieważ Poniższa implementacja `Log` metody.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log`Zamiast tego można zaimplementować w następujący sposób:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Reguła #4: Jeśli metoda akceptuje pamięć\<t> i zwraca zadanie, nie należy używać wystąpienia pamięci\<t> po przejściu zadań do stanu terminalu.**

Jest to tylko asynchroniczny wariant reguły #3. `Log` Metodę z wcześniejszego przykładu można napisać w następujący sposób, aby zachować zgodność z tą regułą:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

W tym miejscu "stan terminalu" oznacza, że zadanie przechodzi do stanu ukończone, Niepowodzenie lub anulowane. Innymi słowy "stan terminalu" oznacza "wszystkie elementy, które mogłyby spowodować, że oczekujące na zgłoszenie lub kontynuowanie wykonywania".

Te wskazówki dotyczą metod, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>lub mają podobny typ.

**Reguła #5: Jeśli Konstruktor akceptuje> pamięci\<jako parametr, zakłada się, że metody wystąpienia na skonstruowanym obiekcie są traktowane jako konsumenci z wystąpienia pamięci\<t>.**

Rozważmy następujący przykład:

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

W tym miejscu `OddValueExtractor` Konstruktor akceptuje `ReadOnlyMemory<int>` jako parametr konstruktora, więc Konstruktor jest odbiorcą `ReadOnlyMemory<int>` wystąpienia, a wszystkie metody wystąpienia w zwracanej wartości są również odbiorcami oryginalnego `ReadOnlyMemory<int>` wystąpienia. Oznacza to, `TryReadNextOddValue` że zużywa `ReadOnlyMemory<int>` wystąpienie, mimo że wystąpienie nie jest bezpośrednio przesyłane do `TryReadNextOddValue` metody.

**Reguła #6: Jeśli w danym typie istnieje Właściwość Set> Table\<(lub równoważna metoda wystąpienia) dla tego obiektu, zakłada się, że metody wystąpień na tym obiekcie są klientami z wystąpienia pamięci\<T>.**

Jest to tylko wariant reguły #5. Ta reguła istnieje, ponieważ przyjmuje się, że metody ustawiające właściwości lub równoważne metody przechwytują i utrzymują dane wejściowe

Poniższy przykład wyzwala tę regułę:

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

**#7 reguły: Jeśli masz odwołanie IMemoryOwner\<T>, musisz mieć w pewnym momencie usunąć lub przenieść jego własność (ale nie oba).**

Ponieważ <xref:System.Memory%601> wystąpienie może być obsługiwane przez pamięć zarządzaną lub niezarządzaną, właściciel musi wywołać <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> , gdy działanie wykonane w <xref:System.Memory%601> wystąpieniu zostało zakończone. Alternatywnie właściciel może przenieść własność <xref:System.Buffers.IMemoryOwner%601> wystąpienia do innego składnika, w tym momencie składnik pozyskiwania będzie odpowiedzialny za wywoływanie <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> w odpowiednim czasie (więcej informacji na ten temat).

Niepowodzenie wywołania <xref:System.Buffers.MemoryPool%601.Dispose%2A> metody może prowadzić do niezarządzanych przecieków pamięci lub obniżenia wydajności.

Ta reguła dotyczy również kodu, który wywołuje metody fabryki, <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>takie jak. Obiekt wywołujący zostaje właścicielem zwróconego <xref:System.Buffers.IMemoryOwner%601> i jest odpowiedzialny za likwidację wystąpienia po zakończeniu.

**Reguła #8: Jeśli masz parametr IMemoryOwner\<T> na powierzchni interfejsu API, akceptujesz własność tego wystąpienia.**

Zaakceptowanie wystąpienia tego typu sygnalizuje, że składnik zamierza przejąć własność tego wystąpienia. Składnik jest odpowiedzialny za poprawność usuwania zgodnie z regułą #7.

Każdy składnik, który przenosi własność <xref:System.Buffers.IMemoryOwner%601> wystąpienia na inny składnik, nie powinien już korzystać z tego wystąpienia po zakończeniu wywołania metody.

> [!IMPORTANT]
> Jeśli <xref:System.Buffers.IMemoryOwner%601> Konstruktor akceptuje jako parametr, jego typ powinien implementować <xref:System.IDisposable>, a <xref:System.IDisposable.Dispose%2A> Metoda powinna wywołać. <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>

**#9 reguły: w przypadku pakowania synchronicznej metody p/Invoke interfejs API powinien akceptować zakres\<T> jako parametr.**

Zgodnie z regułą #1, <xref:System.Span%601> jest zazwyczaj prawidłowym typem używanym do synchronicznych interfejsów API. Można przypiąć <xref:System.Span%601> wystąpienia za pomocą [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) słowa kluczowego, jak w poniższym przykładzie.

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

W poprzednim przykładzie `pbData` może mieć wartość null, jeśli na przykład zakres wejściowy jest pusty. Jeśli wyeksportowana Metoda absolutnie wymaga `pbData` , aby nie mieć wartości null, `cbData` nawet jeśli jest równa 0, Metoda może być implementowana w następujący sposób:

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

**#10 reguły: w przypadku zawijania asynchronicznej metody p/Invoke interfejs API powinien akceptować>\<pamięci jako parametr.**

Ponieważ nie można użyć [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) słowa kluczowego w operacjach asynchronicznych, <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> należy użyć metody <xref:System.Memory%601> , aby przypiąć wystąpienia, niezależnie od rodzaju ciągłej pamięci reprezentowanej przez wystąpienie. Poniższy przykład pokazuje, jak używać tego interfejsu API do wykonywania asynchronicznego wywołania p/Invoke.

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)(handle.Target);
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
