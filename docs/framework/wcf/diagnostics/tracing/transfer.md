---
title: Transfer
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 52b0cf35a2f8bab17252d3711f3143738c2bc39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587771"
---
# <a name="transfer"></a>Transfer
W tym temacie opisano transfer w modelu śledzenia działań Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Definicja transferu  
 Transfery między działaniami reprezentują związek przyczyn między zdarzeniami w pokrewnych działaniach w punktach końcowych. Dwie działania są powiązane z transferami, gdy sterowanie przepływem między tymi działaniami, na przykład wywołanie metody przecina granice działania. W programie WCF, gdy w usłudze są przyjmowane bajty, nasłuchiwanie w działaniu jest przesyłane do działania odbierania bajtów, w którym jest tworzony obiekt wiadomości. Aby zapoznać się z listą kompleksowych scenariuszy śledzenia i ich odpowiedniego projektu działań i śledzenia, zobacz [kompleksowe scenariusze śledzenia](end-to-end-tracing-scenarios.md).  
  
 Aby emitować ślady transferu, użyj `ActivityTracing` Ustawienia ze źródła śledzenia, jak pokazano w poniższym kodzie konfiguracyjnym.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Używanie transferu do skorelowania działań w punktach końcowych  
 Działania i transfery umożliwiają użytkownikowi probabilistically lokalizowanie głównej przyczyny błędu. Jeśli na przykład przeniesiemy z powrotem i wstecz między działaniami M i N w składnikach M i N, a awaria wystąpi w N prawo po przeniesieniu z powrotem do M, możemy sporządzić wniosek, że najprawdopodobniej jest to spowodowane przekazywaniem danych z powrotem do M.  
  
 Ślad transferu jest emitowany z działania M do działania N, gdy istnieje przepływ sterowania między M i N. Na przykład N wykonuje część pracy dla M ze względu na to, że wywołanie metody przekracza granice działania. N może już istnieć lub został utworzony. N jest duplikowany przez M, gdy N to nowe działanie, które wykonuje pewną pracę dla M.  
  
 Po przekazaniu od M do N nie można wykonać transferu z powrotem z N do M. Jest to spowodowane tym, że M może zduplikować część pracy w N i nie śledzić, gdy N kończy pracę. W rzeczywistości M może zakończyć się przed N zakończeniem zadania. Dzieje się tak w przypadku działania "Otwórz ServiceHost" (M), które powoduje zduplikowanie aktywności odbiornika (N), a następnie kończy działanie. Transfer z powrotem z N do M oznacza, że N ukończył pracę związaną z M.  
  
 N może kontynuować wykonywanie innych operacji przetwarzania niezwiązanych z M, na przykład istniejącej aktywności uwierzytelniania (N), która zachowuje żądania logowania (M) z różnych działań logowania.  
  
 Relacja zagnieżdżenia nie musi istnieć między działaniami M i N. Może się to zdarzyć z dwóch przyczyn. Po pierwsze, gdy działanie M nie monitoruje rzeczywistego przetwarzania wykonanego w N, chociaż M zainicjowano N. Sekunda, gdy N już istnieje.  
  
## <a name="example-of-transfers"></a>Przykład transferu  
 Poniżej wymieniono dwa przykłady transferu.  
  
- Podczas tworzenia hosta usługi Konstruktor uzyskuje kontrolę nad wywoływanym kodem lub wywoływanie przesyłanych kodu do konstruktora. Gdy Konstruktor zakończył wykonywanie, zwraca sterowanie do kodu wywołującego lub Konstruktor przesyła z powrotem do kodu wywołującego. Jest to przypadek relacji zagnieżdżonej.  
  
- Gdy odbiornik zacznie przetwarzać dane transportu, tworzy nowy wątek i ręce do działania odbierania bajtów, który jest odpowiednim kontekstem do przetwarzania, przekazywania kontroli i danych. Gdy ten wątek zakończy przetwarzanie żądania, działanie odbieraj bajty kończy się bez powrotu do odbiornika. W takim przypadku mamy transfer w przypadku, gdy nie przeprowadzono transferu z nowego wątku. Te dwa działania są powiązane, ale nie są zagnieżdżone.  
  
## <a name="activity-transfer-sequence"></a>Sekwencja transferu działań  
 Poprawnie sformułowana sekwencja transferu działań obejmuje następujące kroki.  
  
1. Rozpocznij nowe działanie, które składa się z wyboru nowego gAId.  
  
2. Emituj ślad transferu do tego nowego gAId z bieżącego identyfikatora działania  
  
3. Ustaw nowy identyfikator w protokole TLS  
  
4. Emituj początkowy ślad, aby wskazać początek nowej aktywności przez.  
  
5. Powrót do oryginalnego działania składa się z następujących elementów:  
  
6. Emituj ślad transferu do oryginalnego gAId  
  
7. Emituj śledzenie zatrzymania, aby wskazać koniec nowego działania  
  
8. Ustaw protokół TLS na stary gAId.  
  
 Poniższy przykład kodu demonstruje, jak to zrobić. W tym przykładzie przyjęto założenie, że jest wywoływane wywołanie podczas przenoszenia do nowego działania i zawiera dane śledzenia wstrzymania/wznowienia.  
  
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

- [Konfigurowanie śledzenia](configuring-tracing.md)
- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scenariusze kompleksowego śledzenia](end-to-end-tracing-scenarios.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
