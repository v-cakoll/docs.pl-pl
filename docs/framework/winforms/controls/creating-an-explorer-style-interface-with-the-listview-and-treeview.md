---
title: 'Wskazówki: tworzenie interfejsu w stylu Eksploratora Windows z kontrolkami ListView i TreeView za pomocą narzędzia Projektant'
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
ms.openlocfilehash: 73d3a0bef1ab075aee8e06f676ef17b853773552
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468067"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="9193b-102">Wskazówki: tworzenie interfejsu w stylu Eksploratora Windows z kontrolkami ListView i TreeView za pomocą narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9193b-102">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>
<span data-ttu-id="9193b-103">Jedną z zalet programu Visual Studio jest możliwość tworzenia profesjonalnych aplikacji Windows Forms w krótki czas.</span><span class="sxs-lookup"><span data-stu-id="9193b-103">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="9193b-104">Typowym scenariuszem jest tworzenie interfejsu użytkownika (UI) za pomocą <xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView> formantów, które przypomina funkcji Eksploratora Windows, systemów operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="9193b-104">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="9193b-105">Eksplorator Windows wyświetla hierarchiczną strukturę plików i folderów na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9193b-105">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9193b-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="9193b-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9193b-107">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="9193b-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9193b-108">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9193b-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="9193b-109">Aby utworzyć formularz zawierający kontrolki ListView i TreeView</span><span class="sxs-lookup"><span data-stu-id="9193b-109">To create the form containing a ListView and TreeView control</span></span>  
  
1.  <span data-ttu-id="9193b-110">Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="9193b-110">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="9193b-111">W **nowy projekt** okna dialogowego pole, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9193b-111">In the **New Project** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="9193b-112">Do kategorii wybierz **języka Visual Basic** lub **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="9193b-112">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>  
  
    2.  <span data-ttu-id="9193b-113">Z listy szablonów wybierz **aplikacja interfejsu Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="9193b-113">In the list of templates, choose **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="9193b-114">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9193b-114">Click **OK**.</span></span> <span data-ttu-id="9193b-115">Utworzono nowy projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9193b-115">A new Windows Forms project is created.</span></span>  
  
4.  <span data-ttu-id="9193b-116">Dodaj <xref:System.Windows.Forms.SplitContainer> do formularza i ustaw jego <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="9193b-116">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="9193b-117">Dodaj <xref:System.Windows.Forms.ImageList> o nazwie `imageList1` formularza i użyj okna właściwości, aby dodać dwa obrazy: Obraz folderu i obraz dokumentu w tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="9193b-117">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>  
  
6.  <span data-ttu-id="9193b-118">Dodaj <xref:System.Windows.Forms.TreeView> formantu o nazwie `treeview1` do formularza i umieść ją w lewej części <xref:System.Windows.Forms.SplitContainer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9193b-118">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="9193b-119">W oknie dialogowym właściwości `treeView1` wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9193b-119">In the Properties window for `treeView1` do the following:</span></span>  
  
    1.  <span data-ttu-id="9193b-120">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="9193b-120">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="9193b-121">Ustaw <xref:System.Windows.Forms.TreeView.ImageList%2A> właściwości `imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="9193b-121">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>  
  
7.  <span data-ttu-id="9193b-122">Dodaj <xref:System.Windows.Forms.ListView> formantu o nazwie `listView1` do formularza i umieść ją na prawej krawędzi <xref:System.Windows.Forms.SplitContainer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9193b-122">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="9193b-123">W oknie dialogowym właściwości `listview1` wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9193b-123">In the Properties window for `listview1` do the following:</span></span>  
  
    1.  <span data-ttu-id="9193b-124">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="9193b-124">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="9193b-125">Ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwość <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="9193b-125">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
    3.  <span data-ttu-id="9193b-126">Otwórz ColumnHeader — Edytor kolekcji, klikając przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) w <xref:System.Windows.Forms.ListView.Columns%2A> właściwość **.**</span><span class="sxs-lookup"><span data-stu-id="9193b-126">Open the ColumnHeader Collection Editor by clicking the ellipses (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="9193b-127">Dodaj trzy kolumny i ustaw ich <xref:System.Windows.Forms.ColumnHeader.Text%2A> właściwości `Name`, `Type`, i `Last Modified`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9193b-127">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="9193b-128">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="9193b-128">Click **OK** to close the dialog box.</span></span>  
  
    4.  <span data-ttu-id="9193b-129">Ustaw <xref:System.Windows.Forms.ListView.SmallImageList%2A> właściwości `imageList1.`</span><span class="sxs-lookup"><span data-stu-id="9193b-129">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>  
  
8.  <span data-ttu-id="9193b-130">Implementowania kodu służącego do wypełnienia <xref:System.Windows.Forms.TreeView> z węzłów i węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="9193b-130">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="9193b-131">Dodaj następujący kod do `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="9193b-131">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. <span data-ttu-id="9193b-132">Ponieważ w poprzednim kodzie używa przestrzeni nazw System.IO, Dodaj odpowiedni using lub Importuj instrukcję w górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="9193b-132">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="9193b-133">Wywołaj metodę konfiguracji z poprzedniego kroku w Konstruktorze formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9193b-133">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="9193b-134">Dodaj następujący kod do konstruktora formularza.</span><span class="sxs-lookup"><span data-stu-id="9193b-134">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. <span data-ttu-id="9193b-135">Obsługa <xref:System.Windows.Forms.TreeView.NodeMouseClick> zdarzenia dla `treeview1` **,** i zaimplementuj kod, aby wypełnić `listview1` z zawartością węzła po kliknięciu węzła.</span><span class="sxs-lookup"><span data-stu-id="9193b-135">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="9193b-136">Dodaj następujący kod do `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="9193b-136">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     <span data-ttu-id="9193b-137">Jeśli używasz języka C#, upewnij się, że masz <xref:System.Windows.Forms.TreeView.NodeMouseClick> zdarzenie skojarzone z jego metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9193b-137">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="9193b-138">Dodaj następujący kod do konstruktora formularza.</span><span class="sxs-lookup"><span data-stu-id="9193b-138">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="9193b-139">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="9193b-139">Testing the Application</span></span>  
 <span data-ttu-id="9193b-140">Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="9193b-140">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="9193b-141">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="9193b-141">To test the form</span></span>  
  
-   <span data-ttu-id="9193b-142">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="9193b-142">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="9193b-143">Zostanie wyświetlony, zawierający formularz podziału <xref:System.Windows.Forms.TreeView> formant, który wyświetla katalogu projektu po lewej stronie i <xref:System.Windows.Forms.ListView> kontroli po prawej stronie przy użyciu trzech kolumnach.</span><span class="sxs-lookup"><span data-stu-id="9193b-143">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="9193b-144">Mogą przechodzić <xref:System.Windows.Forms.TreeView> , wybierając węzłów katalogu i <xref:System.Windows.Forms.ListView> jest wypełniana przy użyciu zawartość wybranego katalogu.</span><span class="sxs-lookup"><span data-stu-id="9193b-144">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9193b-145">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9193b-145">Next Steps</span></span>  
 <span data-ttu-id="9193b-146">Ta aplikacja zawiera przykładowy sposób korzystania <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ListView> kontroluje ze sobą.</span><span class="sxs-lookup"><span data-stu-id="9193b-146">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="9193b-147">Aby uzyskać więcej informacji na temat tych kontrolek zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="9193b-147">For more information on these controls, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9193b-148">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9193b-148">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [<span data-ttu-id="9193b-149">Instrukcje: dodawanie funkcji wyszukiwania do kontrolki ListView</span><span class="sxs-lookup"><span data-stu-id="9193b-149">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [<span data-ttu-id="9193b-150">Instrukcje: dołączanie menu ShortCut do węzła TreeView</span><span class="sxs-lookup"><span data-stu-id="9193b-150">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a><span data-ttu-id="9193b-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9193b-151">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [<span data-ttu-id="9193b-152">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="9193b-152">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="9193b-153">Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9193b-153">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="9193b-154">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9193b-154">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="9193b-155">Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9193b-155">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
