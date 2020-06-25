---
title: Dodawanie kontrolek
description: Dowiedz się, jak narysować kontrolkę w formularzu systemu Windows. Kontrolka jest składnikiem formularza, którego można użyć do wyświetlania informacji lub akceptowania danych wejściowych użytkownika.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: d9ab0d78fa0153cce20fb17d22f6e9e781229ece
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325887"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="e32bc-104">Porady: dodawanie formantów do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e32bc-104">How to: Add Controls to Windows Forms</span></span>

<span data-ttu-id="e32bc-105">Większość formularzy służy do dodawania kontrolek do powierzchni formularza w celu zdefiniowania interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e32bc-105">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="e32bc-106">*Kontrolka* to składnik formularza służący do wyświetlania informacji lub akceptowania danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e32bc-106">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="e32bc-107">Aby uzyskać więcej informacji na temat kontrolek, zobacz [Windows Forms Controls](index.md).</span><span class="sxs-lookup"><span data-stu-id="e32bc-107">For more information about controls, see [Windows Forms Controls](index.md).</span></span>

## <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="e32bc-108">Aby narysować kontrolkę w formularzu</span><span class="sxs-lookup"><span data-stu-id="e32bc-108">To draw a control on a form</span></span>

1. <span data-ttu-id="e32bc-109">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="e32bc-109">Open the form.</span></span> <span data-ttu-id="e32bc-110">Aby uzyskać więcej informacji, zobacz [How to: Display Windows Forms in a Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e32bc-110">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="e32bc-111">W **przyborniku**kliknij kontrolkę, którą chcesz dodać do formularza.</span><span class="sxs-lookup"><span data-stu-id="e32bc-111">In the **Toolbox**, click the control you want to add to your form.</span></span>

3. <span data-ttu-id="e32bc-112">Na formularzu kliknij miejsce w lewym górnym rogu kontrolki, a następnie przeciągnij do miejsca, w którym ma się znajdować prawy dolny róg kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e32bc-112">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>

    <span data-ttu-id="e32bc-113">Kontrolka zostanie dodana do formularza z określoną lokalizacją i rozmiarem.</span><span class="sxs-lookup"><span data-stu-id="e32bc-113">The control is added to the form with the specified location and size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e32bc-114">Każdy formant ma zdefiniowany rozmiar domyślny.</span><span class="sxs-lookup"><span data-stu-id="e32bc-114">Each control has a default size defined.</span></span> <span data-ttu-id="e32bc-115">Możesz dodać formant do formularza w domyślnym rozmiarze kontrolki, przeciągając go z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="e32bc-115">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>

## <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="e32bc-116">Aby przeciągnąć formant do formularza</span><span class="sxs-lookup"><span data-stu-id="e32bc-116">To drag a control to a form</span></span>

1. <span data-ttu-id="e32bc-117">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="e32bc-117">Open the form.</span></span> <span data-ttu-id="e32bc-118">Aby uzyskać więcej informacji, zobacz [How to: Display Windows Forms in a Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e32bc-118">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="e32bc-119">W **przyborniku**kliknij żądany formant i przeciągnij go do formularza.</span><span class="sxs-lookup"><span data-stu-id="e32bc-119">In the **Toolbox**, click the control you want and drag it to your form.</span></span>

    <span data-ttu-id="e32bc-120">Kontrolka jest dodawana do formularza w określonej lokalizacji w domyślnym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="e32bc-120">The control is added to the form at the specified location in its default size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e32bc-121">Możesz dwukrotnie kliknąć kontrolkę w **przyborniku** , aby dodać ją do lewego górnego rogu formularza w domyślnym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="e32bc-121">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>

    <span data-ttu-id="e32bc-122">Kontrolki można także dynamicznie dodawać do formularza w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e32bc-122">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="e32bc-123">W poniższym przykładzie kodu <xref:System.Windows.Forms.TextBox> formant zostanie dodany do formularza, gdy zostanie <xref:System.Windows.Forms.Button> kliknięty formant.</span><span class="sxs-lookup"><span data-stu-id="e32bc-123">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e32bc-124">Poniższa procedura wymaga istnienia formularza z kontrolką **przycisku** , która jest `Button1` już umieszczona w nim.</span><span class="sxs-lookup"><span data-stu-id="e32bc-124">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>

## <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="e32bc-125">Aby programowo dodać formant do formularza</span><span class="sxs-lookup"><span data-stu-id="e32bc-125">To add a control to a form programmatically</span></span>

1. <span data-ttu-id="e32bc-126">W metodzie, która obsługuje zdarzenie przycisku `Click` w klasie formularza, Wstaw kod podobny do poniższego, aby dodać odwołanie do zmiennej kontroli, ustaw kontrolkę `Location` i Dodaj kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="e32bc-126">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>

    ```vb
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim MyText As New TextBox()
       MyText.Location = New Point(25, 25)
       Me.Controls.Add(MyText)
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
       TextBox myText = new TextBox();
       myText.Location = new Point(25,25);
       this.Controls.Add (myText);
    }
    ```

    ```cpp
    private:
      System::Void button1_Click(System::Object ^  sender,
        System::EventArgs ^  e)
      {
        TextBox ^ myText = gcnew TextBox();
        myText->Location = Point(25,25);
        this->Controls->Add(myText);
      }
    ```

    > [!NOTE]
    > <span data-ttu-id="e32bc-127">Możesz również dodać kod, aby zainicjować inne właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="e32bc-127">You can also add code to initialize other properties of the control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e32bc-128">Komputer lokalny może być narażony na zagrożenia bezpieczeństwa przez sieć, odwołując się do złośliwej `UserControl` .</span><span class="sxs-lookup"><span data-stu-id="e32bc-128">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="e32bc-129">Może to stanowić problem tylko w przypadku złośliwej osoby, która tworzy szkodliwą kontrolkę niestandardową, a następnie nie dodawaj jej do projektu.</span><span class="sxs-lookup"><span data-stu-id="e32bc-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="e32bc-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e32bc-130">See also</span></span>

- [<span data-ttu-id="e32bc-131">Kontrolki Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e32bc-131">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="e32bc-132">Porady: zmienianie rozmiaru formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e32bc-132">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="e32bc-133">Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e32bc-133">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="e32bc-134">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e32bc-134">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
