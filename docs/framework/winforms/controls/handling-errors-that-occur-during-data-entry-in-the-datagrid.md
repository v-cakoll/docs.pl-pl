---
title: 'Przewodnik: obsługa błędów występujących podczas wprowadzania danych w formancie DataGridView'
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
ms.openlocfilehash: 77a4dcd9cf069ed8bbee6c49aa41db619c8e12ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738740"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7579a-102">Wskazówki: obsługa błędów występujących podczas wprowadzania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7579a-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>

<span data-ttu-id="7579a-103">Obsługa błędów z bazowego magazynu danych jest funkcją wymaganą dla aplikacji do wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="7579a-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="7579a-104">Formant Windows Forms <xref:System.Windows.Forms.DataGridView> ułatwia to poprzez ujawnienie zdarzenia <xref:System.Windows.Forms.DataGridView.DataError>, które jest zgłaszane, gdy magazyn danych wykryje naruszenie ograniczenia lub naruszoną regułę biznesową.</span><span class="sxs-lookup"><span data-stu-id="7579a-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>

<span data-ttu-id="7579a-105">W tym instruktażu uzyskasz pobieranie wierszy z tabeli `Customers` w przykładowej bazie danych Northwind i wyświetlanie ich w kontrolce <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7579a-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7579a-106">W przypadku wykrycia zduplikowanej wartości `CustomerID` w nowym wierszu lub zmodyfikowanym wierszu <xref:System.Windows.Forms.DataGridView.DataError> zdarzenie zostanie wykonane, które zostanie obsłużone przez wyświetlenie <xref:System.Windows.Forms.MessageBox> opisującego wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7579a-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>

<span data-ttu-id="7579a-107">Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="7579a-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7579a-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7579a-108">Prerequisites</span></span>

<span data-ttu-id="7579a-109">Aby ukończyć ten Instruktaż, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="7579a-109">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="7579a-110">Dostęp do serwera z przykładową bazą danych Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7579a-110">Access to a server that has the Northwind SQL Server sample database.</span></span>

## <a name="creating-the-form"></a><span data-ttu-id="7579a-111">Tworzenie formularza</span><span class="sxs-lookup"><span data-stu-id="7579a-111">Creating the Form</span></span>

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="7579a-112">Aby obsłużyć błędy wprowadzania danych w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="7579a-112">To handle data-entry errors in the DataGridView control</span></span>

1. <span data-ttu-id="7579a-113">Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i zawiera kontrolkę <xref:System.Windows.Forms.DataGridView> i składnik <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="7579a-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>

    <span data-ttu-id="7579a-114">Poniższy przykład kodu zapewnia inicjalizację podstawową i zawiera metodę `Main`.</span><span class="sxs-lookup"><span data-stu-id="7579a-114">The following code example provides basic initialization and includes a `Main` method.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. <span data-ttu-id="7579a-115">Zaimplementuj metodę w definicji klasy formularza do obsługi szczegółów połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="7579a-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>

    <span data-ttu-id="7579a-116">Ten przykład kodu używa metody `GetData`, która zwraca wypełniony obiekt <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="7579a-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="7579a-117">Upewnij się, że zmienna `connectionString` jest ustawiona na wartość, która jest odpowiednia dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7579a-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7579a-118">Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7579a-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="7579a-119">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7579a-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="7579a-120">Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="7579a-120">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. <span data-ttu-id="7579a-121">Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.Form.Load> formularza, które inicjuje <xref:System.Windows.Forms.DataGridView> i <xref:System.Windows.Forms.BindingSource> i konfiguruje powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="7579a-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. <span data-ttu-id="7579a-122">Obsłuż zdarzenie <xref:System.Windows.Forms.DataGridView.DataError> w <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7579a-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>

    <span data-ttu-id="7579a-123">Jeśli kontekstem błędu jest operacja zatwierdzania, Wyświetl błąd w <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="7579a-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a><span data-ttu-id="7579a-124">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7579a-124">Testing the Application</span></span>

<span data-ttu-id="7579a-125">Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="7579a-125">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="7579a-126">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="7579a-126">To test the form</span></span>

- <span data-ttu-id="7579a-127">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="7579a-127">Press F5 to run the application.</span></span>

  <span data-ttu-id="7579a-128">Zobaczysz, że formant <xref:System.Windows.Forms.DataGridView> wypełniony danymi z tabeli Customers.</span><span class="sxs-lookup"><span data-stu-id="7579a-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="7579a-129">Jeśli wprowadzisz zduplikowaną wartość `CustomerID` i zatwierdzisz edycję, wartość komórki zostanie automatycznie przywrócona, a zobaczysz <xref:System.Windows.Forms.MessageBox>, który wyświetla błąd wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="7579a-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7579a-130">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7579a-130">Next Steps</span></span>

<span data-ttu-id="7579a-131">Ta aplikacja zapewnia podstawowe informacje o możliwościach kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7579a-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="7579a-132">Wygląd i zachowanie kontrolki <xref:System.Windows.Forms.DataGridView> można dostosować na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="7579a-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>

- <span data-ttu-id="7579a-133">Zmień style obramowania i nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7579a-133">Change border and header styles.</span></span> <span data-ttu-id="7579a-134">Aby uzyskać więcej informacji, zobacz [How to: zmiana stylu obramowania i linii siatki w kontrolce DataGridView Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="7579a-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>

- <span data-ttu-id="7579a-135">Włącz lub Ogranicz dane wejściowe użytkownika do kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7579a-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7579a-136">Aby uzyskać więcej informacji, zobacz [How to: Zapobieganie dodawaniu i usuwaniu wierszy w kontrolce datagridview Windows Forms](prevent-row-addition-and-deletion-datagridview.md)i [instrukcje: Określanie kolumn jako tylko do odczytu w kontrolce DataGridView Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7579a-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="7579a-137">Sprawdź poprawność danych wejściowych użytkownika do kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7579a-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7579a-138">Aby uzyskać więcej informacji, zobacz [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7579a-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="7579a-139">Obsługa bardzo dużych zestawów danych przy użyciu trybu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="7579a-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="7579a-140">Aby uzyskać więcej informacji, zobacz [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7579a-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>

- <span data-ttu-id="7579a-141">Dostosuj wygląd komórek.</span><span class="sxs-lookup"><span data-stu-id="7579a-141">Customize the appearance of cells.</span></span> <span data-ttu-id="7579a-142">Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie wyglądu komórek w kontrolce datagridview Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) i [instrukcje: Ustawianie domyślnych stylów komórek dla kontrolki DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7579a-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7579a-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7579a-143">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="7579a-144">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7579a-144">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7579a-145">Instrukcje: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7579a-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="7579a-146">Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7579a-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7579a-147">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="7579a-147">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
