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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3dcee9c45cdbf029ccba90a963c9cea0a9c7ad4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963577"
---
# <a name="pausing-and-interrupting-threads"></a>Wstrzymywanie i przerywanie wątków

Najczęstszym sposobem synchronizacji działań wątków jest zablokowanie i wydawanie wątków oraz zablokowanie obiektów lub regionów kodu. Aby uzyskać więcej informacji na temat tych mechanizmów blokowania i blokowania, zobacz [Omówienie elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Możesz również mieć wątki umieszczają się w stanie uśpienia. Gdy wątki są zablokowane lub uśpione, można użyć <xref:System.Threading.ThreadInterruptedException> , aby przerwać ich Stany oczekiwania.  
  
## <a name="the-threadsleep-method"></a>Wątek. Sleep — metoda

 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> Wywołanie metody powoduje natychmiastowe zablokowanie bieżącego wątku przez liczbę milisekund lub przedział czasu przekazywany do metody, a następnie zwraca resztę z wycinka czasu do innego wątku. Po upływie tego czasu wątek uśpiony wznowi wykonywanie.  
  
 Jeden wątek nie może <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> wywołać w innym wątku.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>to metoda statyczna, która zawsze powoduje, że bieżący wątek jest w stanie uśpienia.  
  
 Wywoływanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wartości powoduje, że wątek jest uśpiony, dopóki nie zostanie przerwany przez inny wątek, który wywołuje metodę w wątku uśpionym lub dopóki nie zostanie zakończone przez wywołanie <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody. <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType>  Poniższy przykład ilustruje obie metody przerywania uśpienia wątku.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Przerywanie wątków

 Możesz przerwać wątek oczekujący przez wywołanie <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody w zablokowanym wątku w celu wygenerowania elementu <xref:System.Threading.ThreadInterruptedException>, który przerwie wątek poza wywołaniem blokującym. Wątek powinien przechwycić <xref:System.Threading.ThreadInterruptedException> i wykonać wszelkie odpowiednie działania, aby kontynuować pracę. Jeśli wątek ignoruje wyjątek, środowisko uruchomieniowe przechwytuje wyjątek i zatrzyma wątek.  
  
> [!NOTE]
> Jeśli wątek docelowy nie jest blokowany, gdy <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> jest wywoływana, wątek nie zostanie przerwany do momentu jego zablokowania. Jeśli wątek nigdy nie jest blokowany, może zakończyć się bez przerywania działania.  
  
 Jeśli oczekiwane jest odczekanie zarządzane, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> następnie natychmiast Wznów wątek. Jeśli oczekiwanie jest niezarządzanym oczekiwaniem (na przykład wywołaniem platformy w funkcji [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) Win32) <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ani nie może przejąć kontroli nad wątkiem do momentu, aż zwróci lub wywoła kod zarządzany. W kodzie zarządzanym zachowanie jest następujące:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>wznawia wątek z dowolnego oczekiwania, który może znajdować się w wątku docelowym i <xref:System.Threading.ThreadInterruptedException> powoduje jego wygenerowanie.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>wznawia wątek z dowolnego oczekiwania, który może znajdować się w <xref:System.Threading.ThreadAbortException> wątku. Aby uzyskać szczegółowe informacje, zobacz [niszczenie wątków](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [Wątkowość](../../../docs/standard/threading/index.md)
- [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)
- [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
