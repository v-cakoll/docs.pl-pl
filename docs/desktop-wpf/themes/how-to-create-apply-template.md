---
title: Tworzenie szablonu w WPF - .NET Desktop
description: Dowiedz się, jak utworzyć i odwołać się do szablonu formantu w programie Windows Presentation Foundation i .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071249"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="dd683-103">Tworzenie szablonu formantu</span><span class="sxs-lookup"><span data-stu-id="dd683-103">Create a template for a control</span></span>

<span data-ttu-id="dd683-104">Za pomocą programu Windows Presentation Foundation (WPF) można dostosować strukturę wizualną i zachowanie istniejącego formantu za pomocą własnego szablonu wielokrotnegoużycia.</span><span class="sxs-lookup"><span data-stu-id="dd683-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="dd683-105">Szablony mogą być stosowane globalnie do aplikacji, okien i stron lub bezpośrednio do formantów.</span><span class="sxs-lookup"><span data-stu-id="dd683-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="dd683-106">Większość scenariuszy, które wymagają utworzenia nowego formantu mogą być objęte zamiast tworzenia nowego szablonu dla istniejącego formantu.</span><span class="sxs-lookup"><span data-stu-id="dd683-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="dd683-107">W tym artykule zapoznajesz się <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.Button> tworzeniem nowego formantu.</span><span class="sxs-lookup"><span data-stu-id="dd683-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="dd683-108">Kiedy utworzyć płytę controltemplate</span><span class="sxs-lookup"><span data-stu-id="dd683-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="dd683-109">Formanty mają wiele <xref:System.Windows.Controls.Border.Background%2A>właściwości, takich jak , <xref:System.Windows.Controls.Control.Foreground%2A>i <xref:System.Windows.Controls.Control.FontFamily%2A>.</span><span class="sxs-lookup"><span data-stu-id="dd683-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="dd683-110">Właściwości te kontrolują różne aspekty wyglądu formantu, ale zmiany, które można wprowadzić, ustawiając te właściwości, są ograniczone.</span><span class="sxs-lookup"><span data-stu-id="dd683-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="dd683-111">Na przykład można ustawić <xref:System.Windows.Controls.Control.Foreground%2A> właściwość <xref:System.Windows.Controls.Control.FontStyle%2A> na niebieską i <xref:System.Windows.Controls.CheckBox>kursywą na pliku .</span><span class="sxs-lookup"><span data-stu-id="dd683-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="dd683-112">Jeśli chcesz dostosować wygląd formantu poza to, co może zrobić ustawienie innych <xref:System.Windows.Controls.ControlTemplate>właściwości formantu, należy utworzyć program .</span><span class="sxs-lookup"><span data-stu-id="dd683-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="dd683-113">W większości interfejsów użytkownika przycisk ma ten sam ogólny wygląd: prostokąt z tekstem.</span><span class="sxs-lookup"><span data-stu-id="dd683-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="dd683-114">Jeśli chcesz utworzyć zaokrąglony przycisk, można utworzyć nowy formant, który dziedziczy z przycisku lub ponownie tworzy funkcjonalność przycisku.</span><span class="sxs-lookup"><span data-stu-id="dd683-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="dd683-115">Ponadto nowy formant użytkownika zapewni cykliczne wizualizacje.</span><span class="sxs-lookup"><span data-stu-id="dd683-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="dd683-116">Można uniknąć tworzenia nowych formantów, dostosowując układ wizualny istniejącego formantu.</span><span class="sxs-lookup"><span data-stu-id="dd683-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="dd683-117">Za pomocą zaokrąglonego przycisku tworzy się z żądanym układem <xref:System.Windows.Controls.ControlTemplate> wizualnym.</span><span class="sxs-lookup"><span data-stu-id="dd683-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="dd683-118">Z drugiej strony, jeśli potrzebujesz formantu z nową funkcjonalnością, różnymi właściwościami <xref:System.Windows.Controls.UserControl>i nowymi ustawieniami, utwórz nowy program .</span><span class="sxs-lookup"><span data-stu-id="dd683-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd683-119">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="dd683-119">Prerequisites</span></span>

<span data-ttu-id="dd683-120">Utwórz nową aplikację WPF i w *mainwindow.xaml* (lub innym oknie do wyboru) ustaw następujące właściwości w \*\* \<oknie>\*\* element:</span><span class="sxs-lookup"><span data-stu-id="dd683-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

<span data-ttu-id="dd683-121">Ustaw zawartość elementu \*\* \<Window>\*\* na następujący kod XAML:</span><span class="sxs-lookup"><span data-stu-id="dd683-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="dd683-122">Na końcu plik *MainWindow.xaml* powinien wyglądać podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="dd683-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="dd683-123">Po uruchomieniu aplikacji wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="dd683-123">If you run the application, it looks like the following:</span></span>

![Okno WPF z dwoma niestyliowanymi przyciskami](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="dd683-125">Tworzenie panelu sterowania</span><span class="sxs-lookup"><span data-stu-id="dd683-125">Create a ControlTemplate</span></span>

<span data-ttu-id="dd683-126">Najczęstszym sposobem deklarowania <xref:System.Windows.Controls.ControlTemplate> a jest jako `Resources` zasób w sekcji w pliku XAML.</span><span class="sxs-lookup"><span data-stu-id="dd683-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="dd683-127">Ponieważ szablony są zasobami, są one zgodne z tymi samymi regułami zakresu, które mają zastosowanie do wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="dd683-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="dd683-128">Mówiąc prościej, jeśli zadeklarować szablon wpływa na to, gdzie szablon może być stosowany.</span><span class="sxs-lookup"><span data-stu-id="dd683-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="dd683-129">Na przykład jeśli deklarujesz szablon w elemencie głównym pliku XAML definicji aplikacji, szablon może być używany w dowolnym miejscu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd683-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="dd683-130">Jeśli szablon zostanie zdefiniowany w oknie, tylko formanty w tym oknie mogą używać szablonu.</span><span class="sxs-lookup"><span data-stu-id="dd683-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="dd683-131">Na początek dodaj `Window.Resources` element do pliku *MainWindow.xaml:*</span><span class="sxs-lookup"><span data-stu-id="dd683-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="dd683-132">Utwórz nową \*\* \<>ControlTemplate\*\* z następującymi właściwościami:</span><span class="sxs-lookup"><span data-stu-id="dd683-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="dd683-133">**x:Klucz**</span><span class="sxs-lookup"><span data-stu-id="dd683-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="dd683-134">Ten szablon formantu będzie prosty:</span><span class="sxs-lookup"><span data-stu-id="dd683-134">This control template will be simple:</span></span>

- <span data-ttu-id="dd683-135">element główny formantu,<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="dd683-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="dd683-136">a <xref:System.Windows.Shapes.Ellipse> narysować zaokrąglony wygląd przycisku</span><span class="sxs-lookup"><span data-stu-id="dd683-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="dd683-137">a, <xref:System.Windows.Controls.ContentPresenter> aby wyświetlić zawartość przycisku określoną przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="dd683-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="dd683-138">Powiązanie szablonów</span><span class="sxs-lookup"><span data-stu-id="dd683-138">TemplateBinding</span></span>

<span data-ttu-id="dd683-139">Podczas tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>, nadal można użyć właściwości publicznych, aby zmienić wygląd formantu.</span><span class="sxs-lookup"><span data-stu-id="dd683-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="dd683-140">Rozszerzenie znaczników [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) wiąże właściwość elementu, który <xref:System.Windows.Controls.ControlTemplate> znajduje się w właściwości publicznej, która jest zdefiniowana przez formant.</span><span class="sxs-lookup"><span data-stu-id="dd683-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="dd683-141">Korzystając z [funkcji TemplateBinding,](../../framework/wpf/advanced/templatebinding-markup-extension.md)można włączyć właściwości formantu, aby działać jako parametry szablonu.</span><span class="sxs-lookup"><span data-stu-id="dd683-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="dd683-142">Oznacza to, że gdy właściwość na formancie jest ustawiona, ta wartość jest przekazywana do elementu, który ma [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) na nim.</span><span class="sxs-lookup"><span data-stu-id="dd683-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="dd683-143">Elipsy</span><span class="sxs-lookup"><span data-stu-id="dd683-143">Ellipse</span></span>

<span data-ttu-id="dd683-144">Należy **:::no-loc text="Fill":::** zauważyć, **:::no-loc text="Stroke":::** że i właściwości \*\* \<elipsy>\*\* element są powiązane z <xref:System.Windows.Controls.Control.Foreground> <xref:System.Windows.Controls.Control.Background> formantu i właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd683-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="dd683-145">Contentpresenter</span><span class="sxs-lookup"><span data-stu-id="dd683-145">ContentPresenter</span></span>

<span data-ttu-id="dd683-146">Element [ \<>ContentPresenter](xref:System.Windows.Controls.ContentPresenter) jest również dodawany do szablonu.</span><span class="sxs-lookup"><span data-stu-id="dd683-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="dd683-147">Ponieważ ten szablon jest przeznaczony dla przycisku, należy <xref:System.Windows.Controls.ContentControl>wziąć pod uwagę, że przycisk dziedziczy z .</span><span class="sxs-lookup"><span data-stu-id="dd683-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="dd683-148">Przycisk przedstawia zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="dd683-148">The button presents the content of the element.</span></span> <span data-ttu-id="dd683-149">Możesz ustawić wszystko wewnątrz przycisku, takie jak zwykły tekst lub nawet inny formant.</span><span class="sxs-lookup"><span data-stu-id="dd683-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="dd683-150">Oba z poniższych przycisków są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="dd683-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="dd683-151">W obu poprzednich przykładach tekst i pole wyboru są ustawione jako [Właściwość Button.Content.](xref:System.Windows.Controls.ContentControl.Content)</span><span class="sxs-lookup"><span data-stu-id="dd683-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="dd683-152">Cokolwiek jest ustawione, ponieważ zawartość \*\* \< \*\*może być przedstawiona za pośrednictwem contentpreser>, czyli tego, co robi szablon.</span><span class="sxs-lookup"><span data-stu-id="dd683-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="dd683-153">Jeśli <xref:System.Windows.Controls.ControlTemplate> jest stosowany do <xref:System.Windows.Controls.ContentControl> typu, takich `Button`jak <xref:System.Windows.Controls.ContentPresenter> , a jest wyszukiwany w drzewie elementów.</span><span class="sxs-lookup"><span data-stu-id="dd683-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="dd683-154">Jeśli `ContentPresenter` zostanie znaleziony, szablon automatycznie wiąże <xref:System.Windows.Controls.ContentControl.Content> właściwość formantu z . `ContentPresenter`</span><span class="sxs-lookup"><span data-stu-id="dd683-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="dd683-155">Korzystanie z szablonu</span><span class="sxs-lookup"><span data-stu-id="dd683-155">Use the template</span></span>

<span data-ttu-id="dd683-156">Znajdź przyciski, które zostały zadeklarowane na początku tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="dd683-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="dd683-157">Ustaw <xref:System.Windows.Controls.Control.Template> właściwość drugiego przycisku `roundbutton` na zasób:</span><span class="sxs-lookup"><span data-stu-id="dd683-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="dd683-158">Jeśli uruchomisz projekt i spojrzysz na wynik, zobaczysz, że przycisk ma zaokrąglone tło.</span><span class="sxs-lookup"><span data-stu-id="dd683-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![Okno WPF z jednym szablonem owalny przycisk](media/create-apply-template/styled-button.png)

<span data-ttu-id="dd683-160">Być może zauważyłeś, że przycisk nie jest okrąg, ale jest pochylony.</span><span class="sxs-lookup"><span data-stu-id="dd683-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="dd683-161">Ze względu na sposób \*\* \<działania elementu>elipsy,\*\* zawsze rozszerza się, aby wypełnić dostępne miejsce.</span><span class="sxs-lookup"><span data-stu-id="dd683-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="dd683-162">Umundurowanie okręgu, zmieniając **:::no-loc text="width":::** przycisk **:::no-loc text="height":::** i właściwości na tę samą wartość:</span><span class="sxs-lookup"><span data-stu-id="dd683-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Okno WPF z jednym okrągłym przyciskiem szablonu](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="dd683-164">Dodawanie wyzwalacza</span><span class="sxs-lookup"><span data-stu-id="dd683-164">Add a Trigger</span></span>

<span data-ttu-id="dd683-165">Mimo że przycisk z zastosowanym szablonem wygląda inaczej, zachowuje się tak samo jak każdy inny przycisk.</span><span class="sxs-lookup"><span data-stu-id="dd683-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="dd683-166">Po naciśnięciu przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie zostanie podpalene.</span><span class="sxs-lookup"><span data-stu-id="dd683-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="dd683-167">Jednak być może zauważyłeś, że po przesunięciu wskaźnika myszy na przycisk wizualizacje przycisku nie zmieniają się.</span><span class="sxs-lookup"><span data-stu-id="dd683-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="dd683-168">Te interakcje wizualne są zdefiniowane przez szablon.</span><span class="sxs-lookup"><span data-stu-id="dd683-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="dd683-169">Za pomocą dynamicznych systemów zdarzeń i właściwości, które zapewnia WPF, można oglądać określonej właściwości dla wartości, a następnie restyle szablonu w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="dd683-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="dd683-170">W tym przykładzie będziesz obserwować właściwości <xref:System.Windows.UIElement.IsMouseOver> przycisku.</span><span class="sxs-lookup"><span data-stu-id="dd683-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="dd683-171">Gdy mysz jest nad formantem, styl \*\* \<Elipsy>\*\* z nowym kolorem.</span><span class="sxs-lookup"><span data-stu-id="dd683-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="dd683-172">Ten typ wyzwalacza jest znany jako *PropertyTrigger*.</span><span class="sxs-lookup"><span data-stu-id="dd683-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="dd683-173">Aby to zadziałało, musisz dodać nazwę do \*\* \<>elipsy,\*\* do której można się odwołać.</span><span class="sxs-lookup"><span data-stu-id="dd683-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="dd683-174">Nadaj mu nazwę **backgroundElement**.</span><span class="sxs-lookup"><span data-stu-id="dd683-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="dd683-175">Następnie dodaj nowy <xref:System.Windows.Trigger> do [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dd683-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="dd683-176">Wyzwalacz będzie `IsMouseOver` obserwował zdarzenie `true`dla wartości .</span><span class="sxs-lookup"><span data-stu-id="dd683-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="dd683-177">Następnie dodaj \*\* \<seter>\*\* do \*\* \<>wyzwalacza,\*\* który zmienia **Fill** właściwości \*\* \<elipsy>\*\* na nowy kolor.</span><span class="sxs-lookup"><span data-stu-id="dd683-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="dd683-178">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="dd683-178">Run the project.</span></span> <span data-ttu-id="dd683-179">Należy zauważyć, że podczas przesuwania myszy na przycisk, kolor \*\* \<elipsy>\*\* zmienia.</span><span class="sxs-lookup"><span data-stu-id="dd683-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![mysz przesuwa się nad przyciskiem WPF, aby zmienić kolor wypełnienia](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="dd683-181">Używanie funkcji VisualState</span><span class="sxs-lookup"><span data-stu-id="dd683-181">Use a VisualState</span></span>

<span data-ttu-id="dd683-182">Stany wizualne są definiowane i wyzwalane przez formant.</span><span class="sxs-lookup"><span data-stu-id="dd683-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="dd683-183">Na przykład, gdy mysz jest przenoszona `CommonStates.MouseOver` na górze formantu, stan jest wyzwalany.</span><span class="sxs-lookup"><span data-stu-id="dd683-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="dd683-184">Zmiany właściwości można animować na podstawie bieżącego stanu formantu.</span><span class="sxs-lookup"><span data-stu-id="dd683-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="dd683-185">W poprzedniej sekcji \*\* \<>PropertyTrigger\*\* został użyty do zmiany pierwszego planu `AliceBlue` przycisku `IsMouseOver` na `true`kiedy właściwość była .</span><span class="sxs-lookup"><span data-stu-id="dd683-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="dd683-186">Zamiast tego należy utworzyć stan wizualny, który animuje zmianę tego koloru, zapewniając płynne przejście.</span><span class="sxs-lookup"><span data-stu-id="dd683-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="dd683-187">Aby uzyskać więcej informacji na temat *VisualStates*, zobacz [Style i szablony w WPF](../fundamentals/styles-templates-overview.md#visual-states).</span><span class="sxs-lookup"><span data-stu-id="dd683-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="dd683-188">Aby przekonwertować \*\* \<>PropertyTrigger\*\* na animowany stan wizualny, najpierw usuń element \*\* \<ControlTemplate.Triggers>\*\* z szablonu.</span><span class="sxs-lookup"><span data-stu-id="dd683-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="dd683-189">Następnie w \*\* \<katalogu\*\* głównym>siatki szablonu formantu dodaj element \*\* \<VisualStateManager.VisualStateGroups>\*\* za pomocą>`CommonStates` \*\* \<VisualStateGroup\*\* dla .</span><span class="sxs-lookup"><span data-stu-id="dd683-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="dd683-190">Zdefiniuj dwa stany `Normal` i `MouseOver`.</span><span class="sxs-lookup"><span data-stu-id="dd683-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="dd683-191">Wszystkie animacje zdefiniowane w \*\* \<VisualState>\*\* są stosowane, gdy ten stan jest wyzwalany.</span><span class="sxs-lookup"><span data-stu-id="dd683-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="dd683-192">Tworzenie animacji dla każdego stanu.</span><span class="sxs-lookup"><span data-stu-id="dd683-192">Create animations for each state.</span></span> <span data-ttu-id="dd683-193">Animacje są umieszczane wewnątrz \*\* \<scenorysu>\*\* elementu.</span><span class="sxs-lookup"><span data-stu-id="dd683-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="dd683-194">Aby uzyskać więcej informacji na temat scenochło posmówek, zobacz [Omówienie scenoki .](../../framework/wpf/graphics-multimedia/storyboards-overview.md)</span><span class="sxs-lookup"><span data-stu-id="dd683-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="dd683-195">Normalne</span><span class="sxs-lookup"><span data-stu-id="dd683-195">Normal</span></span>

  <span data-ttu-id="dd683-196">Ten stan animuje wypełnienie elipsy, przywracając go `Background` do koloru formantu.</span><span class="sxs-lookup"><span data-stu-id="dd683-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="dd683-197">Mouseover</span><span class="sxs-lookup"><span data-stu-id="dd683-197">MouseOver</span></span>

  <span data-ttu-id="dd683-198">Ten stan animuje `Background` kolor elipsy do `Yellow`nowego koloru: .</span><span class="sxs-lookup"><span data-stu-id="dd683-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="dd683-199">\*\* \<>ControlTemplate\*\* powinien teraz wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="dd683-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="dd683-200">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="dd683-200">Run the project.</span></span> <span data-ttu-id="dd683-201">Należy zauważyć, że podczas przesuwania myszy na przycisk, kolor \*\* \<elipsy>\*\* animuje.</span><span class="sxs-lookup"><span data-stu-id="dd683-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![mysz przesuwa się nad przyciskiem WPF, aby zmienić kolor wypełnienia](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="dd683-203">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="dd683-203">Next steps</span></span>

- [<span data-ttu-id="dd683-204">Tworzenie stylu formantu w WPF</span><span class="sxs-lookup"><span data-stu-id="dd683-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="dd683-205">Style i szablony w wytęzianych w filtrze WPF</span><span class="sxs-lookup"><span data-stu-id="dd683-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="dd683-206">Omówienie zasobów XAML</span><span class="sxs-lookup"><span data-stu-id="dd683-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
