---
title: DataGridView — Architektura formantu (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 81ac17c9f78baa71d005883c9dd928e398b10a33
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842346"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="214a1-102">DataGridView — Architektura formantu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="214a1-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="214a1-103"><xref:System.Windows.Forms.DataGridView> Kontroli oraz ich powiązanymi klasami, które są przeznaczone do elastyczny i rozszerzalny system do wyświetlania i edytowania danych tabelarycznych.</span><span class="sxs-lookup"><span data-stu-id="214a1-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="214a1-104">Te klasy są zawarte w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw, dlatego są nazywane z prefiksem "DataGridView".</span><span class="sxs-lookup"><span data-stu-id="214a1-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="214a1-105">Elementy architektury</span><span class="sxs-lookup"><span data-stu-id="214a1-105">Architecture Elements</span></span>  
 <span data-ttu-id="214a1-106">Podstawowy <xref:System.Windows.Forms.DataGridView> klasy pomocnika pochodzić od <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="214a1-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="214a1-107">Ilustruje następujące modelu obiektów <xref:System.Windows.Forms.DataGridViewElement> hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="214a1-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![Diagram przedstawiający hierarchii DataGridViewElement obiektu modelu.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="214a1-109"><xref:System.Windows.Forms.DataGridViewElement> Klasy zawiera odwołanie do elementu nadrzędnego <xref:System.Windows.Forms.DataGridView> kontroli i ma <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwość, która przechowuje wartość, która reprezentuje kombinację wartości z <xref:System.Windows.Forms.DataGridViewElementStates> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="214a1-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="214a1-110">W poniższych sekcjach opisano <xref:System.Windows.Forms.DataGridView> pomocnika klasy bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="214a1-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="214a1-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="214a1-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="214a1-112"><xref:System.Windows.Forms.DataGridViewElementStates> Wyliczenie zawiera następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="214a1-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="214a1-113">Wartości tego wyliczenia można łączyć z operatory logiczne bitowe, więc <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwości można wyrazić jednocześnie więcej niż jednego stanu.</span><span class="sxs-lookup"><span data-stu-id="214a1-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="214a1-114">Na przykład <xref:System.Windows.Forms.DataGridViewElement> mogą być jednocześnie <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, i <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="214a1-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="214a1-115">Komórki i paski</span><span class="sxs-lookup"><span data-stu-id="214a1-115">Cells and Bands</span></span>  
 <span data-ttu-id="214a1-116"><xref:System.Windows.Forms.DataGridView> Obejmuje dwa podstawowe rodzaje obiektów: komórek i grup.</span><span class="sxs-lookup"><span data-stu-id="214a1-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="214a1-117">Dziedziczyć wszystkie komórki <xref:System.Windows.Forms.DataGridViewCell> klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="214a1-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="214a1-118">Dwa rodzaje grup, <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewRow>, zarówno dziedziczyć <xref:System.Windows.Forms.DataGridViewBand> klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="214a1-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="214a1-119"><xref:System.Windows.Forms.DataGridView> Kontroli współdziała z kilku klas, ale są najczęściej spotykanych <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, i <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="214a1-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="214a1-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="214a1-120">DataGridViewCell</span></span>  
 <span data-ttu-id="214a1-121">Komórka jest podstawową jednostką interakcji dla <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="214a1-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="214a1-122">Wyświetlanie skupia się na komórki i wprowadzania danych często odbywa się za pośrednictwem komórek.</span><span class="sxs-lookup"><span data-stu-id="214a1-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="214a1-123">Dostęp do komórki za pomocą <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> zbiór <xref:System.Windows.Forms.DataGridViewRow> klasy, a dostęp zaznaczonych komórek przy użyciu <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> zbiór <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="214a1-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="214a1-124">Poniższy model obiektów ilustruje użycie tych i pokazuje <xref:System.Windows.Forms.DataGridViewCell> hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="214a1-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![Diagram przedstawiający hierarchii DataGridViewCell obiektu modelu.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="214a1-126"><xref:System.Windows.Forms.DataGridViewCell> Typ jest abstrakcyjna klasa bazowa, z której pochodzą wszystkie typy komórki.</span><span class="sxs-lookup"><span data-stu-id="214a1-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="214a1-127"><xref:System.Windows.Forms.DataGridViewCell> i jego typów pochodnych nie kontrolek formularzy Windows Forms, ale niektóre formanty Windows Forms hosta.</span><span class="sxs-lookup"><span data-stu-id="214a1-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="214a1-128">Żadnych funkcji dotyczących edytowania objęte komórki jest zazwyczaj obsługiwana przez kontrolkę hostowanej.</span><span class="sxs-lookup"><span data-stu-id="214a1-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="214a1-129"><xref:System.Windows.Forms.DataGridViewCell> obiekty nie mają kontroli nad ich wygląd i funkcje malowania w taki sam sposób jak kontrolek formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="214a1-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="214a1-130">Zamiast tego <xref:System.Windows.Forms.DataGridView> jest odpowiedzialny za wyglądu jego <xref:System.Windows.Forms.DataGridViewCell> obiektów.</span><span class="sxs-lookup"><span data-stu-id="214a1-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="214a1-131">Użytkownik może znacząco wpłynąć na wygląd i zachowanie komórek przez interakcję z <xref:System.Windows.Forms.DataGridView> właściwości i zdarzenia formantu.</span><span class="sxs-lookup"><span data-stu-id="214a1-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="214a1-132">Jeśli masz specjalne wymagania dotyczące dostosowań, które wykraczają poza możliwości <xref:System.Windows.Forms.DataGridView> kontrolki, można zaimplementować własną klasę pochodzącą od <xref:System.Windows.Forms.DataGridViewCell> lub jednej z jej klas podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="214a1-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="214a1-133">Na poniższej liście przedstawiono klasy pochodne od elementu <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="214a1-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   <span data-ttu-id="214a1-134">Komórka niestandardowych typów</span><span class="sxs-lookup"><span data-stu-id="214a1-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="214a1-135">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="214a1-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="214a1-136">Schemat <xref:System.Windows.Forms.DataGridView> kontrolki dołączonych danych magazynu danych jest wyrażona w <xref:System.Windows.Forms.DataGridView> kolumn formantu.</span><span class="sxs-lookup"><span data-stu-id="214a1-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="214a1-137">Możesz uzyskać dostęp <xref:System.Windows.Forms.DataGridView> kolumn do formantu za pomocą <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="214a1-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="214a1-138">Dostęp do wybranych kolumn przy użyciu <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="214a1-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="214a1-139">Poniższy model obiektów ilustruje użycie tych i pokazuje <xref:System.Windows.Forms.DataGridViewColumn> hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="214a1-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![Diagram przedstawiający hierarchia modeli obiektów DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="214a1-141">Niektóre typy kluczy komórki mają odpowiednie typy kolumn.</span><span class="sxs-lookup"><span data-stu-id="214a1-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="214a1-142">Te są uzyskiwane z <xref:System.Windows.Forms.DataGridViewColumn> klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="214a1-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="214a1-143">Na poniższej liście przedstawiono klasy pochodne od elementu <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="214a1-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="214a1-144">Typów kolumny niestandardowej</span><span class="sxs-lookup"><span data-stu-id="214a1-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="214a1-145">Formanty edycji DataGridView</span><span class="sxs-lookup"><span data-stu-id="214a1-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="214a1-146">Komórki, które zazwyczaj obsługują zaawansowane funkcje edycji, użyj obsługiwanego formantu, który pochodzi z kontrolki formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="214a1-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="214a1-147">Te kontrolki także implementować <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="214a1-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="214a1-148">Poniższy model obiektów ilustruje użycie tych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="214a1-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![Diagram przedstawiający hierarchii DataGridView Model obiektu.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="214a1-150">Następujące elementy sterujące edycji są dostarczane z <xref:System.Windows.Forms.DataGridView> sterowania:</span><span class="sxs-lookup"><span data-stu-id="214a1-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="214a1-151">Aby uzyskać informacje dotyczące tworzenia własnych do edycji kontrolek, zobacz [jak: Kontrolki hosta w formularzach Windows Forms komórkach DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="214a1-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="214a1-152">W poniższej tabeli przedstawiono relację między komórki typy, typy kolumn i formanty edycji.</span><span class="sxs-lookup"><span data-stu-id="214a1-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="214a1-153">Typ komórki</span><span class="sxs-lookup"><span data-stu-id="214a1-153">Cell type</span></span>|<span data-ttu-id="214a1-154">Obsługiwanego formantu</span><span class="sxs-lookup"><span data-stu-id="214a1-154">Hosted control</span></span>|<span data-ttu-id="214a1-155">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="214a1-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="214a1-156">n/d</span><span class="sxs-lookup"><span data-stu-id="214a1-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="214a1-157">n/d</span><span class="sxs-lookup"><span data-stu-id="214a1-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="214a1-158">n/d</span><span class="sxs-lookup"><span data-stu-id="214a1-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="214a1-159">n/d</span><span class="sxs-lookup"><span data-stu-id="214a1-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="214a1-160">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="214a1-160">DataGridViewRow</span></span>  
 <span data-ttu-id="214a1-161"><xref:System.Windows.Forms.DataGridViewRow> Klasy wyświetla rekord danych pola z danych przechowywania, do której <xref:System.Windows.Forms.DataGridView> związana jest kontrola.</span><span class="sxs-lookup"><span data-stu-id="214a1-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="214a1-162">Możesz uzyskać dostęp <xref:System.Windows.Forms.DataGridView> wierszy formantu za pomocą <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="214a1-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="214a1-163">Dostęp do wybranych wierszy przy użyciu <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="214a1-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="214a1-164">Poniższy model obiektów ilustruje użycie tych i pokazuje <xref:System.Windows.Forms.DataGridViewRow> hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="214a1-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![Diagram przedstawiający hierarchii DataGridViewRow obiektu modelu.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="214a1-166">Uzyskujesz własnych typów z <xref:System.Windows.Forms.DataGridViewRow> klasy, chociaż zazwyczaj nie będzie to konieczne.</span><span class="sxs-lookup"><span data-stu-id="214a1-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="214a1-167"><xref:System.Windows.Forms.DataGridView> Kontrolka ma kilka zdarzeń związanych z wierszy, jak i właściwości dostosowywania zachowania jego <xref:System.Windows.Forms.DataGridViewRow> obiektów.</span><span class="sxs-lookup"><span data-stu-id="214a1-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="214a1-168">Po włączeniu <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> właściwości specjalne wiersz awanie nowych wierszy jest wyświetlany jako ostatni wiersz.</span><span class="sxs-lookup"><span data-stu-id="214a1-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="214a1-169">Ten wiersz jest częścią <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji, ale ma specjalne funkcje, które mogą wymagać Twojej uwagi.</span><span class="sxs-lookup"><span data-stu-id="214a1-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="214a1-170">Aby uzyskać więcej informacji, zobacz [używanie wiersza dla nowych rekordów w formancie DataGridView formularzy Windows](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="214a1-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="214a1-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="214a1-171">See also</span></span>
- [<span data-ttu-id="214a1-172">DataGridView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="214a1-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="214a1-173">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="214a1-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="214a1-174">Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="214a1-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
