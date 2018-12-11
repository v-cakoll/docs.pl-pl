---
title: try-catch - C# odwołania
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
ms.openlocfilehash: 7e48783c01a5b94f51f89d25f465f22358e7aa8f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240025"
---
# <a name="try-catch-c-reference"></a>try-catch (odwołanie w C#)

Instrukcja try-catch, który składa się z `try` bloku, po której następuje co najmniej jeden `catch` zdań, która określa programy obsługi dla różnych wyjątków.

## <a name="remarks"></a>Uwagi

Gdy wyjątek jest generowany, środowisko uruchomieniowe języka wspólnego (CLR) wyszukuje `catch` instrukcję, która obsługuje ten wyjątek. Jeśli aktualnie wykonywanej metody nie zawiera takie `catch` zablokować, CLR prezentuje metody, która wywołała bieżącą metodę, i tak dalej w górę stosu wywołań. Jeśli nie `catch` blok zostanie znaleziony, a następnie CLR zostanie wyświetlony komunikat nieobsługiwany wyjątek użytkownikowi i zatrzymuje wykonywanie programu.

`try` Blok zawiera chronioną kod, który może spowodować wystąpienie wyjątku. Blok jest wykonywany, dopóki nie zostanie zgłoszony wyjątek lub zakończyło się powodzeniem. Na przykład, że próba zrzutowania `null` obiektu zgłasza <xref:System.NullReferenceException> wyjątek:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

Mimo że `catch` bez argumentów można użyć klauzuli można przechwycić wyjątek dowolnego typu, to użycie nie jest zalecane. Ogólnie rzecz biorąc należy tylko przechwytywać te wyjątki, które należy znać sposób sprawności. W związku z tym, należy zawsze podać argument obiektu pochodną <xref:System.Exception?displayProperty=nameWithType> na przykład:

```csharp
catch (InvalidCastException e)
{
}
```

Istnieje możliwość użycia więcej niż jednej określonej `catch` klauzuli w tej samej instrukcji try-catch. W tym przypadku kolejność `catch` klauzule ważne jest, ponieważ `catch` klauzule są badane w kolejności. Rejestrować bardziej szczegółowe wyjątki przed mniej określone z nich. Kompilator generuje błąd, jeśli kolejność, że Twoje catch blokuje tak, aby nigdy nie jest osiągalna nowsze bloku.

Za pomocą `catch` argumentów jest jednym ze sposobów, aby filtrować pod kątem wyjątków, które ma obsługiwać.  Umożliwia także filtr wyjątku, który dodatkowo sprawdza, czy wyjątek zdecydować, czy do jego obsługi.  Jeśli filtr wyjątku zwróci wartość false, wyszukiwanie w przypadku obsługi kontynuowane.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Filtry wyjątków są preferowane w porównaniu do przechwytywania i ponowne generowanie (wyjaśnione poniżej), ponieważ filtry pozostaw stosu nieokaleczone.  Jeśli nowszej obsługi zrzuty stosu, zostanie wyświetlony, wyjątek pierwotnie pochodzenia, a nie tylko ostatnie miejsce, który był zgłaszany ponownie.  Typowym zastosowaniem wyrażenia filtru wyjątków jest rejestrowania.  Można utworzyć filtr, która zawsze zwraca wartość FAŁSZ, który również dane wyjściowe do dziennika, możesz rejestrować wyjątki jako komputery przechodzą bez konieczności ich i ponownego zgłoszenia.

A [throw](throw.md) instrukcja może być używana w `catch` bloku, aby można było ponownie zgłosić wyjątek, który zostanie przechwycony przez `catch` instrukcji. Poniższy przykład wyodrębnia informacje o źródle <xref:System.IO.IOException> wyjątek i następnie zgłasza wyjątek do nadrzędnej metody.

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

Można przechwycić jeden wyjątek i różnych wyjątku. Gdy to zrobisz, określ wyjątek, który przechwycono jako wewnętrzny wyjątek, jak pokazano w poniższym przykładzie.

```csharp
catch (InvalidCastException e) 
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

Użytkownik może również ponowne zgłoszenie wyjątku, gdy określony warunek ma wartość true, jak pokazano w poniższym przykładzie.

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
> Istnieje również możliwość Użyj filtra wyjątku, aby uzyskać podobny efekt w często bardziej przejrzysty sposób (a także nie modyfikowanie stosu, zgodnie z opisem we wcześniejszej części tego dokumentu). W poniższym przykładzie przedstawiono podobne zachowanie dla obiektów wywołujących, jak w poprzednim przykładzie. Funkcja zgłasza `InvalidCastException` obiektu wywołującego podczas `e.Data` jest `null`.
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null) 
> {
>     // Take some action.
> }
> ``` 

Z wewnątrz `try` zablokować, zainicjować tylko zmienne, które są zadeklarowane w nim. W przeciwnym razie może wystąpić wyjątek, przed zakończeniem wykonywania bloku. Na przykład w poniższym przykładzie kodu zmiennej `n` jest inicjowany wewnątrz `try` bloku. Próba użycia tej zmiennej poza `try` bloku `Write(n)` instrukcji spowoduje wygenerowanie błędu kompilatora.

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
Metoda asynchroniczna jest oznaczony za [async](async.md) modyfikator i zwykle zawiera jeden lub więcej await wyrażeń lub instrukcji. Wyrażenie await stosuje [await](await.md) operatora <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.

Gdy kontrola osiąga `await` w metodzie asynchronicznej postęp w metodzie jest wstrzymana, dopóki nie zakończy się oczekiwane zadanie. Kiedy zadanie zostanie ukończone, wykonanie można wznowić w metodzie. Aby uzyskać więcej informacji, zobacz [Asynchronous Programming with async i await](../../programming-guide/concepts/async/index.md) i [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Ukończone zadanie podrzędne, do którego `await` jest stosowany z powodu nieobsługiwanego wyjątku w metodzie, która zwraca zadanie może znajdować się w nieprawidłowym stanie. Oczekiwanie na zadanie zgłasza wyjątek. Zadanie również można znajdą się w stanem anulowane, jeśli proces asynchroniczny, która zwraca go zostało anulowane. Oczekuje na anulowane zadanie zgłasza `OperationCanceledException`. Aby uzyskać więcej informacji o tym, jak można anulować proces asynchroniczny, zobacz [aplikacji asynchronicznej Fine-Tuning](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Aby przechwycić wyjątek, należy poczekać na zadanie `try` zablokować, a następnie przechwycić wyjątek w skojarzonej `catch` bloku. Aby uzyskać przykład zobacz sekcję "Przykład".

Zadanie może być w nieprawidłowym stanie, ponieważ w metodzie async oczekiwane wystąpił wiele wyjątków. Na przykład zadanie może być wynikiem wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. W przypadku takich zadań, jest tylko jeden z wyjątków wychwytywane, a nie można przewidzieć, który wyjątek zostanie zgłoszony. Aby uzyskać przykład zobacz sekcję "Przykład".

## <a name="example"></a>Przykład

W poniższym przykładzie `try` blok zawiera wywołanie `ProcessString` metodę, która może spowodować wyjątek. `catch` Klauzula zawiera program obsługi wyjątków, który po prostu wyświetla komunikat na ekranie. Gdy `throw` instrukcji jest wywoływana z wewnątrz `MyMethod`, system wyszukuje `catch` instrukcji i wyświetla komunikat `Exception caught`.

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="example"></a>Przykład

W poniższym przykładzie są używane dwa bloki catch, a specyficzny wyjątek, który wykorzystasz, zostanie przechwycony.

Aby przechwycić wyjątek najmniej specyficznych, możesz zastąpić instrukcji "throw" w `ProcessString` przy użyciu następującej instrukcji: `throw new Exception()`.

Jeśli najpierw umieścić blok catch do najmniej specyficznych w przykładzie pojawia się następujący komunikat o błędzie: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="example"></a>Przykład

Poniższy przykład ilustruje wyjątków, obsługa do metod asynchronicznych. Aby przechwytywać wyjątek, który zgłasza zadania asynchronicznego, umieść `await` wyrażenia w `try` zablokować, a następnie przechwycić wyjątek w `catch` bloku.

Usuń znaczniki komentarza `throw new Exception` wiersza w przykładzie, aby zademonstrować obsługi wyjątków. Zadania podrzędnego `IsFaulted` właściwość jest ustawiona na `True`, zadania podrzędnego `Exception.InnerException` właściwość jest ustawiona na wyjątek i wyjątek w `catch` bloku.

Usuń znaczniki komentarza `throw new OperationCancelledException` wiersz, aby zademonstrować, co się stanie, gdy anulujesz proces asynchroniczny. Zadania podrzędnego `IsCanceled` właściwość jest ustawiona na `true`, a wyjątek w `catch` bloku. W niektórych warunkach, które nie mają zastosowania do tego przykładu, zadania w `IsFaulted` właściwość jest ustawiona na `true` i `IsCanceled` ustawiono `false`.

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="example"></a>Przykład

Poniższy przykład ilustruje wyjątków, gdzie wiele zadań może spowodować wiele wyjątków. `try` Bloku czeka na zadanie, który jest zwracany przez wywołanie <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Zadanie zostało ukończone, po zakończeniu trzech zadań, do których zastosowano WhenAll.

Każdy z trzech zadań, powoduje wyjątek. `catch` Bloku wykonuje iterację przez wyjątki, które znajdują się w `Exception.InnerExceptions` właściwości zadania, który został zwrócony przez <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje try, throw i catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [Instrukcje obsługi wyjątków](exception-handling-statements.md)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)