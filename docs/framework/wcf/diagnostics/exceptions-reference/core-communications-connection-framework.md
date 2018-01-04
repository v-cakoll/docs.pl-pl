---
title: "Podstawowe wiadomości: Struktura połączenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713788f8938e43f3516edd95646fc6dc653a56c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="core-communications-connection-framework"></a>Podstawowe wiadomości: Struktura połączenia
W tym temacie wymieniono wszystkie wyjątki generowane przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] struktura połączenia.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|CloseTimedOut|Close — metoda, przekroczono limit czasu po upływie określonego czasu. Zwiększ wartość limitu czasu przekazywaną w wywołaniu Close lub wartość CloseTimeout w obiekcie w powiązaniu. Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.|  
|ContentTypeMismatch|Określony typ zawartości został wysłany do usługi, która oczekiwała określony. Powiązania klienta i usługi mogą być niezgodne.|  
|DuplexChannelAbortedDuringOpen|Kanał dupleksowy do określonego została zakończona podczas procesu otwierania.|  
|FramingValueNotAvailable|Wartość nie jest dostępny, ponieważ nie jest całkowicie zdekodować.|  
|OperationAbortedDuringConnectionEstablishment|Operacja została zakończona podczas nawiązywania połączenia z określonym.|  
|ReceiveTimedOut2|Operacja odbioru został przekroczony po określonym czasie. Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.|  
|SendCannotBeCalledAfterCloseOutputSession|Nie można wysłać wiadomości kanałem po wywołaniu CloseOutputSession.|
