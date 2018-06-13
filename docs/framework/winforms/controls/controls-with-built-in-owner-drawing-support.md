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
ms.openlocfilehash: a5cbdc733a2f1cda3e708ceaae8604297f8da58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529250"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="51f27-102">Formanty z wbudowaną obsługą rysowania przez właściciela</span><span class="sxs-lookup"><span data-stu-id="51f27-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="51f27-103">Rysowanie w formularzach systemu Windows, który jest również nazywany Rysowanie niestandardowe, przez właściciela jest technika Zmienianie wyglądu niektórych formantów.</span><span class="sxs-lookup"><span data-stu-id="51f27-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51f27-104">Wyraz "control" w tym temacie służy oznacza klas pochodzących od albo <xref:System.Windows.Forms.Control> lub <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="51f27-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="51f27-105">Zazwyczaj systemu Windows obsługuje rysowania automatycznie przy użyciu ustawień właściwości, takie jak <xref:System.Windows.Forms.Control.BackColor%2A> ustalenie wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="51f27-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="51f27-106">Bez Rysowanie przez właściciela należy wykonać nad procesem rysowania Zmienianie wyglądu elementów, które nie są dostępne za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="51f27-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="51f27-107">Na przykład wiele formantów pozwalają na ustawienie kolor tekstu, która jest wyświetlana, ale jest ograniczone do pojedynczego koloru.</span><span class="sxs-lookup"><span data-stu-id="51f27-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="51f27-108">Rysowanie przez właściciela umożliwia wykonywanie czynności, takich jak wyświetlanie część tekstu w czarne i częściowo w red.</span><span class="sxs-lookup"><span data-stu-id="51f27-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="51f27-109">W praktyce Rysowanie przez właściciela jest podobny do rysowania grafiki na formularzu.</span><span class="sxs-lookup"><span data-stu-id="51f27-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="51f27-110">Na przykład można użyć metody grafiki w procedurze obsługi w formularzu <xref:System.Windows.Forms.Control.Paint> zdarzeń emulować `ListBox` sterowania, ale musi napisać własny kod do obsługi wszystkich interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="51f27-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="51f27-111">W przypadku Rysowanie przez właściciela formantu używa kodu do rysowania jego zawartość, ale w przeciwnym razie zachowuje jego możliwości wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="51f27-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="51f27-112">Metody grafiki służą do rysowania każdego elementu w formancie lub dostosować niektórych aspektów każdego elementu podczas korzystania z domyślnego wyglądu innych aspektów każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="51f27-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="51f27-113">Formanty formularzy rysunku właściciela w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="51f27-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="51f27-114">Aby wykonać właściciela rysowania formantów, które obsługują tę, będzie zwykle ustawić jedną właściwość i obsługi co najmniej jednego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="51f27-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="51f27-115">Większość formantów Rysowanie przez właściciela tego pomocy technicznej ma `OwnerDraw` lub `DrawMode` właściwość, która wskazuje, czy formant zgłosi jego związane z rysowaniem zdarzenie lub zdarzenia, gdy umożliwia malowanie, sama.</span><span class="sxs-lookup"><span data-stu-id="51f27-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="51f27-116">Formanty, które nie mają `OwnerDraw` lub `DrawMode` obejmują właściwości `DataGridView` kontroli, co zapewnia rysowania zdarzenia, które są wykonywane automatycznie, oraz `ToolStrip` formant, który jest rysowane przy użyciu klasy renderowania zewnętrznego, która ma własną zdarzenia związane z rysowaniem.</span><span class="sxs-lookup"><span data-stu-id="51f27-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="51f27-117">Istnieje wiele różnych rodzajów rysowania zdarzeń, ale występuje typowych zdarzeń rysowania, aby narysować pojedynczego elementu w formancie.</span><span class="sxs-lookup"><span data-stu-id="51f27-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="51f27-118">Program obsługi zdarzeń odbiera `EventArgs` obiekt, który zawiera informacje o elemencie rysowania i narzędzi można użyć do rysowania.</span><span class="sxs-lookup"><span data-stu-id="51f27-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="51f27-119">Na przykład ten obiekt zawiera zwykle numer indeksu elementu w obrębie swojej kolekcji nadrzędnej <xref:System.Drawing.Rectangle> który wskazuje element wyświetlany granice i <xref:System.Drawing.Graphics> obiektu do wywoływania metody malowania.</span><span class="sxs-lookup"><span data-stu-id="51f27-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="51f27-120">W przypadku niektórych zdarzeń `EventArgs` obiektu zawiera dodatkowe informacje na temat elementu, a metody wywołujące namalować niektóre aspekty elementu domyślnie, np. tło lub prostokąt fokusu.</span><span class="sxs-lookup"><span data-stu-id="51f27-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="51f27-121">Aby utworzyć formant wielokrotnego użytku, który zawiera dostosowania rysowanych przez właściciela, Utwórz nową klasę pochodzącą z klasy formantu, który obsługuje Rysowanie przez właściciela.</span><span class="sxs-lookup"><span data-stu-id="51f27-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="51f27-122">Zamiast Obsługa zdarzeń rysunku, należy uwzględnić swój kod rysowania przez właściciela w odpowiednie zastąpienia `On` *EventName* metod w nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="51f27-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="51f27-123">Upewnij się, że Wywołaj klasę bazową `On` *EventName* metod, w tym przypadku tak, aby użytkownicy formantu obsługi zdarzenia rysowania przez właściciela i zapewniają dodatkowe możliwości dostosowania.</span><span class="sxs-lookup"><span data-stu-id="51f27-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="51f27-124">Następujące formularzy systemu Windows formanty obsługi Rysowanie przez właściciela we wszystkich wersjach systemu .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="51f27-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <span data-ttu-id="51f27-125"><xref:System.Windows.Forms.MenuItem> (używane przez <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="51f27-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="51f27-126">Następujące formanty obsługuje tylko w Rysowanie przez właściciela [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="51f27-126">The following controls support owner drawing only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="51f27-127">Następujące sterowniki obsługują rysowanie przez właściciela i są nowe w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="51f27-127">The following controls support owner drawing and are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="51f27-128">Poniższe sekcje zawierają dodatkowe szczegóły dla każdego z tych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="51f27-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="51f27-129">Pole listy i formantów ComboBox</span><span class="sxs-lookup"><span data-stu-id="51f27-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="51f27-130"><xref:System.Windows.Forms.ListBox> i <xref:System.Windows.Forms.ComboBox> formanty umożliwiają rysowanie poszczególnych elementów w formancie wszystko w jednym rozmiaru lub w różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="51f27-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51f27-131">Mimo że <xref:System.Windows.Forms.CheckedListBox> kontroli jest pochodną <xref:System.Windows.Forms.ListBox> kontroli, nie obsługuje Rysowanie przez właściciela.</span><span class="sxs-lookup"><span data-stu-id="51f27-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="51f27-132">Aby narysować każdego elementu ten sam rozmiar, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> i obsługiwać `DrawItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51f27-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="51f27-133">Aby narysować każdego elementu przy użyciu innego rozmiaru, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> i obsługiwać oba `MeasureItem` i `DrawItem` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="51f27-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="51f27-134">`MeasureItem` Zdarzeń umożliwia wskazanie rozmiar elementu przed `DrawItem` zdarzenie dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="51f27-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="51f27-135">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="51f27-135">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [<span data-ttu-id="51f27-136">Instrukcje: tworzenie tekstu o zmiennym rozmiarze w kontrolce ComboBox</span><span class="sxs-lookup"><span data-stu-id="51f27-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="51f27-137">Składnik MenuItem</span><span class="sxs-lookup"><span data-stu-id="51f27-137">MenuItem Component</span></span>  
 <span data-ttu-id="51f27-138"><xref:System.Windows.Forms.MenuItem> Składnik reprezentuje pojedynczy element menu w <xref:System.Windows.Forms.MainMenu> lub <xref:System.Windows.Forms.ContextMenu> składnika.</span><span class="sxs-lookup"><span data-stu-id="51f27-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="51f27-139">Rysowanie <xref:System.Windows.Forms.MenuItem>, ustaw jej `OwnerDraw` właściwości `true` i obsługiwać jego `DrawItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51f27-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="51f27-140">Aby dostosować rozmiar elementu menu przed `DrawItem` wystąpi zdarzenie, obsługi elementu `MeasureItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51f27-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="51f27-141">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:</span><span class="sxs-lookup"><span data-stu-id="51f27-141">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="51f27-142">TabControl — Formant</span><span class="sxs-lookup"><span data-stu-id="51f27-142">TabControl Control</span></span>  
 <span data-ttu-id="51f27-143"><xref:System.Windows.Forms.TabControl> Kontroli umożliwia rysowanie poszczególnych kart w formancie.</span><span class="sxs-lookup"><span data-stu-id="51f27-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="51f27-144">Rysowanie przez właściciela dotyczy tylko karty; <xref:System.Windows.Forms.TabPage> nie ma wpływu na zawartość.</span><span class="sxs-lookup"><span data-stu-id="51f27-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="51f27-145">Rysowanie każdej karcie <xref:System.Windows.Forms.TabControl>ustaw `DrawMode` właściwości <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> i obsługiwać `DrawItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51f27-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="51f27-146">To zdarzenie wystąpi jeden raz dla każdej karty tylko wtedy, gdy karta jest widoczna w formancie.</span><span class="sxs-lookup"><span data-stu-id="51f27-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="51f27-147">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:</span><span class="sxs-lookup"><span data-stu-id="51f27-147">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="51f27-148">ToolTip — Składnik</span><span class="sxs-lookup"><span data-stu-id="51f27-148">ToolTip Component</span></span>  
 <span data-ttu-id="51f27-149"><xref:System.Windows.Forms.ToolTip> Składnika pozwala na pobieranie całego etykietka narzędzia, gdy pojawi się.</span><span class="sxs-lookup"><span data-stu-id="51f27-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="51f27-150">Rysowanie <xref:System.Windows.Forms.ToolTip>, ustaw jej `OwnerDraw` właściwości `true` i obsługiwać jego `Draw` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51f27-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="51f27-151">Aby dostosować rozmiar <xref:System.Windows.Forms.ToolTip> przed `Draw` wystąpi zdarzenie, obsługi `Popup` zdarzeń i zestaw <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> właściwości w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51f27-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="51f27-152">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:</span><span class="sxs-lookup"><span data-stu-id="51f27-152">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="51f27-153">ListView — Formant</span><span class="sxs-lookup"><span data-stu-id="51f27-153">ListView Control</span></span>  
 <span data-ttu-id="51f27-154"><xref:System.Windows.Forms.ListView> Kontroli umożliwia rysowanie poszczególnych elementów podrzędnych i nagłówków kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="51f27-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="51f27-155">Aby włączyć Rysowanie w formancie przez właściciela, należy ustawić `OwnerDraw` właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="51f27-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="51f27-156">Do rysowania każdego elementu w formancie, obsługi `DrawItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51f27-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="51f27-157">Do rysowania każdego podelementu lub nagłówek kolumny w formancie podczas <xref:System.Windows.Forms.ListView.View%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.View.Details>, obsługi `DrawSubItem` i `DrawColumnHeader` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="51f27-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="51f27-158">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:</span><span class="sxs-lookup"><span data-stu-id="51f27-158">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="51f27-159">TreeView — Kontrolka</span><span class="sxs-lookup"><span data-stu-id="51f27-159">TreeView Control</span></span>  
 <span data-ttu-id="51f27-160"><xref:System.Windows.Forms.TreeView> Kontroli umożliwia rysowanie poszczególne węzły w formancie.</span><span class="sxs-lookup"><span data-stu-id="51f27-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="51f27-161">Aby narysować tylko tekst wyświetlany w każdym węźle, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> i obsługiwać `DrawNode` zdarzeń pisania tekstu.</span><span class="sxs-lookup"><span data-stu-id="51f27-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="51f27-162">Aby narysować wszystkie elementy w każdym węźle, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> i obsługiwać `DrawNode` zdarzeń do rysowania niezależnie od elementy wymagane, takie jak tekstu, ikony, pola wyboru, plus lub minus znaków i linie łączące węzły.</span><span class="sxs-lookup"><span data-stu-id="51f27-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="51f27-163">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:</span><span class="sxs-lookup"><span data-stu-id="51f27-163">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="51f27-164">DataGridView — Formant</span><span class="sxs-lookup"><span data-stu-id="51f27-164">DataGridView Control</span></span>  
 <span data-ttu-id="51f27-165"><xref:System.Windows.Forms.DataGridView> Kontroli umożliwia rysowanie pojedynczych komórek i wierszy w formancie.</span><span class="sxs-lookup"><span data-stu-id="51f27-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="51f27-166">Rysowanie pojedynczych komórek, obsługi `CellPainting` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51f27-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="51f27-167">Rysowanie elementów wierszy lub poszczególnych wierszy, obsługiwać jeden lub oba `RowPrePaint` i `RowPostPaint` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="51f27-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="51f27-168">`RowPrePaint` Zdarzenie przed komórek w wierszu są rysowane i `RowPostPaint` zdarzenie po komórki są rysowane.</span><span class="sxs-lookup"><span data-stu-id="51f27-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="51f27-169">Może obsługiwać obu zdarzeń i `CellPainting` zdarzeń do rysowania tła wiersza, pojedynczych komórek i pierwszego wiersza oddzielnie, lub zapewniają specjalnego dostosowania, gdy potrzebne i użyć domyślnego wiersza innych elementów.</span><span class="sxs-lookup"><span data-stu-id="51f27-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="51f27-170">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="51f27-170">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [<span data-ttu-id="51f27-171">Instrukcje: dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51f27-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [<span data-ttu-id="51f27-172">Instrukcje: dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51f27-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="51f27-173">ToolStrip — Formant</span><span class="sxs-lookup"><span data-stu-id="51f27-173">ToolStrip Control</span></span>  
 <span data-ttu-id="51f27-174"><xref:System.Windows.Forms.ToolStrip> i formanty pochodne umożliwiają dostosowanie każdego aspektu wyglądu ich.</span><span class="sxs-lookup"><span data-stu-id="51f27-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="51f27-175">Zapewnienie niestandardowe renderowanie <xref:System.Windows.Forms.ToolStrip> formantów, ustaw `Renderer` właściwość <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, lub <xref:System.Windows.Forms.ToolStripContentPanel> do `ToolStripRenderer` obiektu i obsługi co najmniej jedną z wielu zdarzeń rysowania dostarczone przez `ToolStripRenderer` klasy.</span><span class="sxs-lookup"><span data-stu-id="51f27-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="51f27-176">Możesz również ustawić `Renderer` dla właściwości wystąpienia własne klasy pochodzące z `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, lub <xref:System.Windows.Forms.ToolStripSystemRenderer> implementuje lub przesłania określonych `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="51f27-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="51f27-177">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="51f27-177">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [<span data-ttu-id="51f27-178">Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51f27-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [<span data-ttu-id="51f27-179">Instrukcje: niestandardowy rysunek kontrolki ToolStrip</span><span class="sxs-lookup"><span data-stu-id="51f27-179">How to: Custom Draw a ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="51f27-180">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51f27-180">See Also</span></span>  
 [<span data-ttu-id="51f27-181">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51f27-181">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
