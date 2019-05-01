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
ms.openlocfilehash: c004560a0b7ab367fbf4fbb48b0e8d8b63f3d8f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053044"
---
# <a name="templatebinding-markup-extension"></a><span data-ttu-id="70679-102">TemplateBinding — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="70679-102">TemplateBinding Markup Extension</span></span>
<span data-ttu-id="70679-103">Łączy wartość właściwości w szablonie formantu w taki sposób, że staje się ona wartością innej właściwości w formancie z szablonem.</span><span class="sxs-lookup"><span data-stu-id="70679-103">Links the value of a property in a control template to be the value of another property on the templated control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="70679-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="70679-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a><span data-ttu-id="70679-105">Użycie atrybutu języka XAML (we właściwości settera w szablonie lub stylu)</span><span class="sxs-lookup"><span data-stu-id="70679-105">XAML Attribute Usage (for Setter property in template or style)</span></span>  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="70679-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="70679-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`propertyName`|<span data-ttu-id="70679-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> właściwości ustawiany w składni settera.</span><span class="sxs-lookup"><span data-stu-id="70679-107"><xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> of the property being set in the setter syntax.</span></span>|  
|`sourceProperty`|<span data-ttu-id="70679-108">Inna właściwość zależności istniejąca w typie są oparte na szablonach, określony przez jego <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70679-108">Another dependency property that exists on the type being templated, specified by its <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.</span></span><br /><br /> <span data-ttu-id="70679-109">- lub -</span><span class="sxs-lookup"><span data-stu-id="70679-109">- or -</span></span><br /><br /> <span data-ttu-id="70679-110">„Spisana” nazwa właściwości definiowana przez typ inny niż docelowy typ, dla którego jest ustawiany szablon.</span><span class="sxs-lookup"><span data-stu-id="70679-110">A "dotted-down" property name that is defined by a different type than the target type being templated.</span></span> <span data-ttu-id="70679-111">Jest to rzeczywiście <xref:System.Windows.PropertyPath>.</span><span class="sxs-lookup"><span data-stu-id="70679-111">This is actually a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="70679-112">Zobacz [składnia elementu PropertyPath XAML](propertypath-xaml-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="70679-112">See [PropertyPath XAML Syntax](propertypath-xaml-syntax.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70679-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70679-113">Remarks</span></span>  
 <span data-ttu-id="70679-114">A `TemplateBinding` jest zoptymalizowane formą [powiązanie](binding-markup-extension.md) dla scenariuszy szablonów, analogiczne do `Binding` skonstruowany przy użyciu `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="70679-114">A `TemplateBinding` is an optimized form of a [Binding](binding-markup-extension.md) for template scenarios, analogous to a `Binding` constructed with `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="70679-115">Element `TemplateBinding` jest zawsze powiązaniem jednokierunkowym, nawet jeśli jego właściwości domyślnie określają powiązanie dwukierunkowe.</span><span class="sxs-lookup"><span data-stu-id="70679-115">A `TemplateBinding` is always a one-way binding, even if properties involved default to two-way binding.</span></span> <span data-ttu-id="70679-116">Obie używane właściwości muszą być właściwościami zależności.</span><span class="sxs-lookup"><span data-stu-id="70679-116">Both properties involved must be dependency properties.</span></span> <span data-ttu-id="70679-117">Aby osiągnąć określają powiązanie dwukierunkowe oparte na szablonach nadrzędnej następującą instrukcję powiązanie zamiast tego użyj `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span><span class="sxs-lookup"><span data-stu-id="70679-117">In order to achieve two-way binding to a templated parent use the following binding statement instead `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.</span></span> 
  
 <span data-ttu-id="70679-118">[RelativeSource](relativesource-markupextension.md) jest kolejnym rozszerzeniem znacznika, którego używa się czasami w połączeniu lub zamiast `TemplateBinding` w celu względnego powiązania właściwości w szablonie.</span><span class="sxs-lookup"><span data-stu-id="70679-118">[RelativeSource](relativesource-markupextension.md) is another markup extension that is sometimes used in conjunction with or instead of `TemplateBinding` in order to perform relative property binding within a template.</span></span>  
  
 <span data-ttu-id="70679-119">Opisujące szablony kontrolek jako koncepcja nie jest objęty tutaj; Aby uzyskać więcej informacji, zobacz [style i szablony kontrolek](../controls/control-styles-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="70679-119">Describing control templates as a concept is not covered here; for more information, see [Control Styles and Templates](../controls/control-styles-and-templates.md).</span></span>  
  
 <span data-ttu-id="70679-120">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="70679-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="70679-121">Token ciągu podawany po `TemplateBinding` ciągu identyfikatora jest przypisany jako <xref:System.Windows.TemplateBindingExtension.Property%2A> wartości elementu bazowego <xref:System.Windows.TemplateBindingExtension> rozszerzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="70679-121">The string token provided after the `TemplateBinding` identifier string is assigned as the <xref:System.Windows.TemplateBindingExtension.Property%2A> value of the underlying <xref:System.Windows.TemplateBindingExtension> extension class.</span></span>  
  
 <span data-ttu-id="70679-122">Można wprowadzić składnię obiektów, jednak nie pokazano jej tutaj, ponieważ nie ma praktycznego zastosowania.</span><span class="sxs-lookup"><span data-stu-id="70679-122">Object element syntax is possible, but it is not shown because it has no realistic application.</span></span> <span data-ttu-id="70679-123">`TemplateBinding` Służy do wypełnienia wartości setterami przy użyciu obliczane wyrażenia, a za pomocą składni obiektów `TemplateBinding` do wypełnienia `<Setter.Property>` składni elementu właściwości to niepotrzebne powielenie informacji.</span><span class="sxs-lookup"><span data-stu-id="70679-123">`TemplateBinding` is used to fill values within setters, using evaluated expressions, and using object element syntax for `TemplateBinding` to fill `<Setter.Property>` property element syntax is unnecessarily verbose.</span></span>  
  
 <span data-ttu-id="70679-124">`TemplateBinding` można również użycie pełnego atrybut określający <xref:System.Windows.TemplateBindingExtension.Property%2A> właściwość jako właściwość = para wartości:</span><span class="sxs-lookup"><span data-stu-id="70679-124">`TemplateBinding` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.TemplateBindingExtension.Property%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 <span data-ttu-id="70679-125">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="70679-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="70679-126">Ponieważ `TemplateBinding` ma tylko jedną konfigurowalną właściwość, która jest wymagana, użycie tych pełne nie są typowe.</span><span class="sxs-lookup"><span data-stu-id="70679-126">Because `TemplateBinding` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="70679-127">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML, obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.TemplateBindingExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="70679-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.TemplateBindingExtension> class.</span></span>  
  
 <span data-ttu-id="70679-128">`TemplateBinding` jest rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="70679-128">`TemplateBinding` is a markup extension.</span></span> <span data-ttu-id="70679-129">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="70679-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="70679-130">Wszystkie rozszerzenia znaczników w XAML użyj `{` i `}` znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="70679-130">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="70679-131">Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="70679-131">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70679-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70679-132">See also</span></span>

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="70679-133">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="70679-133">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="70679-134">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="70679-134">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="70679-135">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="70679-135">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="70679-136">RelativeSource, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="70679-136">RelativeSource MarkupExtension</span></span>](relativesource-markupextension.md)
- [<span data-ttu-id="70679-137">Rozszerzenie znaczników powiązania</span><span class="sxs-lookup"><span data-stu-id="70679-137">Binding Markup Extension</span></span>](binding-markup-extension.md)
