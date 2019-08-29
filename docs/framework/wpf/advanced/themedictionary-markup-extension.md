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
ms.openlocfilehash: 7fa729d600f25b73028bae0dd6d9248b5839dd4c
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133865"
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
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Zestaw zawierający informacje o motywie. Zwykle jest to identyfikator URI pakietu, który odwołuje się do zestawu w większym pakiecie. Zasoby zestawu i identyfikatory URI pakietów upraszczają problemy z wdrażaniem. Aby uzyskać więcej informacji, zobacz [identyfikatory URI pakietów w WPF](../app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie jest przeznaczone do wypełniania tylko jednej określonej wartości właściwości: wartości <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>dla.  
  
 Za pomocą tego rozszerzenia można określić pojedynczy zestaw tylko zasobów, który zawiera kilka stylów, które mają być używane tylko wtedy, gdy motyw Windows Aero jest stosowany do systemu użytkownika, inne style tylko wtedy, gdy motyw Luna jest aktywny i tak dalej. Za pomocą tego rozszerzenia zawartość słownika zasobów specyficznych dla kontrolki można automatycznie unieważniać i ponownie ładować, aby była określona dla innego motywu, jeśli jest to wymagane.  
  
 `assemblyUri` Ciąg(<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> wartość właściwości) stanowi podstawę konwencji nazewnictwa, która identyfikuje słownik stosowany do określonego motywu. Logika dla `ThemeDictionary` zakończenia Konwencji przez wygenerowanie [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] wskazuje na określony wariant słownika motywu, jak w ramach prekompilowanego zestawu zasobów. <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Opisywanie tej Konwencji lub interakcji z motywem z ogólnymi stylami formantów i stylami na poziomie strony/aplikacji jako koncepcji nie są tu omówione. Podstawowym scenariuszem użycia `ThemeDictionary` jest <xref:System.Windows.ResourceDictionary.Source%2A> określenie właściwości `ResourceDictionary` zadeklarowanej na poziomie aplikacji. Gdy podajesz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zestawu `ThemeDictionary` za pośrednictwem rozszerzenia, a nie bezpośrednio [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], logika rozszerzeń będzie dostarczać logikę unieważnienia, która obowiązuje przy każdej zmianie motywu systemowego.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po `ThemeDictionary` ciągu identyfikatora jest przypisywany <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> jako wartość źródłowej <xref:System.Windows.ThemeDictionaryExtension> klasy rozszerzenia.  
  
 `ThemeDictionary`może być również używany w składni elementu obiektu. W takim przypadku należy określić wartość <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> właściwości.  
  
 `ThemeDictionary`można go również użyć w pełnym użyciu atrybutu, który określa <xref:System.Windows.Markup.StaticExtension.Member%2A> właściwość jako pary właściwość = wartość:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne. Ponieważ `ThemeDictionary` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.  
  
 W implementacji procesora obsługa tego <xref:System.Windows.ThemeDictionaryExtension> rozszerzenia znacznika jest definiowana przez klasę. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 `ThemeDictionary`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której procesor rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Zasoby aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md)
