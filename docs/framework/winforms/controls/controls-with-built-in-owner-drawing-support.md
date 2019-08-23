---
title: Formanty z wbudowaną obsługą rysowania przez właściciela
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930193"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="0193b-102">Formanty z wbudowaną obsługą rysowania przez właściciela</span><span class="sxs-lookup"><span data-stu-id="0193b-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="0193b-103">Rysowanie przez właściciela w Windows Forms, który jest również znany jako rysunek niestandardowy, jest techniką zmiany wyglądu wizualizacji niektórych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="0193b-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0193b-104">Słowo "Control" w tym temacie służy do oznaczania klas, które pochodzą z albo <xref:System.Windows.Forms.Control> lub <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="0193b-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="0193b-105">Zwykle system Windows automatycznie obsługuje malowanie przy użyciu ustawień właściwości, <xref:System.Windows.Forms.Control.BackColor%2A> takich jak w celu określenia wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0193b-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="0193b-106">Przy użyciu rysowania przez właściciela można przetworzyć proces malowania, zmieniając elementy wyglądu, które nie są dostępne za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="0193b-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="0193b-107">Na przykład wiele kontrolek pozwala ustawić kolor wyświetlanego tekstu, ale jest ograniczony do jednego koloru.</span><span class="sxs-lookup"><span data-stu-id="0193b-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="0193b-108">Rysowanie przez właściciela umożliwia wykonywanie takich czynności jak wyświetlanie części tekstu w kolorze czarnym i w kolorze czerwonym.</span><span class="sxs-lookup"><span data-stu-id="0193b-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="0193b-109">W tym temacie rysowanie właściciela jest podobne do rysowania grafiki w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0193b-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="0193b-110">Na przykład można użyć metod graficznych w programie obsługi dla <xref:System.Windows.Forms.Control.Paint> zdarzenia formularza do emulowania `ListBox` kontrolki, ale trzeba napisać własny kod, aby obsłużyć wszystkie interakcje z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="0193b-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="0193b-111">Przy użyciu rysowania przez właściciela formant używa kodu do rysowania jego zawartości, ale w przeciwnym razie zachowuje wszystkie jego funkcje wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="0193b-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="0193b-112">Możesz użyć metod graficznych, aby narysować każdy element w kontrolce lub dostosować niektóre aspekty każdego elementu przy użyciu domyślnego wyglądu dla innych aspektów każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="0193b-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="0193b-113">Rysowanie przez właściciela w kontrolkach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0193b-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="0193b-114">Aby wykonać rysowanie przez właściciela w kontrolkach, które go obsługują, zwykle ustawiana jest jedna właściwość i obsłużą jedno lub więcej zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0193b-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="0193b-115">Większość formantów, które obsługują rysowanie właściciela, `OwnerDraw` ma `DrawMode` właściwość lub, która wskazuje, czy kontrolka będzie zgłaszać zdarzenia związane z rysunkiem, czy zdarzenia, gdy malują się one w sobie.</span><span class="sxs-lookup"><span data-stu-id="0193b-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="0193b-116">Kontrolki, które nie mają `OwnerDraw` właściwości `DrawMode` lub zawierają `DataGridView` kontrolkę, która umożliwia `ToolStrip` rysowanie zdarzeń, które są wykonywane automatycznie, i kontrolki, która jest rysowana przy użyciu zewnętrznej klasy renderowania, która ma własne zdarzenia związane ze rysowaniem.</span><span class="sxs-lookup"><span data-stu-id="0193b-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="0193b-117">Istnieje wiele różnych rodzajów zdarzeń rysowania, ale w celu narysowania pojedynczego elementu wewnątrz kontrolki występuje typowe zdarzenie rysowania.</span><span class="sxs-lookup"><span data-stu-id="0193b-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="0193b-118">Program obsługi zdarzeń odbiera `EventArgs` obiekt, który zawiera informacje o rysowanym elemencie i narzędziach, których można użyć do narysowania.</span><span class="sxs-lookup"><span data-stu-id="0193b-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="0193b-119">Na przykład ten obiekt zwykle zawiera numer indeksu elementu w obrębie jego kolekcji nadrzędnej, <xref:System.Drawing.Rectangle> który wskazuje granice wyświetlania elementu <xref:System.Drawing.Graphics> i obiekt do wywoływania metod malowania.</span><span class="sxs-lookup"><span data-stu-id="0193b-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="0193b-120">W przypadku niektórych zdarzeń `EventArgs` obiekt zawiera dodatkowe informacje na temat elementu i metod, które można wywołać w celu malowania niektórych aspektów elementu domyślnie, takich jak tło lub prostokąt fokusu.</span><span class="sxs-lookup"><span data-stu-id="0193b-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="0193b-121">Aby utworzyć kontrolkę wielokrotnego użytku, która zawiera dostosowania rysowane przez właściciela, Utwórz nową klasę pochodzącą z klasy kontrolki obsługującej rysowanie przez właściciela.</span><span class="sxs-lookup"><span data-stu-id="0193b-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="0193b-122">Zamiast obsłużyć zdarzenia rysowania, Uwzględnij swój kod rysowania przez właściciela w zastąpieniach `On`dla odpowiedniej metody lub metod *EventName* w nowej klasie.</span><span class="sxs-lookup"><span data-stu-id="0193b-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="0193b-123">Upewnij się, że w tym przypadku wywoływana `On`jest metoda lub metody klasy bazowej, tak aby użytkownicy Twojej kontrolki mogli obsłużyć zdarzenia rysowania przez właściciela i zapewnić dodatkowe dostosowanie.</span><span class="sxs-lookup"><span data-stu-id="0193b-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="0193b-124">Następujące kontrolki Windows Forms obsługują rysowanie właściciela we wszystkich wersjach .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0193b-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <span data-ttu-id="0193b-125"><xref:System.Windows.Forms.MenuItem>(używane przez <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="0193b-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
- <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="0193b-126">Poniższe kontrolki obsługują rysowanie właściciela tylko w .NET Framework 2,0:</span><span class="sxs-lookup"><span data-stu-id="0193b-126">The following controls support owner drawing only in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="0193b-127">Poniższe kontrolki obsługują rysowanie właściciela i są nowe w .NET Framework 2,0:</span><span class="sxs-lookup"><span data-stu-id="0193b-127">The following controls support owner drawing and are new in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="0193b-128">Poniższe sekcje zawierają dodatkowe szczegóły dla każdej z tych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="0193b-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="0193b-129">ListBox i ComboBox — formanty</span><span class="sxs-lookup"><span data-stu-id="0193b-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="0193b-130">Formanty <xref:System.Windows.Forms.ListBox> i<xref:System.Windows.Forms.ComboBox> umożliwiają rysowanie poszczególnych elementów w formancie albo w jednym rozmiarze, albo w różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="0193b-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0193b-131">Chociaż formant pochodzi <xref:System.Windows.Forms.ListBox> od kontrolki, nie obsługuje rysowania przez właściciela. <xref:System.Windows.Forms.CheckedListBox></span><span class="sxs-lookup"><span data-stu-id="0193b-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="0193b-132">Aby narysować każdy element o takim samym rozmiarze, `DrawMode` należy ustawić <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> właściwość na i `DrawItem` obsłużyć zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0193b-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="0193b-133">Aby narysować każdy element przy użyciu innego rozmiaru, należy `DrawMode` ustawić właściwość <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> na `DrawItem` i obsłużyć zarówno `MeasureItem` zdarzenie, jak i.</span><span class="sxs-lookup"><span data-stu-id="0193b-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="0193b-134">Zdarzenie umożliwia wskazanie rozmiaru elementu `DrawItem` przed wystąpieniem zdarzenia dla tego elementu. `MeasureItem`</span><span class="sxs-lookup"><span data-stu-id="0193b-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="0193b-135">Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="0193b-135">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [<span data-ttu-id="0193b-136">Instrukcje: Tworzenie tekstu o zmiennym rozmiarze w kontrolce ComboBox</span><span class="sxs-lookup"><span data-stu-id="0193b-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="0193b-137">MenuItem, składnik</span><span class="sxs-lookup"><span data-stu-id="0193b-137">MenuItem Component</span></span>  
 <span data-ttu-id="0193b-138">Składnik reprezentuje pojedynczy element menu <xref:System.Windows.Forms.MainMenu> w składniku lub <xref:System.Windows.Forms.ContextMenu>. <xref:System.Windows.Forms.MenuItem></span><span class="sxs-lookup"><span data-stu-id="0193b-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="0193b-139">Aby narysować <xref:System.Windows.Forms.MenuItem>, ustaw jej `OwnerDraw` właściwość na `true` i obsługuj jej `DrawItem` zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0193b-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="0193b-140">Aby dostosować rozmiar elementu menu przed `DrawItem` wystąpieniem zdarzenia, należy obsłużyć `MeasureItem` zdarzenie elementu.</span><span class="sxs-lookup"><span data-stu-id="0193b-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="0193b-141">Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:</span><span class="sxs-lookup"><span data-stu-id="0193b-141">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="0193b-142">TabControl — Formant</span><span class="sxs-lookup"><span data-stu-id="0193b-142">TabControl Control</span></span>  
 <span data-ttu-id="0193b-143"><xref:System.Windows.Forms.TabControl> Kontrolka umożliwia rysowanie poszczególnych kart w formancie.</span><span class="sxs-lookup"><span data-stu-id="0193b-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="0193b-144">Rysowanie właściciela dotyczy tylko kart; <xref:System.Windows.Forms.TabPage> zawartość nie jest modyfikowana.</span><span class="sxs-lookup"><span data-stu-id="0193b-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="0193b-145">Aby narysować każdą kartę w <xref:System.Windows.Forms.TabControl>, należy `DrawMode` ustawić `DrawItem` właściwość na <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> i obsłużyć zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0193b-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="0193b-146">To zdarzenie występuje raz dla każdej karty tylko wtedy, gdy karta jest widoczna w formancie.</span><span class="sxs-lookup"><span data-stu-id="0193b-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="0193b-147">Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:</span><span class="sxs-lookup"><span data-stu-id="0193b-147">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="0193b-148">ToolTip — Składnik</span><span class="sxs-lookup"><span data-stu-id="0193b-148">ToolTip Component</span></span>  
 <span data-ttu-id="0193b-149"><xref:System.Windows.Forms.ToolTip> Składnik umożliwia narysowanie całej etykietki narzędzia, gdy zostanie ona wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="0193b-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="0193b-150">Aby narysować <xref:System.Windows.Forms.ToolTip>, ustaw jej `OwnerDraw` właściwość na `true` i obsługuj jej `Draw` zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0193b-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="0193b-151">Aby <xref:System.Windows.Forms.ToolTip> dostosować rozmiar `Draw` przed wystąpieniem `Popup` zdarzenia, należy obsłużyć zdarzenie i ustawić <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> właściwość w programie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0193b-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="0193b-152">Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:</span><span class="sxs-lookup"><span data-stu-id="0193b-152">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="0193b-153">ListView — Formant</span><span class="sxs-lookup"><span data-stu-id="0193b-153">ListView Control</span></span>  
 <span data-ttu-id="0193b-154"><xref:System.Windows.Forms.ListView> Kontrolka umożliwia rysowanie poszczególnych elementów, podelementów i nagłówków kolumn w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="0193b-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="0193b-155">Aby włączyć rysowanie właściciela w kontrolce, ustaw `OwnerDraw` właściwość na. `true`</span><span class="sxs-lookup"><span data-stu-id="0193b-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="0193b-156">Aby narysować każdy element w kontrolce, obsłużyć `DrawItem` zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0193b-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="0193b-157">Aby narysować każdy nagłówek podelementu lub kolumny w kontrolce, gdy <xref:System.Windows.Forms.ListView.View%2A> właściwość jest ustawiona na `DrawSubItem` <xref:System.Windows.Forms.View.Details>, `DrawColumnHeader` obsłużyć zdarzenia i.</span><span class="sxs-lookup"><span data-stu-id="0193b-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="0193b-158">Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:</span><span class="sxs-lookup"><span data-stu-id="0193b-158">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="0193b-159">TreeView — Formant</span><span class="sxs-lookup"><span data-stu-id="0193b-159">TreeView Control</span></span>  
 <span data-ttu-id="0193b-160"><xref:System.Windows.Forms.TreeView> Kontrolka umożliwia rysowanie poszczególnych węzłów w formancie.</span><span class="sxs-lookup"><span data-stu-id="0193b-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="0193b-161">Aby narysować tylko tekst wyświetlany w każdym węźle, należy ustawić `DrawMode` właściwość na <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> i obsłużyć `DrawNode` zdarzenie do narysowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="0193b-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="0193b-162">Aby narysować wszystkie elementy każdego węzła, należy ustawić `DrawMode` właściwość na <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> i obsłużyć zdarzenie, aby rysować elementy, które są `DrawNode` potrzebne, takie jak tekst, ikony, pola wyboru, znaki plus i minus i linie łączące węzły.</span><span class="sxs-lookup"><span data-stu-id="0193b-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="0193b-163">Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:</span><span class="sxs-lookup"><span data-stu-id="0193b-163">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="0193b-164">DataGridView — Formant</span><span class="sxs-lookup"><span data-stu-id="0193b-164">DataGridView Control</span></span>  
 <span data-ttu-id="0193b-165"><xref:System.Windows.Forms.DataGridView> Kontrolka umożliwia rysowanie pojedynczych komórek i wierszy w formancie.</span><span class="sxs-lookup"><span data-stu-id="0193b-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="0193b-166">Aby narysować pojedyncze komórki, obsłuż `CellPainting` zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0193b-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="0193b-167">Aby narysować pojedyncze wiersze lub elementy wierszy, należy obsłużyć jedno lub `RowPrePaint` oba `RowPostPaint` zdarzenia i.</span><span class="sxs-lookup"><span data-stu-id="0193b-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="0193b-168">Zdarzenie występuje przed narysowaniem komórek w wierszu, `RowPostPaint` a zdarzenie występuje po narysowaniu komórek. `RowPrePaint`</span><span class="sxs-lookup"><span data-stu-id="0193b-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="0193b-169">Można obsługiwać zarówno zdarzenia, jak i `CellPainting` zdarzenia w celu oddzielenia tła wierszy, poszczególnych komórek i pierwszego planu wiersza, lub można podać konkretne dostosowania, gdy są potrzebne, i użyć domyślnego wyświetlania dla innych elementów wiersza.</span><span class="sxs-lookup"><span data-stu-id="0193b-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="0193b-170">Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="0193b-170">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [<span data-ttu-id="0193b-171">Instrukcje: Dostosowywanie wyglądu komórek w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0193b-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [<span data-ttu-id="0193b-172">Instrukcje: Dostosuj wygląd wierszy w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0193b-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="0193b-173">ToolStrip — Formant</span><span class="sxs-lookup"><span data-stu-id="0193b-173">ToolStrip Control</span></span>  
 <span data-ttu-id="0193b-174"><xref:System.Windows.Forms.ToolStrip>formanty pochodne umożliwiają dostosowanie dowolnego aspektu ich wyglądu.</span><span class="sxs-lookup"><span data-stu-id="0193b-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="0193b-175">Aby zapewnić niestandardowe renderowanie <xref:System.Windows.Forms.ToolStrip> formantów, należy `Renderer` ustawić właściwość <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, lub <xref:System.Windows.Forms.ToolStripContentPanel> na `ToolStripRenderer` obiekt i obsłużyć co najmniej jedno z wielu zdarzeń rysowania dostarczonych przez `ToolStripRenderer` Klasa.</span><span class="sxs-lookup"><span data-stu-id="0193b-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="0193b-176">Alternatywnie `Renderer` można ustawić właściwość na wystąpienie klasy pochodzącej od `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>lub <xref:System.Windows.Forms.ToolStripSystemRenderer> implementujące lub zastępujące określone `On`metody *EventName* .</span><span class="sxs-lookup"><span data-stu-id="0193b-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="0193b-177">Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="0193b-177">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [<span data-ttu-id="0193b-178">Instrukcje: Tworzenie i Ustawianie niestandardowego modułu renderowania dla formantu ToolStrip w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0193b-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [<span data-ttu-id="0193b-179">Instrukcje: Niestandardowe Rysowanie kontrolki ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0193b-179">How to: Custom Draw a ToolStrip Control</span></span>](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="0193b-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0193b-180">See also</span></span>

- [<span data-ttu-id="0193b-181">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0193b-181">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
