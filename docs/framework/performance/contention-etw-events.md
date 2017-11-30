---
title: Zdarzenia rywalizacji ETW
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d739eaf73ff8336e74130d7176697229fdffd12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="contention-etw-events"></a>Zdarzenia rywalizacji ETW
Zdarzenia rywalizacji są wywoływane zawsze, gdy w przypadku konfliktu między <xref:System.Threading.Monitor?displayProperty=nameWithType> blokady lub blokad natywnego używane przez środowisko uruchomieniowe. Gdy wątek oczekuje na blokadę, podczas gdy inny wątek posiada blokady wystąpienia rywalizacji.  
  
 W poniższej tabeli przedstawiono — słowo kluczowe, w którym są wywoływane zdarzenia rywalizacji i poziom zdarzenia. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ContentionKeyword`(0x4000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniach.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|Uruchamia rywalizacji. To zdarzenie nie zawiera ilość wirowania przed wątek oczekuje na uzyskanie blokady; jest on wywoływane tylko wtedy, gdy wątek oczekuje na uzyskanie blokady.|  
|`ContentionStop`|81|Kończy się rywalizacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Flagi|Windows: UInt8|zarządzane 0; 1 w przypadku natywnego.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia środowiska CLR.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
