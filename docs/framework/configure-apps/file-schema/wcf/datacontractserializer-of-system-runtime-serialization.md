---
title: <dataContractSerializer> z < system.runtime.serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: c81fdb040f2e0d6c9a3728d8ed3b917443ecb42e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115365"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a>\<dataContractSerializer> of \<system.runtime.serialization>
Zawierająca dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 \<system.runtime.serialization>  
\<dataContractSerializer>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Element|Opis|  
|-------------|-----------------|  
|ignoreExtensionDataObject|Wartość logiczna określająca, czy ignorować dane dostarczane przez punkt końcowy, gdy jego serializowany lub deserializowany. Ten atrybut jest można ustawić tylko na `<dataContractSerializer>` w obszarze `<behavior>` elementu.|  
|maxItemsInObjectGraph|Liczba całkowita określająca maksymalną liczbę elementów do serializacji lub deserializacji. Ten atrybut jest 65536.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|Zawiera znane typy, które <xref:System.Runtime.Serialization.DataContractSerializer> używa podczas deserializacji.<br /><br /> Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|Reprezentuje element root dla sekcji <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz <xref:System.Runtime.Serialization.DataContractSerializer> i [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [Znane typy kontraktów danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
