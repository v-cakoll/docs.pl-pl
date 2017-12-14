---
title: "Wskazówki: Tworzenie przycisku przy użyciu XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 543e6496c826c864dc77e50fd096fc4cb43f600e
ms.sourcegitcommit: 01ea3686e74ff05e4f6de3d8d46dc603d051ec00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2017
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="99b89-102">Wskazówki: Tworzenie przycisku przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="99b89-102">Walkthrough: Create a Button by Using XAML</span></span>
<span data-ttu-id="99b89-103">Celem tego przewodnika jest Dowiedz się, jak utworzyć animowany przycisk do użycia w [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99b89-103">The objective of this walkthrough is to learn how to create an animated button for use in a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application.</span></span> <span data-ttu-id="99b89-104">W tym przewodniku zastosowano style i szablon, aby utworzyć zasób dostosowany przycisk umożliwiający ponowne użycie kodu i oddzielenie logiki przycisk z deklaracji przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="99b89-105">W tym przewodniku są zapisywane w całości w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99b89-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99b89-106">W tym przewodniku prowadzi użytkownika przez kroki tworzenia aplikacji, wpisując lub kopiowanie i wklejanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99b89-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="99b89-107">Jeśli chcesz dowiedzieć się, jak używać narzędzia projektowe (Microsoft Expression Blend) do tworzenia tej samej aplikacji, zobacz [utworzyć przycisk przy użyciu Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="99b89-107">If you would prefer to learn how to use a design tool (Microsoft Expression Blend) to create the same application, see [Create a Button by Using Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>  
  
 <span data-ttu-id="99b89-108">Na poniższej ilustracji przedstawiono Zakończono przycisków.</span><span class="sxs-lookup"><span data-stu-id="99b89-108">The following figure shows the finished buttons.</span></span>  
  
 <span data-ttu-id="99b89-109">![Przyciski niestandardowe, które zostały utworzone przy użyciu języka XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="99b89-109">![Custom buttons that were created by using XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-basic-buttons"></a><span data-ttu-id="99b89-110">Utwórz podstawowe przyciski</span><span class="sxs-lookup"><span data-stu-id="99b89-110">Create Basic Buttons</span></span>  
 <span data-ttu-id="99b89-111">Zacznijmy od tworzenia nowego projektu i dodawanie przycisków kilka do okna.</span><span class="sxs-lookup"><span data-stu-id="99b89-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="99b89-112">Aby utworzyć nowy projekt WPF i dodawanie przycisków do okna</span><span class="sxs-lookup"><span data-stu-id="99b89-112">To create a new WPF project and add buttons to the window</span></span>  
  
1.  <span data-ttu-id="99b89-113">Uruchom[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99b89-113">Start[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="99b89-114">**Utwórz nowy projekt WPF:** na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="99b89-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="99b89-115">Znajdź **aplikacji systemu Windows (WPF)** szablonu i nazwy projektu "AnimatedButton".</span><span class="sxs-lookup"><span data-stu-id="99b89-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="99b89-116">Spowoduje to utworzenie szkielet dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99b89-116">This will create the skeleton for the application.</span></span>  
  
3.  <span data-ttu-id="99b89-117">**Dodawanie przycisków domyślna podstawowa:** wszystkie pliki, które są potrzebne w tym przewodniku są udostępniane przez szablon.</span><span class="sxs-lookup"><span data-stu-id="99b89-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="99b89-118">Otwórz plik Window1.xaml przez dwukrotne kliknięcie go w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="99b89-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="99b89-119">Domyślnie jest <xref:System.Windows.Controls.Grid> element Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="99b89-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="99b89-120">Usuń <xref:System.Windows.Controls.Grid> element i dodaj kilka przycisków [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony, wpisując lub kopiowania i wklejania następujący wyróżniony kod, aby Window1.xaml:</span><span class="sxs-lookup"><span data-stu-id="99b89-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     <span data-ttu-id="99b89-121">Naciśnij klawisz F5, aby uruchomić tej aplikacji; powinny pojawić się zestaw przycisków, która wygląda podobnie do poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="99b89-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>  
  
     <span data-ttu-id="99b89-122">![Trzy podstawowe przyciski](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="99b89-122">![Three basic buttons](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>  
  
     <span data-ttu-id="99b89-123">Teraz, po utworzeniu podstawowego przycisków, zakończeniu pracy w pliku Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="99b89-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="99b89-124">Pozostałej części przewodnika skupiono się w pliku app.xaml, definiowania stylów i szablon przycisków.</span><span class="sxs-lookup"><span data-stu-id="99b89-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>  
  
## <a name="set-basic-properties"></a><span data-ttu-id="99b89-125">Właściwości podstawowe</span><span class="sxs-lookup"><span data-stu-id="99b89-125">Set Basic Properties</span></span>  
 <span data-ttu-id="99b89-126">Następnie umożliwia ustawienie kilku właściwości tych przycisków, aby kontrolować wygląd przycisku i układu.</span><span class="sxs-lookup"><span data-stu-id="99b89-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="99b89-127">Zamiast ustawienie właściwości na przyciskach oddzielnie zasobów użyje do definiowania właściwości przycisku dla całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99b89-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="99b89-128">Zasoby aplikacji jest podobny do zewnętrznego [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] dla stron sieci Web; jednak zasoby są bardziej efektywne niż [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], jak widać na koniec tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="99b89-128">Application resources are conceptually similar to external [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] for Web pages; however, resources are much more powerful than [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="99b89-129">Aby dowiedzieć się więcej na temat zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="99b89-129">To learn more about resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="99b89-130">Aby używać stylów do ustawiania podstawowych właściwości na przyciskach</span><span class="sxs-lookup"><span data-stu-id="99b89-130">To use styles to set basic properties on the buttons</span></span>  
  
1.  <span data-ttu-id="99b89-131">**Zdefiniuj bloku Application.Resources:** Otwórz app.xaml i Dodaj następujący wyróżniony kod znaczników, jeśli nie jest już istnieje:</span><span class="sxs-lookup"><span data-stu-id="99b89-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>  
  
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
  
     <span data-ttu-id="99b89-132">Zakres zasobów jest określana przez gdzie został zdefiniowany zasób.</span><span class="sxs-lookup"><span data-stu-id="99b89-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="99b89-133">Definiowanie zasobów w `Application.Resources` w pliku app.xaml plik umożliwia zasobów do użycia w dowolnym miejscu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99b89-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="99b89-134">Aby dowiedzieć się więcej na temat definiowania zakresu zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="99b89-134">To learn more about defining the scope of your resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
2.  <span data-ttu-id="99b89-135">**Tworzenie stylu oraz definiować wartości właściwości podstawowych z nim:** Dodaj następujący kod do `Application.Resources` bloku.</span><span class="sxs-lookup"><span data-stu-id="99b89-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="99b89-136">Tworzy tego znacznika <xref:System.Windows.Style> dotyczy wszystkich przycisków w ustawienia aplikacji <xref:System.Windows.FrameworkElement.Width%2A> przycisków do 90 i <xref:System.Windows.FrameworkElement.Margin%2A> do 10:</span><span class="sxs-lookup"><span data-stu-id="99b89-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <span data-ttu-id="99b89-137"><xref:System.Windows.Style.TargetType%2A> Właściwość określa, czy styl ma zastosowanie do wszystkich obiektów typu <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="99b89-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="99b89-138">Każdy <xref:System.Windows.Setter> ustawia wartość inną właściwość <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="99b89-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="99b89-139">W związku z tym w tym momencie co przycisk w aplikacji ma szerokość 90 i margines 10.</span><span class="sxs-lookup"><span data-stu-id="99b89-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="99b89-140">Jeśli użytkownik naciśnie klawisz F5, aby uruchomić aplikację, pojawi się następujące okna.</span><span class="sxs-lookup"><span data-stu-id="99b89-140">If you press F5 to run the application, you see the following window.</span></span>  
  
     <span data-ttu-id="99b89-141">![Przyciski szerokość 90 i margines 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="99b89-141">![Buttons with a width of 90 and a margin of 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>  
  
     <span data-ttu-id="99b89-142">Jest znacznie więcej można zrobić za pomocą stylów, w tym na wiele sposobów w celu dopasowania, jakie obiekty są stosowane, określania wartości właściwości złożonej i nawet przy użyciu stylów jako dane wejściowe dla innych stylów.</span><span class="sxs-lookup"><span data-stu-id="99b89-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="99b89-143">Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="99b89-143">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
3.  <span data-ttu-id="99b89-144">**Ustaw wartość właściwości stylu do zasobu:** zasobów włączyć ponownie użyć wartości często zdefiniowanych obiektów i w prosty sposób.</span><span class="sxs-lookup"><span data-stu-id="99b89-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="99b89-145">Jest szczególnie przydatne określić wartości złożonych korzystanie z zasobów w celu uczynienia kodu więcej moduły.</span><span class="sxs-lookup"><span data-stu-id="99b89-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="99b89-146">Dodaj następujący wyróżniony kod znaczników do pliku app.xaml.</span><span class="sxs-lookup"><span data-stu-id="99b89-146">Add the following highlighted markup to app.xaml.</span></span>  
  
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
  
     <span data-ttu-id="99b89-147">Bezpośrednio pod `Application.Resources` bloku, utworzony zasób o nazwie "GrayBlueGradientBrush".</span><span class="sxs-lookup"><span data-stu-id="99b89-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="99b89-148">Ten zasób definiuje gradient poziomy.</span><span class="sxs-lookup"><span data-stu-id="99b89-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="99b89-149">Ten zasób mogą być używane jako wartości właściwości z dowolnego miejsca w aplikacji, w tym wewnątrz metody ustawiającej styl przycisku dla <xref:System.Windows.Controls.Control.Background%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="99b89-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="99b89-150">Obecnie wszystkie przyciski musi <xref:System.Windows.Controls.Control.Background%2A> wartość właściwości to gradientu.</span><span class="sxs-lookup"><span data-stu-id="99b89-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>  
  
     <span data-ttu-id="99b89-151">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="99b89-151">Press F5 to run the application.</span></span> <span data-ttu-id="99b89-152">Jego wygląd powinien być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="99b89-152">It should look like the following.</span></span>  
  
     <span data-ttu-id="99b89-153">![Przyciski gradientu tła](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="99b89-153">![Buttons with a gradient background](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="99b89-154">Tworzenie szablonu, która definiuje wygląd przycisku</span><span class="sxs-lookup"><span data-stu-id="99b89-154">Create a Template That Defines the Look of the Button</span></span>  
 <span data-ttu-id="99b89-155">W tej sekcji możesz utworzyć szablon, który dostosowuje wygląd przycisku (prezentacja).</span><span class="sxs-lookup"><span data-stu-id="99b89-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="99b89-156">Prezentacja przycisk składa się z kilku obiektów w tym prostokąty i inne składniki umożliwiają unikatowy wygląd przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>  
  
 <span data-ttu-id="99b89-157">Do tej pory kontrolę nad wygląd przycisków w aplikacji ma została ograniczona do zmiana właściwości przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="99b89-158">Co zrobić, jeśli chcesz dokonać bardziej znaczące zmiany wygląd przycisku?</span><span class="sxs-lookup"><span data-stu-id="99b89-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="99b89-159">Szablony włączyć zaawansowaną kontrolę nad prezentacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="99b89-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="99b89-160">Ponieważ szablony mogą być używane w ramach stylów, można zastosować szablonu do wszystkich obiektów, których styl dotyczy (w tym przewodniku przycisku).</span><span class="sxs-lookup"><span data-stu-id="99b89-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="99b89-161">Aby użyć szablonu, aby określić wygląd przycisku</span><span class="sxs-lookup"><span data-stu-id="99b89-161">To use the template to define the look of the button</span></span>  
  
1.  <span data-ttu-id="99b89-162">**Konfigurowanie szablonu:** ponieważ formantów, takich jak <xref:System.Windows.Controls.Button> ma <xref:System.Windows.Controls.Control.Template%2A> właściwości, można zdefiniować wartości właściwości szablonu, podobnie jak inne wartości właściwości ustawiliśmy w <xref:System.Windows.Style> przy użyciu <xref:System.Windows.Setter>.</span><span class="sxs-lookup"><span data-stu-id="99b89-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="99b89-163">Dodaj następujący wyróżniony kod znaczników do własnego stylu przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-163">Add the following highlighted markup to your button style.</span></span>  
  
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
  
2.  <span data-ttu-id="99b89-164">**ALTER prezentacji przycisku:** na tym etapie należy zdefiniować w szablonie.</span><span class="sxs-lookup"><span data-stu-id="99b89-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="99b89-165">Dodaj następujący wyróżniony kod znaczników.</span><span class="sxs-lookup"><span data-stu-id="99b89-165">Add the following highlighted markup.</span></span> <span data-ttu-id="99b89-166">Ten kod znaczników określa dwa <xref:System.Windows.Shapes.Rectangle> elementy z zaokrąglonymi narożnikami, a następnie <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="99b89-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="99b89-167"><xref:System.Windows.Controls.DockPanel> Służy do hosta <xref:System.Windows.Controls.ContentPresenter> przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="99b89-168">A <xref:System.Windows.Controls.ContentPresenter> Wyświetla zawartość przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="99b89-169">W tym przewodniku zawartość jest tekst ("1 przycisk", "Przycisk 2", "Przycisk 3").</span><span class="sxs-lookup"><span data-stu-id="99b89-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="99b89-170">Wszystkie składniki szablonu (prostokątów i <xref:System.Windows.Controls.DockPanel>) są układane wewnątrz <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="99b89-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>  
  
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
  
     <span data-ttu-id="99b89-171">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="99b89-171">Press F5 to run the application.</span></span> <span data-ttu-id="99b89-172">Jego wygląd powinien być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="99b89-172">It should look like the following.</span></span>  
  
     <span data-ttu-id="99b89-173">![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span><span class="sxs-lookup"><span data-stu-id="99b89-173">![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span></span>  
  
3.  <span data-ttu-id="99b89-174">**Dodawanie do szablonu glasseffect:** obok doda szkła.</span><span class="sxs-lookup"><span data-stu-id="99b89-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="99b89-175">Najpierw należy utworzyć kilka Tworzenie gradientu efekt szkła zasobów.</span><span class="sxs-lookup"><span data-stu-id="99b89-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="99b89-176">Dodaj te gradientu zasobów dowolne miejsce w `Application.Resources` bloku:</span><span class="sxs-lookup"><span data-stu-id="99b89-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     <span data-ttu-id="99b89-177">Te zasoby są używane jako <xref:System.Windows.Shapes.Shape.Fill%2A> dla prostokąt NAS wstawianie do <xref:System.Windows.Controls.Grid> szablonu przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="99b89-178">Dodaj następujący wyróżniony kod znaczników do szablonu.</span><span class="sxs-lookup"><span data-stu-id="99b89-178">Add the following highlighted markup to the template.</span></span>  
  
    ```  
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
  
        <!-- Glass Rectangle -->     <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"       VerticalAlignment="Stretch"       StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"       Fill="{StaticResource MyGlassBrushResource}"       RenderTransformOrigin="0.5,0.5">       <Rectangle.Stroke>         <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">           <LinearGradientBrush.GradientStops>             <GradientStop Offset="0.0" Color="LightBlue" />             <GradientStop Offset="1.0" Color="Gray" />           </LinearGradientBrush.GradientStops>         </LinearGradientBrush>       </Rectangle.Stroke>       <!-- These transforms have no effect as they are declared here.             The reason the transforms are included is to be targets             for animation (see later). -->       <Rectangle.RenderTransform>         <TransformGroup>           <ScaleTransform />           <RotateTransform />         </TransformGroup>       </Rectangle.RenderTransform>       <!-- A BevelBitmapEffect is applied to give the button a             "Beveled" look. -->       <Rectangle.BitmapEffect>         <BevelBitmapEffect />       </Rectangle.BitmapEffect>     </Rectangle>  
  
        <!-- Present Text of the button. -->  
        <DockPanel Name="myContentPresenterDockPanel">  
          <ContentPresenter x:Name="myContentPresenter" Margin="20"   
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
        </DockPanel>  
      </Grid>  
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     <span data-ttu-id="99b89-179">Zwróć uwagę, że <xref:System.Windows.UIElement.Opacity%2A> prostokąta z `x:Name` właściwości "glassCube" ma wartość 0, więc po uruchomieniu próbki nie ma prostokąt szkła umieszczenia w górnej części.</span><span class="sxs-lookup"><span data-stu-id="99b89-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="99b89-180">Jest to spowodowane później dodamy Wyzwalacze w szablonie dla gdy użytkownik użyje przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="99b89-181">Jednak widoczny przycisk wygląd teraz zmieniając <xref:System.Windows.UIElement.Opacity%2A> wartości 1 i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99b89-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="99b89-182">Zobacz poniższą ilustrację.</span><span class="sxs-lookup"><span data-stu-id="99b89-182">See the following figure.</span></span> <span data-ttu-id="99b89-183">Przed przejściem do następnego kroku, zmień <xref:System.Windows.UIElement.Opacity%2A> do 0.</span><span class="sxs-lookup"><span data-stu-id="99b89-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>  
  
     <span data-ttu-id="99b89-184">![Przyciski niestandardowe, które zostały utworzone przy użyciu języka XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="99b89-184">![Custom buttons that were created by using XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-button-interactivity"></a><span data-ttu-id="99b89-185">Utwórz interakcyjności przycisku</span><span class="sxs-lookup"><span data-stu-id="99b89-185">Create Button Interactivity</span></span>  
 <span data-ttu-id="99b89-186">W tej sekcji utworzysz wyzwalaczy właściwości i wyzwalacze zdarzeń zmiany wartości właściwości i uruchomić animacji w odpowiedzi na działania użytkownika, takie jak wskaźnika myszy nad przyciskiem i kliknięcie przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>  
  
 <span data-ttu-id="99b89-187">Łatwe dodawanie interakcyjności (myszą, pozostaw myszy, kliknij przycisk itd.) jest zdefiniuj Wyzwalacze w stylu lub szablonie.</span><span class="sxs-lookup"><span data-stu-id="99b89-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="99b89-188">Aby utworzyć <xref:System.Windows.Trigger>, takich jak zdefiniować właściwości "warunku": przycisk <xref:System.Windows.UIElement.IsMouseOver%2A> wartość właściwości jest równa `true`.</span><span class="sxs-lookup"><span data-stu-id="99b89-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="99b89-189">Następnie zdefiniuj ustawiające (Akcje), które mają miejsce, gdy spełniony jest warunek wyzwalacza.</span><span class="sxs-lookup"><span data-stu-id="99b89-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>  
  
#### <a name="to-create-button-interactivity"></a><span data-ttu-id="99b89-190">Aby utworzyć interakcyjności przycisku</span><span class="sxs-lookup"><span data-stu-id="99b89-190">To create button interactivity</span></span>  
  
1.  <span data-ttu-id="99b89-191">**Dodaj szablon wyzwalaczy:** Dodaj wyróżnione znaczników do szablonu.</span><span class="sxs-lookup"><span data-stu-id="99b89-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>  
  
    ```  
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
  
2.  <span data-ttu-id="99b89-192">**Dodaj właściwość wyzwalaczy:** Dodaj wyróżnione znaczników `ControlTemplate.Triggers` bloku:</span><span class="sxs-lookup"><span data-stu-id="99b89-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     <span data-ttu-id="99b89-193">Naciśnij klawisz F5, aby uruchomić aplikację i zobaczyć efekt, jak uruchomić wskaźnik myszy nad przycisków.</span><span class="sxs-lookup"><span data-stu-id="99b89-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>  
  
3.  <span data-ttu-id="99b89-194">**Dodaj wyzwalacz fokus:** następnie dodamy pewnych ustawiające podobne do obsługi w przypadku, gdy przycisk ma fokus (na przykład po kliknięciu przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="99b89-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>  
  
    ```  
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
  
     <span data-ttu-id="99b89-195">Naciśnij klawisz F5, aby uruchomić aplikację i kliknij jeden z przycisków.</span><span class="sxs-lookup"><span data-stu-id="99b89-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="99b89-196">Zwróć uwagę, czy przycisk pozostaje wyróżnione po kliknięciu, ponieważ nadal ma fokus.</span><span class="sxs-lookup"><span data-stu-id="99b89-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="99b89-197">Jeśli klikniesz przycisk inny przycisk Nowy zyskuje fokus podczas ostatnią utraci go.</span><span class="sxs-lookup"><span data-stu-id="99b89-197">If you click another button, the new button gains focus while the last one loses it.</span></span>  
  
4.  <span data-ttu-id="99b89-198">**Dodawanie animacji do** <xref:System.Windows.UIElement.MouseEnter> **i** <xref:System.Windows.UIElement.MouseLeave> **:** obok dodamy niektórych animacji wyzwalacze.</span><span class="sxs-lookup"><span data-stu-id="99b89-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="99b89-199">Dodaj następujący kod w dowolnym miejscu wewnątrz elementu `ControlTemplate.Triggers` bloku.</span><span class="sxs-lookup"><span data-stu-id="99b89-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="99b89-200">Prostokąt szkła zmniejszana, gdy wskaźnik myszy przesuwa się nad przyciskiem i zwraca powrót do normalnego rozmiaru, gdy wskaźnik myszy opuści.</span><span class="sxs-lookup"><span data-stu-id="99b89-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>  
  
     <span data-ttu-id="99b89-201">Istnieją dwa animacji, które są wyzwalane, gdy wskaźnik myszy nad przyciskiem (<xref:System.Windows.UIElement.MouseEnter> zdarzenia).</span><span class="sxs-lookup"><span data-stu-id="99b89-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="99b89-202">Te animacje zmniejszyć prostokąt szkła wzdłuż osi X i Y.</span><span class="sxs-lookup"><span data-stu-id="99b89-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="99b89-203">Zauważ, że właściwości na <xref:System.Windows.Media.Animation.DoubleAnimation> elementy — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span><span class="sxs-lookup"><span data-stu-id="99b89-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="99b89-204"><xref:System.Windows.Media.Animation.Timeline.Duration%2A> Określa animacji ponad pół sekundy, i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Określa, że szkła zmniejsza przy 10%.</span><span class="sxs-lookup"><span data-stu-id="99b89-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>  
  
     <span data-ttu-id="99b89-205">Drugi wyzwalacza zdarzenia (<xref:System.Windows.UIElement.MouseLeave>) po prostu zatrzymuje pierwsza z nich.</span><span class="sxs-lookup"><span data-stu-id="99b89-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="99b89-206">Po zatrzymaniu <xref:System.Windows.Media.Animation.Storyboard>, animowanej właściwości powrócić do wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="99b89-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="99b89-207">W związku z tym gdy użytkownik przesuwa kursor poza przycisk, przycisk powraca sposób przed wskaźnik myszy jest przesuwany nad przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="99b89-208">Aby uzyskać więcej informacji na temat animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="99b89-208">For more information about animations, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
5.  <span data-ttu-id="99b89-209">**Dodaj animację po kliknięciu przycisku:** ostatnim krokiem jest dodanie wyzwalacz po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="99b89-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="99b89-210">Dodaj następujący kod w dowolnym miejscu wewnątrz elementu `ControlTemplate.Triggers` bloku:</span><span class="sxs-lookup"><span data-stu-id="99b89-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="99b89-211">Naciśnij klawisz F5, aby uruchomić aplikację i kliknij jeden z przycisków.</span><span class="sxs-lookup"><span data-stu-id="99b89-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="99b89-212">Po kliknięciu przycisku prostokąt szkła obraca się wokół.</span><span class="sxs-lookup"><span data-stu-id="99b89-212">When you click a button, the glass rectangle spins around.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="99b89-213">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="99b89-213">Summary</span></span>  
 <span data-ttu-id="99b89-214">W tym przewodniku wykonywane są następujące ćwiczeń:</span><span class="sxs-lookup"><span data-stu-id="99b89-214">In this walkthrough, you performed the following exercises:</span></span>  
  
-   <span data-ttu-id="99b89-215">Celem <xref:System.Windows.Style> z typem obiektu (<xref:System.Windows.Controls.Button>).</span><span class="sxs-lookup"><span data-stu-id="99b89-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>  
  
-   <span data-ttu-id="99b89-216">Kontrolowane podstawowe właściwości przycisków w całej aplikacji przy użyciu <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="99b89-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>  
  
-   <span data-ttu-id="99b89-217">Utworzone zasoby, takie jak gradientów do użycia dla wartości właściwości <xref:System.Windows.Style> setters.</span><span class="sxs-lookup"><span data-stu-id="99b89-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>  
  
-   <span data-ttu-id="99b89-218">Dostosować wygląd przycisków w całej aplikacji przez zastosowanie szablonu do przycisków.</span><span class="sxs-lookup"><span data-stu-id="99b89-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>  
  
-   <span data-ttu-id="99b89-219">Dostosowywać zachowanie w przypadku przycisków, w odpowiedzi na działania użytkownika (takich jak <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, i <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) które zawarte efekty animacji.</span><span class="sxs-lookup"><span data-stu-id="99b89-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b89-220">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99b89-220">See Also</span></span>  
 [<span data-ttu-id="99b89-221">Tworzenie przycisku przy użyciu programu Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="99b89-221">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [<span data-ttu-id="99b89-222">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="99b89-222">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="99b89-223">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="99b89-223">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="99b89-224">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="99b89-224">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="99b89-225">Efekty mapy bitowej — przegląd</span><span class="sxs-lookup"><span data-stu-id="99b89-225">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
