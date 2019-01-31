---
title: <add> z <declaredTypes> — Element
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: e6aab0b1eca340e212c34e2d25b9b84984dcc7a0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255513"
---
# <a name="add-of-declaredtypes-element"></a>\<Dodaj > z \<declaredTypes > Element
Dodaje typ używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji. Każdy typ zadeklarowany zawiera znane typy, które zostaną zwrócone jako pole lub właściwość zadeklarowanym typem.  
  
 system.runtime.serialization  
\<dataContractSerializer>  
\<declaredTypes >  
\<Dodaj > z \<declaredTypes >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Atrybut wymagany ciąg.<br /><br /> Określa nazwę typu (włącznie z przestrzenią nazw), nazwę zestawu, numer wersji, kulturę i token klucza publicznego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Element knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Określa typ znany deklarowany typ, który jest dodawany. Gdy deklarowany typ jest typem ogólnym, a następnie element parametru należy także dodać `<knownType>` elementu, aby określić, które parametrów ogólnych służy do zwracania znanego typu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|Zawiera typy, które wymagają znanych typów podczas deserializacji, <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Zobacz [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) na przykład przy użyciu tego elementu.  
  
> [!NOTE]
>  Jeśli dodasz <xref:System.Object> wpisać jako `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> zgłaszany. Jest to spowodowane <xref:System.Object> typ nie może być używany jako zadeklarowanym typem w konfiguracji.  
  
## <a name="example"></a>Przykład  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Znane typy kontraktów danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [\<Dodaj > z \<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
