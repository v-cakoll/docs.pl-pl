---
title: Transfer
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 4753ec85c458a0dde3db4a6b7cdad41c69185019
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311022"
---
# <a name="transfer"></a>Transfer
W tym temacie opisano transfer w modelu śledzenie aktywności Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Definicja transferu  
 Transfery między działaniami reprezentują przyczynowego relacje między zdarzeniami powiązanych działań w obrębie punktów końcowych. Dwa działania są powiązane w przypadku transferów, gdy kontrolka przepływa między te działania, na przykład, wywołanie metody przekraczające granice działania. W programie WCF w przypadku Bajty przychodzące od usługi, działania nasłuchiwania na jest przekazywana do działania odbieranie bajtów tworzona obiekt komunikatu. Aby uzyskać listę scenariuszy śledzenia end-to-end oraz ich odpowiednich działań i śledzenia projektu, zobacz [scenariusze śledzenia End-To-End](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Aby emitować transferu danych śledzenia, należy użyć `ActivityTracing` ustawienie dla źródła śledzenia, jak pokazano w następującym kodem konfiguracji.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Aby skorelować działań w ramach punktów końcowych przy użyciu transferu  
 Działania i transfery zezwolić użytkownikowi probabilistically znaleźć przyczynę błędu. Na przykład jeśli firma Microsoft, przesyłać i z powrotem między działaniami M i N odpowiednio w składnikach, M i N i awarii, odbywa się w prawej N po przeniesieniu do M, firma Microsoft narysować wniosku, że prawdopodobnie z powodu firmy N przekazywanie danych do M.  
  
 Śledzenie transferu jest emitowane przez działanie M działania N po przepływ sterowania między M i N. Na przykład N wykonuje jakąś pracę M ze względu na wywołania metody przekraczające granice działań. N już istnieje lub została utworzona. N jest rozprzestrzeniony, M, gdy N jest nowe działanie, które wykonuje jakąś pracę na M.  
  
 Transfer z M, n może nie może występować transferu wstecz od N do M. Jest to spowodowane M można zduplikować część prac w N i "nie Śledź" gdy N kończy pracę. W rzeczywistości M może zakończyć przed N zakończeniem jej zadania. Dzieje się tak w działaniu "Otwórz ServiceHost" (M), które spowoduje utworzenie odbiornika działań (N), a następnie kończy działanie. Transfer wstecz od N do M oznacza, że N ukończona praca związana M.  
  
 N może kontynuować inne procesy przetwarzania niezwiązanych ze sobą na M, na przykład istniejące działanie wystawcy uwierzytelnienia (N), które utrzymuje odbierania żądań logowania (M) z działania innej nazwy logowania.  
  
 Relacji zagnieżdżenia używa nie zawsze istnieje między działaniami M i N. Może to nastąpić z dwóch powodów. Najpierw podczas działania M nie monitoruje faktyczne przetwarzanie wykonywane w N mimo, że zainicjowano M N. Sekunda, gdy N już istnieje.  
  
## <a name="example-of-transfers"></a>Przykład transferu  
 Wyświetla dwa poniższe transferu przykłady.  
  
-   Podczas tworzenia hosta usługi konstruktora uzyska kontrolę z kod wywołujący lub kod wywołujący przekazuje do konstruktora. Po zakończeniu konstruktora wykonywania przekazuje sterowanie do wywołującego kodu lub Konstruktor przenosi się do kodu wywołującego. Dotyczy to zagnieżdżonych relacji.  
  
-   Po uruchomieniu odbiornika przetwarzania danych transportu tworzy nowy wątek i przekazuje do działania odbierania bajtów odpowiedniego kontekstu do przetwarzania, przekazując kontrolę i danych. Po zakończeniu tego wątku podczas przetwarzania żądania, działanie odbieranie bajtów przekazuje nic do odbiornika. W tym przypadku mamy transfer w, ale żaden transfer poza nowe działanie wątku. Dwa działania są powiązane, ale nie zagnieżdżone.  
  
## <a name="activity-transfer-sequence"></a>Seria przeniesienia działania  
 Poprawnie sformułowany działania sekwencji transferu obejmuje następujące kroki.  
  
1. Rozpocznij nowe działanie wybrać nowy gAId.  
  
2. Emituj śledzenia przeniesienia do tego nowego gAId z bieżący identyfikator działania  
  
3. Ustaw nowy identyfikator w protokole TLS  
  
4. Emituj Rozpocznij śledzenie w celu określenia początku nowe działanie przez.  
  
5. Powrót do oryginalnego działania składa się z następujących czynności:  
  
6. Emituj śledzenia transferu do oryginalnego gAId  
  
7. Emituj Zatrzymaj śledzenie, aby wskazać koniec nowe działanie  
  
8. Ustaw TLS gAId stary.  
  
 Poniższy przykład kodu pokazuje, jak to zrobić. W tym przykładzie przyjęto założenie, wywołania blokowania jest wykonywane podczas przenoszenia do nowego działania i zawiera wstrzymań/wznowień ślady.  
  
```csharp
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
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scenariusze kompleksowego śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
