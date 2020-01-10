---
title: Zdarzenia wyjątku ETW Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: 80faf6e607755ee79c7ec17f2d7d3d5bdce822b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716051"
---
# <a name="exception-thrown_v1-etw-event"></a>Zdarzenia wyjątku ETW Thrown_V1
To zdarzenie przechwytuje informacje o wygenerowanych wyjątkach.  
  
 W poniższej tabeli przedstawiono słowo kluczowe, pod którym zdarzenie jest zgłaszane, oraz poziom zdarzenia. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Ostrzeżenie (2)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniach.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Generowany jest wyjątek zarządzany.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Typ wyjątku|win: UnicodeString|Typ wyjątku; na przykład `System.NullReferenceException`.|  
|Komunikat o wyjątku|win: UnicodeString|Rzeczywisty komunikat o wyjątku.|  
|EIPCodeThrow|win: wskaźnik|Wskaźnik instrukcji, w którym wystąpił wyjątek.|  
|ExceptionHR|win: UInt32|Wyjątek [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).|  
|ExceptionFlags|Win: UInt16|0x01: HasInnerException (zobacz [zdarzenia ETW CLR](clr-etw-events.md) w dokumentacji Visual Basic).<br /><br /> 0x02: isnestexception.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (wskazuje, że stan procesu jest uszkodzony; zobacz [Obsługa wyjątków uszkodzonego stanu](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).<br /><br /> 0x10: IsCLSCompliant (wyjątek pochodzący z <xref:System.Exception> jest zgodny ze specyfikacją CLS; w przeciwnym razie nie jest zgodny ze specyfikacją CLS).|  
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
