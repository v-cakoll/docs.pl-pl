---
title: Typy zwrotu asynchronicznego (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 9926fea5308f9088ad924bcc98d8deed319c6300
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170042"
---
# <a name="async-return-types-c"></a>Typy zwrotu asynchronicznego (C#)
Metody asynchroniczne mogą mieć następujące typy zwracane:

- <xref:System.Threading.Tasks.Task%601>, dla metody asynchronicznej, która zwraca wartość.

- <xref:System.Threading.Tasks.Task>, dla metody asynchronicznej, która wykonuje operację, ale nie zwraca żadnej wartości.

- `void`, dla programu obsługi zdarzeń.

- Począwszy od języka C# 7.0, `GetAwaiter` dowolnego typu, który ma metodę dostępną. Obiekt zwrócony przez `GetAwaiter` metodę musi <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> implementować interfejs.
  
Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [Programowanie asynchroniczne z async i await (C#)](./index.md).  
  
Każdy typ zwracany jest badany w jednej z poniższych sekcji i można znaleźć pełny przykład, który używa wszystkich trzech typów na końcu tematu.  
  
## <a name="BKMK_TaskTReturnType"></a>Typ\<zwracania tresult\> zadania  
Zwracany <xref:System.Threading.Tasks.Task%601> typ jest używany dla metody asynchronicznej, która zawiera [return](../../../language-reference/keywords/return.md) (C#) instrukcji, w którym operand ma typ `TResult`.  
  
W poniższym przykładzie `GetLeisureHours` metoda asynchroniczna zawiera instrukcję, `return` która zwraca liczby całkowitej. W związku z tym deklaracja `Task<int>`metody musi określać typ zwracany .  Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> asynchroniczna jest symbolem zastępczym dla operacji, która zwraca ciąg.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Gdy `GetLeisureHours` jest wywoływana z wewnątrz `ShowTodaysInfo` await wyrażenie w metodzie, await wyrażenie pobiera `leisureHours`wartość całkowitą (wartość ), który `GetLeisureHours` jest przechowywany w zadaniu zwracanym przez metodę. Aby uzyskać więcej informacji na temat wyrażeń await, zobacz [await](../../../language-reference/operators/await.md).  
  
Można lepiej zrozumieć, jak to się `GetLeisureHours` dzieje, oddzielając wywołanie od stosowania `await`, jak pokazano w poniższym kodzie. Wywołanie metody, `GetLeisureHours` która nie jest natychmiast `Task<int>`oczekiwana zwraca , jak można oczekiwać od deklaracji metody. Zadanie jest przypisane do `integerTask` zmiennej w przykładzie. Ponieważ `integerTask` jest <xref:System.Threading.Tasks.Task%601>, zawiera <xref:System.Threading.Tasks.Task%601.Result> właściwość `TResult`typu . W takim `TResult` przypadku reprezentuje typ liczby całkowitej. Po `await` zastosowaniu do `integerTask`wyrażenia await oblicza zawartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości . `integerTask` Wartość jest przypisywana `ret` do zmiennej.  
  
> [!IMPORTANT]
> Obiekt <xref:System.Threading.Tasks.Task%601.Result%2A> jest obiektem blokującym. Jeśli spróbujesz uzyskać do niego dostęp przed zakończeniem jego zadania, wątek, który jest aktualnie aktywny jest zablokowany, dopóki zadanie nie zostanie zakończone, a wartość jest dostępna. W większości przypadków należy uzyskać dostęp `await` do wartości przy użyciu zamiast uzyskiwania dostępu do właściwości bezpośrednio. <br/> W poprzednim przykładzie pobrano <xref:System.Threading.Tasks.Task%601.Result%2A> wartość właściwości, aby zablokować `ShowTodaysInfo` wątek główny, dzięki czemu metoda może zakończyć wykonywanie przed zakończeniem aplikacji.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
## <a name="BKMK_TaskReturnType"></a>Typ zwrotu zadania  
Metody asynchroniczne, które `return` nie zawierają instrukcji `return` lub które zawierają instrukcję, która nie <xref:System.Threading.Tasks.Task>zwraca operand zwykle mają typ zwracany . Takie metody `void` zwracają, jeśli są uruchamiane synchronicznie. Jeśli używasz <xref:System.Threading.Tasks.Task> typu zwracanego dla metody asynchronicznej, `await` metoda wywołująca może użyć operatora do zawieszenia zakończenia wywołującego, dopóki nie zostanie zakończona wywoływana metoda asynchronia.  
  
W poniższym przykładzie `WaitAndApologize` metoda asynchroniczne `return` nie zawiera instrukcji, <xref:System.Threading.Tasks.Task> więc metoda zwraca obiekt. Dzięki `WaitAndApologize` temu można się wyczekiwać. Należy zauważyć, że <xref:System.Threading.Tasks.Task> typ `Result` nie zawiera właściwości, ponieważ nie ma wartości zwracanej.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize`jest oczekiwany przy użyciu await instrukcji zamiast await wyrażenie, podobne do instrukcji wywołującej dla synchronicznej metody zwracania void. Zastosowanie await operatora w tym przypadku nie generuje wartość.  
  
Podobnie jak <xref:System.Threading.Tasks.Task%601> w poprzednim przykładzie, można `WaitAndApologize` oddzielić wywołanie od stosowania operatora await, jak pokazano w poniższym kodzie. Należy jednak pamiętać, że `Task` a `Result` nie ma właściwości i że żadna wartość jest `Task`tworzona, gdy operator await jest stosowany do .  
  
Poniższy kod oddziela `WaitAndApologize` wywoływanie metody z oczekiwania na zadanie, które zwraca metoda.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  

## <a name="BKMK_VoidReturnType"></a>Nieważne zwracanie typu

Typ zwracany `void` jest używany w programach obsługi zdarzeń asynchronicznych, które wymagają typu zwracanego. `void` W przypadku metod innych niż programy obsługi zdarzeń, które <xref:System.Threading.Tasks.Task> nie zwracają wartości, należy `void` zwrócić zamiast tego, ponieważ nie można oczekiwać metody asynchronicznej, która zwraca. Każdy obiekt wywołujący takiej metody musi być w stanie kontynuować wykonywanie bez oczekiwania na wywołaną metodę asynchronicznej, aby zakończyć, a obiekt wywołujący musi być niezależny od wszelkich wartości lub wyjątków, które generuje metoda asynchronii.  
  
Obiekt wywołujący metodę asynchronia zwracającą nieważność nie może przechwycić wyjątków, które są generowane z metody, a takie nieobsługiwane wyjątki mogą spowodować niepowodzenie aplikacji. Jeśli wystąpi wyjątek w metodzie asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, wyjątek jest przechowywany w zwróconym zadaniu i jest rethrown, gdy oczekuje na zadanie. W związku z tym upewnij się, że każda metoda <xref:System.Threading.Tasks.Task> asynchroniczne, które mogą powodować wyjątek ma typ zwracany lub <xref:System.Threading.Tasks.Task%601> że wywołania metody są oczekiwane.  
  
Aby uzyskać więcej informacji na temat sposobu wychwytywania wyjątków w metodach asynchronicznych, zobacz [wyjątki w metodach asynchronicznych](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) sekcji tematu [try-catch.](../../../language-reference/keywords/try-catch.md)  
  
W poniższym przykładzie przedstawiono zachowanie programu obsługi zdarzeń asynchronicznego. Należy zauważyć, że w przykładowym kodzie program obsługi zdarzeń asynchronicznej musi poinformować główny wątek po jego zakończeniu. Następnie główny wątek może czekać na zakończenie programu obsługi zdarzeń asynchronicznej przed zamknięciem programu.

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Uogólnione typy zwrotów\<asynchronicznej i Wynik Zadania ValueTask TResult\>

Począwszy od języka C# 7.0, metoda asynchroniczne można zwrócić dowolny typ, który ma metodę dostępną. `GetAwaiter`

Ponieważ <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> i są typy odwołań, alokacji pamięci w ścieżkach o krytycznym znaczeniu dla wydajności, szczególnie gdy alokacje występują w wąskich pętli, może niekorzystnie wpłynąć na wydajność. Obsługa ogólnych typów zwracanych oznacza, że można zwrócić typ wartości uproszczonej zamiast typu odwołania, aby uniknąć dodatkowych alokacji pamięci.

.NET udostępnia <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> strukturę jako uproszczoną implementację uogólnionej wartości zwracanej zadania. Aby użyć <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> tego typu, `System.Threading.Tasks.Extensions` należy dodać pakiet NuGet do projektu. W poniższym <xref:System.Threading.Tasks.ValueTask%601> przykładzie użyto struktury, aby pobrać wartość dwóch rzutów kości.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Przepływ sterowania w programach asynchroniczny (C#)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
