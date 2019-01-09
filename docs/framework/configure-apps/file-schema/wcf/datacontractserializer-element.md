---
title: '&lt;DataContractSerializer&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: c79c8e8db2a4ea4526000bcbe336d1e664f9c4c2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150958"
---
# <a name="ltdatacontractserializergt"></a>&lt;DataContractSerializer&gt;
Zawierająca dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>. Ten element występuje w dwóch różnych hierarchii. Jeden jest wymieniony w poniższej sekcji hierarchia schematu, a druga znajduje się w sekcji uwag.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<dataContractSerializer >  
  
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
|IgnoreExtensionDataObject|Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jego serializowany lub deserializowany. Ten atrybut jest można ustawić tylko na `<dataContractSerializer>` w obszarze `<behavior>` elementu.|  
|MaxItemsInObjectGraph|Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji. Ten atrybut jest 65536.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|Kolekcję ustawień zachowania usługi.|  
|[\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|Reprezentuje element root dla sekcji <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Uwagi  
 Jak wspomniano we wprowadzeniu do tego tematu, jest to druga hierarchia, w którym \<X509Extension > element występuje.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [Znane typy kontraktów danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Transfer i serializacja danych](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
