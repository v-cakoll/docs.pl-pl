---
title: Element &lt;ImpliesType&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97b3e63ceb4b121c3e71e33a00fdf725258039c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltimpliestypegt-element-net-native"></a>Element &lt;ImpliesType&gt; (architektura .NET Native)
Stosuje zasady do typu, o ile tej zasady zostały zastosowane do typu zawierającego lub metody.  
  
## <a name="syntax"></a>Składnia  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
             Browse="policy_type"  
             Dynamic="policy_type"  
             Serialize="policy_type"   
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Name`|Ogólne|Atrybut wymagany. Określa nazwę typu.|  
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
|*type_name*|Nazwa typu. Jeśli typ reprezentowany przez to `<ImpliesType>` element znajduje się w tej samej przestrzeni nazw jako jego zawierający `<Type>` elementu *type_name* mogą obejmować nazwę typu bez jego przestrzeni nazw. W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowaną nazwę typu.|  
  
## <a name="all-other-attributes"></a>Inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania dla tego typu zasad. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje odbicia zasady do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Stosuje zasady odbicia do metody.|  
  
## <a name="remarks"></a>Uwagi  
 `<ImpliesType>` Element jest przeznaczony głównie do użytku przez biblioteki. Dotyczy on następujący scenariusz:  
  
-   Jeśli procedura wymaga do uwzględnienia w jednym typie, niekoniecznie musi w drugim typu.  
  
-   Metadane dla domyślnych podczas tworzenia wystąpienia typu drugi jest niedostępny, w przeciwnym razie ponieważ analizy statycznej nie oznacza, że jest to konieczne.  
  
 Najczęściej są dwa typy ogólnych utworzonych wystąpieniach z argumentami typu udostępnionego.  
  
 `<ImpliesType>` Element został zdefiniowany przy założeniu, że potrzeba odbicia w typie określonym przez jego elementu nadrzędnego oznacza potrzebę odbicia w typie określonym przez `<ImpliesType>` elementu. Na przykład następujące dyrektywy odbicia dotyczą dwa typy `Explicit<T>` i `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Ta dyrektywa jest nieskuteczne, chyba że tworzenie wystąpienia elementu `Explicit` ma zdefiniowane `Dynamic` ustawienie zasad. Na przykład, jeśli jest to w przypadku `Explicit<Int32>`, `Implicit<Int32>` zostanie uruchomiony z jego publicznych umieszczone elementy członkowskie, a ich metadanych jest dostępne dynamiczne programowania.  
  
 Poniżej przedstawiono przykład rzeczywistych, która ma zastosowanie do co najmniej jeden element serializujący. Dyrektywy przechwytywania wymagania, które odzwierciedlający na coś wpisane jako `IList<` *coś* `>` obejmuje również odbicia w odpowiedniej `List<` *coś* `>` typu bez konieczności żadnej adnotacji dla poszczególnych aplikacji.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 `<ImpliesType>` Element może również zostać wyświetlony w `<Method>` elementu, ponieważ w niektórych przypadkach tworzenia wystąpienia metody ogólnej oznacza odzwierciedlający na wystąpienia typu. Załóżmy na przykład metoda ogólna `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` dostępnym dla danej biblioteki będzie dynamicznie wraz ze skojarzonym <xref:System.Collections.Generic.List%601> i <xref:System.Array> typów. Można to wyrazić jako:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
