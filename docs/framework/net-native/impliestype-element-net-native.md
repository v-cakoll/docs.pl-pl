---
title: Element <ImpliesType> (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 2f0ce1a1587e190627212cba07db298c12f4b30e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128392"
---
# <a name="impliestype-element-net-native"></a>\<element > ImpliesType (.NET Native)
Stosuje zasady do typu, jeśli te zasady zostały zastosowane do zawierającego je typu lub metody.  
  
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
|`Activate`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji JSON korzystającej z klasy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Kontroluje zasady dla serializacji XML, która używa klasy <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interop|Atrybut opcjonalny. Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.|  
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.|  
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*type_name*|Nazwa typu. Jeśli typ reprezentowany przez ten element `<ImpliesType>` znajduje się w tej samej przestrzeni nazw co element zawierający `<Type>`, *TYPE_NAME* może zawierać nazwę typu bez jego przestrzeni nazw. W przeciwnym razie *TYPE_NAME* musi zawierać w pełni kwalifikowaną nazwę typu.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad. Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`i `Required All`. Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Typ\<](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.|  
|[> metody\<](method-element-net-native.md)|Stosuje zasady odbicia do metody.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<ImpliesType>` jest przeznaczony głównie do użytku przez biblioteki. Dotyczy to następujących scenariuszy:  
  
- Jeśli procedura musi być odzwierciedlona na jednym typie, konieczna jest potrzeba odbicia w drugim typie.  
  
- Metadane dla implikowanego wystąpienia drugiego typu są w inny sposób niedostępne, ponieważ analiza statyczna nie wskazuje, że jest to konieczne.  
  
 Najczęściej istnieją dwa typy to ogólne wystąpienia z argumentami typu współużytkowanego.  
  
 Element `<ImpliesType>` został zdefiniowany z założeniem, że konieczność odbicia w typie określonym przez jego element nadrzędny oznacza potrzebę odbicia w typie określonym przez element `<ImpliesType>`. Na przykład następujące dyrektywy odbicia mają zastosowanie do dwóch typów, `Explicit<T>` i `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Ta dyrektywa nie działa, chyba że wystąpienie `Explicit` ma zdefiniowane ustawienie zasad `Dynamic`. Na przykład, jeśli ma to zastosowanie w przypadku `Explicit<Int32>`, `Implicit<Int32>` zostanie utworzone wystąpienie z publicznymi składowymi, a ich metadane są udostępniane do programowania dynamicznego.  
  
 Poniżej znajduje się przykład rzeczywistego, który ma zastosowanie do co najmniej jednego serializatora. Dyrektywy przechwytują wymaganie, które odzwierciedlają coś, co zostało wpisane jako `IList<`*coś*`>` obejmuje również odzwierciedlenie odpowiedniego `List<`*elementu*`>` typ bez konieczności stosowania żadnej aplikacji wskazani.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 Element `<ImpliesType>` może również znajdować się w obrębie elementu `<Method>`, ponieważ w niektórych przypadkach wystąpienie metody ogólnej implikuje odzwierciedlenie w wystąpieniu typu. Załóżmy na przykład, że metoda ogólna `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)`, że dana biblioteka będzie uzyskiwać dostęp dynamicznie wraz ze skojarzonymi typami <xref:System.Collections.Generic.List%601> i <xref:System.Array>. Może to być wyrażone jako:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
