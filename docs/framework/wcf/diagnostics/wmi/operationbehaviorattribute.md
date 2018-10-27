---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 6266713307846ab953299370835726958196fac1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185342"
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
  
 Dostęp do typu: tylko do odczytu  
  
 Stan funkcji automatycznego usuwania dla parametrów.  
  
### <a name="impersonation"></a>Personifikacja  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje poziom personifikacji obiekt wywołujący, który obsługuje operację.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje, że w trakcie wywołania operacji odtworzenie obiektu.  
  
### <a name="transactionautocomplete"></a>Wartość TransactionAutoComplete  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje, czy można zatwierdzić bieżącej transakcji automatycznie, jeśli wystąpi żaden nieobsługiwany wyjątek.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje, czy operacja wymaga transakcji.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
