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
ms.openlocfilehash: 48531ab1ef3b30b6516e3f2e7b5858a8884cbfe8
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211714"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="e0af8-102">Instrukcje: Testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="e0af8-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="e0af8-103">Podczas opracowywania <xref:System.Windows.Forms.UserControl>, należy przetestować jej zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e0af8-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="e0af8-104">Można utworzyć projekt oddzielną aplikację z systemem Windows i umieść swój formant na formularzu testu, ale ta procedura jest wygodne.</span><span class="sxs-lookup"><span data-stu-id="e0af8-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="e0af8-105">Szybciej i łatwiej metodą jest użycie **UserControl — kontener testowy** dostarczane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0af8-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="e0af8-106">Ten kontener testowy uruchamia się bezpośrednio z Twojego Projekt Biblioteka formantów Windows.</span><span class="sxs-lookup"><span data-stu-id="e0af8-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0af8-107">Dla kontenera testów, które można załadować usługi <xref:System.Windows.Forms.UserControl>, kontrolka musi mieć co najmniej jeden konstruktor publiczny.</span><span class="sxs-lookup"><span data-stu-id="e0af8-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="e0af8-108">Kontrolki języka Visual C++ nie można przetestować za pomocą **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="e0af8-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="e0af8-109">Testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="e0af8-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="e0af8-110">W programie Visual Studio Utwórz projekt Biblioteka formantów Windows o nazwie **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="e0af8-110">In Visual Studio, create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="e0af8-111">Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e0af8-111">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="e0af8-112">W **Windows Forms Designer**, przeciągnij <xref:System.Windows.Forms.Label> z kontrolować **przybornika** na powierzchnię projektowania formantu.</span><span class="sxs-lookup"><span data-stu-id="e0af8-112">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="e0af8-113">Naciśnij klawisz **F5** Aby skompilować projekt i uruchomić **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="e0af8-113">Press **F5** to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="e0af8-114">Kontener testu, który jest wyświetlany za pomocą usługi <xref:System.Windows.Forms.UserControl> w **(wersja zapoznawcza)** okienka.</span><span class="sxs-lookup"><span data-stu-id="e0af8-114">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="e0af8-115">Wybierz <xref:System.Windows.Forms.Control.BackColor%2A> właściwości wyświetlane w <xref:System.Windows.Forms.PropertyGrid> kontroli po prawej stronie **Podgląd** okienka.</span><span class="sxs-lookup"><span data-stu-id="e0af8-115">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="e0af8-116">Zmień jej wartość na `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="e0af8-116">Change its value to `ControlDark`.</span></span> <span data-ttu-id="e0af8-117">Sprawdź, czy kontrolka zmienia kolor ciemniejszego.</span><span class="sxs-lookup"><span data-stu-id="e0af8-117">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="e0af8-118">Spróbuj zmienić wartości innych właściwości i obserwuj wpływ na Twoją kontrolą.</span><span class="sxs-lookup"><span data-stu-id="e0af8-118">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="e0af8-119">Kliknij przycisk **kontrolki użytkownika wypełnienia dokowania** poniższe pole wyboru **Podgląd** okienka.</span><span class="sxs-lookup"><span data-stu-id="e0af8-119">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="e0af8-120">Sprawdź, czy zmieni się rozmiar kontrolki do wypełnienia okienka.</span><span class="sxs-lookup"><span data-stu-id="e0af8-120">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="e0af8-121">Zmień rozmiar kontenera testu i obserwować zmiany rozmiaru za pomocą okienka kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e0af8-121">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="e0af8-122">Zamknij kontener testu.</span><span class="sxs-lookup"><span data-stu-id="e0af8-122">Close the test container.</span></span>

7. <span data-ttu-id="e0af8-123">Dodaj inną kontrolkę użytkownika do **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="e0af8-123">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="e0af8-124">Aby uzyskać więcej informacji, zobacz [jak: Dodaj istniejące elementy do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e0af8-124">For details, see [How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span></span>

8. <span data-ttu-id="e0af8-125">W **Windows Forms Designer**, przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** na powierzchnię projektowania formantu.</span><span class="sxs-lookup"><span data-stu-id="e0af8-125">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="e0af8-126">Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu.</span><span class="sxs-lookup"><span data-stu-id="e0af8-126">Press F5 to build the project and run the test container.</span></span>

10. <span data-ttu-id="e0af8-127">Kliknij przycisk **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> Aby przełączyć się między formantami dwóch użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e0af8-127">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="e0af8-128">Formanty użytkownika testów z innego projektu</span><span class="sxs-lookup"><span data-stu-id="e0af8-128">Test user controls from another project</span></span>

<span data-ttu-id="e0af8-129">Możesz przetestować kontrolki użytkownika z innych projektów w kontenerze testów bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="e0af8-129">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="e0af8-130">Utwórz projekt Biblioteka formantów Windows o nazwie **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="e0af8-130">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="e0af8-131">Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e0af8-131">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="e0af8-132">W **Windows Forms Designer**, przeciągnij <xref:System.Windows.Forms.RadioButton> z kontrolować **przybornika** na powierzchnię projektowania formantu.</span><span class="sxs-lookup"><span data-stu-id="e0af8-132">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="e0af8-133">Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu.</span><span class="sxs-lookup"><span data-stu-id="e0af8-133">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="e0af8-134">Kontener testu, który jest wyświetlany za pomocą usługi <xref:System.Windows.Forms.UserControl> w **(wersja zapoznawcza)** okienka.</span><span class="sxs-lookup"><span data-stu-id="e0af8-134">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="e0af8-135">Kliknij przycisk **obciążenia** przycisku.</span><span class="sxs-lookup"><span data-stu-id="e0af8-135">Click the **Load** button.</span></span>

5. <span data-ttu-id="e0af8-136">W **Otwórz** okno dialogowe, przejdź do **TestContainerExample**.dll, która utworzoną w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="e0af8-136">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="e0af8-137">Wybierz **TestContainerExample**.dll i kliknij przycisk **Otwórz** przycisk, aby załadować kontrolki użytkownika</span><span class="sxs-lookup"><span data-stu-id="e0af8-137">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>

6. <span data-ttu-id="e0af8-138">Użyj **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> Aby przełączyć się między formantami dwóch użytkowników z **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="e0af8-138">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0af8-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0af8-139">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="e0af8-140">Instrukcje: Formanty złożone autora</span><span class="sxs-lookup"><span data-stu-id="e0af8-140">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="e0af8-141">Przewodnik: Tworzenie formantu złożonego za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e0af8-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="e0af8-142">Przewodnik: Tworzenie formantu złożonego za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="e0af8-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="e0af8-143">[Projektant kontrolki użytkownika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e0af8-143">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
