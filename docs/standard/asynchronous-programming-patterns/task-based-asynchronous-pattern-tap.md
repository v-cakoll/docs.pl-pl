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
ms.openlocfilehash: f61ad49753da9d96e733ea667095722ddc238fe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121099"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Wzorzec asynchroniczny oparty na zadaniach (TAP)
Wzorzec asynchroniczny oparty na zadaniach (TAP) jest oparty na <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typach w przestrzeni nazw <xref:System.Threading.Tasks?displayProperty=nameWithType>, które są używane do reprezentowania dowolnych operacji asynchronicznych. Wzorzec TAP jest zalecanym asynchronicznym wzorcem projektowym dla nowych prac deweloperskich.  
  
## <a name="naming-parameters-and-return-types"></a>Nazewnictwo, parametry i typy zwracane

We wzorcu TAP do tworzenia wystąpienia i wykonywania operacji asynchronicznej jest używana jedna metoda. To różni się od wzorca programowania asynchronicznego (APM lub `IAsyncResult`) i wzorca asynchronicznego opartego na zdarzeniach (EAP). System APM wymaga metod `Begin` i `End`. Protokół EAP wymaga metody, która ma sufiks `Async`, a także wymaga co najmniej jednego zdarzenia, typów delegatów obsługi zdarzeń i typów pochodnych `EventArg`. Metody asynchroniczne w programie TAP obejmują sufiks `Async` po nazwie operacji dla metod, które zwracają typy oczekujące, takie jak <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>i <xref:System.Threading.Tasks.ValueTask%601>. Na przykład asynchroniczna operacja `Get`, która zwraca `Task<String>` można nazwać `GetAsync`. Jeśli dodajesz metodę TAP do klasy, która zawiera już nazwę metody EAP z sufiksem `Async`, zamiast tego użyj sufiksu `TaskAsync`. Na przykład jeśli klasa ma już metodę `GetAsync`, użyj nazwy `GetTaskAsync`. Jeśli metoda rozpoczyna operację asynchroniczną, ale nie zwraca typu oczekującego, jej nazwa powinna rozpoczynać się od `Begin`, `Start`lub innego zlecenia, aby zasugerować, że ta metoda nie zwraca lub nie generuje wyniku operacji.  
  
 Metoda TAP zwraca <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, w zależności od tego, czy odpowiadająca metoda synchroniczna zwraca typ void lub `TResult`.  
  
 Parametry metody TAP powinny odpowiadać parametrom synchronicznego odpowiednika i powinny być podane w tej samej kolejności.  Jednak parametry `out` i `ref` są wykluczone z tej reguły i należy je całkowicie uniknąć. Wszelkie dane, które zostałyby zwrócone przez `out` lub parametr `ref`, powinny być zwracane jako część `TResult` zwrócone przez <xref:System.Threading.Tasks.Task%601>i powinny używać spójnej struktury danych w celu podzielenia wielu wartości. Należy również rozważyć dodanie <xref:System.Threading.CancellationToken> parametru, nawet jeśli synchroniczny odpowiednik metody TAP nie oferuje tego elementu.
 
 Metody, które są przeznaczone wyłącznie do tworzenia, manipulowania lub łączenia zadań (w przypadku których zamiar asynchroniczny metody jest jasne w nazwie metody lub w nazwie typu, do którego należy Metoda) nie muszą być zgodne z tym wzorcem nazewnictwa; takie metody są często określane jako *kombinatorów*. Przykłady kombinatorów zawierają <xref:System.Threading.Tasks.Task.WhenAll%2A> i <xref:System.Threading.Tasks.Task.WhenAny%2A>i zostały omówione w sekcji [using wbudowanej kombinatorów opartej na zadaniach w artykule korzystającej](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) [ze wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 Aby zapoznać się z przykładami sposobu, w jaki składnia TAP różni się od składni używanej w starszych asynchronicznych wzorcach programowania, takich jak asynchroniczny model programowania (APM) i asynchroniczny wzorzec oparty na zdarzeniach (EAP), zobacz [wzorce programowania asynchronicznego](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Inicjowanie operacji asynchronicznej  
 Metoda asynchroniczna oparta na wzorcu TAP może wykonać synchronicznie niewielką ilość pracy, na przykład weryfikację argumentów i inicjowanie operacji asynchronicznej, zanim zwróci zadanie wynikowe. Praca synchroniczna powinna być ograniczona do minimum, tak aby metoda asynchroniczna mogła szybko zwracać wynik. Powody oczekiwania szybkiego zwrócenia wyniku to m.in.:  
  
- Metody asynchroniczne mogą być wywoływane z wątków interfejsu użytkownika (UI), a jakakolwiek długotrwała praca synchroniczna może niekorzystnie wpływać na czas reakcji aplikacji.  
  
- Wiele metod asynchronicznych może zostać uruchomionych jednocześnie. W związku z tym jakakolwiek długotrwała praca synchroniczna metody asynchronicznej może opóźnić zainicjowanie innych operacji asynchronicznych, zmniejszając w ten sposób korzyści płynące ze współbieżności.  
  
 W niektórych przypadkach nakład pracy wymagany do ukończenia operacji jest mniejszy niż ilość pracy potrzebna do asynchronicznego uruchomienia operacji. Przykładem takiego scenariusza jest odczyt ze strumienia, gdzie operacja odczytu może się odbyć dzięki danym buforowanym już w pamięci. W takich przypadkach operacja może zakończyć się synchronicznie i może zwracać zadanie, które zostało już zakończone.  
  
## <a name="exceptions"></a>Wyjątki  
 Metoda asynchroniczna powinna zgłosić wyjątek z wywołania metody asynchronicznej tylko w odpowiedzi na błąd użycia. Błędy użycia nie powinny nigdy występować w kodzie produkcyjnym. Na przykład jeśli przekazywanie odwołania o wartości null (`Nothing` w Visual Basic) jako jeden z argumentów metody powoduje błąd (zazwyczaj reprezentowany przez wyjątek <xref:System.ArgumentNullException>), można zmodyfikować kod wywołujący, aby upewnić się, że odwołanie o wartości null nigdy nie zostanie przekazane. W przypadku innych błędów wyjątki, które występują, gdy uruchomiona jest metoda asynchroniczna, powinny być przypisane do zwracanego zadania, nawet jeśli metoda asynchroniczna jest wykonywana synchronicznie przed zwróceniem zadania. Zadanie zawiera zazwyczaj co najwyżej jeden wyjątek. Jeśli jednak zadanie reprezentuje wiele operacji (na przykład <xref:System.Threading.Tasks.Task.WhenAll%2A>), wiele wyjątków może być skojarzonych z pojedynczym zadaniem.  
  
## <a name="target-environment"></a>Środowisko docelowe  
 Podczas implementacji metody wzorca TAP można określić, gdzie występuje wykonanie asynchroniczne. Można wybrać opcję wykonania operacji w puli wątków, zaimplementować je za pomocą asynchronicznego wejścia/wyjścia (bez powiązania z wątkiem dla większości wykonywanych operacji), uruchomić je w określonym wątku (na przykład wątku interfejsu użytkownika) lub użyć dowolnej liczby potencjalnych kontekstów. Metoda TAP może nawet nie mieć niczego do wykonania i może po prostu zwrócić <xref:System.Threading.Tasks.Task>, która reprezentuje wystąpienie warunku w innym miejscu w systemie (na przykład zadanie, które reprezentuje dane docierające do struktury danych znajdujących się w kolejce).
 
 Obiekt wywołujący metody TAP może blokować oczekiwanie na ukończenie metody TAP przez synchronicznie czeka na wyniki zadania lub może uruchamiać dodatkowy kod (kontynuacja) po zakończeniu operacji asynchronicznej. Twórca kodu kontynuacji ma kontrolę nad tym, gdzie ten kod jest wykonywany. Kod kontynuacji można utworzyć jawnie za pomocą metod klasy <xref:System.Threading.Tasks.Task> (na przykład <xref:System.Threading.Tasks.Task.ContinueWith%2A>) lub niejawnie, korzystając z pomocy technicznej języka, która jest oparta na kontynuacji (na przykład `await` w C#`Await` w Visual Basic, @no__t _5_ w F#programie).  
  
## <a name="task-status"></a>Stan zadania  
 Klasa <xref:System.Threading.Tasks.Task> dostarcza cykl życia operacji asynchronicznych i ten cykl jest reprezentowany przez Wyliczenie <xref:System.Threading.Tasks.TaskStatus>. Aby obsługiwać przypadki narożne typów, które pochodzą z <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601>i aby obsługiwać separację konstrukcji z planowania, Klasa <xref:System.Threading.Tasks.Task> uwidacznia metodę <xref:System.Threading.Tasks.Task.Start%2A>. Zadania, które są tworzone przez publiczne konstruktory <xref:System.Threading.Tasks.Task>, są określane jako *zimne zadania*, ponieważ zaczynają ich cykl życia w stanie zaplanowanym <xref:System.Threading.Tasks.TaskStatus.Created> i są planowane tylko wtedy, gdy <xref:System.Threading.Tasks.Task.Start%2A> jest wywoływana dla tych wystąpień. 
 
 Wszystkie inne zadania rozpoczynają cykl życia w stanie gorąca, co oznacza, że operacje asynchroniczne, które reprezentują, zostały już zainicjowane, a ich stan zadania jest wartością wyliczenia inną niż <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>. Wszystkie zadania, które są zwracane z metod wzorca TAP, muszą być aktywowane. **Jeśli metoda TAP używa wewnętrznie konstruktora zadania, aby utworzyć wystąpienie zadania do zwrócenia, Metoda TAP musi wywołać <xref:System.Threading.Tasks.Task.Start%2A> na obiekcie <xref:System.Threading.Tasks.Task> przed jego zwróceniem.** Konsumenci metody TAP mogą bezpiecznie założyć, że zwrócone zadanie jest aktywne i nie powinna próbować wywołać <xref:System.Threading.Tasks.Task.Start%2A> na żadnym <xref:System.Threading.Tasks.Task>, który jest zwracany przez metodę TAP. Wywołanie <xref:System.Threading.Tasks.Task.Start%2A> na aktywnym zadaniu powoduje wystąpienie <xref:System.InvalidOperationException> wyjątku.  
  
## <a name="cancellation-optional"></a>Anulowanie (opcjonalne)  
 We wzorcu TAP anulowanie jest opcjonalne dla implementatorów metody asynchronicznej i konsumentów metody asynchronicznej. Jeśli operacja zezwala na anulowanie, ujawnia Przeciążenie metody asynchronicznej, która akceptuje token anulowania (<xref:System.Threading.CancellationToken> wystąpienie). Zgodnie z Konwencją parametr ma nazwę `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Operacja asynchroniczna monitoruje ten token pod kątem żądań anulowania. Jeśli odbierze żądanie anulowania, może je zaakceptować i anulować operację. Jeśli żądanie anulowania spowoduje przedwcześnie zakończenie pracy, Metoda TAP zwraca zadanie, które kończy się w stanie <xref:System.Threading.Tasks.TaskStatus.Canceled>; Brak dostępnego wyniku i nie został zgłoszony żaden wyjątek.  Stan <xref:System.Threading.Tasks.TaskStatus.Canceled> jest uznawany za końcowy (ukończony) dla zadania, wraz ze Stanami <xref:System.Threading.Tasks.TaskStatus.Faulted> i <xref:System.Threading.Tasks.TaskStatus.RanToCompletion>. W związku z tym, jeśli zadanie jest w stanie <xref:System.Threading.Tasks.TaskStatus.Canceled>, jego właściwość <xref:System.Threading.Tasks.Task.IsCompleted%2A> zwraca `true`. Gdy zadanie zostanie ukończone w stanie <xref:System.Threading.Tasks.TaskStatus.Canceled>, wszystkie kontynuacje zarejestrowane w ramach zadania są zaplanowane lub wykonywane, chyba że opcja kontynuacji, taka jak <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled>, została określona w celu rezygnacji z kontynuacji. Każdy kod, który asynchronicznie czeka na anulowane zadanie przy użyciu funkcji języka, jest nadal uruchamiany, ale odbiera <xref:System.OperationCanceledException> lub wyjątek pochodzący od niego. Kod, który jest blokowany synchronicznie, oczekując na zadanie za pomocą metod takich jak <xref:System.Threading.Tasks.Task.Wait%2A> i <xref:System.Threading.Tasks.Task.WaitAll%2A> również nadal uruchamiany z wyjątkiem.  
  
 Jeśli token anulowania zażądał anulowania przed wywołaniem metody, która akceptuje ten token, Metoda TAP powinna zwracać <xref:System.Threading.Tasks.TaskStatus.Canceled> zadanie.  Jeśli jednak żądanie anulowania zostanie zgłoszone, gdy trwa operacja asynchroniczna, operacja asynchroniczna nie musi akceptować żądania anulowania.  Zwrócone zadanie powinno kończyć się w stanie <xref:System.Threading.Tasks.TaskStatus.Canceled> tylko wtedy, gdy operacja kończy się w wyniku żądania anulowania. Jeśli zażądano anulowania, ale nadal jest generowany wynik lub wyjątek, zadanie powinno kończyć się w stanie <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> lub <xref:System.Threading.Tasks.TaskStatus.Faulted>. 
 
 W przypadku metod asynchronicznych, które chcą ujawnić możliwość pierwszego i przedniego anulowania, nie trzeba podawać przeciążenia, które nie akceptuje tokenu anulowania. W przypadku metod, które nie mogą być anulowane, nie należy dostarczać przeciążeń, które akceptują token anulowania. Pomaga to wskazać obiektowi wywołującemu, czy metodę docelową można w rzeczywistości anulować.  Kod klienta, który nie wymaga anulowania, może wywołać metodę, która akceptuje <xref:System.Threading.CancellationToken> i podać <xref:System.Threading.CancellationToken.None%2A> jako wartość argumentu. <xref:System.Threading.CancellationToken.None%2A> jest funkcjonalnie równoważny <xref:System.Threading.CancellationToken>domyślnej.  
  
## <a name="progress-reporting-optional"></a>Raportowanie postępu (opcjonalnie)  
 Niektóre operacje asynchroniczne korzystają z dostarczania powiadomień na temat postępu. Zazwyczaj są one używane do aktualizowania interfejsu użytkownika za pomocą informacji o postępie operacji asynchronicznej. 
 
 W programie TAP postęp jest obsługiwany przez interfejs <xref:System.IProgress%601>, który jest przesyłany do metody asynchronicznej jako parametr, który jest zazwyczaj nazwany `progress`.  Dostarczenie interfejsu postępu, gdy wywoływana jest metoda asynchroniczna, pomaga wyeliminować sytuację wyścigu, która wynika z niepoprawnego użycia (tzn. kiedy obsługa zdarzeń, która jest niepoprawnie rejestrowana po rozpoczęciu operacji, może pominąć aktualizacje).  Co więcej, interfejs postępu obsługuje różne implementacje postępu, co zostało określone przez kod konsumencki.  Kod konsumencki może uwzględniać tylko najnowszą aktualizację postępu lub może buforować wszystkie aktualizacje. Może on wywołać akcję dla każdej aktualizacji lub może określać, czy wywołanie jest przekazywane do określonego wątku. Te opcje można osiągnąć przy użyciu różnej implementacji interfejsu, dostosowanej do potrzeb danego konsumenta.  Podobnie jak w przypadku anulowania, implementacje programu TAP powinny podawać parametr <xref:System.IProgress%601> tylko wtedy, gdy interfejs API obsługuje powiadomienia o postępie. 
 
 Na przykład jeśli metoda `ReadAsync` opisana wcześniej w tym artykule jest w stanie raportować postęp pośredni w postaci liczby odczytanych bajtów w tym zakresie, wywołanie zwrotne postępu może być interfejsem <xref:System.IProgress%601>:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Jeśli metoda `FindFilesAsync` zwraca listę wszystkich plików, które spełniają określony wzorzec wyszukiwania, wywołanie zwrotne postępu może zapewnić oszacowanie wartości procentowej wykonanej pracy, a także bieżący zestaw wyników częściowych.  Może to zrobić za pomocą spójnej kolekcji:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 lub za pomocą typu danych specyficznego dla interfejsu API:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 W tym drugim przypadku specjalny typ danych jest zazwyczaj sufiksem `ProgressInfo`.  
  
 Jeśli implementacje TAP zapewniają przeciążenia, które akceptują parametr `progress`, muszą zezwalać na `null`argumentu, w takim przypadku nie zostanie zgłoszony żaden postęp. Implementacje TAP powinny raportować postęp do obiektu <xref:System.Progress%601> synchronicznie, dzięki czemu Metoda asynchroniczna może szybko zapewnić postęp, a następnie zezwolić konsumentowi postępu na ustalenie, jak i gdzie najlepiej obsługiwać te informacje. Na przykład wystąpienie postępu może wybrać przekazywanie wywołań zwrotnych i generowanie zdarzeń w kontekście przechwyconych synchronizacji.  
  
## <a name="iprogresst-implementations"></a>Implementacje > IProgress\<T  
 .NET Framework 4,5 zawiera jedną implementację <xref:System.IProgress%601>: <xref:System.Progress%601>. Klasa <xref:System.Progress%601> jest zadeklarowana w następujący sposób:  
  
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
  
 Wystąpienie <xref:System.Progress%601> uwidacznia zdarzenie <xref:System.Progress%601.ProgressChanged>, które jest wywoływane za każdym razem, gdy operacja asynchroniczna zgłosi aktualizację postępu. Zdarzenie <xref:System.Progress%601.ProgressChanged> jest zgłaszane na obiekcie <xref:System.Threading.SynchronizationContext>, który został przechwycony podczas tworzenia wystąpienia <xref:System.Progress%601> wystąpieniem. Jeśli kontekst synchronizacji nie był dostępny, używany jest domyślny kontekst ukierunkowany na pulę wątków. Z tym zdarzeniem można zarejestrować programy obsługi. Pojedynczy program obsługi może być również udostępniony konstruktorowi <xref:System.Progress%601> dla wygody i zachowuje się tak jak program obsługi zdarzeń dla zdarzenia <xref:System.Progress%601.ProgressChanged>. Aktualizacje postępu są wywoływane asynchronicznie, aby unikać opóźniania operacji asynchronicznej podczas wykonywania obsługi zdarzeń. Inna implementacja <xref:System.IProgress%601> może zdecydować się na zastosowanie różnych semantyki.  
  
## <a name="choosing-the-overloads-to-provide"></a>Wybieranie przeciążeń do dostarczenia  
 Jeśli implementacja TAP używa zarówno opcjonalne <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A>, jak i opcjonalnych parametrów <xref:System.IProgress%601>, może to wymagać do czterech przeciążeń:  
  
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
  
 Aby skompensować dla dwóch brakujących się kombinacji pośrednich, deweloperzy mogą przekazywać <xref:System.Threading.CancellationToken.None%2A> lub <xref:System.Threading.CancellationToken> domyślny dla parametru `cancellationToken` i `null` dla parametru `progress`.  
  
 Jeśli każde użycie metody wzorca TAP ma obsługiwać anulowanie lub postęp, możesz pominąć przeciążenia, które nie akceptują odpowiedniego parametru.  
  
 W przypadku podjęcia decyzji o udostępnieniu wielu przeciążeń w celu dokonania anulowania lub załadowania postępu przeciążenia, które nie obsługują anulowania lub postępu, powinny zachowywać się tak, jakby przekazały <xref:System.Threading.CancellationToken.None%2A> do anulowania lub `null` do przeładowania do przeciążenia, które obsługuje powyższych.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wzorce programowania asynchronicznego](../../../docs/standard/asynchronous-programming-patterns/index.md)|Wprowadza trzy wzorce do wykonywania operacji asynchronicznych: asynchroniczny wzorzec oparty na zadaniach (TAP), asynchroniczny model programowania (APM) i asynchroniczny wzorzec oparty na zdarzeniach (EAP).|  
|[Implementowanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Opis sposobu implementacji asynchronicznego wzorca opartego na zadaniach (TAP), którą można przeprowadzić na trzy sposoby: za pomocą kompilatorów języków C# i Visual Basic w programie Visual Studio, ręcznie lub za pomocą kombinacji metod kompilatora i manualnych.|  
|[Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Opis sposobu używania zadań i wywołań zwrotnych w celu osiągnięcia oczekiwania bez blokowania.|  
|[Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Opis sposobu używania asynchronicznego wzorca opartego na zadaniach (TAP) w celu implementacji asynchronicznego modelu programowania (APM) i asynchronicznego wzorca opartego na zdarzeniach (EAP).|
