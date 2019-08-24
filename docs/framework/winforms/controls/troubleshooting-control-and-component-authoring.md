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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2e0b98107ac5f43c80aad6cb5ea61e6f4e1e28d3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015715"
---
# <a name="troubleshoot-control-and-component-authoring"></a><span data-ttu-id="b9749-102">Rozwiązywanie problemów dotyczących kontroli i tworzenia składników</span><span class="sxs-lookup"><span data-stu-id="b9749-102">Troubleshoot Control and Component Authoring</span></span>

<span data-ttu-id="b9749-103">W tym temacie wymieniono następujące typowe problemy związane z tworzeniem składników i kontrolek:</span><span class="sxs-lookup"><span data-stu-id="b9749-103">This topic lists the following common problems that arise when developing components and controls:</span></span>

- <span data-ttu-id="b9749-104">Nie można dodać kontrolki do przybornika</span><span class="sxs-lookup"><span data-stu-id="b9749-104">Cannot Add Control to Toolbox</span></span>

- <span data-ttu-id="b9749-105">Nie można debugować kontrolki użytkownika Windows Forms lub składnika</span><span class="sxs-lookup"><span data-stu-id="b9749-105">Cannot Debug the Windows Forms User Control or Component</span></span>

- <span data-ttu-id="b9749-106">Zdarzenie jest zgłaszane dwa razy w dziedziczonej kontrolce lub składniku</span><span class="sxs-lookup"><span data-stu-id="b9749-106">Event Is Raised Twice in Inherited Control or Component</span></span>

- <span data-ttu-id="b9749-107">Błąd czasu projektowania: "Nie można utworzyć składnika"*Nazwa składnika*""</span><span class="sxs-lookup"><span data-stu-id="b9749-107">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>

- <span data-ttu-id="b9749-108">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="b9749-108">STAThreadAttribute</span></span>

- <span data-ttu-id="b9749-109">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="b9749-109">Component Icon Does Not Appear in Toolbox</span></span>

## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="b9749-110">Nie można dodać kontrolki do przybornika</span><span class="sxs-lookup"><span data-stu-id="b9749-110">Cannot Add Control to Toolbox</span></span>

<span data-ttu-id="b9749-111">Aby dodać kontrolkę niestandardową utworzoną w innym projekcie lub kontrolce innej firmy do przybornika, należy tozrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="b9749-111">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="b9749-112">Jeśli bieżący projekt zawiera kontrolkę lub składnik, powinien być automatycznie wyświetlany w **przyborniku** .</span><span class="sxs-lookup"><span data-stu-id="b9749-112">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="b9749-113">Aby uzyskać więcej informacji, [zobacz Przewodnik: Automatyczne wypełnianie przybornika składnikami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)niestandardowymi.</span><span class="sxs-lookup"><span data-stu-id="b9749-113">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="b9749-114">Aby dodać kontrolkę do przybornika</span><span class="sxs-lookup"><span data-stu-id="b9749-114">To add a control to the Toolbox</span></span>

1. <span data-ttu-id="b9749-115">Kliknij prawym przyciskiem myszy **Przybornik** i z menu skrótów wybierz **polecenie Wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="b9749-115">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>

2. <span data-ttu-id="b9749-116">W oknie dialogowym **Wybierz elementy przybornika** Dodaj składnik:</span><span class="sxs-lookup"><span data-stu-id="b9749-116">In the **Choose Toolbox Items** dialog box, add the component:</span></span>

    - <span data-ttu-id="b9749-117">Jeśli chcesz dodać składnik .NET Framework lub kontrolkę, kliknij kartę **składniki .NET Framework** .</span><span class="sxs-lookup"><span data-stu-id="b9749-117">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>

         <span data-ttu-id="b9749-118">— lub —</span><span class="sxs-lookup"><span data-stu-id="b9749-118">– or –</span></span>

    - <span data-ttu-id="b9749-119">Jeśli chcesz dodać składnik COM lub kontrolkę ActiveX, kliknij kartę **składniki com** .</span><span class="sxs-lookup"><span data-stu-id="b9749-119">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>

3. <span data-ttu-id="b9749-120">Jeśli formant znajduje się na liście w oknie dialogowym, potwierdź, że jest zaznaczone, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b9749-120">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>

     <span data-ttu-id="b9749-121">Kontrolka zostanie dodana do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="b9749-121">The control is added to the **Toolbox**.</span></span>

4. <span data-ttu-id="b9749-122">Jeśli formant nie znajduje się na liście w oknie dialogowym, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b9749-122">If your control is not listed in the dialog box, do the following:</span></span>

    1. <span data-ttu-id="b9749-123">Kliknij przycisk **Przeglądaj** .</span><span class="sxs-lookup"><span data-stu-id="b9749-123">Click the **Browse** button.</span></span>

    2. <span data-ttu-id="b9749-124">Przejdź do folderu, który zawiera plik. dll, który zawiera kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="b9749-124">Browse to the folder that contains the .dll file that contains your control.</span></span>

    3. <span data-ttu-id="b9749-125">Wybierz plik. dll, a następnie kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="b9749-125">Select the .dll file and click **Open**.</span></span>

         <span data-ttu-id="b9749-126">Kontrolka zostanie wyświetlona w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="b9749-126">Your control appears in the dialog box.</span></span>

    4. <span data-ttu-id="b9749-127">Upewnij się, że formant jest zaznaczony, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b9749-127">Confirm that your control is selected, and then click **OK**.</span></span>

         <span data-ttu-id="b9749-128">Kontrolka zostanie dodana do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="b9749-128">Your control is added to the **Toolbox**.</span></span>

## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="b9749-129">Nie można debugować kontrolki użytkownika Windows Forms lub składnika</span><span class="sxs-lookup"><span data-stu-id="b9749-129">Cannot Debug the Windows Forms User Control or Component</span></span>

<span data-ttu-id="b9749-130">Jeśli formant pochodzi z <xref:System.Windows.Forms.UserControl> klasy, można debugować jego zachowanie w czasie wykonywania za pomocą kontenera testowego.</span><span class="sxs-lookup"><span data-stu-id="b9749-130">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="b9749-131">Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b9749-131">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="b9749-132">Inne niestandardowe kontrolki i składniki nie są projektami autonomicznymi.</span><span class="sxs-lookup"><span data-stu-id="b9749-132">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="b9749-133">Muszą one być hostowane przez aplikację, taką jak projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b9749-133">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="b9749-134">Aby debugować formant lub składnik, należy dodać go do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b9749-134">To debug a control or component, you must add it to a Windows Forms project.</span></span>

### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="b9749-135">Aby debugować formant lub składnik</span><span class="sxs-lookup"><span data-stu-id="b9749-135">To debug a control or component</span></span>

1. <span data-ttu-id="b9749-136">W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie** , aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="b9749-136">From the **Build** menu, click **Build Solution** to build your solution.</span></span>

2. <span data-ttu-id="b9749-137">Z menu **plik** wybierz polecenie **Dodaj**, a następnie **Nowy projekt** , aby dodać projekt testowy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9749-137">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>

3. <span data-ttu-id="b9749-138">W oknie dialogowym **Dodaj nowy projekt** wybierz pozycję **aplikacja systemu Windows** dla typu projektu.</span><span class="sxs-lookup"><span data-stu-id="b9749-138">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>

4. <span data-ttu-id="b9749-139">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="b9749-139">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="b9749-140">W menu skrótów kliknij pozycję **Dodaj odwołanie** , aby dodać odwołanie do projektu zawierającego formant lub składnik.</span><span class="sxs-lookup"><span data-stu-id="b9749-140">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>

5. <span data-ttu-id="b9749-141">Utwórz wystąpienie formantu lub składnika w projekcie testowym.</span><span class="sxs-lookup"><span data-stu-id="b9749-141">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="b9749-142">Jeśli składnik znajduje się w **przyborniku**, możesz go przeciągnąć na powierzchnię projektanta lub można utworzyć wystąpienie programowo, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b9749-142">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>

    ```vb
    Dim Component1 As New MyNeatComponent()
    ```

    ```csharp
    MyNeatComponent Component1 = new MyNeatComponent();
    ```

   <span data-ttu-id="b9749-143">Teraz można debugować formant lub składnik w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="b9749-143">You can now debug your control or component as usual.</span></span>

<span data-ttu-id="b9749-144">Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) i [Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)projektowania.</span><span class="sxs-lookup"><span data-stu-id="b9749-144">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="b9749-145">Zdarzenie jest zgłaszane dwa razy w dziedziczonej kontrolce lub składniku</span><span class="sxs-lookup"><span data-stu-id="b9749-145">Event Is Raised Twice in Inherited Control or Component</span></span>

<span data-ttu-id="b9749-146">Prawdopodobnie jest to spowodowane zduplikowaną `Handles` klauzulą.</span><span class="sxs-lookup"><span data-stu-id="b9749-146">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="b9749-147">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="b9749-147">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="b9749-148">Błąd czasu projektowania: "Nie można utworzyć składnika" Nazwa składnika ""</span><span class="sxs-lookup"><span data-stu-id="b9749-148">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>

<span data-ttu-id="b9749-149">Składnik lub formant muszą dostarczać Konstruktor bez parametrów z parametrami.</span><span class="sxs-lookup"><span data-stu-id="b9749-149">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="b9749-150">Gdy środowisko projektowe tworzy wystąpienie składnika lub formantu, nie podejmuje próby dostarczenia żadnych parametrów do przeciążenia konstruktorów przyjmujących parametry.</span><span class="sxs-lookup"><span data-stu-id="b9749-150">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>

## <a name="stathreadattribute"></a><span data-ttu-id="b9749-151">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="b9749-151">STAThreadAttribute</span></span>

<span data-ttu-id="b9749-152"><xref:System.STAThreadAttribute> Informuje o tym, że środowisko uruchomieniowe języka wspólnego (CLR), które Windows Forms używa modelu apartamentu jednowątkowego.</span><span class="sxs-lookup"><span data-stu-id="b9749-152">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="b9749-153">Możesz zauważyć niezamierzone zachowanie, jeśli nie zastosujesz tego atrybutu do `Main` metody aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b9749-153">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="b9749-154">Na przykład obrazy tła mogą nie być wyświetlane dla kontrolek <xref:System.Windows.Forms.ListView>takich jak.</span><span class="sxs-lookup"><span data-stu-id="b9749-154">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="b9749-155">Niektóre kontrolki mogą również wymagać tego atrybutu w celu poprawnego autouzupełniania oraz zachowania przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="b9749-155">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>

## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="b9749-156">Ikona składnika nie jest wyświetlana w przyborniku</span><span class="sxs-lookup"><span data-stu-id="b9749-156">Component Icon Does Not Appear in Toolbox</span></span>

<span data-ttu-id="b9749-157">Gdy używasz <xref:System.Drawing.ToolboxBitmapAttribute> do kojarzenia ikony ze składnikiem niestandardowym, mapa bitowa nie jest wyświetlana w przyborniku dla automatycznie generowanych składników.</span><span class="sxs-lookup"><span data-stu-id="b9749-157">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="b9749-158">Aby wyświetlić mapę bitową, Załaduj ponownie formant przy użyciu okna dialogowego **Wybierz elementy przybornika** .</span><span class="sxs-lookup"><span data-stu-id="b9749-158">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="b9749-159">Aby uzyskać więcej informacji, zobacz [jak: Udostępnianie mapy bitowej przybornika dla kontrolki](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="b9749-159">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9749-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9749-160">See also</span></span>

- [<span data-ttu-id="b9749-161">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="b9749-161">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="b9749-162">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="b9749-162">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="b9749-163">Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="b9749-163">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="b9749-164">Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="b9749-164">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
