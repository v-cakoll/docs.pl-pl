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
ms.openlocfilehash: 951941af2568e72fe093860801bd2595b3037e41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428166"
---
# <a name="clr-etw-events"></a>Zdarzenia ETW CLR
W tematach w tej sekcji opisano zdarzenia śledzenia zdarzeń systemu Windows (ETW). Każde zdarzenie ma skojarzone słowo kluczowe i poziom, które są opisane w temacie [słowa kluczowe ETW środowiska CLR i poziomy](clr-etw-keywords-and-levels.md) . Środowisko CLR ma dwóch dostawców dla zdarzeń:  
  
- Dostawca środowiska uruchomieniowego, który wywołuje zdarzenia w zależności od tego, które słowa kluczowe (kategorie zdarzeń) są włączone. Identyfikator GUID dostawcy środowiska uruchomieniowego CLR to e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
- Dostawca uwalniania, który ma specjalne zastosowania. Identyfikator GUID dostawcy uwalniania CLR to a669021c-c450-4609-a035-5af59af4df18.  
  
 Więcej informacji o dostawcach znajduje się w temacie [dostawcy CLR ETW](clr-etw-providers.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Informacje o zdarzeniach środowiska uruchomieniowego](runtime-information-etw-events.md)  
 Przechwytuje informacje o środowisku uruchomieniowym, w tym jednostkę SKU, numer wersji, sposób aktywowania środowiska uruchomieniowego, parametry wiersza polecenia, które zostały uruchomione, identyfikator GUID (jeśli dotyczy) i inne istotne informacje.  
  
 [Zdarzenie wyjątku ETW Thrown_V1](exception-thrown-v1-etw-event.md)  
 Przechwytuje informacje o wygenerowanych wyjątkach.  
  
 [Zdarzenia rywalizacji](contention-etw-events.md)  
 Przechwytuje informacje o rywalizacji o blokady monitora lub blokady natywne używane przez środowisko uruchomieniowe.  
  
 [Zdarzenia puli wątków](thread-pool-etw-events.md)  
 Przechwytuje informacje o pulach wątków roboczych i pulach wątków we/wy.  
  
 [Zdarzenia modułu ładującego](loader-etw-events.md)  
 Przechwytuje informacje dotyczące ładowania i zwalniania domen aplikacji, zestawów i modułów.  
  
 [Zdarzenia metod](method-etw-events.md)  
 Przechwytuje informacje o metodach CLR rozpoznawania symboli.  
  
 [Zdarzenia odzyskiwania pamięci](garbage-collection-etw-events.md)  
 Przechwytuje informacje dotyczące wyrzucania elementów bezużytecznych, aby ułatwić diagnostykę i debugowanie.  
  
 [Zdarzenia śledzenia JIT](jit-tracing-etw-events.md)  
 Przechwytuje informacje o wywołaniach deokładzinowych i końcowych just-in-Time (JIT).  
  
 [Zdarzenia międzyoperacyjności](interop-etw-events.md)  
 Przechwytuje informacje o generacji i buforowaniu klasy języka pośredniego firmy Microsoft (MSIL).  
  
 [Zdarzenia ARM](application-domain-resource-monitoring-arm-etw-events.md)  
 Przechwytuje szczegółowe informacje diagnostyczne o stanie domeny aplikacji.  
  
 [Zdarzenia zabezpieczeń](security-etw-events.md)  
 Przechwytuje informacje o silnych nazwach i weryfikacji Authenticode.  
  
 [Zdarzenie stosu](stack-etw-event.md)  
 Przechwytuje informacje, które są używane z innymi zdarzeniami do generowania śladów stosu po podniesieniu zdarzenia.  
  
## <a name="see-also"></a>Zobacz także

- [Ulepszanie debugowania i dostrajania wydajności za pomocą funkcji ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [Blog o wydajności systemu Windows](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/)
- [Kontrolowanie logowania w programie .NET Framework](controlling-logging.md)
- [Dostawcy CLR ETW](clr-etw-providers.md)
- [Słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)
- [Zdarzenia ETW w środowisku CLR](etw-events-in-the-common-language-runtime.md)
