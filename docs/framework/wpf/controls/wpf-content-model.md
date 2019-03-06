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
ms.openlocfilehash: bd9dc7a441987b2089f0f21c81311a628ae3cdfa
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373099"
---
# <a name="wpf-content-model"></a><span data-ttu-id="4e24a-102">Model zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="4e24a-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="4e24a-103">jest to platforma prezentacji, która zawiera wiele kontrolek i typy kontroli którego podstawowym celem jest do wyświetlania różnych typów zawartości.</span><span class="sxs-lookup"><span data-stu-id="4e24a-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="4e24a-104">Aby określić, które określają, aby używać lub które określają, które ma być z, należy poznać rodzaje obiektów, które najlepiej wyświetlić określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="4e24a-105">Ten temat zawiera podsumowanie model zawartości dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli i typy kontroli.</span><span class="sxs-lookup"><span data-stu-id="4e24a-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="4e24a-106">Model zawartości w tym artykule opisano zawartość, mogą być używane w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="4e24a-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="4e24a-107">Ten temat zawiera także właściwości zawartości dla każdego modelu zawartości.</span><span class="sxs-lookup"><span data-stu-id="4e24a-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="4e24a-108">Właściwość zawartości ma właściwości, która jest używana do przechowywania zawartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-108">A content property is a property that is used to store the content of the object.</span></span>  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="4e24a-109">Klasy, które zawierają dowolne zawartości</span><span class="sxs-lookup"><span data-stu-id="4e24a-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="4e24a-110">Niektóre kontrolki mogą zawierać obiekt dowolnego typu, na przykład ciąg, <xref:System.DateTime> obiektu lub <xref:System.Windows.UIElement> oznacza to kontener dla dodatkowych elementów.</span><span class="sxs-lookup"><span data-stu-id="4e24a-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="4e24a-111">Na przykład <xref:System.Windows.Controls.Button> może zawierać obraz i tekst; lub <xref:System.Windows.Controls.CheckBox> może zawierać wartości <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="4e24a-112">ma cztery klas, które może zawierać dowolną zawartość.</span><span class="sxs-lookup"><span data-stu-id="4e24a-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="4e24a-113">Poniższa tabela zawiera listę klas, które dziedziczą z <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="4e24a-114">Klasa, która zawiera dowolną zawartość</span><span class="sxs-lookup"><span data-stu-id="4e24a-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="4e24a-115">Zawartość</span><span class="sxs-lookup"><span data-stu-id="4e24a-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="4e24a-116">Dowolnego pojedynczego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="4e24a-117">Nagłówek i pojedynczy element, które są dowolne obiekty.</span><span class="sxs-lookup"><span data-stu-id="4e24a-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="4e24a-118">Kolekcja dowolnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="4e24a-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="4e24a-119">Nagłówek i kolekcji elementów, które są dowolne obiekty.</span><span class="sxs-lookup"><span data-stu-id="4e24a-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="4e24a-120">Formanty, które dziedziczą z tych klas może zawierać ten sam typ zawartości i traktować zawartość w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="4e24a-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="4e24a-121">Poniższa ilustracja przedstawia jeden formant z każdego modelu zawartości, który zawiera obraz i tekst.</span><span class="sxs-lookup"><span data-stu-id="4e24a-121">The following illustration shows one control from each content model that contains an image and some text.</span></span>  
  
 <span data-ttu-id="4e24a-122">![Przycisk, GroupBox, obiekty, TreeViewItem](./media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span><span class="sxs-lookup"><span data-stu-id="4e24a-122">![Button, GroupBox, Listbax, TreeViewItem](./media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span></span>  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="4e24a-123">Formanty, które zawierają dowolnego pojedynczego obiektu</span><span class="sxs-lookup"><span data-stu-id="4e24a-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="4e24a-124"><xref:System.Windows.Controls.ContentControl> Klasa zawiera pojedynczy dowolną zawartość.</span><span class="sxs-lookup"><span data-stu-id="4e24a-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="4e24a-125">Jego właściwość zawartości ma <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="4e24a-126">Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.ContentControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="4e24a-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="4e24a-127">Poniższa ilustracja przedstawia cztery przyciski, którego <xref:System.Windows.Controls.ContentControl.Content%2A> jest ustawiony na ciąg <xref:System.DateTime> obiektu <xref:System.Windows.Shapes.Rectangle>, a <xref:System.Windows.Controls.Panel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="4e24a-128">![Cztery przyciski](./media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span><span class="sxs-lookup"><span data-stu-id="4e24a-128">![Four buttons](./media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span></span>  
<span data-ttu-id="4e24a-129">Cztery przyciski, które mają różne typy zawartości</span><span class="sxs-lookup"><span data-stu-id="4e24a-129">Four buttons that have different types of content</span></span>  
  
 <span data-ttu-id="4e24a-130">Aby uzyskać przykład sposobu ustawiania <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości, zobacz <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-130">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="4e24a-131">Formanty, które zawiera nagłówek i dowolnego pojedynczego obiektu</span><span class="sxs-lookup"><span data-stu-id="4e24a-131">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="4e24a-132"><xref:System.Windows.Controls.HeaderedContentControl> Klasa dziedziczy <xref:System.Windows.Controls.ContentControl> i wyświetla zawartość przy użyciu nagłówka.</span><span class="sxs-lookup"><span data-stu-id="4e24a-132">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="4e24a-133">Dziedziczy właściwości zawartości <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> i definiuje <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> właściwość, która jest typu <xref:System.Object>; w związku z tym, jednocześnie może być dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-133">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="4e24a-134">Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.HeaderedContentControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="4e24a-134">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="4e24a-135">Na poniższej ilustracji przedstawiono dwie <xref:System.Windows.Controls.TabItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="4e24a-135">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="4e24a-136">Pierwszy <xref:System.Windows.Controls.TabItem> ma <xref:System.Windows.UIElement> obiektów jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-136">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="4e24a-137"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Ustawiono <xref:System.Windows.Controls.StackPanel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-137">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="4e24a-138"><xref:System.Windows.Controls.ContentControl.Content%2A> Ustawiono <xref:System.Windows.Controls.StackPanel> zawierający <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-138">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="4e24a-139">Drugi <xref:System.Windows.Controls.TabItem> zawiera ciąg <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-139">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 <span data-ttu-id="4e24a-140">![TabControl](./media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span><span class="sxs-lookup"><span data-stu-id="4e24a-140">![TabControl](./media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span></span>  
<span data-ttu-id="4e24a-141">TabControl, który używa różnych typów we właściwości nagłówka</span><span class="sxs-lookup"><span data-stu-id="4e24a-141">TabControl that uses different types in the Header property</span></span>  
  
 <span data-ttu-id="4e24a-142">Aby uzyskać przykład sposobu tworzenia <xref:System.Windows.Controls.TabItem> obiekty, zobacz <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-142">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="4e24a-143">Formanty, które zawiera kolekcję obiektów dowolnego</span><span class="sxs-lookup"><span data-stu-id="4e24a-143">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="4e24a-144"><xref:System.Windows.Controls.ItemsControl> Klasa dziedziczy <xref:System.Windows.Controls.Control> i może zawierać wiele elementów, takich jak ciągi, obiektów i innych elementów.</span><span class="sxs-lookup"><span data-stu-id="4e24a-144">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="4e24a-145">Jej właściwości zawartości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> i <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-145">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="4e24a-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> zazwyczaj używany do wypełnienia <xref:System.Windows.Controls.ItemsControl> ze zbieraniem danych.</span><span class="sxs-lookup"><span data-stu-id="4e24a-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="4e24a-147">Jeśli nie chcesz używać kolekcji, aby wypełnić <xref:System.Windows.Controls.ItemsControl>, można dodać elementy przy użyciu <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4e24a-147">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="4e24a-148">Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.ItemsControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="4e24a-148">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="4e24a-149">Poniższa ilustracja przedstawia <xref:System.Windows.Controls.ListBox> zawiera następujące typy elementów:</span><span class="sxs-lookup"><span data-stu-id="4e24a-149">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
-   <span data-ttu-id="4e24a-150">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="4e24a-150">A string.</span></span>  
  
-   <span data-ttu-id="4e24a-151">Element <xref:System.DateTime> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-151">A <xref:System.DateTime> object.</span></span>  
  
-   <span data-ttu-id="4e24a-152">A <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-152">A <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="4e24a-153">A <xref:System.Windows.Controls.Panel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-153">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="4e24a-154">![Pola listy z czterema typami zawartości](./media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span><span class="sxs-lookup"><span data-stu-id="4e24a-154">![ListBox with four types of content](./media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span></span>  
<span data-ttu-id="4e24a-155">ListBox, który zawiera wiele typów obiektów</span><span class="sxs-lookup"><span data-stu-id="4e24a-155">ListBox that contains multiple types of objects</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="4e24a-156">Formanty, które zawiera nagłówek i kolekcji dowolnych obiektów</span><span class="sxs-lookup"><span data-stu-id="4e24a-156">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="4e24a-157"><xref:System.Windows.Controls.HeaderedItemsControl> Klasa dziedziczy <xref:System.Windows.Controls.ItemsControl> i może zawierać wiele elementów, takich jak ciągi, obiektów, lub innych elementów i nagłówek.</span><span class="sxs-lookup"><span data-stu-id="4e24a-157">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="4e24a-158">Dziedziczy <xref:System.Windows.Controls.ItemsControl> zawartości właściwości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, i <xref:System.Windows.Controls.ItemsControl.Items%2A>, i definiuje <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwości, które mogą być dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-158">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="4e24a-159">Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.HeaderedItemsControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="4e24a-159">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="4e24a-160">Klasy zawierające kolekcję obiektów element interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4e24a-160">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="4e24a-161"><xref:System.Windows.Controls.Panel> Klas umieszcza i rozmieszcza podrzędnych <xref:System.Windows.UIElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="4e24a-161">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="4e24a-162">Jego właściwość zawartości ma <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-162">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="4e24a-163">Następujące klasy dziedziczą <xref:System.Windows.Controls.Panel> klasy i użyć jej w modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="4e24a-163">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="4e24a-164">Aby uzyskać więcej informacji, zobacz [Przegląd panele](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4e24a-164">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="4e24a-165">Klasy, które wpływają na wygląd element interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4e24a-165">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="4e24a-166"><xref:System.Windows.Controls.Decorator> Klasa ma zastosowanie efektów wizualnych lub wokół pojedynczy element podrzędny <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-166">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="4e24a-167">Jego właściwość zawartości ma <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-167">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="4e24a-168">Następujące klasy dziedziczą <xref:System.Windows.Controls.Decorator> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="4e24a-168">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="4e24a-169">Poniższa ilustracja przedstawia <xref:System.Windows.Controls.TextBox> zawierający (zostanie nadany) <xref:System.Windows.Controls.Border> wokół niej.</span><span class="sxs-lookup"><span data-stu-id="4e24a-169">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="4e24a-170">![Pole tekstowe z czarnym obramowaniem](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="4e24a-170">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="4e24a-171">Blok tekstu, który ma obramowanie</span><span class="sxs-lookup"><span data-stu-id="4e24a-171">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="4e24a-172">Klasy, które zapewniają wizualną opinię na temat element interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4e24a-172">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="4e24a-173"><xref:System.Windows.Documents.Adorner> Klasa udostępnia podpowiedzi wizualne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4e24a-173">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="4e24a-174">Na przykład użyć <xref:System.Windows.Documents.Adorner> dodawania funkcjonalności dojść do elementów lub podać informacje o kontrolce stanie.</span><span class="sxs-lookup"><span data-stu-id="4e24a-174">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="4e24a-175"><xref:System.Windows.Documents.Adorner> Klasa udostępnia strukturę, dzięki czemu można tworzyć własne moduły definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-175">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="4e24a-176">nie zapewnia żadnych zaimplementowano moduły definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-176">does not provide any implemented adorners.</span></span> <span data-ttu-id="4e24a-177">Aby uzyskać więcej informacji, zobacz [Przegląd moduły indeksowania układu](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4e24a-177">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="4e24a-178">Klasy, które umożliwiają użytkownikom wprowadzanie tekstu</span><span class="sxs-lookup"><span data-stu-id="4e24a-178">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="4e24a-179">WPF zawiera trzy kontrolki podstawowej, które umożliwiają użytkownikom wprowadzanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-179">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="4e24a-180">Tekst jest wyświetlany w każdej kontrolce inaczej.</span><span class="sxs-lookup"><span data-stu-id="4e24a-180">Each control displays the text differently.</span></span> <span data-ttu-id="4e24a-181">W poniższej tabeli przedstawiono te trzy związane z tekstem kontrolki, ich możliwości, gdy są wyświetlane, tekstu i ich właściwości, które zawierają tekst kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4e24a-181">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="4e24a-182">formant</span><span class="sxs-lookup"><span data-stu-id="4e24a-182">Control</span></span>|<span data-ttu-id="4e24a-183">Tekst jest wyświetlany jako</span><span class="sxs-lookup"><span data-stu-id="4e24a-183">Text is displayed as</span></span>|<span data-ttu-id="4e24a-184">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="4e24a-184">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="4e24a-185">Zwykły tekst</span><span class="sxs-lookup"><span data-stu-id="4e24a-185">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="4e24a-186">Tekst sformatowany</span><span class="sxs-lookup"><span data-stu-id="4e24a-186">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="4e24a-187">Tekst (znaki są maskowane) ukryty</span><span class="sxs-lookup"><span data-stu-id="4e24a-187">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="4e24a-188">Klasy zawierające tekst</span><span class="sxs-lookup"><span data-stu-id="4e24a-188">Classes That Display Your Text</span></span>  
 <span data-ttu-id="4e24a-189">Kilka klas może służyć do wyświetlania tekstu zwykłego lub sformatowany.</span><span class="sxs-lookup"><span data-stu-id="4e24a-189">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="4e24a-190">Możesz użyć <xref:System.Windows.Controls.TextBlock> do wyświetlenia niewielkich ilości tekstu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-190">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="4e24a-191">Aby wyświetlić dużych ilości tekstu, należy użyć <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, lub <xref:System.Windows.Controls.FlowDocumentScrollViewer> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4e24a-191">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="4e24a-192"><xref:System.Windows.Controls.TextBlock> Ma dwie właściwości zawartości: <xref:System.Windows.Controls.TextBlock.Text%2A> i <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e24a-192">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="4e24a-193">Gdy chcesz wyświetlić tekst, który używa spójnego formatowania <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość jest często najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="4e24a-193">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="4e24a-194">Jeśli planujesz korzystanie z innego formatowania przez cały tekst, użyj <xref:System.Windows.Controls.TextBlock.Inlines%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4e24a-194">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="4e24a-195"><xref:System.Windows.Controls.TextBlock.Inlines%2A> Właściwości to zbiór <xref:System.Windows.Documents.Inline> obiektów, które określają sposób formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-195">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="4e24a-196">W poniższej tabeli wymieniono właściwość zawartości dla <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer> klasy.</span><span class="sxs-lookup"><span data-stu-id="4e24a-196">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="4e24a-197">formant</span><span class="sxs-lookup"><span data-stu-id="4e24a-197">Control</span></span>|<span data-ttu-id="4e24a-198">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="4e24a-198">Content property</span></span>|<span data-ttu-id="4e24a-199">Typ właściwości zawartości</span><span class="sxs-lookup"><span data-stu-id="4e24a-199">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="4e24a-200">dokument</span><span class="sxs-lookup"><span data-stu-id="4e24a-200">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="4e24a-201">dokument</span><span class="sxs-lookup"><span data-stu-id="4e24a-201">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="4e24a-202">dokument</span><span class="sxs-lookup"><span data-stu-id="4e24a-202">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="4e24a-203"><xref:System.Windows.Documents.FlowDocument> Implementuje <xref:System.Windows.Documents.IDocumentPaginatorSource> interfejs; w związku z tym, może zająć wszystkich trzech klasach <xref:System.Windows.Documents.FlowDocument> jako zawartość.</span><span class="sxs-lookup"><span data-stu-id="4e24a-203">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="4e24a-204">Klasy, które formatowania tekstu</span><span class="sxs-lookup"><span data-stu-id="4e24a-204">Classes That Format Your Text</span></span>  
 <span data-ttu-id="4e24a-205"><xref:System.Windows.Documents.TextElement> i jej klasy pokrewne pozwalają do formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="4e24a-205"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="4e24a-206"><xref:System.Windows.Documents.TextElement> obiekty zawierają i formatowanie tekstu w <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="4e24a-206"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="4e24a-207">Dwa podstawowe typy <xref:System.Windows.Documents.TextElement> obiekty są <xref:System.Windows.Documents.Block> elementy i <xref:System.Windows.Documents.Inline> elementów.</span><span class="sxs-lookup"><span data-stu-id="4e24a-207">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="4e24a-208">A <xref:System.Windows.Documents.Block> element reprezentuje blok tekstu, np. akapitu lub listy.</span><span class="sxs-lookup"><span data-stu-id="4e24a-208">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="4e24a-209"><xref:System.Windows.Documents.Inline> Element reprezentuje fragment tekstu w bloku.</span><span class="sxs-lookup"><span data-stu-id="4e24a-209">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="4e24a-210">Wiele <xref:System.Windows.Documents.Inline> klasy określić formatowanie tekstu, do której są stosowane.</span><span class="sxs-lookup"><span data-stu-id="4e24a-210">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="4e24a-211">Każdy <xref:System.Windows.Documents.TextElement> ma swój własny model zawartości.</span><span class="sxs-lookup"><span data-stu-id="4e24a-211">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="4e24a-212">Aby uzyskać więcej informacji, zobacz [omówienie modelu zawartości TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4e24a-212">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e24a-213">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e24a-213">See also</span></span>
- [<span data-ttu-id="4e24a-214">Zaawansowane</span><span class="sxs-lookup"><span data-stu-id="4e24a-214">Advanced</span></span>](../advanced/index.md)
