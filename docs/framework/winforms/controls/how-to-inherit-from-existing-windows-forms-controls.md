---
title: 'Porady: dziedziczenie z istniejących formantów formularzy systemu Windows'
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
ms.openlocfilehash: 063f5bb87b6348ee83573cf1506c9fabdaf651ee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460567"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="8f733-102">Porady: dziedziczenie z istniejących formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8f733-102">How to: Inherit from Existing Windows Forms Controls</span></span>

<span data-ttu-id="8f733-103">Jeśli chcesz zwiększyć funkcjonalność istniejącej kontrolki, można utworzyć kontrolkę pochodzącą od istniejącej kontrolki przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="8f733-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="8f733-104">Podczas dziedziczenia z istniejącej kontrolki dziedziczą wszystkie funkcje i właściwości wizualne tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8f733-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="8f733-105">Na przykład, jeśli tworzysz kontrolkę, która dziedziczy po <xref:System.Windows.Forms.Button>, Nowa kontrolka będzie wyglądać i działać tak samo jak w przypadku standardowego formantu <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="8f733-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="8f733-106">Następnie można zwiększyć lub zmodyfikować funkcjonalność nowej kontrolki przez implementację niestandardowych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="8f733-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="8f733-107">W niektórych kontrolkach można także zmienić wygląd dziedziczonej kontrolki, zastępując jej metodę <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f733-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="8f733-108">Aby utworzyć formant dziedziczony</span><span class="sxs-lookup"><span data-stu-id="8f733-108">To create an inherited control</span></span>

1. <span data-ttu-id="8f733-109">W programie Visual Studio Utwórz nowy projekt **aplikacji Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="8f733-109">In Visual Studio, create a new **Windows Forms Application** project.</span></span>

1. <span data-ttu-id="8f733-110">W menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="8f733-110">From the **Project** menu, choose **Add New Item**.</span></span>

    <span data-ttu-id="8f733-111">Pojawi się okno dialogowe **Dodaj nowy element** .</span><span class="sxs-lookup"><span data-stu-id="8f733-111">The **Add New Item** dialog box appears.</span></span>

1. <span data-ttu-id="8f733-112">W oknie dialogowym **Dodaj nowy element** kliknij dwukrotnie **kontrolkę niestandardową**.</span><span class="sxs-lookup"><span data-stu-id="8f733-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

    <span data-ttu-id="8f733-113">Do projektu zostanie dodany nowy formant niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="8f733-113">A new custom control is added to your project.</span></span>

1. <span data-ttu-id="8f733-114">Jeśli używasz:</span><span class="sxs-lookup"><span data-stu-id="8f733-114">If you using:</span></span>

    - <span data-ttu-id="8f733-115">Visual Basic w górnej części **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="8f733-115">Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="8f733-116">Rozwiń CustomControl1. vb, a następnie otwórz CustomControl1. Designer. vb w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="8f733-116">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>
    - <span data-ttu-id="8f733-117">C#Otwórz CustomControl1.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="8f733-117">C#, open CustomControl1.cs in the Code Editor.</span></span>

1. <span data-ttu-id="8f733-118">Znajdź deklarację klasy, która dziedziczy z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="8f733-118">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

1. <span data-ttu-id="8f733-119">Zmień klasę bazową na kontrolkę, z której chcesz dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="8f733-119">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="8f733-120">Na przykład jeśli chcesz dziedziczyć z <xref:System.Windows.Forms.Button>, zmień deklarację klasy na następującą:</span><span class="sxs-lookup"><span data-stu-id="8f733-120">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. <span data-ttu-id="8f733-121">Jeśli używasz Visual Basic, Zapisz i zamknij CustomControl1. Designer. vb.</span><span class="sxs-lookup"><span data-stu-id="8f733-121">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="8f733-122">Otwórz CustomControl1. vb w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="8f733-122">Open CustomControl1.vb in the Code Editor.</span></span>

1. <span data-ttu-id="8f733-123">Zaimplementuj wszelkie niestandardowe metody lub właściwości, które zostaną dołączone do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8f733-123">Implement any custom methods or properties that your control will incorporate.</span></span>

1. <span data-ttu-id="8f733-124">Jeśli chcesz zmodyfikować wygląd graficzny formantu, Zastąp metodę <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f733-124">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8f733-125">Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> nie pozwoli na modyfikowanie wyglądu wszystkich kontrolek.</span><span class="sxs-lookup"><span data-stu-id="8f733-125">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="8f733-126">Te kontrolki, które mają wszystkie malowanie wykonywane przez system Windows (na przykład <xref:System.Windows.Forms.TextBox>) nigdy nie wywołują metody <xref:System.Windows.Forms.Control.OnPaint%2A> i w ten sposób nigdy nie będą używać kodu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="8f733-126">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="8f733-127">Zapoznaj się z dokumentacją dotyczącą konkretnej kontrolki, która ma zostać zmodyfikowana, aby zobaczyć, czy metoda <xref:System.Windows.Forms.Control.OnPaint%2A> jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="8f733-127">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="8f733-128">Aby uzyskać listę wszystkich kontrolek formularzy systemu Windows, zobacz [kontrolki do użycia na Windows Forms](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8f733-128">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="8f733-129">Jeśli kontrolka nie ma <xref:System.Windows.Forms.Control.OnPaint%2A> na liście jako metoda członkowska, nie można zmienić jej wyglądu poprzez zastąpienie tej metody.</span><span class="sxs-lookup"><span data-stu-id="8f733-129">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="8f733-130">Aby uzyskać więcej informacji na temat rysowania niestandardowego, zobacz [malowanie i renderowanie kontrolek niestandardowych](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="8f733-130">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

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

1. <span data-ttu-id="8f733-131">Zapisz i Przetestuj swój formant.</span><span class="sxs-lookup"><span data-stu-id="8f733-131">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f733-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f733-132">See also</span></span>

- [<span data-ttu-id="8f733-133">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="8f733-133">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="8f733-134">Instrukcje: dziedziczenie z klasy kontrolek</span><span class="sxs-lookup"><span data-stu-id="8f733-134">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="8f733-135">Instrukcje: dziedziczenie z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="8f733-135">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="8f733-136">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f733-136">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="8f733-137">Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f733-137">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="8f733-138">Przewodnik: dziedziczenie z kontrolki Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f733-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
