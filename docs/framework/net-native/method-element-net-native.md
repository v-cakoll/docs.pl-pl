---
title: Element <Method> (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 7b0e77e6dea29cbd5218ab3f6f992002efd51656
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128334"
---
# <a name="method-element-net-native"></a>Element > \<metody (.NET Native)
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
|`Signature`|Ogólne|Atrybut opcjonalny. Określa sygnaturę metody. Jeśli istnieją wiele parametrów, są one oddzielone przecinkami. Na przykład poniższy element `<Method>` definiuje zasady dla metody <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29>.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Jeśli atrybut jest nieobecny, dyrektywa Runtime stosuje się do wszystkich przeciążeń metody.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Kontroluje wykonywanie zapytań dotyczących informacji na temat lub wyliczanie metody, ale nie włącza żadnego dynamicznego wywołania w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Kontroluje dostęp środowiska uruchomieniowego do konstruktora lub metody w celu włączenia programowania dynamicznego. Te zasady zapewniają, że element członkowski może być wywoływany dynamicznie w czasie wykonywania.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa metody. Typ metody jest zdefiniowany przez nadrzędny [typ\<, >](type-element-net-native.md) lub [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .|  
  
## <a name="signature-attribute"></a>Atrybut podpisu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_signature*|Typy parametrów, które tworzą sygnaturę metody. Wiele parametrów jest oddzielonych przecinkami, na przykład `"System.String,System.Int32,System.Int32)"`. Nazwy typów parametrów powinny być w pełni kwalifikowane.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zostać zastosowane do tego typu zasad. Możliwe wartości to `Auto`, `Excluded`, `Included`i `Required`. Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<parametr >](parameter-element-net-native.md)|Stosuje zasady do typu argumentu przesłanego do metody.|  
|[\<GenericParameter >](genericparameter-element-net-native.md)|Stosuje zasady do typu parametru typu ogólnego lub metody.|  
|[\<ImpliesType >](impliestype-element-net-native.md)|Stosuje zasady do typu, jeśli te zasady zostały zastosowane do metody reprezentowanej przez zawierający ją element `<Method>`.|  
|[\<TypeParameter >](typeparameter-element-net-native.md)|Stosuje zasady do typu reprezentowanego przez argument <xref:System.Type> przekazaną do metody.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Typ\<](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.|  
  
## <a name="remarks"></a>Uwagi  
 `<Method>` element metody ogólnej stosuje swoje zasady do wszystkich wystąpień, które nie mają własnych zasad.  
  
 Można użyć atrybutu `Signature`, aby określić zasady dla konkretnego przeciążenia metody. W przeciwnym razie, jeśli atrybut `Signature` nie jest obecny, dyrektywa Runtime stosuje się do wszystkich przeciążeń metody.  
  
 Nie można zdefiniować zasad odbicia środowiska uruchomieniowego dla konstruktora przy użyciu elementu `<Method>`. Zamiast tego należy użyć atrybutu `Activate` [zestawu\<](assembly-element-net-native.md), [\<przestrzeni nazw >](namespace-element-net-native.md), [\<typu](type-element-net-native.md)> lub [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementu.  
  
## <a name="example"></a>Przykład  
 Metoda `Stringify` w poniższym przykładzie jest metodą formatowania ogólnego zastosowania, która używa odbicia do przekonwertowania obiektu na jego reprezentację w postaci ciągu. Oprócz wywołania domyślnej metody `ToString` obiektu, Metoda może utworzyć sformatowany ciąg wynikowy przez przekazanie metody `ToString` w postaci ciągu formatu, implementacji <xref:System.IFormatProvider> lub obu tych metod. Może również wywołać jedno z przeciążeń <xref:System.Convert.ToString%2A?displayProperty=nameWithType>, które konwertuje liczbę na reprezentację binarną, szesnastkową lub ósemkową.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Metoda `Stringify` może być wywoływana przez kod podobny do następującego:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 Jednak w przypadku kompilowania z .NET Native przykład może zgłosić liczbę wyjątków w czasie wykonywania, w tym <xref:System.NullReferenceException> i [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) wyjątków, dzieje się tak, ponieważ metoda `Stringify` jest przeznaczona głównie do obsługi dynamiczne formatowanie typów pierwotnych w bibliotece klas .NET Framework. Jednak ich metadane nie są udostępniane przez domyślny plik dyrektyw. Mimo tego, że metadane są udostępniane, przykład zgłasza wyjątki [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , ponieważ odpowiednie implementacje `ToString` nie zostały uwzględnione w kodzie natywnym.  
  
 Te wyjątki można usunąć za pomocą [typu\<](type-element-net-native.md) elementu, aby zdefiniować typy, których metadane muszą być obecne, i przez dodanie `<Method>` elementów, aby upewnić się, że implementacja przeciążeń metody, które mogą być wywołane dynamicznie, jest również aktualny. Poniżej znajduje się domyślny plik. Rd. XML, który eliminuje te wyjątki i pozwala na wykonywanie przykładu bez błędu.  
  
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
- [\<element > MethodInstantiation](methodinstantiation-element-net-native.md)
