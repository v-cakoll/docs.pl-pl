---
title: Asynchroniczne programowanie zadaniowe — .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
ms.openlocfilehash: 51292d977f2be87cec7c3481f5004fe5fe756224
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74204544"
---
# <a name="task-based-asynchronous-programming"></a>Asynchroniczne programowanie zadaniowe

Biblioteka równoległa zadania (TPL) opiera się na koncepcji *zadania,* które reprezentuje operację asynchroniczną. W pewnym sensie zadanie przypomina wątek <xref:System.Threading.ThreadPool> lub element pracy, ale na wyższym poziomie abstrakcji. Termin *równoległość zadania* odnosi się do jednego lub więcej niezależnych zadań uruchomionych jednocześnie. Zadania zapewniają dwie podstawowe korzyści:

- Efektywniejsze i bardziej skalowalne wykorzystanie zasobów systemowych.

     W tle zadania są umieszczane <xref:System.Threading.ThreadPool>w kolejce do , który został wzbogacony o algorytmy, które określają i dostosowują się do liczby wątków i zapewniają równoważenie obciążenia w celu zmaksymalizowania przepływretu. Dzięki temu zadania są stosunkowo lekkie i można tworzyć wiele takich zadań, aby włączyć równoległość drobnoziarnistą.

- Większa kontrola programistyczna niż jest to możliwe za pomocą wątku lub elementu roboczego.

     Zadania i środowisko zbudowane wokół nich zawierają bogaty zestaw interfejsów API, które obsługują oczekiwanie, anulowanie, kontynuację, niezawodną obsługę wyjątków, szczegółowe informacje o stanie, planowanie niestandardowe i nie tylko.

Dla obu tych powodów w .NET Framework TPL jest preferowanym interfejsem API do pisania kodu wielowątkowego, asynchronicznego i równoległego.

## <a name="creating-and-running-tasks-implicitly"></a>Tworzenie i uruchamianie zadań niejawnie

Metoda <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> zapewnia wygodny sposób uruchamiania dowolnej liczby dowolnych instrukcji jednocześnie. Wystarczy przekazać <xref:System.Action> pełnomocnika dla każdego elementu pracy. Wyrażenia lambda są najwygodniejszym sposobem na tworzenie tych delegatów. Wyrażenie lambda może wywołać metodę nazwaną lub zapewnić kod inline. W poniższym przykładzie <xref:System.Threading.Tasks.Parallel.Invoke%2A> przedstawiono podstawowe wywołanie, które tworzy i uruchamia dwa zadania, które są uruchamiane jednocześnie. Pierwsze zadanie jest reprezentowane przez wyrażenie lambda, `DoSomeWork`które wywołuje metodę o nazwie , a drugie zadanie jest `DoSomeOtherWork`reprezentowane przez wyrażenie lambda, które wywołuje metodę o nazwie .

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Liczba <xref:System.Threading.Tasks.Task> wystąpień, które są tworzone za <xref:System.Threading.Tasks.Parallel.Invoke%2A> kulisami przez nie musi równa się liczbę delegatów, które są dostarczane. TPL może wykorzystywać różne optymalizacje, zwłaszcza z dużą liczbą obiektów delegowanych.

Aby uzyskać więcej informacji, zobacz [Jak: Użyj Parallel.Invoke do wykonywania operacji równoległych](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Aby uzyskać większą kontrolę nad wykonaniem zadania lub zwrócić <xref:System.Threading.Tasks.Task> wartość z zadania, należy pracować z obiektami bardziej jawnie.

## <a name="creating-and-running-tasks-explicitly"></a>Jawne tworzenie i uruchamianie zadań

Zadanie, które nie zwraca wartość jest <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> reprezentowana przez klasę. Zadanie, które zwraca wartość jest <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> reprezentowana przez klasę, która dziedziczy z <xref:System.Threading.Tasks.Task>. Obiekt zadania obsługuje szczegóły infrastruktury i zapewnia metody i właściwości, które są dostępne z wątku wywoływania przez cały okres istnienia zadania. Na przykład można uzyskać <xref:System.Threading.Tasks.Task.Status%2A> dostęp do właściwości zadania w dowolnym momencie, aby ustalić, czy został uruchomiony, uruchomiony do zakończenia, został anulowany lub został zgłoszony wyjątek. Stan jest reprezentowany przez <xref:System.Threading.Tasks.TaskStatus> wyliczenie.

Tworząc zadanie, nadajesz mu delegata użytkownika hermetyzującego kod, który zadanie będzie wykonywało. Delegat może być wyrażony jako delegat nazwany, metoda anonimowa lub wyrażenie lambda. Wyrażenia lambda mogą zawierać wywołanie metody nazwanej, jak pokazano w następującym przykładzie. Należy zauważyć, że w <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> przykładzie znajduje się wywołanie metody, aby upewnić się, że zadanie kończy wykonywanie przed zakończeniem aplikacji trybu konsoli.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Można również użyć <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metod do tworzenia i uruchamiania zadania w jednej operacji. Aby zarządzać zadaniem, <xref:System.Threading.Tasks.Task.Run%2A> metody używają domyślnego harmonogramu zadań, niezależnie od tego, który harmonogram zadań jest skojarzony z bieżącym wątkiem. Metody <xref:System.Threading.Tasks.Task.Run%2A> są preferowanym sposobem tworzenia i uruchamiania zadań, gdy nie jest potrzebna większa kontrola nad tworzeniem i planowaniem zadania.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Można również użyć <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody do tworzenia i uruchamiania zadania w jednej operacji. Tej metody należy użyć, gdy tworzenie i planowanie nie muszą być oddzielone i wymagane są dodatkowe opcje tworzenia zadań lub użycie określonego harmonogramu <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> lub gdy trzeba przekazać dodatkowy stan do zadania, które można pobrać za pośrednictwem jego właściwości, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task>i <xref:System.Threading.Tasks.Task%601> każdy uwidacznia statyczną <xref:System.Threading.Tasks.Task.Factory%2A> właściwość, która zwraca domyślne wystąpienie <xref:System.Threading.Tasks.TaskFactory>, dzięki czemu można wywołać metodę jako `Task.Factory.StartNew()`. Ponadto w poniższym przykładzie, ponieważ zadania <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>są typu , <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> każdy z nich ma właściwość publiczną, która zawiera wynik obliczeń. Zadania są wykonywane asynchroniczne i mogą być kończone w dowolnej kolejności. Jeśli <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość jest dostępna przed zakończeniem obliczeń, właściwość blokuje wątek wywołujący, dopóki wartość jest dostępna.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Aby uzyskać więcej informacji, zobacz [Jak: Zwracać wartość z zadania](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Używając wyrażenia lambda do utworzenia delegata, masz dostęp do wszystkich zmiennych, które są widoczne w tym momencie w kodzie źródłowym. Jednak w niektórych przypadkach, zwłaszcza w pętlach, lambda nie przechwytuje zmiennej zgodnie z oczekiwaniami. Przechwytuje tylko wartość końcową, a nie wartość, która mutuje po każdej iteracji. Poniższy przykład ilustruje ten problem. Przekazuje licznik pętli do wyrażenia lambda, który `CustomData` tworzy obiekt i używa licznika pętli jako identyfikator obiektu. Jak pokazuje dane wyjściowe z `CustomData` przykładu, każdy obiekt ma identyczny identyfikator.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

Możesz uzyskać dostęp do wartości w każdej iteracji poprzez zapewnienie obiektu stanu do zadania za pośrednictwem jej konstruktora. Poniższy przykład modyfikuje poprzedni przykład za pomocą licznika pętli podczas tworzenia `CustomData` obiektu, który z kolei jest przekazywany do wyrażenia lambda.  Jak wynika z przykładu, `CustomData` każdy obiekt ma teraz unikatowy identyfikator oparty na wartości licznika pętli w momencie utworzenia obiektu.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Ten stan jest przekazywany jako argument do delegata zadania i można uzyskać <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> do niego dostęp z obiektu zadania przy użyciu właściwości.  Poniższy przykład jest modyfikacją poprzedniego. Używa <xref:System.Threading.Tasks.Task.AsyncState%2A> właściwości do wyświetlania `CustomData` informacji o obiektach przekazanych do wyrażenia lambda.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>Identyfikator zadania

Każde zadanie otrzymuje identyfikator liczby całkowitej, który jednoznacznie identyfikuje go w domenie <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> aplikacji i jest dostępny przy użyciu właściwości. Identyfikator jest przydatny do wyświetlania informacji o zadaniach w **oknach debugerów równoległych programu** Visual Studio i **zadania.** Identyfikator jest tworzony z opóźnieniem, co oznacza, że nie jest on tworzony do momentu pojawienia się stosownego żądania. Dlatego zadanie może mieć inny identyfikator za każdym razem, gdy program jest uruchamiany. Aby uzyskać więcej informacji na temat wyświetlania identyfikatorów zadań w debugerze, zobacz [Korzystanie z okna Zadania](/visualstudio/debugger/using-the-tasks-window) i korzystanie z okna [Stosy równoległe](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Opcje tworzenia zadań

Większość interfejsów API, które tworzą <xref:System.Threading.Tasks.TaskCreationOptions> zadania zapewniają przeciążenia, które akceptują parametr. Określając jedną z poniższych opcji, możesz wskazać harmonogramowi zadań, jak zaplanować zadanie w puli wątków. Poniższa tabela zawiera różne opcje tworzenia zadania.

|<xref:System.Threading.Tasks.TaskCreationOptions>wartość parametru|Opis|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Domyślna, gdy nie określono żadnej opcji. Harmonogram używa domyślnej heurystyki do zaplanowania zadania.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Określa, że zadanie powinno zostać zaplanowane tak, aby zadania utworzone wcześniej były wykonywane wcześniej, a zadania utworzone później były wykonywane później.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Określa, że zadanie reprezentuje operację długotrwałą.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Określa, że zadanie powinno zostać utworzone jako dołączone zadanie podrzędne do bieżącego zadania, jeśli takie istnieje. Aby uzyskać więcej informacji, zobacz [Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Określa, że jeśli zadanie wewnętrzne `AttachedToParent` określa opcję, to zadanie nie stanie się dołączonym zadaniem podrzędnym.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Określa, że harmonogram zadań utworzonych przez metody <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> wywołujące, takie jak lub <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> z określonego zadania, jest domyślnym harmonogramem zamiast harmonogramu, na którym jest uruchomione to zadanie.|

Opcje mogą być łączone za pomocą operacji bitowej **LUB.** W poniższym przykładzie przedstawiono <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> zadanie, które ma i <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> opcji.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Zadania, wątki i kultura

Każdy wątek ma skojarzoną kulturę i kulturę interfejsu użytkownika, która jest definiowana odpowiednio przez <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości i <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> właściwości. Kultura wątku jest używana w takich operacjach, jak formatowanie, analizowanie, sortowanie i porównywanie ciągów. Kultury interfejsu użytkownika wątku jest używany w wyszukiwania zasobów. Zwykle, chyba że określisz domyślną kulturę dla wszystkich wątków <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> w <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> domenie aplikacji przy użyciu i właściwości, kultury domyślnej i kultury interfejsu użytkownika wątku jest zdefiniowany przez kulturę systemu. Jeśli jawnie ustawisz kultury wątku i uruchomić nowy wątek, nowy wątek nie dziedziczy kultury wątku wywołującego; Zamiast tego jego kultura jest domyślną kulturą systemu. Model programowania oparty na zadaniach dla aplikacji, które są przeznaczone dla wersji programu .NET Framework przed .NET Framework 4.6 stosować się do tej praktyki.

> [!IMPORTANT]
> Należy zauważyć, że kultura wątku wywołującego jako część kontekstu zadania ma zastosowanie do aplikacji, które *są przeznaczone dla* .NET Framework 4.6, a nie aplikacje, które są *uruchamiane w ramach* .NET Framework 4.6. Podczas tworzenia projektu w programie Visual Studio można kierować reklamy na określoną wersję programu .NET Framework, wybierając tę wersję z listy rozwijanej u <xref:System.Runtime.Versioning.TargetFrameworkAttribute> góry okna dialogowego Nowy **projekt** lub poza nim, można użyć tego atrybutu. W przypadku aplikacji, które są przeznaczone dla wersji programu .NET Framework przed .NET Framework 4.6 lub które nie są przeznaczone dla określonej wersji programu .NET Framework, kultura zadania jest nadal określana przez kulturę wątku, na którym jest uruchamiany.

Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6, kultury wątku wywołującego jest dziedziczona przez każde zadanie, nawet jeśli zadanie jest uruchamiane asynchronicznie na wątku puli wątków.

Poniższy przykład zawiera prostą ilustrację. Używa atrybutu <xref:System.Runtime.Versioning.TargetFrameworkAttribute> do docelowego .NET Framework 4.6 i zmienia bieżącą kulturę aplikacji na francuski (Francja) lub, jeśli francuski (Francja) jest już bieżącą kulturą, angielski (Stany Zjednoczone). Następnie wywołuje delegata o `formatDelegate` nazwie, który zwraca niektóre liczby sformatowane jako wartości waluty w nowej kulturze. Należy zauważyć, że niezależnie od tego, czy pełnomocnik jako zadanie synchronicznie lub asynchronicznie zwraca oczekiwany wynik, ponieważ kultura wątku wywołującego jest dziedziczona przez zadanie asynchroniczne.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Jeśli używasz programu Visual Studio, można <xref:System.Runtime.Versioning.TargetFrameworkAttribute> pominąć atrybut i zamiast tego wybierz .NET Framework 4.6 jako miejsce docelowe podczas tworzenia projektu w oknie dialogowym **Nowy projekt.**

W przypadku danych wyjściowych, które odzwierciedla zachowanie aplikacji docelowych wersji .NET Framework <xref:System.Runtime.Versioning.TargetFrameworkAttribute> przed .NET Framework 4.6, usuń atrybut z kodu źródłowego. Dane wyjściowe będą odzwierciedlać konwencje formatowania domyślnej kultury systemu, a nie kultury wątku wywołującego.

Aby uzyskać więcej informacji na temat zadań asynchronicznych i kultury, zobacz sekcję "Operacje kulturowe i asynchroniczne operacje oparte na zadaniach" w temacie. <xref:System.Globalization.CultureInfo>

## <a name="creating-task-continuations"></a>Tworzenie kontynuacji zadań

Metody <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> i umożliwiają określenie zadania, które ma zostać zakończone po zakończeniu *zadania poprzednika.* Delegat zadania kontynuacji jest przekazywany odwołanie do poprzedzającego zadania, dzięki czemu można zbadać stan poprzedzającego <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> zadania i, pobierając wartość właściwości, można użyć danych wyjściowych poprzednika jako dane wejściowe dla kontynuacji.

W poniższym `getData` przykładzie zadanie jest uruchamiane <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> przez wywołanie metody. Zadanie `processData` jest uruchamiane `getData` automatycznie po `displayData` zakończeniu i `processData` jest uruchamiane po zakończeniu. `getData`tworzy tablicę całkowitą, która jest `processData` dostępna dla `getData` zadania <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> za pośrednictwem właściwości zadania. Task `processData` przetwarza, że tablica i zwraca wynik, którego typ jest wywnioskowany <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> z typu zwracanego wyrażenia lambda przekazywane do metody. Zadanie `displayData` jest wykonywane automatycznie `processData` po zakończeniu, <xref:System.Tuple%603> a obiekt `processData` zwrócony przez wyrażenie lambda jest dostępny dla `displayData` zadania za pośrednictwem `processData` <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości zadania. Zadanie `displayData` przyjmuje wynik `processData` zadania i generuje wynik, którego typ jest wywnioskowany w podobny sposób i <xref:System.Threading.Tasks.Task%601.Result%2A> który jest udostępniany programowi we właściwości.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Ponieważ <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> jest metodą wystąpienia, można połączyć wywołania metody łańcuchowej razem zamiast tworzenia wystąpienia <xref:System.Threading.Tasks.Task%601> obiektu dla każdego zadania poprzednika. Poniższy przykład jest funkcjonalnie identyczny z poprzednim przykładem, z <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> tą różnicą, że łączy wywołania metody. Należy zauważyć, że <xref:System.Threading.Tasks.Task%601> obiekt zwracany przez łańcuch wywołań metody jest zadaniem kontynuacji końcowej.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

Metody <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> i umożliwiają kontynuowanie z wielu zadań.

Aby uzyskać więcej informacji, zobacz [Łączenie zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Tworzenie odłączonych zadań podrzędnych

Gdy kod użytkownika uruchomiony w zadaniu tworzy nowe zadanie <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> i nie określa opcji, nowe zadanie nie jest synchronizowane z zadaniem nadrzędnym w żaden specjalny sposób. Ten typ niezsynchronizowanego zadania jest nazywany *odłączonym zadaniem zagnieżdżonym* lub *odłączonym zadaniem podrzędnym*. Poniższy przykład przedstawia zadanie, które tworzy jedno odłączone zadanie podrzędne.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Należy zauważyć, że zadanie nadrzędne nie czeka na zakończenie odłączonego zadania podrzędnego.

## <a name="creating-child-tasks"></a>Tworzenie zadań podrzędne

Gdy kod użytkownika uruchomiony w zadaniu tworzy <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> zadanie z opcją, nowe zadanie jest znane jako *dołączone zadanie podrzędne* zadania nadrzędnego. Opcji można <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> użyć do wyrażenia ustrukturyzowanego równoległości zadań, ponieważ zadanie nadrzędne niejawnie czeka na zakończenie wszystkich dołączonych zadań podrzędnych. Poniższy przykład przedstawia zadanie nadrzędne, które tworzy dziesięć dołączonych zadań podrzędnych. Należy zauważyć, że <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> chociaż w przykładzie wywołuje metodę oczekiwania na zakończenie zadania nadrzędnego, nie trzeba jawnie czekać na dołączone zadania podrzędne do wykonania.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Zadanie nadrzędne można <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> użyć opcji, aby zapobiec dołączania innych zadań do zadania nadrzędnego. Aby uzyskać więcej informacji, zobacz [Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Oczekiwanie na zakończenie zadań

I <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typy zapewniają kilka przeciążeń <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metod, które umożliwiają oczekiwanie na zakończenie zadania. Ponadto przeciążenia statyczne <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> metody pozwalają czekać na dowolne lub wszystkie tablicy zadań, aby zakończyć.

Zazwyczaj użytkownik czeka na zadanie z jednego z poniższych powodów:

- Główny wątek zależy od wyniku końcowego obliczonego przez zadanie.

- Trzeba obsługiwać wyjątki, które mogą być zgłoszone przez zadanie.

- Aplikacja może się zakończyć zanim wszystkie zadania zostaną ukończone. Na przykład aplikacje konsoli zakończy się natychmiast po `Main` wykonaniu całego kodu synchronicznego w (punkt wejścia aplikacji).

Poniższy przykład przedstawia podstawowy wzorzec, który nie wymaga obsługi wyjątków.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Na przykład, który pokazuje obsługę wyjątków, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

Niektóre przeciążenia pozwalają określić przekroczenie limitu czasu, a inne mają dodatkowe <xref:System.Threading.CancellationToken> jako parametr wejściowy, dzięki czemu samo oczekiwanie może zostać anulowane programowo lub w odpowiedzi na dane wejściowe użytkownika.

Podczas oczekiwania na zadanie, niejawnie czekać na wszystkie elementy podrzędne <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> tego zadania, które zostały utworzone przy użyciu tej opcji. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>zwraca natychmiast, jeśli zadanie zostało już ukończone. Wszelkie wyjątki wywoływane przez zadanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> zostaną wygenerowane <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> przez metodę, nawet jeśli metoda została wywołana po zakończeniu zadania.

## <a name="composing-tasks"></a>Redagowanie zadań

I <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> klasy zapewniają kilka metod, które mogą pomóc w redagowaniu wielu zadań w celu zaimplementowania typowych wzorców i lepszego korzystania z funkcji języka asynchronicznego, które są dostarczane przez C#, Visual Basic i F#. W tej <xref:System.Threading.Tasks.Task.WhenAll%2A>sekcji <xref:System.Threading.Tasks.Task.WhenAny%2A> <xref:System.Threading.Tasks.Task.Delay%2A>opisano <xref:System.Threading.Tasks.Task.FromResult%2A> metody , , i metody.

### <a name="taskwhenall"></a>Task.WhenAll

Metoda <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> asynchronicznie czeka na <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> wiele lub obiektów do zakończenia. Zapewnia przeciążone wersje, które umożliwiają czekanie na niejednolite zestawy zadań. Na przykład można czekać <xref:System.Threading.Tasks.Task> na <xref:System.Threading.Tasks.Task%601> wiele i obiektów, aby zakończyć z jednej metody wywołania.

### <a name="taskwhenany"></a>Task.WhenAny

Metoda <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> asynchronicznie czeka na jeden <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> z wielu lub obiektów, aby zakończyć. Podobnie jak <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> w metodzie, ta metoda zawiera przeciążone wersje, które umożliwiają oczekiwanie na niejednolite zestawy zadań. Metoda <xref:System.Threading.Tasks.Task.WhenAny%2A> jest szczególnie przydatna w następujących scenariuszach.

- Operacje nadmiarowe. Należy wziąć pod uwagę algorytm lub operację, które mogą być wykonywane na wiele sposobów. Można użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> metody, aby wybrać operację, która kończy się jako pierwsza, a następnie anulować pozostałe operacje.

- Operacje z przeplotem. Można uruchomić wiele operacji, które muszą <xref:System.Threading.Tasks.Task.WhenAny%2A> zakończyć i użyć metody do przetwarzania wyników, jak każda operacja kończy. Po zakończeniu jednej operacji można uruchomić jedno lub więcej dodatkowych zadań.

- Operacje ograniczane. Metoda służy <xref:System.Threading.Tasks.Task.WhenAny%2A> do rozszerzenia poprzedniego scenariusza, ograniczając liczbę równoczesnych operacji.

- Wygasłe operacje. Metoda służy <xref:System.Threading.Tasks.Task.WhenAny%2A> do wybierania między jednym lub więcej zadań i zadania, które kończy się po określonym <xref:System.Threading.Tasks.Task.Delay%2A> czasie, takich jak zadanie, które jest zwracane przez metodę. Metoda <xref:System.Threading.Tasks.Task.Delay%2A> jest opisana w poniższej sekcji.

### <a name="taskdelay"></a>Task.Delay

Metoda <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> tworzy <xref:System.Threading.Tasks.Task> obiekt, który kończy się po określonym czasie. Możesz użyć tej metoda do tworzenia pętli, które od czasu do czasu pobierają dane, wprowadzają limity czasu, opóźniają obsługę danych wejściowych użytkownika przez wyznaczony czas i tak dalej.

### <a name="tasktfromresult"></a>Task(T).FromResult

Za pomocą <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody, można <xref:System.Threading.Tasks.Task%601> utworzyć obiekt, który zawiera wstępnie obliczony wynik. Ta metoda jest przydatna podczas wykonywania operacji <xref:System.Threading.Tasks.Task%601> asynchronicznej, która <xref:System.Threading.Tasks.Task%601> zwraca obiekt, a wynik tego obiektu jest już obliczany. Na przykład, <xref:System.Threading.Tasks.Task.FromResult%2A> który używa do pobierania wyników operacji pobierania asynchronicznego, które są przechowywane w pamięci podręcznej, zobacz [Jak: Tworzenie zadań wstępnie obliczonych](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Obsługa wyjątków w zadaniach

Gdy zadanie zgłasza jeden lub więcej wyjątków, wyjątki <xref:System.AggregateException> są opakowane w wyjątek. Ten wyjątek jest propagowany z powrotem do wątku, który łączy się z zadaniem, który jest zazwyczaj <xref:System.Threading.Tasks.Task%601.Result%2A> wątek, który oczekuje na zakończenie zadania lub wątku, który uzyskuje dostęp do właściwości. To zachowanie służy do wymuszania zasady .NET Framework, zgodnie z którą wszystkie nieobsłużone wyjątki powinny domyślnie przerywać proces. Kod wywołujący może obsługiwać wyjątki przy użyciu `try` / `catch` dowolnej z następujących czynności w bloku:

- Metoda <xref:System.Threading.Tasks.Task.Wait%2A>

- Metoda <xref:System.Threading.Tasks.Task.WaitAll%2A>

- Metoda <xref:System.Threading.Tasks.Task.WaitAny%2A>

- Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A>

Wątek łączenia może również obsługiwać wyjątki, uzyskując dostęp do <xref:System.Threading.Tasks.Task.Exception%2A> właściwości, zanim zadanie jest zbierane bezużyteczno. Dostęp do tej właściwości zapobiega temu, że nieobsługiwany wyjątek inicjuje zachowanie propagacji wyjątku, które przerywa proces wraz z finalizacją obiektu.

Aby uzyskać więcej informacji na temat wyjątków i zadań, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Anulowanie zadań

Klasa <xref:System.Threading.Tasks.Task> obsługuje anulowanie współpracy i <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> jest <xref:System.Threading.CancellationToken?displayProperty=nameWithType> w pełni zintegrowany z klas i, które zostały wprowadzone w .NET Framework 4. Wiele konstruktorów w <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klasie <xref:System.Threading.CancellationToken> wziąć obiekt jako parametr wejściowy. Wiele <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> i <xref:System.Threading.Tasks.Task.Run%2A> przeciążenia również <xref:System.Threading.CancellationToken> parametr.

Można utworzyć token i wydać żądanie anulowania w późniejszym <xref:System.Threading.CancellationTokenSource> czasie, przy użyciu klasy. Przekazać token <xref:System.Threading.Tasks.Task> do argumentu jako, a także odwołać się do tego samego tokenu w pełnomocnika użytkownika, który wykonuje pracę odpowiadania na żądanie anulowania.

Aby uzyskać więcej informacji, zobacz [Anulowanie zadań](../../../docs/standard/parallel-programming/task-cancellation.md) i [jak: Anulowanie zadania i jego dzieci](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>Klasa TaskFactory

Klasa <xref:System.Threading.Tasks.TaskFactory> zawiera metody statyczne, które hermetyzują niektóre typowe wzorce do tworzenia i uruchamiania zadań i zadań kontynuacji.

- Najczęstszym wzorcem jest <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, który tworzy i uruchamia zadanie w jednej instrukcji.

- Podczas tworzenia zadań kontynuacji z wielu poprzedników, należy użyć <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> metody lub <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody lub ich odpowiedniki w <xref:System.Threading.Tasks.Task%601> klasie. Aby uzyskać więcej informacji, zobacz [Łączenie zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

- Aby hermetyzować asynchroniczny `BeginX` `EndX` model programowania <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601> metody w <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> lub wystąpienia, należy użyć metod. Aby uzyskać więcej informacji, zobacz [TPL i tradycyjne programowanie asynchroniczne .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).

Domyślnie <xref:System.Threading.Tasks.TaskFactory> jest dostępny jako właściwość statyczna <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> w klasie lub klasie. Można również utworzyć wystąpienia <xref:System.Threading.Tasks.TaskFactory> bezpośrednio i określić różne <xref:System.Threading.CancellationToken>opcje, <xref:System.Threading.Tasks.TaskCreationOptions> które <xref:System.Threading.Tasks.TaskContinuationOptions> zawierają , <xref:System.Threading.Tasks.TaskScheduler>opcja, opcja lub . Niezależnie od opcji są określone podczas tworzenia fabryki zadań zostaną zastosowane do <xref:System.Threading.Tasks.Task> wszystkich zadań, które <xref:System.Threading.Tasks.TaskCreationOptions> tworzy, chyba że jest tworzony przy użyciu wyliczenia, w którym to przypadku opcje zadania zastąpić te fabryki zadań.

## <a name="tasks-without-delegates"></a>Zadania bez delegatów

W niektórych przypadkach można użyć <xref:System.Threading.Tasks.Task> do hermetyzacji niektórych operacji asynchronicznych, która jest wykonywana przez składnik zewnętrzny zamiast własnego delegata użytkownika. Jeśli operacja jest oparta na wzorcu Początku/Zakończenia modelu programowania asynchronicznego, można użyć <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> tych metod. Jeśli tak nie jest, można <xref:System.Threading.Tasks.TaskCompletionSource%601> użyć obiektu do zawijania operacji w <xref:System.Threading.Tasks.Task> zadaniu, a tym samym uzyskać niektóre korzyści z programowalności, na przykład wsparcie dla propagacji wyjątków i kontynuacji. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Harmonogramy niestandardowe

Większość deweloperów aplikacji lub biblioteki nie obchodzi, który procesor zadanie działa na, jak synchronizuje <xref:System.Threading.ThreadPool?displayProperty=nameWithType>swoją pracę z innymi zadaniami, lub jak jest zaplanowane na . Wymagają one tylko, aby było wykonane jak najwydajniej na komputerze-hoście. Jeśli potrzebna większa kontrola nad szczegółami planowania, biblioteka zadań równoległych pozwala skonfigurować niektóre ustawienia w domyślnym harmonogramie zadań, a nawet pozwala podać niestandardowy harmonogram. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>Powiązane struktury danych

TPL ma kilka nowych typów publicznych, które są przydatne w scenariuszach równoległych i sekwencyjnych. Należą do nich kilka klas kolekcji bezpieczne dla <xref:System.Collections.Concurrent?displayProperty=nameWithType> wątków, szybkie i skalowalne w <xref:System.Threading.Semaphore?displayProperty=nameWithType> <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>obszarze nazw i kilka nowych typów synchronizacji, na przykład i , które są bardziej wydajne niż ich poprzedników dla określonych rodzajów obciążeń. Inne nowe typy w .NET Framework <xref:System.Threading.Barrier?displayProperty=nameWithType> 4, na przykład i <xref:System.Threading.SpinLock?displayProperty=nameWithType>, zapewniają funkcje, które nie były dostępne we wcześniejszych wersjach. Aby uzyskać więcej informacji, zobacz [Struktury danych dla programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Niestandardowe typy zadań

Zaleca się, aby nie <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>dziedziczyć z lub . Zamiast tego zaleca się <xref:System.Threading.Tasks.Task.AsyncState%2A> użyć właściwości do skojarzenia <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> dodatkowych danych lub stanu z lub obiektu. Można również użyć metod rozszerzenia, aby rozszerzyć <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> funkcjonalność i klas. Aby uzyskać więcej informacji na temat metod rozszerzenia, zobacz [Metody rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) i [metody rozszerzenia](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Jeśli musisz dziedziczyć lub <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>nie <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>można <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> użyć <xref:System.Threading.Tasks.Task.Run%2A>, lub , , lub klas <xref:System.Threading.Tasks.Task> do <xref:System.Threading.Tasks.Task%601> tworzenia wystąpień niestandardowego typu zadania, ponieważ te mechanizmy tworzą tylko i obiekty. Ponadto nie można używać mechanizmów kontynuacji <xref:System.Threading.Tasks.Task>zadań, <xref:System.Threading.Tasks.TaskFactory>które <xref:System.Threading.Tasks.TaskFactory%601> są dostarczane przez , <xref:System.Threading.Tasks.Task%601>, i do <xref:System.Threading.Tasks.Task> tworzenia <xref:System.Threading.Tasks.Task%601> wystąpień niestandardowego typu zadania, ponieważ mechanizmy te również utworzyć tylko i obiekty.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-|-|
|[Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Opisuje, jak działa kontynuacja.|
|[Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Opisano różnicę między zadaniami podrzędnymi dołączonymi i odłączonymi.|
|[Anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md)|Opisuje obsługę anulowania, który <xref:System.Threading.Tasks.Task> jest wbudowany w obiekcie.|
|[Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Opisuje sposób obsługi wyjątków w wątkach współbieżnych.|
|[Jak: Użyj Parallel.Invoke do wykonywania operacji równoległych](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Opisuje sposób <xref:System.Threading.Tasks.Parallel.Invoke%2A>używania .|
|[Porady: zwracanie wartości z zadania](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Zawiera opis sposobu zwracania wartości z zadań.|
|[Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Opisuje, jak anulować zadania.|
|[Instrukcje: tworzenie wstępnie obliczonych zadań](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|W tym artykule <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> opisano, jak używać metody do pobierania wyników operacji pobierania asynchronicznego, które są przechowywane w pamięci podręcznej.|
|[Instrukcje: przenoszenie drzewa binarnego z zadaniami równoległymi](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Opisuje używanie zadań do przechodzenia w drzewie binarnym.|
|[Instrukcje: odpakowywanie zadania zagnieżdżonego](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Pokazuje, jak używać <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> metody rozszerzenia.|
|[Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Opisuje sposób <xref:System.Threading.Tasks.Parallel.For%2A> używania <xref:System.Threading.Tasks.Parallel.ForEach%2A> i tworzenia pętli równoległych nad danymi.|
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Węzeł najwyższego poziomu dla .NET Framework programowania równoległego.|

## <a name="see-also"></a>Zobacz też

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Przykłady do programowania równoległego z platformą .NET Framework](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
