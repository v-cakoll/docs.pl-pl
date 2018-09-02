---
title: Zdarzenia ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 983c38567667da911132217dcfda37c009dc833c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423488"
---
# <a name="clr-etw-events"></a>Zdarzenia ETW CLR
W tematach w tej sekcji opisano śledzenie zdarzeń systemu Windows (ETW) zdarzenia. Każde zdarzenie ma skojarzone słowo kluczowe i poziomu, które są opisane w [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) tematu. Środowisko CLR ma dwóch dostawców na potrzeby zdarzeń:  
  
-   Dostawca środowiska uruchomieniowego wywołuje zdarzenia, w zależności od tego, które są włączone słów kluczowych (kategorie zdarzeń). Identyfikator GUID dostawcy środowiska uruchomieniowego CLR to e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
-   Dostawca podsumowań, który ma zastosowań specjalnych. Identyfikator GUID dostawcy podsumowań CLR jest a669021c-c450-4609-a035-5af59af4df18.  
  
 Aby uzyskać więcej informacji na temat dostawców zobacz [dostawcy ETW CLR](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Informacje o zdarzeniach środowiska uruchomieniowego](../../../docs/framework/performance/runtime-information-etw-events.md)  
 Rejestruje informacje o środowisku uruchomieniowym jednostki SKU i numer wersji, w taki sposób, w którym został aktywowany środowiska uruchomieniowego, w tym parametry wiersza polecenia, który został uruchomiony przy użyciu identyfikatora GUID (jeśli dotyczy) oraz inne istotne informacje.  
  
 [Zdarzenie wyjątku ETW Thrown_V1](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Znajdują się informacje dotyczące wyjątków, które są generowane.  
  
 [Zdarzenia rywalizacji](../../../docs/framework/performance/contention-etw-events.md)  
 Przechwytuje informacje o Rywalizacja o blokady monitora lub natywnych blokad, których używa środowiska uruchomieniowego.  
  
 [Zdarzenia puli wątków](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Przechwytuje informacji na temat pul wątków procesów roboczych i pul wątków We/Wy.  
  
 [Zdarzenia modułu ładującego](../../../docs/framework/performance/loader-etw-events.md)  
 Przechwytuje informacje dotyczące ładowanie i zwalnianie domen aplikacji, zestawów i modułów.  
  
 [Zdarzenia metod](../../../docs/framework/performance/method-etw-events.md)  
 Przechwytuje informacje o metodach CLR dla rozpoznawania symboli.  
  
 [Zdarzenia odzyskiwania pamięci](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Przechwytuje informacje dotyczące wyrzucania elementów bezużytecznych, aby pomóc w Diagnostyka i debugowanie.  
  
 [Zdarzenia śledzenia JIT](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Przechwytuje informacje dotyczące just-in-time (JIT) wbudowanie i wywołania zakończenia.  
  
 [Zdarzenia międzyoperacyjności](../../../docs/framework/performance/interop-etw-events.md)  
 Przechwytuje informacje dotyczące generowania szkieletu intermediate language (MSIL) firmy Microsoft i buforowania.  
  
 [Zdarzenia ARM](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Przechwytywanie szczegółowych informacji diagnostycznych o stanie domeny aplikacji.  
  
 [Zdarzenia zabezpieczeń](../../../docs/framework/performance/security-etw-events.md)  
 Przechwytuje informacje o silnej nazwie i weryfikacji Authenticode.  
  
 [Zdarzenie stosu](../../../docs/framework/performance/stack-etw-event.md)  
 Przechwytuje informacje, które jest używany z innymi zdarzeniami można wygenerować ślady stosu, po wydarzenie jest podniesione.  
  
## <a name="see-also"></a>Zobacz też  
 [Poprawić debugowania i dostrajania wydajności za pomocą funkcji ETW](https://go.microsoft.com/fwlink/?LinkId=179696)  
 [Blog poświęcony wydajności Windows](https://go.microsoft.com/fwlink/?LinkId=179509)  
 [Kontrolowanie logowania w programie .NET Framework](../../../docs/framework/performance/controlling-logging.md)  
 [Dostawcy CLR ETW](../../../docs/framework/performance/clr-etw-providers.md)  
 [Słowa kluczowe i poziomy ETW CLR](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [Zdarzenia ETW w środowisku CLR](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
