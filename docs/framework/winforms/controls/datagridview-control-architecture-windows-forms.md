---
title: DataGridView — Architektura formantu
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742529"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="763f1-102">DataGridView — Architektura formantu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="763f1-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="763f1-103">Formant <xref:System.Windows.Forms.DataGridView> i powiązane z nim klasy zostały zaprojektowane jako elastyczny, rozszerzalny system do wyświetlania i edytowania danych tabelarycznych.</span><span class="sxs-lookup"><span data-stu-id="763f1-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="763f1-104">Wszystkie te klasy są zawarte w przestrzeni nazw <xref:System.Windows.Forms?displayProperty=nameWithType> i są wszystkie nazwane z prefiksem "DataGridView".</span><span class="sxs-lookup"><span data-stu-id="763f1-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="763f1-105">Elementy architektury</span><span class="sxs-lookup"><span data-stu-id="763f1-105">Architecture Elements</span></span>  
 <span data-ttu-id="763f1-106">Klasy pomocnika podstawowego <xref:System.Windows.Forms.DataGridView> pochodzą z <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="763f1-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="763f1-107">Poniższy model obiektów ilustruje hierarchię dziedziczenia <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="763f1-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![Diagram przedstawiający hierarchię modeli obiektów DataGridViewelement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="763f1-109">Klasa <xref:System.Windows.Forms.DataGridViewElement> zawiera odwołanie do kontrolki nadrzędnej <xref:System.Windows.Forms.DataGridView> i ma właściwość <xref:System.Windows.Forms.DataGridViewElement.State%2A>, która przechowuje wartość, która reprezentuje kombinację wartości z wyliczenia <xref:System.Windows.Forms.DataGridViewElementStates>.</span><span class="sxs-lookup"><span data-stu-id="763f1-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="763f1-110">W poniższych sekcjach opisano klasy pomocnika <xref:System.Windows.Forms.DataGridView> bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="763f1-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="763f1-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="763f1-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="763f1-112">Wyliczenie <xref:System.Windows.Forms.DataGridViewElementStates> zawiera następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="763f1-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="763f1-113">Wartości tego wyliczenia można łączyć z bitowymi operatorami logicznymi, więc Właściwość <xref:System.Windows.Forms.DataGridViewElement.State%2A> może jawnie wyznaczać więcej niż jeden stan.</span><span class="sxs-lookup"><span data-stu-id="763f1-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="763f1-114">Na przykład <xref:System.Windows.Forms.DataGridViewElement> może być jednocześnie <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>i <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="763f1-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="763f1-115">Komórki i paski</span><span class="sxs-lookup"><span data-stu-id="763f1-115">Cells and Bands</span></span>  
 <span data-ttu-id="763f1-116">Formant <xref:System.Windows.Forms.DataGridView> składa się z dwóch podstawowych rodzajów obiektów: komórek i grup.</span><span class="sxs-lookup"><span data-stu-id="763f1-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="763f1-117">Wszystkie komórki pochodzą z klasy bazowej <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="763f1-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="763f1-118">Dwa rodzaje grup, <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewRow>, są pochodną od klasy bazowej <xref:System.Windows.Forms.DataGridViewBand>.</span><span class="sxs-lookup"><span data-stu-id="763f1-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="763f1-119">Formant <xref:System.Windows.Forms.DataGridView> współdziała z kilkoma klasami, ale najczęściej spotykane są <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>i <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="763f1-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="763f1-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="763f1-120">DataGridViewCell</span></span>  
 <span data-ttu-id="763f1-121">Komórka jest podstawową jednostką interakcji dla <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="763f1-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="763f1-122">Wyświetlacz jest wyśrodkowany w komórkach, a wpis danych jest często wykonywany za poorednictwem komórek.</span><span class="sxs-lookup"><span data-stu-id="763f1-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="763f1-123">Możesz uzyskać dostęp do komórek przy użyciu kolekcji <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> klasy <xref:System.Windows.Forms.DataGridViewRow> i można uzyskać dostęp do wybranych komórek przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="763f1-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="763f1-124">Poniższy model obiektów ilustruje to użycie i pokazuje hierarchię dziedziczenia <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="763f1-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![Diagram przedstawiający hierarchię modeli obiektów DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="763f1-126">Typ <xref:System.Windows.Forms.DataGridViewCell> jest abstrakcyjną klasą bazową, z której są wyprowadzane wszystkie typy komórek.</span><span class="sxs-lookup"><span data-stu-id="763f1-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="763f1-127"><xref:System.Windows.Forms.DataGridViewCell> i jego typy pochodne nie są Windows Forms kontrolkami, ale niektóre kontrolki Windows Forms hosta.</span><span class="sxs-lookup"><span data-stu-id="763f1-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="763f1-128">Wszystkie funkcje edycji obsługiwane przez komórkę są zwykle obsługiwane przez obsługiwaną kontrolę.</span><span class="sxs-lookup"><span data-stu-id="763f1-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="763f1-129">obiekty <xref:System.Windows.Forms.DataGridViewCell> nie kontrolują własnych funkcji wyglądu i malowania w taki sam sposób jak kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="763f1-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="763f1-130">Zamiast tego <xref:System.Windows.Forms.DataGridView> jest odpowiedzialny za wygląd obiektów <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="763f1-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="763f1-131">Możesz znacząco wpłynąć na wygląd i zachowanie komórek, współpracując z właściwościami i zdarzeniami kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="763f1-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="763f1-132">Jeśli istnieją specjalne wymagania dotyczące dostosowań, które wykraczają poza możliwości formantu <xref:System.Windows.Forms.DataGridView>, można zaimplementować własną klasę, która pochodzi od <xref:System.Windows.Forms.DataGridViewCell> lub jednej z jej klas podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="763f1-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="763f1-133">Na poniższej liście przedstawiono klasy pochodne <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="763f1-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- <span data-ttu-id="763f1-134">Niestandardowe typy komórek</span><span class="sxs-lookup"><span data-stu-id="763f1-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="763f1-135">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="763f1-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="763f1-136">Schemat dołączonego magazynu danych kontrolki <xref:System.Windows.Forms.DataGridView> jest wyrażony w kolumnach kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="763f1-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="763f1-137">Dostęp do kolumn kontrolki <xref:System.Windows.Forms.DataGridView> można uzyskać przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="763f1-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="763f1-138">Dostęp do wybranych kolumn można uzyskać przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="763f1-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="763f1-139">Poniższy model obiektów ilustruje to użycie i pokazuje hierarchię dziedziczenia <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="763f1-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![Diagram przedstawiający hierarchię modeli obiektów DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="763f1-141">Niektóre typy komórek klucza mają odpowiednie typy kolumn.</span><span class="sxs-lookup"><span data-stu-id="763f1-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="763f1-142">Są one uzyskiwane z klasy bazowej <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="763f1-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="763f1-143">Na poniższej liście przedstawiono klasy pochodne <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="763f1-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- <span data-ttu-id="763f1-144">Niestandardowe typy kolumn</span><span class="sxs-lookup"><span data-stu-id="763f1-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="763f1-145">Kontrolki edycji DataGridView</span><span class="sxs-lookup"><span data-stu-id="763f1-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="763f1-146">Komórki obsługujące zaawansowane funkcje edycji zwykle korzystają z hostowanej kontrolki, która jest pochodną formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="763f1-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="763f1-147">Te formanty również implementują interfejs <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="763f1-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="763f1-148">Poniższy model obiektów ilustruje użycie tych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="763f1-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![Diagram przedstawiający hierarchię modelu obiektów sterujących kontrolki DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="763f1-150">Następujące kontrolki edycji są dostępne z kontrolką <xref:System.Windows.Forms.DataGridView>:</span><span class="sxs-lookup"><span data-stu-id="763f1-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="763f1-151">Aby uzyskać informacje na temat tworzenia własnych kontrolek edycji, zobacz [How to: Host Controls in Windows Forms Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="763f1-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="763f1-152">W poniższej tabeli przedstawiono relacje między typami komórek, typami kolumn i kontrolkami edycji.</span><span class="sxs-lookup"><span data-stu-id="763f1-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="763f1-153">Typ komórki</span><span class="sxs-lookup"><span data-stu-id="763f1-153">Cell type</span></span>|<span data-ttu-id="763f1-154">Formant hostowany</span><span class="sxs-lookup"><span data-stu-id="763f1-154">Hosted control</span></span>|<span data-ttu-id="763f1-155">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="763f1-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="763f1-156">n/d</span><span class="sxs-lookup"><span data-stu-id="763f1-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="763f1-157">n/d</span><span class="sxs-lookup"><span data-stu-id="763f1-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="763f1-158">n/d</span><span class="sxs-lookup"><span data-stu-id="763f1-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="763f1-159">n/d</span><span class="sxs-lookup"><span data-stu-id="763f1-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="763f1-160">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="763f1-160">DataGridViewRow</span></span>  
 <span data-ttu-id="763f1-161">Klasa <xref:System.Windows.Forms.DataGridViewRow> wyświetla pola danych rekordu z magazynu danych, do którego jest dołączona kontrolka <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="763f1-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="763f1-162">Możesz uzyskać dostęp do wierszy kontrolki <xref:System.Windows.Forms.DataGridView> przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A>.</span><span class="sxs-lookup"><span data-stu-id="763f1-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="763f1-163">Możesz uzyskać dostęp do wybranych wierszy przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="763f1-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="763f1-164">Poniższy model obiektów ilustruje to użycie i pokazuje hierarchię dziedziczenia <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="763f1-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![Diagram przedstawiający hierarchię modeli obiektów DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="763f1-166">Można utworzyć własne typy z klasy <xref:System.Windows.Forms.DataGridViewRow>, chociaż zwykle nie jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="763f1-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="763f1-167">Kontrolka <xref:System.Windows.Forms.DataGridView> ma kilka zdarzeń związanych z wierszami i właściwości służące do dostosowywania zachowania obiektów <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="763f1-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="763f1-168">Jeśli włączysz Właściwość <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> kontrolki <xref:System.Windows.Forms.DataGridView>, w ostatnim wierszu zostanie wyświetlony specjalny wiersz służący do dodawania nowych wierszy.</span><span class="sxs-lookup"><span data-stu-id="763f1-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="763f1-169">Ten wiersz jest częścią kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A>, ale ma specjalne funkcje, które mogą wymagać Twojej uwagi.</span><span class="sxs-lookup"><span data-stu-id="763f1-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="763f1-170">Aby uzyskać więcej informacji, zobacz [używanie wiersza dla nowych rekordów w kontrolce DataGridView Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="763f1-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="763f1-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="763f1-171">See also</span></span>

- [<span data-ttu-id="763f1-172">DataGridView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="763f1-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="763f1-173">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="763f1-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="763f1-174">Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="763f1-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
