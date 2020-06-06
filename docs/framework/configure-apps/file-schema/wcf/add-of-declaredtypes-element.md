---
title: <add><declaredTypes>elementu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400656"
---
# <a name="add-of-declaredtypes-element"></a>\<add>\<declaredTypes>elementu
Dodaje typ używany przez <xref:System.Runtime.Serialization.DataContractSerializer> podczas deserializacji. Każdy zadeklarowany typ zawiera znane typy, które będą zwracane jako pole lub właściwość zadeklarowanego typu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
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
|typ|Wymagany atrybut ciągu.<br /><br /> Określa nazwę typu (w tym przestrzeń nazw), nazwę zestawu, numer wersji, kulturę i token klucza publicznego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|Określa znany typ zadeklarowanego typu, który jest dodawany. Jeśli zadeklarowany typ jest typem ogólnym, należy również dodać element parametru do `<knownType>` elementu, aby określić, który parametr generyczny jest używany do zwrócenia znanego typu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|Zawiera typy, które wymagają znanych typów podczas deserializacji przez <xref:System.Runtime.Serialization.DataContractSerializer> .|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 Zobacz, [\<dataContractSerializer>](datacontractserializer-element.md) Aby zapoznać się z przykładem użycia tego elementu.  
  
> [!NOTE]
> Jeśli typ zostanie dodany <xref:System.Object> jako `<declaredType>` , <xref:System.Configuration.ConfigurationErrorsException> zostanie zgłoszony. Dzieje się tak, ponieważ <xref:System.Object> Typ nie może być używany jako zadeklarowany typ w konfiguracji.  
  
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
- [Znane typy kontraktów danych](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>z\<declaredTypes>](add-of-declaredtypes-element.md)
