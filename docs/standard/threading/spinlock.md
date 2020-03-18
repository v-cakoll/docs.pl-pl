---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: eac9a1be38ea81e8ccee1d05d9061ceeb597627f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106171"
---
# <a name="spinlock"></a>SpinLock
Struktura <xref:System.Threading.SpinLock> jest niskiego poziomu, wzajemnego wykluczenia synchronizacji prymitywu, który obraca się, gdy czeka na uzyskanie blokady. Na komputerach wielordzeniowych, gdy oczekuje się, że <xref:System.Threading.SpinLock> czas oczekiwania będzie krótki, a rywalizacja jest minimalna, może działać lepiej niż inne rodzaje blokad. Jednak zaleca się, <xref:System.Threading.SpinLock> aby używać tylko wtedy, <xref:System.Threading.Monitor?displayProperty=nameWithType> gdy <xref:System.Threading.Interlocked> można określić przez profilowanie, że metoda lub metody są znacznie spowalniając wydajność programu.  
  
 <xref:System.Threading.SpinLock>może przynieść plasterek czasu wątku, nawet jeśli nie nabył jeszcze blokady. Czyni to, aby uniknąć odwrócenia priorytetwątku i włączyć moduł zbierający elementy bezużyteczne, aby postęp. Podczas korzystania <xref:System.Threading.SpinLock>z , upewnij się, że żaden wątek może przytrzymać blokadę przez więcej niż bardzo krótki czas i że żaden wątek nie może blokować, gdy posiada blokadę.  
  
 Ponieważ SpinLock jest typem wartości, należy jawnie przekazać go przez odwołanie, jeśli zamierzasz dwie kopie odwołać się do tej samej blokady.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Threading.SpinLock?displayProperty=nameWithType>używania tego typu, zobacz . Na przykład zobacz [Jak: Użyj SpinLock dla synchronizacji niskiego poziomu](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>obsługuje tryb*śledzenia* *wątku,*-który służy podczas fazy rozwoju, aby pomóc śledzić wątek, który trzyma blokadę w określonym czasie. Tryb śledzenia wątków jest bardzo przydatny do debugowania, ale zaleca się wyłączenie go w wersji programu, ponieważ może to spowolnić wydajność. Aby uzyskać więcej informacji, zobacz [Jak: Włącz tryb śledzenia wątków w SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Zobacz też

- [Wątkowe obiekty i operacje](../../../docs/standard/threading/threading-objects-and-features.md)
