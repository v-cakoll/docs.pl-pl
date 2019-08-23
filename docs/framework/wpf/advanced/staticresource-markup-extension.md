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
ms.openlocfilehash: 7392be182aedeeebe6b7092f9868c1fabfaafcb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963462"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="c407f-102">StaticResource — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="c407f-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="c407f-103">Udostępnia wartość dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu właściwości przez wyszukanie odwołania do już zdefiniowanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="c407f-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="c407f-104">Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie ładowania, które będzie szukać zasobów, które zostały wcześniej załadowane z adiustacji bieżącej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony, a także innych źródeł aplikacji, i spowoduje wygenerowanie tej wartości zasobu jako wartość właściwości w obiektach czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c407f-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c407f-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c407f-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c407f-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c407f-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c407f-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="c407f-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="c407f-108">Klucz dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="c407f-108">The key for the requested resource.</span></span> <span data-ttu-id="c407f-109">Ten klucz został początkowo przypisany przez [dyrektywę x:Key](../../xaml-services/x-key-directive.md) , jeśli zasób został utworzony w znaczniku lub został dostarczony jako `key` parametr podczas wywoływania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> , jeśli zasób został utworzony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c407f-109">This key was initially assigned by the [x:Key Directive](../../xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c407f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c407f-110">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c407f-111">A `StaticResource` nie może próbować wykonać odwołania do przodu do zasobu, który jest bardziej leksykalny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w pliku.</span><span class="sxs-lookup"><span data-stu-id="c407f-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="c407f-112">Próba wykonania tej operacji nie jest obsługiwana, a nawet jeśli takie odwołanie nie powiedzie się, próba odwołania do przodu spowoduje naliczenie opłat za czas ładowania podczas przeszukiwania wewnętrznych tablic <xref:System.Windows.ResourceDictionary> skrótów.</span><span class="sxs-lookup"><span data-stu-id="c407f-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="c407f-113">Aby uzyskać najlepsze wyniki, dostosuj kompozycję słowników zasobów, aby można było uniknąć odwołań do przodu.</span><span class="sxs-lookup"><span data-stu-id="c407f-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="c407f-114">Jeśli nie możesz uniknąć odwołania do przodu, zamiast tego użyj [rozszerzenia znacznika DynamicResource —](dynamicresource-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="c407f-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="c407f-115">Określony <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> element powinien odpowiadać istniejącemu zasobowi, identyfikowanemu z [dyrektywą x:Key](../../xaml-services/x-key-directive.md) na pewnym poziomie na stronie, aplikacji, dostępnych motywów kontroli i zasobach zewnętrznych lub zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="c407f-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="c407f-116">Wyszukiwanie zasobów odbywa się w tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c407f-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="c407f-117">Aby uzyskać więcej informacji o zachowaniu wyszukiwania zasobów dla zasobów statycznych i dynamicznych, zobacz [zasoby XAML](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
 <span data-ttu-id="c407f-118">Klucz zasobu może być dowolnym ciągiem zdefiniowanym w [gramatycename języka XAML](../../xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-118">A resource key can be any string defined in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="c407f-119">Klucz zasobu może być również innymi typami obiektów, takimi jak <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="c407f-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="c407f-120"><xref:System.Type> Klucz ma podstawowe znaczenie dla kontrolek, które mogą być wzorowane przez motywy, za pomocą klucza stylu niejawnego.</span><span class="sxs-lookup"><span data-stu-id="c407f-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="c407f-121">Aby uzyskać więcej informacji, zobacz temat [Tworzenie kontroli — przegląd](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="c407f-122">Alternatywny sposób deklaratywny odwołujący się do zasobu to [rozszerzenie znacznika DynamicResource —](dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="c407f-123">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="c407f-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="c407f-124">Token ciągu podany po `StaticResource` ciągu identyfikatora jest przypisywany <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> jako wartość źródłowej <xref:System.Windows.StaticResourceExtension> klasy rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c407f-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="c407f-125">`StaticResource`może być używany w składni elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="c407f-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="c407f-126">W takim przypadku należy określić wartość <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c407f-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="c407f-127">`StaticResource`można go również użyć w pełnym użyciu atrybutu, który określa <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwość jako pary właściwość = wartość:</span><span class="sxs-lookup"><span data-stu-id="c407f-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="c407f-128">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c407f-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="c407f-129">Ponieważ `StaticResource` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.</span><span class="sxs-lookup"><span data-stu-id="c407f-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="c407f-130">W implementacji procesora obsługa tego <xref:System.Windows.StaticResourceExtension> rozszerzenia znacznika jest definiowana przez klasę. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c407f-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="c407f-131">`StaticResource`jest rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="c407f-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="c407f-132">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="c407f-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="c407f-133">Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której procesor rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut.</span><span class="sxs-lookup"><span data-stu-id="c407f-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="c407f-134">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c407f-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c407f-135">See also</span></span>

- [<span data-ttu-id="c407f-136">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="c407f-136">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="c407f-137">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c407f-137">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="c407f-138">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c407f-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="c407f-139">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="c407f-139">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="c407f-140">Zasoby i kod</span><span class="sxs-lookup"><span data-stu-id="c407f-140">Resources and Code</span></span>](resources-and-code.md)
