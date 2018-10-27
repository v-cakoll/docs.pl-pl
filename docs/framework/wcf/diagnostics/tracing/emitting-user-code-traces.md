---
title: Emitowanie danych śledzenia elementu User-Code
ms.date: 03/30/2017
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
ms.openlocfilehash: 0664c11d8020ee5e712ce6d4843c85a1f30b11a3
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50049168"
---
# <a name="emitting-user-code-traces"></a>Emitowanie danych śledzenia elementu User-Code
Oprócz włączenia śledzenia w konfiguracji, aby zebrać dane Instrumentacji wygenerowane przez Windows Communication Foundation (WCF), można również wysyłać ślady programowo w kodzie użytkownika. W ten sposób można utworzyć z wyprzedzeniem danych instrumentacji, które można przejrzeć w dalszej części w celu diagnostyki. W tym temacie omówiono, jak to zrobić.  
  
 Ponadto [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md) przykład obejmuje cały kod, przedstawione w poniższych sekcjach.  
  
## <a name="creating-a-trace-source"></a>Tworzenie źródła śledzenia  
 Poniższy kod służy do utworzenia źródła śledzenia użytkowników.  
  
```csharp
TraceSource ts = new TraceSource("myUserTraceSource");  
```  
  
## <a name="creating-activities"></a>Tworzenie działań  
 Działania to jednostka logiczna przetwarzania. Możesz utworzyć jedno działanie, dla każdej jednostki główne przetwarzania, w którym chcesz śladów, aby być zgrupowane razem. Na przykład można utworzyć jedno działanie dla każdego żądania do usługi. Aby to zrobić, wykonaj następujące czynności.  
  
1.  Zapisz identyfikator działania w zakresie.  
  
2.  Utwórz nowy identyfikator działania.  
  
3.  Transfer z działania w zakresie na nową, Ustaw nowe działanie w zakresie i emitować Rozpocznij śledzenie dla tego działania.  
  
 Poniższy kod pokazuje, jak to zrobić.  
  
```csharp
Guid oldID = Trace.CorrelationManager.ActivityId;  
Guid traceID = Guid.NewGuid();  
ts.TraceTransfer(0, "transfer", traceID);  
Trace.CorrelationManager.ActivityId = traceID; // Trace is static  
ts.TraceEvent(TraceEventType.Start, 0, "Add request");  
```  
  
## <a name="emitting-traces-within-a-user-activity"></a>Emitowanie danych śledzenia w aktywność użytkownika  
 Poniższy kod generuje ślady wewnątrz działania użytkownika.  
  
```csharp
double value1 = 100.00D;  
double value2 = 15.99D;  
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);  
double result = client.Add(value1, value2);  
ts.TraceInformation("Client receives Add response '" + result + "'");  
```  
  
## <a name="stopping-the-activities"></a>Zatrzymywanie działania  
 Aby zatrzymać działania, transfer powrót do starych działań, Zatrzymaj bieżący identyfikator działania i zresetować stary identyfikator działania w zakresie.  
  
 Poniższy kod pokazuje, jak to zrobić.  
  
```csharp
ts.TraceTransfer(0, "transfer", oldID);  
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");  
Trace.CorrelationManager.ActivityId = oldID;  
```  
  
## <a name="propagating-the-activity-id-to-a-service"></a>Propagowanie identyfikator działania usługi  
 Jeśli ustawisz `propagateActivity` atrybutu `true` dla `System.ServiceModel` plików źródła śledzenia w konfiguracji klienta i usługi, usługi przetwarzania dla żądania Dodaj odbywa się w tym samym działaniu, jak ten zdefiniowany w obiekcie klienta. Jeśli usługa definiuje własne działania i transferu danych śledzenia usługi nie są wyświetlane w działaniu propagowane przez klienta. Zamiast tego są wyświetlane w działaniu Skorelowane przez ślady transferu do działania, których identyfikator jest propagowany przez klienta.  
  
> [!NOTE]
>  Jeśli `propagateActivity` ma ustawioną wartość atrybutu `true` na klienta i usługi, działania otoczenia w zakresie operacji usługi jest ustawiana przez architekturę WCF.  
  
 Poniższy kod służy do sprawdzenia, czy działanie zostało ustawione w zakresie przez architekturę WCF.  
  
```csharp
// Check if an activity was set in scope by WCF, if it was   
// propagated from the client. If not, ( ambient activity is   
// equal to Guid.Empty), create a new one.  
if(Trace.CorrelationManager.ActivityId == Guid.Empty)  
{  
    Guid newGuid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = newGuid;  
}  
// Emit your Start trace.  
ts.TraceEvent(TraceEventType.Start, 0, "Add Activity");  
  
// Emit the processing traces for that request.  
serviceTs.TraceInformation("Service receives Add "   
                            + n1 + ", " + n2);  
// double result = n1 + n2;  
serviceTs.TraceInformation("Service sends Add result" + result);  
  
// Emit the Stop trace and exit the method scope.  
ts.TraceEvent(TraceEventType.Stop, 0, "Add Activity");  
// return result;  
```  
  
## <a name="tracing-exceptions-thrown-in-code"></a>Śledzenie wyjątków zgłoszonych w kodzie  
 Gdy zgłoszenie wyjątku w kodzie, można również śledzenia wyjątków na poziomie ostrzeżenia lub przy użyciu następującego kodu.  
  
```csharp
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");  
```  
  
## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Wyświetlanie śladów użytkownika w narzędziu Podgląd śledzenia usługi  
 Ta sekcja zawiera zrzuty ekranu przedstawiające śledzenie wygenerowane przez uruchomienie [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md) przykładowy, gdy wyświetlany w przeglądarce [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Na poniższym diagramie aktywności "Dodaj żądanie" utworzony wcześniej wybranego na lewym panelu. Jest ona wyświetlana z trzech innych matematycznych operacji działań (dzielenie, odejmowanie, mnożenie) wchodzących w skład programu klienckiego aplikacji. Kod użytkownika został zdefiniowany jeden nowe działanie dla każdej operacji do izolowania potencjalnych wystąpienia błędów w innych żądań.  
  
 Aby zademonstrować użycie transfery [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md) próbki, działanie Kalkulator, który hermetyzuje żądania operacji cztery tworzona jest również. Dla każdego żądania jest transferu i z powrotem z działania kalkulatora działania żądania (śledzenia jest wyróżniony w górnym prawym panelu na rysunku).  
  
 Po wybraniu do działania w lewym panelu, ślady dołączane przez to działanie są wyświetlane w prawym górnym panelu. Jeśli `propagateActivity` jest `true` w każdym punkcie końcowym ścieżki żądania są ślady w działaniu żądania od wszystkich procesów, które uczestniczą w żądaniu. W tym przykładzie widać śladów od klienta i usługi w kolumnie 4. w panelu.  
  
 To działanie pokazano w następującej kolejności przetwarzania:  
  
1.  Klient wysyła komunikat do dodania.  
  
2.  Usługa odbiera komunikat żądania Dodaj.  
  
3.  Dodaj odpowiedzi wysyłane przez usługę.  
  
4.  Klient odbiera odpowiedź Dodaj.  
  
 Ślady te zostały emitowane na poziomie informacji. Klikając śledzenia w prawym górnym rogu panelu zawiera szczegółowe informacje o tym śledzenia w dolnym prawym panelu.  
  
 Na poniższym diagramie Widzimy również ślady transferu, od i do działania Kalkulatora, a także dwie pary uruchomienia i zatrzymania śledzenia na działanie żądania: jeden dla klienta, a drugi dla usługi, (po jednym dla każdego źródła śledzenia).  
  
 ![Przeglądarki danych śledzenia: Emitowanie użytkownika&#45;kodu ślady](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd")  
Listę działań w oparciu o czas utworzenia (panelu po lewej stronie) oraz ich zagnieżdżonych działania (w prawym górnym rogu panelu)  
  
 Jeśli kod usługi zgłasza wyjątek, który powoduje, że klient throw również (na przykład, gdy klient nie uzyskano odpowiedź na żądanie), w tym samym działaniu dla bezpośrednia korelacja wystąpić, zarówno usługi i klienta, ostrzeżenie lub komunikaty o błędach. Na poniższym diagramie usługa zgłasza wyjątek informacją "Usługa odmówi przetworzenia tego żądania, w kodzie użytkownika." Klient również zgłasza wyjątek, informacją "serwer nie może przetworzyć żądania z powodu błędu wewnętrznego."  
  
 ![Używanie przeglądarki danych śledzenia do emitowania użytkownika&#45;kodu ślady](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace2.gif "e2eTrace2")  
Błędy w obrębie punktów końcowych dla danego żądania są wyświetlane w tym samym działaniu, gdy został rozpropagowany identyfikator działania żądania  
  
 Dwukrotne kliknięcie wielokrotnie działania na lewym panelu pokazuje kolejnym wykresie ślady mnożenia działanie dla każdego procesu, które są zaangażowani. Można zauważyć, że najpierw wystąpiło ostrzeżenie w punkcie usług (wystąpienie wyjątku), który następuje ostrzeżeń i błędów na komputerze klienckim, ponieważ nie można przetworzyć żądania. Dlatego firma Microsoft oznaczać błąd przyczynowego relacji między punktami końcowymi i pochodzić główną przyczynę tego błędu.  
  
 ![Używanie przeglądarki danych śledzenia do emitowania użytkownika&#45;kodu ślady](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace3.gif "e2eTrace3")  
Widok wykresu korelacji błąd  
  
 Uzyskanie ślady poprzedniego, ustawiliśmy `ActivityTracing` dla źródła śledzenia użytkowników i `propagateActivity=true` dla `System.ServiceModel` źródła śledzenia. Firma Microsoft nie ustawiła prawidłowo `ActivityTracing` dla `System.ServiceModel` źródła śledzenia, aby włączyć kod użytkownika do propagowania działań kodu użytkownika. (Gdy ServiceModel działania śledzenia jest włączona, identyfikator działania zdefiniowane w obiekcie klienta nie są propagowane do kodu użytkownika usługi; Transfery, jednak skorelować działaniach kodu użytkownika klienta i usługi pośrednie działań usługi WCF.)  
  
 Definiowanie działania zmiany i propagowanie identyfikator działania pozwala nam wykonywać bezpośrednie błąd korelację między punktami końcowymi. Dzięki temu będzie można znaleźć przyczynę błędu szybciej.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md)
