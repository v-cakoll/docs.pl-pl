---
title: 'Porady: uzyskiwanie dostępu do obiektów na liście rozwijanej DataGridViewComboBoxCell formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 2758841031be9ca9f0a5eb5e57165191d6870e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529405"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="4b5da-102">Porady: uzyskiwanie dostępu do obiektów na liście rozwijanej DataGridViewComboBoxCell formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4b5da-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="4b5da-103">Podobnie jak <xref:System.Windows.Forms.ComboBox> kontroli, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i <xref:System.Windows.Forms.DataGridViewComboBoxCell> typy umożliwiają dodanie dowolne obiekty do listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="4b5da-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="4b5da-104">W przypadku tej funkcji może reprezentować złożonych stany na liście rozwijanej bez konieczności przechowywania odpowiednimi obiektami w oddzielnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4b5da-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="4b5da-105">W odróżnieniu od <xref:System.Windows.Forms.ComboBox> kontroli, <xref:System.Windows.Forms.DataGridView> typy nie mają <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> właściwości pobierania obecnie wybranego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4b5da-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="4b5da-106">Zamiast tego należy ustawić <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> właściwości do nazwy właściwości na obiekt biznesowy.</span><span class="sxs-lookup"><span data-stu-id="4b5da-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="4b5da-107">Po dokonaniu wyboru wskazanej właściwości powiązania obiektu biznesowego ustawia komórki <xref:System.Windows.Forms.DataGridViewCell.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4b5da-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="4b5da-108">Można pobrać obiektu biznesowego przez wartość komórki `ValueMember` właściwości musi wskazywać właściwość, która zwraca odwołanie do samego obiektu biznesowego.</span><span class="sxs-lookup"><span data-stu-id="4b5da-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="4b5da-109">W związku z tym jeśli typ powiązania obiektu biznesowego nie jest pod kontrolą, należy dodać takie właściwości przez rozszerzenie typu za pomocą dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="4b5da-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="4b5da-110">Poniższe procedury pokazują, jak do wypełnienia listy rozwijanej z obiektów biznesowych i pobrać obiektów za pomocą komórki <xref:System.Windows.Forms.DataGridViewCell.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4b5da-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="4b5da-111">Aby dodać obiekty biznesowych do listy rozwijanej</span><span class="sxs-lookup"><span data-stu-id="4b5da-111">To add business objects to the drop-down list</span></span>  
  
1.  <span data-ttu-id="4b5da-112">Utwórz nową <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i wypełnić jego <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4b5da-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="4b5da-113">Alternatywnie, można ustawić kolumny <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> właściwości do kolekcji obiektów biznesowych.</span><span class="sxs-lookup"><span data-stu-id="4b5da-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="4b5da-114">W takim przypadku jednak nie można dodać "nieprzypisane" do listy rozwijanej bez tworzenia odpowiedniego obiektu biznesowego z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4b5da-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <span data-ttu-id="4b5da-115">Ustaw <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> i <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4b5da-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="4b5da-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> Wskazuje właściwość powiązania obiektu biznesowego do wyświetlenia na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="4b5da-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="4b5da-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> Wskazuje właściwość, która zwraca odwołanie do obiektu biznesowego.</span><span class="sxs-lookup"><span data-stu-id="4b5da-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  <span data-ttu-id="4b5da-118">Upewnij się, że danego typu obiektu biznesowa zawiera właściwość, która zwraca odwołanie do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4b5da-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="4b5da-119">Ta właściwość musi mieć nazwę z wartością przypisaną do <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="4b5da-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="4b5da-120">Pobiera obiekt obecnie biznesową</span><span class="sxs-lookup"><span data-stu-id="4b5da-120">To retrieve the currently selected business object</span></span>  
  
-   <span data-ttu-id="4b5da-121">Pobierz komórki <xref:System.Windows.Forms.DataGridViewCell.Value%2A> właściwości i rzutować go do typu obiektu biznesowego.</span><span class="sxs-lookup"><span data-stu-id="4b5da-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="4b5da-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b5da-122">Example</span></span>  
 <span data-ttu-id="4b5da-123">Pełny przykład ilustruje obiektów biznesowe na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="4b5da-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="4b5da-124">W tym przykładzie <xref:System.Windows.Forms.DataGridView> kontrolka jest powiązana z kolekcją `Task` obiektów.</span><span class="sxs-lookup"><span data-stu-id="4b5da-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="4b5da-125">Każdy `Task` obiekt ma `AssignedTo` właściwość, która wskazuje `Employee` obiektu aktualnie przypisane do tego zadania.</span><span class="sxs-lookup"><span data-stu-id="4b5da-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="4b5da-126">`Assigned To` Wyświetla kolumny `Name` przypisane wartości właściwości dla każdego pracownika lub, jeśli "nieprzypisane" `Task.AssignedTo` wartość właściwości jest `null`.</span><span class="sxs-lookup"><span data-stu-id="4b5da-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="4b5da-127">Aby wyświetlić zachowanie w tym przykładzie, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4b5da-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="4b5da-128">Zmienić przypisania w `Assigned To` kolumny, wybierając różne wartości z listy rozwijanej lub naciskając klawisz CTRL + 0 w komórce pola kombi.</span><span class="sxs-lookup"><span data-stu-id="4b5da-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2.  <span data-ttu-id="4b5da-129">Kliknij przycisk `Generate Report` Aby wyświetlić bieżące przypisania.</span><span class="sxs-lookup"><span data-stu-id="4b5da-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="4b5da-130">Oznacza to, że zmiana `Assigned To` kolumny automatycznie aktualizuje `tasks` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4b5da-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3.  <span data-ttu-id="4b5da-131">Kliknij przycisk `Request Status` przycisk, aby wywołać `RequestStatus` metody bieżącego `Employee` obiekt dla tego wiersza.</span><span class="sxs-lookup"><span data-stu-id="4b5da-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="4b5da-132">Oznacza to, że wybrany obiekt zostały pomyślnie pobrane.</span><span class="sxs-lookup"><span data-stu-id="4b5da-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b5da-133">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4b5da-133">Compiling the Code</span></span>  
 <span data-ttu-id="4b5da-134">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4b5da-134">This example requires:</span></span>  
  
-   <span data-ttu-id="4b5da-135">Odwołania do zestawów systemu i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="4b5da-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b5da-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b5da-136">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [<span data-ttu-id="4b5da-137">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b5da-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
