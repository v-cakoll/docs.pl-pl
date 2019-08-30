---
title: try-catch- C# Reference
ms.custom: seodec18
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
ms.openlocfilehash: 8f901bd8ab5dcdcf4f5674e3f235267c9f535725
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168719"
---
# <a name="try-catch-c-reference"></a>try-catch (odwołanie w C#)

Instrukcja try-catch składa się z `try` bloku, po którym następuje co `catch` najmniej jedna klauzula, która określa programy obsługi dla różnych wyjątków.

Gdy wyjątek jest zgłaszany, środowisko uruchomieniowe języka wspólnego (CLR) wyszukuje `catch` instrukcję, która obsługuje ten wyjątek. Jeśli aktualnie wykonywana metoda nie zawiera takiego `catch` bloku, środowisko CLR przegląda metodę, która wywołała bieżącą metodę, i tak dalej na stosie wywołań. Jeśli nie `catch` zostanie znaleziony żaden blok, środowisko CLR wyświetli komunikat o nieobsługiwanym wyjątku dla użytkownika i zakończy wykonywanie programu.

`try` Blok zawiera chroniony kod, który może spowodować wyjątek. Blok jest wykonywany do momentu wyrzucania wyjątku lub zostanie ukończony pomyślnie. Na przykład następująca próba rzutowania `null` obiektu <xref:System.NullReferenceException> zgłasza wyjątek:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

`catch` Chociaż klauzula może być używana bez argumentów do przechwytywania dowolnego typu wyjątku, to użycie nie jest zalecane. Ogólnie rzecz biorąc, należy jedynie przechwycić te wyjątki, z których wiadomo, jak odzyskać. W związku z <xref:System.Exception?displayProperty=nameWithType> tym zawsze należy określić argument obiektu pochodny na przykład:

```csharp
catch (InvalidCastException e)
{
}
```

Istnieje możliwość użycia więcej niż jednej klauzuli określonej `catch` w tej samej instrukcji try-catch. W tym przypadku kolejność `catch` klauzul jest ważna, `catch` ponieważ klauzule są badane w kolejności. Przechwyć bardziej szczegółowe wyjątki przed bardziej szczegółowymi. Kompilator generuje błąd w przypadku uporządkowania bloków catch w taki sposób, aby można było nigdy nie dotrzeć do późniejszego bloku.

Używanie `catch` argumentów jest jednym ze sposobów filtrowania wyjątków, które mają być obsługiwane.  Można również użyć filtru wyjątków, który dodatkowo bada wyjątek, aby zdecydować, czy go obsłużyć.  Jeśli filtr wyjątku zwraca wartość false, wyszukiwanie programu obsługi jest kontynuowane.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Filtry wyjątków są preferowane do przechwytywania i ponownego zgłaszania (wyjaśniono poniżej), ponieważ filtry pozostawiają nienaruszony stos.  Jeśli w późniejszym czasie program obsługi będzie zrzucał stos, zobaczysz miejsce, z którego pochodzi wyjątek, a nie tylko ostatnie miejsce, które zostało ponownie zgłoszone.  Typowym zastosowaniem wyrażeń filtrów wyjątków jest rejestrowanie.  Można utworzyć filtr, który zawsze zwraca wartość false, która również prowadzi do dziennika, można rejestrować wyjątki w miarę ich wykonywania, bez konieczności ich obsługi i ponownego zgłaszania.

Instrukcji [throw](throw.md) można użyć w `catch` bloku, aby ponownie zgłosić wyjątek, który `catch` jest przechwytywany przez instrukcję. Poniższy przykład wyodrębnia informacje źródłowe z <xref:System.IO.IOException> wyjątku, a następnie zgłasza wyjątek do metody nadrzędnej.

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

Możesz przechwytywać jeden wyjątek i zgłosić inny wyjątek. Gdy to zrobisz, określ wyjątek, który został przechwycony jako wyjątek wewnętrzny, jak pokazano w poniższym przykładzie.

```csharp
catch (InvalidCastException e) 
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

Możesz również ponownie zgłosić wyjątek, gdy określony warunek ma wartość true, jak pokazano w poniższym przykładzie.

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
> Istnieje również możliwość użycia filtru wyjątków, aby uzyskać podobny wynik w sposób, który jest w sposób bardziej przejrzysty (a także bez modyfikowania stosu, jak wyjaśniono wcześniej w tym dokumencie). Poniższy przykład ma podobne zachowanie w przypadku wywołujących w poprzednim przykładzie. Funkcja zwraca `InvalidCastException` z powrotem do obiektu wywołującego, `e.Data` gdy `null`ma wartość.
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null) 
> {
>     // Take some action.
> }
> ``` 

Z wewnątrz `try` bloku należy inicjować tylko zmienne, które są w nim zadeklarowane. W przeciwnym razie może wystąpić wyjątek przed ukończeniem wykonywania bloku. Na przykład, w poniższym przykładzie kodu zmienna `n` jest inicjowana `try` wewnątrz bloku. Próba użycia tej zmiennej poza `try` blokiem `Write(n)` w instrukcji spowoduje wygenerowanie błędu kompilatora.

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

## <a name="exceptions-in-async-methods"></a>Wyjątki w metodach asynchronicznych

Metoda asynchroniczna jest oznaczona przez modyfikator [Async](async.md) i zwykle zawiera co najmniej jedno wyrażenie lub instrukcje await. Wyrażenie await stosuje operator [await](../operators/await.md) do <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.

Gdy kontrolka osiągnie `await` wartość w metodzie asynchronicznej, postęp w metodzie jest zawieszony do momentu zakończenia zadania oczekiwania. Po zakończeniu zadania wykonywanie może zostać wznowione w metodzie. Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z asynchroniczne i oczekujące](../../programming-guide/concepts/async/index.md) i [przepływ sterowania w programach asynchronicznych](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Ukończone zadanie, do którego `await` zastosowano, może być w stanie awarii z powodu nieobsłużonego wyjątku w metodzie, która zwraca zadanie. Oczekiwanie na zadanie zgłosi wyjątek. Zadanie można także zakończyć w stanie anulowanym, jeśli asynchroniczny proces zwraca go. Oczekiwanie na anulowane zadanie `OperationCanceledException`wyrzuca. Aby uzyskać więcej informacji o tym, jak anulować proces asynchroniczny, zobacz dostrajanie [aplikacji asynchronicznej](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Aby wychwycić wyjątek, oczekiwanie na zadanie w `try` bloku i Przechwyć wyjątek w skojarzonym `catch` bloku. Aby zapoznać się z przykładem, zobacz sekcję dotyczącą [przykładu metody asynchronicznej](#async-method-example) .

Zadanie może być w stanie nieprawidłowym, ponieważ wystąpiły wiele wyjątków w metodzie asynchronicznej oczekiwania. Na przykład zadanie może być wynikiem wywołania metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Podczas oczekiwania na takie zadanie zostanie przechwycony tylko jeden z wyjątków i nie będzie można przewidzieć, który wyjątek zostanie przechwycony. Aby zapoznać się z przykładem, zapoznaj się z sekcją [przykład Task. WhenAll](#taskwhenall-example) .

## <a name="example"></a>Przykład

W poniższym przykładzie `try` blok zawiera wywołanie `ProcessString` metody, która może spowodować wyjątek. `catch` Klauzula zawiera procedurę obsługi wyjątków, która po prostu wyświetla komunikat na ekranie. Gdy instrukcja jest wywoływana z wewnątrz `MyMethod`, system szuka `catch` instrukcji i wyświetla komunikat `Exception caught`. `throw`

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a>Przykład dwóch bloków catch

W poniższym przykładzie są używane dwa bloki catch, a najbardziej konkretny wyjątek, który jest pierwszy, jest przechwytywany.

Aby przechwycić najmniejszy konkretny wyjątek, można zastąpić instrukcję `ProcessString` throw przy użyciu następującej instrukcji:. `throw new Exception()`

W przypadku umieszczenia bloku catch o najniższym poziomie najpierw w tym przykładzie zostanie wyświetlony następujący komunikat o błędzie `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`:.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a>Przykład metody asynchronicznej

Poniższy przykład ilustruje obsługę wyjątków dla metod asynchronicznych. Aby przechwytywać wyjątek, który generuje zadanie asynchroniczne, umieść `await` wyrażenie `try` w bloku i `catch` Przechwyć wyjątek w bloku.

Usuń komentarz `throw new Exception` wiersza z przykładu, aby zademonstrować obsługę wyjątków. `IsFaulted` Właściwość zadania jest ustawiona na `True`, `Exception.InnerException` właściwość zadania jest ustawiana na wyjątek `catch` , a wyjątek jest przechwytywany w bloku.

Usuń komentarz z `throw new OperationCanceledException` wiersza, aby zademonstrować, co się dzieje po anulowaniu procesu asynchronicznego. `IsCanceled` Właściwość zadania jest ustawiona na `true`, a `catch` wyjątek jest przechwytywany w bloku. W przypadku niektórych warunków, które nie dotyczą tego `IsFaulted` przykładu, właściwość zadania jest ustawiona na `true` i `IsCanceled` jest ustawiona na. `false`

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a>Task. WhenAll — przykład

Poniższy przykład ilustruje obsługę wyjątków, gdy wiele zadań może skutkować wieloma wyjątkami. Blok oczekuje zadania, które jest zwracane przez <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>wywołanie metody. `try` Zadanie zostanie ukończone, gdy zostaną wykonane trzy zadania, do których zastosowano WhenAll.

Każdy z tych trzech zadań powoduje wyjątek. Blok wykonuje iterację `Exception.InnerExceptions` w wyjątkach, które są dostępne we właściwości zadania, które zostało zwrócone przez <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. `catch`

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [try instrukcji](~/_csharplang/spec/statements.md#the-try-statement) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje try, throw i catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
