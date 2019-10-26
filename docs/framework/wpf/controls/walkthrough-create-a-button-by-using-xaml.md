---
title: 'Wskazówki: Tworzenie przycisku przy użyciu XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: a0792beca358de52a24bd9bb0dd48a20c175f8ff
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920183"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="eabdf-102">Wskazówki: Tworzenie przycisku przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="eabdf-102">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="eabdf-103">Celem tego instruktażu jest nauczenie się, jak utworzyć animowany przycisk do użycia w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="eabdf-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="eabdf-104">W tym instruktażu zastosowano style i szablon w celu utworzenia niestandardowego zasobu przycisku, który umożliwia ponowne użycie kodu i rozdzielenie logiki przycisku z deklaracji przycisku.</span><span class="sxs-lookup"><span data-stu-id="eabdf-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="eabdf-105">Ten Instruktaż jest zapisywana w całości w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eabdf-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eabdf-106">Ten przewodnik przeprowadzi Cię przez kroki tworzenia aplikacji przez wpisanie lub skopiowanie i wklejenie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eabdf-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="eabdf-107">Jeśli wolisz dowiedzieć się, jak używać projektanta do tworzenia tej samej aplikacji, zobacz [Tworzenie przycisku przy użyciu programu Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="eabdf-107">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="eabdf-108">Na poniższej ilustracji przedstawiono gotowe przyciski.</span><span class="sxs-lookup"><span data-stu-id="eabdf-108">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="eabdf-109">![Przyciski niestandardowe, które zostały utworzone przy użyciu języka XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="eabdf-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="eabdf-110">Utwórz podstawowe przyciski</span><span class="sxs-lookup"><span data-stu-id="eabdf-110">Create Basic Buttons</span></span>

<span data-ttu-id="eabdf-111">Zacznijmy od utworzenia nowego projektu i dodania do okna kilku przycisków.</span><span class="sxs-lookup"><span data-stu-id="eabdf-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="eabdf-112">Aby utworzyć nowy projekt WPF i dodać przyciski do okna</span><span class="sxs-lookup"><span data-stu-id="eabdf-112">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="eabdf-113">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eabdf-113">Start Visual Studio.</span></span>

2. <span data-ttu-id="eabdf-114">**Utwórz nowy projekt WPF:** W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="eabdf-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="eabdf-115">Znajdź szablon **aplikacji systemu Windows (WPF)** i Nadaj projektowi nazwę "AnimatedButton".</span><span class="sxs-lookup"><span data-stu-id="eabdf-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="eabdf-116">Spowoduje to utworzenie szkieletu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eabdf-116">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="eabdf-117">**Dodaj podstawowe przyciski domyślne:** Wszystkie pliki potrzebne do tego przewodnika są udostępniane przez szablon.</span><span class="sxs-lookup"><span data-stu-id="eabdf-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="eabdf-118">Otwórz plik window1. XAML, klikając go dwukrotnie w Eksplorator rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="eabdf-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="eabdf-119">Domyślnie w window1. XAML znajduje się element <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="eabdf-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="eabdf-120">Usuń <xref:System.Windows.Controls.Grid> element i Dodaj kilka przycisków do strony [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], wpisując lub kopiując i wklejając następujący wyróżniony kod do window1. XAML:</span><span class="sxs-lookup"><span data-stu-id="eabdf-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

    ```xaml
    <Window x:Class="AnimatedButton.Window1"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="AnimatedButton" Height="300" Width="300"
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>
    </Window>
    ```

     <span data-ttu-id="eabdf-121">Naciśnij klawisz F5, aby uruchomić aplikację. powinien pojawić się zestaw przycisków, które wyglądają jak na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="eabdf-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="eabdf-122">![Trzy podstawowe przyciski](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="eabdf-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="eabdf-123">Teraz, gdy utworzono podstawowe przyciski, zakończysz pracę w pliku window1. XAML.</span><span class="sxs-lookup"><span data-stu-id="eabdf-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="eabdf-124">Pozostała część przewodnika koncentruje się na pliku App. XAML, definiowaniu stylów i szablonie przycisków.</span><span class="sxs-lookup"><span data-stu-id="eabdf-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="eabdf-125">Ustaw właściwości podstawowe</span><span class="sxs-lookup"><span data-stu-id="eabdf-125">Set Basic Properties</span></span>

<span data-ttu-id="eabdf-126">Następnie Skonfigurujmy niektóre właściwości na tych przyciskach, aby kontrolować wygląd i układ przycisku.</span><span class="sxs-lookup"><span data-stu-id="eabdf-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="eabdf-127">Zamiast ustawiania właściwości na przyciskach indywidualnie, użyjesz zasobów do definiowania właściwości przycisku dla całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eabdf-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="eabdf-128">Zasoby aplikacji są koncepcyjnie podobne do zewnętrznych kaskadowe arkusze stylów (CSS) dla stron sieci Web; jednak zasoby są znacznie bardziej wydajne niż kaskadowe arkusze stylów (CSS), jak widać na końcu tego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="eabdf-128">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="eabdf-129">Aby dowiedzieć się więcej o zasobach, zobacz [zasoby XAML](../advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="eabdf-129">To learn more about resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="eabdf-130">Aby użyć stylów do ustawiania podstawowych właściwości na przyciskach</span><span class="sxs-lookup"><span data-stu-id="eabdf-130">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="eabdf-131">**Zdefiniuj blok Application. Resources:** Otwórz plik App. XAML i Dodaj następujące wyróżnione znaczniki, jeśli jeszcze tego nie zrobiono:</span><span class="sxs-lookup"><span data-stu-id="eabdf-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

    ```xaml
    <Application x:Class="AnimatedButton.App"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      StartupUri="Window1.xaml"
      >
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>
    </Application>
    ```

     <span data-ttu-id="eabdf-132">Zakres zasobów jest określany na podstawie tego, gdzie definiujesz zasób.</span><span class="sxs-lookup"><span data-stu-id="eabdf-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="eabdf-133">Zdefiniowanie zasobów w `Application.Resources` w pliku App. XAML umożliwia użycie zasobu z dowolnego miejsca w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eabdf-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="eabdf-134">Aby dowiedzieć się więcej o definiowaniu zakresu zasobów, zobacz [zasoby XAML](../advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="eabdf-134">To learn more about defining the scope of your resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>

2. <span data-ttu-id="eabdf-135">**Utwórz styl i Zdefiniuj dla niego podstawowe wartości właściwości:** Dodaj następujący znacznik do bloku `Application.Resources`.</span><span class="sxs-lookup"><span data-stu-id="eabdf-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="eabdf-136">Ten znacznik tworzy <xref:System.Windows.Style>, które mają zastosowanie do wszystkich przycisków w aplikacji, ustawiając <xref:System.Windows.FrameworkElement.Width%2A> przycisków na 90 i <xref:System.Windows.FrameworkElement.Margin%2A> do 10:</span><span class="sxs-lookup"><span data-stu-id="eabdf-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="eabdf-137">Właściwość <xref:System.Windows.Style.TargetType%2A> określa, że styl dotyczy wszystkich obiektów typu <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="eabdf-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="eabdf-138">Każda <xref:System.Windows.Setter> ustawia dla <xref:System.Windows.Style>inną wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="eabdf-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="eabdf-139">W związku z tym, w tym momencie każdy przycisk w aplikacji ma szerokość 90 i margines 10.</span><span class="sxs-lookup"><span data-stu-id="eabdf-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="eabdf-140">Jeśli naciśniesz klawisz F5, aby uruchomić aplikację, zobaczysz następujące okno.</span><span class="sxs-lookup"><span data-stu-id="eabdf-140">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="eabdf-141">![Przyciski o szerokości 90 i marginesie 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="eabdf-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="eabdf-142">Istnieje dużo więcej możliwości z stylami, w tym różne sposoby dostosowania obiektów do celów, określania złożonych wartości właściwości, a nawet style jako dane wejściowe dla innych stylów.</span><span class="sxs-lookup"><span data-stu-id="eabdf-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="eabdf-143">Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="eabdf-143">For more information, see [Styling and Templating](styling-and-templating.md).</span></span>

3. <span data-ttu-id="eabdf-144">**Ustaw wartość właściwości styl na zasób:** Zasoby umożliwiają proste użycie często zdefiniowanych obiektów i wartości.</span><span class="sxs-lookup"><span data-stu-id="eabdf-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="eabdf-145">Jest to szczególnie przydatne do definiowania złożonych wartości przy użyciu zasobów, aby kod był bardziej modularny.</span><span class="sxs-lookup"><span data-stu-id="eabdf-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="eabdf-146">Dodaj następujące wyróżnione znaczniki do pliku App. XAML.</span><span class="sxs-lookup"><span data-stu-id="eabdf-146">Add the following highlighted markup to app.xaml.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="eabdf-147">Bezpośrednio w bloku `Application.Resources` został utworzony zasób o nazwie "GrayBlueGradientBrush".</span><span class="sxs-lookup"><span data-stu-id="eabdf-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="eabdf-148">Ten zasób definiuje gradient poziomy.</span><span class="sxs-lookup"><span data-stu-id="eabdf-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="eabdf-149">Tego zasobu można używać jako wartości właściwości z dowolnego miejsca w aplikacji, w tym do metody ustawiającej style przycisku dla właściwości <xref:System.Windows.Controls.Control.Background%2A>.</span><span class="sxs-lookup"><span data-stu-id="eabdf-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="eabdf-150">Teraz wszystkie przyciski mają <xref:System.Windows.Controls.Control.Background%2A> wartość właściwości tego gradientu.</span><span class="sxs-lookup"><span data-stu-id="eabdf-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="eabdf-151">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="eabdf-151">Press F5 to run the application.</span></span> <span data-ttu-id="eabdf-152">Powinien wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="eabdf-152">It should look like the following.</span></span>

     <span data-ttu-id="eabdf-153">![Przyciski z tłem gradientowym](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="eabdf-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="eabdf-154">Utwórz szablon definiujący wygląd przycisku</span><span class="sxs-lookup"><span data-stu-id="eabdf-154">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="eabdf-155">W tej sekcji utworzysz szablon, który dostosowuje wygląd przycisku.</span><span class="sxs-lookup"><span data-stu-id="eabdf-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="eabdf-156">Prezentacja przycisku składa się z kilku obiektów, w tym prostokątów i innych składników, aby nadać przyciskowi unikatowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="eabdf-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="eabdf-157">Do tej pory kontrolka wyglądu przycisków w aplikacji została ograniczona do zmiany właściwości przycisku.</span><span class="sxs-lookup"><span data-stu-id="eabdf-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="eabdf-158">Co zrobić, jeśli chcesz wprowadzić bardziej podstawowe zmiany wyglądu przycisku?</span><span class="sxs-lookup"><span data-stu-id="eabdf-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="eabdf-159">Szablony umożliwiają zaawansowaną kontrolę nad prezentacją obiektu.</span><span class="sxs-lookup"><span data-stu-id="eabdf-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="eabdf-160">Ponieważ szablony mogą być używane w ramach stylów, można zastosować szablon do wszystkich obiektów, do których odnosi się ten styl (w tym instruktażu przycisk).</span><span class="sxs-lookup"><span data-stu-id="eabdf-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="eabdf-161">Aby użyć szablonu do zdefiniowania wyglądu przycisku</span><span class="sxs-lookup"><span data-stu-id="eabdf-161">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="eabdf-162">**Skonfiguruj szablon:** Ponieważ kontrolki, takie jak <xref:System.Windows.Controls.Button>, mają właściwość <xref:System.Windows.Controls.Control.Template%2A>, można zdefiniować wartość właściwości szablonu, tak jak w przypadku innych wartości właściwości ustawionych w <xref:System.Windows.Style> przy użyciu <xref:System.Windows.Setter>.</span><span class="sxs-lookup"><span data-stu-id="eabdf-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="eabdf-163">Dodaj następujący wyróżniony znacznik do stylu przycisku.</span><span class="sxs-lookup"><span data-stu-id="eabdf-163">Add the following highlighted markup to your button style.</span></span>

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"
        StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>
      </Style>
    </Application.Resources>
    ```

2. <span data-ttu-id="eabdf-164">**Zmień prezentację przycisku:** W tym momencie należy zdefiniować szablon.</span><span class="sxs-lookup"><span data-stu-id="eabdf-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="eabdf-165">Dodaj następujący wyróżniony znacznik.</span><span class="sxs-lookup"><span data-stu-id="eabdf-165">Add the following highlighted markup.</span></span> <span data-ttu-id="eabdf-166">Ten znacznik określa dwa <xref:System.Windows.Shapes.Rectangle> elementy z zaokrąglonymi krawędziami, po których następuje <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="eabdf-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="eabdf-167"><xref:System.Windows.Controls.DockPanel> jest używana do hostowania <xref:System.Windows.Controls.ContentPresenter> przycisku.</span><span class="sxs-lookup"><span data-stu-id="eabdf-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="eabdf-168"><xref:System.Windows.Controls.ContentPresenter> wyświetla zawartość przycisku.</span><span class="sxs-lookup"><span data-stu-id="eabdf-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="eabdf-169">W tym instruktażu zawartość jest tekstem ("Button 1", "Button 2", "Button 3").</span><span class="sxs-lookup"><span data-stu-id="eabdf-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="eabdf-170">Wszystkie składniki szablonu (prostokąty i <xref:System.Windows.Controls.DockPanel>) są zawarte w <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="eabdf-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="eabdf-171">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="eabdf-171">Press F5 to run the application.</span></span> <span data-ttu-id="eabdf-172">Powinien wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="eabdf-172">It should look like the following.</span></span>

     ![Okno z 3 przyciskami](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="eabdf-174">**Dodaj GlassEffect do szablonu:** Następnie dodasz szklaną.</span><span class="sxs-lookup"><span data-stu-id="eabdf-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="eabdf-175">Najpierw należy utworzyć zasoby, które tworzą efekt gradientu szkła.</span><span class="sxs-lookup"><span data-stu-id="eabdf-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="eabdf-176">Dodaj te zasoby gradientowe w dowolnym miejscu w bloku `Application.Resources`:</span><span class="sxs-lookup"><span data-stu-id="eabdf-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

    ```xaml
    <Application.Resources>
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />
        <GradientStop Color="Transparent" Offset="0.4" />
        <GradientStop Color="WhiteSmoke" Offset="0.5" />
        <GradientStop Color="Transparent" Offset="0.75" />
        <GradientStop Color="WhiteSmoke" Offset="0.9" />
        <GradientStop Color="Transparent" Offset="1" />
      </GradientStopCollection>
      <LinearGradientBrush x:Key="MyGlassBrushResource"
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />
    <!-- Styles and other resources below here. -->
    ```

     <span data-ttu-id="eabdf-177">Te zasoby są używane jako <xref:System.Windows.Shapes.Shape.Fill%2A> prostokąta, który został wstawiony do <xref:System.Windows.Controls.Grid> szablonu przycisku.</span><span class="sxs-lookup"><span data-stu-id="eabdf-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="eabdf-178">Dodaj następujący wyróżniony znacznik do szablonu.</span><span class="sxs-lookup"><span data-stu-id="eabdf-178">Add the following highlighted markup to the template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"
          ClipToBounds="True">

        <!-- Outer Rectangle with rounded corners. -->
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

        <!-- Inner Rectangle with rounded corners. -->
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />

        <!-- Glass Rectangle -->
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch"
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
          Fill="{StaticResource MyGlassBrushResource}"
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
          </Rectangle.Stroke>
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>

        <!-- Present Text of the button. -->
        <DockPanel Name="myContentPresenterDockPanel">
          <ContentPresenter x:Name="myContentPresenter" Margin="20"
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
        </DockPanel>
      </Grid>
    </ControlTemplate>
    </Setter.Value>
    ```

     <span data-ttu-id="eabdf-179">Zauważ, że <xref:System.Windows.UIElement.Opacity%2A> prostokąta z właściwością `x:Name` "glassCube" ma wartość 0, więc po uruchomieniu przykładu nie widzisz prostokąta szklanego, który jest przełożony na wierzchu.</span><span class="sxs-lookup"><span data-stu-id="eabdf-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="eabdf-180">Dzieje się tak dlatego, że później dodamy wyzwalacze do szablonu, gdy użytkownik będzie współdziałać z przyciskiem.</span><span class="sxs-lookup"><span data-stu-id="eabdf-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="eabdf-181">Można jednak zobaczyć, jak wygląda przycisk teraz, zmieniając wartość <xref:System.Windows.UIElement.Opacity%2A> na 1 i uruchamiając aplikację.</span><span class="sxs-lookup"><span data-stu-id="eabdf-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="eabdf-182">Zapoznaj się z poniższym rysunkiem.</span><span class="sxs-lookup"><span data-stu-id="eabdf-182">See the following figure.</span></span> <span data-ttu-id="eabdf-183">Przed przejściem do następnego kroku Zmień <xref:System.Windows.UIElement.Opacity%2A> z powrotem na 0.</span><span class="sxs-lookup"><span data-stu-id="eabdf-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="eabdf-184">![Przyciski niestandardowe, które zostały utworzone przy użyciu języka XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="eabdf-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="eabdf-185">Utwórz interaktywny przycisk</span><span class="sxs-lookup"><span data-stu-id="eabdf-185">Create Button Interactivity</span></span>

<span data-ttu-id="eabdf-186">W tej sekcji utworzysz wyzwalacze właściwości i wyzwalacze zdarzeń, aby zmienić wartości właściwości i uruchamiać animacje w odpowiedzi na akcje użytkownika, takie jak przesuwanie wskaźnika myszy nad przyciskiem i klikanie.</span><span class="sxs-lookup"><span data-stu-id="eabdf-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="eabdf-187">Prosty sposób na dodanie interaktywności (przesuwanie myszą, wyjście myszy, kliknięcie itd.) polega na zdefiniowaniu wyzwalaczy w szablonie lub stylu.</span><span class="sxs-lookup"><span data-stu-id="eabdf-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="eabdf-188">Aby utworzyć <xref:System.Windows.Trigger>, należy zdefiniować Właściwość "warunek", taką jak: wartość właściwości Button <xref:System.Windows.UIElement.IsMouseOver%2A> jest równa `true`.</span><span class="sxs-lookup"><span data-stu-id="eabdf-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="eabdf-189">Następnie definiuje się metody ustawiające (akcje), które mają miejsce, gdy warunek wyzwalacza ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="eabdf-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="eabdf-190">Aby utworzyć interaktywny przycisk</span><span class="sxs-lookup"><span data-stu-id="eabdf-190">To create button interactivity</span></span>

1. <span data-ttu-id="eabdf-191">**Dodaj wyzwalacze szablonu:** Dodaj wyróżnione adiustacje do szablonu.</span><span class="sxs-lookup"><span data-stu-id="eabdf-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}"
          Height="{TemplateBinding Height}" ClipToBounds="True">

          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch" Stroke="Transparent"
            StrokeThickness="20"
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"
          />

          <!-- Glass Rectangle -->
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch"
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
            Fill="{StaticResource MyGlassBrushResource}"
            RenderTransformOrigin="0.5,0.5">
            <Rectangle.Stroke>
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                <LinearGradientBrush.GradientStops>
                  <GradientStop Offset="0.0" Color="LightBlue" />
                  <GradientStop Offset="1.0" Color="Gray" />
                </LinearGradientBrush.GradientStops>
              </LinearGradientBrush>
            </Rectangle.Stroke>

            <!-- These transforms have no effect as they
                 are declared here.
                 The reason the transforms are included is to be targets
                 for animation (see later). -->
            <Rectangle.RenderTransform>
              <TransformGroup>
                <ScaleTransform />
                <RotateTransform />
              </TransformGroup>
            </Rectangle.RenderTransform>

              <!-- A BevelBitmapEffect is applied to give the button a
                   "Beveled" look. -->
            <Rectangle.BitmapEffect>
              <BevelBitmapEffect />
            </Rectangle.BitmapEffect>
          </Rectangle>

          <!-- Present Text of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20"
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>

        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>
      </ControlTemplate>
    </Setter.Value>
    ```

2. <span data-ttu-id="eabdf-192">**Dodaj wyzwalacze właściwości:** Dodaj wyróżnione znaczniki do bloku `ControlTemplate.Triggers`:</span><span class="sxs-lookup"><span data-stu-id="eabdf-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="eabdf-193">Naciśnij klawisz F5, aby uruchomić aplikację i zobaczyć efekt podczas uruchamiania wskaźnika myszy nad przyciskami.</span><span class="sxs-lookup"><span data-stu-id="eabdf-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="eabdf-194">**Dodaj wyzwalacz fokusu:** Następnie dodamy kilka podobnych metod ustawiających, aby obsłużyć przypadek, gdy przycisk ma fokus (na przykład po kliknięciu przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="eabdf-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->
      <Trigger Property="IsMouseOver" Value="True">

        <!-- Below are three property settings that occur when the
             condition is met (user mouses over button).  -->
        <!-- Change the color of the outer rectangle when user          mouses over it. -->
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />

        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />

        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">
          <Setter.Value>
            <BlurBitmapEffect Radius="1" />
          </Setter.Value>
        </Setter>
      </Trigger>
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>

    </ControlTemplate.Triggers>
    ```

     <span data-ttu-id="eabdf-195">Naciśnij klawisz F5, aby uruchomić aplikację, a następnie kliknij jeden z przycisków.</span><span class="sxs-lookup"><span data-stu-id="eabdf-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="eabdf-196">Zauważ, że przycisk pozostaje wyróżniony po kliknięciu go, ponieważ nadal ma fokus.</span><span class="sxs-lookup"><span data-stu-id="eabdf-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="eabdf-197">Jeśli klikniesz inny przycisk, nowy przycisk stanie się fokusem, a ostatni z nich utraci.</span><span class="sxs-lookup"><span data-stu-id="eabdf-197">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="eabdf-198">**Dodaj animacje dla**  <xref:System.Windows.UIElement.MouseEnter> **i** <xref:System.Windows.UIElement.MouseLeave> **:** następne dodaliśmy pewne animacje do wyzwalaczy.</span><span class="sxs-lookup"><span data-stu-id="eabdf-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="eabdf-199">Dodaj następujące znaczniki w dowolnym miejscu w bloku `ControlTemplate.Triggers`.</span><span class="sxs-lookup"><span data-stu-id="eabdf-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->
    <EventTrigger RoutedEvent="Mouse.MouseEnter">
      <EventTrigger.Actions>
        <BeginStoryboard Name="mouseEnterBeginStoryboard">
          <Storyboard>
          <!-- This animation makes the glass rectangle shrink in the X direction. -->
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"
              By="-0.1" Duration="0:0:0.5" />
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->
            <DoubleAnimation
            Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"
              By="-0.1" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    <EventTrigger RoutedEvent="Mouse.MouseLeave">
      <EventTrigger.Actions>
        <!-- Stopping the storyboard sets all animated properties back to default. -->
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="eabdf-200">Prostokąt szklany zmniejsza się, gdy wskaźnik myszy przesuwa się nad przycisk i wraca do normalnego rozmiaru przy opuszczaniu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="eabdf-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="eabdf-201">Istnieją dwie animacje wyzwalane, gdy wskaźnik myszy znajduje się nad przyciskiem (<xref:System.Windows.UIElement.MouseEnter> zdarzenie jest zgłaszane).</span><span class="sxs-lookup"><span data-stu-id="eabdf-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="eabdf-202">Te animacje zmniejszają prostokąt szklany wzdłuż osi X i Y.</span><span class="sxs-lookup"><span data-stu-id="eabdf-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="eabdf-203">Zwróć uwagę na właściwości elementów <xref:System.Windows.Media.Animation.DoubleAnimation> — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span><span class="sxs-lookup"><span data-stu-id="eabdf-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="eabdf-204"><xref:System.Windows.Media.Animation.Timeline.Duration%2A> określa, że animacja występuje w ciągu 10 sekund, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> określa, że szkło zmniejszy się o dziesięć%.</span><span class="sxs-lookup"><span data-stu-id="eabdf-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="eabdf-205">Drugi wyzwalacz zdarzenia (<xref:System.Windows.UIElement.MouseLeave>) po prostu zatrzyma pierwszy z nich.</span><span class="sxs-lookup"><span data-stu-id="eabdf-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="eabdf-206">Po zatrzymaniu <xref:System.Windows.Media.Animation.Storyboard>wszystkie animowane właściwości powrócą do ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="eabdf-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="eabdf-207">W związku z tym, gdy użytkownik przesuwa wskaźnik poza przycisk, po przesunięciu wskaźnika myszy nad przycisk przechodzi do końca.</span><span class="sxs-lookup"><span data-stu-id="eabdf-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="eabdf-208">Aby uzyskać więcej informacji na temat animacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eabdf-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="eabdf-209">**Dodaj animację dla momentu kliknięcia przycisku:** Ostatnim krokiem jest dodanie wyzwalacza, gdy użytkownik kliknie przycisk.</span><span class="sxs-lookup"><span data-stu-id="eabdf-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="eabdf-210">Dodaj następujące znaczniki w dowolnym miejscu w bloku `ControlTemplate.Triggers`:</span><span class="sxs-lookup"><span data-stu-id="eabdf-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->
    <EventTrigger RoutedEvent="Button.Click">
      <EventTrigger.Actions>
        <BeginStoryboard>
          <Storyboard>
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"
              By="360" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     <span data-ttu-id="eabdf-211">Naciśnij klawisz F5, aby uruchomić aplikację, a następnie kliknij jeden z przycisków.</span><span class="sxs-lookup"><span data-stu-id="eabdf-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="eabdf-212">Po kliknięciu przycisku, prostokąt szklany obraca się wokół siebie.</span><span class="sxs-lookup"><span data-stu-id="eabdf-212">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="eabdf-213">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="eabdf-213">Summary</span></span>
 <span data-ttu-id="eabdf-214">W tym instruktażu wykonasz następujące ćwiczenia:</span><span class="sxs-lookup"><span data-stu-id="eabdf-214">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="eabdf-215">Przekierować <xref:System.Windows.Style> do typu obiektu (<xref:System.Windows.Controls.Button>).</span><span class="sxs-lookup"><span data-stu-id="eabdf-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="eabdf-216">Kontrolowane podstawowe właściwości przycisków w całej aplikacji przy użyciu <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="eabdf-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="eabdf-217">Utworzone zasoby, takie jak gradienty, które mają być używane dla wartości właściwości metod ustawiających <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="eabdf-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="eabdf-218">Dostosowany wygląd przycisków w całej aplikacji przez zastosowanie szablonu do przycisków.</span><span class="sxs-lookup"><span data-stu-id="eabdf-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="eabdf-219">Dostosowane zachowanie przycisków w odpowiedzi na akcje użytkownika (takie jak <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>i <xref:System.Windows.Controls.Primitives.ButtonBase.Click>), które uwzględniają efekty animacji.</span><span class="sxs-lookup"><span data-stu-id="eabdf-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="eabdf-220">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eabdf-220">See also</span></span>

- [<span data-ttu-id="eabdf-221">Tworzenie przycisku przy użyciu programu Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="eabdf-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="eabdf-222">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="eabdf-222">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="eabdf-223">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="eabdf-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="eabdf-224">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="eabdf-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="eabdf-225">Efekty mapy bitowej — przegląd</span><span class="sxs-lookup"><span data-stu-id="eabdf-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
