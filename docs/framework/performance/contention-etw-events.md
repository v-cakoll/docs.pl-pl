---
title: Zdarzenia rywalizacji ETW
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90beb1487581ff4c031d6f10fb613430207dc026
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575570"
---
# <a name="contention-etw-events"></a>Zdarzenia rywalizacji ETW
Zdarzenia rywalizacji o zasoby są wywoływane zawsze wtedy, gdy istnieje rywalizacji o <xref:System.Threading.Monitor?displayProperty=nameWithType> blokad lub natywnych blokady używany przez środowisko uruchomieniowe. Rywalizacji występuje, gdy wątek jest oczekiwanie na blokadę, podczas gdy inny wątek posiada blokadę.  
  
 W poniższej tabeli przedstawiono — słowo kluczowe, w którym są generowane zdarzenia rywalizacji o zasoby i poziom zdarzenia. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ContentionKeyword` (0x4000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|Rozpoczyna się rywalizacji o zasoby. To zdarzenie nie zawiera ilość obrotowych czas, po którym wątek czeka na uzyskanie blokady; jest zgłaszany tylko wtedy, gdy wątek czeka na uzyskanie blokady.|  
|`ContentionStop`|81|Kończy się rywalizacji o zasoby.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Flagi|win:UInt8|0 w przypadku zarządzanych; 1 w przypadku natywnych.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR.|  
  
## <a name="see-also"></a>Zobacz także
- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
