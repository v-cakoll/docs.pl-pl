---
title: 'Porady: zapewnienie pozostawania wybranego wiersza w tabeli potomnej w prawidłowym położeniu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
ms.openlocfilehash: e1fdb007451c157e60a1ad723b5d2d06bc85ecdf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135591"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a><span data-ttu-id="906d5-102">Porady: zapewnienie pozostawania wybranego wiersza w tabeli potomnej w prawidłowym położeniu</span><span class="sxs-lookup"><span data-stu-id="906d5-102">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>
<span data-ttu-id="906d5-103">Często w przypadku, gdy pracujesz z powiązanie danych w formularzach Windows Forms, będą wyświetlane dane, co jest nazywany nadrzędne/podrzędne lub wzorzec/szczegół widoku.</span><span class="sxs-lookup"><span data-stu-id="906d5-103">Oftentimes when you work with data binding in Windows Forms, you will display data in what is called a parent/child or master/details view.</span></span> <span data-ttu-id="906d5-104">Odnosi się do scenariusza wiązania danych, których dane z tego samego źródła są wyświetlane w dwóch kontrolek.</span><span class="sxs-lookup"><span data-stu-id="906d5-104">This refers to a data-binding scenario where data from the same source is displayed in two controls.</span></span> <span data-ttu-id="906d5-105">Zmienianie zaznaczenia w jednym formancie powoduje, że dane wyświetlane w drugiej kontrolce.</span><span class="sxs-lookup"><span data-stu-id="906d5-105">Changing the selection in one control causes the data displayed in the second control to change.</span></span> <span data-ttu-id="906d5-106">Na przykład pierwszy formant może zawierać listę klientów i druga lista zamówień powiązanych z wybranym klientem w pierwszej kontrolce.</span><span class="sxs-lookup"><span data-stu-id="906d5-106">For example, the first control might contain a list of customers and the second a list of orders related to the selected customer in the first control.</span></span>  
  
 <span data-ttu-id="906d5-107">Uruchamianie przy użyciu platformy .NET Framework w wersji 2.0, podczas wyświetlania danych w widoku nadrzędne/podrzędne, które można wykonać dodatkowe czynności, aby upewnić się, ponieważ obecnie wybrany wiersz w tabeli podrzędnej nie jest resetowana do pierwszego wiersza tabeli.</span><span class="sxs-lookup"><span data-stu-id="906d5-107">Starting with the .NET Framework version 2.0, when you display data in a parent/child view you might have to take extra steps to make sure that the currently selected row in the child table is not reset to the first row of the table.</span></span> <span data-ttu-id="906d5-108">Aby to zrobić, trzeba będzie położenie elementów podrzędnych w tabeli w pamięci podręcznej i zresetowanie jej po zmianie tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="906d5-108">In order to do this, you will have to cache the child table position and reset it after the parent table changes.</span></span> <span data-ttu-id="906d5-109">Resetowanie podrzędnych występuje zwykle po raz pierwszy pól w wierszu zmian w tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="906d5-109">Typically the child reset occurs the first time a field in a row of the parent table changes.</span></span>  
  
### <a name="to-cache-the-current-child-position"></a><span data-ttu-id="906d5-110">Buforowanie bieżące położenie elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="906d5-110">To Cache the Current Child Position</span></span>  
  
1.  <span data-ttu-id="906d5-111">Zadeklaruj zmienną całkowitoliczbową do przechowywania położenie listy elementów podrzędnych i zmiennej typu Boolean do przechowywania, czy w pamięci podręcznej położenie elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="906d5-111">Declare an integer variable to store the child list position and a Boolean variable to store whether to cache the child position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  <span data-ttu-id="906d5-112">Obsługa <xref:System.Windows.Forms.CurrencyManager.ListChanged> zdarzenia dla wiązania <xref:System.Windows.Forms.CurrencyManager> i sprawdź, czy <xref:System.ComponentModel.ListChangedType> z <xref:System.ComponentModel.ListChangedType.Reset>.</span><span class="sxs-lookup"><span data-stu-id="906d5-112">Handle the <xref:System.Windows.Forms.CurrencyManager.ListChanged> event for the binding's <xref:System.Windows.Forms.CurrencyManager> and check for a <xref:System.ComponentModel.ListChangedType> of <xref:System.ComponentModel.ListChangedType.Reset>.</span></span>  
  
3.  <span data-ttu-id="906d5-113">Sprawdź bieżące położenie <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="906d5-113">Check the current position of the <xref:System.Windows.Forms.CurrencyManager>.</span></span> <span data-ttu-id="906d5-114">Czy jest on większy niż pierwszy wpis na liście (zazwyczaj 0), zapisz go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="906d5-114">If it is greater than first entry in the list (typically 0), save it to a variable.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="906d5-115">Obsługiwać listy nadrzędnej <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> zdarzenia nadrzędnego menedżera waluty.</span><span class="sxs-lookup"><span data-stu-id="906d5-115">Handle the parent list's <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> event for the parent currency manager.</span></span> <span data-ttu-id="906d5-116">W procedurze obsługi należy ustawić wartość logiczna wskazująca, że nie jest scenariusz buforowania.</span><span class="sxs-lookup"><span data-stu-id="906d5-116">In the handler, set the Boolean value to indicate it is not a caching scenario.</span></span> <span data-ttu-id="906d5-117">Jeśli <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> problem wystąpi, zmiany do elementu nadrzędnego jest zmiana położenia listy i nie zmieniać wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="906d5-117">If the <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> occurs, the change to the parent is a list position change and not an item value change.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a><span data-ttu-id="906d5-118">Aby zresetować położenie elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="906d5-118">To Reset the Child Position</span></span>  
  
1.  <span data-ttu-id="906d5-119">Obsługa <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> zdarzenia podrzędnego wiązania <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="906d5-119">Handle the <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> event for the child binding's <xref:System.Windows.Forms.CurrencyManager>.</span></span>  
  
2.  <span data-ttu-id="906d5-120">Resetuj położenie elementów podrzędnych w tabeli do pamięci podręcznej pozycji zapisany w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="906d5-120">Reset the child table position to the cached position saved in the previous procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="906d5-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="906d5-121">Example</span></span>  
 <span data-ttu-id="906d5-122">Poniższy przykład pokazuje, jak zapisać bieżącą pozycję w <xref:System.Windows.Forms.CurrencyManager>tego tabeli podrzędnej i resetowanie położenia po zakończeniu edycji w tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="906d5-122">The following example demonstrates how to save the current position on the <xref:System.Windows.Forms.CurrencyManager>.for a child table and reset the position after an edit is completed on the parent table.</span></span> <span data-ttu-id="906d5-123">Ten przykład zawiera dwa <xref:System.Windows.Forms.DataGridView> formanty powiązane z dwiema tabelami w <xref:System.Data.DataSet> przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="906d5-123">This example contains two <xref:System.Windows.Forms.DataGridView> controls bound to two tables in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="906d5-124">Ustanowieniu relacji między dwiema tabelami, a relacja jest dodawany do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="906d5-124">A relation is established between the two tables and the relation is added to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="906d5-125">Pozycja w tabeli podrzędnej jest początkowo ustawiona trzeciego wiersza w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="906d5-125">The position in the child table is initially set to the third row for demonstration purposes.</span></span>  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 <span data-ttu-id="906d5-126">Aby przetestować przykładowy kod, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="906d5-126">To test the code example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="906d5-127">Uruchom przykład.</span><span class="sxs-lookup"><span data-stu-id="906d5-127">Run the example.</span></span>  
  
2.  <span data-ttu-id="906d5-128">Upewnij się, że **pamięci podręcznej i Resetuj położenie** pole wyboru jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="906d5-128">Make sure the **Cache and reset position** check box is selected.</span></span>  
  
3.  <span data-ttu-id="906d5-129">Kliknij przycisk **pole nadrzędne wyczyść** przycisk, aby spowodować, że zmiany w tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="906d5-129">Click the **Clear parent field** button to cause a change in a field of the parent table.</span></span> <span data-ttu-id="906d5-130">Należy zauważyć, że zaznaczony wiersz w tabeli podrzędnej nie zmienia się.</span><span class="sxs-lookup"><span data-stu-id="906d5-130">Notice that the selected row in the child table does not change.</span></span>  
  
4.  <span data-ttu-id="906d5-131">Zamknij i ponownie uruchom przykład.</span><span class="sxs-lookup"><span data-stu-id="906d5-131">Close and run the example again.</span></span> <span data-ttu-id="906d5-132">Należy to zrobić, ponieważ spowoduje zachowanie resetowania tylko na pierwszej zmianie wiersza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="906d5-132">You need to do this because the reset behavior occurs only on the first change in the parent row.</span></span>  
  
5.  <span data-ttu-id="906d5-133">Wyczyść **pamięci podręcznej i Resetuj położenie** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="906d5-133">Clear the **Cache and reset position** check box.</span></span>  
  
6.  <span data-ttu-id="906d5-134">Kliknij przycisk **pole nadrzędne wyczyść** przycisku.</span><span class="sxs-lookup"><span data-stu-id="906d5-134">Click the **Clear parent field** button.</span></span> <span data-ttu-id="906d5-135">Należy zauważyć, że zaznaczony wiersz w tabeli podrzędnej zmienia się do pierwszego wiersza.</span><span class="sxs-lookup"><span data-stu-id="906d5-135">Notice that the selected row in the child table changes to the first row.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="906d5-136">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="906d5-136">Compiling the Code</span></span>  
 <span data-ttu-id="906d5-137">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="906d5-137">This example requires:</span></span>  
  
-   <span data-ttu-id="906d5-138">Odwołania do zestawów systemu, dane systemowe, System.Drawing, przestrzeń nazw System.Windows.Forms i System.XML.</span><span class="sxs-lookup"><span data-stu-id="906d5-138">References to the System, System.Data, System.Drawing, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="906d5-139">Aby uzyskać informacje dotyczące sposobu tworzenia tego przykładu z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="906d5-139">For information about how to build this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="906d5-140">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="906d5-140">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="906d5-141">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="906d5-141">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906d5-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="906d5-142">See Also</span></span>  
 [<span data-ttu-id="906d5-143">Instrukcje: zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych</span><span class="sxs-lookup"><span data-stu-id="906d5-143">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [<span data-ttu-id="906d5-144">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="906d5-144">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="906d5-145">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="906d5-145">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
