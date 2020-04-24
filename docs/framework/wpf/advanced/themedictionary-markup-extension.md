---
title: ThemeDictionary — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: f6ba0fe45aa11063c79d673b26794072968f4200
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646189"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary — Rozszerzenie znaczników
Umożliwia niestandardowe formanty lub aplikacje, które integrują formanty innych firm, aby załadować słowniki zasobów specyficzne dla motywu do użycia w stylizacji formantu.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`assemblyUri`|Jednolity identyfikator zasobu (URI) zestawu zawierającego informacje o motywie. Zazwyczaj jest to pakiet URI, który odwołuje się do zestawu w większym pakiecie. Zasoby zestawu i pakiety identyfikatorów URI upraszczają problemy z wdrażaniem. Aby uzyskać więcej informacji, zobacz [Pack URI w WPF](../app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie jest przeznaczone do wypełnienia tylko jednej <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>określonej wartości właściwości: wartości dla .  
  
 Korzystając z tego rozszerzenia, można określić pojedynczy zestaw tylko do zasobów, który zawiera niektóre style do użycia tylko wtedy, gdy kompozycja Windows Aero jest stosowana do systemu użytkownika, inne style tylko wtedy, gdy kompozycja Luna jest aktywna itd. Za pomocą tego rozszerzenia, zawartość słownika zasobów specyficzne dla formantu może być automatycznie unieważnione i ponownie załadowany do specyficznych dla innego tematu, gdy jest to wymagane.  
  
 Ciąg `assemblyUri` (wartość<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> właściwości) stanowi podstawę konwencji nazewnictwa, która identyfikuje słownika, który ma zastosowanie do określonego motywu. Logika <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> `ThemeDictionary` dla kończy konwencję, generując jednolity identyfikator zasobów (URI), który wskazuje na wariant słownika określonego motywu, zawarty w zestawie wstępnie skompilowanych zasobów. Opisujące tę konwencję lub interakcje motywu z ogólnym stylem sterowania i stylem na poziomie strony/aplikacji jako koncepcją nie są w pełni uwzględnione w tym miejscu. Podstawowym scenariuszem `ThemeDictionary` użycia jest <xref:System.Windows.ResourceDictionary.Source%2A> określenie właściwości `ResourceDictionary` zadeklarowanej na poziomie aplikacji. Po podaniu identyfikatora URI `ThemeDictionary` dla zestawu za pośrednictwem rozszerzenia, a nie jako bezpośredni identyfikator URI, logika rozszerzenia zapewni logikę unieważnienia, która ma zastosowanie za każdym razem, gdy zmienia się motyw systemowy.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany `ThemeDictionary` po ciągu identyfikatora jest <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> przypisany <xref:System.Windows.ThemeDictionaryExtension> jako wartość podstawowej klasy rozszerzenia.  
  
 `ThemeDictionary`mogą być również używane w składni elementu obiektu. W takim przypadku wymagane jest <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> określenie wartości właściwości.  
  
 `ThemeDictionary`może być również używany w użyciu atrybutu pełne, <xref:System.Windows.Markup.StaticExtension.Member%2A> który określa właściwość jako właściwość = parę wartości:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `ThemeDictionary` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] W implementacji procesora obsługi dla tego rozszerzenia <xref:System.Windows.ThemeDictionaryExtension> znaczników jest zdefiniowany przez klasę.  
  
 `ThemeDictionary`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w użyciu { i } znaków w składni atrybutu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] który jest konwencją, za pomocą której procesor rozpoznaje, że rozszerzenie znaczników musi przetwarzać atrybut. Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Zasoby aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md)
