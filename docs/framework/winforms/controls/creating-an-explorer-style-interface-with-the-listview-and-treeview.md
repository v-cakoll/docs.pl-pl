---
title: 'Wskazówki: tworzenie interfejsu w stylu Eksploratora Windows z formantami ListView i TreeView za pomocą narzędzia Projektant'
description: Dowiedz się, jak utworzyć interfejs stylu Eksploratora z kontrolkami Windows Forms ListView i TreeView przy użyciu narzędzia Projektant.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: 44d4db1ef3da85dbf411498f486882b86a05c140
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174630"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="13fb2-103">Wskazówki: tworzenie interfejsu w stylu Eksploratora Windows z formantami ListView i TreeView za pomocą narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="13fb2-103">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>

<span data-ttu-id="13fb2-104">Jedną z zalet programu Visual Studio jest możliwość tworzenia profesjonalnych aplikacji Windows Forms w krótkim czasie.</span><span class="sxs-lookup"><span data-stu-id="13fb2-104">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="13fb2-105">Typowy scenariusz polega na tworzeniu interfejsu użytkownika z <xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView> kontrolkami, które przypominają funkcję Eksploratora Windows w systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="13fb2-105">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="13fb2-106">Eksplorator Windows wyświetla hierarchiczną strukturę plików i folderów na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="13fb2-106">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="13fb2-107">Aby utworzyć formularz zawierający formant ListView i widok TreeView</span><span class="sxs-lookup"><span data-stu-id="13fb2-107">To create the form containing a ListView and TreeView control</span></span>

1. <span data-ttu-id="13fb2-108">W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="13fb2-108">On the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="13fb2-109">W oknie dialogowym **Nowy projekt** wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="13fb2-109">In the **New Project** dialog box, do the following:</span></span>

    1. <span data-ttu-id="13fb2-110">W kategorii wybierz pozycję **Visual Basic** lub **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="13fb2-110">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>

    2. <span data-ttu-id="13fb2-111">Z listy szablonów wybierz **Windows Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="13fb2-111">In the list of templates, choose **Windows Forms Application**.</span></span>

3. <span data-ttu-id="13fb2-112">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="13fb2-112">Click **OK**.</span></span> <span data-ttu-id="13fb2-113">Tworzony jest nowy projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="13fb2-113">A new Windows Forms project is created.</span></span>

4. <span data-ttu-id="13fb2-114">Dodaj <xref:System.Windows.Forms.SplitContainer> kontrolkę do formularza i ustaw jej <xref:System.Windows.Forms.SplitContainer.Dock%2A> Właściwość na <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="13fb2-114">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="13fb2-115">Dodaj <xref:System.Windows.Forms.ImageList> nazwę `imageList1` do formularza i użyj okno właściwości, aby dodać dwa obrazy: obraz folderu i obraz dokumentu w tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="13fb2-115">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>

6. <span data-ttu-id="13fb2-116">Dodaj <xref:System.Windows.Forms.TreeView> kontrolkę o nazwie `treeview1` do formularza i umieść ją po lewej stronie <xref:System.Windows.Forms.SplitContainer> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="13fb2-116">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="13fb2-117">W okno Właściwości `treeView1` wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="13fb2-117">In the Properties window for `treeView1` do the following:</span></span>

    1. <span data-ttu-id="13fb2-118">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> Właściwość na wartość <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="13fb2-118">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="13fb2-119">Ustaw <xref:System.Windows.Forms.TreeView.ImageList%2A> Właściwość na`imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="13fb2-119">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>

7. <span data-ttu-id="13fb2-120">Dodaj <xref:System.Windows.Forms.ListView> kontrolkę o nazwie `listView1` do formularza i umieść ją po prawej stronie <xref:System.Windows.Forms.SplitContainer> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="13fb2-120">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="13fb2-121">W okno Właściwości `listview1` wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="13fb2-121">In the Properties window for `listview1` do the following:</span></span>

    1. <span data-ttu-id="13fb2-122">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> Właściwość na wartość <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="13fb2-122">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="13fb2-123">Ustaw <xref:System.Windows.Forms.ListView.View%2A> Właściwość na wartość <xref:System.Windows.Forms.View.Details> .</span><span class="sxs-lookup"><span data-stu-id="13fb2-123">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

    3. <span data-ttu-id="13fb2-124">Otwórz Edytor kolekcji ColumnHeader, klikając ![ wielokropek (przycisk wielokropka (...) w okno właściwości programu Visual Studio. ](./media/visual-studio-ellipsis-button.png) ) we <xref:System.Windows.Forms.ListView.Columns%2A> właściwości **.**</span><span class="sxs-lookup"><span data-stu-id="13fb2-124">Open the ColumnHeader Collection Editor by clicking the ellipses (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="13fb2-125">Dodaj trzy kolumny i ustaw ich <xref:System.Windows.Forms.ColumnHeader.Text%2A> Właściwość na `Name` , `Type` , i `Last Modified` , odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="13fb2-125">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="13fb2-126">Kliknij przycisk **OK**, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="13fb2-126">Click **OK** to close the dialog box.</span></span>

    4. <span data-ttu-id="13fb2-127">Ustaw <xref:System.Windows.Forms.ListView.SmallImageList%2A> Właściwość na`imageList1.`</span><span class="sxs-lookup"><span data-stu-id="13fb2-127">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>

8. <span data-ttu-id="13fb2-128">Zaimplementuj kod, aby wypełnić <xref:System.Windows.Forms.TreeView> węzły węzłami i podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="13fb2-128">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="13fb2-129">Dodaj ten kod do `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="13fb2-129">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. <span data-ttu-id="13fb2-130">Ponieważ poprzedni kod używa przestrzeni nazw System.IO, Dodaj odpowiednią instrukcję using lub import w górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="13fb2-130">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. <span data-ttu-id="13fb2-131">Wywołaj metodę Set z poprzedniego kroku w konstruktorze lub <xref:System.Windows.Forms.Form.Load> metodzie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13fb2-131">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="13fb2-132">Dodaj ten kod do konstruktora formularzy.</span><span class="sxs-lookup"><span data-stu-id="13fb2-132">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <span data-ttu-id="13fb2-133">Obsłuż <xref:System.Windows.Forms.TreeView.NodeMouseClick> zdarzenie dla `treeview1` i zaimplementuj kod **,** aby wypełnić `listview1` zawartość węzła po kliknięciu węzła.</span><span class="sxs-lookup"><span data-stu-id="13fb2-133">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="13fb2-134">Dodaj ten kod do `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="13fb2-134">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     <span data-ttu-id="13fb2-135">Jeśli używasz języka C#, upewnij się, że masz <xref:System.Windows.Forms.TreeView.NodeMouseClick> zdarzenie skojarzone z jego metodą obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13fb2-135">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="13fb2-136">Dodaj ten kod do konstruktora formularzy.</span><span class="sxs-lookup"><span data-stu-id="13fb2-136">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a><span data-ttu-id="13fb2-137">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="13fb2-137">Testing the Application</span></span>

<span data-ttu-id="13fb2-138">Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="13fb2-138">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="13fb2-139">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="13fb2-139">To test the form</span></span>

- <span data-ttu-id="13fb2-140">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="13fb2-140">Press F5 to run the application.</span></span>

     <span data-ttu-id="13fb2-141">Zobaczysz formularz podzielony zawierający <xref:System.Windows.Forms.TreeView> kontrolkę wyświetlającą katalog projektu po lewej stronie i <xref:System.Windows.Forms.ListView> kontrolkę po prawej stronie z trzema kolumnami.</span><span class="sxs-lookup"><span data-stu-id="13fb2-141">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="13fb2-142">Możesz przejść <xref:System.Windows.Forms.TreeView> przez wybranie węzłów katalogów, a <xref:System.Windows.Forms.ListView> zostanie wypełniony zawartość wybranego katalogu.</span><span class="sxs-lookup"><span data-stu-id="13fb2-142">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="13fb2-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="13fb2-143">Next Steps</span></span>

<span data-ttu-id="13fb2-144">Ta aplikacja stanowi przykład sposobu użycia <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ListView> kontroli razem.</span><span class="sxs-lookup"><span data-stu-id="13fb2-144">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="13fb2-145">Aby uzyskać więcej informacji na temat tych kontrolek, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="13fb2-145">For more information on these controls, see the following topics:</span></span>

- [<span data-ttu-id="13fb2-146">Porady: dodawanie niestandardowych informacji do formantu TreeView lub ListView (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="13fb2-146">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [<span data-ttu-id="13fb2-147">Instrukcje: dodawanie funkcji wyszukiwania do kontrolki ListView</span><span class="sxs-lookup"><span data-stu-id="13fb2-147">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)

- [<span data-ttu-id="13fb2-148">Instrukcje: dołączanie menu ShortCut do węzła TreeView</span><span class="sxs-lookup"><span data-stu-id="13fb2-148">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a><span data-ttu-id="13fb2-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13fb2-149">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="13fb2-150">ListView — Formant</span><span class="sxs-lookup"><span data-stu-id="13fb2-150">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="13fb2-151">Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13fb2-151">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="13fb2-152">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13fb2-152">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="13fb2-153">Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13fb2-153">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
