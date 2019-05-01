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
ms.openlocfilehash: 8319e451268152e95326c02027157db72df631b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981906"
---
# <a name="staticresource-markup-extension"></a>StaticResource — Rozszerzenie znaczników
Zawiera wartość dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] właściwości atrybutu przez wyszukanie odwołanie do zasobu już zdefiniowane. Zachowanie wyszukiwania dla tego zasobu jest odpowiednikiem wyszukiwanie czas ładowania, które będzie szukał zasoby, które zostały wcześniej załadowane z kodu znaczników bieżącego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stronie, a także innych źródłach aplikacji i wygeneruje tej wartości zasobów wartość właściwości w obiektach czasu wykonywania.  
  
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
|`key`|Klucz dla żądanego zasobu. Ten klucz była początkowo przypisana przez [x: Key — dyrektywa](../../xaml-services/x-key-directive.md) zasób został utworzony w znaczniku, czy została podana jako `key` parametru podczas wywoływania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  A `StaticResource` nie wolno próbować do przodu odnieść się do zasobu, który jest zdefiniowany leksykalnie dalsze w ramach [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Takie próby nie jest obsługiwany, a nawet wtedy, gdy takiego odwołania nie powiódł się, próby odwołania do przodu pociągnie za sobą zmniejszenie wydajności czas ładowania podczas tabel skrótu wewnętrznego reprezentujące <xref:System.Windows.ResourceDictionary> są przeszukiwane. Aby uzyskać najlepsze wyniki należy dostosować kompozycji słownikach zasobów taki sposób, że można uniknąć odwołania w przód. Jeśli nie można uniknąć odwołania do przodu, użyj [dynamicresource — rozszerzenie znaczników](dynamicresource-markup-extension.md) zamiast tego.  
  
 Określony <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> powinien odpowiadać istniejącego zasobu, identyfikowany za pomocą [x: Key — dyrektywa](../../xaml-services/x-key-directive.md) niektórych w na poziomie strony, aplikacji, motywy dostępne kontrolki i zasoby zewnętrzne lub zasobów systemowych. Wyszukiwania zasobów odbywa się w tej kolejności. Aby uzyskać więcej informacji na temat zachowania wyszukiwania zasobów dla zasobów statycznych i dynamicznych, zobacz [zasoby XAML](xaml-resources.md).  
  
 Klucz zasobu może być dowolnym ciągiem, zdefiniowane w [xamlname — gramatyka](../../xaml-services/xamlname-grammar.md). Klucz zasobu może być również inne typy obiektów, takich jak <xref:System.Type>. A <xref:System.Type> klucza ma podstawowe znaczenie dla jak można różne formanty, motywy, za pomocą klucza usługi stylu niejawnego. Aby uzyskać więcej informacji, zobacz [omówienie tworzenia kontrolek](../controls/control-authoring-overview.md).  
  
 Deklaratywne alternatywnych metod odwołujące się do zasobu jest jako [dynamicresource — rozszerzenie znaczników](dynamicresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podawany po `StaticResource` ciągu identyfikatora jest przypisany jako <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> wartości elementu bazowego <xref:System.Windows.StaticResourceExtension> rozszerzenie klasy.  
  
 `StaticResource` może służyć w składni obiektów. W tym przypadku określającą wartość <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwość jest wymagana.  
  
 `StaticResource` można również użycie pełnego atrybut określający <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwość jako właściwość = para wartości:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `StaticResource` ma tylko jedną konfigurowalną właściwość, która jest wymagana, użycie tych pełne nie są typowe.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora obsługi dla tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.StaticResourceExtension> klasy.  
  
 `StaticResource` jest rozszerzeniem znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Zasoby XAML](xaml-resources.md)
- [Zasoby i kod](resources-and-code.md)
