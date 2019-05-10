---
title: Zarządzana wątkowość — podstawy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b352c35a327ed4736a1f41816d3f15c1a0f559f5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644822"
---
# <a name="managed-threading-basics"></a>Zarządzana wątkowość — podstawy

Pięciu pierwszych tematach w tej sekcji mają ułatwić ustalenie, kiedy używać zarządzanych wątkach i wyjaśnić niektóre podstawowe funkcje. Aby uzyskać informacji na temat klas, które zapewniają dodatkowe funkcje, zobacz [wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md) i [Przegląd podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Pozostałe tematy w tej sekcji cover zaawansowane tematy, w tym interakcję zarządzanych wątkach w systemie operacyjnym Windows.  
  
> [!NOTE]
>  W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], bibliotece równoległych zadań i PLINQ zapewniają interfejsy API równoległość zadań i danych w programach wielowątkowych. Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji

 [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)  
 W tym artykule omówiono zalety i wady wielu wątków i opisano scenariusze, w których może utworzyć wątków lub użyj wątków z puli wątków.  
  
 [Wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 W tym artykule opisano zachowanie nieobsługiwanych wyjątków w wątkach dla różnych wersji programu .NET Framework, w szczególności sytuacje, w której powodują one zakończeniu działania aplikacji.  
  
 [Synchronizowanie danych na potrzeby wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 W tym artykule opisano strategie synchronizowanie danych w klasach, które będą używane w wielu wątkach.  
  
 [Wątki pierwszego planu i tła](../../../docs/standard/threading/foreground-and-background-threads.md)  
 W tym artykule wyjaśniono różnice między wątki pierwszego planu i tła.  
  
 [Zarządzana i niezarządzana wątkowość w systemie Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Związek między zarządzana i niezarządzana wątkowość, zawiera listę zarządzanych odpowiedników dla Windows wątkowości interfejsów API, a w tym artykule omówiono interakcji apartamentach COM i zarządzanych wątków.  
  
 [Lokalny magazyn wątków: Względne wątkom pola statyczne i gniazda danych](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 W tym artykule opisano mechanizmy względne wątkom magazynu.  
  
 [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 W tym artykule opisano sposób asynchronicznego lub długotrwałe operacje synchroniczne można anulować przy użyciu tokenu anulowania.  
  
## <a name="reference"></a>Tematy pomocy

 <xref:System.Threading.Thread>  
 Zawiera dokumentację referencyjną dla **wątku** klasy, która reprezentuje wątków zarządzanych, czy pochodzi z niezarządzanego kodu, czy został utworzony w zarządzanej aplikacji.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Zapewnia bezpieczny sposób implementacji wielowątkowości w połączeniu z obiektami interfejsu użytkownika.  
  
## <a name="related-sections"></a>Sekcje pokrewne

 [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Zawiera opis klas zarządzanych, używane do synchronizowania działania wielu wątków.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md)  
 W tym artykule opisano typowe problemy z usługą wielowątkowości i strategii unikanie problemów.  
  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 W tym artykule opisano bibliotece równoległych zadań i PLINQ, które znacznie upraszczają pracę tworzenie wielowątkowych i asynchronicznego aplikacji programu .NET Framework.
