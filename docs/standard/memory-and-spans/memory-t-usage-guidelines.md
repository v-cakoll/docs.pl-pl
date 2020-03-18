---
title: Wytyczne dotyczące użycia struktur Memory<T> i Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121961"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Wytyczne dotyczące użycia struktur Memory\<T > i Span\<T>

.NET Core zawiera wiele typów, które reprezentują dowolny ciągły region pamięci. .NET Core 2.0 wprowadzone <xref:System.Span%601> i <xref:System.ReadOnlySpan%601>, które są lekkie bufory pamięci, które mogą być wspierane przez pamięć zarządzaną lub niezarządzaną. Ponieważ te typy mogą być przechowywane tylko na stosie, są one nieodpowiednie dla wielu scenariuszy, w tym wywołania metody asynchronicznej. .NET Core 2.1 dodaje szereg dodatkowych <xref:System.Memory%601> <xref:System.ReadOnlyMemory%601>typów, w tym , , <xref:System.Buffers.IMemoryOwner%601>, i <xref:System.Buffers.MemoryPool%601>. Podobnie <xref:System.Span%601> <xref:System.Memory%601> jak , a jego powiązane typy mogą być wspierane przez pamięć zarządzaną i niezarządzaną. W <xref:System.Span%601> <xref:System.Memory%601> przeciwieństwie do , mogą być przechowywane na zarządzanym stercie.

Oba <xref:System.Span%601> <xref:System.Memory%601> i są bufory danych strukturalnych, które mogą być używane w potokach. Oznacza to, że są one zaprojektowane tak, aby niektóre lub wszystkie dane mogą być efektywnie przekazywane do składników w potoku, które mogą je przetwarzać i opcjonalnie modyfikować buforu. Ponieważ <xref:System.Memory%601> i jego powiązanych typów są dostępne przez wiele składników lub przez wiele wątków, ważne jest, aby deweloperzy przestrzegali niektórych standardowych wytycznych użycia do tworzenia niezawodnego kodu.

## <a name="owners-consumers-and-lifetime-management"></a>Właściciele, konsumenci i zarządzanie całym życiem

Ponieważ bufory mogą być przekazywane między interfejsami API, a ponieważ bufory są czasami dostępne z wielu wątków, należy wziąć pod uwagę zarządzanie okresem istnienia. Istnieją trzy podstawowe pojęcia:

- **Własność**. Właściciel wystąpienia buforu jest odpowiedzialny za zarządzanie okresem istnienia, w tym niszczenie buforu, gdy nie jest już używany. Wszystkie bufory mają jednego właściciela. Zazwyczaj właściciel jest składnikiem, który utworzył bufor lub który odebrał bufor z fabryki. Własność może również zostać przeniesiona; **Component-A** może zrezygnować z kontroli nad buforem do **Składnik-B**, w którym to momencie **Component-A** może już nie używać buforu, a **Component-B** staje się odpowiedzialny za zniszczenie buforu, gdy nie jest już używany.

- **Zużycie**. Konsument wystąpienia buforu może używać wystąpienia buforu, odczytując z niego i ewentualnie zapisując do niego. Bufory mogą mieć jednego konsumenta naraz, chyba że podano jakiś mechanizm synchronizacji zewnętrznej. Należy zauważyć, że aktywny konsument buforu niekoniecznie jest właścicielem buforu.

- **Leasing**. Dzierżawa to czas, przez jaki dany składnik może być konsumentem buforu.

Poniższy przykład pseudokodu ilustruje te trzy pojęcia. Zawiera `Main` metodę, która tworzy <xref:System.Memory%601> bufor typu, <xref:System.Char>wywołuje `WriteInt32ToBuffer` metodę do zapisu reprezentacji ciągu liczby całkowitej do buforu, a następnie wywołuje `DisplayBufferToConsole` metodę, aby wyświetlić wartość buforu.

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

Metoda `Main` tworzy bufor (w tym <xref:System.Span%601> przypadku wystąpienie) i tak jest jego właścicielem. W `Main` związku z tym jest odpowiedzialny za zniszczenie buforu, gdy nie jest już używany. Czyni to przez wywołanie <xref:System.Span%601.Clear?displayProperty=nameWithType> metody buforu. (Metoda <xref:System.Span%601.Clear> w tym miejscu faktycznie czyści <xref:System.Span%601> pamięć buforu; struktura nie ma w rzeczywistości metody, która niszczy bufor).)

Bufor ma dwóch `WriteInt32ToBuffer` konsumentów `DisplayBufferToConsole`i . Jest tylko jeden konsument naraz `WriteInt32ToBuffer`(najpierw , potem `DisplayBufferToConsole`), a żaden z konsumentów nie jest właścicielem bufora. Należy również zauważyć, że "konsument" w tym kontekście nie oznacza widok tylko do odczytu buforu; konsumenci mogą modyfikować zawartość buforu, `WriteInt32ToBuffer` podobnie jak w przypadku widoku odczytu/zapisu buforu.

Metoda `WriteInt32ToBuffer` ma dzierżawy na (może zużywać) buformiędzy rozpoczęciem wywołania metody i czas zwraca metoda. Podobnie ma `DisplayBufferToConsole` dzierżawy w buforze podczas wykonywania i dzierżawy jest zwalniany, gdy metoda rozwija. (Nie ma API do zarządzania leasingiem; "leasing" jest sprawą koncepcyjną.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Pamięć\<T> i model właściciela/konsumenta

Jak zauważa [sekcja Właściciele, konsumenci i zarządzanie okresem istnienia,](#owners-consumers-and-lifetime-management) bufor zawsze ma właściciela. Program .NET Core obsługuje dwa modele własności:

- Model, który obsługuje pojedynczej własności. Bufor ma jednego właściciela przez cały okres istnienia.

- Model, który obsługuje przeniesienie własności. Własność buforu może zostać przeniesiona z jego pierwotnego właściciela (jego twórcy) do innego składnika, który następnie staje się odpowiedzialny za zarządzanie okresem istnienia buforu. Ten właściciel może z kolei przenieść własność na inny składnik itd.

Interfejs służy <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> do jawnego zarządzania własnością buforu. <xref:System.Buffers.IMemoryOwner%601>obsługuje oba modele własności. Składnik, który <xref:System.Buffers.IMemoryOwner%601> ma odwołanie jest właścicielem buforu. W poniższym <xref:System.Buffers.IMemoryOwner%601?> przykładzie użyto wystąpienia <xref:System.Memory%601> w celu odzwierciedlenia własności buforu.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Możemy również napisać ten [`using`](../../csharp/language-reference/keywords/using-statement.md)przykład z:

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

W tym kodzie:

- Metoda `Main` przechowuje odwołanie do <xref:System.Buffers.IMemoryOwner%601> wystąpienia, `Main` więc metoda jest właścicielem buforu.

- Metody `WriteInt32ToBuffer` `DisplayBufferToConsole` i zaakceptować <xref:System.Memory%601> jako publiczny interfejs API. W związku z tym są konsumentami buforu. I spożywają go tylko jeden po drugim.

Mimo `WriteInt32ToBuffer` że metoda jest przeznaczona do zapisu `DisplayBufferToConsole` wartości do buforu, metoda nie jest. Aby to odzwierciedlić, mógł zaakceptować argument <xref:System.ReadOnlyMemory%601>typu . Aby uzyskać <xref:System.ReadOnlyMemory%601>dodatkowe informacje na temat , zobacz [reguła #2: Użyj\<ReadOnlySpan T> lub ReadOnlyMemory\<T>, jeśli bufor powinien być tylko do odczytu](#rule-2).

### <a name="ownerless-memoryt-instances"></a>Wystąpienia> pamięci\<"Ownerless" Memory T

Można utworzyć <xref:System.Memory%601> wystąpienie bez <xref:System.Buffers.IMemoryOwner%601>użycia . W takim przypadku własność buforu jest niejawna, a nie jawna i obsługiwany jest tylko model jednego właściciela. Można to zrobić przez:

- Wywołanie jednego <xref:System.Memory%601> z konstruktorów `T[]`bezpośrednio, przekazując w , jak w poniższym przykładzie nie.

- Wywołanie [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) metody rozszerzenia `ReadOnlyMemory<char>` do tworzenia wystąpienia.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Metoda, która początkowo <xref:System.Memory%601> tworzy wystąpienie jest niejawnym właścicielem buforu. Własność nie może zostać przeniesiona na <xref:System.Buffers.IMemoryOwner%601> żaden inny składnik, ponieważ nie ma żadnego przypadku ułatwiającego przeniesienie. (Alternatywnie można również sobie wyobrazić, że moduł zbierający elementy bezużyteczne w czasie wykonywania jest właścicielem buforu, a wszystkie metody po prostu zużywają bufor).

## <a name="usage-guidelines"></a>Wskazówki dotyczące użytkowania

Ponieważ blok pamięci jest własnością, ale jest przeznaczony do przekazania do wielu składników, z których niektóre mogą działać <xref:System.Memory%601> na <xref:System.Span%601>określonym bloku pamięci jednocześnie, ważne jest, aby ustanowić wytyczne dotyczące korzystania z obu i .  Wytyczne są niezbędne, ponieważ:

- Jest możliwe dla składnika, aby zachować odwołanie do bloku pamięci po jego właściciel zwolnił go.

- Jest możliwe dla składnika do pracy w buforze w tym samym czasie, że inny składnik działa na nim, w procesie uszkodzenia danych w buforze.

- Podczas gdy charakter przydzielonego stosoptymalizuje <xref:System.Span%601> wydajność i sprawia, że <xref:System.Span%601> preferowany typ do pracy w bloku pamięci, podlega również <xref:System.Span%601> niektórych głównych ograniczeń. Ważne jest, aby wiedzieć, <xref:System.Span%601> kiedy i <xref:System.Memory%601>kiedy używać .

Poniżej przedstawiono nasze zalecenia dotyczące <xref:System.Memory%601> pomyślnego korzystania z niego i powiązanych z nim typów. Należy pamiętać, że <xref:System.Memory%601> wskazówki, które mają zastosowanie do i <xref:System.Span%601> odnosi się również do <xref:System.ReadOnlyMemory%601> i <xref:System.ReadOnlySpan%601> chyba że wyraźnie zanotujemy inaczej.

**Reguła #1: W przypadku synchronicznego\<interfejsu API\<należy użyć span T> zamiast pamięci T> jako parametr, jeśli to możliwe.**

<xref:System.Span%601>jest bardziej wszechstronny <xref:System.Memory%601> niż i może reprezentować szerszą gamę ciągłych buforów pamięci. <xref:System.Span%601>oferuje również lepszą <xref:System.Memory%601>wydajność niż . Na koniec można <xref:System.Memory%601.Span?displayProperty=nameWithType> użyć właściwości <xref:System.Memory%601> do konwersji <xref:System.Span%601>wystąpienia do\<, chociaż Span T>-to-Memory\<T> konwersja nie jest możliwe. Więc jeśli dzwoniący stało <xref:System.Memory%601> się wystąpienie, będą mogli wywołać metody <xref:System.Span%601> z parametrami i tak.

Przy użyciu parametru <xref:System.Span%601> typu <xref:System.Memory%601> zamiast typu pomaga również napisać implementację metody poprawne. Automatycznie otrzymasz czeki w czasie kompilacji, aby upewnić się, że nie próbujesz uzyskać dostępu do buforu poza dzierżawą metody (więcej na ten temat później).

Czasami trzeba będzie użyć <xref:System.Memory%601> parametru zamiast <xref:System.Span%601> parametru, nawet jeśli jesteś w pełni synchroniczny. Być może interfejs API, który <xref:System.Memory%601> zależy akceptuje tylko argumenty. Jest to w porządku, ale należy pamiętać o <xref:System.Memory%601> kompromisów związanych z korzystaniem synchronicznie.

<a name="rule-2" />

**Reguła #2: Użyj\<readonlySpan T\<> lub ReadOnlyMemory T>, jeśli bufor powinien być tylko do odczytu.**

We wcześniejszych przykładach `DisplayBufferToConsole` metoda odczytuje tylko z buforu; nie modyfikuje zawartości buforu. Podpis metody należy zmienić na następujący.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

W rzeczywistości, jeśli połączymy tę regułę i regułę #1, możemy zrobić jeszcze lepiej i przepisać podpis metody w następujący sposób:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

Metoda `DisplayBufferToConsole` działa teraz z praktycznie każdym `T[]`typem buforu, jaki można sobie wyobrazić: , magazyn przydzielony z [stackalloc](../../csharp/language-reference/operators/stackalloc.md)i tak dalej. Można nawet przekazać <xref:System.String> bezpośrednio do niego!

**Reguła #3: Jeśli metoda\<akceptuje> `void`pamięci T i\<zwraca, nie należy używać wystąpienia> pamięci T po powrocie metody.**

Odnosi się to do wspomnianej wcześniej koncepcji "leasingu". Dzierżawa metody zwracania unieważnienia <xref:System.Memory%601> w wystąpieniu rozpoczyna się po wprowadzeniu metody i kończy się po zamknięciu metody. Należy wziąć pod uwagę `Log` następujący przykład, który wywołuje w pętli na podstawie danych wejściowych z konsoli.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Jeśli `Log` jest w pełni synchroniczną metodą, ten kod będzie zachowywać się zgodnie z oczekiwaniami, ponieważ istnieje tylko jeden aktywny konsument wystąpienia pamięci w danym momencie.
Ale wyobraźcie `Log` sobie, że ma to wdrożenie.

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

W tej `Log` implementacji narusza jego dzierżawy, <xref:System.Memory%601> ponieważ nadal próbuje użyć wystąpienia w tle po zwróceniu oryginalnej metody. Metoda `Main` może mutować buforpodczas `Log` próby odczytu z niego, co może spowodować uszkodzenie danych.

Istnieje kilka sposobów rozwiązania tego problemu:

- Metoda `Log` może zwrócić <xref:System.Threading.Tasks.Task> zamiast `void`, jak wykonuje `Log` następująca implementacja metody.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log`zamiast tego można zaimplementować w następujący sposób:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Reguła #4: Jeśli metoda\<akceptuje> pamięci T i zwraca zadanie, nie można używać wystąpienia> pamięci\<T po przejściu zadania do stanu terminala.**

To tylko asynchroniczne warianty reguły #3. Metoda `Log` z wcześniejszego przykładu może być napisana w następujący sposób, aby zachować zgodność z tą regułą:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

W tym miejscu "stan terminala" oznacza, że zadanie przechodzi do stanu ukończonego, uszkodzonego lub anulowanego. Innymi słowy,"stan końcowy" oznacza "wszystko, co spowodowałoby oczekiwanie na rzut lub kontynuowanie egzekucji".

Niniejsze wskazówki dotyczą metod, <xref:System.Threading.Tasks.Task>które <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask%601>zwracają , , lub podobnego typu.

**Reguła #5: Jeśli konstruktor akceptuje pamięć\<T> jako parametr, metody wystąpienia na\<skonstruowanym obiekcie są uważane za konsumentów wystąpienia> pamięci T.**

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

W tym `OddValueExtractor` miejscu konstruktor akceptuje `ReadOnlyMemory<int>` jako parametr konstruktora, więc `ReadOnlyMemory<int>` sam konstruktor jest konsumentem wystąpienia, a `ReadOnlyMemory<int>` wszystkie metody wystąpienia zwracanej wartości są również konsumentami oryginalnego wystąpienia. Oznacza to, `TryReadNextOddValue` że `ReadOnlyMemory<int>` zużywa wystąpienie, mimo że wystąpienie `TryReadNextOddValue` nie jest przekazywane bezpośrednio do metody.

**Reguła #6: Jeśli masz\<właściwość typu> typu ddefiniowaną pamięć T (lub równoważną metodę wystąpienia) na typie, metody wystąpienia tego obiektu są uważane za konsumentów wystąpienia> memory\<T.**

To jest naprawdę tylko wariant zasady #5. Ta reguła istnieje, ponieważ ustawiaczy właściwości lub równoważne metody są zakładane do przechwytywania i utrwalić swoje dane wejściowe, więc metody wystąpienia na tym samym obiekcie może korzystać ze stanu przechwyconego.

W poniższym przykładzie wyzwoliono następującą regułę:

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

**Reguła #7: Jeśli masz\<iMemoryOwner T> odwołania, należy w pewnym momencie usunąć go lub przenieść jego własności (ale nie oba).**

Ponieważ <xref:System.Memory%601> wystąpienie może być wspierane przez pamięć zarządzaną lub <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> niezarządzaną, właściciel <xref:System.Memory%601> musi wywołać po zakończeniu pracy wykonywanej w wystąpieniu. Alternatywnie właściciel może przenieść własność <xref:System.Buffers.IMemoryOwner%601> wystąpienia na inny składnik, w którym to momencie <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> składnik przejmujący staje się odpowiedzialny za wywołanie w odpowiednim czasie (więcej na ten temat później).

Niepowodzenie wywołania <xref:System.Buffers.MemoryPool%601.Dispose%2A> metody może prowadzić do przecieków pamięci niezarządzanej lub pogorszenia wydajności.

Ta reguła ma również zastosowanie do <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>kodu, który wywołuje metody fabryczne, takie jak . Obiekt wywołujący staje się właścicielem <xref:System.Buffers.IMemoryOwner%601> zwróconego i jest odpowiedzialny za usuwanie wystąpienia po zakończeniu.

**Reguła #8: Jeśli masz\<parametr IMemoryOwner T> na powierzchni interfejsu API, akceptujesz własność tego wystąpienia.**

Zaakceptowanie wystąpienia tego typu sygnalizuje, że składnik zamierza przejąć na własność to wystąpienie. Twój składnik staje się odpowiedzialny za prawidłowe usuwanie zgodnie z zasadą #7.

Każdy składnik, który <xref:System.Buffers.IMemoryOwner%601> przenosi własność wystąpienia do innego składnika nie należy już używać tego wystąpienia po zakończeniu wywołania metody.

> [!IMPORTANT]
> Jeśli konstruktor <xref:System.Buffers.IMemoryOwner%601> akceptuje jako parametr, <xref:System.IDisposable>jego typ <xref:System.IDisposable.Dispose%2A> powinien <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>implementować , a metoda powinna wywołać .

**Reguła #9: Jeśli zawijasz synchroniczną metodę p/invoke, interfejs API powinien zaakceptować> Span\<T jako parametr.**

Zgodnie z regułą #1, <xref:System.Span%601> jest zazwyczaj poprawny typ do użycia dla synchronicznych interfejsów API. Wystąpienia można <xref:System.Span%601> przypiąć za pomocą słowa kluczowego, [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) jak w poniższym przykładzie.

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

W poprzednim przykładzie `pbData` może być null, jeśli na przykład zakres wejściowy jest pusty. Jeśli wyeksportowana metoda `pbData` absolutnie wymaga, aby `cbData` być non-null, nawet jeśli jest 0, metoda może być zaimplementowana w następujący sposób:

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

**Reguła #10: Jeśli zawijasz metodę asynchroniczną p/invoke, interfejs API powinien akceptować> pamięci\<T jako parametr.**

Ponieważ nie można [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) użyć słowa kluczowego w operacjach asynchronicznych, należy użyć <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> metody do przypinania <xref:System.Memory%601> wystąpień, niezależnie od rodzaju ciągłej pamięci, którą reprezentuje wystąpienie. W poniższym przykładzie pokazano, jak używać tego interfejsu API do wykonywania asynchronicznego wywołania p/invoke.

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

## <a name="see-also"></a>Zobacz też

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
