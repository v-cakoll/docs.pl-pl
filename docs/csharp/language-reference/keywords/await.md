---
title: "await (odwołanie w C#)"
ms.date: 05/22/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: "36"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 69a3a575347a62b298c17af050cb925f7819b552
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="await-c-reference"></a>await (odwołanie w C#)
`await` Operator jest stosowany do zadania w można wstawić punktu zawieszenia podczas wykonywania metody do momentu ukończenia zadania Oczekiwano metody asynchronicznej. Zadanie reprezentuje pracy w toku.  
  
`await`można użyć tylko w metodzie asynchronicznej zmodyfikowany przez [async](../../../csharp/language-reference/keywords/async.md) — słowo kluczowe. Taka metoda, zdefiniowany przy użyciu `async` modyfikator, zwykle zawiera co najmniej jeden `await` wyrażenia, jest określany jako *metody asynchronicznej*.  
  
> [!NOTE]
>  `async` i `await` wprowadzono słów kluczowych w języku C# 5. Aby obejrzeć wprowadzenie do programowania asynchronicznego Zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md).  
  
Zadania, które `await` zastosować operatora zazwyczaj zwracane przez wywołanie do metody, która implementuje [wzorca asynchronicznego opartego na zadaniach](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Obejmują one metody, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, i `System.Threading.Tasks.ValueType<TResult>` obiektów.  

  
 W poniższym przykładzie <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> metoda zwraca `Task<byte[]>`. Zadanie jest obietnicę w celu utworzenia tablicy bajtowej rzeczywiste po zakończeniu zadania. `await` Operator wstrzymuje wykonywanie do pracy <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metody została ukończona. Tymczasem zwróceniem sterowania do wywołującego `GetPageSizeAsync`. Gdy zadanie kończy działanie, `await` wyrażenie na tablicę bajtów.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
>  Aby uzyskać pełny przykład, zobacz [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Możesz pobrać próbki z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkID=255191) w witrynie firmy Microsoft. Przykładem jest w projekcie AsyncWalkthrough_HttpClient.  
  
Jak pokazano w poprzednim przykładzie, jeśli `await` jest stosowany do wyniku wywołania metody, która zwraca `Task<TResult>`, następnie typ `await` wyrażenie jest `TResult`. Jeśli `await` jest stosowany do wyniku wywołania metody, która zwraca `Task`, następnie typ `await` wyrażenie jest `void`. Poniższy przykład przedstawia różnicy.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
`await` Wyrażenia nie są blokowane w wątku, na którym jest wykonywany. Zamiast tego należy go powoduje, że kompilator Zarejestruj pozostałe metody asynchronicznej kontynuacji oczekiwano zadania. Formant zwraca do obiektu wywołującego metody asynchronicznej. Po ukończeniu zadania wywołuje kontynuacji i wykonywania wznawia metody asynchronicznej miejsca, w którym.  
  
`await` Wyrażenie może wystąpić tylko w otaczającej jego treści metody, wyrażenia lambda lub metody anonimowej, muszą być oznaczone `async` modyfikator. Termin *await* służy jako słowo kluczowe tylko w tym kontekście. W innym miejscu jest interpretowany jako identyfikator. W ramach metody, wyrażenia lambda lub metody anonimowej `await` wyrażenia nie może wystąpić w treści funkcji synchroniczne w wyrażeniu zapytania w bloku [lock — instrukcja](../../../csharp/language-reference/keywords/lock-statement.md), lub w [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontekstu.  
  
## <a name="exceptions"></a>Wyjątki  
Zwraca większości metod asynchronicznych <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Właściwości zadania zwróconego zawierać informacje o jego stan i Historia, na przykład tego, czy zadanie zostało ukończone, czy metoda asynchroniczna spowodowała wyjątek lub została anulowana i jakie wynik końcowy jest. `await` Operator uzyskuje dostęp do tych właściwości przez wywołanie metody w obiekcie zwracanym przez `GetAwaiter` metody.  
  
Jeśli await umożliwiające zwracanie zadań metoda asynchroniczna, która powoduje zgłoszenie wyjątku `await` operator ponownie zgłasza wyjątek.  
  
Jeśli await umożliwiające zwracanie zadań metoda asynchroniczna, która została anulowana, `await` operator ponownie zgłasza wyjątek <xref:System.OperationCanceledException>.  
  
Pojedyncze zadanie, który jest stan można odzwierciedlać wiele wyjątków. Na przykład zadanie może być wynikiem wywołania do <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Gdy await takie zadania, ponownie zgłasza operacji await tylko jeden z wyjątków. Jednak nie można przewidzieć który wyjątki jest zgłoszony.  
  
Przykłady obsługi błędów w metodach asynchronicznych, zobacz [try-catch](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Przykład  
Poniższy przykład zwraca całkowita liczba znaków na stronach, których adresy URL są przekazywane do niego jako argumenty wiersza polecenia. Przykład wywołania `GetPageLengthsAsync` metodę, która jest oznaczony atrybutem `async` — słowo kluczowe. `GetPageLengthsAsync` Metoda z kolei używa `await` — słowo kluczowe await wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> metody.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

Ponieważ stosowania `async` i `await` we wpisie aplikacji punkt nie jest obsługiwane, nie możemy zastosować `async` atrybutu `Main` metody ani może możemy await `GetPageLengthsAsync` wywołania metody. Firma Microsoft może upewnij się, że `Main` metoda oczekuje na zakończenie pobierając zaletą operacji asynchronicznej <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> właściwości. Dla zadań, które nie zwracają wartości, należy wywołać <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody. 

## <a name="see-also"></a>Zobacz także  
[Programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md)   
[Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
[asynchroniczne](../../../csharp/language-reference/keywords/async.md)
