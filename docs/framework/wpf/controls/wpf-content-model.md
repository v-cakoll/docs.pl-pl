---
title: "Model zawartości WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52cb3a5391d6e24643b03a880d3695a11baceca3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="wpf-content-model"></a><span data-ttu-id="b2674-102">Model zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="b2674-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="b2674-103">jest to platforma prezentacji, która udostępnia wiele formantów i typów kontroli których podstawowym celem jest różnych typów zawartości.</span><span class="sxs-lookup"><span data-stu-id="b2674-103"> is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="b2674-104">Aby ustalić, które formant do użycia lub pochodzić z kontroli, należy zrozumieć typy obiektów, które najlepiej można wyświetlić określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="b2674-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="b2674-105">Ten temat zawiera podsumowanie modelu zawartości dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typów kontroli i kontroli.</span><span class="sxs-lookup"><span data-stu-id="b2674-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="b2674-106">Model zawartości w tym artykule opisano zawartości mogą być używane w formancie.</span><span class="sxs-lookup"><span data-stu-id="b2674-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="b2674-107">Ten temat zawiera także właściwości zawartości dla każdego modelu zawartości.</span><span class="sxs-lookup"><span data-stu-id="b2674-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="b2674-108">Właściwość content jest właściwość, która jest używana do przechowywania zawartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="b2674-108">A content property is a property that is used to store the content of the object.</span></span>  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="b2674-109">Klasy, które zawierają dowolnego zawartości</span><span class="sxs-lookup"><span data-stu-id="b2674-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="b2674-110">Niektóre formanty mogą zawierać obiekt dowolnego typu, takiego jak ciąg, <xref:System.DateTime> obiekt, lub <xref:System.Windows.UIElement> oznacza to kontener dla dodatkowych elementów.</span><span class="sxs-lookup"><span data-stu-id="b2674-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="b2674-111">Na przykład <xref:System.Windows.Controls.Button> może zawierać obraz i tekst; lub <xref:System.Windows.Controls.CheckBox> może zawierać wartości <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b2674-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="b2674-112">ma cztery klasy, które może zawierać dowolną zawartość.</span><span class="sxs-lookup"><span data-stu-id="b2674-112"> has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="b2674-113">W poniższej tabeli wymieniono klasy, które dziedziczą z <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="b2674-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="b2674-114">Klasa, która zawiera dowolnego zawartości</span><span class="sxs-lookup"><span data-stu-id="b2674-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="b2674-115">Zawartość</span><span class="sxs-lookup"><span data-stu-id="b2674-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="b2674-116">Dowolnego pojedynczego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b2674-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="b2674-117">Nagłówek i jeden element, które są dowolne obiekty.</span><span class="sxs-lookup"><span data-stu-id="b2674-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="b2674-118">Kolekcja dowolnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2674-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="b2674-119">Nagłówek i kolekcję elementów, które są dowolne obiekty.</span><span class="sxs-lookup"><span data-stu-id="b2674-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="b2674-120">Formanty, które dziedziczą z tych klas może zawierać zawartość tego samego typu oraz Traktuj zawartość w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="b2674-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="b2674-121">Na poniższej ilustracji przedstawiono jeden formant z każdego modelu zawartości, który zawiera obraz i tekst.</span><span class="sxs-lookup"><span data-stu-id="b2674-121">The following illustration shows one control from each content model that contains an image and some text.</span></span>  
  
 <span data-ttu-id="b2674-122">![Przycisk, GroupBox, obiekty, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span><span class="sxs-lookup"><span data-stu-id="b2674-122">![Button, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span></span>  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="b2674-123">Formanty, które zawierają dowolnego pojedynczego obiektu</span><span class="sxs-lookup"><span data-stu-id="b2674-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="b2674-124"><xref:System.Windows.Controls.ContentControl> Klasa zawiera pojedynczy dowolnego zawartości.</span><span class="sxs-lookup"><span data-stu-id="b2674-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="b2674-125">Właściwości zawartości jest <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2674-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="b2674-126">Następujące formanty dziedziczyć <xref:System.Windows.Controls.ContentControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="b2674-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="b2674-127">Poniższa ilustracja przedstawia cztery przycisków, których <xref:System.Windows.Controls.ContentControl.Content%2A> jest ustawiona na ciąg <xref:System.DateTime> obiektu, <xref:System.Windows.Shapes.Rectangle>, a <xref:System.Windows.Controls.Panel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="b2674-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="b2674-128">![Cztery przyciski](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span><span class="sxs-lookup"><span data-stu-id="b2674-128">![Four buttons](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span></span>  
<span data-ttu-id="b2674-129">Cztery przyciski, które mają różne typy zawartości</span><span class="sxs-lookup"><span data-stu-id="b2674-129">Four buttons that have different types of content</span></span>  
  
 <span data-ttu-id="b2674-130">Przykład sposobu ustawiania <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości, zobacz <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="b2674-130">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="b2674-131">Formanty, które zawierają nagłówka i dowolnego pojedynczego obiektu</span><span class="sxs-lookup"><span data-stu-id="b2674-131">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="b2674-132"><xref:System.Windows.Controls.HeaderedContentControl> Klasa dziedziczy <xref:System.Windows.Controls.ContentControl> i wyświetla zawartość z nagłówkiem.</span><span class="sxs-lookup"><span data-stu-id="b2674-132">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="b2674-133">Dziedziczy właściwość content, <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> i definiuje <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> właściwość, która jest typu <xref:System.Object>; w związku z tym jednocześnie może być dowolny obiekt.</span><span class="sxs-lookup"><span data-stu-id="b2674-133">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="b2674-134">Następujące formanty dziedziczyć <xref:System.Windows.Controls.HeaderedContentControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="b2674-134">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="b2674-135">Na poniższej ilustracji przedstawiono dwie <xref:System.Windows.Controls.TabItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2674-135">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="b2674-136">Pierwszy <xref:System.Windows.Controls.TabItem> ma <xref:System.Windows.UIElement> obiekty jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2674-136">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="b2674-137"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Ustawiono <xref:System.Windows.Controls.StackPanel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="b2674-137">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="b2674-138"><xref:System.Windows.Controls.ContentControl.Content%2A> Ustawiono <xref:System.Windows.Controls.StackPanel> zawierający <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="b2674-138">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="b2674-139">Drugi <xref:System.Windows.Controls.TabItem> zawiera ciąg <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2674-139">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 <span data-ttu-id="b2674-140">![TabControl —](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span><span class="sxs-lookup"><span data-stu-id="b2674-140">![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span></span>  
<span data-ttu-id="b2674-141">TabControl — używający różnych typów we właściwości nagłówka</span><span class="sxs-lookup"><span data-stu-id="b2674-141">TabControl that uses different types in the Header property</span></span>  
  
 <span data-ttu-id="b2674-142">Przykład sposobu tworzenia <xref:System.Windows.Controls.TabItem> obiekty, zobacz <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="b2674-142">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="b2674-143">Formanty, które zawiera kolekcję obiektów dowolnego</span><span class="sxs-lookup"><span data-stu-id="b2674-143">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="b2674-144"><xref:System.Windows.Controls.ItemsControl> Klasa dziedziczy <xref:System.Windows.Controls.Control> i może zawierać wielu elementów, takich jak ciągi, obiektów lub innych elementów.</span><span class="sxs-lookup"><span data-stu-id="b2674-144">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="b2674-145">Jego właściwości zawartości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> i <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2674-145">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="b2674-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>zazwyczaj używany do wypełnienia <xref:System.Windows.Controls.ItemsControl> włączeniu funkcji zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="b2674-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="b2674-147">Jeśli nie chcesz używać do wypełniania kolekcji <xref:System.Windows.Controls.ItemsControl>, można dodawać elementy przy użyciu <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2674-147">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="b2674-148">Następujące formanty dziedziczyć <xref:System.Windows.Controls.ItemsControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="b2674-148">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="b2674-149">Na poniższej ilustracji pokazano <xref:System.Windows.Controls.ListBox> zawiera następujące typy elementów:</span><span class="sxs-lookup"><span data-stu-id="b2674-149">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
-   <span data-ttu-id="b2674-150">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="b2674-150">A string.</span></span>  
  
-   <span data-ttu-id="b2674-151">A <xref:System.DateTime> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b2674-151">A <xref:System.DateTime> object.</span></span>  
  
-   <span data-ttu-id="b2674-152">A <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="b2674-152">A <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="b2674-153">A <xref:System.Windows.Controls.Panel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="b2674-153">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="b2674-154">![Pola listy z czterema typami zawartości](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span><span class="sxs-lookup"><span data-stu-id="b2674-154">![ListBox with four types of content](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span></span>  
<span data-ttu-id="b2674-155">Pola listy, który zawiera wiele typów obiektów</span><span class="sxs-lookup"><span data-stu-id="b2674-155">ListBox that contains multiple types of objects</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="b2674-156">Formanty, które zawierają nagłówka i kolekcji dowolnych obiektów</span><span class="sxs-lookup"><span data-stu-id="b2674-156">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="b2674-157"><xref:System.Windows.Controls.HeaderedItemsControl> Klasa dziedziczy <xref:System.Windows.Controls.ItemsControl> i może zawierać wielu elementów, takich jak ciągów, obiektów lub innych elementów i nagłówek.</span><span class="sxs-lookup"><span data-stu-id="b2674-157">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="b2674-158">Dziedziczy <xref:System.Windows.Controls.ItemsControl> zawartości właściwości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, i <xref:System.Windows.Controls.ItemsControl.Items%2A>, i definiuje <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwości, które mogą być dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b2674-158">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="b2674-159">Następujące formanty dziedziczyć <xref:System.Windows.Controls.HeaderedItemsControl> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="b2674-159">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="b2674-160">Klasy, które zawiera kolekcję obiektów UIElement</span><span class="sxs-lookup"><span data-stu-id="b2674-160">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="b2674-161"><xref:System.Windows.Controls.Panel> Klasa pozycje i rozmieszcza podrzędnych <xref:System.Windows.UIElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2674-161">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="b2674-162">Właściwości zawartości jest <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2674-162">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="b2674-163">Następujące klasy dziedziczą <xref:System.Windows.Controls.Panel> klasy i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="b2674-163">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="b2674-164">Aby uzyskać więcej informacji, zobacz [omówienie panele](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b2674-164">For more information, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="b2674-165">Klasy, które mają wpływ na wygląd elementu UIElement</span><span class="sxs-lookup"><span data-stu-id="b2674-165">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="b2674-166"><xref:System.Windows.Controls.Decorator> Klasy stosuje efekty wizualne lub wokół pojedynczy element potomny <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="b2674-166">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="b2674-167">Właściwości zawartości jest <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2674-167">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="b2674-168">Następujące klasy dziedziczą <xref:System.Windows.Controls.Decorator> i używać jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="b2674-168">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="b2674-169">Na poniższej ilustracji pokazano <xref:System.Windows.Controls.TextBox> mający (zostanie nadany) <xref:System.Windows.Controls.Border> wokół niego.</span><span class="sxs-lookup"><span data-stu-id="b2674-169">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="b2674-170">![Pole tekstowe z czarnym obramowaniem](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="b2674-170">![TextBox with black border](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="b2674-171">Blok tekstu, który ma obramowanie</span><span class="sxs-lookup"><span data-stu-id="b2674-171">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="b2674-172">Klasy, które wizualne o elementu UIElement</span><span class="sxs-lookup"><span data-stu-id="b2674-172">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="b2674-173"><xref:System.Windows.Documents.Adorner> Klasa udostępnia wizualnych do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b2674-173">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="b2674-174">Na przykład użyć <xref:System.Windows.Documents.Adorner> dodawania funkcjonalności dojść do elementów lub podaj informacje o formancie.</span><span class="sxs-lookup"><span data-stu-id="b2674-174">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="b2674-175"><xref:System.Windows.Documents.Adorner> Klasy zapewnia platformę, dzięki czemu można tworzyć własne modułu definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="b2674-175">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="b2674-176">nie ma żadnych zaimplementowanym modułu definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="b2674-176"> does not provide any implemented adorners.</span></span> <span data-ttu-id="b2674-177">Aby uzyskać więcej informacji, zobacz [omówienie modułu definiowania układu kodu](../../../../docs/framework/wpf/controls/adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b2674-177">For more information, see [Adorners Overview](../../../../docs/framework/wpf/controls/adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="b2674-178">Klasy, które umożliwiają użytkownikom wprowadzanie tekstu</span><span class="sxs-lookup"><span data-stu-id="b2674-178">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="b2674-179">WPF udostępnia trzy podstawowe formantami, które umożliwiają użytkownikom wprowadzanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="b2674-179">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="b2674-180">Tekst jest wyświetlany w każdej kontrolki inaczej.</span><span class="sxs-lookup"><span data-stu-id="b2674-180">Each control displays the text differently.</span></span> <span data-ttu-id="b2674-181">W poniższej tabeli przedstawiono te trzy związanych z tekstem formanty, ich możliwości, gdy są one wyświetlane, tekst i ich właściwości, które zawierają tekst kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b2674-181">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="b2674-182">Formant</span><span class="sxs-lookup"><span data-stu-id="b2674-182">Control</span></span>|<span data-ttu-id="b2674-183">Tekst jest wyświetlany jako</span><span class="sxs-lookup"><span data-stu-id="b2674-183">Text is displayed as</span></span>|<span data-ttu-id="b2674-184">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="b2674-184">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="b2674-185">Zwykły tekst</span><span class="sxs-lookup"><span data-stu-id="b2674-185">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="b2674-186">Tekst sformatowany</span><span class="sxs-lookup"><span data-stu-id="b2674-186">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="b2674-187">Ukryty tekst (znaki są maskowane)</span><span class="sxs-lookup"><span data-stu-id="b2674-187">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="b2674-188">Klasy, które zawierają tekst</span><span class="sxs-lookup"><span data-stu-id="b2674-188">Classes That Display Your Text</span></span>  
 <span data-ttu-id="b2674-189">Kilka klas może służyć do wyświetlania tekstu zwykłego lub sformatowany.</span><span class="sxs-lookup"><span data-stu-id="b2674-189">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="b2674-190">Można użyć <xref:System.Windows.Controls.TextBlock> do wyświetlenia niewielkich ilości tekstu.</span><span class="sxs-lookup"><span data-stu-id="b2674-190">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="b2674-191">Jeśli chcesz wyświetlić dużych ilości tekstu, użyj <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, lub <xref:System.Windows.Controls.FlowDocumentScrollViewer> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b2674-191">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="b2674-192"><xref:System.Windows.Controls.TextBlock> Ma dwie właściwości zawartości: <xref:System.Windows.Controls.TextBlock.Text%2A> i <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2674-192">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="b2674-193">Gdy ma być wyświetlany tekst, który używa spójne formatowanie <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość jest często najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="b2674-193">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="b2674-194">Jeśli planujesz użyć różnych formatowania przez cały tekst, użyj <xref:System.Windows.Controls.TextBlock.Inlines%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2674-194">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="b2674-195"><xref:System.Windows.Controls.TextBlock.Inlines%2A> Właściwość jest kolekcją <xref:System.Windows.Documents.Inline> obiektów, które określają sposób formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="b2674-195">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="b2674-196">W poniższej tabeli wymieniono właściwości zawartości dla <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer> klasy.</span><span class="sxs-lookup"><span data-stu-id="b2674-196">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="b2674-197">Formant</span><span class="sxs-lookup"><span data-stu-id="b2674-197">Control</span></span>|<span data-ttu-id="b2674-198">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="b2674-198">Content property</span></span>|<span data-ttu-id="b2674-199">Typ właściwości zawartości</span><span class="sxs-lookup"><span data-stu-id="b2674-199">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="b2674-200">dokument</span><span class="sxs-lookup"><span data-stu-id="b2674-200">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="b2674-201">dokument</span><span class="sxs-lookup"><span data-stu-id="b2674-201">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="b2674-202">dokument</span><span class="sxs-lookup"><span data-stu-id="b2674-202">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="b2674-203"><xref:System.Windows.Documents.FlowDocument> Implementuje <xref:System.Windows.Documents.IDocumentPaginatorSource> interfejsu; w związku z tym można wykonać wszystkie trzy klasy <xref:System.Windows.Documents.FlowDocument> jako zawartości.</span><span class="sxs-lookup"><span data-stu-id="b2674-203">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="b2674-204">Klasy, które formatowania tekstu</span><span class="sxs-lookup"><span data-stu-id="b2674-204">Classes That Format Your Text</span></span>  
 <span data-ttu-id="b2674-205"><xref:System.Windows.Documents.TextElement>oraz ich powiązanymi klasami umożliwiają formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="b2674-205"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="b2674-206"><xref:System.Windows.Documents.TextElement>obiekty zawierają i formatowanie tekstu w <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2674-206"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="b2674-207">Dwa typy podstawowe <xref:System.Windows.Documents.TextElement> obiekty są <xref:System.Windows.Documents.Block> elementów i <xref:System.Windows.Documents.Inline> elementy.</span><span class="sxs-lookup"><span data-stu-id="b2674-207">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="b2674-208">A <xref:System.Windows.Documents.Block> element reprezentuje blok tekstu, np. akapitu lub listy.</span><span class="sxs-lookup"><span data-stu-id="b2674-208">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="b2674-209"><xref:System.Windows.Documents.Inline> Element reprezentuje fragment tekstu w bloku.</span><span class="sxs-lookup"><span data-stu-id="b2674-209">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="b2674-210">Wiele <xref:System.Windows.Documents.Inline> klasy określ formatowanie tekstu, do której są stosowane.</span><span class="sxs-lookup"><span data-stu-id="b2674-210">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="b2674-211">Każdy <xref:System.Windows.Documents.TextElement> ma własną modelu zawartości.</span><span class="sxs-lookup"><span data-stu-id="b2674-211">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="b2674-212">Aby uzyskać więcej informacji, zobacz [omówienie modelu zawartości elementu TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b2674-212">For more information, see the [TextElement Content Model Overview](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2674-213">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2674-213">See Also</span></span>  
 [<span data-ttu-id="b2674-214">Zaawansowane</span><span class="sxs-lookup"><span data-stu-id="b2674-214">Advanced</span></span>](../../../../docs/framework/wpf/advanced/index.md)
