---
title: "Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a26f6750f68609b40e6917fc5b257e43d95c3c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a>Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach
Istnieje wiele sposobów, aby udostępnić funkcje asynchroniczne do kodu klienta. Asynchroniczny wzorzec oparty na zdarzeniach określa zalecany sposób klasy do prezentowania zachowanie asynchronicznego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 W tym artykule opisano, jak wzorca asynchronicznego opartego na zdarzeniach udostępnia zalety aplikacji wielowątkowych wiele złożonych problemów w wielowątkowe projektu są ukryte.  
  
 [Implementacja wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 Opisuje sposób Zestandaryzowany do pakietu klasy, która ma funkcje asynchroniczne.  
  
 [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Opisuje wymagania dotyczące udostępnianie funkcje asynchroniczne zgodnie ze wzorca asynchronicznego opartego na zdarzeniach.  
  
 [Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Opisuje sposób określania, kiedy użytkownik powinien wybrać implementacji wzorca asynchronicznego opartego na zdarzeniach zamiast <xref:System.IAsyncResult> wzorca.  
  
 [Wskazówki: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 Ilustruje sposób tworzenia składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach. Jest stosowana przy użyciu klasy pomocy z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw, który zapewnia składnika działa prawidłowo w dowolnej aplikacji modelu.  
  
 [Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Informacje dotyczące używania składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ComponentModel.AsyncOperation>  
 W tym artykule opisano <xref:System.ComponentModel.AsyncOperation> klasy i zawiera łącza do wszystkich jej członków.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 W tym artykule opisano <xref:System.ComponentModel.AsyncOperationManager> klasy i zawiera łącza do wszystkich jej członków.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 W tym artykule opisano <xref:System.ComponentModel.BackgroundWorker> części oraz zawiera łącza do wszystkich jej członków.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzana wątkowość — najlepsze praktyki](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Zdarzenia](../../../docs/standard/events/index.md)  
 [Wielowątkowość składników](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
