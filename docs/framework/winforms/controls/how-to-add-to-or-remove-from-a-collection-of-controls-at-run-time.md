---
title: 'Instrukcje: Dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania'
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
ms.openlocfilehash: 88a743cc6d0a1e90d2912c9ec610fae326ff5770
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744911"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="595cd-102">Instrukcje: Dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="595cd-102">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="595cd-103">Typowe zadania podczas tworzenia aplikacji są dodawanie formantów do i usuwanie kontrolek z dowolną kontrolkę kontenera na formularzach (takie jak <xref:System.Windows.Forms.Panel> lub <xref:System.Windows.Forms.GroupBox> formantu lub nawet formularza).</span><span class="sxs-lookup"><span data-stu-id="595cd-103">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="595cd-104">W czasie projektowania formanty można przeciągać bezpośrednio okno panel lub grupę.</span><span class="sxs-lookup"><span data-stu-id="595cd-104">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="595cd-105">W czasie wykonywania, obsługa tych formantów `Controls` kolekcji, która przechowuje informacje o kontrolki są umieszczane na nich.</span><span class="sxs-lookup"><span data-stu-id="595cd-105">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="595cd-106">Poniższy przykładowy kod stosuje się do żadnego formantu, który przechowuje kolekcję zawarte w niej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="595cd-106">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="595cd-107">Aby programowo dodać formant do kolekcji</span><span class="sxs-lookup"><span data-stu-id="595cd-107">To add a control to a collection programmatically</span></span>  
  
1.  <span data-ttu-id="595cd-108">Utwórz wystąpienie kontrolki, które mają zostać dodane.</span><span class="sxs-lookup"><span data-stu-id="595cd-108">Create an instance of the control to be added.</span></span>  
  
2.  <span data-ttu-id="595cd-109">Ustaw właściwości nowego formantu.</span><span class="sxs-lookup"><span data-stu-id="595cd-109">Set properties of the new control.</span></span>  
  
3.  <span data-ttu-id="595cd-110">Dodać formant do `Controls` kolekcji do kontrolki nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="595cd-110">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="595cd-111">Poniższy przykład kodu pokazuje, jak utworzyć wystąpienie <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="595cd-111">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="595cd-112">Wymaga formularza z <xref:System.Windows.Forms.Panel> kontroli i że trwa tworzenie metody obsługi zdarzeń dla przycisku, `NewPanelButton_Click`, już istnieje.</span><span class="sxs-lookup"><span data-stu-id="595cd-112">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="595cd-113">Aby programowo usunąć formanty z kolekcji</span><span class="sxs-lookup"><span data-stu-id="595cd-113">To remove controls from a collection programmatically</span></span>  
  
1.  <span data-ttu-id="595cd-114">Usuń obsługi zdarzenia ze zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="595cd-114">Remove the event handler from the event.</span></span> <span data-ttu-id="595cd-115">W języku Visual Basic należy używać [RemoveHandler — instrukcja](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) — słowo kluczowe; w elemencie wizualnym C#, użyj [-= — Operator (C# odwołania)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="595cd-115">In Visual Basic, use the [RemoveHandler Statement](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) keyword; in Visual C#, use the [-= Operator (C# Reference)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).</span></span>  
  
2.  <span data-ttu-id="595cd-116">Użyj `Remove` metodę, aby usunąć żądanego formant na panelu `Controls` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="595cd-116">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3.  <span data-ttu-id="595cd-117">Wywołaj <xref:System.Windows.Forms.Control.Dispose%2A> metodę, aby zwolnić wszystkie zasoby, które są używane przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="595cd-117">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="595cd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="595cd-118">See also</span></span>
- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="595cd-119">Panel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="595cd-119">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
