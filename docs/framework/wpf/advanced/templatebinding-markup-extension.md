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
ms.openlocfilehash: 69698db8b51e3872d5941d4fba67271b1e61226e
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140459"
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding — Rozszerzenie znaczników
Łączy wartość właściwości w szablonie formantu w taki sposób, że staje się ona wartością innej właściwości w formancie z szablonem.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{TemplateBinding sourceProperty}" ... />
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>Użycie atrybutu języka XAML (we właściwości settera w szablonie lub stylu)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" ... />  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>Właściwości ustawianej we składni metody ustawiającej.|  
|`sourceProperty`|Inna właściwość zależności, która istnieje w typie tworzonym przez szablon, określona przez <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>jego wartość.<br /><br /> — lub —<br /><br /> „Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon. Jest to w <xref:System.Windows.PropertyPath>rzeczywistości. Zobacz [składnię XAML PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Uwagi  
 A `TemplateBinding` to zoptymalizowana postać [powiązania](binding-markup-extension.md) dla scenariuszy szablonów, analogiczne do `Binding` zbudowane z. `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}` `TemplateBinding` Jest zawsze powiązanie jednokierunkowe, nawet jeśli właściwości są domyślnie powiązane z powiązaniem dwukierunkowym. Obie używane właściwości muszą być właściwościami zależności. Aby uzyskać dwukierunkowe powiązanie z szablonem nadrzędnym, użyj w zamian `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`następującej instrukcji Binding.
  
 [RelativeSource](relativesource-markupextension.md) to inne rozszerzenie znaczników, które jest czasami używane w połączeniu z lub zamiast `TemplateBinding` w celu wykonania względnego powiązania właściwości w ramach szablonu.  
  
 Opisywanie szablonów kontrolek jako koncepcji nie jest tutaj omówione; Aby uzyskać więcej informacji, zobacz [Style formantów i szablony](../controls/control-styles-and-templates.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po ciągu `TemplateBinding` identyfikatora jest przypisywany jako <xref:System.Windows.TemplateBindingExtension.Property%2A> wartość źródłowej <xref:System.Windows.TemplateBindingExtension> klasy rozszerzenia.  
  
 Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania. `TemplateBinding`służy do wypełniania wartości w metodach ustawiających przy użyciu wyrażeń obliczanych i użycie składni `TemplateBinding` elementu obiektu `<Setter.Property>` dla do wypełniania składni elementu właściwości jest niepotrzebnie pełne.  
  
 `TemplateBinding`można go również użyć w pełnym użyciu atrybutu, który określa <xref:System.Windows.TemplateBindingExtension.Property%2A> właściwość jako pary właściwość = wartość:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" ... />
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `TemplateBinding` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 W implementacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesora XAML obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.TemplateBindingExtension> klasę.  
  
 `TemplateBinding`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w języku XAML używają `{` znaków `}` i w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource MarkupExtension](relativesource-markupextension.md)
- [Rozszerzenie znaczników powiązania](binding-markup-extension.md)
