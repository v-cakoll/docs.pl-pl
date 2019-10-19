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
ms.openlocfilehash: 471b444b66c5e8173542ab1e27cb1233bfde133f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582319"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary — Rozszerzenie znaczników
Udostępnia sposób dla autorów formantów niestandardowych lub aplikacji, które integrują formanty innych firm w celu załadowania słowników zasobów specyficznych dla motywu do użycia w stylu kontrolki.  
  
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
|`assemblyUri`|Uniform Resource Identifier (URI) zestawu, który zawiera informacje o motywie. Zwykle jest to identyfikator URI pakietu, który odwołuje się do zestawu w większym pakiecie. Zasoby zestawu i identyfikatory URI pakietów upraszczają problemy z wdrażaniem. Aby uzyskać więcej informacji, zobacz [identyfikatory URI pakietów w WPF](../app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie jest przeznaczone do wypełniania tylko jednej określonej wartości właściwości: wartości dla <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.  
  
 Za pomocą tego rozszerzenia można określić pojedynczy zestaw tylko zasobów, który zawiera kilka stylów, które mają być używane tylko wtedy, gdy motyw Windows Aero jest stosowany do systemu użytkownika, inne style tylko wtedy, gdy motyw Luna jest aktywny i tak dalej. Za pomocą tego rozszerzenia zawartość słownika zasobów specyficznych dla kontrolki można automatycznie unieważniać i ponownie ładować, aby była określona dla innego motywu, jeśli jest to wymagane.  
  
 Ciąg `assemblyUri` (wartość właściwości <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>) stanowi podstawę konwencji nazewnictwa, która określa, który słownik ma zastosowanie do określonego motywu. Logika <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> dla `ThemeDictionary` pełni Konwencję przez wygenerowanie identyfikatora Uniform Resource Identifier (URI), który wskazuje określony wariant słownika motywu, który jest zawarty w prekompilowanym zestawie zasobów. Opisywanie tej Konwencji lub interakcji z motywem z ogólnymi stylami formantów i stylami na poziomie strony/aplikacji jako koncepcji nie są tu omówione. Podstawowym scenariuszem korzystania z `ThemeDictionary` jest określenie właściwości <xref:System.Windows.ResourceDictionary.Source%2A> `ResourceDictionary` zadeklarowanej na poziomie aplikacji. Po podaniu identyfikatora URI dla zestawu za pośrednictwem rozszerzenia `ThemeDictionary`, a nie jako bezpośredniego identyfikatora URI, logika rozszerzeń będzie dostarczać logikę unieważnienia, która ma zastosowanie zawsze, gdy zmienia się kompozycja systemu.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po ciągu identyfikatora `ThemeDictionary` jest przypisywany jako wartość <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> źródłowej klasy rozszerzenia <xref:System.Windows.ThemeDictionaryExtension>.  
  
 `ThemeDictionary` mogą być również używane w składni elementu obiektu. W takim przypadku należy określić wartość właściwości <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>.  
  
 `ThemeDictionary` można również użyć w pełnym użyciu atrybutu, który określa właściwość <xref:System.Windows.Markup.StaticExtension.Member%2A> jako parę właściwość = wartość:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `ThemeDictionary` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 W implementacji procesora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.ThemeDictionaryExtension>.  
  
 `ThemeDictionary` to rozszerzenie znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą której procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Zasoby aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md)
