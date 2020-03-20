---
title: 'Wskazówki: praca z formantem MaskedTextBox'
ms.date: 03/30/2017
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
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182046"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="a8dbb-102">Wskazówki: praca z formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="a8dbb-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="a8dbb-103">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="a8dbb-103">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="a8dbb-104">Inicjowanie <xref:System.Windows.Forms.MaskedTextBox> formantu</span><span class="sxs-lookup"><span data-stu-id="a8dbb-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
- <span data-ttu-id="a8dbb-105">Za <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> pomocą programu obsługi zdarzeń, aby ostrzec użytkownika, gdy znak nie jest zgodny z maską</span><span class="sxs-lookup"><span data-stu-id="a8dbb-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
- <span data-ttu-id="a8dbb-106">Przypisywanie typu do <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości i <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> używanie programu obsługi zdarzeń do ostrzegania użytkownika, gdy wartość, którą próbują zatwierdzić, jest nieprawidłowa dla tego typu</span><span class="sxs-lookup"><span data-stu-id="a8dbb-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="a8dbb-107">Tworzenie projektu i dodawanie formantu</span><span class="sxs-lookup"><span data-stu-id="a8dbb-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="a8dbb-108">Aby dodać formant MaskedTextBox do formularza</span><span class="sxs-lookup"><span data-stu-id="a8dbb-108">To add a MaskedTextBox control to your form</span></span>  
  
1. <span data-ttu-id="a8dbb-109">Otwórz formularz, w którym chcesz <xref:System.Windows.Forms.MaskedTextBox> umieścić formant.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2. <span data-ttu-id="a8dbb-110">Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> formant z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3. <span data-ttu-id="a8dbb-111">Kliknij prawym przyciskiem myszy formant i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="a8dbb-112">W oknie **Właściwości** wybierz właściwość **Mask i** kliknij przycisk **...** (wielokropek) obok nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4. <span data-ttu-id="a8dbb-113">W oknie **dialogowym Maska wprowadzania** zaznacz maskę **Data krótka** i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5. <span data-ttu-id="a8dbb-114">W oknie **Właściwości** ustaw <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> właściwość na `true`.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="a8dbb-115">Ta właściwość powoduje, że krótki sygnał dźwiękowy do dźwięku za każdym razem, gdy użytkownik próbuje wprowadzić znak, który narusza definicję maski.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="a8dbb-116">Aby uzyskać podsumowanie znaków, które maskuje właściwość, zobacz <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> uwagi sekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="a8dbb-117">Ostrzeganie użytkownika o błędach wprowadzania</span><span class="sxs-lookup"><span data-stu-id="a8dbb-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="a8dbb-118">Dodawanie końcówki dymka dla odrzuconego wprowadzania maski</span><span class="sxs-lookup"><span data-stu-id="a8dbb-118">Add a balloon tip for rejected mask input</span></span>  
  
1. <span data-ttu-id="a8dbb-119">Wróć do **przybornika** <xref:System.Windows.Forms.ToolTip> i dodaj go do formularza.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2. <span data-ttu-id="a8dbb-120">Utwórz program obsługi <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> zdarzeń dla <xref:System.Windows.Forms.ToolTip> zdarzenia, które podnosi, gdy wystąpi błąd wejściowy.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="a8dbb-121">Końcówka dymka pozostaje widoczna przez pięć sekund lub do momentu kliknięcia przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a8dbb-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="a8dbb-122">Ostrzeganie użytkownika o typie, który jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="a8dbb-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="a8dbb-123">Dodawanie końcówki dymka dla nieprawidłowych typów danych</span><span class="sxs-lookup"><span data-stu-id="a8dbb-123">Add a balloon tip for invalid data types</span></span>  
  
1. <span data-ttu-id="a8dbb-124">W programie obsługi <xref:System.Windows.Forms.Form.Load> zdarzeń formularza <xref:System.Type> przypisz obiekt <xref:System.DateTime> reprezentujący <xref:System.Windows.Forms.MaskedTextBox> typ <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> do właściwości formantu:</span><span class="sxs-lookup"><span data-stu-id="a8dbb-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
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
  
2. <span data-ttu-id="a8dbb-125">Dodaj program obsługi <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> zdarzeń dla zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="a8dbb-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8dbb-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8dbb-126">See also</span></span>

- <xref:System.Windows.Forms.MaskedTextBox>
- [<span data-ttu-id="a8dbb-127">MaskedTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a8dbb-127">MaskedTextBox Control</span></span>](maskedtextbox-control-windows-forms.md)
