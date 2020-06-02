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
ms.openlocfilehash: 389e851782edb82578c216951be440070b92723c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286005"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="0abd3-102">Powiadomienia dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="0abd3-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="0abd3-103">Istnieją sytuacje, w których pełne odzyskiwanie pamięci (czyli kolekcja generacji 2) przez środowisko uruchomieniowe języka wspólnego może niekorzystnie wpłynąć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="0abd3-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="0abd3-104">Może to być problem szczególnie w przypadku serwerów, które przetwarzają duże ilości żądań; w takim przypadku długotrwałe wyrzucanie elementów bezużytecznych może spowodować przekroczenie limitu czasu żądania. Aby zapobiec występowaniu pełnej kolekcji w okresie krytycznym, można powiadomić o tym, że pełne odzyskiwanie pamięci zbliża się, a następnie podejmuje działania w celu przekierowania obciążenia do innego wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="0abd3-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="0abd3-105">Istnieje również możliwość wywołania kolekcji samodzielnie, pod warunkiem, że bieżące wystąpienie serwera nie musi przetwarzać żądań.</span><span class="sxs-lookup"><span data-stu-id="0abd3-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="0abd3-106"><xref:System.GC.RegisterForFullGCNotification%2A>Metoda rejestruje powiadomienie, które zostanie wywołane, gdy środowisko uruchomieniowe wskazuje, że zbliża się pełne odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="0abd3-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="0abd3-107">Istnieją dwie części tego powiadomienia: Kiedy pełne odzyskiwanie pamięci zbliża się i gdy pełne odzyskiwanie pamięci zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="0abd3-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="0abd3-108">Tylko blokowanie wyrzucania elementów bezużytecznych powiadomień.</span><span class="sxs-lookup"><span data-stu-id="0abd3-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="0abd3-109">Gdy [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) element konfiguracji jest włączony, wyrzucanie elementów bezużytecznych w tle nie spowoduje zgłoszenia powiadomień.</span><span class="sxs-lookup"><span data-stu-id="0abd3-109">When the [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="0abd3-110">Aby określić, kiedy zostało zgłoszone powiadomienie, użyj <xref:System.GC.WaitForFullGCApproach%2A> metod i <xref:System.GC.WaitForFullGCComplete%2A> .</span><span class="sxs-lookup"><span data-stu-id="0abd3-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="0abd3-111">Zwykle te metody są używane w pętli, `while` aby stale uzyskiwać <xref:System.GCNotificationStatus> Wyliczenie, które pokazuje stan powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="0abd3-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="0abd3-112">W przypadku tej wartości <xref:System.GCNotificationStatus.Succeeded> można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0abd3-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="0abd3-113">W odpowiedzi na powiadomienie uzyskane przy użyciu <xref:System.GC.WaitForFullGCApproach%2A> metody można przekierować obciążenie i ewentualnie wywołać kolekcję.</span><span class="sxs-lookup"><span data-stu-id="0abd3-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="0abd3-114">W odpowiedzi na powiadomienie uzyskane przy użyciu <xref:System.GC.WaitForFullGCComplete%2A> metody można sprawić, aby bieżące wystąpienie serwera było dostępne do ponownego przetwarzania żądań.</span><span class="sxs-lookup"><span data-stu-id="0abd3-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="0abd3-115">Możesz również zebrać informacje.</span><span class="sxs-lookup"><span data-stu-id="0abd3-115">You can also gather information.</span></span> <span data-ttu-id="0abd3-116">Na przykład możesz użyć <xref:System.GC.CollectionCount%2A> metody, aby zarejestrować liczbę kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0abd3-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="0abd3-117"><xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> Metody i są zaprojektowane tak, aby współdziałać.</span><span class="sxs-lookup"><span data-stu-id="0abd3-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="0abd3-118">Użycie jednego bez nich może spowodować uzyskanie nieokreślonych wyników.</span><span class="sxs-lookup"><span data-stu-id="0abd3-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="0abd3-119">Pełne odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="0abd3-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="0abd3-120">Środowisko uruchomieniowe powoduje pełne wyrzucanie elementów bezużytecznych, gdy spełnione są dowolne z następujących scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="0abd3-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="0abd3-121">Dostateczna ilość pamięci została podwyższona do generacji 2 w celu spowodowania nowej kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="0abd3-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="0abd3-122">Zbyt mała ilość pamięci została podzielona na stertę dużego obiektu, aby spowodować wystąpienie następnej generacji 2.</span><span class="sxs-lookup"><span data-stu-id="0abd3-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="0abd3-123">Kolekcja generacji 1 jest eskalacją do kolekcji 2 generacji ze względu na inne czynniki.</span><span class="sxs-lookup"><span data-stu-id="0abd3-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="0abd3-124">Progi określone w <xref:System.GC.RegisterForFullGCNotification%2A> metodzie stosują się do pierwszych dwóch scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="0abd3-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="0abd3-125">Jednak w pierwszym scenariuszu nie zawsze otrzymasz powiadomienie w czasie proporcjonalnym do wartości progowych określonych z dwóch powodów:</span><span class="sxs-lookup"><span data-stu-id="0abd3-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="0abd3-126">Środowisko uruchomieniowe nie sprawdza poszczególnych alokacji małych obiektów (ze względu na wydajność).</span><span class="sxs-lookup"><span data-stu-id="0abd3-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="0abd3-127">Tylko kolekcje generacji 1 promują pamięć do generacji 2.</span><span class="sxs-lookup"><span data-stu-id="0abd3-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="0abd3-128">Trzeci scenariusz przyczynia się również do niepewności, kiedy otrzymasz powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="0abd3-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="0abd3-129">Chociaż nie jest to gwarancja, warto zastanowić się, że jest to przydatny sposób na uniknięcie efektów inopportune pełnego odzyskiwania pamięci przez przekierowanie żądań w tym czasie lub wypróbowanie kolekcji, gdy będzie można lepiej obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="0abd3-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="0abd3-130">Parametry progu powiadomienia</span><span class="sxs-lookup"><span data-stu-id="0abd3-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="0abd3-131"><xref:System.GC.RegisterForFullGCNotification%2A>Metoda ma dwa parametry, aby określić wartości progowe obiektów generacji 2 i sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="0abd3-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="0abd3-132">Gdy te wartości są spełnione, powinno zostać zgłoszone powiadomienie o wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0abd3-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="0abd3-133">W poniższej tabeli opisano te parametry.</span><span class="sxs-lookup"><span data-stu-id="0abd3-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="0abd3-134">Parametr</span><span class="sxs-lookup"><span data-stu-id="0abd3-134">Parameter</span></span>|<span data-ttu-id="0abd3-135">Opis</span><span class="sxs-lookup"><span data-stu-id="0abd3-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="0abd3-136">Liczba z zakresu od 1 do 99 określająca, kiedy powiadomienie powinno zostać zgłoszone na podstawie obiektów podniesionych w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="0abd3-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="0abd3-137">Liczba z zakresu od 1 do 99 określająca, kiedy powiadomienie powinno być zgłaszane na podstawie obiektów, które są przydzielane w stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="0abd3-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="0abd3-138">Jeśli określisz zbyt wysoką wartość, istnieje wysokie prawdopodobieństwo, że otrzymasz powiadomienie, ale może to być zbyt długi czas oczekiwania przed wykonaniem przez środowisko uruchomieniowe kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0abd3-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="0abd3-139">Jeśli samodzielnie wywołująsz kolekcję, możesz odwoływać więcej obiektów, niż byłoby to odrzucane, jeśli środowisko uruchomieniowe powoduje wystąpienie tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0abd3-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="0abd3-140">Jeśli określisz zbyt niską wartość, środowisko uruchomieniowe może spowodować, że zbieranie danych będzie wymagało wystarczającej ilości czasu na powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="0abd3-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0abd3-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="0abd3-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0abd3-142">Opis</span><span class="sxs-lookup"><span data-stu-id="0abd3-142">Description</span></span>  
 <span data-ttu-id="0abd3-143">W poniższym przykładzie Grupa serwerów obsługuje przychodzące żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0abd3-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="0abd3-144">Aby symulować obciążenie żądań przetwarzania, tablice bajtowe są dodawane do <xref:System.Collections.Generic.List%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0abd3-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="0abd3-145">Każdy serwer rejestruje do powiadomienia o wyrzucaniu elementów bezużytecznych, a następnie uruchamia wątek w `WaitForFullGCProc` metodzie użytkownika w celu ciągłego monitorowania <xref:System.GCNotificationStatus> wyliczenia zwracanego przez <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metod.</span><span class="sxs-lookup"><span data-stu-id="0abd3-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="0abd3-146"><xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> Metody i zadzwonią odpowiednie metody użytkownika obsługującego zdarzenia, gdy zostanie zgłoszone powiadomienie:</span><span class="sxs-lookup"><span data-stu-id="0abd3-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="0abd3-147">Ta metoda wywołuje `RedirectRequests` metodę użytkownika, która instruuje serwer kolejkowania żądań, aby zawiesić wysyłanie żądań do serwera.</span><span class="sxs-lookup"><span data-stu-id="0abd3-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="0abd3-148">Jest to symulowane przez ustawienie zmiennej poziomu klasy `bAllocate` na `false` tak, aby nie przydzielono kolejnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="0abd3-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="0abd3-149">Następnie `FinishExistingRequests` Metoda użytkownika jest wywoływana, aby zakończyć przetwarzanie oczekujących żądań serwera.</span><span class="sxs-lookup"><span data-stu-id="0abd3-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="0abd3-150">Jest to symulowane przez wyczyszczenie <xref:System.Collections.Generic.List%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0abd3-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="0abd3-151">Na koniec wyrzucanie elementów bezużytecznych jest wywołane, ponieważ obciążenie jest jasne.</span><span class="sxs-lookup"><span data-stu-id="0abd3-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="0abd3-152">Ta metoda wywołuje metodę użytkownika `AcceptRequests` w celu wznowienia akceptowania żądań, ponieważ serwer nie jest już podatny na pełne odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="0abd3-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="0abd3-153">Ta akcja jest symulowana przez ustawienie `bAllocate` zmiennej na `true` tak, aby obiekty mogły zostać wznowione do <xref:System.Collections.Generic.List%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0abd3-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="0abd3-154">Poniższy kod zawiera `Main` metodę przykładu.</span><span class="sxs-lookup"><span data-stu-id="0abd3-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="0abd3-155">Poniższy kod zawiera `WaitForFullGCProc` metodę użytkownika, która zawiera ciągłą pętlę while, aby sprawdzić powiadomienia o wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0abd3-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="0abd3-156">Poniższy kod zawiera `OnFullGCApproachNotify` metodę wywoływaną z</span><span class="sxs-lookup"><span data-stu-id="0abd3-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="0abd3-157">`WaitForFullGCProc`Method.</span><span class="sxs-lookup"><span data-stu-id="0abd3-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="0abd3-158">Poniższy kod zawiera `OnFullGCApproachComplete` metodę wywoływaną z</span><span class="sxs-lookup"><span data-stu-id="0abd3-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="0abd3-159">`WaitForFullGCProc`Method.</span><span class="sxs-lookup"><span data-stu-id="0abd3-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="0abd3-160">Poniższy kod zawiera metody użytkownika, które są wywoływane z `OnFullGCApproachNotify` `OnFullGCCompleteNotify` metod i.</span><span class="sxs-lookup"><span data-stu-id="0abd3-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="0abd3-161">Metody użytkownika przekierowują żądania, kończyć istniejące żądania, a następnie wznawiają żądania po wystąpieniu pełnego odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="0abd3-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="0abd3-162">Cały przykład kodu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="0abd3-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0abd3-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0abd3-163">See also</span></span>

- [<span data-ttu-id="0abd3-164">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="0abd3-164">Garbage Collection</span></span>](index.md)
