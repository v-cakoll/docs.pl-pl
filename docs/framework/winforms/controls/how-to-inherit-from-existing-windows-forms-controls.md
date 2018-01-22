---
title: "Porady: dziedziczenie z istniejących formantów formularzy systemu Windows"
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
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb50e5b301095cce72e59dc2899d44a47215b536
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="d10aa-102">Porady: dziedziczenie z istniejących formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d10aa-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="d10aa-103">Jeśli chcesz rozszerzyć funkcjonalność istniejącego formantu, można utworzyć formantu pochodzące z istniejącej kontrolce przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="d10aa-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="d10aa-104">Podczas dziedziczenia z istniejącego formantu, dziedziczą wszystkich funkcji i właściwości tego formantu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="d10aa-105">Na przykład, jeśli zostały Tworzenie formantu odziedziczone <xref:System.Windows.Forms.Button>, będzie wyglądać nowego formantu i działanie dokładnie tak jak standard <xref:System.Windows.Forms.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="d10aa-106">Następnie można rozszerzyć lub modyfikowanie funkcjonalności nowego formantu za pomocą implementacji niestandardowych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="d10aa-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="d10aa-107">W niektórych formantów, można zmienić wygląd formantu dziedziczone przez zastąpienie jej <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d10aa-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d10aa-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="d10aa-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d10aa-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d10aa-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d10aa-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-an-inherited-control"></a><span data-ttu-id="d10aa-111">Aby utworzyć kontrolkę dziedziczonych</span><span class="sxs-lookup"><span data-stu-id="d10aa-111">To create an inherited control</span></span>  
  
1.  <span data-ttu-id="d10aa-112">Utwórz nową **aplikacji Windows Forms** projektu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-112">Create a new **Windows Forms Application** project.</span></span>  
  
2.  <span data-ttu-id="d10aa-113">Z **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d10aa-113">From the **Project** menu, choose **Add New Item**.</span></span>  
  
     <span data-ttu-id="d10aa-114">**Dodaj nowy element** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d10aa-114">The **Add New Item** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="d10aa-115">W **Dodaj nowy element** okno dialogowe, kliknij dwukrotnie **formant niestandardowy**.</span><span class="sxs-lookup"><span data-stu-id="d10aa-115">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>  
  
     <span data-ttu-id="d10aa-116">Formant niestandardowy jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="d10aa-117">Jeśli używasz języka Visual Basic w górnej części **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="d10aa-117">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="d10aa-118">Rozwiń węzeł CustomControl1.vb, a następnie otwórz CustomControl1.Designer.vb w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-118">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>  
  
5.  <span data-ttu-id="d10aa-119">Jeśli używasz języka C#, otwórz CustomControl1.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-119">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>  
  
6.  <span data-ttu-id="d10aa-120">Zlokalizuj deklaracji klasy, która dziedziczy od <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="d10aa-120">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>  
  
7.  <span data-ttu-id="d10aa-121">Zmień formant, który ma być dziedziczona z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d10aa-121">Change the base class to the control that you want to inherit from.</span></span>  
  
     <span data-ttu-id="d10aa-122">Na przykład, jeśli ma być dziedziczona z <xref:System.Windows.Forms.Button>, zmień deklaracji klasy następująco:</span><span class="sxs-lookup"><span data-stu-id="d10aa-122">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  <span data-ttu-id="d10aa-123">Jeśli używasz programu Visual Basic, Zapisz i zamknij CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="d10aa-123">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="d10aa-124">Otwórz CustomControl1.vb w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-124">Open CustomControl1.vb in the Code Editor.</span></span>  
  
9. <span data-ttu-id="d10aa-125">Implementowanie niestandardowych metod ani właściwości zawierające formantu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-125">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
10. <span data-ttu-id="d10aa-126">Jeśli chcesz zmodyfikować graficznego wygląd formantu, Zastąp <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d10aa-126">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d10aa-127">Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> nie umożliwia modyfikowanie wyglądu wszystkich kontrolek.</span><span class="sxs-lookup"><span data-stu-id="d10aa-127">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="d10aa-128">Te kontrolki, których wszystkie ich malowania wykonywanej przez system Windows (na przykład <xref:System.Windows.Forms.TextBox>) nigdy wywoływać ich <xref:System.Windows.Forms.Control.OnPaint%2A> metody i w związku z tym nigdy nie będzie używany niestandardowy kod.</span><span class="sxs-lookup"><span data-stu-id="d10aa-128">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="d10aa-129">Zapoznaj się z dokumentacją pomocy dla określonego formantu, który chcesz zmodyfikować, aby sprawdzić, czy <xref:System.Windows.Forms.Control.OnPaint%2A> metoda jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="d10aa-129">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="d10aa-130">Aby uzyskać listę wszystkich kontrolek formularzy systemu Windows, zobacz [formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d10aa-130">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="d10aa-131">Jeśli formant nie ma <xref:System.Windows.Forms.Control.OnPaint%2A> wymieniony jako metodą member, nie można zmienić jego wygląd przez zastąpienie tej metody.</span><span class="sxs-lookup"><span data-stu-id="d10aa-131">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="d10aa-132">Aby uzyskać więcej informacji o rysowania niestandardowych, zobacz [niestandardowych malowanie i renderowanie formantu](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="d10aa-132">For more information about custom painting, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
    ```vb  
    Protected Overrides Sub OnPaint(ByVal e As _  
       System.Windows.Forms.PaintEventArgs)  
       MyBase.OnPaint(e)  
       ' Insert code to do custom painting.   
       ' If you want to completely change the appearance of your control,  
       ' do not call MyBase.OnPaint(e).  
    End Sub  
    ```  
  
    ```csharp  
    protected override void OnPaint(PaintEventArgs pe)  
    {  
       base.OnPaint(pe);  
       // Insert code to do custom painting.  
       // If you want to completely change the appearance of your control,  
       // do not call base.OnPaint(pe).  
    }  
    ```  
  
11. <span data-ttu-id="d10aa-133">Zapisz i przetestować formantu.</span><span class="sxs-lookup"><span data-stu-id="d10aa-133">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d10aa-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d10aa-134">See Also</span></span>  
 [<span data-ttu-id="d10aa-135">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d10aa-135">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="d10aa-136">Instrukcje: dziedziczenie z klasy kontrolek</span><span class="sxs-lookup"><span data-stu-id="d10aa-136">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="d10aa-137">Instrukcje: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="d10aa-137">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="d10aa-138">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d10aa-138">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="d10aa-139">Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d10aa-139">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="d10aa-140">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d10aa-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="d10aa-141">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="d10aa-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
