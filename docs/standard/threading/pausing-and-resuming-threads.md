---
title: "Wstrzymywanie i wznawianie wątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4b87fbb51dbdcd5226a902e8b7ee5aeb7e126b7e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="pausing-and-resuming-threads"></a>Wstrzymywanie i wznawianie wątków
Najbardziej typowe sposoby synchronizowania działania wątków są bloku i wersji wątków lub obiektów blokady lub regiony kodu. Aby uzyskać więcej informacji o tych blokowania i blokuje mechanizmów, zobacz [podstawowych Omówienie synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Może także zawierać wątków put samodzielnie w stan uśpienia. Gdy wątki są zablokowane lub uśpiony, można użyć <xref:System.Threading.ThreadInterruptedException> celu wyjścia ich stany oczekiwania.  
  
## <a name="the-threadsleep-method"></a>Metoda Thread.Sleep  
 Wywoływanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metoda powoduje, że bieżący wątek natychmiast zablokować liczbę milisekund lub przedział czasu możesz przekazać do metody i daje w pozostałej części jej przedział czasu do innego wątku. Po upływie tego przedziału, uśpiony wątku wznawia wykonywanie.  
  
 Nie można wywołać jeden wątek <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> w innym wątku.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>jest metodą statyczną, która zawsze powoduje, że bieżący wątek w stan uśpienia.  
  
 Wywoływanie <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> o wartości <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> powoduje, że wątek w stan uśpienia, dopóki nie zostanie przerwane przez inny wątek, który wywołuje <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody w wątku uśpiony lub dopóki zostanie przerwany przez wywołanie do jego <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody.  Poniższy przykład przedstawia obu metod przerwania uśpiony wątku.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Przerywanie wątków  
 Można przerwać wątek oczekiwania przez wywołanie metody <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody w wątku zablokowanych, aby zgłosić <xref:System.Threading.ThreadInterruptedException>, która dzieli wątek poza blokowania wywołania. Wątek powinien catch <xref:System.Threading.ThreadInterruptedException> i wykonaj niezależnie od jest kontynuować pracę. Jeśli wątek ignoruje wyjątek, środowisko uruchomieniowe przechwytuje wyjątek i zatrzymuje wątek.  
  
> [!NOTE]
>  Jeśli wątek docelowy nie jest blokowane podczas <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> jest wywoływana, wątek nie zostało przerwane aż bloki. Jeśli wątek nigdy nie blokuje, można wykonać bez kiedykolwiek przerwane.  
  
 Jeśli oczekiwania jest zarządzany czas oczekiwania, następnie <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> oba niezwłocznie wake wątku. Jeśli oczekiwania jest niezarządzany oczekiwania (na przykład platformę wywołanie wywołanie Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) funkcji), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ani <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> może przejąć kontrolę nad wątek, dopóki przywraca lub wywołania wewnątrz kodu zarządzanego. W kodzie zarządzanym zachowanie jest następujący:  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>Wznawia działanie wątku poza wszelkie oczekiwania może być w i powoduje, że <xref:System.Threading.ThreadInterruptedException> zostanie wygenerowany w wątek docelowy.  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Wznawia działanie wątku poza wszelkie oczekiwania może być w i powoduje, że <xref:System.Threading.ThreadAbortException> zostanie wygenerowany w wątku. Aby uzyskać więcej informacji, zobacz [niszczenie wątków](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
