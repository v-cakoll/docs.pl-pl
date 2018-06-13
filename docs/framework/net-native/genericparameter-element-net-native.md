---
title: Element &lt;GenericParameter&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c0bf4aff9d7cc657b3005f0a19b09f3df10957c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393097"
---
# <a name="ltgenericparametergt-element-net-native"></a>Element &lt;GenericParameter&gt; (architektura .NET Native)
Stosuje zasady do typu parametru typu ogólnego lub metody.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type" />  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Name`|Ogólne|Atrybut wymagany. Nazwa parametru ogólnego. Na przykład w przypadku Delegat ogólny <xref:System.Func%603>, wartość `Name` atrybutu jest "TResult" do stosowania zasad środowiska uruchomieniowego dla wartości zwracanej delegata.|  
|`Activate`|Odbicie|Atrybut opcjonalny. Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Współdziałanie|Atrybut opcjonalny. Zasady kontroli przekazywanie typów referencyjnych do środowiska wykonawczego systemu Windows i modelu COM.|  
|`MarshalDelegate`|Współdziałanie|Atrybut opcjonalny. Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Współdziałanie|Atrybut opcjonalny. Określa zasady dla przekazywanie typów wartości do kodu natywnego.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*generic_parameter_name*|Atrybut wymagany. Nazwa parametru typu ogólnego. Na przykład w przypadku Delegat ogólny <xref:System.Func%603>, *generic_parameter_name* wartość "TResult" dotyczy delegata zwracana wartość zasad wykonywania.|  
  
## <a name="all-other-attributes"></a>Inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania dla tego typu zasad. Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Zastosowanie zasad wykonywania odbicia do konstruktora lub metody.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Zastosowanie zasad wykonywania odbicia do określonego typu, takich jak klasy lub struktury.|  
  
## <a name="remarks"></a>Uwagi  
 `<GenericParameter>` Element jest elementem podrzędnym albo [ \<metody >](../../../docs/framework/net-native/method-element-net-native.md) lub [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) element i jest używana do stosowania zasad do parametru określonego typu ogólnego, który jest określony przez jego nazwę w ogólnym typie lub metodzie sygnaturze.  
  
 `<GenericParameter>` Element jest najbardziej przydatna, gdy jest używany z serializatorów. W poniższym przykładzie użyto `<GenericParameter>` elementu, aby zastosować zasady do typu `T` w wywołaniach serializator NewtonSoft JSON [JsonConvert.DeserializeObject\<T > (ciąg)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) przeciążenia metody.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Metoda > — Element](../../../docs/framework/net-native/method-element-net-native.md)  
 [\<Typ > — Element](../../../docs/framework/net-native/type-element-net-native.md)  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
