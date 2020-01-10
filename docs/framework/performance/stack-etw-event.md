---
title: Zdarzenie ETW stosu
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: f3014a04ba7cacbe37b6706e2919ffd7de19aa65
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715909"
---
# <a name="stack-etw-event"></a>Zdarzenie ETW stosu
Zdarzenia stosu należy używać w połączeniu z innymi zdarzeniami w celu generowania śladów stosu po podniesieniu zdarzenia. Jest on rejestrowany po włączeniu dostawcy środowiska uruchomieniowego. Jest to zdarzenie o dużej częstotliwości, ponieważ jest zgłaszane przy każdym wywołaniu innego zdarzenia środowiska uruchomieniowego. Z tego powodu zaleca się użycie tego zdarzenia z zachowaniem ostrożności.  
  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways (0)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|W połączeniu z innymi zdarzeniami do generowania śladów stosu po zdarzeniu.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator środowiska uruchomieniowego.|  
|Reserved1|win: UInt8|Rezerwacj.|  
|Reserved2|win: UInt8|Rezerwacj.|  
|FrameCount|win: UInt32|Liczba ramek w śladzie stosu.|  
|Stos|win: wskaźnik|Kolumny wskaźników instrukcji.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
