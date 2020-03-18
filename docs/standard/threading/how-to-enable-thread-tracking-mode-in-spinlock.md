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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138034"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Porady: włączanie śledzenia wątków w strukturze SpinLock
<xref:System.Threading.SpinLock?displayProperty=nameWithType>jest niskopoziomową blokadą wzajemnego wykluczenia, której można użyć w scenariuszach, które mają bardzo krótki czas oczekiwania. <xref:System.Threading.SpinLock>nie jest ponownie wchodzącym na rynek. Po wejściu gwintu do zamka, musi wyjść z blokady poprawnie, zanim będzie mógł wejść ponownie. Zazwyczaj każda próba ponownego wprowadzenia blokady spowoduje zakleszczenie, a zakleszczenia mogą być bardzo trudne do debugowania. Jako pomoc dla <xref:System.Threading.SpinLock?displayProperty=nameWithType> rozwoju obsługuje tryb śledzenia wątków, który powoduje wyjątek, który ma zostać wygenerowany, gdy wątek próbuje ponownie wprowadzić blokadę, która już posiada. Dzięki temu łatwiej zlokalizować punkt, w którym blokada nie została poprawnie wypuszczona. Tryb śledzenia wątków można włączyć <xref:System.Threading.SpinLock> przy użyciu konstruktora, który przyjmuje parametr `true`wejściowy logiczny i przekazując argument . Po zakończeniu fazy tworzenia i testowania wyłącz tryb śledzenia wątków, aby uzyskać lepszą wydajność.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono tryb śledzenia wątków. Wiersze, które poprawnie zakończyć blokadę są komentowane w celu symulacji błędu kodowania, który powoduje jeden z następujących wyników:  
  
- Wyjątek jest zgłaszany, <xref:System.Threading.SpinLock> jeśli został utworzony `true` przy`True` użyciu argumentu ( w języku Visual Basic).  
  
- Zakleszczenie, <xref:System.Threading.SpinLock> jeśli został utworzony `false` `False` przy użyciu argumentu ( w języku Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Zobacz też

- [SpinLock](../../../docs/standard/threading/spinlock.md)
