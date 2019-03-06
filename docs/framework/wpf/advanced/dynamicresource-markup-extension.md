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
ms.openlocfilehash: a7b754ce3fb77314539e6391376b188fe9b15859
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369776"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource — Rozszerzenie znaczników
Zawiera wartość dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] właściwości atrybutu przez tę wartość jako odwołanie do zasobu zdefiniowanego opóźnienie. Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie wykonywania.  
  
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
|`key`|Klucz dla żądanego zasobu. Ten klucz była początkowo przypisana przez [x: Key — dyrektywa](../../xaml-services/x-key-directive.md) zasób został utworzony w znaczniku, czy została podana jako `key` parametru podczas wywoływania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
 A `DynamicResource` spowoduje to utworzenie tymczasowego wyrażenie podczas początkowej kompilacji i związku z tym Odrocz wyszukiwania dla zasobów, dopóki wartość faktycznie wymagane w celu utworzenia obiektu żądanego zasobu. Może to być potencjalnie po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strona została załadowana. Wartość zasobu zostanie znaleziony, na podstawie klucza wyszukiwania względem wszystkich słowniki zasobów aktywne, począwszy od bieżącego zakresu strony i zostanie zastąpiony wyrażenia symbolu zastępczego z kompilacji.  
  
> [!IMPORTANT]
>  Pod względem następstwo właściwości `DynamicResource` wyrażenie jest odpowiednikiem sytuację, w której stosowana jest odwołanie do zasobu dynamicznych. Jeśli ustawisz wartości lokalnej dla właściwości, która miała wcześniej `DynamicResource` wyrażenia jako wartości lokalnej `DynamicResource` zostało całkowicie usunięte. Aby uzyskać więcej informacji, zobacz [następstwo wartości właściwości](dependency-property-value-precedence.md).  
  
 Niektórych scenariuszy dostępu do zasobów są szczególnie odpowiednie dla `DynamicResource` w przeciwieństwie do [staticresource — rozszerzenie znaczników](staticresource-markup-extension.md). Zobacz [zasoby XAML](xaml-resources.md) omówienie względnych zalet i wpływ na wydajność `DynamicResource` i `StaticResource`.  
  
 Określony <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> powinien odpowiadać ustalany na podstawie istniejącego zasobu [x: Key — dyrektywa](../../xaml-services/x-key-directive.md) niektórych w na poziomie strony, aplikacji, motywy dostępne kontrolki i zasoby zewnętrzne lub zasobów systemowych i wyszukiwania zasobów będzie miało miejsce w tej kolejności. Aby uzyskać więcej informacji na temat wyszukiwania zasobów dla zasobów statycznych i dynamicznych, zobacz [zasoby XAML](xaml-resources.md).  
  
 Klucz zasobu może być dowolnym ciągiem, zdefiniowane w [xamlname — gramatyka](../../xaml-services/xamlname-grammar.md). Klucz zasobu może być również inne typy obiektów, takich jak <xref:System.Type>. A <xref:System.Type> klucza ma podstawowe znaczenie dla jak formanty mogą być ich styl, kompozycje. Aby uzyskać więcej informacji, zobacz [omówienie tworzenia kontrolek](../controls/control-authoring-overview.md).  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Podczas wyszukiwania wartości zasobów takich jak <xref:System.Windows.FrameworkElement.FindResource%2A>, wykonaj tę samą logikę wyszukiwania zasobów jako używaną przez `DynamicResource`.  
  
 Deklaratywne alternatywnych metod odwołujące się do zasobu jest jako [staticresource — rozszerzenie znaczników](staticresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podawany po `DynamicResource` ciągu identyfikatora jest przypisany jako <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> wartości elementu bazowego <xref:System.Windows.DynamicResourceExtension> rozszerzenie klasy.  
  
 `DynamicResource` może służyć w składni obiektów. W tym przypadku określającą wartość <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwość jest wymagana.  
  
 `DynamicResource` można również użycie pełnego atrybut określający <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwość jako właściwość = para wartości:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `DynamicResource` ma tylko jedną konfigurowalną właściwość, która jest wymagana, użycie tych pełne nie są typowe.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora obsługi dla tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.DynamicResourceExtension> klasy.  
  
 `DynamicResource` jest rozszerzeniem znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także
- [Zasoby XAML](xaml-resources.md)
- [Zasoby i kod](resources-and-code.md)
- [x:Key, dyrektywa](../../xaml-services/x-key-directive.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource, rozszerzenie znaczników](staticresource-markup-extension.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
