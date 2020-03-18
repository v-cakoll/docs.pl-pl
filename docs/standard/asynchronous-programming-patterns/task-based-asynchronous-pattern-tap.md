---
title: Wzorzec asynchroniczny oparty na zadaniach (TAP)
ms.date: 02/26/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 8cef1fcf-6f9f-417c-b21f-3fd8bac75007
ms.openlocfilehash: 89c486618729c334bf74f0a1f4f9dd1b3cee8b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78158171"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Asynchroniczny wzorzec oparty na zadaniach (TAP)
Wzorzec asynchroniczny (TAP) oparty <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> na <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> zadaniach <xref:System.Threading.Tasks?displayProperty=nameWithType> jest oparty na typach i typach w przestrzeni nazw, które są używane do reprezentowania dowolnych operacji asynchronicznych. Wzorzec TAP jest zalecanym asynchronicznym wzorcem projektowym dla nowych prac deweloperskich.  
  
## <a name="naming-parameters-and-return-types"></a>Nazewnictwo, parametry i typy zwracane

We wzorcu TAP do tworzenia wystąpienia i wykonywania operacji asynchronicznej jest używana jedna metoda. Kontrastuje to zarówno ze wzorem Asynchronicznego modelu `IAsyncResult`programowania (APM lub) oraz wzorcem asynchronicznym opartym na zdarzeniach (EAP). APM `Begin` wymaga `End` i metod. EAP wymaga metody, `Async` która ma sufiks, a także wymaga jednego `EventArg`lub więcej zdarzeń, typy delegatów obsługi zdarzeń i typy pochodne. Metody asynchroniczne w tap `Async` obejmują sufiks po nazwie operacji dla metod, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>które <xref:System.Threading.Tasks.ValueTask>zwracają <xref:System.Threading.Tasks.ValueTask%601>typy oczekujące, takie jak , , , i . Na przykład operacja `Get` asynchroniczna, `Task<String>` która `GetAsync`zwraca a może mieć nazwę . Jeśli dodajesz metodę TAP do klasy, która już zawiera `Async` nazwę metody EAP z `TaskAsync` sufiksem, użyj zamiast tego sufiksu. Na przykład jeśli klasa ma `GetAsync` już metodę, `GetTaskAsync`użyj nazwy . Jeśli metoda uruchamia operację asynchroniczną, ale nie zwraca typu oczekującego, jej nazwa powinna zaczynać się od `Begin`, `Start`lub innego zlecenia sugerującego, że ta metoda nie zwraca lub nie zgłasza wyniku operacji.  
  
 Metoda TAP zwraca <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>lub a , na podstawie tego, czy `TResult`odpowiednia metoda synchroniczna zwraca void, czy typ .  
  
 Parametry metody TAP powinny być zgodne z parametrami jej synchronicznego odpowiednika i powinny być podane w tej samej kolejności.  Jednak `out` parametry `ref` są wyłączone z tej reguły i należy unikać całkowicie. Wszelkie dane, które zostałyby `out` zwrócone za pośrednictwem lub `ref` parametru powinny być zwracane jako część `TResult` zwracane przez <xref:System.Threading.Tasks.Task%601>, i należy użyć krotki lub niestandardowej struktury danych, aby pomieścić wiele wartości. Należy również rozważyć <xref:System.Threading.CancellationToken> dodanie parametru, nawet jeśli synchroniczny odpowiednik metody TAP nie oferuje jeden.

 Metody, które są przeznaczone wyłącznie do tworzenia, manipulacji lub kombinacji zadań (gdzie asynchroniczne intencji metody jest jasne w nazwie metody lub w nazwie typu, do którego należy metoda) nie muszą przestrzegać tego wzorca nazewnictwa; takie metody są często określane jako *kombinatory*. Przykłady kombinatorów obejmują <xref:System.Threading.Tasks.Task.WhenAll%2A> <xref:System.Threading.Tasks.Task.WhenAny%2A>i , i są omówione w [za pomocą wbudowanych kombinatorów opartych na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) sekcji artykułu [Korzystanie z wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 Przykłady tego, jak składnia TAP różni się od składni używanej w starszych wzorcach programowania asynchronicznego, takich jak asynchroniczny model programowania (APM) i asynchroniczny wzorzec (EAP) oparty na zdarzeniach), zobacz [Wzorce programowania asynchronicznego](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Inicjującoperację asynchroniczną  
 Metoda asynchroniczna oparta na wzorcu TAP może wykonać synchronicznie niewielką ilość pracy, na przykład weryfikację argumentów i inicjowanie operacji asynchronicznej, zanim zwróci zadanie wynikowe. Praca synchroniczna powinna być ograniczona do minimum, tak aby metoda asynchroniczna mogła szybko zwracać wynik. Powody oczekiwania szybkiego zwrócenia wyniku to m.in.:  
  
- Metody asynchroniczne mogą być wywoływane z wątków interfejsu użytkownika (UI), a jakakolwiek długotrwała praca synchroniczna może niekorzystnie wpływać na czas reakcji aplikacji.  
  
- Wiele metod asynchronicznych może zostać uruchomionych jednocześnie. W związku z tym jakakolwiek długotrwała praca synchroniczna metody asynchronicznej może opóźnić zainicjowanie innych operacji asynchronicznych, zmniejszając w ten sposób korzyści płynące ze współbieżności.  
  
 W niektórych przypadkach nakład pracy wymagany do ukończenia operacji jest mniejszy niż ilość pracy potrzebna do asynchronicznego uruchomienia operacji. Przykładem takiego scenariusza jest odczyt ze strumienia, gdzie operacja odczytu może się odbyć dzięki danym buforowanym już w pamięci. W takich przypadkach operacja może zakończyć się synchronicznie i może zwracać zadanie, które zostało już zakończone.  
  
## <a name="exceptions"></a>Wyjątki  
 Metoda asynchroniczna powinna zgłosić wyjątek z wywołania metody asynchronicznej tylko w odpowiedzi na błąd użycia. Błędy użycia nie powinny nigdy występować w kodzie produkcyjnym. Na przykład jeśli przekazywanie odwołania`Nothing` null (w języku Visual Basic) jako jeden z argumentów <xref:System.ArgumentNullException> metody powoduje stan błędu (zwykle reprezentowane przez wyjątek), można zmodyfikować kod wywołujący, aby upewnić się, że odwołanie null nigdy nie jest przekazywana. W przypadku innych błędów wyjątki, które występują, gdy uruchomiona jest metoda asynchroniczna, powinny być przypisane do zwracanego zadania, nawet jeśli metoda asynchroniczna jest wykonywana synchronicznie przed zwróceniem zadania. Zadanie zawiera zazwyczaj co najwyżej jeden wyjątek. Jeśli jednak zadanie reprezentuje wiele operacji (na <xref:System.Threading.Tasks.Task.WhenAll%2A>przykład), wiele wyjątków może być skojarzonych z jednym zadaniem.  
  
## <a name="target-environment"></a>Środowisko docelowe  
 Podczas implementacji metody wzorca TAP można określić, gdzie występuje wykonanie asynchroniczne. Można wybrać opcję wykonania operacji w puli wątków, zaimplementować je za pomocą asynchronicznego wejścia/wyjścia (bez powiązania z wątkiem dla większości wykonywanych operacji), uruchomić je w określonym wątku (na przykład wątku interfejsu użytkownika) lub użyć dowolnej liczby potencjalnych kontekstów. Metoda TAP może nawet nie mieć nic do <xref:System.Threading.Tasks.Task> wykonania i może po prostu zwrócić a, który reprezentuje wystąpienie warunku w innym miejscu w systemie (na przykład zadanie, które reprezentuje dane docierające do struktury danych w kolejce).

 Obiekt wywołujący metody TAP może zablokować oczekiwanie na zakończenie metody TAP przez synchroniczne oczekiwanie na wynikowe zadanie lub może uruchomić dodatkowy (kontynuacja) kod po zakończeniu operacji asynchronicznej. Twórca kodu kontynuacji ma kontrolę nad tym, gdzie ten kod jest wykonywany. Można utworzyć kod kontynuacji jawnie, za <xref:System.Threading.Tasks.Task> pomocą metod w <xref:System.Threading.Tasks.Task.ContinueWith%2A>klasie (na przykład) lub niejawnie przy użyciu `await` obsługi języka `Await` zbudowany na `AwaitValue` podstawie kontynuacji (na przykład w języku C#, w języku Visual Basic, w F#).  
  
## <a name="task-status"></a>Stan zadania  
 Klasa <xref:System.Threading.Tasks.Task> zapewnia cykl życia dla operacji asynchronicznych i ten <xref:System.Threading.Tasks.TaskStatus> cykl jest reprezentowany przez wyliczenie. Aby obsługiwać przypadki narożnika <xref:System.Threading.Tasks.Task> typów, które pochodzą z i <xref:System.Threading.Tasks.Task%601>, oraz <xref:System.Threading.Tasks.Task> do obsługi <xref:System.Threading.Tasks.Task.Start%2A> oddzielenia konstrukcji od planowania, klasa udostępnia metodę. Zadania, które są tworzone <xref:System.Threading.Tasks.Task> przez konstruktorów publicznych są określane jako *zimne zadania*, <xref:System.Threading.Tasks.TaskStatus.Created> ponieważ rozpoczynają swój <xref:System.Threading.Tasks.Task.Start%2A> cykl życia w stanie niezaplanowanym i są planowane tylko wtedy, gdy jest wywoływana w tych wystąpieniach.

 Wszystkie inne zadania rozpoczynają swój cykl życia w stanie upalnej, co oznacza, że operacje asynchroniczne, <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>które reprezentują, zostały już zainicjowane, a ich stan zadania jest wartością wyliczenia inną niż . Wszystkie zadania, które są zwracane z metod wzorca TAP, muszą być aktywowane. **Jeśli metoda TAP wewnętrznie używa konstruktora zadania do utworzenia wystąpienia zadania, które ma <xref:System.Threading.Tasks.Task.Start%2A> zostać <xref:System.Threading.Tasks.Task> zwrócone, metoda TAP musi wywołać obiekt przed zwróceniem go.** Konsumenci metody TAP może bezpiecznie założyć, że zwrócone zadanie jest <xref:System.Threading.Tasks.Task.Start%2A> aktywne <xref:System.Threading.Tasks.Task> i nie należy próbować wywołać na każdym, który jest zwracany z metody TAP. Wywołanie <xref:System.Threading.Tasks.Task.Start%2A> aktywnego zadania <xref:System.InvalidOperationException> powoduje wyjątek.  
  
## <a name="cancellation-optional"></a>Anulowanie (opcjonalnie)  
 We wzorcu TAP anulowanie jest opcjonalne dla implementatorów metody asynchronicznej i konsumentów metody asynchronicznej. Jeśli operacja umożliwia anulowanie, udostępnia przeciążenie metody asynchronicznej, która<xref:System.Threading.CancellationToken> akceptuje token anulowania (wystąpienie). Zgodnie z konwencją `cancellationToken`parametr nosi nazwę .  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Operacja asynchroniczna monitoruje ten token pod kątem żądań anulowania. Jeśli odbierze żądanie anulowania, może je zaakceptować i anulować operację. Jeśli żądanie anulowania powoduje przedwczesne zakończenie pracy, metoda TAP zwraca zadanie, które kończy się w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanie; nie ma dostępnego wyniku i nie jest zgłaszany wyjątek.  Stan <xref:System.Threading.Tasks.TaskStatus.Canceled> jest uważany za stan końcowy (ukończony) dla zadania, wraz z <xref:System.Threading.Tasks.TaskStatus.Faulted> i <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stanów. W związku z tym <xref:System.Threading.Tasks.TaskStatus.Canceled> jeśli zadanie <xref:System.Threading.Tasks.Task.IsCompleted%2A> jest `true`w stanie, jego właściwość zwraca . Po zakończeniu zadania w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanie, wszelkie kontynuacje zarejestrowane w zadaniu są zaplanowane lub <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> wykonane, chyba że opcja kontynuacji, takich jak został określony, aby zrezygnować z kontynuacji. Każdy kod, który jest asynchronicznie czeka na anulowane zadanie za pomocą <xref:System.OperationCanceledException> funkcji języka nadal działa, ale odbiera lub wyjątek pochodzi od niego. Kod, który jest blokowany synchronicznie oczekiwanie na <xref:System.Threading.Tasks.Task.Wait%2A> <xref:System.Threading.Tasks.Task.WaitAll%2A> zadanie za pomocą metod, takich jak i również kontynuować uruchamianie z wyjątkiem.  
  
 Jeśli token anulowania zażądał anulowania przed tap metoda, która akceptuje ten token jest <xref:System.Threading.Tasks.TaskStatus.Canceled> wywoływana, metoda TAP należy zwrócić zadanie.  Jeśli jednak żądanie anulowania zostanie zgłoszone, gdy trwa operacja asynchroniczna, operacja asynchroniczna nie musi akceptować żądania anulowania.  Zwrócone zadanie powinno zakończyć <xref:System.Threading.Tasks.TaskStatus.Canceled> się w stanie tylko wtedy, gdy operacja kończy się w wyniku żądania anulowania. Jeśli wymagane jest anulowanie, ale wynik lub wyjątek jest nadal <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> <xref:System.Threading.Tasks.TaskStatus.Faulted> produkowany, zadanie powinno zakończyć się w lub stanie.

 W przypadku metod asynchronicznych, które mają uwidaczniać możliwość anulowania przede wszystkim, nie trzeba podać przeciążenia, które nie akceptuje token anulowania. W przypadku metod, które nie mogą być anulowane, nie należy dostarczać przeciążeń, które akceptują token anulowania. Pomaga to wskazać obiektowi wywołującemu, czy metodę docelową można w rzeczywistości anulować.  Kod konsumenta, który nie chce anulowania może <xref:System.Threading.CancellationToken> wywołać metodę, która akceptuje i podać <xref:System.Threading.CancellationToken.None%2A> jako wartość argumentu. <xref:System.Threading.CancellationToken.None%2A>jest funkcjonalnie równoważny <xref:System.Threading.CancellationToken>domyślnemu .  
  
## <a name="progress-reporting-optional"></a>Raportowanie postępu (opcjonalnie)  
 Niektóre operacje asynchroniczne korzystają z dostarczania powiadomień na temat postępu. Zazwyczaj są one używane do aktualizowania interfejsu użytkownika za pomocą informacji o postępie operacji asynchronicznej.

 W tap postęp jest obsługiwany <xref:System.IProgress%601> przez interfejs, który jest przekazywany do metody asynchronicznej jako parametr, który jest zwykle o nazwie `progress`.  Dostarczenie interfejsu postępu, gdy wywoływana jest metoda asynchroniczna, pomaga wyeliminować sytuację wyścigu, która wynika z niepoprawnego użycia (tzn. kiedy obsługa zdarzeń, która jest niepoprawnie rejestrowana po rozpoczęciu operacji, może pominąć aktualizacje).  Co więcej, interfejs postępu obsługuje różne implementacje postępu, co zostało określone przez kod konsumencki.  Kod konsumencki może uwzględniać tylko najnowszą aktualizację postępu lub może buforować wszystkie aktualizacje. Może on wywołać akcję dla każdej aktualizacji lub może określać, czy wywołanie jest przekazywane do określonego wątku. Te opcje można osiągnąć przy użyciu różnej implementacji interfejsu, dostosowanej do potrzeb danego konsumenta.  Podobnie jak w przypadku anulowania <xref:System.IProgress%601> implementacje TAP powinny zapewniać parametr tylko wtedy, gdy interfejs API obsługuje powiadomienia o postępie.

 Na przykład jeśli `ReadAsync` metoda omówiona wcześniej w tym artykule jest w stanie zgłosić postęp pośredni w postaci liczby <xref:System.IProgress%601> bajtów odczytanych do tej pory, wywołanie wywołania wywołania pokroku może być interfejs:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Jeśli `FindFilesAsync` metoda zwraca listę wszystkich plików, które spełniają określony wzorzec wyszukiwania, wywołanie wywołania wywołania wywołania postępu może dostarczyć oszacowanie procentu pracy wykonanej, a także bieżący zestaw wyników częściowych.  Może to zrobić za pomocą spójnej kolekcji:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 lub za pomocą typu danych specyficznego dla interfejsu API:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 W tym ostatnim przypadku specjalny typ danych jest `ProgressInfo`zwykle sufiksowany z .  
  
 Jeśli implementacje TAP zapewniają `progress` przeciążenia, które akceptują `null`parametr, muszą one zezwalać na argument, w którym to przypadku nie będzie raportowany postęp. Implementacje TAP należy zgłosić <xref:System.Progress%601> postęp do obiektu synchronicznie, co umożliwia metodę asynchroniczną, aby szybko zapewnić postęp i umożliwić konsumentowi postępu, aby określić, jak i gdzie najlepiej obsługiwać informacje. Na przykład wystąpienie postępu może wybrać przekazywanie wywołań zwrotnych i generowanie zdarzeń w kontekście przechwyconych synchronizacji.  
  
## <a name="iprogresst-implementations"></a>Implementacje> IProgress\<T  
 Program .NET Framework 4.5 <xref:System.IProgress%601> zapewnia <xref:System.Progress%601>jedną implementację: . Klasa <xref:System.Progress%601> jest zadeklarowana w następujący sposób:  
  
```csharp  
public class Progress<T> : IProgress<T>  
{  
    public Progress();  
    public Progress(Action<T> handler);  
    protected virtual void OnReport(T value);  
    public event EventHandler<T> ProgressChanged;  
}  
```  
  
```vb  
Public Class Progress(Of T) : Inherits IProgress(Of T)  
    Public Sub New()  
    Public Sub New(handler As Action(Of T))  
    Protected Overridable Sub OnReport(value As T)  
    Public Event ProgressChanged As EventHandler(Of T>  
End Class  
```  
  
 Wystąpienie <xref:System.Progress%601> udostępnia <xref:System.Progress%601.ProgressChanged> zdarzenie, które jest wywoływane za każdym razem, gdy operacja asynchroniczna zgłasza aktualizację postępu. Zdarzenie <xref:System.Progress%601.ProgressChanged> jest wywoływane <xref:System.Threading.SynchronizationContext> na obiekcie, <xref:System.Progress%601> który został przechwycony, gdy wystąpienie zostało uprzedzione. Jeśli kontekst synchronizacji nie był dostępny, używany jest domyślny kontekst ukierunkowany na pulę wątków. Z tym zdarzeniem można zarejestrować programy obsługi. Pojedynczy program obsługi może również <xref:System.Progress%601> być dostarczone do konstruktora dla wygody <xref:System.Progress%601.ProgressChanged> i zachowuje się podobnie jak program obsługi zdarzeń dla zdarzenia. Aktualizacje postępu są wywoływane asynchronicznie, aby unikać opóźniania operacji asynchronicznej podczas wykonywania obsługi zdarzeń. Inna <xref:System.IProgress%601> implementacja może zdecydować się na zastosowanie różnych semantyki.  
  
## <a name="choosing-the-overloads-to-provide"></a>Wybór przeciążeń w celu zapewnienia  
 Jeśli implementacja TAP używa <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> parametrów <xref:System.IProgress%601> opcjonalnych i opcjonalnych, może potencjalnie wymagać maksymalnie czterech przeciążeń:  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, CancellationToken cancellationToken);  
public Task MethodNameAsync(…, IProgress<T> progress);
public Task MethodNameAsync(…,
    CancellationToken cancellationToken, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken cancellationToken) As Task  
Public MethodNameAsync(…, progress As IProgress(Of T)) As Task
Public MethodNameAsync(…, cancellationToken As CancellationToken,
                       progress As IProgress(Of T)) As Task  
```  
  
 Wiele implementacji wzorca TAP nie dostarcza jednak możliwości anulowania ani możliwości obsługi postępu, więc wymagają one pojedynczej metody:  
  
```csharp  
public Task MethodNameAsync(…);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
```  
  
 Jeżeli implementacja wzorca TAP obsługuje anulowanie lub postęp, ale nie obie te możliwości naraz, może ona dostarczać dwa przeciążenia:  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, CancellationToken cancellationToken);  
  
// … or …  
  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken) As Task  
  
' … or …  
  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, progress As IProgress(Of T)) As Task  
```  
  
 Jeśli implementacja wzorca TAP obsługuje zarówno anulowanie, jak i postęp, może uwidaczniać wszystkie cztery przeciążenia. Może jednak dostarczyć tylko następujące dwa:  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…,
    CancellationToken cancellationToken, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken,
                       progress As IProgress(Of T)) As Task  
```  
  
 Aby skompensować dwie brakujące kombinacje <xref:System.Threading.CancellationToken.None%2A> pośrednie, <xref:System.Threading.CancellationToken> deweloperzy mogą przekazać lub domyślnie dla parametru `cancellationToken` i `null` parametru. `progress`  
  
 Jeśli każde użycie metody wzorca TAP ma obsługiwać anulowanie lub postęp, możesz pominąć przeciążenia, które nie akceptują odpowiedniego parametru.  
  
 Jeśli zdecydujesz się uwidaczniać wiele przeciążeń, aby anulowanie lub postęp były opcjonalne, przeciążenia, które nie obsługują anulowania lub postępu, powinny zachowywać się tak, jakby zostały przekazane <xref:System.Threading.CancellationToken.None%2A> do anulowania lub `null` postępu do przeciążenia, które obsługuje te.  
  
## <a name="related-topics"></a>Powiązane tematy  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wzorce programowania asynchronicznego](../../../docs/standard/asynchronous-programming-patterns/index.md)|Wprowadza trzy wzorce do wykonywania operacji asynchronicznych: asynchroniczny wzorzec oparty na zadaniach (TAP), asynchroniczny model programowania (APM) i asynchroniczny wzorzec oparty na zdarzeniach (EAP).|  
|[Implementacja wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Opis sposobu implementacji asynchronicznego wzorca opartego na zadaniach (TAP), którą można przeprowadzić na trzy sposoby: za pomocą kompilatorów języków C# i Visual Basic w programie Visual Studio, ręcznie lub za pomocą kombinacji metod kompilatora i manualnych.|  
|[Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Opis sposobu używania zadań i wywołań zwrotnych w celu osiągnięcia oczekiwania bez blokowania.|  
|[Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Opis sposobu używania asynchronicznego wzorca opartego na zadaniach (TAP) w celu implementacji asynchronicznego modelu programowania (APM) i asynchronicznego wzorca opartego na zdarzeniach (EAP).|
