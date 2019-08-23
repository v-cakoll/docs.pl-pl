---
title: 'Instrukcje: dodawanie kontrolek do formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 7ee603fa5350ef81c6d32d2f22119bbe526295df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912618"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="ee0af-102">Instrukcje: dodawanie kontrolek do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ee0af-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="ee0af-103">Większość formularzy służy do dodawania kontrolek do powierzchni formularza w celu zdefiniowania interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee0af-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="ee0af-104">*Kontrolka* to składnik formularza służący do wyświetlania informacji lub akceptowania danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee0af-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="ee0af-105">Aby uzyskać więcej informacji na temat kontrolek, zobacz [Windows Forms Controls](index.md).</span><span class="sxs-lookup"><span data-stu-id="ee0af-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>

## <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="ee0af-106">Aby narysować kontrolkę w formularzu</span><span class="sxs-lookup"><span data-stu-id="ee0af-106">To draw a control on a form</span></span>

1. <span data-ttu-id="ee0af-107">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="ee0af-107">Open the form.</span></span> <span data-ttu-id="ee0af-108">Aby uzyskać więcej informacji, zobacz [jak: Wyświetl Windows Forms w projektancie](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ee0af-108">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="ee0af-109">W **przyborniku**kliknij kontrolkę, którą chcesz dodać do formularza.</span><span class="sxs-lookup"><span data-stu-id="ee0af-109">In the **Toolbox**, click the control you want to add to your form.</span></span>

3. <span data-ttu-id="ee0af-110">Na formularzu kliknij miejsce w lewym górnym rogu kontrolki, a następnie przeciągnij do miejsca, w którym ma się znajdować prawy dolny róg kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ee0af-110">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>

     <span data-ttu-id="ee0af-111">Kontrolka zostanie dodana do formularza z określoną lokalizacją i rozmiarem.</span><span class="sxs-lookup"><span data-stu-id="ee0af-111">The control is added to the form with the specified location and size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ee0af-112">Każdy formant ma zdefiniowany rozmiar domyślny.</span><span class="sxs-lookup"><span data-stu-id="ee0af-112">Each control has a default size defined.</span></span> <span data-ttu-id="ee0af-113">Możesz dodać formant do formularza w domyślnym rozmiarze kontrolki, przeciągając go z przybornika do formularza .</span><span class="sxs-lookup"><span data-stu-id="ee0af-113">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>

## <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="ee0af-114">Aby przeciągnąć formant do formularza</span><span class="sxs-lookup"><span data-stu-id="ee0af-114">To drag a control to a form</span></span>

1. <span data-ttu-id="ee0af-115">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="ee0af-115">Open the form.</span></span> <span data-ttu-id="ee0af-116">Aby uzyskać więcej informacji, zobacz [jak: Wyświetl Windows Forms w projektancie](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ee0af-116">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="ee0af-117">W **przyborniku**kliknij żądany formant i przeciągnij go do formularza.</span><span class="sxs-lookup"><span data-stu-id="ee0af-117">In the **Toolbox**, click the control you want and drag it to your form.</span></span>

     <span data-ttu-id="ee0af-118">Kontrolka jest dodawana do formularza w określonej lokalizacji w domyślnym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="ee0af-118">The control is added to the form at the specified location in its default size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ee0af-119">Możesz dwukrotnie kliknąć kontrolkę w przyborniku, aby dodać ją do lewego górnego rogu formularza w domyślnym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="ee0af-119">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>

     <span data-ttu-id="ee0af-120">Kontrolki można także dynamicznie dodawać do formularza w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ee0af-120">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="ee0af-121">W poniższym przykładzie <xref:System.Windows.Forms.TextBox> kodu formant zostanie dodany do formularza, <xref:System.Windows.Forms.Button> gdy zostanie kliknięty formant.</span><span class="sxs-lookup"><span data-stu-id="ee0af-121">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ee0af-122">Poniższa procedura wymaga istnienia formularza z kontrolką `Button1` **przycisku** , która jest już umieszczona w nim.</span><span class="sxs-lookup"><span data-stu-id="ee0af-122">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>

## <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="ee0af-123">Aby programowo dodać formant do formularza</span><span class="sxs-lookup"><span data-stu-id="ee0af-123">To add a control to a form programmatically</span></span>

1. <span data-ttu-id="ee0af-124">W metodzie, która obsługuje `Click` zdarzenie przycisku w klasie formularza, Wstaw kod podobny do poniższego, aby dodać odwołanie do zmiennej kontroli, ustaw `Location`kontrolkę i Dodaj kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="ee0af-124">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>

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
    > <span data-ttu-id="ee0af-125">Możesz również dodać kod, aby zainicjować inne właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="ee0af-125">You can also add code to initialize other properties of the control.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="ee0af-126">Komputer lokalny może być narażony na zagrożenia bezpieczeństwa przez sieć, odwołując się do `UserControl`złośliwej.</span><span class="sxs-lookup"><span data-stu-id="ee0af-126">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="ee0af-127">Może to stanowić problem tylko w przypadku złośliwej osoby, która tworzy szkodliwą kontrolkę niestandardową, a następnie nie dodawaj jej do projektu.</span><span class="sxs-lookup"><span data-stu-id="ee0af-127">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee0af-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee0af-128">See also</span></span>

- [<span data-ttu-id="ee0af-129">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee0af-129">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="ee0af-130">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee0af-130">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="ee0af-131">Instrukcje: Zmień rozmiar kontrolek na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee0af-131">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="ee0af-132">Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee0af-132">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="ee0af-133">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee0af-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
