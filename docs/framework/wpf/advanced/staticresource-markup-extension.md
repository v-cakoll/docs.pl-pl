---
title: StaticResource — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: b15e2c0bac5610c6f1b10a640254236987c0bcf5
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458736"
---
# <a name="staticresource-markup-extension"></a>StaticResource — Rozszerzenie znaczników
Udostępnia wartość dowolnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu właściwości poprzez wyszukiwanie odwołania do już zdefiniowanego zasobu. Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie ładowania, które będzie szukać zasobów, które zostały wcześniej załadowane z adiustacji bieżącej strony [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a także innych źródeł aplikacji, i wygeneruje tę wartość zasobu jako właściwość wartość w obiektach czasu wykonywania.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`key`|Klucz dla żądanego zasobu. Ten klucz został początkowo przypisany przez [dyrektywę x:Key](../../xaml-services/x-key-directive.md) , jeśli zasób został utworzony w znaczniku lub został dostarczony jako parametr `key` podczas wywoływania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>, jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> `StaticResource` nie może próbować wykonać odwołania do przodu do zasobu, który jest bardziej leksykalny w pliku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Próba wykonania tej operacji nie jest obsługiwana, a nawet jeśli takie odwołanie nie powiedzie się, próba odwołania do przodu spowoduje naliczenie opłat za czas ładowania podczas przeszukiwania wewnętrznych tablic skrótów reprezentujących <xref:System.Windows.ResourceDictionary>. Aby uzyskać najlepsze wyniki, dostosuj kompozycję słowników zasobów, aby można było uniknąć odwołań do przodu. Jeśli nie możesz uniknąć odwołania do przodu, zamiast tego użyj [rozszerzenia znacznika DynamicResource —](dynamicresource-markup-extension.md) .  
  
 Określony <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> powinien odpowiadać istniejącemu zasobowi, identyfikowanemu z [dyrektywą x:Key](../../xaml-services/x-key-directive.md) na pewnym poziomie na stronie, aplikacji, dostępnych kompozycjach kontroli i zasobach zewnętrznych lub zasobów systemowych. Wyszukiwanie zasobów odbywa się w tej kolejności. Aby uzyskać więcej informacji o zachowaniu wyszukiwania zasobów dla zasobów statycznych i dynamicznych, zobacz [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Klucz zasobu może być dowolnym ciągiem zdefiniowanym w [gramatycename języka XAML](../../xaml-services/xamlname-grammar.md). Klucz zasobu może być również innymi typami obiektów, takimi jak <xref:System.Type>. Klucz <xref:System.Type> ma podstawowe znaczenie dla kontrolek, które mogą być wzorowane przez motywy, za pomocą klucza stylu niejawnego. Aby uzyskać więcej informacji, zobacz temat [Tworzenie kontroli — przegląd](../controls/control-authoring-overview.md).  
  
 Alternatywny sposób deklaratywny odwołujący się do zasobu to [rozszerzenie znacznika DynamicResource —](dynamicresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po ciągu identyfikatora `StaticResource` jest przypisywany jako wartość <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> źródłowej klasy rozszerzenia <xref:System.Windows.StaticResourceExtension>.  
  
 `StaticResource` można używać w składni elementu obiektu. W takim przypadku należy określić wartość właściwości <xref:System.Windows.StaticResourceExtension.ResourceKey%2A>.  
  
 `StaticResource` można również użyć w pełnym użyciu atrybutu, który określa właściwość <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> jako parę właściwość = wartość:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `StaticResource` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 W implementacji procesora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.StaticResourceExtension>.  
  
 `StaticResource` to rozszerzenie znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą której procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zasoby i kod](resources-and-code.md)
