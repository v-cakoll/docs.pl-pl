---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: e24dae47171f741af064ca2eaa822928690acf6e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400448"
---
# \<dataContractSerializer>
Zawiera dane konfiguracji dla programu <xref:System.Runtime.Serialization.DataContractSerializer> . Ten element występuje w dwóch różnych hierarchiach. Jeden z nich znajduje się w poniższej sekcji hierarchii schematu, a drugi jest wymieniony w sekcji uwagi.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
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
|ignoreExtensionDataObject|Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jest on serializowany lub deserializowany. Ten atrybut jest tylko do settable dla `<dataContractSerializer>` `<behavior>` elementu.|  
|maxItemsInObjectGraph|Liczba całkowita, która określa maksymalną liczbę elementów do serializacji lub deserializacji. Ten atrybut to 65536.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|Kolekcja ustawień zachowania usługi.|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|Reprezentuje element główny dla <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawień <xref:System.Runtime.Serialization.DataContractSerializer> .|  
  
## <a name="remarks"></a>Uwagi  
 Zgodnie z wprowadzeniem tego tematu jest to druga hierarchia, w której \<X509Extension> występuje element.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Znane typy kontraktów danych](../../../wcf/feature-details/data-contract-known-types.md)
- [Transfer i serializacja danych](../../../wcf/feature-details/data-transfer-and-serialization.md)
