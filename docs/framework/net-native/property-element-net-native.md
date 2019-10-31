---
title: Element <Property> (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: b9bc89804a872dddf1a56c2a3dadc9c3df4f5fd1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128211"
---
# <a name="property-element-net-native"></a>Element > Właściwości \<(.NET Native)
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
|*method_name*|Nazwa właściwości. Typ właściwości jest zdefiniowany przez nadrzędny [typ\<](type-element-net-native.md) lub [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad dla właściwości. Możliwe wartości to `Auto`, `Excluded`, `Included`i `Required`. Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Typ\<](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zasady właściwości nie są jawnie zdefiniowane, dziedziczy zasad środowiska uruchomieniowego jego elementu nadrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa odbicia, aby utworzyć wystąpienie obiektu `Book` i wyświetlić jego wartości właściwości. Oryginalny plik default. Rd. XML dla projektu jest wyświetlany w następujący sposób:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 Plik stosuje `All` wartość do zasad `Activate` dla klasy `Book`, co umożliwia dostęp do konstruktorów klas poprzez odbicie. Zasady `Browse` dla klasy `Book` są dziedziczone z nadrzędnej przestrzeni nazw. Ta wartość jest ustawiona na `Required Public`, co sprawia, że metadane są dostępne w czasie wykonywania.  
  
 Poniżej znajduje się kod źródłowy dla przykładu. Zmienna `outputBlock` reprezentuje kontrolkę <xref:Windows.UI.Xaml.Controls.TextBlock>.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 Jednak Kompilowanie i wykonywanie tego przykładu zgłasza wyjątek [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) . Mimo że zostały wprowadzone metadane dla `Book` typu, nie udało nam się zapewnić, że implementacje metod pobierających właściwości są dostępne dynamicznie. Możemy naprawić ten błąd w jeden z dwóch sposobów:  
  
- Definiując zasady `Dynamic` dla typu `Book` w [\<typie >](type-element-net-native.md) elementu.  
  
- Dodanie zagnieżdżonej [właściwości\<](property-element-net-native.md) elementu dla każdej właściwości, której ma dotyczyć metoda pobierająca, tak jak w poniższym pliku. Rd. XML.  
  
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
