---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: eac9a1be38ea81e8ccee1d05d9061ceeb597627f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106171"
---
# <a name="spinlock"></a>SpinLock
Struktura <xref:System.Threading.SpinLock> jest podstawową, średnią synchronizacją synchronizacji, która obraca się podczas oczekiwania na uzyskanie blokady. W przypadku komputerów z procesorem wielordzeniowym, gdy czasy oczekiwania będą krótkie i gdy rywalizacja jest minimalna, <xref:System.Threading.SpinLock> może być większa niż w przypadku innych rodzajów blokad. Zaleca się jednak używanie <xref:System.Threading.SpinLock> tylko w przypadku określenia przez profilowanie, że metoda <xref:System.Threading.Monitor?displayProperty=nameWithType> lub metody <xref:System.Threading.Interlocked> znacznie spowalniają wydajność programu.  
  
 <xref:System.Threading.SpinLock> może spowodować wycinek czasu wątku, nawet jeśli nie uzyskał jeszcze blokady. Ma to na celu uniknięcie niedziałania priorytetu wątku oraz umożliwienie wyrzucania elementów bezużytecznych. W przypadku korzystania z <xref:System.Threading.SpinLock>upewnij się, że żaden wątek nie może obsłużyć blokady dłużej niż w bardzo krótkim przedziale czasu i że żaden wątek nie może blokować blokady.  
  
 Ponieważ struktury SpinLock jest typem wartości, należy jawnie przekazać go przez odwołanie, jeśli chcesz, aby te dwie kopie odwołują się do tej samej blokady.  
  
 Aby uzyskać więcej informacji na temat korzystania z tego typu, zobacz <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Aby zapoznać się z przykładem, zobacz [How to: use struktury spinlock to the Low-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock> obsługuje tryb *śledzenia*-*wątku* , którego można użyć w fazie opracowywania, aby ułatwić śledzenie wątku utrzymującego blokadę w określonym czasie. Tryb śledzenia wątków jest bardzo przydatny do debugowania, ale zalecamy wyłączenie go w wydanej wersji programu, ponieważ może to spowodować spadek wydajności. Aby uzyskać więcej informacji, zobacz [jak: włączyć tryb śledzenia wątków w struktury spinlock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
