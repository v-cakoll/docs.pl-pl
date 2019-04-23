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
ms.openlocfilehash: 3ae8a889bf69913d234e31804335ddb08560c30c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343418"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="75432-102">Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów</span><span class="sxs-lookup"><span data-stu-id="75432-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="75432-103">Ten temat zawiera następujące typowe problemy, które występują podczas tworzenia składników i formantów.</span><span class="sxs-lookup"><span data-stu-id="75432-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="75432-104">Aby uzyskać więcej informacji, zobacz [Programowanie przy użyciu składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="75432-104">For more information, see [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
-   <span data-ttu-id="75432-105">Nie można dodać kontrolki do przybornika</span><span class="sxs-lookup"><span data-stu-id="75432-105">Cannot Add Control to Toolbox</span></span>  
  
-   <span data-ttu-id="75432-106">Nie można debugować kontrolki użytkownika interfejsu Windows Forms lub składnika</span><span class="sxs-lookup"><span data-stu-id="75432-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
-   <span data-ttu-id="75432-107">Zdarzenie jest zgłaszane w dwukrotnie odziedziczoną kontrolkę lub składnika</span><span class="sxs-lookup"><span data-stu-id="75432-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
-   <span data-ttu-id="75432-108">Błąd w czasie projektowania: "Nie można utworzyć składnika"*nazwa składnika*""</span><span class="sxs-lookup"><span data-stu-id="75432-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
-   <span data-ttu-id="75432-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="75432-109">STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="75432-110">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="75432-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="75432-111">Nie można dodać kontrolki do przybornika</span><span class="sxs-lookup"><span data-stu-id="75432-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="75432-112">Jeśli chcesz dodać formant niestandardowy, który został utworzony w innym projekcie lub kontrolki z innych firm **przybornika**, należy to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="75432-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="75432-113">Jeśli bieżący projekt zawiera kontrolki lub składnika, powinien pojawić się w **przybornika** automatycznie.</span><span class="sxs-lookup"><span data-stu-id="75432-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="75432-114">Aby uzyskać więcej informacji, zobacz [instruktażu: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="75432-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="75432-115">Aby dodać formant do przybornika</span><span class="sxs-lookup"><span data-stu-id="75432-115">To add a control to the Toolbox</span></span>  
  
1. <span data-ttu-id="75432-116">Kliknij prawym przyciskiem myszy **przybornika** z menu skrótów wybierz **wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="75432-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2. <span data-ttu-id="75432-117">W **wybierz elementy przybornika** okna dialogowego Dodaj składnik:</span><span class="sxs-lookup"><span data-stu-id="75432-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    -   <span data-ttu-id="75432-118">Jeśli chcesz dodać do składnik .NET Framework lub formantu, kliknij przycisk **składników .NET Framework** kartę.</span><span class="sxs-lookup"><span data-stu-id="75432-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="75432-119">— lub —</span><span class="sxs-lookup"><span data-stu-id="75432-119">– or –</span></span>  
  
    -   <span data-ttu-id="75432-120">Aby dodać składnik COM lub formantu ActiveX, kliknij przycisk **składników COM** kartę.</span><span class="sxs-lookup"><span data-stu-id="75432-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3. <span data-ttu-id="75432-121">Jeśli formant znajduje się w oknie dialogowym, upewnij się, jest zaznaczone, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="75432-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="75432-122">Formant jest dodawany do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="75432-122">The control is added to the **Toolbox**.</span></span>  
  
4. <span data-ttu-id="75432-123">Jeśli formant nie znajduje się w oknie dialogowym, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="75432-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="75432-124">Kliknij przycisk **Przeglądaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="75432-124">Click the **Browse** button.</span></span>  
  
    2.  <span data-ttu-id="75432-125">Przejdź do folderu, który zawiera plik .dll, który zawiera formant.</span><span class="sxs-lookup"><span data-stu-id="75432-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3.  <span data-ttu-id="75432-126">Wybierz plik .dll, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="75432-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="75432-127">Formant zostanie wyświetlony w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="75432-127">Your control appears in the dialog box.</span></span>  
  
    4.  <span data-ttu-id="75432-128">Upewnij się, czy formant jest zaznaczone, a następnie kliknij **OK**.</span><span class="sxs-lookup"><span data-stu-id="75432-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="75432-129">Formant jest dodawany do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="75432-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="75432-130">Nie można debugować kontrolki użytkownika interfejsu Windows Forms lub składnika</span><span class="sxs-lookup"><span data-stu-id="75432-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="75432-131">Jeśli pochodzi od klasy formantu <xref:System.Windows.Forms.UserControl> klasy, można debugować jego zachowanie w czasie wykonywania za pomocą kontenera testu.</span><span class="sxs-lookup"><span data-stu-id="75432-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="75432-132">Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="75432-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="75432-133">Inne niestandardowe formanty i składniki nie są autonomiczne projektów.</span><span class="sxs-lookup"><span data-stu-id="75432-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="75432-134">One muszą być obsługiwane przez aplikację, taki jak projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="75432-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="75432-135">Aby debugować formant lub składnika, należy dodać go do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="75432-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="75432-136">Aby debugować formant lub składnika</span><span class="sxs-lookup"><span data-stu-id="75432-136">To debug a control or component</span></span>  
  
1. <span data-ttu-id="75432-137">Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie** tworzenia rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="75432-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2. <span data-ttu-id="75432-138">Z **pliku** menu, wybierz **Dodaj**, a następnie **nowy projekt** dodać projekt testowy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="75432-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3. <span data-ttu-id="75432-139">W **Dodaj nowy projekt** okno dialogowe Wybierz **aplikacji Windows** dla typu projektu.</span><span class="sxs-lookup"><span data-stu-id="75432-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4. <span data-ttu-id="75432-140">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł dla nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="75432-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="75432-141">W menu skrótów kliknij **Dodaj odwołanie** można dodać odwołania do projektu zawierającego kontrola lub składników.</span><span class="sxs-lookup"><span data-stu-id="75432-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5. <span data-ttu-id="75432-142">Utwórz wystąpienie składnika lub kontrolki w projekcie testowym.</span><span class="sxs-lookup"><span data-stu-id="75432-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="75432-143">Jeśli składnik jest w **przybornika**, a następnie przeciągnij go do Twojego powierzchni projektanta lub można utworzyć wystąpienia programistycznie, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="75432-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="75432-144">Można teraz debugować swoje kontroli lub składnika w zwykły sposób w całym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="75432-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="75432-145">Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) i [instruktażu: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="75432-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="75432-146">Zdarzenie jest zgłaszane w dwukrotnie odziedziczoną kontrolkę lub składnika</span><span class="sxs-lookup"><span data-stu-id="75432-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="75432-147">Jest to prawdopodobnie spowodowane zduplikowane `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="75432-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="75432-148">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dziedziczone procedury obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="75432-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="75432-149">Błąd w czasie projektowania: "Nie można utworzyć składnika"Nazwa składnika""</span><span class="sxs-lookup"><span data-stu-id="75432-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="75432-150">Składnik lub kontrolki, należy podać domyślnego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="75432-150">Your component or control must provide a default constructor with no parameters.</span></span> <span data-ttu-id="75432-151">Gdy środowisko projektowania tworzy wystąpienie składnika lub kontrolki, nie próbuje zapewniają żadnych parametrów do przeciążenia konstruktora, które przyjmują parametry.</span><span class="sxs-lookup"><span data-stu-id="75432-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="75432-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="75432-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="75432-153"><xref:System.STAThreadAttribute> Informuje środowisko uruchomieniowe języka wspólnego (CLR), Windows Forms korzysta z modelu apartamentem jednowątkowym.</span><span class="sxs-lookup"><span data-stu-id="75432-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="75432-154">Możesz zauważyć niezamierzone zachowanie, jeśli ten atrybut nie są stosowane do aplikacji Windows Forms `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="75432-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="75432-155">Na przykład obrazy tła mogą być niewidoczne dla kontrolki, takie jak <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="75432-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="75432-156">Niektóre kontrolki mogą także wymagać tego atrybutu poprawne Autouzupełnianie i zachowanie przeciągnij i upuść.</span><span class="sxs-lookup"><span data-stu-id="75432-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="75432-157">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="75432-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="75432-158">Kiedy używasz <xref:System.Drawing.ToolboxBitmapAttribute> zostać skojarzona ikona za pomocą składnika niestandardowego, mapa bitowa nie ma w przyborniku dla składników wygenerowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="75432-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="75432-159">Aby wyświetlić mapę bitową, należy ponownie załadować formantu za pomocą **wybierz elementy przybornika** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="75432-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="75432-160">Aby uzyskać więcej informacji, zobacz [jak: Dostarczanie mapy bitowej przybornika dla formantu](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="75432-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75432-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75432-161">See also</span></span>

- [<span data-ttu-id="75432-162">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="75432-162">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="75432-163">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="75432-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="75432-164">Instrukcje: Testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="75432-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="75432-165">Przewodnik: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="75432-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="75432-166">[Tworzenie składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="75432-166">[Component Authoring](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span></span>
- <span data-ttu-id="75432-167">[Rozwiązywanie problemów podczas projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="75432-167">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
