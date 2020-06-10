---
title: Anulowanie w zarządzanych wątkach
description: Zrozumienie anulowania w zarządzanych wątkach. Poznaj tokeny anulowania w ramach spółdzielni anulowania asynchronicznych lub długotrwałych operacji synchronicznych.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation in .NET, overview
ms.assetid: eea11fe5-d8b0-4314-bb5d-8a58166fb1c3
ms.openlocfilehash: 9af4a64e50eff65023d5ed5bda868af2f8323a96
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662839"
---
# <a name="cancellation-in-managed-threads"></a>Anulowanie w zarządzanych wątkach
Począwszy od .NET Framework 4, .NET Framework korzysta z ujednoliconego modelu do obsługi operacji synchronicznych asynchronicznych lub długotrwałych. Ten model jest oparty na obiekcie lekkim nazywanym tokenem anulowania. Obiekt, który wywołuje jedną lub kilka operacji do anulowania, na przykład przez utworzenie nowych wątków lub zadań, przekazuje token do każdej operacji. Poszczególne operacje mogą z kolei przekazywać kopie tokenu do innych operacji. W późniejszym czasie obiekt, który utworzył token, może go użyć do żądania zatrzymywania wykonywania operacji. Tylko obiekt żądający może wydać żądanie anulowania, a każdy odbiornik jest odpowiedzialny za obserwowanie żądania i odpowiadanie na nie w odpowiednim czasie.  
  
 Ogólny wzorzec dla implementacji spółdzielczego modelu anulowania to:  
  
- Utworzenie wystąpienia <xref:System.Threading.CancellationTokenSource> obiektu, który zarządza i wysyła powiadomienie o anulowaniu do poszczególnych tokenów anulowania.  
  
- Przekaż token zwracany przez <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> Właściwość do każdego zadania lub wątku, który nasłuchuje do anulowania.  
  
- Udostępnij mechanizm dla każdego zadania lub wątku, aby odpowiedzieć na anulowanie.  
  
- Wywołaj <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę, aby powiadomić o anulowaniu.  
  
> [!IMPORTANT]
> Klasa <xref:System.Threading.CancellationTokenSource> implementuje interfejs <xref:System.IDisposable>. Należy pamiętać, aby wywołać <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> metodę po zakończeniu korzystania ze źródła tokenu anulowania w celu zwolnienia wszelkich niezarządzanych zasobów, które przechowuje.  
  
 Poniższa ilustracja przedstawia relację między źródłem tokenu i wszystkimi kopiami jego tokenu.  
  
 ![Tokeny CancellationTokenSource i anulowania](media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Nowy model anulowania ułatwia tworzenie aplikacji obsługujących anulowanie i bibliotek oraz obsługę następujących funkcji:  
  
- Anulowanie jest wspólne i nie jest wymuszane na odbiorniku. Odbiornik Określa, jak bezpiecznie kończyć się w odpowiedzi na żądanie anulowania.  
  
- Żądanie jest różne od nasłuchiwania. Obiekt, który wywołuje operację do anulowania, może kontrolować, kiedy jest wymagane anulowanie (Jeśli kiedykolwiek).  
  
- Obiekt żądający wysyła żądanie anulowania do wszystkich kopii tokenu przy użyciu tylko jednego wywołania metody.  
  
- Odbiornik może nasłuchiwać wielu tokenów jednocześnie, łącząc je w jeden *połączony token*.  
  
- Kod użytkownika może zauważyć i odpowiadać na żądania anulowania z kodu biblioteki, a kod biblioteki może zauważyć żądania anulowania od kodu użytkownika i odpowiadać na nie.  
  
- Odbiorniki mogą otrzymywać powiadomienia o żądaniach anulowania przez sondowanie, rejestrację wywołania zwrotnego lub oczekiwanie na uchwyty oczekiwania.  
  
## <a name="cancellation-types"></a>Typy anulowania  
 Platforma anulowania jest zaimplementowana jako zestaw powiązanych typów, które są wymienione w poniższej tabeli.  
  
|Nazwa typu|Opis|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Obiekt, który tworzy token anulowania, a także wystawia żądanie anulowania dla wszystkich kopii tego tokenu.|  
|<xref:System.Threading.CancellationToken>|Typ wartości uproszczonej przesłany do jednego lub większej liczby detektorów, zazwyczaj jako parametr metody. Odbiorniki monitorują wartość `IsCancellationRequested` właściwości tokenu przez sondowanie, wywołanie zwrotne lub dojście oczekiwania.|  
|<xref:System.OperationCanceledException>|Przeciążenia konstruktora tego wyjątku akceptują <xref:System.Threading.CancellationToken> jako parametr. Odbiorniki mogą opcjonalnie zgłosić ten wyjątek, aby zweryfikować Źródło anulowania i poinformować inne, że odpowiedział na żądanie anulowania.|  
  
 Nowy model anulowania jest zintegrowany z .NET Framework w kilku typach. Najważniejsze są <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> , <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> i <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> . Zalecamy używanie tego nowego modelu anulowania dla całej nowej biblioteki i kodu aplikacji.  
  
## <a name="code-example"></a>Przykład kodu  
 W poniższym przykładzie obiekt żądający tworzy <xref:System.Threading.CancellationTokenSource> obiekt, a następnie przekazuje jego <xref:System.Threading.CancellationTokenSource.Token%2A> Właściwość do operacji do anulowania. Operacja, która odbiera żądanie, monitoruje wartość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości tokenu przez sondowanie. Gdy wartość stanie się `true` , odbiornik może zakończyć się w dowolny sposób. W tym przykładzie metoda tylko opuszcza, która jest wymagana w wielu przypadkach.  
  
> [!NOTE]
> W przykładzie zastosowano <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> metodę, aby zademonstrować, że nowa struktura anulowania jest zgodna ze starszymi interfejsami API. Aby zapoznać się z przykładem wykorzystującym nowy, preferowany <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Typ, zobacz [How to: Cancel a Task and jego Children](../parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Anulowanie operacji względem anulowania obiektu  
 W nowej strukturze anulowania odwołanie odwołuje się do operacji, a nie obiektów. Żądanie anulowania oznacza, że operacja powinna zostać zatrzymana tak szybko, jak to możliwe po przeprowadzeniu wymaganego oczyszczenia. Jeden token anulowania powinien odwoływać się do jednej "operacji możliwej do anulowania", jednak może być zaimplementowana w programie. Po <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> ustawieniu właściwości tokenu na wartość `true` nie można jej resetować do `false` . W związku z tym tokeny anulowania nie mogą być ponownie używane po anulowaniu.  
  
 Jeśli wymagany jest mechanizm anulowania obiektu, można oprzeć go na mechanizmie anulowania operacji, wywołując <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> metodę, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Jeśli obiekt obsługuje więcej niż jedną współbieżną operację, należy przekazać oddzielny token jako dane wejściowe do każdej unikatowej operacji anulowania. Dzięki temu można anulować jedną operację bez wpływu na inne osoby.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Nasłuchiwanie żądań anulowania i reagowanie na nie  
 W delegatze użytkownika, realizator operacji anulowania określa sposób kończenia operacji w odpowiedzi na żądanie anulowania. W wielu przypadkach delegat użytkownika może po prostu wykonać wymagane czyszczenie, a następnie natychmiast zwrócić.  
  
 Jednak w bardziej złożonych przypadkach może być konieczne, aby delegat użytkownika powiadamiał kod biblioteki, że wystąpiło anulowanie. W takich przypadkach poprawny sposób zakończenia operacji jest przeznaczony dla delegata do wywołania <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody, co spowoduje, że zostanie <xref:System.OperationCanceledException> zgłoszony. Kod biblioteki może przechwytywać ten wyjątek w wątku delegata użytkownika i sprawdzać token wyjątku, aby określić, czy wyjątek wskazuje na wcześniejsze anulowanie lub inne wyjątkowe sytuacje.  
  
 <xref:System.Threading.Tasks.Task>Klasa obsługuje <xref:System.OperationCanceledException> w ten sposób. Aby uzyskać więcej informacji, zobacz [Anulowanie zadania](../parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Nasłuchiwanie przez sondowanie  
 W przypadku długotrwałych obliczeń, które są wykonywane w pętli lub rekursywnie, można nasłuchiwać żądania anulowania przez okresowe sondowanie wartości <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> właściwości. Jeśli wartość to `true` , metoda powinna czyścić i kończyć się tak szybko, jak to możliwe. Optymalna częstotliwość sondowania zależy od typu aplikacji. Deweloper może określić najlepszą częstotliwość sondowania dla danego programu. Sondowanie nie ma znaczącego wpływu na wydajność. Poniższy przykład pokazuje jeden możliwy sposób sondowania.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Aby zapoznać się z bardziej kompletnym przykładem, zobacz [jak: nasłuchiwanie żądań anulowania przez sondowanie](how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Nasłuchiwanie przez zarejestrowanie wywołania zwrotnego  
 Niektóre operacje mogą zostać zablokowane w taki sposób, że nie mogą sprawdzić wartości tokenu anulowania w odpowiednim czasie. W takich przypadkach można zarejestrować metodę wywołania zwrotnego, która odblokowuje metodę po odebraniu żądania anulowania.  
  
 <xref:System.Threading.CancellationToken.Register%2A>Metoda zwraca <xref:System.Threading.CancellationTokenRegistration> obiekt, który jest używany specjalnie do tego celu. W poniższym przykładzie pokazano, jak za pomocą <xref:System.Threading.CancellationToken.Register%2A> metody anulować asynchroniczne żądanie sieci Web.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 <xref:System.Threading.CancellationTokenRegistration>Obiekt zarządza synchronizacją wątków i zapewnia, że wywołanie zwrotne przestanie być wykonywane w określonym momencie.  
  
 Aby zapewnić czas odpowiedzi systemu i uniknąć zakleszczeń, należy przestrzegać następujących wytycznych podczas rejestrowania wywołań zwrotnych:  
  
- Metoda wywołania zwrotnego powinna być szybka, ponieważ jest wywoływana synchronicznie i w związku z tym wywołanie <xref:System.Threading.CancellationTokenSource.Cancel%2A> nie zwraca do momentu powrotu wywołania zwrotnego.  
  
- W przypadku wywołania <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> , gdy wywołanie zwrotne jest uruchomione i zatrzymasz blokadę, która oczekuje na wywołanie zwrotne, program może być zakleszczony. Po `Dispose` powrocie można zwolnić wszystkie zasoby wymagane przez wywołanie zwrotne.  
  
- Wywołania zwrotne nie powinny wykonywać żadnego wątku ręcznego ani <xref:System.Threading.SynchronizationContext> użycia w wywołaniu zwrotnym. Jeśli wywołanie zwrotne musi zostać uruchomione w określonym wątku, użyj <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> konstruktora, który umożliwia określenie, że element docelowy syncContext jest aktywny <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> . Ręczne wykonywanie wątków w wywołaniu zwrotnym może spowodować zakleszczenie.  
  
 Aby zapoznać się z bardziej kompletnym przykładem, zobacz [jak: rejestrowanie wywołań zwrotnych żądań anulowania](how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Nasłuchiwanie przy użyciu dojścia oczekiwania  
 Gdy operacja, którą można anulować, może blokować, gdy oczekuje na element pierwotny synchronizacji, taki jak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> lub <xref:System.Threading.Semaphore?displayProperty=nameWithType> , można użyć <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> właściwości, aby umożliwić operacji oczekiwania na zdarzenie i żądanie anulowania. Dojście oczekiwania tokenu anulowania zostanie sygnalizowane w odpowiedzi na żądanie anulowania, a metoda może użyć wartości zwracanej przez <xref:System.Threading.WaitHandle.WaitAny%2A> metodę, aby określić, czy był to token anulowania, który zasygnalizuje. Operacja może po prostu zakończyć lub zgłosić <xref:System.OperationCanceledException> , zgodnie z potrzebami.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 W nowym kodzie, który jest przeznaczony dla .NET Framework 4 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> i <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> obie wersje obsługują nową strukturę anulowania w ich `Wait` metodach. Można przekazać <xref:System.Threading.CancellationToken> do metody, a po zażądaniu anulowania zdarzenie zostanie wznowione i wygeneruje <xref:System.OperationCanceledException> .  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Aby zapoznać się z bardziej kompletnym przykładem, zobacz [jak: nasłuchiwanie żądań anulowania z dojściami oczekiwania](how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Jednoczesne nasłuchiwanie wielu tokenów  
 W niektórych przypadkach odbiornik może chcieć nasłuchiwać wielu tokenów anulowania jednocześnie. Na przykład operacja anulowania może być konieczne do monitorowania wewnętrznego tokenu anulowania oprócz tokenu przesyłanego zewnętrznie jako argumentu do parametru metody. Aby to osiągnąć, Utwórz źródło połączonego tokenu, które może dołączyć dwa lub więcej tokenów do jednego tokenu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Zwróć uwagę, że `Dispose` po wykonaniu tej czynności należy wywołać Źródło połączonego tokenu. Aby zapoznać się z bardziej kompletnym przykładem, zobacz [jak: nasłuchiwanie wielu żądań anulowania](how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Współpraca między kodem biblioteki i kodem użytkownika  
 Ujednolicona platforma anulowania pozwala na kod biblioteki, aby anulować kod użytkownika, a kod użytkownika w celu anulowania kodu biblioteki w sposób współpracy. Bezproblemowa współpraca zależy od następujących wskazówek:  
  
- Jeśli kod biblioteki zapewnia operacje, które można anulować, powinien również dostarczyć metody publiczne, które akceptują Zewnętrzny token anulowania, aby kod użytkownika mógł żądać anulowania.  
  
- Jeśli kod biblioteki wywołuje kod użytkownika, kod biblioteki powinien interpretować OperationCanceledException (externalToken) jako *spółdzielnie anulowania*i niekoniecznie jako wyjątek błędu.  
  
- Delegaty użytkownika powinni próbować odpowiedzieć na żądania anulowania z kodu biblioteki w odpowiednim czasie.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>i <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> są przykładami klas, które są zgodne z tymi wskazówkami. Aby uzyskać więcej informacji, zobacz [Anulowanie zadania](../parallel-programming/task-cancellation.md) i [instrukcje: anulowanie zapytania PLINQ](../parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzana wątkowość — podstawy](managed-threading-basics.md)
