---
title: "Anulowanie w zarządzanych wątkach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation in .NET, overview
ms.assetid: eea11fe5-d8b0-4314-bb5d-8a58166fb1c3
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5407beba999ede6131adbc17f56d139396429597
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="cancellation-in-managed-threads"></a>Anulowanie w zarządzanych wątkach
Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework używa ujednoliconego modelu wspólnych anulowania asynchroniczne lub długotrwałej operacji synchronicznych. Ten model jest oparty na obiekt lekkie o nazwie token anulowania. Obiekt, który wywołuje jeden lub więcej operacji można anulować, na przykład, tworząc nowe wątki i zadań, przekazuje token do każdej operacji. Poszczególnych działań z kolei może przekazać kopie tokenu do innych operacji. W późniejszym czasie obiekt, który utworzył token służy do żądania, że operacje zatrzymana, co robią. Tylko obiektu żądającego mogą wystawiać żądanie anulowania, a każdy odbiornik jest odpowiedzialny za żądanie po raz pierwszy, a odpowiadającym odpowiednią i odpowiednim w sposób.  
  
 Ogólne wzorzec stosowania modelu wspólnych anulowania jest:  
  
-   Utwórz wystąpienie <xref:System.Threading.CancellationTokenSource> obiektu, który zarządza i wysyła powiadomienie do anulowania do poszczególnych anulowanie tokenów.  
  
-   Przekaż token zwracany przez <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> właściwości do każdego zadania lub wątku, który nasłuchuje anulowania.  
  
-   Mechanizm dla każdego wątku odpowiedzieć na anulowanie.  
  
-   Wywołanie <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę w celu zapewnienia powiadomienia o anulowaniu.  
  
> [!IMPORTANT]
>  <xref:System.Threading.CancellationTokenSource> Klasa implementuje <xref:System.IDisposable> interfejsu. Należy się upewnić wywołać <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> metody po zakończeniu przy użyciu źródła token anulowania można zwolnić wszelkie niezarządzane zasoby, które przechowuje.  
  
 Na poniższej ilustracji przedstawiono relację między źródłem tokenu i wszystkie kopie jego tokenu.  
  
 ![CancellationTokenSource i anulowanie tokenów](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Nowy model anulowania ułatwia tworzenie aplikacji obsługujących anulowania i bibliotek i obsługuje następujące funkcje:  
  
-   Anulowanie jest współpracy i nie jest wymuszana odbiornika. Odbiornik Określa, jak bezpiecznie przerwanie w odpowiedzi na żądanie anulowania.  
  
-   Żąda różni się od nasłuchiwania. Obiekt, który wywołuje operację można anulować można kontrolować, gdy (Jeśli kiedykolwiek) anulowania żądania.  
  
-   Przy użyciu wywołania metody tylko jednego obiektu żądającego wystawia żądanie anulowania wszystkie kopie tokenu.  
  
-   Odbiornik można słuchać wiele tokenów jednocześnie łącząc je do jednej *token połączony*.  
  
-   Kod użytkownika można zauważyć i odpowiadać na żądania anulowania kod biblioteki, a kod biblioteki można zauważyć i odpowiadać na żądania anulowania z kodu użytkownika.  
  
-   Odbiorniki może otrzymać powiadomienie żądań anulowania sondowania, wywołania zwrotnego rejestracji lub Oczekiwanie na uchwyty oczekiwania.  
  
## <a name="cancellation-types"></a>Typy anulowania  
 Framework anulowania jest wdrażany jako zestaw powiązanych typów, które są wymienione w poniższej tabeli.  
  
|Nazwa typu|Opis|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Obiekt, który tworzy token anulowania, a także generuje żądanie anulowania wszystkie kopie tego tokenu.|  
|<xref:System.Threading.CancellationToken>|Typ wartości lekkie przekazany do co najmniej jednego odbiornika, zazwyczaj jako parametr metody. Odbiorniki monitorować wartości `IsCancellationRequested` właściwości tokenu sondowania, wywołania zwrotnego lub dojście oczekiwania.|  
|<xref:System.OperationCanceledException>|Zaakceptuj przeciążeń konstruktora tego wyjątku <xref:System.Threading.CancellationToken> jako parametr. Obiekty nasłuchujące Opcjonalnie można zgłosić tego wyjątku, aby zweryfikować źródło anulowanie i powiadomić inne osoby, które zostały wysłane odpowiedzi na żądanie anulowania.|  
  
 Nowy model anulowania jest zintegrowany z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w kilku typów. Najważniejsze alerty są <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> i <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>. Firma Microsoft zaleca używanie tego nowego modelu anulowania dla wszystkich nowy kod biblioteki i aplikacji.  
  
## <a name="code-example"></a>Przykład kodu  
 W poniższym przykładzie tworzy obiektu żądającego <xref:System.Threading.CancellationTokenSource> obiektu, a następnie przekazuje jego <xref:System.Threading.CancellationTokenSource.Token%2A> właściwości można anulować operację. Operacja, która odbiera żądanie monitoruje wartość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości tokenu za pomocą sondowania. Jeśli wartość staje się `true`, odbiornik może obsłużyć w jakikolwiek sposób jest odpowiedni. W tym przykładzie metoda po prostu kończy działanie, czyli wszystko, który jest wymagany w wielu przypadkach.  
  
> [!NOTE]
>  W przykładzie użyto <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metodę, aby wykazać, że nowa struktura anulowania jest zgodny z interfejsów API starszej wersji. Na przykład, który korzysta z nowych, preferowane <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu, zobacz [porady: anulowanie zadania i jego elementy podrzędne](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Anulowanie operacji lub anulowania obiektu  
 W ramach nowych anulowania anulowania odwołuje się do operacji, a nie obiektów. Żądanie anulowania oznacza, że operacja ma zostać zatrzymana, jak najszybciej po wykonaniu wymagane oczyszczania. Jeden token anulowania powinny odwoływać się do jednego "można anulować operacji" jednak tej operacji może być wdrażana w programie. Po <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> ustawioną właściwość tokenu `true`, nie można przywrócić `false`. W związku z tym anulowanie tokenów nie można użyć ponownie po zostały anulowane.  
  
 Jeśli potrzebujesz mechanizm anulowania obiektu, można utworzyć ją na mechanizm anulowania operacji przez wywołanie metody <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> metody, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Jeśli obiekt obsługuje więcej niż jednej równoczesnych operacji można anulować, przekazać oddzielne token jako dane wejściowe do każdej operacji można anulować distinct. W ten sposób można anulować jedną operację bez wpływu na inne.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Nasłuchiwania i odpowiada na żądania anulowania  
 Delegowanie użytkownika Realizator można anulować operacji określa jak zakończyć operację w odpowiedzi na żądanie anulowania. W wielu przypadkach delegowanie użytkownika można po prostu wykonać wszystkie wymagane oczyszczania i wróć natychmiast.  
  
 Jednak w przypadku bardziej złożonych, może być konieczne dla pełnomocnika użytkownika, aby powiadomić kod biblioteki, która nastąpiła anulowania. W takich przypadkach prawidłowy sposób, aby zakończyć operację jest dla pełnomocnika, aby wywołać <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, metody, która spowoduje, że <xref:System.OperationCanceledException> zostanie wygenerowany. Kod biblioteki można przechwycić tego wyjątku w wątku delegata użytkownika i sprawdź token wyjątek, aby ustalić, czy wyjątek wskazuje wspólne anulowanie lub wyjątkowej sytuacji.  
  
 <xref:System.Threading.Tasks.Task> Klasy uchwytów <xref:System.OperationCanceledException> w ten sposób. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Nasłuchiwanie za pomocą sondowania  
 Do obliczenia długotrwałe tej pętli lub recurse, można wykrywać żądanie anulowania okresowo Sondując wartość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> właściwości. Jeśli jego wartość wynosi `true`, metoda powinna wyczyścić i zakończyć tak szybko jak to możliwe. Optymalną częstotliwość sondowania zależy od typu aplikacji. Jest developer, aby określić najlepszy sondowania częstotliwość dla dowolnego danego programu. Sondowanie sam nie znacznie wpływu na wydajność. Poniższy przykład przedstawia sposób możliwe do sondowania.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Aby uzyskać bardziej szczegółowy przykład, zobacz [porady: nasłuchiwanie żądań anulowania za pomocą sondowania](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Nasłuchiwanie rejestrując wywołania zwrotnego  
 Niektóre operacje, mogą stać się zablokowane w taki sposób, że ich nie można sprawdzić wartość token anulowania w odpowiednim czasie. W tych przypadkach należy zarejestrować metody wywołania zwrotnego, która odblokowuje metody, gdy zostanie odebrane żądanie anulowania.  
  
 <xref:System.Threading.CancellationToken.Register%2A> Metoda zwraca <xref:System.Threading.CancellationTokenRegistration> obiekt, który jest używany w tym celu. Poniższy przykład przedstawia użycie <xref:System.Threading.CancellationToken.Register%2A> metodę, aby anulować asynchroniczne żądanie sieci Web.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 <xref:System.Threading.CancellationTokenRegistration> Obiektu zarządza synchronizacja wątku i zapewnia, że wywołanie zwrotne zakończy wykonywanie w określonym punkcie w czasie.  
  
 Aby zapewnić czas reakcji systemu i uniknąć zakleszczenia, poniższe wskazówki musi występować podczas rejestrowania wywołań zwrotnych:  
  
-   Powinna być szybkie metody wywołania zwrotnego, ponieważ jest ona wywoływana synchronicznie i w związku z tym wywołaniu <xref:System.Threading.CancellationTokenSource.Cancel%2A> wraca do momentu zwraca wywołania zwrotnego.  
  
-   Jeśli należy wywołać <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> podczas wywołania zwrotnego jest uruchomiona, przytrzymaj blokadę wywołania zwrotnego oczekuje na programie można zakleszczenie. Po `Dispose` zwraca można zwolnić wszystkie zasoby wymagane przez wywołanie zwrotne.  
  
-   Wywołania zwrotne nie należy wykonać wszelkie ręczne wątku lub <xref:System.Threading.SynchronizationContext> użycia w wywołaniu zwrotnym. Jeśli wywołanie zwrotne muszą być wykonywane w szczególności wątku, użyj <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> Konstruktor, który pozwala określić, że syncContext docelowy jest aktywne <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>. Wykonywanie wątków ręcznego w wywołaniu zwrotnym może spowodować zakleszczenia.  
  
 Aby uzyskać bardziej szczegółowy przykład, zobacz [porady: rejestrowanie wywołań zwrotnych żądań anulowania](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Nasłuchiwanie przy użyciu dojścia oczekiwania  
 Gdy zablokować można anulować operacji podczas oczekiwania na pierwotny, takich jak synchronizacja <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> lub <xref:System.Threading.Semaphore?displayProperty=nameWithType>, można użyć <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> właściwości, aby umożliwić wykonanie operacji oczekiwania na zdarzenia i żądania anulowania. Dojście oczekiwania token anulowania będzie stają się sygnalizowane w odpowiedzi na żądanie anulowania, a metoda może używać wartości zwrotnej <xref:System.Threading.WaitHandle.WaitAny%2A> token metody, aby ustalić, czy został on anulowania, która sygnalizuje. Operację można, a następnie wystarczy zamknąć lub throw <xref:System.OperationCanceledException>odpowiednio.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 W nowy kod, którego celem jest [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> i <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> zarówno obsługi nowej struktury anulowania w ich `Wait` metody. Można przekazać <xref:System.Threading.CancellationToken> do metody, i gdy zażądano anulowania zdarzenia budzi i zgłasza <xref:System.OperationCanceledException>.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Na przykład bardziej szczegółowy, zobacz [porady: nasłuchiwanie anulowania żądania ma czekać obsługi przez](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Nasłuchiwanie jednocześnie wiele tokenów  
 W niektórych przypadkach odbiornik może mieć jednocześnie nasłuchiwanie na wiele tokenów anulowania. Na przykład można anulować operację może być konieczne monitorować token anulowania wewnętrzny oprócz typ tokenu przekazanego w zewnętrznie jako argument do parametru metody. W tym celu należy utworzyć połączonego źródła tokenu, które może dołączyć do dwóch lub więcej tokenów do jednego tokenu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Należy zauważyć, że należy wywołać `Dispose` połączonego tokenu źródłowego po zakończeniu z nim. Aby uzyskać bardziej szczegółowy przykład, zobacz [porady: nasłuchiwanie wielu żądań anulowania](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Współpraca między kodem biblioteki i kodem użytkownika  
 Framework ujednoliconego anulowania umożliwia kod biblioteki anulować kod użytkownika i kodu użytkownika anulować kod biblioteki w sposób współpracy. Smooth współpracy zależy od każdej strony poniższych wskazówek:  
  
-   Jeśli kod biblioteki udostępnia operacje można anulować, on również zawierał metody publiczne akceptujących token anulowania zewnętrznego, dzięki czemu kod użytkownika można żądanie anulowania.  
  
-   Jeśli kod biblioteki odwołuje się do kodu użytkownika, kod biblioteki należy interpretować OperationCanceledException(externalToken) jako *wspólne anulowanie*i niekoniecznie wyjątek błędu.  
  
-   Obiekty delegowane użytkownik powinien próbować odpowiadać na żądania anulowania kod biblioteki w odpowiednim czasie.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>i <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> przedstawiono klasy, które wykonuje te wytyczne. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md)i [porady: Anulowanie zapytania PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)
