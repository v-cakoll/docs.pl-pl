---
title: Tworzenie tabeli odnośników dla kontrolki ComboBox, ListBox lub CheckedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737370"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="cf758-102">Porady: tworzenie tabeli wyszukiwania dla formantów ComboBox, ListBox i CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cf758-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="cf758-103">Czasami warto wyświetlać dane w formacie przyjaznym dla użytkownika w formularzu systemu Windows, ale przechowywać dane w formacie, który jest bardziej zrozumiały dla programu.</span><span class="sxs-lookup"><span data-stu-id="cf758-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="cf758-104">Na przykład formularz zamówienia dla żywności może wyświetlać elementy menu według nazwy w polu listy.</span><span class="sxs-lookup"><span data-stu-id="cf758-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="cf758-105">Jednak tabela danych, która rejestruje zamówienie, będzie zawierać unikatowe numery IDENTYFIKACYJNe reprezentujące żywność.</span><span class="sxs-lookup"><span data-stu-id="cf758-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="cf758-106">W poniższych tabelach przedstawiono przykład przechowywania i wyświetlania danych formularza zamówienia dla żywności.</span><span class="sxs-lookup"><span data-stu-id="cf758-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="cf758-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="cf758-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="cf758-108">Wartooć</span><span class="sxs-lookup"><span data-stu-id="cf758-108">OrderID</span></span>|<span data-ttu-id="cf758-109">Elementów</span><span class="sxs-lookup"><span data-stu-id="cf758-109">ItemID</span></span>|<span data-ttu-id="cf758-110">Zagregowan</span><span class="sxs-lookup"><span data-stu-id="cf758-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="cf758-111">4085</span><span class="sxs-lookup"><span data-stu-id="cf758-111">4085</span></span>|<span data-ttu-id="cf758-112">12</span><span class="sxs-lookup"><span data-stu-id="cf758-112">12</span></span>|<span data-ttu-id="cf758-113">1</span><span class="sxs-lookup"><span data-stu-id="cf758-113">1</span></span>|  
|<span data-ttu-id="cf758-114">4086</span><span class="sxs-lookup"><span data-stu-id="cf758-114">4086</span></span>|<span data-ttu-id="cf758-115">13</span><span class="sxs-lookup"><span data-stu-id="cf758-115">13</span></span>|<span data-ttu-id="cf758-116">3</span><span class="sxs-lookup"><span data-stu-id="cf758-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="cf758-117">Element</span><span class="sxs-lookup"><span data-stu-id="cf758-117">ItemTable</span></span>  
  
|<span data-ttu-id="cf758-118">ID</span><span class="sxs-lookup"><span data-stu-id="cf758-118">ID</span></span>|<span data-ttu-id="cf758-119">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cf758-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="cf758-120">12</span><span class="sxs-lookup"><span data-stu-id="cf758-120">12</span></span>|<span data-ttu-id="cf758-121">Ziemniaczan</span><span class="sxs-lookup"><span data-stu-id="cf758-121">Potato</span></span>|  
|<span data-ttu-id="cf758-122">13</span><span class="sxs-lookup"><span data-stu-id="cf758-122">13</span></span>|<span data-ttu-id="cf758-123">Kury</span><span class="sxs-lookup"><span data-stu-id="cf758-123">Chicken</span></span>|  
  
 <span data-ttu-id="cf758-124">W tym scenariuszu w jednej tabeli, **OrderDetailsTable**przechowywane są rzeczywiste informacje, które są potrzebne do wyświetlania i zapisywania.</span><span class="sxs-lookup"><span data-stu-id="cf758-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="cf758-125">Jednak aby zaoszczędzić miejsce, robi to w dość tajemnicze sposób.</span><span class="sxs-lookup"><span data-stu-id="cf758-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="cf758-126">Druga tabela, **element Items**, zawiera tylko informacje dotyczące wyglądu, na których numer identyfikacyjny jest równoważny z nazwą żywności, a nic nie dotyczy rzeczywistych zamówień żywności.</span><span class="sxs-lookup"><span data-stu-id="cf758-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="cf758-127">**Element Item** jest połączony z <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>lub kontroli <xref:System.Windows.Forms.CheckedListBox> przez trzy właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf758-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="cf758-128">Właściwość `DataSource` zawiera nazwę tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="cf758-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="cf758-129">Właściwość `DisplayMember` zawiera kolumnę danych tej tabeli, która ma być wyświetlana w formancie (nazwa żywności).</span><span class="sxs-lookup"><span data-stu-id="cf758-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="cf758-130">Właściwość `ValueMember` zawiera kolumnę danych tej tabeli zawierającą przechowywane informacje (numer IDENTYFIKACYJNy).</span><span class="sxs-lookup"><span data-stu-id="cf758-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="cf758-131">**OrderDetailsTable** jest połączona z kontrolką przez kolekcję powiązań, do której można uzyskać dostęp za pomocą właściwości <xref:System.Windows.Forms.Control.DataBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf758-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="cf758-132">Po dodaniu obiektu powiązania do kolekcji, należy połączyć właściwość kontrolki z określonym członkiem danych (kolumna numerów IDENTYFIKACYJNych) w źródle danych ( **OrderDetailsTable**).</span><span class="sxs-lookup"><span data-stu-id="cf758-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="cf758-133">Po dokonaniu wyboru w kontrolce, w tej tabeli jest zapisywane dane wejściowe formularza.</span><span class="sxs-lookup"><span data-stu-id="cf758-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="cf758-134">Aby utworzyć tabelę odnośników</span><span class="sxs-lookup"><span data-stu-id="cf758-134">To create a lookup table</span></span>  
  
1. <span data-ttu-id="cf758-135">Dodaj kontrolkę <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>lub <xref:System.Windows.Forms.CheckedListBox> do formularza.</span><span class="sxs-lookup"><span data-stu-id="cf758-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2. <span data-ttu-id="cf758-136">Nawiąż połączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="cf758-136">Connect to your data source.</span></span>  
  
3. <span data-ttu-id="cf758-137">Ustanów relację danych między dwiema tabelami.</span><span class="sxs-lookup"><span data-stu-id="cf758-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="cf758-138">Zobacz [wprowadzenie do obiektów DataRelations](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="cf758-138">See [Introduction to DataRelation Objects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span></span>  
  
4. <span data-ttu-id="cf758-139">Ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf758-139">Set the following properties.</span></span> <span data-ttu-id="cf758-140">Można je ustawić w kodzie lub w projektancie.</span><span class="sxs-lookup"><span data-stu-id="cf758-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="cf758-141">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cf758-141">Property</span></span>|<span data-ttu-id="cf758-142">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="cf758-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="cf758-143">Tabela zawierająca informacje o IDENTYFIKATORze odpowiadającym elementowi.</span><span class="sxs-lookup"><span data-stu-id="cf758-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="cf758-144">W poprzednim scenariuszu jest to `ItemTable`.</span><span class="sxs-lookup"><span data-stu-id="cf758-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="cf758-145">Kolumna tabeli źródła danych, która ma być wyświetlana w formancie.</span><span class="sxs-lookup"><span data-stu-id="cf758-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="cf758-146">W poprzednim scenariuszu jest to `"Name"` (aby ustawić w kodzie, używać cudzysłowów).</span><span class="sxs-lookup"><span data-stu-id="cf758-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="cf758-147">Kolumna tabeli źródła danych zawierająca przechowywane informacje.</span><span class="sxs-lookup"><span data-stu-id="cf758-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="cf758-148">W poprzednim scenariuszu jest to `"ID"` (aby ustawić w kodzie, używać cudzysłowów).</span><span class="sxs-lookup"><span data-stu-id="cf758-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5. <span data-ttu-id="cf758-149">W procedurze należy wywołać metodę <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> klasy <xref:System.Windows.Forms.ControlBindingsCollection>, aby powiązać Właściwość <xref:System.Windows.Forms.ListControl.SelectedValue%2A> kontrolki z tabelą, która rejestruje dane wejściowe formularza.</span><span class="sxs-lookup"><span data-stu-id="cf758-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="cf758-150">Można to również zrobić w projektancie zamiast w kodzie, uzyskując dostęp do właściwości <xref:System.Windows.Forms.Control.DataBindings%2A> formantu w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="cf758-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="cf758-151">W poprzednim scenariuszu jest `OrderDetailsTable`, a kolumna jest `"ItemID"`.</span><span class="sxs-lookup"><span data-stu-id="cf758-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cf758-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf758-152">See also</span></span>

- [<span data-ttu-id="cf758-153">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf758-153">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="cf758-154">ListBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="cf758-154">ListBox Control Overview</span></span>](listbox-control-overview-windows-forms.md)
- [<span data-ttu-id="cf758-155">ComboBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="cf758-155">ComboBox Control Overview</span></span>](combobox-control-overview-windows-forms.md)
- [<span data-ttu-id="cf758-156">CheckedListBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="cf758-156">CheckedListBox Control Overview</span></span>](checkedlistbox-control-overview-windows-forms.md)
- [<span data-ttu-id="cf758-157">Kontrolki formularzy Windows Forms używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="cf758-157">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
