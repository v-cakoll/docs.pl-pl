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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10f947fc44e69368e30614e0b41eaf7c73fb6563
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026201"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="5483a-102">Powiadomienia dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="5483a-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="5483a-103">Istnieją sytuacje, w których pełne wyrzucanie elementów bezużytecznych (czyli kolekcji generacji 2) przez środowisko uruchomieniowe języka wspólnego może niekorzystnie wpłynąć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="5483a-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="5483a-104">Może to być problem szczególnie z serwerów, które przetwarzają duże ilości żądań; w tym przypadku długo wyrzucania elementów bezużytecznych może powodować limit czasu żądania. Aby zapobiec pełnego występowaniu krytyczny okres, możesz otrzymać, pełne odśmiecanie zbliża się do, a następnie podjęcia działania, aby przekierować obciążenie do innego wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="5483a-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="5483a-105">Można również wywołać kolekcję użytkownika, pod warunkiem, że bieżące wystąpienie serwera nie jest konieczne przetwarzanie żądań.</span><span class="sxs-lookup"><span data-stu-id="5483a-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="5483a-106"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda rejestruje powiadomienie, aby być wywoływane, gdy środowisko uruchomieniowe wykrywa, że zbliża się pełne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5483a-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="5483a-107">To powiadomienie, składa się z dwóch części: kiedy zbliża się pełne wyrzucanie elementów bezużytecznych i kiedy zakończyło się pełne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5483a-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5483a-108">Tylko blokowania wyrzucania elementów bezużytecznych wywoływanie powiadomień.</span><span class="sxs-lookup"><span data-stu-id="5483a-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="5483a-109">Gdy [ \<gcconcurrent — >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) element konfiguracji jest włączona, tle wyrzucania elementów bezużytecznych nie zgłosi powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="5483a-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="5483a-110">Aby określić, gdy zgłoszono powiadomienie, należy użyć <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5483a-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="5483a-111">Zazwyczaj można użyć tych metod w `while` pętli stale uzyskać <xref:System.GCNotificationStatus> wyliczenie, który pokazuje stan powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="5483a-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="5483a-112">Jeśli ta wartość jest <xref:System.GCNotificationStatus.Succeeded>, wykonasz następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5483a-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="5483a-113">W odpowiedzi na powiadomienia otrzymane z <xref:System.GC.WaitForFullGCApproach%2A> metody, można przekierować obciążenia, a kolekcja prawdopodobnie occurs, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="5483a-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="5483a-114">W odpowiedzi na powiadomienia otrzymane z <xref:System.GC.WaitForFullGCComplete%2A> metody, aby włączyć bieżące wystąpienie serwera dostępne do przetwarzania żądań ponownie.</span><span class="sxs-lookup"><span data-stu-id="5483a-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="5483a-115">Można także gromadzić informacje.</span><span class="sxs-lookup"><span data-stu-id="5483a-115">You can also gather information.</span></span> <span data-ttu-id="5483a-116">Na przykład, można użyć <xref:System.GC.CollectionCount%2A> metody do rejestrowania wielu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5483a-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="5483a-117"><xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody są zaprojektowane do wspólnej pracy.</span><span class="sxs-lookup"><span data-stu-id="5483a-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="5483a-118">Przy użyciu jednej bez innych może wygenerować wyniki nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="5483a-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="5483a-119">Pełne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="5483a-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="5483a-120">Środowisko uruchomieniowe powoduje pełne odśmiecanie, w przypadku spełnienia dowolnego z następujących scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="5483a-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="5483a-121">Za mało pamięci został podniesiony do generacji 2, aby spowodować, że następny kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5483a-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="5483a-122">Za mało pamięci został podniesiony do sterty dużych obiektów, aby spowodować, że następny kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5483a-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="5483a-123">Kolekcja elementów w generacji 1 jest przekazany do kolekcji generacji 2 z powodu innych czynników.</span><span class="sxs-lookup"><span data-stu-id="5483a-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="5483a-124">Progi w <xref:System.GC.RegisterForFullGCNotification%2A> metoda stosowana w pierwszych dwóch scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="5483a-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="5483a-125">Jednak w pierwszym scenariuszu możesz nie zawsze będzie otrzymywać powiadomienia w czasie proporcjonalna do wartości progowe, które określisz dwóch powodów:</span><span class="sxs-lookup"><span data-stu-id="5483a-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="5483a-126">Środowisko wykonawcze nie sprawdza każdą alokację obiektu mały (ze względu na wydajność).</span><span class="sxs-lookup"><span data-stu-id="5483a-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="5483a-127">Tylko generacji 1 kolekcji przyczyniają się do pamięci w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5483a-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="5483a-128">Trzeci scenariusz przyczynia się również do niedokładność po użytkownik otrzyma powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="5483a-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="5483a-129">Mimo że nie ma gwarancji, to okazać się przydatny sposób łagodzenia skutków nieodpowiednim pełne wyrzucanie elementów bezużytecznych przez przekierowywanie żądań, w tym czasie lub wykonuje kolekcję samodzielnie, gdy są spełnione lepiej.</span><span class="sxs-lookup"><span data-stu-id="5483a-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="5483a-130">Parametry próg powiadomienia</span><span class="sxs-lookup"><span data-stu-id="5483a-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="5483a-131"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda ma dwa parametry, aby określić wartości progowe obiekty generacji 2 i stos dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5483a-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="5483a-132">Gdy te wartości są spełnione, powinien być wywoływany powiadomienia wyrzucania elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5483a-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="5483a-133">W poniższej tabeli opisano te parametry.</span><span class="sxs-lookup"><span data-stu-id="5483a-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="5483a-134">Parametr</span><span class="sxs-lookup"><span data-stu-id="5483a-134">Parameter</span></span>|<span data-ttu-id="5483a-135">Opis</span><span class="sxs-lookup"><span data-stu-id="5483a-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="5483a-136">Liczbą z zakresu od 1 do 99 określający, kiedy powinien być wywoływany powiadomienia na podstawie obiektów promowany w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="5483a-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="5483a-137">Liczbą z zakresu od 1 do 99 określający, kiedy powinien być wywoływany powiadomienia na podstawie obiektów, które są przydzielane w stosie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5483a-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="5483a-138">Jeśli określono wartość, która jest zbyt duża, istnieje wysokie prawdopodobieństwo, otrzymasz powiadomienie, że może to być zbyt długiego okresu oczekiwania dla środowiska uruchomieniowego powoduje, że kolekcja.</span><span class="sxs-lookup"><span data-stu-id="5483a-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="5483a-139">Jeśli occurs kolekcji, samodzielnie, mogą odzyskać więcej obiektów, nie będzie można odzyskać, jeśli środowisko wykonawcze powoduje, że kolekcja.</span><span class="sxs-lookup"><span data-stu-id="5483a-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="5483a-140">Jeśli określono wartość, która ma zbyt niską wartość, środowisko uruchomieniowe może spowodować kolekcji przed miały wystarczająco dużo czasu, aby otrzymywać powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="5483a-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5483a-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="5483a-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5483a-142">Opis</span><span class="sxs-lookup"><span data-stu-id="5483a-142">Description</span></span>  
 <span data-ttu-id="5483a-143">W poniższym przykładzie grupa serwerów usługi przychodzących żądań sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5483a-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="5483a-144">Aby zasymulować obciążenie przetwarzania żądań, tablice bajtowe są dodawane do <xref:System.Collections.Generic.List%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5483a-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="5483a-145">Każdy serwer rejestruje powiadomienia kolekcji wyrzucania elementów, a następnie uruchamia wątku, na `WaitForFullGCProc` metody użytkownika, aby stale monitorować <xref:System.GCNotificationStatus> wyliczenie, który jest zwracany przez <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5483a-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="5483a-146"><xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody wywołania ich odpowiednich metod obsługi zdarzeń w użytkownika, gdy zostanie wywołane przez powiadomienie:</span><span class="sxs-lookup"><span data-stu-id="5483a-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="5483a-147">Ta metoda wywołuje `RedirectRequests` metody użytkownika, która powoduje, że serwer usługi kolejkowania żądanie wstrzymania wysyłania żądań do serwera.</span><span class="sxs-lookup"><span data-stu-id="5483a-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="5483a-148">Jest to symulowane przez ustawienie zmiennej poziomu klasa `bAllocate` do `false` nowych obiektów są przydzielone.</span><span class="sxs-lookup"><span data-stu-id="5483a-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="5483a-149">Następnie `FinishExistingRequests` metoda użytkownika jest wywoływana, aby zakończyć przetwarzanie żądań oczekujących serwera.</span><span class="sxs-lookup"><span data-stu-id="5483a-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="5483a-150">Jest to symulowane przez wyczyszczenie <xref:System.Collections.Generic.List%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5483a-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="5483a-151">Na koniec wyrzucania elementów bezużytecznych jest wywołane, ponieważ obciążenie jest światła.</span><span class="sxs-lookup"><span data-stu-id="5483a-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="5483a-152">Ta metoda wywołuje metodę użytkownika `AcceptRequests` wznowić, akceptując żądania, ponieważ serwer nie jest już się pełne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5483a-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="5483a-153">Ta akcja jest symulowane przez ustawienie `bAllocate` zmienną `true` tak, aby wznowić obiekty dodawane do <xref:System.Collections.Generic.List%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5483a-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="5483a-154">Poniższy kod zawiera `Main` metoda przykładu.</span><span class="sxs-lookup"><span data-stu-id="5483a-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="5483a-155">Poniższy kod zawiera `WaitForFullGCProc` metody użytkownika, zawierającej ciągłej pętli, aby sprawdzić, czy powiadomienia dotyczące odzyskiwania pamięci while.</span><span class="sxs-lookup"><span data-stu-id="5483a-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="5483a-156">Poniższy kod zawiera `OnFullGCApproachNotify` metoda nazywane z</span><span class="sxs-lookup"><span data-stu-id="5483a-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="5483a-157">`WaitForFullGCProc` Metoda.</span><span class="sxs-lookup"><span data-stu-id="5483a-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="5483a-158">Poniższy kod zawiera `OnFullGCApproachComplete` metoda nazywane z</span><span class="sxs-lookup"><span data-stu-id="5483a-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="5483a-159">`WaitForFullGCProc` Metoda.</span><span class="sxs-lookup"><span data-stu-id="5483a-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="5483a-160">Poniższy kod zawiera metody użytkownika, które są wywoływane z `OnFullGCApproachNotify` i `OnFullGCCompleteNotify` metody.</span><span class="sxs-lookup"><span data-stu-id="5483a-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="5483a-161">Metody użytkownika Przekierowywanie żądań, Zakończ istniejącymi żądaniami i wznowienia żądań, po przeprowadzeniu pełnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5483a-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="5483a-162">Przykład całego kodu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="5483a-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5483a-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5483a-163">See also</span></span>

- [<span data-ttu-id="5483a-164">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="5483a-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
