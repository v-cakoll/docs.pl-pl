---
title: Wstrzymywanie i przerywanie wątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interrupting threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
ms.openlocfilehash: 3020694b93479d5f1d64d31c203f8fe033a10320
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129006"
---
# <a name="pausing-and-interrupting-threads"></a>Wstrzymywanie i przerywanie wątków

Najczęstszym sposobem synchronizacji działań wątków jest zablokowanie i wydawanie wątków oraz zablokowanie obiektów lub regionów kodu. Aby uzyskać więcej informacji na temat tych mechanizmów blokowania i blokowania, zobacz [Omówienie elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Możesz również mieć wątki umieszczają się w stanie uśpienia. Gdy wątki są zablokowane lub uśpione, można użyć <xref:System.Threading.ThreadInterruptedException>, aby przerwać ich Stany oczekiwania.  
  
## <a name="the-threadsleep-method"></a>Wątek. Sleep — metoda

 Wywołanie metody <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> powoduje natychmiastowe zablokowanie bieżącego wątku przez liczbę milisekund lub przedział czasu, który przeszedł do metody, i daje pozostałą część tego wycinka czasu do innego wątku. Po upływie tego czasu wątek uśpiony wznowi wykonywanie.  
  
 Jeden wątek nie może wywoływać <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w innym wątku.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> to metoda statyczna, która zawsze powoduje, że bieżący wątek jest w stanie uśpienia.  
  
 Wywołanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> z wartością <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> powoduje, że wątek stanie się uśpiony, dopóki nie zostanie przerwany przez inny wątek, który wywołuje metodę <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> w wątku uśpionym lub dopóki nie zostanie zakończone przez wywołanie metody <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  Poniższy przykład ilustruje obie metody przerywania uśpienia wątku.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Przerywanie wątków

 Możesz przerwać wątek oczekujący, wywołując metodę <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> w zablokowanym wątku, aby zgłosić <xref:System.Threading.ThreadInterruptedException>, która zrywa wątek z wywołania blokującego. Wątek powinien przechwycić <xref:System.Threading.ThreadInterruptedException> i wykonać odpowiednie czynności, aby kontynuować pracę. Jeśli wątek ignoruje wyjątek, środowisko uruchomieniowe przechwytuje wyjątek i zatrzyma wątek.  
  
> [!NOTE]
> Jeśli wątek docelowy nie jest blokowany w przypadku wywołania <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>, wątek nie zostanie przerwany do momentu jego zablokowania. Jeśli wątek nigdy nie jest blokowany, może zakończyć się bez przerywania działania.  
  
 Jeśli oczekiwane jest odczekanie zarządzane, wówczas <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> natychmiast wznowić wątek. Jeśli odczekanie jest niezarządzanym oczekiwaniem (na przykład wywołaniem platformy w systemie Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) ), żadna <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ani <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> nie mogą przejąć kontroli nad wątkiem do momentu, aż zwróci lub wywoła kod zarządzany. W kodzie zarządzanym zachowanie jest następujące:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wznawia wątek z dowolnego oczekiwania, może być w i powoduje, że <xref:System.Threading.ThreadInterruptedException> zostanie wygenerowany w wątku docelowym.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wznawia wątek z dowolnego oczekiwania, może być w i powoduje, że <xref:System.Threading.ThreadAbortException> być zgłaszane w wątku. Aby uzyskać szczegółowe informacje, zobacz [niszczenie wątków](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [Wątkowość](../../../docs/standard/threading/index.md)
- [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)
- [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
