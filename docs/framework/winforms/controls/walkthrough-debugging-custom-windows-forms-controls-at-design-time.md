---
title: Debuguj niestandardowe kontrolki w czasie projektowania
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9e292a1219c24571bcb35db2fe357b0197c8812
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740186"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="6aaac-102">Przewodnik: debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="6aaac-102">Walkthrough: Debug Custom Windows Forms Controls at Design Time</span></span>

<span data-ttu-id="6aaac-103">Podczas tworzenia kontrolki niestandardowej często okaże się, że konieczne jest debugowanie zachowania w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="6aaac-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="6aaac-104">Jest to szczególnie ważne w przypadku tworzenia niestandardowego projektanta dla kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="6aaac-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="6aaac-105">Aby uzyskać szczegółowe informacje, zobacz [Przewodnik: Tworzenie kontrolki Windows Forms, która korzysta z funkcji czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="6aaac-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

<span data-ttu-id="6aaac-106">Kontrolki niestandardowe można debugować przy użyciu programu Visual Studio, podobnie jak w przypadku debugowania innych klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6aaac-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="6aaac-107">Różnica polega na tym, że debugujesz osobne wystąpienie programu Visual Studio, na którym działa kod kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="6aaac-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="6aaac-108">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="6aaac-108">Create the project</span></span>

<span data-ttu-id="6aaac-109">Pierwszym krokiem jest utworzenie projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6aaac-109">The first step is to create the application project.</span></span> <span data-ttu-id="6aaac-110">Ten projekt będzie używany do kompilowania aplikacji, która hostuje kontrolkę niestandardową.</span><span class="sxs-lookup"><span data-stu-id="6aaac-110">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="6aaac-111">W programie Visual Studio Utwórz projekt aplikacji systemu Windows, a następnie nadaj mu nazwę **DebuggingExample**.</span><span class="sxs-lookup"><span data-stu-id="6aaac-111">In Visual Studio, create a Windows Application project, and name it **DebuggingExample**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="6aaac-112">Tworzenie projektu biblioteki formantów</span><span class="sxs-lookup"><span data-stu-id="6aaac-112">Create the control library project</span></span>

1. <span data-ttu-id="6aaac-113">Dodaj projekt **biblioteki formantów systemu Windows** do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6aaac-113">Add a **Windows Control Library** project to the solution.</span></span>

2. <span data-ttu-id="6aaac-114">Dodaj nowy element **UserControl** do projektu DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="6aaac-114">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="6aaac-115">Nadaj mu nazwę **DebugControl**.</span><span class="sxs-lookup"><span data-stu-id="6aaac-115">Name it **DebugControl**.</span></span>

3. <span data-ttu-id="6aaac-116">W **Eksplorator rozwiązań**usuń domyślną kontrolkę projektu, usuwając plik kodu z podstawową nazwą UserControl1.</span><span class="sxs-lookup"><span data-stu-id="6aaac-116">In **Solution Explorer**, delete the project's default control by deleting the code file with a base name of UserControl1.</span></span>

4. <span data-ttu-id="6aaac-117">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6aaac-117">Build the solution.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="6aaac-118">Punkt kontrolny</span><span class="sxs-lookup"><span data-stu-id="6aaac-118">Checkpoint</span></span>

<span data-ttu-id="6aaac-119">W tym momencie będzie można zobaczyć kontrolkę niestandardową w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="6aaac-119">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="6aaac-120">Aby sprawdzić postęp, Znajdź nową kartę o nazwie **DebugControlLibrary Components** i kliknij, aby ją zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="6aaac-120">To check your progress, find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="6aaac-121">Gdy zostanie otwarty, zobaczysz swój formant jako **DebugControl** z domyślną ikoną obok niej.</span><span class="sxs-lookup"><span data-stu-id="6aaac-121">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>

## <a name="add-a-property-to-your-custom-control"></a><span data-ttu-id="6aaac-122">Dodawanie właściwości do kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="6aaac-122">Add a property to your custom control</span></span>

<span data-ttu-id="6aaac-123">Aby zademonstrować, że kod kontrolki niestandardowej jest uruchomiony w czasie projektowania, należy dodać właściwość i ustawić punkt przerwania w kodzie implementującym właściwość.</span><span class="sxs-lookup"><span data-stu-id="6aaac-123">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>

1. <span data-ttu-id="6aaac-124">Otwórz **DebugControl** w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="6aaac-124">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="6aaac-125">Dodaj następujący kod do definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="6aaac-125">Add the following code to the class definition:</span></span>

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

2. <span data-ttu-id="6aaac-126">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6aaac-126">Build the solution.</span></span>

## <a name="add-your-custom-control-to-the-host-form"></a><span data-ttu-id="6aaac-127">Dodawanie kontrolki niestandardowej do formularza hosta</span><span class="sxs-lookup"><span data-stu-id="6aaac-127">Add your custom control to the host form</span></span>

<span data-ttu-id="6aaac-128">Aby debugować zachowanie w czasie projektowania kontrolki niestandardowej, należy umieścić wystąpienie niestandardowej klasy kontrolek w formularzu hosta.</span><span class="sxs-lookup"><span data-stu-id="6aaac-128">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>

1. <span data-ttu-id="6aaac-129">W projekcie "DebuggingExample" Otwórz formularz Form1 w **Projektant formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="6aaac-129">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>

2. <span data-ttu-id="6aaac-130">W **przyborniku**Otwórz kartę **składniki DebugControlLibrary** i przeciągnij wystąpienie **DebugControl** na formularz.</span><span class="sxs-lookup"><span data-stu-id="6aaac-130">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>

3. <span data-ttu-id="6aaac-131">Znajdź `DemoString` właściwość niestandardową w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="6aaac-131">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="6aaac-132">Należy pamiętać, że można zmienić jej wartość tak jak każda inna właściwość.</span><span class="sxs-lookup"><span data-stu-id="6aaac-132">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="6aaac-133">Należy również zauważyć, że po wybraniu właściwości `DemoString`, ciąg opisu właściwości pojawia się u dołu okna **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="6aaac-133">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="6aaac-134">Konfigurowanie projektu na potrzeby debugowania w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="6aaac-134">Set up the project for design-time debugging</span></span>

<span data-ttu-id="6aaac-135">Aby debugować zachowanie w czasie projektowania kontrolki niestandardowej, należy debugować osobne wystąpienie programu Visual Studio, na którym działa kod kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="6aaac-135">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

1. <span data-ttu-id="6aaac-136">Kliknij prawym przyciskiem myszy projekt **DebugControlLibrary** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6aaac-136">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="6aaac-137">Na arkuszu właściwości **DebugControlLibrary** wybierz kartę **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="6aaac-137">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>

     <span data-ttu-id="6aaac-138">W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny**.</span><span class="sxs-lookup"><span data-stu-id="6aaac-138">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="6aaac-139">Będziesz debugować osobne wystąpienie programu Visual Studio, więc kliknij przycisk wielokropka (![przycisk wielokropka (...) na okno Właściwości przycisku programu Visual Studio](./media/visual-studio-ellipsis-button.png)), aby wyszukać środowisko IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6aaac-139">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="6aaac-140">Nazwa pliku wykonywalnego to **devenv. exe**, a jeśli została zainstalowana w lokalizacji domyślnej, jego ścieżka to *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE*.</span><span class="sxs-lookup"><span data-stu-id="6aaac-140">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE*.</span></span>

3. <span data-ttu-id="6aaac-141">Wybierz **przycisk OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6aaac-141">Select **OK** to close the dialog box.</span></span>

4. <span data-ttu-id="6aaac-142">Kliknij prawym przyciskiem myszy projekt **DebugControlLibrary** i wybierz pozycję **Ustaw jako projekt startowy** , aby włączyć tę konfigurację debugowania.</span><span class="sxs-lookup"><span data-stu-id="6aaac-142">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="debug-your-custom-control-at-design-time"></a><span data-ttu-id="6aaac-143">Debuguj kontrolkę niestandardową w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="6aaac-143">Debug your custom control at design time</span></span>

<span data-ttu-id="6aaac-144">Teraz możesz przystąpić do debugowania kontrolki niestandardowej, która jest uruchamiana w trybie projektowania.</span><span class="sxs-lookup"><span data-stu-id="6aaac-144">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="6aaac-145">Po uruchomieniu sesji debugowania zostanie utworzone nowe wystąpienie programu Visual Studio i zostanie ono użyte do załadowania rozwiązania "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="6aaac-145">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="6aaac-146">Po otwarciu formularza Form1 w **projektancie formularzy**wystąpienie kontrolki niestandardowej zostanie utworzone i rozpocznie działanie.</span><span class="sxs-lookup"><span data-stu-id="6aaac-146">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>

1. <span data-ttu-id="6aaac-147">Otwórz plik źródłowy **DebugControl** w **edytorze kodu** i umieść punkt przerwania w metodzie dostępu `Set` właściwości `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="6aaac-147">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>

2. <span data-ttu-id="6aaac-148">Naciśnij klawisz **F5** , aby rozpocząć sesję debugowania.</span><span class="sxs-lookup"><span data-stu-id="6aaac-148">Press **F5** to start the debugging session.</span></span> <span data-ttu-id="6aaac-149">Zostanie utworzone nowe wystąpienie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6aaac-149">A new instance of Visual Studio is created.</span></span> <span data-ttu-id="6aaac-150">Wystąpienia można rozróżnić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="6aaac-150">You can distinguish between the instances in two ways:</span></span>

    - <span data-ttu-id="6aaac-151">W wystąpieniu debugowania jest **uruchomione** słowo na pasku tytułu</span><span class="sxs-lookup"><span data-stu-id="6aaac-151">The debugging instance has the word **Running** in its title bar</span></span>

    - <span data-ttu-id="6aaac-152">Na wystąpieniu debugowania jest wyłączony przycisk **Start** na pasku narzędzi **debugowania**</span><span class="sxs-lookup"><span data-stu-id="6aaac-152">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>

   <span data-ttu-id="6aaac-153">Punkt przerwania jest ustawiany w wystąpieniu debugowania.</span><span class="sxs-lookup"><span data-stu-id="6aaac-153">Your breakpoint is set in the debugging instance.</span></span>

3. <span data-ttu-id="6aaac-154">W nowym wystąpieniu programu Visual Studio Otwórz rozwiązanie "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="6aaac-154">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="6aaac-155">Możesz łatwo znaleźć rozwiązanie, wybierając pozycję **ostatnie projekty** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="6aaac-155">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="6aaac-156">Plik rozwiązania "DebuggingExample. sln" będzie wyświetlany jako ostatnio używany plik.</span><span class="sxs-lookup"><span data-stu-id="6aaac-156">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="6aaac-157">Otwórz formularz Form1 w **projektancie formularzy** i wybierz formant **DebugControl** .</span><span class="sxs-lookup"><span data-stu-id="6aaac-157">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>

5. <span data-ttu-id="6aaac-158">Zmień wartość właściwości `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="6aaac-158">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="6aaac-159">Po zatwierdzeniu zmiany wystąpienie debugowania programu Visual Studio uzyskuje fokus i wykonywanie zostaje zatrzymane w punkcie przerwania.</span><span class="sxs-lookup"><span data-stu-id="6aaac-159">When you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="6aaac-160">Można wykonać jeden krok przez metodę dostępu do właściwości tak samo jak w przypadku każdego innego kodu.</span><span class="sxs-lookup"><span data-stu-id="6aaac-160">You can single-step through the property accessor just as your would any other code.</span></span>

6. <span data-ttu-id="6aaac-161">Aby zatrzymać debugowanie, Zamknij hostowane wystąpienie programu Visual Studio lub wybierz przycisk **Zatrzymaj debugowanie** w wystąpieniu debugowania.</span><span class="sxs-lookup"><span data-stu-id="6aaac-161">To stop debugging, exit the hosted instance of Visual Studio or select the **Stop Debugging** button in the debugging instance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6aaac-162">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="6aaac-162">Next steps</span></span>

<span data-ttu-id="6aaac-163">Teraz, gdy można debugować niestandardowe kontrolki w czasie projektowania, istnieje wiele możliwości rozszerzania interakcji kontrolki ze środowiskiem IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6aaac-163">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>

- <span data-ttu-id="6aaac-164">Aby napisać kod, który będzie wykonywany tylko w czasie projektowania, można użyć właściwości <xref:System.ComponentModel.Component.DesignMode%2A> klasy <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="6aaac-164">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="6aaac-165">Aby uzyskać szczegółowe informacje, zobacz <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="6aaac-165">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>

- <span data-ttu-id="6aaac-166">Istnieje kilka atrybutów, które można zastosować do właściwości kontrolki, aby manipulować interakcją kontrolki niestandardowej z projektantem.</span><span class="sxs-lookup"><span data-stu-id="6aaac-166">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="6aaac-167">Te atrybuty można znaleźć w przestrzeni nazw <xref:System.ComponentModel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6aaac-167">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="6aaac-168">Można napisać niestandardowy Projektant dla kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="6aaac-168">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="6aaac-169">Zapewnia to pełną kontrolę nad doświadczeniem projektowym przy użyciu rozszerzalnej infrastruktury projektanta uwidocznionej przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6aaac-169">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="6aaac-170">Aby uzyskać szczegółowe informacje, zobacz [Przewodnik: Tworzenie kontrolki Windows Forms, która korzysta z funkcji czasu projektowania programu Visual Studio](creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="6aaac-170">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6aaac-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6aaac-171">See also</span></span>

- [<span data-ttu-id="6aaac-172">Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6aaac-172">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
