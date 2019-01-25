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
ms.openlocfilehash: 3ae17dc98137bd417d2468fb0415fb2078acf20f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686026"
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
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> właściwości ustawiany w składni settera.|  
|`sourceProperty`|Inna właściwość zależności istniejąca w typie są oparte na szablonach, określony przez jego <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> - lub -<br /><br /> „Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon. Jest to rzeczywiście <xref:System.Windows.PropertyPath>. Zobacz [składnia elementu PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Uwagi  
 A `TemplateBinding` jest zoptymalizowane formą [powiązanie](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) dla scenariuszy szablonów, analogiczne do `Binding` skonstruowany przy użyciu `{Binding RelativeSource={RelativeSource TemplatedParent}}`. Element `TemplateBinding` jest zawsze powiązaniem jednokierunkowym, nawet jeśli jego właściwości domyślnie określają powiązanie dwukierunkowe. Obie używane właściwości muszą być właściwościami zależności. Aby osiągnąć określają powiązanie dwukierunkowe oparte na szablonach nadrzędnej następującą instrukcję powiązanie zamiast tego użyj `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`. 
  
 [RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) jest kolejnym rozszerzeniem znacznika, którego używa się czasami w połączeniu lub zamiast `TemplateBinding` w celu względnego powiązania właściwości w szablonie.  
  
 Opisujące szablony kontrolek jako koncepcja nie jest objęty tutaj; Aby uzyskać więcej informacji, zobacz [style i szablony kontrolek](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podawany po `TemplateBinding` ciągu identyfikatora jest przypisany jako <xref:System.Windows.TemplateBindingExtension.Property%2A> wartości elementu bazowego <xref:System.Windows.TemplateBindingExtension> rozszerzenie klasy.  
  
 Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania. `TemplateBinding` Służy do wypełnienia wartości setterami przy użyciu obliczane wyrażenia, a za pomocą składni obiektów `TemplateBinding` do wypełnienia `<Setter.Property>` składni elementu właściwości to niepotrzebne powielenie informacji.  
  
 `TemplateBinding` można również użycie pełnego atrybut określający <xref:System.Windows.TemplateBindingExtension.Property%2A> właściwość jako właściwość = para wartości:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `TemplateBinding` ma tylko jedną konfigurowalną właściwość, która jest wymagana, użycie tych pełne nie są typowe.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML, obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.TemplateBindingExtension> klasy.  
  
 `TemplateBinding` jest rozszerzeniem znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w XAML użyj `{` i `}` znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [RelativeSource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)
- [Rozszerzenie znaczników powiązania](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
