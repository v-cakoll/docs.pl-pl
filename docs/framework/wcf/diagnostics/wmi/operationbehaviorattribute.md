---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63824ae2171053bee2af204e748a6fa811f2ba82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Składnia  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa OperationBehaviorAttribute nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa OperationBehaviorAttribute ma następujące właściwości:  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Stan funkcji automatycznego usuwania parametrów.  
  
### <a name="impersonation"></a>Personifikacja  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje poziom personifikacji wywołującego obsługiwany przez operację.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, kiedy ma wywołania operacji ponowne przetworzenie obiektu.  
  
### <a name="transactionautocomplete"></a>Wartość TransactionAutoComplete  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy ma być automatycznie przekazywana bieżącej transakcji, jeśli wystąpi żaden nieobsługiwany wyjątek.  
  
### <a name="transactionscoperequired"></a>Właściwości TransactionScopeRequired  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy operacja wymaga transakcji.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
