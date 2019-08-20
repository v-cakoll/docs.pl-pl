---
title: await — C# odwołanie
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 2f6fb9fb8c29013165298c186ec072aa1e750ab9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602299"
---
# <a name="await-c-reference"></a>await (odwołanie w C#)
`await` Operator jest stosowany do zadania w metodzie asynchronicznej, aby wstawić punkt zawieszenia w trakcie wykonywania metody do momentu zakończenia zadania oczekiwania. Zadanie reprezentuje trwającą prace.  
  
`await`może być używany tylko w metodzie asynchronicznej modyfikowane przez słowo kluczowe [Async](./async.md) . Takie metody, zdefiniowane za pomocą `async` modyfikatora i zwykle zawierające co najmniej jedno `await` wyrażenie, są określane jako *Metoda async*.  
  
> [!NOTE]
> Słowa kluczowe `await`izostały wprowadzone w C# 5. `async` Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../programming-guide/concepts/async/index.md).  
  
Zadanie, do którego `await` jest stosowany operator zazwyczaj jest zwracane przez wywołanie metody implementującej [wzorzec asynchroniczny oparty na zadaniach](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Obejmują one metody, które <xref:System.Threading.Tasks.Task>zwracają <xref:System.Threading.Tasks.Task%601>obiekty <xref:System.Threading.Tasks.ValueTask>,, <xref:System.Threading.Tasks.ValueTask%601> , i.  

W poniższym przykładzie <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> Metoda `Task<byte[]>`zwraca. Zadanie to obietnica do tworzenia rzeczywistej tablicy bajtów po zakończeniu zadania. Operator zawiesza wykonywanie do momentu zakończenia pracy <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metody. `await` W międzyczasie formant jest zwracany do obiektu wywołującego `GetPageSizeAsync`. Po zakończeniu wykonywania zadania, `await` wyrażenie daje w wyniku tablicę bajtów.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
> Aby zapoznać się z kompletnym [przykładem, zobacz Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)Async i await. Możesz pobrać przykład z [przykładów kodu dla deweloperów](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) w witrynie sieci Web firmy Microsoft. Przykład znajduje się w projekcie AsyncWalkthrough_HttpClient.  
  
Jak pokazano w poprzednim `await` przykładzie, jeśli jest stosowany do wyniku wywołania metody, które `Task<TResult>`zwraca, `await` a następnie typ wyrażenia jest `TResult`. Jeśli `await` jest stosowany do wyniku wywołania metody, które `Task`zwraca, `await` wówczas typem wyrażenia jest `void`. Poniższy przykład ilustruje różnicę.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
`await` Wyrażenie nie blokuje wątku, w którym jest wykonywane. Zamiast tego powoduje, że kompilator rejestruje resztę metody asynchronicznej jako kontynuację w oczekiwanym zadaniu. Następnie formant wraca do obiektu wywołującego metody asynchronicznej. Po zakończeniu zadania wywołuje jego kontynuację i wykonywanie metody asynchronicznej zostaje wznowione w miejscu, w którym została przerwana.  
  
Wyrażenie może wystąpić tylko w treści otaczającej metody, wyrażenia lambda lub metody anonimowej, która musi być oznaczona `async` modyfikatorem. `await` Termin *await* służy jako słowo kluczowe tylko w tym kontekście. W innym miejscu jest interpretowana jako identyfikator. W ramach metody, wyrażenia lambda lub metody `await` anonimowej wyrażenie nie może wystąpić w treści funkcji synchronicznej, w wyrażeniu zapytania, w bloku [instrukcji lock](./lock-statement.md)lub w niebezpiecznym kontekście. [](./unsafe.md)  
  
## <a name="exceptions"></a>Wyjątki  
Większość metod asynchronicznych zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Właściwości zwróconego zadania zawierają informacje o jego stanie i historii, na przykład o tym, czy zadanie zostało ukończone, czy Metoda asynchroniczna spowodowała wyjątek, czy została anulowana, oraz jaki jest wynik końcowy. Operator uzyskuje dostęp do tych właściwości poprzez wywoływanie metod dla obiektu zwróconego `GetAwaiter` przez metodę. `await`  
  
Jeśli czekasz na metodę asynchroniczną zwracającą zadanie, która powoduje wyjątek, `await` operator ponownie zgłosi wyjątek.  
  
Jeśli oczekujesz, że zachodzi Metoda asynchroniczna zwracająca zadanie, `await` która została anulowana, <xref:System.OperationCanceledException>operator ponownie zgłosi.  
  
Pojedyncze zadanie, które jest w stanie awarii może odzwierciedlać wiele wyjątków. Na przykład zadanie może być wynikiem wywołania metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Po oczekiwaniu na takie zadanie Operacja await ponownie zgłosi tylko jeden z wyjątków. Nie można jednak przewidzieć, które wyjątki są ponownie zgłaszane.  
  
Aby zapoznać się z przykładami obsługi błędów w metodach asynchronicznych, zobacz [try-catch](./try-catch.md).  
  
## <a name="example"></a>Przykład  
Poniższy przykład zwraca łączną liczbę znaków na stronach, których adresy URL są przekazane do niego jako argumenty wiersza polecenia. Przykład wywołuje `GetPageLengthsAsync` metodę, która jest oznaczona `async` za pomocą słowa kluczowego. Metoda z kolei `await` używa słowa kluczowego <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> do oczekiwania na wywołania metody. `GetPageLengthsAsync`  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

W poprzednim przykładzie używany C# jest [ `async` `Main` ](../../programming-guide/main-and-command-args/index.md)7,1, który obsługuje metodę. Ze C# względu na to, że wcześniejsze wersje nie <xref:System.Threading.Tasks.Task> obsługują punktów wejścia aplikacji zwracających `async` lub <xref:System.Threading.Tasks.Task%601>, nie `Main` można zastosować modyfikatora `GetPageLengthsAsync` do metody i oczekiwania na wywołanie metody. W takim przypadku można upewnić się, że `Main` Metoda czeka na zakończenie operacji asynchronicznej przez pobranie wartości <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> właściwości. W przypadku zadań, które nie zwracają wartości, można wywołać <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodę. Aby uzyskać informacje o sposobach wybierania wersji językowej, zobacz [Wybieranie C# wersji językowej](../configure-language-version.md).

## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await](../../programming-guide/concepts/async/index.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [async](./async.md)
