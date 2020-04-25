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
ms.openlocfilehash: 69698db8b51e3872d5941d4fba67271b1e61226e
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140459"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="f2b99-102">TemplateBinding — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="f2b99-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="f2b99-103">Łączy wartość właściwości w szablonie formantu w taki sposób, że staje się ona wartością innej właściwości w formancie z szablonem.</span><span class="sxs-lookup"><span data-stu-id="f2b99-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f2b99-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="f2b99-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" ... />
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="f2b99-105">Użycie atrybutu języka XAML (we właściwości settera w szablonie lub stylu)</span><span class="sxs-lookup"><span data-stu-id="f2b99-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" ... />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f2b99-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="f2b99-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="f2b99-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>Właściwości ustawianej we składni metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="f2b99-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="f2b99-108">Inna właściwość zależności, która istnieje w typie tworzonym przez szablon, określona przez <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>jego wartość.</span><span class="sxs-lookup"><span data-stu-id="f2b99-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="f2b99-109">— lub —</span><span class="sxs-lookup"><span data-stu-id="f2b99-109">- or -</span></span><br /><br /> <span data-ttu-id="f2b99-110">„Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon.</span><span class="sxs-lookup"><span data-stu-id="f2b99-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="f2b99-111">Jest to w <xref:System.Windows.PropertyPath>rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="f2b99-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="f2b99-112">Zobacz [składnię XAML PropertyPath](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="f2b99-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2b99-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2b99-113">Remarks</span></span>  
 <span data-ttu-id="f2b99-114">A `TemplateBinding` to zoptymalizowana postać [powiązania](binding-markup-extension.md) dla scenariuszy szablonów, analogiczne do `Binding` zbudowane z. `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`</span><span class="sxs-lookup"><span data-stu-id="f2b99-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`.</span></span> <span data-ttu-id="f2b99-115">`TemplateBinding` Jest zawsze powiązanie jednokierunkowe, nawet jeśli właściwości są domyślnie powiązane z powiązaniem dwukierunkowym.</span><span class="sxs-lookup"><span data-stu-id="f2b99-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="f2b99-116">Obie używane właściwości muszą być właściwościami zależności.</span><span class="sxs-lookup"><span data-stu-id="f2b99-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="f2b99-117">Aby uzyskać dwukierunkowe powiązanie z szablonem nadrzędnym, użyj w zamian `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`następującej instrukcji Binding.</span><span class="sxs-lookup"><span data-stu-id="f2b99-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span>
  
 <span data-ttu-id="f2b99-118">[RelativeSource](relativesource-markupextension.md) to inne rozszerzenie znaczników, które jest czasami używane w połączeniu z lub zamiast `TemplateBinding` w celu wykonania względnego powiązania właściwości w ramach szablonu.</span><span class="sxs-lookup"><span data-stu-id="f2b99-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="f2b99-119">Opisywanie szablonów kontrolek jako koncepcji nie jest tutaj omówione; Aby uzyskać więcej informacji, zobacz [Style formantów i szablony](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="f2b99-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="f2b99-120">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="f2b99-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="f2b99-121">Token ciągu podany po ciągu `TemplateBinding` identyfikatora jest przypisywany jako <xref:System.Windows.TemplateBindingExtension.Property%2A> wartość źródłowej <xref:System.Windows.TemplateBindingExtension> klasy rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f2b99-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="f2b99-122">Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania.</span><span class="sxs-lookup"><span data-stu-id="f2b99-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="f2b99-123">`TemplateBinding`służy do wypełniania wartości w metodach ustawiających przy użyciu wyrażeń obliczanych i użycie składni `TemplateBinding` elementu obiektu `<Setter.Property>` dla do wypełniania składni elementu właściwości jest niepotrzebnie pełne.</span><span class="sxs-lookup"><span data-stu-id="f2b99-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="f2b99-124">`TemplateBinding`można go również użyć w pełnym użyciu atrybutu, który określa <xref:System.Windows.TemplateBindingExtension.Property%2A> właściwość jako pary właściwość = wartość:</span><span class="sxs-lookup"><span data-stu-id="f2b99-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" ... />
```  
  
 <span data-ttu-id="f2b99-125">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f2b99-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="f2b99-126">Ponieważ `TemplateBinding` ma tylko jedną właściwość settable, która jest wymagana, to pełne użycie nie jest typowe.</span><span class="sxs-lookup"><span data-stu-id="f2b99-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="f2b99-127">W implementacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesora XAML obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.TemplateBindingExtension> klasę.</span><span class="sxs-lookup"><span data-stu-id="f2b99-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="f2b99-128">`TemplateBinding`jest rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="f2b99-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="f2b99-129">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="f2b99-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="f2b99-130">Wszystkie rozszerzenia znaczników w języku XAML używają `{` znaków `}` i w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut.</span><span class="sxs-lookup"><span data-stu-id="f2b99-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="f2b99-131">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f2b99-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b99-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2b99-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f2b99-133">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="f2b99-133">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f2b99-134">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="f2b99-134">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="f2b99-135">Rozszerzenia znacznikowania i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="f2b99-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="f2b99-136">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="f2b99-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="f2b99-137">Rozszerzenie znaczników powiązania</span><span class="sxs-lookup"><span data-stu-id="f2b99-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
