---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa5394e874e35b80b01796642e18d69c71e867dc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
 Dostęp typu: tylko do odczytu  
  
 Określa wymaganie zabezpieczeń wystawionych tokenów nagłówka (IssuedTokens z protokołu WS-Trust).  
  
### <a name="transactionprotocol"></a>Element TransactionProtocol  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Protokół transakcji używany przez usługę przepływ transakcji.  
  
### <a name="transactions"></a>Transakcje  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy obsługiwane jest transakcją przychodzącą.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
