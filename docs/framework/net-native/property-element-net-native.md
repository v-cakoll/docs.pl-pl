---
title: Element &lt;Property&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a857523b15631aa9c112c9c0d208d96b0ec0d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltpropertygt-element-net-native"></a>Element &lt;Property&gt; (architektura .NET Native)
Zastosowanie zasad wykonywania odbicia właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Name`|Ogólne|Atrybut wymagany. Określa nazwę właściwości.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Określa, czy wykonywania zapytania dotyczącego informacji o wyliczaniu właściwości, ale nie umożliwia dostępu dynamicznej w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Formanty środowiska uruchomieniowego dostępu do właściwości, aby włączyć dynamiczne programowania. Ta zasada zapewnia, że właściwość można ustawić ani pobrać dynamicznie w czasie wykonywania.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Formanty środowiska uruchomieniowego dostęp do właściwości w celu włączenia wystąpień typów przez biblioteki, takich jak serializator Newtonsoft JSON lub do użycia dla powiązania danych.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa właściwości. Typ właściwości jest zdefiniowana przez nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="all-other-attributes"></a>Inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|To ustawienie, aby zastosować do tego typu właściwości. Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje odbicia zasady do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli właściwość zasad nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania jego elementu nadrzędnego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto odbicia do utworzenia wystąpienia `Book` obiektu i wyświetlić jej wartości właściwości. Oryginalny plik default.rd.xml projektu wygląda następująco:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Zastosowanie pliku `All` do wartości `Activate` zasady dla `Book` klasy, która zezwala na dostęp do konstruktorów klasy przy użyciu odbicia. `Browse` Zasady dla `Book` klasy jest dziedziczona z jej nadrzędną przestrzeń nazw. Ta wartość jest równa `Required Public`, który udostępnia metadane w czasie wykonywania.  
  
 Oto przykładowy kod źródłowy. `outputBlock` Reprezentuje zmienną [blok tekstu](http://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) formantu.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Jednakże, kompilowania i wykonywania w tym przykładzie zgłasza [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątku. Mimo że wprowadziliśmy metadanych `Book` typ jest dostępny, już nie możemy udostępnić implementacje metody pobierające właściwości dynamicznie. Firma Microsoft może rozwiązać ten problem przez w jeden z dwóch sposobów:  
  
-   Definiując `Dynamic` zasady dla `Book` wpisz jego [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) elementu.  
  
-   Dodając zagnieżdżoną [ \<właściwość >](../../../docs/framework/net-native/property-element-net-native.md) dla każdej właściwości, którego metoda pobierająca chcielibyśmy do wywołania, tak jak w następującym pliku default.rd.xml.  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
