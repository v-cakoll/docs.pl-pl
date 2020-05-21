---
title: Asynchroniczne typy zwracane (C#)
ms.date: 04/14/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: c2584f1e285a7ab76eb43f9a211a8d2a51c2c55e
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761879"
---
# <a name="async-return-types-c"></a>Asynchroniczne typy zwracane (C#)

Metody asynchroniczne mogą mieć następujące typy zwracane:

- <xref:System.Threading.Tasks.Task%601>dla metody asynchronicznej, która zwraca wartość.
- <xref:System.Threading.Tasks.Task>dla metody asynchronicznej, która wykonuje operację, ale nie zwraca żadnej wartości.
- `void`dla programu obsługi zdarzeń.
- Począwszy od języka C# 7,0, dowolnego typu, który ma dostępną `GetAwaiter` metodę. Obiekt zwrócony przez `GetAwaiter` metodę musi implementować <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> interfejs.
- Począwszy od języka C# 8,0, <xref:System.Collections.Generic.IAsyncEnumerable%601> dla metody asynchronicznej zwracającej *strumień asynchroniczny*.

Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i Await (C#)](./index.md).  
  
## <a name="tasktresult-return-type"></a>\< \> Typ zwracany TResult zadania  
<xref:System.Threading.Tasks.Task%601>Typ zwracany jest używany dla metody asynchronicznej, która zawiera instrukcję [Return](../../../language-reference/keywords/return.md) (C#), w której operandem jest `TResult` .  
  
W poniższym przykładzie `GetLeisureHours` Metoda async zawiera `return` instrukcję zwracającą liczbę całkowitą. W związku z tym Deklaracja metody musi określać zwracany typ `Task<int>` .  <xref:System.Threading.Tasks.Task.FromResult%2A>Metoda async jest symbolem zastępczym dla operacji zwracającej ciąg.
  
:::code language="csharp" source="./snippets/async-return-types/async-returns1.cs" id="SnippetFirstExample":::

Gdy `GetLeisureHours` jest wywoływana z w wyrażeniu await w `ShowTodaysInfo` metodzie, wyrażenie await Pobiera wartość całkowitą (wartość `leisureHours` ), która jest przechowywana w zadaniu zwróconym przez `GetLeisureHours` metodę. Aby uzyskać więcej informacji na temat wyrażeń await, zobacz [await](../../../language-reference/operators/await.md).  
  
Można lepiej zrozumieć, jak `await` Pobiera wynik z a `Task<T>` przez oddzielenie wywołania `GetLeisureHours` z aplikacji `await` , jak pokazano w poniższym kodzie. Wywołanie metody `GetLeisureHours` , która nie jest bezpośrednio oczekiwane, zwraca `Task<int>` , jak oczekiwano od deklaracji metody. Zadanie jest przypisane do `integerTask` zmiennej w przykładzie. Ponieważ `integerTask` jest <xref:System.Threading.Tasks.Task%601> , zawiera <xref:System.Threading.Tasks.Task%601.Result> Właściwość typu `TResult` . W tym przypadku `TResult` reprezentuje typ Integer. Gdy `await` jest stosowany do `integerTask` , wyrażenie await oblicza zawartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości `integerTask` . Wartość jest przypisana do `ret` zmiennej.  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A>Właściwość jest właściwością blokującą. Jeśli spróbujesz uzyskać dostęp do niego przed ukończeniem zadania, wątek, który jest obecnie aktywny, jest blokowany do momentu zakończenia zadania, a wartość jest dostępna. W większości przypadków należy uzyskać dostęp do wartości przy użyciu `await` zamiast bezpośrednio uzyskać dostęp do właściwości. <br/> W poprzednim przykładzie pobrano wartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości w celu zablokowania wątku głównego, tak aby `ShowTodaysInfo` Metoda mogła zakończyć wykonywanie przed zakończeniem działania aplikacji.  

:::code language="csharp" source="./snippets/async-return-types/async-returns1a.cs" id="SnippetSecondVersion":::

## <a name="task-return-type"></a>Typ zwracany zadania  
Metody asynchroniczne, które nie zawierają `return` instrukcji lub zawierające `return` instrukcję, która nie zwraca operandu, zwykle mają typ zwracany <xref:System.Threading.Tasks.Task> . Takie metody zwracają, `void` Jeśli są uruchamiane synchronicznie. Jeśli używasz <xref:System.Threading.Tasks.Task> typu zwracanego dla metody asynchronicznej, Metoda wywołująca może użyć operatora, `await` Aby zawiesić zakończenie obiektu wywołującego do momentu zakończenia wywołanej metody asynchronicznej.  
  
W poniższym przykładzie `WaitAndApologize` Metoda async nie zawiera `return` instrukcji, dlatego metoda zwraca <xref:System.Threading.Tasks.Task> obiekt. Zwracanie elementu `Task` umożliwia `WaitAndApologize` oczekiwanie. <xref:System.Threading.Tasks.Task>Typ nie zawiera właściwości, `Result` ponieważ nie ma wartości zwracanej.  

:::code language="csharp" source="./snippets/async-return-types/async-returns2.cs" id="SnippetTaskReturn":::

`WaitAndApologize`oczekuje się przy użyciu instrukcji Await zamiast wyrażenia await, podobnie jak instrukcja wywołująca synchronicznej metody zwracającej wartość void. W tym przypadku aplikacja operatora await nie tworzy wartości.  
  
Tak jak w poprzednim <xref:System.Threading.Tasks.Task%601> przykładzie, można oddzielić wywołanie `WaitAndApologize` od aplikacji operatora await, jak pokazano w poniższym kodzie. Należy jednak pamiętać, że element `Task` nie ma `Result` właściwości i że żadna wartość nie jest generowana, gdy operator await jest stosowany do `Task` .  
  
Poniższy kod oddziela wywoływanie `WaitAndApologize` metody od oczekiwania na zadanie, które zwraca metoda.  

:::code language="csharp" source="./snippets/async-return-types/async-returns2a.cs" id="SnippetAwaitTask":::

## <a name="void-return-type"></a>Typ zwracany void

`void`Typ zwracany jest używany w asynchronicznych obsłudze zdarzeń, które wymagają `void` typu zwracanego. W przypadku metod innych niż programy obsługi zdarzeń, które nie zwracają wartości, należy zwrócić <xref:System.Threading.Tasks.Task> zamiast tego, ponieważ Metoda async, która zwraca `void` nie można oczekiwać. Każdy obiekt wywołujący taką metodę musi kontynuować działanie bez oczekiwania na zakończenie wywołanej metody asynchronicznej. Obiekt wywołujący musi być niezależny od wszelkich wartości lub wyjątków generowanych przez metodę asynchroniczną.  
  
Obiekt wywołujący metodę asynchroniczną zwracającą wartość void nie może przechwytywać wyjątków zgłoszonych z metody, a takie Nieobsłużone wyjątki mogą spowodować niepowodzenie działania aplikacji. Jeśli metoda zwracająca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> zgłasza wyjątek, wyjątek jest przechowywany w zwracanym zadaniu. Wyjątek jest zgłaszany ponownie po oczekiwaniu na zadanie. W związku z tym upewnij się, że jakakolwiek Metoda asynchroniczna, która może generować wyjątek, ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i że wywołania metody są oczekiwane.  
  
Aby uzyskać więcej informacji o sposobie przechwytywania wyjątków w metodach asynchronicznych, zobacz sekcję [wyjątki w metodach asynchronicznych](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) artykułu [try-catch](../../../language-reference/keywords/try-catch.md) .  
  
W poniższym przykładzie pokazano zachowanie programu obsługi zdarzeń asynchronicznych. W przykładowym kodzie, procedura obsługi zdarzeń asynchronicznych musi pozwolić, aby główny wątek był znany po zakończeniu. Następnie wątek główny może poczekać na zakończenie obsługi zdarzeń asynchronicznych przed zamknięciem programu.

:::code language="csharp" source="./snippets/async-return-types/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Uogólnione asynchroniczne typy zwracane i ValueTask \< TResult\>

Począwszy od języka C# 7,0, Metoda asynchroniczna może zwracać dowolny typ, który ma dostępną `GetAwaiter` metodę.

Ponieważ <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> są typami odwołań, alokacja pamięci w ścieżkach o krytycznym znaczeniu dla wydajności, szczególnie gdy przydziały występują w ścisłych pętlach, mogą mieć negatywny wpływ na wydajność. Obsługa uogólnionych typów zwracanych oznacza, że można zwrócić typ wartości lekkiej zamiast typu referencyjnego, aby uniknąć dodatkowych alokacji pamięci.

Platforma .NET udostępnia <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> strukturę jako lekkie implementacje ogólnej wartości zwracanego zadania. Aby użyć tego <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> typu, należy dodać `System.Threading.Tasks.Extensions` pakiet NuGet do projektu. Poniższy przykład używa struktury, <xref:System.Threading.Tasks.ValueTask%601> Aby pobrać wartość dwóch przerzutów z kością.
  
:::code language="csharp" source="./snippets/async-return-types/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>Strumienie asynchroniczne z IAsyncEnumerable \< T\>

Począwszy od języka C# 8,0, Metoda asynchroniczna może zwracać *strumień asynchroniczny*reprezentowany przez <xref:System.Collections.Generic.IAsyncEnumerable%601> . Strumień asynchroniczny umożliwia Wyliczenie elementów odczytanych ze strumienia, gdy elementy są generowane w fragmentach z powtarzalnymi wywołaniami asynchronicznymi. Poniższy przykład przedstawia metodę asynchroniczną generującą strumień asynchroniczny:

:::code language="csharp" source="./snippets/async-return-types/AsyncStreams.cs" id="SnippetGenerateAsyncStream":::

Poprzedni przykład odczytuje wiersze z ciągu asynchronicznie. Po odczytaniu każdego wiersza kod wylicza każdy wyraz w ciągu. Obiekty wywołujące spowodują Wyliczenie każdego wyrazu przy użyciu `await foreach` instrukcji. Metoda oczekuje, gdy musi asynchronicznie odczytać następny wiersz z ciągu źródłowego.

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Przepływ sterowania w programach asynchronicznych (C#)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
