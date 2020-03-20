---
title: <ImpliesType>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181015"
---
# <a name="impliestype-element-net-native"></a>\<Element imptype> (natywny.NET)
Stosuje zasady do typu, jeśli ta zasada została zastosowana do typu lub metody zawierającej.  
  
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
|`Activate`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do konstruktorów, aby włączyć aktywację wystąpień.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań o informacje o elementach programu, ale nie włącza dostępu do środowiska uruchomieniowego.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska uruchomieniowego do wszystkich elementów członkowskich typu, w tym konstruktorów, metod, pól, właściwości i zdarzeń, aby włączyć programowanie dynamiczne.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do konstruktorów, pól i właściwości, aby umożliwić serializowanie i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON firmy Newtonsoft.|  
|`DataContractSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> która używa klasy.|  
|`DataContractJsonSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji JSON, która używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.|  
|`XmlSerializer`|Serializacja|Atrybut opcjonalny. Steruje zasadami serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> tej klasy.|  
|`MarshalObject`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów odwołań do środowiska wykonawczego systemu Windows i środowiska COM.|  
|`MarshalDelegate`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu macierzystego.|  
|`MarshalStructure`|Interop|Atrybut opcjonalny. Steruje zasadami organizowania typów wartości do kodu macierzystego.|  
  
## <a name="name-attribute"></a>Atrybut Nazwa  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*Type_name*|Nazwa typu. Jeśli typ reprezentowany `<ImpliesType>` przez ten element znajduje się w `<Type>` tej samej przestrzeni nazw co jego element zawierający, *type_name* może zawierać nazwę typu bez jego obszaru nazw. W przeciwnym razie *type_name* musi zawierać w pełni kwalifikowaną nazwę typu.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zastosowanie do tego typu zasad. Możliwe wartości `All` `Auto`to `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , i . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ>](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego członków.|  
|[\<>typu>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego elementów członkowskich.|  
|[\<Metoda>](method-element-net-native.md)|Stosuje zasady odbicia do metody.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<ImpliesType>` jest przeznaczony głównie do użytku przez biblioteki. Dotyczy następującego scenariusza:  
  
- Jeśli procedura musi zastanowić się nad jednym typem, musi koniecznie zastanowić się nad drugim typem.  
  
- Metadane dla dorozumianego wystąpienia drugiego typu jest w przeciwnym razie niedostępne, ponieważ analiza statyczna nie wskazuje, że jest to konieczne.  
  
 Najczęściej dwa typy są ogólne wystąpienia z argumentami typu udostępnionego.  
  
 Element `<ImpliesType>` został zdefiniowany przy założeniu, że potrzeba odbicia na typ określony przez jego element nadrzędny implikuje potrzebę odbicia na typ określony przez `<ImpliesType>` element. Na przykład następujące dyrektywy refleksji mają `Explicit<T>` zastosowanie `Implicit<T>`do dwóch typów i .  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Ta dyrektywa nie ma wpływu, `Explicit` chyba że `Dynamic` wystąpienie ma zdefiniowane ustawienie zasad. Na przykład jeśli tak jest `Explicit<Int32>`w `Implicit<Int32>` przypadku , jest tworzone z jego elementów publicznych elementów członkowskich zakorzenione, a ich metadane są dostępne dla programowania dynamicznego.  
  
 Poniżej przedstawiono przykład w świecie rzeczywistym, który ma zastosowanie do co najmniej jednego serializatora. Dyrektywy przechwytywania wymóg, że refleksja na `IList<`coś wpisane jako *coś* `>` obejmuje również refleksji na odpowiedni `List<`typ *coś* `>` bez konieczności żadnych adnotacji na aplikację.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 Element `<ImpliesType>` może również pojawić `<Method>` się w elemencie, ponieważ w niektórych przypadkach tworzenie wystąpienia metody rodzajowej oznacza odzwierciedlenia na wystąpienie typu. Na przykład wyobraź sobie `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` metodę rodzajową, że dana biblioteka <xref:System.Collections.Generic.List%601> <xref:System.Array> będzie uzyskać dostęp dynamicznie wraz z skojarzonych i typów. Może to być wyrażone jako:  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
