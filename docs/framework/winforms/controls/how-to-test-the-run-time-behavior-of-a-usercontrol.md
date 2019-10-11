---
title: 'Instrukcje: testowanie zachowania elementu UserControl w czasie wykonywania'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 110036e5031a2956375b1edf0689237661522d39
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180207"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="86a9e-102">Instrukcje: testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="86a9e-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="86a9e-103">Podczas tworzenia <xref:System.Windows.Forms.UserControl> należy przetestować jego zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="86a9e-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="86a9e-104">Można utworzyć oddzielny projekt aplikacji oparty na systemie Windows i umieścić swój formant w formularzu testowym, ale ta procedura jest niewygodna.</span><span class="sxs-lookup"><span data-stu-id="86a9e-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="86a9e-105">Szybszym i łatwiejszym sposobem jest użycie obiektu **UserControl Test Container** dostarczonego przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="86a9e-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="86a9e-106">Ten kontener testowy jest uruchamiany bezpośrednio z projektu biblioteki formantów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="86a9e-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a9e-107">Aby kontener testowy załadował <xref:System.Windows.Forms.UserControl>, formant musi mieć co najmniej jednego konstruktora publicznego.</span><span class="sxs-lookup"><span data-stu-id="86a9e-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="86a9e-108">Kontrolka C++ wizualizacji nie może być testowana przy użyciu obiektu **UserControl Test Container**.</span><span class="sxs-lookup"><span data-stu-id="86a9e-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="86a9e-109">Testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="86a9e-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="86a9e-110">W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="86a9e-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="86a9e-111">W **Projektant formularzy systemu Windows**przeciągnij kontrolkę <xref:System.Windows.Forms.Label> z **przybornika** na powierzchnię projektu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="86a9e-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="86a9e-112">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować projekt i uruchomić **kontener testów UserControl**.</span><span class="sxs-lookup"><span data-stu-id="86a9e-112">Press <kbd>F5</kbd> to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="86a9e-113">Kontener testowy pojawia się z <xref:System.Windows.Forms.UserControl> w okienku **podglądu** .</span><span class="sxs-lookup"><span data-stu-id="86a9e-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="86a9e-114">Wybierz właściwość <xref:System.Windows.Forms.Control.BackColor%2A> wyświetlaną w kontrolce <xref:System.Windows.Forms.PropertyGrid> po prawej stronie okienka **podglądu** .</span><span class="sxs-lookup"><span data-stu-id="86a9e-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="86a9e-115">Zmień jej wartość na **ControlDark**.</span><span class="sxs-lookup"><span data-stu-id="86a9e-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="86a9e-116">Zwróć uwagę, że formant zmieni się na ciemniejszy kolor.</span><span class="sxs-lookup"><span data-stu-id="86a9e-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="86a9e-117">Spróbuj zmienić inne wartości właściwości i obserwuj wpływ na kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="86a9e-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="86a9e-118">Kliknij pole wyboru **Zadokuj wypełnienie użytkownika** w okienku **podglądu** .</span><span class="sxs-lookup"><span data-stu-id="86a9e-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="86a9e-119">Zwróć uwagę, że rozmiar kontrolki został zmieniony w celu wypełnienia okienka.</span><span class="sxs-lookup"><span data-stu-id="86a9e-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="86a9e-120">Zmień rozmiar kontenera testowego i zwróć uwagę, że zmiana rozmiaru kontrolki jest w okienku.</span><span class="sxs-lookup"><span data-stu-id="86a9e-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="86a9e-121">Zamknij kontener testowy.</span><span class="sxs-lookup"><span data-stu-id="86a9e-121">Close the test container.</span></span>

7. <span data-ttu-id="86a9e-122">Dodaj kolejną kontrolkę użytkownika do projektu **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="86a9e-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="86a9e-123">W **Projektant formularzy systemu Windows**przeciągnij kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** na powierzchnię projektu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="86a9e-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="86a9e-124">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować projekt i uruchomić kontener testowy.</span><span class="sxs-lookup"><span data-stu-id="86a9e-124">Press <kbd>F5</kbd> to build the project and run the test container.</span></span>

10. <span data-ttu-id="86a9e-125">Kliknij przycisk **Wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox>, aby przełączać się między dwoma kontrolkami użytkownika.</span><span class="sxs-lookup"><span data-stu-id="86a9e-125">Click the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="86a9e-126">Testowanie kontrolek użytkownika z innego projektu</span><span class="sxs-lookup"><span data-stu-id="86a9e-126">Test user controls from another project</span></span>

<span data-ttu-id="86a9e-127">Kontrolki użytkownika można testować z innych projektów w kontenerze testów bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="86a9e-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="86a9e-128">W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="86a9e-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="86a9e-129">W **Projektant formularzy systemu Windows**przeciągnij kontrolkę <xref:System.Windows.Forms.RadioButton> z **przybornika** na powierzchnię projektu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="86a9e-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="86a9e-130">Naciśnij klawisz <kbd>F5</kbd> , aby skompilować projekt i uruchomić kontener testowy.</span><span class="sxs-lookup"><span data-stu-id="86a9e-130">Press <kbd>F5</kbd> to build the project and run the test container.</span></span> <span data-ttu-id="86a9e-131">Kontener testowy pojawia się z <xref:System.Windows.Forms.UserControl> w okienku **podglądu** .</span><span class="sxs-lookup"><span data-stu-id="86a9e-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="86a9e-132">Kliknij przycisk **ładowania** .</span><span class="sxs-lookup"><span data-stu-id="86a9e-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="86a9e-133">W oknie dialogowym **Otwórz** przejdź do *TestContainerExample. dll*, który został utworzony w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="86a9e-133">In the **Open** dialog box, navigate to *TestContainerExample.dll*, which you built in the previous procedure.</span></span> <span data-ttu-id="86a9e-134">Wybierz *TestContainerExample. dll* , a następnie kliknij przycisk **Otwórz** , aby załadować kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="86a9e-134">Select *TestContainerExample.dll* and click the **Open** button to load the user controls.</span></span>

6. <span data-ttu-id="86a9e-135">Użyj **opcji Wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox>, aby przełączać między dwoma kontrolkami użytkownika z projektu **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="86a9e-135">Use the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="86a9e-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86a9e-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="86a9e-137">Instrukcje: Tworzenie kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="86a9e-137">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="86a9e-138">Przewodnik: Tworzenie kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="86a9e-138">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="86a9e-139">[Projektant formantów użytkownika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="86a9e-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
