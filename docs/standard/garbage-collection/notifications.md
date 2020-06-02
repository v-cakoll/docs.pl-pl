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
# <a name="garbage-collection-notifications"></a>Powiadomienia dotyczące odzyskiwania pamięci
Istnieją sytuacje, w których pełne odzyskiwanie pamięci (czyli kolekcja generacji 2) przez środowisko uruchomieniowe języka wspólnego może niekorzystnie wpłynąć na wydajność. Może to być problem szczególnie w przypadku serwerów, które przetwarzają duże ilości żądań; w takim przypadku długotrwałe wyrzucanie elementów bezużytecznych może spowodować przekroczenie limitu czasu żądania. Aby zapobiec występowaniu pełnej kolekcji w okresie krytycznym, można powiadomić o tym, że pełne odzyskiwanie pamięci zbliża się, a następnie podejmuje działania w celu przekierowania obciążenia do innego wystąpienia serwera. Istnieje również możliwość wywołania kolekcji samodzielnie, pod warunkiem, że bieżące wystąpienie serwera nie musi przetwarzać żądań.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A>Metoda rejestruje powiadomienie, które zostanie wywołane, gdy środowisko uruchomieniowe wskazuje, że zbliża się pełne odzyskiwanie pamięci. Istnieją dwie części tego powiadomienia: Kiedy pełne odzyskiwanie pamięci zbliża się i gdy pełne odzyskiwanie pamięci zostało zakończone.  
  
> [!WARNING]
> Tylko blokowanie wyrzucania elementów bezużytecznych powiadomień. Gdy [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) element konfiguracji jest włączony, wyrzucanie elementów bezużytecznych w tle nie spowoduje zgłoszenia powiadomień.  
  
 Aby określić, kiedy zostało zgłoszone powiadomienie, użyj <xref:System.GC.WaitForFullGCApproach%2A> metod i <xref:System.GC.WaitForFullGCComplete%2A> . Zwykle te metody są używane w pętli, `while` aby stale uzyskiwać <xref:System.GCNotificationStatus> Wyliczenie, które pokazuje stan powiadomienia. W przypadku tej wartości <xref:System.GCNotificationStatus.Succeeded> można wykonać następujące czynności:  
  
- W odpowiedzi na powiadomienie uzyskane przy użyciu <xref:System.GC.WaitForFullGCApproach%2A> metody można przekierować obciążenie i ewentualnie wywołać kolekcję.  
  
- W odpowiedzi na powiadomienie uzyskane przy użyciu <xref:System.GC.WaitForFullGCComplete%2A> metody można sprawić, aby bieżące wystąpienie serwera było dostępne do ponownego przetwarzania żądań. Możesz również zebrać informacje. Na przykład możesz użyć <xref:System.GC.CollectionCount%2A> metody, aby zarejestrować liczbę kolekcji.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> Metody i są zaprojektowane tak, aby współdziałać. Użycie jednego bez nich może spowodować uzyskanie nieokreślonych wyników.  
  
## <a name="full-garbage-collection"></a>Pełne odzyskiwanie pamięci  
 Środowisko uruchomieniowe powoduje pełne wyrzucanie elementów bezużytecznych, gdy spełnione są dowolne z następujących scenariuszy:  
  
- Dostateczna ilość pamięci została podwyższona do generacji 2 w celu spowodowania nowej kolekcji generacji 2.  
  
- Zbyt mała ilość pamięci została podzielona na stertę dużego obiektu, aby spowodować wystąpienie następnej generacji 2.  
  
- Kolekcja generacji 1 jest eskalacją do kolekcji 2 generacji ze względu na inne czynniki.  
  
 Progi określone w <xref:System.GC.RegisterForFullGCNotification%2A> metodzie stosują się do pierwszych dwóch scenariuszy. Jednak w pierwszym scenariuszu nie zawsze otrzymasz powiadomienie w czasie proporcjonalnym do wartości progowych określonych z dwóch powodów:  
  
- Środowisko uruchomieniowe nie sprawdza poszczególnych alokacji małych obiektów (ze względu na wydajność).  
  
- Tylko kolekcje generacji 1 promują pamięć do generacji 2.  
  
 Trzeci scenariusz przyczynia się również do niepewności, kiedy otrzymasz powiadomienie. Chociaż nie jest to gwarancja, warto zastanowić się, że jest to przydatny sposób na uniknięcie efektów inopportune pełnego odzyskiwania pamięci przez przekierowanie żądań w tym czasie lub wypróbowanie kolekcji, gdy będzie można lepiej obsłużyć.  
  
## <a name="notification-threshold-parameters"></a>Parametry progu powiadomienia  
 <xref:System.GC.RegisterForFullGCNotification%2A>Metoda ma dwa parametry, aby określić wartości progowe obiektów generacji 2 i sterty dużego obiektu. Gdy te wartości są spełnione, powinno zostać zgłoszone powiadomienie o wyrzucaniu elementów bezużytecznych. W poniższej tabeli opisano te parametry.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Liczba z zakresu od 1 do 99 określająca, kiedy powiadomienie powinno zostać zgłoszone na podstawie obiektów podniesionych w generacji 2.|  
|`largeObjectHeapThreshold`|Liczba z zakresu od 1 do 99 określająca, kiedy powiadomienie powinno być zgłaszane na podstawie obiektów, które są przydzielane w stercie dużego obiektu.|  
  
 Jeśli określisz zbyt wysoką wartość, istnieje wysokie prawdopodobieństwo, że otrzymasz powiadomienie, ale może to być zbyt długi czas oczekiwania przed wykonaniem przez środowisko uruchomieniowe kolekcji. Jeśli samodzielnie wywołująsz kolekcję, możesz odwoływać więcej obiektów, niż byłoby to odrzucane, jeśli środowisko uruchomieniowe powoduje wystąpienie tej kolekcji.  
  
 Jeśli określisz zbyt niską wartość, środowisko uruchomieniowe może spowodować, że zbieranie danych będzie wymagało wystarczającej ilości czasu na powiadomienie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie Grupa serwerów obsługuje przychodzące żądania sieci Web. Aby symulować obciążenie żądań przetwarzania, tablice bajtowe są dodawane do <xref:System.Collections.Generic.List%601> kolekcji. Każdy serwer rejestruje do powiadomienia o wyrzucaniu elementów bezużytecznych, a następnie uruchamia wątek w `WaitForFullGCProc` metodzie użytkownika w celu ciągłego monitorowania <xref:System.GCNotificationStatus> wyliczenia zwracanego przez <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metod.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> Metody i zadzwonią odpowiednie metody użytkownika obsługującego zdarzenia, gdy zostanie zgłoszone powiadomienie:  
  
- `OnFullGCApproachNotify`  
  
     Ta metoda wywołuje `RedirectRequests` metodę użytkownika, która instruuje serwer kolejkowania żądań, aby zawiesić wysyłanie żądań do serwera. Jest to symulowane przez ustawienie zmiennej poziomu klasy `bAllocate` na `false` tak, aby nie przydzielono kolejnych obiektów.  
  
     Następnie `FinishExistingRequests` Metoda użytkownika jest wywoływana, aby zakończyć przetwarzanie oczekujących żądań serwera. Jest to symulowane przez wyczyszczenie <xref:System.Collections.Generic.List%601> kolekcji.  
  
     Na koniec wyrzucanie elementów bezużytecznych jest wywołane, ponieważ obciążenie jest jasne.  
  
- `OnFullGCCompleteNotify`  
  
     Ta metoda wywołuje metodę użytkownika `AcceptRequests` w celu wznowienia akceptowania żądań, ponieważ serwer nie jest już podatny na pełne odzyskiwanie pamięci. Ta akcja jest symulowana przez ustawienie `bAllocate` zmiennej na `true` tak, aby obiekty mogły zostać wznowione do <xref:System.Collections.Generic.List%601> kolekcji.  
  
 Poniższy kod zawiera `Main` metodę przykładu.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Poniższy kod zawiera `WaitForFullGCProc` metodę użytkownika, która zawiera ciągłą pętlę while, aby sprawdzić powiadomienia o wyrzucaniu elementów bezużytecznych.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Poniższy kod zawiera `OnFullGCApproachNotify` metodę wywoływaną z  
  
 `WaitForFullGCProc`Method.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Poniższy kod zawiera `OnFullGCApproachComplete` metodę wywoływaną z  
  
 `WaitForFullGCProc`Method.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Poniższy kod zawiera metody użytkownika, które są wywoływane z `OnFullGCApproachNotify` `OnFullGCCompleteNotify` metod i. Metody użytkownika przekierowują żądania, kończyć istniejące żądania, a następnie wznawiają żądania po wystąpieniu pełnego odzyskiwania pamięci.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Cały przykład kodu jest następujący:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Odzyskiwanie pamięci](index.md)
