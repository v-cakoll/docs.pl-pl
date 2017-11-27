---
title: SpinWait
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
helpviewer_keywords: synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfaf85c0fe1de3be89618ae540e9c183b66a11eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>jest typem synchronizacji lekkie, który można użyć w scenariuszach niskiego poziomu, aby uniknąć przełączeń kontekstu kosztowne i przejścia jądra, które są wymagane w przypadku zdarzeń jądra. Na komputerach wielordzeniowych gdy zasób nie powinno być przechowywane przez długi czas, może być bardziej wydajny oczekiwania wątku pokrętła w trybie użytkownika przez kilka dozen lub kilka cykli kilkuset, a następnie spróbuj ponownie do uzyskania dostępu do zasobu. Jeśli zasób jest dostępny po Obracająca, zostały zapisane w kilku tysięcy cykle. Jeśli zasób jest nadal niedostępna, następnie poświęcony tylko kilka cykli i nadal można wprowadzić oczekiwania na podstawie jądra. Ta kombinacja Obracająca następnie oczekiwania jest czasami nazywany *dwufazowej operacji oczekiwania*.  
  
 <xref:System.Threading.SpinWait>jest przeznaczony do użycia w połączeniu z typów .NET Framework, które otaczają zdarzeń jądra, takich jak <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait>można również samodzielnie Obracająca podstawowych funkcji programu tylko jeden.  
  
 <xref:System.Threading.SpinWait>jest więcej niż tylko puste pętli. Starannie wdrażana jest zapewnienie Obracająca poprawne zachowanie w przypadku ogólnych i samego zainicjuje przełączenia kontekstu, jeśli jego obraca wystarczająco długi (około długość czasu wymaganego do przejścia jądra). Na przykład na komputerach jednordzeniowy <xref:System.Threading.SpinWait> daje przedział czasu wątku natychmiast, ponieważ bloki Obracająca przekazywania postępu na wszystkie wątki. <xref:System.Threading.SpinWait>daje również nawet w wielordzeniowych maszynach, aby zapobiec oczekiwania wątku zablokowanie wątków o wyższym priorytecie lub moduł garbage collector. Dlatego jeśli używasz <xref:System.Threading.SpinWait> w dwufazowej operacji oczekiwania, zaleca się, że wywołanie jądra czas oczekiwania przed <xref:System.Threading.SpinWait> inicjuje się przełączenie kontekstu. <xref:System.Threading.SpinWait>udostępnia <xref:System.Threading.SpinWait.NextSpinWillYield%2A> właściwości, które można sprawdzić przed każdym wywołaniu <xref:System.Threading.SpinWait.SpinOnce%2A>. Gdy właściwość zwraca `true`, Inicjowanie operacji oczekiwania. Na przykład zobacz [porady: użycie metody SpinWait, aby zaimplementować operację oczekiwania dwufazowy](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Jeśli bez wykonywania dwufazowej operacji oczekiwania, ale są po prostu wirowania do czasu spełnienia określonego warunku jest PRAWDA, aby umożliwić <xref:System.Threading.SpinWait> przeprowadzić jego kontekstu przełącza się tak, aby dobrej obywateli w środowisku systemu operacyjnego Windows. W poniższym przykładzie podstawowe przedstawiono <xref:System.Threading.SpinWait> w stosie bez blokady. Jeśli potrzebujesz stosu wysokiej wydajności, bezpieczne wątkowo, należy rozważyć użycie <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
