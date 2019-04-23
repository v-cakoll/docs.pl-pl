---
title: Zdarzenie ETW stosu
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7cba2bd1dd5b83e29c7a6c192a1a7e5e2d33ecc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076484"
---
# <a name="stack-etw-event"></a>Zdarzenie ETW stosu
Zdarzenie stosu powinny służyć w połączeniu z innymi zdarzeniami można wygenerować ślady stosu, po wydarzenie jest podniesione. Jest on rejestrowane, gdy jest włączony dostawca środowiska uruchomieniowego. To wydarzenie bardzo wysokiej częstotliwości, ponieważ jest zgłaszany w każdym przypadku, gdy inne zdarzenie środowiska wykonawczego jest wywoływane. Z tego powodu zaleca się używać tego wydarzenia z ostrożnością.  
  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways(0)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|W połączeniu z innymi zdarzeniami, aby wygenerować ślady stosu, następujące zdarzenie.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win: Uint16.|Identyfikator unikatowy środowiska uruchomieniowego.|  
|Reserved1|win:UInt8|Zastrzeżone.|  
|Zarezerwowane2|win:UInt8|Zastrzeżone.|  
|FrameCount|win: UInt32.|Liczba klatek ślad stosu.|  
|Stos|win: wskaźnik|Kolumny wskaźników instrukcji.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
