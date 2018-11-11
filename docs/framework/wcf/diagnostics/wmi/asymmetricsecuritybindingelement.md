---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 076313548828f1fbce9c68b48c0fa7db9cca095f
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982793"
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement
AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa element AsymmetricSecurityBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa element AsymmetricSecurityBindingElement ma następujące właściwości:  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Czy wiązanie wymaga potwierdzenia podpisu.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
