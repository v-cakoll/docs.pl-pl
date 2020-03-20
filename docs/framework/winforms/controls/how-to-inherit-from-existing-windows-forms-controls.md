---
title: dziedziczenie z istniejących kontrolek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b0e0053816efde349c7e4d13d03bef5f8801c667
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849383"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="32586-102">Porady: dziedziczenie z istniejących formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="32586-102">How to: Inherit from Existing Windows Forms Controls</span></span>

<span data-ttu-id="32586-103">Jeśli chcesz rozszerzyć funkcjonalność istniejącego formantu, można utworzyć formant pochodzący z istniejącego formantu poprzez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="32586-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="32586-104">Dziedzicząc z istniejącego formantu, dziedziczysz wszystkie funkcje i właściwości wizualne tego formantu.</span><span class="sxs-lookup"><span data-stu-id="32586-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="32586-105">Na przykład, jeśli tworzysz formant, <xref:System.Windows.Forms.Button>który dziedziczył po, nowy formant <xref:System.Windows.Forms.Button> będzie wyglądać i działać dokładnie tak, jak standardowy formant.</span><span class="sxs-lookup"><span data-stu-id="32586-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="32586-106">Następnie można rozszerzyć lub zmodyfikować funkcjonalność nowego formantu za pomocą implementacji metod i właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="32586-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="32586-107">W niektórych formantów można również zmienić wygląd odziedziczonego <xref:System.Windows.Forms.Control.OnPaint%2A> formantu, zastępując jego metody.</span><span class="sxs-lookup"><span data-stu-id="32586-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="32586-108">Aby utworzyć formant dziedziczony</span><span class="sxs-lookup"><span data-stu-id="32586-108">To create an inherited control</span></span>

1. <span data-ttu-id="32586-109">W programie Visual Studio utwórz nowy projekt **aplikacji formularzy systemu Windows.**</span><span class="sxs-lookup"><span data-stu-id="32586-109">In Visual Studio, create a new **Windows Forms Application** project.</span></span>

1. <span data-ttu-id="32586-110">Z menu **Projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="32586-110">From the **Project** menu, choose **Add New Item**.</span></span>

    <span data-ttu-id="32586-111">Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.</span><span class="sxs-lookup"><span data-stu-id="32586-111">The **Add New Item** dialog box appears.</span></span>

1. <span data-ttu-id="32586-112">W oknie dialogowym **Dodawanie nowego elementu** kliknij dwukrotnie pozycję **Formant niestandardowy**.</span><span class="sxs-lookup"><span data-stu-id="32586-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

    <span data-ttu-id="32586-113">Nowy formant niestandardowy jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="32586-113">A new custom control is added to your project.</span></span>

1. <span data-ttu-id="32586-114">Jeśli używasz:</span><span class="sxs-lookup"><span data-stu-id="32586-114">If you're using:</span></span>

    - <span data-ttu-id="32586-115">Visual Basic, u góry **Eksploratora rozwiązań,** kliknij pozycję **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="32586-115">Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="32586-116">Rozwiń pozycję CustomControl1.vb, a następnie otwórz plik CustomControl1.Designer.vb w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="32586-116">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>
    - <span data-ttu-id="32586-117">C#, otwórz CustomControl1.cs w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="32586-117">C#, open CustomControl1.cs in the Code Editor.</span></span>

1. <span data-ttu-id="32586-118">Znajdź deklarację klasy, która <xref:System.Windows.Forms.Control>dziedziczy po .</span><span class="sxs-lookup"><span data-stu-id="32586-118">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

1. <span data-ttu-id="32586-119">Zmień klasę podstawową na formant, z którego chcesz dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="32586-119">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="32586-120">Na przykład, jeśli chcesz <xref:System.Windows.Forms.Button>dziedziczyć z , zmień deklarację klasy na następującą:</span><span class="sxs-lookup"><span data-stu-id="32586-120">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. <span data-ttu-id="32586-121">Jeśli używasz języka Visual Basic, zapisz i zamknij CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="32586-121">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="32586-122">Otwórz CustomControl1.vb w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="32586-122">Open CustomControl1.vb in the Code Editor.</span></span>

1. <span data-ttu-id="32586-123">Zaimplementuj wszystkie niestandardowe metody lub właściwości, które będzie zawierać formant.</span><span class="sxs-lookup"><span data-stu-id="32586-123">Implement any custom methods or properties that your control will incorporate.</span></span>

1. <span data-ttu-id="32586-124">Jeśli chcesz zmodyfikować wygląd graficzny formantu, należy <xref:System.Windows.Forms.Control.OnPaint%2A> zastąpić metodę.</span><span class="sxs-lookup"><span data-stu-id="32586-124">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="32586-125">Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> nie pozwala na modyfikowanie wyglądu wszystkich formantów.</span><span class="sxs-lookup"><span data-stu-id="32586-125">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="32586-126">Te formanty, które mają wszystkie ich <xref:System.Windows.Forms.TextBox>obraz wykonane <xref:System.Windows.Forms.Control.OnPaint%2A> przez system Windows (na przykład) nigdy nie wywołać ich metody, a tym samym nigdy nie będzie używać kodu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="32586-126">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="32586-127">Zapoznaj się z dokumentacją Pomocy dla określonego formantu, który chcesz zmodyfikować, aby sprawdzić, <xref:System.Windows.Forms.Control.OnPaint%2A> czy metoda jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="32586-127">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="32586-128">Aby uzyskać listę wszystkich formantów formularza systemu Windows, zobacz [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="32586-128">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="32586-129">Jeśli formant nie <xref:System.Windows.Forms.Control.OnPaint%2A> ma wymienione jako metoda elementu członkowskiego, nie można zmienić jego wygląd, zastępując tę metodę.</span><span class="sxs-lookup"><span data-stu-id="32586-129">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="32586-130">Aby uzyskać więcej informacji na temat malowania niestandardowego, zobacz [Niestandardowe malowanie i renderowanie sterowania](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="32586-130">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

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

1. <span data-ttu-id="32586-131">Zapisz i przetestuj swoją kontrolę.</span><span class="sxs-lookup"><span data-stu-id="32586-131">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="32586-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32586-132">See also</span></span>

- [<span data-ttu-id="32586-133">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="32586-133">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="32586-134">Instrukcje: dziedziczenie z klasy kontrolek</span><span class="sxs-lookup"><span data-stu-id="32586-134">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="32586-135">Instrukcje: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="32586-135">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="32586-136">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32586-136">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="32586-137">Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32586-137">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="32586-138">Przewodnik: Dziedziczenie z formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="32586-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
