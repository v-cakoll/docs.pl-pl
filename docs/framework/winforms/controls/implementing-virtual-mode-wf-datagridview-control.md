---
title: 'Przewodnik: implementowanie trybu wirtualnego w formancie DataGridView'
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
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746520"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2d779-102">Wskazówki: implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2d779-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2d779-103">Aby wyświetlić bardzo duże ilości danych tabelarycznych w kontrolce <xref:System.Windows.Forms.DataGridView>, można ustawić właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> na `true` i jawnie zarządzać interakcją formantu z jego magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="2d779-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="2d779-104">Pozwala to dostosować wydajność kontroli w tej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="2d779-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="2d779-105">Kontrolka <xref:System.Windows.Forms.DataGridView> zawiera kilka zdarzeń, które można obsłużyć w celu współpracy z niestandardowym magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="2d779-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="2d779-106">Ten przewodnik przeprowadzi Cię przez proces wdrażania tych programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2d779-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="2d779-107">Przykład kodu w tym temacie używa bardzo prostego źródła danych na potrzeby ilustracji.</span><span class="sxs-lookup"><span data-stu-id="2d779-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="2d779-108">W ustawieniu produkcji zwykle ładowane są tylko te wiersze, które mają być wyświetlane w pamięci podręcznej, i obsługują zdarzenia <xref:System.Windows.Forms.DataGridView>, aby współtworzyć i zaktualizować pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="2d779-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="2d779-109">Aby uzyskać więcej informacji, zobacz [implementowanie trybu wirtualnego przy użyciu ładowania danych just-in-Time w kontrolce DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="2d779-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="2d779-110">Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [jak: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="2d779-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="2d779-111">Tworzenie formularza</span><span class="sxs-lookup"><span data-stu-id="2d779-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="2d779-112">Aby zaimplementować tryb wirtualny</span><span class="sxs-lookup"><span data-stu-id="2d779-112">To implement virtual mode</span></span>  
  
1. <span data-ttu-id="2d779-113">Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i zawiera kontrolkę <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="2d779-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="2d779-114">Poniższy kod zawiera pewne inicjalizacje podstawowe.</span><span class="sxs-lookup"><span data-stu-id="2d779-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="2d779-115">Deklaruje pewne zmienne, które będą używane w kolejnych krokach, zapewnia metodę `Main` i udostępnia prosty układ formularza w konstruktorze klas.</span><span class="sxs-lookup"><span data-stu-id="2d779-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. <span data-ttu-id="2d779-116">Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.Form.Load> formularza, która inicjuje formant <xref:System.Windows.Forms.DataGridView> i wypełnia magazyn danych wartościami przykładowymi.</span><span class="sxs-lookup"><span data-stu-id="2d779-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. <span data-ttu-id="2d779-117">Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellValueNeeded>, które pobiera żądaną wartość komórki z magazynu danych lub obiektu `Customer`, który jest obecnie w trakcie edycji.</span><span class="sxs-lookup"><span data-stu-id="2d779-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="2d779-118">To zdarzenie występuje, gdy kontrolka <xref:System.Windows.Forms.DataGridView> musi malować komórkę.</span><span class="sxs-lookup"><span data-stu-id="2d779-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. <span data-ttu-id="2d779-119">Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellValuePushed>, które przechowuje edytowaną wartość komórki w obiekcie `Customer` reprezentującym edytowany wiersz.</span><span class="sxs-lookup"><span data-stu-id="2d779-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="2d779-120">To zdarzenie występuje zawsze, gdy użytkownik zatwierdzi zmianę wartości komórki.</span><span class="sxs-lookup"><span data-stu-id="2d779-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. <span data-ttu-id="2d779-121">Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.NewRowNeeded>, które tworzy nowy obiekt `Customer` reprezentujący nowo utworzony wiersz.</span><span class="sxs-lookup"><span data-stu-id="2d779-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="2d779-122">To zdarzenie występuje zawsze, gdy użytkownik wprowadzi wiersz dla nowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="2d779-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. <span data-ttu-id="2d779-123">Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.RowValidated>, które zapisuje nowe lub zmodyfikowane wiersze w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="2d779-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="2d779-124">To zdarzenie występuje zawsze, gdy użytkownik zmieni bieżący wiersz.</span><span class="sxs-lookup"><span data-stu-id="2d779-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. <span data-ttu-id="2d779-125">Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>, która wskazuje, czy zdarzenie <xref:System.Windows.Forms.DataGridView.CancelRowEdit> nastąpi, gdy użytkownik sygnalizuje ponownie wersję wiersza przez naciśnięcie klawisza ESC dwa razy w trybie edycji lub poza trybem edycji.</span><span class="sxs-lookup"><span data-stu-id="2d779-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="2d779-126">Domyślnie <xref:System.Windows.Forms.DataGridView.CancelRowEdit> występuje po zmianie wersji wiersza, gdy wszystkie komórki w bieżącym wierszu zostały zmodyfikowane, chyba że właściwość <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> jest ustawiona na `true` w programie obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.</span><span class="sxs-lookup"><span data-stu-id="2d779-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="2d779-127">To zdarzenie jest przydatne, gdy zakres zatwierdzania jest określany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2d779-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. <span data-ttu-id="2d779-128">Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CancelRowEdit>, które odrzuca wartości obiektu `Customer` reprezentującego bieżący wiersz.</span><span class="sxs-lookup"><span data-stu-id="2d779-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="2d779-129">To zdarzenie występuje, gdy użytkownik sygnalizuje przewinięcie wiersza przez naciśnięcie klawisza ESC dwa razy w trybie edycji lub poza trybem edycji.</span><span class="sxs-lookup"><span data-stu-id="2d779-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="2d779-130">To zdarzenie nie występuje, jeśli żadna komórka w bieżącym wierszu nie została zmodyfikowana lub jeśli wartość właściwości <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> została ustawiona na `false` w obsłudze zdarzeń <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.</span><span class="sxs-lookup"><span data-stu-id="2d779-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="2d779-131">Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.UserDeletingRow>, które usuwa istniejący obiekt `Customer` z magazynu danych lub odrzuca niezapisany obiekt `Customer` reprezentujący nowo utworzony wiersz.</span><span class="sxs-lookup"><span data-stu-id="2d779-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="2d779-132">To zdarzenie występuje zawsze, gdy użytkownik usuwa wiersz, klikając nagłówek wiersza i naciskając klawisz DELETE.</span><span class="sxs-lookup"><span data-stu-id="2d779-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="2d779-133">Zaimplementuj prostą klasę `Customers`, aby reprezentować elementy danych używane przez ten przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="2d779-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="2d779-134">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="2d779-134">Testing the Application</span></span>  
 <span data-ttu-id="2d779-135">Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="2d779-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="2d779-136">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="2d779-136">To test the form</span></span>  
  
- <span data-ttu-id="2d779-137">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="2d779-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="2d779-138">Zostanie wyświetlona kontrolka <xref:System.Windows.Forms.DataGridView> zawierająca trzy rekordy klientów.</span><span class="sxs-lookup"><span data-stu-id="2d779-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="2d779-139">Możesz zmodyfikować wartości wielu komórek w wierszu i nacisnąć klawisz ESC dwa razy w trybie edycji i poza trybem edycji, aby przywrócić pierwotne wartości w całym wierszu.</span><span class="sxs-lookup"><span data-stu-id="2d779-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="2d779-140">W przypadku modyfikowania, dodawania lub usuwania wierszy w kontrolce `Customer` obiektów w magazynie danych są również modyfikowane, dodawane lub usuwane.</span><span class="sxs-lookup"><span data-stu-id="2d779-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2d779-141">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2d779-141">Next Steps</span></span>  
 <span data-ttu-id="2d779-142">Ta aplikacja zawiera podstawowe informacje o zdarzeniach, które należy obsłużyć w celu zaimplementowania trybu wirtualnego w kontrolce <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="2d779-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="2d779-143">Tę podstawową aplikację można ulepszyć na wiele sposobów:</span><span class="sxs-lookup"><span data-stu-id="2d779-143">You can improve this basic application in a number of ways:</span></span>  
  
- <span data-ttu-id="2d779-144">Zaimplementuj magazyn danych, który buforuje wartości z zewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2d779-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="2d779-145">Pamięć podręczna powinna pobierać i odrzucać wartości zgodnie z potrzebami, tak aby zawierała tylko te dane, które są niezbędne do wyświetlania podczas zużywania niewielkiej ilości pamięci na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="2d779-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
- <span data-ttu-id="2d779-146">Dostosuj wydajność magazynu danych w zależności od wymagań.</span><span class="sxs-lookup"><span data-stu-id="2d779-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="2d779-147">Można na przykład zrekompensować wolne połączenia sieciowe zamiast ograniczeń pamięci klienta, używając większego rozmiaru pamięci podręcznej i minimalizując liczbę zapytań bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2d779-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="2d779-148">Aby uzyskać więcej informacji na temat buforowania wartości z zewnętrznej bazy danych, zobacz [How to: Implementuj tryb wirtualny przy użyciu ładowania danych just-in-Time w kontrolce DataGridView Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="2d779-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d779-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d779-149">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="2d779-150">Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d779-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2d779-151">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d779-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2d779-152">Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d779-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="2d779-153">Instrukcje: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d779-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
