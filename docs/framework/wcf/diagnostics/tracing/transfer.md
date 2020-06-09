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
# <a name="transfer"></a><span data-ttu-id="d97d3-102">Transfer</span><span class="sxs-lookup"><span data-stu-id="d97d3-102">Transfer</span></span>
<span data-ttu-id="d97d3-103">W tym temacie opisano transfer w modelu śledzenia działań Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d97d3-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="d97d3-104">Definicja transferu</span><span class="sxs-lookup"><span data-stu-id="d97d3-104">Transfer Definition</span></span>  
 <span data-ttu-id="d97d3-105">Transfery między działaniami reprezentują związek przyczyn między zdarzeniami w pokrewnych działaniach w punktach końcowych.</span><span class="sxs-lookup"><span data-stu-id="d97d3-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="d97d3-106">Dwie działania są powiązane z transferami, gdy sterowanie przepływem między tymi działaniami, na przykład wywołanie metody przecina granice działania.</span><span class="sxs-lookup"><span data-stu-id="d97d3-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="d97d3-107">W programie WCF, gdy w usłudze są przyjmowane bajty, nasłuchiwanie w działaniu jest przesyłane do działania odbierania bajtów, w którym jest tworzony obiekt wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d97d3-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="d97d3-108">Aby zapoznać się z listą kompleksowych scenariuszy śledzenia i ich odpowiedniego projektu działań i śledzenia, zobacz [kompleksowe scenariusze śledzenia](end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="d97d3-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="d97d3-109">Aby emitować ślady transferu, użyj `ActivityTracing` Ustawienia ze źródła śledzenia, jak pokazano w poniższym kodzie konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="d97d3-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="d97d3-110">Używanie transferu do skorelowania działań w punktach końcowych</span><span class="sxs-lookup"><span data-stu-id="d97d3-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="d97d3-111">Działania i transfery umożliwiają użytkownikowi probabilistically lokalizowanie głównej przyczyny błędu.</span><span class="sxs-lookup"><span data-stu-id="d97d3-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="d97d3-112">Jeśli na przykład przeniesiemy z powrotem i wstecz między działaniami M i N w składnikach M i N, a awaria wystąpi w N prawo po przeniesieniu z powrotem do M, możemy sporządzić wniosek, że najprawdopodobniej jest to spowodowane przekazywaniem danych z powrotem do M.</span><span class="sxs-lookup"><span data-stu-id="d97d3-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="d97d3-113">Ślad transferu jest emitowany z działania M do działania N, gdy istnieje przepływ sterowania między M i N. Na przykład N wykonuje część pracy dla M ze względu na to, że wywołanie metody przekracza granice działania.</span><span class="sxs-lookup"><span data-stu-id="d97d3-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="d97d3-114">N może już istnieć lub został utworzony.</span><span class="sxs-lookup"><span data-stu-id="d97d3-114">N may already exist or has been created.</span></span> <span data-ttu-id="d97d3-115">N jest duplikowany przez M, gdy N to nowe działanie, które wykonuje pewną pracę dla M.</span><span class="sxs-lookup"><span data-stu-id="d97d3-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="d97d3-116">Po przekazaniu od M do N nie można wykonać transferu z powrotem z N do M. Jest to spowodowane tym, że M może zduplikować część pracy w N i nie śledzić, gdy N kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="d97d3-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="d97d3-117">W rzeczywistości M może zakończyć się przed N zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="d97d3-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="d97d3-118">Dzieje się tak w przypadku działania "Otwórz ServiceHost" (M), które powoduje zduplikowanie aktywności odbiornika (N), a następnie kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="d97d3-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="d97d3-119">Transfer z powrotem z N do M oznacza, że N ukończył pracę związaną z M.</span><span class="sxs-lookup"><span data-stu-id="d97d3-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="d97d3-120">N może kontynuować wykonywanie innych operacji przetwarzania niezwiązanych z M, na przykład istniejącej aktywności uwierzytelniania (N), która zachowuje żądania logowania (M) z różnych działań logowania.</span><span class="sxs-lookup"><span data-stu-id="d97d3-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="d97d3-121">Relacja zagnieżdżenia nie musi istnieć między działaniami M i N. Może się to zdarzyć z dwóch przyczyn.</span><span class="sxs-lookup"><span data-stu-id="d97d3-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="d97d3-122">Po pierwsze, gdy działanie M nie monitoruje rzeczywistego przetwarzania wykonanego w N, chociaż M zainicjowano N. Sekunda, gdy N już istnieje.</span><span class="sxs-lookup"><span data-stu-id="d97d3-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="d97d3-123">Przykład transferu</span><span class="sxs-lookup"><span data-stu-id="d97d3-123">Example of Transfers</span></span>  
 <span data-ttu-id="d97d3-124">Poniżej wymieniono dwa przykłady transferu.</span><span class="sxs-lookup"><span data-stu-id="d97d3-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="d97d3-125">Podczas tworzenia hosta usługi Konstruktor uzyskuje kontrolę nad wywoływanym kodem lub wywoływanie przesyłanych kodu do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d97d3-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="d97d3-126">Gdy Konstruktor zakończył wykonywanie, zwraca sterowanie do kodu wywołującego lub Konstruktor przesyła z powrotem do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d97d3-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="d97d3-127">Jest to przypadek relacji zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="d97d3-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="d97d3-128">Gdy odbiornik zacznie przetwarzać dane transportu, tworzy nowy wątek i ręce do działania odbierania bajtów, który jest odpowiednim kontekstem do przetwarzania, przekazywania kontroli i danych.</span><span class="sxs-lookup"><span data-stu-id="d97d3-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="d97d3-129">Gdy ten wątek zakończy przetwarzanie żądania, działanie odbieraj bajty kończy się bez powrotu do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="d97d3-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="d97d3-130">W takim przypadku mamy transfer w przypadku, gdy nie przeprowadzono transferu z nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="d97d3-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="d97d3-131">Te dwa działania są powiązane, ale nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="d97d3-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="d97d3-132">Sekwencja transferu działań</span><span class="sxs-lookup"><span data-stu-id="d97d3-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="d97d3-133">Poprawnie sformułowana sekwencja transferu działań obejmuje następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="d97d3-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="d97d3-134">Rozpocznij nowe działanie, które składa się z wyboru nowego gAId.</span><span class="sxs-lookup"><span data-stu-id="d97d3-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="d97d3-135">Emituj ślad transferu do tego nowego gAId z bieżącego identyfikatora działania</span><span class="sxs-lookup"><span data-stu-id="d97d3-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="d97d3-136">Ustaw nowy identyfikator w protokole TLS</span><span class="sxs-lookup"><span data-stu-id="d97d3-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="d97d3-137">Emituj początkowy ślad, aby wskazać początek nowej aktywności przez.</span><span class="sxs-lookup"><span data-stu-id="d97d3-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="d97d3-138">Powrót do oryginalnego działania składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="d97d3-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="d97d3-139">Emituj ślad transferu do oryginalnego gAId</span><span class="sxs-lookup"><span data-stu-id="d97d3-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="d97d3-140">Emituj śledzenie zatrzymania, aby wskazać koniec nowego działania</span><span class="sxs-lookup"><span data-stu-id="d97d3-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="d97d3-141">Ustaw protokół TLS na stary gAId.</span><span class="sxs-lookup"><span data-stu-id="d97d3-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="d97d3-142">Poniższy przykład kodu demonstruje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="d97d3-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="d97d3-143">W tym przykładzie przyjęto założenie, że jest wywoływane wywołanie podczas przenoszenia do nowego działania i zawiera dane śledzenia wstrzymania/wznowienia.</span><span class="sxs-lookup"><span data-stu-id="d97d3-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d97d3-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d97d3-144">See also</span></span>

- [<span data-ttu-id="d97d3-145">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="d97d3-145">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="d97d3-146">Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="d97d3-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="d97d3-147">Scenariusze kompleksowego śledzenia</span><span class="sxs-lookup"><span data-stu-id="d97d3-147">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="d97d3-148">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="d97d3-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
