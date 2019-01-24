---
title: Element &lt;Method&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdfec7ce93dd3954af03f6f4822ac00576a7e043
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562937"
---
# <a name="ltmethodgt-element-net-native"></a>Element &lt;Method&gt; (architektura .NET Native)
Ma zastosowanie zasad odbicia środowiska uruchomieniowego do konstruktora lub metody.  
  
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
|`Signature`|Ogólne|Atrybut opcjonalny. Określa podpis metody. Jeśli podano wiele parametrów są oddzielone przecinkami. Na przykład następująca `<Method>` element definiuje zasady dla <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metody.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Jeśli ten atrybut jest nieobecne, dyrektyw środowiska uruchomieniowego ma zastosowanie do wszystkich przeciążeń metody.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Określa wykonanie zapytania dotyczącego informacji o wyliczanie metody, ale nie uwzględnia żadnych wywołanie dynamiczne w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Dostęp do środowiska uruchomieniowego formanty do konstruktora lub metody, aby włączyć dynamiczne programowania. Te zasady zapewniają, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa metody. Typ metody jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="signature-attribute"></a>Atrybut podpisu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_signature*|Typy parametrów, które tworzą podpis metody. Wiele parametrów są oddzielone przecinkami, na przykład `"System.String,System.Int32,System.Int32)"`. Nazwami typu parametru powinna być w pełni kwalifikowana.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania do tego typu zasad. Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)|Stosuje zasady do typu argumentu przekazanego do metody.|  
|[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Stosuje zasady do typu parametru typu ogólnego lub metody.|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|Stosuje zasady do typu, jeśli te zasady zostały doliczone do metody reprezentowanej przez zawierający `<Method>` elementu.|  
|[\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|Stosuje zasady na typ reprezentowany przez <xref:System.Type> argument przekazywany do metody.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<Method>` elementu metody ogólnej stosuje swoje zasady do wszystkich wystąpień, które nie mają własnych zasad.  
  
 Możesz użyć `Signature` atrybutu, aby określić zasady dla przeciążeń określonej metody. W przeciwnym razie, jeśli `Signature` atrybut jest nieobecne, dyrektyw środowiska uruchomieniowego ma zastosowanie do wszystkich przeciążeń metody.  
  
 Nie można zdefiniować zasady odbicia środowiska uruchomieniowego dla konstruktora przy użyciu `<Method>` elementu. Zamiast tego należy użyć `Activate` atrybutu [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md), lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.  
  
## <a name="example"></a>Przykład  
 `Stringify` Metody w poniższym przykładzie jest metodą formatowania ogólnego przeznaczenia, która używa odbicia w celu konwersji obiektu na jego reprezentację ciągu. Oprócz wywołanie domyślnego obiektu `ToString` metody, metoda może wygenerować sformatowany ciąg wynikowy przez przekazanie obiektu `ToString` metoda ciąg formatu <xref:System.IFormatProvider> implementacji i / lub. Można też wywołać jedną z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> przeciążenia, które konwertuje liczbę na jego reprezentację binarnym, szesnastkowym lub ósemkowo.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify` Metoda może być wywoływana przez kod, podobnie do poniższego:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Jednak, gdy skompilowano z architekturą .NET Native, przykładu może zgłosić liczba wyjątków w czasie wykonywania, w tym <xref:System.NullReferenceException> i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, dzieje się tak dlatego `Stringify` jest — metoda przeznaczona głównie w celu obsługi dynamicznie formatowanie typów pierwotnych w bibliotece klas programu .NET Framework. Jednak ich metadanych nie zostanie udostępniony przez domyślny plik dyrektywy. Nawet wtedy, gdy ich metadane są udostępniane, jednak przykład generuje [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątków ponieważ odpowiednie `ToString` nie zostały zawiera implementacji w kodzie natywnym.  
  
 Wyjątki te mogą wszystkie zostać usunięte przy użyciu [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu, aby zdefiniować typy, których metadane muszą być obecne, a przez dodanie `<Method>` elementy, aby zapewnić, że implementacja przeciążenia metody którą można wywołać dynamicznie również jest obecny. Poniżej znajduje się plik default.rd.xml eliminuje tych wyjątków i zezwala na przykład można wykonać bez błędów.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [\<MethodInstantiation > Element](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)
