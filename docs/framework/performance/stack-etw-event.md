---
title: Zdarzenie ETW stosu
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 073622c22b957975ed799cf5b3bc3826473114b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396357"
---
# <a name="stack-etw-event"></a>Zdarzenie ETW stosu
Zdarzenie stosu stosuje się w połączeniu z innymi zdarzeniami, można wygenerować śladów stosu po wywołaniu zdarzenia. Jest on rejestrowane, gdy dostawca środowiska uruchomieniowego jest włączony. Jest to zdarzenie bardzo wysokiej częstotliwości, ponieważ jest wywoływane, gdy innego środowiska uruchomieniowego zdarzenia. Z tego powodu zaleca się, użyj tego zdarzenia z rozwagą.  
  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways(0)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|W połączeniu z innymi zdarzeniami, aby wygenerować ślady stosu, następujące zdarzenie.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Windows: Uint16|Środowisko uruchomieniowe Unikatowy identyfikator.|  
|Reserved1|Windows: UInt8|Zastrzeżone.|  
|Zarezerwowane2|Windows: UInt8|Zastrzeżone.|  
|Wartości FrameCount|Windows: UInt32.|Liczba ramek w ślad stosu.|  
|Stos|Windows: wskaźnik|Kolumny wskaźników instrukcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
