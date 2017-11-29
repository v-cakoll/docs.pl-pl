---
title: "DynamicResource — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c80d975e756fab449c254b9e1d8d1bc99a25652e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="dynamicresource-markup-extension"></a><span data-ttu-id="bbffe-102">DynamicResource — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="bbffe-102">DynamicResource Markup Extension</span></span>
<span data-ttu-id="bbffe-103">Zawiera wartość dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu właściwości przez odkładanie tej wartości jako odwołanie do określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="bbffe-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by deferring that value to be a reference to a defined resource.</span></span> <span data-ttu-id="bbffe-104">Zachowanie wyszukiwania dla tego zasobu jest odpowiednikiem odnośników czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bbffe-104">Lookup behavior for that resource is analogous to run-time lookup.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="bbffe-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="bbffe-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="bbffe-106">Użycie elementu właściwości języka XAML</span><span class="sxs-lookup"><span data-stu-id="bbffe-106">XAML Property Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="bbffe-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="bbffe-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="bbffe-108">Klucz do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="bbffe-108">The key for the requested resource.</span></span> <span data-ttu-id="bbffe-109">Ten klucz była początkowo przypisana przez [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) zasób został utworzony w znaczniku, czy podany jako `key` parametr podczas wywoływania metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Jeśli zasób został utworzony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="bbffe-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbffe-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbffe-110">Remarks</span></span>  
 <span data-ttu-id="bbffe-111">A `DynamicResource` spowoduje to utworzenie tymczasowego wyrażenie podczas początkowej kompilacji i w związku z tym odroczenie wyszukiwania zasobów, dopóki wartość żądany zasób nie zostanie faktycznie wymagane do utworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="bbffe-111">A `DynamicResource` will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="bbffe-112">Może to być potencjalnie po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] załadowanej strony.</span><span class="sxs-lookup"><span data-stu-id="bbffe-112">This may potentially be after the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is loaded.</span></span> <span data-ttu-id="bbffe-113">Wartość zasobu zostaną znalezione w oparciu klucza wyszukiwania względem wszystkich słowniki zasobów active, zaczynając od bieżącego zakresu strony i zastępuje symbol zastępczy wyrażenie z kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bbffe-113">The resource value will be found based on key search against all active resource dictionaries starting from the current page scope, and is substituted for the placeholder expression from compilation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bbffe-114">Pod względem pierwszeństwo właściwości zależności `DynamicResource` wyrażenie jest odpowiednikiem sytuację, w których stosowane jest odwołanie do zasobu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="bbffe-114">In terms of dependency property precedence, a `DynamicResource` expression is equivalent to the position where the dynamic resource reference is applied.</span></span> <span data-ttu-id="bbffe-115">Jeśli ustawisz wartości lokalnej dla właściwości, która wcześniej była `DynamicResource` wyrażenia jako wartości lokalnej `DynamicResource` zostanie całkowicie usunięta.</span><span class="sxs-lookup"><span data-stu-id="bbffe-115">If you set a local value for a property that previously had a `DynamicResource` expression as the local value, the `DynamicResource` is completely removed.</span></span> <span data-ttu-id="bbffe-116">Aby uzyskać więcej informacji, zobacz [pierwszeństwo wartość właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="bbffe-116">For details, see [Dependency Property Value Precedence](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).</span></span>  
  
 <span data-ttu-id="bbffe-117">Są szczególnie odpowiednie dla scenariuszy dostępu do niektórych zasobów `DynamicResource` w przeciwieństwie do [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="bbffe-117">Certain resource access scenarios are particularly appropriate for `DynamicResource` as opposed to a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span> <span data-ttu-id="bbffe-118">Zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) omówienie o względnych zalet i wpływu na wydajność programu `DynamicResource` i `StaticResource`.</span><span class="sxs-lookup"><span data-stu-id="bbffe-118">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for a discussion about the relative merits and performance implications of `DynamicResource` and `StaticResource`.</span></span>  
  
 <span data-ttu-id="bbffe-119">Określony <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> powinien odpowiadać istniejący zasób ustaleniami [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) na określonym poziomie w ze strony, aplikacji, kompozycje dostępne kontrolki i zasobów zewnętrznych lub zasobów systemowych i Wyszukiwanie zasobów nastąpi w podanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="bbffe-119">The specified <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> should correspond to an existing resource determined by [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources, and the resource lookup will happen in that order.</span></span> <span data-ttu-id="bbffe-120">Aby uzyskać więcej informacji na temat wyszukiwania zasobów dla statycznych i dynamicznych zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="bbffe-120">For more information about resource lookup for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="bbffe-121">Klucz zasobu może być zdefiniowany w [xamlname — gramatyka](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="bbffe-121">A resource key may be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="bbffe-122">Klucz zasobu może być również innych obiektów, takich jak <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="bbffe-122">A resource key may also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="bbffe-123">A <xref:System.Type> klucza jest niezbędne, aby jak formanty można wstawiony przez motywów.</span><span class="sxs-lookup"><span data-stu-id="bbffe-123">A <xref:System.Type> key is fundamental to how controls can be styled by themes.</span></span> <span data-ttu-id="bbffe-124">Aby uzyskać więcej informacji, zobacz [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bbffe-124">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]<span data-ttu-id="bbffe-125">Podczas wyszukiwania wartości zasobów takich jak <xref:System.Windows.FrameworkElement.FindResource%2A>, postępuj zgodnie z tej samej logiki wyszukiwania zasobów jako używane przez `DynamicResource`.</span><span class="sxs-lookup"><span data-stu-id="bbffe-125"> for lookup of resource values, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, follow the same resource lookup logic as used by `DynamicResource`.</span></span>  
  
 <span data-ttu-id="bbffe-126">Deklaracyjne alternatywnych środków odwołujące się do zasobu jest jako [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="bbffe-126">The alternative declarative means of referencing a resource is as a [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="bbffe-127">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="bbffe-127">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="bbffe-128">Token ciągu po `DynamicResource` przypisany jako identyfikator ciągu <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> wartości podstawowych <xref:System.Windows.DynamicResourceExtension> rozszerzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="bbffe-128">The string token provided after the `DynamicResource` identifier string is assigned as the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.DynamicResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="bbffe-129">`DynamicResource`można w składni elementu obiekt.</span><span class="sxs-lookup"><span data-stu-id="bbffe-129">`DynamicResource` can be used in object element syntax.</span></span> <span data-ttu-id="bbffe-130">W takim przypadku określającą wartość <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="bbffe-130">In this case, specifying the value of the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="bbffe-131">`DynamicResource`można również w Określa użycie atrybutu pełne <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> właściwości jako właściwość = pary wartości:</span><span class="sxs-lookup"><span data-stu-id="bbffe-131">`DynamicResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="bbffe-132">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="bbffe-132">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="bbffe-133">Ponieważ `DynamicResource` ma tylko jedną można ustawić właściwości, która jest wymagana, to użycie Pełne nie są typowe.</span><span class="sxs-lookup"><span data-stu-id="bbffe-133">Because `DynamicResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="bbffe-134">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.DynamicResourceExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="bbffe-134">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.DynamicResourceExtension> class.</span></span>  
  
 <span data-ttu-id="bbffe-135">`DynamicResource`to rozszerzenie znacznika.</span><span class="sxs-lookup"><span data-stu-id="bbffe-135">`DynamicResource` is a markup extension.</span></span> <span data-ttu-id="bbffe-136">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="bbffe-136">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="bbffe-137">Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w ich składni atrybutu Konwencji za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bbffe-137">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="bbffe-138">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="bbffe-138">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbffe-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbffe-139">See Also</span></span>  
 [<span data-ttu-id="bbffe-140">Zasoby dla języka XAML</span><span class="sxs-lookup"><span data-stu-id="bbffe-140">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="bbffe-141">Zasoby i kod</span><span class="sxs-lookup"><span data-stu-id="bbffe-141">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="bbffe-142">x: Key — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="bbffe-142">x:Key Directive</span></span>](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [<span data-ttu-id="bbffe-143">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="bbffe-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="bbffe-144">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="bbffe-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="bbffe-145">Rozszerzenie StaticResource znaczników</span><span class="sxs-lookup"><span data-stu-id="bbffe-145">StaticResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [<span data-ttu-id="bbffe-146">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="bbffe-146">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
