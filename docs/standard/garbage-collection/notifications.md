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
# <a name="garbage-collection-notifications"></a>Powiadomienia dotyczące odzyskiwania pamięci
Istnieją sytuacje, w których pełne wyrzucania elementów bezużytecznych (czyli kolekcji generacji 2) przez kod uruchomieniowy języka wspólnego może niekorzystnie wpłynąć na wydajność. Może to być problem szczególnie z serwerami, które przetwarzają duże ilości żądań; w takim przypadku długi wyrzucania elementów bezużytecznych może spowodować uchybienie żądania. Aby zapobiec wystąpieniu pełnej kolekcji w krytycznym okresie, można powiadomić, że zbliża się pełne wyrzucanie elementów bezużytecznych, a następnie podjąć działania, aby przekierować obciążenie do innego wystąpienia serwera. Można również wywołać kolekcji samodzielnie, pod warunkiem, że bieżące wystąpienie serwera nie trzeba przetwarzać żądania.  
  
 Metoda <xref:System.GC.RegisterForFullGCNotification%2A> rejestruje powiadomienie, które mają być wywoływane, gdy czas wykonywania wyczuwa, że zbliża się pełne wyrzucanie elementów bezużytecznych. Istnieją dwie części tego powiadomienia: gdy zbliża się pełna wyrzucania elementów bezużytecznych i po zakończeniu pełnego wyrzucania elementów bezużytecznych.  
  
> [!WARNING]
> Tylko blokowanie wyrzucania elementów bezużytecznych zgłaszapowiadomienia. Po włączeniu elementu konfiguracji [ \<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) wyrzucanie elementów bezużytecznych w tle nie będzie zgłaszać powiadomień.  
  
 Aby określić, kiedy powiadomienie zostało <xref:System.GC.WaitForFullGCApproach%2A> zgłoszone, należy użyć i <xref:System.GC.WaitForFullGCComplete%2A> metody. Zazwyczaj używasz tych metod w `while` pętli, aby stale <xref:System.GCNotificationStatus> uzyskiwać wyliczenie, które pokazuje stan powiadomienia. Jeśli ta <xref:System.GCNotificationStatus.Succeeded>wartość jest , można wykonać następujące czynności:  
  
- W odpowiedzi na powiadomienie <xref:System.GC.WaitForFullGCApproach%2A> uzyskane za pomocą metody można przekierować obciążenia i ewentualnie wywołać kolekcji samodzielnie.  
  
- W odpowiedzi na powiadomienie <xref:System.GC.WaitForFullGCComplete%2A> uzyskane za pomocą metody można udostępnić bieżące wystąpienie serwera do ponownego przetworzenia żądań. Można również zbierać informacje. Na przykład można użyć <xref:System.GC.CollectionCount%2A> metody do rejestrowania liczby kolekcji.  
  
 Metody <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> są przeznaczone do współpracy. Za pomocą jednego bez drugiego może produkować nieokreślone wyniki.  
  
## <a name="full-garbage-collection"></a>Pełne wyrzucanie elementów bezużytecznych  
 Środowiska uruchomieniowego powoduje pełne wyrzucanie elementów bezużytecznych, gdy którykolwiek z następujących scenariuszy są prawdziwe:  
  
- Wystarczająca ilość pamięci została wyawansona do generacji 2, aby spowodować kolekcję następnej generacji 2.  
  
- Wystarczająca ilość pamięci została wyawansona do sterty dużych obiektów, aby spowodować nowej generacji 2 kolekcji.  
  
- Kolekcja generacji 1 jest eskalowana do kolekcji generacji 2 ze względu na inne czynniki.  
  
 Progi określone w <xref:System.GC.RegisterForFullGCNotification%2A> metodzie dotyczą dwóch pierwszych scenariuszy. Jednak w pierwszym scenariuszu nie zawsze otrzymasz powiadomienie w czasie proporcjonalnym do wartości progowych, które określisz z dwóch powodów:  
  
- Czas wykonywania nie sprawdza każdej alokacji małych obiektów (ze względu na wydajność).  
  
- Tylko kolekcje 1 generacji promują pamięć w generacji 2.  
  
 Trzeci scenariusz przyczynia się również do niepewności co do tego, kiedy otrzymasz powiadomienie. Mimo że nie jest to gwarancja, okaże się być przydatnym sposobem złagodzenia skutków nieodpowiedniego pełnego wyrzucania elementów bezużytecznych, przekierowując żądania w tym czasie lub wywołując kolekcję samodzielnie, gdy może być lepiej zakwaterowana.  
  
## <a name="notification-threshold-parameters"></a>Parametry progu powiadomień  
 Metoda <xref:System.GC.RegisterForFullGCNotification%2A> ma dwa parametry, aby określić wartości progowe obiektów generacji 2 i sterty dużych obiektów. Po spełnieniu tych wartości należy zgłaszać powiadomienie o wyrzucaniu elementów bezużytecznych. W poniższej tabeli opisano te parametry.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Liczba z lat 1-99 określająca, kiedy powiadomienie powinno być wywoływane na podstawie obiektów promowanych w generacji 2.|  
|`largeObjectHeapThreshold`|Liczba z lat 1-99 określająca, kiedy powiadomienie powinno być wywoływane na podstawie obiektów przydzielonych w stercie dużego obiektu.|  
  
 Jeśli określisz wartość, która jest zbyt wysoka, istnieje duże prawdopodobieństwo, że otrzymasz powiadomienie, ale może to być zbyt długi okres oczekiwania, zanim środowiska uruchomieniowego powoduje kolekcję. Jeśli wywołasz kolekcji samodzielnie, można odzyskać więcej obiektów niż zostanie odzyskane, jeśli środowiska uruchomieniowego powoduje kolekcji.  
  
 Jeśli określisz wartość, która jest zbyt niska, czas wykonywania może spowodować kolekcji, zanim masz wystarczająco dużo czasu, aby otrzymywać powiadomienia.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie grupa serwerów usługi przychodzących żądań sieci Web. Aby symulować obciążenie przetwarzania żądań, tablice <xref:System.Collections.Generic.List%601> bajtów są dodawane do kolekcji. Każdy serwer rejestruje się dla powiadomienia wyrzucania elementów `WaitForFullGCProc` bezużytecznych, a <xref:System.GCNotificationStatus> następnie uruchamia wątek na metodę <xref:System.GC.WaitForFullGCApproach%2A> użytkownika, aby stale monitorować wyliczenie, które jest zwracane przez i <xref:System.GC.WaitForFullGCComplete%2A> metody.  
  
 Metody <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> wywołać ich odpowiednich metod obsługi zdarzeń użytkownika, gdy powiadomienie jest wywoływane:  
  
- `OnFullGCApproachNotify`  
  
     Ta metoda `RedirectRequests` wywołuje metodę użytkownika, która nakazuje serwerowi kolejki żądań zawieszenie wysyłania żądań do serwera. Jest to symulowane przez ustawienie `bAllocate` zmiennej na poziomie klasy tak, aby `false` nie więcej obiektów są przydzielane.  
  
     Następnie metoda `FinishExistingRequests` użytkownika jest wywoływana, aby zakończyć przetwarzanie oczekujących żądań serwera. Jest to symulowane <xref:System.Collections.Generic.List%601> przez wyczyszczenie kolekcji.  
  
     Na koniec wyrzucanie elementów bezużytecznych jest indukowany, ponieważ obciążenie jest lekkie.  
  
- `OnFullGCCompleteNotify`  
  
     Ta metoda wywołuje `AcceptRequests` metodę użytkownika, aby wznowić akceptowanie żądań, ponieważ serwer nie jest już podatny na pełne wyrzucanie elementów bezużytecznych. Ta akcja jest symulowana `bAllocate` przez `true` ustawienie zmiennej tak, <xref:System.Collections.Generic.List%601> aby obiekty mogły zostać wznowione dodawane do kolekcji.  
  
 Poniższy kod zawiera `Main` metodę przykładu.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Poniższy kod zawiera `WaitForFullGCProc` metodę użytkownika, który zawiera ciągłe while pętli, aby sprawdzić, czy powiadomienia wyrzucania elementów bezużytecznych.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Poniższy kod zawiera `OnFullGCApproachNotify` metodę wywoływana z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Poniższy kod zawiera `OnFullGCApproachComplete` metodę wywoływana z  
  
 `WaitForFullGCProc`Metoda.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Poniższy kod zawiera metody użytkownika, które `OnFullGCApproachNotify` są `OnFullGCCompleteNotify` wywoływane z i metody. Metody użytkownika przekierowują żądania, kończą istniejące żądania, a następnie wznawiają żądania po wystąpieniu pełnego wyrzucania elementów bezużytecznych.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Cały przykład kodu jest następujący:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
