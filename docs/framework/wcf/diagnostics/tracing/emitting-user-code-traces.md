---
title: "Emitowanie danych śledzenia elementu User-Code"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d743ae68955bba844f84fed71047d9331fd349af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="emitting-user-code-traces"></a>Emitowanie danych śledzenia elementu User-Code
Oprócz włączenia śledzenia w konfiguracji, aby zbieranie danych Instrumentacji generowanych przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], można również wysyłać dane śledzenia w kodzie użytkownika. W ten sposób można utworzyć aktywne dane instrumentacji, który można przejrzeć później w celu diagnostyki. W tym temacie opisano, jak to zrobić.  
  
 Ponadto [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md) próbki obejmuje całego kodu pokazano w poniższych sekcjach.  
  
## <a name="creating-a-trace-source"></a>Tworzenie źródła śledzenia  
 Poniższy kod umożliwia utworzenie źródła śledzenia użytkownika.  
  
```  
TraceSource ts = new TraceSource("myUserTraceSource");  
```  
  
## <a name="creating-activities"></a>Tworzenie działania  
 Działania są jednostki logicznej przetwarzania. Dla każdej jednostki przetwarzania głównych, w której ma zostać śladów do można grupować można utworzyć jedno działanie. Na przykład można utworzyć jedno działanie dla każdego żądania do usługi. Aby to zrobić, wykonaj następujące czynności.  
  
1.  Zapisz identyfikator działania w zakresie.  
  
2.  Utwórz nowy identyfikator działania.  
  
3.  Transfer z działania w zakresie do nowego, Ustaw nowe działanie w zakresie a emisją Rozpocznij śledzenie dla tego działania.  
  
 Poniższy kod przedstawia, jak to zrobić.  
  
```  
Guid oldID = Trace.CorrelationManager.ActivityId;  
Guid traceID = Guid.NewGuid();  
ts.TraceTransfer(0, "transfer", traceID);  
Trace.CorrelationManager.ActivityId = traceID; // Trace is static  
ts.TraceEvent(TraceEventType.Start, 0, "Add request");  
```  
  
## <a name="emitting-traces-within-a-user-activity"></a>Emitowanie danych śledzenia w ramach działania użytkownika  
 Poniższy kod emituje dane śledzenia w ramach działania użytkownika.  
  
```  
double value1 = 100.00D;  
double value2 = 15.99D;  
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);  
double result = client.Add(value1, value2);  
ts.TraceInformation("Client receives Add response '" + result + "'");  
```  
  
## <a name="stopping-the-activities"></a>Zatrzymywanie działania  
 Zatrzymanie działania, transfer do starego działania, Zatrzymaj bieżący identyfikator działania i zresetować stary identyfikator działania w zakresie.  
  
 Poniższy kod przedstawia, jak to zrobić.  
  
```  
ts.TraceTransfer(0, "transfer", oldID);  
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");  
Trace.CorrelationManager.ActivityId = oldID;  
```  
  
## <a name="propagating-the-activity-id-to-a-service"></a>Propagowanie identyfikator działania z usługą  
 Jeśli ustawisz `propagateActivity` atrybutu `true` dla `System.ServiceModel` pliki źródłowe śledzenia w konfiguracji klienta i usługi, usługi przetwarzanie żądania Dodaj występuje w to samo działanie jak określono w kliencie. Jeśli usługa definiuje własne działania i transfery, ślady usługi nie są wyświetlane w działaniu propagowane klienta. Zamiast tego pojawią się one w działaniu Skorelowane za transfer śladów do działania, których identyfikator jest propagowana przez klienta.  
  
> [!NOTE]
>  Jeśli `propagateActivity` atrybut ma ustawioną `true` na klienta i usługi, otoczenia działania w zakresie operacji usługi jest ustawiana przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  
  
 Można użyć poniższego kodu, aby sprawdzić, czy działanie zostało ustawione w zakresie przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  
  
```  
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
 Gdy Zgłoś wyjątek w kodzie, można również śledzenia wyjątków na poziomie ostrzeżenia lub przy użyciu następującego kodu.  
  
```  
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");  
```  
  
## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Wyświetlanie śladów użytkownika za pomocą narzędzia podglądu śledzenia usługi  
 Ta sekcja zawiera zrzuty ekranu śladów generowane przez uruchomienie [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md) próbkowania, podczas wyświetlania przy użyciu [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Na poniższym diagramie działania "Dodaj żądanie" utworzone wcześniej wybrano w lewym panelu. Znajduje się on z trzech innymi matematyczne operacji (dzielenie, różnicowe, mnożenie) wchodzących w skład programu klienta aplikacji. Kod użytkownika został zdefiniowany jeden nowe działanie dla każdej operacji do izolowania potencjalnych wystąpienia błędu w różnych żądań.  
  
 Aby zademonstrować stosowania transferów [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md) próbki, działanie Kalkulator, które hermetyzuje żądania operacji cztery tworzona jest również. Dla każdego żądania jest transferu i z powrotem z działania Kalkulator do działania żądania (śledzenia zostanie wyróżniona w górnym prawym panelu na rysunku).  
  
 Po wybraniu do działania w lewym panelu śladów uwzględnionych tego działania są wyświetlane w górnym prawym panelu. Jeśli `propagateActivity` jest `true` w każdym punkcie końcowym ścieżka żądania, dane śledzenia w działaniu żądania są od wszystkich procesów, które uczestniczą w żądaniu. W tym przykładzie widać śladów pochodzących z klienta i usługi, w kolumnie 4. w panelu.  
  
 To działanie zawiera następujące kolejność przetwarzania:  
  
1.  Klient wysyła komunikat do dodania.  
  
2.  Usługa odbiera komunikat żądania Dodaj.  
  
3.  Dodaj odpowiedzi wysyłane przez usługę.  
  
4.  Klient odbiera odpowiedź Dodaj.  
  
 Te operacje śledzenia zostały wyemitowane na poziomie informacji. Kliknięcie przycisku śledzenia w prawym górnym panelu przedstawia szczegóły tego śladu w prawym dolnym panelu.  
  
 Na poniższym diagramie Widzimy również śladów transfer od i do działania Kalkulator, jak również dwie pary uruchomienia i zatrzymania śledzenia na działanie żądania, jeden dla klienta i jeden dla usługi (po jednej dla każdego źródła śledzenia).  
  
 ![Podgląd śledzenia: Emitowanie użytkownika &#45; kod śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd")  
Lista działań w oparciu o czas utworzenia (lewego panelu) i ich zagnieżdżonych działań (prawym górnym panelu)  
  
 Jeśli kod usługi zgłasza wyjątek, który powoduje, że klient ma zostać zgłoszony, jak również (na przykład, gdy klient nie pobrały odpowiedzi na żądania), zarówno usługa i klient ostrzeżenia lub komunikaty o błędach występować w tym samym działaniu dla korelacji bezpośredniego. Na poniższym diagramie usługa zgłasza wyjątek stwierdzający "Usługa odmówi przetworzyć tego żądania w kodzie użytkownika." Klient również zgłasza wyjątek stwierdzający "serwer nie może przetworzyć żądania z powodu błędu wewnętrznego."  
  
 ![Emituj 45; & użytkownika za pomocą podglądu śledzenia śledzi kodu](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace2.gif "e2eTrace2")  
Błędy w obrębie punktów końcowych dla danego żądania są wyświetlane w tym samym działaniu jeśli pochodzi żądanie identyfikator działania  
  
 Dwukrotne kliknięcie mnożenie działania w lewym panelu przedstawia wykres następujących, za pomocą danych śledzenia dla mnożenia działanie dla każdego procesu związane. Firma Microsoft można zauważyć, że najpierw wystąpiło ostrzeżenie w usług (wystąpienie wyjątku), której następuje ostrzeżeń i błędów na komputerze klienckim, ponieważ nie można przetworzyć żądania. Firma Microsoft w związku z tym oznacza błąd przyczynowy relacji między punktami końcowymi i pochodzić przyczynę błędu.  
  
 ![Emituj 45; & użytkownika za pomocą podglądu śledzenia śledzi kodu](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace3.gif "e2eTrace3")  
Widok wykresu błąd korelacji  
  
 Uzyskanie poprzedniej śladów ustawiliśmy `ActivityTracing` źródeł śledzenia użytkownika i `propagateActivity=true` dla `System.ServiceModel` źródła śledzenia. Firma Microsoft nie określono `ActivityTracing` dla `System.ServiceModel` źródła śledzenia do kodu użytkownika rozprzestrzenianie działania kodu użytkownika. (Jeśli ServiceModel czynność śledzenia jest włączona, identyfikator działania zdefiniowane na komputerze klienckim nie są propagowane do kodu użytkownika usługi; Transfery, jednak skorelowania działania kodu użytkownika klienta i usługi do pośredniego [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] działania.)  
  
 Definiowanie działań i propagowanie identyfikator działania umożliwia firmie Microsoft w celu wykonania bezpośredniego błąd korelacji między punktami końcowymi. W ten sposób można zlokalizować przyczynę błędu szybciej.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md)
