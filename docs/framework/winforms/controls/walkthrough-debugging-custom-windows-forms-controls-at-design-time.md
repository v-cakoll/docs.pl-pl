---
title: 'Przewodnik: debugowanie niestandardowych kontrolek formularzy systemu Windows w czasie projektowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
ms.openlocfilehash: db6266f30c4fb62364f3c40a75a4a11ef853c1cb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325361"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="f2a90-102">Przewodnik: debugowanie niestandardowych kontrolek formularzy systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f2a90-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="f2a90-103">Kiedy tworzysz formant niestandardowy, będzie często jest konieczne do debugowania zachowania w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="f2a90-104">Jest to szczególnie istotne w przypadku tworzenia niestandardowego projektanta dla formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f2a90-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="f2a90-105">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie Windows Forms kontroli wykorzystującego funkcje czasu projektowania w programie Visual Studio](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="f2a90-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="f2a90-106">Kontrolki niestandardowe przy użyciu programu Visual Studio umożliwia debugowanie tak samo, jak debuguje się inne klasy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f2a90-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="f2a90-107">Różnica polega na to, że będziesz debugował osobnego wystąpienia programu Visual Studio, który jest uruchomiony kod kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f2a90-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="f2a90-108">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="f2a90-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="f2a90-109">Tworzenie projektu Windows Forms do hostowania formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="f2a90-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="f2a90-110">Tworzenie projektu biblioteki kontrolek</span><span class="sxs-lookup"><span data-stu-id="f2a90-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="f2a90-111">Dodawanie właściwości do kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f2a90-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="f2a90-112">Dodawanie niestandardowego formantu do formularza hosta</span><span class="sxs-lookup"><span data-stu-id="f2a90-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="f2a90-113">Konfigurowanie projektu dla debugowania w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f2a90-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="f2a90-114">Debugowanie niestandardowego formantu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f2a90-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="f2a90-115">Gdy skończysz, masz zrozumienia zadań niezbędnych do debugowania zachowania w czasie projektowania formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f2a90-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2a90-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f2a90-117">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="f2a90-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f2a90-118">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f2a90-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f2a90-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="f2a90-119">Creating the Project</span></span>  
 <span data-ttu-id="f2a90-120">Pierwszym krokiem jest utworzenie projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2a90-120">The first step is to create the application project.</span></span> <span data-ttu-id="f2a90-121">Użyjesz tego projektu do kompilowania aplikacji, który jest hostem kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f2a90-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="f2a90-122">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="f2a90-122">To create the project</span></span>  
  
-   <span data-ttu-id="f2a90-123">Utwórz projekt aplikacji Windows o nazwie "DebuggingExample" (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="f2a90-123">Create a Windows Application project called "DebuggingExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="f2a90-124">Tworzenie projektu biblioteki kontrolek</span><span class="sxs-lookup"><span data-stu-id="f2a90-124">Creating a Control Library Project</span></span>  
 <span data-ttu-id="f2a90-125">Następnym krokiem jest tworzenie projektu biblioteki kontrolek i konfigurowanie kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f2a90-125">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="f2a90-126">Aby utworzyć projekt Biblioteka formantów</span><span class="sxs-lookup"><span data-stu-id="f2a90-126">To create the control library project</span></span>  
  
1. <span data-ttu-id="f2a90-127">Dodaj **Biblioteka formantów Windows** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-127">Add a **Windows Control Library** project to the solution.</span></span>  
  
2. <span data-ttu-id="f2a90-128">Dodaj nową **UserControl** elementu do projektu DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="f2a90-128">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="f2a90-129">Aby uzyskać więcej informacji, zobacz [jak: Dodaj nowe elementy projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f2a90-129">For details, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span> <span data-ttu-id="f2a90-130">Nazwij nowy plik źródłowy podstawowego elementu "DebugControl".</span><span class="sxs-lookup"><span data-stu-id="f2a90-130">Give the new source file a base name of "DebugControl".</span></span>  
  
3. <span data-ttu-id="f2a90-131">Za pomocą **Eksploratora rozwiązań**, usunąć projekt domyślny formant przez usunięcie pliku kodu z podstawowej nazwy "`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="f2a90-131">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="f2a90-132">Aby uzyskać więcej informacji, zobacz [jak: Usuń Delete i wykluczyć elementy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f2a90-132">For details, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>  
  
4. <span data-ttu-id="f2a90-133">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="f2a90-133">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="f2a90-134">Punkt kontrolny</span><span class="sxs-lookup"><span data-stu-id="f2a90-134">Checkpoint</span></span>  
 <span data-ttu-id="f2a90-135">W tym momencie można wyświetlić niestandardową kontrolkę w **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="f2a90-135">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="f2a90-136">Aby sprawdzić postęp</span><span class="sxs-lookup"><span data-stu-id="f2a90-136">To check your progress</span></span>  
  
-   <span data-ttu-id="f2a90-137">Znajdź Nowa karta o nazwie **składniki DebugControlLibrary** i kliknij, aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="f2a90-137">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="f2a90-138">Po otwarciu, zobaczysz kontrolki wymieniony jako **DebugControl** z domyślną ikonę obok niej.</span><span class="sxs-lookup"><span data-stu-id="f2a90-138">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="f2a90-139">Dodawanie właściwości do kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f2a90-139">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="f2a90-140">Aby zademonstrować, że formant niestandardowy kod jest uruchamiany w czasie projektowania, możesz dodać właściwość i ustaw punkt przerwania w kodzie, który implementuje właściwości.</span><span class="sxs-lookup"><span data-stu-id="f2a90-140">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="f2a90-141">Aby dodać właściwość do formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="f2a90-141">To add a property to your custom control</span></span>  
  
1. <span data-ttu-id="f2a90-142">Otwórz **DebugControl** w **Edytor kodu**.</span><span class="sxs-lookup"><span data-stu-id="f2a90-142">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="f2a90-143">Dodaj następujący kod do definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="f2a90-143">Add the following code to the class definition:</span></span>  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2. <span data-ttu-id="f2a90-144">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="f2a90-144">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="f2a90-145">Dodawanie niestandardowego formantu do formularza hosta</span><span class="sxs-lookup"><span data-stu-id="f2a90-145">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="f2a90-146">Do debugowania zachowania w czasie projektowania niestandardową kontrolkę, spowoduje umieszczenie wystąpienia klasy kontrolki niestandardowej w formularzu hosta.</span><span class="sxs-lookup"><span data-stu-id="f2a90-146">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="f2a90-147">Aby dodać niestandardową kontrolkę w formularzu hosta</span><span class="sxs-lookup"><span data-stu-id="f2a90-147">To add your custom control to the host form</span></span>  
  
1. <span data-ttu-id="f2a90-148">W projekcie "DebuggingExample" Otwórz formularz Form1 w **Windows Forms Designer**.</span><span class="sxs-lookup"><span data-stu-id="f2a90-148">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2. <span data-ttu-id="f2a90-149">W **przybornika**, otwórz **składniki DebugControlLibrary** kartę, a następnie przeciągnij **DebugControl** wystąpienia do formularza.</span><span class="sxs-lookup"><span data-stu-id="f2a90-149">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3. <span data-ttu-id="f2a90-150">Znajdź `DemoString` właściwości niestandardowe w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="f2a90-150">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="f2a90-151">Należy pamiętać, że można zmienić jego wartość, jak w przypadku wszystkich innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="f2a90-151">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="f2a90-152">Należy również zauważyć, że w przypadku `DemoString` właściwości jest zaznaczone, ciąg opisu właściwości, pojawia się w dolnej części **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="f2a90-152">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="f2a90-153">Konfigurowanie projektu dla debugowania w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f2a90-153">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="f2a90-154">Do debugowania zachowania w czasie projektowania formantu niestandardowego, będzie debugować osobnego wystąpienia programu Visual Studio, który jest uruchomiony formantu niestandardowego kodu.</span><span class="sxs-lookup"><span data-stu-id="f2a90-154">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="f2a90-155">Aby skonfigurować projekt do debugowania w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f2a90-155">To set up the project for design-time debugging</span></span>  
  
1. <span data-ttu-id="f2a90-156">Kliknij prawym przyciskiem myszy **DebugControlLibrary** projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f2a90-156">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2. <span data-ttu-id="f2a90-157">W **DebugControlLibrary** arkusza właściwości, wybierz opcję **debugowania** kartę.</span><span class="sxs-lookup"><span data-stu-id="f2a90-157">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="f2a90-158">W **Akcja uruchamiania** zaznacz **uruchomienia programu zewnętrznego**.</span><span class="sxs-lookup"><span data-stu-id="f2a90-158">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="f2a90-159">Można więc debugowanie osobnego wystąpienia programu Visual Studio, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby przejść do środowiska IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2a90-159">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="f2a90-160">Nazwa pliku wykonywalnego jest **devenv.exe**, a jeśli został zainstalowany w lokalizacji domyślnej, jego ścieżka jest %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span><span class="sxs-lookup"><span data-stu-id="f2a90-160">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3. <span data-ttu-id="f2a90-161">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f2a90-161">Click **OK** to close the dialog box.</span></span>  
  
4. <span data-ttu-id="f2a90-162">Kliknij prawym przyciskiem myszy **DebugControlLibrary** projektu, a następnie wybierz **Ustaw jako projekt startowy** umożliwiające tej konfiguracji debugowania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-162">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="f2a90-163">Debugowanie niestandardowego formantu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f2a90-163">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="f2a90-164">Teraz można przystąpić do debugowania niestandardową kontrolkę, jak działa w trybie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-164">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="f2a90-165">Podczas uruchamiania sesji debugowania, zostanie utworzone nowe wystąpienie programu Visual Studio, a następnie użyje ładowanie rozwiązań "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="f2a90-165">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="f2a90-166">Po otwarciu formularza Form1 w **projektanta formularzy**, wystąpienie niestandardową kontrolkę zostanie utworzona i zostanie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="f2a90-166">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="f2a90-167">Aby debugować niestandardową kontrolkę w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f2a90-167">To debug your custom control at design time</span></span>  
  
1. <span data-ttu-id="f2a90-168">Otwórz **DebugControl** pliku źródłowego w **Edytor kodu** i umieść punkt przerwania na `Set` akcesor `DemoString` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f2a90-168">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2. <span data-ttu-id="f2a90-169">Naciśnij klawisz F5, aby rozpocząć sesję debugowania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-169">Press F5 to start the debugging session.</span></span> <span data-ttu-id="f2a90-170">Należy pamiętać, że tworzone jest nowe wystąpienie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2a90-170">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="f2a90-171">Można rozróżnić wystąpień na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="f2a90-171">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="f2a90-172">Wystąpienie debugowania zawiera wyraz **systemem** na pasku tytułu</span><span class="sxs-lookup"><span data-stu-id="f2a90-172">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="f2a90-173">Wystąpienie debugowania ma **Start** znajdujący się na jej **debugowania** narzędzi wyłączone</span><span class="sxs-lookup"><span data-stu-id="f2a90-173">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="f2a90-174">Punkt przerwania jest ustawiony za wystąpienie debugowania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-174">Your breakpoint is set in the debugging instance.</span></span>  
  
3. <span data-ttu-id="f2a90-175">Nowe wystąpienie programu Visual Studio Otwórz rozwiązanie "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="f2a90-175">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="f2a90-176">Rozwiązanie można łatwo znaleźć, wybierając **ostatnich projektów** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="f2a90-176">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="f2a90-177">Plik rozwiązania "DebuggingExample.sln" będą wyświetlane zgodnie z ostatnio używanych plików.</span><span class="sxs-lookup"><span data-stu-id="f2a90-177">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4. <span data-ttu-id="f2a90-178">Otwórz formularz Form1 w **projektanta formularzy** i wybierz **DebugControl** kontroli.</span><span class="sxs-lookup"><span data-stu-id="f2a90-178">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5. <span data-ttu-id="f2a90-179">Zmień wartość właściwości `DemoString` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f2a90-179">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="f2a90-180">Pamiętaj, że po zatwierdzeniu zmiany wystąpienie debugowania programu Visual Studio uzyskuje fokus wykonywania zatrzymuje się na punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-180">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="f2a90-181">Możesz pojedynczy krok za pomocą metody dostępu właściwości podobnie jak usługi będzie inny kod.</span><span class="sxs-lookup"><span data-stu-id="f2a90-181">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6. <span data-ttu-id="f2a90-182">Po zakończeniu sesji debugowania możesz wyjść, odrzucanie hostowanej wystąpieniu programu Visual Studio lub klikając **Zatrzymaj debugowanie** przycisk wystąpienie debugowania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-182">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f2a90-183">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f2a90-183">Next Steps</span></span>  
 <span data-ttu-id="f2a90-184">Teraz, aby można było debugować Kontrolki niestandardowe, w czasie projektowania, istnieje wiele możliwości rozszerzania kontroli nad interakcji ze środowiskiem IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2a90-184">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="f2a90-185">Możesz użyć <xref:System.ComponentModel.Component.DesignMode%2A> właściwość <xref:System.ComponentModel.Component> klasy pisanie kodu, który będzie wykonywać tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f2a90-185">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="f2a90-186">Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2a90-186">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="f2a90-187">Istnieje kilka atrybutów można zastosować do właściwości formantu do manipulowania interakcji kontrolki niestandardowej za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="f2a90-187">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="f2a90-188">Można znaleźć tych atrybutów w <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f2a90-188">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="f2a90-189">Możesz napisać niestandardowego projektanta dla niestandardowej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f2a90-189">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="f2a90-190">Zapewnia pełną kontrolę nad środowiskiem projektowania przy użyciu rozszerzonego infrastruktury projektanta udostępnianych przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2a90-190">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="f2a90-191">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie Windows Forms kontroli wykorzystującego funkcje czasu projektowania w programie Visual Studio](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="f2a90-191">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a90-192">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2a90-192">See also</span></span>

- [<span data-ttu-id="f2a90-193">Przewodnik: tworzenie kontrolki formularzy systemu Windows wykorzystującego funkcje czasu projektowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f2a90-193">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
- [<span data-ttu-id="f2a90-194">Instrukcje: Dostęp do usługi w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f2a90-194">How to: Access Design-Time Services</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171822(v=vs.120))
- [<span data-ttu-id="f2a90-195">Instrukcje: Dostęp do obsługi w czasie projektowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f2a90-195">How to: Access Design-Time Support in Windows Forms</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171827(v=vs.120))
