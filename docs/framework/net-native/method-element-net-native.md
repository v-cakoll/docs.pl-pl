---
title: <Method>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180988"
---
# <a name="method-element-net-native"></a>\<Method>— Element (.NET Native)
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
|`Signature`|Ogólne|Atrybut opcjonalny. Określa sygnaturę metody. Jeśli istnieją wiele parametrów, są one oddzielone przecinkami. Na przykład poniższy `<Method>` element definiuje zasady dla <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metody.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Jeśli atrybut jest nieobecny, dyrektywa Runtime stosuje się do wszystkich przeciążeń metody.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje wykonywanie zapytań dotyczących informacji na temat lub wyliczanie metody, ale nie włącza żadnego dynamicznego wywołania w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktora lub metody w celu włączenia programowania dynamicznego. Te zasady zapewniają, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa metody. Typ metody jest zdefiniowany przez [\<Type>](type-element-net-native.md) element nadrzędny lub [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .|  
  
## <a name="signature-attribute"></a>Atrybut podpisu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_signature*|Typy parametrów, które tworzą sygnaturę metody. Wiele parametrów jest oddzielonych przecinkami, na przykład `"System.String,System.Int32,System.Int32)"` . Nazwy typów parametrów powinny być w pełni kwalifikowane.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad. Możliwe wartości to `Auto` , `Excluded` , `Included` , i `Required` . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|Stosuje zasady do typu argumentu przesłanego do metody.|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|Stosuje zasady do typu parametru typu ogólnego lub metody.|  
|[\<ImpliesType>](impliestype-element-net-native.md)|Stosuje zasady do typu, jeśli te zasady zostały zastosowane do metody reprezentowanej przez `<Method>` element zawierający.|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|Stosuje zasady do typu reprezentowanego przez <xref:System.Type> argument przesłany do metody.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.|  
  
## <a name="remarks"></a>Uwagi  
 `<Method>`Element metody ogólnej stosuje swoje zasady do wszystkich wystąpień, które nie mają własnych zasad.  
  
 Możesz użyć atrybutu, `Signature` Aby określić zasady dla konkretnego przeciążenia metody. W przeciwnym razie, jeśli `Signature` atrybut jest nieobecny, dyrektywa Runtime stosuje się do wszystkich przeciążeń metody.  
  
 Nie można zdefiniować zasad odbicia środowiska uruchomieniowego dla konstruktora przy użyciu `<Method>` elementu. Zamiast tego należy użyć `Activate` atrybutu [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) elementu,, [\<Type>](type-element-net-native.md) , lub [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .  
  
## <a name="example"></a>Przykład  
 `Stringify`Metoda w poniższym przykładzie jest metodą formatowania ogólnego zastosowania, która używa odbicia do przekonwertowania obiektu na jego reprezentację w postaci ciągu. Oprócz wywoływania domyślnej `ToString` metody obiektu Metoda może utworzyć sformatowany ciąg wynikowy przez przekazanie `ToString` metody obiektu ciągu formatu, <xref:System.IFormatProvider> implementacji lub obu. Może również wywołać jedno z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> przeciążeń, które konwertuje liczbę na jej reprezentację binarną, szesnastkową lub ósemkową.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify`Metoda może być wywoływana przez kod podobny do następującego:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Jednak podczas kompilowania z .NET Native przykład może zgłosić liczbę wyjątków w czasie wykonywania, w tym <xref:System.NullReferenceException> wyjątki i [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , dzieje się tak, ponieważ `Stringify` Metoda jest zaprojektowana głównie do obsługi dynamicznego formatowania typów pierwotnych w bibliotece klas .NET Framework. Jednak ich metadane nie są udostępniane przez domyślny plik dyrektyw. Jednak w przypadku udostępnienia ich metadanych przykład zgłasza wyjątki [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , ponieważ odpowiednie `ToString` implementacje nie zostały uwzględnione w kodzie natywnym.  
  
 Te wyjątki można usunąć za pomocą [\<Type>](type-element-net-native.md) elementu, aby zdefiniować typy, których metadane muszą być obecne, i przez dodanie elementów, `<Method>` Aby upewnić się, że implementacja przeciążeń metody, które mogą być wywołane dynamicznie. Poniżej znajduje się domyślny plik. Rd. XML, który eliminuje te wyjątki i pozwala na wykonywanie przykładu bez błędu.  
  
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

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
- [\<MethodInstantiation>Postaci](methodinstantiation-element-net-native.md)
