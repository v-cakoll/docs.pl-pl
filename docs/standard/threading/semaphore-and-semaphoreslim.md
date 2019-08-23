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
ms.openlocfilehash: 25121ea2b089df49efa77dcf363e2a0e400b3bff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968424"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor i klasa SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType> Klasa reprezentuje nazwę (systemowo) lub semafor lokalny. Jest to cienka otoka otaczająca obiekt semafora Win32. Semafory Win32 to zliczanie semaforów, które mogą służyć do kontrolowania dostępu do puli zasobów.  
  
 <xref:System.Threading.SemaphoreSlim> Klasa reprezentuje lekki, szybki semafor, który może być używany do oczekiwania w pojedynczym procesie, gdy oczekiwane czasy oczekiwania są bardzo krótkie. <xref:System.Threading.SemaphoreSlim>jest tak dużo jak to możliwe w przypadku prymitywów synchronizacji dostarczonych przez środowisko uruchomieniowe języka wspólnego (CLR). Zapewnia on jednak również opóźnieniem zainicjowane, zależne od jądra uchwyty do obsługi oczekiwania na wiele semaforów. <xref:System.Threading.SemaphoreSlim>Program obsługuje także tokeny anulowania, ale nie obsługuje semaforów nazwanych ani użycia uchwytu oczekiwania na potrzeby synchronizacji.  
  
## <a name="managing-a-limited-resource"></a>Zarządzanie zasobem ograniczonym  
 Wątki <xref:System.Threading.WaitHandle.WaitOne%2A> wprowadzają semafor, wywołując metodę, która jest dziedziczona <xref:System.Threading.WaitHandle> z klasy, <xref:System.Threading.Semaphore?displayProperty=nameWithType> w przypadku obiektu, lub <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> metody, w przypadku <xref:System.Threading.SemaphoreSlim> obiektu. Gdy wywołanie zwróci wartość, licznik semafora jest zmniejszany. Gdy wątek żąda wpisu, a liczba jest równa zero, bloki wątku. Ponieważ wątki zwalniają semafor przez wywołanie <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> metody lub <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> , blokowane wątki mogą wprowadzić. Brak uporządkowanej kolejności, takiej jak First-In, First-Out (FIFO) lub Last-in, First-Out (LIFO), w przypadku zablokowanych wątków do wprowadzania semafora.  
  
 Wątek może wielokrotnie <xref:System.Threading.Semaphore?displayProperty=nameWithType> wprowadzać semafor, wywołując <xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.SemaphoreSlim.Wait%2A> metodę obiektu lub <xref:System.Threading.SemaphoreSlim> metodę obiektu wielokrotnie. Aby zwolnić semafor <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> , wątek może wywoływać lub przeciążać <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> metodę lub wywoływać metodę przeciążoną, a także <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> określić liczbę wpisów do zwolnienia.  
  
### <a name="semaphores-and-thread-identity"></a>Semafory i tożsamość wątku  
 Dwa typy semaforów <xref:System.Threading.WaitHandle.WaitOne%2A>nie wymuszają tożsamości wątku dla wywołań metod, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>i <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> . Na przykład typowy scenariusz użycia dla semaforów obejmuje wątek producenta i wątek odbiorcy, przy czym jeden wątek zawsze zwiększa liczbę semaforów, a druga zawsze zmniejsza.  
  
 Programista może zapewnić, że wątek nie zwolni semafora zbyt wiele razy. Załóżmy na przykład, że semafor ma maksymalną liczbę dwóch, a wątek a i wątek B jednocześnie wprowadźe semafor. Jeśli błąd programowania w wątku B powoduje wywołanie `Release` dwa razy, oba wywołania powiodą się. Licznik semafora jest zapełniony, a kiedy wątek a ostatecznie wywołuje `Release` <xref:System.Threading.SemaphoreFullException> , jest zgłaszany.  
  
## <a name="named-semaphores"></a>Semafory nazwane  
 System operacyjny Windows umożliwia semaforom używanie nazw. Nazwany Semafor to Wide system. Oznacza to, że po utworzeniu nazwanego semafora jest on widoczny dla wszystkich wątków we wszystkich procesach. Z tego względu nazwany semafor może służyć do synchronizowania działań procesów oraz wątków.  
  
 Można utworzyć <xref:System.Threading.Semaphore> obiekt reprezentujący nazwany semafor systemowy przy użyciu jednego z konstruktorów, które określają nazwę.  
  
> [!NOTE]
> Ponieważ nazwane semafory są systemem Wide, możliwe jest posiadanie wielu <xref:System.Threading.Semaphore> obiektów, które reprezentują ten sam semafor nazwany. Za każdym razem, gdy wywołujesz konstruktora <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> lub metodę, tworzony <xref:System.Threading.Semaphore> jest nowy obiekt. Wielokrotne Określanie nazwy powoduje utworzenie wielu obiektów, które reprezentują ten sam semafor nazwany.  
  
 Należy zachować ostrożność w przypadku używania semaforów nazwanych. Ponieważ są one całego systemu, inny proces, który używa tej samej nazwy, może nieoczekiwanie wprowadzić semafor. Złośliwy kod wykonywany na tym samym komputerze może być używany jako podstawa ataku typu "odmowa usługi".  
  
 Użyj zabezpieczeń kontroli dostępu, aby chronić <xref:System.Threading.Semaphore> obiekt, który reprezentuje nazwany semafor, najlepiej przy użyciu konstruktora, który <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> określa obiekt. Można również zastosować zabezpieczenia kontroli dostępu przy użyciu <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> metody, ale powoduje to pozostawienie okna luk w zabezpieczeniach między momentem utworzenia semafora a czasem jego ochrony. Ochrona semaforów z zabezpieczeniami kontroli dostępu pomaga zapobiegać złośliwym atakom, ale nie rozwiązuje problemu przypadkowych kolizji nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
