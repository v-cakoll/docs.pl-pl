---
title: 'Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: 9e803b6450fb8c9ade4adde5bf98fb1c3c62c861
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971278"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1f3f8-102">Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1f3f8-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1f3f8-103">Obsługa błędów z źródłowy magazyn danych jest wymagana funkcja dla aplikacji wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="1f3f8-104">Formularze Windows <xref:System.Windows.Forms.DataGridView> kontroli ułatwia to dzięki uwidocznieniu działania <xref:System.Windows.Forms.DataGridView.DataError> zdarzenie, które jest wywoływane, gdy magazyn danych wykryje naruszenie ograniczenia lub reguła biznesowa przerwane.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>  
  
 <span data-ttu-id="1f3f8-105">W tym instruktażu będą pobierać wiersze z `Customers` tabeli w bazie danych Northwind i wyświetlaj je w <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1f3f8-106">Gdy duplikat `CustomerID` niewykrycia wartości w nowym wierszu lub edytowane istniejącego wiersza, <xref:System.Windows.Forms.DataGridView.DataError> wystąpi zdarzenie, który będzie obsługiwany przez wyświetlenie <xref:System.Windows.Forms.MessageBox> opisujący wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>  
  
 <span data-ttu-id="1f3f8-107">Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Obsługa błędów występujących podczas wprowadzania danych w Windows formantu DataGridView formularzy](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1f3f8-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1f3f8-108">Prerequisites</span></span>  
 <span data-ttu-id="1f3f8-109">Aby ukończyć ten przewodnik, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="1f3f8-109">In order to complete this walkthrough, you will need:</span></span>  
  
- <span data-ttu-id="1f3f8-110">Dostęp do serwera z przykładowej bazy danych Northwind programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-110">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="1f3f8-111">Tworzenie formularza</span><span class="sxs-lookup"><span data-stu-id="1f3f8-111">Creating the Form</span></span>  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="1f3f8-112">Aby obsługiwać błędy wprowadzania danych w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f3f8-112">To handle data-entry errors in the DataGridView control</span></span>  
  
1. <span data-ttu-id="1f3f8-113">Utwórz klasę, która pochodzi od klasy <xref:System.Windows.Forms.Form> i zawiera <xref:System.Windows.Forms.DataGridView> kontroli i <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     <span data-ttu-id="1f3f8-114">Poniższy przykład kodu zawiera inicjowanie podstawowych oraz `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-114">The following code example provides basic initialization and includes a `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2. <span data-ttu-id="1f3f8-115">W definicji klasy formularza do obsługi szczegółowe informacje o połączenie z bazą danych, należy zaimplementować metodę.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>  
  
     <span data-ttu-id="1f3f8-116">W tym przykładzie kodu użyto `GetData` metodę, która zwraca wypełnione <xref:System.Data.DataTable> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="1f3f8-117">Upewnij się, że możesz `connectionString` zmiennej na wartość, która jest odpowiednia dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1f3f8-118">Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="1f3f8-119">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="1f3f8-120">Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-120">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3. <span data-ttu-id="1f3f8-121">Implementowanie obsługi dla formularza użytkownika <xref:System.Windows.Forms.Form.Load> zdarzeń, która inicjuje <xref:System.Windows.Forms.DataGridView> i <xref:System.Windows.Forms.BindingSource> i konfiguruje powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4. <span data-ttu-id="1f3f8-122">Obsługa <xref:System.Windows.Forms.DataGridView.DataError> zdarzenie na <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="1f3f8-123">Kontekst błędu w przypadku operacji zatwierdzania, wyświetla błąd w <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="1f3f8-124">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1f3f8-124">Testing the Application</span></span>  
 <span data-ttu-id="1f3f8-125">Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-125">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="1f3f8-126">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="1f3f8-126">To test the form</span></span>  
  
- <span data-ttu-id="1f3f8-127">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-127">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="1f3f8-128">Zostanie wyświetlony <xref:System.Windows.Forms.DataGridView> kontroli wypełnione danymi z tabeli Customers.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="1f3f8-129">Jeśli wprowadzasz zduplikowane wartości `CustomerID` i zatwierdź edycję, wartość komórki zostaną przywrócone automatycznie i zostanie wyświetlony <xref:System.Windows.Forms.MessageBox> wyświetlającą błąd zapisu danych.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1f3f8-130">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1f3f8-130">Next Steps</span></span>  
 <span data-ttu-id="1f3f8-131">Ta aplikacja zapewnia podstawową wiedzę na temat <xref:System.Windows.Forms.DataGridView> funkcje formantu.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="1f3f8-132">Można dostosować wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> kontroli na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="1f3f8-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
- <span data-ttu-id="1f3f8-133">Zmienianie stylów obramowania i nagłówek.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-133">Change border and header styles.</span></span> <span data-ttu-id="1f3f8-134">Aby uzyskać więcej informacji, zobacz [jak: Zmiana obramowania i formantu DataGridView formularzy style linii siatki w Windows](change-the-border-and-gridline-styles-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
- <span data-ttu-id="1f3f8-135">Włączać lub ograniczać danych wprowadzonych przez użytkownika <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1f3f8-136">Aby uzyskać więcej informacji, zobacz [jak: Zapobieganie dodawaniu i usuwaniu w Windows formantu DataGridView formularzy](prevent-row-addition-and-deletion-datagridview.md), i [jak: Określanie kolumn jako tylko do odczytu w Windows formantu DataGridView formularzy](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
- <span data-ttu-id="1f3f8-137">Weryfikowanie danych wejściowych użytkownika do <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1f3f8-138">Aby uzyskać więcej informacji, zobacz [instruktażu: Sprawdzanie poprawności danych w Windows formantu DataGridView formularzy](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
- <span data-ttu-id="1f3f8-139">Obsłużyć bardzo dużych zestawów danych przy użyciu trybu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="1f3f8-140">Aby uzyskać więcej informacji, zobacz [instruktażu: Implementowanie trybu wirtualnego w Windows formantu DataGridView formularzy](implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
- <span data-ttu-id="1f3f8-141">Dostosowywanie wyglądu komórek.</span><span class="sxs-lookup"><span data-stu-id="1f3f8-141">Customize the appearance of cells.</span></span> <span data-ttu-id="1f3f8-142">Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie wyglądu komórek w formancie DataGridView formularzy Windows](customize-the-appearance-of-cells-in-the-datagrid.md) i [jak: Ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy Windows](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f3f8-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f3f8-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f3f8-143">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1f3f8-144">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f3f8-144">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1f3f8-145">Instrukcje: Obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f3f8-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="1f3f8-146">Przewodnik: Sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f3f8-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1f3f8-147">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="1f3f8-147">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
