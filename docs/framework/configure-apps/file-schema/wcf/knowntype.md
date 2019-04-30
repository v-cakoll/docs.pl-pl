---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760691"
---
# <a name="knowntype"></a>\<Element knownType >
Określa typ, który ma być używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji. Element określa "znany typ" zwracanym przez pole lub właściwość "type zadeklarowany". Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 \<system.runtime.serialization>  
\<dataContractSerializer>  
\<declaredTypes > Element  
\<Dodaj > z \<declaredTypes >  
\<knownType> Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a>Typ  
 `string`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Określa typ (włącznie z przestrzenią nazw), nazwę zestawu, wersji, kulturę i token klucza publicznego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Parametr >](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|Określa indeks parametru, gdy deklarowany typ jest typem ogólnym.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Dodaje deklarowany typ do kolekcji typów zadeklarowane.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) na przykład przy użyciu tego elementu.  
  
## <a name="example"></a>Przykład  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Znane typy kontraktów danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
