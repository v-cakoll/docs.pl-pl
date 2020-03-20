---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152973"
---
# <a name="systemruntimeserialization"></a>\<> system.runtime.serialization
Reprezentuje element główny <xref:System.Runtime.Serialization> sekcji obszaru nazw i zawiera elementy <xref:System.Runtime.Serialization.DataContractSerializer>do ustawiania opcji programu .  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;**\<>system.runtime.serialization**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|Umożliwia dodawanie znanych typów, które mają być używane podczas deserializacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<element> konfiguracji](../configuration-element.md)|Element najwyższego poziomu dla konfiguracji.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization>
- [Używanie kontraktów danych](../../../wcf/feature-details/using-data-contracts.md)
- [Znane typy kontraktów danych](../../../wcf/feature-details/data-contract-known-types.md)
