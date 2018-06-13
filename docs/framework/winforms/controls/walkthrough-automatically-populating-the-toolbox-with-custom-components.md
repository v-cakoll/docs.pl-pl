---
title: 'Wskazówki: automatyczne zapełnianie Przybornika składnikami niestandardowymi'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: d446ab84cfe135e56483b8b309b696f7f15044fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540049"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="9c5b0-102">Wskazówki: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="9c5b0-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="9c5b0-103">Jeśli składniki są zdefiniowane przez projekt w aktualnie otwarte rozwiązanie, będzie automatycznie wyświetlane w **przybornika**, z trzeba wykonywać żadnych czynności przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="9c5b0-104">Można też ręcznie wypełnić **przybornika** Twojego składnikami niestandardowymi za pomocą [wybierz przybornika elementy — okno dialogowe (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ale **przybornika** uwzględnia elementów rozwiązania kompilacji dane wyjściowe o następującej charakterystyce:</span><span class="sxs-lookup"><span data-stu-id="9c5b0-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="9c5b0-105">Implementuje <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="9c5b0-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="9c5b0-106">Nie ma <xref:System.ComponentModel.ToolboxItemAttribute> ustawioną `false`;</span><span class="sxs-lookup"><span data-stu-id="9c5b0-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="9c5b0-107">Nie ma <xref:System.ComponentModel.DesignTimeVisibleAttribute> ustawioną `false`.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c5b0-108">**Przybornika** nie jest zgodna z łańcuchów odwołanie, nie będzie on wyświetlany elementy, które nie są tworzone przez projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="9c5b0-109">W tym przewodniku pokazano, jak niestandardowy składnik zostanie automatycznie wyświetlony w **przybornika** po utworzeniu składnika.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="9c5b0-110">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="9c5b0-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="9c5b0-111">Tworzenie projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="9c5b0-112">Tworzenie niestandardowych składników.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="9c5b0-113">Utworzenie wystąpienia składnika niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="9c5b0-114">Zwolnienie i ponowne załadowanie niestandardowych składników.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="9c5b0-115">Gdy skończysz, zostanie wyświetlone **przybornika** jest wypełniane przy użyciu składnika, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c5b0-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9c5b0-117">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9c5b0-118">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="9c5b0-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="9c5b0-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="9c5b0-119">Creating the Project</span></span>  
 <span data-ttu-id="9c5b0-120">Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="9c5b0-121">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="9c5b0-121">To create the project</span></span>  
  
1.  <span data-ttu-id="9c5b0-122">Utwórz projekt aplikacji systemu Windows o nazwie `ToolboxExample`.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-122">Create a Windows-based application project called `ToolboxExample`.</span></span>  
  
     <span data-ttu-id="9c5b0-123">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="9c5b0-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="9c5b0-124">Dodaj nowy składnik do projektu.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-124">Add a new component to the project.</span></span> <span data-ttu-id="9c5b0-125">Wywołać ją `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-125">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="9c5b0-126">Aby uzyskać więcej informacji, zobacz [NIB: porady: dodawanie nowych elementów projektu](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="9c5b0-126">For more information, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="9c5b0-127">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-127">Build the project.</span></span>  
  
4.  <span data-ttu-id="9c5b0-128">Z **narzędzia** menu, kliknij przycisk **opcje** elementu.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-128">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="9c5b0-129">Kliknij przycisk **ogólne** w obszarze **Projektant formularzy systemu Windows** element i upewnij się, że **AutoToolboxPopulate** ustawiono opcję **True**.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-129">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="9c5b0-130">Utworzenie wystąpienia składnika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="9c5b0-130">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="9c5b0-131">Następnym krokiem jest można utworzyć wystąpienia niestandardowego składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-131">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="9c5b0-132">Ponieważ **przybornika** automatycznie kont dla nowego składnika jest równie proste jak tworzenie innych składnika lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-132">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="9c5b0-133">Aby utworzyć wystąpienie niestandardowych składników</span><span class="sxs-lookup"><span data-stu-id="9c5b0-133">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="9c5b0-134">Otwórz formularz projektu w **Projektant formularzy**.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-134">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="9c5b0-135">W **przybornika**, kliknij kartę nowej nazwie **składniki ToolboxExample**.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-135">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="9c5b0-136">Po kliknięciu karty zostanie wyświetlona **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-136">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9c5b0-137">Ze względu na wydajność, składników, w obszarze wypełniana automatycznie **przybornika** nie wyświetlaj niestandardowych map bitowych i <xref:System.Drawing.ToolboxBitmapAttribute> nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-137">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="9c5b0-138">Aby wyświetlić ikony dla niestandardowych składników w **przybornika**, użyj **wybierz elementy przybornika** okno dialogowe, aby załadować składnika.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-138">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="9c5b0-139">Przeciągnij składnika na formularzu.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-139">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="9c5b0-140">Wystąpienie składnika jest tworzony i dodawany do **zasobnik składnika**.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-140">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="9c5b0-141">Zwolnienie i ponowne załadowanie niestandardowych składników</span><span class="sxs-lookup"><span data-stu-id="9c5b0-141">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="9c5b0-142">**Przybornika** uwzględnia składników w każdym ładowania projektu oraz gdy projekt jest zwolniony, powoduje usunięcie odwołania do projektu składników.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-142">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="9c5b0-143">Eksperymentować wpływa na przybornika zwolnienie i ponowne załadowanie składników</span><span class="sxs-lookup"><span data-stu-id="9c5b0-143">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="9c5b0-144">Zwolnienie projektu z rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-144">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="9c5b0-145">Aby uzyskać więcej informacji na temat zwalnianie projektów, zobacz [NIB: porady: zwolnienie i ponowne załadowanie projektów](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span><span class="sxs-lookup"><span data-stu-id="9c5b0-145">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="9c5b0-146">Jeśli zostanie wyświetlony monit o zapisanie, wybierz **tak**.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-146">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="9c5b0-147">Dodaj nową **aplikacji systemu Windows** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-147">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="9c5b0-148">Otwórz formularz w **projektanta**.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-148">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="9c5b0-149">**Składniki ToolboxExample** kartę z poprzednich projektu jest obecnie usunięty.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-149">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="9c5b0-150">Załaduj ponownie `ToolboxExample` projektu.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-150">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="9c5b0-151">**Składniki ToolboxExample** karcie teraz pojawi się.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-151">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9c5b0-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9c5b0-152">Next Steps</span></span>  
 <span data-ttu-id="9c5b0-153">W tym przewodniku wykaże, że **przybornika** uwzględnia elementów projektu, ale **przybornika** jest również uwzględnia kontrolek.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-153">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="9c5b0-154">Wypróbuj Kontrolki niestandardowe przez dodawanie i usuwanie projektów kontroli z rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9c5b0-154">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c5b0-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c5b0-155">See Also</span></span>  
 [<span data-ttu-id="9c5b0-156">Ogólne, Projektant formularzy systemu Windows, opcje — Okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="9c5b0-156">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="9c5b0-157">Porady: manipulowanie kart z przybornika</span><span class="sxs-lookup"><span data-stu-id="9c5b0-157">How to: Manipulate Toolbox Tabs</span></span>](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [<span data-ttu-id="9c5b0-158">Wybierz elementy przybornika, okno dialogowe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="9c5b0-158">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="9c5b0-159">Umieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c5b0-159">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
