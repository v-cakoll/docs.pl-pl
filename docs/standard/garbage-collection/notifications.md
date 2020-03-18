---
title: Powiadomienia dotyczące odzyskiwania pamięci
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
ms.openlocfilehash: d5646c4969c95350ab4cd63b16f6f99ffba3a4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131534"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="49199-102">Powiadomienia dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="49199-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="49199-103">Istnieją sytuacje, w których pełne wyrzucania elementów bezużytecznych (czyli kolekcji generacji 2) przez kod uruchomieniowy języka wspólnego może niekorzystnie wpłynąć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="49199-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="49199-104">Może to być problem szczególnie z serwerami, które przetwarzają duże ilości żądań; w takim przypadku długi wyrzucania elementów bezużytecznych może spowodować uchybienie żądania. Aby zapobiec wystąpieniu pełnej kolekcji w krytycznym okresie, można powiadomić, że zbliża się pełne wyrzucanie elementów bezużytecznych, a następnie podjąć działania, aby przekierować obciążenie do innego wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="49199-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="49199-105">Można również wywołać kolekcji samodzielnie, pod warunkiem, że bieżące wystąpienie serwera nie trzeba przetwarzać żądania.</span><span class="sxs-lookup"><span data-stu-id="49199-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="49199-106">Metoda <xref:System.GC.RegisterForFullGCNotification%2A> rejestruje powiadomienie, które mają być wywoływane, gdy czas wykonywania wyczuwa, że zbliża się pełne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="49199-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="49199-107">Istnieją dwie części tego powiadomienia: gdy zbliża się pełna wyrzucania elementów bezużytecznych i po zakończeniu pełnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="49199-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="49199-108">Tylko blokowanie wyrzucania elementów bezużytecznych zgłaszapowiadomienia.</span><span class="sxs-lookup"><span data-stu-id="49199-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="49199-109">Po włączeniu elementu konfiguracji [ \<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) wyrzucanie elementów bezużytecznych w tle nie będzie zgłaszać powiadomień.</span><span class="sxs-lookup"><span data-stu-id="49199-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="49199-110">Aby określić, kiedy powiadomienie zostało <xref:System.GC.WaitForFullGCApproach%2A> zgłoszone, należy użyć i <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49199-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="49199-111">Zazwyczaj używasz tych metod w `while` pętli, aby stale <xref:System.GCNotificationStatus> uzyskiwać wyliczenie, które pokazuje stan powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="49199-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="49199-112">Jeśli ta <xref:System.GCNotificationStatus.Succeeded>wartość jest , można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="49199-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="49199-113">W odpowiedzi na powiadomienie <xref:System.GC.WaitForFullGCApproach%2A> uzyskane za pomocą metody można przekierować obciążenia i ewentualnie wywołać kolekcji samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="49199-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="49199-114">W odpowiedzi na powiadomienie <xref:System.GC.WaitForFullGCComplete%2A> uzyskane za pomocą metody można udostępnić bieżące wystąpienie serwera do ponownego przetworzenia żądań.</span><span class="sxs-lookup"><span data-stu-id="49199-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="49199-115">Można również zbierać informacje.</span><span class="sxs-lookup"><span data-stu-id="49199-115">You can also gather information.</span></span> <span data-ttu-id="49199-116">Na przykład można użyć <xref:System.GC.CollectionCount%2A> metody do rejestrowania liczby kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49199-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="49199-117">Metody <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> są przeznaczone do współpracy.</span><span class="sxs-lookup"><span data-stu-id="49199-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="49199-118">Za pomocą jednego bez drugiego może produkować nieokreślone wyniki.</span><span class="sxs-lookup"><span data-stu-id="49199-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="49199-119">Pełne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="49199-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="49199-120">Środowiska uruchomieniowego powoduje pełne wyrzucanie elementów bezużytecznych, gdy którykolwiek z następujących scenariuszy są prawdziwe:</span><span class="sxs-lookup"><span data-stu-id="49199-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="49199-121">Wystarczająca ilość pamięci została wyawansona do generacji 2, aby spowodować kolekcję następnej generacji 2.</span><span class="sxs-lookup"><span data-stu-id="49199-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="49199-122">Wystarczająca ilość pamięci została wyawansona do sterty dużych obiektów, aby spowodować nowej generacji 2 kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49199-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="49199-123">Kolekcja generacji 1 jest eskalowana do kolekcji generacji 2 ze względu na inne czynniki.</span><span class="sxs-lookup"><span data-stu-id="49199-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="49199-124">Progi określone w <xref:System.GC.RegisterForFullGCNotification%2A> metodzie dotyczą dwóch pierwszych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="49199-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="49199-125">Jednak w pierwszym scenariuszu nie zawsze otrzymasz powiadomienie w czasie proporcjonalnym do wartości progowych, które określisz z dwóch powodów:</span><span class="sxs-lookup"><span data-stu-id="49199-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="49199-126">Czas wykonywania nie sprawdza każdej alokacji małych obiektów (ze względu na wydajność).</span><span class="sxs-lookup"><span data-stu-id="49199-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="49199-127">Tylko kolekcje 1 generacji promują pamięć w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="49199-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="49199-128">Trzeci scenariusz przyczynia się również do niepewności co do tego, kiedy otrzymasz powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="49199-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="49199-129">Mimo że nie jest to gwarancja, okaże się być przydatnym sposobem złagodzenia skutków nieodpowiedniego pełnego wyrzucania elementów bezużytecznych, przekierowując żądania w tym czasie lub wywołując kolekcję samodzielnie, gdy może być lepiej zakwaterowana.</span><span class="sxs-lookup"><span data-stu-id="49199-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="49199-130">Parametry progu powiadomień</span><span class="sxs-lookup"><span data-stu-id="49199-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="49199-131">Metoda <xref:System.GC.RegisterForFullGCNotification%2A> ma dwa parametry, aby określić wartości progowe obiektów generacji 2 i sterty dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="49199-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="49199-132">Po spełnieniu tych wartości należy zgłaszać powiadomienie o wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="49199-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="49199-133">W poniższej tabeli opisano te parametry.</span><span class="sxs-lookup"><span data-stu-id="49199-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="49199-134">Parametr</span><span class="sxs-lookup"><span data-stu-id="49199-134">Parameter</span></span>|<span data-ttu-id="49199-135">Opis</span><span class="sxs-lookup"><span data-stu-id="49199-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="49199-136">Liczba z lat 1-99 określająca, kiedy powiadomienie powinno być wywoływane na podstawie obiektów promowanych w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="49199-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="49199-137">Liczba z lat 1-99 określająca, kiedy powiadomienie powinno być wywoływane na podstawie obiektów przydzielonych w stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="49199-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="49199-138">Jeśli określisz wartość, która jest zbyt wysoka, istnieje duże prawdopodobieństwo, że otrzymasz powiadomienie, ale może to być zbyt długi okres oczekiwania, zanim środowiska uruchomieniowego powoduje kolekcję.</span><span class="sxs-lookup"><span data-stu-id="49199-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="49199-139">Jeśli wywołasz kolekcji samodzielnie, można odzyskać więcej obiektów niż zostanie odzyskane, jeśli środowiska uruchomieniowego powoduje kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49199-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="49199-140">Jeśli określisz wartość, która jest zbyt niska, czas wykonywania może spowodować kolekcji, zanim masz wystarczająco dużo czasu, aby otrzymywać powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="49199-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49199-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="49199-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="49199-142">Opis</span><span class="sxs-lookup"><span data-stu-id="49199-142">Description</span></span>  
 <span data-ttu-id="49199-143">W poniższym przykładzie grupa serwerów usługi przychodzących żądań sieci Web.</span><span class="sxs-lookup"><span data-stu-id="49199-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="49199-144">Aby symulować obciążenie przetwarzania żądań, tablice <xref:System.Collections.Generic.List%601> bajtów są dodawane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49199-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="49199-145">Każdy serwer rejestruje się dla powiadomienia wyrzucania elementów `WaitForFullGCProc` bezużytecznych, a <xref:System.GCNotificationStatus> następnie uruchamia wątek na metodę <xref:System.GC.WaitForFullGCApproach%2A> użytkownika, aby stale monitorować wyliczenie, które jest zwracane przez i <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49199-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="49199-146">Metody <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> wywołać ich odpowiednich metod obsługi zdarzeń użytkownika, gdy powiadomienie jest wywoływane:</span><span class="sxs-lookup"><span data-stu-id="49199-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="49199-147">Ta metoda `RedirectRequests` wywołuje metodę użytkownika, która nakazuje serwerowi kolejki żądań zawieszenie wysyłania żądań do serwera.</span><span class="sxs-lookup"><span data-stu-id="49199-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="49199-148">Jest to symulowane przez ustawienie `bAllocate` zmiennej na poziomie klasy tak, aby `false` nie więcej obiektów są przydzielane.</span><span class="sxs-lookup"><span data-stu-id="49199-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="49199-149">Następnie metoda `FinishExistingRequests` użytkownika jest wywoływana, aby zakończyć przetwarzanie oczekujących żądań serwera.</span><span class="sxs-lookup"><span data-stu-id="49199-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="49199-150">Jest to symulowane <xref:System.Collections.Generic.List%601> przez wyczyszczenie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49199-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="49199-151">Na koniec wyrzucanie elementów bezużytecznych jest indukowany, ponieważ obciążenie jest lekkie.</span><span class="sxs-lookup"><span data-stu-id="49199-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="49199-152">Ta metoda wywołuje `AcceptRequests` metodę użytkownika, aby wznowić akceptowanie żądań, ponieważ serwer nie jest już podatny na pełne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="49199-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="49199-153">Ta akcja jest symulowana `bAllocate` przez `true` ustawienie zmiennej tak, <xref:System.Collections.Generic.List%601> aby obiekty mogły zostać wznowione dodawane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="49199-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="49199-154">Poniższy kod zawiera `Main` metodę przykładu.</span><span class="sxs-lookup"><span data-stu-id="49199-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="49199-155">Poniższy kod zawiera `WaitForFullGCProc` metodę użytkownika, który zawiera ciągłe while pętli, aby sprawdzić, czy powiadomienia wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="49199-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="49199-156">Poniższy kod zawiera `OnFullGCApproachNotify` metodę wywoływana z</span><span class="sxs-lookup"><span data-stu-id="49199-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="49199-157">`WaitForFullGCProc`Metoda.</span><span class="sxs-lookup"><span data-stu-id="49199-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="49199-158">Poniższy kod zawiera `OnFullGCApproachComplete` metodę wywoływana z</span><span class="sxs-lookup"><span data-stu-id="49199-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="49199-159">`WaitForFullGCProc`Metoda.</span><span class="sxs-lookup"><span data-stu-id="49199-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="49199-160">Poniższy kod zawiera metody użytkownika, które `OnFullGCApproachNotify` są `OnFullGCCompleteNotify` wywoływane z i metody.</span><span class="sxs-lookup"><span data-stu-id="49199-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="49199-161">Metody użytkownika przekierowują żądania, kończą istniejące żądania, a następnie wznawiają żądania po wystąpieniu pełnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="49199-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="49199-162">Cały przykład kodu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="49199-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="49199-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49199-163">See also</span></span>

- [<span data-ttu-id="49199-164">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="49199-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
