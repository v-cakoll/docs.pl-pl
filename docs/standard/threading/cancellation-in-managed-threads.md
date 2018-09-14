---
title: Anulowanie w zarządzanych wątkach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation in .NET, overview
ms.assetid: eea11fe5-d8b0-4314-bb5d-8a58166fb1c3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 088faaf454d3b188cff681fb7c41f3966b2e93fd
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617503"
---
# <a name="cancellation-in-managed-threads"></a>Anulowanie w zarządzanych wątkach
Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework przy użyciu ujednoliconego modelu kooperatywne anulowanie asynchronicznego lub długotrwałe operacje synchroniczne. Ten model opiera się na lekki obiekt o nazwie token anulowania. Obiekt, który wywołuje co najmniej jednej operacji można anulować, na przykład, tworząc nowe wątki lub zadania, przekazuje ten token do każdej operacji. Poszczególne operacje z kolei można przekazać kopie tokenu do innych operacji. W późniejszym czasie obiekt, który utworzył token służy do żądania, że operacje przerwana, co robią. Tylko obiekt żądania można wydawać żądanie anulowania i każdego odbiornika jest odpowiedzialny za obserwowanie żądania i odpowiedzi do niej w sposób odpowiedni i terminowe.  
  
 Ogólny schemat implementowania modelu kooperatywne anulowanie jest:  
  
-   Utwórz wystąpienie <xref:System.Threading.CancellationTokenSource> obiektu, który zarządza i wysyła powiadomienie odwołania do tokenów anulowania indywidualnych.  
  
-   Przekaż token zwrócony przez <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> właściwość do każdego zadania lub wątkiem, który będzie nasłuchiwać pod kątem anulowania.  
  
-   Mechanizm dla każdego zadania lub wątek reagowanie na operację anulowania.  
  
-   Wywołaj <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę w celu udostępnienia powiadomienia o anulowaniu.  
  
> [!IMPORTANT]
>  <xref:System.Threading.CancellationTokenSource> Klasy implementuje <xref:System.IDisposable> interfejsu. Należy upewnić się wywołać <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> metoda po zakończeniu przy użyciu źródła tokenu anulowania z bezpłatnymi dowolne niezarządzanych zasobów, które przechowuje.  
  
 Poniższa ilustracja przedstawia relację między źródłem tokenu i wszystkie kopie jej token.  
  
 ![Cancellationtokensource — i anulowania tokeny](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Nowy model anulowania ułatwia tworzenie aplikacji obsługujących anulowania i bibliotek i obsługuje następujące funkcje:  
  
-   Anulowanie jest wspólne i nie jest wymuszana odbiornika. Odbiornik Określa, jak bezpiecznie zakończyć w odpowiedzi na żądanie anulowania.  
  
-   Żądanie różni się od nasłuchiwania. Obiekt, który wywołuje możliwości anulowania operacji można kontrolować, kiedy (Jeśli w ogóle) zażądano anulowania.  
  
-   Obiektu żądającego wystawia żądanie anulowania wszystkie kopie tokenu przy użyciu tylko jednego wywołania metody.  
  
-   Odbiornik może nasłuchiwać wielu tokenów jednocześnie, dołączając do nich w jednym *token połączony*.  
  
-   Kod użytkownika można zauważyć odpowiadać na żądania anulowania z biblioteki kodu i kod biblioteki można zauważyć i odpowiadać na żądania anulowania z kodu użytkownika.  
  
-   Odbiorniki może zostać poinformowany o żądań anulowania, sondowania, wywołanie zwrotne rejestracji lub Oczekiwanie na dojść oczekiwania.  
  
## <a name="cancellation-types"></a>Typami anulowania  
 W ramach anulowania jest wdrażany jako zestaw powiązanych typów, które są wymienione w poniższej tabeli.  
  
|Nazwa typu|Opis|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Obiekt, który tworzy token anulowania, a także generuje żądanie anulowania, aby uzyskać wszystkie kopie tego tokenu.|  
|<xref:System.Threading.CancellationToken>|Typ wartości uproszczone są przekazywane do co najmniej jednego odbiornika, zwykle jako parametr metody. Odbiorniki monitorować wartości `IsCancellationRequested` właściwość tokenu przez sondowanie, a także dojście oczekiwania.|  
|<xref:System.OperationCanceledException>|Zaakceptuj przeciążeń konstruktora wyjątków w <xref:System.Threading.CancellationToken> jako parametr. Odbiorniki opcjonalnie może zgłosić wyjątek w ten sposób, aby zweryfikować źródło anulowania i powiadomić inne osoby, które zostały wysłane odpowiedzi na żądanie anulowania.|  
  
 Nowy model anulowania jest zintegrowana z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w kilku typach. Najważniejsze są <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> i <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>. Zalecamy użycie tego nowego modelu anulowania dla wszystkich nowych kodu biblioteki i aplikacji.  
  
## <a name="code-example"></a>Przykład kodu  
 W poniższym przykładzie tworzy się obiektu żądającego <xref:System.Threading.CancellationTokenSource> obiektu, a następnie przekazuje jej <xref:System.Threading.CancellationTokenSource.Token%2A> właściwości można anulować operacji. Operacja, która odbiera żądanie monitoruje wartość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość token za pomocą sondowania. Gdy wartość staje się `true`, odbiornik może zakończyć w jakikolwiek sposób jest odpowiednia. W tym przykładzie metoda po prostu kończy działanie, czyli wszystko, co jest wymagane w wielu przypadkach.  
  
> [!NOTE]
>  W przykładzie użyto <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metodę, aby wykazać, że nowa struktura anulowania jest zgodna z interfejsami API w starszej wersji. Na przykład, który korzysta z nowych, preferowany <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu, zobacz [porady: anulowanie zadania i jego elementy podrzędne](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Anulowanie operacji i anulowania obiektu  
 W nowej struktury anulowania anulowania odnosi się do operacji, a nie obiektów. Żądanie anulowania oznacza, że operacja powinna zostać przerwana możliwie najszybciej po wykonaniu wymagane czyszczenia. Jednego tokenu anulowania powinni zapoznać się z jednego "można anulować operacji", jednak tej operacji może być implementowana w programach. Po <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> ustawiono właściwość tokenu `true`, nie można zresetować do `false`. W związku z tym anulowanie tokenów nie może zostać ponownie użyte po zostały anulowane.  
  
 Jeśli potrzebujesz mechanizmie anulowania obiektu, można utworzyć ją na mechanizmie anulowania operacji przez wywołanie metody <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> metodzie, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Jeśli obiekt obsługuje więcej niż jedną współbieżnych można anulować operację, należy przekazać tokenu oddzielnych jako dane wejściowe dla poszczególnych unikatowych możliwości anulowania operacji. Dzięki temu jedna operacja można anulować bez wpływu na inne.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Nasłuchiwanie i odpowiadać na żądania anulowania  
 W delegowanym użytkowniku implementujący można anulować operacji określa, jak zakończyć operację w odpowiedzi na żądanie anulowania. W wielu przypadkach pełnomocnika użytkownika można po prostu wykonać wszelkie wymagane oczyszczania, a następnie powróć natychmiast.  
  
 Jednak w bardziej złożonych przypadkach może być konieczne do pełnomocnika użytkownika powiadomić kod biblioteki, które nastąpiło anulowanie. W takich przypadkach, prawidłowym sposobem, aby zakończyć operację dotyczy pełnomocnika do wywołania <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, metody, która spowoduje, że <xref:System.OperationCanceledException> zostanie wygenerowany. Kod biblioteki można przechwycić ten wyjątek w wątku pełnomocnika użytkownika i sprawdź token wyjątku, aby ustalić, czy wyjątek wskazuje kooperatywne anulowanie lub wyjątkowej sytuacji.  
  
 <xref:System.Threading.Tasks.Task> Klasy obsługuje <xref:System.OperationCanceledException> w ten sposób. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Nasłuchiwanie za pomocą sondowania  
 Dla długotrwałe obliczenia tej pętli lub recurse, użytkownik może nasłuchiwać w oczekiwaniu na żądanie anulowania, okresowo Sondując wartość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> właściwości. Jeśli wartość to `true`, metody, należy wyczyścić i zakończyć tak szybko, jak to możliwe. Optymalną częstotliwość sondowania zależy od typu aplikacji. Jest dla deweloperów, aby określić najlepszy sondowania częstotliwości dowolnego danego programu. Sondowanie sam nie znacznie wpłynąć na wydajność. Poniższy przykład przedstawia sposób możliwych do sondowania.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Aby uzyskać pełniejszy przykład, zobacz [porady: nasłuchiwanie żądań anulowania za pomocą sondowania](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Nasłuchiwanie przez zarejestrowanie wywołania zwrotnego  
 Niektóre operacje mogą stać się zablokowane w taki sposób, że ich nie może sprawdzić wartość tokenu anulowania w sposób terminowy. W takich przypadkach należy zarejestrować metodę wywołania zwrotnego, która odblokowuje metody, gdy odbierze żądanie anulowania.  
  
 <xref:System.Threading.CancellationToken.Register%2A> Metoda zwraca <xref:System.Threading.CancellationTokenRegistration> obiekt, który jest używany w tym celu. Poniższy przykład pokazuje, jak używać <xref:System.Threading.CancellationToken.Register%2A> metodę, aby anulować asynchroniczne żądanie sieci Web.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 <xref:System.Threading.CancellationTokenRegistration> Obiektu zarządza synchronizacji wątków i gwarantuje, że wywołanie zwrotne wykonywanie zostanie przerwane w określonym punkcie w czasie.  
  
 W celu zapewnienia czasu reakcji systemu i w celu uniknięcia zakleszczenia podczas rejestrowania wywołań zwrotnych należy przestrzegać następujących wytycznych:  
  
-   Powinien być szybkie metody wywołania zwrotnego, ponieważ jest ona wywoływana synchronicznie, dlatego wywołanie <xref:System.Threading.CancellationTokenSource.Cancel%2A> nie powróci do momentu wywołania zwrotnego zwraca.  
  
-   Jeśli wywołasz <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> podczas wywołania zwrotnego jest uruchomiony i przytrzymaj, wywołanie zwrotne oczekuje na blokadę, program może zakleszczenie. Po `Dispose` zwraca, można zwolnić wszystkie zasoby wymagane przez wywołanie zwrotne.  
  
-   Wywołania zwrotne nie należy wykonywać ręcznie wątek lub <xref:System.Threading.SynchronizationContext> użycia w wywołaniu zwrotnym. Jeśli wywołanie zwrotne muszą być wykonywane w określonym wątku, należy użyć <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> Konstruktor, który pozwala określić, że syncContext docelowy jest aktywny <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>. Wykonywanie ręczne wielowątkowości w wywołaniu zwrotnym może spowodować zakleszczenia.  
  
 Aby uzyskać pełniejszy przykład, zobacz [porady: rejestrowanie wywołań zwrotnych żądań anulowania](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Nasłuchiwanie przy użyciu dojścia oczekiwania  
 Gdy zablokować możliwości anulowania operacji podczas oczekiwania na pierwotnych, takie jak synchronizacja <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> lub <xref:System.Threading.Semaphore?displayProperty=nameWithType>, możesz użyć <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> właściwością pozwalającą włączyć na oczekiwanie na zdarzenia i żądania anulowania operacji. Dojście oczekiwania token anulowania, zostanie zasygnalizowane w odpowiedzi na żądanie anulowania, a następnie użyć wartość zwracaną przez metodę <xref:System.Threading.WaitHandle.WaitAny%2A> metodę pozwala ustalić, czy została ona anulowania tokenu, który zasygnalizowane. Operacja, a następnie po prostu, lub zakończenia throw <xref:System.OperationCanceledException>, odpowiednio.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 W nowym kodzie, który jest przeznaczony dla [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> i <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> zarówno obsługi nowej struktury anulowania w ich `Wait` metody. Możesz przekazać <xref:System.Threading.CancellationToken> do metody, i po żądania anulowania zdarzenia zostanie wznowiona i zgłasza <xref:System.OperationCanceledException>.  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Aby uzyskać pełniejszy przykład, zobacz [jak: nasłuchiwania anulowania żądania ma czekać obsługi przez](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Nasłuchiwanie wielu tokenów jednocześnie  
 W niektórych przypadkach odbiornik może być jednocześnie nasłuchiwać wielu tokenów anulowania. Na przykład pewnej operacji trzeba monitorować tokenu anulowania wewnętrzny oprócz tokenu przekazanego zewnętrznie jako argumentu do parametru metody. W tym celu utwórz połączone źródło tokenu, który można dołączyć co najmniej dwa tokeny do jednego tokenu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Należy zauważyć, że należy wywołać `Dispose` na połączone źródło tokenu po wykonaniu tych czynności z nim. Aby uzyskać pełniejszy przykład, zobacz [porady: nasłuchiwanie wielu żądań anulowania](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Współpraca między kodem biblioteki i kod użytkownika  
 W ramach ujednoliconego anulowania umożliwia kod biblioteki anulować kod użytkownika i kod użytkownika anulować kod biblioteki w sposób współpracujący. Bezproblemowe współpracy zależy od każdej stronie poniższych wskazówek:  
  
-   Jeśli kod biblioteki udostępnia operacje można anulować, powinno dodatkowo dostarczać metody publiczne, które akceptują token anulowania zewnętrznych tak, aby kod użytkownika mogą żądać anulowania.  
  
-   Jeśli kod użytkownika wywołuje kod biblioteki, kod biblioteki należy interpretować OperationCanceledException(externalToken) jako *kooperatywne anulowanie*i niekoniecznie jako wyjątek błędu.  
  
-   Delegatów użytkownika powinien próbować odpowiadać na żądania anulowania z biblioteki kodu w odpowiednim czasie.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> to przykłady klas, które następują te wytyczne. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md)i [porady: Anulowanie zapytania PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)
