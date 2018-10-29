---
title: Transfer
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 360367803fc014c83ae377309b9029dafa3040bd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202897"
---
# <a name="transfer"></a><span data-ttu-id="6ec30-102">Transfer</span><span class="sxs-lookup"><span data-stu-id="6ec30-102">Transfer</span></span>
<span data-ttu-id="6ec30-103">W tym temacie opisano transfer w modelu śledzenie aktywności Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6ec30-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="6ec30-104">Definicja transferu</span><span class="sxs-lookup"><span data-stu-id="6ec30-104">Transfer Definition</span></span>  
 <span data-ttu-id="6ec30-105">Transfery między działaniami reprezentują przyczynowego relacje między zdarzeniami powiązanych działań w obrębie punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="6ec30-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="6ec30-106">Dwa działania są powiązane w przypadku transferów, gdy kontrolka przepływa między te działania, na przykład, wywołanie metody przekraczające granice działania.</span><span class="sxs-lookup"><span data-stu-id="6ec30-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="6ec30-107">W programie WCF w przypadku Bajty przychodzące od usługi, działania nasłuchiwania na jest przekazywana do działania odbieranie bajtów tworzona obiekt komunikatu.</span><span class="sxs-lookup"><span data-stu-id="6ec30-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="6ec30-108">Aby uzyskać listę scenariuszy śledzenia end-to-end oraz ich odpowiednich działań i śledzenia projektu, zobacz [scenariusze śledzenia End-To-End](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="6ec30-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="6ec30-109">Aby emitować transferu danych śledzenia, należy użyć `ActivityTracing` ustawienie dla źródła śledzenia, jak pokazano w następującym kodem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6ec30-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="6ec30-110">Aby skorelować działań w ramach punktów końcowych przy użyciu transferu</span><span class="sxs-lookup"><span data-stu-id="6ec30-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="6ec30-111">Działania i transfery zezwolić użytkownikowi probabilistically znaleźć przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="6ec30-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="6ec30-112">Na przykład jeśli firma Microsoft, przesyłać i z powrotem między działaniami M i N odpowiednio w składnikach, M i N i awarii, odbywa się w prawej N po przeniesieniu do M, firma Microsoft narysować wniosku, że prawdopodobnie z powodu firmy N przekazywanie danych do M.</span><span class="sxs-lookup"><span data-stu-id="6ec30-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="6ec30-113">Śledzenie transferu jest emitowane przez działanie M działania N po przepływ sterowania między M i N. Na przykład N wykonuje jakąś pracę M ze względu na wywołania metody przekraczające granice działań.</span><span class="sxs-lookup"><span data-stu-id="6ec30-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="6ec30-114">N już istnieje lub została utworzona.</span><span class="sxs-lookup"><span data-stu-id="6ec30-114">N may already exist or has been created.</span></span> <span data-ttu-id="6ec30-115">N jest rozprzestrzeniony, M, gdy N jest nowe działanie, które wykonuje jakąś pracę na M.</span><span class="sxs-lookup"><span data-stu-id="6ec30-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="6ec30-116">Transfer z M, n może nie może występować transferu wstecz od N do M. Jest to spowodowane M można zduplikować część prac w N i "nie Śledź" gdy N kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="6ec30-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="6ec30-117">W rzeczywistości M może zakończyć przed N zakończeniem jej zadania.</span><span class="sxs-lookup"><span data-stu-id="6ec30-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="6ec30-118">Dzieje się tak w działaniu "Otwórz ServiceHost" (M), które spowoduje utworzenie odbiornika działań (N), a następnie kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="6ec30-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="6ec30-119">Transfer wstecz od N do M oznacza, że N ukończona praca związana M.</span><span class="sxs-lookup"><span data-stu-id="6ec30-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="6ec30-120">N może kontynuować inne procesy przetwarzania niezwiązanych ze sobą na M, na przykład istniejące działanie wystawcy uwierzytelnienia (N), które utrzymuje odbierania żądań logowania (M) z działania innej nazwy logowania.</span><span class="sxs-lookup"><span data-stu-id="6ec30-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="6ec30-121">Relacji zagnieżdżenia używa nie zawsze istnieje między działaniami M i N. Może to nastąpić z dwóch powodów.</span><span class="sxs-lookup"><span data-stu-id="6ec30-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="6ec30-122">Najpierw podczas działania M nie monitoruje faktyczne przetwarzanie wykonywane w N mimo, że zainicjowano M N. Sekunda, gdy N już istnieje.</span><span class="sxs-lookup"><span data-stu-id="6ec30-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="6ec30-123">Przykład transferu</span><span class="sxs-lookup"><span data-stu-id="6ec30-123">Example of Transfers</span></span>  
 <span data-ttu-id="6ec30-124">Wyświetla dwa poniższe transferu przykłady.</span><span class="sxs-lookup"><span data-stu-id="6ec30-124">The following lists two transfer examples.</span></span>  
  
-   <span data-ttu-id="6ec30-125">Podczas tworzenia hosta usługi konstruktora uzyska kontrolę z kod wywołujący lub kod wywołujący przekazuje do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="6ec30-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="6ec30-126">Po zakończeniu konstruktora wykonywania przekazuje sterowanie do wywołującego kodu lub Konstruktor przenosi się do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6ec30-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="6ec30-127">Dotyczy to zagnieżdżonych relacji.</span><span class="sxs-lookup"><span data-stu-id="6ec30-127">This is the case of a nested relationship.</span></span>  
  
-   <span data-ttu-id="6ec30-128">Po uruchomieniu odbiornika przetwarzania danych transportu tworzy nowy wątek i przekazuje do działania odbierania bajtów odpowiedniego kontekstu do przetwarzania, przekazując kontrolę i danych.</span><span class="sxs-lookup"><span data-stu-id="6ec30-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="6ec30-129">Po zakończeniu tego wątku podczas przetwarzania żądania, działanie odbieranie bajtów przekazuje nic do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6ec30-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="6ec30-130">W tym przypadku mamy transfer w, ale żaden transfer poza nowe działanie wątku.</span><span class="sxs-lookup"><span data-stu-id="6ec30-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="6ec30-131">Dwa działania są powiązane, ale nie zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="6ec30-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="6ec30-132">Seria przeniesienia działania</span><span class="sxs-lookup"><span data-stu-id="6ec30-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="6ec30-133">Poprawnie sformułowany działania sekwencji transferu obejmuje następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="6ec30-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1.  <span data-ttu-id="6ec30-134">Rozpocznij nowe działanie wybrać nowy gAId.</span><span class="sxs-lookup"><span data-stu-id="6ec30-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2.  <span data-ttu-id="6ec30-135">Emituj śledzenia przeniesienia do tego nowego gAId z bieżący identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="6ec30-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3.  <span data-ttu-id="6ec30-136">Ustaw nowy identyfikator w protokole TLS</span><span class="sxs-lookup"><span data-stu-id="6ec30-136">Set the new ID in TLS</span></span>  
  
4.  <span data-ttu-id="6ec30-137">Emituj Rozpocznij śledzenie w celu określenia początku nowe działanie przez.</span><span class="sxs-lookup"><span data-stu-id="6ec30-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5.  <span data-ttu-id="6ec30-138">Powrót do oryginalnego działania składa się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6ec30-138">Return to the original activity consists of the following:</span></span>  
  
6.  <span data-ttu-id="6ec30-139">Emituj śledzenia transferu do oryginalnego gAId</span><span class="sxs-lookup"><span data-stu-id="6ec30-139">Emit a transfer trace to the original gAId</span></span>  
  
7.  <span data-ttu-id="6ec30-140">Emituj Zatrzymaj śledzenie, aby wskazać koniec nowe działanie</span><span class="sxs-lookup"><span data-stu-id="6ec30-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8.  <span data-ttu-id="6ec30-141">Ustaw TLS gAId stary.</span><span class="sxs-lookup"><span data-stu-id="6ec30-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="6ec30-142">Poniższy przykład kodu pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="6ec30-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="6ec30-143">W tym przykładzie przyjęto założenie, wywołania blokowania jest wykonywane podczas przenoszenia do nowego działania i zawiera wstrzymań/wznowień ślady.</span><span class="sxs-lookup"><span data-stu-id="6ec30-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ec30-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ec30-144">See Also</span></span>  
 [<span data-ttu-id="6ec30-145">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="6ec30-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="6ec30-146">Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="6ec30-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="6ec30-147">Scenariusze kompleksowego śledzenia</span><span class="sxs-lookup"><span data-stu-id="6ec30-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="6ec30-148">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="6ec30-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
