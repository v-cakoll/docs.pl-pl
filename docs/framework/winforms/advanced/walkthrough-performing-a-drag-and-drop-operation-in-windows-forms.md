---
title: 'Instruktaż: Wykonywanie operacji przeciągania i upuszczania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182440"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="df81f-102">Wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="df81f-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="df81f-103">Aby wykonać operacje przeciągania i upuszczania w aplikacjach opartych <xref:System.Windows.Forms.Control.DragEnter>na <xref:System.Windows.Forms.Control.DragLeave>systemie <xref:System.Windows.Forms.Control.DragDrop> Windows, należy obsługiwać serię zdarzeń, w szczególności , i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="df81f-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="df81f-104">Pracując z informacjami dostępnymi w argumentach zdarzeń tych zdarzeń, można łatwo ułatwić operacje przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="df81f-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="df81f-105">Przeciąganie danych</span><span class="sxs-lookup"><span data-stu-id="df81f-105">Dragging Data</span></span>  
 <span data-ttu-id="df81f-106">Wszystkie operacje przeciągania i upuszczania rozpoczynają się od przeciągania.</span><span class="sxs-lookup"><span data-stu-id="df81f-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="df81f-107">Funkcja umożliwiająca zbieranie danych podczas przeciągania rozpoczyna się <xref:System.Windows.Forms.Control.DoDragDrop%2A> zaimplementowana w metodzie.</span><span class="sxs-lookup"><span data-stu-id="df81f-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="df81f-108">W poniższym przykładzie <xref:System.Windows.Forms.Control.MouseDown> zdarzenie jest używane do rozpoczęcia operacji przeciągania, ponieważ jest najbardziej intuicyjne (większość akcji przeciągania i upuszczania rozpoczyna się od wciśnięciu przycisku myszy).</span><span class="sxs-lookup"><span data-stu-id="df81f-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="df81f-109">Należy jednak pamiętać, że każde zdarzenie może służyć do inicjowania procedury przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="df81f-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df81f-110">Niektóre formanty mają niestandardowe zdarzenia specyficzne dla przeciągania.</span><span class="sxs-lookup"><span data-stu-id="df81f-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="df81f-111">I <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> formanty, na <xref:System.Windows.Forms.TreeView.ItemDrag> przykład, mają zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="df81f-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="df81f-112">Aby rozpocząć operację przeciągania</span><span class="sxs-lookup"><span data-stu-id="df81f-112">To start a drag operation</span></span>  
  
1. <span data-ttu-id="df81f-113">W <xref:System.Windows.Forms.Control.MouseDown> przypadku formantu, w którym rozpocznie `DoDragDrop` się przeciąganie, użyj metody, aby ustawić dane do przeciągania i będzie miało dozwolony efekt przeciągania.</span><span class="sxs-lookup"><span data-stu-id="df81f-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="df81f-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="df81f-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="df81f-115">W poniższym przykładzie pokazano, jak zainicjować operację przeciągania.</span><span class="sxs-lookup"><span data-stu-id="df81f-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="df81f-116">Formant, w którym <xref:System.Windows.Forms.Button> rozpoczyna się przeciąganie jest formantem, dane przeciągane jest ciąg reprezentujący <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> formantu, a dozwolone efekty są kopiowanie lub przenoszenie.</span><span class="sxs-lookup"><span data-stu-id="df81f-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    > <span data-ttu-id="df81f-117">Wszelkie dane mogą być używane `DoDragDrop` jako parametr w metodzie; w powyższym przykładzie <xref:System.Windows.Forms.Control.Text%2A> użyto właściwości <xref:System.Windows.Forms.Button> formantu (zamiast twardego kodowania wartości lub pobierania danych z zestawu danych), ponieważ właściwość <xref:System.Windows.Forms.Button> była powiązana z lokalizacją przeciąganą z (formant).</span><span class="sxs-lookup"><span data-stu-id="df81f-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="df81f-118">Należy o tym pamiętać, włączanie operacji przeciągania i upuszczania do aplikacji opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="df81f-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="df81f-119">Podczas operacji przeciągania jest w <xref:System.Windows.Forms.Control.QueryContinueDrag> życie, można obsłużyć zdarzenie, które "prosi uprawnienia" systemu, aby kontynuować operację przeciągania.</span><span class="sxs-lookup"><span data-stu-id="df81f-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="df81f-120">Podczas obsługi tej metody, jest również odpowiedni punkt do wywołania metod, które będą miały <xref:System.Windows.Forms.TreeNode> wpływ <xref:System.Windows.Forms.TreeView> na operację przeciągania, takich jak rozwijanie w formancie, gdy kursor najeżdża nad nim.</span><span class="sxs-lookup"><span data-stu-id="df81f-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="df81f-121">Upuszczanie danych</span><span class="sxs-lookup"><span data-stu-id="df81f-121">Dropping Data</span></span>  
 <span data-ttu-id="df81f-122">Po rozpoczęciu przeciągania danych z lokalizacji w formularzu systemu Windows lub formancie, naturalnie chcesz go gdzieś upuścić.</span><span class="sxs-lookup"><span data-stu-id="df81f-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="df81f-123">Kursor zmieni się po przekroczeniu obszaru formularza lub formantu, który jest poprawnie skonfigurowany do upuszczania danych.</span><span class="sxs-lookup"><span data-stu-id="df81f-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="df81f-124">Każdy obszar w formularzu systemu Windows lub formantu <xref:System.Windows.Forms.Control.AllowDrop%2A> można dokonać, aby zaakceptować porzucone dane, ustawiając właściwość i obsługi <xref:System.Windows.Forms.Control.DragEnter> zdarzeń. <xref:System.Windows.Forms.Control.DragDrop></span><span class="sxs-lookup"><span data-stu-id="df81f-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="df81f-125">Aby wykonać upuszczenie</span><span class="sxs-lookup"><span data-stu-id="df81f-125">To perform a drop</span></span>  
  
1. <span data-ttu-id="df81f-126">Ustaw <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwość na true.</span><span class="sxs-lookup"><span data-stu-id="df81f-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2. <span data-ttu-id="df81f-127">W `DragEnter` przypadku formantu, w którym nastąpi upuszczenie, upewnij się, że przeciągane dane są akceptowalnym typem (w tym przypadku). <xref:System.Windows.Forms.Control.Text%2A></span><span class="sxs-lookup"><span data-stu-id="df81f-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="df81f-128">Kod następnie ustawia efekt, który nastąpi, gdy spadek <xref:System.Windows.Forms.DragDropEffects> wystąpi do wartości w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="df81f-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="df81f-129">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="df81f-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    > <span data-ttu-id="df81f-130">Można zdefiniować <xref:System.Windows.Forms.DataFormats> własne, określając własny obiekt <xref:System.Object> jako <xref:System.Windows.Forms.DataObject.SetData%2A> parametr metody.</span><span class="sxs-lookup"><span data-stu-id="df81f-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="df81f-131">Upewnij się, że podczas wykonywania tej pracy, że obiekt określony jest serializable.</span><span class="sxs-lookup"><span data-stu-id="df81f-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="df81f-132">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="df81f-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3. <span data-ttu-id="df81f-133">W <xref:System.Windows.Forms.Control.DragDrop> przypadku formantu, w którym nastąpi <xref:System.Windows.Forms.DataObject.GetData%2A> upuszczenie, użyj metody, aby pobrać przeciągane dane.</span><span class="sxs-lookup"><span data-stu-id="df81f-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="df81f-134">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="df81f-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="df81f-135">W poniższym przykładzie formant <xref:System.Windows.Forms.TextBox> jest formant przeciągany do (gdzie nastąpi spadek).</span><span class="sxs-lookup"><span data-stu-id="df81f-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="df81f-136">Kod ustawia <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.TextBox> formantu równa przeciąganych danych.</span><span class="sxs-lookup"><span data-stu-id="df81f-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    > <span data-ttu-id="df81f-137">Ponadto można pracować z <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> właściwością, dzięki czemu, w zależności od klawiszy wciśnięty podczas operacji przeciągania i upuszczania, pewne efekty występują (na przykład jest standardem kopiowania przeciągniętych danych po naciśnięciu klawisza CTRL).</span><span class="sxs-lookup"><span data-stu-id="df81f-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df81f-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df81f-138">See also</span></span>

- [<span data-ttu-id="df81f-139">Instrukcje: dodawanie danych do schowka</span><span class="sxs-lookup"><span data-stu-id="df81f-139">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="df81f-140">Instrukcje: pobieranie danych ze schowka</span><span class="sxs-lookup"><span data-stu-id="df81f-140">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="df81f-141">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="df81f-141">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
