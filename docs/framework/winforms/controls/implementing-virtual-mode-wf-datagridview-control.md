---
title: 'Wskazówki: implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 52e93ebe0b2903fdf2fe97f4ce812331e740f8b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539922"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="71f5f-102">Wskazówki: implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="71f5f-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="71f5f-103">Jeśli chcesz wyświetlić bardzo dużych ilości danych tabelarycznych w <xref:System.Windows.Forms.DataGridView> sterowania, można ustawić <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości `true` i jawnego zarządzania formantu interakcji z jej magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="71f5f-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="71f5f-104">Dzięki temu można dostrojenie wydajności formantu w tej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="71f5f-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="71f5f-105"><xref:System.Windows.Forms.DataGridView> Kontrola zapewnia kilka zdarzeń, które może obsłużyć do interakcji z niestandardowego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="71f5f-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="71f5f-106">Ten przewodnik ułatwia wdrażanie tych programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71f5f-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="71f5f-107">Przykładowy kod w tym temacie korzysta z źródła danych bardzo proste w celach ilustracyjnych.</span><span class="sxs-lookup"><span data-stu-id="71f5f-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="71f5f-108">W środowisku produkcyjnym zwykle załaduje tylko na wierszach, które są potrzebne do wyświetlenia w pamięci podręcznej i obsługi <xref:System.Windows.Forms.DataGridView> zdarzenia do i z aktualizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="71f5f-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="71f5f-109">Aby uzyskać więcej informacji, zobacz [Implementowanie trybu wirtualnego przy użyciu just in time w formancie DataGridView formularzy systemu Windows podczas ładowania danych](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="71f5f-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="71f5f-110">Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="71f5f-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="71f5f-111">Tworzenie formularza</span><span class="sxs-lookup"><span data-stu-id="71f5f-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="71f5f-112">Aby zaimplementować tryb wirtualny</span><span class="sxs-lookup"><span data-stu-id="71f5f-112">To implement virtual mode</span></span>  
  
1.  <span data-ttu-id="71f5f-113">Utwórz klasę pochodną <xref:System.Windows.Forms.Form> i zawiera <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="71f5f-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="71f5f-114">Poniższy kod zawiera niektóre podstawowe inicjowania.</span><span class="sxs-lookup"><span data-stu-id="71f5f-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="71f5f-115">Deklaruje niektóre zmienne, które będą używane w kolejnych krokach, zapewnia `Main` metody i udostępnia układu formularza proste w konstruktorze klasy.</span><span class="sxs-lookup"><span data-stu-id="71f5f-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  <span data-ttu-id="71f5f-116">Implementowanie obsługi dla formularza użytkownika <xref:System.Windows.Forms.Form.Load> zdarzenie, które inicjuje <xref:System.Windows.Forms.DataGridView> kontroli i wypełnia magazynu danych z wartości przykładowych.</span><span class="sxs-lookup"><span data-stu-id="71f5f-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  <span data-ttu-id="71f5f-117">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CellValueNeeded> zdarzeń, który pobiera wartość komórki żądanego z magazynu danych lub `Customer` obiektu obecnie w edycji.</span><span class="sxs-lookup"><span data-stu-id="71f5f-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="71f5f-118">To zdarzenie występuje zawsze, gdy <xref:System.Windows.Forms.DataGridView> formant wymaga malowania komórki.</span><span class="sxs-lookup"><span data-stu-id="71f5f-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  <span data-ttu-id="71f5f-119">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CellValuePushed> zdarzeń, która przechowuje wartość edytowanej komórki w `Customer` obiekt reprezentujący wiersz edytowany.</span><span class="sxs-lookup"><span data-stu-id="71f5f-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="71f5f-120">To zdarzenie występuje, gdy użytkownik zatwierdza zmiany wartości komórki.</span><span class="sxs-lookup"><span data-stu-id="71f5f-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  <span data-ttu-id="71f5f-121">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.NewRowNeeded> zdarzenie, które tworzy nową `Customer` obiekt reprezentujący nowo utworzony wiersza.</span><span class="sxs-lookup"><span data-stu-id="71f5f-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="71f5f-122">To zdarzenie występuje, gdy użytkownik wprowadzi wiersz dla nowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="71f5f-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  <span data-ttu-id="71f5f-123">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.RowValidated> zdarzenie, które zapisuje nowych lub zmodyfikowanych wierszy w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="71f5f-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="71f5f-124">To zdarzenie występuje, gdy użytkownik zmieni bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="71f5f-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  <span data-ttu-id="71f5f-125">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> zdarzeń, która wskazuje, czy <xref:System.Windows.Forms.DataGridView.CancelRowEdit> zdarzeń ma miejsce, gdy użytkownik sygnały odwrócenie wiersza, naciskając klawisz ESC dwa razy w trybie edycji lub raz poza trybem edycji.</span><span class="sxs-lookup"><span data-stu-id="71f5f-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="71f5f-126">Domyślnie <xref:System.Windows.Forms.DataGridView.CancelRowEdit> występuje po odwrócenie wierszy, gdy wszystkie komórki w bieżącym wierszu zostały zmodyfikowane, chyba że <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> właściwość jest ustawiona na `true` w <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71f5f-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="71f5f-127">To zdarzenie jest przydatne, gdy zakres zatwierdzania jest określana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="71f5f-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  <span data-ttu-id="71f5f-128">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CancelRowEdit> zdarzenie, które odrzuca wszystkie wartości `Customer` obiekt reprezentujący bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="71f5f-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="71f5f-129">To zdarzenie występuje, gdy użytkownik sygnały odwrócenie wiersza, naciskając klawisz ESC dwa razy w trybie edycji lub raz poza trybem edycji.</span><span class="sxs-lookup"><span data-stu-id="71f5f-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="71f5f-130">To zdarzenie nie występuje, jeśli żadna z komórek w bieżącym wierszu zostały zmodyfikowane lub wartość <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> ustawioną właściwość `false` w <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71f5f-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="71f5f-131">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.UserDeletingRow> zdarzenie, które usuwa istniejące `Customer` obiektu z magazynu danych lub odrzuca wszystkie niezapisane `Customer` obiekt reprezentujący nowo utworzony wiersza.</span><span class="sxs-lookup"><span data-stu-id="71f5f-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="71f5f-132">To zdarzenie występuje, gdy użytkownik usuwa wiersz przez kliknięcie nagłówka wiersza i naciskając klawisz DELETE.</span><span class="sxs-lookup"><span data-stu-id="71f5f-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="71f5f-133">Implementowanie prostego `Customers` klasy do reprezentowania elementów danych używany przez ten przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="71f5f-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="71f5f-134">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="71f5f-134">Testing the Application</span></span>  
 <span data-ttu-id="71f5f-135">Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="71f5f-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="71f5f-136">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="71f5f-136">To test the form</span></span>  
  
-   <span data-ttu-id="71f5f-137">Kompilowanie i uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71f5f-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="71f5f-138">Zobaczysz <xref:System.Windows.Forms.DataGridView> kontroli wypełniane przy użyciu trzech rekordów klientów.</span><span class="sxs-lookup"><span data-stu-id="71f5f-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="71f5f-139">Można zmodyfikować wartości wielu komórek w wierszu, a następnie naciśnij klawisz ESC, dwa razy w trybie edycji i raz poza trybem edycji można przywrócić cały wiersz do jego oryginalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="71f5f-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="71f5f-140">Podczas modyfikowania, dodawania i usuwania wierszy w formancie, `Customer` zmodyfikowane, dodane lub usunięte również obiektów w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="71f5f-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="71f5f-141">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="71f5f-141">Next Steps</span></span>  
 <span data-ttu-id="71f5f-142">Ta aplikacja zawiera podstawową wiedzę na temat zdarzeń musi obsługiwać do zaimplementowania tryb wirtualny w <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="71f5f-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="71f5f-143">Można zwiększyć tej aplikacji w warstwie podstawowa na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="71f5f-143">You can improve this basic application in a number of ways:</span></span>  
  
-   <span data-ttu-id="71f5f-144">Implementuje magazynu danych, który buforuje wartości z zewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="71f5f-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="71f5f-145">Pamięć podręczna należy pobrać i odrzucić wartości zgodnie z potrzebami, tak aby zawierała tylko niezbędne do wyświetlenia podczas korzystania z małą ilością pamięci na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="71f5f-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
-   <span data-ttu-id="71f5f-146">Dostrojenie wydajności magazynu danych, w zależności od wymagań.</span><span class="sxs-lookup"><span data-stu-id="71f5f-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="71f5f-147">Na przykład możesz chcieć kompensacji wolne połączenia sieciowe, a nie ograniczenia pamięci komputera klienckiego za pomocą większego rozmiaru pamięci podręcznej i minimalizację liczby zapytań bazy danych.</span><span class="sxs-lookup"><span data-stu-id="71f5f-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="71f5f-148">Aby uzyskać więcej informacji na temat buforowania wartości z zewnętrznej bazy danych, zobacz [porady: Implementowanie trybu wirtualnego just in time w formancie DataGridView formularzy systemu Windows podczas ładowania danych](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="71f5f-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f5f-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71f5f-149">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [<span data-ttu-id="71f5f-150">Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71f5f-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="71f5f-151">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71f5f-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="71f5f-152">Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71f5f-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [<span data-ttu-id="71f5f-153">Instrukcje: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71f5f-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
