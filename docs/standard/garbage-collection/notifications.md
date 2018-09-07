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
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084952"
---
# <a name="garbage-collection-notifications"></a>Powiadomienia dotyczące odzyskiwania pamięci
Istnieją sytuacje, w których pełne wyrzucanie elementów bezużytecznych (czyli kolekcji generacji 2) przez środowisko uruchomieniowe języka wspólnego może niekorzystnie wpłynąć na wydajność. Może to być problem szczególnie z serwerów, które przetwarzają duże ilości żądań; w tym przypadku długo wyrzucania elementów bezużytecznych może powodować limit czasu żądania. Aby zapobiec pełnego występowaniu krytyczny okres, możesz otrzymać, pełne odśmiecanie zbliża się do, a następnie podjęcia działania, aby przekierować obciążenie do innego wystąpienia serwera. Można również wywołać kolekcję użytkownika, pod warunkiem, że bieżące wystąpienie serwera nie jest konieczne przetwarzanie żądań.  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda rejestruje powiadomienie, aby być wywoływane, gdy środowisko uruchomieniowe wykrywa, że zbliża się pełne wyrzucanie elementów bezużytecznych. To powiadomienie, składa się z dwóch części: kiedy zbliża się pełne wyrzucanie elementów bezużytecznych i kiedy zakończyło się pełne wyrzucanie elementów bezużytecznych.  
  
> [!WARNING]
>  Tylko blokowania wyrzucania elementów bezużytecznych wywoływanie powiadomień. Gdy [ \<gcconcurrent — >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) element konfiguracji jest włączona, tle wyrzucania elementów bezużytecznych nie zgłosi powiadomienia.  
  
 Aby określić, gdy zgłoszono powiadomienie, należy użyć <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody. Zazwyczaj można użyć tych metod w `while` pętli stale uzyskać <xref:System.GCNotificationStatus> wyliczenie, który pokazuje stan powiadomienia. Jeśli ta wartość jest <xref:System.GCNotificationStatus.Succeeded>, wykonasz następujące czynności:  
  
-   W odpowiedzi na powiadomienia otrzymane z <xref:System.GC.WaitForFullGCApproach%2A> metody, można przekierować obciążenia, a kolekcja prawdopodobnie occurs, samodzielnie.  
  
-   W odpowiedzi na powiadomienia otrzymane z <xref:System.GC.WaitForFullGCComplete%2A> metody, aby włączyć bieżące wystąpienie serwera dostępne do przetwarzania żądań ponownie. Można także gromadzić informacje. Na przykład, można użyć <xref:System.GC.CollectionCount%2A> metody do rejestrowania wielu kolekcji.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody są zaprojektowane do wspólnej pracy. Przy użyciu jednej bez innych może wygenerować wyniki nieokreślony.  
  
## <a name="full-garbage-collection"></a>Pełne wyrzucanie elementów bezużytecznych  
 Środowisko uruchomieniowe powoduje pełne odśmiecanie, w przypadku spełnienia dowolnego z następujących scenariuszy:  
  
-   Za mało pamięci został podniesiony do generacji 2, aby spowodować, że następny kolekcji generacji 2.  
  
-   Za mało pamięci został podniesiony do sterty dużych obiektów, aby spowodować, że następny kolekcji generacji 2.  
  
-   Kolekcja elementów w generacji 1 jest przekazany do kolekcji generacji 2 z powodu innych czynników.  
  
 Progi w <xref:System.GC.RegisterForFullGCNotification%2A> metoda stosowana w pierwszych dwóch scenariuszy. Jednak w pierwszym scenariuszu możesz nie zawsze będzie otrzymywać powiadomienia w czasie proporcjonalna do wartości progowe, które określisz dwóch powodów:  
  
-   Środowisko wykonawcze nie sprawdza każdą alokację obiektu mały (ze względu na wydajność).  
  
-   Tylko generacji 1 kolekcji przyczyniają się do pamięci w generacji 2.  
  
 Trzeci scenariusz przyczynia się również do niedokładność po użytkownik otrzyma powiadomienie. Mimo że nie ma gwarancji, to okazać się przydatny sposób łagodzenia skutków nieodpowiednim pełne wyrzucanie elementów bezużytecznych przez przekierowywanie żądań, w tym czasie lub wykonuje kolekcję samodzielnie, gdy są spełnione lepiej.  
  
## <a name="notification-threshold-parameters"></a>Parametry próg powiadomienia  
 <xref:System.GC.RegisterForFullGCNotification%2A> Metoda ma dwa parametry, aby określić wartości progowe obiekty generacji 2 i stos dużych obiektów. Gdy te wartości są spełnione, powinien być wywoływany powiadomienia wyrzucania elementów kolekcji. W poniższej tabeli opisano te parametry.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Liczbą z zakresu od 1 do 99 określający, kiedy powinien być wywoływany powiadomienia na podstawie obiektów promowany w generacji 2.|  
|`largeObjectHeapThreshold`|Liczbą z zakresu od 1 do 99 określający, kiedy powinien być wywoływany powiadomienia na podstawie obiektów, które są przydzielane w stosie dużego obiektu.|  
  
 Jeśli określono wartość, która jest zbyt duża, istnieje wysokie prawdopodobieństwo, otrzymasz powiadomienie, że może to być zbyt długiego okresu oczekiwania dla środowiska uruchomieniowego powoduje, że kolekcja. Jeśli occurs kolekcji, samodzielnie, mogą odzyskać więcej obiektów, nie będzie można odzyskać, jeśli środowisko wykonawcze powoduje, że kolekcja.  
  
 Jeśli określono wartość, która ma zbyt niską wartość, środowisko uruchomieniowe może spowodować kolekcji przed miały wystarczająco dużo czasu, aby otrzymywać powiadomienia.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie grupa serwerów usługi przychodzących żądań sieci Web. Aby zasymulować obciążenie przetwarzania żądań, tablice bajtowe są dodawane do <xref:System.Collections.Generic.List%601> kolekcji. Każdy serwer rejestruje powiadomienia kolekcji wyrzucania elementów, a następnie uruchamia wątku, na `WaitForFullGCProc` metody użytkownika, aby stale monitorować <xref:System.GCNotificationStatus> wyliczenie, który jest zwracany przez <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody.  
  
 <xref:System.GC.WaitForFullGCApproach%2A> i <xref:System.GC.WaitForFullGCComplete%2A> metody wywołania ich odpowiednich metod obsługi zdarzeń w użytkownika, gdy zostanie wywołane przez powiadomienie:  
  
-   `OnFullGCApproachNotify`  
  
     Ta metoda wywołuje `RedirectRequests` metody użytkownika, która powoduje, że serwer usługi kolejkowania żądanie wstrzymania wysyłania żądań do serwera. Jest to symulowane przez ustawienie zmiennej poziomu klasa `bAllocate` do `false` nowych obiektów są przydzielone.  
  
     Następnie `FinishExistingRequests` metoda użytkownika jest wywoływana, aby zakończyć przetwarzanie żądań oczekujących serwera. Jest to symulowane przez wyczyszczenie <xref:System.Collections.Generic.List%601> kolekcji.  
  
     Na koniec wyrzucania elementów bezużytecznych jest wywołane, ponieważ obciążenie jest światła.  
  
-   `OnFullGCCompleteNotify`  
  
     Ta metoda wywołuje metodę użytkownika `AcceptRequests` wznowić, akceptując żądania, ponieważ serwer nie jest już się pełne wyrzucanie elementów bezużytecznych. Ta akcja jest symulowane przez ustawienie `bAllocate` zmienną `true` tak, aby wznowić obiekty dodawane do <xref:System.Collections.Generic.List%601> kolekcji.  
  
 Poniższy kod zawiera `Main` metoda przykładu.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Poniższy kod zawiera `WaitForFullGCProc` metody użytkownika, zawierającej ciągłej pętli, aby sprawdzić, czy powiadomienia dotyczące odzyskiwania pamięci while.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Poniższy kod zawiera `OnFullGCApproachNotify` metoda nazywane z  
  
 `WaitForFullGCProc` Metoda.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Poniższy kod zawiera `OnFullGCApproachComplete` metoda nazywane z  
  
 `WaitForFullGCProc` Metoda.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Poniższy kod zawiera metody użytkownika, które są wywoływane z `OnFullGCApproachNotify` i `OnFullGCCompleteNotify` metody. Metody użytkownika Przekierowywanie żądań, Zakończ istniejącymi żądaniami i wznowienia żądań, po przeprowadzeniu pełnego wyrzucania elementów bezużytecznych.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Przykład całego kodu jest następująca:  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
