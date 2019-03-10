---
title: 'Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 8ddb248d2e011714ddc7fb68474f0e92e9ad8b5e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723975"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="3f62b-102">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="3f62b-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="3f62b-103">Jeśli składniki są zdefiniowane w projekcie w aktualnie otwarte rozwiązanie, zostanie automatycznie wyświetlona w **przybornika**, za pomocą trzeba wykonywać żadnych czynności przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3f62b-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="3f62b-104">Możesz również ręcznie wypełnić **przybornika** za pomocą składników niestandardowych za pomocą [wybierz przybornika dialogowego elementy (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), ale **przybornika** uwzględnia elementy w Twoim rozwiązaniu kompilacji danych wyjściowych o następującej charakterystyce:</span><span class="sxs-lookup"><span data-stu-id="3f62b-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="3f62b-105">Implementuje <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="3f62b-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="3f62b-106">Nie ma <xref:System.ComponentModel.ToolboxItemAttribute> równa `false`;</span><span class="sxs-lookup"><span data-stu-id="3f62b-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="3f62b-107">Nie ma <xref:System.ComponentModel.DesignTimeVisibleAttribute> równa `false`.</span><span class="sxs-lookup"><span data-stu-id="3f62b-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f62b-108">**Przybornika** nie jest zgodna z łańcuchów odwołania, dzięki czemu nie będą wyświetlane elementy, które nie są kompilowane przez projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="3f62b-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="3f62b-109">W tym instruktażu pokazano, jak niestandardowy składnik jest automatycznie odzwierciedlana w **przybornika** Po skompilowaniu składnika.</span><span class="sxs-lookup"><span data-stu-id="3f62b-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="3f62b-110">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="3f62b-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="3f62b-111">Tworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3f62b-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="3f62b-112">Tworzenie niestandardowych składników.</span><span class="sxs-lookup"><span data-stu-id="3f62b-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="3f62b-113">Tworzenie wystąpienia składnika niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3f62b-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="3f62b-114">Zwalnianie i ponowne załadowanie niestandardowych składników.</span><span class="sxs-lookup"><span data-stu-id="3f62b-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="3f62b-115">Gdy to zrobisz, zostanie wyświetlony **przybornika** jest wypełniana przy użyciu składnika, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="3f62b-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f62b-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="3f62b-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3f62b-117">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="3f62b-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3f62b-118">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="3f62b-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="3f62b-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="3f62b-119">Creating the Project</span></span>  
 <span data-ttu-id="3f62b-120">Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="3f62b-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="3f62b-121">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="3f62b-121">To create the project</span></span>  
  
1.  <span data-ttu-id="3f62b-122">Utwórz projekt aplikacji systemu Windows o nazwie `ToolboxExample` (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="3f62b-122">Create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="3f62b-123">Dodaj nowy składnik do projektu.</span><span class="sxs-lookup"><span data-stu-id="3f62b-123">Add a new component to the project.</span></span> <span data-ttu-id="3f62b-124">Wywołaj go `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="3f62b-124">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="3f62b-125">Aby uzyskać więcej informacji, zobacz [jak: Dodaj nowe elementy projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3f62b-125">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span>  
  
3.  <span data-ttu-id="3f62b-126">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="3f62b-126">Build the project.</span></span>  
  
4.  <span data-ttu-id="3f62b-127">Z **narzędzia** menu, kliknij przycisk **opcje** elementu.</span><span class="sxs-lookup"><span data-stu-id="3f62b-127">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="3f62b-128">Kliknij przycisk **ogólne** w obszarze **Windows Forms Designer** element i upewnij się, że **AutoToolboxPopulate** ustawiono opcję **True**.</span><span class="sxs-lookup"><span data-stu-id="3f62b-128">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="3f62b-129">Tworzenie wystąpienia składnika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="3f62b-129">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="3f62b-130">Następnym krokiem jest do utworzenia wystąpienia składnika niestandardowego w formularzu.</span><span class="sxs-lookup"><span data-stu-id="3f62b-130">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="3f62b-131">Ponieważ **przybornika** automatycznie kont dla nowego składnika, jest to tak proste, jak tworzenie innych składnika lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3f62b-131">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="3f62b-132">Aby utworzyć wystąpienie składnika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="3f62b-132">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="3f62b-133">Otwieranie formularza projektu w **projektanta formularzy**.</span><span class="sxs-lookup"><span data-stu-id="3f62b-133">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="3f62b-134">W **przybornika**, kliknij przycisk Nowa karta o nazwie **składniki ToolboxExample**.</span><span class="sxs-lookup"><span data-stu-id="3f62b-134">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="3f62b-135">Po kliknięciu karty, zostanie wyświetlony **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="3f62b-135">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3f62b-136">Ze względu na wydajność składników w obszarze automatycznie wypełniony **przybornika** niestandardowych map bitowych, nie są wyświetlane i <xref:System.Drawing.ToolboxBitmapAttribute> nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="3f62b-136">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="3f62b-137">Aby wyświetlić ikonę do składnika niestandardowego w **przybornika**, użyj **wybierz elementy przybornika** okno dialogowe, aby załadować składnika.</span><span class="sxs-lookup"><span data-stu-id="3f62b-137">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="3f62b-138">Przeciągnij składnik do formularza.</span><span class="sxs-lookup"><span data-stu-id="3f62b-138">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="3f62b-139">Wystąpienia składnika, zostanie utworzony i dodany do **zasobniku składnika**.</span><span class="sxs-lookup"><span data-stu-id="3f62b-139">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="3f62b-140">Zwalnianie i ponowne załadowanie niestandardowych składników</span><span class="sxs-lookup"><span data-stu-id="3f62b-140">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="3f62b-141">**Przybornika** uwzględnia składników w każdym ładowania projektu oraz gdy projekt jest zwalniana, powoduje usunięcie odwołania do składników projektów.</span><span class="sxs-lookup"><span data-stu-id="3f62b-141">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="3f62b-142">Aby eksperymentować z wpływu na przybornika zwalniania i ponownego ładowania składników</span><span class="sxs-lookup"><span data-stu-id="3f62b-142">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="3f62b-143">Zwolnij projekt z rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3f62b-143">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="3f62b-144">Aby uzyskać więcej informacji na temat zwalniając projekty, zobacz [jak: Zwolnij i ponownie Załaduj projekty](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3f62b-144">For more information about unloading projects, see [How to: Unload and Reload Projects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span></span> <span data-ttu-id="3f62b-145">Jeśli zostanie wyświetlony monit, aby zapisać, wybierz opcję **tak**.</span><span class="sxs-lookup"><span data-stu-id="3f62b-145">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="3f62b-146">Dodaj nową **aplikacji Windows** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3f62b-146">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="3f62b-147">Otwórz formularz w **projektanta**.</span><span class="sxs-lookup"><span data-stu-id="3f62b-147">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="3f62b-148">**Składniki ToolboxExample** kartę z poprzednim projektu jest teraz usunięte.</span><span class="sxs-lookup"><span data-stu-id="3f62b-148">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="3f62b-149">Załaduj ponownie `ToolboxExample` projektu.</span><span class="sxs-lookup"><span data-stu-id="3f62b-149">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="3f62b-150">**Składniki ToolboxExample** karcie teraz będzie pojawiać się ponownie.</span><span class="sxs-lookup"><span data-stu-id="3f62b-150">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3f62b-151">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3f62b-151">Next Steps</span></span>  
 <span data-ttu-id="3f62b-152">Ten przewodnik pokazuje, że **przybornika** bierze pod uwagę elementów projektu, ale **przybornika** jest również uwzględnia kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3f62b-152">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="3f62b-153">Poeksperymentuj z Kontrolki niestandardowe, dodając i usuwając kontroli projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="3f62b-153">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f62b-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f62b-154">See also</span></span>
- <span data-ttu-id="3f62b-155">[Ogólne, Windows Forms Designer, okno dialogowe Opcje](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f62b-155">[General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span></span>
- <span data-ttu-id="3f62b-156">[Instrukcje: Manipulowanie karty przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f62b-156">[How to: Manipulate Toolbox Tabs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span></span>
- <span data-ttu-id="3f62b-157">[Wybierz elementy przybornika, okno dialogowe (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f62b-157">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- [<span data-ttu-id="3f62b-158">Umieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f62b-158">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
