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
ms.openlocfilehash: bec769043ab630b37609bed12302ceff5b90474a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139227"
---
# <a name="managed-threading-basics"></a>Podstawy wątków zarządzanych

Pierwsze pięć tematów tej sekcji zostały zaprojektowane, aby ułatwić określenie, kiedy używać zarządzanych wątków i wyjaśnić niektóre podstawowe funkcje. Aby uzyskać informacje na temat klas, które zapewniają dodatkowe funkcje, zobacz [Threading obiekty i funkcje](../../../docs/standard/threading/threading-objects-and-features.md) i [Omówienie podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Pozostałe tematy w tej sekcji obejmują zaawansowane tematy, w tym interakcję zarządzanego wątków z systemem operacyjnym Windows.  
  
> [!NOTE]
> W .NET Framework 4 Biblioteka równoległa zadań i PLINQ zapewniają interfejsy API dla równoległości zadań i danych w programach wielowątkowych. Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji

 [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)  
 W tym artykule omówiono zalety i wady wielu wątków i przedstawia scenariusze, w których można utworzyć wątki lub użyć wątków puli wątków.  
  
 [Wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Opisuje zachowanie nieobsługiwanych wyjątków w wątkach dla różnych wersji programu .NET Framework, w szczególności sytuacje, w których powodują one zakończenie aplikacji.  
  
 [Synchronizowanie danych na potrzeby wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 W tym artykule opisano strategie synchronizowania danych w klasach, które będą używane z wieloma wątkami.  
  
 [Wątki pierwszego planu i tła](../../../docs/standard/threading/foreground-and-background-threads.md)  
 W tym artykule wyjaśniono różnice między wątkami pierwszego planu i tła.  
  
 [Zarządzana i niezarządzana wątkowość w systemie Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 W tym artykule omówiono relację między zarządzanym i niezarządzanym wątkowaniem, wyświetla listę zarządzanych odpowiedników interfejsów API wątków systemu Windows i omówiono interakcję apartamentów COM i wątków zarządzanych.  
  
 [Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Opisuje mechanizmy magazynu względnego wątku.  
  
## <a name="reference"></a>Dokumentacja

 <xref:System.Threading.Thread>  
 Zawiera dokumentację referencyjną dla **Thread** klasy, która reprezentuje wątek zarządzany, czy pochodzi z kodu niezarządzanego lub został utworzony w aplikacji zarządzanej.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Zapewnia bezpieczny sposób implementowania wielowątkowości w połączeniu z obiektami interfejsu użytkownika.  
  
## <a name="related-sections"></a>Sekcje pokrewne

 [Omówienie elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Opisuje klasy zarządzane używane do synchronizowania działań wielu wątków.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Opisuje typowe problemy z wielowątkowości i strategii unikania problemów.  
  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 Opisuje bibliotekę równoległą zadania i PLINQ, które znacznie upraszczają pracę tworzenia aplikacji asynchronicznych i wielowątkowych .NET Framework.
