---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 4f731d146885265d9f956c182f1bebdba5db924b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486874"
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
