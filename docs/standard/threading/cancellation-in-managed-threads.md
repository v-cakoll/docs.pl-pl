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
ms.openlocfilehash: d4bbf30923d65ad7aeced80efa626136ae27491b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138137"
---
# <a name="cancellation-in-managed-threads"></a>Anulowanie w zarządzanych wątkach
Począwszy od .NET Framework 4 , .NET Framework używa ujednoliconego modelu do współpracy anulowania operacji synchronicznych lub długotrwałych synchronicznych. Ten model jest oparty na lekkim obiekcie o nazwie token anulowania. Obiekt, który wywołuje jedną lub więcej operacji można anulować, na przykład przez utworzenie nowych wątków lub zadań, przekazuje token do każdej operacji. Poszczególne operacje można z kolei przekazać kopie tokenu do innych operacji. W późniejszym czasie obiekt, który utworzył token można go używać do żądania, że operacje zatrzymać to, co robią. Tylko żądający obiekt może wystawić żądanie anulowania, a każdy odbiornik jest odpowiedzialny za zauważenie żądania i udzielenie na nie odpowiedzi w odpowiedni i terminowy sposób.  
  
 Ogólny wzorzec wdrażania modelu anulowania współpracy jest:  
  
- Tworzenie wystąpienia <xref:System.Threading.CancellationTokenSource> obiektu, który zarządza i wysyła powiadomienie o anulowaniu do poszczególnych tokenów anulowania.  
  
- Przekaż token zwrócony <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> przez właściwość do każdego zadania lub wątku, który nasłuchuje anulowania.  
  
- Podaj mechanizm dla każdego zadania lub wątku, aby odpowiedzieć na anulowanie.  
  
- Wywołaj <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę, aby powiadomić o anulowaniu.  
  
> [!IMPORTANT]
> Klasa <xref:System.Threading.CancellationTokenSource> implementuje interfejs <xref:System.IDisposable>. Należy upewnić się, <xref:System.Threading.CancellationTokenSource.Dispose%2A?displayProperty=nameWithType> aby wywołać metodę po zakończeniu przy użyciu źródła tokenu anulowania, aby zwolnić wszystkie zasoby niezarządzane, które posiada.  
  
 Na poniższej ilustracji przedstawiono relację między źródłem tokenu a wszystkimi kopiami jego tokenu.  
  
 ![CancellationTokenSource i tokeny anulowania](../../../docs/standard/threading/media/vs-cancellationtoken.png "VS_CancellationToken")  
  
 Nowy model anulowania ułatwia tworzenie aplikacji i bibliotek obsługujących anulowanie i obsługuje następujące funkcje:  
  
- Anulowanie jest spółdzielnia i nie jest zmuszony do odbiornika. Odbiornik określa, jak bezpiecznie zakończyć w odpowiedzi na żądanie anulowania.  
  
- Żądanie różni się od słuchania. Obiekt, który wywołuje operację anulowania można kontrolować, gdy (jeśli kiedykolwiek) anulowanie jest wymagane.  
  
- Żądający obiekt wystawia żądanie anulowania do wszystkich kopii tokenu przy użyciu tylko jednego wywołania metody.  
  
- Odbiornik może słuchać wielu tokenów jednocześnie, łącząc je w jeden *połączony token*.  
  
- Kod użytkownika może zauważyć i odpowiedzieć na żądania anulowania z kodu biblioteki, a kod biblioteki może zauważyć i odpowiadać na żądania anulowania z kodu użytkownika.  
  
- Odbiorniki mogą być powiadamiane o żądaniach anulowania przez sondowanie, rejestrację wywołania zwrotu lub oczekiwanie na dojścia oczekiwania.  
  
## <a name="cancellation-types"></a>Typy anulowania  
 Struktura anulowania jest implementowana jako zestaw powiązanych typów, które są wymienione w poniższej tabeli.  
  
|Nazwa typu|Opis|  
|---------------|-----------------|  
|<xref:System.Threading.CancellationTokenSource>|Obiekt, który tworzy token anulowania, a także wystawia żądanie anulowania dla wszystkich kopii tego tokenu.|  
|<xref:System.Threading.CancellationToken>|Typ wartości uproszczonej przekazany do jednego lub więcej odbiorników, zazwyczaj jako parametr metody. Detektory monitorują `IsCancellationRequested` wartość właściwości tokenu przez sondowanie, wywołanie wywołania zwrotu lub dojście oczekiwania.|  
|<xref:System.OperationCanceledException>|Przeciążenia konstruktora tego <xref:System.Threading.CancellationToken> wyjątku akceptują jako parametr. Odbiorniki mogą opcjonalnie zgłosić ten wyjątek, aby zweryfikować źródło anulowania i powiadomić inne osoby, że odpowiedział na żądanie anulowania.|  
  
 Nowy model anulowania jest zintegrowany z .NET Framework w kilku typach. Najważniejsze z nich <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>to <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> , <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>i . Zaleca się użycie tego nowego modelu anulowania dla wszystkich nowych biblioteki i kodu aplikacji.  
  
## <a name="code-example"></a>Przykład kodu  
 W poniższym przykładzie żądający obiekt <xref:System.Threading.CancellationTokenSource> tworzy obiekt, <xref:System.Threading.CancellationTokenSource.Token%2A> a następnie przekazuje jego właściwość do operacji można anulować. Operacja, która odbiera żądanie monitoruje wartość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości tokenu przez sondowanie. Gdy wartość staje `true`się , odbiornik może zakończyć się w dowolny sposób jest odpowiedni. W tym przykładzie metoda po prostu kończy działanie, co jest wszystko, co jest wymagane w wielu przypadkach.  
  
> [!NOTE]
> W przykładzie <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> użyto metody, aby wykazać, że nowa struktura anulowania jest zgodna ze starszymi interfejsami API. Na przykład, który używa <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nowego, preferowanego typu, zobacz [Jak: Anulowanie zadania i jego podrzędne](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 [!code-csharp[Cancellation#1](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex1.cs#1)]
 [!code-vb[Cancellation#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex1.vb#1)]  
  
## <a name="operation-cancellation-versus-object-cancellation"></a>Anulowanie operacji a anulowanie obiektu  
 W nowej strukturze anulowania anulowanie odnosi się do operacji, a nie obiektów. Żądanie anulowania oznacza, że operacja powinna zostać zatrzymana tak szybko, jak to możliwe po wykonaniu wymaganego oczyszczania. Jeden token anulowania powinien odnosić się do jednej "operacji można anulować", jednak ta operacja może być zaimplementowana w programie. Po <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> ustawieniu właściwości tokenu `true`nie można go `false`zresetować do wartości . W związku z tym tokeny anulowania nie mogą być ponownie używane po ich anulowaniu.  
  
 Jeśli potrzebujesz mechanizmu anulowania obiektu, można oprzeć go na <xref:System.Threading.CancellationToken.Register%2A?displayProperty=nameWithType> mechanizm anulowania operacji, wywołując metodę, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Cancellation#2](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/objectcancellation1.cs#2)]
 [!code-vb[Cancellation#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/objectcancellation1.vb#2)]  
  
 Jeśli obiekt obsługuje więcej niż jedną operację równoległą anulowaną, przekazać oddzielny token jako dane wejściowe do każdej odrębnej operacji anulowania. W ten sposób jedna operacja może zostać anulowana bez wpływu na inne.  
  
## <a name="listening-and-responding-to-cancellation-requests"></a>Nasłuchiwanie i odpowiadanie na żądania anulowania  
 W delegata użytkownika realizator operacji anulowane określa sposób zakończenia operacji w odpowiedzi na żądanie anulowania. W wielu przypadkach delegat użytkownika może po prostu wykonać wymagane oczyszczanie, a następnie natychmiast powrócić.  
  
 Jednak w bardziej złożonych przypadkach może być konieczne dla delegata użytkownika, aby powiadomić kod biblioteki, że nastąpiło anulowanie. W takich przypadkach właściwym sposobem zakończenia operacji jest dla delegata wywołać <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, <xref:System.OperationCanceledException> metoda, która spowoduje, że zostanie wyrzucony. Kod biblioteki można przechwycić ten wyjątek w wątku delegata użytkownika i sprawdzić token wyjątku, aby ustalić, czy wyjątek wskazuje anulowanie współpracy lub innej wyjątkowej sytuacji.  
  
 Klasa <xref:System.Threading.Tasks.Task> obsługuje <xref:System.OperationCanceledException> w ten sposób. Aby uzyskać więcej informacji, zobacz [Anulowanie zadań](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="listening-by-polling"></a>Słuchanie przez sondowanie  
 W przypadku długotrwałych obliczeń, które pętli lub recurse, można nasłuchiwać <xref:System.Threading.CancellationToken.IsCancellationRequested%2A?displayProperty=nameWithType> żądania anulowania przez okresowe sondowania wartości właściwości. Jeśli jego `true`wartość jest , metoda powinna oczyścić i zakończyć tak szybko, jak to możliwe. Optymalna częstotliwość sondowania zależy od typu aplikacji. To do dewelopera, aby określić najlepszą częstotliwość sondowania dla danego programu. Samo sondowanie nie ma znaczącego wpływu na wydajność. Poniższy przykład pokazuje jeden możliwy sposób sondowania.  
  
 [!code-csharp[Cancellation#3](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#3)]
 [!code-vb[Cancellation#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#3)]  
  
 Aby uzyskać pełniejszy przykład, zobacz [Jak: Nasłuchiwać żądań anulowania przez sondowanie](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-by-polling.md).  
  
### <a name="listening-by-registering-a-callback"></a>Słuchanie przez zarejestrowanie wywołania oddzwonienia  
 Niektóre operacje mogą zostać zablokowane w taki sposób, że nie można sprawdzić wartość tokenu anulowania w odpowiednim czasie. W takich przypadkach można zarejestrować metodę wywołania wywołania wstecz, która odblokowuje metodę po odebraniu żądania anulowania.  
  
 Metoda <xref:System.Threading.CancellationToken.Register%2A> zwraca <xref:System.Threading.CancellationTokenRegistration> obiekt, który jest używany specjalnie do tego celu. W poniższym przykładzie pokazano, jak użyć <xref:System.Threading.CancellationToken.Register%2A> metody do anulowania asynchronicznego żądania sieci Web.  
  
 [!code-csharp[Cancellation#4](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex4.cs#4)]
 [!code-vb[Cancellation#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex4.vb#4)]  
  
 Obiekt <xref:System.Threading.CancellationTokenRegistration> zarządza synchronizacją wątków i zapewnia, że wywołanie wsteczne przestanie wykonywać w określonym momencie.  
  
 W celu zapewnienia reakcji systemu i uniknięcia zakleszczenia, podczas rejestrowania wywołań wywołania wywołań wywołania należy przestrzegać następujących wytycznych:  
  
- Metoda wywołania zwrotnego powinna być szybka, ponieważ jest <xref:System.Threading.CancellationTokenSource.Cancel%2A> wywoływana synchronicznie i dlatego wywołanie nie zwraca, dopóki zwrot wywołania zwrotnego nie powróci.  
  
- Jeśli wywołasz <xref:System.Threading.CancellationTokenRegistration.Dispose%2A> podczas wywołania wywołania wywołania wywołania jest uruchomiony i trzymać blokadę, że wywołanie wstecz oczekuje na, program może zakleszczenie. Po `Dispose` powrocie można zwolnić wszystkie zasoby wymagane przez wywołanie wsteczne.  
  
- Wywołania odgłosów nie należy <xref:System.Threading.SynchronizationContext> wykonywać żadnych wątków ręcznych lub użycia w wywołaniu wywołania. Jeśli wywołanie wsteczne musi być uruchamiane w określonym wątku, należy użyć <xref:System.Threading.CancellationTokenRegistration?displayProperty=nameWithType> konstruktora, który umożliwia określenie, że docelowy syncContext jest aktywny <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>. Wykonywanie ręcznego wątkowania w wywołaniu wywołania wywołania może spowodować zakleszczenie.  
  
 Aby uzyskać pełniejszy przykład, zobacz [Jak: Rejestrować wywołania wywołań zwrotu dla żądań anulowania](../../../docs/standard/threading/how-to-register-callbacks-for-cancellation-requests.md).  
  
### <a name="listening-by-using-a-wait-handle"></a>Słuchanie za pomocą uchwytu oczekiwania  
 Gdy operacja anulowana może zablokować, gdy czeka na prymityw synchronizacji, takich jak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> lub <xref:System.Threading.Semaphore?displayProperty=nameWithType>, można użyć <xref:System.Threading.CancellationToken.WaitHandle%2A?displayProperty=nameWithType> właściwości, aby umożliwić operacji czekać na zdarzenie i żądanie anulowania. Dojście oczekiwania tokenu anulowania zostanie zasygnalizowane w odpowiedzi na żądanie anulowania, <xref:System.Threading.WaitHandle.WaitAny%2A> a metoda może użyć wartości zwracanej metody, aby ustalić, czy był to token anulowania, który zasygnalizował. Operacja może po prostu wyjść <xref:System.OperationCanceledException>lub rzucić , w razie potrzeby.  
  
 [!code-csharp[Cancellation#5](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#5)]
 [!code-vb[Cancellation#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#5)]  
  
 W nowym kodzie, który jest <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> przeznaczony dla .NET Framework `Wait` 4 i zarówno obsługi nowych struktur anulowania w swoich metodach. Można <xref:System.Threading.CancellationToken> przekazać do metody, a gdy odwołanie jest wymagane, zdarzenie budzi <xref:System.OperationCanceledException>się i zgłasza .  
  
 [!code-csharp[Cancellation#6](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#6)]
 [!code-vb[Cancellation#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#6)]  
  
 Aby uzyskać pełniejszy przykład, zobacz [Jak: Nasłuchiwać żądań anulowania, które mają uchwyty oczekiwania](../../../docs/standard/threading/how-to-listen-for-cancellation-requests-that-have-wait-handles.md).  
  
### <a name="listening-to-multiple-tokens-simultaneously"></a>Jednoczesne słuchanie wielu tokenów  
 W niektórych przypadkach odbiornik może być konieczne nasłuchiwanie wielu tokenów anulowania jednocześnie. Na przykład operacja anulowana może być musiał monitorować token anulowania wewnętrznego oprócz tokenu przekazywanego zewnętrznie jako argument do parametru metody. Aby to osiągnąć, utwórz źródło połączonego tokenu, które może dołączyć dwa lub więcej tokenów do jednego tokenu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Cancellation#7](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#7)]
 [!code-vb[Cancellation#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#7)]  
  
 Należy zauważyć, `Dispose` że należy wywołać źródło połączonego tokenu, gdy skończysz z nim. Aby uzyskać pełniejszy przykład, zobacz [Jak: Nasłuchiwać żądań wielokrotnego anulowania](../../../docs/standard/threading/how-to-listen-for-multiple-cancellation-requests.md).  
  
## <a name="cooperation-between-library-code-and-user-code"></a>Współpraca między kodem biblioteki a kodem użytkownika  
 Ujednolicona struktura anulowania umożliwia kod biblioteki, aby anulować kod użytkownika, a kod użytkownika, aby anulować kod biblioteki w sposób współpracy. Sprawne współpracy zależy od każdej ze stron, następujących wytycznych:  
  
- Jeśli kod biblioteki zawiera operacje anulowane, należy również podać metody publiczne, które akceptują token anulowania zewnętrznego, dzięki czemu kod użytkownika może zażądać anulowania.  
  
- Jeśli kod biblioteki wywołuje kod użytkownika, kod biblioteki należy interpretować OperationCanceledException(externalToken) jako *anulowanie współpracy*, a niekoniecznie jako wyjątek awarii.  
  
- Delegaci użytkownika powinni próbować odpowiedzieć na żądania anulowania z kodu biblioteki w odpowiednim czasie.  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>i <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> są przykładami klas, które postępują zgodnie z tymi wytycznymi. Aby uzyskać więcej informacji, zobacz [Anulowanie zadań](../../../docs/standard/parallel-programming/task-cancellation.md) i [jak: Anulowanie kwerendy PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)
