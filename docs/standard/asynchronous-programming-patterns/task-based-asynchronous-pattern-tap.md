---
title: Wzorzec asynchroniczny oparty na zadaniach (TAP)
ms.date: 03/30/2017
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
ms.openlocfilehash: fe69943a6f87bbbb7f29d1e4d6d30c26709725d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579018"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Wzorzec asynchroniczny oparty na zadaniach (TAP)
Na podstawie jest oparty na zadaniach asynchronicznej wzorca (TAP) <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> typy w <xref:System.Threading.Tasks?displayProperty=nameWithType> przestrzeni nazw, które są używane do reprezentowania dowolnego operacji asynchronicznych. Wzorzec TAP jest zalecanym asynchronicznym wzorcem projektowym dla nowych prac deweloperskich.  
  
## <a name="naming-parameters-and-return-types"></a>Nazewnictwo, parametry i typy zwracane  
 We wzorcu TAP do tworzenia wystąpienia i wykonywania operacji asynchronicznej jest używana jedna metoda. Dzięki temu nie trzeba modelu programowania asynchronicznego (APM lub `IAsyncResult`) wzorzec, który wymaga `Begin` i `End` metod i z kolei oparty na zdarzeniach wzorca asynchronicznego (EAP), który wymaga metody, która ma `Async`sufiks domeny i wymaga także co najmniej jednego zdarzenia, typów obiektu delegowanego obsługi zdarzeń, a `EventArg`-typów pochodnych. Obejmują metod asynchronicznych w NACIŚNIJ `Async` sufiks po nazwie operacji; na przykład `GetAsync` dla `Get` operacji. W przypadku dodawania wybierz metodę do klasy, która zawiera już tę nazwę metody z `Async` sufiks, Użyj sufiksu `TaskAsync` zamiast tego. Na przykład, jeśli klasa już `GetAsync` metody, należy użyć nazwy `GetTaskAsync`.  
  
 Wybierz metodę zwraca albo <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, na podstawie tego, czy odpowiedniej metody synchroniczne zwraca typ void lub typu `TResult`.  
  
 Parametry metody wzorca TAP powinny odpowiadać parametrom jej synchronicznego odpowiednika i powinny być podane w tej samej kolejności.  Jednak `out` i `ref` parametry są wyjątkiem od tej reguły i należy unikać całkowicie. Dane, które mogłyby być zwracane za pośrednictwem `out` lub `ref` parametru powinny być zwracane w ramach `TResult` zwrócony przez <xref:System.Threading.Tasks.Task%601>i powinna być używana spójnej kolekcji lub struktury danych niestandardowych do uwzględnienia wielu wartości. 
 
 Metody, które są przeznaczone wyłącznie do tworzenia, manipulowanie lub kombinację zadania (gdzie wyczyść nazwę metody lub nazwę typu, do którego należy metody jest celem asynchronicznej metody) nie należy wykonać czynności ten wzorzec nazewnictwa; metody te są często nazywane *combinators*. Przykłady combinators <xref:System.Threading.Tasks.Task.WhenAll%2A> i <xref:System.Threading.Tasks.Task.WhenAny%2A>i opisano w [przy użyciu opartego na zadaniach wbudowanych Combinators](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) sekcji tego artykułu [wykorzystywanie opartego na zadaniach wzorca asynchronicznego](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 Przykłady sposobu składni NACIŚNIJ różni się od składni używanej w starszej wersji wzorce programowania asynchronicznego takich jak asynchronicznego programowania modelu (APM) i oparty na zdarzeniach asynchroniczny wzorzec (EAP), zobacz [wzorce programowania asynchronicznego ](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Inicjowanie operacji asynchronicznej  
 Metoda asynchroniczna oparta na wzorcu TAP może wykonać synchronicznie niewielką ilość pracy, na przykład weryfikację argumentów i inicjowanie operacji asynchronicznej, zanim zwróci zadanie wynikowe. Praca synchroniczna powinna być ograniczona do minimum, tak aby metoda asynchroniczna mogła szybko zwracać wynik. Powody oczekiwania szybkiego zwrócenia wyniku to m.in.:  
  
-   Metody asynchroniczne mogą być wywoływane z wątków interfejsu użytkownika (UI), a jakakolwiek długotrwała praca synchroniczna może niekorzystnie wpływać na czas reakcji aplikacji.  
  
-   Wiele metod asynchronicznych może zostać uruchomionych jednocześnie. W związku z tym jakakolwiek długotrwała praca synchroniczna metody asynchronicznej może opóźnić zainicjowanie innych operacji asynchronicznych, zmniejszając w ten sposób korzyści płynące ze współbieżności.  
  
 W niektórych przypadkach nakład pracy wymagany do ukończenia operacji jest mniejszy niż ilość pracy potrzebna do asynchronicznego uruchomienia operacji. Przykładem takiego scenariusza jest odczyt ze strumienia, gdzie operacja odczytu może się odbyć dzięki danym buforowanym już w pamięci. W takich przypadkach operacja może zakończyć się synchronicznie i może zwracać zadanie, które zostało już zakończone.  
  
## <a name="exceptions"></a>Wyjątki  
 Metoda asynchroniczna powinna zgłosić wyjątek z wywołania metody asynchronicznej tylko w odpowiedzi na błąd użycia. Błędy użycia nie powinny nigdy występować w kodzie produkcyjnym. Na przykład, jeśli przekazywanie odwołanie o wartości null (`Nothing` w języku Visual Basic) jako jeden z argumentów metody powoduje, że stan błędu (zazwyczaj reprezentowany przez <xref:System.ArgumentNullException> wyjątku), można zmodyfikować kod wywołujący, aby upewnić się, że nigdy nie jest przekazywany odwołanie o wartości null. W przypadku innych błędów wyjątki, które występują, gdy uruchomiona jest metoda asynchroniczna, powinny być przypisane do zwracanego zadania, nawet jeśli metoda asynchroniczna jest wykonywana synchronicznie przed zwróceniem zadania. Zadanie zawiera zazwyczaj co najwyżej jeden wyjątek. Jednak jeśli zadanie reprezentuje wiele operacji (na przykład <xref:System.Threading.Tasks.Task.WhenAll%2A>), wiele wyjątków może być skojarzony z jednego zadania.  
  
## <a name="target-environment"></a>Środowisko docelowe  
 Podczas implementacji metody wzorca TAP można określić, gdzie występuje wykonanie asynchroniczne. Można wybrać opcję wykonania operacji w puli wątków, zaimplementować je za pomocą asynchronicznego wejścia/wyjścia (bez powiązania z wątkiem dla większości wykonywanych operacji), uruchomić je w określonym wątku (na przykład wątku interfejsu użytkownika) lub użyć dowolnej liczby potencjalnych kontekstów. Metoda NACIŚNIJ może nawet nie mają nic wspólnego do wykonania i tylko może zwrócić <xref:System.Threading.Tasks.Task> reprezentujący wystąpienie warunek z innym w systemie (na przykład zadanie reprezentujące danych otrzymywanych przez to struktura danych umieszczonych w kolejce).
 
 Obiekt wywołujący metody NACIŚNIJ może zablokować oczekiwania dla metody NACIŚNIJ zakończenie poprzez synchronicznie oczekiwania w zadaniu wynikowym lub może uruchomić kod dodatkowe (kontynuacji), po zakończeniu operacji asynchronicznej. Twórca kodu kontynuacji ma kontrolę nad tym, gdzie ten kod jest wykonywany. Możesz utworzyć kod kontynuacji albo jawnie, za pomocą metody na <xref:System.Threading.Tasks.Task> klasy (na przykład <xref:System.Threading.Tasks.Task.ContinueWith%2A>) lub niejawnie, przy użyciu obsługi języków, rozszerzający kontynuacje (na przykład `await` w języku C# `Await` w Języka Visual Basic, `AwaitValue` w języku F #).  
  
## <a name="task-status"></a>Stan zadania  
 <xref:System.Threading.Tasks.Task> Klasy zawiera cykl życia dla operacji asynchronicznych i cyklu jest reprezentowana przez <xref:System.Threading.Tasks.TaskStatus> wyliczenia. Do obsługi sytuacjach wyjątkowych typów wyprowadzonych z <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601>i obsługuje separację konstrukcji z planowania, <xref:System.Threading.Tasks.Task> klasy ujawnia <xref:System.Threading.Tasks.Task.Start%2A> metody. Zadania, które zostały utworzone przy użyciu publicznego <xref:System.Threading.Tasks.Task> konstruktory są określane jako *zimnych zadania*, ponieważ rozpoczęciem ich cyklu życia w nieregularne <xref:System.Threading.Tasks.TaskStatus.Created> stanu i są zaplanowane tylko wtedy, gdy <xref:System.Threading.Tasks.Task.Start%2A> jest wywoływana w te wystąpienia. 
 
 Inne zadania rozpocząć ich cyklu życia w stanie dynamicznej, co oznacza, że operacje asynchroniczne reprezentują one już zostało zainicjowane i ich stan zadania jest inny niż wartość wyliczenia <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>. Wszystkie zadania, które są zwracane z metod wzorca TAP, muszą być aktywowane. **Jeśli metoda NACIŚNIJ wewnętrznie używa konstruktora zadania można utworzyć wystąpienia zadania, które ma zostać zwrócona, należy wywołać metodę NACIŚNIJ <xref:System.Threading.Tasks.Task.Start%2A> na <xref:System.Threading.Tasks.Task> obiektu przed zwróceniem.** Konsumentów metody NACIŚNIJ bezpiecznie może założyć, że zadanie zwracane jest aktywne i nie należy próbować wywołać <xref:System.Threading.Tasks.Task.Start%2A> na dowolnym <xref:System.Threading.Tasks.Task> która jest zwracana z metody NACIŚNIJ. Wywoływanie <xref:System.Threading.Tasks.Task.Start%2A> na aktywne zadanie powoduje <xref:System.InvalidOperationException> wyjątku.  
  
## <a name="cancellation-optional"></a>Anulowanie (opcjonalnie)  
 We wzorcu TAP anulowanie jest opcjonalne dla implementatorów metody asynchronicznej i konsumentów metody asynchronicznej. Jeśli operacja pozwala na anulowanie, udostępnia ona przeciążenia metody asynchroniczne, który akceptuje token anulowania (<xref:System.Threading.CancellationToken> wystąpienie). Konwencja, parametr o nazwie `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Operacja asynchroniczna monitoruje ten token pod kątem żądań anulowania. Jeśli odbierze żądanie anulowania, może je zaakceptować i anulować operację. Jeśli żądanie anulowania powoduje przedwcześnie zakończył pracę, metoda NACIŚNIJ zwraca klasę task, która kończy się <xref:System.Threading.Tasks.TaskStatus.Canceled> stanie; nie ma żadnych dostępnych wyników i nie jest wyjątek.  <xref:System.Threading.Tasks.TaskStatus.Canceled> Stanu jest uznawany za stan końcowy (ukończone) dla zadania, wraz z <xref:System.Threading.Tasks.TaskStatus.Faulted> i <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> stanów. W związku z tym jeśli zadanie jest w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu, jego <xref:System.Threading.Tasks.Task.IsCompleted%2A> zwraca właściwość `true`. Po ukończeniu zadania w <xref:System.Threading.Tasks.TaskStatus.Canceled> stanu dowolnego kontynuacje zarejestrowany z zadaniem są zaplanowane lub wykonane w chyba że utrzymania takie jak opcja <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> określono rezygnacji z kontynuacji. Każdy kod asynchronicznie oczekuje dla anulowanych zadań przy użyciu funkcji języka jest nadal uruchomiona, ale odbiera <xref:System.OperationCanceledException> lub wyjątek pochodzić od niego. Kod, który jest zablokowany synchronicznie oczekiwanie na zadanie za pomocą metody takie jak <xref:System.Threading.Tasks.Task.Wait%2A> i <xref:System.Threading.Tasks.Task.WaitAll%2A> również kontynuować działanie z powodu wyjątku.  
  
 Jeśli token anulowania zażądał anulowania przed wywołaniem metody NACIŚNIJ akceptującego token jest wywoływana, metoda NACIŚNIJ powinna zwrócić <xref:System.Threading.Tasks.TaskStatus.Canceled> zadań.  Jeśli jednak żądanie anulowania zostanie zgłoszone, gdy trwa operacja asynchroniczna, operacja asynchroniczna nie musi akceptować żądania anulowania.  Zadanie zwrócone powinien kończyć się <xref:System.Threading.Tasks.TaskStatus.Canceled> stan tylko, jeśli operacja kończy się w wyniku żądania anulowania. Jeśli zażądano anulowania, ale wynik lub wyjątek nadal jest generowany, zadanie powinien kończyć się <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> lub <xref:System.Threading.Tasks.TaskStatus.Faulted> stanu. 
 
 Dla metod asynchronicznych, które mają być ujawnia możliwość anulowane przede wszystkim nie trzeba podać przeciążenia, które nie akceptuje token anulowania. W przypadku metod, które nie mogą być anulowane, nie należy dostarczać przeciążeń, które akceptują token anulowania. Pomaga to wskazać obiektowi wywołującemu, czy metodę docelową można w rzeczywistości anulować.  Kod użytkownika, który nie potrzeby anulowania może wywołać metodę, która akceptuje <xref:System.Threading.CancellationToken> i podaj <xref:System.Threading.CancellationToken.None%2A> jako wartość argumentu. <xref:System.Threading.CancellationToken.None%2A> jest funkcjonalnym odpowiednikiem domyślnie <xref:System.Threading.CancellationToken>.  
  
## <a name="progress-reporting-optional"></a>Raportowanie postępu (opcjonalnie)  
 Niektóre operacje asynchroniczne korzystają z dostarczania powiadomień na temat postępu. Zazwyczaj są one używane do aktualizowania interfejsu użytkownika za pomocą informacji o postępie operacji asynchronicznej. 
 
 W PRZYŁOŻENIU postępu odbywa się za pośrednictwem <xref:System.IProgress%601> interfejsu, który jest przekazywany do metody asynchronicznej jako parametr o nazwie zwykle `progress`.  Dostarczenie interfejsu postępu, gdy wywoływana jest metoda asynchroniczna, pomaga wyeliminować sytuację wyścigu, która wynika z niepoprawnego użycia (tzn. kiedy obsługa zdarzeń, która jest niepoprawnie rejestrowana po rozpoczęciu operacji, może pominąć aktualizacje).  Co więcej, interfejs postępu obsługuje różne implementacje postępu, co zostało określone przez kod konsumencki.  Kod konsumencki może uwzględniać tylko najnowszą aktualizację postępu lub może buforować wszystkie aktualizacje. Może on wywołać akcję dla każdej aktualizacji lub może określać, czy wywołanie jest przekazywane do określonego wątku. Te opcje można osiągnąć przy użyciu różnej implementacji interfejsu, dostosowanej do potrzeb danego konsumenta.  Zgodnie z anulowania, powinno dostarczyć implementacje NACIŚNIJ <xref:System.IProgress%601> parametru tylko wtedy, gdy interfejs API obsługuje powiadomienia postępu. 
 
 Na przykład jeśli `ReadAsync` metody omówione w tym artykule jest może zgłosić pośredniego postęp w postaci liczby bajtów do odczytu pory, postęp wywołania zwrotnego może być <xref:System.IProgress%601> interfejsu:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Jeśli `FindFilesAsync` metoda zwraca listę wszystkich plików spełniających wzorzec wyszukiwania w szczególności, wywołania zwrotnego postęp można podać szacunkowe procent wykonania oraz bieżącego zestawu wyników częściowych.  Może to zrobić za pomocą spójnej kolekcji:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 lub za pomocą typu danych specyficznego dla interfejsu API:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 W drugim przypadku specjalny typ danych jest zazwyczaj z sufiksem `ProgressInfo`.  
  
 Jeśli implementacje NACIŚNIJ Podaj przeciążenia, które przyjmują `progress` parametru także muszą zezwalać argumentu w `null`, w którym to przypadku należy podać żadnego postępu. NACIŚNIJ implementacje powinny raportu postępu do <xref:System.Progress%601> obiekt synchronicznie, co pozwala metoda asynchroniczna szybko zapewnić postępu, a następnie poczekanie konsumenta postęp ustalenie, jak i gdzie najlepiej do obsługi danych. Na przykład wystąpienie postępu może wybrać przekazywanie wywołań zwrotnych i generowanie zdarzeń w kontekście przechwyconych synchronizacji.  
  
## <a name="iprogresst-implementations"></a>IProgress\<T > implementacji  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Zapewnia jeden <xref:System.IProgress%601> implementacja: <xref:System.Progress%601>. <xref:System.Progress%601> Klasy jest zadeklarowany w następujący sposób:  
  
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
  
 Wystąpienie <xref:System.Progress%601> przedstawia <xref:System.Progress%601.ProgressChanged> zdarzenie, które jest wywoływane każdorazowo operację asynchroniczną raportów aktualizacji postępu. <xref:System.Progress%601.ProgressChanged> Zdarzenie jest zgłaszane przy <xref:System.Threading.SynchronizationContext> obiekt, który zostało przechwycone podczas <xref:System.Progress%601> wystąpienie zostało utworzone. Jeśli kontekst synchronizacji nie był dostępny, używany jest domyślny kontekst ukierunkowany na pulę wątków. Z tym zdarzeniem można zarejestrować programy obsługi. Pojedynczy obsługi mogą być również dostarczane do <xref:System.Progress%601> konstruktora dla wygody i zachowuje się jak program obsługi zdarzeń dla <xref:System.Progress%601.ProgressChanged> zdarzeń. Aktualizacje postępu są wywoływane asynchronicznie, aby unikać opóźniania operacji asynchronicznej podczas wykonywania obsługi zdarzeń. Inny <xref:System.IProgress%601> można zastosować semantykę różną implementacji.  
  
## <a name="choosing-the-overloads-to-provide"></a>Wybieranie przeciążeń do dostarczenia  
 Jeśli implementacja NACIŚNIJ używa zarówno opcjonalne <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> i opcjonalne <xref:System.IProgress%601> parametrów go może potencjalnie wymagać maksymalnie cztery przeciążenia:  
  
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
  
 Kompensacji dwa brakuje pośredniego kombinacje, deweloperzy mogą przechodzić <xref:System.Threading.CancellationToken.None%2A> lub domyślnego <xref:System.Threading.CancellationToken> dla `cancellationToken` parametru i `null` dla `progress` parametru.  
  
 Jeśli każde użycie metody wzorca TAP ma obsługiwać anulowanie lub postęp, możesz pominąć przeciążenia, które nie akceptują odpowiedniego parametru.  
  
 Jeśli zdecydujesz się ujawnia wielu przeciążeń powoduje anulowanie lub postępu opcjonalne, przeciążeń, które nie obsługują anulowania lub postępu powinny działać tak, jakby one przekazywane <xref:System.Threading.CancellationToken.None%2A> anulowania lub `null` postępu do przeciążenia który je obsługiwać.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wzorce programowania asynchronicznego](../../../docs/standard/asynchronous-programming-patterns/index.md)|Wprowadza trzy wzorce do wykonywania operacji asynchronicznych: asynchroniczny wzorzec oparty na zadaniach (TAP), asynchroniczny model programowania (APM) i asynchroniczny wzorzec oparty na zdarzeniach (EAP).|  
|[Implementowanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Opis sposobu implementacji asynchronicznego wzorca opartego na zadaniach (TAP), którą można przeprowadzić na trzy sposoby: za pomocą kompilatorów języków C# i Visual Basic w programie Visual Studio, ręcznie lub za pomocą kombinacji metod kompilatora i manualnych.|  
|[Wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Opis sposobu używania zadań i wywołań zwrotnych w celu osiągnięcia oczekiwania bez blokowania.|  
|[Współdziałanie z innymi wzorcami asynchronicznymi i typami](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Opis sposobu używania asynchronicznego wzorca opartego na zadaniach (TAP) w celu implementacji asynchronicznego modelu programowania (APM) i asynchronicznego wzorca opartego na zdarzeniach (EAP).|
