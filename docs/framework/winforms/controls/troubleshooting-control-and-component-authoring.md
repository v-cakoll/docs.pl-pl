---
title: "Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e027a5b60e066a8d38db530c37a394227f2e892
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="57635-102">Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów</span><span class="sxs-lookup"><span data-stu-id="57635-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="57635-103">Ten temat zawiera następujące typowe problemy, które powstają podczas tworzenia składników i formantów.</span><span class="sxs-lookup"><span data-stu-id="57635-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="57635-104">Aby uzyskać więcej informacji, zobacz [programowania ze składnikami](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span><span class="sxs-lookup"><span data-stu-id="57635-104">For more information, see [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
-   <span data-ttu-id="57635-105">Nie można dodać formantu do przybornika</span><span class="sxs-lookup"><span data-stu-id="57635-105">Cannot Add Control to Toolbox</span></span>  
  
-   <span data-ttu-id="57635-106">Nie można debugować formantu użytkownika formularzy systemu Windows lub składnik</span><span class="sxs-lookup"><span data-stu-id="57635-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
-   <span data-ttu-id="57635-107">Zdarzenie jest zgłaszane w dziedziczonej formant lub składnik</span><span class="sxs-lookup"><span data-stu-id="57635-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
-   <span data-ttu-id="57635-108">Błąd w czasie projektowania: "nie można utworzyć składnika '*nazwa składnika*" "</span><span class="sxs-lookup"><span data-stu-id="57635-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
-   <span data-ttu-id="57635-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="57635-109">STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="57635-110">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="57635-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="57635-111">Nie można dodać formantu do przybornika</span><span class="sxs-lookup"><span data-stu-id="57635-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="57635-112">Jeśli chcesz dodać kontrolkę niestandardową, który został utworzony w innym projekcie lub innych firm formantu **przybornika**, należy to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="57635-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="57635-113">Jeśli bieżący projekt zawiera formant lub składnik, powinny być wyświetlane w **przybornika** automatycznie.</span><span class="sxs-lookup"><span data-stu-id="57635-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="57635-114">Aby uzyskać więcej informacji, zobacz [wskazówki: automatyczne zapełnianie przybornika składnikami niestandardowe](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="57635-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="57635-115">Aby dodać kontrolkę do przybornika</span><span class="sxs-lookup"><span data-stu-id="57635-115">To add a control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="57635-116">Kliknij prawym przyciskiem myszy **przybornika** z menu skrótów wybierz **wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="57635-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2.  <span data-ttu-id="57635-117">W **wybierz elementy przybornika** okno dialogowe Dodaj składnik:</span><span class="sxs-lookup"><span data-stu-id="57635-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    -   <span data-ttu-id="57635-118">Jeśli chcesz dodać .NET Framework składnika lub kontrolki, kliknij przycisk **składników .NET Framework** kartę.</span><span class="sxs-lookup"><span data-stu-id="57635-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="57635-119">— lub —</span><span class="sxs-lookup"><span data-stu-id="57635-119">– or –</span></span>  
  
    -   <span data-ttu-id="57635-120">Jeśli chcesz dodać składnik COM lub formantu ActiveX, kliknij przycisk **składniki COM** kartę.</span><span class="sxs-lookup"><span data-stu-id="57635-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3.  <span data-ttu-id="57635-121">Jeśli formant jest wyświetlana w oknie dialogowym, upewnij się, jest zaznaczone, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="57635-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="57635-122">Formant został dodany do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="57635-122">The control is added to the **Toolbox**.</span></span>  
  
4.  <span data-ttu-id="57635-123">Formant nie ma na liście w oknie dialogowym, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="57635-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="57635-124">Kliknij przycisk **Przeglądaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="57635-124">Click the **Browse** button.</span></span>  
  
    2.  <span data-ttu-id="57635-125">Przejdź do folderu, który zawiera plik .dll, który zawiera formantu.</span><span class="sxs-lookup"><span data-stu-id="57635-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3.  <span data-ttu-id="57635-126">Wybierz plik dll, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="57635-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="57635-127">W oknie dialogowym zostanie wyświetlona formantu.</span><span class="sxs-lookup"><span data-stu-id="57635-127">Your control appears in the dialog box.</span></span>  
  
    4.  <span data-ttu-id="57635-128">Upewnij się, czy formant jest zaznaczone, a następnie kliknij **OK**.</span><span class="sxs-lookup"><span data-stu-id="57635-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="57635-129">Formantu zostanie dodany do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="57635-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="57635-130">Nie można debugować formantu użytkownika formularzy systemu Windows lub składnik</span><span class="sxs-lookup"><span data-stu-id="57635-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="57635-131">Jeśli pochodzi z klasy formantu <xref:System.Windows.Forms.UserControl> klasy, można debugować jego zachowania w czasie wykonywania pomocą kontenera testu.</span><span class="sxs-lookup"><span data-stu-id="57635-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="57635-132">Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="57635-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="57635-133">Inne niestandardowe formanty i składniki nie są autonomicznych projektów.</span><span class="sxs-lookup"><span data-stu-id="57635-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="57635-134">Muszą one obsługiwane przez aplikację, takich jak projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="57635-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="57635-135">Aby debugować formant lub składnik, należy go dodać do projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="57635-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="57635-136">Aby debugować formant lub składnik</span><span class="sxs-lookup"><span data-stu-id="57635-136">To debug a control or component</span></span>  
  
1.  <span data-ttu-id="57635-137">Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie** tworzenia rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="57635-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2.  <span data-ttu-id="57635-138">Z **pliku** menu, wybierz **Dodaj**, a następnie **nowy projekt** dodać projekt testowy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57635-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3.  <span data-ttu-id="57635-139">W **Dodawanie nowego projektu** okno dialogowe Wybieranie **aplikacji systemu Windows** dla typu projektu.</span><span class="sxs-lookup"><span data-stu-id="57635-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4.  <span data-ttu-id="57635-140">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł dla nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="57635-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="57635-141">W menu skrótów kliknij **Dodaj odwołanie** można dodać odwołania do projektu zawierającego formant lub składnik.</span><span class="sxs-lookup"><span data-stu-id="57635-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5.  <span data-ttu-id="57635-142">Utwórz wystąpienie składnika lub formantu w projekcie testowym.</span><span class="sxs-lookup"><span data-stu-id="57635-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="57635-143">Jeśli składnik jest w **przybornika**, przeciągnij go do Twojego powierzchni projektanta, lub można utworzyć wystąpienia programowo, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="57635-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="57635-144">Możesz teraz debugować użytkownika formant lub składnik w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="57635-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="57635-145">Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) i [wskazówki: debugowanie niestandardowych formantów formularzy systemu Windows w czasie projektowania](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="57635-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="57635-146">Zdarzenie jest zgłaszane w dziedziczonej formant lub składnik</span><span class="sxs-lookup"><span data-stu-id="57635-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="57635-147">Jest to prawdopodobnie z powodu zduplikowanego `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="57635-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="57635-148">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dziedziczone programów obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="57635-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="57635-149">Błąd w czasie projektowania: "nie można utworzyć składnika 'Nazwa składnika'"</span><span class="sxs-lookup"><span data-stu-id="57635-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="57635-150">Twoje składnika lub kontrolki musisz podać domyślnego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="57635-150">Your component or control must provide a default constructor with no parameters.</span></span> <span data-ttu-id="57635-151">W środowisku projektowania tworzy wystąpienie składnika lub kontrolki, nie jest podejmowana zapewnienie żadnych parametrów przeciążeń konstruktora, które przyjmują parametrów.</span><span class="sxs-lookup"><span data-stu-id="57635-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="57635-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="57635-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="57635-153"><xref:System.STAThreadAttribute> Środowisko uruchomieniowe języka wspólnego (CLR) informuje, że formularzy systemu Windows używa modelu jednowątkowego apartamentu.</span><span class="sxs-lookup"><span data-stu-id="57635-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="57635-154">Jeśli ten atrybut nie stosować do aplikacji formularzy systemu Windows mogą pojawić się niezamierzone zachowanie `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="57635-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="57635-155">Na przykład obrazy tła mogą być niewidoczne dla formantów, takich jak <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="57635-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="57635-156">Niektóre kontrolki mogą także wymagać tego atrybutu do autouzupełniania poprawne i zachowanie przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="57635-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="57635-157">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="57635-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="57635-158">Jeśli używasz <xref:System.Drawing.ToolboxBitmapAttribute> zostać skojarzona ikona z składnik niestandardowy, mapy bitowej nie pojawia się w przyborniku składników wygenerowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="57635-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="57635-159">Aby wyświetlić mapę bitową, należy ponownie załadować formantu przy użyciu **wybierz elementy przybornika** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="57635-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="57635-160">Aby uzyskać więcej informacji, zobacz [porady: Podaj mapy bitowej przybornika dla formantu](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="57635-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57635-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57635-161">See Also</span></span>  
 [<span data-ttu-id="57635-162">Opracowywanie formularzy systemu Windows formantów w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="57635-162">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="57635-163">Wskazówki: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="57635-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="57635-164">Porady: testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="57635-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [<span data-ttu-id="57635-165">Wskazówki: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="57635-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="57635-166">Tworzenie składników</span><span class="sxs-lookup"><span data-stu-id="57635-166">Component Authoring</span></span>](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [<span data-ttu-id="57635-167">Rozwiązywanie problemów z Programowanie w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="57635-167">Troubleshooting Design-Time Development</span></span>](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="57635-168">Programowanie przy użyciu składników</span><span class="sxs-lookup"><span data-stu-id="57635-168">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
