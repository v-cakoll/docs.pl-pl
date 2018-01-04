---
title: "Porady: zapewnienie pozostawania wybranego wiersza w tabeli potomnej w prawidłowym położeniu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c06692f19fe31bfcf2ae1f9778d847f412a007e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a><span data-ttu-id="f6407-102">Porady: zapewnienie pozostawania wybranego wiersza w tabeli potomnej w prawidłowym położeniu</span><span class="sxs-lookup"><span data-stu-id="f6407-102">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>
<span data-ttu-id="f6407-103">Często po współpracujesz powiązanie danych w formularzach systemu Windows, co jest nazywane nadrzędny/podrzędny lub głównych/szczegółów widoku będą wyświetlane dane.</span><span class="sxs-lookup"><span data-stu-id="f6407-103">Oftentimes when you work with data binding in Windows Forms, you will display data in what is called a parent/child or master/details view.</span></span> <span data-ttu-id="f6407-104">Odnosi się do scenariusz wiązania danych, których dane z tego samego źródła są wyświetlane w dwóch formantów.</span><span class="sxs-lookup"><span data-stu-id="f6407-104">This refers to a data-binding scenario where data from the same source is displayed in two controls.</span></span> <span data-ttu-id="f6407-105">Zmiana wyboru w jeden formant powoduje danych wyświetlanych w formancie drugi do zmiany.</span><span class="sxs-lookup"><span data-stu-id="f6407-105">Changing the selection in one control causes the data displayed in the second control to change.</span></span> <span data-ttu-id="f6407-106">Na przykład pierwszy formant może zawierać listę klientów, a drugi listę zleceń związane z wybranego klienta w pierwszego formantu.</span><span class="sxs-lookup"><span data-stu-id="f6407-106">For example, the first control might contain a list of customers and the second a list of orders related to the selected customer in the first control.</span></span>  
  
 <span data-ttu-id="f6407-107">.NET Framework w wersji 2.0, począwszy od podczas wyświetlania danych w widoku nadrzędny/podrzędny, że trzeba będzie wykonać dodatkowe czynności, aby upewnić się, czy obecnie wybrany wiersz w tabeli podrzędnej nie zostanie zresetowana do pierwszego wiersza tabeli.</span><span class="sxs-lookup"><span data-stu-id="f6407-107">Starting with the .NET Framework version 2.0, when you display data in a parent/child view you might have to take extra steps to make sure that the currently selected row in the child table is not reset to the first row of the table.</span></span> <span data-ttu-id="f6407-108">W tym celu należy do pamięci podręcznej położenie elementów podrzędnych tabeli i resetuje je po zmianie tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f6407-108">In order to do this, you will have to cache the child table position and reset it after the parent table changes.</span></span> <span data-ttu-id="f6407-109">Zazwyczaj resetowania podrzędnych występuje po raz pierwszy pól w wierszu zmian w tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f6407-109">Typically the child reset occurs the first time a field in a row of the parent table changes.</span></span>  
  
### <a name="to-cache-the-current-child-position"></a><span data-ttu-id="f6407-110">Do pamięci podręcznej bieżące położenie elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="f6407-110">To Cache the Current Child Position</span></span>  
  
1.  <span data-ttu-id="f6407-111">Należy zadeklarować zmienną całkowitą do przechowywania położenie listy elementów podrzędnych i zmienną wartości logicznej do przechowywania, czy w pamięci podręcznej położenie elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f6407-111">Declare an integer variable to store the child list position and a Boolean variable to store whether to cache the child position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  <span data-ttu-id="f6407-112">Obsługa <xref:System.Windows.Forms.CurrencyManager.ListChanged> zdarzenia dla tego powiązania <xref:System.Windows.Forms.CurrencyManager> i sprawdź, czy <xref:System.ComponentModel.ListChangedType> z <xref:System.ComponentModel.ListChangedType.Reset>.</span><span class="sxs-lookup"><span data-stu-id="f6407-112">Handle the <xref:System.Windows.Forms.CurrencyManager.ListChanged> event for the binding's <xref:System.Windows.Forms.CurrencyManager> and check for a <xref:System.ComponentModel.ListChangedType> of <xref:System.ComponentModel.ListChangedType.Reset>.</span></span>  
  
3.  <span data-ttu-id="f6407-113">Sprawdź bieżącą pozycję <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="f6407-113">Check the current position of the <xref:System.Windows.Forms.CurrencyManager>.</span></span> <span data-ttu-id="f6407-114">Jeśli jest większa niż pierwsza pozycja na liście (zazwyczaj 0), zapisz go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f6407-114">If it is greater than first entry in the list (typically 0), save it to a variable.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="f6407-115">Obsługiwać listy nadrzędnych <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> zdarzenia nadrzędnego menedżera waluty.</span><span class="sxs-lookup"><span data-stu-id="f6407-115">Handle the parent list's <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> event for the parent currency manager.</span></span> <span data-ttu-id="f6407-116">W obsłudze ustaw wartość logiczna wskazująca, że nie jest scenariusz buforowania.</span><span class="sxs-lookup"><span data-stu-id="f6407-116">In the handler, set the Boolean value to indicate it is not a caching scenario.</span></span> <span data-ttu-id="f6407-117">Jeśli <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> występuje zmiany do elementu nadrzędnego jest zmiana pozycji listy, a nie zmiany wartości elementu.</span><span class="sxs-lookup"><span data-stu-id="f6407-117">If the <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> occurs, the change to the parent is a list position change and not an item value change.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a><span data-ttu-id="f6407-118">Aby zresetować położenie elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="f6407-118">To Reset the Child Position</span></span>  
  
1.  <span data-ttu-id="f6407-119">Obsługa <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> zdarzenia dla obiekt podrzędny powiązania <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="f6407-119">Handle the <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> event for the child binding's <xref:System.Windows.Forms.CurrencyManager>.</span></span>  
  
2.  <span data-ttu-id="f6407-120">Resetuj położenie elementów podrzędnych w tabeli w pamięci podręcznej miejsce zapisane w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="f6407-120">Reset the child table position to the cached position saved in the previous procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="f6407-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6407-121">Example</span></span>  
 <span data-ttu-id="f6407-122">W poniższym przykładzie pokazano, jak zapisać bieżącą pozycję w <xref:System.Windows.Forms.CurrencyManager>.for tabelą podrzędną i resetowanie położenia po zakończeniu edycji w tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f6407-122">The following example demonstrates how to save the current position on the <xref:System.Windows.Forms.CurrencyManager>.for a child table and reset the position after an edit is completed on the parent table.</span></span> <span data-ttu-id="f6407-123">Ten przykład zawiera dwa <xref:System.Windows.Forms.DataGridView> formanty powiązane z dwiema tabelami w <xref:System.Data.DataSet> przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="f6407-123">This example contains two <xref:System.Windows.Forms.DataGridView> controls bound to two tables in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="f6407-124">Ustanowieniu relacji między dwiema tabelami i Relacja jest dodawany do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f6407-124">A relation is established between the two tables and the relation is added to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f6407-125">Pozycja w tabeli podrzędnej jest początkowo ustawiona trzeciego wiersza w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f6407-125">The position in the child table is initially set to the third row for demonstration purposes.</span></span>  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 <span data-ttu-id="f6407-126">Aby przetestować przykładów kodu, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f6407-126">To test the code example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="f6407-127">Można uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="f6407-127">Run the example.</span></span>  
  
2.  <span data-ttu-id="f6407-128">Upewnij się, że **pamięci podręcznej i resetowanie Umieść** pole wyboru jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f6407-128">Make sure the **Cache and reset position** check box is selected.</span></span>  
  
3.  <span data-ttu-id="f6407-129">Kliknij przycisk **pola nadrzędnego wyczyść** przycisk, aby spowodować zmiany w tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f6407-129">Click the **Clear parent field** button to cause a change in a field of the parent table.</span></span> <span data-ttu-id="f6407-130">Należy zauważyć, że wybrany wiersz w tabeli podrzędnej nie ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="f6407-130">Notice that the selected row in the child table does not change.</span></span>  
  
4.  <span data-ttu-id="f6407-131">Zamknij i ponownie uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="f6407-131">Close and run the example again.</span></span> <span data-ttu-id="f6407-132">Należy to zrobić, ponieważ spowoduje zresetowanie zachowanie tylko na pierwszej zmianie wiersza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f6407-132">You need to do this because the reset behavior occurs only on the first change in the parent row.</span></span>  
  
5.  <span data-ttu-id="f6407-133">Wyczyść **pamięci podręcznej i resetowanie Umieść** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="f6407-133">Clear the **Cache and reset position** check box.</span></span>  
  
6.  <span data-ttu-id="f6407-134">Kliknij przycisk **pola nadrzędnego wyczyść** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f6407-134">Click the **Clear parent field** button.</span></span> <span data-ttu-id="f6407-135">Należy zauważyć, że zmiany wybranego wiersza w tabeli podrzędnej w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="f6407-135">Notice that the selected row in the child table changes to the first row.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6407-136">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f6407-136">Compiling the Code</span></span>  
 <span data-ttu-id="f6407-137">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f6407-137">This example requires:</span></span>  
  
-   <span data-ttu-id="f6407-138">Odwołania do zestawów systemu, system.dane System.Drawing, System.Windows.Forms i zestawów System.XML.</span><span class="sxs-lookup"><span data-stu-id="f6407-138">References to the System, System.Data, System.Drawing, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="f6407-139">Informacje o sposobie budowania w tym przykładzie z wiersza polecenia dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [csc.exe budynku wiersza polecenia z](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f6407-139">For information about how to build this example from the command line for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f6407-140">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="f6407-140">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="f6407-141">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f6407-141">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6407-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6407-142">See Also</span></span>  
 [<span data-ttu-id="f6407-143">Instrukcje: zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych</span><span class="sxs-lookup"><span data-stu-id="f6407-143">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [<span data-ttu-id="f6407-144">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="f6407-144">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="f6407-145">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6407-145">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
