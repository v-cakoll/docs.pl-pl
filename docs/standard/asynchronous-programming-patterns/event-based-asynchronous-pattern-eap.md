---
title: Asynchroniczny wzorzec oparty na zdarzeniach (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 604e7a944579a284004817009b06c11b268d5daf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289437"
---
# <a name="event-based-asynchronous-pattern-eap"></a>Asynchroniczny wzorzec oparty na zdarzeniach (EAP)

Istnieje wiele sposobów udostępniania funkcji asynchronicznych kodowi klienta. Wzorzec asynchroniczny oparty na zdarzeniach umożliwia jednokierunkową metodę prezentowania zachowań asynchronicznych.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, Biblioteka zadań równoległych udostępnia nowy model dla programowania asynchronicznego i równoległego. Aby uzyskać więcej informacji, zobacz [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [wzorzec asynchroniczny oparty na zadaniach (TAP)](task-based-asynchronous-pattern-tap.md).
  
## <a name="in-this-section"></a>W tej sekcji

 [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](event-based-asynchronous-pattern-overview.md)  
 Opisuje sposób, w jaki wzorzec asynchroniczny oparty na zdarzeniach udostępnia zalety aplikacji wielowątkowych, jednocześnie ukrywając wiele złożonych problemów niezależnych od projektów wielowątkowych.  
  
 [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](implementing-the-event-based-asynchronous-pattern.md)  
 Opisuje ustandaryzowany sposób spakowania klasy, która ma funkcje asynchroniczne.  
  
 [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Opisuje wymagania dotyczące uwidaczniania funkcji asynchronicznych zgodnie ze wzorcem asynchronicznym opartym na zdarzeniach.  
  
 [Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Opisuje, jak określić, kiedy należy wybrać implementację wzorca asynchronicznego opartego na zdarzeniach zamiast <xref:System.IAsyncResult> wzorca reprezentowanego przez [model programowania ASYNCHRONICZNEGO (APM)](asynchronous-programming-model-apm.md)
  
 [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](component-that-supports-the-event-based-asynchronous-pattern.md)  
 Opisuje sposób tworzenia składnika implementującego wzorzec asynchroniczny oparty na zdarzeniach. Jest implementowana przy użyciu klas pomocników z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw, co gwarantuje, że składnik działa prawidłowo w ramach dowolnego modelu aplikacji.  

 [Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 Opisuje sposób tworzenia klienta korzystającego ze składnika implementującego wzorzec asynchroniczny oparty na zdarzeniach.
  
 [Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Opisuje sposób użycia składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach.  
  
## <a name="reference"></a>Dokumentacja

 <xref:System.ComponentModel.AsyncOperation>  
 Opisuje <xref:System.ComponentModel.AsyncOperation> klasę i zawiera linki do wszystkich jej elementów członkowskich.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Opisuje <xref:System.ComponentModel.AsyncOperationManager> klasę i zawiera linki do wszystkich jej elementów członkowskich.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Opisuje <xref:System.ComponentModel.BackgroundWorker> składnik i zawiera linki do wszystkich jego członków.  
  
## <a name="related-sections"></a>Sekcje pokrewne

 [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 Opisuje model programowania dla operacji asynchronicznych i równoległych.  
  
 [Wątkowość](../threading/index.md)  
 Opisuje funkcje wielowątkowości w programie .NET.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzana wątkowość — najlepsze rozwiązania](../threading/managed-threading-best-practices.md)
- [Zdarzenia](../events/index.md)
- [Wzorce projektowania programowania asynchronicznego](index.md)
