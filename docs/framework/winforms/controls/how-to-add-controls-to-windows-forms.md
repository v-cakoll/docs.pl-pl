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
ms.openlocfilehash: 72b5931a79284a93a4e0fdf3cb2cc3b03157f5f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106486"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="d94ca-102">Instrukcje: dodawanie kontrolek do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d94ca-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="d94ca-103">Większość formularzy poprzez dodawanie formantów do powierzchni formularza do definiowania interfejsu użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="d94ca-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="d94ca-104">A *kontroli* jest składnikiem w formularzu, używane do wyświetlania informacji i akceptuje dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d94ca-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="d94ca-105">Aby uzyskać więcej informacji na temat formantów, zobacz [kontrolek formularzy Windows Forms](index.md).</span><span class="sxs-lookup"><span data-stu-id="d94ca-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d94ca-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="d94ca-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d94ca-107">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="d94ca-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d94ca-108">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d94ca-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="d94ca-109">Narysuj kontrolkę w formularzu</span><span class="sxs-lookup"><span data-stu-id="d94ca-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="d94ca-110">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="d94ca-110">Open the form.</span></span> <span data-ttu-id="d94ca-111">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie formularzy Windows w Projektancie](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d94ca-111">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="d94ca-112">W **przybornika**, kliknij kontrolkę, którą chcesz dodać do formularza.</span><span class="sxs-lookup"><span data-stu-id="d94ca-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="d94ca-113">W formularzu kliknij w miejscu lewego górnego rogu kontrolki można znaleźć i przeciągnij w odpowiednie miejsce prawym dolnym rogu formantu w zlokalizowanym.</span><span class="sxs-lookup"><span data-stu-id="d94ca-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="d94ca-114">Formant jest dodawany do formularza z określonej lokalizacji i rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="d94ca-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d94ca-115">Każda kontrolka ma domyślny rozmiar zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d94ca-115">Each control has a default size defined.</span></span> <span data-ttu-id="d94ca-116">Można dodać formant do formularza w formantu domyślny rozmiar, przeciągając go z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="d94ca-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="d94ca-117">Przeciągnij formant do formularza</span><span class="sxs-lookup"><span data-stu-id="d94ca-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="d94ca-118">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="d94ca-118">Open the form.</span></span> <span data-ttu-id="d94ca-119">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie formularzy Windows w Projektancie](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d94ca-119">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="d94ca-120">W **przybornika**, ma miejsce kliknięcie kontrolki i przeciągnij je do formularza.</span><span class="sxs-lookup"><span data-stu-id="d94ca-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="d94ca-121">Formant jest dodawany do formularza w określonej lokalizacji w jej domyślny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="d94ca-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d94ca-122">Możesz kliknąć dwukrotnie formant w **przybornika** Aby dodać go do lewego górnego rogu formularza w jej domyślny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="d94ca-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="d94ca-123">Możesz również dodać formanty dynamicznie do formularza w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d94ca-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="d94ca-124">W poniższym przykładzie kodu <xref:System.Windows.Forms.TextBox> formant zostanie dodany do formularza, gdy <xref:System.Windows.Forms.Button> kliknięciu formantu.</span><span class="sxs-lookup"><span data-stu-id="d94ca-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d94ca-125">Poniższa procedura wymaga istnienia formularza z **przycisk** kontroli `Button1`, już umieszczony na nim.</span><span class="sxs-lookup"><span data-stu-id="d94ca-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="d94ca-126">Aby programowo dodać formant do formularza</span><span class="sxs-lookup"><span data-stu-id="d94ca-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="d94ca-127">W metodzie, która obsługuje przycisku `Click` zdarzenia w obrębie klasy formularza, Wstaw kod podobne do następujących czynności, aby dodać odwołanie do zmiennej kontrolki, ustaw dla formantu `Location`i Dodaj formant.</span><span class="sxs-lookup"><span data-stu-id="d94ca-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
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
    >  <span data-ttu-id="d94ca-128">Można również dodać kod do zainicjowania inne właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="d94ca-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d94ca-129">Na komputerze lokalnym to zagrożenie bezpieczeństwa, za pośrednictwem sieci można uwidocznić, odwołując się do złośliwych `UserControl`.</span><span class="sxs-lookup"><span data-stu-id="d94ca-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="d94ca-130">Powinien to być jedynie kwestią w przypadku złośliwe osoby tworzącej szkodliwe kontrolka niestandardowa, a następnie przez Ciebie przez pomyłkę dodawania do projektu.</span><span class="sxs-lookup"><span data-stu-id="d94ca-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d94ca-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d94ca-131">See also</span></span>

- [<span data-ttu-id="d94ca-132">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d94ca-132">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="d94ca-133">Rozmieszczanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d94ca-133">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="d94ca-134">Instrukcje: zmienianie rozmiaru kontrolek na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d94ca-134">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="d94ca-135">Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d94ca-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="d94ca-136">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d94ca-136">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
