---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956718"
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement
SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa element SymmetricSecurityBindingElement ma następujące właściwości:  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Czy wiązanie wymaga potwierdzenia podpisu.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
