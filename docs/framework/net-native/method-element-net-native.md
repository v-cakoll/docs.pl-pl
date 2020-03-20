---
title: <Method>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180988"
---
# <a name="method-element-net-native"></a>\<Metoda> element (.NET native)
Stosuje zasady odbicia środowiska uruchomieniowego do konstruktora lub metody.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Name`|Ogólne|Atrybut wymagany. Określa nazwę metody.|  
|`Signature`|Ogólne|Atrybut opcjonalny. Określa podpis metody. Jeśli istnieje wiele parametrów, są one oddzielone przecinkami. Na przykład następujący `<Method>` element definiuje zasady <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> dla metody.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Jeśli atrybut jest nieobecny, dyrektywy środowiska uruchomieniowego stosuje się do wszystkich przeciążeń metody.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań o informacje o metodzie lub wyliczanie, ale nie włącza żadnych wywołań dynamicznych w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do konstruktora lub metody, aby włączyć programowanie dynamiczne. Ta zasada gwarantuje, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.|  
  
## <a name="name-attribute"></a>Atrybut Nazwa  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa metody. Typ metody jest zdefiniowany przez [ \<](type-element-net-native.md) element nadrzędny Typ>lub [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) element.|  
  
## <a name="signature-attribute"></a>Atrybut podpisu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_signature*|Typy parametrów, które tworzą podpis metody. Wiele parametrów jest oddzielonych przecinkami, `"System.String,System.Int32,System.Int32)"`na przykład . Nazwy typów parametrów powinny być w pełni kwalifikowane.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zastosowanie do tego typu zasad. Możliwe wartości `Auto` `Excluded`to `Included`, `Required`, i . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>parametrów](parameter-element-net-native.md)|Stosuje zasady do typu argumentu przekazanego do metody.|  
|[\<>genericparameter](genericparameter-element-net-native.md)|Stosuje zasady do typu parametru typu lub metody rodzajowej.|  
|[\<ImpType>](impliestype-element-net-native.md)|Stosuje zasady do typu, jeśli ta zasada została zastosowana do `<Method>` metody reprezentowane przez element zawierający.|  
|[\<>typuParameter](typeparameter-element-net-native.md)|Stosuje zasady do typu reprezentowanego <xref:System.Type> przez argument przekazany do metody.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ>](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego członków.|  
|[\<>typu>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<Method>` metody rodzajowej stosuje swoje zasady do wszystkich wystąpienia, które nie mają własnych zasad.  
  
 Za pomocą `Signature` atrybutu można określić zasady dla przeciążenia określonej metody. W przeciwnym `Signature` razie jeśli atrybut jest nieobecny, dyrektywy środowiska uruchomieniowego stosuje się do wszystkich przeciążeń metody.  
  
 Nie można zdefiniować zasady odbicia środowiska wykonawczego `<Method>` dla konstruktora przy użyciu elementu. Zamiast tego należy `Activate` użyć atrybutu [ \<>zestawu ](assembly-element-net-native.md), [ \<>obszaru nazw ](namespace-element-net-native.md), [ \<Type>](type-element-net-native.md)lub [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) element.  
  
## <a name="example"></a>Przykład  
 Metoda `Stringify` w poniższym przykładzie jest metoda formatowania ogólnego przeznaczenia, który używa odbicia do konwersji obiektu do jego reprezentacji ciągu. Oprócz wywoływania domyślnej `ToString` metody obiektu, metoda może utworzyć sformatowany ciąg `ToString` wynik, przekazując <xref:System.IFormatProvider> metodę obiektu ciąg formatu, implementacji lub obu. Można również wywołać <xref:System.Convert.ToString%2A?displayProperty=nameWithType> jeden z przeciążeń, który konwertuje liczbę do jego binarne, szesnastkowe lub ósemkowe reprezentacji.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Metoda `Stringify` może być wywoływana przez kod, jak następujące:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Jednak po skompilowaniu z .NET Native, przykład może zgłosić <xref:System.NullReferenceException> szereg wyjątków w czasie wykonywania, w tym i `Stringify` [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) wyjątki, Dzieje się tak, ponieważ metoda jest przeznaczona głównie do obsługi dynamicznego formatowania typów pierwotnych w bibliotece klas .NET Framework. Jednak ich metadane nie są udostępniane przez domyślny plik dyrektyw. Nawet wtedy, gdy ich metadane są udostępniane, jednak w przykładzie zgłasza [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) wyjątki, ponieważ odpowiednie `ToString` implementacje nie zostały uwzględnione w kodzie macierzystym.  
  
 Wyjątki te można wyeliminować za pomocą [ \<Type>](type-element-net-native.md) element do definiowania typów, których metadane muszą być obecne i dodając `<Method>` elementy, aby upewnić się, że implementacja przeciążenia metody, które mogą być wywoływane dynamicznie jest również obecny. Poniżej znajduje się plik default.rd.xml, który eliminuje te wyjątki i umożliwia wykonanie przykładu bez błędu.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
- [\<Element> metody](methodinstantiation-element-net-native.md)
