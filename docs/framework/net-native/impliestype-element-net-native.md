---
title: Element &lt;ImpliesType&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 867a11eae14c3e7b2fb09acac5849698119e72c7
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065976"
---
# <a name="ltimpliestypegt-element-net-native"></a>Element &lt;ImpliesType&gt; (architektura .NET Native)
W przypadku zasad do typu, że zasady zostały zastosowane do zawierający typ lub metoda.  
  
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
|*type_name*|Nazwa typu. Jeśli typ reprezentowany przez ten `<ImpliesType>` element znajduje się w tej samej przestrzeni nazw jako jego zawierający `<Type>` elementu *type_name* można uwzględnić nazwę typu bez jego przestrzeń nazw. W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowana nazwa typu.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.|  
|[\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)|Zastosowanie zasad odbicia do metody.|  
  
## <a name="remarks"></a>Uwagi  
 `<ImpliesType>` Element jest przeznaczona głównie do użytku przez biblioteki. Dotyczy on następujący scenariusz:  
  
-   Jeśli procedura wymaga zastanowić się nad jednego typu, niekoniecznie musi na zastanowienie się nad drugiego typu.  
  
-   Metadane dla wystąpienia dorozumianych drugi typ jest niedostępna, w przeciwnym razie w przypadku, ponieważ analizy statycznej nie oznacza, że jest to konieczne.  
  
 Najczęściej są dwa typy ogólnych instancji z argumentami typu udostępnionej.  
  
 `<ImpliesType>` Element został zdefiniowany przy założeniu, że na potrzeby odbicia na typ określony przez jego elementu nadrzędnego oznacza potrzebę odbicia dla typu określonego przez `<ImpliesType>` elementu. Na przykład, zastosuj następujące dyrektywy odbicia do dwóch typów `Explicit<T>` i `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Ta dyrektywa nie obowiązuje, chyba że egzemplarz o `Explicit` ma zdefiniowanych `Dynamic` ustawienie zasad. Na przykład, jeśli tak jest aby uzyskać `Explicit<Int32>`, `Implicit<Int32>` jest utworzone za pomocą jego publiczny dostęp do konta root członków i ich metadanych jest dostępne dla programowania dynamicznego.  
  
 Oto przykład świata rzeczywistego, który ma zastosowanie do co najmniej jeden element serializujący. Dyrektywy przechwytywania wymogu, że rozważania na temat coś wpisać jako `IList<` *coś* `>` obejmuje również odzwierciedlenie w odpowiedniej `List<` *coś* `>` typu bez konieczności żadnej adnotacji poszczególnych aplikacji.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 `<ImpliesType>` Element może znajdować się również w `<Method>` elementu, ponieważ w niektórych przypadkach tworzenia wystąpienia metody rodzajowej oznacza rozważania na temat wystąpienia typu. Na przykład Wyobraź sobie metody ogólnej `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` który danej biblioteki będzie miał dostęp dynamicznie wraz z skojarzonego <xref:System.Collections.Generic.List%601> i <xref:System.Array> typów. Może to być wyrażona jako:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
