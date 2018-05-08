---
title: Semafor i klasa SemaphoreSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- counting semaphores
- semaphores
- threading [.NET Framework], cross-process synchronization
- Semaphore class, about Semaphore class
- SemaphoreSlim class, about SemaphoreSlim class
- threading [.NET Framework], Semaphore class
ms.assetid: 7722a333-b974-47a2-a7c0-f09097fb644e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f9c6df23ae1a142d208672a03ffeb74709a0a05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor i klasa SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType> Klasa reprezentuje nazwanych (ogólnosystemowe) lub semafora lokalnego. Jest cienką otoką wokół obiektu semafora Win32. Semaforów Win32 są liczenie semaforów, które mogą być używane do kontrolowania dostępu do puli zasobów.  
  
 <xref:System.Threading.SemaphoreSlim> Klasa reprezentuje semafora niewielka, szybkie, który może służyć do oczekujących w ramach jednego procesu, gdy powinny być bardzo krótki czas oczekiwania. <xref:System.Threading.SemaphoreSlim> opiera się możliwie często na elementy podstawowe synchronizacji udostępniane przez środowisko uruchomieniowe języka wspólnego (CLR). Jednak także uchwyty oczekiwania opóźnieniem zainicjowane, na podstawie jądra niezbędnych do obsługi oczekiwanie na wielu semaforów. <xref:System.Threading.SemaphoreSlim> również obsługuje używanie anulowanie tokenów, ale nie obsługuje nazwane semaforów lub użycie dojście oczekiwania synchronizacji.  
  
## <a name="managing-a-limited-resource"></a>Zarządzanie zasobem ograniczone  
 Wątki wprowadź semafora przez wywołanie metody <xref:System.Threading.WaitHandle.WaitOne%2A> metodę, która jest dziedziczona z <xref:System.Threading.WaitHandle> klasy, w przypadku <xref:System.Threading.Semaphore?displayProperty=nameWithType> obiektu, lub <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> lub <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> metody, w przypadku <xref:System.Threading.SemaphoreSlim> obiektu... Po powrocie z wywołania licznik na semafora zostanie zmniejszona. Gdy wątek żąda wpis oraz liczbę wynosi zero, bloki wątku. Jak wątków wersji semafora przez wywołanie metody <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> lub <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metody zablokowanych wątków mogą wprowadzać. Brak nie gwarantuje kolejność, takich jak pierwszy, FIFO (FIFO) lub ostatni na, wytworzenia, dla zablokowanych wątków na wejście do semafora.  
  
 Wątek można wprowadzić semafora wielokrotnie przez wywołanie metody <xref:System.Threading.Semaphore?displayProperty=nameWithType> obiektu <xref:System.Threading.WaitHandle.WaitOne%2A> metody lub <xref:System.Threading.SemaphoreSlim> obiektu <xref:System.Threading.SemaphoreSlim.Wait%2A> metody wielokrotnie. Aby zwolnić semafora, Wątek można albo wywołanie <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> lub <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> metoda przeciążenia taką samą liczbę razy, lub zadzwoń <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> lub <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> metoda przeciążenia i określ liczbę wpisów do zwolnienia.  
  
### <a name="semaphores-and-thread-identity"></a>Semaforów i tożsamości wątku  
 Typy dwóch semafora nie Wymuszaj tożsamość wątku na wywołania <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>, i <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metody. Na przykład typowy scenariusz użycia dla semaforów obejmuje wątku producentów i konsumentów wątków, z jednego wątku zawsze zwiększanie Licznik semafora, a drugi zawsze zmniejszanie go.  
  
 Odpowiada programisty upewnij się, że wątek nie zwalnia semafora zbyt wiele razy. Na przykład załóżmy, że maksymalna liczba dwóch i który wątku A i B wątku ma semafora zarówno wprowadź semafora. Jeśli to błąd programistyczny w wątku B powoduje go do wywołania `Release` dwa razy, zarówno wywołania powiodło się. Licznik na semafora jest pełny i gdy wątku A ostatecznie wywołuje `Release`, <xref:System.Threading.SemaphoreFullException> jest generowany.  
  
## <a name="named-semaphores"></a>Nazwane semaforów  
 System operacyjny Windows umożliwia semaforów mieć nazwy. Semafor o nazwie jest całym systemie. Oznacza to, że po utworzeniu semafor o nazwie jest widoczne dla wszystkich wątków w wszystkich procesów. W związku z tym semafor o nazwie może służyć do synchronizowania działania procesów, a także wątków.  
  
 Można utworzyć <xref:System.Threading.Semaphore> obiekt, który reprezentuje semafor o nazwie systemu za pomocą jednego z konstruktorów, które określa nazwę.  
  
> [!NOTE]
>  Ponieważ nazwanego semaforów całym systemie, istnieje możliwość wielu <xref:System.Threading.Semaphore> semafor o nazwie obiekty reprezentujące takie same. Zawsze należy wywołać konstruktora lub <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> metoda, nowy <xref:System.Threading.Semaphore> tworzony jest obiekt. Określenie tej samej nazwie wielokrotnie tworzy wiele obiektów, które reprezentują tego samego semafor o nazwie.  
  
 Użyj semaforów nazwanego, należy zachować ostrożność. Ponieważ są one całym systemie, inny proces, który używa tej samej nazwie można wprowadzić Twojej semafora nieoczekiwanie. Złośliwy kod na tym samym komputerze może wykorzystać tę podstawę ataku typu "odmowa usługi".  
  
 Umożliwia kontrolę dostępu, aby chronić <xref:System.Threading.Semaphore> obiekt, który reprezentuje semafora nazwanego, najlepiej przy użyciu konstruktora, który określa <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> obiektu. Można także zastosować dla zabezpieczeń kontroli dostępu przy użyciu opcji <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> metody, ale pozostawia okno luki w zabezpieczeniach między semafora została utworzona, a czas jest chroniony. Ochrona semaforów za pomocą kontrolę dostępu pomaga zapobiegać złośliwe ataki, ale nie rozwiązuje problemu konflikty nazw przypadkowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Semaphore>  
 <xref:System.Threading.SemaphoreSlim>  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
