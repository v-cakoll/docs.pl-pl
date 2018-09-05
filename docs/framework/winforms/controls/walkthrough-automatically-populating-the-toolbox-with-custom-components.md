---
title: 'Wskazówki: automatyczne zapełnianie Przybornika składnikami niestandardowymi'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 488d51e748ea17b09e61b982db7abadc34f8e311
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671894"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="d4aae-102">Wskazówki: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="d4aae-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="d4aae-103">Jeśli składniki są zdefiniowane w projekcie w aktualnie otwarte rozwiązanie, zostanie automatycznie wyświetlona w **przybornika**, za pomocą trzeba wykonywać żadnych czynności przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d4aae-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="d4aae-104">Możesz również ręcznie wypełnić **przybornika** za pomocą składników niestandardowych za pomocą [wybierz przybornika dialogowego elementy (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ale **przybornika** uwzględnia elementy w Twoim rozwiązaniu kompilacji danych wyjściowych o następującej charakterystyce:</span><span class="sxs-lookup"><span data-stu-id="d4aae-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="d4aae-105">Implementuje <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="d4aae-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="d4aae-106">Nie ma <xref:System.ComponentModel.ToolboxItemAttribute> równa `false`;</span><span class="sxs-lookup"><span data-stu-id="d4aae-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="d4aae-107">Nie ma <xref:System.ComponentModel.DesignTimeVisibleAttribute> równa `false`.</span><span class="sxs-lookup"><span data-stu-id="d4aae-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4aae-108">**Przybornika** nie jest zgodna z łańcuchów odwołania, dzięki czemu nie będą wyświetlane elementy, które nie są kompilowane przez projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="d4aae-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="d4aae-109">W tym instruktażu pokazano, jak niestandardowy składnik jest automatycznie odzwierciedlana w **przybornika** Po skompilowaniu składnika.</span><span class="sxs-lookup"><span data-stu-id="d4aae-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="d4aae-110">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="d4aae-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="d4aae-111">Tworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d4aae-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="d4aae-112">Tworzenie niestandardowych składników.</span><span class="sxs-lookup"><span data-stu-id="d4aae-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="d4aae-113">Tworzenie wystąpienia składnika niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="d4aae-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="d4aae-114">Zwalnianie i ponowne załadowanie niestandardowych składników.</span><span class="sxs-lookup"><span data-stu-id="d4aae-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="d4aae-115">Gdy to zrobisz, zostanie wyświetlony **przybornika** jest wypełniana przy użyciu składnika, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="d4aae-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4aae-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="d4aae-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d4aae-117">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="d4aae-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d4aae-118">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d4aae-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d4aae-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="d4aae-119">Creating the Project</span></span>  
 <span data-ttu-id="d4aae-120">Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="d4aae-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d4aae-121">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="d4aae-121">To create the project</span></span>  
  
1.  <span data-ttu-id="d4aae-122">Utwórz projekt aplikacji systemu Windows o nazwie `ToolboxExample` (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="d4aae-122">Create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="d4aae-123">Dodaj nowy składnik do projektu.</span><span class="sxs-lookup"><span data-stu-id="d4aae-123">Add a new component to the project.</span></span> <span data-ttu-id="d4aae-124">Wywołaj go `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="d4aae-124">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="d4aae-125">Aby uzyskać więcej informacji, zobacz [NIB: instrukcje: dodawanie nowych elementów projektu](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="d4aae-125">For more information, see [NIB:How to: Add New Project Items](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="d4aae-126">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="d4aae-126">Build the project.</span></span>  
  
4.  <span data-ttu-id="d4aae-127">Z **narzędzia** menu, kliknij przycisk **opcje** elementu.</span><span class="sxs-lookup"><span data-stu-id="d4aae-127">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="d4aae-128">Kliknij przycisk **ogólne** w obszarze **Windows Forms Designer** element i upewnij się, że **AutoToolboxPopulate** ustawiono opcję **True**.</span><span class="sxs-lookup"><span data-stu-id="d4aae-128">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="d4aae-129">Tworzenie wystąpienia składnika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="d4aae-129">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="d4aae-130">Następnym krokiem jest do utworzenia wystąpienia składnika niestandardowego w formularzu.</span><span class="sxs-lookup"><span data-stu-id="d4aae-130">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="d4aae-131">Ponieważ **przybornika** automatycznie kont dla nowego składnika, jest to tak proste, jak tworzenie innych składnika lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d4aae-131">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="d4aae-132">Aby utworzyć wystąpienie składnika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="d4aae-132">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="d4aae-133">Otwieranie formularza projektu w **projektanta formularzy**.</span><span class="sxs-lookup"><span data-stu-id="d4aae-133">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="d4aae-134">W **przybornika**, kliknij przycisk Nowa karta o nazwie **składniki ToolboxExample**.</span><span class="sxs-lookup"><span data-stu-id="d4aae-134">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="d4aae-135">Po kliknięciu karty, zostanie wyświetlony **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="d4aae-135">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4aae-136">Ze względu na wydajność składników w obszarze automatycznie wypełniony **przybornika** niestandardowych map bitowych, nie są wyświetlane i <xref:System.Drawing.ToolboxBitmapAttribute> nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d4aae-136">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="d4aae-137">Aby wyświetlić ikonę do składnika niestandardowego w **przybornika**, użyj **wybierz elementy przybornika** okno dialogowe, aby załadować składnika.</span><span class="sxs-lookup"><span data-stu-id="d4aae-137">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="d4aae-138">Przeciągnij składnik do formularza.</span><span class="sxs-lookup"><span data-stu-id="d4aae-138">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="d4aae-139">Wystąpienia składnika, zostanie utworzony i dodany do **zasobniku składnika**.</span><span class="sxs-lookup"><span data-stu-id="d4aae-139">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="d4aae-140">Zwalnianie i ponowne załadowanie niestandardowych składników</span><span class="sxs-lookup"><span data-stu-id="d4aae-140">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="d4aae-141">**Przybornika** uwzględnia składników w każdym ładowania projektu oraz gdy projekt jest zwalniana, powoduje usunięcie odwołania do składników projektów.</span><span class="sxs-lookup"><span data-stu-id="d4aae-141">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="d4aae-142">Aby eksperymentować z wpływu na przybornika zwalniania i ponownego ładowania składników</span><span class="sxs-lookup"><span data-stu-id="d4aae-142">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="d4aae-143">Zwolnij projekt z rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d4aae-143">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="d4aae-144">Aby uzyskać więcej informacji na temat zwalniając projekty, zobacz [NIB: instrukcje: zwolnienie i ponownego ładowania projektów](https://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span><span class="sxs-lookup"><span data-stu-id="d4aae-144">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](https://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="d4aae-145">Jeśli zostanie wyświetlony monit, aby zapisać, wybierz opcję **tak**.</span><span class="sxs-lookup"><span data-stu-id="d4aae-145">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="d4aae-146">Dodaj nową **aplikacji Windows** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d4aae-146">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="d4aae-147">Otwórz formularz w **projektanta**.</span><span class="sxs-lookup"><span data-stu-id="d4aae-147">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="d4aae-148">**Składniki ToolboxExample** kartę z poprzednim projektu jest teraz usunięte.</span><span class="sxs-lookup"><span data-stu-id="d4aae-148">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="d4aae-149">Załaduj ponownie `ToolboxExample` projektu.</span><span class="sxs-lookup"><span data-stu-id="d4aae-149">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="d4aae-150">**Składniki ToolboxExample** karcie teraz będzie pojawiać się ponownie.</span><span class="sxs-lookup"><span data-stu-id="d4aae-150">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d4aae-151">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d4aae-151">Next Steps</span></span>  
 <span data-ttu-id="d4aae-152">Ten przewodnik pokazuje, że **przybornika** bierze pod uwagę elementów projektu, ale **przybornika** jest również uwzględnia kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d4aae-152">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="d4aae-153">Poeksperymentuj z Kontrolki niestandardowe, dodając i usuwając kontroli projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="d4aae-153">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4aae-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4aae-154">See Also</span></span>  
 [<span data-ttu-id="d4aae-155">Ogólne, Windows Forms Designer, okno dialogowe Opcje</span><span class="sxs-lookup"><span data-stu-id="d4aae-155">General, Windows Forms Designer, Options Dialog Box</span></span>](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="d4aae-156">Porady: manipulowanie karty przybornika</span><span class="sxs-lookup"><span data-stu-id="d4aae-156">How to: Manipulate Toolbox Tabs</span></span>](https://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [<span data-ttu-id="d4aae-157">Wybierz elementy przybornika, okno dialogowe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="d4aae-157">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="d4aae-158">Umieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d4aae-158">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
