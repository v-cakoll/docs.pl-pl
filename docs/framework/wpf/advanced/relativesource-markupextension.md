---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 28f3aa500014b768bd07723511613a42df8689aa
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458772"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="5de7c-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="5de7c-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="5de7c-103">Określa właściwości źródła powiązań <xref:System.Windows.Data.RelativeSource>, które ma być używane w ramach [rozszerzenia znacznika powiązania](binding-markup-extension.md)lub podczas ustawiania właściwości <xref:System.Windows.Data.Binding.RelativeSource%2A> elementu <xref:System.Windows.Data.Binding> ustalonego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="5de7c-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="5de7c-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="5de7c-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="5de7c-105">Użycie atrybutu języka XAML (zagnieżdżonego w rozszerzeniu Binding)</span><span class="sxs-lookup"><span data-stu-id="5de7c-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="5de7c-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="5de7c-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="5de7c-107">—lub—</span><span class="sxs-lookup"><span data-stu-id="5de7c-107">-or-</span></span>

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

## <a name="xaml-values"></a><span data-ttu-id="5de7c-108">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="5de7c-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="5de7c-109">Jeden z poniższych:</span><span class="sxs-lookup"><span data-stu-id="5de7c-109">One of the following:</span></span><br /><br /> <span data-ttu-id="5de7c-110">-Token ciągu `Self`; odnosi się do <xref:System.Windows.Data.RelativeSource>, jak zostało utworzone z właściwością <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną na <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="5de7c-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="5de7c-111">-Token ciągu `TemplatedParent`; odnosi się do <xref:System.Windows.Data.RelativeSource>, jak zostało utworzone z właściwością <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną na <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="5de7c-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="5de7c-112">-Token ciągu `PreviousData`; odnosi się do <xref:System.Windows.Data.RelativeSource>, jak zostało utworzone z właściwością <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną na <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="5de7c-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="5de7c-113">-Zobacz poniżej, aby uzyskać informacje o trybie `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="5de7c-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="5de7c-114">Token ciągu `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="5de7c-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="5de7c-115">Użycie tego tokenu spowoduje przejście do trybu, w którym `RelativeSource` określa typ elementu nadrzędnego i opcjonalnie poziom nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="5de7c-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="5de7c-116">Odnosi się to do <xref:System.Windows.Data.RelativeSource>, jak zostało utworzone z właściwością <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną na <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="5de7c-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="5de7c-117">Wymagany w trybie `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="5de7c-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="5de7c-118">Nazwa typu, który wypełnia Właściwość <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="5de7c-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="5de7c-119">Opcjonalne dla trybu `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="5de7c-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="5de7c-120">Poziom elementu nadrzędnego (patrząc w kierunku nadrzędności w drzewie logicznym).</span><span class="sxs-lookup"><span data-stu-id="5de7c-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="5de7c-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5de7c-121">Remarks</span></span>

<span data-ttu-id="5de7c-122">Użycie powiązań `{RelativeSource TemplatedParent}` jest kluczową techniką, która odnosi się do większej koncepcji separacji interfejsu użytkownika kontrolki i logiki kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5de7c-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="5de7c-123">Umożliwia tworzenie powiązań z wewnątrz definicji szablonu do elementu nadrzędnego używającego szablonu (tzn. do wystąpienia obiektu, do którego w czasie wykonywania szablon jest stosowany).</span><span class="sxs-lookup"><span data-stu-id="5de7c-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="5de7c-124">W takim przypadku rozszerzenie " [TemplateBinding Markup](templatebinding-markup-extension.md) " jest w istocie skrót dla następującego wyrażenia powiązania: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="5de7c-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="5de7c-125">`TemplateBinding` lub `{RelativeSource TemplatedParent}` użycia są odpowiednie tylko w kodzie XAML, który definiuje szablon.</span><span class="sxs-lookup"><span data-stu-id="5de7c-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="5de7c-126">Aby uzyskać więcej informacji, zobacz [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="5de7c-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="5de7c-127">`{RelativeSource FindAncestor}` jest używany głównie w szablonach kontroli lub przewidywalnym samoobsługowym kompozycjom interfejsu użytkownika, w przypadkach, gdy kontrolka zawsze powinna znajdować się w drzewie wizualnym określonego typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5de7c-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="5de7c-128">Na przykład elementy formantu Items mogą używać `FindAncestor` użycia, aby powiązać z właściwościami ich elementów w nadrzędnym elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="5de7c-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="5de7c-129">Lub elementy, które są częścią kompozycji formantu w szablonie, mogą używać powiązań `FindAncestor` do elementów nadrzędnych w tej samej strukturze kompozycji.</span><span class="sxs-lookup"><span data-stu-id="5de7c-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="5de7c-130">W składni elementu obiektu dla `FindAncestor` trybu pokazanego w sekcjach składni języka XAML druga składnia elementu obiektu jest używana w trybie `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="5de7c-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="5de7c-131">Tryb `FindAncestor` wymaga wartości <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="5de7c-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="5de7c-132">Należy ustawić <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atrybut przy użyciu odwołania do [rozszerzenia znacznika x:Type —](../../xaml-services/x-type-markup-extension.md) do typu elementu nadrzędnego, który ma zostać wyszukany.</span><span class="sxs-lookup"><span data-stu-id="5de7c-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="5de7c-133">Wartość <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jest używana, gdy żądanie powiązania jest przetwarzane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5de7c-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="5de7c-134">W trybie `FindAncestor` Właściwość opcjonalna <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> może pomóc w odróżnieniu wyszukiwania nadrzędnego w przypadkach, gdy istnieje więcej niż jeden element nadrzędny tego typu istniejący w drzewie elementów.</span><span class="sxs-lookup"><span data-stu-id="5de7c-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="5de7c-135">Aby uzyskać więcej informacji na temat używania trybu `FindAncestor`, zobacz <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="5de7c-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="5de7c-136">`{RelativeSource Self}` jest przydatne w scenariuszach, w których jedna Właściwość wystąpienia powinna zależeć od wartości innej właściwości tego samego wystąpienia, a żadna relacja głównej właściwości zależności (na przykład przekształcenie) już istnieje między tymi dwiema właściwościami.</span><span class="sxs-lookup"><span data-stu-id="5de7c-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="5de7c-137">Chociaż jest to rzadki, że dwie właściwości istnieją w obiekcie, tak że wartości są identyczne (i są identyczne), można również zastosować `Converter` parametru do powiązania, które ma `{RelativeSource Self}`, i użyć konwertera do konwersji między źródłem i docelowym Typ.</span><span class="sxs-lookup"><span data-stu-id="5de7c-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="5de7c-138">Inny scenariusz dla `{RelativeSource Self}` jest częścią <xref:System.Windows.MultiDataTrigger>.</span><span class="sxs-lookup"><span data-stu-id="5de7c-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="5de7c-139">Na przykład poniższy kod XAML definiuje <xref:System.Windows.Shapes.Rectangle> elementu, w taki sposób, aby niezależnie od wartości wprowadzonej dla <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> jest zawsze kwadratem: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="5de7c-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="5de7c-140">`{RelativeSource PreviousData}` jest przydatne w szablonach danych lub w przypadkach, gdy powiązania używają kolekcji jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5de7c-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="5de7c-141">Możesz użyć `{RelativeSource PreviousData}`, aby wyróżnić relacje między sąsiednimi elementami danych w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5de7c-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="5de7c-142">Pokrewna Technika polega na ustanowieniu <xref:System.Windows.Data.MultiBinding> między bieżącą i poprzednimi elementami w źródle danych, a następnie użyć konwertera dla tego powiązania, aby określić różnicę między dwoma elementami i ich właściwościami.</span><span class="sxs-lookup"><span data-stu-id="5de7c-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="5de7c-143">W poniższym przykładzie pierwsze <xref:System.Windows.Controls.TextBlock> w szablonie Items wyświetla bieżącą liczbę.</span><span class="sxs-lookup"><span data-stu-id="5de7c-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="5de7c-144">Drugie powiązanie <xref:System.Windows.Controls.TextBlock> jest <xref:System.Windows.Data.MultiBinding>, która nominalnie ma dwa elementy <xref:System.Windows.Data.Binding>e: bieżący rekord i powiązanie, które w sposób celowy używa poprzedniego rekordu danych przy użyciu `{RelativeSource PreviousData}`.</span><span class="sxs-lookup"><span data-stu-id="5de7c-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="5de7c-145">Następnie konwerter <xref:System.Windows.Data.MultiBinding> oblicza różnicę i zwraca go do powiązania.</span><span class="sxs-lookup"><span data-stu-id="5de7c-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

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

<span data-ttu-id="5de7c-146">Opisywanie powiązania danych jako koncepcji nie jest tutaj omówione, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5de7c-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="5de7c-147">W implementacji procesora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="5de7c-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="5de7c-148">`RelativeSource` to rozszerzenie znaczników.</span><span class="sxs-lookup"><span data-stu-id="5de7c-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="5de7c-149">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="5de7c-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="5de7c-150">Wszystkie rozszerzenia znaczników w języku XAML używają znaków `{` i `}` w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut.</span><span class="sxs-lookup"><span data-stu-id="5de7c-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="5de7c-151">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="5de7c-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5de7c-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5de7c-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="5de7c-153">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="5de7c-153">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="5de7c-154">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="5de7c-154">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="5de7c-155">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="5de7c-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="5de7c-156">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="5de7c-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="5de7c-157">Powiązanie deklaracji — omówienie</span><span class="sxs-lookup"><span data-stu-id="5de7c-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="5de7c-158">x:Type, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="5de7c-158">x:Type Markup Extension</span></span>](../../xaml-services/x-type-markup-extension.md)
