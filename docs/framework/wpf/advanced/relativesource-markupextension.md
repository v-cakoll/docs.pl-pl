---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 47117d684a981f31e22cf513fc78e1e2dda73f8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141265"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="52cb8-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="52cb8-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="52cb8-103">Określa właściwości źródła <xref:System.Windows.Data.RelativeSource> powiązania, które ma być używane w [rozszerzeniu Binding Markup](binding-markup-extension.md)lub podczas ustawiania <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwości <xref:System.Windows.Data.Binding> elementu ustanowionego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="52cb8-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="52cb8-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="52cb8-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="52cb8-105">Użycie atrybutu języka XAML (zagnieżdżonego w rozszerzeniu Binding)</span><span class="sxs-lookup"><span data-stu-id="52cb8-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="52cb8-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="52cb8-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="52cb8-107">— lub —</span><span class="sxs-lookup"><span data-stu-id="52cb8-107">-or-</span></span>

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

## <a name="xaml-values"></a><span data-ttu-id="52cb8-108">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="52cb8-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="52cb8-109">Jeden z poniższych programów:</span><span class="sxs-lookup"><span data-stu-id="52cb8-109">One of the following:</span></span><br /><br /> <span data-ttu-id="52cb8-110">-Token `Self`ciągu; odnosi się do <xref:System.Windows.Data.RelativeSource> elementu as utworzonego z <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością ustawioną na <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="52cb8-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="52cb8-111">-Token `TemplatedParent`ciągu; odnosi się do <xref:System.Windows.Data.RelativeSource> elementu as utworzonego z <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością ustawioną na <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="52cb8-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="52cb8-112">-Token `PreviousData`ciągu; odnosi się do <xref:System.Windows.Data.RelativeSource> elementu as utworzonego z <xref:System.Windows.Data.RelativeSource.Mode%2A> właściwością ustawioną na <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="52cb8-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="52cb8-113">-Zobacz poniżej, aby uzyskać `FindAncestor` informacje o trybie.</span><span class="sxs-lookup"><span data-stu-id="52cb8-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="52cb8-114">Token `FindAncestor`ciągu.</span><span class="sxs-lookup"><span data-stu-id="52cb8-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="52cb8-115">Użycie tego tokenu spowoduje przejście do trybu, `RelativeSource` w którym określa typ elementu nadrzędnego i opcjonalnie poziomu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="52cb8-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="52cb8-116">Odnosi się to <xref:System.Windows.Data.RelativeSource> tak, jakby został utworzony <xref:System.Windows.Data.RelativeSource.Mode%2A> z właściwością <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>ustawioną na.</span><span class="sxs-lookup"><span data-stu-id="52cb8-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="52cb8-117">Wymagane dla `FindAncestor` trybu.</span><span class="sxs-lookup"><span data-stu-id="52cb8-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="52cb8-118">Nazwa typu, który wypełnia <xref:System.Windows.Data.RelativeSource.AncestorType%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="52cb8-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="52cb8-119">Opcjonalne dla `FindAncestor` trybu.</span><span class="sxs-lookup"><span data-stu-id="52cb8-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="52cb8-120">Poziom elementu nadrzędnego (patrząc w kierunku nadrzędności w drzewie logicznym).</span><span class="sxs-lookup"><span data-stu-id="52cb8-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="52cb8-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52cb8-121">Remarks</span></span>

<span data-ttu-id="52cb8-122">`{RelativeSource TemplatedParent}`Użycie powiązań jest kluczową techniką, która eliminuje większą koncepcję rozdzielania interfejsu użytkownika kontrolki i logiki kontrolki.</span><span class="sxs-lookup"><span data-stu-id="52cb8-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="52cb8-123">Umożliwia tworzenie powiązań z wewnątrz definicji szablonu do elementu nadrzędnego używającego szablonu (tzn. do wystąpienia obiektu, do którego w czasie wykonywania szablon jest stosowany).</span><span class="sxs-lookup"><span data-stu-id="52cb8-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="52cb8-124">W takim przypadku rozszerzenie " [TemplateBinding Markup](templatebinding-markup-extension.md) " jest w istocie skrót dla następującego wyrażenia powiązania: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="52cb8-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="52cb8-125">`TemplateBinding`lub `{RelativeSource TemplatedParent}` użycia są odpowiednie tylko w kodzie XAML, który definiuje szablon.</span><span class="sxs-lookup"><span data-stu-id="52cb8-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="52cb8-126">Aby uzyskać więcej informacji, zobacz [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="52cb8-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="52cb8-127">`{RelativeSource FindAncestor}`jest używany głównie w szablonach kontroli lub przewidywalnym samoobsługowym kompozycjom interfejsu użytkownika, w przypadkach, gdy kontrolka zawsze powinna znajdować się w drzewie wizualnym określonego typu elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="52cb8-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="52cb8-128">Na przykład elementy kontrolki elementów mogą używać `FindAncestor` użycia do powiązania z właściwościami elementów nadrzędnych elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="52cb8-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="52cb8-129">Lub elementy, które są częścią kompozycji formantu w szablonie, mogą używać `FindAncestor` powiązań z elementami nadrzędnymi w tej samej strukturze kompozycji.</span><span class="sxs-lookup"><span data-stu-id="52cb8-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="52cb8-130">W składni elementu obiektu dla `FindAncestor` trybu pokazanego w sekcjach SKŁADNI języka XAML, składnia drugiego elementu obiektu jest używana do `FindAncestor` trybu.</span><span class="sxs-lookup"><span data-stu-id="52cb8-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="52cb8-131">`FindAncestor`tryb wymaga <xref:System.Windows.Data.RelativeSource.AncestorType%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="52cb8-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="52cb8-132">Należy ustawić <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako atrybut, używając [x:Type — znacznika](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) odwołania do typu elementu nadrzędnego, który ma zostać wyszukany.</span><span class="sxs-lookup"><span data-stu-id="52cb8-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="52cb8-133">Wartość <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jest używana, gdy żądanie powiązania jest przetwarzane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="52cb8-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="52cb8-134">W `FindAncestor` przypadku trybu Właściwość <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> opcjonalna może pomóc w odróżnieniu wyszukiwania nadrzędnego w przypadkach, gdy istnieje prawdopodobnie więcej niż jeden element nadrzędny tego typu istniejący w drzewie elementów.</span><span class="sxs-lookup"><span data-stu-id="52cb8-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="52cb8-135">Aby uzyskać więcej informacji na temat używania `FindAncestor` trybu, zobacz. <xref:System.Windows.Data.RelativeSource></span><span class="sxs-lookup"><span data-stu-id="52cb8-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="52cb8-136">`{RelativeSource Self}`jest przydatne w scenariuszach, w których jedna Właściwość wystąpienia powinna zależeć od wartości innej właściwości tego samego wystąpienia, a żadna nie ogólna relacja między właściwościami zależności (na przykład przymusu) istnieje już między tymi dwiema właściwościami.</span><span class="sxs-lookup"><span data-stu-id="52cb8-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="52cb8-137">Chociaż jest to rzadki, że dwie właściwości istnieją w obiekcie, tak że wartości są identyczne (i są identyczne), można również zastosować `Converter` parametr do powiązania, które ma `{RelativeSource Self}`, i użyć konwertera do konwersji między typami źródłowymi i docelowymi.</span><span class="sxs-lookup"><span data-stu-id="52cb8-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="52cb8-138">Inny scenariusz dla `{RelativeSource Self}` jest jako część elementu <xref:System.Windows.MultiDataTrigger>.</span><span class="sxs-lookup"><span data-stu-id="52cb8-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="52cb8-139">Na przykład poniższy kod XAML definiuje <xref:System.Windows.Shapes.Rectangle> element <xref:System.Windows.FrameworkElement.Width%2A>, który nie ma znaczenia wartości, <xref:System.Windows.Shapes.Rectangle> jest zawsze kwadratem:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="52cb8-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="52cb8-140">`{RelativeSource PreviousData}`jest przydatne w szablonach danych lub w przypadkach, gdy powiązania używają kolekcji jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="52cb8-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="52cb8-141">Możesz użyć `{RelativeSource PreviousData}` , aby wyróżnić relacje między sąsiednimi elementami danych w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="52cb8-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="52cb8-142">Pokrewna Technika polega na ustanowieniu <xref:System.Windows.Data.MultiBinding> między bieżącymi i poprzednimi elementami w źródle danych i wykorzystaniu konwertera dla tego powiązania, aby określić różnicę między dwoma elementami i ich właściwościami.</span><span class="sxs-lookup"><span data-stu-id="52cb8-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="52cb8-143">W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> w szablonie Items wyświetla bieżącą liczbę.</span><span class="sxs-lookup"><span data-stu-id="52cb8-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="52cb8-144">Drugie <xref:System.Windows.Controls.TextBlock> powiązanie jest <xref:System.Windows.Data.MultiBinding> , które w sposób nominalny ma dwa <xref:System.Windows.Data.Binding> składniki: bieżący rekord i powiązanie, które w sposób celowy używa poprzedniego rekordu danych przy użyciu. `{RelativeSource PreviousData}`</span><span class="sxs-lookup"><span data-stu-id="52cb8-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="52cb8-145">Następnie konwerter <xref:System.Windows.Data.MultiBinding> oblicza różnicę i zwraca go do powiązania.</span><span class="sxs-lookup"><span data-stu-id="52cb8-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

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
</ListBox>
```

<span data-ttu-id="52cb8-146">Opisywanie powiązania danych jako koncepcji nie jest tutaj omówione, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="52cb8-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="52cb8-147">W implementacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesora XAML obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.Data.RelativeSource> klasę.</span><span class="sxs-lookup"><span data-stu-id="52cb8-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="52cb8-148">`RelativeSource`jest rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="52cb8-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="52cb8-149">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="52cb8-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="52cb8-150">Wszystkie rozszerzenia znaczników w języku XAML używają `{` znaków `}` i w ich składni atrybutów, która jest konwencją, za pomocą której procesor XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut.</span><span class="sxs-lookup"><span data-stu-id="52cb8-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="52cb8-151">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="52cb8-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="52cb8-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52cb8-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="52cb8-153">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="52cb8-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="52cb8-154">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="52cb8-154">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="52cb8-155">Rozszerzenia znacznikowania i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="52cb8-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="52cb8-156">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="52cb8-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="52cb8-157">Przegląd Wiązanie deklaracji</span><span class="sxs-lookup"><span data-stu-id="52cb8-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="52cb8-158">x:Type — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="52cb8-158">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
