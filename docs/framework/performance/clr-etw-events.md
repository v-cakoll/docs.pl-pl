---
title: Zdarzenia ETW CLR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d0619388b429bd1824a62bc29ccb222eea1ffde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="clr-etw-events"></a>Zdarzenia ETW CLR
W tematach w tej sekcji opisano zdarzenia śledzenia dla zdarzeń systemu Windows (ETW). Każde zdarzenie ma skojarzone — słowo kluczowe i poziomu, które są opisane w [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) tematu. Środowisko CLR ma dwóch dostawców na potrzeby zdarzenia:  
  
-   Dostawcy środowiska uruchomieniowego, który informuje o zdarzeniach, w zależności od tego, które są włączone słowa kluczowe (kategorie zdarzeń). Dostawca środowiska uruchomieniowego CLR identyfikator GUID jest e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
-   Używa stert dostawcy, który ma specjalnych. Dostawca stert CLR identyfikator GUID jest a669021c-c450-4609-a035-5af59af4df18.  
  
 Aby uzyskać więcej informacji o dostawcach, zobacz [dostawcy ETW CLR](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Środowisko uruchomieniowe informacje o zdarzeniach](../../../docs/framework/performance/runtime-information-etw-events.md)  
 Przechwytuje informacji na temat środowiska uruchomieniowego, jednostka SKU, numer wersji, sposób, w którym środowiska wykonawczego został aktywowany, w tym parametry wiersza polecenia, który został uruchomiony z identyfikatorem GUID (jeśli dotyczy) oraz inne istotne informacje.  
  
 [Zdarzenie wyjątku ETW Thrown_V1](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Przechwytuje informacje dotyczące wyjątków, które są zgłaszane.  
  
 [Zdarzenia rywalizacji](../../../docs/framework/performance/contention-etw-events.md)  
 Przechwytuje informacje o rywalizacji blokad monitora lub blokad natywnego używane przez środowisko uruchomieniowe.  
  
 [Zdarzenia puli wątków](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Przechwytuje informacje o puli wątków roboczych i pule wątków We/Wy.  
  
 [Zdarzenia modułu ładującego](../../../docs/framework/performance/loader-etw-events.md)  
 Przechwytuje informacje dotyczące ładowanie i zwalnianie domen aplikacji, zestawów i modułów.  
  
 [Zdarzenia metod](../../../docs/framework/performance/method-etw-events.md)  
 Przechwytuje informacje o metodach CLR do rozpoznawania symboli.  
  
 [Zdarzenia wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Przechwytuje informacje dotyczące pamięci, aby pomóc w diagnostyki i debugowanie.  
  
 [Zdarzenia śledzenia JIT](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Przechwytuje informacje dotyczące just-in-time (JIT) ze śródwierszowaniem i wywołania tail.  
  
 [Zdarzenia międzyoperacyjności](../../../docs/framework/performance/interop-etw-events.md)  
 Przechwytuje informacje dotyczące generowania szkieletu język pośredni (MSIL) firmy Microsoft i buforowania.  
  
 [Zdarzenia ARM](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Przechwytywanie szczegółowe informacje diagnostyczne o stanie domeny aplikacji.  
  
 [Zdarzenia zabezpieczeń](../../../docs/framework/performance/security-etw-events.md)  
 Przechwytuje informacje o silnej nazwie i weryfikacji Authenticode.  
  
 [Zdarzenie stosu](../../../docs/framework/performance/stack-etw-event.md)  
 Przechwytuje informacje, które jest używany z innymi zdarzeniami do generowania ślady stosu, po wywołaniu zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Poprawa debugowania i dostrajania wydajności za pomocą funkcji ETW](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [Blog dotyczący wydajności systemu Windows](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [Kontrolowanie .NET Framework rejestrowania](../../../docs/framework/performance/controlling-logging.md)  
 [Dostawcy CLR ETW](../../../docs/framework/performance/clr-etw-providers.md)  
 [Słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [Zdarzenia ETW w środowisko uruchomieniowe języka wspólnego](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
