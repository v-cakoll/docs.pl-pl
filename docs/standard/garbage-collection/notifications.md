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
# <a name="garbage-collection-notifications"></a>Powiadomienia dotyczące odzyskiwania pamięci
Istnieją sytuacje, w których pełnego wyrzucania elementów bezużytecznych (czyli kolekcji generacji 2) przez środowisko uruchomieniowe języka wspólnego może niekorzystnie wpłynąć na wydajność. Może to być problem szczególnie z serwerów, które przetwarzają dużą liczbę żądań; w takim przypadku długich wyrzucania elementów bezużytecznych może spowodować limit czasu żądania. Aby zapobiec pełną kolekcję wystąpienia krytyczny okres, użytkownik może zostać powiadomiony czy pełnego wyrzucania elementów bezużytecznych zbliża się do, a następnie podjęcia działania, aby przekierować obciążenia do innego wystąpienia serwera. Użytkownik może także wywołać kolekcji samodzielnie, pod warunkiem, że bieżące wystąpienie serwera nie jest konieczne przetwarzanie żądań.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda rejestruje powiadomienia do wywołania, gdy środowisko uruchomieniowe wykrywa, że zbliża się do pełnego wyrzucania elementów bezużytecznych. To powiadomienie, składa się z dwóch części: gdy zbliża się do pełnego wyrzucania elementów bezużytecznych i po zakończeniu pełnego wyrzucania elementów bezużytecznych.  
  
> [!WARNING]
>  Kolekcje garbage blokujące tylko wywoływanie powiadomień o. Gdy [ \<gcconcurrent — >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) element konfiguracji jest włączona, wyrzucania tła nie będą powodowały powiadomienia.  
  
 Aby określić, kiedy powiadomienie zostanie podniesiony, użyj <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody. Zazwyczaj korzystają z tych metod w `while` pętli stale uzyskanie <xref:System.GCNotificationStatus> wyliczenia, który zawiera stan powiadomienia. Jeśli ta wartość jest <xref:System.GCNotificationStatus.Succeeded>, można wykonaj następujące czynności:  
  
-   W odpowiedzi na powiadomienie uzyskany z <xref:System.GC.WaitForFullGCApproach%2A> metody, można przekierować obciążenia i kolekcji prawdopodobnie wywoływać, samodzielnie.  
  
-   W odpowiedzi na powiadomienie uzyskany z <xref:System.GC.WaitForFullGCComplete%2A> metody, możesz wprowadzić bieżące wystąpienie serwera dostępnych do przetwarzania żądań ponownie. Można także gromadzić informacje. Na przykład można użyć <xref:System.GC.CollectionCount%2A> metody do rejestrowania wielu kolekcji.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody zostały zaprojektowane do siebie. Przy użyciu jednej bez innych może dać wyniki nieokreślony.  
  
## <a name="full-garbage-collection"></a>Pełnego wyrzucania elementów bezużytecznych  
 Środowisko uruchomieniowe powoduje, że pełnego wyrzucania elementów bezużytecznych po spełnieniu jednego z następujących scenariuszy:  
  
-   Za mało pamięci został podniesiony do generacji 2, aby spowodować kolekcji następnej generacji 2.  
  
-   Za mało pamięci został podniesiony do sterty dużego obiektu spowodować kolekcji następnej generacji 2.  
  
-   Kolekcja generacji 1 jest przekazany do kolekcji generacji 2 z powodu innych czynników.  
  
 Progi w <xref:System.GC.RegisterForFullGCNotification%2A> metoda stosowana w przypadku dwóch pierwszych scenariuszy. Jednak w scenariuszu pierwszy nie zawsze otrzymasz powiadomienie w momencie proporcjonalny do wartości progowe, które określisz dwóch powodów:  
  
-   Środowisko uruchomieniowe nie sprawdza każdej alokacji małego obiektu (ze względu na wydajność).  
  
-   Tylko generacji 1 kolekcje podwyższania pamięci w generacji 2.  
  
 Trzeci scenariusz przyczynia się również do niedokładność gdy otrzymasz powiadomienie. Mimo że nie ma gwarancji, okazać się przydatne sposobem łagodzenia skutków nieodpowiednim pełnego wyrzucania elementów bezużytecznych przez przekierowywanie żądań w tym czasie lub wywołania kolekcji samodzielnie, gdy są spełnione lepiej.  
  
## <a name="notification-threshold-parameters"></a>Parametry próg powiadomienia  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda ma dwa parametry, aby określić wartości progowe obiektów pokolenia 2 oraz sterty dużego obiektu. Po spełnieniu tych wartości, powinien być wywoływany powiadomienie kolekcji pamięci. W poniższej tabeli opisano te parametry.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Liczbą z zakresu od 1 do 99 określająca, kiedy powiadomienie zostanie zgłoszony oparte na obiektach awansowane w generacji 2.|  
|`largeObjectHeapThreshold`|Liczbą z zakresu od 1 do 99 określająca, kiedy powiadomienie zostanie zgłoszony oparte na obiekty, które są przydzielane w sterty dużego obiektu.|  
  
 Jeśli określono wartość, która jest zbyt wysoka, istnieje wysokie prawdopodobieństwo, otrzymasz powiadomienie, że może być zbyt długiego okresu oczekiwania dla środowiska uruchomieniowego powoduje, że kolekcja. Jeśli należy wywołać kolekcji samodzielnie, może odzyskać więcej obiektów, nie będzie można odzyskać, jeśli środowisko uruchomieniowe powoduje kolekcji.  
  
 Jeśli określono wartość, która ma zbyt niską wartość, środowisko uruchomieniowe może spowodować kolekcji przed miały wystarczająco dużo czasu, aby otrzymywać powiadomienia.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie grupy serwerów usługi przychodzących żądań sieci Web. Aby symulować obciążenie przetwarzania żądań, tablice typu byte są dodawane do <xref:System.Collections.Generic.List%601> kolekcji. Każdy serwer rejestruje powiadomienia kolekcji pamięci, a następnie uruchamia wątek na `WaitForFullGCProc` metoda użytkownika do ciągłego monitorowania <xref:System.GCNotificationStatus> wyliczenia, który jest zwracany przez <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody wywołania ich odpowiednich metod użytkownika obsługi zdarzeń, gdy jest wywoływane powiadomienie:  
  
-   `OnFullGCApproachNotify`  
  
     Ta metoda wywołuje `RedirectRequests` metoda użytkownika, który powoduje, że serwer usługi kolejkowania wiadomości żądania wstrzymania wysyłania żądań do serwera. Jest to symulowane przez ustawienie zmiennej poziomie klasy `bAllocate` do `false` tak, aby nie więcej obiektów są przydzielone.  
  
     Następnie `FinishExistingRequests` użytkownika metoda jest wywoływana na zakończenie przetwarzania żądań oczekujących serwera. Jest to symulowane przez wyczyszczenie <xref:System.Collections.Generic.List%601> kolekcji.  
  
     Na koniec wyrzucania elementów bezużytecznych jest wywołane, ponieważ obciążenie jest lekki.  
  
-   `OnFullGCCompleteNotify`  
  
     Ta metoda wywołuje metodę użytkownika `AcceptRequests` wznowienia, akceptując żądania, ponieważ serwer nie jest już podatne na pełnego wyrzucania elementów bezużytecznych. Ta akcja jest symulowane przez ustawienie `bAllocate` zmienną `true` tak, aby wznowić obiekty dodawane do <xref:System.Collections.Generic.List%601> kolekcji.  
  
 Poniższy kod zawiera `Main` metody przykładu.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Poniższy kod zawiera `WaitForFullGCProc` metoda użytkownika, zawierający ciągły podczas pętli, aby wyszukać powiadomienia dotyczące odzyskiwania pamięci.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Poniższy kod zawiera `OnFullGCApproachNotify` metoda wywoływana z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Poniższy kod zawiera `OnFullGCApproachComplete` metoda wywoływana z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Poniższy kod zawiera metody użytkownika, które są wywoływane z `OnFullGCApproachNotify` i `OnFullGCCompleteNotify` metody. Metody użytkownika przekierować żądania, Zakończ istniejących żądań i wznowienia żądań, po zakończeniu pełnego wyrzucania elementów bezużytecznych.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Cały kod przykładowy wygląda następująco:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
