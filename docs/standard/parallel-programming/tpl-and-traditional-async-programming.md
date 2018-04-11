---
title: Programowanie asynchroniczne w TPL i standardowym .NET Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2acfb9a564f3a7bc96ed303f49349afe56ca7fe4
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>Programowanie asynchroniczne w TPL i standardowym .NET Framework
.NET Framework zapewnia następujące dwa standardowe wzorce do wykonywania operacji asynchronicznych I/E-granica i obliczeń związanych:  
  
-   Asynchroniczne programowania modelu (APM), w których operacje asynchroniczne są reprezentowane przez pary metod Begin/End takich jak <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
-   Oparty na zdarzeniach wzorca asynchronicznego (EAP), w których operacje asynchroniczne są reprezentowane przez parę metody lub zdarzenia, które są nazywane *OperationName*Async i *OperationName*ukończona, na przykład <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> i <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (EAP została wprowadzona w programie .NET Framework w wersji 2.0).  
  
 Zadania biblioteki równoległych (TPL) służy w różny sposób w połączeniu z jednego z wzorców asynchronicznych. Mogą uwidaczniać operacje zarówno APM, jak i EAP jako zadania dla biblioteki konsumentów lub może narazić wzorce APM, ale wewnętrznie ich wdrażania za pomocą obiektów zadań. W obu przypadkach za pomocą obiektów zadań można uprościć kod i wykorzystać przydatne następujące funkcje:  
  
-   Rejestrowanie wywołań zwrotnych, w formie kontynuacje zadania, w dowolnym momencie po uruchomieniu zadania.  
  
-   Koordynacji wielu operacji, które są wykonywane w odpowiedzi na `Begin_` — metoda, za pomocą <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody, lub <xref:System.Threading.Tasks.Task.WaitAll%2A> — metoda lub <xref:System.Threading.Tasks.Task.WaitAny%2A> metody.  
  
-   Hermetyzuj operacji asynchronicznych I/E-granica i powiązane z obliczeń w tym samym obiekcie zadania.  
  
-   Monitorowanie stanu obiektu zadania.  
  
-   Kierowanie stan operacji do obiektu zadania przy użyciu <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Zawijanie operacji APM w zadanie  
 Zarówno <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> klasy podać kilka przeciążeń <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metod, które pozwalają Hermetyzowanie pary metody APM początek/koniec w jednym <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> wystąpienia. Różne przeciążenia uwzględnić wszystkie pary — metoda początek/koniec, które różnią się od zera do trzech parametrów wejściowych.  
  
 Dla par, które mają `End` metod, które zwracają wartości (`Function` w języku Visual Basic), należy użyć metod w <xref:System.Threading.Tasks.TaskFactory%601> aby tworzenia <xref:System.Threading.Tasks.Task%601>. Dla `End` metody zwracające typ void (`Sub` w języku Visual Basic), należy użyć metod w <xref:System.Threading.Tasks.TaskFactory> aby tworzenia <xref:System.Threading.Tasks.Task>.  
  
 Dla tych kilka przypadków, w którym `Begin` metoda ma więcej niż trzy parametry lub zawiera `ref` lub `out` Parametry dodatkowe `FromAsync` przeciążeń, które hermetyzują tylko `End` metody są udostępniane.  
  
 W poniższym przykładzie przedstawiono podpis dla `FromAsync` przeciążenia, które odpowiada <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> metody. To przeciążenie przyjmuje trzy parametry wejściowe, w następujący sposób.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 Pierwszym parametrem jest <xref:System.Func%606> delegata, który pasuje do podpisu <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metody. Drugi parametr jest <xref:System.Func%602> delegata, który przyjmuje <xref:System.IAsyncResult> i zwraca `TResult`. Ponieważ <xref:System.IO.FileStream.EndRead%2A> zwraca całkowitą, kompilator wnioskuje typ `TResult` jako <xref:System.Int32> i typ tworzonego zadania jako <xref:System.Threading.Tasks.Task>. Ostatnie cztery parametry są takie same jak te w <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metody:  
  
-   Bufor do przechowywania danych plików.  
  
-   Przesunięcie w buforze, od którego ma zostać rozpoczęta zapisywania danych.  
  
-   Maksymalna ilość danych do odczytu z pliku.  
  
-   Obiekt opcjonalne, która przechowuje dane stanu użytkownika do przekazania do wywołania zwrotnego.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Za pomocą ContinueWith dla funkcji wywołania zwrotnego  
 Jeśli potrzebujesz dostępu do danych w pliku, a nie tylko liczba bajtów, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> — metoda nie jest wystarczająca. Zamiast tego należy użyć <xref:System.Threading.Tasks.Task>, których `Result` właściwość zawiera dane plików. Można to zrobić przez dodanie do oryginalnego zadania kontynuacji. Kontynuacji wykonuje pracę, która może być zwykle przeprowadzona przy <xref:System.AsyncCallback> delegowanie. Jest wywoływana po ukończeniu antecedent i wypełniane buforu danych. ( <xref:System.IO.FileStream> Obiekt powinien zostać zamknięty przed zwróceniem.)  
  
 Poniższy przykład przedstawia sposób zwrócenia <xref:System.Threading.Tasks.Task> która hermetyzuje para BeginRead/EndRead można wywołać <xref:System.IO.FileStream> klasy.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Następnie można wywołać metody, w następujący sposób.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Dostarcza dane stanu niestandardowe  
 W przypadku typowych <xref:System.IAsyncResult> operacji, jeśli Twoje <xref:System.AsyncCallback> delegata wymaga niektóre dane o stanie niestandardowych, trzeba przekazać go do ostatniego parametru w `Begin` metodę, tak, aby dane mogą być umieszczone w <xref:System.IAsyncResult> obiektu, który ostatecznie przekazywany do metody wywołania zwrotnego. Nie jest to zwykle wymagane podczas `FromAsync` metody są używane. Jeśli znane jest niestandardowe dane do kontynuacji, jego mogą być przechwytywane bezpośrednio w delegata kontynuacji. Poniższy przykład podobny do poprzedniego przykładu, ale zamiast badanie `Result` właściwość antecedent, kontynuacji sprawdza dane o stanie niestandardowy jest dostępny bezpośrednio do delegata użytkownika o kontynuację.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Synchronizowanie wielu zadań metody FromAsync  
 Statycznych <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody zapewniają elastyczność dodanych, gdy jest używany w połączeniu z `FromAsync` metody. Poniższy przykład pokazuje, jak można inicjować wielu operacji asynchronicznych We/Wy, a następnie zaczekaj na ich zakończenie przed wykonaniem kontynuacji wszystkie.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Metody FromAsync zadania tylko metody End  
 Dla tych kilka przypadków, w którym `Begin` metoda wymaga więcej niż trzy parametry wejściowe lub ma `ref` lub `out` parametry, można użyć `FromAsync` overloads, na przykład <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, reprezentujące tylko `End`metody. Te metody można również w jakimkolwiek scenariuszu, w którym są przekazywane <xref:System.IAsyncResult> i aby hermetyzować go w zadaniu.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Uruchamianie i anulowanie zadań metody FromAsync  
 Zadanie zwrócone przez `FromAsync` metoda ma stan WaitingForActivation i po utworzeniu zadania zostanie uruchomiony przez system, w pewnym momencie. Przy próbie Wywołaj metodę Start takie zadania, zostanie zgłoszony wyjątek.  
  
 Nie można anulować `FromAsync` zadań, ponieważ podstawowych interfejsów API Framework .NET aktualnie nie obsługują w trakcie anulowania pliku lub operacji We/Wy sieci. Funkcje anulowania można dodać do metody, która hermetyzuje `FromAsync` wywołanie, ale tylko mogą odpowiadać na anulowanie przed `FromAsync` o nazwie lub po jej zakończeniu (na przykład w zadania kontynuacji).  
  
 Niektóre klasy, które obsługują protokół EAP, na przykład <xref:System.Net.WebClient>, obsługuje anulowania, a funkcja macierzystego anulowania można zintegrować za pomocą tokenów anulowania.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Udostępnianie EAP złożone operacje jako zadania  
 TPL nie zawiera żadnych metod, które zostały zaprojektowane specjalnie w celu hermetyzacji oparty na zdarzeniach operacji asynchronicznej w tej samej jak robi `FromAsync` rodzina zawijania metody <xref:System.IAsyncResult> wzorca. Zapewnia jednak TPL <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> klasy, która może służyć do reprezentowania dowolny dowolnych zbiór operacje jako <xref:System.Threading.Tasks.Task%601>. Operacje mogą być synchroniczna lub asynchroniczna i może być powiązana We/Wy i/lub powiązane z obliczeń.  
  
 Poniższy przykład przedstawia użycie <xref:System.Threading.Tasks.TaskCompletionSource%601> do udostępnienia zbiór asynchroniczne <xref:System.Net.WebClient> operacji do kodu klienta jako podstawowy <xref:System.Threading.Tasks.Task%601>. Metoda pozwala wprowadzić tablicę adresów URL sieci Web i termin lub nazwę do wyszukania, a następnie zwraca liczbę powtórzeń wyszukiwany termin występuje w każdej lokacji.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Aby uzyskać bardziej szczegółowy przykład, który obejmuje dodatkowe wyjątków i przedstawia sposób wywołania metody z kodu klienta, zobacz [porady: zawijanie wzorów EAP w zadanie](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Należy pamiętać, że wszelkie zadanie, które jest tworzony przez <xref:System.Threading.Tasks.TaskCompletionSource%601> zostanie uruchomione przez tego TaskCompletionSource i, w związku z tym kod użytkownika nie powinien wywoływać metodę rozpoczęcia tego zadania.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementacja wzorca APM przy użyciu zadań  
 W niektórych scenariuszach może być pożądane, aby bezpośrednio <xref:System.IAsyncResult> wzorzec przy użyciu pary metody Begin/End w interfejsie API. Na przykład chcesz zachować spójność z istniejących interfejsów API lub automatycznego narzędzia, które wymagają tego wzorca. W takich przypadkach można użyć zadania uprościć sposobu implementacji wzorca APM w wewnętrznie.  
  
 Poniższy przykład przedstawia sposób wykorzystania zadań do zaimplementowania pary metody APM początek/koniec metody obliczeniowe wiązaniem długotrwałe.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Przy użyciu StreamExtensions przykładowy kod  
 W pliku Streamextensions.cs [przykłady dla programowania równoległego przy użyciu programu .NET Framework 4](https://code.msdn.microsoft.com/ParExtSamples), zawiera kilka implementacje odwołania, które użyć obiektów zadanie asynchroniczne pliku i sieciowych operacji We/Wy.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
