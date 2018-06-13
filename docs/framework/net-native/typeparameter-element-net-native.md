---
title: Element &lt;TypeParameter&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cc2faf9768b60d49f573720df8763813000a6b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393871"
---
# <a name="lttypeparametergt-element-net-native"></a>Element &lt;TypeParameter&gt; (architektura .NET Native)
Stosuje zasady do typu reprezentowanego przez argument typu przekazana do metody.  
  
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
|`Name`|Ogólne|Atrybut wymagany. Nazwa parametru typu <xref:System.Type>. Na przykład w podpisie metody `Type.GetInterfaceMap(Type interfaceType)`, wartość `Name` atrybutu jest "interfaceType".|  
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
|*nazwa_parametru*|Nazwa parametru typu <xref:System.Type>. Na przykład w podpisie metody `Type.GetInterfaceMap(Type interfaceType)`, wartość `Name` atrybutu jest "interfaceType".|  
  
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
  
## <a name="remarks"></a>Uwagi  
 `<TypeParameter>` Element jest podobny do [ \<parametru >](../../../docs/framework/net-native/parameter-element-net-native.md) element, z wyjątkiem, że mogą być stosowane tylko do parametrów typu <xref:System.Type>. Ma zastosowanie zasad do jakiegokolwiek rodzaju jest reprezentowana w czasie wykonywania przez określony przez argument typu `Name` atrybutu.  
  
 Na przykład serializator NewtonSoft JSON zawiera statycznego `JsonConvert.DeserializeObject(String value, Type type)` metody. Następujące dyrektywy odbicia:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 Określ tych metadanych dla typu środowiska uruchomieniowego reprezentowany przez `type` argument powinna zostać udostępniona do serializacji. Jeśli te dyrektyw środowiska uruchomieniowego stosuje się do projektu, który zawiera następujący kod źródłowy:  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 dyrektywy odbicia udostępnić metadanych dla `StockQuote` typu dostępne dla serializator NewtonSoft JSON w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Metoda > — Element](../../../docs/framework/net-native/method-element-net-native.md)  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
