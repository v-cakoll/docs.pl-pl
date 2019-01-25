---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: d0bf59e6064748a045f761777a2f8f3e88f1cb5a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504330"
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
 Gdy klasa nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Gdy klasa ma następujące właściwości:  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Stan funkcji automatycznego usuwania dla parametrów.  
  
### <a name="impersonation"></a>Personifikacja  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje poziom personifikacji obiekt wywołujący, który obsługuje operację.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, że w trakcie wywołania operacji odtworzenie obiektu.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy można zatwierdzić bieżącej transakcji automatycznie, jeśli wystąpi żaden nieobsługiwany wyjątek.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy operacja wymaga transakcji.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.OperationBehaviorAttribute>
