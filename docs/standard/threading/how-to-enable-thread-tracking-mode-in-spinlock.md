---
title: "Porady: włączanie śledzenia wątków w strukturze SpinLock"
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
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Porady: włączanie śledzenia wątków w strukturze SpinLock
<xref:System.Threading.SpinLock?displayProperty=nameWithType>jest blokady niskiego poziomu wzajemne wykluczenie używanej w scenariuszach, w których czasy oczekiwania bardzo krótki. <xref:System.Threading.SpinLock>nie jest wielobieżnej. Od wątku wejścia blokady, jego musi się zakończyć blokady prawidłowo przed można wprowadzić ponownie. Zazwyczaj próba ponowne wprowadzenie blokady spowodowałoby zakleszczenie i zakleszczenie może być bardzo trudne do debugowania. Jako pomoc do rozwoju <xref:System.Threading.SpinLock?displayProperty=nameWithType> obsługuje tryb śledzenia wątków, powodujący wyjątek zostanie wygenerowany, gdy wątek próbuje ponowne wprowadzenie blokady, który już zawiera. Dzięki temu można łatwo zlokalizować więcej punktu, jaką blokady nie został zakończony poprawnie. Tryb śledzenia wątków można włączyć za pomocą <xref:System.Threading.SpinLock> wejściowych konstruktora, który przyjmuje wartość logiczną parametru i przekazywanie w argumencie `true`. Po zakończeniu tworzenia i testowania fazy, należy wyłączyć tryb śledzenia wątków w celu poprawy wydajności.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano śledzenia wątków. Wiersze, które prawidłowo zakończyć blokady są oznaczone jako komentarz do symulowania błąd kodowania, który powoduje, że jeden z następujących wyników:  
  
-   Jest zwracany wyjątek, jeśli <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `true` (`True` w języku Visual Basic).  
  
-   Jeśli do zakleszczenia <xref:System.Threading.SpinLock> został utworzony przy użyciu argumentu `false` (`False` w języku Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury SpinLock](../../../docs/standard/threading/spinlock.md)
