---
title: Asynchroniczny wzorzec oparty na zdarzeniach (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: ee8c90d63478e444b7d25cb7cbb5c969963d7c63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130942"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Asynchroniczny wzorzec oparty na zdarzeniach (EAP)

Istnieje wiele sposobów, aby udostępnić funkcje asynchroniczne do kodu klienta. Wzorzec asynchroniczny oparty na zdarzeniach zaleca jeden sposób dla klas do przedstawienia zachowania asynchronicznego.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, biblioteka równoległa zadania zapewnia nowy model programowania asynchronicznego i równoległego. Aby uzyskać więcej informacji, zobacz [Biblioteka równoległa zadań (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [Asynchroniczny wzorzec (TAP) oparty na zadaniach](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>W tej sekcji

 [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](event-based-asynchronous-pattern-overview.md)  
 Opisuje, jak oparty na zdarzeniach wzorzec asynchroniczny udostępnia zalety aplikacji wielowątkowych, ukrywając wiele złożonych problemów związanych z projektem wielowątkowym.  
  
 [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](implementing-the-event-based-asynchronous-pattern.md)  
 W tym artykule opisano znormalizowany sposób pakowania klasy, która ma funkcje asynchroniczne.  
  
 [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 W tym artykule opisano wymagania dotyczące ujawniania obiektów asynchronicznych zgodnie z wzorcem asynchronicznym opartym na zdarzeniach.  
  
 [Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 W tym artykule opisano, jak określić, kiedy należy zaimplementować <xref:System.IAsyncResult> wzorzec asynchroniczny oparty na zdarzeniach, a nie wzorzec reprezentowany przez [asynchroniczny model programowania (APM)](asynchronous-programming-model-apm.md)
  
 [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Opisuje sposób tworzenia składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach. Jest implementowany przy użyciu klas <xref:System.ComponentModel?displayProperty=nameWithType> pomocnika z obszaru nazw, który zapewnia, że składnik działa poprawnie w dowolnym modelu aplikacji.  

 [Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 W tym artykule opisano sposób tworzenia klienta, który używa składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach.
  
 [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Opisuje sposób używania składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach.  
  
## <a name="reference"></a>Dokumentacja

 <xref:System.ComponentModel.AsyncOperation>  
 Opisuje <xref:System.ComponentModel.AsyncOperation> klasę i zawiera łącza do wszystkich jej członków.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Opisuje <xref:System.ComponentModel.AsyncOperationManager> klasę i zawiera łącza do wszystkich jej członków.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Opisuje <xref:System.ComponentModel.BackgroundWorker> składnik i zawiera łącza do wszystkich jego elementów członkowskich.  
  
## <a name="related-sections"></a>Sekcje pokrewne

 [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Opisuje model programowania dla operacji asynchronicznych i równoległych.  
  
 [Wątków](../../../docs/standard/threading/index.md)  
 Opisuje funkcje wielowątkowości w platformie .NET.  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzana wątkowość — najlepsze rozwiązania](../threading/managed-threading-best-practices.md)
- [Zdarzenia](../events/index.md)
- [Wzorce projektowania programowania asynchronicznego](index.md)
