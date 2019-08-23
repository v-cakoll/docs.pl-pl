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
ms.openlocfilehash: 06355c64d36d2688ef027c1940688d4c87e51ec8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964798"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource — Rozszerzenie znaczników
Udostępnia wartość dowolnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów właściwości przez odroczenie tej wartości jako odwołania do zdefiniowanego zasobu. Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie wykonywania.  
  
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
|`key`|Klucz dla żądanego zasobu. Ten klucz został początkowo przypisany przez [dyrektywę x:Key](../../xaml-services/x-key-directive.md) , jeśli zasób został utworzony w znaczniku lub został dostarczony jako `key` parametr podczas wywoływania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> , jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `DynamicResource` utworzy wyrażenie tymczasowe podczas początkowej kompilacji i w ten sposób opóźnia Wyszukiwanie zasobów do momentu, gdy żądana wartość zasobu jest wymagana w celu skonstruowania obiektu. Może to być możliwe po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] załadowaniu strony. Wartość zasobu zostanie znaleziona na podstawie wyszukiwania kluczy względem wszystkich aktywnych słowników zasobów, zaczynając od bieżącego zakresu strony i jest zastępowana dla wyrażenia symbolu zastępczego z kompilacji.  
  
> [!IMPORTANT]
> W obszarze pierwszeństwo właściwości zależności `DynamicResource` wyrażenie jest równoznaczne z pozycją, w której jest stosowane dynamiczne odwołanie do zasobów. `DynamicResource` W`DynamicResource` przypadku ustawienia wartości lokalnej dla właściwości, która wcześniej zawierała wyrażenie jako wartość lokalną, zostaje całkowicie usunięty. Aby uzyskać szczegółowe informacje, zobacz [pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).  
  
 Niektóre scenariusze dostępu do zasobów są szczególnie odpowiednie `DynamicResource` dla, w przeciwieństwie do [rozszerzenia znacznika StaticResource](staticresource-markup-extension.md). Zobacz [zasoby XAML](xaml-resources.md) , aby poznać informacje o względnych wartościach i skutkach `DynamicResource` wydajności `StaticResource`i.  
  
 Określony <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> element powinien odpowiadać istniejącemu zasobowi określonemu przez [dyrektywę x:Key](../../xaml-services/x-key-directive.md) na pewnym poziomie na stronie, aplikacji, dostępnych kompozycjach kontroli i zasobach zewnętrznych lub zasobów systemowych, a wyszukiwanie zasobów zostanie wykonane w tej kolejności. Aby uzyskać więcej informacji na temat wyszukiwania zasobów dla zasobów statycznych i dynamicznych, zobacz [zasoby XAML](xaml-resources.md).  
  
 Klucz zasobu może być dowolnym ciągiem zdefiniowanym w [gramatycename języka XAML](../../xaml-services/xamlname-grammar.md). Klucz zasobu może być również innymi typami obiektów, takimi jak <xref:System.Type>. <xref:System.Type> Klucz ma podstawowe znaczenie dla formantów, które mogą być wzorowane na podstawie motywów. Aby uzyskać więcej informacji, zobacz temat [Tworzenie kontroli — przegląd](../controls/control-authoring-overview.md).  
  
 Interfejsy API do wyszukiwania wartości zasobów, <xref:System.Windows.FrameworkElement.FindResource%2A>na przykład, postępuj zgodnie z tą samą logiką wyszukiwania zasobów, która jest używana przez `DynamicResource`program.  
  
 Alternatywny sposób deklaratywny odwołujący się do zasobu to [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po `DynamicResource` ciągu identyfikatora jest przypisywany <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> jako wartość źródłowej <xref:System.Windows.DynamicResourceExtension> klasy rozszerzenia.  
  
 `DynamicResource`może być używany w składni elementu obiektu. W takim przypadku należy określić wartość <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwości.  
  
 `DynamicResource`można go również użyć w pełnym użyciu atrybutu, który określa <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwość jako pary właściwość = wartość:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `DynamicResource` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 W implementacji procesora obsługa tego <xref:System.Windows.DynamicResourceExtension> rozszerzenia znacznika jest definiowana przez klasę. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 `DynamicResource`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której procesor rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](xaml-resources.md)
- [Zasoby i kod](resources-and-code.md)
- [x:Key, dyrektywa](../../xaml-services/x-key-directive.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource, rozszerzenie znaczników](staticresource-markup-extension.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
