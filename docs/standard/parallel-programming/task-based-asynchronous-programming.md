---
title: Oparta na zadaniach programowanie asynchroniczne — .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad13a5771adbfbd389feeccd3e8c833c4c2f778a
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300632"
---
# <a name="task-based-asynchronous-programming"></a>Programowanie asynchroniczne oparte na zadanie

Biblioteka zadań równoległych (TPL) opiera się na koncepcji *zadań*, które reprezentuje operację asynchroniczną. Pod pewnymi względami zadanie jest podobne do wątku lub <xref:System.Threading.ThreadPool> pracy elementu, ale na wyższym poziomie abstrakcji. Termin *równoległość zadań* odwołuje się do co najmniej jeden niezależnych zadań działających równocześnie. Zadania zapewniają dwie podstawowe korzyści:

- Efektywniejsze i bardziej skalowalne wykorzystanie zasobów systemowych.

     W tle zadania są umieszczane w kolejce do <xref:System.Threading.ThreadPool>, który został rozszerzony o algorytmy, które określają i dostosowują się do liczby wątków i umożliwiają równoważenie obciążenia w celu zmaksymalizowania wydajności. Dzięki temu zadania są stosunkowo lekkie i można tworzyć wiele takich zadań, aby włączyć równoległość drobnoziarnistą.

- Większa kontrola programistyczna niż jest to możliwe za pomocą wątku lub elementu roboczego.

     Zadania i środowisko zbudowane wokół nich zawierają bogaty zestaw interfejsów API, które obsługują oczekiwanie, anulowanie, kontynuację, niezawodną obsługę wyjątków, szczegółowe informacje o stanie, planowanie niestandardowe i nie tylko.

Dla obu tych powodów w .NET Framework TPL jest preferowanym interfejsem API do pisania kodu wielowątkowego, asynchronicznego i równoległego.

## <a name="creating-and-running-tasks-implicitly"></a>Tworzenie i uruchamianie zadań w sposób niejawny

<xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> Metoda zapewnia wygodny sposób uruchamiania dowolnej ilości instrukcji umownych jednocześnie. Po prostu Przekaż <xref:System.Action> delegata dla każdego elementu pracy. Wyrażenia lambda są najwygodniejszym sposobem na tworzenie tych delegatów. Wyrażenie lambda może wywołać metodę nazwaną lub zapewnić kod inline. Poniższy przykład przedstawia podstawowe <xref:System.Threading.Tasks.Parallel.Invoke%2A> wywołania, które tworzy i rozpoczyna dwa zadania, działające równocześnie. Pierwsze zadanie jest reprezentowane przez wyrażenie lambda, które wywołuje metodę o nazwie `DoSomeWork`, a drugie zadanie jest reprezentowane przez wyrażenie lambda, która wywołuje metodę o nazwie `DoSomeOtherWork`.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Liczba <xref:System.Threading.Tasks.Task> wystąpień, które są tworzone w tle przez <xref:System.Threading.Tasks.Parallel.Invoke%2A> nie jest zawsze równa liczbie dostarczanych delegatów. TPL może wykorzystywać różne optymalizacje, zwłaszcza z dużą liczbą obiektów delegowanych.

Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Aby uzyskać większą kontrolę nad wykonywaniem zadań lub w celu zwrócenia wartości z zadania trzeba pracować z <xref:System.Threading.Tasks.Task> obiekty w bardziej jawny sposób.

## <a name="creating-and-running-tasks-explicitly"></a>Tworzenie i uruchamianie zadań w sposób jawny

Zadanie, która nie zwraca wartości jest reprezentowane przez <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klasy. Zadanie zwracające wartość jest reprezentowany przez <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> klasy, która dziedziczy po elemencie <xref:System.Threading.Tasks.Task>. Obiekt zadania obsługuje szczegóły infrastruktury i zapewnia metody i właściwości, które są dostępne z wątku wywoływania przez cały okres istnienia zadania. Na przykład, możesz uzyskać dostęp <xref:System.Threading.Tasks.Task.Status%2A> właściwości zadania w dowolnym momencie, aby ustalić, czy rozpoczęło działanie, zakończyło się, zostało anulowane lub został zgłoszony wyjątek. Stan jest reprezentowany przez <xref:System.Threading.Tasks.TaskStatus> wyliczenia.

Tworząc zadanie, nadajesz mu delegata użytkownika hermetyzującego kod, który zadanie będzie wykonywało. Delegat może być wyrażony jako delegat nazwany, metoda anonimowa lub wyrażenie lambda. Wyrażenia lambda mogą zawierać wywołanie metody nazwanej, jak pokazano w następującym przykładzie. Należy zauważyć, że przykład zawiera wywołanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodę, aby upewnić się, że zadanie kończy wykonywanie przed zakończeniem aplikacji trybu konsoli.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Można również użyć <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody, aby utworzyć i uruchomić zadanie w ramach jednej operacji. Aby zarządzać zadaniem, <xref:System.Threading.Tasks.Task.Run%2A> metody używają domyślnego harmonogramu zadań, niezależnie od tego, które zadanie harmonogram jest skojarzony z bieżącym wątkiem. <xref:System.Threading.Tasks.Task.Run%2A> Metody są preferowanym sposobem tworzenia i uruchamiania zadań, gdy nie jest potrzebna większa kontrola nad tworzeniem i planowaniem zadania.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Można również użyć <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metodę, aby utworzyć i uruchomić zadanie w ramach jednej operacji. Użyj tej metody, gdy tworzenie i planowanie nie muszą być rozdzielone i wymagasz dodatkowych opcje tworzenia zadań lub użycia określonego harmonogramu, lub gdy potrzebujesz przekazać dodatkowy stan do zadania, które można pobrać przy użyciu jego <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> Właściwość, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> ujawniają statyczną <xref:System.Threading.Tasks.Task.Factory%2A> właściwość, która zwraca wystąpienie domyślne <xref:System.Threading.Tasks.TaskFactory>, dzięki czemu można wywołać metodę jako `Task.Factory.StartNew()`. Ponadto w poniższym przykładzie ponieważ zadania są typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, każdy z nich ma publiczną <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwość, która zawiera wynik obliczenia. Zadania są wykonywane asynchroniczne i mogą być kończone w dowolnej kolejności. Jeśli <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość odbywa się przed zakończeniem obliczania, właściwość blokuje wątek wywołujący, aż wartość jest dostępna.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Aby uzyskać więcej informacji, zobacz [jak: Zwracanie wartości z zadania](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Używając wyrażenia lambda do utworzenia delegata, masz dostęp do wszystkich zmiennych, które są widoczne w tym momencie w kodzie źródłowym. Jednak w niektórych przypadkach, zwłaszcza w pętlach, lambda nie przechwytuje zmiennej zgodnie z oczekiwaniami. Przechwytuje tylko wartość końcową, a nie wartość, która mutuje po każdej iteracji. Poniższy przykład ilustruje ten problem. Pętla przekazuje licznik do wyrażenia lambda, która tworzy wystąpienie `CustomData` obiektu i używa licznika pętli jako identyfikatora obiektu. Jak wynika z przykładu pokazują, każdy `CustomData` obiekt ma identyczny identyfikator.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

Możesz uzyskać dostęp do wartości w każdej iteracji poprzez zapewnienie obiektu stanu do zadania za pośrednictwem jej konstruktora. Poniższy przykład modyfikuje poprzedni przykład za pomocą licznika pętli przy tworzeniu `CustomData` obiektu, który z kolei jest przekazywany do wyrażenia lambda.  Jak wynika z przykładu pokazują, każdy `CustomData` obiekt ma teraz unikatowy identyfikator na podstawie wartości licznika pętli w momencie wystąpienia obiektu.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Ten stan jest przekazywany jako argument do delegata zadania, i jest dostępny z obiektu zadania przy użyciu <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> właściwości.  Poniższy przykład jest modyfikacją poprzedniego. Używa ona <xref:System.Threading.Tasks.Task.AsyncState%2A> właściwości, aby wyświetlić informacje o `CustomData` przekazywanym do wyrażenia lambda.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>Identyfikator zadania

Każde zadanie otrzymuje identyfikator całkowitoliczbowy, który unikatowo identyfikuje je w domenie aplikacji i jest możliwy za pomocą <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> właściwości. Identyfikator jest przydatny do wyświetlania informacji o zadaniu w debugerze programu Visual Studio **stosów równoległych** i **zadania** systemu windows. Identyfikator jest tworzony z opóźnieniem, co oznacza, że nie jest on tworzony do momentu pojawienia się stosownego żądania. Dlatego zadanie może mieć inny identyfikator za każdym razem, gdy program jest uruchamiany. Aby uzyskać więcej informacji na temat sposobu wyświetlania identyfikatorów zadań w debugerze, zobacz [korzystanie z okna zadań](/visualstudio/debugger/using-the-tasks-window) i [przy użyciu Parallel Stacks Window](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Opcje tworzenia zadań

Większość interfejsów API, które tworzą zadania, zapewnienia przeciążenia, które akceptują <xref:System.Threading.Tasks.TaskCreationOptions> parametru. Określając jedną z poniższych opcji, możesz wskazać harmonogramowi zadań, jak zaplanować zadanie w puli wątków. Poniższa tabela zawiera różne opcje tworzenia zadania.

|<xref:System.Threading.Tasks.TaskCreationOptions> Wartość parametru|Opis|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Domyślna, gdy nie określono żadnej opcji. Harmonogram używa domyślnej heurystyki do zaplanowania zadania.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Określa, że zadanie powinno zostać zaplanowane tak, aby zadania utworzone wcześniej były wykonywane wcześniej, a zadania utworzone później były wykonywane później.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Określa, że zadanie reprezentuje operację długotrwałą.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Określa, że zadanie powinno zostać utworzone jako dołączone zadanie podrzędne do bieżącego zadania, jeśli takie istnieje. Aby uzyskać więcej informacji, zobacz [dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Określa, że jeśli wewnętrzne zadanie Określa `AttachedToParent` opcji, zadanie to nie stanie się dołączonym zadaniem podrzędnym.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Określa, że harmonogram zadań dla zadań utworzonych przez wywoływanie metod, takich jak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> z poziomu danego zadania jest harmonogramem domyślnym zamiast harmonogramu, na którym działa zadanie.|

Opcje mogą być połączone za pomocą bitowej **lub** operacji. Poniższy przykład przedstawia zadanie, które ma <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> i <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> opcji.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Zadania, wątki i kultury

Każdy wątek ma skojarzone kultury i kultury UI, która jest zdefiniowana przez <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> właściwości, odpowiednio. Kultury wątku jest używana w operacjach, takich jak formatowanie, analizowanie, sortowania i porównywania ciągów. Kultura interfejsu użytkownika dla wątku jest używany podczas wyszukiwania zasobów. Zazwyczaj chyba że określisz domyślną kulturę używaną do wszystkich wątków w domenie aplikacji przy użyciu <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> i <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> właściwości domyślnej kultury i kultury wątku interfejsu użytkownika jest definiowany przez kultury systemu. Jeśli jawnie ustawić kultury wątku i uruchomić nowy wątek, nowy wątek nie dziedziczy kultury wątku wywołującego; Zamiast tego jego kultury jest domyślną kulturą systemu. Model programowania opartego na zadaniach dla aplikacji przeznaczonych dla wersji .NET Framework wcześniejszych niż .NET Framework 4.6 stosować się do tej praktyką.

> [!IMPORTANT]
> Należy zauważyć, że kultury wątku wywołującego jako część kontekstu zadania mają zastosowanie do aplikacji, *docelowej* programu .NET Framework 4.6, nie aplikacje, *uruchamiana* programu .NET Framework 4.6. Możliwe jest określanie konkretnej wersji programu .NET Framework podczas tworzenia projektu w programie Visual Studio, wybierając tę wersję z listy rozwijanej w górnej części **nowy projekt** okno dialogowe lub poza programem Visual Studio, można użyć <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atrybutu. W przypadku aplikacji, docelowymi są wersje programu .NET Framework wcześniejszych niż .NET Framework 4.6 lub że nie docelowej określonej wersji programu .NET Framework, kultury zadania podrzędnego w dalszym ciągu zależeć od kultury wątku, na którym jest uruchomiony.

Począwszy od aplikacji przeznaczonych na .NET Framework 4.6, kultury wątku wywołującego jest dziedziczona przez każde zadanie podrzędne, nawet wtedy, gdy zadanie jest uruchamiane asynchronicznie na wątku z puli wątków.

W poniższym przykładzie przedstawiono prosty ilustracji. Używa ona <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atrybutu pod kątem programu .NET Framework 4.6 i zmiany bieżącej kultury aplikacji albo francuski (Francja) lub, jeśli francuski (Francja) jest już bieżącej kultury angielski (Stany Zjednoczone). Następnie wywołuje delegata, o nazwie `formatDelegate` zwracającego niektóre numery sformatowane jako wartości waluty w nową kulturą. Należy pamiętać, że czy delegata jako zadanie synchronicznie lub asynchronicznie, zwraca oczekiwany wynik ponieważ kultura wątku wywołującego jest dziedziczona przez zadanie asynchroniczne.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Jeśli używasz programu Visual Studio, można pominąć <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atrybutu, a zamiast tego wybierz pozycję .NET Framework 4.6 jako element docelowy, podczas tworzenia projektu w **nowy projekt** okna dialogowego.

Dla danych wyjściowych, które odzwierciedla zachowanie aplikacji w wersji docelowej programu .NET Framework przed .NET Framework 4.6, Usuń <xref:System.Runtime.Versioning.TargetFrameworkAttribute> atrybutu z kodu źródłowego. Dane wyjściowe odzwierciedlają konwencje formatowania domyślna kultura systemu, nie kultury wątku wywołującego.

Aby uzyskać więcej informacji na temat zadań asynchronicznych i kultury, zobacz sekcję "Kultury i operacje asynchroniczne opartego na zadaniach" w <xref:System.Globalization.CultureInfo> tematu.

## <a name="creating-task-continuations"></a>Tworzenie kontynuacji zadań

<xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> metody umożliwiają określanie zadań do uruchamiania po *zadania poprzedzającego* zakończy się. Delegat zadania kontynuacji jest przekazywany odwołanie do zadania poprzedzającego, dzięki czemu może sprawdzać stan zadania poprzedzającego i, poprzez pobranie wartości <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> , wykorzystywać dane wyjściowe zadania poprzedzającego jako danych wejściowych kontynuacji.

W poniższym przykładzie `getData` zadanie zostało uruchomione przez wywołanie <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> metody. `processData` Zadania jest uruchomiane automatycznie po `getData` zakończy pracę, i `displayData` po uruchomieniu `processData` zakończy się. `getData` generuje tablicę liczb całkowitych, która jest dostępna dla `processData` za pośrednictwem zadań `getData` zadania podrzędnego <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości. `processData` Zadanie przetwarza tę tablicę i zwraca wynik, którego typ jest wnioskowany ze zwracanego typu wyrażenia lambda przekazanego do <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> metody. `displayData` Zadanie podrzędne jest wykonywane automatycznie po `processData` zakończy pracę i <xref:System.Tuple%603> obiektu zwróconego przez `processData` wyrażenia lambda jest dostępny dla `displayData` za pośrednictwem zadań `processData` zadania podrzędnego <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Właściwość. `displayData` Zadanie pobiera wynik `processData` i produkuje wynik, którego typ jest wnioskowany w podobny sposób i który jest udostępniany programowi we <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Ponieważ <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> jest metodą wystąpienia można połączyć w łańcuch wywołań metody zamiast tworzenia wystąpienia <xref:System.Threading.Tasks.Task%601> obiekt dla każdego zadania poprzedzającego. Poniższy przykład jest funkcjonalnie identyczny z poprzednim przykładem, z tą różnicą, że łańcuchy wywołania <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Należy pamiętać, że <xref:System.Threading.Tasks.Task%601> obiekt zwrócony przez łańcuch wywołań metod jest zadaniem końcowym kontynuacji.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

<xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> i <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody umożliwiają kontynuowanie z wielu zadań.

Aby uzyskać więcej informacji, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Tworzenie odłączonych zadań podrzędnych

Gdy kod użytkownika, który jest uruchomiony w zadaniu, tworzy nowe zadanie i nie określa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcji, nowe zadanie nie jest zsynchronizowane z zadaniem nadrzędnym w żaden specjalny sposób. Ten typ niezsynchronizowanego zadania nosi nazwę *odłączone zadanie zagnieżdżone* lub *odłączone zadanie podrzędne*. Poniższy przykład przedstawia zadanie, które tworzy jedno odłączone zadanie podrzędne.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Należy zauważyć, że zadanie nadrzędne nie czeka na zakończenie odłączonego zadania podrzędnego.

## <a name="creating-child-tasks"></a>Tworzenie zadań podrzędnych

Gdy kod użytkownika, który jest uruchomiony w zadaniu, tworzy zadanie z <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcji, nowe zadanie jest znany jako *dołączone zadanie podrzędne* zadania nadrzędnego. Możesz użyć <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcji do wyrażania równoległości zadań strukturalnych, ponieważ zadanie nadrzędne czeka na zakończenie wszystkich zadań dołączonych zadań podrzędnych. Poniższy przykład przedstawia zadanie nadrzędne, które tworzy dziesięć dołączonych zadań podrzędnych. Należy pamiętać, że chociaż w przykładzie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodę, aby czekać na zadanie nadrzędne zakończyć, nie musi jawnie czekać na zakończenie zadań dołączonych zadań podrzędnych.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Zadanie nadrzędne może użyć <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcję, aby uniemożliwić innym zadaniom dołączanie do zadania nadrzędnego. Aby uzyskać więcej informacji, zobacz [dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Oczekiwanie na zakończenie zadań

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typy zapewniają kilka przeciążeń <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody, które umożliwiają czekanie na zakończenie zadania. Ponadto przeciążenia statycznych <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody umożliwiają oczekiwanie poszczególnych lub wszystkich tablicy na zakończenie zadań.

Zazwyczaj użytkownik czeka na zadanie z jednego z poniższych powodów:

- Główny wątek zależy od wyniku końcowego obliczonego przez zadanie.

- Trzeba obsługiwać wyjątki, które mogą być zgłoszone przez zadanie.

- Aplikacja może się zakończyć zanim wszystkie zadania zostaną ukończone. Na przykład aplikacje konsoli zakończą tak szybko, jak cały synchroniczny kod w `Main` zostało wykonane (punkcie wejścia aplikacji).

Poniższy przykład przedstawia podstawowy wzorzec, który nie wymaga obsługi wyjątków.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Na przykład, który przedstawia obsługę wyjątków, zobacz [wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

Niektóre przeciążenia pozwalają określać limit czasu, a inne dodatkowo przejąć <xref:System.Threading.CancellationToken> jako parametr wejściowy, tak aby sam czas oczekiwania mógł być anulowany albo programowo, albo w odpowiedzi na użytkownika dane wejściowe.

Gdy czekasz na zadanie, poczekasz na wszystkie obiekty podrzędne danego zadania, które zostały utworzone przy użyciu <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcji. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> zwraca niezwłocznie, jeśli zadanie zostało już ukończone. Wszelkie wyjątki wywoływane przez zadanie zostaną wyrzucone przez <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody, nawet jeśli <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda została wywołana po ukończeniu zadania.

## <a name="composing-tasks"></a>Tworzenie zadań

<xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> klasy zapewniają kilka metod, które mogą pomóc Ci tworzenie wielu zadań do realizacji typowych wzorców i lepszego wykorzystywania asynchronicznych funkcji języka, które są dostarczane przez C#, Visual Basic i F#. W tej sekcji opisano <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A>, i <xref:System.Threading.Tasks.Task.FromResult%2A> metody.

### <a name="taskwhenall"></a>Task.WhenAll

<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> Metoda asynchronicznie czeka na wiele <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektów, aby zakończyć. Zapewnia przeciążone wersje, które umożliwiają czekanie na niejednolite zestawy zadań. Na przykład, możesz poczekać, aż wielu <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiektów z jednego wywołania metody.

### <a name="taskwhenany"></a>Task.WhenAny

<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> Metoda asynchronicznie czeka na jedno z wielu <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektów, aby zakończyć. Podobnie jak w <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> , ta metoda zapewnia przeciążone wersje, które umożliwiają czekanie na niejednolite zestawy zadań. <xref:System.Threading.Tasks.Task.WhenAny%2A> Metoda jest szczególnie użyteczna w następujących scenariuszach.

- Operacje nadmiarowe. Należy wziąć pod uwagę algorytm lub operację, które mogą być wykonywane na wiele sposobów. Możesz użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metodę, aby wybrać operację, która zakończy się pierwsza, a następnie anulować pozostałe operacje.

- Operacje z przeplotem. Można uruchomić wiele operacji, które muszą się zakończyć i używać <xref:System.Threading.Tasks.Task.WhenAny%2A> metody do przetwarzania wyników, po zakończeniu każdej operacji. Po zakończeniu jednej operacji można uruchomić jedno lub więcej dodatkowych zadań.

- Operacje ograniczane. Możesz użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metodę, aby rozszerzyć poprzedni scenariusz poprzez ograniczenie liczby operacji jednoczesnych.

- Wygasłe operacje. Możesz użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metodę, aby wybrać jedno lub więcej zadań i zadań, który kończy się po określonym czasie, takie jak zadanie zwracane przez <xref:System.Threading.Tasks.Task.Delay%2A> metody. <xref:System.Threading.Tasks.Task.Delay%2A> Metoda została opisana w następnej sekcji.

### <a name="taskdelay"></a>Task.Delay

<xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Metoda <xref:System.Threading.Tasks.Task> obiektu, który kończy się po określonym czasie. Możesz użyć tej metoda do tworzenia pętli, które od czasu do czasu pobierają dane, wprowadzają limity czasu, opóźniają obsługę danych wejściowych użytkownika przez wyznaczony czas i tak dalej.

### <a name="tasktfromresult"></a>Task(T).FromResult

Za pomocą <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody, można utworzyć <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje wstępnie obliczony wynik. Ta metoda jest przydatna, gdy wykonujesz operację asynchroniczną, która zwraca <xref:System.Threading.Tasks.Task%601> obiektu, a wynik tego obiektu <xref:System.Threading.Tasks.Task%601> obiektu jest już obliczony. Aby uzyskać przykład, który używa <xref:System.Threading.Tasks.Task.FromResult%2A> do pobierania wyników asynchronicznych operacji pobrania, które są przechowywane w pamięci podręcznej, zobacz [jak: Tworzenie wstępnie obliczonych zadań](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Obsługa wyjątków w zadaniach

Gdy zadanie wyrzuca jeden lub kilka wyjątków, wyjątki są opakowane w <xref:System.AggregateException> wyjątku. Ten wyjątek jest propagowany z powrotem do wątku, który łączy się z zadaniem, które jest zazwyczaj wątkiem, który oczekuje na zakończenie zadania lub wątkiem, który uzyskuje dostęp do <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości. To zachowanie służy do wymuszania zasady .NET Framework, zgodnie z którą wszystkie nieobsłużone wyjątki powinny domyślnie przerywać proces. Kod wywołujący może obsługiwać wyjątki za pomocą jednej z następujących czynności w `try` / `catch` bloku:

- <xref:System.Threading.Tasks.Task.Wait%2A> — Metoda

- <xref:System.Threading.Tasks.Task.WaitAll%2A> — Metoda

- <xref:System.Threading.Tasks.Task.WaitAny%2A> — Metoda

- <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwości

Przyłączany wątek może również obsługiwać wyjątki, uzyskując dostęp do <xref:System.Threading.Tasks.Task.Exception%2A> właściwości przed usunięciem z zadania zebranych elementów bezużytecznych. Dostęp do tej właściwości zapobiega temu, że nieobsługiwany wyjątek inicjuje zachowanie propagacji wyjątku, które przerywa proces wraz z finalizacją obiektu.

Aby uzyskać więcej informacji dotyczących wyjątków i zadań, zobacz [wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Anulowanie zadania

<xref:System.Threading.Tasks.Task> Klasy obsługuje kooperatywne anulowanie i jest w pełni zintegrowana z <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> i <xref:System.Threading.CancellationToken?displayProperty=nameWithType> klasy, które zostały wprowadzone w programie .NET Framework 4. Wiele konstruktorów w <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> take klasy <xref:System.Threading.CancellationToken> obiekt jako parametr wejściowy. Wiele <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> i <xref:System.Threading.Tasks.Task.Run%2A> przeciążenia również obejmować <xref:System.Threading.CancellationToken> parametru.

Możesz utworzyć token i wydawać żądanie anulowania w późniejszym czasie, przy użyciu <xref:System.Threading.CancellationTokenSource> klasy. Przekaż token do <xref:System.Threading.Tasks.Task> jako argument, a także odwołanie do tego samego tokenu w swoim delegacie użytkownika, który wykonuje pracę odpowiadania na żądanie anulowania.

Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md) i [jak: Anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>Klasa TaskFactory

<xref:System.Threading.Tasks.TaskFactory> Klasa zawiera metody statyczne, które hermetyzują niektóre typowe wzorce do tworzenia i uruchamiania zadań oraz zadań kontynuacji.

- Najczęstszym wzorcem jest <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, który tworzy i uruchamia zadanie w jednej instrukcji.

- Podczas tworzenia zadań kontynuacji z wielu poprzedników, użyj <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> metody lub <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> lub ich odpowiedników w <xref:System.Threading.Tasks.Task%601> klasy. Aby uzyskać więcej informacji, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

- Do hermetyzacji modelu programowania asynchronicznego `BeginX` i `EndX` metody <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> wystąpienia, należy użyć <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Aby uzyskać więcej informacji, zobacz [TPL i tradycyjnym .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).

Wartość domyślna <xref:System.Threading.Tasks.TaskFactory> może być dostępna jako właściwość statyczna w <xref:System.Threading.Tasks.Task> klasy lub <xref:System.Threading.Tasks.Task%601> klasy. Można również utworzyć wystąpienie <xref:System.Threading.Tasks.TaskFactory> bezpośrednio i określić różne opcje, które obejmują <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.TaskCreationOptions> opcji <xref:System.Threading.Tasks.TaskContinuationOptions> opcji lub <xref:System.Threading.Tasks.TaskScheduler>. Niezależnie od opcji określanych podczas tworzenia fabryka zadań zostaną zastosowane do wszystkich zadań, które tworzy, chyba że <xref:System.Threading.Tasks.Task> jest tworzona przy użyciu <xref:System.Threading.Tasks.TaskCreationOptions> wyliczenia, w którym wówczas Opcje zadania zastępują opcje fabryki zadań.

## <a name="tasks-without-delegates"></a>Zadania bez delegatów

W niektórych przypadkach warto użyć <xref:System.Threading.Tasks.Task> do hermetyzacji pewnej operacji asynchronicznej wykonywaną przez składnik zewnętrzny zamiast delegata użytkownika. Jeśli operacja jest oparta na wzorcu asynchronicznego programowania początku/końca modelu, można użyć <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metody. Jeśli nie jest tak, możesz użyć <xref:System.Threading.Tasks.TaskCompletionSource%601> obiekt, aby opakować operację w zadanie co pozwala na uzyskanie niektórych korzyści zapewnianych przez <xref:System.Threading.Tasks.Task> programowania, na przykład obsługi propagacji i kontynuacji wyjątków. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Planiści niestandardowi

Większość deweloperów aplikacji lub biblioteki nie obchodzi, na którym procesorze zadanie będzie uruchamiane, jak synchronizuje swoją pracę z innymi zadaniami lub jak je zaplanowano w <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Wymagają one tylko, aby było wykonane jak najwydajniej na komputerze-hoście. Jeśli potrzebna większa kontrola nad szczegółami planowania, biblioteka zadań równoległych pozwala skonfigurować niektóre ustawienia w domyślnym harmonogramie zadań, a nawet pozwala podać niestandardowy harmonogram. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>Pokrewne struktury danych

TPL ma kilka nowych typów publicznych, które są przydatne w scenariuszach równoległych i sekwencyjnych. Obejmują one kilka klas kolekcji wątkowo, szybkich i skalowalnych przestrzeni <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw oraz kilka nowych typów synchronizacji, na przykład <xref:System.Threading.Semaphore?displayProperty=nameWithType> i <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, które są bardziej wydajne niż ich starsze wersje dla określonych rodzaje obciążeń. Inne nowe typy w .NET Framework 4, na przykład <xref:System.Threading.Barrier?displayProperty=nameWithType> i <xref:System.Threading.SpinLock?displayProperty=nameWithType>, oferują funkcje, które nie były dostępne we wcześniejszych wersjach. Aby uzyskać więcej informacji, zobacz [struktury danych dla programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Niestandardowe typy zadań

Firma Microsoft zaleca, aby nie dziedziczyć z <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Zamiast tego zaleca się używanie <xref:System.Threading.Tasks.Task.AsyncState%2A> właściwości, aby skojarzyć dodatkowe dane lub stan z <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu. Umożliwia także metod rozszerzających do rozszerzenia funkcji <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> klasy. Aby uzyskać więcej informacji dotyczących metod rozszerzających, zobacz [metody rozszerzenia](~/docs/csharp/programming-guide/classes-and-structs/extension-methods.md) i [metody rozszerzenia](~/docs/visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Jeśli trzeba dziedziczyć z <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, nie można użyć <xref:System.Threading.Tasks.Task.Run%2A>, <xref:System.Threading.Tasks.Task.Run%2A>, lub <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>, lub <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> typu klasy, aby utworzyć wystąpienia niestandardowego zadania, ponieważ te mechanizmy tworzą tylko <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> obiektów. Ponadto nie można użyć mechanizmów kontynuacji zadań, które są dostarczane przez <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory>, i <xref:System.Threading.Tasks.TaskFactory%601> do tworzenia wystąpień tego typu niestandardowego zadania, ponieważ te mechanizmy również utworzą tylko <xref:System.Threading.Tasks.Task> i  <xref:System.Threading.Tasks.Task%601> obiektów.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-|-|
|[Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Opisuje, jak działa kontynuacja.|
|[Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Opisano różnicę między zadaniami podrzędnymi dołączonymi i odłączonymi.|
|[Anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md)|W tym artykule opisano obsługę anulowania, która jest wbudowana w <xref:System.Threading.Tasks.Task> obiektu.|
|[Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Opisuje sposób obsługi wyjątków w wątkach współbieżnych.|
|[Instrukcje: Wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Opisuje sposób używania <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|
|[Instrukcje: Zwracanie wartości z zadania](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Zawiera opis sposobu zwracania wartości z zadań.|
|[Instrukcje: Anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Opisuje, jak anulować zadania.|
|[Instrukcje: Tworzenie wstępnie obliczonych zadań](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Opisuje sposób używania <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody do pobierania wyników asynchronicznych operacji pobrania, które są przechowywane w pamięci podręcznej.|
|[Instrukcje: Przenoszenie drzewa binarnego z zadaniami równoległymi](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Opisuje używanie zadań do przechodzenia w drzewie binarnym.|
|[Instrukcje: Dekodowanie zadania zagnieżdżonego](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Pokazuje sposób użycia <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> — metoda rozszerzenia.|
|[Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Opisuje sposób używania <xref:System.Threading.Tasks.Parallel.For%2A> i <xref:System.Threading.Tasks.Parallel.ForEach%2A> do tworzenia pętli równoległych nad danymi.|
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Węzeł najwyższego poziomu dla .NET Framework programowania równoległego.|

## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Przykłady dotyczące programowania równoległego za pomocą programu .NET Framework](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
