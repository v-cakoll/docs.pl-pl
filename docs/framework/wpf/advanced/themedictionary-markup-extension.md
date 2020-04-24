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
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="c04ee-102">ThemeDictionary — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="c04ee-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="c04ee-103">Umożliwia niestandardowe formanty lub aplikacje, które integrują formanty innych firm, aby załadować słowniki zasobów specyficzne dla motywu do użycia w stylizacji formantu.</span><span class="sxs-lookup"><span data-stu-id="c04ee-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c04ee-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c04ee-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c04ee-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c04ee-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c04ee-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="c04ee-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="c04ee-107">Jednolity identyfikator zasobu (URI) zestawu zawierającego informacje o motywie.</span><span class="sxs-lookup"><span data-stu-id="c04ee-107">The uniform resource identifier (URI) of the assembly that contains theme information.</span></span> <span data-ttu-id="c04ee-108">Zazwyczaj jest to pakiet URI, który odwołuje się do zestawu w większym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="c04ee-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="c04ee-109">Zasoby zestawu i pakiety identyfikatorów URI upraszczają problemy z wdrażaniem.</span><span class="sxs-lookup"><span data-stu-id="c04ee-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="c04ee-110">Aby uzyskać więcej informacji, zobacz [Pack URI w WPF](../app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="c04ee-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c04ee-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c04ee-111">Remarks</span></span>  
 <span data-ttu-id="c04ee-112">To rozszerzenie jest przeznaczone do wypełnienia tylko jednej <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>określonej wartości właściwości: wartości dla .</span><span class="sxs-lookup"><span data-stu-id="c04ee-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c04ee-113">Korzystając z tego rozszerzenia, można określić pojedynczy zestaw tylko do zasobów, który zawiera niektóre style do użycia tylko wtedy, gdy kompozycja Windows Aero jest stosowana do systemu użytkownika, inne style tylko wtedy, gdy kompozycja Luna jest aktywna itd.</span><span class="sxs-lookup"><span data-stu-id="c04ee-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="c04ee-114">Za pomocą tego rozszerzenia, zawartość słownika zasobów specyficzne dla formantu może być automatycznie unieważnione i ponownie załadowany do specyficznych dla innego tematu, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="c04ee-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="c04ee-115">Ciąg `assemblyUri` (wartość<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> właściwości) stanowi podstawę konwencji nazewnictwa, która identyfikuje słownika, który ma zastosowanie do określonego motywu.</span><span class="sxs-lookup"><span data-stu-id="c04ee-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="c04ee-116">Logika <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> `ThemeDictionary` dla kończy konwencję, generując jednolity identyfikator zasobów (URI), który wskazuje na wariant słownika określonego motywu, zawarty w zestawie wstępnie skompilowanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="c04ee-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a uniform resource identifier (URI) that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="c04ee-117">Opisujące tę konwencję lub interakcje motywu z ogólnym stylem sterowania i stylem na poziomie strony/aplikacji jako koncepcją nie są w pełni uwzględnione w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="c04ee-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="c04ee-118">Podstawowym scenariuszem `ThemeDictionary` użycia jest <xref:System.Windows.ResourceDictionary.Source%2A> określenie właściwości `ResourceDictionary` zadeklarowanej na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c04ee-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="c04ee-119">Po podaniu identyfikatora URI `ThemeDictionary` dla zestawu za pośrednictwem rozszerzenia, a nie jako bezpośredni identyfikator URI, logika rozszerzenia zapewni logikę unieważnienia, która ma zastosowanie za każdym razem, gdy zmienia się motyw systemowy.</span><span class="sxs-lookup"><span data-stu-id="c04ee-119">When you provide a URI for the assembly through a `ThemeDictionary` extension rather than as a direct URI, the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="c04ee-120">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="c04ee-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="c04ee-121">Token ciągu podany `ThemeDictionary` po ciągu identyfikatora jest <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> przypisany <xref:System.Windows.ThemeDictionaryExtension> jako wartość podstawowej klasy rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c04ee-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="c04ee-122">`ThemeDictionary`mogą być również używane w składni elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="c04ee-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="c04ee-123">W takim przypadku wymagane jest <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> określenie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="c04ee-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="c04ee-124">`ThemeDictionary`może być również używany w użyciu atrybutu pełne, <xref:System.Windows.Markup.StaticExtension.Member%2A> który określa właściwość jako właściwość = parę wartości:</span><span class="sxs-lookup"><span data-stu-id="c04ee-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="c04ee-125">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c04ee-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="c04ee-126">Ponieważ `ThemeDictionary` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.</span><span class="sxs-lookup"><span data-stu-id="c04ee-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="c04ee-127">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] W implementacji procesora obsługi dla tego rozszerzenia <xref:System.Windows.ThemeDictionaryExtension> znaczników jest zdefiniowany przez klasę.</span><span class="sxs-lookup"><span data-stu-id="c04ee-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="c04ee-128">`ThemeDictionary`jest rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="c04ee-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="c04ee-129">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="c04ee-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="c04ee-130">Wszystkie rozszerzenia znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w użyciu { i } znaków w składni atrybutu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] który jest konwencją, za pomocą której procesor rozpoznaje, że rozszerzenie znaczników musi przetwarzać atrybut.</span><span class="sxs-lookup"><span data-stu-id="c04ee-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="c04ee-131">Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c04ee-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04ee-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c04ee-132">See also</span></span>

- [<span data-ttu-id="c04ee-133">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="c04ee-133">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c04ee-134">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c04ee-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="c04ee-135">Rozszerzenia znacznikowania i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c04ee-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="c04ee-136">Zasoby aplikacji WPF, zawartość i pliki danych</span><span class="sxs-lookup"><span data-stu-id="c04ee-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
