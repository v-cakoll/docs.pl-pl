---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771598"
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
  
 Typ dostępu: tylko do odczytu  
  
 Określa wymagania dla nagłówka tokenów zabezpieczeń (IssuedTokens z protokołu WS-Trust).  
  
### <a name="transactionprotocol"></a>TransactionProtocol  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Protokół transakcji, używane przez usługę przepływ transakcji.  
  
### <a name="transactions"></a>Transakcje  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy przychodzące transakcji jest obsługiwane.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
