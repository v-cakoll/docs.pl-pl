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
ms.openlocfilehash: 27766c10d0624b5eda8256a3211662036a1b16b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139948"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>Programowanie asynchroniczne w TPL i standardowym .NET Framework
.NET Framework udostępnia dwa następujące wzorce standardowe do wykonywania operacji asynchronicznych związanych z operacjami we/wy i powiązanymi z obliczeniami:  
  
- Asynchroniczny model programowania (APM), w którym operacje asynchroniczne są reprezentowane przez parę metod begin/end, takich jak <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
- Asynchroniczny wzorzec oparty na zdarzeniach (EAP), w którym operacje asynchroniczne są reprezentowane przez parę metod/zdarzeń o nazwie *OperationName*Async i *OperationName*została zakończona, na przykład <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> i <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (Protokół EAP został wprowadzony w .NET Framework w wersji 2,0).  
  
 Biblioteka zadań równoległych (TPL) może być używana na różne sposoby w połączeniu z dowolnym wzorcem asynchronicznym. Można uwidocznić operacje APM i EAP jako zadania dla odbiorców biblioteki lub udostępnić wzorce APM, ale używać obiektów zadań do ich wewnętrznej implementacji. W obu scenariuszach, za pomocą obiektów zadań, można uprościć kod i korzystać z następujących użytecznych funkcji:  
  
- Zarejestruj wywołania zwrotne w formie kontynuacji zadania w dowolnym momencie po rozpoczęciu zadania.  
  
- Koordynuj wiele operacji, które są wykonywane w odpowiedzi na metodę `Begin_`, przy użyciu metod <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> albo metody <xref:System.Threading.Tasks.Task.WaitAll%2A> lub metody <xref:System.Threading.Tasks.Task.WaitAny%2A>.  
  
- Hermetyzowaj asynchroniczne operacje we/wy i powiązane z obliczeniami w tym samym obiekcie zadania.  
  
- Monitorowanie stanu obiektu zadania.  
  
- Kierowanie stanu operacji do obiektu zadania przy użyciu <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Zawijanie operacji APM w zadaniu  
 Klasy <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> zapewniają kilka przeciążeń <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metod, które umożliwiają Hermetyzowanie pary metod begin/end APM w jednym <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> wystąpieniu. Różne przeciążenia uwzględniają każdą parę metod begin/end, które mają od zera do trzech parametrów wejściowych.  
  
 W przypadku par, które mają metody `End` zwracające wartość (`Function` w Visual Basic), należy użyć metod w <xref:System.Threading.Tasks.TaskFactory%601>, które tworzą <xref:System.Threading.Tasks.Task%601>. W przypadku metod `End` zwracających wartość void (`Sub` w Visual Basic) Użyj metod w <xref:System.Threading.Tasks.TaskFactory>, które tworzą <xref:System.Threading.Tasks.Task>.  
  
 Dla tych kilku przypadków, w których Metoda `Begin` ma więcej niż trzy parametry lub zawiera parametry `ref` lub `out`, dostępne są dodatkowe przeciążenia `FromAsync`, które hermetyzują tylko metodę `End`.  
  
 Poniższy przykład przedstawia sygnaturę przeciążenia `FromAsync`, która pasuje do metody <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType>. To Przeciążenie wymaga trzech parametrów wejściowych, jak pokazano poniżej.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 Pierwszy parametr jest delegatem <xref:System.Func%606>, który pasuje do sygnatury metody <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType>. Drugi parametr jest delegatem <xref:System.Func%602>, który pobiera <xref:System.IAsyncResult> i zwraca `TResult`. Ponieważ <xref:System.IO.FileStream.EndRead%2A> zwraca liczbę całkowitą, kompilator wnioskuje typ `TResult` jako <xref:System.Int32> i typ zadania jako <xref:System.Threading.Tasks.Task>. Ostatnie cztery parametry są identyczne z tymi w <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metodzie:  
  
- Bufor, w którym mają być przechowywane dane pliku.  
  
- Przesunięcie w buforze, od którego ma zostać rozpoczęte zapisywanie danych.  
  
- Maksymalna ilość danych do odczytania z pliku.  
  
- Opcjonalny obiekt, który przechowuje dane stanu zdefiniowane przez użytkownika do przekazania do wywołania zwrotnego.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Korzystanie z ContinueWith dla funkcji wywołania zwrotnego  
 Jeśli wymagany jest dostęp do danych w pliku, a nie tylko liczba bajtów, Metoda <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> nie jest wystarczająca. Zamiast tego należy użyć <xref:System.Threading.Tasks.Task>, którego właściwość `Result` zawiera dane pliku. Można to zrobić, dodając kontynuację do oryginalnego zadania. Kontynuacja wykonuje prace, które zwykle są wykonywane przez delegata <xref:System.AsyncCallback>. Jest wywoływana po zakończeniu poprzedzającego, a bufor danych został wypełniony. (Przed zwróceniem obiekt <xref:System.IO.FileStream> powinien zostać zamknięty).  
  
 Poniższy przykład pokazuje, jak zwrócić <xref:System.Threading.Tasks.Task>, który hermetyzuje parę BeginRead/EndRead klasy <xref:System.IO.FileStream>.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Metodę można następnie wywołać w następujący sposób.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Dostarczanie niestandardowych danych o stanie  
 W typowych operacjach <xref:System.IAsyncResult>, jeśli delegat <xref:System.AsyncCallback> wymaga pewnych danych o stanie niestandardowym, należy przekazać go za pomocą ostatniego parametru w metodzie `Begin`, aby dane mogły być spakowane do obiektu <xref:System.IAsyncResult>, który jest ostatecznie przekazywany do wywołania zwrotnego Method. Zwykle nie jest to wymagane, gdy używane są metody `FromAsync`. Jeśli dane niestandardowe są znane jako kontynuacja, można je przechwycić bezpośrednio z delegata kontynuacji. Poniższy przykład przypomina poprzedni przykład, ale zamiast badania właściwości `Result` poprzedzającego, kontynuacja bada dane stanu niestandardowego, które są bezpośrednio dostępne dla delegata kontynuacji użytkownika.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Synchronizowanie wielu zadań wywołaniach metody FromAsync  
 Metody static <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> zapewniają dodatkową elastyczność, gdy są używane w połączeniu z metodami `FromAsync`. Poniższy przykład pokazuje, jak zainicjować wiele asynchronicznych operacji we/wy, a następnie zaczekać, aż wszystkie z nich zostaną wykonane przed wykonaniem kontynuacji.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Wywołaniach metody FromAsync zadania tylko dla metody End  
 Dla tych kilku przypadków, w których Metoda `Begin` wymaga więcej niż trzech parametrów wejściowych lub ma parametry `ref` lub `out`, można użyć przeciążeń `FromAsync`, na przykład <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, który reprezentuje tylko metodę `End`. Te metody mogą być również używane w dowolnym scenariuszu, w którym są przesyłane <xref:System.IAsyncResult> i chcą hermetyzować je w zadaniu.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Uruchamianie i anulowanie zadań wywołaniach metody FromAsync  
 Zadanie zwrócone przez metodę `FromAsync` ma stan WaitingForActivation i zostanie uruchomione przez system w pewnym momencie po utworzeniu zadania. Próba wywołania uruchomienia tego zadania spowoduje wystąpienie wyjątku.  
  
 Nie można anulować zadania `FromAsync`, ponieważ podstawowe interfejsy API .NET Framework obecnie nie obsługują anulowania operacji we/wy pliku lub sieci. Można dodać funkcję anulowania do metody, która hermetyzuje wywołanie `FromAsync`, ale można odpowiedzieć na anulowanie, zanim `FromAsync` zostanie wywołana lub po zakończeniu (na przykład w zadaniu kontynuacji).  
  
 Niektóre klasy, które obsługują protokół EAP, na przykład <xref:System.Net.WebClient>, obsługują anulowanie i można zintegrować te natywne funkcje anulowania za pomocą tokenów anulowania.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Uwidacznianie złożonych operacji EAP jako zadań  
 TPL nie zapewnia żadnych metod, które są specjalnie przeznaczone do hermetyzacji asynchronicznej operacji opartej na zdarzeniach w taki sam sposób `FromAsync`, że rodzina metod otacza wzorzec <xref:System.IAsyncResult>. Jednak TPL udostępnia klasę <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType>, która może być używana do reprezentowania dowolnego dowolnego zestawu operacji jako <xref:System.Threading.Tasks.Task%601>. Operacje mogą być synchroniczne lub asynchroniczne i mogą być powiązane ze współdziałaniem we/wy lub z tymi samymi ograniczeniami.  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Threading.Tasks.TaskCompletionSource%601>, aby uwidocznić zestaw asynchronicznych operacji <xref:System.Net.WebClient> do kodu klienta jako podstawowy <xref:System.Threading.Tasks.Task%601>. Metoda pozwala wprowadzić tablicę adresów URL sieci Web oraz termin lub nazwę do wyszukania, a następnie zwraca liczbę wystąpień wyszukiwanego terminu w poszczególnych lokacjach.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Aby zapoznać się z bardziej kompletnym przykładem, który obejmuje dodatkową obsługę wyjątków i pokazuje, jak wywołać metodę z kodu klienta, zobacz [How to: Otocz wzorce protokołu EAP w zadaniu](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Należy pamiętać, że każde zadanie, które jest tworzone przez <xref:System.Threading.Tasks.TaskCompletionSource%601>, zostanie uruchomione przez ten TaskCompletionSource i dlatego kod użytkownika nie powinien wywoływać metody Start dla tego zadania.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementowanie wzorca APM za pomocą zadań  
 W niektórych scenariuszach może być pożądane bezpośrednie uwidocznienie wzorca <xref:System.IAsyncResult> przy użyciu par metod begin/end w interfejsie API. Na przykład możesz chcieć zachować spójność z istniejącymi interfejsami API lub można mieć zautomatyzowane narzędzia, które wymagają tego wzorca. W takich przypadkach można użyć zadań, aby uprościć sposób, w jaki wzorzec APM jest implementowany wewnętrznie.  
  
 W poniższym przykładzie pokazano, jak za pomocą zadań zaimplementować parę metod begin/end APM dla długotrwałej metody powiązanej z obliczaniem.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Korzystanie z przykładowego kodu StreamExtensions  
 Plik Streamextensions.cs, w przykładach [programowania równoległego z .NET Framework 4](https://code.msdn.microsoft.com/ParExtSamples), zawiera kilka implementacji referencyjnych, które używają obiektów zadań do asynchronicznej operacji we/wy na plikach i sieci.  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
