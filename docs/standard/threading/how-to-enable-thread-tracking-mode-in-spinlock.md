---
title: 'Porady: włączanie śledzenia wątków w strukturze SpinLock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
ms.openlocfilehash: f52a844284cf46bcace3f54f8b320d336050a64e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138034"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Porady: włączanie śledzenia wątków w strukturze SpinLock
<xref:System.Threading.SpinLock?displayProperty=nameWithType> to blokada wzajemnego wykluczania niskiego poziomu, która może być używana w scenariuszach, które mają bardzo krótkie czasy oczekiwania. <xref:System.Threading.SpinLock> nie jest w odróżnieniu od siebie. Po przejściu przez wątek na blokadę należy prawidłowo zamknąć blokadę, aby można było wprowadzić ją ponownie. Zwykle każda próba ponownego wprowadzenia blokady spowodowałaby zakleszczenie i zakleszczenie może być bardzo trudne do debugowania. Jako pomoc dla rozwoju, <xref:System.Threading.SpinLock?displayProperty=nameWithType> obsługuje tryb śledzenia wątków, który powoduje, że wyjątek jest zgłaszany, gdy wątek próbuje ponownie wprowadzić blokadę, która już mieści się. Umożliwia to łatwiejsze lokalizowanie punktu, w którym blokada nie została prawidłowo zakończona. Tryb śledzenia wątków można włączyć, używając konstruktora <xref:System.Threading.SpinLock>, który przyjmuje parametr wejściowy Boolean i przekazując argument `true`. Po zakończeniu etapów tworzenia i testowania Wyłącz tryb śledzenia wątków, aby uzyskać lepszą wydajność.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje tryb śledzenia wątków. Wiersze, które prawidłowo zamykają blokadę, są oznaczone jako komentarze, aby symulować błąd kodowania, który powoduje wystąpienie jednego z następujących wyników:  
  
- Wyjątek jest generowany, jeśli <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `true` (`True` w Visual Basic).  
  
- Zakleszczenie, jeśli <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `false` (`False` w Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Zobacz także

- [SpinLock](../../../docs/standard/threading/spinlock.md)
