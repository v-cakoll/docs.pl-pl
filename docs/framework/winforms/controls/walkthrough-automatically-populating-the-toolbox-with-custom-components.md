---
title: 'Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 876de650f9c182c0f82a02d1c5b356faa4f7f118
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211160"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="7a855-102">Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="7a855-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>

<span data-ttu-id="7a855-103">Jeśli składniki są zdefiniowane w projekcie w aktualnie otwarte rozwiązanie, zostanie automatycznie wyświetlona w **przybornika**, za pomocą trzeba wykonywać żadnych czynności przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7a855-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="7a855-104">Możesz również ręcznie wypełnić **przybornika** za pomocą składników niestandardowych za pomocą [wybierz przybornika dialogowego elementy (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), ale **przybornika** uwzględnia elementy w Twoim rozwiązaniu kompilacji danych wyjściowych o następującej charakterystyce:</span><span class="sxs-lookup"><span data-stu-id="7a855-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>

- <span data-ttu-id="7a855-105">Implementuje <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="7a855-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>

- <span data-ttu-id="7a855-106">Nie ma <xref:System.ComponentModel.ToolboxItemAttribute> równa `false`;</span><span class="sxs-lookup"><span data-stu-id="7a855-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>

- <span data-ttu-id="7a855-107">Nie ma <xref:System.ComponentModel.DesignTimeVisibleAttribute> równa `false`.</span><span class="sxs-lookup"><span data-stu-id="7a855-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="7a855-108">**Przybornika** nie jest zgodna z łańcuchów odwołania, dzięki czemu nie będzie ona wyświetlana elementy, które nie są kompilowane przez projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="7a855-108">The **Toolbox** does not follow reference chains, so it won't display items that are not built by a project in your solution.</span></span>

<span data-ttu-id="7a855-109">W tym instruktażu pokazano, jak niestandardowy składnik jest automatycznie odzwierciedlana w **przybornika** Po skompilowaniu składnika.</span><span class="sxs-lookup"><span data-stu-id="7a855-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="7a855-110">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="7a855-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="7a855-111">Tworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7a855-111">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="7a855-112">Tworzenie niestandardowych składników.</span><span class="sxs-lookup"><span data-stu-id="7a855-112">Creating a custom component.</span></span>

- <span data-ttu-id="7a855-113">Tworzenie wystąpienia składnika niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="7a855-113">Creating an instance of a custom component.</span></span>

- <span data-ttu-id="7a855-114">Zwalnianie i ponowne załadowanie niestandardowych składników.</span><span class="sxs-lookup"><span data-stu-id="7a855-114">Unloading and reloading a custom component.</span></span>

<span data-ttu-id="7a855-115">Gdy to zrobisz, zostanie wyświetlony **przybornika** jest wypełniana przy użyciu składnika, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="7a855-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="7a855-116">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="7a855-116">Create the project</span></span>

1. <span data-ttu-id="7a855-117">W programie Visual Studio Utwórz projekt aplikacji systemu Windows o nazwie `ToolboxExample` (**pliku** > **New** > **projektu**  >  **Visual C#**  lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms Aplikacja**).</span><span class="sxs-lookup"><span data-stu-id="7a855-117">In Visual Studio, create a Windows-based application project called `ToolboxExample` (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="7a855-118">Dodaj nowy składnik do projektu.</span><span class="sxs-lookup"><span data-stu-id="7a855-118">Add a new component to the project.</span></span> <span data-ttu-id="7a855-119">Wywołaj go `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="7a855-119">Call it `DemoComponent`.</span></span>

     <span data-ttu-id="7a855-120">Aby uzyskać więcej informacji, zobacz [jak: Dodaj nowe elementy projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7a855-120">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span>

3. <span data-ttu-id="7a855-121">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="7a855-121">Build the project.</span></span>

4. <span data-ttu-id="7a855-122">Z **narzędzia** menu, kliknij przycisk **opcje** elementu.</span><span class="sxs-lookup"><span data-stu-id="7a855-122">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="7a855-123">Kliknij przycisk **ogólne** w obszarze **Windows Forms Designer** element i upewnij się, że **AutoToolboxPopulate** ustawiono opcję **True**.</span><span class="sxs-lookup"><span data-stu-id="7a855-123">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>

## <a name="create-an-instance-of-a-custom-component"></a><span data-ttu-id="7a855-124">Utwórz wystąpienie obiektu niestandardowych składników</span><span class="sxs-lookup"><span data-stu-id="7a855-124">Create an instance of a custom component</span></span>

<span data-ttu-id="7a855-125">Następnym krokiem jest do utworzenia wystąpienia składnika niestandardowego w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7a855-125">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="7a855-126">Ponieważ **przybornika** automatycznie kont dla nowego składnika, jest to tak proste, jak tworzenie innych składnika lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7a855-126">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>

1. <span data-ttu-id="7a855-127">Otwieranie formularza projektu w **projektanta formularzy**.</span><span class="sxs-lookup"><span data-stu-id="7a855-127">Open the project's form in the **Forms Designer**.</span></span>

2. <span data-ttu-id="7a855-128">W **przybornika**, kliknij przycisk Nowa karta o nazwie **składniki ToolboxExample**.</span><span class="sxs-lookup"><span data-stu-id="7a855-128">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>

     <span data-ttu-id="7a855-129">Po kliknięciu karty, zostanie wyświetlony **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="7a855-129">Once you click the tab, you will see **DemoComponent**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7a855-130">Ze względu na wydajność składników w obszarze automatycznie wypełniony **przybornika** niestandardowych map bitowych, nie są wyświetlane i <xref:System.Drawing.ToolboxBitmapAttribute> nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7a855-130">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="7a855-131">Aby wyświetlić ikonę do składnika niestandardowego w **przybornika**, użyj **wybierz elementy przybornika** okno dialogowe, aby załadować składnika.</span><span class="sxs-lookup"><span data-stu-id="7a855-131">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>

3. <span data-ttu-id="7a855-132">Przeciągnij składnik do formularza.</span><span class="sxs-lookup"><span data-stu-id="7a855-132">Drag your component onto your form.</span></span>

     <span data-ttu-id="7a855-133">Wystąpienia składnika, zostanie utworzony i dodany do **zasobniku składnika**.</span><span class="sxs-lookup"><span data-stu-id="7a855-133">An instance of the component is created and added to the **Component Tray**.</span></span>

## <a name="unload-and-reload-a-custom-component"></a><span data-ttu-id="7a855-134">Zwolnij i ponownie załaduj niestandardowych składników</span><span class="sxs-lookup"><span data-stu-id="7a855-134">Unload and reload a custom component</span></span>

<span data-ttu-id="7a855-135">**Przybornika** uwzględnia składników w każdym ładowania projektu oraz gdy projekt jest zwalniana, powoduje usunięcie odwołania do składników projektów.</span><span class="sxs-lookup"><span data-stu-id="7a855-135">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>

1. <span data-ttu-id="7a855-136">Zwolnij projekt z rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7a855-136">Unload the project from the solution.</span></span>

     <span data-ttu-id="7a855-137">Aby uzyskać więcej informacji na temat zwalniając projekty, zobacz [jak: Zwolnij i ponownie Załaduj projekty](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7a855-137">For more information about unloading projects, see [How to: Unload and Reload Projects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)).</span></span> <span data-ttu-id="7a855-138">Jeśli zostanie wyświetlony monit, aby zapisać, wybierz opcję **tak**.</span><span class="sxs-lookup"><span data-stu-id="7a855-138">If you are prompted to save, choose **Yes**.</span></span>

2. <span data-ttu-id="7a855-139">Dodaj nową **aplikacji Windows** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7a855-139">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="7a855-140">Otwórz formularz w **projektanta**.</span><span class="sxs-lookup"><span data-stu-id="7a855-140">Open the form in the **Designer**.</span></span>

     <span data-ttu-id="7a855-141">**Składniki ToolboxExample** kartę z poprzednim projektu jest teraz usunięte.</span><span class="sxs-lookup"><span data-stu-id="7a855-141">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>

3. <span data-ttu-id="7a855-142">Załaduj ponownie `ToolboxExample` projektu.</span><span class="sxs-lookup"><span data-stu-id="7a855-142">Reload the `ToolboxExample` project.</span></span>

     <span data-ttu-id="7a855-143">**Składniki ToolboxExample** karcie teraz będzie pojawiać się ponownie.</span><span class="sxs-lookup"><span data-stu-id="7a855-143">The **ToolboxExample Components** tab now reappears.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7a855-144">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7a855-144">Next steps</span></span>

<span data-ttu-id="7a855-145">Ten przewodnik pokazuje, że **przybornika** bierze pod uwagę elementów projektu, ale **przybornika** jest również uwzględnia kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7a855-145">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="7a855-146">Poeksperymentuj z Kontrolki niestandardowe, dodając i usuwając kontroli projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="7a855-146">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a855-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a855-147">See also</span></span>

- <span data-ttu-id="7a855-148">[Ogólne, Windows Forms Designer, okno dialogowe Opcje](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a855-148">[General, Windows Forms Designer, Options Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))</span></span>
- <span data-ttu-id="7a855-149">[Instrukcje: Manipulowanie karty przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a855-149">[How to: Manipulate Toolbox Tabs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))</span></span>
- <span data-ttu-id="7a855-150">[Wybierz elementy przybornika, okno dialogowe (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7a855-150">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- [<span data-ttu-id="7a855-151">Umieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a855-151">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
