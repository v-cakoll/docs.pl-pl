---
title: "Wskazówki: debugowanie niestandardowych formantów formularzy systemu Windows w czasie projektowania"
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dfdc102a5aeb2e3eaccde28a8ce57a1878141e4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="db383-102">Wskazówki: debugowanie niestandardowych formantów formularzy systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="db383-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="db383-103">Podczas tworzenia niestandardowego formantu będzie często jest konieczne do debugowania swojego zachowania w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="db383-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="db383-104">Jest to szczególnie w przypadku tworzenia niestandardowych projektanta dla formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="db383-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="db383-105">Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie funkcje systemu Windows formularze kontroli czy ma korzystać z programu Visual Studio czasu projektowania](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="db383-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="db383-106">Kontrolki niestandardowe przy użyciu programu Visual Studio można debugować tak samo, jak może debugować innych klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db383-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="db383-107">Różnica polega na tym że będzie debugowania osobnego wystąpienia programu Visual Studio, która działa formantu niestandardowego kodu</span><span class="sxs-lookup"><span data-stu-id="db383-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="db383-108">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="db383-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="db383-109">Tworzenie projektu formularzy systemu Windows do hostowania formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="db383-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="db383-110">Tworzenie projektu biblioteki formantu</span><span class="sxs-lookup"><span data-stu-id="db383-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="db383-111">Dodawanie właściwości do formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="db383-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="db383-112">Dodawanie formantu niestandardowego do formularza hosta</span><span class="sxs-lookup"><span data-stu-id="db383-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="db383-113">Konfigurowanie projektu debugowanie w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="db383-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="db383-114">Debugowanie formantu niestandardowego w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="db383-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="db383-115">Gdy skończysz, konieczne będzie zrozumienia zadań niezbędnych do debugowania zachowania czasu projektowania formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="db383-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db383-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="db383-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="db383-117">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="db383-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="db383-118">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="db383-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="db383-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="db383-119">Creating the Project</span></span>  
 <span data-ttu-id="db383-120">Pierwszym krokiem jest utworzenie projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db383-120">The first step is to create the application project.</span></span> <span data-ttu-id="db383-121">Użyjesz tego projektu do tworzenia aplikacji, która obsługuje kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="db383-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="db383-122">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="db383-122">To create the project</span></span>  
  
-   <span data-ttu-id="db383-123">Utwórz projekt aplikacji systemu Windows o nazwie "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="db383-123">Create a Windows Application project called "DebuggingExample".</span></span> <span data-ttu-id="db383-124">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="db383-124">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="db383-125">Tworzenie projektu biblioteki formantu</span><span class="sxs-lookup"><span data-stu-id="db383-125">Creating a Control Library Project</span></span>  
 <span data-ttu-id="db383-126">Następnym krokiem jest utworzenie projektu biblioteki kontroli i skonfigurować kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="db383-126">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="db383-127">Aby utworzyć projekt z kontroli biblioteki</span><span class="sxs-lookup"><span data-stu-id="db383-127">To create the control library project</span></span>  
  
1.  <span data-ttu-id="db383-128">Dodaj **Biblioteka formantów systemu Windows** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="db383-128">Add a **Windows Control Library** project to the solution.</span></span>  
  
2.  <span data-ttu-id="db383-129">Dodaj nową **UserControl** elementu do projektu DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="db383-129">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="db383-130">Aby uzyskać więcej informacji, zobacz [NIB: porady: dodawanie nowych elementów projektu](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="db383-130">For details, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="db383-131">Nadaj nazwę bazową "DebugControl" nowego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="db383-131">Give the new source file a base name of "DebugControl".</span></span>  
  
3.  <span data-ttu-id="db383-132">Przy użyciu **Eksploratora rozwiązań**, usuń formant domyślnego projektu przez usunięcie pliku kodu z podstawowej nazwy "`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="db383-132">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="db383-133">Aby uzyskać więcej informacji, zobacz [NIB: porady: usuwanie, usuwania i wykluczanie elementów](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="db383-133">For details, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
4.  <span data-ttu-id="db383-134">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="db383-134">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="db383-135">Punkt kontrolny</span><span class="sxs-lookup"><span data-stu-id="db383-135">Checkpoint</span></span>  
 <span data-ttu-id="db383-136">W tym momencie można odwołać się do niestandardowego formantu w **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="db383-136">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="db383-137">Aby sprawdzić postęp</span><span class="sxs-lookup"><span data-stu-id="db383-137">To check your progress</span></span>  
  
-   <span data-ttu-id="db383-138">Znajdź nową kartę o nazwie **składniki DebugControlLibrary** i kliknij, aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="db383-138">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="db383-139">Po otwarciu, zobaczysz formantu wymienionym **DebugControl** z domyślną ikonę obok siebie.</span><span class="sxs-lookup"><span data-stu-id="db383-139">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="db383-140">Dodawanie właściwości do formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="db383-140">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="db383-141">Wykazać, że formant niestandardowy kod działa w czasie projektowania, możesz dodać właściwość i ustaw punkt przerwania w kodzie, który implementuje właściwości.</span><span class="sxs-lookup"><span data-stu-id="db383-141">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="db383-142">Aby dodać właściwość do formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="db383-142">To add a property to your custom control</span></span>  
  
1.  <span data-ttu-id="db383-143">Otwórz **DebugControl** w **edytora kodu**.</span><span class="sxs-lookup"><span data-stu-id="db383-143">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="db383-144">Dodaj następujący kod do definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="db383-144">Add the following code to the class definition:</span></span>  
  
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
  
2.  <span data-ttu-id="db383-145">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="db383-145">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="db383-146">Dodawanie formantu niestandardowego do formularza hosta</span><span class="sxs-lookup"><span data-stu-id="db383-146">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="db383-147">Aby debugować zachowania czasu projektowania formantu niestandardowego, zostaną umieszczone wystąpienia klasy kontrolki niestandardowej w formularzu hosta.</span><span class="sxs-lookup"><span data-stu-id="db383-147">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="db383-148">Aby dodać formantu niestandardowego do formularza hosta</span><span class="sxs-lookup"><span data-stu-id="db383-148">To add your custom control to the host form</span></span>  
  
1.  <span data-ttu-id="db383-149">W projekcie "DebuggingExample" otworzyć Form1 w **Projektant formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="db383-149">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="db383-150">W **przybornika**, otwórz **składniki DebugControlLibrary** karcie i przeciągnij **DebugControl** wystąpienia na formularzu.</span><span class="sxs-lookup"><span data-stu-id="db383-150">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3.  <span data-ttu-id="db383-151">Znajdź `DemoString` właściwość niestandardową **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="db383-151">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="db383-152">Należy pamiętać, można zmienić jego wartość, jak w przypadku innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="db383-152">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="db383-153">Należy również zauważyć, że w przypadku `DemoString` właściwość jest wybrana, ciąg opisu właściwości wyświetlane w dolnej części **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="db383-153">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="db383-154">Konfigurowanie projektu debugowanie w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="db383-154">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="db383-155">Aby debugować zachowanie czasu projektowania formantu niestandardowego, będzie debugowania osobnego wystąpienia programu Visual Studio, która działa formantu niestandardowego kodu.</span><span class="sxs-lookup"><span data-stu-id="db383-155">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="db383-156">Aby skonfigurować projekt dla debugowanie w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="db383-156">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="db383-157">Kliknij prawym przyciskiem myszy **DebugControlLibrary** projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="db383-157">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="db383-158">W **DebugControlLibrary** arkusza właściwości, wybierz opcję **debugowania** kartę.</span><span class="sxs-lookup"><span data-stu-id="db383-158">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="db383-159">W **Akcja uruchamiania** zaznacz **uruchomienia programu zewnętrznego**.</span><span class="sxs-lookup"><span data-stu-id="db383-159">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="db383-160">Można więc debugowanie osobnego wystąpienia programu Visual Studio, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby wyszukać środowiska IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="db383-160">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="db383-161">Nazwa pliku wykonywalnego jest **devenv.exe**, a jeśli został zainstalowany w domyślnej lokalizacji ścieżki %programfiles%\Microsoft 9.0\Common7\IDE\devenv.exe programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="db383-161">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3.  <span data-ttu-id="db383-162">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="db383-162">Click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="db383-163">Kliknij prawym przyciskiem myszy **DebugControlLibrary** projekt i wybierz **Ustaw jako projekt startowy** umożliwiające tej konfiguracji debugowania.</span><span class="sxs-lookup"><span data-stu-id="db383-163">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="db383-164">Debugowanie formantu niestandardowego w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="db383-164">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="db383-165">Teraz można przystąpić do debugowania formantu niestandardowego, jak działa w trybie projektowania.</span><span class="sxs-lookup"><span data-stu-id="db383-165">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="db383-166">Po ponownym uruchomieniu sesji debugowania, zostanie utworzone nowe wystąpienie programu Visual Studio i użyje do załadowania rozwiązania "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="db383-166">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="db383-167">Po otwarciu Form1 w **Projektant formularzy**, wystąpienie formantu niestandardowego zostanie utworzona oraz zostanie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="db383-167">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="db383-168">Aby debugować niestandardowego formantu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="db383-168">To debug your custom control at design time</span></span>  
  
1.  <span data-ttu-id="db383-169">Otwórz **DebugControl** pliku źródłowego w **edytora kodu** i umieść punkt przerwania na `Set` akcesor `DemoString` właściwości.</span><span class="sxs-lookup"><span data-stu-id="db383-169">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2.  <span data-ttu-id="db383-170">Naciśnij klawisz F5, aby rozpocząć sesję debugowania.</span><span class="sxs-lookup"><span data-stu-id="db383-170">Press F5 to start the debugging session.</span></span> <span data-ttu-id="db383-171">Należy pamiętać, że utworzono nowe wystąpienie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="db383-171">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="db383-172">Można rozróżnić wystąpień na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="db383-172">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="db383-173">Wystąpienie debugowania ma wyraz **systemem** na pasku tytułu</span><span class="sxs-lookup"><span data-stu-id="db383-173">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="db383-174">Wystąpienie debugowania ma **Start** znajdującego się na jego **debugowania** narzędzi wyłączone</span><span class="sxs-lookup"><span data-stu-id="db383-174">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="db383-175">Punkt przerwania jest ustawiony w przypadku debugowania.</span><span class="sxs-lookup"><span data-stu-id="db383-175">Your breakpoint is set in the debugging instance.</span></span>  
  
3.  <span data-ttu-id="db383-176">W tym nowym wystąpieniu programu Visual Studio Otwórz rozwiązanie "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="db383-176">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="db383-177">Można łatwo znaleźć rozwiązania, wybierając **ostatnich projektów** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="db383-177">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="db383-178">Plik rozwiązania "DebuggingExample.sln" zostaną wyświetlone jako ostatnio używanych plików.</span><span class="sxs-lookup"><span data-stu-id="db383-178">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="db383-179">Otwórz Form1 w **Projektant formularzy** i wybierz **DebugControl** formantu.</span><span class="sxs-lookup"><span data-stu-id="db383-179">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5.  <span data-ttu-id="db383-180">Zmień wartość `DemoString` właściwości.</span><span class="sxs-lookup"><span data-stu-id="db383-180">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="db383-181">Zauważ, że po zatwierdzeniu zmian debugowania wystąpienie programu Visual Studio uzyskuje fokus i wykonywania zatrzymuje się na punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="db383-181">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="db383-182">Można pojedynczy krok za pomocą metody dostępu właściwości równie Twojej czy innego kodu.</span><span class="sxs-lookup"><span data-stu-id="db383-182">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6.  <span data-ttu-id="db383-183">Po zakończeniu sesję debugowania można zamknąć odrzucając hostowanej wystąpienie programu Visual Studio lub klikając **Zatrzymaj debugowanie** przycisk w przypadku debugowania.</span><span class="sxs-lookup"><span data-stu-id="db383-183">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="db383-184">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="db383-184">Next Steps</span></span>  
 <span data-ttu-id="db383-185">Teraz, aby umożliwić debugowanie niestandardowych formantów w czasie projektowania, istnieje wiele możliwości rozszerzania formantu interakcji z programu Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="db383-185">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="db383-186">Można użyć <xref:System.ComponentModel.Component.DesignMode%2A> właściwość <xref:System.ComponentModel.Component> klasy do kodu zapisu, które zostaną wykonane tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="db383-186">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="db383-187">Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="db383-187">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="db383-188">Istnieje kilka atrybutów można zastosować do właściwości formantu do manipulowania interakcji kontrolki niestandardowej przy użyciu projektanta.</span><span class="sxs-lookup"><span data-stu-id="db383-188">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="db383-189">Można znaleźć tych atrybutów w <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="db383-189">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="db383-190">Można pisać niestandardowe projektanta dla formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="db383-190">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="db383-191">Umożliwia pełną kontrolę nad środowiskiem projektu przy użyciu extensible infrastruktury projektanta udostępnianych przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="db383-191">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="db383-192">Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie funkcje systemu Windows formularze kontroli czy ma korzystać z programu Visual Studio czasu projektowania](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="db383-192">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db383-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db383-193">See Also</span></span>  
 [<span data-ttu-id="db383-194">Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="db383-194">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [<span data-ttu-id="db383-195">Porady: uzyskiwanie dostępu do usług w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="db383-195">How to: Access Design-Time Services</span></span>](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [<span data-ttu-id="db383-196">Porady: dostęp do obsługi w formularzach systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="db383-196">How to: Access Design-Time Support in Windows Forms</span></span>](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
