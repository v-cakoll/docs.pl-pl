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
ms.openlocfilehash: a04e1569f77fed73a480fda3d63cabf6dbc30664
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460507"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource — Rozszerzenie znaczników
Udostępnia wartość dowolnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu właściwości przez odroczenie tej wartości jako odwołania do zdefiniowanego zasobu. Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie wykonywania.  
  
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
|`key`|Klucz dla żądanego zasobu. Ten klucz został początkowo przypisany przez [dyrektywę x:Key](../../xaml-services/x-key-directive.md) , jeśli zasób został utworzony w znaczniku lub został dostarczony jako parametr `key` podczas wywoływania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>, jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
 `DynamicResource` utworzy tymczasowe wyrażenie podczas początkowej kompilacji i w ten sposób opóźnia Wyszukiwanie zasobów do momentu, gdy żądana wartość zasobu jest wymagana w celu skonstruowania obiektu. Może to być możliwe po załadowaniu strony [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Wartość zasobu zostanie znaleziona na podstawie wyszukiwania kluczy względem wszystkich aktywnych słowników zasobów, zaczynając od bieżącego zakresu strony i jest zastępowana dla wyrażenia symbolu zastępczego z kompilacji.  
  
> [!IMPORTANT]
> W obszarze pierwszeństwo właściwości zależności wyrażenie `DynamicResource` jest równoznaczne z pozycją, w której jest stosowane dynamiczne odwołanie do zasobów. Jeśli ustawisz wartość lokalną dla właściwości, która wcześniej zawierała wyrażenie `DynamicResource` jako wartość lokalna, `DynamicResource` zostanie całkowicie usunięta. Aby uzyskać szczegółowe informacje, zobacz [pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).  
  
 Niektóre scenariusze dostępu do zasobów są szczególnie odpowiednie dla `DynamicResource`, w przeciwieństwie do [rozszerzenia znacznika StaticResource](staticresource-markup-extension.md). Zobacz [zasoby XAML](xaml-resources.md) , aby poznać informacje o względnych wartościach i wpływach wydajności `DynamicResource` i `StaticResource`.  
  
 Określony <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> powinien odpowiadać istniejącemu zasobowi, który został określony przez [dyrektywę x:Key](../../xaml-services/x-key-directive.md) na pewnym poziomie na stronie, aplikacji, dostępnych motywów kontroli i zasobach zewnętrznych lub zasobów systemowych, a wyszukiwanie zasobów nastąpi w Ta kolejność. Aby uzyskać więcej informacji na temat wyszukiwania zasobów dla zasobów statycznych i dynamicznych, zobacz [zasoby XAML](xaml-resources.md).  
  
 Klucz zasobu może być dowolnym ciągiem zdefiniowanym w [gramatycename języka XAML](../../xaml-services/xamlname-grammar.md). Klucz zasobu może być również innymi typami obiektów, takimi jak <xref:System.Type>. Klucz <xref:System.Type> ma podstawowe znaczenie dla formantów, które mogą być wzorowane przez motywy. Aby uzyskać więcej informacji, zobacz temat [Tworzenie kontroli — przegląd](../controls/control-authoring-overview.md).  
  
 Interfejsy API do wyszukiwania wartości zasobów, takich jak <xref:System.Windows.FrameworkElement.FindResource%2A>, postępuj zgodnie z tą samą logiką wyszukiwania zasobów, która jest używana przez `DynamicResource`.  
  
 Alternatywny sposób deklaratywny odwołujący się do zasobu to [rozszerzenie znacznika StaticResource](staticresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po ciągu identyfikatora `DynamicResource` jest przypisywany jako wartość <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> źródłowej klasy rozszerzenia <xref:System.Windows.DynamicResourceExtension>.  
  
 `DynamicResource` można używać w składni elementu obiektu. W takim przypadku należy określić wartość właściwości <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>.  
  
 `DynamicResource` można również użyć w pełnym użyciu atrybutu, który określa właściwość <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> jako parę właściwość = wartość:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `DynamicResource` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 W implementacji procesora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.DynamicResourceExtension>.  
  
 `DynamicResource` to rozszerzenie znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą której procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](xaml-resources.md)
- [Zasoby i kod](resources-and-code.md)
- [x:Key, dyrektywa](../../xaml-services/x-key-directive.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource, rozszerzenie znaczników](staticresource-markup-extension.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
