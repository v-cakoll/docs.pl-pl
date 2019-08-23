---
title: 'Przewodnik: Wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: cda3e87a4b0eb680d374eb0419a6b6b3157dc4a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957122"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="a43c7-102">Przewodnik: Wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a43c7-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="a43c7-103">Aby wykonać operacje przeciągania i upuszczania w aplikacjach opartych na systemie Windows, musisz obsługiwać serie zdarzeń, w szczególności <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragLeave> <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a43c7-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="a43c7-104">Pracując z informacjami dostępnymi w argumentach zdarzeń tych zdarzeń, można łatwo ułatwić wykonywanie operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="a43c7-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="a43c7-105">Przeciąganie danych</span><span class="sxs-lookup"><span data-stu-id="a43c7-105">Dragging Data</span></span>  
 <span data-ttu-id="a43c7-106">Wszystkie operacje przeciągania i upuszczania zaczynają się od przeciągania.</span><span class="sxs-lookup"><span data-stu-id="a43c7-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="a43c7-107">Funkcja umożliwiająca zbieranie danych po rozpoczęciu przeciągania jest zaimplementowana w <xref:System.Windows.Forms.Control.DoDragDrop%2A> metodzie.</span><span class="sxs-lookup"><span data-stu-id="a43c7-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="a43c7-108">W poniższym przykładzie <xref:System.Windows.Forms.Control.MouseDown> zdarzenie jest używane do uruchamiania operacji przeciągania, ponieważ jest najbardziej intuicyjne (większość akcji przeciągania i upuszczania zaczyna się od naciśnięcia przycisku myszy).</span><span class="sxs-lookup"><span data-stu-id="a43c7-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="a43c7-109">Należy jednak pamiętać, że dowolnego zdarzenia można użyć do zainicjowania procedury przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="a43c7-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a43c7-110">Niektóre kontrolki mają niestandardowe zdarzenia dotyczące przeciągania.</span><span class="sxs-lookup"><span data-stu-id="a43c7-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="a43c7-111">Na przykład <xref:System.Windows.Forms.TreeView> kontrolki <xref:System.Windows.Forms.ListView> i mają zdarzenie. <xref:System.Windows.Forms.TreeView.ItemDrag></span><span class="sxs-lookup"><span data-stu-id="a43c7-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="a43c7-112">Aby rozpocząć operację przeciągania</span><span class="sxs-lookup"><span data-stu-id="a43c7-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="a43c7-113">W przypadku kontrolki, w której rozpocznie się przeciąganie, `DoDragDrop` Użyj metody, aby ustawić przeciąganie i dozwolony efekt przeciągania. <xref:System.Windows.Forms.Control.MouseDown></span><span class="sxs-lookup"><span data-stu-id="a43c7-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="a43c7-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="a43c7-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="a43c7-115">Poniższy przykład pokazuje, jak zainicjować operację przeciągania.</span><span class="sxs-lookup"><span data-stu-id="a43c7-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="a43c7-116">Formant, w którym rozpoczyna się przeciąganie, jest <xref:System.Windows.Forms.Button> formantem, przeciągane dane są ciągiem <xref:System.Windows.Forms.Control.Text%2A> reprezentującym Właściwość <xref:System.Windows.Forms.Button> kontrolki, a dozwolone efekty są kopiowane lub przenoszone.</span><span class="sxs-lookup"><span data-stu-id="a43c7-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="a43c7-117">Wszystkie dane mogą być używane jako parametr w `DoDragDrop` metodzie; w powyższym przykładzie <xref:System.Windows.Forms.Control.Text%2A> Właściwość <xref:System.Windows.Forms.Button> kontrolki została użyta (zamiast kodowaniem twardą wartości lub pobraniem danych z zestawu danych), ponieważ właściwość została powiązana z lokalizacja, z której jest przeciągany <xref:System.Windows.Forms.Button> (kontrolka).</span><span class="sxs-lookup"><span data-stu-id="a43c7-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="a43c7-118">Należy pamiętać o uwzględnieniu operacji przeciągania i upuszczania w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="a43c7-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="a43c7-119">Podczas operacji przeciągania można obsłużyć <xref:System.Windows.Forms.Control.QueryContinueDrag> zdarzenie, które "Zażądaj uprawnienia" systemu do kontynuowania operacji przeciągania.</span><span class="sxs-lookup"><span data-stu-id="a43c7-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="a43c7-120">W przypadku obsługi tej metody jest również odpowiednim punktem, aby wywołać metody, które będą miały wpływ na operację przeciągania, na przykład rozszerzając element <xref:System.Windows.Forms.TreeNode> <xref:System.Windows.Forms.TreeView> w kontrolce, gdy kursor znajduje się nad nim.</span><span class="sxs-lookup"><span data-stu-id="a43c7-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="a43c7-121">Usuwanie danych</span><span class="sxs-lookup"><span data-stu-id="a43c7-121">Dropping Data</span></span>  
 <span data-ttu-id="a43c7-122">Po rozpoczęciu przeciągania danych z lokalizacji w formularzu lub kontrolce systemu Windows można w naturalny sposób upuścić je w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="a43c7-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="a43c7-123">Kursor zmieni się po przekroczeniu obszaru formularza lub kontrolki, która jest prawidłowo skonfigurowana do upuszczania danych.</span><span class="sxs-lookup"><span data-stu-id="a43c7-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="a43c7-124">Każdy obszar w formularzu lub kontrolce systemu Windows można wprowadzić w celu zaakceptowania porzuconych danych przez ustawienie <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości <xref:System.Windows.Forms.Control.DragDrop> i <xref:System.Windows.Forms.Control.DragEnter> obsługę zdarzeń i.</span><span class="sxs-lookup"><span data-stu-id="a43c7-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="a43c7-125">Aby wykonać upuszczanie</span><span class="sxs-lookup"><span data-stu-id="a43c7-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="a43c7-126"><xref:System.Windows.Forms.Control.AllowDrop%2A> Ustaw właściwość na wartość true.</span><span class="sxs-lookup"><span data-stu-id="a43c7-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="a43c7-127">W przypadku kontrolki, w której nastąpi upuszczenie, upewnij się, że przeciągane dane mają akceptowalny typ (w tym <xref:System.Windows.Forms.Control.Text%2A>przypadku). `DragEnter`</span><span class="sxs-lookup"><span data-stu-id="a43c7-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="a43c7-128">Następnie kod ustawia efekt, który zostanie wykonany, gdy porzucanie będzie miało wartość w <xref:System.Windows.Forms.DragDropEffects> wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="a43c7-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="a43c7-129">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="a43c7-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="a43c7-130">Można zdefiniować <xref:System.Windows.Forms.DataFormats> własne, określając własny obiekt <xref:System.Object> jako parametr <xref:System.Windows.Forms.DataObject.SetData%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a43c7-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="a43c7-131">Upewnij się, że w tym przypadku obiekt jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="a43c7-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="a43c7-132">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="a43c7-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="a43c7-133">W przypadku kontrolki, w której nastąpi upuszczenie, <xref:System.Windows.Forms.DataObject.GetData%2A> Użyj metody, aby pobrać przeciągane dane. <xref:System.Windows.Forms.Control.DragDrop></span><span class="sxs-lookup"><span data-stu-id="a43c7-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="a43c7-134">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="a43c7-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="a43c7-135">W poniższym <xref:System.Windows.Forms.TextBox> przykładzie formant jest przeciągany do (w którym wystąpił spadek).</span><span class="sxs-lookup"><span data-stu-id="a43c7-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="a43c7-136">Kod ustawia <xref:System.Windows.Forms.Control.Text%2A> Właściwość <xref:System.Windows.Forms.TextBox> kontrolki równej przeciąganym danym.</span><span class="sxs-lookup"><span data-stu-id="a43c7-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="a43c7-137">Ponadto można korzystać z <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> właściwości, tak aby w zależności od kluczy podczas operacji przeciągania i upuszczania wystąpił pewne efekty (na przykład standardowe do kopiowania przeciąganych danych po naciśnięciu klawisza Ctrl).</span><span class="sxs-lookup"><span data-stu-id="a43c7-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a43c7-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a43c7-138">See also</span></span>

- [<span data-ttu-id="a43c7-139">Instrukcje: Dodawanie danych do schowka</span><span class="sxs-lookup"><span data-stu-id="a43c7-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="a43c7-140">Instrukcje: Pobieranie danych ze schowka</span><span class="sxs-lookup"><span data-stu-id="a43c7-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="a43c7-141">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="a43c7-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
