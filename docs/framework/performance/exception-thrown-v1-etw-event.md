---
title: "Zdarzenia wyjątku ETW Thrown_V1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60013d0df8c63033f6da8d61479bacac7b944094
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="exception-thrownv1-etw-event"></a>Zdarzenia wyjątku ETW Thrown_V1
To zdarzenie znajdują się informacje dotyczące wyjątków, które są zgłaszane.  
  
 W poniższej tabeli przedstawiono — słowo kluczowe, w którym zdarzenie jest zgłaszane, a poziom zdarzenia. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ExceptionKeyword`(0x8000)|Ostrzeżenie (2)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniach.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Zarządzanych wyjątku.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Typ wyjątku|Windows: UnicodeString|Typ wyjątku; na przykład `System.NullReferenceException`.|  
|Komunikat o wyjątku|Windows: UnicodeString|Komunikat o wyjątku rzeczywistych.|  
|EIPCodeThrow|Windows: wskaźnik|Wskaźnik instrukcji, w którym wyjątek wystąpił.|  
|ExceptionHR|Windows: UInt32.|Wyjątek [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).|  
|ExceptionFlags|Windows: UInt16|0x01: HasInnerException (zobacz [zdarzenia ETW CLR](../../../docs/framework/performance/clr-etw-events.md) w dokumentacji programu Visual Basic).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (wskazuje, że stan procesu jest uszkodzony; zobacz [obsługi wyjątków stan uszkodzony](http://go.microsoft.com/fwlink/?LinkId=179681) w witrynie MSDN).<br /><br /> 0x10: IsCLSCompliant (wyjątek, która jest pochodną <xref:System.Exception> zgodne ze specyfikacją CLS, a w przeciwnym razie nie jest zgodne ze specyfikacją CLS).|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
