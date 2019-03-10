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
ms.openlocfilehash: 50f180f2f3fe825f617ae441906a7414a6b8bced
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707364"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="7a347-102">Formanty z wbudowaną obsługą rysowania przez właściciela</span><span class="sxs-lookup"><span data-stu-id="7a347-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="7a347-103">Rysowanie w formularzach Windows, który jest znany także jako rysowanie niestandardowe, przez właściciela to technika zmiany wyglądu niektórych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="7a347-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a347-104">Słowo "control", w tym temacie stosuje się do określenia klasy, które wynikają z poziomu <xref:System.Windows.Forms.Control> lub <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="7a347-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="7a347-105">Zazwyczaj Windows obsługuje malowania automatycznie przy użyciu ustawień właściwości, takie jak <xref:System.Windows.Forms.Control.BackColor%2A> w celu określenia wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="7a347-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="7a347-106">Za pomocą Rysowanie przez właściciela możesz przejąć proces rysowania zmiana elementami wyglądu, które nie są dostępne za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="7a347-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="7a347-107">Na przykład wiele kontrolek umożliwiają ustawianie koloru tekstu, która jest wyświetlana, ale są ograniczone do pojedynczego koloru.</span><span class="sxs-lookup"><span data-stu-id="7a347-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="7a347-108">Rysowanie przez właściciela umożliwia wykonywanie takich czynności, jak wyświetlić część tekstu w czarny i części w kolorze czerwonym.</span><span class="sxs-lookup"><span data-stu-id="7a347-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="7a347-109">W praktyce Rysowanie przez właściciela jest podobny do rysowania grafiki w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7a347-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="7a347-110">Na przykład można użyć metod graficznych w obsłudze w formularzu <xref:System.Windows.Forms.Control.Paint> zdarzenie, aby emulować `ListBox` kontroli, ale musi napisać własny kod do obsługi wszystkich interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="7a347-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="7a347-111">Za pomocą Rysowanie przez właściciela formant używa kodu, aby narysować jego zawartość, ale w przeciwnym razie zachowuje wszystkie jego funkcje wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="7a347-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="7a347-112">Narysuj każdy element w kontrolce lub dostosować niektóre aspekty każdego elementu, a domyślny wygląd innych aspektów każdego elementu, można użyć metody grafiki.</span><span class="sxs-lookup"><span data-stu-id="7a347-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="7a347-113">Rysowanie właściciela w Windows Forms kontrolek</span><span class="sxs-lookup"><span data-stu-id="7a347-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="7a347-114">Aby wykonać właściciela rysowania formantów, które go obsługują, będzie zwykle ustawić jedną właściwość i obsługę zdarzeń co najmniej jeden.</span><span class="sxs-lookup"><span data-stu-id="7a347-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="7a347-115">Większość formanty Rysowanie przez właściciela tej pomocy technicznej mają `OwnerDraw` lub `DrawMode` właściwość, która wskazuje, czy kontrolka zgłosi jego zdarzenia związane z rysowaniem lub zdarzenia podczas jego samego do malowania.</span><span class="sxs-lookup"><span data-stu-id="7a347-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="7a347-116">Formanty, które nie mają `OwnerDraw` lub `DrawMode` właściwość zawierać `DataGridView` formant, który udostępnia zdarzenia rysowania, które automatycznie są wykonywane, i `ToolStrip` formant, który jest rysowany przy użyciu klasy renderowania zewnętrznego, który ma swój własny zdarzenia związane z rysowaniem.</span><span class="sxs-lookup"><span data-stu-id="7a347-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="7a347-117">Istnieją różne rodzaje zdarzenia rysowania, ale występuje typowych zdarzeń rysowania, aby narysować pojedynczy element w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="7a347-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="7a347-118">Program obsługi zdarzeń odbierze `EventArgs` obiekt, który zawiera informacje na temat elementu, rysowania i narzędzi można użyć do rysowania.</span><span class="sxs-lookup"><span data-stu-id="7a347-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="7a347-119">Na przykład, ten obiekt zawiera zazwyczaj numer indeksu elementu w obrębie swojej kolekcji nadrzędnej <xref:System.Drawing.Rectangle> oznacza, że dla wybranego elementu wyświetlone granice, a <xref:System.Drawing.Graphics> obiekt do wywoływania metod malowania.</span><span class="sxs-lookup"><span data-stu-id="7a347-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="7a347-120">Niektóre zdarzenia `EventArgs` obiekt zawiera dodatkowe informacje na temat elementu a metody wywołujące do malowania niektóre aspekty elementu domyślnie, np. tło lub prostokąt fokusu.</span><span class="sxs-lookup"><span data-stu-id="7a347-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="7a347-121">Aby utworzyć formant wielokrotnego użytku, który zawiera dostosowania rysowanych przez właściciela, Utwórz nową klasę pochodzącą od klasy kontrolki, która obsługuje Rysowanie przez właściciela.</span><span class="sxs-lookup"><span data-stu-id="7a347-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="7a347-122">Zamiast obsługi zdarzenia rysowania, należy uwzględnić swój kod rysowania przez właściciela odpowiednie zastąpienia `On` *EventName* metodę lub metody w nowej klasie.</span><span class="sxs-lookup"><span data-stu-id="7a347-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="7a347-123">Upewnij się, że wywołanie klasy bazowej `On` *EventName* metodę lub metody w tym przypadku tak, aby użytkownicy kontrolki można obsługiwać zdarzenia rysowania przez właściciela i zapewnia dodatkowe możliwości dostosowania.</span><span class="sxs-lookup"><span data-stu-id="7a347-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="7a347-124">Następujące formy Windows kontrolki Rysowanie we wszystkich wersjach programu .NET Framework przez właściciela pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="7a347-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <span data-ttu-id="7a347-125"><xref:System.Windows.Forms.MenuItem> (używane przez <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="7a347-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="7a347-126">Następujące elementy sterujące obsługuje tylko Rysowanie przez właściciela [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7a347-126">The following controls support owner drawing only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="7a347-127">Następujące elementy sterujące obsługuje Rysowanie przez właściciela i są nowe w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7a347-127">The following controls support owner drawing and are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="7a347-128">Poniższe sekcje zawierają dodatkowe szczegóły dla każdego z tych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="7a347-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="7a347-129">Pola listy i kontrolki ComboBox</span><span class="sxs-lookup"><span data-stu-id="7a347-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="7a347-130"><xref:System.Windows.Forms.ListBox> i <xref:System.Windows.Forms.ComboBox> formanty umożliwiają narysuj poszczególnych elementów w kontrolce, wszystko w jedno rozwiązanie lub w różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="7a347-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a347-131">Mimo że <xref:System.Windows.Forms.CheckedListBox> kontroli jest tworzony na podstawie <xref:System.Windows.Forms.ListBox> control, nie obsługuje ona Rysowanie przez właściciela.</span><span class="sxs-lookup"><span data-stu-id="7a347-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="7a347-132">Aby narysować każdego elementu w taki sam rozmiar, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> i obsługiwać `DrawItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a347-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="7a347-133">Aby narysować każdego elementu przy użyciu innego rozmiaru, należy ustawić `DrawMode` właściwości <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> i obsługiwać oba modele `MeasureItem` i `DrawItem` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a347-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="7a347-134">`MeasureItem` Zdarzeń umożliwia wskazanie rozmiaru elementu przed `DrawItem` wystąpi zdarzenie dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="7a347-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="7a347-135">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="7a347-135">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [<span data-ttu-id="7a347-136">Instrukcje: Tworzenie tekstu o zmiennym rozmiarze w formancie ComboBox</span><span class="sxs-lookup"><span data-stu-id="7a347-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="7a347-137">Składnik element MenuItem</span><span class="sxs-lookup"><span data-stu-id="7a347-137">MenuItem Component</span></span>  
 <span data-ttu-id="7a347-138"><xref:System.Windows.Forms.MenuItem> Składnika reprezentuje pojedynczy element menu w <xref:System.Windows.Forms.MainMenu> lub <xref:System.Windows.Forms.ContextMenu> składnika.</span><span class="sxs-lookup"><span data-stu-id="7a347-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="7a347-139">Aby narysować <xref:System.Windows.Forms.MenuItem>ustaw jego `OwnerDraw` właściwości `true` i obsługiwać jego `DrawItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a347-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="7a347-140">Aby dostosować rozmiar elementu menu przed `DrawItem` wystąpi zdarzenie obsługi elementu `MeasureItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a347-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="7a347-141">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:</span><span class="sxs-lookup"><span data-stu-id="7a347-141">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="7a347-142">TabControl — Formant</span><span class="sxs-lookup"><span data-stu-id="7a347-142">TabControl Control</span></span>  
 <span data-ttu-id="7a347-143"><xref:System.Windows.Forms.TabControl> Control umożliwia rysowanie poszczególnych kart w formancie.</span><span class="sxs-lookup"><span data-stu-id="7a347-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="7a347-144">Rysowanie przez właściciela ma wpływ na kartach. <xref:System.Windows.Forms.TabPage> nie wpływają na zawartość.</span><span class="sxs-lookup"><span data-stu-id="7a347-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="7a347-145">Aby narysować każda karta w <xref:System.Windows.Forms.TabControl>ustaw `DrawMode` właściwości <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> i obsługiwać `DrawItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a347-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="7a347-146">To zdarzenie występuje jeden raz dla każdej karty, tylko wtedy, gdy karta jest widoczny w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="7a347-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="7a347-147">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:</span><span class="sxs-lookup"><span data-stu-id="7a347-147">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="7a347-148">ToolTip — Składnik</span><span class="sxs-lookup"><span data-stu-id="7a347-148">ToolTip Component</span></span>  
 <span data-ttu-id="7a347-149"><xref:System.Windows.Forms.ToolTip> Składnika umożliwia rysowania całego etykietki narzędzia, gdy jest on wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="7a347-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="7a347-150">Aby narysować <xref:System.Windows.Forms.ToolTip>ustaw jego `OwnerDraw` właściwości `true` i obsługiwać jego `Draw` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a347-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="7a347-151">Aby dostosować rozmiar <xref:System.Windows.Forms.ToolTip> przed `Draw` wystąpi zdarzenie, obsługi `Popup` zdarzeń i ustaw <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> właściwość w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a347-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="7a347-152">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:</span><span class="sxs-lookup"><span data-stu-id="7a347-152">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="7a347-153">ListView — Formant</span><span class="sxs-lookup"><span data-stu-id="7a347-153">ListView Control</span></span>  
 <span data-ttu-id="7a347-154"><xref:System.Windows.Forms.ListView> Control umożliwia rysowanie pojedynczych elementów podrzędnych i nagłówków kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="7a347-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="7a347-155">Aby włączyć Rysowanie w kontrolce przez właściciela, ustaw `OwnerDraw` właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="7a347-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="7a347-156">Aby narysować każdy element w kontrolce, obsługi `DrawItem` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a347-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="7a347-157">Aby narysować każdej podpozycji lub nagłówek kolumny w kontrolce po <xref:System.Windows.Forms.ListView.View%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.View.Details>, obsługi `DrawSubItem` i `DrawColumnHeader` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a347-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="7a347-158">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:</span><span class="sxs-lookup"><span data-stu-id="7a347-158">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="7a347-159">TreeView — Formant</span><span class="sxs-lookup"><span data-stu-id="7a347-159">TreeView Control</span></span>  
 <span data-ttu-id="7a347-160"><xref:System.Windows.Forms.TreeView> Control umożliwia rysowanie poszczególnych węzłów w formancie.</span><span class="sxs-lookup"><span data-stu-id="7a347-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="7a347-161">Aby narysować tylko tekstu wyświetlanego w każdym węźle, należy ustawić `DrawMode` właściwości <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> i obsługiwać `DrawNode` zdarzenie ma zostać narysowany tekst.</span><span class="sxs-lookup"><span data-stu-id="7a347-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="7a347-162">Aby narysować wszystkie elementy w każdym węźle, należy ustawić `DrawMode` właściwości <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> i obsługiwać `DrawNode` zdarzenie, aby rysować elementy, niezależnie od tego potrzebujesz, takie jak tekst, ikony, pola wyboru, plus lub minus znaków i linie, łączenie węzłów.</span><span class="sxs-lookup"><span data-stu-id="7a347-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="7a347-163">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:</span><span class="sxs-lookup"><span data-stu-id="7a347-163">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="7a347-164">DataGridView — Formant</span><span class="sxs-lookup"><span data-stu-id="7a347-164">DataGridView Control</span></span>  
 <span data-ttu-id="7a347-165"><xref:System.Windows.Forms.DataGridView> Control umożliwia rysowanie pojedynczych komórek i wierszy w formancie.</span><span class="sxs-lookup"><span data-stu-id="7a347-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="7a347-166">Aby narysować pojedyncze komórki, obsługi `CellPainting` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a347-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="7a347-167">Aby narysować poszczególne wiersze lub elementy wierszy, obsługiwać jeden lub oba `RowPrePaint` i `RowPostPaint` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a347-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="7a347-168">`RowPrePaint` Wystąpi zdarzenie przed komórki w wierszu są rysowane i `RowPostPaint` zdarzenie występuje po komórki są rysowane.</span><span class="sxs-lookup"><span data-stu-id="7a347-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="7a347-169">Może obsługiwać obu zdarzeń i `CellPainting` zdarzenia rysowania tła wiersza, pojedyncze komórki i pierwszego planu wiersz oddzielnie, lub może zapewnić specjalnego dostosowania, w którym ich potrzebują i użyj domyślnego wyświetlania innych elementów wiersza.</span><span class="sxs-lookup"><span data-stu-id="7a347-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="7a347-170">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="7a347-170">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [<span data-ttu-id="7a347-171">Instrukcje: Dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a347-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [<span data-ttu-id="7a347-172">Instrukcje: Dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a347-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="7a347-173">ToolStrip — Formant</span><span class="sxs-lookup"><span data-stu-id="7a347-173">ToolStrip Control</span></span>  
 <span data-ttu-id="7a347-174"><xref:System.Windows.Forms.ToolStrip> i formanty pochodne umożliwiają dostosowanie każdego aspektu wyglądu ich.</span><span class="sxs-lookup"><span data-stu-id="7a347-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="7a347-175">Zapewnienie niestandardowe renderowanie <xref:System.Windows.Forms.ToolStrip> formanty, ustawić `Renderer` właściwość <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, lub <xref:System.Windows.Forms.ToolStripContentPanel> do `ToolStripRenderer` obiektu i obsługi co najmniej jeden z wielu zdarzeń rysowania, dostarczone przez `ToolStripRenderer` klasy.</span><span class="sxs-lookup"><span data-stu-id="7a347-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="7a347-176">Także ustawić `Renderer` właściwości wystąpienia klasy własną pochodną `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, lub <xref:System.Windows.Forms.ToolStripSystemRenderer> , który implementuje lub przesłania określonych `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="7a347-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="7a347-177">Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="7a347-177">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [<span data-ttu-id="7a347-178">Instrukcje: Tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a347-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [<span data-ttu-id="7a347-179">Instrukcje: Rysowanie niestandardowego formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="7a347-179">How to: Custom Draw a ToolStrip Control</span></span>](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="7a347-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a347-180">See also</span></span>
- [<span data-ttu-id="7a347-181">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a347-181">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
