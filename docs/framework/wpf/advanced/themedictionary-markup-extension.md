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
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="c8722-102">ThemeDictionary — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="c8722-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="c8722-103">Udostępnia sposób dla autorów formantów niestandardowych lub aplikacji, które integrują formanty innych firm w celu załadowania słowników zasobów specyficznych dla motywu do użycia w stylu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c8722-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c8722-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c8722-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c8722-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c8722-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c8722-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="c8722-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="c8722-107">Uniform Resource Identifier (URI) zestawu, który zawiera informacje o motywie.</span><span class="sxs-lookup"><span data-stu-id="c8722-107">The uniform resource identifier (URI) of the assembly that contains theme information.</span></span> <span data-ttu-id="c8722-108">Zwykle jest to identyfikator URI pakietu, który odwołuje się do zestawu w większym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="c8722-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="c8722-109">Zasoby zestawu i identyfikatory URI pakietów upraszczają problemy z wdrażaniem.</span><span class="sxs-lookup"><span data-stu-id="c8722-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="c8722-110">Aby uzyskać więcej informacji, zobacz [identyfikatory URI pakietów w WPF](../app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="c8722-110">For more information see [Pack URIs in WPF](../app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8722-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8722-111">Remarks</span></span>  
 <span data-ttu-id="c8722-112">To rozszerzenie jest przeznaczone do wypełniania tylko jednej określonej wartości właściwości: wartości dla <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8722-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c8722-113">Za pomocą tego rozszerzenia można określić pojedynczy zestaw tylko zasobów, który zawiera kilka stylów, które mają być używane tylko wtedy, gdy motyw Windows Aero jest stosowany do systemu użytkownika, inne style tylko wtedy, gdy motyw Luna jest aktywny i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c8722-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the Windows Aero theme is applied to the user's system, other styles only when the Luna theme is active, and so on.</span></span> <span data-ttu-id="c8722-114">Za pomocą tego rozszerzenia zawartość słownika zasobów specyficznych dla kontrolki można automatycznie unieważniać i ponownie ładować, aby była określona dla innego motywu, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="c8722-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="c8722-115">Ciąg `assemblyUri` (wartość właściwości <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>) stanowi podstawę konwencji nazewnictwa, która określa, który słownik ma zastosowanie do określonego motywu.</span><span class="sxs-lookup"><span data-stu-id="c8722-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="c8722-116">Logika <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> dla `ThemeDictionary` pełni Konwencję przez wygenerowanie identyfikatora Uniform Resource Identifier (URI), który wskazuje określony wariant słownika motywu, który jest zawarty w prekompilowanym zestawie zasobów.</span><span class="sxs-lookup"><span data-stu-id="c8722-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a uniform resource identifier (URI) that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="c8722-117">Opisywanie tej Konwencji lub interakcji z motywem z ogólnymi stylami formantów i stylami na poziomie strony/aplikacji jako koncepcji nie są tu omówione.</span><span class="sxs-lookup"><span data-stu-id="c8722-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="c8722-118">Podstawowym scenariuszem korzystania z `ThemeDictionary` jest określenie właściwości <xref:System.Windows.ResourceDictionary.Source%2A> `ResourceDictionary` zadeklarowanej na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8722-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="c8722-119">Po podaniu identyfikatora URI dla zestawu za pośrednictwem rozszerzenia `ThemeDictionary`, a nie jako bezpośredniego identyfikatora URI, logika rozszerzeń będzie dostarczać logikę unieważnienia, która ma zastosowanie zawsze, gdy zmienia się kompozycja systemu.</span><span class="sxs-lookup"><span data-stu-id="c8722-119">When you provide a URI for the assembly through a `ThemeDictionary` extension rather than as a direct URI, the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="c8722-120">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="c8722-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="c8722-121">Token ciągu podany po ciągu identyfikatora `ThemeDictionary` jest przypisywany jako wartość <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> źródłowej klasy rozszerzenia <xref:System.Windows.ThemeDictionaryExtension>.</span><span class="sxs-lookup"><span data-stu-id="c8722-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="c8722-122">`ThemeDictionary` mogą być również używane w składni elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="c8722-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="c8722-123">W takim przypadku należy określić wartość właściwości <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8722-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="c8722-124">`ThemeDictionary` można również użyć w pełnym użyciu atrybutu, który określa właściwość <xref:System.Windows.Markup.StaticExtension.Member%2A> jako parę właściwość = wartość:</span><span class="sxs-lookup"><span data-stu-id="c8722-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="c8722-125">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c8722-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="c8722-126">Ponieważ `ThemeDictionary` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.</span><span class="sxs-lookup"><span data-stu-id="c8722-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="c8722-127">W implementacji procesora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.ThemeDictionaryExtension>.</span><span class="sxs-lookup"><span data-stu-id="c8722-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="c8722-128">`ThemeDictionary` to rozszerzenie znaczników.</span><span class="sxs-lookup"><span data-stu-id="c8722-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="c8722-129">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="c8722-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="c8722-130">Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą której procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut.</span><span class="sxs-lookup"><span data-stu-id="c8722-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="c8722-131">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c8722-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8722-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8722-132">See also</span></span>

- [<span data-ttu-id="c8722-133">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="c8722-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="c8722-134">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c8722-134">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="c8722-135">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c8722-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="c8722-136">Zasoby aplikacji WPF, zawartość i pliki danych</span><span class="sxs-lookup"><span data-stu-id="c8722-136">WPF Application Resource, Content, and Data Files</span></span>](../app-development/wpf-application-resource-content-and-data-files.md)
