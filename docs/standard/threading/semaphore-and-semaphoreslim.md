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
ms.openlocfilehash: e7d7f791fbc68a526f428f4f79d9b379a23ca771
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199490"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor i klasa SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType> Klasa reprezentuje nazwane (ogólnosystemowe) lub semafor lokalnego. To cienka otokę wokół obiektu semafora Win32. Semaforów Win32 są liczenie semaforów, które mogą być używane do kontrolowania dostępu do puli zasobów.  
  
 <xref:System.Threading.SemaphoreSlim> Klasa reprezentuje lekkie, szybkie semafor, który może służyć do oczekiwania w ramach jednego procesu, gdy spodziewane czasy oczekiwania będą bardzo krótkie. <xref:System.Threading.SemaphoreSlim> opiera się jak najszerzej w podstawowych synchronizacji dostarczane przez środowisko uruchomieniowe języka wspólnego (CLR). Jednak zapewnia również dojść oczekiwania opóźnieniem zainicjowany, na podstawie jądra co jest niezbędne do obsługi oczekiwanie na wielu semaforów. <xref:System.Threading.SemaphoreSlim> również obsługuje korzystanie z tokenów anulowania, ale nie obsługuje o nazwie semaforów lub użytkowania dojście oczekiwania synchronizacji.  
  
## <a name="managing-a-limited-resource"></a>Zarządzanie zasobem ograniczone  
 Wątki wprowadź semafora przez wywołanie metody <xref:System.Threading.WaitHandle.WaitOne%2A> metody, która jest dziedziczona z <xref:System.Threading.WaitHandle> klasy, w przypadku <xref:System.Threading.Semaphore?displayProperty=nameWithType> obiektu lub <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> lub <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> metody, w przypadku <xref:System.Threading.SemaphoreSlim> obiektu. Po powrocie z wywołania liczba klientów na semafora zostanie zmniejszony. Kiedy wątek żądań zapisu oraz liczbę wynosi zero, blokuje wątek. Co wątków wersji semafora przez wywołanie metody <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> lub <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metody zablokowane wątki mogą wprowadzać. Nie dotyczy zagwarantowana kolejność, takich jak pierwszy in, first-out (FIFO) lub ostatni na wejściu, (LIFO), zablokowane wątki wprowadzić semafora.  
  
 Wątek można wprowadzić semafora wiele razy, wywołując <xref:System.Threading.Semaphore?displayProperty=nameWithType> obiektu <xref:System.Threading.WaitHandle.WaitOne%2A> metody lub <xref:System.Threading.SemaphoreSlim> obiektu <xref:System.Threading.SemaphoreSlim.Wait%2A> metoda wielokrotnie. Aby zwolnić semafora, wątek może wywołać <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> lub <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> metoda przeciążenia taką samą liczbę razy, lub zadzwoń <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> lub <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> metoda przeciążenia i określ liczbę wpisów, które mogą być wprowadzane.  
  
### <a name="semaphores-and-thread-identity"></a>Semaforów i tożsamości wątku  
 Semafor dwóch typów bez wymuszania tożsamość wątku na wywołania <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>, i <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metody. Na przykład typowym scenariuszem użycia na semaforów zawiera wątku producentów i konsumentów wątku, z jednego wątku zawsze zwiększenie liczby semafor, a drugi zawsze zmniejszanie go.  
  
 Jest odpowiedzialny za programisty, aby upewnić się, że wątek nie spowoduje zwolnienia semafora zbyt wiele razy. Na przykład załóżmy, że semafor ma maksymalną liczbę dwóch tego wątku, A i B wątku obydwa wprowadź semafora. Jeśli to błąd programistyczny w wątku B powoduje go do wywoływania `Release` dwa razy, oba wywołania powiodło się. Liczba klientów na semafora jest zapełniony i kiedy wątek, A ostatecznie wywołuje `Release`, <xref:System.Threading.SemaphoreFullException> zgłaszany.  
  
## <a name="named-semaphores"></a>Nazwane semaforów  
 System operacyjny Windows umożliwia semaforów mieć nazwy. Semafor nazwanych jest całego systemu. Oznacza to po utworzeniu nazwane semafora jest widoczny dla wszystkich wątków we wszystkich procesów. W związku z tym o nazwie semafora może służyć do Synchronizuj działania procesów, a także wątków.  
  
 Możesz utworzyć <xref:System.Threading.Semaphore> obiekt, który przedstawia semafor systemu o nazwie przy użyciu jednego z konstruktorów, które określa nazwę.  
  
> [!NOTE]
>  Ponieważ nazwany semaforów całego systemu, istnieje możliwość wielu <xref:System.Threading.Semaphore> obiekty reprezentujące takie same, o nazwie semafora. Każdorazowo, można wywołać konstruktora lub <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> metodę, nowe <xref:System.Threading.Semaphore> obiekt zostanie utworzony. Określenie tej samej nazwie wielokrotnie tworzy wiele obiektów, które reprezentują ten sam semafora o nazwie.  
  
 Możesz użyć nazwanych semaforów, należy zachować ostrożność. Ponieważ są one całego systemu, inny proces, który używa tej samej nazwy można wprowadzić swoje semafora nieoczekiwanie. Złośliwy kod, wykonania na tym samym komputerze może wykorzystać tę podstawę ataku typu "odmowa usługi".  
  
 Umożliwia kontrolę dostępu, aby chronić <xref:System.Threading.Semaphore> obiekt, który najlepiej reprezentuje nazwane semafor, za pomocą konstruktora, który określa <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> obiektu. Można również stosować przy użyciu zabezpieczeń kontroli dostępu <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> metody, ale pozostawia oknem lukę między czas semafora jest tworzony i jest chroniony. Ochrona semaforów za pomocą kontrolę dostępu pomaga zapobiegać złośliwe ataki, ale nie rozwiązuje problemu Kolizje nazw niezamierzone.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Semaphore>  
- <xref:System.Threading.SemaphoreSlim>  
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
