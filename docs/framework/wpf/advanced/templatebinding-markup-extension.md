---
title: TemplateBinding — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: d425d17405bc8241c3fd85c77c6672265a060900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="05a29-102">TemplateBinding — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="05a29-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="05a29-103">Łączy wartość właściwości w szablonie formantu w taki sposób, że staje się ona wartością innej właściwości w formancie z szablonem.</span><span class="sxs-lookup"><span data-stu-id="05a29-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="05a29-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="05a29-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="05a29-105">Użycie atrybutu języka XAML (we właściwości settera w szablonie lub stylu)</span><span class="sxs-lookup"><span data-stu-id="05a29-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="05a29-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="05a29-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="05a29-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> właściwości ustawione w składni metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="05a29-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="05a29-108">Inna właściwość zależności, który istnieje w typie szablonem, określony przez jego <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05a29-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="05a29-109">- lub -</span><span class="sxs-lookup"><span data-stu-id="05a29-109">- or -</span></span><br /><br /> <span data-ttu-id="05a29-110">„Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon.</span><span class="sxs-lookup"><span data-stu-id="05a29-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="05a29-111">Jest to rzeczywiście <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="05a29-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="05a29-112">Zobacz [składnia PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="05a29-112">See [PropertyPath XAML Syntax](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05a29-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05a29-113">Remarks</span></span>  
 <span data-ttu-id="05a29-114">A `TemplateBinding` jest zoptymalizowany formę [powiązanie](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) dla scenariuszy szablonu odpowiednikiem `Binding` skonstruowany przy `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="05a29-114">A `TemplateBinding` is an optimized form of a [Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="05a29-115">A `TemplateBinding` jest zawsze jednokierunkowe powiązanie, nawet jeśli właściwości domyślnie powiązanie dwustronne.</span><span class="sxs-lookup"><span data-stu-id="05a29-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="05a29-116">Obie używane właściwości muszą być właściwościami zależności.</span><span class="sxs-lookup"><span data-stu-id="05a29-116">Both properties involved must be dependency properties.</span></span>  
  
 <span data-ttu-id="05a29-117">[RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) jest inne rozszerzenie znaczników, która czasami jest używane w połączeniu z lub a `TemplateBinding` w celu wykonywania powiązania właściwości względne w ramach szablonu.</span><span class="sxs-lookup"><span data-stu-id="05a29-117">[RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="05a29-118">Opisujące szablonów kontrolki jako koncepcji nie pasuje do Aby uzyskać więcej informacji, zobacz [stylów formantu i szablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="05a29-118">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="05a29-119">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="05a29-119">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="05a29-120">Token ciągu po `TemplateBinding` przypisany jako identyfikator ciągu <xref:System.Windows.TemplateBindingExtension.Property%2A> wartości podstawowych <xref:System.Windows.TemplateBindingExtension> rozszerzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="05a29-120">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="05a29-121">Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania.</span><span class="sxs-lookup"><span data-stu-id="05a29-121">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="05a29-122">`TemplateBinding` jest używany do wypełniania wyrażenia wartości w obrębie metody ustawiające, przy użyciu obliczone i przy użyciu obiektu składnia elementu `TemplateBinding` do wypełnienia `<Setter.Property>` jest niepotrzebnie pełne składni elementu właściwości.</span><span class="sxs-lookup"><span data-stu-id="05a29-122">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="05a29-123">`TemplateBinding` można również w Określa użycie atrybutu pełne <xref:System.Windows.TemplateBindingExtension.Property%2A> właściwości jako właściwość = pary wartości:</span><span class="sxs-lookup"><span data-stu-id="05a29-123">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="05a29-124">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="05a29-124">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="05a29-125">Ponieważ `TemplateBinding` ma tylko jedną można ustawić właściwości, która jest wymagana, to użycie Pełne nie są typowe.</span><span class="sxs-lookup"><span data-stu-id="05a29-125">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="05a29-126">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML, obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.TemplateBindingExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="05a29-126">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="05a29-127">`TemplateBinding` to rozszerzenie znacznika.</span><span class="sxs-lookup"><span data-stu-id="05a29-127">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="05a29-128">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="05a29-128">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="05a29-129">Wszystkie rozszerzenia znaczników w XAML, użyj `{` i `}` znaków w ich składni atrybutu Konwencji, za pomocą którego procesora XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="05a29-129">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="05a29-130">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="05a29-130">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a29-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05a29-131">See Also</span></span>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="05a29-132">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="05a29-132">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="05a29-133">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="05a29-133">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="05a29-134">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="05a29-134">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="05a29-135">RelativeSource, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="05a29-135">RelativeSource MarkupExtension</span></span>](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)  
 [<span data-ttu-id="05a29-136">Rozszerzenie znaczników powiązania</span><span class="sxs-lookup"><span data-stu-id="05a29-136">Binding Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
