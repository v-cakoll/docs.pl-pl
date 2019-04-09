---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101780"
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa Element DeliveryRequirementsAttribute nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa Element DeliveryRequirementsAttribute ma następujące właściwości:  
  
### <a name="queueddeliveryrequirements"></a>QueuedDeliveryRequirements  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy wiązanie dla usługi obsługuje umów.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy powiązanie obsługuje uporządkowane komunikaty.  
  
### <a name="targetcontract"></a>TargetContract  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Kontrakt, której dotyczy.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
