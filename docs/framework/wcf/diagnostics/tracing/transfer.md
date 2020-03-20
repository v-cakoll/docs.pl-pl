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
# <a name="transfer"></a><span data-ttu-id="ebce0-102">Transfer</span><span class="sxs-lookup"><span data-stu-id="ebce0-102">Transfer</span></span>
<span data-ttu-id="ebce0-103">W tym temacie opisano transfer w modelu śledzenia działań programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ebce0-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="ebce0-104">Definicja transferu</span><span class="sxs-lookup"><span data-stu-id="ebce0-104">Transfer Definition</span></span>  
 <span data-ttu-id="ebce0-105">Transfery między działaniami reprezentują związek przyczynowy między zdarzeniami w powiązanych działaniach w punktach końcowych.</span><span class="sxs-lookup"><span data-stu-id="ebce0-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="ebce0-106">Dwa działania są powiązane z transferów, gdy przepływy kontroli między tymi działaniami, na przykład wywołanie metody przekraczania granic działania.</span><span class="sxs-lookup"><span data-stu-id="ebce0-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="ebce0-107">W WCF, gdy bajty są przychodzące w usłudze, Nasłuchaj na działanie jest przenoszone do receive bajtów działania, gdzie obiekt wiadomości jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="ebce0-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="ebce0-108">Aby uzyskać listę scenariuszy śledzenia end-to-end oraz ich odpowiednie działanie i projekt śledzenia, zobacz [Scenariusze śledzenia end-to-end](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="ebce0-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="ebce0-109">Aby emitować ślady `ActivityTracing` transferu, należy użyć ustawienia na źródle śledzenia, jak pokazano w poniższym kodzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ebce0-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="ebce0-110">Korzystanie z funkcji Transfer do skorelowania działań w punktach końcowych</span><span class="sxs-lookup"><span data-stu-id="ebce0-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="ebce0-111">Działania i transfery pozwalają użytkownikowi probabilistycznie zlokalizować główną przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="ebce0-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="ebce0-112">Na przykład, jeśli przeniesiemy tam iz powrotem między działaniami M i N odpowiednio w składnikach M i N, a awaria dzieje się w N zaraz po przeniesieniu z powrotem do M, możemy wyciągnąć wniosek, że jest to prawdopodobnie spowodowane przekazywaniem danych N z powrotem do M.</span><span class="sxs-lookup"><span data-stu-id="ebce0-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="ebce0-113">Śledzenia transferu jest emitowany z działania M do działania N, gdy istnieje przepływ kontroli między M i N. Na przykład N wykonuje pewną pracę dla M z powodu wywołania metody przekraczania granic działań.</span><span class="sxs-lookup"><span data-stu-id="ebce0-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="ebce0-114">N może już istnieć lub został utworzony.</span><span class="sxs-lookup"><span data-stu-id="ebce0-114">N may already exist or has been created.</span></span> <span data-ttu-id="ebce0-115">N jest zduplikowany przez M, gdy N jest nowe działanie, które wykonuje pewną pracę dla M.</span><span class="sxs-lookup"><span data-stu-id="ebce0-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="ebce0-116">Po przeniesieniu z M do N może nie nastąpić transfer z powrotem z N do M. Dzieje się tak dlatego, że M może odradzać niektóre prace w N i nie śledzić, kiedy N kończy tę pracę.</span><span class="sxs-lookup"><span data-stu-id="ebce0-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="ebce0-117">W rzeczywistości M można zakończyć przed N kończy swoje zadanie.</span><span class="sxs-lookup"><span data-stu-id="ebce0-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="ebce0-118">Dzieje się tak w "Open ServiceHost" działania (M), który spawns działania odbiornika (N), a następnie kończy.</span><span class="sxs-lookup"><span data-stu-id="ebce0-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="ebce0-119">Przeniesienie z powrotem z N do M oznacza, że N zakończył pracę związaną z M.</span><span class="sxs-lookup"><span data-stu-id="ebce0-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="ebce0-120">N można kontynuować wykonywanie innych przetwarzania niezwiązanych z M, na przykład istniejące działanie wystawcy uwierzytelnienia (N), który utrzymuje odbieranie żądań logowania (M) z różnych działań logowania.</span><span class="sxs-lookup"><span data-stu-id="ebce0-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="ebce0-121">Relacja zagnieżdżania nie musi istnieć między działaniami M i N. Może się to zdarzyć z dwóch powodów.</span><span class="sxs-lookup"><span data-stu-id="ebce0-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="ebce0-122">Po pierwsze, gdy działanie M nie monitoruje rzeczywistego przetwarzania wykonywanego w N, chociaż M zainicjował N. Po drugie, gdy N już istnieje.</span><span class="sxs-lookup"><span data-stu-id="ebce0-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="ebce0-123">Przykład transferów</span><span class="sxs-lookup"><span data-stu-id="ebce0-123">Example of Transfers</span></span>  
 <span data-ttu-id="ebce0-124">Poniżej wymieniono dwa przykłady transferu.</span><span class="sxs-lookup"><span data-stu-id="ebce0-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="ebce0-125">Podczas tworzenia hosta usługi konstruktor zyskuje kontrolę z kodu wywołującego lub kod wywołujący przenosi do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ebce0-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="ebce0-126">Po zakończeniu wykonywania konstruktora zwraca kontrolę do kodu wywołującego lub konstruktora przenosi z powrotem do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ebce0-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="ebce0-127">Jest to przypadek relacji zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="ebce0-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="ebce0-128">Gdy odbiornik rozpoczyna przetwarzanie danych transportu, tworzy nowy wątek i ręce do receive bajty działania odpowiedni kontekst do przetwarzania, przekazywania kontroli i danych.</span><span class="sxs-lookup"><span data-stu-id="ebce0-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="ebce0-129">Po zakończeniu przetwarzania żądania tego wątku, Receive Bytes działania przekazuje nic z powrotem do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="ebce0-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="ebce0-130">W takim przypadku mamy przeniesienie, ale nie przenieść z nowej działalności wątku.</span><span class="sxs-lookup"><span data-stu-id="ebce0-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="ebce0-131">Te dwa działania są powiązane, ale nie zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="ebce0-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="ebce0-132">Sekwencja transferu aktywności</span><span class="sxs-lookup"><span data-stu-id="ebce0-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="ebce0-133">Dobrze sformułowana sekwencja transferu aktywności zawiera następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="ebce0-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="ebce0-134">Rozpocznij nowe działanie, które polega na wybraniu nowego gAId.</span><span class="sxs-lookup"><span data-stu-id="ebce0-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="ebce0-135">Emitowanie śledzenia transferu do tego nowego identyfikatora gAId z bieżącego identyfikatora działania</span><span class="sxs-lookup"><span data-stu-id="ebce0-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="ebce0-136">Ustawianie nowego identyfikatora w tls</span><span class="sxs-lookup"><span data-stu-id="ebce0-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="ebce0-137">Emituj śledzenie początkowe, aby wskazać początek nowego działania przez.</span><span class="sxs-lookup"><span data-stu-id="ebce0-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="ebce0-138">Powrót do pierwotnego działania składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="ebce0-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="ebce0-139">Emitowanie śledzenia transferu do oryginalnego gAId</span><span class="sxs-lookup"><span data-stu-id="ebce0-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="ebce0-140">Emituj śledzenie zatrzymania, aby wskazać koniec nowego działania</span><span class="sxs-lookup"><span data-stu-id="ebce0-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="ebce0-141">Ustaw TLS na stary gAId.</span><span class="sxs-lookup"><span data-stu-id="ebce0-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="ebce0-142">Poniższy przykład kodu pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="ebce0-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="ebce0-143">W tym przykładzie przyjęto założenie, że wywołanie blokowania jest nawiązywany podczas przenoszenia do nowego działania i zawiera śledzenie wstrzymania/wznowienia.</span><span class="sxs-lookup"><span data-stu-id="ebce0-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebce0-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebce0-144">See also</span></span>

- [<span data-ttu-id="ebce0-145">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="ebce0-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="ebce0-146">Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="ebce0-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="ebce0-147">Scenariusze kompleksowego śledzenia</span><span class="sxs-lookup"><span data-stu-id="ebce0-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="ebce0-148">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="ebce0-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
