---
title: Asynchroniczne typy zwracane (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 07aefcf3149b2210e3dc97713647fa3a0133a535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334187"
---
# <a name="async-return-types-c"></a>Asynchroniczne typy zwracane (C#)
Metody asynchroniczne może mieć następujące typy zwracane:

- <xref:System.Threading.Tasks.Task%601>, dla metody asynchronicznej, która nie zwraca wartości. 
 
-  <xref:System.Threading.Tasks.Task>, dla metody asynchronicznej, który wykonuje operację, ale nie zwraca żadnej wartości.

- `void`, dla programu obsługi zdarzeń. 

- Począwszy od C# 7.0, dowolnego typu, który jest dostępny `GetAwaiter` metody. Obiekt zwrócony przez `GetAwaiter` musi implementować metodę <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> interfejsu.
  
Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
Każdy typ zwracany jest sprawdzany w jednej z następujących sekcji, a znajduje się pełny przykład, który używa wszystkich trzech typów na końcu tego tematu.  
  
##  <a name="BKMK_TaskTReturnType"></a> Zwracany typ Task(T)  
<xref:System.Threading.Tasks.Task%601> Zwracany typ jest używany dla metody asynchronicznej, który zawiera [zwracać](../../../../csharp/language-reference/keywords/return.md) instrukcji (C#), w którym argument operacji ma typ `TResult`.  
  
W poniższym przykładzie `GetLeisureHours` zawiera metody asynchronicznej `return` instrukcji, która zwraca liczbę całkowitą. W związku z tym deklaracji metody należy określić typ zwracany `Task<int>`.  <xref:System.Threading.Tasks.Task.FromResult%2A> Metody asynchronicznej jest symbolem zastępczym dla danej operacji, która zwraca wartość typu ciąg.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Gdy `GetLeisureHours` jest wywołana wewnątrz wyrażenie await w `ShowTodaysInfo` metoda, wyrażenie await pobiera wartość całkowita (wartość `leisureHours`) jest przechowywana w zadanie zwrócone przez `GetLeisureHours` — metoda. Aby uzyskać więcej informacji na temat await wyrażeń, zobacz [await](../../../../csharp/language-reference/keywords/await.md).  
  
Lepiej zrozumieć, jak dzieje się tak, dzieląc wywołanie `GetLeisureHours` ze stosowania `await`, jak pokazano w następującym kodem. Wywołanie metody `TaskOfT_MethodAsync` , która nie jest od razu oczekiwano zwraca `Task<int>`, jak można oczekiwać od deklaracji metody. Zadanie jest przypisany do `integerTask` zmiennej w przykładzie. Ponieważ `integerTask` jest <xref:System.Threading.Tasks.Task%601>, zawiera <xref:System.Threading.Tasks.Task%601.Result> właściwości typu `TResult`. W takim przypadku TResult reprezentuje typu integer. Gdy `await` jest stosowany do `integerTask`, wyrażenie await ma zawartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość `integerTask`. Wartość jest przypisywana do `result2` zmiennej.  
  
> [!IMPORTANT]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość jest właściwością blokowania. Jeśli spróbujesz się do niego dostęp, przed jego zadanie jest zakończone, wątku, który jest obecnie aktywny jest zablokowany, dopiero po zakończeniu zadania i wartość jest dostępna. W większości przypadków, uzyskaniu dostępu wartość w przy użyciu `await` zamiast bezpośrednie uzyskiwanie dostępu do właściwości. <br/> Poprzedni przykład pobrać wartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości mają być blokowane z wątku głównego, aby `ShowTodaysInfo` metody może zakończyć wykonywania, zanim aplikacja została zakończona.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
##  <a name="BKMK_TaskReturnType"></a> Zwracany typ zadania  
Metody asynchroniczne, które nie zawierają `return` instrukcji lub które zawiera `return` instrukcji, która nie zwraca zwykle argumentu operacji ma typ zwracany <xref:System.Threading.Tasks.Task>. Takie metody zwracają `void` jeśli są uruchamiane synchronicznie. Jeśli używasz <xref:System.Threading.Tasks.Task> typ zwracany dla metody asynchronicznej metody wywołującej można użyć `await` operatora, aby wstrzymać ukończenia wywołującego przed zakończeniem metody asynchronicznej o nazwie.  
  
W poniższym przykładzie `WaitAndApologize` metoda asynchroniczna nie zawiera `return` instrukcji, dlatego metoda zwraca <xref:System.Threading.Tasks.Task> obiektu. Dzięki temu `WaitAndApologize` do można zdefiniować dla niego oczekiwania. Należy pamiętać, że <xref:System.Threading.Tasks.Task> nie zawiera typu `Result` właściwości ponieważ go nie ma zwracanych wartości.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize` jest oczekiwane przy użyciu instrukcji await zamiast wyrażenie await, podobna do instrukcji wywołania synchronicznego metody zwracające typ void. W tym przypadku zastosowanie operatora await nie tworzy wartości.  
  
Jak w poprzedniej <xref:System.Threading.Tasks.Task%601> przykładzie można oddzielić wywołanie `Task_MethodAsync` z zastosowania operatora await jako poniższy kod przedstawia. Należy jednak pamiętać, że `Task` nie ma `Result` właściwości i że żadna wartość jest generowany po zastosowaniu operatora await do `Task`.  
  
Poniższy kod oddziela wywołania `WaitAndApologize` metody z oczekiwanie na zadanie, które zwraca metodę.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
##  <a name="BKMK_VoidReturnType"></a> Zwrócony typ void  
Możesz użyć `void` typ zwracany w obsłudze zdarzenia asynchroniczne, które wymagają `void` typ zwracany. Dla metod innych niż zdarzeń obsługi nie zwraca wartości, jak Zwróć <xref:System.Threading.Tasks.Task> , ponieważ metoda asynchroniczna zwracająca `void` nie może być oczekiwane. Wszelkie wywołującego taka metoda musi mieć możliwość nadal ukończenia bez oczekiwania na metody asynchronicznej wywołany zakończyć, a obiekt wywołujący musi być niezależne od dowolnej wartości lub wyjątki, które generuje metody asynchronicznej.  
  
Obiekt wywołujący metody asynchronicznej zwracające typ void nie może przechwycić wyjątki, które są generowane przez metodę i takich nieobsługiwanych wyjątków są może spowodować awarię aplikacji. Jeśli wystąpi wyjątek w to metoda asynchroniczna, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, wyjątek jest przechowywany w zwrócony zadań i jest zgłoszony, gdy zadanie jest oczekiwane. W związku z tym, upewnij się, że wszystkie metoda asynchroniczna, która może spowodować wyjątek ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i że wywołania metody są oczekiwane.  
  
Aby uzyskać więcej informacji o sposobie przechwytywanie wyjątków w metodach asynchronicznych, zobacz [try-catch](../../../../csharp/language-reference/keywords/try-catch.md) .  
  
Następujące eample definiuje asynchronicznej obsługi zdarzeń.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetaskt"></a>Uogólniony asynchroniczne typy zwracane i ValueTask<T>

Począwszy od wersji 7.0 C#, to metoda asynchroniczna może zwracać dowolnego typu, który jest dostępny `GetAwaiter` metody.
 
Ponieważ <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> są typów referencyjnych, alokacji pamięci ścieżek krytycznych wydajności, szczególnie w przypadku, gdy występują alokacji w pętli ścisłej może niekorzystnie wpłynąć na wydajność. Obsługa oznacza uogólniony zwracane typy czy może zwracać typu lightweight wartości zamiast typem referencyjnym, aby uniknąć dodatkowej pamięci alokacji. 

Udostępnia .NET <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> struktury jako lekki stosowania uogólniony wartości umożliwiające zwracanie zadań. Aby użyć <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> typu, należy dodać `System.Threading.Tasks.Extensions` pakiet NuGet do projektu. W poniższym przykładzie użyto <xref:System.Threading.Tasks.ValueTask%601> przedstawia strukturę do pobierania wartości dwa grupowane. 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Zobacz także  
<xref:System.Threading.Tasks.Task.FromResult%2A>   
[Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
[Przepływ sterowania w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)   
[Asynchroniczne](../../../../csharp/language-reference/keywords/async.md)   
[await](../../../../csharp/language-reference/keywords/await.md)
