---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bd2468c7b68a9c79e7418a32294676fb468e1a9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042637"
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> Struktury jest niskiego poziomu, wykluczania wzajemnego synchronizacji, który uruchamia podczas oczekiwania na uzyskanie blokady. Na komputerach wielordzeniowych, gdy czasy oczekiwania powinny być krótki, a gdy rywalizacja jest minimalny <xref:System.Threading.SpinLock> można mają lepszą wydajność niż inne rodzaje blokady. Jednak firma Microsoft zaleca użycie <xref:System.Threading.SpinLock> tylko przy określaniu przez profilowanie, który <xref:System.Threading.Monitor?displayProperty=nameWithType> metody lub <xref:System.Threading.Interlocked> znacznie metody są spowolnienia działania programu.  
  
 <xref:System.Threading.SpinLock> może przynieść przedziału czasu wątku, nawet wtedy, gdy nie ma jeszcze uzyskać blokadę. Robi to, aby uniknąć odwrócenie priorytetu wątku i włączyć moduł garbage collector postępu. Kiedy używasz <xref:System.Threading.SpinLock>, upewnij się, żaden wątek nie może zawierać blokady dla więcej niż bardzo krótki okres i że żaden wątek nie można zablokować, gdy posiada blokadę.  
  
 Ponieważ struktury SpinLock jest typem wartości, musi jawnie przekazujesz ją przez odwołanie, jeśli mają dwie kopie do odwoływania się do tego samego blokady.  
  
 Aby uzyskać więcej informacji na temat używania tego typu, zobacz <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Aby uzyskać przykład, zobacz [jak: struktury Użyj SpinLock do synchronizacji niższego poziomu](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock> obsługuje *wątku*-*śledzenia* tryb, który można użyć w fazie opracowywania, ułatwiają śledzenie wątku, który powoduje blokadę o określonej godzinie. Tryb śledzenia wątków jest bardzo przydatne podczas debugowania, ale firma Microsoft zaleca wyłączenie go w wersji programu, ponieważ jego może obniżyć wydajność. Aby uzyskać więcej informacji, zobacz [jak: tryb śledzenia Włącz wątków w strukturze SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
