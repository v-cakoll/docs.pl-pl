---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: a6a7d615a3a54fbc75bb86b295fdf80433a31dc5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476337"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="60be9-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="60be9-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="60be9-103">Określa właściwości <xref:System.Windows.Data.RelativeSource> źródło powiązania, do użycia w [Binding Markup Extension](binding-markup-extension.md), lub podczas ustawiania <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwość <xref:System.Windows.Data.Binding> elementu ustanowionych w XAML.</span><span class="sxs-lookup"><span data-stu-id="60be9-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="60be9-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="60be9-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="60be9-105">Użycie atrybutu języka XAML (zagnieżdżonego w rozszerzeniu Binding)</span><span class="sxs-lookup"><span data-stu-id="60be9-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="60be9-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="60be9-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="60be9-107">—lub—</span><span class="sxs-lookup"><span data-stu-id="60be9-107">-or-</span></span>

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

## <a name="xaml-values"></a><span data-ttu-id="60be9-108">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="60be9-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="60be9-109">Jeden z poniższych:</span><span class="sxs-lookup"><span data-stu-id="60be9-109">One of the following:</span></span><br /><br /> <span data-ttu-id="60be9-110">-Token ciągu `Self`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonemu z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="60be9-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="60be9-111">-Token ciągu `TemplatedParent`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonemu z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="60be9-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="60be9-112">-Token ciągu `PreviousData`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonemu z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="60be9-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="60be9-113">-Poniżej znajdują się informacje o `FindAncestor` trybu.</span><span class="sxs-lookup"><span data-stu-id="60be9-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="60be9-114">Token ciągu `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="60be9-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="60be9-115">Przy użyciu tego tokenu zgodnie z którą przechodzi w tryb `RelativeSource` Określa typ elementu nadrzędnego oraz opcjonalnie jego poziom.</span><span class="sxs-lookup"><span data-stu-id="60be9-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="60be9-116">Odpowiada to <xref:System.Windows.Data.RelativeSource> utworzonemu z jego <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="60be9-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="60be9-117">Wymagane dla `FindAncestor` trybu.</span><span class="sxs-lookup"><span data-stu-id="60be9-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="60be9-118">Nazwa typu, która wypełnia <xref:System.Windows.Data.RelativeSource.AncestorType%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="60be9-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="60be9-119">Opcjonalnie na potrzeby `FindAncestor` trybu.</span><span class="sxs-lookup"><span data-stu-id="60be9-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="60be9-120">Poziom elementu nadrzędnego (patrząc w kierunku nadrzędności w drzewie logicznym).</span><span class="sxs-lookup"><span data-stu-id="60be9-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="60be9-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60be9-121">Remarks</span></span>

<span data-ttu-id="60be9-122">`{RelativeSource TemplatedParent}` powiązań to technika odnoszący się do koncepcji oddzielania Interfejsu użytkownika formantu i od logiki formantu.</span><span class="sxs-lookup"><span data-stu-id="60be9-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="60be9-123">Umożliwia tworzenie powiązań z wewnątrz definicji szablonu do elementu nadrzędnego używającego szablonu (tzn. do wystąpienia obiektu, do którego w czasie wykonywania szablon jest stosowany).</span><span class="sxs-lookup"><span data-stu-id="60be9-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="60be9-124">Dla tego przypadku [TemplateBinding Markup Extension](templatebinding-markup-extension.md) jest w rzeczywistości skrótem następującego wyrażenia powiązania: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="60be9-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="60be9-125">`TemplateBinding` lub `{RelativeSource TemplatedParent}` użycia są istotne tylko w ramach XAML, który definiuje szablonu.</span><span class="sxs-lookup"><span data-stu-id="60be9-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="60be9-126">Aby uzyskać więcej informacji, zobacz [TemplateBinding Markup Extension](templatebinding-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="60be9-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md)</span></span>

<span data-ttu-id="60be9-127">`{RelativeSource FindAncestor}` jest głównie używane w szablonach formantów lub przewidywalnych samodzielnych kompozycjach interfejsu użytkownika, w przypadkach, w którym formantu zawsze oczekuje się, w drzewie wizualnym określonego typu elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="60be9-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="60be9-128">Na przykład, elementy z formantem elementów mogą używać `FindAncestor` elementu nadrzędnego formantu w celu utworzenia powiązania z właściwości ich pozycji.</span><span class="sxs-lookup"><span data-stu-id="60be9-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="60be9-129">Ewentualnie elementy będące częścią kompozycji formantu w szablonie można użyć `FindAncestor` powiązania z elementami nadrzędnymi w tej samej strukturze kompozycji.</span><span class="sxs-lookup"><span data-stu-id="60be9-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="60be9-130">W składni obiektów `FindAncestor` wyświetlane w sekcjach XAML składnia drugiego składnia elementu obiektu jest używana specjalnie dla trybu `FindAncestor` trybu.</span><span class="sxs-lookup"><span data-stu-id="60be9-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="60be9-131">`FindAncestor` tryb wymaga <xref:System.Windows.Data.RelativeSource.AncestorType%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="60be9-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="60be9-132">Należy ustawić <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atrybut poprzez [x: Type Markup Extension](../../xaml-services/x-type-markup-extension.md) odwołanie do typu szukanego elementu nadrzędnego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="60be9-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="60be9-133"><xref:System.Windows.Data.RelativeSource.AncestorType%2A> Wartość jest używana podczas przetwarzania żądania powiązania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="60be9-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="60be9-134">Dla `FindAncestor` tryb, opcjonalna właściwość <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> może pomóc odróżnić w przypadkach, gdzie prawdopodobnie jest więcej niż jednego elementu nadrzędnego tego typu w drzewie elementów.</span><span class="sxs-lookup"><span data-stu-id="60be9-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="60be9-135">Aby uzyskać więcej informacji na temat sposobu użycia `FindAncestor` tryb, zobacz <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="60be9-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="60be9-136">`{RelativeSource Self}` jest przydatne w scenariuszach między właściwościami, gdzie jedna właściwość wystąpienia powinna zależeć od wartości innej właściwości tego samego wystąpienia, a nie ogólna Relacja zależności (np. przekształcenie) już istnieje.</span><span class="sxs-lookup"><span data-stu-id="60be9-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="60be9-137">Chociaż rzadko, że dwie właściwości istnieje w obiekcie w taki sposób, że wartości są niemal identycznych (i takich samych typach), można także zastosować `Converter` parametr do powiązania mającego `{RelativeSource Self}`i używać konwertera do konwersji między źródłowymi i typy elementów docelowych.</span><span class="sxs-lookup"><span data-stu-id="60be9-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="60be9-138">Inny scenariusz dla `{RelativeSource Self}` jest jako część <xref:System.Windows.MultiDataTrigger>.</span><span class="sxs-lookup"><span data-stu-id="60be9-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="60be9-139">Na przykład, poniższy XAML definiuje <xref:System.Windows.Shapes.Rectangle> element takich niezależnie od wartości wprowadzonej w <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> jest zawsze kwadratem: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="60be9-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="60be9-140">`{RelativeSource PreviousData}` jest przydatne w szablonach danych lub w sytuacjach, w którym powiązania korzystają z kolekcji jako źródło danych.</span><span class="sxs-lookup"><span data-stu-id="60be9-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="60be9-141">Możesz użyć `{RelativeSource PreviousData}` może akcentować relacje między sąsiednimi elementami danych w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="60be9-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="60be9-142">Pokrewną techniką jest ustanowienie <xref:System.Windows.Data.MultiBinding> między elementami bieżącym i poprzednim w źródle danych i użyj powiązania konwertera w celu ustalenia różnic między dwoma elementami i ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="60be9-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="60be9-143">W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> w elementach szablonów pokazuje bieżący numer.</span><span class="sxs-lookup"><span data-stu-id="60be9-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="60be9-144">Drugi <xref:System.Windows.Controls.TextBlock> powiązanie jest <xref:System.Windows.Data.MultiBinding> nominalnie ma dwa <xref:System.Windows.Data.Binding> składników: bieżący rekord oraz powiązanie, które celowo używa poprzedniego rekordu danych przy użyciu `{RelativeSource PreviousData}`.</span><span class="sxs-lookup"><span data-stu-id="60be9-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="60be9-145">Następnie konwerter <xref:System.Windows.Data.MultiBinding> oblicza różnicę i zwraca go do powiązania.</span><span class="sxs-lookup"><span data-stu-id="60be9-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

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

<span data-ttu-id="60be9-146">Nie omówiono w tym miejscu całej koncepcji powiązań danych. dokładniejsze zobacz [Data Binding Overview](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="60be9-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="60be9-147">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML, obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.Data.RelativeSource> klasy.</span><span class="sxs-lookup"><span data-stu-id="60be9-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="60be9-148">`RelativeSource` jest rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="60be9-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="60be9-149">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="60be9-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="60be9-150">Wszystkie rozszerzenia znaczników w XAML użyj `{` i `}` znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="60be9-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="60be9-151">Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="60be9-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60be9-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60be9-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="60be9-153">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="60be9-153">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="60be9-154">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="60be9-154">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="60be9-155">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="60be9-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="60be9-156">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="60be9-156">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="60be9-157">Powiązanie deklaracji — omówienie</span><span class="sxs-lookup"><span data-stu-id="60be9-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="60be9-158">x:Type, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="60be9-158">x:Type Markup Extension</span></span>](../../xaml-services/x-type-markup-extension.md)
