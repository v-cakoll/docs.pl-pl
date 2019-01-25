---
title: Element &lt;TypeParameter&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79e7a61f66a29ad4eeca1c6413b87d4b9ee9632e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644342"
---
# <a name="lttypeparametergt-element-net-native"></a>Element &lt;TypeParameter&gt; (architektura .NET Native)
Stosuje zasady na typ reprezentowany przez argument typu przekazany do metody.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Parameter Name="parameter_name"  
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
|`Name`|Ogólne|Atrybut wymagany. Nazwa parametru typu <xref:System.Type>. Na przykład dla sygnatury metody `Type.GetInterfaceMap(Type interfaceType)`, wartość `Name` atrybut jest "interfaceType".|  
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.|  
|`MarshalObject`|Usługa międzyoperacyjna|Atrybut opcjonalny. Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.|  
|`MarshalDelegate`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.|  
|`MarshalStructure`|Usługa międzyoperacyjna|Atrybut opcjonalny. Określa zasady dla marshaling typów wartości do kodu natywnego.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*parameter_name*|Nazwa parametru typu <xref:System.Type>. Na przykład dla sygnatury metody `Type.GetInterfaceMap(Type interfaceType)`, wartość `Name` atrybut jest "interfaceType".|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad. Możliwe wartości to `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Ma zastosowanie zasad odbicia środowiska uruchomieniowego do konstruktora lub metody.|  
  
## <a name="remarks"></a>Uwagi  
 `<TypeParameter>` Element jest podobny do [ \<parametr >](../../../docs/framework/net-native/parameter-element-net-native.md) elementu, z wyjątkiem, że można zastosować tylko do parametrów typu <xref:System.Type>. Ma zastosowanie zasad do jakiegokolwiek rodzaju jest reprezentowany w czasie wykonywania przez argument typu określonego przez `Name` atrybutu.  
  
 Na przykład serializator NewtonSoft JSON obejmuje statyczne `JsonConvert.DeserializeObject(String value, Type type)` metody. Następujące dyrektywy odbicia:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 Określ tych metadanych dla typu środowiska uruchomieniowego, reprezentowane przez `type` argument powinny być udostępnione do serializacji. Jeśli te dyrektywy środowiska uruchomieniowego stosują się do projektu, który zawiera następujący kod źródłowy:  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 dyrektywy odbicia, że metadane dla `StockQuote` typu dostępne dla serializator NewtonSoft JSON w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz także
- [\<Metoda > Element](../../../docs/framework/net-native/method-element-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
