---
title: "Wyjątki dotyczące transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f13a39c251afd55dbb1f0d2dde4fc66fe38d30a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-exceptions"></a>Wyjątki dotyczące transakcji
W tym temacie wymieniono wszystkie wyjątki generowane przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] transakcji.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Informacje o zasadach, które zostały zaimportowane z metadanych określa różne wartości element TransactionProtocol między operacje. Obsługiwane jest tylko pojedynczy element TransactionProtocol dla każdego punktu końcowego.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Wartość TransactionAutoComplete nie może być fałszywa, chyba że właściwość InstanceContextMode usługi jest PerSession. Znaleziono błąd wykonania określonej kontrakt i operacja.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete może zostać wywołany w operacji tylko wtedy, gdy wartość TransactionAutoComplete jest ustawiona na false i wartością TransactionScopeRequired ma wartość true. Jest to nieprawidłowy scenariusz i bieżąca transakcja została przerwana.|  
|TransactionFlowRequiredIssuedTokens|Przepływ transakcji, musi być także obsługiwany przepływ wystawionych tokenów.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|Skonfigurowana wersja zaufania nie obsługuje wystawionych tokenów. Skorzystaj z wersji WSTrustFeb2005 lub nowszej.|
