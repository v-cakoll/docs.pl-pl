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
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187404"
---
# <a name="wpf-content-model"></a><span data-ttu-id="4ecd0-102">Model zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="4ecd0-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="4ecd0-103">to platforma prezentacji, która udostępnia wiele formantów i typów podobnych do kontroli, których głównym celem jest wyświetlanie różnych typów zawartości.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="4ecd0-104">Aby określić, który formant do użycia lub który formant pochodzi od, należy zrozumieć rodzaje obiektów określonego formantu najlepiej wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="4ecd0-105">W tym temacie podsumowano [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] model zawartości dla typów formantów i formantów.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="4ecd0-106">Model zawartości opisuje, jaka zawartość może być używana w formancie.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="4ecd0-107">W tym temacie wymieniono również właściwości zawartości dla każdego modelu zawartości.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="4ecd0-108">Właściwość content jest właściwością, która jest używana do przechowywania zawartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="4ecd0-109">Klasy, które zawierają dowolną zawartość</span><span class="sxs-lookup"><span data-stu-id="4ecd0-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="4ecd0-110">Niektóre formanty mogą zawierać obiekt dowolnego typu, <xref:System.DateTime> takich jak <xref:System.Windows.UIElement> ciąg, obiekt lub kontener dla dodatkowych elementów.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="4ecd0-111">Na przykład <xref:System.Windows.Controls.Button> może zawierać obraz i niektóre tekst; lub <xref:System.Windows.Controls.CheckBox> może zawierać wartość <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="4ecd0-112">ma cztery klasy, które mogą zawierać dowolną zawartość.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="4ecd0-113">W poniższej tabeli wymieniono <xref:System.Windows.Controls.Control>klasy, które dziedziczą po .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="4ecd0-114">Klasa zawierająca dowolną zawartość</span><span class="sxs-lookup"><span data-stu-id="4ecd0-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="4ecd0-115">Zawartość</span><span class="sxs-lookup"><span data-stu-id="4ecd0-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="4ecd0-116">Pojedynczy dowolny obiekt.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="4ecd0-117">Nagłówek i pojedynczy element, z których oba są dowolne obiekty.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="4ecd0-118">Kolekcja dowolnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="4ecd0-119">Nagłówek i kolekcja elementów, z których wszystkie są dowolne obiekty.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="4ecd0-120">Formanty, które dziedziczą z tych klas może zawierać ten sam typ zawartości i traktować zawartość w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="4ecd0-121">Na poniższej ilustracji przedstawiono jeden formant z każdego modelu zawartości, który zawiera obraz i tekst:</span><span class="sxs-lookup"><span data-stu-id="4ecd0-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Zrzut ekranu przedstawiający cztery różne kontrolki, po jednym z każdego modelu zawartości.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="4ecd0-123">Formanty zawierające pojedynczy dowolny obiekt</span><span class="sxs-lookup"><span data-stu-id="4ecd0-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="4ecd0-124">Klasa <xref:System.Windows.Controls.ContentControl> zawiera pojedynczy fragment dowolnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="4ecd0-125">Jego właściwość <xref:System.Windows.Controls.ContentControl.Content%2A>zawartości jest .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="4ecd0-126">Następujące formanty <xref:System.Windows.Controls.ContentControl> dziedziczą z jego modelu zawartości i używają go:</span><span class="sxs-lookup"><span data-stu-id="4ecd0-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="4ecd0-127">Na poniższej ilustracji <xref:System.Windows.Controls.ContentControl.Content%2A> przedstawiono cztery przyciski, <xref:System.Windows.Shapes.Rectangle>których jest <xref:System.Windows.Controls.Panel> ustawiony <xref:System.Windows.Shapes.Ellipse> na <xref:System.Windows.Controls.TextBlock>ciąg, <xref:System.DateTime> obiekt, , i , który zawiera i a :</span><span class="sxs-lookup"><span data-stu-id="4ecd0-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Zrzut ekranu przedstawiający cztery przyciski z różnymi typami zawartości.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="4ecd0-129">Na przykład jak ustawić <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość, <xref:System.Windows.Controls.ContentControl>zobacz .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="4ecd0-130">Formanty zawierające nagłówek i pojedynczy dowolny obiekt</span><span class="sxs-lookup"><span data-stu-id="4ecd0-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="4ecd0-131">Klasa <xref:System.Windows.Controls.HeaderedContentControl> dziedziczy <xref:System.Windows.Controls.ContentControl> i wyświetla zawartość z nagłówkiem.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="4ecd0-132"><xref:System.Windows.Controls.ContentControl.Content%2A>Dziedziczy właściwość zawartości, <xref:System.Windows.Controls.ContentControl> z i <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> definiuje właściwość, <xref:System.Object>która jest typu; w związku z tym oba mogą być dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="4ecd0-133">Następujące formanty <xref:System.Windows.Controls.HeaderedContentControl> dziedziczą z jego modelu zawartości i używają go:</span><span class="sxs-lookup"><span data-stu-id="4ecd0-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="4ecd0-134">Na poniższej <xref:System.Windows.Controls.TabItem> ilustracji przedstawiono dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="4ecd0-135">Pierwszy <xref:System.Windows.Controls.TabItem> ma <xref:System.Windows.UIElement> obiekty <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> jako <xref:System.Windows.Controls.ContentControl.Content%2A>i .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="4ecd0-136">Jest <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ustawiona <xref:System.Windows.Controls.StackPanel> na a, który zawiera <xref:System.Windows.Shapes.Ellipse> i . <xref:System.Windows.Controls.TextBlock></span><span class="sxs-lookup"><span data-stu-id="4ecd0-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="4ecd0-137">Jest <xref:System.Windows.Controls.ContentControl.Content%2A> ustawiona <xref:System.Windows.Controls.StackPanel> na a, który zawiera i <xref:System.Windows.Controls.TextBlock> . <xref:System.Windows.Controls.Label></span><span class="sxs-lookup"><span data-stu-id="4ecd0-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="4ecd0-138">Drugi <xref:System.Windows.Controls.TabItem> ma ciąg w <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![TabControl, który używa różnych typów w Header właściwości.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="4ecd0-140">Aby uzyskać przykład tworzenia <xref:System.Windows.Controls.TabItem> obiektów, <xref:System.Windows.Controls.HeaderedContentControl>zobacz .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="4ecd0-141">Formanty zawierające kolekcję dowolnych obiektów</span><span class="sxs-lookup"><span data-stu-id="4ecd0-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="4ecd0-142">Klasa <xref:System.Windows.Controls.ItemsControl> dziedziczy <xref:System.Windows.Controls.Control> i może zawierać wiele elementów, takich jak ciągi, obiekty lub inne elementy.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="4ecd0-143">Jego właściwości zawartości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A>są i .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="4ecd0-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>jest zwykle używany do wypełniania <xref:System.Windows.Controls.ItemsControl> z kolekcji danych.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="4ecd0-145">Jeśli nie chcesz używać kolekcji do wypełniania <xref:System.Windows.Controls.ItemsControl>programu , można <xref:System.Windows.Controls.ItemsControl.Items%2A> dodać elementy przy użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="4ecd0-146">Następujące formanty <xref:System.Windows.Controls.ItemsControl> dziedziczą z jego modelu zawartości i używają go:</span><span class="sxs-lookup"><span data-stu-id="4ecd0-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="4ecd0-147">Na poniższej <xref:System.Windows.Controls.ListBox> ilustracji przedstawiono element zawierający następujące typy elementów:</span><span class="sxs-lookup"><span data-stu-id="4ecd0-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="4ecd0-148">Ciąg.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-148">A string.</span></span>  
  
- <span data-ttu-id="4ecd0-149">Obiekt <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="4ecd0-150">Klasa <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="4ecd0-151">A, <xref:System.Windows.Controls.Panel> który <xref:System.Windows.Shapes.Ellipse> zawiera <xref:System.Windows.Controls.TextBlock>i .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Zrzut ekranu przedstawiający ListBox z czterema typami zawartości.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="4ecd0-153">Formanty zawierające nagłówek i zbiór dowolnych obiektów</span><span class="sxs-lookup"><span data-stu-id="4ecd0-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="4ecd0-154">Klasa <xref:System.Windows.Controls.HeaderedItemsControl> dziedziczy <xref:System.Windows.Controls.ItemsControl> i może zawierać wiele elementów, takich jak ciągi, obiekty lub inne elementy i nagłówek.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="4ecd0-155">Dziedziczy właściwości <xref:System.Windows.Controls.ItemsControl> zawartości i <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, <xref:System.Windows.Controls.ItemsControl.Items%2A>i definiuje <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwość, która może być dowolny obiekt.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="4ecd0-156">Następujące formanty <xref:System.Windows.Controls.HeaderedItemsControl> dziedziczą z jego modelu zawartości i używają go:</span><span class="sxs-lookup"><span data-stu-id="4ecd0-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="4ecd0-157">Klasy, które zawierają kolekcję obiektów UIElement</span><span class="sxs-lookup"><span data-stu-id="4ecd0-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="4ecd0-158">Klasa <xref:System.Windows.Controls.Panel> umieszcza i rozmieszcza obiekty podrzędne. <xref:System.Windows.UIElement></span><span class="sxs-lookup"><span data-stu-id="4ecd0-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="4ecd0-159">Jego właściwość <xref:System.Windows.Controls.Panel.Children%2A>zawartości jest .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="4ecd0-160">Następujące klasy dziedziczą <xref:System.Windows.Controls.Panel> z klasy i używają jej modelu zawartości:</span><span class="sxs-lookup"><span data-stu-id="4ecd0-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="4ecd0-161">Aby uzyskać więcej informacji, zobacz [Omówienie paneli](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4ecd0-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="4ecd0-162">Klasy, które wpływają na wygląd UIElement</span><span class="sxs-lookup"><span data-stu-id="4ecd0-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="4ecd0-163">Klasa <xref:System.Windows.Controls.Decorator> stosuje efekty wizualne na lub <xref:System.Windows.UIElement>wokół jednego dziecka .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="4ecd0-164">Jego właściwość <xref:System.Windows.Controls.Decorator.Child%2A>zawartości jest .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="4ecd0-165">Następujące klasy dziedziczą z <xref:System.Windows.Controls.Decorator> jego modelu zawartości i używają go:</span><span class="sxs-lookup"><span data-stu-id="4ecd0-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="4ecd0-166">Na poniższej <xref:System.Windows.Controls.TextBox> ilustracji przedstawiono, że <xref:System.Windows.Controls.Border> ma (jest ozdobiony) wokół niego.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="4ecd0-167">![TextBox z czarnym obramowaniem](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="4ecd0-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="4ecd0-168">TextBlock z obramowaniem</span><span class="sxs-lookup"><span data-stu-id="4ecd0-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="4ecd0-169">Klasy, które zapewniają wizualną opinię o UIElement</span><span class="sxs-lookup"><span data-stu-id="4ecd0-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="4ecd0-170">Klasa <xref:System.Windows.Documents.Adorner> zawiera wizualne wskazówki dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="4ecd0-171">Na przykład <xref:System.Windows.Documents.Adorner> użyj, aby dodać dojścia funkcjonalne do elementów lub podać informacje o stanie formantu.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="4ecd0-172">Klasa <xref:System.Windows.Documents.Adorner> zapewnia strukturę, dzięki czemu można utworzyć własne adorners.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="4ecd0-173">nie zapewnia żadnych wdrożonych adorners.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="4ecd0-174">Aby uzyskać więcej informacji, zobacz [Adorners Overview](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4ecd0-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="4ecd0-175">Klasy, które umożliwiają użytkownikom wprowadzanie tekstu</span><span class="sxs-lookup"><span data-stu-id="4ecd0-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="4ecd0-176">WPF WPF zapewnia trzy podstawowe formanty, które umożliwiają użytkownikom wprowadzanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="4ecd0-177">Każdy formant wyświetla tekst w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-177">Each control displays the text differently.</span></span> <span data-ttu-id="4ecd0-178">W poniższej tabeli wymieniono te trzy formanty związane z tekstem, ich możliwości podczas wyświetlania tekstu i ich właściwości, które zawierają tekst formantu.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="4ecd0-179">Kontrola</span><span class="sxs-lookup"><span data-stu-id="4ecd0-179">Control</span></span>|<span data-ttu-id="4ecd0-180">Tekst jest wyświetlany jako</span><span class="sxs-lookup"><span data-stu-id="4ecd0-180">Text is displayed as</span></span>|<span data-ttu-id="4ecd0-181">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="4ecd0-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="4ecd0-182">Zwykły tekst</span><span class="sxs-lookup"><span data-stu-id="4ecd0-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="4ecd0-183">Sformatowany tekst</span><span class="sxs-lookup"><span data-stu-id="4ecd0-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="4ecd0-184">Ukryty tekst (znaki są maskowane)</span><span class="sxs-lookup"><span data-stu-id="4ecd0-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a><span data-ttu-id="4ecd0-185">Klasy, które wyświetlają twój tekst</span><span class="sxs-lookup"><span data-stu-id="4ecd0-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="4ecd0-186">Kilka klas może służyć do wyświetlania zwykłego lub sformatowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="4ecd0-187">Można użyć <xref:System.Windows.Controls.TextBlock> do wyświetlania niewielkich ilości tekstu.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="4ecd0-188">Jeśli chcesz wyświetlić duże ilości tekstu, <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer>użyj <xref:System.Windows.Controls.FlowDocumentScrollViewer> przycisku , lub formantów.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="4ecd0-189">Ma <xref:System.Windows.Controls.TextBlock> dwie właściwości <xref:System.Windows.Controls.TextBlock.Text%2A> zawartości: <xref:System.Windows.Controls.TextBlock.Inlines%2A>i .</span><span class="sxs-lookup"><span data-stu-id="4ecd0-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="4ecd0-190">Jeśli chcesz wyświetlić tekst, który używa <xref:System.Windows.Controls.TextBlock.Text%2A> spójnego formatowania, właściwość jest często najlepszym wyborem.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="4ecd0-191">Jeśli planujesz używać innego formatowania w całym <xref:System.Windows.Controls.TextBlock.Inlines%2A> tekście, użyj właściwości.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="4ecd0-192">Właściwość <xref:System.Windows.Controls.TextBlock.Inlines%2A> jest kolekcją <xref:System.Windows.Documents.Inline> obiektów, które określają sposób formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="4ecd0-193">W poniższej tabeli <xref:System.Windows.Controls.FlowDocumentReader>wymieniono właściwość zawartości dla , <xref:System.Windows.Controls.FlowDocumentPageViewer>i <xref:System.Windows.Controls.FlowDocumentScrollViewer> klasy.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="4ecd0-194">Kontrola</span><span class="sxs-lookup"><span data-stu-id="4ecd0-194">Control</span></span>|<span data-ttu-id="4ecd0-195">Właściwość zawartości</span><span class="sxs-lookup"><span data-stu-id="4ecd0-195">Content property</span></span>|<span data-ttu-id="4ecd0-196">Typ właściwości zawartości</span><span class="sxs-lookup"><span data-stu-id="4ecd0-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="4ecd0-197">Dokument</span><span class="sxs-lookup"><span data-stu-id="4ecd0-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="4ecd0-198">Dokument</span><span class="sxs-lookup"><span data-stu-id="4ecd0-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="4ecd0-199">Dokument</span><span class="sxs-lookup"><span data-stu-id="4ecd0-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="4ecd0-200">Implementuje <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.IDocumentPaginatorSource> interfejs; w związku z tym wszystkie <xref:System.Windows.Documents.FlowDocument> trzy klasy mogą przyjmować jako zawartość.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a><span data-ttu-id="4ecd0-201">Klasy, które formatuje tekst</span><span class="sxs-lookup"><span data-stu-id="4ecd0-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="4ecd0-202"><xref:System.Windows.Documents.TextElement>i powiązane z nim klasy umożliwiają formatowanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="4ecd0-203"><xref:System.Windows.Documents.TextElement>obiekty zawierają i <xref:System.Windows.Controls.TextBlock> formatuje tekst w i <xref:System.Windows.Documents.FlowDocument> obiekty.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="4ecd0-204">Dwa podstawowe typy <xref:System.Windows.Documents.TextElement> <xref:System.Windows.Documents.Block> obiektów <xref:System.Windows.Documents.Inline> są elementami i elementami.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="4ecd0-205">Element <xref:System.Windows.Documents.Block> reprezentuje blok tekstu, taki jak akapit lub lista.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="4ecd0-206">Element <xref:System.Windows.Documents.Inline> reprezentuje część tekstu w bloku.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="4ecd0-207">Wiele <xref:System.Windows.Documents.Inline> klas określa formatowanie tekstu, do którego są stosowane.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="4ecd0-208">Każdy <xref:System.Windows.Documents.TextElement> ma swój własny model zawartości.</span><span class="sxs-lookup"><span data-stu-id="4ecd0-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="4ecd0-209">Aby uzyskać więcej informacji, zobacz [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4ecd0-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ecd0-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ecd0-210">See also</span></span>

- [<span data-ttu-id="4ecd0-211">Zaawansowane</span><span class="sxs-lookup"><span data-stu-id="4ecd0-211">Advanced</span></span>](../advanced/index.md)
