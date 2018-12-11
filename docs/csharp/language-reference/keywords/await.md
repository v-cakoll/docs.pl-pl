---
title: await — C# odwołania
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: c80d6598540700fdb8559497f10c66726c384519
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239686"
---
# <a name="await-c-reference"></a>await (odwołanie w C#)
`await` Operator jest stosowany do zadania w metodzie asynchronicznej, aby wstawić punkt zawieszenia podczas wykonywania metody, dopóki nie zakończy się oczekiwane zadanie. Zadanie reprezentuje pracę w toku.  
  
`await` należy używać tylko w metodzie asynchronicznej, zmodyfikowany przez [async](../../../csharp/language-reference/keywords/async.md) — słowo kluczowe. Taka metoda, zdefiniowana za pomocą `async` modyfikator i zwykle zawierająca co najmniej jeden `await` wyrażeń, jest określany jako *metody asynchronicznej*.  
  
> [!NOTE]
>  `async` i `await` słowa kluczowe zostały wprowadzone w języku C# 5. Wprowadzenie do programowania asynchronicznego, zobacz [Asynchronous Programming with async i await](../../../csharp/programming-guide/concepts/async/index.md).  
  
Zadanie, do którego `await` jest stosowany operator zazwyczaj jest zwracany przez wywołanie metody, która implementuje [wzorca asynchronicznego opartego na zadaniach](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Obejmują one metody, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, i `System.Threading.Tasks.ValueType<TResult>` obiektów.  

  
 W poniższym przykładzie <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> metoda zwraca `Task<byte[]>`. Zadanie jest obietnicą utworzenia rzeczywistej tablicy bajtowej, jeśli zadanie zostało ukończone. `await` Operator zawiesza wykonywanie aż do pracy <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metoda zostało zakończone. W międzyczasie formant zostaje zwrócony do obiektu wywołującego `GetPageSizeAsync`. Po zakończeniu zadania wykonywania `await` wynikiem wyrażenia jest tablicą bajtów.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
>  Aby uzyskać kompletny przykład, zobacz [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Możesz pobrać próbkę z [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) w witrynie internetowej firmy Microsoft. Przykład znajduje się w projekcie AsyncWalkthrough_HttpClient.  
  
Jak pokazano w poprzednim przykładzie, jeśli `await` jest stosowany do wyniku wywołania metody, która zwraca `Task<TResult>`, następnie typ `await` wyrażenie jest `TResult`. Jeśli `await` jest stosowany do wyniku wywołania metody, która zwraca `Task`, następnie typ `await` wyrażenie jest `void`. Poniższy przykład ilustruje tę różnicę.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
`await` Wyrażenie nie blokuje wątku, na którym jest wykonywany. Zamiast tego należy go powoduje, że kompilator pozostałą metodę asynchronicznej jako kontynuację w oczekiwane zadanie. Formant powraca do obiektu wywołującego metody asynchronicznej. Po zakończeniu zadania wywołuje jego kontynuację, a wykonywanie metody asynchronicznej zostaje wznowione tam, gdzie ją przerwaliśmy.  
  
`await` Wyrażenie może wystąpić tylko w treści jego otaczającej metody, wyrażenia lambda lub metody anonimowej, muszą być oznaczone `async` modyfikator. Termin *await* służy jako słowo kluczowe tylko w tym kontekście. Gdzie indziej będzie interpretowany jako identyfikator. W ramach metody, wyrażenia lambda lub metody anonimowej `await` wyrażenia nie może wystąpić w treści funkcji synchronicznej, w wyrażeniu zapytania w bloku [lock — instrukcja](../../../csharp/language-reference/keywords/lock-statement.md), lub [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontekstu.  
  
## <a name="exceptions"></a>Wyjątki  
Większości metod asynchronicznych zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Właściwości zwracanego zadania przenoszą informacje o jego stanie i historii, takich jak tego, czy zadanie zostało ukończone, czy metoda async spowodowała wyjątek lub została anulowana i jaki jest wynik końcowy. `await` Operator uzyskuje dostęp do tych właściwości przez wywołanie metody w obiekcie zwracanym przez `GetAwaiter` metody.  
  
Jeśli włączysz zwracającą zadanie metodę asynchroniczną, która powoduje wyjątek `await` operator ponownie zgłasza wyjątek.  
  
Jeśli włączysz zwracającą zadanie metody asynchronicznej, która została anulowana, `await` ponownie zgłasza operator <xref:System.OperationCanceledException>.  
  
Pojedynczego zadania, które jest w stanie błędnym może odzwierciedlać wiele wyjątków. Na przykład zadanie może być wynikiem wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. W przypadku takiego zadania, ponownie zgłasza operacji await, tylko jeden z wyjątków. Jednak nie można przewidzieć, który z tych wyjątków jest zgłaszany ponownie.  
  
Aby uzyskać przykłady obsługi błędów w metodach asynchronicznych, zobacz [try-catch —](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Przykład  
Poniższy przykład zwraca całkowita liczba znaków w stron, których adresy URL są przekazywane do niego jako argumenty wiersza polecenia. Przykład wywołuje `GetPageLengthsAsync` metody, która jest oznaczona za pomocą `async` — słowo kluczowe. `GetPageLengthsAsync` Metoda z kolei używa `await` słowa kluczowego await wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> metody.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

W poprzednim przykładzie użyto C# 7.1, która obsługuje [ `async` `Main` metoda](../../programming-guide/main-and-command-args/index.md). Ponieważ wcześniej C# wersje nie obsługują punkty wejścia aplikacji, które zwracają <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, nie można zastosować `async` modyfikatora `Main` metody i await `GetPageLengthsAsync` wywołania metody. W takiej sytuacji należy upewnić się, że `Main` metoda czeka na zakończenie poprzez pobranie wartości dla operacji asynchronicznej <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> właściwości. Zadania, które nie zwracają wartości, można wywołać <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody. Aby uzyskać informacje o sposobie wybierz wersję językową, zobacz [wybierz C# wersji językowej](../configure-language-version.md).

## <a name="see-also"></a>Zobacz także  
- [Programowanie asynchroniczne z Async i Await](../../../csharp/programming-guide/concepts/async/index.md)   
- [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
- [async](../../../csharp/language-reference/keywords/async.md)
