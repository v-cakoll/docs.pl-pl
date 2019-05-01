---
title: 'Instrukcje: dziedziczenie z istniejących kontrolek formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 788addee7c024577d029626da4aeb86d0ca9076a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941157"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="57e83-102">Instrukcje: dziedziczenie z istniejących kontrolek formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="57e83-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="57e83-103">Jeśli chcesz rozszerzyć funkcjonalność istniejącej kontrolki, można utworzyć formant pochodzące z istniejącej kontrolki przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="57e83-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="57e83-104">Dziedziczy z istniejącej kontrolki, dziedziczenie, wszystkie funkcje i wizualne właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="57e83-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="57e83-105">Na przykład, jeśli podczas tworzenia formant, który odziedziczone <xref:System.Windows.Forms.Button>nowego formantu będzie wyglądała i act dokładnie tak jak standardowy <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="57e83-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="57e83-106">Można następnie rozszerzyć lub zmodyfikować funkcje nowego formantu poprzez wdrożenie niestandardowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="57e83-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="57e83-107">W niektórych kontrolek można zmienić wygląd formantu dziedziczone przez zastąpienie jej <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="57e83-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57e83-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="57e83-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="57e83-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="57e83-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="57e83-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="57e83-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-an-inherited-control"></a><span data-ttu-id="57e83-111">Aby utworzyć odziedziczoną kontrolkę</span><span class="sxs-lookup"><span data-stu-id="57e83-111">To create an inherited control</span></span>  
  
1. <span data-ttu-id="57e83-112">Utwórz nową **aplikacja interfejsu Windows Forms** projektu.</span><span class="sxs-lookup"><span data-stu-id="57e83-112">Create a new **Windows Forms Application** project.</span></span>  
  
2. <span data-ttu-id="57e83-113">Z **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="57e83-113">From the **Project** menu, choose **Add New Item**.</span></span>  
  
     <span data-ttu-id="57e83-114">**Dodaj nowy element** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="57e83-114">The **Add New Item** dialog box appears.</span></span>  
  
3. <span data-ttu-id="57e83-115">W **Dodaj nowy element** okno dialogowe, kliknij dwukrotnie **kontrolkę niestandardową**.</span><span class="sxs-lookup"><span data-stu-id="57e83-115">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>  
  
     <span data-ttu-id="57e83-116">Nowy formant niestandardowy zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="57e83-116">A new custom control is added to your project.</span></span>  
  
4. <span data-ttu-id="57e83-117">Jeśli używasz języka Visual Basic w górnej części **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="57e83-117">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="57e83-118">Rozwiń CustomControl1.vb, a następnie otwórz CustomControl1.Designer.vb w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="57e83-118">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>  
  
5. <span data-ttu-id="57e83-119">Jeśli używasz języka C#, należy otworzyć CustomControl1.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="57e83-119">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>  
  
6. <span data-ttu-id="57e83-120">Znajdź deklaracji klasy, która dziedziczy z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="57e83-120">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>  
  
7. <span data-ttu-id="57e83-121">Zmień formant, który ma być dziedziczona z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="57e83-121">Change the base class to the control that you want to inherit from.</span></span>  
  
     <span data-ttu-id="57e83-122">Na przykład, jeśli ma być dziedziczona z <xref:System.Windows.Forms.Button>, zmień deklarację klasy następująco:</span><span class="sxs-lookup"><span data-stu-id="57e83-122">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8. <span data-ttu-id="57e83-123">Jeśli używasz języka Visual Basic, Zapisz i zamknij CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="57e83-123">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="57e83-124">Otwórz CustomControl1.vb w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="57e83-124">Open CustomControl1.vb in the Code Editor.</span></span>  
  
9. <span data-ttu-id="57e83-125">Implementowanie niestandardowych metod dowolnej właściwości, które będą zawierały kontrolki.</span><span class="sxs-lookup"><span data-stu-id="57e83-125">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
10. <span data-ttu-id="57e83-126">Jeśli chcesz zmodyfikować graficzny wygląd kontrolki, zastępują <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="57e83-126">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57e83-127">Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> nie umożliwia modyfikowania wyglądu wszystkich kontrolek.</span><span class="sxs-lookup"><span data-stu-id="57e83-127">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="57e83-128">Te kontrolki, w których wszystkie ich malowania wykonywane przez Windows (na przykład <xref:System.Windows.Forms.TextBox>) nigdy nie wywołują metody ich <xref:System.Windows.Forms.Control.OnPaint%2A> metody i w związku z tym nigdy nie będzie użycie kodu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="57e83-128">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="57e83-129">Można znaleźć w dokumentacji pomocy dla określonego formantu, który chcesz zmodyfikować, aby sprawdzić, czy <xref:System.Windows.Forms.Control.OnPaint%2A> metoda jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="57e83-129">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="57e83-130">Aby uzyskać listę wszystkich kontrolek formularza Windows, zobacz [kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="57e83-130">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="57e83-131">Jeśli formant nie ma <xref:System.Windows.Forms.Control.OnPaint%2A> wymieniony jako metoda elementu członkowskiego, nie można zmieniać jego wygląd poprzez zastąpienie tej metody.</span><span class="sxs-lookup"><span data-stu-id="57e83-131">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="57e83-132">Aby uzyskać więcej informacji na temat niestandardowych malowania zobacz [niestandardowe malowanie i renderowanie formantu](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="57e83-132">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>  
  
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
  
11. <span data-ttu-id="57e83-133">Zapisz i przetestuj formantu.</span><span class="sxs-lookup"><span data-stu-id="57e83-133">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e83-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57e83-134">See also</span></span>

- [<span data-ttu-id="57e83-135">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="57e83-135">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="57e83-136">Instrukcje: Dziedziczenie z klasy formantów</span><span class="sxs-lookup"><span data-stu-id="57e83-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="57e83-137">Instrukcje: Dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="57e83-137">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="57e83-138">Instrukcje: Tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57e83-138">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="57e83-139">Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57e83-139">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="57e83-140">Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57e83-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="57e83-141">Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="57e83-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
