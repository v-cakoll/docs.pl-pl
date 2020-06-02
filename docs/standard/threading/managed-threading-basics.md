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
ms.openlocfilehash: 4d2a96619fd1c48c79b5590efdb52c307d29710c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291009"
---
# <a name="managed-threading-basics"></a>Zarządzane wątki — podstawy

Pięć pierwszych tematów tej sekcji zaprojektowano w celu ułatwienia ustalenia, kiedy należy używać zarządzanych wątków i wyjaśnić niektóre podstawowe funkcje. Aby uzyskać informacje na temat klas, które udostępniają dodatkowe funkcje, zobacz temat [wątkowość obiektów i funkcji](threading-objects-and-features.md) oraz [Przegląd elementów pierwotnych synchronizacji](overview-of-synchronization-primitives.md).  
  
 W pozostałych tematach w tej sekcji omówiono zaawansowane tematy, w tym interakcje zarządzanej wątkowości z systemem operacyjnym Windows.  
  
> [!NOTE]
> W .NET Framework 4, Biblioteka zadań równoległych i PLINQ zapewniają interfejsy API do równoległych zadań i danych w programach wielowątkowych. Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji

 [Wątki i wątkowość](threads-and-threading.md)  
 W tym artykule omówiono zalety i wady wielu wątków oraz opisano scenariusze, w których można tworzyć wątki lub używać wątków puli wątków.  
  
 [Wyjątki w zarządzanych wątkach](exceptions-in-managed-threads.md)  
 Opisuje zachowanie nieobsłużonych wyjątków w wątkach dla różnych wersji .NET Framework, w szczególności sytuacje, w których powodują zakończenie działania aplikacji.  
  
 [Synchronizowanie danych na potrzeby wielowątkowości](synchronizing-data-for-multithreading.md)  
 Opisuje strategie synchronizowania danych w klasach, które będą używane z wieloma wątkami.  
  
 [Wątki pierwszego planu i tła](foreground-and-background-threads.md)  
 Wyjaśnia różnice między wątkami na pierwszym planie i w tle.  
  
 [Zarządzana i niezarządzana wątkowość w systemie Windows](managed-and-unmanaged-threading-in-windows.md)  
 W tym artykule omówiono relacje między zarządzaną i niezarządzaną wielowątkowością, listę zarządzanych odpowiedników interfejsów API wątków systemu Windows i omówiono interakcję apartamentach COM i zarządzanych wątków.  
  
 [Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Opisuje mechanizmy przechowywania względem wątków.  
  
## <a name="reference"></a>Dokumentacja

 <xref:System.Threading.Thread>  
 Zawiera dokumentację referencyjną dla klasy **wątku** , która reprezentuje wątek zarządzany, niezależnie od tego, czy pochodzi ona z kodu niezarządzanego, czy też została utworzona w zarządzanej aplikacji.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Zapewnia bezpieczny sposób implementacji wielowątkowości w połączeniu z obiektami interfejsu użytkownika.  
  
## <a name="related-sections"></a>Sekcje pokrewne

 [Przegląd elementów podstawowych synchronizacji](overview-of-synchronization-primitives.md)  
 Opisuje zarządzane klasy używane do synchronizowania działań wielu wątków.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](managed-threading-best-practices.md)  
 Opisuje typowe problemy związane z wielowątkowością i strategiami w celu uniknięcia problemów.  
  
 [Programowanie równoległe](../parallel-programming/index.md)  
 Opisuje bibliotekę zadań równoległych i PLINQ, co znacznie upraszcza pracę tworzenia asynchronicznych i wielowątkowych aplikacji .NET Framework.
