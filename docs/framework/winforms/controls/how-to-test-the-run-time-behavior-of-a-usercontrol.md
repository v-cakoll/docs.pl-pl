---
title: 'Instrukcje: testowanie zachowania UserControl w czasie wykonywania'
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
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015777"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="8afdd-102">Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="8afdd-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="8afdd-103">Podczas opracowywania programu <xref:System.Windows.Forms.UserControl>należy przetestować jego zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8afdd-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="8afdd-104">Można utworzyć oddzielny projekt aplikacji oparty na systemie Windows i umieścić swój formant w formularzu testowym, ale ta procedura jest niewygodna.</span><span class="sxs-lookup"><span data-stu-id="8afdd-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="8afdd-105">Szybszym i łatwiejszym sposobem jest użycie obiektu **UserControl Test Container** dostarczonego przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8afdd-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="8afdd-106">Ten kontener testowy jest uruchamiany bezpośrednio z projektu biblioteki formantów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8afdd-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8afdd-107">Aby można było załadować <xref:System.Windows.Forms.UserControl>kontener testowy, formant musi mieć co najmniej jednego konstruktora publicznego.</span><span class="sxs-lookup"><span data-stu-id="8afdd-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="8afdd-108">Kontrolka C++ wizualizacji nie może być testowana przy użyciu obiektu **UserControl Test Container**.</span><span class="sxs-lookup"><span data-stu-id="8afdd-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="8afdd-109">Testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="8afdd-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="8afdd-110">W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="8afdd-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="8afdd-111">W **Projektant formularzy systemu Windows**przeciągnij <xref:System.Windows.Forms.Label> kontrolkę z przybornika na powierzchnię projektu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8afdd-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="8afdd-112">Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić **kontener testów UserControl**.</span><span class="sxs-lookup"><span data-stu-id="8afdd-112">Press **F5** to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="8afdd-113">Kontener testowy zostanie wyświetlony <xref:System.Windows.Forms.UserControl> w okienku **podglądu** .</span><span class="sxs-lookup"><span data-stu-id="8afdd-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="8afdd-114">Wybierz właściwość wyświetlaną <xref:System.Windows.Forms.PropertyGrid> w kontrolce po prawej stronie okienka **podglądu.** <xref:System.Windows.Forms.Control.BackColor%2A></span><span class="sxs-lookup"><span data-stu-id="8afdd-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="8afdd-115">Zmień jej wartość na **ControlDark**.</span><span class="sxs-lookup"><span data-stu-id="8afdd-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="8afdd-116">Zwróć uwagę, że formant zmieni się na ciemniejszy kolor.</span><span class="sxs-lookup"><span data-stu-id="8afdd-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="8afdd-117">Spróbuj zmienić inne wartości właściwości i obserwuj wpływ na kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="8afdd-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="8afdd-118">Kliknij pole wyboru Zadokuj **wypełnienie użytkownika** w okienku **podglądu** .</span><span class="sxs-lookup"><span data-stu-id="8afdd-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="8afdd-119">Zwróć uwagę, że rozmiar kontrolki został zmieniony w celu wypełnienia okienka.</span><span class="sxs-lookup"><span data-stu-id="8afdd-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="8afdd-120">Zmień rozmiar kontenera testowego i zwróć uwagę, że zmiana rozmiaru kontrolki jest w okienku.</span><span class="sxs-lookup"><span data-stu-id="8afdd-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="8afdd-121">Zamknij kontener testowy.</span><span class="sxs-lookup"><span data-stu-id="8afdd-121">Close the test container.</span></span>

7. <span data-ttu-id="8afdd-122">Dodaj kolejną kontrolkę użytkownika do projektu **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="8afdd-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="8afdd-123">W **Projektant formularzy systemu Windows**przeciągnij <xref:System.Windows.Forms.Button> kontrolkę z przybornika na powierzchnię projektu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8afdd-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="8afdd-124">Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić kontener testowy.</span><span class="sxs-lookup"><span data-stu-id="8afdd-124">Press **F5** to build the project and run the test container.</span></span>

10. <span data-ttu-id="8afdd-125">Kliknij przycisk **Wybierz kontrolkę** <xref:System.Windows.Forms.ComboBox> użytkownika, aby przełączać się między dwoma kontrolkami użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8afdd-125">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="8afdd-126">Testowanie kontrolek użytkownika z innego projektu</span><span class="sxs-lookup"><span data-stu-id="8afdd-126">Test user controls from another project</span></span>

<span data-ttu-id="8afdd-127">Kontrolki użytkownika można testować z innych projektów w kontenerze testów bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="8afdd-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="8afdd-128">W programie Visual Studio Utwórz projekt biblioteki formantów systemu Windows, a następnie nadaj mu nazwę **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="8afdd-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="8afdd-129">W **Projektant formularzy systemu Windows**przeciągnij <xref:System.Windows.Forms.RadioButton> kontrolkę z przybornika na powierzchnię projektu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8afdd-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="8afdd-130">Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić kontener testowy.</span><span class="sxs-lookup"><span data-stu-id="8afdd-130">Press **F5** to build the project and run the test container.</span></span> <span data-ttu-id="8afdd-131">Kontener testowy zostanie wyświetlony <xref:System.Windows.Forms.UserControl> w okienku **podglądu** .</span><span class="sxs-lookup"><span data-stu-id="8afdd-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="8afdd-132">Kliknij przycisk **ładowania** .</span><span class="sxs-lookup"><span data-stu-id="8afdd-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="8afdd-133">W oknie dialogowym **Otwórz** przejdź do **TestContainerExample**. dll, który został utworzony w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="8afdd-133">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="8afdd-134">Wybierz **TestContainerExample**. dll, a następnie kliknij przycisk **Otwórz** , aby załadować kontrolki użytkownika</span><span class="sxs-lookup"><span data-stu-id="8afdd-134">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>

6. <span data-ttu-id="8afdd-135">Użyj<xref:System.Windows.Forms.ComboBox> **kontrolki wybierz użytkownika** , aby przełączać między dwoma kontrolkami użytkownika z projektu **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="8afdd-135">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="8afdd-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8afdd-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="8afdd-137">Instrukcje: Tworzenie złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="8afdd-137">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="8afdd-138">Przewodnik: Tworzenie kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="8afdd-138">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="8afdd-139">[Projektant formantów użytkownika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8afdd-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
