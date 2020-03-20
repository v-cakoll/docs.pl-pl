---
title: TemplateBinding — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 8cebbf717f66b072bc84b2068193ff2fe76ea87b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187282"
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding — Rozszerzenie znaczników
Łączy wartość właściwości w szablonie formantu w taki sposób, że staje się ona wartością innej właściwości w formancie z szablonem.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>Użycie atrybutu języka XAML (we właściwości settera w szablonie lub stylu)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>właściwości ustawionej w składni ustawiacza.|  
|`sourceProperty`|Inna właściwość zależności, która istnieje na typie, <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>który jest szablonem, określony przez jego .<br /><br /> — lub —<br /><br /> „Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon. To jest <xref:System.Windows.PropertyPath>rzeczywiście . Zobacz [Składnia XAML ścieżki właściwości](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Uwagi  
 A `TemplateBinding` jest zoptymalizowaną formą [Powiązania](binding-markup-extension.md) dla scenariuszy szablonów, analogiczną do skonstruowanej `Binding` za pomocą `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`programu . A `TemplateBinding` jest zawsze jednokierunkowe powiązanie, nawet jeśli właściwości zaangażowane domyślnie do wiązania dwukierunkowego. Obie używane właściwości muszą być właściwościami zależności. Aby osiągnąć dwukierunkowe powiązanie z elementem nadrzędnym szablonem, użyj następującej instrukcji powiązania `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`zamiast .
  
 [RelativeSource](relativesource-markupextension.md) to kolejne rozszerzenie znaczników, które jest czasami `TemplateBinding` używane w połączeniu z lub zamiast w celu wykonania powiązania właściwości względnej w szablonie.  
  
 Opisywanie szablonów formantu jako koncepcji nie jest tutaj omówione; Aby uzyskać więcej informacji, zobacz [Style sterowania i szablony](../controls/control-styles-and-templates.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany `TemplateBinding` po ciągu identyfikatora jest <xref:System.Windows.TemplateBindingExtension.Property%2A> przypisany <xref:System.Windows.TemplateBindingExtension> jako wartość podstawowej klasy rozszerzenia.  
  
 Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania. `TemplateBinding`służy do wypełniania wartości w obrębie ustawiaczy, przy użyciu obliczonych `TemplateBinding` wyrażeń, a używanie składni elementu obiektu do wypełniania `<Setter.Property>` składni elementu właściwości jest niepotrzebnie pełne.  
  
 `TemplateBinding`może być również używany w użyciu atrybutu pełne, <xref:System.Windows.TemplateBindingExtension.Property%2A> który określa właściwość jako właściwość = parę wartości:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `TemplateBinding` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML obsługa tego rozszerzenia znaczników jest definiowana <xref:System.Windows.TemplateBindingExtension> przez klasę.  
  
 `TemplateBinding`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w XAML używają `{` znaków i `}` w składni atrybutów, czyli konwencji, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znaczników musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource MarkupExtension](relativesource-markupextension.md)
- [Rozszerzenie znaczników powiązania](binding-markup-extension.md)
