---
title: DynamicResource — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: 5ccda8ba8f41a30e0ce1c832a6d3176b7fb8e8c2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646263"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource — Rozszerzenie znaczników
Zapewnia wartość dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dowolnego atrybutu właściwości, odraczając tę wartość jako odwołanie do zdefiniowanego zasobu. Zachowanie odnośnika dla tego zasobu jest analogiczne do wyszukiwania w czasie wykonywania.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>Użycie elementu właściwości języka XAML  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`key`|Klucz żądanego zasobu. Ten klucz został początkowo przypisany przez [x:Key Dyrektywy,](../../../desktop-wpf/xaml-services/xkey-directive.md) jeśli zasób `key` został utworzony <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> w znacznikach lub został dostarczony jako parametr podczas wywoływania, jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
 A `DynamicResource` utworzy wyrażenie tymczasowe podczas kompilacji początkowej i w ten sposób odroczy wyszukiwanie zasobów, dopóki żądana wartość zasobu nie jest faktycznie wymagana do skonstruowania obiektu. Może to być [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] potencjalnie po załadowaniu strony. Wartość zasobu zostanie znaleziona na podstawie wyszukiwania kluczy względem wszystkich aktywnych słowników zasobów, począwszy od bieżącego zakresu strony, i zostanie zastąpiona wyrażeniem zastępczym z kompilacji.  
  
> [!IMPORTANT]
> Pod względem pierwszeństwa właściwości zależności `DynamicResource` wyrażenie jest równoważne pozycji, w której stosowane jest odwołanie do zasobu dynamicznego. Jeśli ustawisz wartość lokalną dla właściwości, `DynamicResource` która wcześniej miała `DynamicResource` wyrażenie jako wartość lokalną, zostanie całkowicie usunięta. Aby uzyskać szczegółowe informacje, zobacz [Pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).  
  
 Niektóre scenariusze dostępu do zasobów `DynamicResource` są szczególnie odpowiednie dla, w przeciwieństwie do [rozszerzenia znaczników StaticResource](staticresource-markup-extension.md). Zobacz [Zasoby XAML,](../../../desktop-wpf/fundamentals/xaml-resources-define.md) aby zapoznać się z `DynamicResource` omówienia względnych zalet i wpływu na wydajność i `StaticResource`.  
  
 Określony <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> powinien odpowiadać istniejącemu zasobowi określonemu przez [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) na pewnym poziomie na stronie, aplikacji, dostępnych motywach kontroli i zasobach zewnętrznych lub zasobach systemowych, a wyszukiwanie zasobów będzie odbywać się w tej kolejności. Aby uzyskać więcej informacji na temat wyszukiwania zasobów statycznych i dynamicznych zasobów zasobów, zobacz [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Klucz zasobu może być dowolnym ciągiem zdefiniowanym w [gramatyki XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Klucz zasobu może być również inne <xref:System.Type>typy obiektów, takie jak . Klucz <xref:System.Type> ma zasadnicze znaczenie dla sposobu formantów mogą być stylizowane przez motywy. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia formantu](../controls/control-authoring-overview.md).  
  
 Interfejsy API wyszukiwania wartości zasobów, <xref:System.Windows.FrameworkElement.FindResource%2A>takie jak , postępuj zgodnie `DynamicResource`z tą samą logiką wyszukiwania zasobów, jak w przypadku .  
  
 Alternatywnym deklaratywnym sposobem odwoływania się do zasobu jest [rozszerzenie znaczników StaticResource](staticresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany `DynamicResource` po ciągu identyfikatora jest <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> przypisany <xref:System.Windows.DynamicResourceExtension> jako wartość podstawowej klasy rozszerzenia.  
  
 `DynamicResource`może być stosowany w składni elementu obiektu. W takim przypadku wymagane jest <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> określenie wartości właściwości.  
  
 `DynamicResource`może być również używany w użyciu atrybutu pełne, <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> który określa właściwość jako właściwość = parę wartości:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `DynamicResource` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] W implementacji procesora obsługi dla tego rozszerzenia <xref:System.Windows.DynamicResourceExtension> znaczników jest zdefiniowany przez klasę.  
  
 `DynamicResource`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w użyciu { i } znaków w składni atrybutu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] który jest konwencją, za pomocą której procesor rozpoznaje, że rozszerzenie znaczników musi przetwarzać atrybut. Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zasoby i kod](resources-and-code.md)
- [x:Key — dyrektywa](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource — Rozszerzenie znaczników](staticresource-markup-extension.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
