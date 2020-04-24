---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 6301299da966ade9b5cc7ccd105c8269a486744e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646228"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="fc0da-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="fc0da-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="fc0da-103">Określa właściwości źródła <xref:System.Windows.Data.RelativeSource> powiązania, które mają być używane w [rozszerzeniu znaczników powiązania](binding-markup-extension.md)lub podczas ustawiania <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwości <xref:System.Windows.Data.Binding> elementu ustanowionego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="fc0da-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="fc0da-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="fc0da-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="fc0da-105">Użycie atrybutu języka XAML (zagnieżdżonego w rozszerzeniu Binding)</span><span class="sxs-lookup"><span data-stu-id="fc0da-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="fc0da-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="fc0da-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="fc0da-107">— lub —</span><span class="sxs-lookup"><span data-stu-id="fc0da-107">-or-</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a><span data-ttu-id="fc0da-108">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="fc0da-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="fc0da-109">Jeden z poniższych programów:</span><span class="sxs-lookup"><span data-stu-id="fc0da-109">One of the following:</span></span><br /><br /> <span data-ttu-id="fc0da-110">- Token `Self`ciągu; odpowiada utworzonej <xref:System.Windows.Data.RelativeSource> z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.Self>ustawioną na .</span><span class="sxs-lookup"><span data-stu-id="fc0da-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="fc0da-111">- Token `TemplatedParent`ciągu; odpowiada utworzonej <xref:System.Windows.Data.RelativeSource> z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>ustawioną na .</span><span class="sxs-lookup"><span data-stu-id="fc0da-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="fc0da-112">- Token `PreviousData`ciągu; odpowiada utworzonej <xref:System.Windows.Data.RelativeSource> z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.PreviousData>ustawioną na .</span><span class="sxs-lookup"><span data-stu-id="fc0da-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="fc0da-113">- Zobacz poniżej, aby uzyskać informacje na `FindAncestor` temat trybu.</span><span class="sxs-lookup"><span data-stu-id="fc0da-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="fc0da-114">Token `FindAncestor`ciągu .</span><span class="sxs-lookup"><span data-stu-id="fc0da-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="fc0da-115">Za pomocą tego tokenu wchodzi `RelativeSource` w tryb, w którym określa typ nadrzędny i opcjonalnie poziom nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="fc0da-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="fc0da-116">Odpowiada to utworzonej z jego właściwością ustawioną <xref:System.Windows.Data.RelativeSource> <xref:System.Windows.Data.RelativeSource.Mode%2A> na <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="fc0da-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="fc0da-117">Wymagane w `FindAncestor` trybie.</span><span class="sxs-lookup"><span data-stu-id="fc0da-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="fc0da-118">Nazwa typu, który wypełnia <xref:System.Windows.Data.RelativeSource.AncestorType%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="fc0da-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="fc0da-119">Opcjonalnie `FindAncestor` dla trybu.</span><span class="sxs-lookup"><span data-stu-id="fc0da-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="fc0da-120">Poziom elementu nadrzędnego (patrząc w kierunku nadrzędności w drzewie logicznym).</span><span class="sxs-lookup"><span data-stu-id="fc0da-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="fc0da-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc0da-121">Remarks</span></span>

<span data-ttu-id="fc0da-122">`{RelativeSource TemplatedParent}`użycie wiązania są kluczową techniką, która rozwiązuje się z większą koncepcją oddzielenia interfejsu użytkownika formantu i logiki formantu.</span><span class="sxs-lookup"><span data-stu-id="fc0da-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="fc0da-123">Umożliwia tworzenie powiązań z wewnątrz definicji szablonu do elementu nadrzędnego używającego szablonu (tzn. do wystąpienia obiektu, do którego w czasie wykonywania szablon jest stosowany).</span><span class="sxs-lookup"><span data-stu-id="fc0da-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="fc0da-124">W tym przypadku [rozszerzenie templatebinding znaczników](templatebinding-markup-extension.md) jest w rzeczywistości skrótem `{Binding RelativeSource={RelativeSource TemplatedParent}}`dla następującego wyrażenia wiązania: .</span><span class="sxs-lookup"><span data-stu-id="fc0da-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="fc0da-125">`TemplateBinding`lub `{RelativeSource TemplatedParent}` użycia są istotne tylko w XAML, który definiuje szablon.</span><span class="sxs-lookup"><span data-stu-id="fc0da-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="fc0da-126">Aby uzyskać więcej informacji, zobacz [Rozszerzenie znaczników powiązanie szablonu .](templatebinding-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="fc0da-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="fc0da-127">`{RelativeSource FindAncestor}`jest używany głównie w szablonach kontroli lub przewidywalne kompozycje interfejsu użytkownika, w przypadkach, gdy formant jest zawsze oczekuje się w drzewie wizualnym określonego typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fc0da-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="fc0da-128">Na przykład elementy formantu `FindAncestor` elementów może używać użycia do powiązania z właściwości ich elementów nadrzędnego nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fc0da-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="fc0da-129">Lub elementy, które są częścią kompozycji `FindAncestor` kontroli w szablonie można użyć powiązań do elementów nadrzędnych w tej samej strukturze kompozycji.</span><span class="sxs-lookup"><span data-stu-id="fc0da-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="fc0da-130">W składni elementu obiektu `FindAncestor` dla trybu pokazanego w sekcjach składni XAML składnia drugiego `FindAncestor` elementu obiektu jest używana specjalnie dla trybu.</span><span class="sxs-lookup"><span data-stu-id="fc0da-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="fc0da-131">`FindAncestor`wymaga <xref:System.Windows.Data.RelativeSource.AncestorType%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="fc0da-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="fc0da-132">Należy ustawić <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atrybut przy użyciu [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) odwołania do typu element nadrzędny, aby wyszukać.</span><span class="sxs-lookup"><span data-stu-id="fc0da-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="fc0da-133">Wartość <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jest używana, gdy żądanie powiązania jest przetwarzane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fc0da-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="fc0da-134">Dla `FindAncestor` trybu, opcjonalna właściwość <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> może pomóc rozróżniać wyszukiwanie nadrzędnego w przypadkach, gdy istnieje prawdopodobnie więcej niż jeden element nadrzędny tego typu istniejących w drzewie elementów.</span><span class="sxs-lookup"><span data-stu-id="fc0da-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="fc0da-135">Aby uzyskać więcej informacji `FindAncestor` na temat <xref:System.Windows.Data.RelativeSource>korzystania z tego trybu, zobacz .</span><span class="sxs-lookup"><span data-stu-id="fc0da-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="fc0da-136">`{RelativeSource Self}`jest przydatne w scenariuszach, w których jedna właściwość wystąpienia powinna zależeć od wartości innej właściwości tego samego wystąpienia, a nie ma już ogólnej relacji właściwości zależności (takiej jak przymus) między tymi dwiema właściwościami.</span><span class="sxs-lookup"><span data-stu-id="fc0da-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="fc0da-137">Chociaż rzadko istnieją dwie właściwości obiektu, takie jak, że wartości są dosłownie identyczne (i `Converter` są identycznie wpisane), można również zastosować parametr do powiązania, które ma `{RelativeSource Self}`, i użyć konwertera do konwersji między typami źródłowymi i docelowymi.</span><span class="sxs-lookup"><span data-stu-id="fc0da-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="fc0da-138">Innym scenariuszem `{RelativeSource Self}` jest jako <xref:System.Windows.MultiDataTrigger>część .</span><span class="sxs-lookup"><span data-stu-id="fc0da-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="fc0da-139">Na przykład następujący kod XAML <xref:System.Windows.Shapes.Rectangle> definiuje element w taki sposób, <xref:System.Windows.FrameworkElement.Width%2A>że <xref:System.Windows.Shapes.Rectangle> bez względu na to, dla jakiej wartości jest wprowadzona wartość, jest zawsze kwadratem:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="fc0da-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="fc0da-140">`{RelativeSource PreviousData}`jest przydatne w szablonach danych lub w przypadkach, gdy powiązania używają kolekcji jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="fc0da-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="fc0da-141">Można użyć `{RelativeSource PreviousData}` do podświetlenia relacji między sąsiednimi elementami danych w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fc0da-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="fc0da-142">Technika pokrewna <xref:System.Windows.Data.MultiBinding> jest ustanowienie między bieżącymi i poprzednimi elementami w źródle danych i użyć konwertera na tym wiązanie, aby określić różnicę między dwoma elementami i ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc0da-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="fc0da-143">W poniższym przykładzie <xref:System.Windows.Controls.TextBlock> pierwszy w szablonie elementów wyświetla bieżący numer.</span><span class="sxs-lookup"><span data-stu-id="fc0da-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="fc0da-144">Drugie <xref:System.Windows.Controls.TextBlock> powiązanie <xref:System.Windows.Data.MultiBinding> jest nominalnie <xref:System.Windows.Data.Binding> ma dwa składniki: bieżący rekord i powiązanie, które celowo `{RelativeSource PreviousData}`używa poprzedniego rekordu danych za pomocą .</span><span class="sxs-lookup"><span data-stu-id="fc0da-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="fc0da-145">Następnie konwerter na <xref:System.Windows.Data.MultiBinding> oblicza różnicę i zwraca ją do powiązania.</span><span class="sxs-lookup"><span data-stu-id="fc0da-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
```

<span data-ttu-id="fc0da-146">Opisujące powiązanie danych jako pojęcie nie jest tutaj omówione, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fc0da-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="fc0da-147">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML obsługa tego rozszerzenia znaczników jest definiowana <xref:System.Windows.Data.RelativeSource> przez klasę.</span><span class="sxs-lookup"><span data-stu-id="fc0da-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="fc0da-148">`RelativeSource`jest rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="fc0da-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="fc0da-149">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="fc0da-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="fc0da-150">Wszystkie rozszerzenia znaczników w XAML używają `{` znaków i `}` w składni atrybutów, czyli konwencji, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znaczników musi przetworzyć atrybut.</span><span class="sxs-lookup"><span data-stu-id="fc0da-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="fc0da-151">Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="fc0da-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc0da-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc0da-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="fc0da-153">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="fc0da-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="fc0da-154">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="fc0da-154">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="fc0da-155">Rozszerzenia znacznikowania i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="fc0da-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="fc0da-156">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="fc0da-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="fc0da-157">Przegląd Wiązanie deklaracji</span><span class="sxs-lookup"><span data-stu-id="fc0da-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="fc0da-158">x:Type — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="fc0da-158">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
