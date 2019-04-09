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
ms.openlocfilehash: 4f4e26eb3e5ccaf66b2173c7fc9952375c5f2a58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139142"
---
# <a name="xarray-markup-extension"></a>x:Array — Rozszerzenie znaczników
Oferuje ogólną pomoc techniczną dla tablic obiektów w XAML poprzez rozszerzenie znaczników. Odpowiada to `x:ArrayExtension` typu XAML w [MS-XAML].  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`typeName`|Nazwa typu, Twoje `x:Array` będzie zawierać. `typeName` może być (i często jest) prefiks dla XAML przestrzeń nazw zawierająca XAML definicje typów.|  
|`arrayContents`|Zawartość elementów, która jest przypisana do wewnętrznych `ArrayExtension.Items` właściwości. Zazwyczaj te elementy są określane jako co najmniej jeden obiekt zawartym w elemencie `x:Array` znaczników otwierających i zamykających. Obiekty określone w tym polu powinny być można przypisać do typu XAML określonego w `typeName`.|  
  
## <a name="remarks"></a>Uwagi  
 `Type` jest wymaganego atrybutu dla wszystkich `x:Array` obiektu elementów. A `Type` wartość parametru nie trzeba używać `x:Type` — rozszerzenie znaczników; krótką nazwę typu jest typu XAML, który może być określony jako ciąg.  
  
 W przypadku wdrażania usług programu .NET Framework XAML, relacji między typ XAML w danych wejściowych i wyjściowych CLR <xref:System.Type> z utworzona tablica ma wpływ kontekst usługi rozszerzenia znaczników. Dane wyjściowe <xref:System.Type> jest <xref:System.Xaml.XamlType.UnderlyingType%2A> wejściowego typu XAML, po wyszukaniu niezbędne <xref:System.Xaml.XamlType> oparte na kontekst schematu XAML i <xref:System.Windows.Markup.IXamlTypeResolver> dostarcza kontekst usługi.  
  
 Podczas przetwarzania zawartości tablicy są przypisane do `ArrayExtension.Items` wewnętrzną właściwość. W <xref:System.Windows.Markup.ArrayExtension> wdrażania, jest reprezentowane przez <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.  
  
 W implementacji .NET Framework XAML Services obsługi dla tego rozszerzenia znacznika jest definiowany przez <xref:System.Windows.Markup.ArrayExtension> klasy. <xref:System.Windows.Markup.ArrayExtension> nie jest zapieczętowany i może służyć jako podstawa dla implementacji rozszerzenia znaczników dla typu niestandardowego tablicy.  
  
 `x:Array` jest więcej przeznaczony dla ogólnych możliwość języka XAML. Ale `x:Array` może być również przydatne w przypadku określania wartości XAML niektórych właściwości, które przyjmują obsługiwane XAML kolekcji jako ich zawartość właściwości strukturalne. Na przykład można określić zawartość <xref:System.Collections.IEnumerable> właściwość o `x:Array` użycia.  
  
 `x:Array` jest rozszerzeniem znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. `x:Array` częściowo są wyjątkiem od tej reguły, ponieważ zamiast podawać inny atrybut obsługi wartości `x:Array` zapewnia alternatywną obsługę swoją zawartość tekst wewnętrzny. To zachowanie umożliwia typy, które nie mogą być obsługiwane przez istniejący model zawartości może być pogrupowane w tablicy i do których odwołuje się w dalszej części związanym z kodem, uzyskując dostęp do tablicy o nazwie; Możesz wywołać <xref:System.Array> metody w celu uzyskania tablicy poszczególne elementy.  
  
 Wszystkie rozszerzenia znaczników w XAML ujmować w nawiasy klamrowe ({,} `)` w składni swoich atrybutów, która jest Konwencja, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć wartość atrybutu. Aby uzyskać więcej informacji na temat rozszerzenia znaczników ogólnie rzecz biorąc, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 XAML 2009 roku `x:Array` jest zdefiniowany jako język pierwotnych zamiast rozszerzenia znaczników. Aby uzyskać więcej informacji, zobacz [typy wbudowane dla wspólnych elementów podstawowych języka XAML](built-in-types-for-common-xaml-language-primitives.md).  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użytkowania WPF  
 Zazwyczaj elementów obiektu, służące do wypełniania `x:Array` nie są elementami, które istnieją w [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przestrzeni nazw XAML i muszą być mapowane prefiks przestrzeni nazw XAML innych niż domyślne.  
  
 Na przykład Oto prostej tablicy dwa ciągi przy użyciu `sys` prefiksu (a także `x`) zdefiniowana na poziomie tablicy.  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 Niestandardowe typy, które są używane jako elementów tablicy klasa również musi obsługiwać wymagania dotyczące wystąpienia w XAML jako elementy obiektu. Aby uzyskać więcej informacji, zobacz [XAML oraz klas niestandardowe dla WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzenia znacznikowania i WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Typy migrowane z WPF do System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
