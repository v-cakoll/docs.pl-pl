---
title: Model zawartości
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: a84ab2e66b4e373591fc9365b1c17d0bb0c66713
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738280"
---
# <a name="wpf-content-model"></a><span data-ttu-id="be2cc-102">Model zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="be2cc-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="be2cc-103">jest platformą prezentacji, która udostępnia wiele kontrolek i typy podobne do kontroli, których głównym celem jest wyświetlanie różnych typów zawartości.</span><span class="sxs-lookup"><span data-stu-id="be2cc-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="be2cc-104">Aby określić, która kontrolka ma być używana lub która z nich pochodzi, należy zrozumieć rodzaje obiektów, które mogą być wyświetlane dla konkretnej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be2cc-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="be2cc-105">Ten temat zawiera podsumowanie modelu zawartości dla formantów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i typów przypominających o kontrolkach.</span><span class="sxs-lookup"><span data-stu-id="be2cc-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="be2cc-106">Model zawartości opisuje zawartość, która może być używana w formancie.</span><span class="sxs-lookup"><span data-stu-id="be2cc-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="be2cc-107">W tym temacie wymieniono również właściwości zawartości dla każdego modelu zawartości.</span><span class="sxs-lookup"><span data-stu-id="be2cc-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="be2cc-108">Właściwość Content jest właściwością, która jest używana do przechowywania zawartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="be2cc-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="be2cc-109">Klasy, które zawierają dowolną zawartość</span><span class="sxs-lookup"><span data-stu-id="be2cc-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="be2cc-110">Niektóre kontrolki mogą zawierać obiekt dowolnego typu, takich jak ciąg, obiekt <xref:System.DateTime> lub <xref:System.Windows.UIElement>, który jest kontenerem dla dodatkowych elementów.</span><span class="sxs-lookup"><span data-stu-id="be2cc-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="be2cc-111">Na przykład <xref:System.Windows.Controls.Button> może zawierać obraz i jakiś tekst; lub <xref:System.Windows.Controls.CheckBox> może zawierać wartość <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="be2cc-112">ma cztery klasy, które mogą zawierać dowolną zawartość.</span><span class="sxs-lookup"><span data-stu-id="be2cc-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="be2cc-113">Poniższa tabela zawiera listę klas, które dziedziczą z <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="be2cc-114">Klasa, która zawiera dowolną zawartość</span><span class="sxs-lookup"><span data-stu-id="be2cc-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="be2cc-115">Zawartość</span><span class="sxs-lookup"><span data-stu-id="be2cc-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="be2cc-116">Pojedynczy dowolny obiekt.</span><span class="sxs-lookup"><span data-stu-id="be2cc-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="be2cc-117">Nagłówek i jeden element, z których oba są dowolnymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="be2cc-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="be2cc-118">Kolekcja dowolnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="be2cc-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="be2cc-119">Nagłówek i Kolekcja elementów, z których wszystkie są dowolnymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="be2cc-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="be2cc-120">Kontrolki dziedziczące z tych klas mogą zawierać ten sam typ zawartości i traktują zawartość w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="be2cc-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="be2cc-121">Na poniższej ilustracji przedstawiono jeden formant z każdego modelu zawartości, który zawiera obraz i jakiś tekst:</span><span class="sxs-lookup"><span data-stu-id="be2cc-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Zrzut ekranu, który pokazuje cztery różne kontrolki, jeden z każdego modelu zawartości.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="be2cc-123">Kontrolki zawierające pojedynczy dowolny obiekt</span><span class="sxs-lookup"><span data-stu-id="be2cc-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="be2cc-124">Klasa <xref:System.Windows.Controls.ContentControl> zawiera jedną część dowolnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="be2cc-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="be2cc-125">Jej właściwość content ma <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="be2cc-126">Następujące kontrolki dziedziczą z <xref:System.Windows.Controls.ContentControl> i używają modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="be2cc-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 <span data-ttu-id="be2cc-127">Na poniższej ilustracji przedstawiono cztery przyciski, których <xref:System.Windows.Controls.ContentControl.Content%2A> jest ustawiona na ciąg, obiekt <xref:System.DateTime>, <xref:System.Windows.Shapes.Rectangle>i <xref:System.Windows.Controls.Panel>, który zawiera <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>:</span><span class="sxs-lookup"><span data-stu-id="be2cc-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Zrzut ekranu przedstawiający cztery przyciski z różnymi typami zawartości.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="be2cc-129">Aby zapoznać się z przykładem sposobu ustawiania właściwości <xref:System.Windows.Controls.ContentControl.Content%2A>, zobacz <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="be2cc-130">Kontrolki zawierające nagłówek i pojedynczy dowolny obiekt</span><span class="sxs-lookup"><span data-stu-id="be2cc-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="be2cc-131">Klasa <xref:System.Windows.Controls.HeaderedContentControl> dziedziczy po <xref:System.Windows.Controls.ContentControl> i wyświetla zawartość z nagłówkiem.</span><span class="sxs-lookup"><span data-stu-id="be2cc-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="be2cc-132">Dziedziczy właściwość content, <xref:System.Windows.Controls.ContentControl.Content%2A>z <xref:System.Windows.Controls.ContentControl> i definiuje Właściwość <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>, która jest typu <xref:System.Object>; w związku z tym oba mogą być dowolnym obiektem.</span><span class="sxs-lookup"><span data-stu-id="be2cc-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="be2cc-133">Następujące kontrolki dziedziczą z <xref:System.Windows.Controls.HeaderedContentControl> i używają modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="be2cc-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="be2cc-134">Na poniższej ilustracji przedstawiono dwa obiekty <xref:System.Windows.Controls.TabItem>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="be2cc-135">Pierwszy <xref:System.Windows.Controls.TabItem> ma <xref:System.Windows.UIElement> obiekty jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="be2cc-136"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A> jest ustawiona na <xref:System.Windows.Controls.StackPanel>, która zawiera <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="be2cc-137"><xref:System.Windows.Controls.ContentControl.Content%2A> jest ustawiona na <xref:System.Windows.Controls.StackPanel>, która zawiera <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="be2cc-138">Druga <xref:System.Windows.Controls.TabItem> zawiera ciąg w <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![Kontrolka TabControl używająca różnych typów we właściwości nagłówka.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="be2cc-140">Aby zapoznać się z przykładem sposobu tworzenia obiektów <xref:System.Windows.Controls.TabItem>, zobacz <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="be2cc-141">Kontrolki zawierające kolekcję dowolnych obiektów</span><span class="sxs-lookup"><span data-stu-id="be2cc-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="be2cc-142">Klasa <xref:System.Windows.Controls.ItemsControl> dziedziczy po <xref:System.Windows.Controls.Control> i może zawierać wiele elementów, takich jak ciągi, obiekty lub inne elementy.</span><span class="sxs-lookup"><span data-stu-id="be2cc-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="be2cc-143">Jego właściwości zawartości są <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> i <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="be2cc-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jest zwykle używany do wypełniania <xref:System.Windows.Controls.ItemsControl> za pomocą zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="be2cc-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="be2cc-145">Jeśli nie chcesz używać kolekcji w celu wypełnienia <xref:System.Windows.Controls.ItemsControl>, możesz dodać elementy przy użyciu właściwości <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="be2cc-146">Następujące kontrolki dziedziczą z <xref:System.Windows.Controls.ItemsControl> i używają modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="be2cc-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="be2cc-147">Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.ListBox> zawierający następujące typy elementów:</span><span class="sxs-lookup"><span data-stu-id="be2cc-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="be2cc-148">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="be2cc-148">A string.</span></span>  
  
- <span data-ttu-id="be2cc-149">Obiekt <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="be2cc-150">Klasa <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="be2cc-151"><xref:System.Windows.Controls.Panel>, który zawiera <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Zrzut ekranu przedstawiający pole listy z czterema typami zawartości.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="be2cc-153">Kontrolki zawierające nagłówek i kolekcję dowolnych obiektów</span><span class="sxs-lookup"><span data-stu-id="be2cc-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="be2cc-154">Klasa <xref:System.Windows.Controls.HeaderedItemsControl> dziedziczy po <xref:System.Windows.Controls.ItemsControl> i może zawierać wiele elementów, takich jak ciągi, obiekty lub inne elementy oraz nagłówek.</span><span class="sxs-lookup"><span data-stu-id="be2cc-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="be2cc-155">Dziedziczy <xref:System.Windows.Controls.ItemsControl> właściwości zawartości, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>i <xref:System.Windows.Controls.ItemsControl.Items%2A>i definiuje Właściwość <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>, która może być dowolnym obiektem.</span><span class="sxs-lookup"><span data-stu-id="be2cc-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="be2cc-156">Następujące kontrolki dziedziczą z <xref:System.Windows.Controls.HeaderedItemsControl> i używają modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="be2cc-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="be2cc-157">Klasy, które zawierają kolekcję obiektów UIElement</span><span class="sxs-lookup"><span data-stu-id="be2cc-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="be2cc-158">Klasy <xref:System.Windows.Controls.Panel> umieszczają i układają obiekty podrzędne <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="be2cc-159">Jej właściwość content ma <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="be2cc-160">Następujące klasy dziedziczą z klasy <xref:System.Windows.Controls.Panel> i używają jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="be2cc-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="be2cc-161">Aby uzyskać więcej informacji, zobacz [panele — Omówienie](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="be2cc-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="be2cc-162">Klasy, które wpływają na wygląd elementu UIElement</span><span class="sxs-lookup"><span data-stu-id="be2cc-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="be2cc-163">Klasa <xref:System.Windows.Controls.Decorator> stosuje efekty wizualne na lub wokół pojedynczego <xref:System.Windows.UIElement>podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="be2cc-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="be2cc-164">Jej właściwość content ma <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="be2cc-165">Następujące klasy dziedziczą z <xref:System.Windows.Controls.Decorator> i używają modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="be2cc-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="be2cc-166">Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.TextBox>, która ma (jest dekoracyjna) <xref:System.Windows.Controls.Border> wokół niego.</span><span class="sxs-lookup"><span data-stu-id="be2cc-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="be2cc-167">![Pole tekstowe z czarnym obramowaniem](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="be2cc-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="be2cc-168">TextBlock, który ma obramowanie</span><span class="sxs-lookup"><span data-stu-id="be2cc-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="be2cc-169">Klasy, które zapewniają wizualną opinię na temat UIElement</span><span class="sxs-lookup"><span data-stu-id="be2cc-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="be2cc-170">Klasa <xref:System.Windows.Documents.Adorner> dostarcza użytkownikowi podpowiedzi do wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="be2cc-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="be2cc-171">Na przykład użyj <xref:System.Windows.Documents.Adorner>, aby dodać uchwyty funkcjonalne do elementów lub podać informacje o stanie formantu.</span><span class="sxs-lookup"><span data-stu-id="be2cc-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="be2cc-172">Klasa <xref:System.Windows.Documents.Adorner> udostępnia strukturę, która umożliwia tworzenie własnych modułów definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="be2cc-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="be2cc-173">nie udostępnia żadnych zaimplementowanych modułów definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="be2cc-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="be2cc-174">Aby uzyskać więcej informacji, zobacz Moduły [definiowania](adorners-overview.md)układu.</span><span class="sxs-lookup"><span data-stu-id="be2cc-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="be2cc-175">Klasy, które umożliwiają użytkownikom wprowadzanie tekstu</span><span class="sxs-lookup"><span data-stu-id="be2cc-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="be2cc-176">WPF udostępnia trzy podstawowe kontrolki, które umożliwiają użytkownikom wprowadzanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="be2cc-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="be2cc-177">Każdy formant Wyświetla tekst inaczej.</span><span class="sxs-lookup"><span data-stu-id="be2cc-177">Each control displays the text differently.</span></span> <span data-ttu-id="be2cc-178">W poniższej tabeli wymieniono te trzy kontrolki związane z tekstem, ich możliwości podczas wyświetlania tekstu oraz ich właściwości, które zawierają tekst kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be2cc-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="be2cc-179">formant</span><span class="sxs-lookup"><span data-stu-id="be2cc-179">Control</span></span>|<span data-ttu-id="be2cc-180">Tekst jest wyświetlany jako</span><span class="sxs-lookup"><span data-stu-id="be2cc-180">Text is displayed as</span></span>|<span data-ttu-id="be2cc-181">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="be2cc-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="be2cc-182">Zwykły tekst</span><span class="sxs-lookup"><span data-stu-id="be2cc-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="be2cc-183">Tekst sformatowany</span><span class="sxs-lookup"><span data-stu-id="be2cc-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="be2cc-184">Tekst ukryty (znaki są maskowane)</span><span class="sxs-lookup"><span data-stu-id="be2cc-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="be2cc-185">Klasy, w których jest wyświetlany tekst</span><span class="sxs-lookup"><span data-stu-id="be2cc-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="be2cc-186">Do wyświetlania zwykłego lub sformatowanego tekstu można użyć kilku klas.</span><span class="sxs-lookup"><span data-stu-id="be2cc-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="be2cc-187">Możesz użyć <xref:System.Windows.Controls.TextBlock>, aby wyświetlić małe ilości tekstu.</span><span class="sxs-lookup"><span data-stu-id="be2cc-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="be2cc-188">Aby wyświetlić duże ilości tekstu, Użyj kontrolek <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>lub <xref:System.Windows.Controls.FlowDocumentScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="be2cc-189"><xref:System.Windows.Controls.TextBlock> ma dwie właściwości zawartości: <xref:System.Windows.Controls.TextBlock.Text%2A> i <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="be2cc-190">Gdy chcesz wyświetlić tekst, który używa spójnego formatowania, właściwość <xref:System.Windows.Controls.TextBlock.Text%2A> jest często najlepszym wyborem.</span><span class="sxs-lookup"><span data-stu-id="be2cc-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="be2cc-191">Jeśli planujesz użyć innego formatowania w tekście, użyj właściwości <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="be2cc-192">Właściwość <xref:System.Windows.Controls.TextBlock.Inlines%2A> jest kolekcją obiektów <xref:System.Windows.Documents.Inline>, które określają sposób formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="be2cc-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="be2cc-193">Poniższa tabela zawiera listę właściwości zawartości dla klas <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>i <xref:System.Windows.Controls.FlowDocumentScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="be2cc-194">formant</span><span class="sxs-lookup"><span data-stu-id="be2cc-194">Control</span></span>|<span data-ttu-id="be2cc-195">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="be2cc-195">Content property</span></span>|<span data-ttu-id="be2cc-196">Typ właściwości zawartości</span><span class="sxs-lookup"><span data-stu-id="be2cc-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="be2cc-197">dokument</span><span class="sxs-lookup"><span data-stu-id="be2cc-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="be2cc-198">dokument</span><span class="sxs-lookup"><span data-stu-id="be2cc-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="be2cc-199">dokument</span><span class="sxs-lookup"><span data-stu-id="be2cc-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="be2cc-200"><xref:System.Windows.Documents.FlowDocument> implementuje interfejs <xref:System.Windows.Documents.IDocumentPaginatorSource>; w związku z tym wszystkie trzy klasy mogą przyjmować <xref:System.Windows.Documents.FlowDocument> jako zawartość.</span><span class="sxs-lookup"><span data-stu-id="be2cc-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="be2cc-201">Klasy, które formatują tekst</span><span class="sxs-lookup"><span data-stu-id="be2cc-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="be2cc-202"><xref:System.Windows.Documents.TextElement> i powiązane klasy umożliwiają formatowanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="be2cc-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="be2cc-203">obiekty <xref:System.Windows.Documents.TextElement> zawierają i formatują tekst w obiektach <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="be2cc-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="be2cc-204">Dwa podstawowe typy obiektów <xref:System.Windows.Documents.TextElement> są <xref:System.Windows.Documents.Block> elementów i <xref:System.Windows.Documents.Inline> elementów.</span><span class="sxs-lookup"><span data-stu-id="be2cc-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="be2cc-205">Element <xref:System.Windows.Documents.Block> reprezentuje blok tekstu, taki jak akapit lub lista.</span><span class="sxs-lookup"><span data-stu-id="be2cc-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="be2cc-206">Element <xref:System.Windows.Documents.Inline> reprezentuje część tekstu w bloku.</span><span class="sxs-lookup"><span data-stu-id="be2cc-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="be2cc-207">Wiele klas <xref:System.Windows.Documents.Inline> określa formatowanie tekstu, do którego są stosowane.</span><span class="sxs-lookup"><span data-stu-id="be2cc-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="be2cc-208">Każda <xref:System.Windows.Documents.TextElement> ma własny model zawartości.</span><span class="sxs-lookup"><span data-stu-id="be2cc-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="be2cc-209">Aby uzyskać więcej informacji, zobacz [Omówienie modelu zawartości TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="be2cc-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2cc-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be2cc-210">See also</span></span>

- [<span data-ttu-id="be2cc-211">Zaawansowane</span><span class="sxs-lookup"><span data-stu-id="be2cc-211">Advanced</span></span>](../advanced/index.md)
