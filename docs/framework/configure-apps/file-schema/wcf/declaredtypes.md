---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 138bc800625a8334d692bd46a3ceb7dfe2ea4ae1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdeclaredtypesgt"></a>&lt;declaredTypes&gt;
Zawiera znane typy, które <xref:System.Runtime.Serialization.DataContractSerializer> używa podczas deserializacji.  
  
 Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
                <parameter index="Integer"/>  
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
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Dodaje typy, które wymagają znanych typów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|Zawiera dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]znane typy, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML zawiera typy zadeklarowane i znanych typów dodane do `DataContractSerializer` elementu. W przykładzie trzy typy dodawany. Pierwsza to typ niestandardowy o nazwie "Zamówienia" używającej znanego typu o nazwie "Item". Drugi zadeklarowany typ jest <xref:System.Collections.Generic.List%601> używającą `Item` jako znanego typu. Na koniec trzeci zadeklarowany jako typ jest <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Collections.Generic.Dictionary%602> Typu klasy jest typem ogólnym, dwa typy parametrów. Pierwszy reprezentuje klucz, a druga wartość. W poniższym przykładzie dodano <xref:System.Collections.Generic.List%601> drugiego typu (wartość) do listy znanych typów. Należy użyć `index` atrybutu, aby określić, którego parametr typu do użycia w znanym typem. W takim przypadku typ wartości jest określane przez atrybut indeksu, ustaw wartość "1" (kolekcja jest liczony od zera).  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
            <parameter index="1"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [Znane typy kontraktów danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
