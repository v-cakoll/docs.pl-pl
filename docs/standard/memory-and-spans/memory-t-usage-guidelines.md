---
title: Wytyczne dotyczące użycia struktur Memory<T> i Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121961"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>\<pamięci i zakres\<T > wytyczne dotyczące użycia

Platforma .NET Core zawiera wiele typów, które reprezentują dowolny ciągły region pamięci. W środowisku .NET Core 2,0 wprowadzono <xref:System.Span%601> i <xref:System.ReadOnlySpan%601>, które są lekkimi buforami pamięci, które mogą być obsługiwane przez pamięć zarządzaną lub niezarządzaną. Ponieważ te typy mogą być przechowywane na stosie, są one nieodpowiednie dla wielu scenariuszy, w tym wywołań metod asynchronicznych. Program .NET Core 2,1 dodaje wiele typów dodatkowych, w tym <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>i <xref:System.Buffers.MemoryPool%601>. Podobnie jak <xref:System.Span%601>, <xref:System.Memory%601> i powiązane typy mogą być obsługiwane przez pamięć zarządzaną i niezarządzaną. W przeciwieństwie do <xref:System.Span%601>, <xref:System.Memory%601> można przechowywać na zarządzanym stosie.

Zarówno <xref:System.Span%601>, jak i <xref:System.Memory%601> są buforami danych strukturalnych, które mogą być używane w potokach. Oznacza to, że zostały zaprojektowane tak, aby niektóre lub wszystkie dane mogły być efektywnie przesyłane do składników w potoku, które mogą je przetworzyć i opcjonalnie zmodyfikować bufor. Ze względu na to, że <xref:System.Memory%601> i powiązane z nim typy są dostępne przez wiele składników lub przez wiele wątków, ważne jest, aby deweloperzy przestrzegali niektórych standardowych wytycznych dotyczących użycia w celu utworzenia niezawodnego kodu.

## <a name="owners-consumers-and-lifetime-management"></a>Właściciele, konsumenci i zarządzanie okresem istnienia

Ponieważ bufory mogą być przesyłane między interfejsami API, a ponieważ bufory mogą być dostępne z wielu wątków, ważne jest, aby wziąć pod uwagę zarządzanie okresem istnienia. Istnieją trzy podstawowe koncepcje:

- **Własność**. Właściciel wystąpienia buforu jest odpowiedzialny za zarządzanie okresem istnienia, w tym niszczenie bufora, gdy nie jest już używany. Wszystkie bufory mają jednego właściciela. Zazwyczaj właścicielem jest składnik, który utworzył bufor lub odebrał bufor od fabryki. Własność można także przenieść; **Składnik-a** może nawiązać kontrolę nad buforem ze **składnikiem B**, gdzie **składnik-a** nie może już korzystać z bufora, a **składnik-b** jest odpowiedzialny za niszczenie bufora, gdy nie jest już używany.

- **Użycie**. Odbiorca wystąpienia buforu może używać wystąpienia buforu przez odczyt z niego i prawdopodobnie zapis. Bufory mogą mieć jednego konsumenta w danym momencie, chyba że zostanie podany zewnętrzny mechanizm synchronizacji. Należy zauważyć, że aktywny konsument buforu nie musi być właścicielem bufora.

- **Dzierżawa**. Dzierżawa to długość czasu, przez jaki dany składnik może być odbiorcą buforu.

Poniższy przykład pseudo kodu ilustruje te trzy koncepcje. Zawiera metodę `Main`, która tworzy wystąpienie buforu <xref:System.Memory%601> typu <xref:System.Char>, wywołuje metodę `WriteInt32ToBuffer`, aby napisać ciąg reprezentujący liczbę całkowitą do bufora, a następnie wywołuje metodę `DisplayBufferToConsole`, aby wyświetlić wartość buforu.

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

Metoda `Main` tworzy bufor (w tym przypadku wystąpienie <xref:System.Span%601>) i dlatego jest jego właścicielem. W związku z tym `Main` jest odpowiedzialny za niszczenie bufora, gdy nie jest już używany. Robi to przez wywołanie metody <xref:System.Span%601.Clear?displayProperty=nameWithType> bufora. (Metoda <xref:System.Span%601.Clear> w rzeczywistości czyści pamięć buforu; struktura <xref:System.Span%601> nie ma w rzeczywistości metody, która niszczy bufor).

Bufor ma dwóch użytkowników, `WriteInt32ToBuffer` i `DisplayBufferToConsole`. Istnieje tylko jeden konsument naraz (pierwszy `WriteInt32ToBuffer`, a następnie `DisplayBufferToConsole`), a żaden z nich nie jest właścicielem buforu. Należy zauważyć, że "konsument" w tym kontekście nie implikuje widoku tylko do odczytu buforu; Użytkownicy mogą modyfikować zawartość bufora, tak jak `WriteInt32ToBuffer`, jeśli ma on widok do odczytu/zapisu w buforze.

Metoda `WriteInt32ToBuffer` ma dzierżawę (może zużywać) bufor między początkiem wywołania metody a czasem zwracanym przez metodę. Podobnie `DisplayBufferToConsole` ma dzierżawę w buforze podczas wykonywania, a dzierżawa jest wydawana, gdy metoda zostanie rozwinięcia. (Nie ma interfejsu API do zarządzania dzierżawą; "dzierżawa" jest kwestią koncepcyjną).

## <a name="memoryt-and-the-ownerconsumer-model"></a>Pamięć\<T > i model właściciel/odbiorca

W przypadku, gdy [właściciele, odbiorcy i informacje o zarządzaniu okresem istnienia](#owners-consumers-and-lifetime-management) są uwagi, bufor zawsze ma właściciela. Platforma .NET Core obsługuje dwa modele własności:

- Model, który obsługuje pojedyncze własności. Bufor ma jednego właściciela na cały okres istnienia.

- Model obsługujący przenoszenie własności. Własność buforu można przenieść z jego oryginalnego właściciela (jego twórcy) do innego składnika, który następnie jest odpowiedzialny za zarządzanie okresem istnienia bufora. Ten właściciel może zmienić własność transferu na inny składnik i tak dalej.

Za pomocą interfejsu <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> można jawnie zarządzać własnością bufora. <xref:System.Buffers.IMemoryOwner%601> obsługuje obydwa modele własności. Składnik zawierający odwołanie <xref:System.Buffers.IMemoryOwner%601> jest właścicielem buforu. Poniższy przykład używa wystąpienia <xref:System.Buffers.IMemoryOwner%601?>, aby odzwierciedlić własność bufora <xref:System.Memory%601>.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Możemy również napisać następujący przykład z [`using`](../../csharp/language-reference/keywords/using-statement.md):

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

W tym kodzie:

- Metoda `Main` przechowuje odwołanie do wystąpienia <xref:System.Buffers.IMemoryOwner%601>, dlatego Metoda `Main` jest właścicielem buforu.

- Metody `WriteInt32ToBuffer` i `DisplayBufferToConsole` akceptują <xref:System.Memory%601> jako publiczny interfejs API. W związku z tym są użytkownikami bufora. I je zużywają jednocześnie.

Chociaż metoda `WriteInt32ToBuffer` jest przeznaczona do zapisu wartości w buforze, Metoda `DisplayBufferToConsole` nie jest. Aby to odzwierciedlić, może zatwierdzić argument typu <xref:System.ReadOnlyMemory%601>. Aby uzyskać dodatkowe informacje na temat <xref:System.ReadOnlyMemory%601>, zobacz [reguła #2: Użyj ReadOnlySpan\<t > lub ReadOnlyMemory\<t >, jeśli bufor powinien być tylko do odczytu](#rule-2).

### <a name="ownerless-memoryt-instances"></a>"Pamięć bezwłaścicielowa"\<wystąpienia T >

Można utworzyć wystąpienie <xref:System.Memory%601> bez korzystania z <xref:System.Buffers.IMemoryOwner%601>. W takim przypadku własność buforu jest niejawna, a nie jawna, a tylko model jednego właściciela jest obsługiwany. Można to zrobić, wykonując następujące czynności:

- Wywołanie jednego z konstruktorów <xref:System.Memory%601> bezpośrednio, przekazanie w `T[]`, jak pokazano w poniższym przykładzie.

- Wywoływanie metody rozszerzenia [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) , aby utworzyć wystąpienie `ReadOnlyMemory<char>`.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Metoda, która początkowo tworzy wystąpienie <xref:System.Memory%601>, jest niejawnym właścicielem buforu. Własności nie można przenieść do żadnego innego składnika, ponieważ nie ma <xref:System.Buffers.IMemoryOwner%601> wystąpienia, aby ułatwić transfer. (Alternatywnie można również wyobrazić, że moduł wyrzucania elementów bezużytecznych środowiska uruchomieniowego jest właścicielem buforu, a wszystkie metody zużywają bufor).

## <a name="usage-guidelines"></a>Wskazówki dotyczące użycia

Ponieważ blok pamięci jest własnością, ale jest przeznaczony do przekazywania do wielu składników, a niektóre z nich mogą działać jednocześnie w konkretnym bloku pamięci, ważne jest ustanowienie wytycznych dotyczących używania zarówno <xref:System.Memory%601>, jak i <xref:System.Span%601>.  Wytyczne są niezbędne, ponieważ:

- Jest możliwe, że składnik zachowuje odwołanie do bloku pamięci po jego udostępnieniu przez jego właściciela.

- Składnik może działać w buforze w tym samym czasie, w którym działa inny składnik, w procesie uszkodzonym dane w buforze.

- Chociaż przydzielony przez stos charakter <xref:System.Span%601> optymalizuje wydajność i tworzy <xref:System.Span%601> preferowany typ dla działania w bloku pamięci, zagadnienia te <xref:System.Span%601> również pewne istotne ograniczenia. Ważne jest, aby wiedzieć, kiedy używać <xref:System.Span%601> i kiedy należy używać <xref:System.Memory%601>.

Poniżej znajdują się nasze zalecenia dotyczące pomyślnego użycia <xref:System.Memory%601> i powiązanych typów. Należy zauważyć, że wskazówki dotyczące <xref:System.Memory%601> i <xref:System.Span%601> dotyczą również <xref:System.ReadOnlyMemory%601> i <xref:System.ReadOnlySpan%601>, chyba że jawnie zanotujemy inaczej.

**Reguła #1: dla synchronicznego interfejsu API należy użyć span\<T > zamiast pamięci\<T > jako parametru, jeśli jest to możliwe.**

<xref:System.Span%601> jest bardziej uniwersalny niż <xref:System.Memory%601> i może reprezentować szeroką gamę ciągłych buforów pamięci. <xref:System.Span%601> również zapewnia lepszą wydajność niż <xref:System.Memory%601>. Na koniec można użyć właściwości <xref:System.Memory%601.Span?displayProperty=nameWithType>, aby przekonwertować wystąpienie <xref:System.Memory%601> na <xref:System.Span%601>, mimo że\<T > do-pamięci\<nie jest możliwe przeprowadzenie konwersji >. Tak więc jeśli obiekty wywołujące miały <xref:System.Memory%601> wystąpienie, będą mogły wywołać metody z parametrami <xref:System.Span%601> mimo to.

Użycie parametru typu <xref:System.Span%601> zamiast typu <xref:System.Memory%601> pomaga również napisać poprawną implementację metody. Będziesz automatycznie otrzymywać sprawdzenia czasu kompilacji, aby upewnić się, że nie próbujesz uzyskać dostępu do buforu poza dzierżawą metody (więcej informacji na ten temat).

Czasami konieczne będzie użycie parametru <xref:System.Memory%601> zamiast parametru <xref:System.Span%601>, nawet jeśli użytkownik jest w pełni synchroniczny. Być może interfejs API, który jest zależny, akceptuje tylko <xref:System.Memory%601> argumenty. Jest to bardzo precyzyjne, ale należy pamiętać o kompromisach, które są wykorzystywane podczas synchronicznego korzystania <xref:System.Memory%601>.

<a name="rule-2" />

**Reguła #2: Użyj ReadOnlySpan\<T > lub ReadOnlyMemory\<T >, jeśli bufor powinien być tylko do odczytu.**

We wcześniejszych przykładach Metoda `DisplayBufferToConsole` odczytuje tylko z buforu; nie modyfikuje zawartości buforu. Sygnaturę metody należy zmienić na następujący.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

W rzeczywistości, Jeśli połączymy tę regułę i #1 reguł, możemy jeszcze bardziej ulepszyć i napisać sygnaturę metody w następujący sposób:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

Metoda `DisplayBufferToConsole` działa teraz z niemal każdym typem bufora urojonym: `T[]`, magazynem przydzielonym [stackalloc](../../csharp/language-reference/operators/stackalloc.md)i tak dalej. Możesz nawet przekazać <xref:System.String> bezpośrednio do programu!

**Reguła #3: Jeśli metoda akceptuje pamięć\<T > i zwraca `void`, nie należy używać wystąpienia\<pamięci > T po powrocie metody.**

Odnosi się to do pojęcia "Lease" wymienionego wcześniej. Dzierżawa metody zwracającej wartość void w wystąpieniu <xref:System.Memory%601> rozpoczyna się po wprowadzeniu metody i kończy się po zakończeniu metody. Rozważmy poniższy przykład, który wywołuje `Log` w pętli na podstawie danych wejściowych z konsoli.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Jeśli `Log` jest w pełni synchroniczną metodą, ten kod będzie zachowywać się zgodnie z oczekiwaniami, ponieważ w danym momencie istnieje tylko jeden aktywny użytkownik wystąpienia pamięci.
Ale zamiast tego Wyobraź sobie, że `Log` ma tę implementację.

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

W tej implementacji `Log` narusza swoją dzierżawę, ponieważ nadal próbuje użyć wystąpienia <xref:System.Memory%601> w tle po zwróceniu pierwotnej metody. Metoda `Main` może przeniknąć bufor, podczas gdy `Log` próbuje odczytać z niego, co może spowodować uszkodzenie danych.

Istnieje kilka sposobów rozwiązania tego problemu:

- Metoda `Log` może zwrócić <xref:System.Threading.Tasks.Task> zamiast `void`, ponieważ Poniższa implementacja metody `Log`.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- Zamiast tego można zaimplementować `Log` w następujący sposób:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Reguła #4: Jeśli metoda akceptuje pamięć\<T > i zwraca zadanie, nie należy używać wystąpienia pamięci\<T > po przejściu zadania do stanu terminalu.**

Jest to tylko asynchroniczny wariant reguły #3. Metodę `Log` z wcześniejszego przykładu można napisać w następujący sposób, aby zachować zgodność z tą regułą:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

W tym miejscu "stan terminalu" oznacza, że zadanie przechodzi do stanu ukończone, Niepowodzenie lub anulowane. Innymi słowy "stan terminalu" oznacza "wszystkie elementy, które mogłyby spowodować, że oczekujące na zgłoszenie lub kontynuowanie wykonywania".

Te wskazówki dotyczą metod, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>lub dowolny podobny typ.

**Reguła #5: Jeśli Konstruktor akceptuje pamięć\<T > jako parametr, zakłada się, że metody wystąpienia na skonstruowanym obiekcie są konsumentami pamięci\<T >.**

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

W tym miejscu Konstruktor `OddValueExtractor` akceptuje `ReadOnlyMemory<int>` jako parametr konstruktora, więc Konstruktor jest odbiorcą wystąpienia `ReadOnlyMemory<int>`, a wszystkie metody wystąpienia w zwracanej wartości są również konsumentami oryginalnego wystąpienia `ReadOnlyMemory<int>`. Oznacza to, że `TryReadNextOddValue` zużywa wystąpienie `ReadOnlyMemory<int>`, mimo że wystąpienie nie jest bezpośrednio przesyłane do metody `TryReadNextOddValue`.

**Reguła #6: Jeśli w danym typie jest dostępna właściwość settable\<T > (lub równoważna metoda wystąpienia), metody wystąpienia na tym obiekcie założono, że są konsumentami pamięci\<T > wystąpieniem.**

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

**#7 reguły: Jeśli masz odwołanie do IMemoryOwner\<T >, musisz mieć w pewnym momencie usunąć lub przenieść jego własność (ale nie oba).**

Ponieważ wystąpienie <xref:System.Memory%601> może być obsługiwane przez pamięć zarządzaną lub niezarządzaną, właściciel musi wywołać <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>, gdy działanie wykonane w wystąpieniu <xref:System.Memory%601> zostało zakończone. Alternatywnie właściciel może przenieść własność wystąpienia <xref:System.Buffers.IMemoryOwner%601> do innego składnika, w tym momencie składnik pozyskiwania będzie odpowiedzialny za wywoływanie <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> w odpowiednim czasie (więcej informacji na ten temat).

Niepowodzenie wywołania metody <xref:System.Buffers.MemoryPool%601.Dispose%2A> może prowadzić do niezarządzanych przecieków pamięci lub obniżenia wydajności.

Ta reguła dotyczy również kodu, który wywołuje metody fabryki, takie jak <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>. Obiekt wywołujący zostaje właścicielem zwracanego <xref:System.Buffers.IMemoryOwner%601> i jest odpowiedzialny za wyzbywanie wystąpienia po zakończeniu.

**Reguła #8: Jeśli masz parametr IMemoryOwner\<T > na powierzchni interfejsu API, akceptujesz własność tego wystąpienia.**

Zaakceptowanie wystąpienia tego typu sygnalizuje, że składnik zamierza przejąć własność tego wystąpienia. Składnik jest odpowiedzialny za poprawność usuwania zgodnie z regułą #7.

Dowolny składnik, który przetransferuje własność wystąpienia <xref:System.Buffers.IMemoryOwner%601> do innego składnika, nie powinien już używać tego wystąpienia po zakończeniu wywołania metody.

> [!IMPORTANT]
> Jeśli Konstruktor akceptuje <xref:System.Buffers.IMemoryOwner%601> jako parametr, jego typ powinien implementować <xref:System.IDisposable>, a metoda <xref:System.IDisposable.Dispose%2A> powinna wywołać <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.

**#9 reguły: w przypadku pakowania synchronicznej metody p/Invoke interfejs API powinien akceptować zakres\<T > jako parametr.**

Zgodnie z #1 regułą <xref:System.Span%601> jest zazwyczaj prawidłowym typem używanym do synchronicznych interfejsów API. Można przypiąć wystąpienia <xref:System.Span%601> za pomocą słowa kluczowego [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) , jak w poniższym przykładzie.

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

W poprzednim przykładzie `pbData` może mieć wartość null, jeśli na przykład zakres wejściowy jest pusty. Jeśli wyeksportowana Metoda absolutnie wymaga, aby `pbData` mieć wartości inne niż null, nawet jeśli `cbData` ma wartość 0, Metoda może być implementowana w następujący sposób:

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

**#10 reguły: w przypadku zawijania asynchronicznej metody p/Invoke interfejs API powinien akceptować pamięć\<T > jako parametr.**

Ponieważ nie można użyć słowa kluczowego [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) w operacjach asynchronicznych, należy użyć metody <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> do przypinania <xref:System.Memory%601> wystąpień, niezależnie od rodzaju ciągłej pamięci reprezentowanej przez wystąpienie. Poniższy przykład pokazuje, jak używać tego interfejsu API do wykonywania asynchronicznego wywołania p/Invoke.

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
    var actualState = (MyCompletedCallbackState)state;
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

## <a name="see-also"></a>Zobacz także

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
