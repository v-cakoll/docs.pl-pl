---
title: <GenericParameter>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
ms.openlocfilehash: d0b18211206a8f9d4365ab3affe6d1c376003348
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128430"
---
# <a name="genericparameter-element-net-native"></a>\<GenericParameter>— Element (.NET Native)
Stosuje zasady do typu parametru typu ogólnego lub metody.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Name`|Ogólne|Atrybut wymagany. Nazwa parametru generycznego. Na przykład dla delegata ogólnego <xref:System.Func%603> wartość `Name` atrybutu jest "TResult", aby zastosować zasady środowiska uruchomieniowego do wartości zwracanej przez delegata.|  
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Interop|Atrybut opcjonalny. Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.|  
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*generic_parameter_name*|Atrybut wymagany. Nazwa parametru typu ogólnego. Na przykład dla delegata ogólnego <xref:System.Func%603> *generic_parameter_name* wartość "TResult" stosuje zasady środowiska uruchomieniowego do wartości zwracanej przez delegata.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad. Możliwe wartości to `All` , `Public` , `PublicAndInternal` , `Required Public` , `Required PublicAndInternal` i `Required All` . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|Stosuje zasady odbicia środowiska uruchomieniowego do konstruktora lub metody.|  
|[\<Type>](type-element-net-native.md)|Stosuje zasady odbicia środowiska uruchomieniowego do określonego typu, takiego jak Klasa lub struktura.|  
  
## <a name="remarks"></a>Uwagi  
 `<GenericParameter>`Element jest elementem podrzędnym [\<Method>](method-element-net-native.md) [\<Type>](type-element-net-native.md) elementu or i służy do stosowania zasad do określonego parametru typu ogólnego, który jest określony przez jego nazwę w typie ogólnym lub w podpisie metody.  
  
 `<GenericParameter>`Element jest najbardziej przydatny, gdy jest używany z serializatorami. Poniższy przykład używa elementu, `<GenericParameter>` Aby zastosować zasady do typu `T` w wywołaniach do [JsonConvert. \<T> deserializacji](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) metody Newtonsoft JSON serializator.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz także

- [\<Method>Postaci](method-element-net-native.md)
- [\<Type>Postaci](type-element-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
