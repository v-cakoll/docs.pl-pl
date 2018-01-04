---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e83505a36252457d286bc7fbc6bbe442732229a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> Struktura jest niskiego poziomu, wzajemne wykluczenie prymitywu synchronizacji, który obraca podczas oczekiwania na uzyskanie blokady. W przypadku komputerów wielordzeniowych podczas czasy oczekiwania są powinien być krótki i kiedy rywalizacji jest minimalny <xref:System.Threading.SpinLock> może działać lepiej niż inne rodzaje blokad. Jednak zaleca się używanie <xref:System.Threading.SpinLock> tylko przy określaniu przez profilowania, która <xref:System.Threading.Monitor?displayProperty=nameWithType> metody lub <xref:System.Threading.Interlocked> metody znacznie spowalniają działanie programu.  
  
 <xref:System.Threading.SpinLock>może spowodować przedział czasu w wątku, nawet jeśli nie ma jeszcze uzyskać blokady. Jest to, aby uniknąć odwracanie priorytetu wątku i Włącz moduł zbierający elementy bezużyteczne postęp. Jeśli używasz <xref:System.Threading.SpinLock>, upewnij się, wątku nie może zawierać blokady dla więcej niż bardzo krótki okres oraz że wątku nie można zablokować, gdy posiada blokady.  
  
 Ponieważ struktury SpinLock jest typem wartości, należy jawnie przekazujesz ją przez odwołanie, jeśli planujesz obydwie kopie do odwoływania się do tego samego blokady.  
  
 Aby uzyskać więcej informacji na temat używania tego typu, zobacz <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Na przykład zobacz [porady: struktury Użyj SpinLock do synchronizacji niższego poziomu](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>obsługuje *wątku*-*śledzenia* tryb pomocne podczas fazy opracowywania służące do śledzenia w wątku, który jest z blokadą w określonym czasie. Tryb śledzenia wątków jest bardzo przydatne w przypadku debugowania, ale firma Microsoft zaleca wyłączenie go w wydanej wersji programu, ponieważ może zmniejszyć wydajność. Aby uzyskać więcej informacji, zobacz [porady: tryb włączyć wątku śledzenia w strukturze SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
