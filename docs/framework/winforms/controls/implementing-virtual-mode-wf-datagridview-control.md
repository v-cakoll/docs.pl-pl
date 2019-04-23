---
title: 'Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: 7f6bf1703a6536f4d22b3a2fbe412579c59d39dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344328"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9b265-102">Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9b265-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9b265-103">Gdy zachodzi potrzeba wyświetlenia bardzo dużych ilości danych tabelarycznych w <xref:System.Windows.Forms.DataGridView> kontrolki, można ustawić <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość `true` i jawnie zarządzać kontrolki interakcji z jej magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="9b265-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="9b265-104">Dzięki temu można dostosowywać wydajność kontrolki w tej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="9b265-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="9b265-105"><xref:System.Windows.Forms.DataGridView> Kontrola zapewnia kilka zdarzeń, które może obsłużyć do interakcji z niestandardowego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="9b265-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="9b265-106">Ten przewodnik przeprowadzi Cię przez proces implementowania tych programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9b265-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="9b265-107">W przykładzie kodu, w tym temacie korzysta z źródła danych bardzo prosty w celach ilustracyjnych.</span><span class="sxs-lookup"><span data-stu-id="9b265-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="9b265-108">W środowisku produkcyjnym zazwyczaj załaduje tylko tych wierszy, które są potrzebne do wyświetlania w pamięci podręcznej i obsługiwać <xref:System.Windows.Forms.DataGridView> zdarzenia w interakcję i zaktualizuj pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="9b265-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="9b265-109">Aby uzyskać więcej informacji, zobacz [Implementowanie trybu wirtualnego przy użyciu ładowanie danych just in time w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="9b265-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="9b265-110">Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Implementowanie trybu wirtualnego w Windows formantu DataGridView formularzy](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9b265-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="9b265-111">Tworzenie formularza</span><span class="sxs-lookup"><span data-stu-id="9b265-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="9b265-112">Aby zaimplementować trybu wirtualnego</span><span class="sxs-lookup"><span data-stu-id="9b265-112">To implement virtual mode</span></span>  
  
1. <span data-ttu-id="9b265-113">Utwórz klasę, która pochodzi od klasy <xref:System.Windows.Forms.Form> i zawiera <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9b265-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="9b265-114">Poniższy kod zawiera kilka podstawowych inicjowania.</span><span class="sxs-lookup"><span data-stu-id="9b265-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="9b265-115">Deklaruje niektóre zmienne, które będą używane w kolejnych krokach, zapewnia `Main` metody i zapewnia prosty formularz układu w konstruktorze klasy.</span><span class="sxs-lookup"><span data-stu-id="9b265-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. <span data-ttu-id="9b265-116">Implementowanie obsługi dla formularza użytkownika <xref:System.Windows.Forms.Form.Load> zdarzeń, która inicjuje <xref:System.Windows.Forms.DataGridView> kontroli i wypełnia magazynu danych z przykładowymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="9b265-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. <span data-ttu-id="9b265-117">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CellValueNeeded> zdarzeń, który pobiera wartość żądanej komórki z magazynu danych lub `Customer` obiektu aktualnie w trakcie edycji.</span><span class="sxs-lookup"><span data-stu-id="9b265-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="9b265-118">To zdarzenie występuje zawsze, gdy <xref:System.Windows.Forms.DataGridView> kontrolka wymaga malowania komórki.</span><span class="sxs-lookup"><span data-stu-id="9b265-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. <span data-ttu-id="9b265-119">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CellValuePushed> zdarzeń, która przechowuje wartość edytowane komórki w `Customer` obiekt reprezentujący wiersz edytowany.</span><span class="sxs-lookup"><span data-stu-id="9b265-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="9b265-120">To zdarzenie występuje, gdy użytkownik zatwierdza zmiany wartości komórki.</span><span class="sxs-lookup"><span data-stu-id="9b265-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. <span data-ttu-id="9b265-121">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.NewRowNeeded> zdarzenia, które tworzy nową `Customer` wiersz nowo utworzony obiekt.</span><span class="sxs-lookup"><span data-stu-id="9b265-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="9b265-122">To zdarzenie występuje, gdy użytkownik wprowadzi wiersza dla nowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="9b265-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. <span data-ttu-id="9b265-123">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.RowValidated> zdarzeń, która zapisuje nowe lub zmodyfikowane wiersze w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="9b265-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="9b265-124">To zdarzenie występuje, gdy użytkownik zmienia bieżący wiersz.</span><span class="sxs-lookup"><span data-stu-id="9b265-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. <span data-ttu-id="9b265-125">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> zdarzeń, która wskazuje, czy <xref:System.Windows.Forms.DataGridView.CancelRowEdit> zdarzeń ma miejsce, gdy użytkownik sygnalizuje operacja cofania wiersza przez naciśnięcie klawisza ESC dwa razy w trybie edycji lub raz poza trybem edycji.</span><span class="sxs-lookup"><span data-stu-id="9b265-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="9b265-126">Domyślnie <xref:System.Windows.Forms.DataGridView.CancelRowEdit> występuje po wierszu operacja cofania, gdy zmodyfikowano wszystkie komórki w bieżącym wierszu, chyba że <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> właściwość jest ustawiona na `true` w <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9b265-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="9b265-127">To zdarzenie jest przydatne, gdy zakres zatwierdzenia jest określana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9b265-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. <span data-ttu-id="9b265-128">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CancelRowEdit> zdarzenia, które odrzuca wszystkie wartości `Customer` obiekt reprezentujący bieżącego wiersza.</span><span class="sxs-lookup"><span data-stu-id="9b265-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="9b265-129">To zdarzenie występuje, gdy użytkownik sygnalizuje operacja cofania wiersza przez naciśnięcie klawisza ESC dwa razy w trybie edycji lub raz poza trybem edycji.</span><span class="sxs-lookup"><span data-stu-id="9b265-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="9b265-130">To zdarzenie nie występuje, jeśli zmodyfikowano żadnych komórek w bieżącym wierszu lub wartość <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> została ustawiona właściwość `false` w <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9b265-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="9b265-131">Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.UserDeletingRow> zdarzenia, które usuwa istniejące `Customer` obiektu z magazynu danych lub odrzuca wszystkie niezapisane `Customer` wiersz nowo utworzony obiekt.</span><span class="sxs-lookup"><span data-stu-id="9b265-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="9b265-132">To zdarzenie występuje, gdy użytkownik usuwa wiersz, klikając nagłówek wiersza i naciskając klawisz DELETE.</span><span class="sxs-lookup"><span data-stu-id="9b265-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="9b265-133">Implementowanie prostego `Customers` klasy do reprezentowania elementów danych używane przez ten przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="9b265-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="9b265-134">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="9b265-134">Testing the Application</span></span>  
 <span data-ttu-id="9b265-135">Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="9b265-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="9b265-136">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="9b265-136">To test the form</span></span>  
  
-   <span data-ttu-id="9b265-137">Skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="9b265-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="9b265-138">Zostanie wyświetlony <xref:System.Windows.Forms.DataGridView> kontroli wypełniane przy użyciu trzech rekordów klientów.</span><span class="sxs-lookup"><span data-stu-id="9b265-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="9b265-139">Można zmodyfikować wartości wielu komórek w wierszu, a następnie naciśnij klawisz ESC, dwa razy w trybie edycji, a po poza trybem edycji, aby przywrócić cały wiersz do ich oryginalnych wartości.</span><span class="sxs-lookup"><span data-stu-id="9b265-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="9b265-140">Podczas modyfikowania, dodawanie lub usuwanie wierszy w kontrolce `Customer` zmodyfikowane, dodane lub usunięte również obiekty w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="9b265-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9b265-141">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9b265-141">Next Steps</span></span>  
 <span data-ttu-id="9b265-142">Ta aplikacja zapewnia podstawową wiedzę na temat zdarzeń musi obsługiwać na implementowanie trybu wirtualnego w <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9b265-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9b265-143">Możesz ulepszyć to podstawowa aplikacja na różne sposoby:</span><span class="sxs-lookup"><span data-stu-id="9b265-143">You can improve this basic application in a number of ways:</span></span>  
  
-   <span data-ttu-id="9b265-144">Implementowanie magazyn danych, który przechowuje wartości z zewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9b265-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="9b265-145">Pamięć podręczną należy pobrać i odrzucić wartości zgodnie z potrzebami, tak aby zawierała tylko co jest potrzebne do wyświetlenia podczas korzystania z małą ilością pamięci na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="9b265-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
-   <span data-ttu-id="9b265-146">Dostosuj wydajność magazynu danych, w zależności od wymagań.</span><span class="sxs-lookup"><span data-stu-id="9b265-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="9b265-147">Na przykład możesz chcieć kompensacji wolne połączenia sieciowe, a nie ograniczenia ilości pamięci w komputerze klienckim, używając większy rozmiar pamięci podręcznej i minimalizuje liczbę zapytań do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9b265-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="9b265-148">Aby uzyskać więcej informacji na temat buforowania wartości z zewnętrznej bazy danych, zobacz [jak: Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w Windows formantu DataGridView formularzy](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="9b265-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b265-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b265-149">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="9b265-150">Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b265-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9b265-151">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b265-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9b265-152">Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b265-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="9b265-153">Instrukcje: Implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b265-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
