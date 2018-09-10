---
title: Asynchroniczny wzorzec oparty na zdarzeniach (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be4935d74affa227386aa6c63dad13e7e2f7d3dd
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262649"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Asynchroniczny wzorzec oparty na zdarzeniach (EAP)

Istnieją różne sposoby do udostępnienia asynchronicznego cech dla kodu klienta. Asynchroniczny wzorzec oparty na zdarzeniach określa jeden ze sposobów dla klas przedstawić zachowanie asynchroniczne.  
  
> [!NOTE]
> Począwszy od programu .NET Framework 4 w bibliotece zadań równoległych przewiduje nowy model programowania asynchronicznego i równoległego. Aby uzyskać więcej informacji, zobacz [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [opartego na zadaniach asynchronicznej wzorca (TAP)](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>W tej sekcji

 [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](event-based-asynchronous-pattern-overview.md)  
 W tym artykule opisano, jak asynchroniczny wzorzec oparty na zdarzeniach udostępnia zalety aplikacji wielowątkowych wiele skomplikowane problemy związane z wielowątkowych projektu są ukryte.  
  
 [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](implementing-the-event-based-asynchronous-pattern.md)  
 W tym artykule opisano standardowy sposób pakietu klasę, która ma funkcje asynchroniczne.  
  
 [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 W tym artykule opisano wymagania dotyczące udostępniania funkcje asynchroniczne zgodnie z wzorca asynchronicznego opartego na zdarzeniach.  
  
 [Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Opisuje sposób określenia, kiedy należy wybrać implementacji wzorca asynchronicznego opartego na zdarzeniach — zamiast <xref:System.IAsyncResult> wzorzec reprezentowany przez [modelu programowania asynchronicznego (APM)](asynchronous-programming-model-apm.md)
  
 [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](component-that-supports-the-event-based-asynchronous-pattern.md)  
 W tym artykule opisano sposób tworzenia składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach. Jej implementacji przy użyciu klas pomocy z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeń nazw, która zapewnia składnika działa prawidłowo w ramach dowolnego modelu aplikacji.  

 [Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 W tym artykule opisano sposób tworzenia klienta, który używa składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach.
  
 [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Opisuje sposób używania składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach.  
  
## <a name="reference"></a>Tematy pomocy

 <xref:System.ComponentModel.AsyncOperation>  
 W tym artykule opisano <xref:System.ComponentModel.AsyncOperation> klasy i zawiera linki do wszystkich jej członków.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 W tym artykule opisano <xref:System.ComponentModel.AsyncOperationManager> klasy i zawiera linki do wszystkich jej członków.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 W tym artykule opisano <xref:System.ComponentModel.BackgroundWorker> składnika i zawiera linki do wszystkich jej członków.  
  
## <a name="related-sections"></a>Sekcje pokrewne

 [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 W tym artykule opisano model programowania dla operacji asynchronicznych i równoległych.  
  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 Opisuje funkcje wielowątkowości w środowisku .NET.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzana wątkowość — najlepsze rozwiązania](../threading/managed-threading-best-practices.md)  
- [Zdarzenia](../events/index.md)  
- [Wzorce projektowania programowania asynchronicznego](index.md)
