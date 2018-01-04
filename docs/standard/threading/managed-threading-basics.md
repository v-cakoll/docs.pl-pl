---
title: "Zarządzana wątkowość — podstawy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 035834959aa5f9340727327b22cae93b3f21b056
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="managed-threading-basics"></a>Zarządzana wątkowość — podstawy
Pierwsze pięć tematy w tej sekcji mają ułatwić określenie, kiedy używać zarządzanych wątków i opisano niektóre podstawowe funkcje. Aby informacji na temat klas, które zapewniają dodatkowe funkcje, zobacz [wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md) i [podstawowych Omówienie synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Pozostałe tematy w tej sekcji obejmują zaawansowane tematy, w tym interakcji z zarządzanych wątków w systemie operacyjnym Windows.  
  
> [!NOTE]
>  W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], bibliotece równoległych zadań i PLINQ podanie interfejsów API równoległość zadań i danych w programów wielowątkowych. Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)  
 W tym artykule omówiono zalety i wady wiele wątków i opisano scenariusze, w których można utworzyć wątków lub użyj wątków z puli wątków.  
  
 [Wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Opisuje zachowanie nieobsługiwanych wyjątków w wątkach dla różnych wersji programu .NET Framework, w szczególności sytuacji w co ich spowodować przerwanie aplikacji.  
  
 [Synchronizowanie danych na potrzeby wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 W tym artykule opisano strategie synchronizacji danych w grupach, które będą używane z wielu wątków.  
  
 [Zarządzane stany wątków](../../../docs/standard/threading/managed-thread-states.md)  
 Opisano stany wątków podstawowych oraz wyjaśniono, jak wykryć, czy wątek jest uruchomiony.  
  
 [Wątki pierwszego planu i tła](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Wyjaśniono różnice między wątkami pierwszego planu i tła.  
  
 [Zarządzana i niezarządzana wątkowość w systemie Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Związek między zarządzana i niezarządzana wątkowość, zawiera listę zarządzanych odpowiedników wątkowość interfejsów API systemu Windows i w tym artykule omówiono interakcji apartamentach COM i zarządzanych wątków.  
  
 [Thread.Suspend, odzyskiwanie pamięci i punkty bezpieczeństwa](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 W tym artykule opisano wątku zawieszenia i odzyskiwanie pamięci.  
  
 [Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 W tym artykule opisano mechanizmy magazynu powiązane z wątkiem.  
  
 [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 Opisuje sposób asynchronicznego lub długotrwałe operacje synchroniczne mogą zostać anulowane za pomocą token anulowania.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Threading.Thread>  
 Zawiera dokumentacja referencyjna dla **wątku** klasy, która reprezentuje zarządzanego wątku, czy pochodzi kodu niezarządzanego, lub został utworzony w zarządzanej aplikacji.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Zapewnia bezpieczny sposób do zaimplementowania wielowątkowości w połączeniu z obiektów interfejsu użytkownika.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 W tym artykule opisano klasy zarządzane używane do synchronizowania działania wiele wątków.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md)  
 W tym artykule opisano typowe problemy z wielowątkowość i strategii unikanie problemów.  
  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 Opisuje bibliotece równoległych zadań i PLINQ, co znacznie upraszcza pracy tworzenia aplikacji .NET Framework asynchroniczne i wielowątkowych.
