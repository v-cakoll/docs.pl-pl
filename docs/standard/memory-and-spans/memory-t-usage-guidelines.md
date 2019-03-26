---
title: Pamięć<T> i zakres<T> wytyczne dotyczące użycia
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a72e90a6233d03fd641675bfbeee2145709e57fe
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463153"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Pamięć\<T > i zakres\<T > wytyczne dotyczące użycia

.NET core zawiera wiele typów, które reprezentują dowolnego niego ciągły region pamięci. .NET core 2.0 wprowadzono <xref:System.Span%601> i <xref:System.ReadOnlySpan%601>, buforów pamięci uproszczone, które mogą być wspierany przez, które są zarządzane lub niezarządzane pamięci. Te typy mogą być przechowywane w stosie, dlatego mogą nie nadaje się do liczby scenariuszy, w tym wywołania metody asynchronicznej. .NET core 2.1 dodaje szereg dodatkowych typów, w tym <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, i <xref:System.Buffers.MemoryPool%601>. Podobnie jak <xref:System.Span%601>, <xref:System.Memory%601> i jego powiązanych typów może być zabezpieczony za pomocą zarządzanych i niezarządzanych pamięci. W odróżnieniu od <xref:System.Span%601>, <xref:System.Memory%601> mogą być przechowywane tylko na stosie zarządzanym.

Zarówno <xref:System.Span%601> i <xref:System.Memory%601> są buforów danych strukturalnych, który może służyć w potokach. Oznacza to, że są one przeznaczone tak, aby niektóre lub wszystkie dane mogą być skutecznie przekazywane do składniki w potoku, które mogą je przetworzyć i opcjonalnie modyfikują bufor. Ponieważ <xref:System.Memory%601> i jej powiązane typy można uzyskać dostęp przez kilka składników lub przez wiele wątków, ważne jest, deweloperzy wykonać niektóre wytyczne standardowego użycia, aby utworzyć niezawodny kod.

## <a name="owners-consumers-and-lifetime-management"></a>Właściciele, klientów i zarządzanie okresem istnienia

Ponieważ bufory można przekazać wokół między interfejsami API, a ponieważ buforów czasami dostęp jest możliwy z wielu wątków, należy wziąć pod uwagę zarządzanie okresem istnienia. Istnieją trzy podstawowe pojęcia:

- **Własność**. Właściciel wystąpienie buforu jest odpowiedzialny za zarządzanie okresem istnienia, w tym zniszczenie buforu, gdy nie jest już używana. Wszystkie bufory zostały jednego właściciela. Ogólnie rzecz biorąc właściciel jest składnik, który utworzył buforu lub te, które otrzymały buforu z fabryki. Można również przenieść własność; **Składnik A** można zwalnia bufor do **B składnika**, w tym momencie **składnik A** nie mogą korzystać z buforu, i **składnika B**  staje się odpowiedzialny za zniszczenie buforu, gdy nie jest już używana.

- **Użycie**. Konsument wystąpienie buforu może użyć wystąpienia buforu przez odczytanie z niego i prawdopodobnie zapisywania. Bufory może mieć jednego użytkownika w czasie, ile pewien mechanizm synchronizacji zewnętrznych. Należy pamiętać o tym, czy active konsumenta bufor niekoniecznie właściciela buforu.

- **Dzierżawy**. Dzierżawa jest czas, który może być konsumenta buforu określonego składnika.

Poniższy przykład pseudo-kodu przedstawiono te trzy pojęcia. Zawiera on `Main` metody, która tworzy wystąpienie <xref:System.Memory%601> bufora o typie <xref:System.Char>, wywołania `WriteInt32ToBuffer` metodę, aby zapisać ciąg reprezentujący liczbę całkowitą do buforu, a następnie wywołuje `DisplayBufferToConsole` metodę, aby wyświetlić wartość bufor.

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
        try {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally {
            buffer.Destroy();
        }
    }
}
```

`Main` Metoda tworzy buforu (w tym przypadku <xref:System.Span%601> wystąpienia) i dlatego jest jego właścicielem. W związku z tym `Main` jest odpowiedzialny za zniszczenie buforu, gdy nie jest już używana. Jest to realizowane przez wywołanie metody buforu <xref:System.Span%601.Clear?displayProperty=nameWithType> metody. ( <xref:System.Span%601.Clear> Metoda tutaj faktycznie Czyści pamięć buforu; <xref:System.Span%601> struktura faktycznie nie zawiera metody, która niszczy buforu.)

Bufor składa się z dwóch konsumentów `WriteInt32ToBuffer` i `DisplayBufferToConsole`. Istnieje tylko jednego użytkownika w czasie (pierwszy `WriteInt32ToBuffer`, następnie `DisplayBufferToConsole`), a właścicielem żadnego konsumentów buforu. Należy zauważyć, że "klienta" w tym kontekście nie implikują widok tylko do odczytu buforu; klientów można modyfikować zawartość buforu jako `WriteInt32ToBuffer` się dzieje, jeśli widok odczytu/zapisu buforu.

`WriteInt32ToBuffer` Metoda ma dzierżawę (mogą wykorzystywać) buforu między początkiem wywołania metody a czas, metoda zwraca wartość. Podobnie `DisplayBufferToConsole` ma dzierżawę na buforze, podczas wykonywania i dzierżawy jest zwalniany, gdy metoda rozwija. (Nie ma żadnych interfejsów API do zarządzania dzierżawy; "dzierżawy" jest kwestią koncepcyjny).

## <a name="memoryt-and-the-ownerconsumer-model"></a>Pamięć\<T > i model właściciela i odbiorcy

Jako [właściciele, klientów i zarządzanie okresem istnienia](#owners-consumers-and-lifetime-management) informacje o sekcji, bufor zawsze ma właściciela. Program .NET core obsługuje dwa modele własności:

- Model, który obsługuje jednego właściciela. Bufor składa się z jednego właściciela dla jego cały okres istnienia.

- Model, który obsługuje przenoszenie własności. Własność buforu można przenieść z jej właścicielem (twórcy) do innego składnika, która staje się odpowiedzialni za zarządzanie okresem istnienia buforu. Ten właściciel z kolei może przenieść własność na innego składnika i tak dalej.

Możesz użyć <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interfejsu jawnego zarządzania własności buforu. <xref:System.Buffers.IMemoryOwner%601> obsługuje oba modele własności. Składnik, który ma <xref:System.Buffers.IMemoryOwner%601> odwołanie jest właścicielem buforu. W poniższym przykładzie użyto <xref:System.Buffers.IMemoryOwner%601?> wystąpienia, aby odzwierciedlić własności <xref:System.Memory%601> buforu.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Ten przykład z można także napisać [ `using` ](~/docs/csharp/language-reference/keywords/using-statement.md):

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

W tym kodzie:

- `Main` Metoda zawiera odwołanie do <xref:System.Buffers.IMemoryOwner%601> wystąpienia, więc `Main` metody jest właścicielem buforu.

- `WriteInt32ToBuffer` i `DisplayBufferToConsole` metody akceptują xref:System.Memory%601 > jako publiczny interfejs API. W związku z tym są one konsumentów buforu. I tylko zużywają go jednym naraz.

Mimo że `WriteInt32ToBuffer` metoda jest przeznaczona do zapisu wartości w buforze `DisplayBufferToConsole` metoda nie jest. Aby to odzwierciedlić go może zaakceptowali argumentu typu <xref:System.ReadOnlyMemory%601>. Aby uzyskać dodatkowe informacje na temat <xref:System.ReadOnlyMemory%601>, zobacz [reguły nr 2: Użyj ReadOnlySpan\<T > lub ReadOnlyMemory\<T >, jeśli bufor ma być tylko do odczytu](#rule-2).

### <a name="ownerless-memoryt-instances"></a>"Ownerless" pamięci\<T > wystąpień

Możesz utworzyć <xref:System.Memory%601> wystąpienia bez użycia <xref:System.Buffers.IMemoryOwner%601>. W tym przypadku własności buforu jest niejawny zamiast jawnego i tylko model jednego właściciela jest obsługiwany. Można to zrobić:

- Wywołanie jednej z <xref:System.Memory%601> konstruktory bezpośrednio, przekazując `T[]`, tak jak w poniższym przykładzie.

- Wywoływanie [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) metodę rozszerzenia, aby wygenerować `ReadOnlyMemory<char>` wystąpienia.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Metody, która początkowo <xref:System.Memory%601> wystąpienie jest niejawne właściciela buforu. Własność nie można przenosić do innych składników, ponieważ nie istnieje żadne <xref:System.Buffers.IMemoryOwner%601> wystąpienia w celu ułatwienia transferu. (Jako alternatywę, można także wyobrazić sobie, moduł odśmiecania pamięci środowiska wykonawczego jest właścicielem buforu i wszystkie metody tylko używanie buforu.)

## <a name="usage-guidelines"></a>Wytyczne dotyczące użycia

Ponieważ blok pamięci jest właścicielem, ale jest przeznaczona do przekazania do wielu składników, z których część może działać po bloku pamięci jednocześnie, to ważne, aby ustanowić wytyczne dotyczące korzystania z obu <xref:System.Memory%601> i <xref:System.Span%601>.  Wytyczne są niezbędne, ponieważ:

- Istnieje możliwość dla składnika, aby zachować odwołanie do bloku pamięci, po jego właściciela została wydana go.

- Istnieje możliwość dla składnika może działać w buforze w tym samym czasie, który inny składnik działa na nim w procesie uszkodzenie danych w buforze.

- While przydzielanych ze stosów rodzaj <xref:System.Span%601> optymalizację wydajności i sprawia, że <xref:System.Span%601> preferowany typ pracy w bloku pamięci, ona też przedmioty <xref:System.Span%601> do niektórych ograniczeń główne ograniczenia. Ważne jest, aby wiedzieć, kiedy należy używać <xref:System.Span%601> i kiedy należy używać <xref:System.Memory%601>.

Oto Nasze zalecenia dotyczące korzystania z pomyślnie <xref:System.Memory%601> i jej powiązane typy. Należy pamiętać, że wskazówki, które ma zastosowanie do <xref:System.Memory%601> i <xref:System.Span%601> dotyczy także <xref:System.ReadOnlyMemory%601> i <xref:System.ReadOnlySpan%601> , chyba że firma Microsoft wyraźnie należy pamiętać, w przeciwnym razie.

**Reguła #1: Synchroniczne interfejsu API, należy użyć zakresu\<T > zamiast pamięci\<T > jako parametru, jeśli jest to możliwe.**

<xref:System.Span%601> jest bardziej wszechstronna niż <xref:System.Memory%601> i może reprezentować szeroką gamę buforów pamięci ciągłej. <xref:System.Span%601> Ponadto zapewnia większą wydajność niż <xref:System.Memory%601>>. Na koniec można użyć <xref:System.Memory%601.Span?displayProperty=nameWithType> właściwości, aby przekonwertować <xref:System.Memory%601> wystąpienia do <xref:System.Span%601>, chociaż zakresu\<T > - do - pamięci\<T > Konwersja nie jest możliwe. Tak, jeśli mają swoje obiekty wywołujące <xref:System.Memory%601> wystąpienia będą możliwe do wywołania metody z <xref:System.Span%601> parametry mimo to.

Za pomocą parametru typu <xref:System.Span%601> zamiast typu <xref:System.Memory%601> umożliwia też zapisu poprawne konsumencki implementacji metody. Automatycznie uzyskasz kontroli czasu kompilacji, aby upewnić się, że użytkownik nie próbujesz uzyskać dostęp w buforze poza dzierżawy Twojej formy, (uzyskać więcej informacji na ten temat poniżej).

Czasami musisz użyć <xref:System.Memory%601> parametr zamiast <xref:System.Span%601> parametru, nawet jeśli jesteś w pełni synchroniczne. Przykład interfejsu API, który zależy Twoja praca akceptuje tylko <xref:System.Memory%601> argumentów. Jest to poprawne, ale należy pamiętać o kompromisy związane, korzystając z <xref:System.Memory%601> synchronicznie.

<a name="rule-2" />

**Reguła #2: Użyj ReadOnlySpan\<T > lub ReadOnlyMemory\<T >, jeśli bufor ma być tylko do odczytu.**

W przypadku wcześniejszych przykładów `DisplayBufferToConsole` odczytuje tylko metody z buforu; go nie modyfikuje zawartość buforu. Podpis metody należy je zmienić poniżej.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

W rzeczywistości Jeśli połączono tej reguły i zasady nr 1, możemy zrobić jeszcze lepiej i ponowne zapisywanie adresów podpis metody:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

`DisplayBufferToConsole` Metoda współpracuje teraz z niemal każdego typu buforu imaginable: `T[]`, Magazyn jest przydzielany za pomocą [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md)i tak dalej. Możesz nawet przekazać <xref:System.String> bezpośrednio do niego!

**Reguła #3: Jeśli metoda akceptuje pamięci\<T > i zwraca `void`, nie można używać pamięci\<T > wystąpienie, po powrocie z metody.**

Odnosi się to do pojęcia "dzierżawa" wspomnianych wcześniej. Dzierżawa metodę zwracającą typ void <xref:System.Memory%601> wystąpienia rozpoczyna się po wprowadzeniu metody i go kończy się, gdy metoda kończy działanie. Rozważmy następujący przykład wywołuje `Log` w pętli, na podstawie danych wejściowych z konsoli.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Jeśli `Log` jest metodą synchroniczną pełni ten kod będzie działać zgodnie z oczekiwaniami, ponieważ istnieje tylko jeden aktywny konsumenta wystąpienia pamięci w danym momencie.
Ale zamiast tego Załóżmy, że `Log` ma tę implementację.

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() => {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);    });
}
```

W tej implementacji `Log` narusza swojej dzierżawy, ponieważ nadal próbuje ona użyć <xref:System.Memory%601> wystąpienia w tle po zwrócił oryginalną metodę. `Main` Metoda można zmutować bufora podczas `Log` próbuje odczytać z niego, co może spowodować uszkodzenie danych.

Istnieje kilka sposobów, aby rozwiązać ten problem:

- `Log` Metoda może zwracać <xref:System.Threading.Tasks.Task> zamiast `void`, jako wykonania następujących `Log` metody.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log` Zamiast tego można zaimplementować w następujący sposób:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Reguła #4: Jeśli metoda akceptuje pamięci\<T > i zwraca klasę Task, nie można używać pamięć\<T > wystąpienie po przejścia do zadań, aby stan końcowy.**

Jest to po prostu wariant async reguły nr 3. `Log` Metody z poprzedniego przykładu mogą być zapisywane w następujący sposób są zgodne z tą regułą:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

W tym miejscu "Stan końcowy" oznacza, że wystąpił błąd przejścia do zadań, aby ukończone, lub anulowane stanu. Innymi słowy "Stan końcowy" oznacza "wszystko, co mogłoby spowodować await throw lub kontynuować wykonywanie."

Te wskazówki dotyczą metod, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, lub dowolny typ podobne.

**Reguła #5: Jeśli konstruktora akceptuje pamięci\<T > jako parametru, metodami wystąpień w utworzonym obiekcie są zakłada się, że konsumenci pamięci\<T > wystąpienia.**

Rozważmy następujący przykład:

```csharp
class OddValueExtractor {
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

W tym miejscu `OddValueExtractor` Konstruktor akceptuje `ReadOnlyMemory<int>` jako parametr konstruktora sam Konstruktor więc konsumenta `ReadOnlyMemory<int>` wystąpienie, a wszystkie metody wystąpienia, w zwracanej wartości są również konsumentów oryginalny `ReadOnlyMemory<int>` wystąpienie. Oznacza to, że `TryReadNextOddValue` zużywa `ReadOnlyMemory<int>` wystąpienia, nawet jeśli wystąpienie nie jest przekazywana bezpośrednio do `TryReadNextOddValue` metody.

**Reguła #6: Jeśli masz można ustawić pamięci\<T > — właściwości z określonym typem (lub metodą wystąpienia równoważne) od typu, metody wystąpienia obiektu, na którym są zakłada się, że konsumenci pamięci\<T > wystąpienia.**

Jest to tylko w wariancie reguły nr 5. Ta reguła istnieje, ponieważ metod ustawiających właściwości lub metody równoważne są uznawane za przechwytywanie i zachować swoje dane wejściowe, więc metodami wystąpień w tym samym obiekcie mogących wykorzystywać przechwyconego stanu.

Poniższy przykład wyzwala tej reguły:

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

**Reguła #7: Jeśli masz IMemoryOwner\<T > odwołania, należy w pewnym punktu usuwać je lub przenieść własność (ale nie obu).**

Ponieważ <xref:System.Memory%601> wystąpienia może być zabezpieczony za pomocą zarządzanych lub niezarządzanych pamięci, należy wywołać właściciela <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> gdy praca jest wykonywana na <xref:System.Memory%601> wystąpienie zostało zakończone. Alternatywnie właściciel może przenieść własność <xref:System.Buffers.IMemoryOwner%601> wystąpienia inny składnik, w tym momencie uzyskiwania składnik jest odpowiedzialny za wywołanie <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> w odpowiednim czasie (więcej informacji na ten temat poniżej).

Nie można wywołać <xref:System.Buffers.MemoryPool%601.Dispose%2A> metoda może prowadzić do przecieków pamięci niezarządzanej lub innych spadek wydajności.

Ta reguła obowiązuje także kod, który wywołuje fabryki metod, takich jak <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>. Obiekt wywołujący staje się właścicielem zwracanego <xref:System.Buffers.IMemoryOwner%601> i jest odpowiedzialny za usuwanie wystąpienia, po zakończeniu.

**Reguła #8: Jeśli masz IMemoryOwner\<T > parametru w swojej powierzchni interfejsu API są akceptowane własności tego wystąpienia.**

Akceptowanie wystąpienia tego typu sygnalizuje, że zamierza przejąć prawo własności tego wystąpienia składnika. Składnik staje się odpowiedzialny za właściwe usuwania zgodnie z reguły #7.

Dowolny składnik, który przenosi własności <xref:System.Buffers.IMemoryOwner%601> wystąpienia do innego składnika już nie należy używać tego wystąpienia, po zakończeniu wywołania metody.

> [!IMPORTANT]
> Jeśli konstruktora akceptuje <xref:System.Buffers.IMemoryOwner%601> jako parametru, jego typ powinien implementować <xref:System.IDisposable>i <xref:System.IDisposable.Dispose%2A> powinny wywoływać metodę <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.

**Reguła #9: Jeżeli metoda synchroniczna p/invoke, interfejs API powinien akceptować zakres\<T > jako parametr.**

Zgodnie z zasadą #1 <xref:System.Span%601> ogólnie jest poprawnego typu na potrzeby synchronicznych interfejsów API. Możesz przypiąć <xref:System.Span%601> \<T > wystąpień za pośrednictwem [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) — słowo kluczowe, jak w poniższym przykładzie.

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

W poprzednim przykładzie `pbData` może mieć wartości null, jeśli na przykład zakres danych wejściowych jest pusta. Jeśli metoda wyeksportowanego absolutnie wymaga, aby `pbData` wartości inne niż null, nawet jeśli `cbData` wynosi 0, metody można zaimplementować w następujący sposób:

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

**Reguła #10: Jeżeli metodą asynchroniczną p/invoke, interfejs API powinien akceptować pamięci\<T > jako parametr.**

Ponieważ nie można użyć [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) — słowo kluczowe w operacji asynchronicznych, możesz użyć <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> metodę, aby przypiąć <xref:System.Memory%601> wystąpień, niezależnie od rodzaju ciągłej pamięci, które reprezentuje wystąpienie. Poniższy przykład pokazuje, jak wykonać wywołanie asynchroniczne p/invoke za pomocą tego interfejsu API.

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
    var state = new MyCompletedCallbackState {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state;

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    } catch {
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

    if (error) { actualState.Tcs.SetException(...); }
    else { actualState.Tcs.SetResult(result); }
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
