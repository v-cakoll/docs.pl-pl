---
title: Transfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83bb76cc46d72f3d368de20669391c3e7f24a0f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transfer"></a><span data-ttu-id="84329-102">Transfer</span><span class="sxs-lookup"><span data-stu-id="84329-102">Transfer</span></span>
<span data-ttu-id="84329-103">W tym temacie opisano transferu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] działania śledzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="84329-103">This topic describes transfer in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="84329-104">Definicja transferu</span><span class="sxs-lookup"><span data-stu-id="84329-104">Transfer Definition</span></span>  
 <span data-ttu-id="84329-105">Transfery między działaniami reprezentują przyczynowy relacje między zdarzeniami w powiązanych działań w ramach punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="84329-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="84329-106">Dwa działania są powiązane z transferów podczas kontroli przepływają między te działania, na przykład wywołanie metody przekraczające granice działania.</span><span class="sxs-lookup"><span data-stu-id="84329-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="84329-107">W [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], gdy bajty znajdują się w usłudze nasłuchiwania podczas działania jest przenoszona do działania odbierania bajtów której jest tworzony obiekt komunikatu przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="84329-107">In [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="84329-108">Listę scenariuszy śledzenia end-to-end oraz ich odpowiednich działania i śledzenia projektu, zobacz [scenariusze śledzenia End-To-End](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="84329-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="84329-109">Aby emitować transferu danych śledzenia, należy użyć `ActivityTracing` ustawienie w źródle śledzenia, jak pokazano w następującym kodem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="84329-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="84329-110">Przy użyciu transferu do skorelowania działań w ramach punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="84329-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="84329-111">Działania i transferów zezwolić użytkownikowi probabilistically Znajdź przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="84329-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="84329-112">Na przykład jeśli firma Microsoft i z powrotem transferu między działaniami M i N odpowiednio w składnikach M i N, a awarii odbywa się w prawej N po przeniesieniu do M, możemy narysować wniosku, że prawdopodobnie z powodu jego N przekazywanie danych do M.</span><span class="sxs-lookup"><span data-stu-id="84329-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="84329-113">Śledzenia transfer jest emitowany z działania M do działania N po przepływu sterowania między M i N. Na przykład N przeprowadza niektórych pracy M ze względu na wywołania metody przekraczające granice działań.</span><span class="sxs-lookup"><span data-stu-id="84329-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="84329-114">N już istnieje lub została utworzona.</span><span class="sxs-lookup"><span data-stu-id="84329-114">N may already exist or has been created.</span></span> <span data-ttu-id="84329-115">N jest zduplikowany przez M, gdy N jest nowe działanie, które wykonuje pracę niektórych m.</span><span class="sxs-lookup"><span data-stu-id="84329-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="84329-116">Transfer z M, n może nie może występować przeniesienia od N do M. Jest to spowodowane M można zduplikować dodatkowych czynności w N i nie Śledź N zakończeniu pracy.</span><span class="sxs-lookup"><span data-stu-id="84329-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="84329-117">W rzeczywistości M może zakończyć ukończenia N swojego zadania.</span><span class="sxs-lookup"><span data-stu-id="84329-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="84329-118">Dzieje się tak w działaniu "Otwórz ServiceHost" (M), które spowoduje utworzenie działania odbiornika (N), a następnie zostaje zakończony.</span><span class="sxs-lookup"><span data-stu-id="84329-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="84329-119">Transfer wstecz od N do M oznacza, że N ukończono pracy związanych z M.</span><span class="sxs-lookup"><span data-stu-id="84329-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="84329-120">N można kontynuować wykonywanie innych przetwarzania niezwiązanych ze sobą M, na przykład istniejące działanie wystawcy uwierzytelnienia (N), który śledzi odbierania żądań logowania (M) z działania inny login.</span><span class="sxs-lookup"><span data-stu-id="84329-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="84329-121">Zagnieżdżenia relacja nie istnieje zawsze między działaniami M i N. Może to nastąpić z dwóch powodów.</span><span class="sxs-lookup"><span data-stu-id="84329-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="84329-122">Najpierw działania M nie monitoruje aktualnie przetwarzanego wykonywane w N chociaż zainicjował M N. Drugi, gdy N już istnieje.</span><span class="sxs-lookup"><span data-stu-id="84329-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="84329-123">Przykład transferu</span><span class="sxs-lookup"><span data-stu-id="84329-123">Example of Transfers</span></span>  
 <span data-ttu-id="84329-124">Poniższe listy dwóch transfer przykłady.</span><span class="sxs-lookup"><span data-stu-id="84329-124">The following lists two transfer examples.</span></span>  
  
-   <span data-ttu-id="84329-125">Podczas tworzenia usługi hosta konstruktora uzyska kontrolę z kodu wywołującego, lub kod wywołujący przekazuje do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="84329-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="84329-126">Po zakończeniu konstruktora wykonywania zwraca sterowania do wywołującego kodu lub konstruktora przenosi do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="84329-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="84329-127">Jest to relacja zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="84329-127">This is the case of a nested relationship.</span></span>  
  
-   <span data-ttu-id="84329-128">Po uruchomieniu odbiornik przetwarzania transportu danych powoduje utworzenie nowego wątku i przekazuje do działania odbierania bajtów odpowiedniego kontekstu do przetwarzania, przekazywanie i kontroli danych.</span><span class="sxs-lookup"><span data-stu-id="84329-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="84329-129">Po zakończeniu tego wątku przetwarzania żądania działania odbierania bajtów przekazuje nic do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="84329-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="84329-130">W takim przypadku mamy transfer w, ale brak transferu poza nowe działanie wątku.</span><span class="sxs-lookup"><span data-stu-id="84329-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="84329-131">Dwa działania są powiązane, ale nie było zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="84329-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="84329-132">Działania sekwencji transferu</span><span class="sxs-lookup"><span data-stu-id="84329-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="84329-133">Poprawnie sformułowany działania sekwencji transferu obejmuje następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="84329-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1.  <span data-ttu-id="84329-134">Rozpocznij nowe działanie wybrać nowy gAId.</span><span class="sxs-lookup"><span data-stu-id="84329-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2.  <span data-ttu-id="84329-135">Emituj śledzenia transferu do tej nowej gAId od bieżącego Identyfikatora działania</span><span class="sxs-lookup"><span data-stu-id="84329-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3.  <span data-ttu-id="84329-136">Ustaw nowy identyfikator w protokole TLS</span><span class="sxs-lookup"><span data-stu-id="84329-136">Set the new ID in TLS</span></span>  
  
4.  <span data-ttu-id="84329-137">Emituj Rozpocznij śledzenie, aby wskazać początku nowe działanie przez.</span><span class="sxs-lookup"><span data-stu-id="84329-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5.  <span data-ttu-id="84329-138">Wrócić do oryginalnego działania składa się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="84329-138">Return to the original activity consists of the following:</span></span>  
  
6.  <span data-ttu-id="84329-139">Emituj śledzenia transferu do oryginalnego gAId</span><span class="sxs-lookup"><span data-stu-id="84329-139">Emit a transfer trace to the original gAId</span></span>  
  
7.  <span data-ttu-id="84329-140">Emituj Zatrzymaj śledzenie, aby wskazać koniec nowe działanie</span><span class="sxs-lookup"><span data-stu-id="84329-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8.  <span data-ttu-id="84329-141">Ustaw TLS do starego gAId.</span><span class="sxs-lookup"><span data-stu-id="84329-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="84329-142">W poniższym przykładzie pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="84329-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="84329-143">W tym przykładzie przyjęto założenie, blokowania połączeń są wysyłane w przypadku przenoszenia do nowego działania i obejmuje wstrzymanie/wznowienie śladów.</span><span class="sxs-lookup"><span data-stu-id="84329-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84329-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84329-144">See Also</span></span>  
 [<span data-ttu-id="84329-145">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="84329-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="84329-146">Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="84329-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="84329-147">Scenariusze kompleksowego śledzenia</span><span class="sxs-lookup"><span data-stu-id="84329-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="84329-148">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="84329-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
