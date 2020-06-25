---
title: Tworzenie szablonu w WPF — .NET Desktop
description: Dowiedz się, jak utworzyć szablon formantu i odwołać się do niego w Windows Presentation Foundation i .NET Core.
author: adegeo
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
ms.openlocfilehash: c372659676b450cde789c96e45c7ec5de2aea194
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325722"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="7a4e0-103">Tworzenie szablonu dla kontrolki</span><span class="sxs-lookup"><span data-stu-id="7a4e0-103">Create a template for a control</span></span>

<span data-ttu-id="7a4e0-104">Za pomocą Windows Presentation Foundation (WPF) można dostosować strukturę i zachowanie istniejącej kontrolki przy użyciu własnego szablonu wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="7a4e0-105">Szablony mogą być stosowane globalnie do aplikacji, okien i stron lub bezpośrednio do kontrolek.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="7a4e0-106">Większość scenariuszy, które wymagają utworzenia nowej kontrolki, może być objęta tworzeniem nowego szablonu dla istniejącej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="7a4e0-107">W tym artykule opisano tworzenie nowej <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="7a4e0-108">Kiedy należy utworzyć ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7a4e0-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="7a4e0-109">Kontrolki mają wiele właściwości, takich jak <xref:System.Windows.Controls.Border.Background%2A> , <xref:System.Windows.Controls.Control.Foreground%2A> , i <xref:System.Windows.Controls.Control.FontFamily%2A> .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="7a4e0-110">Te właściwości kontrolują różne aspekty wyglądu kontrolki, ale zmiany, które można wprowadzić, ustawiając te właściwości, są ograniczone.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="7a4e0-111">Na przykład możesz ustawić <xref:System.Windows.Controls.Control.Foreground%2A> Właściwość na niebieską i <xref:System.Windows.Controls.Control.FontStyle%2A> kursywę w <xref:System.Windows.Controls.CheckBox> .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="7a4e0-112">Jeśli chcesz dostosować wygląd kontrolki poza tym, co ustawienie innych właściwości kontrolki może zrobić, Utwórz <xref:System.Windows.Controls.ControlTemplate> .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="7a4e0-113">W większości interfejsów użytkownika przycisk ma ten sam wygląd ogólny: prostokąt z tekstem.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="7a4e0-114">Jeśli chcesz utworzyć przycisk zaokrąglony, można utworzyć nową kontrolkę, która dziedziczy po przycisku lub ponownie tworzy funkcję przycisku.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="7a4e0-115">Ponadto Nowa kontrolka użytkownika zapewni cykliczną wizualizację.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="7a4e0-116">Można uniknąć tworzenia nowych kontrolek przez dostosowanie układu wizualizacji istniejącej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="7a4e0-117">Za pomocą przycisku zaokrąglonego utworzysz <xref:System.Windows.Controls.ControlTemplate> z żądanym układem wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="7a4e0-118">Z drugiej strony, jeśli potrzebujesz kontrolki z nową funkcją, różnymi właściwościami i nowymi ustawieniami, utworzysz nowy <xref:System.Windows.Controls.UserControl> .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7a4e0-119">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7a4e0-119">Prerequisites</span></span>

<span data-ttu-id="7a4e0-120">Utwórz nową aplikację WPF i w *MainWindow. XAML* (lub innym wybranym oknie) ustaw następujące właściwości dla **\<Window>** elementu:</span><span class="sxs-lookup"><span data-stu-id="7a4e0-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

<span data-ttu-id="7a4e0-121">Ustaw zawartość **\<Window>** elementu na następujący kod XAML:</span><span class="sxs-lookup"><span data-stu-id="7a4e0-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="7a4e0-122">Na końcu plik *MainWindow. XAML* powinien wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="7a4e0-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="7a4e0-123">Jeśli aplikacja zostanie uruchomiona, wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="7a4e0-123">If you run the application, it looks like the following:</span></span>

![Okno WPF z dwoma niestylowymi przyciskami](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="7a4e0-125">Utwórz ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7a4e0-125">Create a ControlTemplate</span></span>

<span data-ttu-id="7a4e0-126">Najbardziej typowym sposobem deklarowania elementu <xref:System.Windows.Controls.ControlTemplate> jest jako zasobu w `Resources` sekcji w pliku XAML.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="7a4e0-127">Ponieważ szablony są zasobami, przestrzegają one tych samych reguł określania zakresu, które mają zastosowanie do wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="7a4e0-128">Umieść po prostu, gdzie deklarujesz szablon, ma wpływ na miejsce, w którym można zastosować szablon.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="7a4e0-129">Na przykład, Jeśli zadeklarujesz szablon w głównym elemencie pliku XAML definicji aplikacji, szablon może być używany w dowolnym miejscu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="7a4e0-130">Jeśli zdefiniujesz szablon w oknie, tylko kontrolki w tym oknie mogą używać szablonu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="7a4e0-131">Aby rozpocząć od, Dodaj `Window.Resources` element do pliku *MainWindow. XAML* :</span><span class="sxs-lookup"><span data-stu-id="7a4e0-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="7a4e0-132">Utwórz nowy **\<ControlTemplate>** z zestawem następujących właściwości:</span><span class="sxs-lookup"><span data-stu-id="7a4e0-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="7a4e0-133">**x:Key**</span><span class="sxs-lookup"><span data-stu-id="7a4e0-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="7a4e0-134">Ten szablon kontrolki będzie prosty:</span><span class="sxs-lookup"><span data-stu-id="7a4e0-134">This control template will be simple:</span></span>

- <span data-ttu-id="7a4e0-135">element główny formantu, a<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="7a4e0-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="7a4e0-136"><xref:System.Windows.Shapes.Ellipse>Aby narysować zaokrąglony wygląd przycisku</span><span class="sxs-lookup"><span data-stu-id="7a4e0-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="7a4e0-137">a, <xref:System.Windows.Controls.ContentPresenter> Aby wyświetlić zawartość przycisku określonego przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="7a4e0-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="7a4e0-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="7a4e0-138">TemplateBinding</span></span>

<span data-ttu-id="7a4e0-139">Podczas tworzenia nowego programu <xref:System.Windows.Controls.ControlTemplate> nadal można użyć właściwości publicznych do zmiany wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="7a4e0-140">Rozszerzenie " [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) " tworzy powiązanie właściwości elementu, który znajduje się w <xref:System.Windows.Controls.ControlTemplate> Właściwości publicznej zdefiniowanej przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="7a4e0-141">W przypadku użycia [szablonubinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)należy włączyć właściwości kontrolki, aby działały jako parametry szablonu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="7a4e0-142">Oznacza to, że po ustawieniu właściwości kontrolki ta wartość jest przenoszona do elementu, który ma element [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="7a4e0-143">Elipsa</span><span class="sxs-lookup"><span data-stu-id="7a4e0-143">Ellipse</span></span>

<span data-ttu-id="7a4e0-144">Zauważ, że **:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** właściwości i **\<Ellipse>** elementu są powiązane z kontrolką <xref:System.Windows.Controls.Control.Foreground> i <xref:System.Windows.Controls.Control.Background> właściwościami.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="7a4e0-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="7a4e0-145">ContentPresenter</span></span>

<span data-ttu-id="7a4e0-146">[\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter)Element zostanie również dodany do szablonu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="7a4e0-147">Ponieważ ten szablon jest przeznaczony dla przycisku, weź pod uwagę, że przycisk dziedziczy z <xref:System.Windows.Controls.ContentControl> .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="7a4e0-148">Przycisk przedstawia zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-148">The button presents the content of the element.</span></span> <span data-ttu-id="7a4e0-149">Można ustawić dowolne elementy wewnątrz przycisku, np. zwykły tekst, lub nawet inną kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="7a4e0-150">Oba z poniższych elementów są prawidłowymi przyciskami:</span><span class="sxs-lookup"><span data-stu-id="7a4e0-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="7a4e0-151">W obu powyższych przykładach tekst i pole wyboru są ustawiane jako właściwość [Button. Content](xref:System.Windows.Controls.ContentControl.Content) .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="7a4e0-152">Niezależnie od tego, co jest ustawione jako zawartość może być prezentowane za pomocą **\<ContentPresenter>** , co jest szablonem.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="7a4e0-153">Jeśli <xref:System.Windows.Controls.ControlTemplate> zostanie zastosowany do <xref:System.Windows.Controls.ContentControl> typu, takiego jak `Button` , <xref:System.Windows.Controls.ContentPresenter> jest wyszukiwany w drzewie elementów.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="7a4e0-154">Jeśli `ContentPresenter` zostanie znaleziony, szablon automatycznie wiąże właściwość kontrolki <xref:System.Windows.Controls.ContentControl.Content> z `ContentPresenter` .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="7a4e0-155">Korzystanie z szablonu</span><span class="sxs-lookup"><span data-stu-id="7a4e0-155">Use the template</span></span>

<span data-ttu-id="7a4e0-156">Znajdź przyciski, które zostały zadeklarowane na początku tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="7a4e0-157">Ustaw właściwość drugiego przycisku <xref:System.Windows.Controls.Control.Template> na `roundbutton` zasób:</span><span class="sxs-lookup"><span data-stu-id="7a4e0-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="7a4e0-158">Jeśli uruchomisz projekt i przyjrzyjsz się wynikowi, zobaczysz, że przycisk ma zaokrąglone tło.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![Okno WPF z jednym szablonem przycisku owalne](media/create-apply-template/styled-button.png)

<span data-ttu-id="7a4e0-160">Być może zauważono, że przycisk nie jest okrąg, ale jest skośny.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="7a4e0-161">Ze względu na sposób **\<Ellipse>** działania elementu, zawsze rozszerza się, aby wypełnić dostępne miejsce.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="7a4e0-162">Zmień okrąg, zmieniając **:::no-loc text="width":::** wartości przycisku i **:::no-loc text="height":::** właściwości na tę samą wartość:</span><span class="sxs-lookup"><span data-stu-id="7a4e0-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Okno WPF z jednym cyklicznym przyciskiem szablonu](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="7a4e0-164">Dodawanie wyzwalacza</span><span class="sxs-lookup"><span data-stu-id="7a4e0-164">Add a Trigger</span></span>

<span data-ttu-id="7a4e0-165">Mimo że przycisk z zastosowanym szablonem wygląda inaczej, zachowuje się tak samo jak każdy inny przycisk.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="7a4e0-166">Jeśli naciśniesz przycisk, zdarzenie zostanie wyzwolone <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="7a4e0-167">Można jednak zauważyć, że po przesunięciu wskaźnika myszy nad przycisk, wizualizacje przycisku nie są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="7a4e0-168">Te interakcje wizualne są definiowane przez szablon.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="7a4e0-169">Przy użyciu dynamicznych zdarzeń i systemów właściwości, które zapewnia WPF, można obejrzeć określoną właściwość dla wartości, a następnie w razie potrzeby ponownie styl szablonu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="7a4e0-170">W tym przykładzie zobaczysz <xref:System.Windows.UIElement.IsMouseOver> Właściwość przycisku.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="7a4e0-171">Gdy wskaźnik myszy znajduje się nad kontrolką, styl **\<Ellipse>** z nowym kolorem.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="7a4e0-172">Ten typ wyzwalacza jest znany jako *PropertyTrigger*.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="7a4e0-173">Aby to działało, należy dodać nazwę do elementu, do którego można się **\<Ellipse>** odwołać.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="7a4e0-174">Nadaj jej nazwę **backgroundelement**.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="7a4e0-175">Następnie Dodaj nową <xref:System.Windows.Trigger> do kolekcji [ControlTemplate. triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="7a4e0-176">Wyzwalacz będzie obserwować `IsMouseOver` zdarzenie dla wartości `true` .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="7a4e0-177">Następnie Dodaj do elementu, **\<Setter>** **\<Trigger>** który zmienia właściwość **Fill** elementu **\<Ellipse>** na nowy kolor.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="7a4e0-178">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-178">Run the project.</span></span> <span data-ttu-id="7a4e0-179">Zauważ, że po przesunięciu wskaźnika myszy nad przycisk, kolorem **\<Ellipse>** zmian.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![wskaźnik myszy jest przesuwany nad przyciskiem WPF, aby zmienić kolor wypełnienia](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="7a4e0-181">Użyj stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="7a4e0-181">Use a VisualState</span></span>

<span data-ttu-id="7a4e0-182">Stany wizualne są definiowane i wyzwalane przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="7a4e0-183">Na przykład, gdy wskaźnik myszy zostanie przesunięty nad formantem, `CommonStates.MouseOver` stan zostanie wyzwolony.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="7a4e0-184">Można animować zmiany właściwości w zależności od bieżącego stanu formantu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="7a4e0-185">W poprzedniej sekcji, użyto **\<PropertyTrigger>** do zmiany pierwszego planu przycisku do `AliceBlue` momentu, gdy `IsMouseOver` Właściwość była `true` .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="7a4e0-186">Zamiast tego należy utworzyć stan wizualizacji, który Animuj zmianę tego koloru, zapewniając bezproblemowe przejście.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="7a4e0-187">Aby uzyskać więcej informacji na temat *VisualStates*, zobacz [Style i szablony w WPF](../fundamentals/styles-templates-overview.md#visual-states).</span><span class="sxs-lookup"><span data-stu-id="7a4e0-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="7a4e0-188">Aby skonwertować **\<PropertyTrigger>** do animowanego stanu wizualnego, najpierw usuń **\<ControlTemplate.Triggers>** element z szablonu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="7a4e0-189">Następnie w **\<Grid>** katalogu głównym szablonu kontrolki Dodaj **\<VisualStateManager.VisualStateGroups>** element z **\<VisualStateGroup>** dla elementu `CommonStates` .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="7a4e0-190">Zdefiniuj dwa stany `Normal` i `MouseOver` .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="7a4e0-191">Wszelkie animacje zdefiniowane w elemencie **\<VisualState>** są stosowane w momencie wyzwolenia tego stanu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="7a4e0-192">Utwórz animacje dla każdego stanu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-192">Create animations for each state.</span></span> <span data-ttu-id="7a4e0-193">Animacje są umieszczane wewnątrz **\<Storyboard>** elementu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="7a4e0-194">Aby uzyskać więcej informacji na temat scenorysów, zobacz [Omówienie scenorysów](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7a4e0-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="7a4e0-195">Normalne</span><span class="sxs-lookup"><span data-stu-id="7a4e0-195">Normal</span></span>

  <span data-ttu-id="7a4e0-196">Ten stan Animuj wypełnienie elipsy, przywracając go do `Background` koloru formantu.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="7a4e0-197">MouseOver</span><span class="sxs-lookup"><span data-stu-id="7a4e0-197">MouseOver</span></span>

  <span data-ttu-id="7a4e0-198">Ten stan pozwala animować kolor elipsy `Background` do nowego koloru: `Yellow` .</span><span class="sxs-lookup"><span data-stu-id="7a4e0-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="7a4e0-199">**\<ControlTemplate>** Powinien teraz wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="7a4e0-200">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-200">Run the project.</span></span> <span data-ttu-id="7a4e0-201">Należy zauważyć, że po przesunięciu wskaźnika myszy nad przycisk, kolorem **\<Ellipse>** animacji.</span><span class="sxs-lookup"><span data-stu-id="7a4e0-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![wskaźnik myszy jest przesuwany nad przyciskiem WPF, aby zmienić kolor wypełnienia](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="7a4e0-203">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7a4e0-203">Next steps</span></span>

- [<span data-ttu-id="7a4e0-204">Tworzenie stylu kontrolki w WPF</span><span class="sxs-lookup"><span data-stu-id="7a4e0-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="7a4e0-205">Style i szablony w WPF</span><span class="sxs-lookup"><span data-stu-id="7a4e0-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="7a4e0-206">Przegląd zasobów XAML</span><span class="sxs-lookup"><span data-stu-id="7a4e0-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
