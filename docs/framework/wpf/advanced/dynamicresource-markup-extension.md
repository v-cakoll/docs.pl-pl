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
ms.openlocfilehash: c09d009a8cc90e050f6cfb1a8d2abd5c61c5b19f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545327"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource — Rozszerzenie znaczników
Zawiera wartość dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu właściwości przez odkładanie tej wartości jako odwołanie do określonych zasobów. Zachowanie wyszukiwania dla tego zasobu jest odpowiednikiem odnośników czasu wykonywania.  
  
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
|`key`|Klucz do żądanego zasobu. Ten klucz była początkowo przypisana przez [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) zasób został utworzony w znaczniku, czy podany jako `key` parametr podczas wywoływania metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
 A `DynamicResource` spowoduje to utworzenie tymczasowego wyrażenie podczas początkowej kompilacji i w związku z tym odroczenie wyszukiwania zasobów, dopóki wartość żądany zasób nie zostanie faktycznie wymagane do utworzenia obiektu. Może to być potencjalnie po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] załadowanej strony. Wartość zasobu zostaną znalezione w oparciu klucza wyszukiwania względem wszystkich słowniki zasobów active, zaczynając od bieżącego zakresu strony i zastępuje symbol zastępczy wyrażenie z kompilacji.  
  
> [!IMPORTANT]
>  Pod względem pierwszeństwo właściwości zależności `DynamicResource` wyrażenie jest odpowiednikiem sytuację, w których stosowane jest odwołanie do zasobu dynamicznego. Jeśli ustawisz wartości lokalnej dla właściwości, która wcześniej była `DynamicResource` wyrażenia jako wartości lokalnej `DynamicResource` zostanie całkowicie usunięta. Aby uzyskać więcej informacji, zobacz [pierwszeństwo wartość właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Są szczególnie odpowiednie dla scenariuszy dostępu do niektórych zasobów `DynamicResource` w przeciwieństwie do [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) omówienie o względnych zalet i wpływu na wydajność programu `DynamicResource` i `StaticResource`.  
  
 Określony <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> powinien odpowiadać istniejący zasób ustaleniami [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) na określonym poziomie w ze strony, aplikacji, kompozycje dostępne kontrolki i zasobów zewnętrznych lub zasobów systemowych i Wyszukiwanie zasobów nastąpi w podanej kolejności. Aby uzyskać więcej informacji na temat wyszukiwania zasobów dla statycznych i dynamicznych zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Klucz zasobu może być zdefiniowany w [xamlname — gramatyka](../../../../docs/framework/xaml-services/xamlname-grammar.md). Klucz zasobu może być również innych obiektów, takich jak <xref:System.Type>. A <xref:System.Type> klucza jest niezbędne, aby jak formanty można wstawiony przez motywów. Aby uzyskać więcej informacji, zobacz [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Podczas wyszukiwania wartości zasobów takich jak <xref:System.Windows.FrameworkElement.FindResource%2A>, postępuj zgodnie z tej samej logiki wyszukiwania zasobów jako używane przez `DynamicResource`.  
  
 Deklaracyjne alternatywnych środków odwołujące się do zasobu jest jako [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu po `DynamicResource` przypisany jako identyfikator ciągu <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> wartości podstawowych <xref:System.Windows.DynamicResourceExtension> rozszerzenie klasy.  
  
 `DynamicResource` można w składni elementu obiekt. W takim przypadku określającą wartość <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwość jest wymagana.  
  
 `DynamicResource` można również w Określa użycie atrybutu pełne <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwości jako właściwość = pary wartości:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `DynamicResource` ma tylko jedną można ustawić właściwości, która jest wymagana, to użycie Pełne nie są typowe.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.DynamicResourceExtension> klasy.  
  
 `DynamicResource` to rozszerzenie znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w ich składni atrybutu Konwencji za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Zasoby i kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [x:Key, dyrektywa](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [StaticResource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
