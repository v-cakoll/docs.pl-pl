---
title: Asynchroniczne typy zwracane (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 2c0dae6b4357ce89325ecb9b7d70ffd79f4e9417
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168400"
---
# <a name="async-return-types-c"></a>Asynchroniczne typy zwracane (C#)
Metody asynchroniczne mogą mieć następujące typy zwracane:

- <xref:System.Threading.Tasks.Task%601>dla metody asynchronicznej, która zwraca wartość. 
 
- <xref:System.Threading.Tasks.Task>dla metody asynchronicznej, która wykonuje operację, ale nie zwraca żadnej wartości.

- `void`dla programu obsługi zdarzeń. 

- Począwszy od C# 7,0, dowolnego typu, który ma dostępną `GetAwaiter` metodę. Obiekt zwrócony przez `GetAwaiter` metodę musi <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> implementować interfejs.
  
Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z AsyncC#i Await ()](./index.md).  
  
Każdy typ zwracany jest badany w jednej z poniższych sekcji i można znaleźć pełny przykład, który używa wszystkich trzech typów na końcu tematu.  
  
## <a name="BKMK_TaskTReturnType"></a>Typ\<zwracany\> TResult zadania  
Typ zwracany jest używany dla metody asynchronicznej, która zawiera instrukcję [Return](../../../language-reference/keywords/return.md) (C#), w której argument operacji ma typ `TResult`. <xref:System.Threading.Tasks.Task%601>  
  
W poniższym przykładzie `GetLeisureHours` Metoda async `return` zawiera instrukcję zwracającą liczbę całkowitą. W związku z tym Deklaracja metody musi określać zwracany typ `Task<int>`.  Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> Async jest symbolem zastępczym dla operacji zwracającej ciąg.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Gdy `GetLeisureHours` jest wywoływana z w wyrażeniu await `ShowTodaysInfo` w metodzie, wyrażenie await pobiera `leisureHours`wartość całkowitą (wartość), która `GetLeisureHours` jest przechowywana w zadaniu zwróconym przez metodę. Aby uzyskać więcej informacji na temat wyrażeń await, zobacz [await](../../../language-reference/operators/await.md).  
  
Można lepiej zrozumieć `GetLeisureHours` `await`, jak to się dzieje, oddzielając wywołanie od aplikacji, jak pokazano w poniższym kodzie. Wywołanie metody `GetLeisureHours` , która nie jest bezpośrednio oczekiwane `Task<int>`, zwraca, jak oczekiwano od deklaracji metody. Zadanie jest przypisane do `integerTask` zmiennej w przykładzie. Ponieważ `integerTask` jest,zawiera<xref:System.Threading.Tasks.Task%601.Result> właściwość typu `TResult`. <xref:System.Threading.Tasks.Task%601> W tym przypadku `TResult` reprezentuje typ Integer. Gdy `await` jest stosowany do `integerTask`, wyrażenie await oblicza `integerTask`zawartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości. Wartość jest przypisana do `ret` zmiennej.  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość jest właściwością blokującą. Jeśli spróbujesz uzyskać dostęp do niego przed ukończeniem zadania, wątek, który jest obecnie aktywny, jest blokowany do momentu zakończenia zadania, a wartość jest dostępna. W większości przypadków należy uzyskać dostęp do wartości przy użyciu `await` zamiast bezpośrednio uzyskać dostęp do właściwości. <br/> W poprzednim przykładzie pobrano wartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości w celu zablokowania wątku głównego, tak `ShowTodaysInfo` aby Metoda mogła zakończyć wykonywanie przed zakończeniem działania aplikacji.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
## <a name="BKMK_TaskReturnType"></a>Typ zwracany zadania  
Metody asynchroniczne, które nie zawierają `return` instrukcji lub `return` zawierające instrukcję, która nie zwraca operandu, zwykle <xref:System.Threading.Tasks.Task>mają typ zwracany. Takie metody zwracają `void` , jeśli są uruchamiane synchronicznie. Jeśli używasz <xref:System.Threading.Tasks.Task> typu zwracanego dla metody asynchronicznej, Metoda wywołująca może `await` użyć operatora, aby zawiesić zakończenie obiektu wywołującego do momentu zakończenia wywołanej metody asynchronicznej.  
  
W poniższym przykładzie `WaitAndApologize` Metoda async nie `return` zawiera instrukcji, <xref:System.Threading.Tasks.Task> Dlatego metoda zwraca obiekt. Dzięki `WaitAndApologize` temu można oczekiwać. Należy zauważyć, <xref:System.Threading.Tasks.Task> że typ nie `Result` zawiera właściwości, ponieważ nie ma wartości zwracanej.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize`oczekuje się przy użyciu instrukcji Await zamiast wyrażenia await, podobnie jak instrukcja wywołująca synchronicznej metody zwracającej wartość void. W tym przypadku aplikacja operatora await nie tworzy wartości.  
  
Tak jak w poprzednim <xref:System.Threading.Tasks.Task%601> przykładzie, można oddzielić `WaitAndApologize` wywołanie od aplikacji operatora await, jak pokazano w poniższym kodzie. Należy jednak pamiętać, że `Task` element nie `Result` ma właściwości i że żadna wartość nie jest generowana, gdy `Task`operator await jest stosowany do.  
  
Poniższy kod oddziela wywoływanie `WaitAndApologize` metody od oczekiwania na zadanie, które zwraca metoda.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
## <a name="BKMK_VoidReturnType"></a>Typ zwracany void

Typ `void` zwracany jest używany w asynchronicznych obsłudze zdarzeń, które `void` wymagają typu zwracanego. W przypadku metod innych niż programy obsługi zdarzeń, które nie zwracają wartości, należy zwrócić <xref:System.Threading.Tasks.Task> zamiast tego, ponieważ Metoda async, która zwraca `void` nie można oczekiwać. Każdy obiekt wywołujący taką metodę musi być w stanie kontynuować ukończenie bez oczekiwania na zakończenie wywołanej metody asynchronicznej, a obiekt wywołujący musi być niezależny od wartości lub wyjątków, które generuje Metoda asynchroniczna.  
  
Obiekt wywołujący metodę asynchroniczną zwracającą wartość void nie może przechwytywać wyjątków, które są generowane przez metodę, a takie Nieobsłużone wyjątki mogą spowodować niepowodzenie działania aplikacji. Jeśli wystąpi wyjątek w metodzie asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, wyjątek jest przechowywany w zwracanym zadaniu i jest ponownie zgłaszany, gdy zadanie zostanie oczekiwane. W związku z tym upewnij się, że jakakolwiek Metoda asynchroniczna, która może generować wyjątek, <xref:System.Threading.Tasks.Task> ma <xref:System.Threading.Tasks.Task%601> typ zwracany lub i że wywołania metody są oczekiwane.  
  
Aby uzyskać więcej informacji o sposobie przechwytywania wyjątków w metodach asynchronicznych, zobacz sekcję [wyjątki w metodach asynchronicznych](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) tematu [try-catch](../../../language-reference/keywords/try-catch.md) .  
  
W poniższym przykładzie pokazano zachowanie programu obsługi zdarzeń asynchronicznych. Należy zauważyć, że w przykładowym kodzie procedura obsługi zdarzeń asynchronicznych musi pozwolić, aby główny wątek wiedział, kiedy zakończy się. Następnie wątek główny może poczekać na zakończenie obsługi zdarzeń asynchronicznych przed zamknięciem programu.
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetasktresult"></a>Uogólnione asynchroniczne typy zwracane i ValueTask\<TResult\>

Począwszy od C# 7,0, Metoda asynchroniczna może zwracać dowolny typ, który ma dostępną `GetAwaiter` metodę.
 
Ponieważ <xref:System.Threading.Tasks.Task> i<xref:System.Threading.Tasks.Task%601> są typami odwołań, alokacja pamięci w ścieżkach o krytycznym znaczeniu dla wydajności, szczególnie gdy przydziały występują w ścisłych pętlach, mogą mieć negatywny wpływ na wydajność. Obsługa uogólnionych typów zwracanych oznacza, że można zwrócić typ wartości lekkiej zamiast typu referencyjnego, aby uniknąć dodatkowych alokacji pamięci. 

Platforma .NET udostępnia <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> strukturę jako lekkie implementacje ogólnej wartości zwracanego zadania. Aby użyć tego <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> typu, należy `System.Threading.Tasks.Extensions` dodać pakiet NuGet do projektu. Poniższy przykład używa <xref:System.Threading.Tasks.ValueTask%601> struktury, aby pobrać wartość dwóch przerzutów z kością. 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą AsyncC#i Await ()](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Przepływ sterowania w programach asynchronicznychC#()](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
