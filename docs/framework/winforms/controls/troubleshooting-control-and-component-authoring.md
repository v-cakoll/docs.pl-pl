---
title: Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów
ms.date: 03/30/2017
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
ms.openlocfilehash: caad6a76b52a970e133425c484602deb8801d252
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45692831"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="7539b-102">Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów</span><span class="sxs-lookup"><span data-stu-id="7539b-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="7539b-103">Ten temat zawiera następujące typowe problemy, które występują podczas tworzenia składników i formantów.</span><span class="sxs-lookup"><span data-stu-id="7539b-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="7539b-104">Aby uzyskać więcej informacji, zobacz [Programowanie przy użyciu składników](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span><span class="sxs-lookup"><span data-stu-id="7539b-104">For more information, see [Programming with Components](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
-   <span data-ttu-id="7539b-105">Nie można dodać kontrolki do przybornika</span><span class="sxs-lookup"><span data-stu-id="7539b-105">Cannot Add Control to Toolbox</span></span>  
  
-   <span data-ttu-id="7539b-106">Nie można debugować kontrolki użytkownika interfejsu Windows Forms lub składnika</span><span class="sxs-lookup"><span data-stu-id="7539b-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
-   <span data-ttu-id="7539b-107">Zdarzenie jest zgłaszane w dwukrotnie odziedziczoną kontrolkę lub składnika</span><span class="sxs-lookup"><span data-stu-id="7539b-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
-   <span data-ttu-id="7539b-108">Błąd w czasie projektowania: "nie można utworzyć składnika"*nazwa składnika*""</span><span class="sxs-lookup"><span data-stu-id="7539b-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
-   <span data-ttu-id="7539b-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="7539b-109">STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="7539b-110">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="7539b-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="7539b-111">Nie można dodać kontrolki do przybornika</span><span class="sxs-lookup"><span data-stu-id="7539b-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="7539b-112">Jeśli chcesz dodać formant niestandardowy, który został utworzony w innym projekcie lub kontrolki z innych firm **przybornika**, należy to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="7539b-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="7539b-113">Jeśli bieżący projekt zawiera kontrolki lub składnika, powinien pojawić się w **przybornika** automatycznie.</span><span class="sxs-lookup"><span data-stu-id="7539b-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="7539b-114">Aby uzyskać więcej informacji, zobacz [wskazówki: automatyczne zapełnianie przybornika składnikami niestandardowe](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="7539b-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="7539b-115">Aby dodać formant do przybornika</span><span class="sxs-lookup"><span data-stu-id="7539b-115">To add a control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="7539b-116">Kliknij prawym przyciskiem myszy **przybornika** z menu skrótów wybierz **wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="7539b-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2.  <span data-ttu-id="7539b-117">W **wybierz elementy przybornika** okna dialogowego Dodaj składnik:</span><span class="sxs-lookup"><span data-stu-id="7539b-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    -   <span data-ttu-id="7539b-118">Jeśli chcesz dodać do składnik .NET Framework lub formantu, kliknij przycisk **składników .NET Framework** kartę.</span><span class="sxs-lookup"><span data-stu-id="7539b-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="7539b-119">— lub —</span><span class="sxs-lookup"><span data-stu-id="7539b-119">– or –</span></span>  
  
    -   <span data-ttu-id="7539b-120">Aby dodać składnik COM lub formantu ActiveX, kliknij przycisk **składników COM** kartę.</span><span class="sxs-lookup"><span data-stu-id="7539b-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3.  <span data-ttu-id="7539b-121">Jeśli formant znajduje się w oknie dialogowym, upewnij się, jest zaznaczone, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7539b-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7539b-122">Formant jest dodawany do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="7539b-122">The control is added to the **Toolbox**.</span></span>  
  
4.  <span data-ttu-id="7539b-123">Jeśli formant nie znajduje się w oknie dialogowym, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7539b-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="7539b-124">Kliknij przycisk **Przeglądaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="7539b-124">Click the **Browse** button.</span></span>  
  
    2.  <span data-ttu-id="7539b-125">Przejdź do folderu, który zawiera plik .dll, który zawiera formant.</span><span class="sxs-lookup"><span data-stu-id="7539b-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3.  <span data-ttu-id="7539b-126">Wybierz plik .dll, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="7539b-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="7539b-127">Formant zostanie wyświetlony w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="7539b-127">Your control appears in the dialog box.</span></span>  
  
    4.  <span data-ttu-id="7539b-128">Upewnij się, czy formant jest zaznaczone, a następnie kliknij **OK**.</span><span class="sxs-lookup"><span data-stu-id="7539b-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="7539b-129">Formant jest dodawany do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="7539b-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="7539b-130">Nie można debugować kontrolki użytkownika interfejsu Windows Forms lub składnika</span><span class="sxs-lookup"><span data-stu-id="7539b-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="7539b-131">Jeśli pochodzi od klasy formantu <xref:System.Windows.Forms.UserControl> klasy, można debugować jego zachowanie w czasie wykonywania za pomocą kontenera testu.</span><span class="sxs-lookup"><span data-stu-id="7539b-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="7539b-132">Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="7539b-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="7539b-133">Inne niestandardowe formanty i składniki nie są autonomiczne projektów.</span><span class="sxs-lookup"><span data-stu-id="7539b-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="7539b-134">One muszą być obsługiwane przez aplikację, taki jak projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7539b-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="7539b-135">Aby debugować formant lub składnika, należy dodać go do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7539b-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="7539b-136">Aby debugować formant lub składnika</span><span class="sxs-lookup"><span data-stu-id="7539b-136">To debug a control or component</span></span>  
  
1.  <span data-ttu-id="7539b-137">Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie** tworzenia rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="7539b-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2.  <span data-ttu-id="7539b-138">Z **pliku** menu, wybierz **Dodaj**, a następnie **nowy projekt** dodać projekt testowy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7539b-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3.  <span data-ttu-id="7539b-139">W **Dodaj nowy projekt** okno dialogowe Wybierz **aplikacji Windows** dla typu projektu.</span><span class="sxs-lookup"><span data-stu-id="7539b-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4.  <span data-ttu-id="7539b-140">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł dla nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="7539b-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="7539b-141">W menu skrótów kliknij **Dodaj odwołanie** można dodać odwołania do projektu zawierającego kontrola lub składników.</span><span class="sxs-lookup"><span data-stu-id="7539b-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5.  <span data-ttu-id="7539b-142">Utwórz wystąpienie składnika lub kontrolki w projekcie testowym.</span><span class="sxs-lookup"><span data-stu-id="7539b-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="7539b-143">Jeśli składnik jest w **przybornika**, a następnie przeciągnij go do Twojego powierzchni projektanta lub można utworzyć wystąpienia programistycznie, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7539b-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="7539b-144">Można teraz debugować swoje kontroli lub składnika w zwykły sposób w całym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="7539b-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="7539b-145">Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) i [wskazówki: debugowanie niestandardowych Windows formantów formularzy w czasie projektowania](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7539b-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="7539b-146">Zdarzenie jest zgłaszane w dwukrotnie odziedziczoną kontrolkę lub składnika</span><span class="sxs-lookup"><span data-stu-id="7539b-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="7539b-147">Jest to prawdopodobnie spowodowane zduplikowane `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7539b-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="7539b-148">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dziedziczone procedury obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="7539b-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="7539b-149">Błąd w czasie projektowania: "nie można utworzyć składnik"Składnik Name""</span><span class="sxs-lookup"><span data-stu-id="7539b-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="7539b-150">Składnik lub kontrolki, należy podać domyślnego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="7539b-150">Your component or control must provide a default constructor with no parameters.</span></span> <span data-ttu-id="7539b-151">Gdy środowisko projektowania tworzy wystąpienie składnika lub kontrolki, nie próbuje zapewniają żadnych parametrów do przeciążenia konstruktora, które przyjmują parametry.</span><span class="sxs-lookup"><span data-stu-id="7539b-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="7539b-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="7539b-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="7539b-153"><xref:System.STAThreadAttribute> Informuje środowisko uruchomieniowe języka wspólnego (CLR), Windows Forms korzysta z modelu apartamentem jednowątkowym.</span><span class="sxs-lookup"><span data-stu-id="7539b-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="7539b-154">Możesz zauważyć niezamierzone zachowanie, jeśli ten atrybut nie są stosowane do aplikacji Windows Forms `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="7539b-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="7539b-155">Na przykład obrazy tła mogą być niewidoczne dla kontrolki, takie jak <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="7539b-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="7539b-156">Niektóre kontrolki mogą także wymagać tego atrybutu poprawne Autouzupełnianie i zachowanie przeciągnij i upuść.</span><span class="sxs-lookup"><span data-stu-id="7539b-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="7539b-157">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="7539b-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="7539b-158">Kiedy używasz <xref:System.Drawing.ToolboxBitmapAttribute> zostać skojarzona ikona za pomocą składnika niestandardowego, mapa bitowa nie ma w przyborniku dla składników wygenerowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="7539b-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="7539b-159">Aby wyświetlić mapę bitową, należy ponownie załadować formantu za pomocą **wybierz elementy przybornika** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="7539b-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="7539b-160">Aby uzyskać więcej informacji, zobacz [porady: dostarczanie mapy bitowej przybornika dla formantu](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="7539b-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7539b-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7539b-161">See Also</span></span>  
 [<span data-ttu-id="7539b-162">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="7539b-162">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="7539b-163">Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="7539b-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="7539b-164">Instrukcje: testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="7539b-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [<span data-ttu-id="7539b-165">Przewodnik: debugowanie niestandardowych kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="7539b-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="7539b-166">Tworzenie składników</span><span class="sxs-lookup"><span data-stu-id="7539b-166">Component Authoring</span></span>](https://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [<span data-ttu-id="7539b-167">Rozwiązywanie problemów podczas projektowania</span><span class="sxs-lookup"><span data-stu-id="7539b-167">Troubleshooting Design-Time Development</span></span>](https://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="7539b-168">Programowanie przy użyciu składników</span><span class="sxs-lookup"><span data-stu-id="7539b-168">Programming with Components</span></span>](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
