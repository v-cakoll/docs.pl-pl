---
title: Programowanie asynchroniczne w TPL i standardowym .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
ms.openlocfilehash: e71c609b500bc6771c405cfb6f4ac14923cc3939
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507549"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>Programowanie asynchroniczne w TPL i standardowym .NET Framework
.NET Framework udostępnia dwa następujące wzorce standardowe do wykonywania operacji asynchronicznych związanych z operacjami we/wy i powiązanymi z obliczeniami:  
  
- Asynchroniczny model programowania (APM), w którym operacje asynchroniczne są reprezentowane przez parę metod begin/end, takich jak <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
- Asynchroniczny wzorzec oparty na zdarzeniach (EAP), w którym operacje asynchroniczne są reprezentowane przez parę metod/zdarzeń o nazwie *OperationName*Async i *OperationName*została zakończona, na przykład <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> i <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (Protokół EAP został wprowadzony w .NET Framework w wersji 2,0).  
  
 Biblioteka zadań równoległych (TPL) może być używana na różne sposoby w połączeniu z dowolnym wzorcem asynchronicznym. Można uwidocznić operacje APM i EAP jako zadania dla odbiorców biblioteki lub udostępnić wzorce APM, ale używać obiektów zadań do ich wewnętrznej implementacji. W obu scenariuszach, za pomocą obiektów zadań, można uprościć kod i korzystać z następujących użytecznych funkcji:  
  
- Zarejestruj wywołania zwrotne w formie kontynuacji zadania w dowolnym momencie po rozpoczęciu zadania.  
  
- Koordynuj wiele operacji, które są wykonywane w odpowiedzi `Begin_` na metodę, przy użyciu <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> metod <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> i lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metody lub <xref:System.Threading.Tasks.Task.WaitAny%2A> metody.  
  
- Hermetyzowaj asynchroniczne operacje we/wy i powiązane z obliczeniami w tym samym obiekcie zadania.  
  
- Monitorowanie stanu obiektu zadania.  
  
- Kierowanie stanu operacji do obiektu zadania przy użyciu <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Zawijanie operacji APM w zadaniu  
 <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> Klasy i <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> zapewniają kilka przeciążeń metod <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> , które umożliwiają Hermetyzowanie pary metod begin/end APM w jednym <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> wystąpieniu. Różne przeciążenia uwzględniają każdą parę metod begin/end, które mają od zera do trzech parametrów wejściowych.  
  
 Dla par, które `End` mają metody zwracające wartość (`Function` w Visual Basic), należy użyć metod w <xref:System.Threading.Tasks.TaskFactory%601> programie, które <xref:System.Threading.Tasks.Task%601>tworzą. Dla `End` metod, które zwracają wartość`Sub` <xref:System.Threading.Tasks.Task>void (w Visual Basic), należy użyć <xref:System.Threading.Tasks.TaskFactory> metod w programie, które tworzą.  
  
 Dla tych kilku przypadków, w których `Begin` Metoda ma więcej niż trzy parametry lub zawiera `ref` lub `out` parametry, dostępne `FromAsync` są dodatkowe przeciążenia, które hermetyzują tylko `End` metodę.  
  
 Poniższy przykład przedstawia sygnaturę `FromAsync` przeciążenia odpowiadającą metodom <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i. <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> To Przeciążenie wymaga trzech parametrów wejściowych, jak pokazano poniżej.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 Pierwszy parametr jest <xref:System.Func%606> delegatem, który jest zgodny z podpisem <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metody. Drugi parametr jest <xref:System.Func%602> delegatem, który pobiera <xref:System.IAsyncResult> i zwraca. `TResult` Ponieważ <xref:System.IO.FileStream.EndRead%2A> zwraca liczbę całkowitą, kompilator wnioskuje typ `TResult` jako <xref:System.Int32> i typ zadania jako. <xref:System.Threading.Tasks.Task> Ostatnie cztery parametry są identyczne z tymi w <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metodzie:  
  
- Bufor, w którym mają być przechowywane dane pliku.  
  
- Przesunięcie w buforze, od którego ma zostać rozpoczęte zapisywanie danych.  
  
- Maksymalna ilość danych do odczytania z pliku.  
  
- Opcjonalny obiekt, który przechowuje dane stanu zdefiniowane przez użytkownika do przekazania do wywołania zwrotnego.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Korzystanie z ContinueWith dla funkcji wywołania zwrotnego  
 Jeśli potrzebujesz dostępu do danych w pliku, w przeciwieństwie do tylko liczby bajtów, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> Metoda jest niewystarczająca. Zamiast tego należy <xref:System.Threading.Tasks.Task>użyć, `Result` którego właściwość zawiera dane pliku. Można to zrobić, dodając kontynuację do oryginalnego zadania. Kontynuacja wykonuje prace, które zwykle są wykonywane przez <xref:System.AsyncCallback> delegata. Jest wywoływana po zakończeniu poprzedzającego, a bufor danych został wypełniony. (Przed <xref:System.IO.FileStream> zwróceniem obiekt powinien zostać zamknięty).  
  
 Poniższy przykład pokazuje, jak zwrócić obiekt <xref:System.Threading.Tasks.Task> , który hermetyzuje parę BeginRead/EndRead <xref:System.IO.FileStream> klasy.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Metodę można następnie wywołać w następujący sposób.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Dostarczanie niestandardowych danych o stanie  
 W przypadku <xref:System.IAsyncResult> typowych operacji, jeśli <xref:System.AsyncCallback> delegat wymaga pewnych danych o stanie niestandardowym, należy przekazać go za pomocą ostatniego parametru w `Begin` metodzie, tak aby dane mogły być spakowane do <xref:System.IAsyncResult> obiektu, który jest ostatecznie przekazywany do metody wywołania zwrotnego. Zwykle nie jest to wymagane w `FromAsync` przypadku użycia metod. Jeśli dane niestandardowe są znane jako kontynuacja, można je przechwycić bezpośrednio z delegata kontynuacji. Poniższy przykład przypomina poprzedni przykład, ale zamiast badania `Result` właściwości poprzedzającego, kontynuacja bada dane stanu niestandardowego, które są bezpośrednio dostępne dla delegata kontynuacji użytkownika.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Synchronizowanie wielu zadań wywołaniach metody FromAsync  
 Metody statyczne <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> zapewniają dodatkową elastyczność, gdy są `FromAsync` używane w połączeniu z metodami. Poniższy przykład pokazuje, jak zainicjować wiele asynchronicznych operacji we/wy, a następnie zaczekać, aż wszystkie z nich zostaną wykonane przed wykonaniem kontynuacji.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Wywołaniach metody FromAsync zadania tylko dla metody End  
 Dla tych kilku przypadków, w których `Begin` metoda wymaga więcej niż trzech parametrów wejściowych lub ma `ref` lub `out` parametry, można użyć `FromAsync` przeciążeń, na przykład <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, który reprezentuje tylko `End` metodę. Te metody mogą być również używane w dowolnym scenariuszu, w którym są przesyłane <xref:System.IAsyncResult> i chcą hermetyzować je w zadaniu.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Uruchamianie i anulowanie zadań wywołaniach metody FromAsync  
 Zadanie zwrócone przez `FromAsync` metodę ma stan WaitingForActivation i zostanie uruchomione przez system w pewnym momencie po utworzeniu zadania. Próba wywołania uruchomienia tego zadania spowoduje wystąpienie wyjątku.  
  
 Nie można anulować `FromAsync` zadania, ponieważ bazowe interfejsy API .NET Framework obecnie nie obsługują anulowania operacji we/wy pliku lub sieci. Można dodać funkcję anulowania do metody, która hermetyzuje `FromAsync` wywołanie, ale można odpowiedzieć na anulowanie dopiero przed `FromAsync` wywołaniem lub po jego zakończeniu (na przykład w zadaniu kontynuacji).  
  
 Niektóre klasy, które obsługują protokół EAP, na <xref:System.Net.WebClient>przykład, obsługują anulowanie i można zintegrować te natywne funkcje anulowania za pomocą tokenów anulowania.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Uwidacznianie złożonych operacji EAP jako zadań  
 TPL nie zapewnia żadnych metod przeznaczonych specjalnie do hermetyzacji asynchronicznej operacji opartej na zdarzeniach w taki sam sposób, w jaki `FromAsync` rodzina metod otacza <xref:System.IAsyncResult> wzorzec. Jednakże TPL udostępnia <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> klasę, która może służyć do reprezentowania dowolnego dowolnego zestawu operacji jako <xref:System.Threading.Tasks.Task%601>. Operacje mogą być synchroniczne lub asynchroniczne i mogą być powiązane ze współdziałaniem we/wy lub z tymi samymi ograniczeniami.  
  
 Poniższy przykład pokazuje, jak użyć, <xref:System.Threading.Tasks.TaskCompletionSource%601> Aby uwidocznić zestaw operacji asynchronicznych <xref:System.Net.WebClient> w kodzie klienta jako podstawowa. <xref:System.Threading.Tasks.Task%601> Metoda pozwala wprowadzić tablicę adresów URL sieci Web oraz termin lub nazwę do wyszukania, a następnie zwraca liczbę wystąpień wyszukiwanego terminu w poszczególnych lokacjach.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Aby zapoznać się z bardziej kompletnym przykładem, który obejmuje dodatkową obsługę wyjątków i pokazuje, jak wywołać metodę z kodu klienta, zobacz [How to: Otocz wzorce protokołu EAP w zadaniu](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Należy pamiętać, że każde zadanie, które jest <xref:System.Threading.Tasks.TaskCompletionSource%601> tworzone przez program, zostanie uruchomione przez ten TaskCompletionSource, dlatego kod użytkownika nie powinien wywoływać metody Start dla tego zadania.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementowanie wzorca APM za pomocą zadań  
 W niektórych scenariuszach może być pożądane bezpośrednie uwidocznienie <xref:System.IAsyncResult> wzorca przy użyciu par metod begin/end w interfejsie API. Na przykład możesz chcieć zachować spójność z istniejącymi interfejsami API lub można mieć zautomatyzowane narzędzia, które wymagają tego wzorca. W takich przypadkach można użyć zadań, aby uprościć sposób, w jaki wzorzec APM jest implementowany wewnętrznie.  
  
 W poniższym przykładzie pokazano, jak za pomocą zadań zaimplementować parę metod begin/end APM dla długotrwałej metody powiązanej z obliczaniem.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Korzystanie z przykładowego kodu StreamExtensions  
 Plik *StreamExtensions.cs* , .NET standard w repozytorium [dodatków Parallel Extensions](/samples/dotnet/samples/parallel-programming-extensions-extras-cs/) , zawiera kilka implementacji referencyjnych, które `Task` używają obiektów do asynchronicznego we/wy plików i sieci.
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
