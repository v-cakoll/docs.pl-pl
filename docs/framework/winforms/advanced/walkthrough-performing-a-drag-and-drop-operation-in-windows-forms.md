---
title: 'Przewodnik: Wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b582043b3b576b3750b897b17a5f6e0cbdeb84f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647637"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="5b6b6-102">Przewodnik: Wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5b6b6-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="5b6b6-103">Wykonywanie operacji przeciągania i upuszczania w aplikacji systemu Windows musi obsługiwać szereg zdarzeń, głównie <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="5b6b6-104">Praca z dostępnych informacji w zdarzeniu argumenty te zdarzenia, można łatwo ułatwić operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="5b6b6-105">Przeciąganie danych</span><span class="sxs-lookup"><span data-stu-id="5b6b6-105">Dragging Data</span></span>  
 <span data-ttu-id="5b6b6-106">Wszystkie operacje przeciągania i upuszczania rozpoczynają się od przeciągania.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="5b6b6-107">Funkcje umożliwiające podczas przeciągania rozpoczyna się zbieranie danych jest zaimplementowana w <xref:System.Windows.Forms.Control.DoDragDrop%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="5b6b6-108">W poniższym przykładzie <xref:System.Windows.Forms.Control.MouseDown> zdarzenia są używane do uruchamiania operacji przeciągania, ponieważ jest on w najbardziej intuicyjnej (Większość akcji przeciągania i upuszczania zaczynają się od przycisk myszy jest wciśnięty).</span><span class="sxs-lookup"><span data-stu-id="5b6b6-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="5b6b6-109">Należy jednak pamiętać, że dowolne zdarzenie, może służyć do zainicjowania procedury przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b6b6-110">Niektóre formanty mają niestandardowych zdarzeń specyficznych dla przeciągania.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="5b6b6-111"><xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView> kontrolki, na przykład mieć <xref:System.Windows.Forms.TreeView.ItemDrag> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="5b6b6-112">Aby rozpocząć operację przeciągania</span><span class="sxs-lookup"><span data-stu-id="5b6b6-112">To start a drag operation</span></span>  
  
1.  <span data-ttu-id="5b6b6-113">W <xref:System.Windows.Forms.Control.MouseDown> zdarzeń dla formantu, gdy rozpocznie się przeciąganie, użyj `DoDragDrop` metodę, aby ustawić dane, które mają być przeciągane i dozwolonym efektem przeciąganie będą mieć.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="5b6b6-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="5b6b6-115">Poniższy przykład pokazuje, jak zainicjować operacji przeciągania.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="5b6b6-116">Kontrolka, gdzie rozpoczyna się przeciągania jest <xref:System.Windows.Forms.Button> kontroli danych przeciąganie jest ciąg reprezentujący <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> kontroli i dozwolone efekty są kopiowania lub przenoszenia.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5b6b6-117">Wszystkie dane mogą być używane jako parametr w `DoDragDrop` metoda; w powyższym przykładzie <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> formant został użyty (a nie zakodowane na stałe wartości lub pobieranie danych z zestawu danych), ponieważ właściwość był powiązany z przeciąganie z lokalizacji ( <xref:System.Windows.Forms.Button> kontroli).</span><span class="sxs-lookup"><span data-stu-id="5b6b6-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="5b6b6-118">Miej to na uwadze, jak włączenie operacji przeciągania i upuszczania do aplikacji z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="5b6b6-119">Operacja przeciągania w czasie działania, które ułatwią Ci obsługę <xref:System.Windows.Forms.Control.QueryContinueDrag> zdarzenie, które "żąda uprawnienia" systemu, aby kontynuować operację przeciągania.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="5b6b6-120">Podczas obsługi tej metody, jest również odpowiedni punkt wywoływać metody mające wpływ na operacji przeciągania, takich jak rozwijanie <xref:System.Windows.Forms.TreeNode> w <xref:System.Windows.Forms.TreeView> kontroli, gdy kursor znajduje się nad nią.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="5b6b6-121">Usuwanie danych</span><span class="sxs-lookup"><span data-stu-id="5b6b6-121">Dropping Data</span></span>  
 <span data-ttu-id="5b6b6-122">Po rozpoczęciu przeciągając danych z lokalizacji Windows formularza lub formantu, naturalnie można je gdzieś umieścić.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="5b6b6-123">Kursor zmieni się na jej przecina obszaru formularza lub formantu, który jest poprawnie skonfigurowany dla porzucenie danych.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="5b6b6-124">Każdy obszar w Windows formularza lub formantu można wprowadzić na akceptowanie danych porzuconych przez ustawienie <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości i obsługa <xref:System.Windows.Forms.Control.DragEnter> i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="5b6b6-125">Aby wykonać zrzutu</span><span class="sxs-lookup"><span data-stu-id="5b6b6-125">To perform a drop</span></span>  
  
1.  <span data-ttu-id="5b6b6-126">Ustaw <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości na wartość true.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2.  <span data-ttu-id="5b6b6-127">W `DragEnter` zdarzeń dla formantu, gdy nastąpi spadek, upewnij się, że dane przeciąganie typu dopuszczalnych (w tym przypadku <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="5b6b6-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="5b6b6-128">Kod następnie ustawia wpływ, jaki nastąpi wartości w przypadku listy <xref:System.Windows.Forms.DragDropEffects> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="5b6b6-129">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5b6b6-130">Definiowanie swoich własnych <xref:System.Windows.Forms.DataFormats> , określając obiektu jako <xref:System.Object> parametru <xref:System.Windows.Forms.DataObject.SetData%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="5b6b6-131">Upewnij się, w trakcie tego, czy określony obiekt jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="5b6b6-132">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3.  <span data-ttu-id="5b6b6-133">W <xref:System.Windows.Forms.Control.DragDrop> zdarzeń dla formantu, gdzie nastąpi spadek, użyj <xref:System.Windows.Forms.DataObject.GetData%2A> metody do pobierania danych przeciągania.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="5b6b6-134">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="5b6b6-135">W poniższym przykładzie <xref:System.Windows.Forms.TextBox> jest kontrolka przeciąganego (gdzie listy nastąpi).</span><span class="sxs-lookup"><span data-stu-id="5b6b6-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="5b6b6-136">Zestawy kodów <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.TextBox> kontrolować równa danych przeciągania.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5b6b6-137">Ponadto można pracować z <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> właściwość tak, aby w zależności od klucze obniżone podczas operacji przeciągania i upuszczania pewne efekty wystąpić (na przykład jest standard, aby skopiować dane przeciąganego, po naciśnięciu klawisza CTRL).</span><span class="sxs-lookup"><span data-stu-id="5b6b6-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b6b6-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b6b6-138">See also</span></span>
- [<span data-ttu-id="5b6b6-139">Instrukcje: Dodawanie danych do Schowka</span><span class="sxs-lookup"><span data-stu-id="5b6b6-139">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="5b6b6-140">Instrukcje: Pobieranie danych ze Schowka</span><span class="sxs-lookup"><span data-stu-id="5b6b6-140">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="5b6b6-141">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="5b6b6-141">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
