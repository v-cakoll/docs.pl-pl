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
ms.openlocfilehash: d425d17405bc8241c3fd85c77c6672265a060900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546923"
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
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> właściwości ustawione w składni metody ustawiającej.|  
|`sourceProperty`|Inna właściwość zależności, który istnieje w typie szablonem, określony przez jego <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> - lub -<br /><br /> „Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon. Jest to rzeczywiście <xref:System.Windows.PropertyPath>. Zobacz [składnia PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Uwagi  
 A `TemplateBinding` jest zoptymalizowany formę [powiązanie](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) dla scenariuszy szablonu odpowiednikiem `Binding` skonstruowany przy `{Binding RelativeSource={RelativeSource TemplatedParent}}`. A `TemplateBinding` jest zawsze jednokierunkowe powiązanie, nawet jeśli właściwości domyślnie powiązanie dwustronne. Obie używane właściwości muszą być właściwościami zależności.  
  
 [RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) jest inne rozszerzenie znaczników, która czasami jest używane w połączeniu z lub a `TemplateBinding` w celu wykonywania powiązania właściwości względne w ramach szablonu.  
  
 Opisujące szablonów kontrolki jako koncepcji nie pasuje do Aby uzyskać więcej informacji, zobacz [stylów formantu i szablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu po `TemplateBinding` przypisany jako identyfikator ciągu <xref:System.Windows.TemplateBindingExtension.Property%2A> wartości podstawowych <xref:System.Windows.TemplateBindingExtension> rozszerzenie klasy.  
  
 Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania. `TemplateBinding` jest używany do wypełniania wyrażenia wartości w obrębie metody ustawiające, przy użyciu obliczone i przy użyciu obiektu składnia elementu `TemplateBinding` do wypełnienia `<Setter.Property>` jest niepotrzebnie pełne składni elementu właściwości.  
  
 `TemplateBinding` można również w Określa użycie atrybutu pełne <xref:System.Windows.TemplateBindingExtension.Property%2A> właściwości jako właściwość = pary wartości:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `TemplateBinding` ma tylko jedną można ustawić właściwości, która jest wymagana, to użycie Pełne nie są typowe.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML, obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.TemplateBindingExtension> klasy.  
  
 `TemplateBinding` to rozszerzenie znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w XAML, użyj `{` i `}` znaków w ich składni atrybutu Konwencji, za pomocą którego procesora XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [RelativeSource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)  
 [Rozszerzenie znaczników powiązania](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
