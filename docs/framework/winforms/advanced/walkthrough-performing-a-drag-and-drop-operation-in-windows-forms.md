---
title: 'Przewodnik: wykonywanie operacji przeciągania i upuszczania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 265e6d4f9e3370d28a18b86dea983bb0b556be41
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746793"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="0d6f8-102">Wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0d6f8-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="0d6f8-103">Aby wykonać operacje przeciągania i upuszczania w aplikacjach opartych na systemie Windows, musisz obsługiwać szereg zdarzeń, w szczególności zdarzenia <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>i <xref:System.Windows.Forms.Control.DragDrop>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="0d6f8-104">Pracując z informacjami dostępnymi w argumentach zdarzeń tych zdarzeń, można łatwo ułatwić wykonywanie operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="0d6f8-105">Przeciąganie danych</span><span class="sxs-lookup"><span data-stu-id="0d6f8-105">Dragging Data</span></span>  
 <span data-ttu-id="0d6f8-106">Wszystkie operacje przeciągania i upuszczania zaczynają się od przeciągania.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="0d6f8-107">Funkcja umożliwiająca zbieranie danych po rozpoczęciu przeciągania jest zaimplementowana w metodzie <xref:System.Windows.Forms.Control.DoDragDrop%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="0d6f8-108">W poniższym przykładzie zdarzenie <xref:System.Windows.Forms.Control.MouseDown> służy do uruchamiania operacji przeciągania, ponieważ jest najbardziej intuicyjne (większość akcji przeciągania i upuszczania zaczyna się od naciśnięcia przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="0d6f8-109">Należy jednak pamiętać, że dowolnego zdarzenia można użyć do zainicjowania procedury przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d6f8-110">Niektóre kontrolki mają niestandardowe zdarzenia dotyczące przeciągania.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="0d6f8-111">Kontrolki <xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView>, na przykład, mają zdarzenie <xref:System.Windows.Forms.TreeView.ItemDrag>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="0d6f8-112">Aby rozpocząć operację przeciągania</span><span class="sxs-lookup"><span data-stu-id="0d6f8-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="0d6f8-113">W zdarzeniu <xref:System.Windows.Forms.Control.MouseDown> dla kontrolki, w której rozpocznie się przeciąganie, użyj metody `DoDragDrop`, aby ustawić przeciąganie i dozwolony efekt przeciągania.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="0d6f8-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="0d6f8-115">Poniższy przykład pokazuje, jak zainicjować operację przeciągania.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="0d6f8-116">Kontrolka, w której rozpoczyna się przeciąganie, jest kontrolką <xref:System.Windows.Forms.Button>, przeciągane dane są ciągiem reprezentującym Właściwość <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.Button> i dozwolone efekty są kopiowane lub przenoszone.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="0d6f8-117">Wszystkie dane mogą być używane jako parametr w metodzie `DoDragDrop`; w powyższym przykładzie użyto właściwości <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.Button> (zamiast kodowania wartości lub pobierania danych z zestawu danych), ponieważ właściwość została powiązana z lokalizacją, z której jest przeciągany (kontrolka <xref:System.Windows.Forms.Button>).</span><span class="sxs-lookup"><span data-stu-id="0d6f8-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="0d6f8-118">Należy pamiętać o uwzględnieniu operacji przeciągania i upuszczania w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="0d6f8-119">Podczas operacji przeciągania można obsłużyć zdarzenie <xref:System.Windows.Forms.Control.QueryContinueDrag>, które "prosi o uprawnienia" systemu do kontynuowania operacji przeciągania.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="0d6f8-120">Podczas obsługi tej metody jest również odpowiednim punktem, aby wywołać metody, które będą miały wpływ na operację przeciągania, na przykład rozszerzając <xref:System.Windows.Forms.TreeNode> w kontrolce <xref:System.Windows.Forms.TreeView>, gdy kursor znajduje się nad nim.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="0d6f8-121">Usuwanie danych</span><span class="sxs-lookup"><span data-stu-id="0d6f8-121">Dropping Data</span></span>  
 <span data-ttu-id="0d6f8-122">Po rozpoczęciu przeciągania danych z lokalizacji w formularzu lub kontrolce systemu Windows można w naturalny sposób upuścić je w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="0d6f8-123">Kursor zmieni się po przekroczeniu obszaru formularza lub kontrolki, która jest prawidłowo skonfigurowana do upuszczania danych.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="0d6f8-124">Każdy obszar w formularzu lub kontrolce systemu Windows można wprowadzić w celu zaakceptowania porzuconych danych przez ustawienie właściwości <xref:System.Windows.Forms.Control.AllowDrop%2A> i obsługę zdarzeń <xref:System.Windows.Forms.Control.DragEnter> i <xref:System.Windows.Forms.Control.DragDrop>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="0d6f8-125">Aby wykonać upuszczanie</span><span class="sxs-lookup"><span data-stu-id="0d6f8-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="0d6f8-126">Ustaw właściwość <xref:System.Windows.Forms.Control.AllowDrop%2A> na wartość true.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="0d6f8-127">W zdarzeniu `DragEnter` dla kontrolki, w której nastąpi upuszczenie, upewnij się, że przeciągane dane mają akceptowalny typ (w tym przypadku <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="0d6f8-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="0d6f8-128">Następnie kod ustawia efekt, który zostanie wykonany, gdy porzucanie zostanie wykonane do wartości w wyliczeniu <xref:System.Windows.Forms.DragDropEffects>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="0d6f8-129">Aby uzyskać więcej informacji, zobacz temat <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="0d6f8-130">Możesz zdefiniować własne <xref:System.Windows.Forms.DataFormats>, określając własny obiekt jako parametr <xref:System.Object> metody <xref:System.Windows.Forms.DataObject.SetData%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="0d6f8-131">Upewnij się, że w tym przypadku obiekt jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="0d6f8-132">Aby uzyskać więcej informacji, zobacz temat <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="0d6f8-133">W zdarzeniu <xref:System.Windows.Forms.Control.DragDrop> dla kontrolki, w której nastąpi upuszczenie, użyj metody <xref:System.Windows.Forms.DataObject.GetData%2A>, aby pobrać przeciągane dane.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="0d6f8-134">Aby uzyskać więcej informacji, zobacz temat <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="0d6f8-135">W poniższym przykładzie formant <xref:System.Windows.Forms.TextBox> jest przeciągany do (w którym wystąpił spadek).</span><span class="sxs-lookup"><span data-stu-id="0d6f8-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="0d6f8-136">Kod ustawia właściwość <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.TextBox> równej przeciąganym danym.</span><span class="sxs-lookup"><span data-stu-id="0d6f8-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="0d6f8-137">Ponadto można korzystać z właściwości <xref:System.Windows.Forms.DragEventArgs.KeyState%2A>, dzięki czemu w zależności od kluczy podczas operacji przeciągania i upuszczania pojawiają się pewne efekty (na przykład standardowe do kopiowania przeciąganych danych po naciśnięciu klawisza CTRL).</span><span class="sxs-lookup"><span data-stu-id="0d6f8-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6f8-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d6f8-138">See also</span></span>

- [<span data-ttu-id="0d6f8-139">Instrukcje: dodawanie danych do schowka</span><span class="sxs-lookup"><span data-stu-id="0d6f8-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="0d6f8-140">Instrukcje: pobieranie danych ze schowka</span><span class="sxs-lookup"><span data-stu-id="0d6f8-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="0d6f8-141">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="0d6f8-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
