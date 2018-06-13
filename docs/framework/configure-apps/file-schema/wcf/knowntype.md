---
title: '&lt;Typ knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: b2445f12f1eaac03b3f3ab66f3d13a5f465a1133
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753329"
---
# <a name="ltknowntypegt"></a>&lt;Typ knownType&gt;
Określa typ, który będzie używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji. Element "znanego typu" Określa, który jest zwracany przez pole lub właściwość "zadeklarowanym typem". Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 \<System.Runtime.serialization >  
\<dataContractSerializer >  
\<declaredTypes > — Element  
\<Dodaj > z \<declaredTypes >  
\<Typ knownType > — Element  
  
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
|— typ|Określa typ (włącznie z przestrzenią nazw), nazwę zestawu, wersję, kulturę i token klucza publicznego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Parametr >](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|Określa indeks parametru, gdy deklarowany typ jest typem ogólnym.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Dodaje deklarowany typ do kolekcji zadeklarowanych typów.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) przykład za pomocą tego elementu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Znane typy kontraktów danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
