---
title: Asynchroniczne typy zwracane (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 3d3c7d610dd1287d2c7284a5edd9c92810a74dba
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45526918"
---
# <a name="async-return-types-c"></a>Asynchroniczne typy zwracane (C#)
Metody asynchroniczne mogą być zwracane typy:

- <xref:System.Threading.Tasks.Task%601>, w metodzie asynchronicznej, która nie zwraca wartości. 
 
-  <xref:System.Threading.Tasks.Task>, w metodzie asynchronicznej, która wykonuje operację, ale nie zwraca żadnej wartości.

- `void`, procedury obsługi zdarzeń. 

- Począwszy od C# 7.0, dowolny typ, który jest dostępny `GetAwaiter` metody. Obiekt zwrócony przez `GetAwaiter` musi implementować metody <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> interfejsu.
  
Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [Asynchronous Programming with async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
Każdy typ zwracany jest badany w jednej z następujących sekcji, a można znaleźć pełny przykład, który używa wszystkich trzech typów na końcu tego tematu.  
  
##  <a name="BKMK_TaskTReturnType"></a> Zadanie\<TResult\> zwracany typ  
<xref:System.Threading.Tasks.Task%601> Typ zwracany jest używany w metodzie asynchronicznej, która zawiera [zwracają](../../../../csharp/language-reference/keywords/return.md) instrukcji (C#), w której operator ma typ `TResult`.  
  
W poniższym przykładzie `GetLeisureHours` metoda asynchroniczna `return` instrukcję, która zwraca liczbę całkowitą. Dlatego deklaracja metody musi określać typ zwracany `Task<int>`.  <xref:System.Threading.Tasks.Task.FromResult%2A> Metody asynchronicznej jest symbolem zastępczym dla operacji, która zwraca wartość typu ciąg.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Podczas `GetLeisureHours` jest wywoływana z poziomu wyrażenia await w `ShowTodaysInfo` metodę, wyrażenie await pobiera wartość całkowitą (wartość `leisureHours`) jest przechowywana w zadaniu zwrócony przez `GetLeisureHours` metody. Aby uzyskać więcej informacji dotyczących wyrażeń oczekiwania, zobacz [await](../../../../csharp/language-reference/keywords/await.md).  
  
Można lepiej zrozumieć, jak to się dzieje oddzielając wywołanie `GetLeisureHours` ze stosowania `await`, jak pokazano w poniższym kodzie. Wywołanie metody `GetLeisureHours` , która nie jest oczekiwana natychmiast zwraca `Task<int>`, jak można oczekiwać od deklaracji metody. Zadanie zostanie przypisane do `infoTask` zmiennej w przykładzie. Ponieważ `infoTask` jest <xref:System.Threading.Tasks.Task%601>, zawiera on <xref:System.Threading.Tasks.Task%601.Result> właściwości typu `TResult`. W tym przypadku `TResult` reprezentuje typ liczby całkowitej. Gdy `await` jest stosowany do `infoTask`, wyrażenie czekania zwraca wynik zawartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość `infoTask`. Wartość jest przypisywana do `ret` zmiennej.  
  
> [!IMPORTANT]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość jest właściwością blokowania. Jeśli spróbujesz się do niej dostęp przed zakończeniem jej zadania, wątek, który jest obecnie aktywny jest zablokowany do momentu ukończenia zadania i wartość jest dostępna. W większości przypadków należy dostęp do wartości przy użyciu `await` zamiast bezpośrednio dostęp do właściwości. <br/> Poprzedni przykład pobrać wartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości do blokowania wątku głównego, aby `ShowTodaysInfo` metoda może zakończyć wykonywania przed aplikacji zakończył się.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
##  <a name="BKMK_TaskReturnType"></a> Zwracany typ Task  
Metody asynchroniczne, które nie zawierają `return` instrukcji lub które zawierają `return` instrukcję, która nie zwraca operandu są zazwyczaj ma typ zwracany <xref:System.Threading.Tasks.Task>. Takie metody zwracają `void` jeśli one były uruchamiane synchronicznie. Jeśli używasz <xref:System.Threading.Tasks.Task> zwracany typ metody asynchronicznej, wywoływania metody można użyć `await` operator wstrzymania uzupełniania wywołującego do momentu zakończenia wywołanej metody asynchronicznej.  
  
W poniższym przykładzie `WaitAndApologize` metoda asynchroniczna nie zawiera `return` instrukcji, więc metoda ta zwraca <xref:System.Threading.Tasks.Task> obiektu. Dzięki temu `WaitAndApologize` oczekiwanie. Należy pamiętać, że <xref:System.Threading.Tasks.Task> nie zawiera typu `Result` właściwość ponieważ nie zwraca żadnej wartości.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize` jest oczekiwane, za pomocą instrukcji await, a nie wyrażenia await, podobnie do instrukcji wywołujące na metodę asynchroniczną zwracającą typ void. W tym przypadku zastosowanie operatora await nie generuje wartości.  
  
Jak w poprzednim <xref:System.Threading.Tasks.Task%601> przykład, można oddzielić wywołanie `WaitAndApologize` z aplikacji operatora await, jak poniższy kod przedstawia. Jednak należy pamiętać, że `Task` nie ma `Result` właściwość i że wartość nie jest generowany, gdy await operator jest stosowany do `Task`.  
  
Poniższy kod oddziela wywoływanie metody `WaitAndApologize` metody z Oczekujące na zadanie, które zwraca metoda.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
##  <a name="BKMK_VoidReturnType"></a> Typ zwracany void

Możesz użyć `void` zwracany typ w procedurze obsługi zdarzeń asynchronicznych, które wymagają `void` typ zwracany. W przypadku metod innych niż procedury obsługi zdarzeń, które nie zwrócą wartość, powinna zwrócić <xref:System.Threading.Tasks.Task> zamiast tego, ponieważ metoda asynchroniczna zwraca `void` nie może być oczekiwany. Dowolny obiekt wywołujący taką metodę musi być w stanie kontynuować do zakończenia bez oczekiwania na zakończenie metody asynchronicznej, a obiekt wywołujący musi być niezależny od wartości lub wyjątków, które generuje metoda asynchroniczna.  
  
Obiekt wywołujący metodę async zwraca void nie może przechwytywać wyjątków, które są generowane przez tę metodę, i takie nieobsłużone wyjątki mogą może spowodować awarię aplikacji. Jeśli wystąpi wyjątek w metodzie asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, wyjątek jest przechowywany w zwróconym zadaniu i jest ponownie zgłaszany, gdy zadanie jest oczekiwane. Dlatego upewnij się, że każda metoda asynchroniczna, która może spowodować wyjątek ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i że trwa oczekiwanie na wywołania metody.  
  
Aby uzyskać więcej informacji dotyczących wyjątków CATCH w metodach asynchronicznych, zobacz [wyjątki w metodach asynchronicznych](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) części [try-catch —](../../../language-reference/keywords/try-catch.md) tematu.  
  
Poniższy przykład pokazuje zachowanie programu async obsługi zdarzeń. Należy pamiętać, że w przykładowym kodzie, programu async obsługi zdarzeń musi umożliwić wiedzieć, po zakończeniu wątku głównego. Następnie wątek główny może oczekiwać programu async obsługi zdarzeń ukończyć przed zakończeniem pracy w programie.
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetasktresult"></a>Uogólnionego asynchroniczne typy zwracane i ValueTask\<TResult\>

Począwszy od języka C# 7.0 metody asynchronicznej może zwrócić dowolnego typu, który ma dostępne `GetAwaiter` metody.
 
Ponieważ <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> są typami odwołań, alokacji pamięci w ścieżkach newralgicznym dla wydajności, szczególnie w przypadku, gdy alokacje występują w ścisłej pętli, może niekorzystnie wpłynąć na wydajność. Pomoc techniczna dla ogólnych typów zwracanych oznacza, że może zwrócić typu lightweight wartości zamiast typem referencyjnym, aby uniknąć alokacji pamięci dodatkowe. 

.NET zapewnia <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> struktury jako lekki stosowania uogólnionego wartość zwracania zadania. Aby użyć <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> typu, należy dodać `System.Threading.Tasks.Extensions` pakiet NuGet do projektu. W poniższym przykładzie użyto <xref:System.Threading.Tasks.ValueTask%601> przedstawia strukturę, aby pobrać wartość dwóch dice. 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.Task.FromResult%2A>   
- [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
- [Przepływ sterowania w programach Async (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)   
- [async](../../../../csharp/language-reference/keywords/async.md)   
- [await](../../../../csharp/language-reference/keywords/await.md)
