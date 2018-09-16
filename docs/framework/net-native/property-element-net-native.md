---
title: Element &lt;Property&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ed75d377814a740edece2b6a69e44acbd8ef0c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676814"
---
# <a name="ltpropertygt-element-net-native"></a>Element &lt;Property&gt; (architektura .NET Native)
Zastosowanie zasad odbicia środowiska uruchomieniowego do właściwości.  
  
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
|`Browse`|Odbicie|Atrybut opcjonalny. Określa wykonanie zapytania dotyczącego informacji o wyliczanie właściwości, ale nie uwzględnia żadnych dostępu dynamicznego w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Dostęp do środowiska uruchomieniowego formanty do właściwości, aby włączyć dynamiczne programowania. Te zasady zapewniają, że właściwość można ustawić lub pobrać dynamicznie w czasie wykonywania.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp do środowiska uruchomieniowego do właściwości w celu włączenia wystąpień typu przez biblioteki, takie jak serializator Newtonsoft JSON lub ma być używany dla powiązania danych.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa właściwości. Typ właściwości jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad dla właściwości. Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli właściwość zasad nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania odpowiedniego elementu nadrzędnego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto odbicia w celu utworzenia wystąpienia `Book` obiektów i wyświetlić jego wartości właściwości. Oryginalny plik default.rd.xml projektu wygląda następująco:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Plik ma zastosowanie `All` wartość `Activate` zasady dla `Book` klasy, która zezwala na dostęp do konstruktorów klas przy użyciu odbicia. `Browse` Zasady `Book` klasy jest dziedziczony z jego nadrzędna przestrzeń nazw. Jest ono ustawione na `Required Public`, co sprawia, że metadane dostępne w czasie wykonywania.  
  
 Poniżej znajduje się kod źródłowy dla przykładu. `outputBlock` Reprezentuje zmienną [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) kontroli.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Jednak kompilowanie i wykonywania w tym przykładzie zgłasza [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątku. Mimo że wprowadziliśmy metadanych `Book` typ jest dostępny, już nie możemy udostępnić implementacji metody pobierające właściwości dynamicznie. Możemy naprawić ten błąd, wybierając w jeden z dwóch sposobów:  
  
-   Definiując `Dynamic` zasady `Book` wpisz jego [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu.  
  
-   Dodając zagnieżdżoną [ \<właściwości >](../../../docs/framework/net-native/property-element-net-native.md) dla każdej właściwości, której metody pobierającej, prosimy o poświęcenie do wywołania, tak jak w następującym pliku default.rd.xml.  
  
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
