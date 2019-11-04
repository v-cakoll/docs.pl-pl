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
ms.openlocfilehash: 399e4ac223d2fcb728ece2c92d25a087990992f2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458670"
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
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> właściwości ustawianej we składni metody ustawiającej.|  
|`sourceProperty`|Inna właściwość zależności, która istnieje w typie tworzonym przez szablon, określony przez jego <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> oraz<br /><br /> „Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon. Jest to w rzeczywistości <xref:System.Windows.PropertyPath>. Zobacz [składnię XAML PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Uwagi  
 `TemplateBinding` to zoptymalizowana postać [powiązania](binding-markup-extension.md) dla scenariuszy szablonów, analogiczna do `Binding` skonstruowana przy użyciu `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding` jest zawsze powiązanie jednokierunkowe, nawet jeśli właściwości są domyślnie powiązane z powiązaniem dwukierunkowym. Obie używane właściwości muszą być właściwościami zależności. Aby uzyskać dwukierunkowe powiązanie z szablonem nadrzędnym, użyj poniższego instrukcji Binding zamiast `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`. 
  
 [RelativeSource](relativesource-markupextension.md) to inne rozszerzenie znaczników, które jest czasami używane w połączeniu z lub zamiast `TemplateBinding`, aby można było wykonać powiązanie właściwości względnej w ramach szablonu.  
  
 Opisywanie szablonów kontrolek jako koncepcji nie jest tutaj omówione; Aby uzyskać więcej informacji, zobacz [Style formantów i szablony](../controls/control-styles-and-templates.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po ciągu identyfikatora `TemplateBinding` jest przypisywany jako wartość <xref:System.Windows.TemplateBindingExtension.Property%2A> źródłowej klasy rozszerzenia <xref:System.Windows.TemplateBindingExtension>.  
  
 Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania. `TemplateBinding` służy do wypełniania wartości w metodach ustawiających przy użyciu wyrażeń obliczanych i używania składni elementu obiektu dla `TemplateBinding` do wypełnienia składni `<Setter.Property>` elementu właściwości jest niepotrzebnie pełne.  
  
 `TemplateBinding` można również użyć w pełnym użyciu atrybutu, który określa właściwość <xref:System.Windows.TemplateBindingExtension.Property%2A> jako parę właściwość = wartość:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `TemplateBinding` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 W implementacji procesora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.TemplateBindingExtension>.  
  
 `TemplateBinding` to rozszerzenie znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w języku XAML używają znaków `{` i `}` w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource, rozszerzenie znaczników](relativesource-markupextension.md)
- [Rozszerzenie znaczników powiązania](binding-markup-extension.md)
