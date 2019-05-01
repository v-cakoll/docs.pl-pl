---
title: 'Komunikacja podstawowa: Struktura połączenia'
ms.date: 03/30/2017
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
ms.openlocfilehash: a3f52ac82c2bf09ded504e412d7f216dd0b39959
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998689"
---
# <a name="core-communications-connection-framework"></a>Komunikacja podstawowa: Struktura połączenia
Ten temat zawiera listę wszystkich wyjątków generowanych przez struktura połączenia usług Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|CloseTimedOut|Close — metoda, upłynął limit czasu po określonym czasie. Zwiększ wartość limitu czasu, który jest przekazywany do wywołaniu Close lub wartość CloseTimeout w obiekcie w powiązaniu. Czas przydzielony na tę operację mógł stanowić część większego limitu czasu.|  
|ContentTypeMismatch|Określony typ zawartości został wysłany do usługi, która oczekiwała na określony. Powiązania klienta i usługi mogą być niezgodne.|  
|DuplexChannelAbortedDuringOpen|Kanał dupleksowy do określonego została zakończona podczas procesu otwierania.|  
|FramingValueNotAvailable|Wartość nie jest dostępny, ponieważ nie jest w pełni zdekodowane.|  
|OperationAbortedDuringConnectionEstablishment|Operacja została zakończona podczas nawiązywania połączenia z określonym.|  
|ReceiveTimedOut2|Operacja odbioru został przekroczony po określonym czasie. Czas przydzielony na tę operację mógł stanowić część większego limitu czasu.|  
|SendCannotBeCalledAfterCloseOutputSession|Nie można wysłać wiadomości na kanale, po wywołaniu CloseOutputSession.|
