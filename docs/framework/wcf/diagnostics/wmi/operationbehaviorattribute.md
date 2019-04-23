---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 79601308c66abe43dd5a7f72bd2a05b9d2346c2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975159"
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
