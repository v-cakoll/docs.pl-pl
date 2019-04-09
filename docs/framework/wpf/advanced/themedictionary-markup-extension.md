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
ms.openlocfilehash: ad2248c791fadc5363d90ff496d5e040f6036ab3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132096"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary — Rozszerzenie znaczników
Umożliwia autorom kontrolkę niestandardową lub aplikacje, które integrują się formanty innych firm, aby załadować słowniki zasobów specyficznych dla motywów do użycia w style kontrolki.  
  
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
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Zestawu, który zawiera informacje o motywie. Zazwyczaj jest to identyfikator URI, który odwołuje się do zestawu w pakiecie większy pakiet. Zestaw zasobów i dodatkiem Service pack identyfikatorów URI upraszczają problemy z wdrażaniem. Aby uzyskać więcej informacji, zobacz [pakiet URI w WPF](../app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie jest przeznaczona do wypełnienia tylko jedna wartość określoną właściwość: wartość <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.  
  
 Za pomocą tego rozszerzenia, można określić pojedynczy zestaw tylko do zasobów, który zawiera niektóre style, które mają być używane tylko wtedy, gdy [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] motyw jest stosowany do systemu użytkownika i innych stylów, gdy Luna motywu jest aktywna i tak dalej. Za pomocą tego rozszerzenia, zawartość słownika zasobów specyficznej dla kontroli może być automatycznie unieważnione i ponownie załadowany można określić dla innego motywu, gdy jest to wymagane.  
  
 `assemblyUri` Ciąg (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> wartość właściwości) stanowi podstawę konwencji nazewnictwa, która identyfikuje słownik, który ma zastosowanie do wybranego motywu. <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Logikę `ThemeDictionary` kończy Konwencji, generując [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] wskazującej wariant słownika wybranego motywu, zawarty w zestawie prekompilowanych zasobów. Opisujący, lub na podstawie motywu interakcji z Nadawanie stylów kontrolek ogólne i stylów poziomu aplikacji/strony jako koncepcji, nie pasuje do w pełni tutaj. Podstawowy scenariusz użycia `ThemeDictionary` jest określenie <xref:System.Windows.ResourceDictionary.Source%2A> właściwość `ResourceDictionary` zadeklarowane na poziomie aplikacji. Jeśli podasz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zestawu za pomocą `ThemeDictionary` rozszerzenia, a nie jako bezpośredni [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], logiki rozszerzenia zapewni logiki unieważniania, która ma zastosowanie zawsze po zmianie motywu systemu.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podawany po `ThemeDictionary` ciągu identyfikatora jest przypisany jako <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> wartości elementu bazowego <xref:System.Windows.ThemeDictionaryExtension> rozszerzenie klasy.  
  
 `ThemeDictionary` może również w składni obiektów. W tym przypadku określającą wartość <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> właściwość jest wymagana.  
  
 `ThemeDictionary` można również użycie pełnego atrybut określający <xref:System.Windows.Markup.StaticExtension.Member%2A> właściwość jako właściwość = para wartości:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `ThemeDictionary` ma tylko jedną konfigurowalną właściwość, która jest wymagana, użycie tych pełne nie są typowe.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora obsługi dla tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.ThemeDictionaryExtension> klasy.  
  
 `ThemeDictionary` jest rozszerzeniem znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Omówienie XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Zasoby aplikacji WPF, zawartość, pliki danych](../app-development/wpf-application-resource-content-and-data-files.md)
