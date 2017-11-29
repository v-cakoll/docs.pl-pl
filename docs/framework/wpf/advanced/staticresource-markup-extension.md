---
title: "StaticResource — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 821cd152ccb7a02dda5338d6a3ec44d6625c0097
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="staticresource-markup-extension"></a>StaticResource — Rozszerzenie znaczników
Zawiera wartość dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu właściwości wyszukując odwołanie do zasobu już zdefiniowane. Zachowanie wyszukiwania dla tego zasobu jest odpowiednikiem wyszukiwanie czas ładowania, które będzie wyglądać na zasoby, które wcześniej zostały załadowane z poziomu znacznika bieżącego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony oraz innych źródeł aplikacji i wygeneruje tej wartości zasobu jako wartość właściwości w obiektach czasu wykonywania.  
  
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
|`key`|Klucz do żądanego zasobu. Ten klucz była początkowo przypisana przez [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) zasób został utworzony w znaczniku, czy podany jako `key` parametr podczas wywoływania metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  A `StaticResource` nie należy próbować do przodu odnieść się do zasobu, która jest zdefiniowana lexically dalsze w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Próby nie jest obsługiwany, a nawet, jeśli odniesienie nie powiedzie się, próby odwołaniem w przód będzie spowodować zmniejszenie wydajności czasu obciążenia podczas tabel skrótu wewnętrznego reprezentujące <xref:System.Windows.ResourceDictionary> są przeszukiwane. Aby uzyskać najlepsze rezultaty należy dopasować kompozycji słownikach zasobów tak, aby uniknąć odwołania w przód. Jeśli nie można uniknąć odwołaniem w przód, użyj [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) zamiast tego.  
  
 Określony <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> powinien odpowiadać istniejącego zasobu, oznaczone symbolem [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) na określonym poziomie w ze strony, aplikacji, kompozycje dostępne kontrolki i zasobów zewnętrznych lub zasoby systemowe. Wyszukiwanie zasobów występuje w podanej kolejności. Aby uzyskać więcej informacji na temat zachowanie wyszukiwania zasobów dla statycznych i dynamicznych zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Klucz zasobu może być zdefiniowany w [xamlname — gramatyka](../../../../docs/framework/xaml-services/xamlname-grammar.md). Klucz zasobu można też inne typy obiektów, takich jak <xref:System.Type>. A <xref:System.Type> klucza jest niezbędne, aby jak formantów można wstawiony przez kompozycje, za pomocą klucza niejawne stylu. Aby uzyskać więcej informacji, zobacz [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Deklaracyjne alternatywnych środków odwołujące się do zasobu jest jako [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu po `StaticResource` przypisany jako identyfikator ciągu <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> wartości podstawowych <xref:System.Windows.StaticResourceExtension> rozszerzenie klasy.  
  
 `StaticResource`można w składni elementu obiekt. W takim przypadku określającą wartość <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwość jest wymagana.  
  
 `StaticResource`można również w Określa użycie atrybutu pełne <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwości jako właściwość = pary wartości:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `StaticResource` ma tylko jedną można ustawić właściwości, która jest wymagana, to użycie Pełne nie są typowe.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.StaticResourceExtension> klasy.  
  
 `StaticResource`to rozszerzenie znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w ich składni atrybutu Konwencji za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Zasoby dla języka XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Zasoby i kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)
