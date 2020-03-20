---
title: Transfer
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: e0ebfff97cd33e7a588a1ab92399a97a0fbec039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185705"
---
# <a name="transfer"></a>Transfer
W tym temacie opisano transfer w modelu śledzenia działań programu Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Definicja transferu  
 Transfery między działaniami reprezentują związek przyczynowy między zdarzeniami w powiązanych działaniach w punktach końcowych. Dwa działania są powiązane z transferów, gdy przepływy kontroli między tymi działaniami, na przykład wywołanie metody przekraczania granic działania. W WCF, gdy bajty są przychodzące w usłudze, Nasłuchaj na działanie jest przenoszone do receive bajtów działania, gdzie obiekt wiadomości jest tworzony. Aby uzyskać listę scenariuszy śledzenia end-to-end oraz ich odpowiednie działanie i projekt śledzenia, zobacz [Scenariusze śledzenia end-to-end](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Aby emitować ślady `ActivityTracing` transferu, należy użyć ustawienia na źródle śledzenia, jak pokazano w poniższym kodzie konfiguracji.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Korzystanie z funkcji Transfer do skorelowania działań w punktach końcowych  
 Działania i transfery pozwalają użytkownikowi probabilistycznie zlokalizować główną przyczynę błędu. Na przykład, jeśli przeniesiemy tam iz powrotem między działaniami M i N odpowiednio w składnikach M i N, a awaria dzieje się w N zaraz po przeniesieniu z powrotem do M, możemy wyciągnąć wniosek, że jest to prawdopodobnie spowodowane przekazywaniem danych N z powrotem do M.  
  
 Śledzenia transferu jest emitowany z działania M do działania N, gdy istnieje przepływ kontroli między M i N. Na przykład N wykonuje pewną pracę dla M z powodu wywołania metody przekraczania granic działań. N może już istnieć lub został utworzony. N jest zduplikowany przez M, gdy N jest nowe działanie, które wykonuje pewną pracę dla M.  
  
 Po przeniesieniu z M do N może nie nastąpić transfer z powrotem z N do M. Dzieje się tak dlatego, że M może odradzać niektóre prace w N i nie śledzić, kiedy N kończy tę pracę. W rzeczywistości M można zakończyć przed N kończy swoje zadanie. Dzieje się tak w "Open ServiceHost" działania (M), który spawns działania odbiornika (N), a następnie kończy. Przeniesienie z powrotem z N do M oznacza, że N zakończył pracę związaną z M.  
  
 N można kontynuować wykonywanie innych przetwarzania niezwiązanych z M, na przykład istniejące działanie wystawcy uwierzytelnienia (N), który utrzymuje odbieranie żądań logowania (M) z różnych działań logowania.  
  
 Relacja zagnieżdżania nie musi istnieć między działaniami M i N. Może się to zdarzyć z dwóch powodów. Po pierwsze, gdy działanie M nie monitoruje rzeczywistego przetwarzania wykonywanego w N, chociaż M zainicjował N. Po drugie, gdy N już istnieje.  
  
## <a name="example-of-transfers"></a>Przykład transferów  
 Poniżej wymieniono dwa przykłady transferu.  
  
- Podczas tworzenia hosta usługi konstruktor zyskuje kontrolę z kodu wywołującego lub kod wywołujący przenosi do konstruktora. Po zakończeniu wykonywania konstruktora zwraca kontrolę do kodu wywołującego lub konstruktora przenosi z powrotem do kodu wywołującego. Jest to przypadek relacji zagnieżdżonej.  
  
- Gdy odbiornik rozpoczyna przetwarzanie danych transportu, tworzy nowy wątek i ręce do receive bajty działania odpowiedni kontekst do przetwarzania, przekazywania kontroli i danych. Po zakończeniu przetwarzania żądania tego wątku, Receive Bytes działania przekazuje nic z powrotem do odbiornika. W takim przypadku mamy przeniesienie, ale nie przenieść z nowej działalności wątku. Te dwa działania są powiązane, ale nie zagnieżdżone.  
  
## <a name="activity-transfer-sequence"></a>Sekwencja transferu aktywności  
 Dobrze sformułowana sekwencja transferu aktywności zawiera następujące kroki.  
  
1. Rozpocznij nowe działanie, które polega na wybraniu nowego gAId.  
  
2. Emitowanie śledzenia transferu do tego nowego identyfikatora gAId z bieżącego identyfikatora działania  
  
3. Ustawianie nowego identyfikatora w tls  
  
4. Emituj śledzenie początkowe, aby wskazać początek nowego działania przez.  
  
5. Powrót do pierwotnego działania składa się z następujących elementów:  
  
6. Emitowanie śledzenia transferu do oryginalnego gAId  
  
7. Emituj śledzenie zatrzymania, aby wskazać koniec nowego działania  
  
8. Ustaw TLS na stary gAId.  
  
 Poniższy przykład kodu pokazuje, jak to zrobić. W tym przykładzie przyjęto założenie, że wywołanie blokowania jest nawiązywany podczas przenoszenia do nowego działania i zawiera śledzenie wstrzymania/wznowienia.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scenariusze kompleksowego śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
