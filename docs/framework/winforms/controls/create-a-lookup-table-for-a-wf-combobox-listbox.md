---
title: 'Porady: tworzenie tabeli wyszukiwania dla formantów ComboBox, ListBox i CheckedListBox formularzy systemu Windows'
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
ms.openlocfilehash: 212cc229d8a496be11c84e30dbf3a0eedb952006
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529382"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="9dfc4-102">Porady: tworzenie tabeli wyszukiwania dla formantów ComboBox, ListBox i CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9dfc4-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="9dfc4-103">Czasami jest przydatne do wyświetlania danych w formacie przyjazną dla użytkownika na formularzu systemu Windows, ale przechowywania danych w formacie, który jest bardziej zrozumiałej do programu.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="9dfc4-104">Na przykład w formularzu zamówienia ds może być wyświetlany elementów menu według nazwy w polu listy.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="9dfc4-105">Jednak w tabeli danych rejestrowania kolejność może zawierać unikatowe numery identyfikacyjne reprezentujący żywności.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="9dfc4-106">W poniższej tabeli przedstawiono przykład sposobu przechowywania i wyświetlania danych formularza zamówienia ds.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="9dfc4-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="9dfc4-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="9dfc4-108">OrderID</span><span class="sxs-lookup"><span data-stu-id="9dfc4-108">OrderID</span></span>|<span data-ttu-id="9dfc4-109">Identyfikator elementu</span><span class="sxs-lookup"><span data-stu-id="9dfc4-109">ItemID</span></span>|<span data-ttu-id="9dfc4-110">Ilość</span><span class="sxs-lookup"><span data-stu-id="9dfc4-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="9dfc4-111">4085</span><span class="sxs-lookup"><span data-stu-id="9dfc4-111">4085</span></span>|<span data-ttu-id="9dfc4-112">12</span><span class="sxs-lookup"><span data-stu-id="9dfc4-112">12</span></span>|<span data-ttu-id="9dfc4-113">1</span><span class="sxs-lookup"><span data-stu-id="9dfc4-113">1</span></span>|  
|<span data-ttu-id="9dfc4-114">4086</span><span class="sxs-lookup"><span data-stu-id="9dfc4-114">4086</span></span>|<span data-ttu-id="9dfc4-115">13</span><span class="sxs-lookup"><span data-stu-id="9dfc4-115">13</span></span>|<span data-ttu-id="9dfc4-116">3</span><span class="sxs-lookup"><span data-stu-id="9dfc4-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="9dfc4-117">ItemTable</span><span class="sxs-lookup"><span data-stu-id="9dfc4-117">ItemTable</span></span>  
  
|<span data-ttu-id="9dfc4-118">ID</span><span class="sxs-lookup"><span data-stu-id="9dfc4-118">ID</span></span>|<span data-ttu-id="9dfc4-119">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9dfc4-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="9dfc4-120">12</span><span class="sxs-lookup"><span data-stu-id="9dfc4-120">12</span></span>|<span data-ttu-id="9dfc4-121">Ziemniaka</span><span class="sxs-lookup"><span data-stu-id="9dfc4-121">Potato</span></span>|  
|<span data-ttu-id="9dfc4-122">13</span><span class="sxs-lookup"><span data-stu-id="9dfc4-122">13</span></span>|<span data-ttu-id="9dfc4-123">Kurczaka</span><span class="sxs-lookup"><span data-stu-id="9dfc4-123">Chicken</span></span>|  
  
 <span data-ttu-id="9dfc4-124">W tym scenariuszu, w jednej tabeli, **OrderDetailsTable**, są przechowywane informacje dotyczy wyświetlanie i zapisywanie.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="9dfc4-125">Jednak aby zaoszczędzić miejsce, robi to w sposób dość one niezrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="9dfc4-126">Drugiej tabeli **ItemTable**, zawiera tylko informacje związane z wygląd o identyfikator, z którym odpowiada liczba, która nazwa żywności i nic o żywności rzeczywistej zleceń.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="9dfc4-127">**ItemTable** jest podłączony do <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, lub <xref:System.Windows.Forms.CheckedListBox> sterowanie za pośrednictwem trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="9dfc4-128">`DataSource` Właściwość zawiera nazwę tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="9dfc4-129">`DisplayMember` Właściwość zawiera kolumny danych tej tabeli, które mają być wyświetlane w formancie (nazwa żywności).</span><span class="sxs-lookup"><span data-stu-id="9dfc4-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="9dfc4-130">`ValueMember` Właściwość zawiera kolumny danych tej tabeli z przechowywanych informacji (numer identyfikacyjny).</span><span class="sxs-lookup"><span data-stu-id="9dfc4-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="9dfc4-131">**OrderDetailsTable** jest podłączony do formantu przez jego kolekcję powiązań, dostępne za pośrednictwem <xref:System.Windows.Forms.Control.DataBindings%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="9dfc4-132">Po dodaniu obiektu powiązania w kolekcji właściwości formantu nawiązywane określony element członkowski danych (kolumna identyfikatorów) w źródle danych ( **OrderDetailsTable**).</span><span class="sxs-lookup"><span data-stu-id="9dfc4-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="9dfc4-133">Po dokonaniu wyboru w formancie, ta tabela jest lokalizacji zapisywania danych wejściowych z formularza.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="9dfc4-134">Można utworzyć tabeli odnośników</span><span class="sxs-lookup"><span data-stu-id="9dfc4-134">To create a lookup table</span></span>  
  
1.  <span data-ttu-id="9dfc4-135">Dodaj <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, lub <xref:System.Windows.Forms.CheckedListBox> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2.  <span data-ttu-id="9dfc4-136">Połączenie ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-136">Connect to your data source.</span></span>  
  
3.  <span data-ttu-id="9dfc4-137">Należy ustanowić relację danych między dwiema tabelami.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="9dfc4-138">Zobacz [wprowadzenie do obiektów DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).</span><span class="sxs-lookup"><span data-stu-id="9dfc4-138">See [Introduction to DataRelation Objects](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).</span></span>  
  
4.  <span data-ttu-id="9dfc4-139">Ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-139">Set the following properties.</span></span> <span data-ttu-id="9dfc4-140">Można można ustawić w kodzie, lub w projektancie.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="9dfc4-141">Właściwość</span><span class="sxs-lookup"><span data-stu-id="9dfc4-141">Property</span></span>|<span data-ttu-id="9dfc4-142">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="9dfc4-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="9dfc4-143">Tabela, która zawiera informacje o identyfikator, z którym jest odpowiednikiem elementu numer.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="9dfc4-144">W poprzednim scenariuszu jest to `ItemTable`.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="9dfc4-145">Kolumna tabeli źródła danych, który ma być wyświetlany w formancie.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="9dfc4-146">W poprzednim scenariuszu jest to `"Name"` (można ustawić w kodzie, użyj cudzysłowów).</span><span class="sxs-lookup"><span data-stu-id="9dfc4-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="9dfc4-147">Kolumna tabeli źródła danych, który zawiera informacje przechowywane.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="9dfc4-148">W poprzednim scenariuszu jest to `"ID"` (można ustawić w kodzie, użyj cudzysłowów).</span><span class="sxs-lookup"><span data-stu-id="9dfc4-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5.  <span data-ttu-id="9dfc4-149">W procedurze, wywołaj <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody <xref:System.Windows.Forms.ControlBindingsCollection> klasy do wiązania kontrolki <xref:System.Windows.Forms.ListControl.SelectedValue%2A> właściwości do tabeli rejestrowania danych wejściowych z formularza.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="9dfc4-150">Możesz również to zrobić w Projektancie zamiast w kodzie, uzyskując dostęp do formantu <xref:System.Windows.Forms.Control.DataBindings%2A> właściwości w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="9dfc4-151">W poprzednim scenariuszu jest to `OrderDetailsTable`, a kolumna jest `"ItemID"`.</span><span class="sxs-lookup"><span data-stu-id="9dfc4-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9dfc4-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9dfc4-152">See Also</span></span>  
 [<span data-ttu-id="9dfc4-153">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9dfc4-153">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="9dfc4-154">ListBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="9dfc4-154">ListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="9dfc4-155">ComboBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="9dfc4-155">ComboBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [<span data-ttu-id="9dfc4-156">CheckedListBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="9dfc4-156">CheckedListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="9dfc4-157">Kontrolki formularzy Windows Forms używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="9dfc4-157">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
