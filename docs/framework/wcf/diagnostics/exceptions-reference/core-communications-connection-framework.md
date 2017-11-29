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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c485c05c1c54a19a102a8378dc79c908a29aa658
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
