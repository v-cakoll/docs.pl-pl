---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: d294ba4f14472012b9e311ee53742633b5173f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485825"
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Składnia  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>Metody  
 Element DeliveryRequirementsAttribute klasa nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Element DeliveryRequirementsAttribute klasa ma następujące właściwości:  
  
### <a name="queueddeliveryrequirements"></a>Pola QueuedDeliveryRequirements  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy wiązanie dla usługi obsługuje kontrakty.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy wiązanie obsługuje uporządkowane komunikaty.  
  
### <a name="targetcontract"></a>TargetContract  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Kontrakt, którego dotyczy.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
