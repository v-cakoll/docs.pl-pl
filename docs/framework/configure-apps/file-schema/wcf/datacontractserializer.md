---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8814a48df8933cf08db78e397c24d42f2da26026
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919229"
---
# <a name="datacontractserializer"></a>dataContractSerializer
Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
\<dataContractSerializer>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Element|Opis|  
|-------------|-----------------|  
|ignoreExtensionDataObject|Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany.|  
|maxItemsInObjectGraph|Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego.|  
  
## <a name="remarks"></a>Uwagi  
 Zapoznaj <xref:System.Runtime.Serialization.DataContractSerializer> się z dokumentacją, aby uzyskać więcej informacji na temat znanych typów.  
  
> [!CAUTION]
>  Element Behavior (jeśli istnieje) powinien zawsze występować `<enableWebScript>` przed elementem Behavior w pliku konfiguracji. `<dataContractSerializer>` W przeciwnym razie zachowanie nie jest zdefiniowane.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Znane typy kontraktów danych](../../../wcf/feature-details/data-contract-known-types.md)
- [Transfer i serializacja danych](../../../wcf/feature-details/data-transfer-and-serialization.md)
