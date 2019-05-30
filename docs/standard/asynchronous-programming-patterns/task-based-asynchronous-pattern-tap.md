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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 052f6a61fb1b03b060e22bbff2d8124ac3a1c0c0
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377659"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Wzorca asynchronicznego opartego na zadaniach (TAP)
Oparta na zadaniach asynchronicznej wzorca (TAP) jest oparty na <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> wpisuje <xref:System.Threading.Tasks?displayProperty=nameWithType> przestrzeni nazw, które są używane do reprezentowania dowolnych operacji asynchronicznych. Wzorzec TAP jest zalecanym asynchronicznym wzorcem projektowym dla nowych prac deweloperskich.  
  
## <a name="naming-parameters-and-return-types"></a>Nazewnictwo, parametry i zwracane typy

We wzorcu TAP do tworzenia wystąpienia i wykonywania operacji asynchronicznej jest używana jedna metoda. To zachowanie różni się od obu modelu programowania asynchronicznego (APM lub `IAsyncResult`) wzorca i oparte na zdarzeniach asynchronicznych wzorca (EAP). Wymaga APM `Begin` i `End` metody. Protokół EAP wymaga metody, która ma `Async` sufiks, a także wymaga przynajmniej jednego zdarzenia, typów delegatów obsługi zdarzeń, a `EventArg`— typy pochodne. Metod asynchronicznych we wzorcu TAP zawierają `Async` sufiks po nazwy operacji w przypadku metod zwracających oczekujący typów, takich jak <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, i <xref:System.Threading.Tasks.ValueTask%601>. Na przykład asynchronicznej `Get` operację, która zwraca `Task<String>` może mieć nazwę `GetAsync`. W przypadku dodawania metody wzorca TAP do klasy, która zawiera już nazwę metody EAP z `Async` sufiksu domeny, należy użyć sufiksu `TaskAsync` zamiast tego. Na przykład, jeśli klasa ma już `GetAsync` metody, użyj nazwy `GetTaskAsync`. Jeśli metoda rozpoczyna operację asynchroniczną, ale nie może zwracać typu oczekujący, jego nazwa powinna rozpoczynać `Begin`, `Start`, lub niektóre inne zlecenie sugerujące, ta metoda nie zwraca lub zgłosić wyniku operacji.  
  
 Metoda wzorca TAP zwraca albo <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, zależnie od tego, czy odpowiednia metoda asynchroniczna zwraca wartość void lub typ `TResult`.  
  
 Parametry metody wzorca TAP powinny odpowiadać parametrom jej synchronicznego odpowiednika i powinny być podane w tej samej kolejności.  Jednak `out` i `ref` parametry są wykluczone z tej reguły i powinna być w ogóle. Wszelkie dane, które mogłyby zostały zwrócone za pośrednictwem `out` lub `ref` parametru powinny zostać zwrócone jako część `TResult` zwrócone przez <xref:System.Threading.Tasks.Task%601>i powinna być używana spójna Kolekcja lub struktura danych niestandardowych do uwzględnienia wielu wartości. Należy również rozważyć dodanie <xref:System.Threading.CancellationToken> nawet, jeśli metoda wzorca TAP synchronicznego odpowiednika nie oferuje jeden parametr.
 
 Metody przeznaczone wyłącznie do tworzenia, modyfikowania lub zadań (gdzie asynchroniczne przeznaczenie metody jest jasne, w nazwie metody lub nazwie typu, do którego należy metoda) nie muszą korzystać z tego wzoru nazewnictwa; metody te są często nazywane *metody*. Przykładami kombinacji są metody <xref:System.Threading.Tasks.Task.WhenAll%2A> i <xref:System.Threading.Tasks.Task.WhenAny%2A>, zostały one omówione w [przy użyciu metody oparte na wbudowanych zadań](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) część artykułu [wykorzystywanie opartego na zadaniach wzorca asynchronicznego](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 Aby uzyskać przykłady, czym różni się składnią wzorca TAP składnią używaną w starszych asynchronicznych wzorcach programowania takich jak modelu programowania asynchronicznego (APM) i oparty na zdarzeniach asynchronicznych wzorca (EAP), zobacz [Asynchronous Programming Patterns ](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Inicjowanie operacji asynchronicznej  
 Metoda asynchroniczna oparta na wzorcu TAP może wykonać synchronicznie niewielką ilość pracy, na przykład weryfikację argumentów i inicjowanie operacji asynchronicznej, zanim zwróci zadanie wynikowe. Praca synchroniczna powinna być ograniczona do minimum, tak aby metoda asynchroniczna mogła szybko zwracać wynik. Powody oczekiwania szybkiego zwrócenia wyniku to m.in.:  
  
- Metody asynchroniczne mogą być wywoływane z wątków interfejsu użytkownika (UI), a jakakolwiek długotrwała praca synchroniczna może niekorzystnie wpływać na czas reakcji aplikacji.  
  
- Wiele metod asynchronicznych może zostać uruchomionych jednocześnie. W związku z tym jakakolwiek długotrwała praca synchroniczna metody asynchronicznej może opóźnić zainicjowanie innych operacji asynchronicznych, zmniejszając w ten sposób korzyści płynące ze współbieżności.  
  
 W niektórych przypadkach nakład pracy wymagany do ukończenia operacji jest mniejszy niż ilość pracy potrzebna do asynchronicznego uruchomienia operacji. Przykładem takiego scenariusza jest odczyt ze strumienia, gdzie operacja odczytu może się odbyć dzięki danym buforowanym już w pamięci. W takich przypadkach operacja może zakończyć się synchronicznie i może zwracać zadanie, które zostało już zakończone.  
  
## <a name="exceptions"></a>Wyjątki  
 Metoda asynchroniczna powinna zgłosić wyjątek z wywołania metody asynchronicznej tylko w odpowiedzi na błąd użycia. Błędy użycia nie powinny nigdy występować w kodzie produkcyjnym. Na przykład w przypadku przekazywania odwołanie o wartości null (`Nothing` w języku Visual Basic) jako jeden z argumentów metody powoduje stan błędu (zwykle reprezentowany przez <xref:System.ArgumentNullException> wyjątek), można zmodyfikować kod wywołujący, aby upewnić się, że odwołanie o wartości null nie będzie przekazywane. W przypadku innych błędów wyjątki, które występują, gdy uruchomiona jest metoda asynchroniczna, powinny być przypisane do zwracanego zadania, nawet jeśli metoda asynchroniczna jest wykonywana synchronicznie przed zwróceniem zadania. Zadanie zawiera zazwyczaj co najwyżej jeden wyjątek. Jednakże jeśli zadanie reprezentuje wiele operacji (na przykład <xref:System.Threading.Tasks.Task.WhenAll%2A>), wiele wyjątków może być skojarzone z pojedynczym zadaniem.  
  
## <a name="target-environment"></a>Środowisko docelowe  
 Podczas implementacji metody wzorca TAP można określić, gdzie występuje wykonanie asynchroniczne. Można wybrać opcję wykonania operacji w puli wątków, zaimplementować je za pomocą asynchronicznego wejścia/wyjścia (bez powiązania z wątkiem dla większości wykonywanych operacji), uruchomić je w określonym wątku (na przykład wątku interfejsu użytkownika) lub użyć dowolnej liczby potencjalnych kontekstów. Metoda wzorca TAP może nawet mają one nic wspólnego są wykonywane i po prostu może zwrócić <xref:System.Threading.Tasks.Task> reprezentujący wystąpienie warunku z innym miejscu w systemie (na przykład zadanie, które reprezentuje danych otrzymywanych przez strukturę danych umieszczonych w kolejce).
 
 Obiekt wywołujący metody wzorca TAP może blokować oczekiwanie na zakończenie poprzez synchronicznie oczekuje na zadanie wynikowe metody wzorca TAP lub może uruchomić kod dodatkowy (kontynuacji), po zakończeniu operacji asynchronicznej. Twórca kodu kontynuacji ma kontrolę nad tym, gdzie ten kod jest wykonywany. Możesz utworzyć kod kontynuacji albo jawnie za pomocą metod na <xref:System.Threading.Tasks.Task> klasy (na przykład <xref:System.Threading.Tasks.Task.ContinueWith%2A>) lub niejawnie, korzystając z obsługi języków, zbudowany na podstawie kontynuacji (na przykład `await` w C#, `Await` w języku Visual Basic `AwaitValue` w F#).  
  
## <a name="task-status"></a>Stan zadania  
 <xref:System.Threading.Tasks.Task> Klasa dostarcza cykl życia dla operacji asynchronicznych, a ten cykl jest reprezentowany przez <xref:System.Threading.Tasks.TaskStatus> wyliczenia. Aby obsługiwać przypadki narożne typów, które wynikają z <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601>, a także obsługiwać separację konstrukcji od planowania, <xref:System.Threading.Tasks.Task> klasy ujawnia <xref:System.Threading.Tasks.Task.Start%2A> metody. Zadania, które są tworzone przez publiczne <xref:System.Threading.Tasks.Task> konstruktory są określane jako *zadania nieaktywne*, ponieważ zaczynają cykl życia w niezaplanowanym <xref:System.Threading.Tasks.TaskStatus.Created> stanu i są planowane tylko wtedy, gdy <xref:System.Threading.Tasks.Task.Start%2A> jest wywoływana w te wystąpienia. 
 
 Wszystkie inne zadania rozpoczynają cykl życia w stanie, co oznacza, że operacje asynchroniczne, stanowią one zostały już zainicjowane i ich stan zadania jest wartością wyliczenia innych niż <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>. Wszystkie zadania, które są zwracane z metod wzorca TAP, muszą być aktywowane. **Jeśli metoda wzorca TAP używa wewnętrznie konstruktora zadania do utworzenia wystąpienia zadania, które ma zostać zwrócone, metoda wzorca TAP musi wywołać <xref:System.Threading.Tasks.Task.Start%2A> na <xref:System.Threading.Tasks.Task> obiektu przed zwróceniem.** Konsumenci metody wzorca TAP mogą bezpiecznie założyć, że zwracane zadanie jest aktywne i nie należy próbować wywołać <xref:System.Threading.Tasks.Task.Start%2A> na dowolnym <xref:System.Threading.Tasks.Task> zwrócone z metody wzorca TAP. Wywoływanie <xref:System.Threading.Tasks.Task.Start%2A> na aktywnym zadaniu powoduje <xref:System.InvalidOperationException> wyjątku.  
  
## <a name="cancellation-optional"></a>Anulowanie (opcjonalnie)  
 We wzorcu TAP anulowanie jest opcjonalne dla implementatorów metody asynchronicznej i konsumentów metody asynchronicznej. Jeśli operacja umożliwia anulowanie, udostępnia ona przeciążenie metody asynchronicznej, która akceptuje tokenu anulowania (<xref:System.Threading.CancellationToken> wystąpienie). Umownie ten parametr nosi `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Operacja asynchroniczna monitoruje ten token pod kątem żądań anulowania. Jeśli odbierze żądanie anulowania, może je zaakceptować i anulować operację. Jeśli żądanie anulowania skutkuje przedwcześnie zakończoną pracą, metoda wzorca TAP zwraca zadanie, które kończy się <xref:System.Threading.Tasks.TaskStatus.Canceled> stanie; nie ma żadnego dostępnego wyniku, i jest zgłaszany żaden wyjątek.  <xref:System.Threading.Tasks.TaskStatus.Canceled> Stanu jest uważany za stan końcowy (ukończenie) zadania, wraz z <xref:System.Threading.Tasks.TaskStatus.Faulted> i <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stanów. W związku z tym jeśli znajduje się ono w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu, jego <xref:System.Threading.Tasks.Task.IsCompleted%2A> właściwość zwraca `true`. Kiedy zadanie zostanie ukończone w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu, wszelkie kontynuacje zarejestrowane dla zadania są planowane lub wykonywane, chyba, że opcja kontynuacji, takich jak <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> została określona w celu rezygnacji z kontynuacji. Wszelki kod, który asynchronicznie oczekuje na anulowane zadanie poprzez korzystanie z funkcji języka, kontynuuje działanie, ale odbiera <xref:System.OperationCanceledException> lub wyjątek pochodzić od niego. Kod, który jest zablokowany, synchronicznie oczekuje na zadanie za pomocą metody takie jak <xref:System.Threading.Tasks.Task.Wait%2A> i <xref:System.Threading.Tasks.Task.WaitAll%2A> również kontynuuje działanie z powodu wyjątku.  
  
 Jeśli token odwołania zażądał anulowania przed metodą wzorca TAP, akceptującego wywołanie tokenu, metoda wzorca TAP powinna zwrócić <xref:System.Threading.Tasks.TaskStatus.Canceled> zadania.  Jeśli jednak żądanie anulowania zostanie zgłoszone, gdy trwa operacja asynchroniczna, operacja asynchroniczna nie musi akceptować żądania anulowania.  Zwrócone zadanie powinno zakończyć <xref:System.Threading.Tasks.TaskStatus.Canceled> stan tylko, jeśli operacja kończy się w wyniku żądania anulowania. Jeśli zażądano anulowania, ale wynik lub wyjątek nadal jest generowany, zadanie powinno zakończyć <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> lub <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu. 
 
 W przypadku metod asynchronicznych, które ma zostać uwidoczniona możliwość przede wszystkim anulowane nie trzeba dostarczać przeciążenia, które nie akceptują token anulowania. W przypadku metod, które nie mogą być anulowane, nie należy dostarczać przeciążeń, które akceptują token anulowania. Pomaga to wskazać obiektowi wywołującemu, czy metodę docelową można w rzeczywistości anulować.  Kod konsumenta, który nie wymaga anulowania, może wywołać metodę, która akceptuje <xref:System.Threading.CancellationToken> i podaj <xref:System.Threading.CancellationToken.None%2A> jako wartość argumentu. <xref:System.Threading.CancellationToken.None%2A> jest funkcjonalnie odpowiada domyślnemu <xref:System.Threading.CancellationToken>.  
  
## <a name="progress-reporting-optional"></a>Raportowanie postępu (opcjonalnie)  
 Niektóre operacje asynchroniczne korzystają z dostarczania powiadomień na temat postępu. Zazwyczaj są one używane do aktualizowania interfejsu użytkownika za pomocą informacji o postępie operacji asynchronicznej. 
 
 We wzorcu TAP postęp jest obsługiwany za pośrednictwem <xref:System.IProgress%601> interfejs, który jest przekazywany do metody asynchronicznej jako parametr, który zazwyczaj jest on nazywany `progress`.  Dostarczenie interfejsu postępu, gdy wywoływana jest metoda asynchroniczna, pomaga wyeliminować sytuację wyścigu, która wynika z niepoprawnego użycia (tzn. kiedy obsługa zdarzeń, która jest niepoprawnie rejestrowana po rozpoczęciu operacji, może pominąć aktualizacje).  Co więcej, interfejs postępu obsługuje różne implementacje postępu, co zostało określone przez kod konsumencki.  Kod konsumencki może uwzględniać tylko najnowszą aktualizację postępu lub może buforować wszystkie aktualizacje. Może on wywołać akcję dla każdej aktualizacji lub może określać, czy wywołanie jest przekazywane do określonego wątku. Te opcje można osiągnąć przy użyciu różnej implementacji interfejsu, dostosowanej do potrzeb danego konsumenta.  Jak w przypadku anulowania, implementacje wzorca TAP powinny dostarczyć <xref:System.IProgress%601> parametru tylko wtedy, gdy interfejs API obsługuje powiadomienia o postępie. 
 
 Na przykład jeśli `ReadAsync` metoda omówionych wcześniej w tym artykule jest w stanie zgłosić pośredni postęp w postaci liczby bajtów do tej pory, wywołanie zwrotne postępu może być <xref:System.IProgress%601> interfejsu:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Jeśli `FindFilesAsync` metoda zwraca listę wszystkich plików, które spełniają określony wzorzec wyszukiwania, wywołanie zwrotne postępu może dostarczyć oszacować procent pracy wykonanej, a także bieżący zestaw wyników częściowych.  Może to zrobić za pomocą spójnej kolekcji:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 lub za pomocą typu danych specyficznego dla interfejsu API:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 W tym ostatnim przypadku specjalny typ danych ma zazwyczaj sufiks `ProgressInfo`.  
  
 Jeśli implementacje wzorca TAP dostarczają przeciążenia, które przyjmują `progress` parametru, muszą one umożliwić argumentowi `null`, w którym to przypadku będą raportowane żadnego postępu. Implementacje wzorca TAP powinny raportować postęp do <xref:System.Progress%601> synchronicznie, obiekt, który umożliwia metodzie asynchronicznej szybkie dostarczanie postępu i umożliwia konsumentowi postępu ustalenie, jak i gdzie najlepiej obsługiwać informacje. Na przykład wystąpienie postępu może wybrać przekazywanie wywołań zwrotnych i generowanie zdarzeń w kontekście przechwyconych synchronizacji.  
  
## <a name="iprogresst-implementations"></a>IProgress\<T > implementacji  
 .NET Framework 4.5 zapewnia pojedynczy <xref:System.IProgress%601> implementacja: <xref:System.Progress%601>. <xref:System.Progress%601> Klasy jest zadeklarowana w następujący sposób:  
  
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
  
 Wystąpienie <xref:System.Progress%601> udostępnia <xref:System.Progress%601.ProgressChanged> zdarzenie, które jest wywoływane za każdym razem, gdy operacja asynchroniczna raportuje aktualizację postępu. <xref:System.Progress%601.ProgressChanged> Zdarzenie jest zgłaszane w <xref:System.Threading.SynchronizationContext> obiektu, który został przechwycony podczas <xref:System.Progress%601> tworzenia wystąpienia. Jeśli kontekst synchronizacji nie był dostępny, używany jest domyślny kontekst ukierunkowany na pulę wątków. Z tym zdarzeniem można zarejestrować programy obsługi. Pojedynczy program obsługi może również być przewidziane do <xref:System.Progress%601> konstruktora dla wygody i zachowuje się podobnie jak program obsługi zdarzeń dla <xref:System.Progress%601.ProgressChanged> zdarzeń. Aktualizacje postępu są wywoływane asynchronicznie, aby unikać opóźniania operacji asynchronicznej podczas wykonywania obsługi zdarzeń. Inny <xref:System.IProgress%601> wdrażania można wybrać do zaimplementowania innej semantyki.  
  
## <a name="choosing-the-overloads-to-provide"></a>Wybieranie przeciążeń do dostarczenia  
 Jeśli implementacja wzorca TAP używane zarówno opcjonalne <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> i opcjonalne <xref:System.IProgress%601> parametrów, może to wymagać do czterech przeciążeń:  
  
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
  
 Aby zrekompensować Brak dwóch pośrednich kombinacji, deweloperzy mogą przekazywać <xref:System.Threading.CancellationToken.None%2A> lub domyślną <xref:System.Threading.CancellationToken> dla `cancellationToken` parametru i `null` dla `progress` parametru.  
  
 Jeśli każde użycie metody wzorca TAP ma obsługiwać anulowanie lub postęp, możesz pominąć przeciążenia, które nie akceptują odpowiedniego parametru.  
  
 Jeśli ma być uwidacznianych wiele przeciążeń, dzięki czemu anulowanie lub postęp opcjonalny, przeciążenia, które nie obsługują anulowania lub postępu powinny zachowywać się, jak gdyby przekazywały <xref:System.Threading.CancellationToken.None%2A> anulowania lub `null` dla postępu do przeciążenia, które je obsługuje.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wzorce programowania asynchronicznego](../../../docs/standard/asynchronous-programming-patterns/index.md)|Wprowadza trzy wzorce do wykonywania operacji asynchronicznych: asynchroniczny wzorzec oparty na zadaniach (TAP), asynchroniczny model programowania (APM) i asynchroniczny wzorzec oparty na zdarzeniach (EAP).|  
|[Implementowanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Opis sposobu implementacji asynchronicznego wzorca opartego na zadaniach (TAP), którą można przeprowadzić na trzy sposoby: za pomocą kompilatorów języków C# i Visual Basic w programie Visual Studio, ręcznie lub za pomocą kombinacji metod kompilatora i manualnych.|  
|[Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Opis sposobu używania zadań i wywołań zwrotnych w celu osiągnięcia oczekiwania bez blokowania.|  
|[Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Opis sposobu używania asynchronicznego wzorca opartego na zadaniach (TAP) w celu implementacji asynchronicznego modelu programowania (APM) i asynchronicznego wzorca opartego na zdarzeniach (EAP).|
