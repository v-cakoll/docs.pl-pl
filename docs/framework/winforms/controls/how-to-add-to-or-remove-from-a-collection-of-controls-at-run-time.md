---
title: 'Porady: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 369946581847b4bdcf8bc658aeb94b14c529061c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182290"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="d77b6-102">Porady: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="d77b6-102">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="d77b6-103">Typowe zadania w tworzeniu aplikacji są dodawanie formantów i usuwanie formantów z dowolnego formantu kontenera w formularzach (takich jak <xref:System.Windows.Forms.Panel> lub <xref:System.Windows.Forms.GroupBox> formantu, a nawet sam formularz).</span><span class="sxs-lookup"><span data-stu-id="d77b6-103">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="d77b6-104">W czasie projektowania formanty mogą być przeciągane bezpośrednio na pole panelu lub grupy.</span><span class="sxs-lookup"><span data-stu-id="d77b6-104">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="d77b6-105">W czasie wykonywania te `Controls` formanty obsługi kolekcji, która śledzi, jakie formanty są umieszczane na nich.</span><span class="sxs-lookup"><span data-stu-id="d77b6-105">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d77b6-106">Poniższy przykład kodu ma zastosowanie do dowolnego formantu, który utrzymuje kolekcję formantów w nim.</span><span class="sxs-lookup"><span data-stu-id="d77b6-106">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="d77b6-107">Aby programowo dodać formant do kolekcji</span><span class="sxs-lookup"><span data-stu-id="d77b6-107">To add a control to a collection programmatically</span></span>  
  
1. <span data-ttu-id="d77b6-108">Utwórz wystąpienie formantu, które ma zostać dodane.</span><span class="sxs-lookup"><span data-stu-id="d77b6-108">Create an instance of the control to be added.</span></span>  
  
2. <span data-ttu-id="d77b6-109">Ustaw właściwości nowego formantu.</span><span class="sxs-lookup"><span data-stu-id="d77b6-109">Set properties of the new control.</span></span>  
  
3. <span data-ttu-id="d77b6-110">Dodaj formant `Controls` do kolekcji formantu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d77b6-110">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="d77b6-111">Poniższy przykład kodu pokazuje, jak <xref:System.Windows.Forms.Button> utworzyć wystąpienie formantu.</span><span class="sxs-lookup"><span data-stu-id="d77b6-111">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="d77b6-112">Wymaga formularza z <xref:System.Windows.Forms.Panel> formantem i że metoda obsługi zdarzeń `NewPanelButton_Click`dla tworzonego przycisku , już istnieje.</span><span class="sxs-lookup"><span data-stu-id="d77b6-112">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="d77b6-113">Aby programowo usunąć formanty z kolekcji</span><span class="sxs-lookup"><span data-stu-id="d77b6-113">To remove controls from a collection programmatically</span></span>  
  
1. <span data-ttu-id="d77b6-114">Usuń program obsługi zdarzeń ze zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d77b6-114">Remove the event handler from the event.</span></span> <span data-ttu-id="d77b6-115">W języku Visual Basic użyj słowa kluczowego [RemoveHandler Statement;](../../../visual-basic/language-reference/statements/removehandler-statement.md) w języku C#, użyj [operatora -=](../../../csharp/language-reference/operators/subtraction-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d77b6-115">In Visual Basic, use the [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) keyword; in C#, use the [-= operator](../../../csharp/language-reference/operators/subtraction-operator.md).</span></span>  
  
2. <span data-ttu-id="d77b6-116">Użyj `Remove` metody, aby usunąć żądany formant z kolekcji `Controls` panelu.</span><span class="sxs-lookup"><span data-stu-id="d77b6-116">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3. <span data-ttu-id="d77b6-117">Wywołanie <xref:System.Windows.Forms.Control.Dispose%2A> metody, aby zwolnić wszystkie zasoby używane przez formant.</span><span class="sxs-lookup"><span data-stu-id="d77b6-117">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d77b6-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d77b6-118">See also</span></span>

- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="d77b6-119">Panel — Formant</span><span class="sxs-lookup"><span data-stu-id="d77b6-119">Panel Control</span></span>](panel-control-windows-forms.md)
