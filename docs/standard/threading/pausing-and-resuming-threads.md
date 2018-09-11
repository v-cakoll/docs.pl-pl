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
ms.openlocfilehash: b66881a8a42c0c34b5c2119f7404fe7787c8f3f2
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273129"
---
# <a name="pausing-and-interrupting-threads"></a>Wstrzymywanie i przerywanie wątków

Najbardziej typowych sposobów do synchronizowania działania wątki są bloku i wersji wątków lub blokowanie obiektów lub regiony kodu. Aby uzyskać więcej informacji na temat tych blokowania i blokowanie mechanizmów, zobacz [Przegląd podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Mogą też istnieć wątków, umieść samodzielnie w stan uśpienia. Gdy są blokowane wątki lub uśpiony, możesz użyć <xref:System.Threading.ThreadInterruptedException> aby zerwać ich stanów oczekiwania.  
  
## <a name="the-threadsleep-method"></a>Metoda Thread.Sleep

 Wywoływanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metoda powoduje, że bieżący wątek natychmiast zablokować na liczbę milisekund lub przedział czasu, możesz przekazać do metody i daje resztę uzyskaną z jego przedziału czasu na inny wątek. Po upływie tego interwału, uśpionych wątków wznawia działanie.  
  
 Nie można wywołać jeden wątek <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w innym wątku.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> jest metoda statyczna zawsze powoduje, że bieżący wątek w stan uśpienia.  
  
 Wywoływanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> o wartości <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> powoduje, że wątek w tryb uśpienia, dopóki nie zostanie przerwane przez inny wątek, który wywołuje <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody w wątku, uśpiony lub dopóki zostanie przerwany przez wywołanie jego <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody.  Poniższy przykład ilustruje obie metody przerywania uśpionych wątków.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Przerywanie wątków

 Zostanie przerwany wątek oczekiwania przez wywołanie metody <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody na zablokowany wątek zgłosić <xref:System.Threading.ThreadInterruptedException>, która dzieli wątku poza wywołania blokowania. Przechwytywać wątku <xref:System.Threading.ThreadInterruptedException> i wykonaj, niezależnie od rodzaju przydaje się kontynuować pracę. Jeśli wątek ignoruje wyjątek, środowisko uruchomieniowe przechwytuje wyjątek i zatrzymuje wątek.  
  
> [!NOTE]
>  Jeśli wątek docelowy nie jest zablokowane, gdy <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> jest wywoływana, wątek nie zostało przerwane aż bloków. Jeśli wątek nigdy nie blokuje, mogło zostać zakończone bez kiedykolwiek przerwane.  
  
 W przypadku oczekiwania zarządzanych oczekiwania, następnie <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zarówno od razu wznawiania wątku. W przypadku oczekiwania niezarządzanych oczekiwania (na przykład, wywołanie Win32 przez wywołania platformy [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) funkcji), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ani <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> może przejąć kontrolę nad wątku, dopóki przywraca lub wywołuje kod zarządzany. W kodzie zarządzanym zachowanie jest następujący:  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> Wznawia działanie wątku z dowolnym oczekiwania, mogą powodować i powoduje, że <xref:System.Threading.ThreadInterruptedException> zostanie wygenerowany w wątek docelowy.  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Wznawia działanie wątku z dowolnym oczekiwania, mogą powodować i powoduje, że <xref:System.Threading.ThreadAbortException> zostanie wygenerowany w wątku. Aby uzyskać więcej informacji, zobacz [niszczenie wątków](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadInterruptedException>  
- <xref:System.Threading.ThreadAbortException>  
- [Wątkowość](../../../docs/standard/threading/index.md)  
- [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)  
- [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
