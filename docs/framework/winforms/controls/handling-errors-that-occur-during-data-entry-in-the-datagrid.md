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
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046074"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d7860-102">Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d7860-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>

<span data-ttu-id="d7860-103">Obsługa błędów z bazowego magazynu danych jest funkcją wymaganą dla aplikacji do wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="d7860-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="d7860-104">Formant Windows Forms <xref:System.Windows.Forms.DataGridView> ułatwia to <xref:System.Windows.Forms.DataGridView.DataError> ujawnienie zdarzenia, które jest zgłaszane, gdy magazyn danych wykryje naruszenie ograniczenia lub naruszoną regułę biznesową.</span><span class="sxs-lookup"><span data-stu-id="d7860-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>

<span data-ttu-id="d7860-105">W tym instruktażu uzyskasz pobieranie wierszy z `Customers` tabeli w przykładowej bazie danych Northwind i wyświetlanie ich <xref:System.Windows.Forms.DataGridView> w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="d7860-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d7860-106">W przypadku wykrycia zduplikowanej `CustomerID` wartości w nowym wierszu lub edytowanego istniejącego wiersza <xref:System.Windows.Forms.DataGridView.DataError> zdarzenie zostanie wykonane, które będzie obsługiwane przez wyświetlenie <xref:System.Windows.Forms.MessageBox> opisu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d7860-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>

<span data-ttu-id="d7860-107">Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Obsługa błędów występujących podczas wprowadzania danych w kontrolce](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)DataGridView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d7860-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d7860-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d7860-108">Prerequisites</span></span>

<span data-ttu-id="d7860-109">Aby ukończyć ten Instruktaż, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="d7860-109">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="d7860-110">Dostęp do serwera z przykładową bazą danych Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d7860-110">Access to a server that has the Northwind SQL Server sample database.</span></span>

## <a name="creating-the-form"></a><span data-ttu-id="d7860-111">Tworzenie formularza</span><span class="sxs-lookup"><span data-stu-id="d7860-111">Creating the Form</span></span>

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="d7860-112">Aby obsłużyć błędy wprowadzania danych w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="d7860-112">To handle data-entry errors in the DataGridView control</span></span>

1. <span data-ttu-id="d7860-113">Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i <xref:System.Windows.Forms.DataGridView> zawiera kontrolkę i <xref:System.Windows.Forms.BindingSource> składnik.</span><span class="sxs-lookup"><span data-stu-id="d7860-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>

    <span data-ttu-id="d7860-114">Poniższy przykład kodu zapewnia inicjalizację podstawową i zawiera `Main` metodę.</span><span class="sxs-lookup"><span data-stu-id="d7860-114">The following code example provides basic initialization and includes a `Main` method.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. <span data-ttu-id="d7860-115">Zaimplementuj metodę w definicji klasy formularza do obsługi szczegółów połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="d7860-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>

    <span data-ttu-id="d7860-116">Ten przykład kodu używa `GetData` metody, która zwraca wypełniony <xref:System.Data.DataTable> obiekt.</span><span class="sxs-lookup"><span data-stu-id="d7860-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="d7860-117">Upewnij się, że ustawiono `connectionString` zmienną na wartość odpowiednią dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d7860-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d7860-118">Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7860-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="d7860-119">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d7860-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="d7860-120">Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="d7860-120">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. <span data-ttu-id="d7860-121">Zaimplementuj procedurę obsługi dla <xref:System.Windows.Forms.Form.Load> zdarzenia formularza, która <xref:System.Windows.Forms.DataGridView> inicjuje i <xref:System.Windows.Forms.BindingSource> konfiguruje powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="d7860-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. <span data-ttu-id="d7860-122">Obsłuż <xref:System.Windows.Forms.DataGridView>zdarzenie w. <xref:System.Windows.Forms.DataGridView.DataError></span><span class="sxs-lookup"><span data-stu-id="d7860-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>

    <span data-ttu-id="d7860-123">Jeśli kontekstem błędu jest operacja zatwierdzania, Wyświetl błąd w <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="d7860-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a><span data-ttu-id="d7860-124">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="d7860-124">Testing the Application</span></span>

<span data-ttu-id="d7860-125">Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="d7860-125">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="d7860-126">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="d7860-126">To test the form</span></span>

- <span data-ttu-id="d7860-127">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="d7860-127">Press F5 to run the application.</span></span>

  <span data-ttu-id="d7860-128">Zobaczysz <xref:System.Windows.Forms.DataGridView> kontrolkę wypełnioną danymi z tabeli Customers.</span><span class="sxs-lookup"><span data-stu-id="d7860-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="d7860-129">Jeśli wprowadzisz zduplikowaną wartość dla `CustomerID` i zatwierdzisz edycję, wartość komórki zostanie automatycznie przywrócona, a zobaczysz <xref:System.Windows.Forms.MessageBox> , że zostanie wyświetlony komunikat o błędzie wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="d7860-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d7860-130">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d7860-130">Next Steps</span></span>

<span data-ttu-id="d7860-131">Ta aplikacja zapewnia podstawowe informacje o <xref:System.Windows.Forms.DataGridView> możliwościach formantu.</span><span class="sxs-lookup"><span data-stu-id="d7860-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="d7860-132">Wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> kontrolki można dostosować na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="d7860-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>

- <span data-ttu-id="d7860-133">Zmień style obramowania i nagłówka.</span><span class="sxs-lookup"><span data-stu-id="d7860-133">Change border and header styles.</span></span> <span data-ttu-id="d7860-134">Aby uzyskać więcej informacji, zobacz [jak: Zmień style obramowania i linii siatki w kontrolce](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d7860-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>

- <span data-ttu-id="d7860-135">Włącz lub Ogranicz dane wejściowe użytkownika do <xref:System.Windows.Forms.DataGridView> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d7860-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d7860-136">Aby uzyskać więcej informacji, zobacz [jak: Zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce](prevent-row-addition-and-deletion-datagridview.md)DataGridView Windows Forms i [instrukcje: Ustaw kolumny jako tylko do odczytu w kontrolce](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d7860-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="d7860-137">Sprawdź poprawność danych <xref:System.Windows.Forms.DataGridView> wejściowych użytkownika do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d7860-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d7860-138">Aby uzyskać więcej informacji, [zobacz Przewodnik: Sprawdzanie poprawności danych w kontrolce](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d7860-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="d7860-139">Obsługa bardzo dużych zestawów danych przy użyciu trybu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="d7860-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="d7860-140">Aby uzyskać więcej informacji, [zobacz Przewodnik: Implementowanie trybu wirtualnego w kontrolce](implementing-virtual-mode-wf-datagridview-control.md)DataGridView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d7860-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>

- <span data-ttu-id="d7860-141">Dostosuj wygląd komórek.</span><span class="sxs-lookup"><span data-stu-id="d7860-141">Customize the appearance of cells.</span></span> <span data-ttu-id="d7860-142">Aby uzyskać więcej informacji, zobacz [jak: Dostosuj wygląd komórek w kontrolce](customize-the-appearance-of-cells-in-the-datagrid.md) DataGridView Windows Forms i [instrukcje: Ustaw domyślne style komórek dla kontrolki](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d7860-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7860-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7860-143">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="d7860-144">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7860-144">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d7860-145">Instrukcje: Obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7860-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="d7860-146">Przewodnik: Sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7860-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d7860-147">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="d7860-147">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
