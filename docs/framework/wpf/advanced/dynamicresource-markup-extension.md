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
ms.openlocfilehash: 579fae46a7c53a61b728d7526ef397eb371abb74
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141071"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource — Rozszerzenie znaczników
Udostępnia wartość dowolnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów właściwości przez odroczenie tej wartości jako odwołania do zdefiniowanego zasobu. Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie wykonywania.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{DynamicResource key}" ... />  
```  
  
## <a name="xaml-property-element-usage"></a>Użycie elementu właściwości języka XAML  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`key`|Klucz dla żądanego zasobu. Ten klucz został początkowo przypisany przez [dyrektywę x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) , jeśli zasób został utworzony w znaczniku lub został dostarczony jako `key` parametr podczas wywoływania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> , jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `DynamicResource` utworzy wyrażenie tymczasowe podczas początkowej kompilacji i w ten sposób opóźnia Wyszukiwanie zasobów do momentu, gdy żądana wartość zasobu jest wymagana w celu skonstruowania obiektu. Może to być możliwe po załadowaniu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony. Wartość zasobu zostanie znaleziona na podstawie wyszukiwania kluczy względem wszystkich aktywnych słowników zasobów, zaczynając od bieżącego zakresu strony i jest zastępowana dla wyrażenia symbolu zastępczego z kompilacji.  
  
> [!IMPORTANT]
> W obszarze pierwszeństwo właściwości zależności `DynamicResource` wyrażenie jest równoznaczne z pozycją, w której jest stosowane dynamiczne odwołanie do zasobów. W `DynamicResource` `DynamicResource` przypadku ustawienia wartości lokalnej dla właściwości, która wcześniej zawierała wyrażenie jako wartość lokalną, zostaje całkowicie usunięty. Aby uzyskać szczegółowe informacje, zobacz [pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).  
  
 Niektóre scenariusze dostępu do zasobów są szczególnie odpowiednie `DynamicResource` dla, w przeciwieństwie do [rozszerzenia znacznika StaticResource](staticresource-markup-extension.md). Zobacz [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) , aby poznać informacje o względnych wartościach i skutkach `DynamicResource` wydajności `StaticResource`i.  
  
 Określony <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> element powinien odpowiadać istniejącemu zasobowi określonemu przez [dyrektywę x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) na pewnym poziomie na stronie, aplikacji, dostępnych kompozycjach kontroli i zasobach zewnętrznych, a także w tej kolejności Wyszukiwanie zasobów. Aby uzyskać więcej informacji na temat wyszukiwania zasobów dla zasobów statycznych i dynamicznych, zobacz [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Klucz zasobu może być dowolnym ciągiem zdefiniowanym w [gramatycename języka XAML](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Klucz zasobu może być również innymi typami obiektów, takimi jak <xref:System.Type>. <xref:System.Type> Klucz ma podstawowe znaczenie dla formantów, które mogą być wzorowane na podstawie motywów. Aby uzyskać więcej informacji, zobacz temat [Tworzenie kontroli — przegląd](../controls/control-authoring-overview.md).  
  
 Interfejsy API do wyszukiwania wartości zasobów, na przykład <xref:System.Windows.FrameworkElement.FindResource%2A>, postępuj zgodnie z tą samą logiką wyszukiwania `DynamicResource`zasobów, która jest używana przez program.  
  
 Alternatywny sposób deklaratywny odwołujący się do zasobu to [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po ciągu `DynamicResource` identyfikatora jest przypisywany jako <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> wartość źródłowej <xref:System.Windows.DynamicResourceExtension> klasy rozszerzenia.  
  
 `DynamicResource`może być używany w składni elementu obiektu. W takim przypadku należy określić wartość <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwości.  
  
 `DynamicResource`można go również użyć w pełnym użyciu atrybutu, który określa <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwość jako pary właściwość = wartość:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" ... />  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `DynamicResource` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] W implementacji procesora obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.DynamicResourceExtension> klasę.  
  
 `DynamicResource`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której procesor rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zasoby i kod](resources-and-code.md)
- [x:Key — dyrektywa](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource — Rozszerzenie znaczników](staticresource-markup-extension.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
