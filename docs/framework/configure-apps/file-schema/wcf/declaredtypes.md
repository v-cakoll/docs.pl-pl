---
title: '&lt;declaredTypes&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: 405a6f21af1cb3508b7b88625101ed75f198bbaa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682670"
---
# <a name="ltdeclaredtypesgt"></a>&lt;declaredTypes&gt;
Zawiera znane typy, które <xref:System.Runtime.Serialization.DataContractSerializer> używa podczas deserializacji.  
  
 Aby uzyskać więcej informacji na temat kontraktów danych i znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 system.runtime.serialization  
\<dataContractSerializer>  
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
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Dodaje typy, które wymagają znane typy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|Zawierająca dane konfiguracyjne <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) i <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML przedstawiono typy zadeklarowane i znanych typów, które dodano do `DataContractSerializer` elementu. W przykładzie pokazano trzy typy dodawany. Pierwszy to typ niestandardowy o nazwie "Orders", który używa znany typ o nazwie "Item". Drugi zadeklarowany typ jest <xref:System.Collections.Generic.List%601> , który używa `Item` jako znanego typu. Na koniec trzeciego zadeklarowany typ jest <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Collections.Generic.Dictionary%602> Typem klasy jest typ ogólny, z parametrami typu dwa. Pierwszy reprezentuje klucz, a druga wartość. W poniższym przykładzie dodano <xref:System.Collections.Generic.List%601> drugiego typu (wartość) do listy znanych typów. Należy użyć `index` atrybutu, aby określić które parametr typu do użycia w znanego typu. W tym przypadku typ wartości jest wskazywany przez indeks atrybut ustawiony na wartość "1" (kolekcja jest liczony od zera).  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [Znane typy kontraktów danych](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
