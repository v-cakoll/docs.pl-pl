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
ms.openlocfilehash: f55057e40a251be49898b9b1b7862bd243b2a70c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913185"
---
# <a name="managed-threading-basics"></a>Zarządzane wątki — podstawy

Pięć pierwszych tematów tej sekcji zaprojektowano w celu ułatwienia ustalenia, kiedy należy używać zarządzanych wątków i wyjaśnić niektóre podstawowe funkcje. Aby uzyskać informacje na temat klas, które udostępniają dodatkowe funkcje, zobacz temat [wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md) oraz [Przegląd elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 W pozostałych tematach w tej sekcji omówiono zaawansowane tematy, w tym interakcje zarządzanej wątkowości z systemem operacyjnym Windows.  
  
> [!NOTE]
> W .NET Framework 4, Biblioteka zadań równoległych i PLINQ zapewniają interfejsy API do równoległych zadań i danych w programach wielowątkowych. Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji

 [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)  
 W tym artykule omówiono zalety i wady wielu wątków oraz opisano scenariusze, w których można tworzyć wątki lub używać wątków puli wątków.  
  
 [Wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Opisuje zachowanie nieobsłużonych wyjątków w wątkach dla różnych wersji .NET Framework, w szczególności sytuacje, w których powodują zakończenie działania aplikacji.  
  
 [Synchronizowanie danych na potrzeby wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Opisuje strategie synchronizowania danych w klasach, które będą używane z wieloma wątkami.  
  
 [Wątki pierwszego planu i tła](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Wyjaśnia różnice między wątkami na pierwszym planie i w tle.  
  
 [Zarządzana i niezarządzana wątkowość w systemie Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 W tym artykule omówiono relacje między zarządzaną i niezarządzaną wielowątkowością, listę zarządzanych odpowiedników interfejsów API wątków systemu Windows i omówiono interakcję apartamentach COM i zarządzanych wątków.  
  
 [Lokalny magazyn wątków: Pola statyczne powiązane z wątkiem i gniazda danych](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Opisuje mechanizmy przechowywania względem wątków.  
  
## <a name="reference"></a>Tematy pomocy

 <xref:System.Threading.Thread>  
 Zawiera dokumentację referencyjną dla klasy **wątku** , która reprezentuje wątek zarządzany, niezależnie od tego, czy pochodzi ona z kodu niezarządzanego, czy też została utworzona w zarządzanej aplikacji.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Zapewnia bezpieczny sposób implementacji wielowątkowości w połączeniu z obiektami interfejsu użytkownika.  
  
## <a name="related-sections"></a>Sekcje pokrewne

 [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Opisuje zarządzane klasy używane do synchronizowania działań wielu wątków.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Opisuje typowe problemy związane z wielowątkowością i strategiami w celu uniknięcia problemów.  
  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 Opisuje bibliotekę zadań równoległych i PLINQ, co znacznie upraszcza pracę tworzenia asynchronicznych i wielowątkowych aplikacji .NET Framework.
