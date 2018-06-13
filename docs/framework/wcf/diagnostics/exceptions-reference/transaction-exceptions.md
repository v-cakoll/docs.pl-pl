---
title: Wyjątki dotyczące transakcji
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474834"
---
# <a name="transaction-exceptions"></a>Wyjątki dotyczące transakcji
Ten temat zawiera listę wszystkich wyjątków generowanych przez transakcję Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Informacje o zasadach, które zostały zaimportowane z metadanych określa różne wartości element TransactionProtocol między operacje. Obsługiwane jest tylko pojedynczy element TransactionProtocol dla każdego punktu końcowego.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Wartość TransactionAutoComplete nie może być fałszywa, chyba że właściwość InstanceContextMode usługi jest PerSession. Znaleziono błąd wykonania określonej kontrakt i operacja.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete może zostać wywołany w operacji tylko wtedy, gdy wartość TransactionAutoComplete jest ustawiona na false i wartością TransactionScopeRequired ma wartość true. Jest to nieprawidłowy scenariusz i bieżąca transakcja została przerwana.|  
|TransactionFlowRequiredIssuedTokens|Przepływ transakcji, musi być także obsługiwany przepływ wystawionych tokenów.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|Skonfigurowana wersja zaufania nie obsługuje wystawionych tokenów. Skorzystaj z wersji WSTrustFeb2005 lub nowszej.|
