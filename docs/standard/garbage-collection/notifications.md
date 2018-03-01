---
title: "Powiadomienia dotyczące odzyskiwania pamięci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ac951ad1f89d058b06280bc176ca7928a1dc65bf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="f0d2a-102">Powiadomienia dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="f0d2a-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="f0d2a-103">Istnieją sytuacje, w których pełnego wyrzucania elementów bezużytecznych (czyli kolekcji generacji 2) przez środowisko uruchomieniowe języka wspólnego może niekorzystnie wpłynąć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="f0d2a-104">Może to być problem szczególnie z serwerów, które przetwarzają dużą liczbę żądań; w takim przypadku długich wyrzucania elementów bezużytecznych może spowodować limit czasu żądania. Aby zapobiec pełną kolekcję wystąpienia krytyczny okres, użytkownik może zostać powiadomiony czy pełnego wyrzucania elementów bezużytecznych zbliża się do, a następnie podjęcia działania, aby przekierować obciążenia do innego wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="f0d2a-105">Użytkownik może także wywołać kolekcji samodzielnie, pod warunkiem, że bieżące wystąpienie serwera nie jest konieczne przetwarzanie żądań.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="f0d2a-106"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda rejestruje powiadomienia do wywołania, gdy środowisko uruchomieniowe wykrywa, że zbliża się do pełnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="f0d2a-107">To powiadomienie, składa się z dwóch części: gdy zbliża się do pełnego wyrzucania elementów bezużytecznych i po zakończeniu pełnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f0d2a-108">Kolekcje garbage blokujące tylko wywoływanie powiadomień o.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="f0d2a-109">Gdy [ \<gcconcurrent — >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) element konfiguracji jest włączona, wyrzucania tła nie będą powodowały powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="f0d2a-110">Aby określić, kiedy powiadomienie zostanie podniesiony, użyj <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="f0d2a-111">Zazwyczaj korzystają z tych metod w `while` pętli stale uzyskanie <xref:System.GCNotificationStatus> wyliczenia, który zawiera stan powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="f0d2a-112">Jeśli ta wartość jest <xref:System.GCNotificationStatus.Succeeded>, można wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f0d2a-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
-   <span data-ttu-id="f0d2a-113">W odpowiedzi na powiadomienie uzyskany z <xref:System.GC.WaitForFullGCApproach%2A> metody, można przekierować obciążenia i kolekcji prawdopodobnie wywoływać, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
-   <span data-ttu-id="f0d2a-114">W odpowiedzi na powiadomienie uzyskany z <xref:System.GC.WaitForFullGCComplete%2A> metody, możesz wprowadzić bieżące wystąpienie serwera dostępnych do przetwarzania żądań ponownie.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="f0d2a-115">Można także gromadzić informacje.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-115">You can also gather information.</span></span> <span data-ttu-id="f0d2a-116">Na przykład można użyć <xref:System.GC.CollectionCount%2A> metody do rejestrowania wielu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="f0d2a-117"><xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody zostały zaprojektowane do siebie.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="f0d2a-118">Przy użyciu jednej bez innych może dać wyniki nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="f0d2a-119">Pełnego wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="f0d2a-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="f0d2a-120">Środowisko uruchomieniowe powoduje, że pełnego wyrzucania elementów bezużytecznych po spełnieniu jednego z następujących scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="f0d2a-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
-   <span data-ttu-id="f0d2a-121">Za mało pamięci został podniesiony do generacji 2, aby spowodować kolekcji następnej generacji 2.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="f0d2a-122">Za mało pamięci został podniesiony do sterty dużego obiektu spowodować kolekcji następnej generacji 2.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="f0d2a-123">Kolekcja generacji 1 jest przekazany do kolekcji generacji 2 z powodu innych czynników.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="f0d2a-124">Progi w <xref:System.GC.RegisterForFullGCNotification%2A> metoda stosowana w przypadku dwóch pierwszych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="f0d2a-125">Jednak w scenariuszu pierwszy nie zawsze otrzymasz powiadomienie w momencie proporcjonalny do wartości progowe, które określisz dwóch powodów:</span><span class="sxs-lookup"><span data-stu-id="f0d2a-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
-   <span data-ttu-id="f0d2a-126">Środowisko uruchomieniowe nie sprawdza każdej alokacji małego obiektu (ze względu na wydajność).</span><span class="sxs-lookup"><span data-stu-id="f0d2a-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
-   <span data-ttu-id="f0d2a-127">Tylko generacji 1 kolekcje podwyższania pamięci w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="f0d2a-128">Trzeci scenariusz przyczynia się również do niedokładność gdy otrzymasz powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="f0d2a-129">Mimo że nie ma gwarancji, okazać się przydatne sposobem łagodzenia skutków nieodpowiednim pełnego wyrzucania elementów bezużytecznych przez przekierowywanie żądań w tym czasie lub wywołania kolekcji samodzielnie, gdy są spełnione lepiej.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="f0d2a-130">Parametry próg powiadomienia</span><span class="sxs-lookup"><span data-stu-id="f0d2a-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="f0d2a-131"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda ma dwa parametry, aby określić wartości progowe obiektów pokolenia 2 oraz sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="f0d2a-132">Po spełnieniu tych wartości, powinien być wywoływany powiadomienie kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="f0d2a-133">W poniższej tabeli opisano te parametry.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="f0d2a-134">Parametr</span><span class="sxs-lookup"><span data-stu-id="f0d2a-134">Parameter</span></span>|<span data-ttu-id="f0d2a-135">Opis</span><span class="sxs-lookup"><span data-stu-id="f0d2a-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="f0d2a-136">Liczbą z zakresu od 1 do 99 określająca, kiedy powiadomienie zostanie zgłoszony oparte na obiektach awansowane w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="f0d2a-137">Liczbą z zakresu od 1 do 99 określająca, kiedy powiadomienie zostanie zgłoszony oparte na obiekty, które są przydzielane w sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="f0d2a-138">Jeśli określono wartość, która jest zbyt wysoka, istnieje wysokie prawdopodobieństwo, otrzymasz powiadomienie, że może być zbyt długiego okresu oczekiwania dla środowiska uruchomieniowego powoduje, że kolekcja.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="f0d2a-139">Jeśli należy wywołać kolekcji samodzielnie, może odzyskać więcej obiektów, nie będzie można odzyskać, jeśli środowisko uruchomieniowe powoduje kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="f0d2a-140">Jeśli określono wartość, która ma zbyt niską wartość, środowisko uruchomieniowe może spowodować kolekcji przed miały wystarczająco dużo czasu, aby otrzymywać powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0d2a-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0d2a-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f0d2a-142">Opis</span><span class="sxs-lookup"><span data-stu-id="f0d2a-142">Description</span></span>  
 <span data-ttu-id="f0d2a-143">W poniższym przykładzie grupy serwerów usługi przychodzących żądań sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="f0d2a-144">Aby symulować obciążenie przetwarzania żądań, tablice typu byte są dodawane do <xref:System.Collections.Generic.List%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="f0d2a-145">Każdy serwer rejestruje powiadomienia kolekcji pamięci, a następnie uruchamia wątek na `WaitForFullGCProc` metoda użytkownika do ciągłego monitorowania <xref:System.GCNotificationStatus> wyliczenia, który jest zwracany przez <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="f0d2a-146"><xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody wywołania ich odpowiednich metod użytkownika obsługi zdarzeń, gdy jest wywoływane powiadomienie:</span><span class="sxs-lookup"><span data-stu-id="f0d2a-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
-   `OnFullGCApproachNotify`  
  
     <span data-ttu-id="f0d2a-147">Ta metoda wywołuje `RedirectRequests` metoda użytkownika, który powoduje, że serwer usługi kolejkowania wiadomości żądania wstrzymania wysyłania żądań do serwera.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="f0d2a-148">Jest to symulowane przez ustawienie zmiennej poziomie klasy `bAllocate` do `false` tak, aby nie więcej obiektów są przydzielone.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="f0d2a-149">Następnie `FinishExistingRequests` użytkownika metoda jest wywoływana na zakończenie przetwarzania żądań oczekujących serwera.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="f0d2a-150">Jest to symulowane przez wyczyszczenie <xref:System.Collections.Generic.List%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="f0d2a-151">Na koniec wyrzucania elementów bezużytecznych jest wywołane, ponieważ obciążenie jest lekki.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
-   `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="f0d2a-152">Ta metoda wywołuje metodę użytkownika `AcceptRequests` wznowienia, akceptując żądania, ponieważ serwer nie jest już podatne na pełnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="f0d2a-153">Ta akcja jest symulowane przez ustawienie `bAllocate` zmienną `true` tak, aby wznowić obiekty dodawane do <xref:System.Collections.Generic.List%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="f0d2a-154">Poniższy kod zawiera `Main` metody przykładu.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="f0d2a-155">Poniższy kod zawiera `WaitForFullGCProc` metoda użytkownika, zawierający ciągły podczas pętli, aby wyszukać powiadomienia dotyczące odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="f0d2a-156">Poniższy kod zawiera `OnFullGCApproachNotify` metoda wywoływana z</span><span class="sxs-lookup"><span data-stu-id="f0d2a-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="f0d2a-157">`WaitForFullGCProc`Metoda.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="f0d2a-158">Poniższy kod zawiera `OnFullGCApproachComplete` metoda wywoływana z</span><span class="sxs-lookup"><span data-stu-id="f0d2a-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="f0d2a-159">`WaitForFullGCProc`Metoda.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="f0d2a-160">Poniższy kod zawiera metody użytkownika, które są wywoływane z `OnFullGCApproachNotify` i `OnFullGCCompleteNotify` metody.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="f0d2a-161">Metody użytkownika przekierować żądania, Zakończ istniejących żądań i wznowienia żądań, po zakończeniu pełnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f0d2a-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="f0d2a-162">Cały kod przykładowy wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="f0d2a-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f0d2a-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0d2a-163">See Also</span></span>  
 [<span data-ttu-id="f0d2a-164">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="f0d2a-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
