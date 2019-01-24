---
title: Zdarzenia wyjątku ETW Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07932a12916138dd7cbee2576e4fc747898b8063
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610853"
---
# <a name="exception-thrownv1-etw-event"></a>Zdarzenia wyjątku ETW Thrown_V1
To zdarzenie znajdują się informacje dotyczące wyjątków, które są generowane.  
  
 W poniższej tabeli przedstawiono — słowo kluczowe, w którym zdarzenie jest wywoływane, a poziom zdarzenia. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Ostrzeżenie (2)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Zarządzane wyjątek jest generowany.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Typ wyjątku|win:UnicodeString|Typ wyjątku; na przykład `System.NullReferenceException`.|  
|Komunikat o wyjątku|win:UnicodeString|Komunikat o wyjątku rzeczywistych.|  
|EIPCodeThrow|win: wskaźnik|Wskaźnik instrukcji, w którym wyjątek wystąpił.|  
|ExceptionHR|win: UInt32.|Wyjątek [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).|  
|ExceptionFlags|win: UInt16.|0x01: HasInnerException (zobacz [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) w dokumentacji języka Visual Basic).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (wskazuje, że stan procesu jest uszkodzony; zobacz [obsługi wyjątków stan uszkodzony](https://go.microsoft.com/fwlink/?LinkId=179681) w witrynie MSDN).<br /><br /> 0x10: IsCLSCompliant (wyjątek, który pochodzi od klasy <xref:System.Exception> jest zgodny ze specyfikacją CLS; w przeciwnym razie nie jest zgodny ze specyfikacją CLS).|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
## <a name="see-also"></a>Zobacz także
- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
