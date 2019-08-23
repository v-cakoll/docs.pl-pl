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
ms.openlocfilehash: 7392be182aedeeebe6b7092f9868c1fabfaafcb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963462"
---
# <a name="staticresource-markup-extension"></a>StaticResource — Rozszerzenie znaczników
Udostępnia wartość dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu właściwości przez wyszukanie odwołania do już zdefiniowanego zasobu. Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie ładowania, które będzie szukać zasobów, które zostały wcześniej załadowane z adiustacji bieżącej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony, a także innych źródeł aplikacji, i spowoduje wygenerowanie tej wartości zasobu jako wartość właściwości w obiektach czasu wykonywania.  
  
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
|`key`|Klucz dla żądanego zasobu. Ten klucz został początkowo przypisany przez [dyrektywę x:Key](../../xaml-services/x-key-directive.md) , jeśli zasób został utworzony w znaczniku lub został dostarczony jako `key` parametr podczas wywoływania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> , jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> A `StaticResource` nie może próbować wykonać odwołania do przodu do zasobu, który jest bardziej leksykalny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w pliku. Próba wykonania tej operacji nie jest obsługiwana, a nawet jeśli takie odwołanie nie powiedzie się, próba odwołania do przodu spowoduje naliczenie opłat za czas ładowania podczas przeszukiwania wewnętrznych tablic <xref:System.Windows.ResourceDictionary> skrótów. Aby uzyskać najlepsze wyniki, dostosuj kompozycję słowników zasobów, aby można było uniknąć odwołań do przodu. Jeśli nie możesz uniknąć odwołania do przodu, zamiast tego użyj [rozszerzenia znacznika DynamicResource —](dynamicresource-markup-extension.md) .  
  
 Określony <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> element powinien odpowiadać istniejącemu zasobowi, identyfikowanemu z [dyrektywą x:Key](../../xaml-services/x-key-directive.md) na pewnym poziomie na stronie, aplikacji, dostępnych motywów kontroli i zasobach zewnętrznych lub zasobów systemowych. Wyszukiwanie zasobów odbywa się w tej kolejności. Aby uzyskać więcej informacji o zachowaniu wyszukiwania zasobów dla zasobów statycznych i dynamicznych, zobacz [zasoby XAML](xaml-resources.md).  
  
 Klucz zasobu może być dowolnym ciągiem zdefiniowanym w [gramatycename języka XAML](../../xaml-services/xamlname-grammar.md). Klucz zasobu może być również innymi typami obiektów, takimi jak <xref:System.Type>. <xref:System.Type> Klucz ma podstawowe znaczenie dla kontrolek, które mogą być wzorowane przez motywy, za pomocą klucza stylu niejawnego. Aby uzyskać więcej informacji, zobacz temat [Tworzenie kontroli — przegląd](../controls/control-authoring-overview.md).  
  
 Alternatywny sposób deklaratywny odwołujący się do zasobu to [rozszerzenie znacznika DynamicResource —](dynamicresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po `StaticResource` ciągu identyfikatora jest przypisywany <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> jako wartość źródłowej <xref:System.Windows.StaticResourceExtension> klasy rozszerzenia.  
  
 `StaticResource`może być używany w składni elementu obiektu. W takim przypadku należy określić wartość <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwości.  
  
 `StaticResource`można go również użyć w pełnym użyciu atrybutu, który określa <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwość jako pary właściwość = wartość:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `StaticResource` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 W implementacji procesora obsługa tego <xref:System.Windows.StaticResourceExtension> rozszerzenia znacznika jest definiowana przez klasę. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 `StaticResource`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której procesor rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Zasoby XAML](xaml-resources.md)
- [Zasoby i kod](resources-and-code.md)
