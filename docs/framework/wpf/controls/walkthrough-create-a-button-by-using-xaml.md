---
title: 'Przewodnik: Utwórz przyciska przy użyciu XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 0d8b3e476488f81e4154c876e555b3090d0287f9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377345"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="f880e-102">Przewodnik: Utwórz przyciska przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="f880e-102">Walkthrough: Create a Button by Using XAML</span></span>
<span data-ttu-id="f880e-103">Celem tego przewodnika jest Dowiedz się, jak utworzyć przycisk animowany do użycia w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f880e-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="f880e-104">W tym przewodniku używa szablonu i style w celu utworzenia zasobu dostosowany przycisk, który umożliwia oddzielenie logiki przycisk od deklaracji przycisku i ponowne użycie kodu.</span><span class="sxs-lookup"><span data-stu-id="f880e-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="f880e-105">W tym przewodniku są zapisywane w całości w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f880e-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f880e-106">Ten przewodnik przeprowadzi Cię przez kroki tworzenia aplikacji przez wpisanie lub kopiowanie i wklejanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do programu Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f880e-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Microsoft Visual Studio.</span></span> <span data-ttu-id="f880e-107">Jeśli chcesz użyć dowiedzieć się, jak używać narzędzia do projektowania (Microsoft Expression Blend) do tworzenia tej samej aplikacji, zobacz [tworzenie przycisku przy użyciu Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="f880e-107">If you would prefer to learn how to use a design tool (Microsoft Expression Blend) to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>  
  
 <span data-ttu-id="f880e-108">Na poniższej ilustracji przedstawiono Zakończono przycisków.</span><span class="sxs-lookup"><span data-stu-id="f880e-108">The following figure shows the finished buttons.</span></span>  
  
 <span data-ttu-id="f880e-109">![Przyciski niestandardowe, które zostały utworzone przy użyciu XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="f880e-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-basic-buttons"></a><span data-ttu-id="f880e-110">Tworzenie przycisków podstawowe</span><span class="sxs-lookup"><span data-stu-id="f880e-110">Create Basic Buttons</span></span>  
 <span data-ttu-id="f880e-111">Zacznijmy od utworzenia nowego projektu i dodanie kilku przycisków do okna.</span><span class="sxs-lookup"><span data-stu-id="f880e-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="f880e-112">Aby utworzyć nowy projekt WPF i dodać przyciski do okna</span><span class="sxs-lookup"><span data-stu-id="f880e-112">To create a new WPF project and add buttons to the window</span></span>  
  
1.  <span data-ttu-id="f880e-113">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f880e-113">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f880e-114">**Utwórz nowy projekt WPF:** Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f880e-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="f880e-115">Znajdź **Windows aplikacji (WPF)** szablonu i nazwy projektu "AnimatedButton".</span><span class="sxs-lookup"><span data-stu-id="f880e-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="f880e-116">Spowoduje to utworzenie szkielet dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f880e-116">This will create the skeleton for the application.</span></span>  
  
3.  <span data-ttu-id="f880e-117">**Dodaj przyciski podstawowe domyślne:** Wszystkie pliki potrzebne w tym przewodniku znajdują się w szablonie.</span><span class="sxs-lookup"><span data-stu-id="f880e-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="f880e-118">Otwórz plik Window1.xaml, klikając go dwukrotnie w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="f880e-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="f880e-119">Domyślnie jest <xref:System.Windows.Controls.Grid> element Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="f880e-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="f880e-120">Usuń <xref:System.Windows.Controls.Grid> elementu i kilku przycisków, aby dodać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony, wpisując lub skopiować i wkleić następujący wyróżniony kod do Window1.xaml:</span><span class="sxs-lookup"><span data-stu-id="f880e-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>  
  
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
  
     <span data-ttu-id="f880e-121">Naciśnij klawisz F5, aby uruchomić aplikację; powinien zostać wyświetlony zestaw przycisków, która wygląda podobnie do poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="f880e-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>  
  
     <span data-ttu-id="f880e-122">![Trzy podstawowe przyciski](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="f880e-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>  
  
     <span data-ttu-id="f880e-123">Teraz, po utworzeniu podstawowe przyciski, po zakończeniu pracy w pliku Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="f880e-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="f880e-124">Pozostałe przewodnik koncentruje się na pliku app.xaml, definiowania stylów i szablonów dla przycisków.</span><span class="sxs-lookup"><span data-stu-id="f880e-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>  
  
## <a name="set-basic-properties"></a><span data-ttu-id="f880e-125">Ustawianie właściwości podstawowe</span><span class="sxs-lookup"><span data-stu-id="f880e-125">Set Basic Properties</span></span>  
 <span data-ttu-id="f880e-126">Następnie możemy ustawić niektóre właściwości na tych przycisków, aby kontrolować wyglądu przycisku i układu.</span><span class="sxs-lookup"><span data-stu-id="f880e-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="f880e-127">Zamiast ustawienie właściwości na przyciskach oddzielnie, użyjesz zasobów do definiowania właściwości przycisku dla całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f880e-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="f880e-128">Zasoby aplikacji są koncepcyjnie podobne zewnętrznych [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] dla stron sieci Web; jednak zasoby są znacznie bardziej zaawansowane niż [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], bo pozwoli zauważyć do końca tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="f880e-128">Application resources are conceptually similar to external [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] for Web pages; however, resources are much more powerful than [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="f880e-129">Aby dowiedzieć się więcej na temat zasobów, zobacz [zasoby XAML](../advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="f880e-129">To learn more about resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="f880e-130">Aby używać stylów do ustawiania właściwości podstawowe na przyciskach</span><span class="sxs-lookup"><span data-stu-id="f880e-130">To use styles to set basic properties on the buttons</span></span>  
  
1.  <span data-ttu-id="f880e-131">**Zdefiniuj blokiem Application.Resources:** Otwórz pliku app.xaml i Dodaj następujący wyróżniony kod znaczników, jeśli nie jest już istnieje:</span><span class="sxs-lookup"><span data-stu-id="f880e-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>  
  
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
  
     <span data-ttu-id="f880e-132">Zakres zasobów jest określana przez gdy zdefiniujesz zasób.</span><span class="sxs-lookup"><span data-stu-id="f880e-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="f880e-133">Definiowanie zasobów w `Application.Resources` w pliku app.xaml plik umożliwia zasobów do użycia w dowolnym miejscu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f880e-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="f880e-134">Aby dowiedzieć się więcej na temat definiowania zakresu zasobów, zobacz [zasoby XAML](../advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="f880e-134">To learn more about defining the scope of your resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>  
  
2.  <span data-ttu-id="f880e-135">**Tworzenie stylu i definiować wartości właściwości podstawowe z nią:** Dodaj następujący kod do `Application.Resources` bloku.</span><span class="sxs-lookup"><span data-stu-id="f880e-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="f880e-136">Ten kod znaczników tworzy <xref:System.Windows.Style> która odnosi się do wszystkich przycisków w aplikacji, ustawienie <xref:System.Windows.FrameworkElement.Width%2A> przycisków do 90 i <xref:System.Windows.FrameworkElement.Margin%2A> 10:</span><span class="sxs-lookup"><span data-stu-id="f880e-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <span data-ttu-id="f880e-137"><xref:System.Windows.Style.TargetType%2A> Właściwość określa, że styl ma zastosowanie do wszystkich obiektów typu <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="f880e-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="f880e-138">Każdy <xref:System.Windows.Setter> ustawienie wartości różnych właściwości <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="f880e-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="f880e-139">W związku z tym w tym momencie każdy przycisk w aplikacji ma szerokość 90 i margines 10.</span><span class="sxs-lookup"><span data-stu-id="f880e-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="f880e-140">Jeśli użytkownik naciśnie klawisz F5, aby uruchomić aplikację, zobaczysz następujące okno.</span><span class="sxs-lookup"><span data-stu-id="f880e-140">If you press F5 to run the application, you see the following window.</span></span>  
  
     <span data-ttu-id="f880e-141">![Przyciski szerokość 90 i margines 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="f880e-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>  
  
     <span data-ttu-id="f880e-142">Jest znacznie więcej możliwości style, tym na różne sposoby, aby dostroić, które obiekty są stosowane, określając wartości właściwości złożonej i nawet przy użyciu stylów jako dane wejściowe dla innych stylów.</span><span class="sxs-lookup"><span data-stu-id="f880e-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="f880e-143">Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="f880e-143">For more information, see [Styling and Templating](styling-and-templating.md).</span></span>  
  
3.  <span data-ttu-id="f880e-144">**Ustaw wartość właściwości stylu do zasobu:** Zasoby Włącz prosty sposób na ponowne użycie typowych zdefiniowanych obiektów i wartości.</span><span class="sxs-lookup"><span data-stu-id="f880e-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="f880e-145">Jest to szczególnie przydatne do definiowania złożonych wartości przy użyciu zasobów, aby sprawić, że kod jest bardziej moduły.</span><span class="sxs-lookup"><span data-stu-id="f880e-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="f880e-146">Dodaj następujący wyróżniony kod znaczników do pliku app.xaml.</span><span class="sxs-lookup"><span data-stu-id="f880e-146">Add the following highlighted markup to app.xaml.</span></span>  
  
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
  
     <span data-ttu-id="f880e-147">Bezpośrednio pod `Application.Resources` bloku, został utworzony zasób o nazwie "GrayBlueGradientBrush".</span><span class="sxs-lookup"><span data-stu-id="f880e-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="f880e-148">Ten zasób definiuje gradient poziomy.</span><span class="sxs-lookup"><span data-stu-id="f880e-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="f880e-149">Ten zasób może służyć jako wartość właściwości z dowolnego miejsca w aplikacji, między innymi wewnątrz metoda ustawiająca styl przycisku dla <xref:System.Windows.Controls.Control.Background%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f880e-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="f880e-150">Teraz wszystkie przyciski powinny mieć <xref:System.Windows.Controls.Control.Background%2A> wartość właściwości to gradientu.</span><span class="sxs-lookup"><span data-stu-id="f880e-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>  
  
     <span data-ttu-id="f880e-151">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f880e-151">Press F5 to run the application.</span></span> <span data-ttu-id="f880e-152">Powinno to wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="f880e-152">It should look like the following.</span></span>  
  
     <span data-ttu-id="f880e-153">![Przyciski z gradientu tła](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="f880e-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="f880e-154">Tworzenie szablonu, która definiuje wygląd przycisku</span><span class="sxs-lookup"><span data-stu-id="f880e-154">Create a Template That Defines the Look of the Button</span></span>  
 <span data-ttu-id="f880e-155">W tej sekcji utworzysz szablon, który dostosowuje wyglądu przycisku (prezentacja).</span><span class="sxs-lookup"><span data-stu-id="f880e-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="f880e-156">Prezentacji przycisk składa się kilka obiektów, w tym prostokąty i inne składniki zapewniające niepowtarzalnego wyglądu przycisku.</span><span class="sxs-lookup"><span data-stu-id="f880e-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>  
  
 <span data-ttu-id="f880e-157">Do tej pory kontroli wygląd przycisków w aplikacji ma została ograniczona do zmiana właściwości przycisku.</span><span class="sxs-lookup"><span data-stu-id="f880e-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="f880e-158">Co zrobić, jeśli chcesz dokonać istotnych zmian wyglądu przycisku?</span><span class="sxs-lookup"><span data-stu-id="f880e-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="f880e-159">Dzięki szablonom zaawansowane kontrolę nad prezentacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="f880e-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="f880e-160">Ponieważ szablony mogą być używane w ramach stylów, można zastosować szablonu do wszystkich obiektów, których dotyczy stylu (w tym przewodniku przycisk).</span><span class="sxs-lookup"><span data-stu-id="f880e-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="f880e-161">Aby użyć szablonu, aby zdefiniować wyglądu przycisku</span><span class="sxs-lookup"><span data-stu-id="f880e-161">To use the template to define the look of the button</span></span>  
  
1.  <span data-ttu-id="f880e-162">**Konfigurowanie szablonu:** Ponieważ kontrolki, takie jak <xref:System.Windows.Controls.Button> mają <xref:System.Windows.Controls.Control.Template%2A> właściwości, można zdefiniować wartości właściwości szablonu, podobnie jak inne wartości właściwości ustawimy w <xref:System.Windows.Style> przy użyciu <xref:System.Windows.Setter>.</span><span class="sxs-lookup"><span data-stu-id="f880e-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="f880e-163">Dodaj następujący wyróżniony kod znaczników do własnego stylu przycisku.</span><span class="sxs-lookup"><span data-stu-id="f880e-163">Add the following highlighted markup to your button style.</span></span>  
  
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
  
2.  <span data-ttu-id="f880e-164">**Instrukcja ALTER prezentacji przycisku:** W tym momencie należy zdefiniować w szablonie.</span><span class="sxs-lookup"><span data-stu-id="f880e-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="f880e-165">Dodaj następujący wyróżniony kod znaczników.</span><span class="sxs-lookup"><span data-stu-id="f880e-165">Add the following highlighted markup.</span></span> <span data-ttu-id="f880e-166">Ten kod znaczników określa dwa <xref:System.Windows.Shapes.Rectangle> elementy z zaokrąglonymi narożnikami, następuje <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="f880e-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="f880e-167"><xref:System.Windows.Controls.DockPanel> Służy do hosta <xref:System.Windows.Controls.ContentPresenter> przycisku.</span><span class="sxs-lookup"><span data-stu-id="f880e-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="f880e-168">A <xref:System.Windows.Controls.ContentPresenter> Wyświetla zawartość przycisku.</span><span class="sxs-lookup"><span data-stu-id="f880e-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="f880e-169">W tym przewodniku zawartości jest tekst ("Przycisk 1", "Button 2", "Button 3").</span><span class="sxs-lookup"><span data-stu-id="f880e-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="f880e-170">Wszystkie składniki szablonu (prostokątów i <xref:System.Windows.Controls.DockPanel>) są ułożone wewnątrz <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f880e-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>  
  
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
  
     <span data-ttu-id="f880e-171">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f880e-171">Press F5 to run the application.</span></span> <span data-ttu-id="f880e-172">Powinno to wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="f880e-172">It should look like the following.</span></span>  
  
     <span data-ttu-id="f880e-173">![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span><span class="sxs-lookup"><span data-stu-id="f880e-173">![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span></span>  
  
3.  <span data-ttu-id="f880e-174">**Dodaj glasseffect do szablonu:** Następnie dodasz szkła.</span><span class="sxs-lookup"><span data-stu-id="f880e-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="f880e-175">Najpierw należy utworzyć niektóre zasoby tworzone efekt szkła gradientu.</span><span class="sxs-lookup"><span data-stu-id="f880e-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="f880e-176">Dodaj zasobom gradientu w dowolnym miejscu w obrębie `Application.Resources` bloku:</span><span class="sxs-lookup"><span data-stu-id="f880e-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>  
  
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
  
     <span data-ttu-id="f880e-177">Te zasoby są używane jako <xref:System.Windows.Shapes.Shape.Fill%2A> dla prostokąt, który możemy wstawianie <xref:System.Windows.Controls.Grid> szablonu przycisku.</span><span class="sxs-lookup"><span data-stu-id="f880e-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="f880e-178">Dodaj następujący wyróżniony kod znaczników do szablonu.</span><span class="sxs-lookup"><span data-stu-id="f880e-178">Add the following highlighted markup to the template.</span></span>  
  
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
  
     <span data-ttu-id="f880e-179">Należy zauważyć, że <xref:System.Windows.UIElement.Opacity%2A> prostokąta przy użyciu `x:Name` właściwość "glassCube" ma wartość 0, więc po uruchomieniu przykładu, nie ma prostokąt szkła nałożony na górze.</span><span class="sxs-lookup"><span data-stu-id="f880e-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="f880e-180">Jest to spowodowane później dodamy Wyzwalacze w szablonie dla po użytkownik wchodzi w interakcję z przyciskiem.</span><span class="sxs-lookup"><span data-stu-id="f880e-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="f880e-181">Jednak zobaczyć, jak przycisk wygląda teraz, zmieniając <xref:System.Windows.UIElement.Opacity%2A> wartości 1 i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f880e-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="f880e-182">Zobacz poniższą ilustrację.</span><span class="sxs-lookup"><span data-stu-id="f880e-182">See the following figure.</span></span> <span data-ttu-id="f880e-183">Przed przejściem do następnego kroku, należy zmienić <xref:System.Windows.UIElement.Opacity%2A> na 0.</span><span class="sxs-lookup"><span data-stu-id="f880e-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>  
  
     <span data-ttu-id="f880e-184">![Przyciski niestandardowe, które zostały utworzone przy użyciu XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="f880e-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-button-interactivity"></a><span data-ttu-id="f880e-185">Tworzenie przycisku interakcyjność</span><span class="sxs-lookup"><span data-stu-id="f880e-185">Create Button Interactivity</span></span>  
 <span data-ttu-id="f880e-186">W tej sekcji utworzysz wyzwalacze właściwości i wyzwalacze zdarzeń, aby zmienić wartości właściwości i uruchamianie animacji w odpowiedzi na akcje użytkownika, takie jak przesuwając wskaźnik myszy na przycisku, a następnie klikając polecenie.</span><span class="sxs-lookup"><span data-stu-id="f880e-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>  
  
 <span data-ttu-id="f880e-187">Łatwe dodawanie interaktywności (myszą, pozostaw myszy, kliknij pozycję i tak dalej) jest zdefiniuj Wyzwalacze w stylu lub szablonu.</span><span class="sxs-lookup"><span data-stu-id="f880e-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="f880e-188">Aby utworzyć <xref:System.Windows.Trigger>, takich jak zdefiniować właściwość "warunek": Przycisk <xref:System.Windows.UIElement.IsMouseOver%2A> wartość właściwości jest równa `true`.</span><span class="sxs-lookup"><span data-stu-id="f880e-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="f880e-189">Następnie zdefiniuj metody ustawiające (Akcje), które mają miejsce, gdy spełniony jest warunek wyzwalacza.</span><span class="sxs-lookup"><span data-stu-id="f880e-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>  
  
#### <a name="to-create-button-interactivity"></a><span data-ttu-id="f880e-190">Aby utworzyć przycisk interakcyjność</span><span class="sxs-lookup"><span data-stu-id="f880e-190">To create button interactivity</span></span>  
  
1.  <span data-ttu-id="f880e-191">**Dodawanie wyzwalaczy szablonu:** Dodaj wyróżnione znaczników do szablonu.</span><span class="sxs-lookup"><span data-stu-id="f880e-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>  
  
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
  
2.  <span data-ttu-id="f880e-192">**Dodaj wyzwalacze właściwości:** Dodaj wyróżnione znaczników `ControlTemplate.Triggers` bloku:</span><span class="sxs-lookup"><span data-stu-id="f880e-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     <span data-ttu-id="f880e-193">Naciśnij klawisz F5, aby uruchomić aplikację i zobaczyć efekt, podczas uruchamiania wskaźnik myszy nad przycisków.</span><span class="sxs-lookup"><span data-stu-id="f880e-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>  
  
3.  <span data-ttu-id="f880e-194">**Dodawanie wyzwalacza koncentracji uwagi:** Następnie dodamy kilka podobnych metod ustawiających, aby obsłużyć przypadek, gdy przycisk ma fokus (na przykład po kliknięciu przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="f880e-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>  
  
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
  
     <span data-ttu-id="f880e-195">Naciśnij klawisz F5, aby uruchomić aplikację, a następnie kliknij jeden z przycisków.</span><span class="sxs-lookup"><span data-stu-id="f880e-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="f880e-196">Zwróć uwagę, przycisk pozostaje wyróżniony, po kliknięciu ponieważ wciąż jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="f880e-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="f880e-197">Po kliknięciu przycisku inny przycisk Nowy przycisk uzyska fokus, gdy ostatnie traci go.</span><span class="sxs-lookup"><span data-stu-id="f880e-197">If you click another button, the new button gains focus while the last one loses it.</span></span>  
  
4.  <span data-ttu-id="f880e-198">**Dodawanie animacji do** <xref:System.Windows.UIElement.MouseEnter> **i** <xref:System.Windows.UIElement.MouseLeave> **:** Następnie dodamy niektórych animacji do wyzwalaczy.</span><span class="sxs-lookup"><span data-stu-id="f880e-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="f880e-199">Dodaj następujący kod, dowolne miejsce wewnątrz elementu `ControlTemplate.Triggers` bloku.</span><span class="sxs-lookup"><span data-stu-id="f880e-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>  
  
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
  
     <span data-ttu-id="f880e-200">Prostokąt szkła zmniejszana, gdy wskaźnik myszy przesuwa się nad przyciskiem i zwraca z powrotem do normalnego rozmiaru po odsunięciu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f880e-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>  
  
     <span data-ttu-id="f880e-201">Istnieją dwa animacji, które są wyzwalane, gdy wskaźnik myszy nad przyciskiem (<xref:System.Windows.UIElement.MouseEnter> zdarzenie jest zgłaszane).</span><span class="sxs-lookup"><span data-stu-id="f880e-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="f880e-202">Te animacji zmniejszyć prostokąt szkła wzdłuż osi X i Y.</span><span class="sxs-lookup"><span data-stu-id="f880e-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="f880e-203">Zauważ, że właściwości na <xref:System.Windows.Media.Animation.DoubleAnimation> elementów — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span><span class="sxs-lookup"><span data-stu-id="f880e-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="f880e-204"><xref:System.Windows.Media.Animation.Timeline.Duration%2A> Określa animacji ponad pół sekundy, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Określa, że szkła zmniejsza się o 10%.</span><span class="sxs-lookup"><span data-stu-id="f880e-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>  
  
     <span data-ttu-id="f880e-205">Drugi wyzwalacz zdarzenia (<xref:System.Windows.UIElement.MouseLeave>) po prostu zatrzymuje pierwszy z nich.</span><span class="sxs-lookup"><span data-stu-id="f880e-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="f880e-206">W chwili zatrzymania <xref:System.Windows.Media.Animation.Storyboard>, animowany właściwości powrócić do wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="f880e-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="f880e-207">W związku z tym kiedy użytkownik przesunie wskaźnik myszy poza przycisk, przycisk powraca do sposób, w jaki był, zanim wskaźnik myszy jest przesuwany nad przycisku.</span><span class="sxs-lookup"><span data-stu-id="f880e-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="f880e-208">Aby uzyskać więcej informacji na temat animacji, zobacz [Przegląd animacja](../graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f880e-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>  
  
5.  <span data-ttu-id="f880e-209">**Dodawanie animacji do po kliknięciu przycisku:** Ostatnim krokiem jest dodać wyzwalacza, gdy użytkownik kliknie przycisk.</span><span class="sxs-lookup"><span data-stu-id="f880e-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="f880e-210">Dodaj następujący kod, dowolne miejsce wewnątrz elementu `ControlTemplate.Triggers` bloku:</span><span class="sxs-lookup"><span data-stu-id="f880e-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>  
  
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
  
     <span data-ttu-id="f880e-211">Naciśnij klawisz F5, aby uruchomić aplikację i kliknij jeden z przycisków.</span><span class="sxs-lookup"><span data-stu-id="f880e-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="f880e-212">Po kliknięciu przycisku, szkła prostokąt obraca się wokół.</span><span class="sxs-lookup"><span data-stu-id="f880e-212">When you click a button, the glass rectangle spins around.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="f880e-213">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="f880e-213">Summary</span></span>  
 <span data-ttu-id="f880e-214">W tym przewodniku wykonywane są następujące Ćwiczenia:</span><span class="sxs-lookup"><span data-stu-id="f880e-214">In this walkthrough, you performed the following exercises:</span></span>  
  
-   <span data-ttu-id="f880e-215">Docelowe <xref:System.Windows.Style> z typem obiektu (<xref:System.Windows.Controls.Button>).</span><span class="sxs-lookup"><span data-stu-id="f880e-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>  
  
-   <span data-ttu-id="f880e-216">Podstawowe właściwości przycisków w całej aplikacji, używając kontrolowane <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="f880e-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>  
  
-   <span data-ttu-id="f880e-217">Utworzone zasoby, takie jak gradientów do użycia dla wartości właściwości <xref:System.Windows.Style> metod ustawiających.</span><span class="sxs-lookup"><span data-stu-id="f880e-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>  
  
-   <span data-ttu-id="f880e-218">Dostosować wygląd przycisków w całej aplikacji, stosując szablon do przycisków.</span><span class="sxs-lookup"><span data-stu-id="f880e-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>  
  
-   <span data-ttu-id="f880e-219">Dostosowywać zachowanie dla przycisków w odpowiedzi na działanie użytkownika (takie jak <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, i <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) które zawarte efektów animacji.</span><span class="sxs-lookup"><span data-stu-id="f880e-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f880e-220">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f880e-220">See also</span></span>
- [<span data-ttu-id="f880e-221">Tworzenie przycisku przy użyciu programu Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="f880e-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="f880e-222">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="f880e-222">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="f880e-223">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="f880e-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="f880e-224">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="f880e-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="f880e-225">Efekty mapy bitowej — przegląd</span><span class="sxs-lookup"><span data-stu-id="f880e-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
