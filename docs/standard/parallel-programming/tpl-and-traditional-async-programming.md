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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139948"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>Programowanie asynchroniczne w TPL i standardowym .NET Framework
Program .NET Framework udostępnia następujące dwa wzorce standardowe do wykonywania operacji asynchronicznych związanych z we/wy i obliczeniowych:  
  
- Asynchroniczny model programowania (APM), w którym operacje asynchroniczne są reprezentowane przez <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> parę <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>metod Begin/End, takich jak i .  
  
- Oparty na zdarzeniach wzorzec asynchroniczny (EAP), w którym operacje asynchroniczne są reprezentowane przez parę metody/zdarzeń o nazwie *OperationName*Async i *OperationName*Completed, na przykład i <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (EAP został wprowadzony w wersji .NET Framework 2.0.)  
  
 Biblioteka równoległa zadania (TPL) może być używana na różne sposoby w połączeniu z jednym z wzorców asynchronicznych. Można udostępnić operacje APM i EAP jako zadania dla konsumentów biblioteki lub można udostępnić wzorce APM, ale używać Task obiektów do zaimplementowania ich wewnętrznie. W obu scenariuszach za pomocą Task obiektów, można uprościć kod i skorzystać z następujących przydatnych funkcji:  
  
- Zarejestruj wywołania wywołania wywołania, w postaci kontynuacji zadań, w dowolnym momencie po uruchomieniu zadania.  
  
- Koordynuj wiele operacji wykonywanych `Begin_` w odpowiedzi na <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metodę, przy <xref:System.Threading.Tasks.Task.WaitAll%2A> użyciu metod <xref:System.Threading.Tasks.Task.WaitAny%2A> i lub metody lub metody.  
  
- Hermetyzować operacje asynchroniczne we/wy związane z obliczeniami i obliczeniowe w tym samym obiekcie zadania.  
  
- Monitorowanie stanu obiektu Task.  
  
- Kierowanie stanu operacji do Task obiektu <xref:System.Threading.Tasks.TaskCompletionSource%601>przy użyciu .  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Zawijanie operacji APM w zadaniu  
 Zarówno <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> klas zapewniają kilka <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> przeciążeń i <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody, które umożliwiają hermetyzacje <xref:System.Threading.Tasks.Task> APM Begin/End pary metody w jednym lub <xref:System.Threading.Tasks.Task%601> wystąpieniu. Różne przeciążenia pomieścić wszystkie Begin/End pary metody, które mają od zera do trzech parametrów wejściowych.  
  
 W przypadku par, które `End` mają metody`Function` zwracające wartość (w <xref:System.Threading.Tasks.TaskFactory%601> języku <xref:System.Threading.Tasks.Task%601>Visual Basic), należy użyć metod w tym create a . W `End` przypadku metod,`Sub` które zwracają void (w <xref:System.Threading.Tasks.TaskFactory> języku <xref:System.Threading.Tasks.Task>Visual Basic), należy użyć metod, które tworzą .  
  
 W przypadku tych kilku `Begin` przypadków, w których metoda `ref` `out` ma więcej `FromAsync` niż trzy parametry lub zawiera `End` lub parametry, dodatkowe przeciążenia, które hermetyzują tylko metodę są dostarczane.  
  
 W poniższym przykładzie przedstawiono `FromAsync` podpis przeciążenia, który pasuje do <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> metody. To przeciążenie ma trzy parametry wejściowe, w następujący sposób.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 Pierwszy parametr jest <xref:System.Func%606> pełnomocnikiem, który pasuje <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> do podpisu metody. Drugi parametr jest <xref:System.Func%602> pełnomocnikiem, <xref:System.IAsyncResult> który przyjmuje `TResult`i zwraca . Ponieważ <xref:System.IO.FileStream.EndRead%2A> zwraca liczbę całkowitą, kompilator wnioskuje typ `TResult` jako <xref:System.Int32> i <xref:System.Threading.Tasks.Task>typ zadania jako . Ostatnie cztery parametry są identyczne <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> z parametrami w metodzie:  
  
- Bufor, w którym mają być przechowywane dane pliku.  
  
- Przesunięcie w buforze, w którym ma rozpocząć zapisywanie danych.  
  
- Maksymalna ilość danych do odczytu z pliku.  
  
- Opcjonalny obiekt, który przechowuje dane o stanie zdefiniowanym przez użytkownika, aby przekazać do wywołania oddzwonić.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Korzystanie z funkcji continuewith dla funkcji wywołania zwrotu  
 Jeśli potrzebujesz dostępu do danych w pliku, w przeciwieństwie do liczby bajtów, metoda nie jest wystarczająca. <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> Zamiast tego <xref:System.Threading.Tasks.Task>użyj `Result` , którego właściwość zawiera dane pliku. Można to zrobić, dodając kontynuację do oryginalnego zadania. Kontynuacja wykonuje pracę, która zazwyczaj będzie wykonywana przez delegata. <xref:System.AsyncCallback> Jest wywoływana po zakończeniu antecedent i bufor danych został wypełniony. (Obiekt <xref:System.IO.FileStream> powinien zostać zamknięty przed zwróceniem).  
  
 W poniższym przykładzie pokazano, jak zwrócić a, <xref:System.Threading.Tasks.Task> który hermetyzuje BeginRead/EndRead parę <xref:System.IO.FileStream> klasy.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Metoda może być wywoływana w następujący sposób.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Dostarczanie danych o stanie niestandardowym  
 W <xref:System.IAsyncResult> typowych operacjach, jeśli <xref:System.AsyncCallback> pełnomocnik wymaga pewnych danych stanu niestandardowego, musisz `Begin` przekazać go za pośrednictwem ostatniego <xref:System.IAsyncResult> parametru w metodzie, aby dane mogły zostać spakowane do obiektu, który zostanie ostatecznie przekazany do metody wywołania wywołania. Zazwyczaj nie jest to wymagane, `FromAsync` gdy metody są używane. Jeśli dane niestandardowe są znane kontynuacji, a następnie mogą być przechwytywane bezpośrednio w delegata kontynuacji. Poniższy przykład przypomina poprzedni przykład, ale zamiast `Result` badać właściwość poprzednika, kontynuacja sprawdza dane stanu niestandardowego, który jest bezpośrednio dostępny dla delegata użytkownika kontynuacji.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Synchronizowanie wielu zadań FromAsync  
 Statyczne <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody zapewniają dodatkową elastyczność w `FromAsync` połączeniu z metodami. W poniższym przykładzie pokazano, jak zainicjować wiele operacji we/wy asynchronicznej, a następnie poczekać na ich zakończenie przed wykonaniem kontynuacji.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>FromAsync zadania tylko dla metody końcowej  
 W przypadku tych kilku `Begin` przypadków, w których metoda wymaga `ref` `out` więcej niż trzech parametrów `FromAsync` wejściowych lub <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>ma lub parametrów, można użyć przeciążeń, na przykład, które reprezentują tylko `End` metodę. Te metody mogą być również używane w dowolnym <xref:System.IAsyncResult> scenariuszu, w którym są przekazywane i chcesz hermetyzować go w zadaniu.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Uruchamianie i anulowanie zadań FromAsync  
 Zadanie zwracane przez `FromAsync` metodę ma stan WaitingForActivation i zostanie uruchomione przez system w pewnym momencie po utworzeniu zadania. Jeśli spróbujesz wywołać Start na takie zadanie, zostanie zgłoszony wyjątek.  
  
 Nie można `FromAsync` anulować zadania, ponieważ podstawowe interfejsy API platformy .NET Framework nie obsługują obecnie w toku anulowania we/wy plików lub sieci. Można dodać funkcje anulowania do metody, która hermetyzuje `FromAsync` wywołanie, ale `FromAsync` można odpowiedzieć na anulowanie tylko przed wywołaniem lub po zakończeniu (na przykład w zadaniu kontynuacji).  
  
 Niektóre klasy, które obsługują EAP, na przykład, <xref:System.Net.WebClient>obsługują anulowanie i można zintegrować tę funkcję anulowania natywnego przy użyciu tokenów anulowania.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Wystawianie złożonych operacji EAP jako zadań  
 TPL nie udostępnia żadnych metod, które są specjalnie zaprojektowane do hermetyzacji operacji asynchronicznej opartej `FromAsync` na zdarzeniach w <xref:System.IAsyncResult> taki sam sposób, jak rodzina metod zawijać wzorzec. Jednak TPL zapewnia <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> klasę, która może służyć do reprezentowania dowolnego <xref:System.Threading.Tasks.Task%601>zestawu operacji jako . Operacje mogą być synchroniczne lub asynchroniczne i mogą być powiązane we/wy lub związane z obliczeniami lub oba te elementy.  
  
 W poniższym przykładzie pokazano, jak użyć <xref:System.Threading.Tasks.TaskCompletionSource%601> zestawu <xref:System.Net.WebClient> operacji asynchronicznych <xref:System.Threading.Tasks.Task%601>do kodu klienta jako podstawowego . Metoda umożliwia wprowadzenie tablicy adresów URL sieci Web oraz terminu lub nazwy do wyszukania, a następnie zwraca liczbę wystąpień wyszukiwanego hasła w każdej witrynie.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Aby uzyskać pełniejszy przykład, który zawiera dodatkową obsługę wyjątków i pokazuje, jak wywołać metodę z kodu klienta, zobacz [Jak: Zawijanie wzorców Protokołu EAP w zadaniu](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Należy pamiętać, że każde zadanie, które jest tworzone przez a <xref:System.Threading.Tasks.TaskCompletionSource%601> zostanie uruchomiony przez taskcompletionsource i w związku z tym kod użytkownika nie należy wywoływać Start metody na to zadanie.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementowanie wzorca APM przy użyciu zadań  
 W niektórych scenariuszach może być pożądane, <xref:System.IAsyncResult> aby bezpośrednio udostępnić wzorzec przy użyciu begin/end pary metod w interfejsie API. Na przykład można zachować spójność z istniejącymi interfejsami API lub mogą istnieć zautomatyzowane narzędzia, które wymagają tego wzorca. W takich przypadkach można użyć zadania, aby uprościć sposób wzorzec APM jest implementowany wewnętrznie.  
  
 W poniższym przykładzie pokazano, jak używać zadań do implementowania pary metod Begin/End apm dla długo działającej metody obliczeniowej.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Korzystanie z przykładowego kodu StreamExtensions  
 Plik Streamextensions.cs w [przykładach do programowania równoległego z .NET Framework 4](https://code.msdn.microsoft.com/ParExtSamples)zawiera kilka implementacji referencyjnych, które używają obiektów task dla asynchronicznego we/wy plików i sieci.  
  
## <a name="see-also"></a>Zobacz też

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
