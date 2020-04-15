---
title: Typy zwrotów asynchronii (C#)
ms.date: 04/14/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 73a6e1924652c8635377547e2faddc864ac5540a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389132"
---
# <a name="async-return-types-c"></a>Typy zwrotów asynchronii (C#)

Metody asynchronizowe mogą mieć następujące typy zwracane:

- <xref:System.Threading.Tasks.Task%601>, dla metody asynchronii, która zwraca wartość.
- <xref:System.Threading.Tasks.Task>, dla metody asynchronizowej, która wykonuje operację, ale zwraca żadną wartość.
- `void`, dla programu obsługi zdarzeń.
- Począwszy od języka C# 7.0, `GetAwaiter` dowolnego typu, który ma metodę dostępną. Obiekt zwracany `GetAwaiter` przez metodę <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> musi implementować interfejs.
- Począwszy od C# 8.0, <xref:System.Collections.Generic.IAsyncEnumerable%601>dla metody asynchronii, która zwraca strumień *asynchronii*.

Aby uzyskać więcej informacji na temat metod [asynchronicznych, zobacz Programowanie asynchroniczne za pomocą asynchronii i await (C#)](./index.md).  
  
## <a name="tasktresult-return-type"></a>Typ\<powrotu\> zadania TResult  
Typ <xref:System.Threading.Tasks.Task%601> zwracany jest używany dla metody asynchroniiowej, która zawiera instrukcję [return](../../../language-reference/keywords/return.md) (C#), w której jest `TResult`operand .  
  
W poniższym przykładzie `GetLeisureHours` metoda asynchroniowa zawiera instrukcję, `return` która zwraca liczbę całkowitą. W związku z tym deklaracja metody `Task<int>`musi określać typ zwracany .  Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> asynchronikowa jest symbolem zastępczym operacji zwraca ciąg.
  
:::code language="csharp" source="./snippets/async-returns1.cs" id="SnippetFirstExample":::

Gdy `GetLeisureHours` jest wywoływana z wewnątrz `ShowTodaysInfo` await wyrażenie w metodzie, wyrażenie await pobiera `leisureHours`wartość całkowitą (wartość ), który `GetLeisureHours` jest przechowywany w zadaniu zwróconym przez metodę. Aby uzyskać więcej informacji na temat oczekujących wyrażeń, zobacz [await](../../../language-reference/operators/await.md).  
  
Można lepiej zrozumieć, `await` jak pobiera `Task<T>` wynik z a `GetLeisureHours` przez oddzielenie `await`wywołania od aplikacji , jak pokazano w poniższym kodzie. Wywołanie metody, `GetLeisureHours` która nie jest natychmiast `Task<int>`oczekiwana zwraca , zgodnie z oczekiwaniami po deklaracji metody. Zadanie jest przypisane `integerTask` do zmiennej w przykładzie. Ponieważ `integerTask` jest <xref:System.Threading.Tasks.Task%601>, zawiera <xref:System.Threading.Tasks.Task%601.Result> właściwość `TResult`typu . W takim `TResult` przypadku reprezentuje typ liczby całkowitej. Po `await` zastosowaniu `integerTask`do wyrażenia await oblicza zawartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości `integerTask`. Wartość jest przypisana `ret` do zmiennej.  
  
> [!IMPORTANT]
> Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A> jest właściwością blokującą. Jeśli spróbujesz uzyskać do niego dostęp przed zakończeniem zadania, wątek, który jest aktualnie aktywny, jest zablokowany do momentu ukończenia zadania i udostępnienia wartości. W większości przypadków należy uzyskać dostęp `await` do wartości przy użyciu zamiast dostępu do właściwości bezpośrednio. <br/> W poprzednim przykładzie pobrano <xref:System.Threading.Tasks.Task%601.Result%2A> wartość właściwości, aby zablokować wątek główny, dzięki czemu `ShowTodaysInfo` metoda może zakończyć wykonywanie przed zakończeniem aplikacji.  

:::code language="csharp" source="./snippets/async-returns1a.cs" id="SnippetSecondVersion":::

## <a name="task-return-type"></a>Typ zwrotu zadania  
Metody asynchronizowe, `return` które nie zawierają `return` instrukcji lub które zawierają instrukcję, która <xref:System.Threading.Tasks.Task>nie zwraca operandu, zwykle mają typ zwracany . Takie metody `void` zwracają, jeśli działają synchronicznie. Jeśli używasz <xref:System.Threading.Tasks.Task> typu zwracanego dla metody asynchroniiowej, metoda wywołująca może użyć `await` operatora, aby zawiesić zakończenie wywołującego, dopóki wywołana metoda asynchronii nie zostanie zakończona.  
  
W poniższym przykładzie `WaitAndApologize` metoda asynchroniowa `return` nie zawiera instrukcji, <xref:System.Threading.Tasks.Task> więc metoda zwraca obiekt. Powrót umożliwia `Task` `WaitAndApologize` oczekiwanie. Typ <xref:System.Threading.Tasks.Task> nie zawiera `Result` właściwości, ponieważ nie ma wartości zwracanej.  

:::code language="csharp" source="./snippets/async-returns2.cs" id="SnippetTaskReturn":::

`WaitAndApologize`oczekuje się za pomocą await instrukcji zamiast await wyrażenie, podobne do instrukcji wywołującej dla synchroniczne void-returning metody. Zastosowanie operatora await w tym przypadku nie daje wartości.  
  
Podobnie jak <xref:System.Threading.Tasks.Task%601> w poprzednim przykładzie, `WaitAndApologize` można oddzielić wywołanie od zastosowania operatora await, jak pokazano w poniższym kodzie. Należy jednak pamiętać, że `Task` a `Result` nie ma właściwości i że żadna wartość nie `Task`jest wytwarzana, gdy operator await jest stosowany do .  
  
Poniższy kod oddziela `WaitAndApologize` wywołanie metody od oczekiwania na zadanie, które zwraca metoda.  

:::code language="csharp" source="./snippets/async-returns2a.cs" id="SnippetAwaitTask":::

## <a name="void-return-type"></a>Unieważnij typ zwrotu

Typ zwracany `void` jest używany w programach obsługi zdarzeń `void` asynchronicznych, które wymagają typu zwracanego. Dla metod innych niż programy obsługi zdarzeń, które nie <xref:System.Threading.Tasks.Task> zwracają wartości, należy zwrócić zamiast `void` tego, ponieważ metoda asynchronii, która zwraca nie można oczekiwać. Każdy wywołujący takiej metody musi kontynuować dopełnienia bez oczekiwania na wywołaną metodę asynchronii, aby zakończyć. Wywołujący musi być niezależny od wszelkich wartości lub wyjątków, które generuje metoda asynchroniza.  
  
Wywołujący metody asynchronii zwracającej void nie można złapać wyjątki generowane z metody i takie nieobsługiwanie wyjątki mogą spowodować, że aplikacja zakończy się niepowodzeniem. Jeśli metoda, która <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> zwraca lub zgłasza wyjątek, wyjątek jest przechowywany w zwróconym zadaniu. Wyjątek jest rethrown, gdy zadanie jest oczekiwany. W związku z tym upewnij się, że każda metoda asynchronii, która może powodować wyjątek ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> że wywołania metody są oczekiwane.  
  
Aby uzyskać więcej informacji na temat sposobu wychwytuj wyjątki w metodach asynchronizacyjnych, zobacz [wyjątki w metody asynchronii](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) sekcji [try-catch](../../../language-reference/keywords/try-catch.md) artykułu.  
  
W poniższym przykładzie przedstawiono zachowanie programu obsługi zdarzeń asynchronicznych. W przykładowym kodzie program obsługi zdarzeń asynchroniiowych musi poinformować o zakończeniu wątku głównego. Następnie główny wątek może czekać na program obsługi zdarzeń asynchronii, aby zakończyć przed zamknięciem programu.

:::code language="csharp" source="./snippets/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Uogólnione typy zwracania\<asynchronii i ValueTask TResult\>

Począwszy od języka C# 7.0, metoda asynchroniowa może zwracać dowolny typ, który ma dostępną `GetAwaiter` metodę.

Ponieważ <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> i są typy odwołań, alokacji pamięci w ścieżkach krytycznych dla wydajności, szczególnie gdy alokacje występują w ciasnych pętli, może niekorzystnie wpłynąć na wydajność. Obsługa uogólnionych typów zwracanych oznacza, że można zwrócić lekki typ wartości zamiast typu odwołania, aby uniknąć dodatkowych alokacji pamięci.

.NET zapewnia <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> strukturę jako lekką implementację uogólnionej wartości zwracającej zadania. Aby użyć <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> tego typu, `System.Threading.Tasks.Extensions` należy dodać pakiet NuGet do projektu. W poniższym przykładzie <xref:System.Threading.Tasks.ValueTask%601> użyto struktury do pobrania wartości dwóch kośćch rolkach.
  
:::code language="csharp" source="./snippets/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>Strumienie asynchroniczne z IAsyncEnumerable\<T\>

Począwszy od C# 8.0, metoda asynchroniowa może zwrócić <xref:System.Collections.Generic.IAsyncEnumerable%601> *strumień asynchroniowy,* reprezentowany przez . Strumień asynchronowy umożliwia wyliczenie elementów odczytanych ze strumienia, gdy elementy są generowane we fragmentach z powtarzającymi się wywołaniami asynchronizacyjnymi. W poniższym przykładzie przedstawiono metodę asynchronizową, która generuje strumień asynchronii:

:::code language="csharp" source="./snippets/AsyncStreams.cs" id="SnippetGenerateAsyncStream":::

W poprzednim przykładzie odczytuje wiersze z ciągu asynchronicznie. Po odczytie każdego wiersza kod wylicza każde słowo w ciągu. Wywołujący będzie wyliczyć każdego `await foreach` wyrazu za pomocą instrukcji. Metoda oczekuje, gdy trzeba asynchronicznie odczytać następny wiersz z ciągu źródłowego.

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Przewodnik: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwania (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Przepływ sterowania w programach Asynchronii (C#)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
