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
ms.openlocfilehash: 8319e451268152e95326c02027157db72df631b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981906"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="d3a19-102">StaticResource — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="d3a19-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="d3a19-103">Zawiera wartość dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] właściwości atrybutu przez wyszukanie odwołanie do zasobu już zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="d3a19-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="d3a19-104">Zachowanie wyszukiwania dla tego zasobu jest odpowiednikiem wyszukiwanie czas ładowania, które będzie szukał zasoby, które zostały wcześniej załadowane z kodu znaczników bieżącego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stronie, a także innych źródłach aplikacji i wygeneruje tej wartości zasobów wartość właściwości w obiektach czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d3a19-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="d3a19-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="d3a19-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="d3a19-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="d3a19-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="d3a19-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="d3a19-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="d3a19-108">Klucz dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="d3a19-108">The key for the requested resource.</span></span> <span data-ttu-id="d3a19-109">Ten klucz była początkowo przypisana przez [x: Key — dyrektywa](../../xaml-services/x-key-directive.md) zasób został utworzony w znaczniku, czy została podana jako `key` parametru podczas wywoływania <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Jeśli zasób został utworzony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d3a19-109">This key was initially assigned by the [x:Key Directive](../../xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3a19-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3a19-110">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d3a19-111">A `StaticResource` nie wolno próbować do przodu odnieść się do zasobu, który jest zdefiniowany leksykalnie dalsze w ramach [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku.</span><span class="sxs-lookup"><span data-stu-id="d3a19-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="d3a19-112">Takie próby nie jest obsługiwany, a nawet wtedy, gdy takiego odwołania nie powiódł się, próby odwołania do przodu pociągnie za sobą zmniejszenie wydajności czas ładowania podczas tabel skrótu wewnętrznego reprezentujące <xref:System.Windows.ResourceDictionary> są przeszukiwane.</span><span class="sxs-lookup"><span data-stu-id="d3a19-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="d3a19-113">Aby uzyskać najlepsze wyniki należy dostosować kompozycji słownikach zasobów taki sposób, że można uniknąć odwołania w przód.</span><span class="sxs-lookup"><span data-stu-id="d3a19-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="d3a19-114">Jeśli nie można uniknąć odwołania do przodu, użyj [dynamicresource — rozszerzenie znaczników](dynamicresource-markup-extension.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="d3a19-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="d3a19-115">Określony <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> powinien odpowiadać istniejącego zasobu, identyfikowany za pomocą [x: Key — dyrektywa](../../xaml-services/x-key-directive.md) niektórych w na poziomie strony, aplikacji, motywy dostępne kontrolki i zasoby zewnętrzne lub zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="d3a19-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="d3a19-116">Wyszukiwania zasobów odbywa się w tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="d3a19-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="d3a19-117">Aby uzyskać więcej informacji na temat zachowania wyszukiwania zasobów dla zasobów statycznych i dynamicznych, zobacz [zasoby XAML](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="d3a19-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
 <span data-ttu-id="d3a19-118">Klucz zasobu może być dowolnym ciągiem, zdefiniowane w [xamlname — gramatyka](../../xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="d3a19-118">A resource key can be any string defined in the [XamlName Grammar](../../xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="d3a19-119">Klucz zasobu może być również inne typy obiektów, takich jak <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="d3a19-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="d3a19-120">A <xref:System.Type> klucza ma podstawowe znaczenie dla jak można różne formanty, motywy, za pomocą klucza usługi stylu niejawnego.</span><span class="sxs-lookup"><span data-stu-id="d3a19-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="d3a19-121">Aby uzyskać więcej informacji, zobacz [omówienie tworzenia kontrolek](../controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d3a19-121">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="d3a19-122">Deklaratywne alternatywnych metod odwołujące się do zasobu jest jako [dynamicresource — rozszerzenie znaczników](dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="d3a19-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="d3a19-123">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="d3a19-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="d3a19-124">Token ciągu podawany po `StaticResource` ciągu identyfikatora jest przypisany jako <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> wartości elementu bazowego <xref:System.Windows.StaticResourceExtension> rozszerzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="d3a19-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="d3a19-125">`StaticResource` może służyć w składni obiektów.</span><span class="sxs-lookup"><span data-stu-id="d3a19-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="d3a19-126">W tym przypadku określającą wartość <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d3a19-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="d3a19-127">`StaticResource` można również użycie pełnego atrybut określający <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwość jako właściwość = para wartości:</span><span class="sxs-lookup"><span data-stu-id="d3a19-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="d3a19-128">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d3a19-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="d3a19-129">Ponieważ `StaticResource` ma tylko jedną konfigurowalną właściwość, która jest wymagana, użycie tych pełne nie są typowe.</span><span class="sxs-lookup"><span data-stu-id="d3a19-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="d3a19-130">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora obsługi dla tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.StaticResourceExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="d3a19-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="d3a19-131">`StaticResource` jest rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="d3a19-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="d3a19-132">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="d3a19-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="d3a19-133">Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d3a19-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="d3a19-134">Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="d3a19-134">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a19-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3a19-135">See also</span></span>

- [<span data-ttu-id="d3a19-136">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="d3a19-136">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="d3a19-137">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="d3a19-137">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="d3a19-138">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="d3a19-138">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="d3a19-139">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="d3a19-139">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="d3a19-140">Zasoby i kod</span><span class="sxs-lookup"><span data-stu-id="d3a19-140">Resources and Code</span></span>](resources-and-code.md)
