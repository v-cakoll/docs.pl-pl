---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 027ace6ea9fc2a0e5ce63efa84e1a49c0ed2cd0a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188030"
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa TransactionFlowBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa TransactionFlowBindingElement ma następujące właściwości:  
  
### <a name="issuedtokens"></a>IssuedTokens  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa wymagania dla nagłówka tokenów zabezpieczeń (IssuedTokens z protokołu WS-Trust).  
  
### <a name="transactionprotocol"></a>Element transactionProtocol  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Protokół transakcji, używane przez usługę przepływ transakcji.  
  
### <a name="transactions"></a>Transakcje  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje, czy przychodzące transakcji jest obsługiwane.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
