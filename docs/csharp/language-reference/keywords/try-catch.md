---
title: try-catch - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: 3d4315a09869b77b4ae8cbb43646f9a96280b678
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173474"
---
# <a name="try-catch-c-reference"></a>try-catch (odwołanie w C#)

Try-catch instrukcja składa `try` się z bloku, a następnie jeden lub więcej `catch` klauzul, które określają programy obsługi dla różnych wyjątków.

Gdy wyjątek, czas wykonywania języka wspólnego (CLR) `catch` szuka instrukcji, która obsługuje ten wyjątek. Jeśli aktualnie wykonywana metoda nie `catch` zawiera takiego bloku, CLR patrzy na metodę, która nazywa bieżącą metodę i tak dalej stosu wywołań. Jeśli `catch` nie zostanie znaleziony żaden blok, clr wyświetla nieobsługiwany komunikat o wyjątku dla użytkownika i zatrzymuje wykonywanie programu.

Blok `try` zawiera kod strzeżony, który może spowodować wyjątek. Blok jest wykonywany, dopóki nie zostanie zgłoszony wyjątek lub zostanie pomyślnie ukończony. Na przykład następująca próba `null` rzutować <xref:System.NullReferenceException> obiekt wywołuje wyjątek:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

Mimo `catch` że klauzula może służyć bez argumentów do przechwycania dowolnego typu wyjątku, to użycie nie jest zalecane. Ogólnie rzecz biorąc należy przechwycić tylko te wyjątki, które wiesz, jak odzyskać z. W związku z tym należy zawsze <xref:System.Exception?displayProperty=nameWithType> określić argument obiektu pochodzące z na przykład:

```csharp
catch (InvalidCastException e)
{
}
```

Istnieje możliwość użycia więcej niż `catch` jednej określonej klauzuli w tej samej instrukcji try-catch. W takim przypadku kolejność `catch` klauzul jest ważna, ponieważ `catch` klauzule są badane w kolejności. Złap bardziej szczegółowe wyjątki przed mniej szczegółowymi. Kompilator generuje błąd, jeśli zamówisz catch bloki tak, że nowszy blok nigdy nie można osiągnąć.

Za `catch` pomocą argumentów jest jednym ze sposobów filtrowania wyjątków, które chcesz obsłużyć.  Można również użyć filtru wyjątków, który dodatkowo sprawdza wyjątek, aby zdecydować, czy go obsłużyć.  Jeśli filtr wyjątków zwraca false, a następnie wyszukiwanie obsługi nadal.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Filtry wyjątków są lepsze niż przechwytywanie i wyrzucanie (wyjaśnione poniżej), ponieważ filtry pozostawiają stos bez szwanku.  Jeśli później obsługi zrzutu stosu, można zobaczyć, gdzie wyjątek pierwotnie pochodzi, a nie tylko ostatnie miejsce został ponownie wyrzucony.  Typowe użycie wyrażeń filtru wyjątków jest rejestrowanie.  Można utworzyć filtr, który zawsze zwraca false, który również dane wyjściowe do dziennika, można rejestrować wyjątki, jak przejść bez konieczności ich obsługi i rethrow.

Throw [throw](throw.md) Instrukcji może służyć `catch` w bloku, aby ponownie zgłosić wyjątek, który jest przechwycone przez instrukcję. `catch` Poniższy przykład wyodrębnia informacje <xref:System.IO.IOException> o źródle z wyjątku, a następnie zgłasza wyjątek do metody nadrzędnej.

```csharp
catch (FileNotFoundException e)
{
    // FileNotFoundExceptions are handled here.
}
catch (IOException e)
{
    // Extract some information from this exception, and then
    // throw it to the parent method.
    if (e.Source != null)
        Console.WriteLine("IOException source: {0}", e.Source);
    throw;
}
```

Można przechwycić jeden wyjątek i zgłosić inny wyjątek. Po złożeniu tej czynności określ wyjątek, który został przechwycony jako wyjątek wewnętrzny, jak pokazano w poniższym przykładzie.

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

Można również ponownie zgłosić wyjątek, gdy określony warunek jest true, jak pokazano w poniższym przykładzie.

```csharp
catch (InvalidCastException e)
{
    if (e.Data == null)
    {
        throw;
    }
    else
    {
        // Take some action.
    }
}
```

> [!NOTE]
> Możliwe jest również użycie filtru wyjątków, aby uzyskać podobny wynik w często czystszy sposób (a także nie modyfikować stosu, jak wyjaśniono wcześniej w tym dokumencie). Poniższy przykład ma podobne zachowanie dla wywoływania jak w poprzednim przykładzie. Funkcja wyrzuca `InvalidCastException` z powrotem do `e.Data` obiektu `null`wywołującego, gdy jest .
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

Z wewnątrz `try` bloku, inicjowanie tylko zmienne, które są zadeklarowane w nim. W przeciwnym razie może wystąpić wyjątek przed wykonaniem bloku jest zakończona. Na przykład w poniższym przykładzie `n` kodu zmienna `try` jest inicjowana wewnątrz bloku. Próba użycia tej zmiennej `try` poza `Write(n)` blokiem w instrukcji wygeneruje błąd kompilatora.

```csharp
static void Main()
{
    int n;
    try
    {
        // Do not initialize this variable here.
        n = 123;
    }
    catch
    {
    }
    // Error: Use of unassigned local variable 'n'.
    Console.Write(n);
}
```

Aby uzyskać więcej informacji na temat catch, zobacz [try-catch-finally](try-catch-finally.md).

## <a name="exceptions-in-async-methods"></a>Wyjątki w metodach asynchronicznej

Metoda asynchroniczna jest oznaczona modyfikatorem [asynchronii](async.md) i zwykle zawiera jedno lub więcej wyrażeń lub instrukcji await. Wyrażenie await stosuje operator [await](../operators/await.md) <xref:System.Threading.Tasks.Task> do <xref:System.Threading.Tasks.Task%601>a lub .

Gdy formant osiągnie `await` w metodzie asynchronicznej, postęp w metodzie jest zawieszony, dopóki nie zostanie ukończone oczekiwane zadanie. Po zakończeniu zadania wykonanie można wznowić w metodzie. Aby uzyskać więcej informacji, zobacz [Programowanie asynchroniczne z async i await](../../programming-guide/concepts/async/index.md) i [Control Flow w programach asynchronicznych](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Ukończone zadanie, `await` do którego jest stosowany może być w stanie błędnym z powodu nieobsługiwanego wyjątku w metodzie, która zwraca zadanie. Oczekiwanie na zadanie zgłasza wyjątek. Zadanie może również zakończyć się w stanie anulowanym, jeśli proces asynchroniczny, który go zwraca, zostanie anulowany. Oczekiwanie na anulowane zadanie wysuwa plik `OperationCanceledException`. Aby uzyskać więcej informacji na temat anulowania procesu asynchronicznego, zobacz [Dostrajanie aplikacji asynchronicznej](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Aby przechwycić wyjątek, poczekaj `try` na zadanie w bloku i `catch` przechwyć wyjątek w skojarzonym bloku. Na przykład zobacz [przykładową sekcję Metoda asynchronicznej.](#async-method-example)

Zadanie może być w stanie błędnym, ponieważ wystąpiło wiele wyjątków w oczekiwanej metodzie asynchronicznej. Na przykład zadanie może być wynikiem wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Gdy oczekujesz na takie zadanie, tylko jeden z wyjątków jest przechwycone i nie można przewidzieć, który wyjątek zostanie przechwycona. Na przykład zobacz [Task.WhenAll przykładsekcji.](#taskwhenall-example)

## <a name="example"></a>Przykład

W poniższym `try` przykładzie blok zawiera wywołanie `ProcessString` metody, która może spowodować wyjątek. Klauzula `catch` zawiera program obsługi wyjątków, który po prostu wyświetla komunikat na ekranie. Gdy `throw` instrukcja jest `MyMethod`wywoływana od wewnątrz, system szuka `catch` `Exception caught`instrukcji i wyświetla komunikat .

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a>Przykład dwóch bloków catch

W poniższym przykładzie używane są dwa bloki catch, a najbardziej szczegółowy wyjątek, który jest pierwszy, jest przechwycony.

Aby przechwycić najmniej szczegółowy wyjątek, można `ProcessString` zastąpić throw instrukcji `throw new Exception()`w następującej instrukcji: .

Jeśli w przykładzie najpierw umieścisz najmniej specyficzny blok catch, zostanie wyświetlony następujący komunikat o błędzie: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a>Przykład metody asynchronicznej

W poniższym przykładzie przedstawiono obsługę wyjątków dla metod asynchronii. Aby przechwycić wyjątek, który zgłasza zadanie `await` asynchroniczne, umieść wyrażenie `try` w `catch` bloku i przechwyć wyjątek w bloku.

Odkomentuj `throw new Exception` wiersz w przykładzie, aby zademonstrować obsługę wyjątków. Właściwość zadania jest ustawiona `True`na , `Exception.InnerException` właściwość zadania jest ustawiona na wyjątek, a `catch` wyjątek jest przechwycone w bloku. `IsFaulted`

Odkomentuj `throw new OperationCanceledException` wiersz, aby zademonstrować, co się dzieje po anulowaniu procesu asynchronicznego. `IsCanceled` Właściwość zadania jest ustawiona `true`na , a wyjątek `catch` jest przechwycone w bloku. W niektórych warunkach, które nie mają zastosowania do `IsFaulted` tego przykładu, właściwość zadania jest ustawiona `true` na i `IsCanceled` jest ustawiona na `false`.

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a>Task.WhenAll przykład

W poniższym przykładzie przedstawiono obsługę wyjątków, gdzie wiele zadań może spowodować wiele wyjątków. Blok `try` czeka na zadanie, które jest zwracane <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>przez wywołanie . Zadanie zostanie ukończone po zakończeniu trzech zadań, do których jest stosowana WhenAll.

Każde z trzech zadań powoduje wyjątek. Blok `catch` iteruje za pomocą wyjątków, `Exception.InnerExceptions` które znajdują się we właściwości <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>zadania, który został zwrócony przez .

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [instrukcja wypróbuj](~/_csharplang/spec/statements.md#the-try-statement) [specyfikację języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje try, throw i catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
