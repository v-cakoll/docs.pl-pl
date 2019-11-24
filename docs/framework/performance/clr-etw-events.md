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
The topics in this section describe event tracing for Windows (ETW) events. Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic. The CLR has two providers for the events:  
  
- The runtime provider, which raises events depending on which keywords (categories of events) are enabled. The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
- The rundown provider, which has special-purpose uses. The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.  
  
 For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Informacje o zdarzeniach środowiska uruchomieniowego](runtime-information-etw-events.md)  
 Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.  
  
 [Zdarzenie wyjątku ETW Thrown_V1](exception-thrown-v1-etw-event.md)  
 Captures information about exceptions that are thrown.  
  
 [Zdarzenia rywalizacji](contention-etw-events.md)  
 Captures information about contention for monitor locks or native locks that the runtime uses.  
  
 [Zdarzenia puli wątków](thread-pool-etw-events.md)  
 Captures information about worker thread pools and I/O thread pools.  
  
 [Zdarzenia modułu ładującego](loader-etw-events.md)  
 Captures information about loading and unloading application domains, assemblies, and modules.  
  
 [Zdarzenia metod](method-etw-events.md)  
 Captures information about CLR methods for symbol resolution.  
  
 [Zdarzenia odzyskiwania pamięci](garbage-collection-etw-events.md)  
 Captures information pertaining to garbage collection, to help in diagnostics and debugging.  
  
 [Zdarzenia śledzenia JIT](jit-tracing-etw-events.md)  
 Captures information about just-in-time (JIT) inlining and tail calls.  
  
 [Zdarzenia międzyoperacyjności](interop-etw-events.md)  
 Captures information about Microsoft intermediate language (MSIL) stub generation and caching.  
  
 [Zdarzenia ARM](application-domain-resource-monitoring-arm-etw-events.md)  
 Captures detailed diagnostic information about the state of an application domain.  
  
 [Zdarzenia zabezpieczeń](security-etw-events.md)  
 Captures information about strong name and Authenticode verification.  
  
 [Zdarzenie stosu](stack-etw-event.md)  
 Captures information that is used with other events to generate stack traces after an event is raised.  
  
## <a name="see-also"></a>Zobacz także

- [Improve Debugging And Performance Tuning With ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [Windows Performance Blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/)
- [Kontrolowanie logowania w programie .NET Framework](controlling-logging.md)
- [Dostawcy CLR ETW](clr-etw-providers.md)
- [Słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)
- [Zdarzenia ETW w środowisku CLR](etw-events-in-the-common-language-runtime.md)
