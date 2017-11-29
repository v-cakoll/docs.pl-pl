---
title: Element &lt;Method&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6d70fd560cb7b164460eb3882cac88ed733d788
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmethodgt-element-net-native"></a>Element &lt;Method&gt; (architektura .NET Native)
Zastosowanie zasad wykonywania odbicia do konstruktora lub metody.  
  
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
|`Browse`|Odbicie|Atrybut opcjonalny. Określa, czy podczas badania informacji dotyczących metody wyliczania, jednak nie wszystkie wywołania dynamicznej w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Sterowanie dostępem środowiska uruchomieniowego do konstruktora lub metody, aby włączyć dynamiczne programowania. Ta zasada zapewnia, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa metody. Typ metody jest określany przez element nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.|  
  
## <a name="signature-attribute"></a>Atrybut podpisu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_signature*|Typy parametrów, które tworzą podpis metody. Wiele parametrów są oddzielone przecinkami, na przykład `"System.String,System.Int32,System.Int32)"`. Nazwy parametrów typu powinny być w pełni kwalifikowana.|  
  
## <a name="all-other-attributes"></a>Inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienia do zastosowania dla tego typu zasad. Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`. Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)|Stosuje zasady do typu argumentu przekazanego do metody.|  
|[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Stosuje zasady do typu parametru typu ogólnego lub metody.|  
|[\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)|Stosuje zasady do typu, o ile tej zasady zostały zastosowane do metody reprezentowany przez zawierający `<Method>` elementu.|  
|[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|Stosuje zasady do typu reprezentowanego przez <xref:System.Type> argument przekazany do metody.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje odbicia zasady do typu i jej elementów członkowskich.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 A `<Method>` element metody rodzajowej dotyczy wszystkich wystąpień, które nie mają własnych zasad polityki.  
  
 Można użyć `Signature` atrybutu, aby określić zasady przeciążenia konkretnej metody. W przeciwnym razie, jeśli `Signature` nie jest obecny atrybut, dyrektyw środowiska uruchomieniowego mają zastosowanie do wszystkich przeciążeń metody.  
  
 Nie można zdefiniować zasady odbicia środowiska uruchomieniowego dla konstruktora przy użyciu `<Method>` elementu. Zamiast tego należy użyć `Activate` atrybutu [ \<zestawu >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md), lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.  
  
## <a name="example"></a>Przykład  
 `Stringify` Metoda w poniższym przykładzie jest metodę formatowania ogólnego przeznaczenia, która używa odbicia do konwersji obiektu do reprezentacji ciągu. Oprócz wywoływania domyślnego obiektu `ToString` metody, metody powodują ciąg sformatowany wynik przez przekazanie obiektu `ToString` metody ciąg formatu <xref:System.IFormatProvider> implementacji lub oba. Można również wywoływanie jednego z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> przeciążeń, które konwertuje liczbę na jej reprezentację binarnego, szesnastkową lub ósemkowo.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify` Metoda może być wywoływany przez kod podobnie do następującej:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Jednak gdy skompilowano z platformą .NET Native, przykładzie może zgłosić liczba wyjątków w czasie wykonywania, w tym <xref:System.NullReferenceException> i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, dzieje się tak dlatego `Stringify` jest — metoda przeznaczony głównie do obsługi dynamicznie pierwotne typy formatowania w bibliotece klas programu .NET Framework. Jednak ich metadanych nie zostanie udostępniony przez domyślny plik dyrektywy. Nawet wtedy, gdy metadane są udostępniane, jednak przykładzie zgłasza [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki ponieważ odpowiednie `ToString` ma zostały zawiera implementacji w kodzie natywnym.  
  
 Wyjątki te wszystkie można wyeliminować za pomocą [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) elementu, aby zdefiniować typy, których metadane muszą być obecne, a przez dodanie `<Method>` elementy, aby zapewnić, że implementacja przeciążenia metody można dynamicznie wywołać który również jest obecny. Poniżej znajduje się plik default.rd.xml eliminuje tych wyjątków i zezwala na przykład aby zostanie wykonane bez błędów.  
  
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
 [Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [\<MethodInstantiation > — Element](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)
