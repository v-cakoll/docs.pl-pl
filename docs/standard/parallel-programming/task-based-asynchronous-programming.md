---
title: Programowanie asynchroniczne opartego na zadaniach
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
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8e5367c8a786d720cdf3394922527020f8d4d47a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="task-based-asynchronous-programming"></a>Programowanie asynchroniczne opartego na zadaniach
Zadania biblioteki równoległych (TPL) opiera się na koncepcji *zadań*, który reprezentuje operację asynchroniczną. W pewnym sensie zadania jest podobny wątku lub <xref:System.Threading.ThreadPool> pracy elementu, ale na wyższym poziomie abstrakcji. Termin *równoległość zadań* odwołuje się do jednego lub więcej zadań niezależnie od uruchomione jednocześnie. Zadania zapewniają dwie podstawowe korzyści:  
  
-   Efektywniejsze i bardziej skalowalne wykorzystanie zasobów systemowych.  
  
     W tle zadań są umieszczane w kolejce <xref:System.Threading.ThreadPool>, która została rozszerzona o algorytmy, które ustalić i Dostosuj liczbę wątków i które zapewniają równoważenia obciążenia, aby zmaksymalizować przepustowość. Dzięki temu zadania są stosunkowo lekkie i można tworzyć wiele takich zadań, aby włączyć równoległość drobnoziarnistą.  
  
-   Większa kontrola programistyczna niż jest to możliwe za pomocą wątku lub elementu roboczego.  
  
     Zadania i środowisko zbudowane wokół nich zawierają bogaty zestaw interfejsów API, które obsługują oczekiwanie, anulowanie, kontynuację, niezawodną obsługę wyjątków, szczegółowe informacje o stanie, planowanie niestandardowe i nie tylko.  
  
 Dla obu tych powodów w .NET Framework TPL jest preferowanym interfejsem API do pisania kodu wielowątkowego, asynchronicznego i równoległego.  
  
## <a name="creating-and-running-tasks-implicitly"></a>Tworzenie i uruchamianie zadań niejawnie  
 <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> Metody oferują wygodny sposób równoczesne uruchamianie dowolną liczbę dowolnego instrukcje. Po prostu Przekaż w <xref:System.Action> delegowanego dla każdego elementu roboczego. Wyrażenia lambda są najwygodniejszym sposobem na tworzenie tych delegatów. Wyrażenie lambda może wywołać metodę nazwaną lub zapewnić kod inline. Poniższy przykład przedstawia podstawowy <xref:System.Threading.Tasks.Parallel.Invoke%2A> wywołaniu, które tworzy i uruchamia dwóch zadań związanych z zarządzaniem uruchamiać jednocześnie. Pierwszym zadaniem jest reprezentowana przez wyrażenie lambda, która wywołuje metodę o nazwie `DoSomeWork`, i drugie zadanie jest reprezentowana przez wyrażenie lambda, która wywołuje metodę o nazwie `DoSomeOtherWork`.  
  
> [!NOTE]
>  Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie masz doświadczenia z wyrażenia lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
 [!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]  
  
> [!NOTE]
>  Liczba <xref:System.Threading.Tasks.Task> wystąpień, które są tworzone w tle przez <xref:System.Threading.Tasks.Parallel.Invoke%2A> nie jest zawsze równa liczbie delegatów, które zostały opublikowane. TPL może wykorzystywać różne optymalizacje, zwłaszcza z dużą liczbą obiektów delegowanych.  
  
 Aby uzyskać więcej informacji, zobacz [porady: użycie parallel_invoke podczas przeprowadzania do przeprowadzania operacji równoległych](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).  
  
 Aby uzyskać większą kontrolę nad wykonywania zadania lub w celu zwrócenia wartości z zadania, masz do pracy z <xref:System.Threading.Tasks.Task> więcej jawnie obiektów.  
  
## <a name="creating-and-running-tasks-explicitly"></a>Tworzenie i uruchamianie zadań jawnie  
 Zadania, która nie zwraca wartości jest reprezentowana przez <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klasy. Zadanie zwracające wartość jest reprezentowana przez <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> klasy, która dziedziczy <xref:System.Threading.Tasks.Task>. Obiekt zadania obsługuje szczegóły infrastruktury i zapewnia metody i właściwości, które są dostępne z wątku wywoływania przez cały okres istnienia zadania. Na przykład można uzyskać dostęp <xref:System.Threading.Tasks.Task.Status%2A> właściwości zadania w dowolnym momencie w celu ustalenia, czy jego uruchomieniu, uruchomienia do ukończenia, została anulowana lub wywołało wyjątek. Stan jest reprezentowana przez <xref:System.Threading.Tasks.TaskStatus> wyliczenia.  
  
 Tworząc zadanie, nadajesz mu delegata użytkownika hermetyzującego kod, który zadanie będzie wykonywało. Delegat może być wyrażony jako delegat nazwany, metoda anonimowa lub wyrażenie lambda. Wyrażenia lambda mogą zawierać wywołanie metody nazwanej, jak pokazano w następującym przykładzie. Należy pamiętać, że przykład zawiera wywołanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody, aby upewnić się, że zadanie zostało ukończone wykonywania przed zakończeniem aplikacji w trybie konsoli.  
  
 [!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
 [!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]  
  
 Można również użyć <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody do tworzenia i uruchamiania zadania w jednej operacji. Aby zarządzanie zadaniami, <xref:System.Threading.Tasks.Task.Run%2A> metody za pomocą domyślnego harmonogramu zadań, niezależnie od tego, które zadania harmonogramu jest skojarzony z bieżącego wątku. <xref:System.Threading.Tasks.Task.Run%2A> Metody to preferowany sposób tworzenia i uruchamiania zadań, gdy nie jest wymagana większa kontrola nad tworzenie i Planowanie zadania.  
  
 [!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
 [!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]  
  
 Można również użyć <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metodę, aby utworzyć i uruchomić zadania w jednej operacji. Użyj tej metody, gdy tworzenie i planowanie nie muszą być rozdzielone i wymagane dodatkowe opcje tworzenia lub użycie określonego harmonogramu lub gdy musisz przekazać dodatkowe stanu do zadania za pomocą jego <xref:System.Threading.Tasks.Task.AsyncState%2A> właściwości, jak pokazano w Poniższy przykład.  
  
 [!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/startnew1.cs#3)]
 [!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/startnew1.vb#3)]  
  
 <xref:System.Threading.Tasks.Task>i <xref:System.Threading.Tasks.Task%601> każdy ujawnia statycznego <xref:System.Threading.Tasks.Task.Factory%2A> właściwość, która zwraca wystąpienie domyślne <xref:System.Threading.Tasks.TaskFactory>, dzięki czemu można wywołać metodę jako `Task.Factory.StartNew()`. Ponadto w poniższym przykładzie ponieważ zadania są typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, każdy z nich ma publiczny <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwość, która zawiera wynikiem obliczenia. Zadania są wykonywane asynchroniczne i mogą być kończone w dowolnej kolejności. Jeśli <xref:System.Threading.Tasks.Task%601.Result%2A> przed zakończeniem obliczenia dostępu do właściwości, właściwość blokuje wątek wywołujący, dopóki wartość jest dostępna.  
  
 [!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
 [!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: zwracanie wartości z zadania](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).  
  
 Używając wyrażenia lambda do utworzenia delegata, masz dostęp do wszystkich zmiennych, które są widoczne w tym momencie w kodzie źródłowym. Jednak w niektórych przypadkach, zwłaszcza w pętlach, lambda nie przechwytuje zmiennej zgodnie z oczekiwaniami. Przechwytuje tylko wartość końcową, a nie wartość, która mutuje po każdej iteracji. Poniższy przykład ilustruje ten problem. Przekazuje pętlę w licznik do wyrażenia lambda, tworzącym `CustomData` obiektu i używa licznika pętli jako identyfikator obiektu. Jako dane wyjściowe w przykładzie przedstawiono wszystkie `CustomData` obiekt ma taki sam identyfikator.  
  
 [!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
 [!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]  
  
 Możesz uzyskać dostęp do wartości w każdej iteracji poprzez zapewnienie obiektu stanu do zadania za pośrednictwem jej konstruktora. Poniższy przykład modyfikuje poprzedni przykład za pomocą licznika pętli, tworząc `CustomData` obiektu, który z kolei jest przekazywana do wyrażenia lambda.  Jako dane wyjściowe w przykładzie przedstawiono wszystkie `CustomData` obiekt teraz ma unikatowy identyfikator, na podstawie wartości licznika pętli w momencie wystąpienia obiektu.  
  
 [!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
 [!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]  
  
 Ten stan jest przekazywany jako argument do delegowanie zadań i jest dostępny z obiektu zadania przy użyciu <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> właściwości.  Poniższy przykład jest modyfikacją poprzedniego. Używa <xref:System.Threading.Tasks.Task.AsyncState%2A> właściwość, aby wyświetlić informacje o `CustomData` obiekty przekazywane do wyrażenia lambda.  
  
 [!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
 [!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]  
  
## <a name="task-id"></a>Identyfikator zadania  
 Każde zadanie odbiera liczbą całkowitą identyfikator, który unikatowo identyfikuje ją w domenie aplikacji i jest możliwy za pomocą <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> właściwości. Identyfikator jest przydatne w celu wyświetlenia informacji o zadaniach w debugerze programu Visual Studio **stosów równoległych** i **zadania** systemu windows. Identyfikator jest tworzony z opóźnieniem, co oznacza, że nie jest on tworzony do momentu pojawienia się stosownego żądania. Dlatego zadanie może mieć inny identyfikator za każdym razem, gdy program jest uruchamiany. Aby uzyskać więcej informacji o sposobie wyświetlania identyfikatorów zadań w debugerze, zobacz [korzystanie z okna zadań](/visualstudio/debugger/using-the-tasks-window) i [za pomocą okna stosów równoległych](/visualstudio/debugger/using-the-parallel-stacks-window).  
  
## <a name="task-creation-options"></a>Opcje tworzenia zadań  
 Większość interfejsów API, które tworzenie zadań podać przeciążenia, które akceptują <xref:System.Threading.Tasks.TaskCreationOptions> parametru. Określając jedną z poniższych opcji, możesz wskazać harmonogramowi zadań, jak zaplanować zadanie w puli wątków. Poniższa tabela zawiera różne opcje tworzenia zadania.  
  
|<xref:System.Threading.Tasks.TaskCreationOptions>wartość parametru|Opis|  
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|  
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Domyślna, gdy nie określono żadnej opcji. Harmonogram używa domyślnej heurystyki do zaplanowania zadania.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Określa, że zadanie powinno zostać zaplanowane tak, aby zadania utworzone wcześniej były wykonywane wcześniej, a zadania utworzone później były wykonywane później.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Określa, że zadanie reprezentuje operację długotrwałą.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Określa, że zadanie powinno zostać utworzone jako dołączone zadanie podrzędne do bieżącego zadania, jeśli takie istnieje. Aby uzyskać więcej informacji, zobacz [dołączonego i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|  
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Określa, że jeśli zadanie wewnętrzny Określa `AttachedToParent` opcji tego zadania nie staną się zadania podrzędnego dołączone.|  
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Określa, że harmonogram zadań dla zadania utworzone przez wywołanie metody, takie jak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> z poziomu konkretne zadanie jest harmonogram domyślny zamiast harmonogramu, w którym to zadanie jest uruchomiona.|  
  
 Opcje mogą być łączone przy użyciu bitowej **lub** operacji. W poniższym przykładzie przedstawiono zadania, które ma <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> i <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> opcji.  
  
 [!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
 [!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]  
  
## <a name="tasks-threads-and-culture"></a>Zadania, wątki i kultury.  
 Każdy wątek ma skojarzone kultury i kultury interfejsu użytkownika, który jest zdefiniowany przez <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> właściwości, odpowiednio. Kultury wątku jest używany podczas działania, takie jak formatowanie, analizy, sortowania i porównywania ciągów. Kultura interfejsu użytkownika dla wątku jest używany podczas wyszukiwania zasobów. Zwykle chyba że zostanie domyślną kulturę używaną do wszystkich wątków w domenie aplikacji przy użyciu <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> właściwości domyślną kulturę i kultury wątku interfejsu użytkownika jest definiowana za pomocą kultury systemu. Jeśli jawnie ustawione kultury wątku i uruchomić nowego wątku, nowego wątku nie dziedziczy kultury wątku; Zamiast tego jego kultury jest domyślną kulturą systemu. Modelu programowania opartego na zadaniach dla aplikacji, które odnoszą się do wersji programu .NET Framework, przed [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] być zgodne z tym rozwiązaniem.  
  
> [!IMPORTANT]
>  Należy pamiętać, że kultura wątku wywołującym jako część kontekstu zadania dotyczą aplikacji który *docelowej* [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], nie aplikacje który *uruchamiana* [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Podczas tworzenia projektu w programie Visual Studio, wybierając je z listy rozwijanej w górnej części tej wersji można wskazać określonej wersji programu .NET Framework **nowy projekt** okno dialogowe, lub na zewnątrz programu Visual Studio możesz użyć <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atrybutu. Dla aplikacji, które odnoszą się do wersji programu .NET Framework, przed [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], lub które nie są kierowane określonej wersji programu .NET Framework, kultury zadanie nadal będzie określany przez kultury wątku, na którym jest uruchomiony.  
  
 Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], kultury wątku wywołującym jest dziedziczona przez każde zadanie, nawet wtedy, gdy zadanie jest uruchamiane asynchronicznie w wątku puli wątków.  
  
 W poniższym przykładzie przedstawiono prosty ilustracji. Używa <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atrybut do docelowego [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] i zmiany bieżącej kultury aplikacji albo francuski (Francja) lub, jeśli francuski (Francja) jest już bieżącej kultury, angielski (Stany Zjednoczone). Następnie wywołuje delegata o nazwie `formatDelegate` zwracającą liczby sformatowane jako wartości waluty w nowej kultury. Należy pamiętać, że czy delegata jako zadanie synchronicznie lub asynchronicznie, zwraca oczekiwany wynik ponieważ kultury wątku jest dziedziczona przez zadanie asynchroniczne.  
  
 [!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
 [!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]  
  
 Jeśli używasz programu Visual Studio, można pominąć <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atrybutu i zamiast tego wybrać .NET Framework 4.6 jako element docelowy, podczas tworzenia projektu w **nowy projekt** okna dialogowego.  
  
 Dla danych wyjściowych, które odzwierciedla działanie aplikacji w wersji docelowej platformy .NET przed [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], Usuń <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atrybutu z kodu źródłowego. Dane wyjściowe zostaną one zastosowane formatowania konwencjach domyślną kulturę systemu nie kultury wątku.  
  
 Aby uzyskać więcej informacji na zadań asynchronicznych i kultury, zobacz sekcję "Kultury i operacji asynchronicznych opartego na zadaniach" w <xref:System.Globalization.CultureInfo> tematu.  
  
## <a name="creating-task-continuations"></a>Tworzenie zadań kontynuacje  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> metody umożliwiają określenie zadania w celu uruchomienia, gdy *poprzedzających zadań* zakończeniu. Delegat zadania kontynuacji jest przekazywany odwołanie do zadania poprzedzających, dzięki czemu można zbadać stanu zadania poprzedzających i, pobierając zaletą <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości, można użyć danych wyjściowych Antecedent jako dane wejściowe dla kontynuacji.  
  
 W poniższym przykładzie `getData` zadanie zostało uruchomione przez wywołanie do <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> metody. `processData` Zadanie zostało uruchomione automatycznie po `getData` zakończeniu i `displayData` po uruchomieniu `processData` zakończeniu. `getData`Tworzy tablicy liczba całkowita, która jest dostępna do `processData` zadań za pomocą `getData` zadania <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości. `processData` Zadanie przetwarza tablicy i zwraca wynik, którego typ jest wywnioskowany z zwracany typ wyrażenia lambda przekazany do <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> metody. `displayData` Zadanie wykonywane automatycznie po `processData` zakończeniu i <xref:System.Tuple%603> obiektu zwróconego przez `processData` Wyrażenie lambda jest dostępny dla `displayData` zadań za pomocą `processData` zadania <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Właściwość. `displayData` Zadanie trwa wynik `processData` zadań i daje wyniki o typie jest wywnioskowany w podobny sposób i który ma zostać udostępnione programu w <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości.  
  
 [!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
 [!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]  
  
 Ponieważ <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> jest metodą wystąpienia tworzenia łańcucha wywołań metody razem zamiast tworzenia wystąpienia <xref:System.Threading.Tasks.Task%601> obiekt dla każdego zadania poprzedzających. Poniższy przykład jest funkcjonalnie taki sam, jak poprzedni przykład, z wyjątkiem tego, że jednocześnie powiązany wywołań <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Należy pamiętać, że <xref:System.Threading.Tasks.Task%601> obiektu zwróconego przez cały łańcuch wywołań metody jest zadania kontynuacji końcowego.  
  
 [!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
 [!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]  
  
 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody umożliwiają kontynuować z wielu zadań.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="creating-detached-child-tasks"></a>Tworzenie zadania podrzędne odłączona  
 Jeśli kod użytkownika, który działa w zadaniu utworzenie nowego zadania i nie określa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcji, nowe zadanie nie jest zsynchronizowany z zadaniem nadrzędnym w specjalny sposób. Niezsynchronizowany zadań tego typu jest nazywana *odłączone zadania zagnieżdżonego* lub *zadania podrzędnego odłączyć*. Poniższy przykład przedstawia zadanie, które tworzy jedno odłączone zadanie podrzędne.  
  
 [!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
 [!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]  
  
 Należy zauważyć, że zadanie nadrzędne nie czeka na zakończenie odłączonego zadania podrzędnego.  
  
## <a name="creating-child-tasks"></a>Tworzenie zadań podrzędnych  
 Jeśli kod użytkownika, który działa w zadaniu tworzy zadanie z <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcji nowe zadanie jest nazywany *dołączony zadania podrzędnego* z zadaniem nadrzędnym. Można użyć <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcji w celu równoległość express strukturalne zadania, ponieważ zadaniem nadrzędnym niejawnie czeka na zakończenie wszystkich zadań podrzędnych dołączonych. Poniższy przykład przedstawia zadanie nadrzędne, które tworzy dziesięć dołączonych zadań podrzędnych. Należy pamiętać, że chociaż w przykładzie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody oczekiwania zadaniem nadrzędnym zakończyć, nie trzeba jawnie poczekaj na ukończenie zadań podrzędnych dołączone.  
  
 [!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
 [!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]  
  
 Można użyć zadaniem nadrzędnym <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcję, aby uniemożliwić innych zadań związanych z zadaniem nadrzędnym. Aby uzyskać więcej informacji, zobacz [dołączonego i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="waiting-for-tasks-to-finish"></a>Oczekiwanie na zakończenie zadań  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typy zapewniają kilka przeciążeń <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> i <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>--> `System.Threading.Tasks.Task.Wait` metod, które umożliwiają poczekaj na zakończenie zadania. Ponadto overloads statycznych <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody umożliwiają poczekaj, aż wybranych lub wszystkich tablicy zadań w celu zakończenia.  
  
 Zazwyczaj użytkownik czeka na zadanie z jednego z poniższych powodów:  
  
-   Główny wątek zależy od wyniku końcowego obliczonego przez zadanie.  
  
-   Trzeba obsługiwać wyjątki, które mogą być zgłoszone przez zadanie.  
  
-   Aplikacja może się zakończyć zanim wszystkie zadania zostaną ukończone. Na przykład aplikacje konsoli spowoduje przerwanie tak szybko, jak wszystkie synchroniczne kodu w `Main` zostało wykonane (punkt wejścia aplikacji).  
  
 Poniższy przykład przedstawia podstawowy wzorzec, który nie wymaga obsługi wyjątków.  
  
 [!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
 [!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]  
  
 Na przykład, który pokazuje obsługi wyjątków, zobacz [obsługi wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
 Niektóre przeciążenia pozwalają określić limit czasu i inne wykorzystują dodatkowe <xref:System.Threading.CancellationToken> jako parametr wejściowy, dzięki czemu można anulować sam czas oczekiwania albo programowo lub w odpowiedzi na użytkownika danych wejściowych.  
  
 Jeśli po odczekaniu zadania można niejawnie czekać, aż wszystkie elementy podrzędne danego zadania, które zostały utworzone przy użyciu <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcji. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>Zwraca natychmiast, jeśli zadanie zostało już ukończone. Wszelkie wyjątki zgłoszone przez zadanie zostanie zgłoszony przez <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody, nawet jeśli <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> wywołano metodę po zadanie zostało zakończone.  
  
## <a name="composing-tasks"></a>Tworzenie zadań  
 <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> klasy podać kilka metod, które mogą ułatwić utworzenie wielu zadań do zaimplementowania typowych wzorców i na lepsze wykorzystanie funkcji asynchronicznych języka, które znajdują się w języku C# [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]i F #. W tej sekcji opisano <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A>, i <xref:System.Threading.Tasks.Task.FromResult%2A> metody.  
  
### <a name="taskwhenall"></a>Task.WhenAll  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> Metody asynchronicznie oczekuje na wielu <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektów, aby zakończyć. Zapewnia przeciążone wersje, które umożliwiają czekanie na niejednolite zestawy zadań. Na przykład możesz poczekać na wielu <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiekty z jednej metody wywołania.  
  
### <a name="taskwhenany"></a>Task.WhenAny  
 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> Metody asynchronicznie oczekuje na jedną z wielu <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektów, aby zakończyć. Podobnie jak w <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> — metoda, ta metoda zapewnia przeciążone wersji, które umożliwiają poczekaj, aż niejednolitego zestawy zadań. <xref:System.Threading.Tasks.Task.WhenAny%2A> Metoda jest szczególnie przydatne w następujących scenariuszach.  
  
-   Operacje nadmiarowe. Należy wziąć pod uwagę algorytm lub operację, które mogą być wykonywane na wiele sposobów. Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metodę wybierz operację, którą najpierw zakończy, a następnie Anuluj pozostałych operacji.  
  
-   Operacje z przeplotem. Można uruchomić wiele operacji musi zakończyć wszystkie, które obsługują <xref:System.Threading.Tasks.Task.WhenAny%2A> metody do przetwarzania wyników zakończeniu każdej operacji. Po zakończeniu jednej operacji można uruchomić jedno lub więcej dodatkowych zadań.  
  
-   Operacje ograniczane. Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metodę rozszerzenie w poprzednim scenariuszu przez ograniczenie liczby równoczesnych operacji.  
  
-   Wygasłe operacje. Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> umożliwia wybranie jednego lub więcej zadań i zadań, która kończy się po określonym czasie, takie jak zadania, który jest zwracany przez metodę <xref:System.Threading.Tasks.Task.Delay%2A> metody. <xref:System.Threading.Tasks.Task.Delay%2A> Metoda została opisana w następnej sekcji.  
  
### <a name="taskdelay"></a>Task.Delay  
 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda tworzy <xref:System.Threading.Tasks.Task> obiekt, który kończy się po określonym czasie. Możesz użyć tej metoda do tworzenia pętli, które od czasu do czasu pobierają dane, wprowadzają limity czasu, opóźniają obsługę danych wejściowych użytkownika przez wyznaczony czas i tak dalej.  
  
### <a name="tasktfromresult"></a>Task(T).FromResult  
 Za pomocą <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody, można utworzyć <xref:System.Threading.Tasks.Task%601> obiekt przechowujący wynik wstępnie obliczone. Ta metoda jest przydatna, gdy wykonujesz operację asynchroniczną, która zwraca <xref:System.Threading.Tasks.Task%601> obiektu i wynik tego <xref:System.Threading.Tasks.Task%601> obiekt już jest obliczana. Na przykład, który używa <xref:System.Threading.Tasks.Task.FromResult%2A> można pobrać wyników operacji pobierania asynchroniczne, które są przechowywane w pamięci podręcznej, zobacz [porady: Tworzenie zadania Pre-Computed](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).  
  
## <a name="handling-exceptions-in-tasks"></a>Obsługa wyjątków w zadaniach  
 Gdy zadanie zwraca co najmniej jeden wyjątek, wyjątki są ujęte w <xref:System.AggregateException> wyjątku. Czy wyjątek jest propagowana do wątku, który tworzy sprzężenie z zadaniem, które jest zazwyczaj wątku, który oczekuje na zakończenie zadania lub wątku, który uzyskuje dostęp do <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości. To zachowanie służy do wymuszania zasady .NET Framework, zgodnie z którą wszystkie nieobsłużone wyjątki powinny domyślnie przerywać proces. Kod wywołujący może obsłużyć wyjątków przy użyciu dowolnej z następujących czynności w `try` / `catch` bloku:  
  
-   <xref:System.Threading.Tasks.Task.Wait%2A> — Metoda  
  
-   <xref:System.Threading.Tasks.Task.WaitAll%2A> — Metoda  
  
-   <xref:System.Threading.Tasks.Task.WaitAny%2A> — Metoda  
  
-   <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwości  
  
 Łącząca wątku mogą również obsługi wyjątków, uzyskując dostęp do <xref:System.Threading.Tasks.Task.Exception%2A> właściwości przed zadanie jest zbierane pamięci. Dostęp do tej właściwości zapobiega temu, że nieobsługiwany wyjątek inicjuje zachowanie propagacji wyjątku, które przerywa proces wraz z finalizacją obiektu.  
  
 Aby uzyskać więcej informacji dotyczących wyjątków i zadań, zobacz [obsługi wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="canceling-tasks"></a>Anulowanie zadania  
 `Task` Klasa obsługuje wspólne anulowanie i jest w pełni zintegrowana z <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> i <xref:System.Threading.CancellationToken?displayProperty=nameWithType> klasy, które zostały wprowadzone w programie .NET Framework 4. Wiele konstruktorów w <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> podjęcia klasy <xref:System.Threading.CancellationToken> obiektu jako parametr wejściowy. Duża liczba <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> i <xref:System.Threading.Tasks.Task.Run%2A> przeciążenia również obejmować <xref:System.Threading.CancellationToken> parametru.  
  
 Można utworzyć tokenu i wydać żądanie anulowania w późniejszym czasie, przy użyciu <xref:System.Threading.CancellationTokenSource> klasy. Przekaż token do <xref:System.Threading.Tasks.Task> jako argument, a także odwołanie do tego samego tokenu w elemencie delegowanym sieci użytkownika, który wykonuje pracę odpowiada na żądanie anulowania.  
  
 Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md) i [porady: anulowanie zadania i jego elementy podrzędne](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
## <a name="the-taskfactory-class"></a>Klasa fabryka zadań  
 <xref:System.Threading.Tasks.TaskFactory> Klasa udostępnia metody statyczne, które hermetyzują niektóre typowe wzorce tworzenia i uruchamiania zadań i zadań kontynuacji.  
  
-   Najbardziej typowe wzorzec jest <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, które tworzy i uruchamia zadania w jednej instrukcji.  
  
-   Po utworzeniu zadania kontynuacji z wielu antecedents użyj <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> metody lub <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody lub ich odpowiedniki w <xref:System.Threading.Tasks.Task%601> klasy. Aby uzyskać więcej informacji, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
-   Model programowania asynchronicznego hermetyzacji `BeginX` i `EndX` metod w <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> wystąpienia, należy użyć <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Aby uzyskać więcej informacji, zobacz [TPL i tradycyjnych .NET Framework asynchronicznego programowania](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 Wartość domyślna <xref:System.Threading.Tasks.TaskFactory> jest dostępny jako właściwość statyczna na <xref:System.Threading.Tasks.Task> klasy lub <xref:System.Threading.Tasks.Task%601> klasy. Można również utworzyć wystąpienie <xref:System.Threading.Tasks.TaskFactory> bezpośrednio i określ różne opcje, które obejmują <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.TaskCreationOptions> opcji <xref:System.Threading.Tasks.TaskContinuationOptions> opcji lub <xref:System.Threading.Tasks.TaskScheduler>. Niezależnie od opcji zostały określone podczas tworzenia fabryki zadań zostaną zastosowane do wszystkich zadań, które tworzy, chyba że <xref:System.Threading.Tasks.Task> jest tworzona przy użyciu <xref:System.Threading.Tasks.TaskCreationOptions> wyliczenia, w których przypadku zastąpienie Opcje zadania w odniesieniu do fabryki zadań.  
  
## <a name="tasks-without-delegates"></a>Zadania bez delegatów  
 W niektórych przypadkach warto użyć <xref:System.Threading.Tasks.Task> celu hermetyzacji niektórych operację asynchroniczną, która jest wykonywane przez składnik zewnętrzny zamiast pełnomocnika użytkownika. Jeśli operacja jest oparta na wzorcu asynchronicznego programowania modelu początek/koniec, możesz użyć <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Jeśli nie jest wielkość liter, możesz użyć <xref:System.Threading.Tasks.TaskCompletionSource%601> obiekt, aby zawijać operacji w zadaniu co pozwala na uzyskanie niektóre zalety <xref:System.Threading.Tasks.Task> programowania, na przykład, obsługa wyjątków propagacji i kontynuacje. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="custom-schedulers"></a>Planiści niestandardowi  
 Większość deweloperów aplikacji lub biblioteki nie zależy, który procesor zadanie jest uruchamiane na, jak synchronizuje pracę z innych zadań lub jak zostało zaplanowane na <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Wymagają one tylko, aby było wykonane jak najwydajniej na komputerze-hoście. Jeśli potrzebna większa kontrola nad szczegółami planowania, biblioteka zadań równoległych pozwala skonfigurować niektóre ustawienia w domyślnym harmonogramie zadań, a nawet pozwala podać niestandardowy harmonogram. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Tasks.TaskScheduler>.  
  
## <a name="related-data-structures"></a>Dane dotyczące struktur  
 TPL ma kilka nowych typów publicznych, które są przydatne w scenariuszach równoległych i sekwencyjnych. Obejmują one kilka klasy bezpieczne wątkowo, szybka i skalowalna kolekcji w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw i kilka synchronizacji nowe typy, na przykład <xref:System.Threading.Semaphore?displayProperty=nameWithType> i <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, które są bardziej efektywne niż ich starsza wersja określonych rodzaje obciążeń. Inne nowe typy w .NET Framework 4, na przykład <xref:System.Threading.Barrier?displayProperty=nameWithType> i <xref:System.Threading.SpinLock?displayProperty=nameWithType>, zapewniać funkcje, które nie były dostępne w starszych wersjach. Aby uzyskać więcej informacji, zobacz [struktury danych dla programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).  
  
## <a name="custom-task-types"></a>Zadanie niestandardowe typy  
 Firma Microsoft zaleca, aby nie dziedziczy z <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Zamiast tego zaleca się używanie <xref:System.Threading.Tasks.Task.AsyncState%2A> właściwości do kojarzenia dodatkowych danych i stanu z <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu. Umożliwia także metody rozszerzenia, aby rozszerzyć funkcjonalność <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> klasy. Aby uzyskać więcej informacji na temat metody rozszerzenia, zobacz [metody rozszerzenia](~/docs/csharp/programming-guide/classes-and-structs/extension-methods.md) i [metody rozszerzenia](~/docs/visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Jeśli musi dziedziczyć z <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, nie można użyć <xref:System.Threading.Tasks.Task.Run%2A>, <xref:System.Threading.Tasks.Task.Run%2A>, lub <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>, lub <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> typu klasy można utworzyć wystąpienia niestandardowego zadania, ponieważ tworzenie tych mechanizmów tylko <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiektów. Ponadto nie można użyć mechanizmy kontynuacji zadań, które są udostępniane przez <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory>, i <xref:System.Threading.Tasks.TaskFactory%601> można utworzyć wystąpień tego typu niestandardowego zadania, ponieważ te mechanizmy również tworzyć tylko <xref:System.Threading.Tasks.Task> i  <xref:System.Threading.Tasks.Task%601> obiektów.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-|-|  
|[Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Opisuje, jak działa kontynuacja.|  
|[Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Opisano różnicę między zadaniami podrzędnymi dołączonymi i odłączonymi.|  
|[Anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md)|Opisuje wbudowaną obsługę anulowania <xref:System.Threading.Tasks.Task> obiektu.|  
|[Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Opisuje sposób obsługi wyjątków w wątkach współbieżnych.|  
|[Instrukcje: wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Informacje dotyczące używania <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|  
|[Instrukcje: zwracanie wartości z zadania](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Zawiera opis sposobu zwracania wartości z zadań.|  
|[Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Opisuje, jak anulować zadania.|  
|[Instrukcje: tworzenie wstępnie obliczonych zadań](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Informacje dotyczące używania <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metoda pobierania wyników operacji pobierania asynchroniczne, które są przechowywane w pamięci podręcznej.|  
|[Instrukcje: przenoszenie drzewa binarnego z zadaniami równoległymi](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Opisuje używanie zadań do przechodzenia w drzewie binarnym.|  
|[Instrukcje: odpakowywanie zadania zagnieżdżonego](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Pokazuje, jak używać <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> — metoda rozszerzenia.|  
|[Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Informacje dotyczące używania <xref:System.Threading.Tasks.Parallel.For%2A> i <xref:System.Threading.Tasks.Parallel.ForEach%2A> umożliwia tworzenie pętle równoległe w danych.|  
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Węzeł najwyższego poziomu dla .NET Framework programowania równoległego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 [Programowanie równoległe w środowisku .NET Framework — przykłady](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
