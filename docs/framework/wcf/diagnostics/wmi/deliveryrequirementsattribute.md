---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 172f7df4f028c1ddc0f5565e95291e857ee6fa1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
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
