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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129006"
---
# <a name="pausing-and-interrupting-threads"></a>Wstrzymywanie i przerywanie wątków

Najczęstszymi sposobami synchronizowania działań wątków są blokowanie i zwalnianie wątków lub blokowanie obiektów lub regionów kodu. Aby uzyskać więcej informacji na temat tych mechanizmów blokowania i blokowania, zobacz [Omówienie podstawowych elementów synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Można również mieć wątki umieścić się w stanie uśpienia. Gdy wątki są zablokowane lub śpiące, można użyć <xref:System.Threading.ThreadInterruptedException> do wyrwania ich ze stanów oczekiwania.  
  
## <a name="the-threadsleep-method"></a>Metoda Thread.Sleep

 Wywołanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metody powoduje, że bieżący wątek natychmiast zablokować liczbę milisekund lub przedział czasu, który można przekazać do metody i daje resztę jego wycinek czasu do innego wątku. Po upływie tego interwału wątek uśpiony wznawia wykonywanie.  
  
 Jeden wątek <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> nie może wywołać innego wątku.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>jest metodą statyczną, która zawsze powoduje, że bieżący wątek jest w stanie uśpienia.  
  
 Wywołanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> z <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> wartością powoduje, że wątek do uśpienia, dopóki nie zostanie przerwane przez inny wątek, który wywołuje <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metodę w wątku uśpienia lub dopóki nie zostanie zakończona przez wywołanie jego <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody.  Poniższy przykład ilustruje obie metody przerywania wątku uśpionego.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Przerywanie wątków

 Można przerwać wątek oczekiwania, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wywołując metodę w zablokowanym <xref:System.Threading.ThreadInterruptedException>wątku, aby wyrzucić , który przerywa wątek z wywołania blokowania. Wątek powinien złapać <xref:System.Threading.ThreadInterruptedException> i zrobić wszystko, co jest właściwe, aby kontynuować pracę. Jeśli wątek ignoruje wyjątek, czas wykonywania przechwytuje wyjątek i zatrzymuje wątek.  
  
> [!NOTE]
> Jeśli wątek docelowy nie jest <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> zablokowany, gdy jest wywoływana, wątek nie jest przerywany, dopóki nie blokuje. Jeśli wątek nigdy nie blokuje, może zakończyć się bez przerywania.  
  
 Jeśli oczekiwanie jest zarządzane czekać, a następnie <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> oba wybudzają wątek natychmiast. Jeśli wait jest niezarządzane czekać (na przykład platforma wywołać wywołanie funkcji Win32 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> [WaitForSingleObject),](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) ani nie może przejąć kontrolę nad wątkiem, dopóki nie powróci do lub wywołuje do kodu zarządzanego. W kodzie zarządzanym zachowanie jest następujące:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>wybudza wątek z dowolnego oczekiwania może <xref:System.Threading.ThreadInterruptedException> być w i powoduje, że mają być wyrzucone w wątku docelowego.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>wybudza wątek z dowolnego oczekiwania może <xref:System.Threading.ThreadAbortException> być w i powoduje, że mają być wyrzucane na wątku. Aby uzyskać szczegółowe informacje, zobacz [Niszczenie wątków](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [Wątków](../../../docs/standard/threading/index.md)
- [Korzystanie z wątków i wątków](../../../docs/standard/threading/using-threads-and-threading.md)
- [Omówienie elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
