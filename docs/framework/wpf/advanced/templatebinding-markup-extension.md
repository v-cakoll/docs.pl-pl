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
ms.openlocfilehash: 399e4ac223d2fcb728ece2c92d25a087990992f2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458670"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="f50d5-102">TemplateBinding — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="f50d5-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="f50d5-103">Łączy wartość właściwości w szablonie formantu w taki sposób, że staje się ona wartością innej właściwości w formancie z szablonem.</span><span class="sxs-lookup"><span data-stu-id="f50d5-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f50d5-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="f50d5-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="f50d5-105">Użycie atrybutu języka XAML (we właściwości settera w szablonie lub stylu)</span><span class="sxs-lookup"><span data-stu-id="f50d5-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f50d5-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="f50d5-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="f50d5-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> właściwości ustawianej we składni metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="f50d5-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="f50d5-108">Inna właściwość zależności, która istnieje w typie tworzonym przez szablon, określony przez jego <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f50d5-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="f50d5-109">oraz</span><span class="sxs-lookup"><span data-stu-id="f50d5-109">- or -</span></span><br /><br /> <span data-ttu-id="f50d5-110">„Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon.</span><span class="sxs-lookup"><span data-stu-id="f50d5-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="f50d5-111">Jest to w rzeczywistości <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="f50d5-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="f50d5-112">Zobacz [składnię XAML PropertyPath](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="f50d5-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f50d5-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f50d5-113">Remarks</span></span>  
 <span data-ttu-id="f50d5-114">`TemplateBinding` to zoptymalizowana postać [powiązania](binding-markup-extension.md) dla scenariuszy szablonów, analogiczna do `Binding` skonstruowana przy użyciu `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="f50d5-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="f50d5-115">`TemplateBinding` jest zawsze powiązanie jednokierunkowe, nawet jeśli właściwości są domyślnie powiązane z powiązaniem dwukierunkowym.</span><span class="sxs-lookup"><span data-stu-id="f50d5-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="f50d5-116">Obie używane właściwości muszą być właściwościami zależności.</span><span class="sxs-lookup"><span data-stu-id="f50d5-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="f50d5-117">Aby uzyskać dwukierunkowe powiązanie z szablonem nadrzędnym, użyj poniższego instrukcji Binding zamiast `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span><span class="sxs-lookup"><span data-stu-id="f50d5-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span> 
  
 <span data-ttu-id="f50d5-118">[RelativeSource](relativesource-markupextension.md) to inne rozszerzenie znaczników, które jest czasami używane w połączeniu z lub zamiast `TemplateBinding`, aby można było wykonać powiązanie właściwości względnej w ramach szablonu.</span><span class="sxs-lookup"><span data-stu-id="f50d5-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="f50d5-119">Opisywanie szablonów kontrolek jako koncepcji nie jest tutaj omówione; Aby uzyskać więcej informacji, zobacz [Style formantów i szablony](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="f50d5-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="f50d5-120">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="f50d5-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="f50d5-121">Token ciągu podany po ciągu identyfikatora `TemplateBinding` jest przypisywany jako wartość <xref:System.Windows.TemplateBindingExtension.Property%2A> źródłowej klasy rozszerzenia <xref:System.Windows.TemplateBindingExtension>.</span><span class="sxs-lookup"><span data-stu-id="f50d5-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="f50d5-122">Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania.</span><span class="sxs-lookup"><span data-stu-id="f50d5-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="f50d5-123">`TemplateBinding` służy do wypełniania wartości w metodach ustawiających przy użyciu wyrażeń obliczanych i używania składni elementu obiektu dla `TemplateBinding` do wypełnienia składni `<Setter.Property>` elementu właściwości jest niepotrzebnie pełne.</span><span class="sxs-lookup"><span data-stu-id="f50d5-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="f50d5-124">`TemplateBinding` można również użyć w pełnym użyciu atrybutu, który określa właściwość <xref:System.Windows.TemplateBindingExtension.Property%2A> jako parę właściwość = wartość:</span><span class="sxs-lookup"><span data-stu-id="f50d5-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="f50d5-125">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f50d5-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="f50d5-126">Ponieważ `TemplateBinding` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.</span><span class="sxs-lookup"><span data-stu-id="f50d5-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="f50d5-127">W implementacji procesora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.TemplateBindingExtension>.</span><span class="sxs-lookup"><span data-stu-id="f50d5-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="f50d5-128">`TemplateBinding` to rozszerzenie znaczników.</span><span class="sxs-lookup"><span data-stu-id="f50d5-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="f50d5-129">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="f50d5-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="f50d5-130">Wszystkie rozszerzenia znaczników w języku XAML używają znaków `{` i `}` w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut.</span><span class="sxs-lookup"><span data-stu-id="f50d5-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="f50d5-131">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f50d5-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50d5-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f50d5-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f50d5-133">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="f50d5-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="f50d5-134">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="f50d5-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="f50d5-135">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="f50d5-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="f50d5-136">RelativeSource, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="f50d5-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="f50d5-137">Rozszerzenie znaczników powiązania</span><span class="sxs-lookup"><span data-stu-id="f50d5-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
