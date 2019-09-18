---
title: <Property>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54daf15c593327bf3255f40f6eb6931ffc8bd3c6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049308"
---
# <a name="property-element-net-native"></a>\<Element > Właściwości (.NET Native)
Stosuje zasady odbicia środowiska uruchomieniowego do właściwości.  
  
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
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje wykonywanie zapytań dotyczących informacji o lub wyliczania właściwości, ale nie umożliwia dostępu dynamicznego w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do właściwości w celu włączenia programowania dynamicznego. Te zasady zapewniają, że właściwość może być ustawiana lub pobierana dynamicznie w czasie wykonywania.|  
|`Serialize`|Serializacja|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do właściwości, aby umożliwić Serializowanie wystąpień typu przez biblioteki takie jak serializator JSON Newtonsoft lub używany do wiązania danych.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa właściwości. Typ właściwości jest zdefiniowany przez [ \<typ nadrzędny >](type-element-net-native.md) lub [ \<element > TypeInstantiation](typeinstantiation-element-net-native.md) .|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad dla właściwości. Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`. Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zasady właściwości nie są jawnie zdefiniowane, dziedziczy zasad środowiska uruchomieniowego jego elementu nadrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa odbicia, aby utworzyć `Book` wystąpienie obiektu i wyświetlić jego wartości właściwości. Oryginalny plik default. Rd. XML dla projektu jest wyświetlany w następujący sposób:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Plik stosuje `All` wartość `Activate` do zasad dla `Book` klasy, co umożliwia dostęp do konstruktorów klas poprzez odbicie. `Browse` Zasady`Book` dla klasy są dziedziczone z jego nadrzędnej przestrzeni nazw. Ta wartość jest ustawiona `Required Public`na, co sprawia, że metadane są dostępne w czasie wykonywania.  
  
 Poniżej znajduje się kod źródłowy dla przykładu. `outputBlock` Zmienna<xref:Windows.UI.Xaml.Controls.TextBlock> reprezentuje kontrolkę.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Jednak Kompilowanie i wykonywanie tego przykładu zgłasza wyjątek [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) . Mimo że zostały zgłoszone metadane dla `Book` dostępnego typu, nie udało nam się zapewnić, że implementacje metod pobierających właściwości są dostępne dynamicznie. Możemy naprawić ten błąd w jeden z dwóch sposobów:  
  
- przez zdefiniowanie `Dynamic` zasad `Book` dla typu w [ \<typie >](type-element-net-native.md) element.  
  
- Dodając [ \<> Właściwość](property-element-net-native.md) zagnieżdżoną dla każdej właściwości, której ma dotyczyć metoda pobierająca, jako następujący domyślny plik. Rd. XML.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
