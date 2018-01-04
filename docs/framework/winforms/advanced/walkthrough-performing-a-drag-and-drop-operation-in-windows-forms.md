---
title: "Wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows"
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
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173af57f1ec5d9ed14afc0ef5d6ddd391e15d534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="d7121-102">Wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d7121-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="d7121-103">Wykonywanie operacji przeciągania i upuszczania w aplikacjach opartych na systemie Windows musi obsługiwać szereg zdarzeń, głównie <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d7121-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="d7121-104">Praca z informacji dostępnych w przypadku argumentów te zdarzenia, można łatwo ułatwienia operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="d7121-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="d7121-105">Przeciąganie danych</span><span class="sxs-lookup"><span data-stu-id="d7121-105">Dragging Data</span></span>  
 <span data-ttu-id="d7121-106">Wszystkie operacje przeciągania i upuszczania zaczynać przeciągania.</span><span class="sxs-lookup"><span data-stu-id="d7121-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="d7121-107">Funkcje umożliwiające podczas przeciągania rozpoczyna zbieranie danych jest zaimplementowana w <xref:System.Windows.Forms.Control.DoDragDrop%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d7121-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="d7121-108">W poniższym przykładzie <xref:System.Windows.Forms.Control.MouseDown> zdarzenia są używane do uruchamiania operacji przeciągania, ponieważ jest najbardziej intuicyjnego (Większość akcji przeciągania i upuszczania zaczynać się przycisk myszy jest wciśnięty).</span><span class="sxs-lookup"><span data-stu-id="d7121-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="d7121-109">Należy jednak pamiętać, że wszystkie zdarzenia może posłużyć do zainicjowania procedury przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="d7121-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7121-110">Niektóre formanty ma niestandardowych zdarzeń specyficznych dla przeciągania.</span><span class="sxs-lookup"><span data-stu-id="d7121-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="d7121-111"><xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView> kontrolki, na przykład mieć <xref:System.Windows.Forms.TreeView.ItemDrag> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d7121-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="d7121-112">Aby uruchomić operację przeciągania</span><span class="sxs-lookup"><span data-stu-id="d7121-112">To start a drag operation</span></span>  
  
1.  <span data-ttu-id="d7121-113">W <xref:System.Windows.Forms.Control.MouseDown> zdarzeń dla formantu, gdzie rozpocznie przeciąganie, użyj `DoDragDrop` ma metodę, aby ustawić dane do przeciąganych i dozwolonym efektem przeciągania.</span><span class="sxs-lookup"><span data-stu-id="d7121-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="d7121-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7121-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="d7121-115">Poniższy przykład pokazuje, jak zainicjować operacji przeciągania.</span><span class="sxs-lookup"><span data-stu-id="d7121-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="d7121-116">Formant, gdzie zaczyna się przeciągania jest <xref:System.Windows.Forms.Button> kontroli, dane przeciągane jest ciąg reprezentujący <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> kontroli i dozwolone efekty są kopiowania lub przenoszenia.</span><span class="sxs-lookup"><span data-stu-id="d7121-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
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
    >  <span data-ttu-id="d7121-117">Wszystkie dane mogą być używane jako parametru w `DoDragDrop` — metoda; w powyższym przykładzie <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> formant został użyty (zamiast kodować wartość lub pobieranie danych z zestawu danych) ponieważ właściwość nie została powiązana z przeciąganie z lokalizacji ( <xref:System.Windows.Forms.Button> kontroli).</span><span class="sxs-lookup"><span data-stu-id="d7121-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="d7121-118">Należy to pamiętać, jak zastosować operacji przeciągania i upuszczania w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="d7121-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="d7121-119">Podczas operacji przeciągania jest włączone, można obsługiwać <xref:System.Windows.Forms.Control.QueryContinueDrag> zdarzenie, które "prosi o uprawnienie" systemu, aby kontynuować operację przeciągania.</span><span class="sxs-lookup"><span data-stu-id="d7121-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="d7121-120">Podczas przetwarzania tej metody, jest również odpowiedniego punktu można wywoływać metod, które będą miały wpływu na operację przeciągania, takich jak rozszerzanie <xref:System.Windows.Forms.TreeNode> w <xref:System.Windows.Forms.TreeView> kontroli, gdy kursor znajduje się nad nim.</span><span class="sxs-lookup"><span data-stu-id="d7121-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="d7121-121">Usuwanie danych</span><span class="sxs-lookup"><span data-stu-id="d7121-121">Dropping Data</span></span>  
 <span data-ttu-id="d7121-122">Po rozpoczęciu przeciąganie danych z lokalizacji w formularzu systemu Windows lub kontrolki, należy naturalny Porzuć go innym.</span><span class="sxs-lookup"><span data-stu-id="d7121-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="d7121-123">Kursor ulegnie zmianie po jego przecina obszaru formularz lub formant, który jest poprawnie skonfigurowany dla usunięcie danych.</span><span class="sxs-lookup"><span data-stu-id="d7121-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="d7121-124">Każdy obszar w formularzu systemu Windows lub formant może również akceptować dane porzuconych przez ustawienie <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości i obsługa <xref:System.Windows.Forms.Control.DragEnter> i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d7121-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="d7121-125">Aby wykonać spadek</span><span class="sxs-lookup"><span data-stu-id="d7121-125">To perform a drop</span></span>  
  
1.  <span data-ttu-id="d7121-126">Ustaw <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości na wartość true.</span><span class="sxs-lookup"><span data-stu-id="d7121-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2.  <span data-ttu-id="d7121-127">W `DragEnter` zdarzeń dla formantu, gdy nastąpi spadek Sprawdź, czy dane przeciągane jest dopuszczalne typu (w tym przypadku <xref:System.Windows.Forms.Control.Text%2A>).</span><span class="sxs-lookup"><span data-stu-id="d7121-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="d7121-128">Kod następnie ustawia efekt, który nastąpi po wartości w polu listy <xref:System.Windows.Forms.DragDropEffects> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d7121-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="d7121-129">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7121-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
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
    >  <span data-ttu-id="d7121-130">Można definiować własnych <xref:System.Windows.Forms.DataFormats> , określając obiektu jako <xref:System.Object> parametr <xref:System.Windows.Forms.DataObject.SetData%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d7121-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="d7121-131">Upewnij się, gdy spowoduje to, że określony obiekt jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="d7121-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="d7121-132">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="d7121-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3.  <span data-ttu-id="d7121-133">W <xref:System.Windows.Forms.Control.DragDrop> zdarzeń dla formantu, gdzie nastąpi spadek użyj <xref:System.Windows.Forms.DataObject.GetData%2A> metody do pobierania danych przeciągania.</span><span class="sxs-lookup"><span data-stu-id="d7121-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="d7121-134">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7121-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="d7121-135">W poniższym przykładzie <xref:System.Windows.Forms.TextBox> formant jest formantem przeciąganego (listy będą mieć miejsce).</span><span class="sxs-lookup"><span data-stu-id="d7121-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="d7121-136">Ustawia kod <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.TextBox> kontrolować równa dane przeciągane.</span><span class="sxs-lookup"><span data-stu-id="d7121-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
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
    >  <span data-ttu-id="d7121-137">Ponadto możesz pracować z <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> właściwości, dzięki czemu w zależności od klucze wciśnięty podczas operacji przeciągania i upuszczania niektórych występują skutki (na przykład jest standard, aby skopiować dane przeciąganego, gdy zostanie naciśnięty klawisz CTRL).</span><span class="sxs-lookup"><span data-stu-id="d7121-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7121-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7121-138">See Also</span></span>  
 [<span data-ttu-id="d7121-139">Instrukcje: dodawanie danych do schowka</span><span class="sxs-lookup"><span data-stu-id="d7121-139">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [<span data-ttu-id="d7121-140">Instrukcje: pobieranie danych ze schowka</span><span class="sxs-lookup"><span data-stu-id="d7121-140">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [<span data-ttu-id="d7121-141">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="d7121-141">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
