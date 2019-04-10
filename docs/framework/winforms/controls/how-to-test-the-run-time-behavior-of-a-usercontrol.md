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
ms.openlocfilehash: 15b37c71e6643b588c0378510965a9a3e7cb56e9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321773"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="f4d93-102">Instrukcje: testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="f4d93-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="f4d93-103">Podczas opracowywania <xref:System.Windows.Forms.UserControl>, należy przetestować jej zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f4d93-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="f4d93-104">Można utworzyć projekt oddzielną aplikację z systemem Windows i umieść swój formant na formularzu testu, ale ta procedura jest wygodne.</span><span class="sxs-lookup"><span data-stu-id="f4d93-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="f4d93-105">Szybciej i łatwiej metodą jest użycie **UserControl — kontener testowy** dostarczane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f4d93-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="f4d93-106">Ten kontener testowy uruchamia się bezpośrednio z Twojego Projekt Biblioteka formantów Windows.</span><span class="sxs-lookup"><span data-stu-id="f4d93-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4d93-107">Dla kontenera testów, które można załadować usługi <xref:System.Windows.Forms.UserControl>, kontrolka musi mieć co najmniej jeden konstruktor publiczny.</span><span class="sxs-lookup"><span data-stu-id="f4d93-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4d93-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="f4d93-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f4d93-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f4d93-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f4d93-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4d93-111">Kontrolki języka Visual C++ nie można przetestować za pomocą **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="f4d93-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="f4d93-112">Aby testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="f4d93-112">To test the run-time behavior of a UserControl</span></span>  
  
1. <span data-ttu-id="f4d93-113">Utwórz projekt Biblioteka formantów Windows o nazwie **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="f4d93-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="f4d93-114">Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f4d93-114">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="f4d93-115">W **Windows Forms Designer**, przeciągnij <xref:System.Windows.Forms.Label> z kontrolować **przybornika** na powierzchnię projektowania formantu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3. <span data-ttu-id="f4d93-116">Naciśnij klawisz F5, aby skompilować projekt i uruchomić **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="f4d93-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="f4d93-117">Kontener testu, który jest wyświetlany za pomocą usługi <xref:System.Windows.Forms.UserControl> w **(wersja zapoznawcza)** okienka.</span><span class="sxs-lookup"><span data-stu-id="f4d93-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4. <span data-ttu-id="f4d93-118">Wybierz <xref:System.Windows.Forms.Control.BackColor%2A> właściwości wyświetlane w <xref:System.Windows.Forms.PropertyGrid> kontroli po prawej stronie **Podgląd** okienka.</span><span class="sxs-lookup"><span data-stu-id="f4d93-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="f4d93-119">Zmień jej wartość na `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="f4d93-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="f4d93-120">Sprawdź, czy kontrolka zmienia kolor ciemniejszego.</span><span class="sxs-lookup"><span data-stu-id="f4d93-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="f4d93-121">Spróbuj zmienić wartości innych właściwości i obserwuj wpływ na Twoją kontrolą.</span><span class="sxs-lookup"><span data-stu-id="f4d93-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5. <span data-ttu-id="f4d93-122">Kliknij przycisk **kontrolki użytkownika wypełnienia dokowania** poniższe pole wyboru **Podgląd** okienka.</span><span class="sxs-lookup"><span data-stu-id="f4d93-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="f4d93-123">Sprawdź, czy zmieni się rozmiar kontrolki do wypełnienia okienka.</span><span class="sxs-lookup"><span data-stu-id="f4d93-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="f4d93-124">Zmień rozmiar kontenera testu i obserwować zmiany rozmiaru za pomocą okienka kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f4d93-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6. <span data-ttu-id="f4d93-125">Zamknij kontener testu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-125">Close the test container.</span></span>  
  
7. <span data-ttu-id="f4d93-126">Dodaj inną kontrolkę użytkownika do **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="f4d93-127">Aby uzyskać więcej informacji, zobacz [jak: Dodaj istniejące elementy do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f4d93-127">For details, see [How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span></span>  
  
8. <span data-ttu-id="f4d93-128">W **Windows Forms Designer**, przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** na powierzchnię projektowania formantu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="f4d93-129">Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="f4d93-130">Kliknij przycisk **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> Aby przełączyć się między formantami dwóch użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f4d93-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="f4d93-131">Testowanie kontrolki użytkownika z innego projektu</span><span class="sxs-lookup"><span data-stu-id="f4d93-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="f4d93-132">Możesz przetestować kontrolki użytkownika z innych projektów w kontenerze testów bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="f4d93-133">Aby przetestować kontrolki użytkownika z innego projektu</span><span class="sxs-lookup"><span data-stu-id="f4d93-133">To test user controls from another project</span></span>  
  
1. <span data-ttu-id="f4d93-134">Utwórz projekt Biblioteka formantów Windows o nazwie **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="f4d93-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="f4d93-135">Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f4d93-135">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="f4d93-136">W **Windows Forms Designer**, przeciągnij <xref:System.Windows.Forms.RadioButton> z kontrolować **przybornika** na powierzchnię projektowania formantu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3. <span data-ttu-id="f4d93-137">Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="f4d93-138">Kontener testu, który jest wyświetlany za pomocą usługi <xref:System.Windows.Forms.UserControl> w **(wersja zapoznawcza)** okienka.</span><span class="sxs-lookup"><span data-stu-id="f4d93-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4. <span data-ttu-id="f4d93-139">Kliknij przycisk **obciążenia** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f4d93-139">Click the **Load** button.</span></span>  
  
5. <span data-ttu-id="f4d93-140">W **Otwórz** okno dialogowe, przejdź do **TestContainerExample**.dll, która utworzoną w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="f4d93-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="f4d93-141">Wybierz **TestContainerExample**.dll i kliknij przycisk **Otwórz** przycisk, aby załadować kontrolki użytkownika</span><span class="sxs-lookup"><span data-stu-id="f4d93-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6. <span data-ttu-id="f4d93-142">Użyj **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> Aby przełączyć się między formantami dwóch użytkowników z **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="f4d93-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d93-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4d93-143">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="f4d93-144">Instrukcje: autoryzowanie kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="f4d93-144">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="f4d93-145">Przewodnik: tworzenie kontrolki złożonej za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4d93-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="f4d93-146">Przewodnik: tworzenie kontrolki złożonej za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="f4d93-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="f4d93-147">Projektant kontrolki użytkownika</span><span class="sxs-lookup"><span data-stu-id="f4d93-147">User Control Designer</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
