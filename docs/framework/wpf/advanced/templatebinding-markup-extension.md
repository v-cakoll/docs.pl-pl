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
ms.openlocfilehash: 8c631a5a78db90187f0375181d4d4d1832159b7d
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646168"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="83c9e-102">TemplateBinding — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="83c9e-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="83c9e-103">Łączy wartość właściwości w szablonie formantu w taki sposób, że staje się ona wartością innej właściwości w formancie z szablonem.</span><span class="sxs-lookup"><span data-stu-id="83c9e-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="83c9e-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="83c9e-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="83c9e-105">Użycie atrybutu języka XAML (we właściwości settera w szablonie lub stylu)</span><span class="sxs-lookup"><span data-stu-id="83c9e-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="83c9e-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="83c9e-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="83c9e-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>właściwości ustawionej w składni ustawiacza.</span><span class="sxs-lookup"><span data-stu-id="83c9e-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="83c9e-108">Inna właściwość zależności, która istnieje na typie, <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>który jest szablonem, określony przez jego .</span><span class="sxs-lookup"><span data-stu-id="83c9e-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="83c9e-109">— lub —</span><span class="sxs-lookup"><span data-stu-id="83c9e-109">- or -</span></span><br /><br /> <span data-ttu-id="83c9e-110">„Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon.</span><span class="sxs-lookup"><span data-stu-id="83c9e-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="83c9e-111">To jest <xref:System.Windows.PropertyPath>rzeczywiście .</span><span class="sxs-lookup"><span data-stu-id="83c9e-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="83c9e-112">Zobacz [Składnia XAML ścieżki właściwości](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="83c9e-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83c9e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83c9e-113">Remarks</span></span>  
 <span data-ttu-id="83c9e-114">A `TemplateBinding` jest zoptymalizowaną formą [Powiązania](binding-markup-extension.md) dla scenariuszy szablonów, analogiczną do skonstruowanej `Binding` za pomocą `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`programu .</span><span class="sxs-lookup"><span data-stu-id="83c9e-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`.</span></span> <span data-ttu-id="83c9e-115">A `TemplateBinding` jest zawsze jednokierunkowe powiązanie, nawet jeśli właściwości zaangażowane domyślnie do wiązania dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="83c9e-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="83c9e-116">Obie używane właściwości muszą być właściwościami zależności.</span><span class="sxs-lookup"><span data-stu-id="83c9e-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="83c9e-117">Aby osiągnąć dwukierunkowe powiązanie z elementem nadrzędnym szablonem, użyj następującej instrukcji powiązania `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`zamiast .</span><span class="sxs-lookup"><span data-stu-id="83c9e-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span>
  
 <span data-ttu-id="83c9e-118">[RelativeSource](relativesource-markupextension.md) to kolejne rozszerzenie znaczników, które jest czasami `TemplateBinding` używane w połączeniu z lub zamiast w celu wykonania powiązania właściwości względnej w szablonie.</span><span class="sxs-lookup"><span data-stu-id="83c9e-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="83c9e-119">Opisywanie szablonów formantu jako koncepcji nie jest tutaj omówione; Aby uzyskać więcej informacji, zobacz [Style sterowania i szablony](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="83c9e-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="83c9e-120">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="83c9e-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="83c9e-121">Token ciągu podany `TemplateBinding` po ciągu identyfikatora jest <xref:System.Windows.TemplateBindingExtension.Property%2A> przypisany <xref:System.Windows.TemplateBindingExtension> jako wartość podstawowej klasy rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="83c9e-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="83c9e-122">Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania.</span><span class="sxs-lookup"><span data-stu-id="83c9e-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="83c9e-123">`TemplateBinding`służy do wypełniania wartości w obrębie ustawiaczy, przy użyciu obliczonych `TemplateBinding` wyrażeń, a używanie składni elementu obiektu do wypełniania `<Setter.Property>` składni elementu właściwości jest niepotrzebnie pełne.</span><span class="sxs-lookup"><span data-stu-id="83c9e-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="83c9e-124">`TemplateBinding`może być również używany w użyciu atrybutu pełne, <xref:System.Windows.TemplateBindingExtension.Property%2A> który określa właściwość jako właściwość = parę wartości:</span><span class="sxs-lookup"><span data-stu-id="83c9e-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="83c9e-125">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="83c9e-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="83c9e-126">Ponieważ `TemplateBinding` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.</span><span class="sxs-lookup"><span data-stu-id="83c9e-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="83c9e-127">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML obsługa tego rozszerzenia znaczników jest definiowana <xref:System.Windows.TemplateBindingExtension> przez klasę.</span><span class="sxs-lookup"><span data-stu-id="83c9e-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="83c9e-128">`TemplateBinding`jest rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="83c9e-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="83c9e-129">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="83c9e-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="83c9e-130">Wszystkie rozszerzenia znaczników w XAML używają `{` znaków i `}` w składni atrybutów, czyli konwencji, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znaczników musi przetworzyć atrybut.</span><span class="sxs-lookup"><span data-stu-id="83c9e-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="83c9e-131">Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="83c9e-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c9e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83c9e-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="83c9e-133">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="83c9e-133">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="83c9e-134">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="83c9e-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="83c9e-135">Rozszerzenia znacznikowania i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="83c9e-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="83c9e-136">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="83c9e-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="83c9e-137">Rozszerzenie znaczników powiązania</span><span class="sxs-lookup"><span data-stu-id="83c9e-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
