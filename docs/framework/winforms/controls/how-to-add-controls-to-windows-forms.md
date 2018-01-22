---
title: "Porady: dodawanie formantów do formularzy systemu Windows"
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
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab92f7a56173ec71642d0cc09f3f81e9859533b4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="a9878-102">Porady: dodawanie formantów do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a9878-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="a9878-103">Większość formularzy przez dodawanie formantów do powierzchni formularza do definiowania interfejsu użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="a9878-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="a9878-104">A *kontroli* jest składnikiem w formularzu używane do wyświetlania informacji i akceptowanie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a9878-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="a9878-105">Aby uzyskać więcej informacji na temat formantów, zobacz [formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9878-105">For more information about controls, see [Windows Forms Controls](../../../../docs/framework/winforms/controls/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9878-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="a9878-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a9878-107">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="a9878-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a9878-108">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a9878-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="a9878-109">Aby narysować kontrolkę w formularzu</span><span class="sxs-lookup"><span data-stu-id="a9878-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="a9878-110">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="a9878-110">Open the form.</span></span> <span data-ttu-id="a9878-111">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formularzy systemu Windows w Projektancie](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="a9878-111">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="a9878-112">W **przybornika**, kliknij przycisk formantu ma zostać dodany do formularza.</span><span class="sxs-lookup"><span data-stu-id="a9878-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="a9878-113">Na formularzu kliknij w miejscu górnego lewego rogu formantu znajdował się i przeciągnij, aby miejsce prawym dolnym rogu formantu można znaleźć.</span><span class="sxs-lookup"><span data-stu-id="a9878-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="a9878-114">Formant został dodany do formularza z określonej lokalizacji i rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="a9878-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9878-115">Każdy formant ma domyślny rozmiar zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="a9878-115">Each control has a default size defined.</span></span> <span data-ttu-id="a9878-116">Można dodać kontrolkę do formularza w formantu domyślny rozmiar, przeciągając je z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="a9878-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="a9878-117">Przeciągnij formant do formularza</span><span class="sxs-lookup"><span data-stu-id="a9878-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="a9878-118">Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="a9878-118">Open the form.</span></span> <span data-ttu-id="a9878-119">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formularzy systemu Windows w Projektancie](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="a9878-119">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="a9878-120">W **przybornika**, kliknij i przeciągnij go do formularza formantu.</span><span class="sxs-lookup"><span data-stu-id="a9878-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="a9878-121">Formant został dodany do formularza w określonej lokalizacji w jego domyślny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="a9878-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9878-122">Możesz kliknąć dwukrotnie formantu w **przybornika** Aby dodać go do lewego górnego rogu formularza w jego domyślny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="a9878-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="a9878-123">Można również dodawać formanty dynamicznie do formularza w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a9878-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="a9878-124">W poniższym przykładzie kodu <xref:System.Windows.Forms.TextBox> formantu zostanie dodany do formularza po <xref:System.Windows.Forms.Button> formant zostanie kliknięty.</span><span class="sxs-lookup"><span data-stu-id="a9878-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9878-125">Poniższa procedura wymaga istnienia formularza z **przycisk** kontroli, `Button1`, już umieszczony na nim.</span><span class="sxs-lookup"><span data-stu-id="a9878-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="a9878-126">Aby programowo Dodawanie formantu do formularza</span><span class="sxs-lookup"><span data-stu-id="a9878-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="a9878-127">W metodzie, który obsługuje przycisku `Click` zdarzenia w klasie formularza, Wstaw kod podobne do następujących czynności, aby dodać odwołanie do zmiennej formantu użytkownika Ustawianie formantu `Location`i Dodaj formant.</span><span class="sxs-lookup"><span data-stu-id="a9878-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
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
    >  <span data-ttu-id="a9878-128">Można również dodać kod do zainicjowania inne właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="a9878-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a9878-129">Na komputerze lokalnym zagrożenie bezpieczeństwa w sieci może udostępniać za pomocą odwołań do złośliwych `UserControl`.</span><span class="sxs-lookup"><span data-stu-id="a9878-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="a9878-130">Tylko będzie to problemem w przypadku złośliwe osoby tworzenie kontrolkę niestandardową szkodliwy, następuje można przez pomyłkę dodanie go do projektu.</span><span class="sxs-lookup"><span data-stu-id="a9878-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9878-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9878-131">See Also</span></span>  
 [<span data-ttu-id="a9878-132">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9878-132">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="a9878-133">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9878-133">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="a9878-134">Instrukcje: zmienianie rozmiaru kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9878-134">How to: Resize Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [<span data-ttu-id="a9878-135">Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9878-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="a9878-136">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9878-136">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
