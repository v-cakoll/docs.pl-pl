---
title: Dostęp do obiektów na liście rozwijanej DataGridViewComboBoxCell
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 7e76ab1ac9089778e4371f4ee65b06d5ebc570bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746310"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="ccb6b-102">Porady: uzyskiwanie dostępu do obiektów na liście rozwijanej DataGridViewComboBoxCell formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ccb6b-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="ccb6b-103">Podobnie jak w przypadku kontrolki <xref:System.Windows.Forms.ComboBox>, typy <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i <xref:System.Windows.Forms.DataGridViewComboBoxCell> umożliwiają dodawanie dowolnych obiektów do ich list rozwijanych.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="ccb6b-104">Za pomocą tej funkcji można reprezentować złożone Stany na liście rozwijanej bez konieczności przechowywania odpowiednich obiektów w oddzielnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="ccb6b-105">W przeciwieństwie do kontrolki <xref:System.Windows.Forms.ComboBox> typy <xref:System.Windows.Forms.DataGridView> nie mają właściwości <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> do pobrania aktualnie zaznaczonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="ccb6b-106">Zamiast tego należy ustawić właściwość <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> na nazwę właściwości w obiekcie biznesowym.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="ccb6b-107">Gdy użytkownik dokonuje wyboru, wskazana właściwość obiektu biznesowego ustawia właściwość <xref:System.Windows.Forms.DataGridViewCell.Value%2A> komórki.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="ccb6b-108">Aby można było pobrać obiekt biznesowy za pomocą wartości komórki, właściwość `ValueMember` musi wskazywać właściwość, która zwraca odwołanie do obiektu biznesowego.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="ccb6b-109">W związku z tym, jeśli typ obiektu biznesowego nie znajduje się w kontrolce, należy dodać taką właściwość, rozszerzając typ przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="ccb6b-110">W poniższych procedurach pokazano, jak wypełnić listę rozwijaną z obiektami biznesowymi i pobrać obiekty za pomocą właściwości <xref:System.Windows.Forms.DataGridViewCell.Value%2A> komórki.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="ccb6b-111">Aby dodać obiekty biznesowe do listy rozwijanej</span><span class="sxs-lookup"><span data-stu-id="ccb6b-111">To add business objects to the drop-down list</span></span>  
  
1. <span data-ttu-id="ccb6b-112">Utwórz nowy <xref:System.Windows.Forms.DataGridViewComboBoxColumn> i wypełnij jego kolekcję <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="ccb6b-113">Alternatywnie możesz ustawić Właściwość Column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> na kolekcję obiektów biznes.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="ccb6b-114">W takim przypadku nie można jednak dodać "nieprzypisane" do listy rozwijanej bez tworzenia odpowiedniego obiektu biznesowego w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. <span data-ttu-id="ccb6b-115">Ustaw właściwości <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> i <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="ccb6b-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> wskazuje właściwość obiektu biznesowego do wyświetlenia na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="ccb6b-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> wskazuje właściwość, która zwraca odwołanie do obiektu biznesowego.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. <span data-ttu-id="ccb6b-118">Upewnij się, że typ obiektu biznesowego zawiera właściwość zwracającą odwołanie do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="ccb6b-119">Ta właściwość musi mieć nazwę z wartością przypisaną do <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="ccb6b-120">Aby pobrać aktualnie wybrany obiekt biznesowy</span><span class="sxs-lookup"><span data-stu-id="ccb6b-120">To retrieve the currently selected business object</span></span>  
  
- <span data-ttu-id="ccb6b-121">Pobierz Właściwość <xref:System.Windows.Forms.DataGridViewCell.Value%2A> komórki i przerzutj ją na typ obiektu biznesowego.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="ccb6b-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccb6b-122">Example</span></span>  
 <span data-ttu-id="ccb6b-123">Kompletny przykład ilustruje użycie obiektów biznesowych na liście rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="ccb6b-124">W przykładzie formant <xref:System.Windows.Forms.DataGridView> jest powiązany z kolekcją obiektów `Task`.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="ccb6b-125">Każdy obiekt `Task` ma właściwość `AssignedTo`, która wskazuje obiekt `Employee` aktualnie przypisany do tego zadania.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="ccb6b-126">Kolumna `Assigned To` wyświetla wartość właściwości `Name` dla każdego przypisanego pracownika lub "UNASSIGNED", jeśli wartość właściwości `Task.AssignedTo` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="ccb6b-127">Aby wyświetlić zachowanie tego przykładu, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ccb6b-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="ccb6b-128">Zmień przypisania w kolumnie `Assigned To`, wybierając różne wartości z listy rozwijanej lub naciskając kombinację klawiszy CTRL + 0 w komórce pola kombi.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2. <span data-ttu-id="ccb6b-129">Kliknij przycisk `Generate Report`, aby wyświetlić bieżące przypisania.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="ccb6b-130">Pokazuje to, że zmiana w kolumnie `Assigned To` automatycznie aktualizuje kolekcję `tasks`.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3. <span data-ttu-id="ccb6b-131">Kliknij przycisk `Request Status`, aby wywołać metodę `RequestStatus` bieżącego obiektu `Employee` dla tego wiersza.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="ccb6b-132">Pokazuje to, że wybrany obiekt został pomyślnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ccb6b-133">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ccb6b-133">Compiling the Code</span></span>  
 <span data-ttu-id="ccb6b-134">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ccb6b-134">This example requires:</span></span>  
  
- <span data-ttu-id="ccb6b-135">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="ccb6b-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb6b-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccb6b-136">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [<span data-ttu-id="ccb6b-137">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ccb6b-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
