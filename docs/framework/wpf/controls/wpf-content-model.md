---
title: Model zawartości WPF
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
ms.openlocfilehash: 4f866e0366a7781c287b3ebae7b668c2b296a5cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134611"
---
# <a name="wpf-content-model"></a><span data-ttu-id="fbc33-102">Model zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="fbc33-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="fbc33-103">jest to platforma prezentacji, która zawiera wiele kontrolek i typy kontroli którego podstawowym celem jest do wyświetlania różnych typów zawartości.</span><span class="sxs-lookup"><span data-stu-id="fbc33-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="fbc33-104">Aby określić, które określają, aby używać lub które określają, które ma być z, należy poznać rodzaje obiektów, które najlepiej wyświetlić określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="fbc33-105">Ten temat zawiera podsumowanie model zawartości dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli i typy kontroli.</span><span class="sxs-lookup"><span data-stu-id="fbc33-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="fbc33-106">Model zawartości w tym artykule opisano zawartość, mogą być używane w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="fbc33-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="fbc33-107">Ten temat zawiera także właściwości zawartości dla każdego modelu zawartości.</span><span class="sxs-lookup"><span data-stu-id="fbc33-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="fbc33-108">Właściwość zawartości ma właściwości, która jest używana do przechowywania zawartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="fbc33-109">Klasy, które zawierają dowolne zawartości</span><span class="sxs-lookup"><span data-stu-id="fbc33-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="fbc33-110">Niektóre kontrolki mogą zawierać obiekt dowolnego typu, na przykład ciąg, <xref:System.DateTime> obiektu lub <xref:System.Windows.UIElement> oznacza to kontener dla dodatkowych elementów.</span><span class="sxs-lookup"><span data-stu-id="fbc33-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="fbc33-111">Na przykład <xref:System.Windows.Controls.Button> może zawierać obraz i tekst; lub <xref:System.Windows.Controls.CheckBox> może zawierać wartości <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="fbc33-112">ma cztery klas, które może zawierać dowolną zawartość.</span><span class="sxs-lookup"><span data-stu-id="fbc33-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="fbc33-113">Poniższa tabela zawiera listę klas, które dziedziczą z <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="fbc33-114">Klasa, która zawiera dowolną zawartość</span><span class="sxs-lookup"><span data-stu-id="fbc33-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="fbc33-115">Zawartość</span><span class="sxs-lookup"><span data-stu-id="fbc33-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="fbc33-116">Dowolnego pojedynczego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="fbc33-117">Nagłówek i pojedynczy element, które są dowolne obiekty.</span><span class="sxs-lookup"><span data-stu-id="fbc33-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="fbc33-118">Kolekcja dowolnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="fbc33-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="fbc33-119">Nagłówek i kolekcji elementów, które są dowolne obiekty.</span><span class="sxs-lookup"><span data-stu-id="fbc33-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="fbc33-120">Formanty, które dziedziczą z tych klas może zawierać ten sam typ zawartości i traktować zawartość w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="fbc33-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="fbc33-121">Poniższa ilustracja przedstawia jeden formant z każdego modelu zawartości, który zawiera obraz i tekst:</span><span class="sxs-lookup"><span data-stu-id="fbc33-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Zrzut ekranu pokazujący cztery różne formanty z każdego modelu zawartości.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="fbc33-123">Formanty, które zawierają dowolnego pojedynczego obiektu</span><span class="sxs-lookup"><span data-stu-id="fbc33-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="fbc33-124"><xref:System.Windows.Controls.ContentControl> Klasa zawiera pojedynczy dowolną zawartość.</span><span class="sxs-lookup"><span data-stu-id="fbc33-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="fbc33-125">Jego właściwość zawartości ma <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="fbc33-126">Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.ContentControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="fbc33-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 <span data-ttu-id="fbc33-127">Poniższa ilustracja przedstawia cztery przyciski, którego <xref:System.Windows.Controls.ContentControl.Content%2A> jest ustawiony na ciąg <xref:System.DateTime> obiektu <xref:System.Windows.Shapes.Rectangle>, a <xref:System.Windows.Controls.Panel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>:</span><span class="sxs-lookup"><span data-stu-id="fbc33-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Zrzut ekranu pokazujący czterech przycisków z różnymi typami zawartości.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="fbc33-129">Aby uzyskać przykład sposobu ustawiania <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości, zobacz <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="fbc33-130">Formanty, które zawiera nagłówek i dowolnego pojedynczego obiektu</span><span class="sxs-lookup"><span data-stu-id="fbc33-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="fbc33-131"><xref:System.Windows.Controls.HeaderedContentControl> Klasa dziedziczy <xref:System.Windows.Controls.ContentControl> i wyświetla zawartość przy użyciu nagłówka.</span><span class="sxs-lookup"><span data-stu-id="fbc33-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="fbc33-132">Dziedziczy właściwości zawartości <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> i definiuje <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> właściwość, która jest typu <xref:System.Object>; w związku z tym, jednocześnie może być dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="fbc33-133">Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.HeaderedContentControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="fbc33-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="fbc33-134">Na poniższej ilustracji przedstawiono dwie <xref:System.Windows.Controls.TabItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fbc33-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="fbc33-135">Pierwszy <xref:System.Windows.Controls.TabItem> ma <xref:System.Windows.UIElement> obiektów jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="fbc33-136"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Ustawiono <xref:System.Windows.Controls.StackPanel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="fbc33-137"><xref:System.Windows.Controls.ContentControl.Content%2A> Ustawiono <xref:System.Windows.Controls.StackPanel> zawierający <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="fbc33-138">Drugi <xref:System.Windows.Controls.TabItem> zawiera ciąg <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![TabControl, który używa różnych typów we właściwości nagłówka.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="fbc33-140">Aby uzyskać przykład sposobu tworzenia <xref:System.Windows.Controls.TabItem> obiekty, zobacz <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="fbc33-141">Formanty, które zawiera kolekcję obiektów dowolnego</span><span class="sxs-lookup"><span data-stu-id="fbc33-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="fbc33-142"><xref:System.Windows.Controls.ItemsControl> Klasa dziedziczy <xref:System.Windows.Controls.Control> i może zawierać wiele elementów, takich jak ciągi, obiektów i innych elementów.</span><span class="sxs-lookup"><span data-stu-id="fbc33-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="fbc33-143">Jej właściwości zawartości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> i <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="fbc33-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> zazwyczaj używany do wypełnienia <xref:System.Windows.Controls.ItemsControl> ze zbieraniem danych.</span><span class="sxs-lookup"><span data-stu-id="fbc33-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="fbc33-145">Jeśli nie chcesz używać kolekcji, aby wypełnić <xref:System.Windows.Controls.ItemsControl>, można dodać elementy przy użyciu <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc33-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="fbc33-146">Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.ItemsControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="fbc33-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="fbc33-147">Poniższa ilustracja przedstawia <xref:System.Windows.Controls.ListBox> zawiera następujące typy elementów:</span><span class="sxs-lookup"><span data-stu-id="fbc33-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
-   <span data-ttu-id="fbc33-148">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="fbc33-148">A string.</span></span>  
  
-   <span data-ttu-id="fbc33-149">Element <xref:System.DateTime> obiektu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-149">A <xref:System.DateTime> object.</span></span>  
  
-   <span data-ttu-id="fbc33-150">A <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-150">A <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="fbc33-151">A <xref:System.Windows.Controls.Panel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Zrzut ekranu pokazujący ListBox z czterema typami zawartości.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="fbc33-153">Formanty, które zawiera nagłówek i kolekcji dowolnych obiektów</span><span class="sxs-lookup"><span data-stu-id="fbc33-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="fbc33-154"><xref:System.Windows.Controls.HeaderedItemsControl> Klasa dziedziczy <xref:System.Windows.Controls.ItemsControl> i może zawierać wiele elementów, takich jak ciągi, obiektów, lub innych elementów i nagłówek.</span><span class="sxs-lookup"><span data-stu-id="fbc33-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="fbc33-155">Dziedziczy <xref:System.Windows.Controls.ItemsControl> zawartości właściwości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, i <xref:System.Windows.Controls.ItemsControl.Items%2A>, i definiuje <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwości, które mogą być dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="fbc33-156">Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.HeaderedItemsControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="fbc33-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="fbc33-157">Klasy zawierające kolekcję obiektów element interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fbc33-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="fbc33-158"><xref:System.Windows.Controls.Panel> Klas umieszcza i rozmieszcza podrzędnych <xref:System.Windows.UIElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fbc33-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="fbc33-159">Jego właściwość zawartości ma <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="fbc33-160">Następujące klasy dziedziczą <xref:System.Windows.Controls.Panel> klasy i użyć jej w modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="fbc33-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="fbc33-161">Aby uzyskać więcej informacji, zobacz [Przegląd panele](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fbc33-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="fbc33-162">Klasy, które wpływają na wygląd element interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fbc33-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="fbc33-163"><xref:System.Windows.Controls.Decorator> Klasa ma zastosowanie efektów wizualnych lub wokół pojedynczy element podrzędny <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="fbc33-164">Jego właściwość zawartości ma <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="fbc33-165">Następujące klasy dziedziczą <xref:System.Windows.Controls.Decorator> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="fbc33-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="fbc33-166">Poniższa ilustracja przedstawia <xref:System.Windows.Controls.TextBox> zawierający (zostanie nadany) <xref:System.Windows.Controls.Border> wokół niej.</span><span class="sxs-lookup"><span data-stu-id="fbc33-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="fbc33-167">![Pole tekstowe z czarnym obramowaniem](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="fbc33-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="fbc33-168">Blok tekstu, który ma obramowanie</span><span class="sxs-lookup"><span data-stu-id="fbc33-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="fbc33-169">Klasy, które zapewniają wizualną opinię na temat element interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fbc33-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="fbc33-170"><xref:System.Windows.Documents.Adorner> Klasa udostępnia podpowiedzi wizualne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fbc33-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="fbc33-171">Na przykład użyć <xref:System.Windows.Documents.Adorner> dodawania funkcjonalności dojść do elementów lub podać informacje o kontrolce stanie.</span><span class="sxs-lookup"><span data-stu-id="fbc33-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="fbc33-172"><xref:System.Windows.Documents.Adorner> Klasa udostępnia strukturę, dzięki czemu można tworzyć własne moduły definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="fbc33-173">nie zapewnia żadnych zaimplementowano moduły definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="fbc33-174">Aby uzyskać więcej informacji, zobacz [Przegląd moduły indeksowania układu](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fbc33-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="fbc33-175">Klasy, które umożliwiają użytkownikom wprowadzanie tekstu</span><span class="sxs-lookup"><span data-stu-id="fbc33-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="fbc33-176">WPF zawiera trzy kontrolki podstawowej, które umożliwiają użytkownikom wprowadzanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="fbc33-177">Tekst jest wyświetlany w każdej kontrolce inaczej.</span><span class="sxs-lookup"><span data-stu-id="fbc33-177">Each control displays the text differently.</span></span> <span data-ttu-id="fbc33-178">W poniższej tabeli przedstawiono te trzy związane z tekstem kontrolki, ich możliwości, gdy są wyświetlane, tekstu i ich właściwości, które zawierają tekst kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fbc33-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="fbc33-179">formant</span><span class="sxs-lookup"><span data-stu-id="fbc33-179">Control</span></span>|<span data-ttu-id="fbc33-180">Tekst jest wyświetlany jako</span><span class="sxs-lookup"><span data-stu-id="fbc33-180">Text is displayed as</span></span>|<span data-ttu-id="fbc33-181">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="fbc33-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="fbc33-182">Zwykły tekst</span><span class="sxs-lookup"><span data-stu-id="fbc33-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="fbc33-183">Tekst sformatowany</span><span class="sxs-lookup"><span data-stu-id="fbc33-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="fbc33-184">Tekst (znaki są maskowane) ukryty</span><span class="sxs-lookup"><span data-stu-id="fbc33-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="fbc33-185">Klasy zawierające tekst</span><span class="sxs-lookup"><span data-stu-id="fbc33-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="fbc33-186">Kilka klas może służyć do wyświetlania tekstu zwykłego lub sformatowany.</span><span class="sxs-lookup"><span data-stu-id="fbc33-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="fbc33-187">Możesz użyć <xref:System.Windows.Controls.TextBlock> do wyświetlenia niewielkich ilości tekstu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="fbc33-188">Aby wyświetlić dużych ilości tekstu, należy użyć <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, lub <xref:System.Windows.Controls.FlowDocumentScrollViewer> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fbc33-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="fbc33-189"><xref:System.Windows.Controls.TextBlock> Ma dwie właściwości zawartości: <xref:System.Windows.Controls.TextBlock.Text%2A> i <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbc33-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="fbc33-190">Gdy chcesz wyświetlić tekst, który używa spójnego formatowania <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość jest często najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="fbc33-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="fbc33-191">Jeśli planujesz korzystanie z innego formatowania przez cały tekst, użyj <xref:System.Windows.Controls.TextBlock.Inlines%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc33-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="fbc33-192"><xref:System.Windows.Controls.TextBlock.Inlines%2A> Właściwości to zbiór <xref:System.Windows.Documents.Inline> obiektów, które określają sposób formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="fbc33-193">W poniższej tabeli wymieniono właściwość zawartości dla <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer> klasy.</span><span class="sxs-lookup"><span data-stu-id="fbc33-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="fbc33-194">formant</span><span class="sxs-lookup"><span data-stu-id="fbc33-194">Control</span></span>|<span data-ttu-id="fbc33-195">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="fbc33-195">Content property</span></span>|<span data-ttu-id="fbc33-196">Typ właściwości zawartości</span><span class="sxs-lookup"><span data-stu-id="fbc33-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="fbc33-197">dokument</span><span class="sxs-lookup"><span data-stu-id="fbc33-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="fbc33-198">dokument</span><span class="sxs-lookup"><span data-stu-id="fbc33-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="fbc33-199">dokument</span><span class="sxs-lookup"><span data-stu-id="fbc33-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="fbc33-200"><xref:System.Windows.Documents.FlowDocument> Implementuje <xref:System.Windows.Documents.IDocumentPaginatorSource> interfejs; w związku z tym, może zająć wszystkich trzech klasach <xref:System.Windows.Documents.FlowDocument> jako zawartość.</span><span class="sxs-lookup"><span data-stu-id="fbc33-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="fbc33-201">Klasy, które formatowania tekstu</span><span class="sxs-lookup"><span data-stu-id="fbc33-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="fbc33-202"><xref:System.Windows.Documents.TextElement> i jej klasy pokrewne pozwalają do formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="fbc33-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="fbc33-203"><xref:System.Windows.Documents.TextElement> obiekty zawierają i formatowanie tekstu w <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fbc33-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="fbc33-204">Dwa podstawowe typy <xref:System.Windows.Documents.TextElement> obiekty są <xref:System.Windows.Documents.Block> elementy i <xref:System.Windows.Documents.Inline> elementów.</span><span class="sxs-lookup"><span data-stu-id="fbc33-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="fbc33-205">A <xref:System.Windows.Documents.Block> element reprezentuje blok tekstu, np. akapitu lub listy.</span><span class="sxs-lookup"><span data-stu-id="fbc33-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="fbc33-206"><xref:System.Windows.Documents.Inline> Element reprezentuje fragment tekstu w bloku.</span><span class="sxs-lookup"><span data-stu-id="fbc33-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="fbc33-207">Wiele <xref:System.Windows.Documents.Inline> klasy określić formatowanie tekstu, do której są stosowane.</span><span class="sxs-lookup"><span data-stu-id="fbc33-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="fbc33-208">Każdy <xref:System.Windows.Documents.TextElement> ma swój własny model zawartości.</span><span class="sxs-lookup"><span data-stu-id="fbc33-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="fbc33-209">Aby uzyskać więcej informacji, zobacz [omówienie modelu zawartości TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fbc33-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc33-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbc33-210">See also</span></span>

- [<span data-ttu-id="fbc33-211">Zaawansowane</span><span class="sxs-lookup"><span data-stu-id="fbc33-211">Advanced</span></span>](../advanced/index.md)
