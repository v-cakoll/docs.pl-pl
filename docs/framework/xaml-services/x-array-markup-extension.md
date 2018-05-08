---
title: x:Array — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: 7c728b63c16d8f24c4ad68d07e6d174f510204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xarray-markup-extension"></a>x:Array — Rozszerzenie znaczników
Zapewnia obsługę ogólne dla tablic obiektów w języku XAML, za pomocą rozszerzenia znaczników. Odpowiada to `x:ArrayExtension` typu XAML w [MS-XAML].  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`typeName`|Nazwa typu który Twojej `x:Array` będzie zawierać. `typeName` może być (i często jest) i jest poprzedzony dla XAML przestrzeni nazw, która zawiera XAML definicje typów.|  
|`arrayContents`|Zawartość elementów przypisanego do wewnętrznej `ArrayExtension.Items` właściwości. Zazwyczaj te elementy są określone jako co najmniej jeden obiekt zawartym w elemencie `x:Array` otwierające i zamykające znaczniki. Obiekty określone w tym miejscu powinny być można przypisać do typu XAML, określonego w `typeName`.|  
  
## <a name="remarks"></a>Uwagi  
 `Type` jest wymagany atrybut dla wszystkich `x:Array` obiekt elementów. A `Type` wartość parametru nie trzeba używać `x:Type` — rozszerzenie znaczników; krótkim Nazwa typu jest typu XAML, który może być określony jako ciąg.  
  
 W implementacji usług .NET Framework XAML, relacja między XAML typ danych wejściowych i wyjściowych CLR <xref:System.Type> utworzony tablicy ma wpływ kontekst usługi rozszerzenia znaczników. Dane wyjściowe <xref:System.Type> jest <xref:System.Xaml.XamlType.UnderlyingType%2A> wejściowego typu XAML po wyszukiwania niezbędnych <xref:System.Xaml.XamlType> oparte na kontekst schematu XAML i <xref:System.Windows.Markup.IXamlTypeResolver> usługi udostępnia kontekst.  
  
 Podczas przetwarzania zawartości tablicy są przypisane do `ArrayExtension.Items` wewnętrzną właściwość. W <xref:System.Windows.Markup.ArrayExtension> implementacji jest reprezentowane przez <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.  
  
 W implementacji usług .NET Framework XAML obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.Markup.ArrayExtension> klasy. <xref:System.Windows.Markup.ArrayExtension> nie jest zapieczętowany i może służyć jako podstawa implementacji rozszerzenie znaczników typu tablicy niestandardowych.  
  
 `x:Array` jest kilka przeznaczonych do ogólne rozszerzalności języka w języku XAML. Ale `x:Array` może także służyć do określania wartości XAML niektórych właściwości, które przyjmować obsługiwane XAML kolekcji jako ich zawartość właściwości strukturalne. Na przykład można określić zawartości <xref:System.Collections.IEnumerable> właściwości o `x:Array` użycia.  
  
 `x:Array` to rozszerzenie znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. `x:Array` jest częściowo wyjątek od tej reguły, ponieważ zamiast zapewnienie obsługi wartość atrybutu alternatywnego `x:Array` zapewnia alternatywny Obsługa zawartość tekst wewnętrzny. To zachowanie umożliwia typy, które nie mogą być obsługiwane przez istniejącego modelu zawartości można grupować w tablicy i odwołuje się w dalszej części kodu powiązanego podczas uzyskiwania dostępu do tablicy o nazwie; Możesz wywołać <xref:System.Array> metod do pobrania tablicy poszczególne elementy.  
  
 Wszystkie rozszerzenia znaczników w XAML przy użyciu nawiasy klamrowe ({,} `)` w ich Składnia atrybutu, który jest Konwencji, za pomocą którego procesora XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć wartości atrybutu. Aby uzyskać więcej informacji na temat rozszerzeń znaczników w ogólności, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 W języku XAML 2009 `x:Array` jest zdefiniowany jako język pierwotnych zamiast rozszerzenia znaczników. Aby uzyskać więcej informacji, zobacz [typy wbudowane dla wspólnych elementów podstawowych języka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Zazwyczaj elementy obiektu wypełnić `x:Array` nie są elementami, które istnieją w [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] nazw XAML i muszą być mapowane prefiks przestrzeni nazw XAML innych niż domyślne.  
  
 Na przykład poniżej przedstawiono prosty tablicę dwa ciągi z `sys` prefiksu (a także `x`) zdefiniowane na poziomie tablicy.  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 Dla niestandardowych typów, które są używane jako elementy tablicy klasa muszą również obsługiwać wymagania dotyczące uruchamianiu jako elementy obiektu w języku XAML. Aby uzyskać więcej informacji, zobacz [XAML oraz klas niestandardowych dla WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia znaczników i WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Typy migrowane z WPF do System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
