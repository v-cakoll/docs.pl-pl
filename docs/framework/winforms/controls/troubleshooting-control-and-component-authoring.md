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
ms.openlocfilehash: 6494a154b9b4bd5bf29fc0e2fbd0b4e5e84550ff
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364166"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="3a804-102">Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów</span><span class="sxs-lookup"><span data-stu-id="3a804-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="3a804-103">W tym temacie wymieniono następujące typowe problemy występujące podczas opracowywania składników i kontrolek.</span><span class="sxs-lookup"><span data-stu-id="3a804-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="3a804-104">Aby uzyskać więcej informacji, zobacz [programowanie ze składnikami](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="3a804-104">For more information, see [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
- <span data-ttu-id="3a804-105">Nie można dodać kontrolki do przybornika</span><span class="sxs-lookup"><span data-stu-id="3a804-105">Cannot Add Control to Toolbox</span></span>  
  
- <span data-ttu-id="3a804-106">Nie można debugować kontrolki użytkownika Windows Forms lub składnika</span><span class="sxs-lookup"><span data-stu-id="3a804-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
- <span data-ttu-id="3a804-107">Zdarzenie jest zgłaszane dwa razy w dziedziczonej kontrolce lub składniku</span><span class="sxs-lookup"><span data-stu-id="3a804-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
- <span data-ttu-id="3a804-108">Błąd czasu projektowania: "Nie można utworzyć składnika"*Nazwa składnika*""</span><span class="sxs-lookup"><span data-stu-id="3a804-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
- <span data-ttu-id="3a804-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="3a804-109">STAThreadAttribute</span></span>  
  
- <span data-ttu-id="3a804-110">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="3a804-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="3a804-111">Nie można dodać kontrolki do przybornika</span><span class="sxs-lookup"><span data-stu-id="3a804-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="3a804-112">Aby dodać kontrolkę niestandardową utworzoną w innym projekcie lub kontrolce innej firmy do przybornika, należy to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="3a804-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="3a804-113">Jeśli bieżący projekt zawiera kontrolkę lub składnik, powinien być automatycznie wyświetlany w **przyborniku** .</span><span class="sxs-lookup"><span data-stu-id="3a804-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="3a804-114">Aby uzyskać więcej informacji, [zobacz Przewodnik: Automatyczne wypełnianie przybornika składnikami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)niestandardowymi.</span><span class="sxs-lookup"><span data-stu-id="3a804-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="3a804-115">Aby dodać kontrolkę do przybornika</span><span class="sxs-lookup"><span data-stu-id="3a804-115">To add a control to the Toolbox</span></span>  
  
1. <span data-ttu-id="3a804-116">Kliknij prawym przyciskiem myszy **Przybornik** i z menu skrótów wybierz **polecenie Wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="3a804-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2. <span data-ttu-id="3a804-117">W oknie dialogowym **Wybierz elementy przybornika** Dodaj składnik:</span><span class="sxs-lookup"><span data-stu-id="3a804-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    - <span data-ttu-id="3a804-118">Jeśli chcesz dodać składnik .NET Framework lub kontrolkę, kliknij kartę **składniki .NET Framework** .</span><span class="sxs-lookup"><span data-stu-id="3a804-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="3a804-119">— lub —</span><span class="sxs-lookup"><span data-stu-id="3a804-119">– or –</span></span>  
  
    - <span data-ttu-id="3a804-120">Jeśli chcesz dodać składnik COM lub kontrolkę ActiveX, kliknij kartę **składniki com** .</span><span class="sxs-lookup"><span data-stu-id="3a804-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3. <span data-ttu-id="3a804-121">Jeśli formant znajduje się na liście w oknie dialogowym, potwierdź, że jest zaznaczone, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="3a804-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3a804-122">Kontrolka zostanie dodana do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="3a804-122">The control is added to the **Toolbox**.</span></span>  
  
4. <span data-ttu-id="3a804-123">Jeśli formant nie znajduje się na liście w oknie dialogowym, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="3a804-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1. <span data-ttu-id="3a804-124">Kliknij przycisk **Przeglądaj** .</span><span class="sxs-lookup"><span data-stu-id="3a804-124">Click the **Browse** button.</span></span>  
  
    2. <span data-ttu-id="3a804-125">Przejdź do folderu, który zawiera plik. dll, który zawiera kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="3a804-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3. <span data-ttu-id="3a804-126">Wybierz plik. dll, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="3a804-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="3a804-127">Kontrolka zostanie wyświetlona w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="3a804-127">Your control appears in the dialog box.</span></span>  
  
    4. <span data-ttu-id="3a804-128">Upewnij się, że formant jest zaznaczony, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="3a804-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="3a804-129">Kontrolka zostanie dodana do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="3a804-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="3a804-130">Nie można debugować kontrolki użytkownika Windows Forms lub składnika</span><span class="sxs-lookup"><span data-stu-id="3a804-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="3a804-131">Jeśli formant pochodzi z <xref:System.Windows.Forms.UserControl> klasy, można debugować jego zachowanie w czasie wykonywania za pomocą kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="3a804-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="3a804-132">Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3a804-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="3a804-133">Inne niestandardowe kontrolki i składniki nie są projektami autonomicznymi.</span><span class="sxs-lookup"><span data-stu-id="3a804-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="3a804-134">Muszą one być hostowane przez aplikację, taką jak projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3a804-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="3a804-135">Aby debugować formant lub składnik, należy dodać go do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3a804-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="3a804-136">Aby debugować formant lub składnik</span><span class="sxs-lookup"><span data-stu-id="3a804-136">To debug a control or component</span></span>  
  
1. <span data-ttu-id="3a804-137">W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie** , aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="3a804-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2. <span data-ttu-id="3a804-138">Z menu **plik** wybierz polecenie **Dodaj**, a następnie **Nowy projekt** , aby dodać projekt testowy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a804-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3. <span data-ttu-id="3a804-139">W oknie dialogowym **Dodaj nowy projekt** wybierz pozycję **aplikacja systemu Windows** dla typu projektu.</span><span class="sxs-lookup"><span data-stu-id="3a804-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4. <span data-ttu-id="3a804-140">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="3a804-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="3a804-141">W menu skrótów kliknij pozycję **Dodaj odwołanie** , aby dodać odwołanie do projektu zawierającego formant lub składnik.</span><span class="sxs-lookup"><span data-stu-id="3a804-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5. <span data-ttu-id="3a804-142">Utwórz wystąpienie formantu lub składnika w projekcie testowym.</span><span class="sxs-lookup"><span data-stu-id="3a804-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="3a804-143">Jeśli składnik znajduje się w **przyborniku**, możesz go przeciągnąć na powierzchnię projektanta lub można utworzyć wystąpienie programowo, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="3a804-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="3a804-144">Teraz można debugować formant lub składnik w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="3a804-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="3a804-145">Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) i [Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)projektowania.</span><span class="sxs-lookup"><span data-stu-id="3a804-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="3a804-146">Zdarzenie jest zgłaszane dwa razy w dziedziczonej kontrolce lub składniku</span><span class="sxs-lookup"><span data-stu-id="3a804-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="3a804-147">Prawdopodobnie jest to spowodowane zduplikowaną `Handles` klauzulą.</span><span class="sxs-lookup"><span data-stu-id="3a804-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="3a804-148">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="3a804-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="3a804-149">Błąd czasu projektowania: "Nie można utworzyć składnika" Nazwa składnika ""</span><span class="sxs-lookup"><span data-stu-id="3a804-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="3a804-150">Składnik lub formant muszą dostarczać Konstruktor bez parametrów z parametrami.</span><span class="sxs-lookup"><span data-stu-id="3a804-150">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="3a804-151">Gdy środowisko projektowe tworzy wystąpienie składnika lub formantu, nie podejmuje próby dostarczenia żadnych parametrów do przeciążenia konstruktorów przyjmujących parametry.</span><span class="sxs-lookup"><span data-stu-id="3a804-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="3a804-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="3a804-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="3a804-153"><xref:System.STAThreadAttribute> Informuje o tym, że środowisko uruchomieniowe języka wspólnego (CLR), które Windows Forms używa modelu apartamentu jednowątkowego.</span><span class="sxs-lookup"><span data-stu-id="3a804-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="3a804-154">Możesz zauważyć niezamierzone zachowanie, jeśli nie zastosujesz tego atrybutu do `Main` metody aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3a804-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="3a804-155">Na przykład obrazy tła mogą nie być wyświetlane dla kontrolek <xref:System.Windows.Forms.ListView>takich jak.</span><span class="sxs-lookup"><span data-stu-id="3a804-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="3a804-156">Niektóre kontrolki mogą również wymagać tego atrybutu w celu poprawnego autouzupełniania oraz zachowania przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="3a804-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="3a804-157">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="3a804-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="3a804-158">Gdy używasz <xref:System.Drawing.ToolboxBitmapAttribute> do kojarzenia ikony ze składnikiem niestandardowym, mapa bitowa nie jest wyświetlana w przyborniku dla automatycznie generowanych składników.</span><span class="sxs-lookup"><span data-stu-id="3a804-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="3a804-159">Aby wyświetlić mapę bitową, Załaduj ponownie formant przy użyciu okna dialogowego **Wybierz elementy przybornika** .</span><span class="sxs-lookup"><span data-stu-id="3a804-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="3a804-160">Aby uzyskać więcej informacji, zobacz [jak: Udostępnianie mapy bitowej przybornika dla kontrolki](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="3a804-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a804-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a804-161">See also</span></span>

- [<span data-ttu-id="3a804-162">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="3a804-162">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="3a804-163">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="3a804-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="3a804-164">Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="3a804-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="3a804-165">Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="3a804-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="3a804-166">[Tworzenie składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="3a804-166">[Component Authoring](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span></span>
- <span data-ttu-id="3a804-167">[Rozwiązywanie problemów związanych z projektowaniem czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="3a804-167">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
