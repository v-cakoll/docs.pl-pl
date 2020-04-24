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
ms.openlocfilehash: 5c0bb247bae525658d89d53f1672e57b87aba7bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646214"
---
# <a name="staticresource-markup-extension"></a>StaticResource — Rozszerzenie znaczników
Zapewnia wartość dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dowolnego atrybutu właściwości, wyszukując odwołanie do już zdefiniowanego zasobu. Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie ładowania, które będzie szukać [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zasobów, które zostały wcześniej załadowane z znaczników bieżącej strony, a także innych źródeł aplikacji i wygeneruje tę wartość zasobu jako wartość właściwości w obiektach w czasie wykonywania.  
  
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
|`key`|Klucz żądanego zasobu. Ten klucz został początkowo przypisany przez [x:Key Dyrektywy,](../../../desktop-wpf/xaml-services/xkey-directive.md) jeśli zasób `key` został utworzony <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> w znacznikach lub został dostarczony jako parametr podczas wywoływania, jeśli zasób został utworzony w kodzie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> A `StaticResource` nie może podejmować próby przekazywania odwołania do zasobu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] który jest zdefiniowany leksykalnie dalej w pliku. Próba wykonania tej zasady nie jest obsługiwana i nawet jeśli takie odwołanie nie zakończy się niepowodzeniem, próba odwołania do przodu <xref:System.Windows.ResourceDictionary> spowoduje obciążenie czasu obciążenia, gdy są przeszukiwane wewnętrzne tabele mieszania reprezentujące a. Aby uzyskać najlepsze wyniki, dostosuj skład słowników zasobów, aby uniknąć odwołań do przodu. Jeśli nie można uniknąć odwołania do przodu, należy użyć [DynamicResource Markup Extension](dynamicresource-markup-extension.md) zamiast.  
  
 Określony <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> powinien odpowiadać istniejącemu zasobowi, identyfikowane z [x:Key Dyrektywy](../../../desktop-wpf/xaml-services/xkey-directive.md) na pewnym poziomie na stronie, aplikacji, dostępnych motywów kontroli i zasobów zewnętrznych lub zasobów systemowych. Wyszukiwanie zasobów odbywa się w tej kolejności. Aby uzyskać więcej informacji na temat zachowania wyszukiwania zasobów statycznych i dynamicznych zasobów, zobacz [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Klucz zasobu może być dowolnym ciągiem zdefiniowanym w [gramatyki XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Klucz zasobu może być również inne <xref:System.Type>typy obiektów, takie jak . Klucz <xref:System.Type> ma zasadnicze znaczenie dla sposobu formantów mogą być stylizowane przez motywy, za pośrednictwem klucza stylu niejawnego. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia formantu](../controls/control-authoring-overview.md).  
  
 Alternatywnym deklaratywnym sposobem odwoływania się do zasobu jest [rozszerzenie znaczników DynamicResource](dynamicresource-markup-extension.md).  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany `StaticResource` po ciągu identyfikatora jest <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> przypisany <xref:System.Windows.StaticResourceExtension> jako wartość podstawowej klasy rozszerzenia.  
  
 `StaticResource`może być stosowany w składni elementu obiektu. W takim przypadku wymagane jest <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> określenie wartości właściwości.  
  
 `StaticResource`może być również używany w użyciu atrybutu pełne, <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> który określa właściwość jako właściwość = parę wartości:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `StaticResource` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] W implementacji procesora obsługi dla tego rozszerzenia <xref:System.Windows.StaticResourceExtension> znaczników jest zdefiniowany przez klasę.  
  
 `StaticResource`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w użyciu { i } znaków w składni atrybutu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] który jest konwencją, za pomocą której procesor rozpoznaje, że rozszerzenie znaczników musi przetwarzać atrybut. Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zasoby i kod](resources-and-code.md)
