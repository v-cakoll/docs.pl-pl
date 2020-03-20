---
title: <Subtypes>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: bb719449f3769c5dbbde6d05efdb865c18bb4ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180937"
---
# <a name="subtypes-element-net-native"></a>\<Podtypy> elementu (.NET Native)
Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Subtypes Activate="policy_type"  
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
  
## <a name="all-attributes"></a>Wszystkie atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zastosowanie do tego typu zasad. Możliwe wartości `All` `Auto`to `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , i . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ>](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego członków.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<Subtypes>` stosuje zasady do wszystkich podtypów jego typu zawierającego. Można go używać, gdy chcesz zastosować różne zasady do typów pochodnych i ich klas podstawowych.  
  
 Atrybuty odbicia, serializacji i międzyoperacyjne są opcjonalne, chociaż co najmniej jeden powinien być obecny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje klasę `BaseClass` o nazwie `Derived1`i podklasę o nazwie .  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 Jak pokazano w poniższym kodzie, plik dyrektyw `Dynamic` środowiska `Activate` uruchomieniowego jawnie ustawia zasady i zasady dla `BaseClass` . `Excluded` Z tego powodu obiekty `BaseClass` typu nie mogą być tworzone dynamicznie lub przez wywołania konstruktora `BaseClass` klasy. Jednak `<Subtypes>` element umożliwia klasy pochodzące z `BaseClass` do wystąpienia dynamicznie i za pośrednictwem wywołań do ich konstruktorów klas.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 Ze względu `<Subtypes>` na dyrektywę następujący kod, `Derived1` który dynamicznie <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> wywołuje wystąpienie, wywołując metodę, jest wykonywana pomyślnie.  Zmienna bloku w <xref:System.Windows.Controls.TextBlock> tym miejscu jest obiektem w pustej aplikacji ze Sklepu Windows.  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a>Zobacz też

- [\<Wpisz element>](type-element-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
