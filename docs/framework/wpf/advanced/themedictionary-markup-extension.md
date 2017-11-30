---
title: "ThemeDictionary — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f878ce89dcf76ae800ade10a0e67f019741f65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="770db-102">ThemeDictionary — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="770db-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="770db-103">Umożliwia autorom kontrolkę niestandardową lub aplikacje, które integracji formanty innych firm do załadowania słowniki zasobów specyficznych dla motywów do użycia w stylów formantu.</span><span class="sxs-lookup"><span data-stu-id="770db-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="770db-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="770db-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="770db-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="770db-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="770db-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="770db-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="770db-107">[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Zestawu, który zawiera informacje o motywu.</span><span class="sxs-lookup"><span data-stu-id="770db-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="770db-108">Zazwyczaj jest to pakiet identyfikator URI, który odwołuje się do zestawu w pakiecie większy.</span><span class="sxs-lookup"><span data-stu-id="770db-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="770db-109">Zestaw zasobów i identyfikatory URI pochodzące z uproszczenia problemów dotyczących wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="770db-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="770db-110">Aby uzyskać więcej informacji, zobacz [identyfikatorów URI pakietu na platformie WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="770db-110">For more information see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="770db-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="770db-111">Remarks</span></span>  
 <span data-ttu-id="770db-112">To rozszerzenie jest przeznaczona do wypełnienia tylko jedna wartość określoną właściwość: wartość <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="770db-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="770db-113">Za pomocą tego rozszerzenia, można określić jednym zestawie tylko do zasobów, który zawiera niektóre style, które mają być używane tylko wtedy, gdy [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] motyw jest stosowany do użytkownika systemu, inne style, gdy Luna motywu jest aktywna i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="770db-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] theme is applied to the user's system, other styles when Luna theme is active, and so on.</span></span> <span data-ttu-id="770db-114">Za pomocą tego rozszerzenia, zawartość słownika zasobów specyficznych dla formantu można automatycznie unieważniona i załadowania przeznaczone dla innej motywu, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="770db-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="770db-115">`assemblyUri` Ciąg (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> wartości właściwości) stanowi podstawę konwencji nazewnictwa, która identyfikuje słownik, który ma zastosowanie do wybranego motywu.</span><span class="sxs-lookup"><span data-stu-id="770db-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="770db-116"><xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Logikę `ThemeDictionary` zakończeniu Konwencji, generując [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] wskazującego typ variant słownika wybranego motywu, zawarty w zestawie wstępnie skompilowanym zasobów.</span><span class="sxs-lookup"><span data-stu-id="770db-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="770db-117">Opisujące, lub na podstawie motywu interakcji z stylów formantu ogólne i poziomu stylów strony aplikacji jako koncepcji, nie pasuje do pełni tutaj.</span><span class="sxs-lookup"><span data-stu-id="770db-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="770db-118">Podstawowe scenariusz użycia `ThemeDictionary` jest określenie <xref:System.Windows.ResourceDictionary.Source%2A> właściwość `ResourceDictionary` zadeklarowane na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="770db-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="770db-119">Jeśli podasz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zestawu za pomocą `ThemeDictionary` rozszerzenia, a nie jako bezpośredniego [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], logiki rozszerzenia zapewni unieważniania logikę, która ma zastosowanie przy każdej zmianie motywu systemu.</span><span class="sxs-lookup"><span data-stu-id="770db-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="770db-120">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="770db-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="770db-121">Token ciągu po `ThemeDictionary` przypisany jako identyfikator ciągu <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> wartości podstawowych <xref:System.Windows.ThemeDictionaryExtension> rozszerzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="770db-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="770db-122">`ThemeDictionary`może być również w składni elementu obiekt.</span><span class="sxs-lookup"><span data-stu-id="770db-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="770db-123">W takim przypadku określającą wartość <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="770db-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="770db-124">`ThemeDictionary`można również w Określa użycie atrybutu pełne <xref:System.Windows.Markup.StaticExtension.Member%2A> właściwości jako właściwość = pary wartości:</span><span class="sxs-lookup"><span data-stu-id="770db-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="770db-125">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="770db-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="770db-126">Ponieważ `ThemeDictionary` ma tylko jedną można ustawić właściwości, która jest wymagana, to użycie Pełne nie są typowe.</span><span class="sxs-lookup"><span data-stu-id="770db-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="770db-127">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.ThemeDictionaryExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="770db-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="770db-128">`ThemeDictionary`to rozszerzenie znacznika.</span><span class="sxs-lookup"><span data-stu-id="770db-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="770db-129">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="770db-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="770db-130">Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w ich składni atrybutu Konwencji za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="770db-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="770db-131">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="770db-131">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="770db-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="770db-132">See Also</span></span>  
 [<span data-ttu-id="770db-133">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="770db-133">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="770db-134">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="770db-134">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="770db-135">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="770db-135">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="770db-136">Zasób w aplikacji WPF, zawartość i plików danych</span><span class="sxs-lookup"><span data-stu-id="770db-136">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
