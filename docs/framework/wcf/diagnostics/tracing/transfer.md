---
title: Transfer
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: aa7535aa393544077a9802b5c3255d6e5f6accda
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803003"
---
# <a name="transfer"></a>Transfer
W tym temacie opisano transfer w modelu śledzenie działania Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Definicja transferu  
 Transfery między działaniami reprezentują przyczynowy relacje między zdarzeniami w powiązanych działań w ramach punktów końcowych. Dwa działania są powiązane z transferów podczas kontroli przepływają między te działania, na przykład wywołanie metody przekraczające granice działania. W programie WCF podczas bajtów jest przychodzące od usługi, działania nasłuchiwania na jest przenoszona do działania odbierania bajtów której jest tworzony obiekt komunikatu. Listę scenariuszy śledzenia end-to-end oraz ich odpowiednich działania i śledzenia projektu, zobacz [scenariusze śledzenia End-To-End](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Aby emitować transferu danych śledzenia, należy użyć `ActivityTracing` ustawienie w źródle śledzenia, jak pokazano w następującym kodem konfiguracji.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Przy użyciu transferu do skorelowania działań w ramach punktów końcowych  
 Działania i transferów zezwolić użytkownikowi probabilistically Znajdź przyczynę błędu. Na przykład jeśli firma Microsoft i z powrotem transferu między działaniami M i N odpowiednio w składnikach M i N, a awarii odbywa się w prawej N po przeniesieniu do M, możemy narysować wniosku, że prawdopodobnie z powodu jego N przekazywanie danych do M.  
  
 Śledzenia transfer jest emitowany z działania M do działania N po przepływu sterowania między M i N. Na przykład N przeprowadza niektórych pracy M ze względu na wywołania metody przekraczające granice działań. N już istnieje lub została utworzona. N jest zduplikowany przez M, gdy N jest nowe działanie, które wykonuje pracę niektórych m.  
  
 Transfer z M, n może nie może występować przeniesienia od N do M. Jest to spowodowane M można zduplikować dodatkowych czynności w N i nie Śledź N zakończeniu pracy. W rzeczywistości M może zakończyć ukończenia N swojego zadania. Dzieje się tak w działaniu "Otwórz ServiceHost" (M), które spowoduje utworzenie działania odbiornika (N), a następnie zostaje zakończony. Transfer wstecz od N do M oznacza, że N ukończono pracy związanych z M.  
  
 N można kontynuować wykonywanie innych przetwarzania niezwiązanych ze sobą M, na przykład istniejące działanie wystawcy uwierzytelnienia (N), który śledzi odbierania żądań logowania (M) z działania inny login.  
  
 Zagnieżdżenia relacja nie istnieje zawsze między działaniami M i N. Może to nastąpić z dwóch powodów. Najpierw działania M nie monitoruje aktualnie przetwarzanego wykonywane w N chociaż zainicjował M N. Drugi, gdy N już istnieje.  
  
## <a name="example-of-transfers"></a>Przykład transferu  
 Poniższe listy dwóch transfer przykłady.  
  
-   Podczas tworzenia usługi hosta konstruktora uzyska kontrolę z kodu wywołującego, lub kod wywołujący przekazuje do konstruktora. Po zakończeniu konstruktora wykonywania zwraca sterowania do wywołującego kodu lub konstruktora przenosi do wywołującego kodu. Jest to relacja zagnieżdżonych.  
  
-   Po uruchomieniu odbiornik przetwarzania transportu danych powoduje utworzenie nowego wątku i przekazuje do działania odbierania bajtów odpowiedniego kontekstu do przetwarzania, przekazywanie i kontroli danych. Po zakończeniu tego wątku przetwarzania żądania działania odbierania bajtów przekazuje nic do odbiornika. W takim przypadku mamy transfer w, ale brak transferu poza nowe działanie wątku. Dwa działania są powiązane, ale nie było zagnieżdżone.  
  
## <a name="activity-transfer-sequence"></a>Działania sekwencji transferu  
 Poprawnie sformułowany działania sekwencji transferu obejmuje następujące kroki.  
  
1.  Rozpocznij nowe działanie wybrać nowy gAId.  
  
2.  Emituj śledzenia transferu do tej nowej gAId od bieżącego Identyfikatora działania  
  
3.  Ustaw nowy identyfikator w protokole TLS  
  
4.  Emituj Rozpocznij śledzenie, aby wskazać początku nowe działanie przez.  
  
5.  Wrócić do oryginalnego działania składa się z następujących czynności:  
  
6.  Emituj śledzenia transferu do oryginalnego gAId  
  
7.  Emituj Zatrzymaj śledzenie, aby wskazać koniec nowe działanie  
  
8.  Ustaw TLS do starego gAId.  
  
 W poniższym przykładzie pokazano, jak to zrobić. W tym przykładzie przyjęto założenie, blokowania połączeń są wysyłane w przypadku przenoszenia do nowego działania i obejmuje wstrzymanie/wznowienie śladów.  
  
```  
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  
// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();   
// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  
// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  
// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  
// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  
// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  
// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);   
// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  
// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  
// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;    
// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Scenariusze kompleksowego śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
