---
title: "Thread.Suspend, odzyskiwanie pamięci i punkty bezpieczeństwa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fdd56763712dee9c6fa1f292eb3bbb2f0ccbf505
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend, odzyskiwanie pamięci i punkty bezpieczeństwa
Podczas wywoływania <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> w wątku, system uwagi dotyczące czy zawieszenia wątku zażądano i umożliwia wątku do wykonania, dopóki osiągnie bezpiecznym faktycznie wstrzymania wątku. Bezpieczne punktu dla wątku jest punktem w pamięci, które mogą być wykonywane kolekcji podczas jej wykonywania.  
  
 Po osiągnięciu punktu bezpieczne środowisko uruchomieniowe gwarantuje, że wątku zawieszonym nie dokona żadnych dalszych postępów w kodzie zarządzanym. Wątek wykonywania poza kod zarządzany jest zawsze bezpieczne dla wyrzucanie elementów bezużytecznych i jego wykonywanie będzie kontynuowane, dopóki próbuje wznowić wykonywanie kodu zarządzanego.  
  
> [!NOTE]
>  Aby można było wykonać wyrzucania elementów bezużytecznych, środowiska uruchomieniowego musi zawiesić wszystkie wątki oprócz wątku wykonywania kolekcji. Każdy wątek musi być wprowadzane do bezpiecznego punktu przed może zostać zawieszone.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Automatyczne zarządzanie pamięcią](../../../docs/standard/automatic-memory-management.md)
