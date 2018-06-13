---
title: DataGridView — Architektura formantu (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: a9fc1707b1691266d1844c411a08e7e8f35514ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529485"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="95fd1-102">DataGridView — Architektura formantu (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="95fd1-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="95fd1-103"><xref:System.Windows.Forms.DataGridView> Kontroli oraz ich powiązanymi klasami, które są zaprojektowane jako elastyczny i rozszerzalny system do wyświetlania i edytowania danych tabelarycznych.</span><span class="sxs-lookup"><span data-stu-id="95fd1-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="95fd1-104">Te klasy są zawarte w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw, a ich są nazywane z prefiksem "DataGridView".</span><span class="sxs-lookup"><span data-stu-id="95fd1-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="95fd1-105">Elementy architektury</span><span class="sxs-lookup"><span data-stu-id="95fd1-105">Architecture Elements</span></span>  
 <span data-ttu-id="95fd1-106">Podstawowy <xref:System.Windows.Forms.DataGridView> pochodną klasy Pomocnika <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="95fd1-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="95fd1-107">Przedstawiono w następujących modelu obiektów <xref:System.Windows.Forms.DataGridViewElement> hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="95fd1-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="95fd1-108">![Model obiektu DataGridViewElement](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span><span class="sxs-lookup"><span data-stu-id="95fd1-108">![DataGridViewElement Object Model](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span></span>  
<span data-ttu-id="95fd1-109">Model obiektu DataGridViewElement</span><span class="sxs-lookup"><span data-stu-id="95fd1-109">DataGridViewElement object model</span></span>  
  
 <span data-ttu-id="95fd1-110"><xref:System.Windows.Forms.DataGridViewElement> Klasy zawiera odwołanie do elementu nadrzędnego <xref:System.Windows.Forms.DataGridView> kontroli i ma <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwość, która zawiera wartość, która reprezentuje kombinację wartości z <xref:System.Windows.Forms.DataGridViewElementStates> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="95fd1-110">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="95fd1-111">W poniższych sekcjach opisano <xref:System.Windows.Forms.DataGridView> pomocniczy klasy bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="95fd1-111">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="95fd1-112">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="95fd1-112">DataGridViewElementStates</span></span>  
 <span data-ttu-id="95fd1-113"><xref:System.Windows.Forms.DataGridViewElementStates> Wyliczenie zawiera następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="95fd1-113">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="95fd1-114">Wartości tego wyliczenia można łączyć z bitowego operatorów logicznych, więc <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwości można wyrazić więcej niż jednego stanu na raz.</span><span class="sxs-lookup"><span data-stu-id="95fd1-114">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="95fd1-115">Na przykład <xref:System.Windows.Forms.DataGridViewElement> mogą być jednocześnie <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, i <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="95fd1-115">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="95fd1-116">Komórek i paski</span><span class="sxs-lookup"><span data-stu-id="95fd1-116">Cells and Bands</span></span>  
 <span data-ttu-id="95fd1-117"><xref:System.Windows.Forms.DataGridView> Kontroli składa się z dwóch podstawowych typów obiektów: komórek i grup.</span><span class="sxs-lookup"><span data-stu-id="95fd1-117">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="95fd1-118">Wszystkie komórki pochodzi od <xref:System.Windows.Forms.DataGridViewCell> klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="95fd1-118">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="95fd1-119">Dwa rodzaje grup, <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewRow>, zarówno pochodzi od <xref:System.Windows.Forms.DataGridViewBand> klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="95fd1-119">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="95fd1-120"><xref:System.Windows.Forms.DataGridView> Kontroli współdziała z kilku klas, ale są najczęściej spotykanych <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, i <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="95fd1-120">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="95fd1-121">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="95fd1-121">DataGridViewCell</span></span>  
 <span data-ttu-id="95fd1-122">Komórka jest podstawową jednostkę interakcji dla <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="95fd1-122">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="95fd1-123">Wyświetl skupia się na komórek i wprowadzania danych zwykle odbywa się za pośrednictwem komórek.</span><span class="sxs-lookup"><span data-stu-id="95fd1-123">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="95fd1-124">Dostęp do komórki za pomocą <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> zbiór <xref:System.Windows.Forms.DataGridViewRow> klasy, a mogą uzyskiwać dostęp do zaznaczonych komórek przy użyciu <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekcję <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="95fd1-124">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="95fd1-125">Następujące modelu obiektów przedstawiono użycia i przedstawia <xref:System.Windows.Forms.DataGridViewCell> hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="95fd1-125">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="95fd1-126">![Obiekt DataGridViewCell modelu](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span><span class="sxs-lookup"><span data-stu-id="95fd1-126">![DataGridViewCell Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span></span>  
<span data-ttu-id="95fd1-127">Model obiektu DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="95fd1-127">DataGridViewCell object model</span></span>  
  
 <span data-ttu-id="95fd1-128"><xref:System.Windows.Forms.DataGridViewCell> Typu jest abstrakcyjna klasa podstawowa, z którego pochodzi wszystkie typy komórki.</span><span class="sxs-lookup"><span data-stu-id="95fd1-128">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="95fd1-129"><xref:System.Windows.Forms.DataGridViewCell> i jego typów pochodnych nie są formanty formularzy systemu Windows, ale niektóre formanty formularzy systemu Windows hosta.</span><span class="sxs-lookup"><span data-stu-id="95fd1-129"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="95fd1-130">Wszystkie funkcje edytowania obsługiwane przez komórki jest zazwyczaj obsługiwane przez formant hostowanej.</span><span class="sxs-lookup"><span data-stu-id="95fd1-130">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="95fd1-131"><xref:System.Windows.Forms.DataGridViewCell> obiekty nie kontroli własnych wygląd i funkcje malowania w taki sam sposób jak formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95fd1-131"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="95fd1-132">Zamiast tego <xref:System.Windows.Forms.DataGridView> jest odpowiedzialny za wygląd jego <xref:System.Windows.Forms.DataGridViewCell> obiektów.</span><span class="sxs-lookup"><span data-stu-id="95fd1-132">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="95fd1-133">Użytkownik może znacząco wpłynąć na wygląd i zachowanie komórki za pomocą <xref:System.Windows.Forms.DataGridView> właściwości i zdarzeń formantu.</span><span class="sxs-lookup"><span data-stu-id="95fd1-133">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="95fd1-134">Jeśli masz specjalne wymagania dotyczące dostosowania, które są poza możliwościami <xref:System.Windows.Forms.DataGridView> sterowania, można zaimplementować własne klasy, która pochodzi z <xref:System.Windows.Forms.DataGridViewCell> lub jednej z jej klas podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="95fd1-134">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="95fd1-135">Poniższa lista zawiera klasy pochodne od <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="95fd1-135">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
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
  
-   <span data-ttu-id="95fd1-136">Z typów niestandardowych komórki</span><span class="sxs-lookup"><span data-stu-id="95fd1-136">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="95fd1-137">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="95fd1-137">DataGridViewColumn</span></span>  
 <span data-ttu-id="95fd1-138">Schemat <xref:System.Windows.Forms.DataGridView> magazynu dołączonych danych formantu jest wyrażona w <xref:System.Windows.Forms.DataGridView> kolumn formantu.</span><span class="sxs-lookup"><span data-stu-id="95fd1-138">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="95fd1-139">Dostęp można uzyskać <xref:System.Windows.Forms.DataGridView> kolumn formantu przy użyciu <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="95fd1-139">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="95fd1-140">Dostęp do wybranych kolumn za pomocą <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="95fd1-140">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="95fd1-141">Następujące modelu obiektów przedstawiono użycia i przedstawia <xref:System.Windows.Forms.DataGridViewColumn> hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="95fd1-141">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="95fd1-142">![Model obiektu DataGridViewColumn](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span><span class="sxs-lookup"><span data-stu-id="95fd1-142">![DataGridViewColumn Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span></span>  
<span data-ttu-id="95fd1-143">Model obiektu DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="95fd1-143">DataGridViewColumn object model</span></span>  
  
 <span data-ttu-id="95fd1-144">Niektóre typy komórka klucza mają odpowiednie typy kolumn.</span><span class="sxs-lookup"><span data-stu-id="95fd1-144">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="95fd1-145">Te pochodzą od <xref:System.Windows.Forms.DataGridViewColumn> klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="95fd1-145">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="95fd1-146">Poniższa lista zawiera klasy pochodne od <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="95fd1-146">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="95fd1-147">Z typów kolumn niestandardowych</span><span class="sxs-lookup"><span data-stu-id="95fd1-147">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="95fd1-148">Formanty edycji DataGridView</span><span class="sxs-lookup"><span data-stu-id="95fd1-148">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="95fd1-149">Komórki, które zwykle obsługuje zaawansowane funkcje edytowania Użyj hostowanej kontrolkę, która pochodzi z formantu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95fd1-149">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="95fd1-150">Formanty także implementować <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="95fd1-150">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="95fd1-151">Następujące model obiektów przedstawiono sposób użycia tych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="95fd1-151">The following object model illustrates the usage of these controls.</span></span>  
  
 <span data-ttu-id="95fd1-152">![Edytowania modelu obiektu formant DataGridView](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span><span class="sxs-lookup"><span data-stu-id="95fd1-152">![DataGridView Editing Control Object Model](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span></span>  
<span data-ttu-id="95fd1-153">Formant DataGridView edycji model obiektu</span><span class="sxs-lookup"><span data-stu-id="95fd1-153">DataGridView editing control object model</span></span>  
  
 <span data-ttu-id="95fd1-154">Następujące formantów edycji są dostarczane z <xref:System.Windows.Forms.DataGridView> sterowania:</span><span class="sxs-lookup"><span data-stu-id="95fd1-154">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="95fd1-155">Informacji o tworzeniu własnych edycji formantów, zobacz [porady: formanty hosta w komórkach DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="95fd1-155">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="95fd1-156">W poniższej tabeli przedstawiono relacje między formantów edycji komórki typów i typy kolumn.</span><span class="sxs-lookup"><span data-stu-id="95fd1-156">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="95fd1-157">Typ komórki</span><span class="sxs-lookup"><span data-stu-id="95fd1-157">Cell type</span></span>|<span data-ttu-id="95fd1-158">Obsługiwanego formantu</span><span class="sxs-lookup"><span data-stu-id="95fd1-158">Hosted control</span></span>|<span data-ttu-id="95fd1-159">Typ kolumny</span><span class="sxs-lookup"><span data-stu-id="95fd1-159">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="95fd1-160">n/d</span><span class="sxs-lookup"><span data-stu-id="95fd1-160">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="95fd1-161">n/d</span><span class="sxs-lookup"><span data-stu-id="95fd1-161">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="95fd1-162">n/d</span><span class="sxs-lookup"><span data-stu-id="95fd1-162">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="95fd1-163">n/d</span><span class="sxs-lookup"><span data-stu-id="95fd1-163">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="95fd1-164">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="95fd1-164">DataGridViewRow</span></span>  
 <span data-ttu-id="95fd1-165"><xref:System.Windows.Forms.DataGridViewRow> Pola rekordu danych z danych wyświetla klasy magazynu do której <xref:System.Windows.Forms.DataGridView> kontroli jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="95fd1-165">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="95fd1-166">Dostęp można uzyskać <xref:System.Windows.Forms.DataGridView> wierszy formantu przy użyciu <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="95fd1-166">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="95fd1-167">Dostęp do zaznaczonych wierszy za pomocą <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="95fd1-167">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="95fd1-168">Następujące modelu obiektów przedstawiono użycia i przedstawia <xref:System.Windows.Forms.DataGridViewRow> hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="95fd1-168">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="95fd1-169">![Model obiektu DataGridViewRow](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span><span class="sxs-lookup"><span data-stu-id="95fd1-169">![DataGridViewRow Object Model](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span></span>  
<span data-ttu-id="95fd1-170">Model obiektu DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="95fd1-170">DataGridViewRow object model</span></span>  
  
 <span data-ttu-id="95fd1-171">Mogą pochodzić własnych typów z <xref:System.Windows.Forms.DataGridViewRow> klasy, mimo że zwykle nie będzie to konieczne.</span><span class="sxs-lookup"><span data-stu-id="95fd1-171">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="95fd1-172"><xref:System.Windows.Forms.DataGridView> Formant ma kilka zdarzeń związanych z wiersza i właściwości dostosowywania zachowania jego <xref:System.Windows.Forms.DataGridViewRow> obiektów.</span><span class="sxs-lookup"><span data-stu-id="95fd1-172">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="95fd1-173">Po włączeniu <xref:System.Windows.Forms.DataGridView> formantu <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> właściwość specjalne wiersz dodawania nowych wierszy jest wyświetlana jako ostatni wiersz.</span><span class="sxs-lookup"><span data-stu-id="95fd1-173">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="95fd1-174">Ten wiersz jest częścią <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji, ale ma specjalne funkcje, które mogą wymagać Twojej uwagi.</span><span class="sxs-lookup"><span data-stu-id="95fd1-174">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="95fd1-175">Aby uzyskać więcej informacji, zobacz [używanie wiersza dla nowych rekordów w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="95fd1-175">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fd1-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95fd1-176">See Also</span></span>  
 [<span data-ttu-id="95fd1-177">DataGridView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="95fd1-177">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [<span data-ttu-id="95fd1-178">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95fd1-178">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="95fd1-179">Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95fd1-179">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
