---
title: Wyjątki dotyczące transakcji
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936984"
---
# <a name="transaction-exceptions"></a>Wyjątki dotyczące transakcji
Ten temat zawiera listę wszystkich wyjątków generowanych przez transakcję usługi Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Informacje o zasadach, które zostały zaimportowane z metadanych określa różne wartości element TransactionProtocol między operacji. Tylko pojedynczy element TransactionProtocol dla każdego punktu końcowego jest obsługiwane.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Wartość TransactionAutoComplete nie może mieć wartość false, chyba że właściwość InstanceContextMode usługi PerSession. Wykryto błąd wykonania określonego kontraktu i operacji.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete można wywołać w przypadku operacji tylko wtedy, gdy wartość TransactionAutoComplete jest ustawiona na false i TransactionScopeRequired jest ustawiona na wartość true. Jest to nieprawidłowy scenariusz, a bieżąca transakcja została przerwana.|  
|TransactionFlowRequiredIssuedTokens|Przepływ transakcji, musi być również obsługiwany przepływ wystawionych tokenów.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|Skonfigurowana wersja Trust nie obsługuje wystawionych tokenów. Skorzystaj z wersji WSTrustFeb2005 lub nowszej.|
