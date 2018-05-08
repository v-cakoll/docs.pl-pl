---
title: 'Podstawowe wiadomości: Struktura połączenia'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: a3f52ac82c2bf09ded504e412d7f216dd0b39959
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="core-communications-connection-framework"></a>Podstawowe wiadomości: Struktura połączenia
W tym temacie wymieniono wszystkie wyjątki generowane przez platformę połączenia usług Windows Communication Foundation (WCF).  
  
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
