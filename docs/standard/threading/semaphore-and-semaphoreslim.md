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
ms.openlocfilehash: b9f7c122ac8acf34f740aca5f0fafc162edcea82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127583"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor i klasa SemaphoreSlim
Klasa <xref:System.Threading.Semaphore?displayProperty=nameWithType> reprezentuje nazwany (systemowy) lub lokalny semafor. Jest to cienka owijka wokół obiektu semafora Win32. Semafory Win32 zliczają semafory, które mogą służyć do kontrolowania dostępu do puli zasobów.  
  
 Klasa <xref:System.Threading.SemaphoreSlim> reprezentuje lekki, szybki semafor, który może służyć do oczekiwania w ramach jednego procesu, gdy oczekuje się, że czas oczekiwania będzie bardzo krótki. <xref:System.Threading.SemaphoreSlim>opiera się w jak największym stopniu na prymitywy synchronizacji dostarczonych przez program runtime języka wspólnego (CLR). Jednak zapewnia również leniwie zainicjowane, oparte na jądrze uchwyty oczekiwania, zgodnie z potrzebami, aby obsługiwać oczekiwanie na wiele semaforów. <xref:System.Threading.SemaphoreSlim>obsługuje również użycie tokenów anulowania, ale nie obsługuje nazwanych semaforów ani użycia uchwytu oczekiwania do synchronizacji.  
  
## <a name="managing-a-limited-resource"></a>Zarządzanie ograniczonym zasobem  
 Wątki wprowadzić semafora, <xref:System.Threading.WaitHandle.WaitOne%2A> wywołując metodę, która jest <xref:System.Threading.WaitHandle> dziedziczona z <xref:System.Threading.Semaphore?displayProperty=nameWithType> klasy, <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> w <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> przypadku obiektu lub <xref:System.Threading.SemaphoreSlim> lub metody, w przypadku obiektu. Po powrocie połączenia, liczba na semaforjest zmniejszana. Gdy wątek żąda wpisu i liczba wynosi zero, bloki wątku. Jak wątki zwolnić semafora, <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> wywołując lub metody, blokowane wątki mogą wejść. Nie ma gwarantowanej kolejności, takiej jak fifo (first-in, first-out) lub last-in, first-out (LIFO), dla zablokowanych wątków, aby wejść do semafora.  
  
 Wątek może wprowadzić semafora wiele razy, <xref:System.Threading.Semaphore?displayProperty=nameWithType> wywołując <xref:System.Threading.WaitHandle.WaitOne%2A> metodę <xref:System.Threading.SemaphoreSlim> obiektu lub <xref:System.Threading.SemaphoreSlim.Wait%2A> metody obiektu wielokrotnie. Aby zwolnić semafora, wątek można <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> wywołać lub <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> przeciążenia metody tyle <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> samo <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> razy lub wywołać przeciążenie lub metody i określić liczbę wpisów do zwolnienia.  
  
### <a name="semaphores-and-thread-identity"></a>Semafory i tożsamość wątku  
 Dwa typy semafora nie wymuszają tożsamości <xref:System.Threading.WaitHandle.WaitOne%2A>wątku w wywołaniach , <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>i <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metod. Na przykład typowy scenariusz użycia semaforów obejmuje wątek producenta i wątek konsumenta, z jednym wątkiem zawsze zwiększa liczbę semaforów, a drugi zawsze zmniejsza go.  
  
 Obowiązkiem programisty jest upewnienie się, że wątek nie zwalnia semafora zbyt wiele razy. Załóżmy na przykład, że semafor ma maksymalną liczbę dwóch, a ten wątek A i wątek B wprowadzają semafor. Jeśli błąd programowania w wątku B `Release` powoduje wywołanie dwa razy, oba wywołania powiedzie się. Liczba semafora jest pełna, a gdy wątek `Release`A <xref:System.Threading.SemaphoreFullException> ostatecznie wywołuje , a jest wyrzucany.  
  
## <a name="named-semaphores"></a>Nazwane Semafory  
 System operacyjny Windows umożliwia semafory mieć nazwy. Nazwany semafor jest szeroki w systemie. Oznacza to, że po utworzeniu nazwanego semafora jest widoczny dla wszystkich wątków we wszystkich procesach. W związku z tym nazwany semafor może służyć do synchronizacji działań procesów, a także wątków.  
  
 Można utworzyć <xref:System.Threading.Semaphore> obiekt, który reprezentuje nazwany semafor systemu przy użyciu jednego z konstruktorów, który określa nazwę.  
  
> [!NOTE]
> Ponieważ nazwane semafory są szerokie systemowe, <xref:System.Threading.Semaphore> możliwe jest, aby wiele obiektów, które reprezentują ten sam semafor o nazwie. Za każdym razem, gdy <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> wywołasz <xref:System.Threading.Semaphore> konstruktora lub metodę, tworzony jest nowy obiekt. Określanie tej samej nazwy wielokrotnie tworzy wiele obiektów, które reprezentują ten sam nazwany semafor.  
  
 Należy zachować ostrożność podczas używania nazwanych semaforów. Ponieważ są one ogólnosystemowe, inny proces, który używa tej samej nazwy można wprowadzić semafora nieoczekiwanie. Złośliwy kod wykonywany na tym samym komputerze może użyć tego jako podstawy ataku typu "odmowa usługi".  
  
 Użyj zabezpieczeń kontroli dostępu, aby chronić <xref:System.Threading.Semaphore> obiekt, który reprezentuje nazwany semafor, najlepiej <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> przy użyciu konstruktora, który określa obiekt. Można również zastosować zabezpieczenia kontroli <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> dostępu za pomocą tej metody, ale pozostawia to okno luki między czasem utworzenia semafora a czasem, w którym jest chroniony. Ochrona semaforów z zabezpieczeniami kontroli dostępu pomaga zapobiegać złośliwym atakom, ale nie rozwiązuje problemu niezamierzonych kolizji nazw.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [Wątkowe obiekty i operacje](../../../docs/standard/threading/threading-objects-and-features.md)
