---
title: "Wskazówki: praca z formantem MaskedTextBox"
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
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 006dafe88c5db7cb1499d7c1902d295841bfb5ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="cdcce-102">Wskazówki: praca z formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="cdcce-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="cdcce-103">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="cdcce-103">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="cdcce-104">Inicjowanie <xref:System.Windows.Forms.MaskedTextBox> formantu</span><span class="sxs-lookup"><span data-stu-id="cdcce-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
-   <span data-ttu-id="cdcce-105">Przy użyciu <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> obsługi zdarzeń, aby ostrzec użytkownika, gdy znak jest niezgodna z maską</span><span class="sxs-lookup"><span data-stu-id="cdcce-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
-   <span data-ttu-id="cdcce-106">Typ do przypisywania <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości i przy użyciu <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> obsługi zdarzeń, aby ostrzec użytkownika, gdy wartość one próby przekazania nie jest prawidłowa dla typu</span><span class="sxs-lookup"><span data-stu-id="cdcce-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="cdcce-107">Tworzenie projektu i dodawanie formantu</span><span class="sxs-lookup"><span data-stu-id="cdcce-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="cdcce-108">Aby dodać do formularza maskedtextbox — formant</span><span class="sxs-lookup"><span data-stu-id="cdcce-108">To add a MaskedTextBox control to your form</span></span>  
  
1.  <span data-ttu-id="cdcce-109">Otwórz formularz, na którym chcesz umieścić <xref:System.Windows.Forms.MaskedTextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="cdcce-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2.  <span data-ttu-id="cdcce-110">Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> kontrolować z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="cdcce-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3.  <span data-ttu-id="cdcce-111">Kliknij prawym przyciskiem myszy formantu i wybierz polecenie **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="cdcce-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="cdcce-112">W **właściwości** wybierz **maski** właściwości i kliknij przycisk **...**  (wielokropkiem) obok nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="cdcce-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4.  <span data-ttu-id="cdcce-113">W **maska wprowadzania** okno dialogowe, wybierz opcję **Data krótka** maski, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cdcce-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5.  <span data-ttu-id="cdcce-114">W **właściwości** zestaw okna <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="cdcce-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="cdcce-115">Ta właściwość powoduje, że krótkich dźwiękowego dźwięk za każdym razem, gdy użytkownik próbuje znak, który narusza definicję maski wprowadzania.</span><span class="sxs-lookup"><span data-stu-id="cdcce-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="cdcce-116">Podsumowanie znaki, które obsługuje właściwość maska, zobacz sekcję uwag <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cdcce-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="cdcce-117">Błędy wejściowych użytkownika</span><span class="sxs-lookup"><span data-stu-id="cdcce-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="cdcce-118">Dodaj etykieta dymka dla odrzucone maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="cdcce-118">Add a balloon tip for rejected mask input</span></span>  
  
1.  <span data-ttu-id="cdcce-119">Wróć do **przybornika** i Dodaj <xref:System.Windows.Forms.ToolTip> do formularza.</span><span class="sxs-lookup"><span data-stu-id="cdcce-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2.  <span data-ttu-id="cdcce-120">Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> zdarzeń, który wywołuje <xref:System.Windows.Forms.ToolTip> gdy wystąpi błąd danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="cdcce-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="cdcce-121">Etykieta dymka pozostanie widoczny przez pięć sekund, lub kliknięciu przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cdcce-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="cdcce-122">Użytkownika typu, który jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="cdcce-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="cdcce-123">Dodaj etykieta dymka dla typów nieprawidłowe dane</span><span class="sxs-lookup"><span data-stu-id="cdcce-123">Add a balloon tip for invalid data types</span></span>  
  
1.  <span data-ttu-id="cdcce-124">Do formularza <xref:System.Windows.Forms.Form.Load> program obsługi zdarzeń, Przypisz <xref:System.Type> reprezentujący obiekt <xref:System.DateTime> typ <xref:System.Windows.Forms.MaskedTextBox> formantu <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości:</span><span class="sxs-lookup"><span data-stu-id="cdcce-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  <span data-ttu-id="cdcce-125">Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="cdcce-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cdcce-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cdcce-126">See Also</span></span>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [<span data-ttu-id="cdcce-127">MaskedTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="cdcce-127">MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)
